---
description: Konfigurieren der Spaltenverschlüsselung mithilfe von Always Encrypted mit PowerShell
title: Konfigurieren der Spaltenverschlüsselung mithilfe von Always Encrypted mit PowerShell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
ms.assetid: 074c012b-cf14-4230-bf0d-55e23d24f9c8
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f03f5dc54c525e850c7654c5860fb56d35ad75c7
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475601"
---
# <a name="configure-column-encryption-using-always-encrypted-with-powershell"></a>Konfigurieren der Spaltenverschlüsselung mithilfe von Always Encrypted mit PowerShell
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]

Dieser Artikel enthält die Schritte zum Festlegen der Always Encrypted-Zielkonfiguration für Datenbankspalten mithilfe des Cmdlet [Set-SqlColumnEncryption](/powershell/sqlserver/sqlserver/vlatest/set-sqlcolumnencryption) (im PowerShell-Modul *SqlServer* ). Das Cmdlet **Set-SqlColumnEncryption** ändert sowohl das Schema der Zieldatenbank sowie die in den ausgewählten Spalten gespeicherten Daten. Die in einer Spalte gespeicherten Daten können verschlüsselt, erneut verschlüsselt oder entschlüsselt werden, je nachdem, welche Zielverschlüsselungseinstellungen für die Spalten angegeben wurden und wie die aktuelle Verschlüsselungskonfiguration aussieht.

::: moniker range=">=sql-server-ver15"

> [!NOTE]
> Wenn Sie [!INCLUDE [sssqlv15-md](../../../includes/sssqlv15-md.md)] verwenden und Ihre SQL Server-Instanz mit Secure Enclave konfiguriert ist, können Sie kryptografische Vorgänge direkt ausführen, ohne Daten aus der Datenbank zu verschieben. Informationen hierzu finden Sie unter [Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-configure-encryption.md). Beachten Sie, dass PowerShell keine direkte Verschlüsselung unterstützt.

::: moniker-end
Weitere Informationen zur Unterstützung von Always Encrytped im PowerShell-Modul „SqlServer“ finden Sie unter [Konfigurieren von Always Encrypted mithilfe von PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md).

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie Folgendes sicher, um die Zielverschlüsselungskonfiguration festzulegen:
- Ein Spaltenverschlüsselungsschlüssel muss in der Datenbank konfiguriert sein (wenn Sie eine Spalte ver- oder entschlüsseln). Weitere Informationen finden Sie unter [Konfigurieren von Always Encrypted-Schlüsseln mithilfe von PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md).
- Sie müssen von dem Computer aus, auf dem die PowerShell-Cmdlets ausgeführt werden, Zugriff auf den Spaltenhauptschlüssel jeder Spalte haben, die Sie verschlüsseln, erneut verschlüsseln oder entschlüsseln möchten. 

## <a name="performance-and-availability-considerations"></a>Überlegungen zu Leistung und Verfügbarkeit

Zum Anwenden der angegebenen Zielverschlüsselungseinstellungen für die Datenbank lädt das Cmdlet **Set SqlColumnEncryption** alle Daten transparent aus den Spalten herunter, die die Zieltabellen enthalten. Danach lädt es die Daten (mit den Zielverschlüsselungseinstellungen) zurück in eine Gruppe temporärer Tabellen und ersetzt schließlich die Originaltabellen durch die neuen Versionen der Tabellen. Der zugrunde liegende .NET Framework-Datenanbieter für SQL Server verschlüsselt und/oder entschlüsselt Daten beim Herunterladen und/oder Hochladen. Dies hängt von der aktuellen Verschlüsselungskonfiguration der Zielspalte und den angegebenen Zielverschlüsselungseinstellungen für die Zielspalten ab. Der Vorgang zum Verschieben der Daten dauert ggf. sehr lange, was von der Größe der Daten in betroffenen Tabellen und der Netzwerkbandbreite abhängt.

Das Cmdlet **Set SqlColumnEncryption** unterstützt zwei Ansätze zum Einrichten der Zielverschlüsselungskonfiguration: online und offline.

Beim Offlineansatz sind die Zieltabellen (sowie alle Tabellen mit Beziehungen zu den Zieltabellen, z.B. Tabellen, mit denen eine Zieltabelle eine Fremdschlüsselbeziehung hat) während der Dauer des Vorgangs für Schreibtransaktionen nicht verfügbar. Die Semantik von Fremdschlüsseleinschränkungen (**CHECK** oder **NOCHECK**) wird beim Offlineansatz immer beibehalten.

Beim Onlineansatz (erfordert das PowerShell-Modul „SqlServer“ mit Version 21.x oder höher) erfolgt der Vorgang des Kopierens und Verschlüsselns, Entschlüsselns oder erneuten Verschlüsselns der Daten inkrementell. Anwendungen können während des Datenverschiebevorgangs Daten in den Zieltabellen lesen und schreiben. Das gilt jedoch nicht für die letzte Iteration, deren Dauer durch den Parameter **MaxDownTimeInSeconds** (den Sie definieren können) begrenzt wird. Zum Erkennen und Verarbeiten der Änderungen, die Anwendungen während des Kopierens der Daten vornehmen können, ermöglicht das Cmdlet die [Änderungsnachverfolgung](../../track-changes/enable-and-disable-change-tracking-sql-server.md) in der Zieldatenbank. Aus diesem Grund belegt der Onlineansatz wahrscheinlich mehr Ressourcen auf Serverseite als der Offlineansatz. Beim Onlineansatz kann der Vorgang ggf. auch wesentlich länger dauern, insbesondere wenn in der Datenbank eine schreibintensive Workload ausgeführt wird. Der Onlineansatz kann verwendet werden, um jeweils eine Tabelle zu verschlüsseln, die über einen Primärschlüssel verfügen muss. Fremdschlüsseleinschränkungen werden standardmäßig mit der **NOCHECK**-Option neu erstellt, um die Auswirkung auf die Anwendungen zu minimieren. Durch Angeben der Option **KeepCheckForeignKeyConstraints** können Sie das Beibehalten der Semantik von Fremdschlüsseleinschränkungen erzwingen. 

Es folgen die Leitlinien für die Wahl zwischen Offline- und Onlineansatz:

Verwenden Sie den Offlineansatz:
- Um die Dauer des Vorgangs zu minimieren. 
- Um Spalten in mehreren Tabellen gleichzeitig zu verschlüsseln/entschlüsseln/neu zu verschlüsseln.
- Wenn die Zieltabelle keinen Primärschlüssel besitzt.

Verwenden Sie den Onlineansatz:
- Um die Ausfallzeit/Nichtverfügbarkeit der Datenbank für die Anwendungen zu minimieren.

## <a name="security-considerations"></a>Sicherheitsüberlegungen

Das Cmdlet **Set-SqlColumnEncryption** , das zum Konfigurieren der Verschlüsselung von Datenbankspalten verwendet wird, verarbeitet sowohl Always Encrypted-Schlüssel als auch die in Datenbankspalten gespeicherten Daten. Es ist daher wichtig, das Cmdlet auf einem sicheren Computer auszuführen. Wenn sich Ihre Datenbank in SQL Server befindet, führen Sie das Cmdlet auf einem anderen Computer als dem Computer aus, der die SQL Server-Instanz hostet. Der primäre Zweck von Always Encrypted ist, sicherzustellen, dass verschlüsselte sensible Daten sicher sind, wenn das Datenbanksystem kompromittiert wird. Daher kann das Ausführen eines PowerShell-Skripts, das Schlüssel und/oder sensible Daten auf dem SQL Server-Computer verarbeitet, die Vorteile der Funktion einschränken oder zunichte machen.

Aufgabe  |Artikel  |Greift auf Klartextschlüssel/-schlüsselspeicher zu  |Greift auf Datenbank zu   
---|---|---|---
Schritt 1: Starten Sie eine PowerShell-Umgebung, und importieren Sie das SqlServer-Modul. | [Importieren des SqlServer-Moduls](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md#importsqlservermodule) | Nein | Nein
Schritt 2: Stellen Sie eine Verbindung mit Ihrem Server und Ihrer Datenbank her. | [Herstellen einer Verbindung mit einer Datenbank](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md#connectingtodatabase) | Nein | Ja
Schritt 3: Authentifizieren Sie sich bei Azure, wenn Ihr Spaltenhauptschlüssel (der den Spaltenverschlüsselungsschlüssel schützt, der rotiert werden soll) in Azure Key Vault gespeichert ist. | [Add-SqlAzureAuthenticationContext](/powershell/sqlserver/sqlserver/vlatest/add-sqlazureauthenticationcontext) | Ja | Nein
Schritt 4. Erstellen Sie ein Array von SqlColumnEncryptionSettings-Objekten – eines für jede Datenbankspalte, die Sie verschlüsseln, erneut verschlüsseln oder entschlüsseln möchten. SqlColumnMasterKeySettings ist ein Objekt, das im Arbeitsspeicher (in PowerShell) vorhanden ist. Es gibt das Zielverschlüsselungsschema für eine Spalte an. | [New-SqlColumnEncryptionSettings](/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionsettings) | Nein | Nein
Schritt 5: Legen Sie die gewünschte Verschlüsselungskonfiguration fest, die in dem Array von SqlColumnMasterKeySettings-Objekten angegeben ist, das Sie im vorherigen Schritt erstellt haben. Eine Spalte wird verschlüsselt, erneut verschlüsselt oder entschlüsselt, je nachdem, welche Zieleinstellungen angegeben wurden und wie die aktuelle Verschlüsselungskonfiguration der Spalte aussieht.| [Set-SqlColumnEncryption](/powershell/sqlserver/sqlserver/vlatest/set-sqlcolumnencryption)<br><br>**Hinweis:** Dieser Schritt kann lange dauern. Je nach gewähltem Ansatz (online oder offline) können Ihre Anwendungen während des gesamten Vorgangs oder nur teilweise nicht auf die Tabellen zugreifen. | Ja | Ja

## <a name="encrypt-columns-using-offline-approach---example"></a>Verschlüsseln von Spalten mithilfe des Offlineansatzes: Beispiel

Das folgende Beispiel veranschaulicht das Festlegen der Zielverschlüsselungskonfiguration für einige Spalten. Wenn eine der Spalten noch nicht verschlüsselt ist, wird sie verschlüsselt. Wenn eine Spalte bereits mit einem anderen Schlüssel und/oder einem anderen Verschlüsselungstyp verschlüsselt ist, wird Sie entschlüsselt und dann mit dem angegebenen Zielschlüssel/-typ erneut verschlüsselt.


```PowerShell
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
# Change the authentication method in the connection string, if needed.
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$database = Get-SqlDatabase -ConnectionString $connStr

# Encrypt the selected columns (or re-encrypt, if they are already encrypted using keys/encrypt types, different than the specified keys/types.
$ces = @()
$ces += New-SqlColumnEncryptionSettings -ColumnName "dbo.Patients.SSN" -EncryptionType "Deterministic" -EncryptionKey "CEK1"
$ces += New-SqlColumnEncryptionSettings -ColumnName "dbo.Patients.BirthDate" -EncryptionType "Randomized" -EncryptionKey "CEK1"
Set-SqlColumnEncryption -InputObject $database -ColumnEncryptionSettings $ces -LogFileDirectory .
```
 
## <a name="encrypt-columns-using-online-approach---example"></a>Verschlüsseln von Spalten mithilfe des Onlineansatzes: Beispiel

Das folgende Beispiel veranschaulicht das Festlegen der Zielverschlüsselungskonfiguration für einige Spalten mithilfe des Onlineansatzes. Wenn eine der Spalten noch nicht verschlüsselt ist, wird sie verschlüsselt. Wenn eine Spalte bereits mit einem anderen Schlüssel und/oder einem anderen Verschlüsselungstyp verschlüsselt ist, wird Sie entschlüsselt und dann mit dem angegebenen Zielschlüssel/-typ erneut verschlüsselt.

```PowerShell
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
# Change the authentication method in the connection string, if needed.
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$database = Get-SqlDatabase -ConnectionString $connStr

# Encrypt the selected columns (or re-encrypt, if they are already encrypted using keys/encrypt types, different than the specified keys/types.
$ces = @()
$ces += New-SqlColumnEncryptionSettings -ColumnName "dbo.Patients.SSN" -EncryptionType "Deterministic" -EncryptionKey "CEK1"
$ces += New-SqlColumnEncryptionSettings -ColumnName "dbo.Patients.BirthDate" -EncryptionType "Randomized" -EncryptionKey "CEK1"
Set-SqlColumnEncryption -InputObject $database -ColumnEncryptionSettings $ces -UseOnlineApproach -MaxDowntimeInSeconds 180 -LogFileDirectory .
```
## <a name="decrypt-columns---example"></a>Entschlüsseln von Spalten: Beispiel

Das folgende Beispiel zeigt, wie alle Spalten, die derzeit in einer Datenbank verschlüsselt sind, entschlüsselt werden können.


```PowerShell
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
# Change the authentication method in the connection string, if needed.
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$database = Get-SqlDatabase -ConnectionString $connStr

# Find all encrypted columns, and create a SqlColumnEncryptionSetting object for each column.
$ces = @()
$tables = $database.Tables
for($i=0; $i -lt $tables.Count; $i++){
    $columns = $tables[$i].Columns
    for($j=0; $j -lt $columns.Count; $j++) {
        if($columns[$j].isEncrypted) {
            $threeColPartName = $tables[$i].Schema + "." + $tables[$i].Name + "." + $columns[$j].Name 
            $ces += New-SqlColumnEncryptionSettings -ColumnName $threeColPartName -EncryptionType "Plaintext" 
        }
    }
}

# Decrypt all columns.
Set-SqlColumnEncryption -ColumnEncryptionSettings $ces -InputObject $database -LogFileDirectory .
```
 
## <a name="next-steps"></a>Nächste Schritte
- [Entwickeln von Anwendungen mit Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>Weitere Informationen  
 - [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
 - [Übersicht über die Schlüsselverwaltung für Always Encrypted](overview-of-key-management-for-always-encrypted.md) 
 - [Konfigurieren von Always Encrypted mithilfe von PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)
 - [Konfigurieren der Spaltenverschlüsselung mit dem Always Encrypted-Assistenten](always-encrypted-wizard.md)
 - [Konfigurieren der Spaltenverschlüsselung unter Verwendung von Always Encrypted mit einem DAC-Paket](configure-always-encrypted-using-dacpac.md)