---
title: Konfigurieren von Always Encrypted mit Secure Enclaves | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 866d71333297b609642707a793b27c735d29057d
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54327886"
---
# <a name="configure-always-encrypted-with-secure-enclaves"></a>Konfigurieren von Always Encrypted mit Secure Enclaves

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md) erweitert das vorhandene [Always Encrypted](always-encrypted-database-engine.md)-Feature um umfangreichere Funktionalitäten für sensible Daten und schützt gleichzeitig die vertraulichen Daten.

Um Always Encrypted mit Secure Enclaves einzurichten, verwenden Sie den folgenden Workflow:

1. Konfigurieren Sie den Nachweis für den Host-Überwachungsdienst (Host Guardian Service, HSG).
2. Installieren Sie [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] auf dem SQL Server-Computer.
3. Installieren Sie Tools auf dem Client-/Entwicklungscomputer.
4. Konfigurieren Sie den Enclave-Typ in Ihrer SQL Server-Instanz.
5. Stellen Sie Enclave-fähige Schlüssel bereit.
6. Verschlüsseln Sie Spalten, die sensible Daten enthalten.

> [!NOTE]
> Ein ausführliches Tutorial zum Einrichten Ihrer Testumgebung mit anschließendem Testen der Funktionalität von Always Encrypted mit Secure Enclaves in SSMS finden Sie unter [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="configure-your-environment"></a>Konfigurieren Ihrer Umgebung

Um Secure Enclaves mit Always Encrypted verwenden zu können, benötigt Ihre Umgebung Windows Server 2019 Preview und SQL Server Management Studio (SSMS) 18.0 (Vorschauversion), .NET Framework und verschiedene andere Komponenten. In den folgenden Abschnitten finden Sie Details und Links zu den erforderlichen Komponenten.

### <a name="sql-server-computer-requirements"></a>SQL Server-Computeranforderungen

Der Computer, auf dem SQL Server ausgeführt wird, benötigt das folgende Betriebssystem und diese SQL Server-Version:

*SQL Server*:

- [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] oder höher

*Windows*:

- Windows 10 Enterprise, Version 1809
- Windows Server DataCenter (Halbjährlicher Kanal), Version 1809
- Windows Server 2019 Datacenter

> [!IMPORTANT]
> Der SQL Server-Computer muss als überwachten Host mit HGS-Nachweis konfiguriert werden. Der TPM-Nachweis ist die empfohlene Enclave-Nachweis-Methode für Produktionsumgebungen und erfordert, dass SQL Server auf einem physischen und nicht auf einem virtuellen Computer ausgeführt wird. Virtuelle Computer sind ausschließlich für Vorproduktionsumgebungen geeignet.

### <a name="hgs-computer-requirements"></a>HGS-Computeranforderungen

Beim Testen und Erstellen von Prototypen ist ein einzelner HGS-Computer ausreichend. Für die Produktion wird ein Windows-Failovercluster mit 3 Computern dringend empfohlen.

Der Windows Host-Überwachungsdienst (HGS) muss auf separaten HGS-Computern und nicht auf demselben Computer wie SQL Server installiert werden. Informationen zu den Anforderungen an HGS-Computer und zur Einrichtung finden Sie unter [Einrichten des Host-Überwachungsdiensts für Always Encrypted in SQL Server](https://docs.microsoft.com/windows-server/security/set-up-hgs-for-always-encrypted-in-sql-server).


### <a name="determine-your-attestation-service-url"></a>Ermitteln Ihrer URL für den Nachweisdienst

Um diese URL zu ermitteln, müssen Sie Ihre Tools und Anwendungen konfigurieren:

1. Melden Sie sich bei Ihrem SQL Server-Computer als Administrator an.
2. Führen Sie PowerShell als Administrator aus.
3. Führen Sie [Get-HGSClientConfiguration](https://docs.microsoft.com/powershell/module/hgsclient/get-hgsclientconfiguration) aus.
4. Notieren und speichern Sie sich die Eigenschaft „AttestationServerURL“. Dies sollte etwa wie folgt aussehen: `https://x.x.x.x/Attestation`.


### <a name="install-tools"></a>Installieren der Tools

Installieren Sie die folgenden Tools auf dem Client-/Entwicklungscomputer:

1. [.NET Framework 4.7.2](https://www.microsoft.com/net/download/dotnet-framework-runtime).
2. [SSMS 18.0 oder höher](../../../ssms/download-sql-server-management-studio-ssms.md).
3. [SQL Server PowerShell-Module](../../../powershell/download-sql-server-ps-module.md) Version 21.1 oder höher.
4. [Visual Studio (2017 oder höher empfohlen)](https://visualstudio.microsoft.com/downloads/).
5. [Developer Pack für .NET Framework 4.7.2](https://www.microsoft.com/net/download/visual-studio-sdks).
6. [Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider-NuGet-Paket](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider), Version 2.2.0 oder höher.
7. [Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders-NuGet-Paket](https://www.nuget.org/packages?q=Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders).

Die NuGet-Pakete sind für den Einsatz in Visual Studio-Projekten zur Entwicklung von Anwendungen mit Always Encrypted mit Secure Enclaves vorgesehen. Das erste Paket ist nur erforderlich, wenn Sie Ihre Spaltenhauptschlüssel in Azure Key Vault speichern. Weitere Informationen finden Sie unter [Entwickeln von Anwendungen](#develop-applications-issuing-rich-queries-in-visual-studio).

### <a name="configure-a-secure-enclave"></a>Konfigurieren einer Secure Enclave

Auf dem Client-/Entwicklungscomputer:

1. Öffnen Sie SSMS und stellen Sie eine Verbindung mit Ihrer SQL Server-Instanz als Administrator für Active Directory (AD) her.
2. Um sicherzustellen, dass Always Encrypted mit Secure Enclaves in Ihrer Instanz unterstützt wird, führen Sie die folgende Abfrage aus:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type'
   ```

    Die Abfrage sollte eine Zeile zurückgeben, die wie folgt aussieht:  

    | NAME                           | Wert | value_in_use |
    | ------------------------------ | ----- | -------------|
    | column encryption enclave type | 0     | 0            |

3. Konfigurieren Sie den Secure Enclave-Typen als VBS-Enclaves.

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1
   RECONFIGURE
   ```

4. Starten Sie Ihre SQL Server-Instanz neu, damit die vorherige Änderung übernommen wird. Sie können die Instanz in SSMS neu starten, indem Sie im Objekt-Explorer mit der rechten Maustaste darauf klicken und „Neustart“ auswählen. Stellen Sie nach dem Neustart der Instanz eine neue Verbindung her.

5. Vergewissern Sie sich, dass die Secure Enclave geladen ist, indem Sie die folgende Abfrage ausführen:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type'
   ```   

    Die Abfrage sollte eine Zeile zurückgeben, die wie folgt aussieht:  

    | NAME                           | Wert | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | column encryption enclave type | 1     | 1              |

6. Um umfangreiche Berechnungen mit verschlüsselten Spalten zu aktivieren, führen Sie die folgende Abfrage aus:

   ```sql
   DBCC traceon(127,-1)
   ```

    > [!NOTE]
    > Umfangreiche Berechnungen sind in [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] standardmäßig deaktiviert. Sie müssen über die oben genannte Anweisung nach jedem Neustart der SQL Server-Instanz aktiviert werden.

## <a name="provision-enclave-enabled-keys"></a>Bereitstellen Enclave-fähiger Schlüssel

Die Einführung von Enclave-fähigen Schlüsseln ändert nichts an den [Workflows für die Schlüsselbereitstellung und -verwaltung für Always Encrypted](overview-of-key-management-for-always-encrypted.md). Die einzige Änderung betrifft den Workflow zur Bereitstellung von Spaltenschlüsseln, bei dem Sie den Schlüssel nun als Enclave-fähig markieren können (standardmäßig sind Spaltenhauptschlüssel nicht Enclave-fähig). Wenn Sie angeben, dass der neue Spaltenhauptschlüssel Enclave-fähig sein soll (mit SSMS oder PowerShell), geschieht Folgendes:

- Die Eigenschaft **ENCLAVE_COMPUTATIONS** in den Metadaten des Spaltenschlüssels in der Datenbank wird gesetzt.
- Die Werte der Eigenschaften des Spaltenhauptschlüssels (einschließlich der Einstellung von **ENCLAVE_COMPUTATIONS**) werden digital signiert. Das Tool fügt den Metadaten die Signatur hinzu, die mit dem eigentlichen Spaltenhauptschlüssel erzeugt wird. Der Zweck der Signatur ist es zu verhindern, dass böswillige DBAs und Computeradministratoren die Einstellung **ENCLAVE_COMPUTATIONS** manipulieren. Der SQL-Clienttreiber überprüft die Signaturen, bevor die Enclave-Nutzung zugelassen wird. Dadurch haben Sicherheitsadministratoren die Kontrolle darüber, welche Spaltendaten innerhalb der Enclave berechnet werden können.

Die Eigenschaft **ENCLAVE_COMPUTATIONS** eines Spaltenhauptschlüssels ist unveränderlich – Sie können sie nicht mehr ändern, nachdem der Schlüssel bereitgestellt wurde. Sie können jedoch den Spaltenhauptschlüssel durch einen neuen Schlüssel ersetzen, der einen anderen Wert der Eigenschaft **ENCLAVE_COMPUTATIONS** als der ursprüngliche Schlüssel hat, und zwar über einen Prozess, der als [Rotation der Spaltenhauptschlüssel](#initiate-the-rotation-from-the-current-column-master-key-to-the-new-column-master-key) bezeichnet wird. Weitere Informationen zur Eigenschaft **ENCLAVE_COMPUTATIONS** finden Sie unter [ERSTELLEN DES SPALTENHAUPTSCHLÜSSELS](../../../t-sql/statements/create-column-master-key-transact-sql.md).

Um einen Enclave-fähigen Spaltenverschlüsselungsschlüssel bereitzustellen, müssen Sie sicherstellen, dass der Spaltenhauptschlüssel, der den Spaltenverschlüsselungsschlüssel verschlüsselt, Enclave-fähig ist.

Derzeit gelten die folgenden Einschränkungen für die Bereitstellung Enclave-fähiger Schlüssel:

- Enclave-fähige **Spaltenhauptschlüssel müssen im Windows-Zertifikatspeicher oder im Azure Key Vault** gespeichert sein. Das Speichern von Enclave-fähigen Spaltenhauptschlüsseln in anderen Arten von Schlüsselspeichern (Hardwaresicherheitsmodule oder kundenspezifische Schlüsselspeicher) wird derzeit nicht unterstützt.

### <a name="provision-enclave-enabled-keys-using-sql-server-management-studio-ssms"></a>**Bereitstellen von Enclave-fähigen-Schlüsseln mithilfe von SQL Server Management Studio (SSMS)**

Die folgenden Schritte erstellen Enclave-fähige Schlüssel (erfordert SSMS 18.0 oder höher):

1. Stellen Sie mit SSMS eine Datenbankverbindung her.
2. Erweitern Sie Ihre Datenbank im **Objekt-Explorer**, und navigieren Sie zu **Sicherheit** > **Always Encrypted-Schlüssel**.
3. Stellen Sie einen neuen Enclave-fähigen Spaltenhauptschlüssel bereit:

    1. Klicken Sie mit der rechten Maustaste auf **Always Encrypted-Schlüssel**, und wählen Sie **Neuer Spaltenhauptschlüssel...**.
    2. Wählen Sie den Namen des Spaltenhauptschlüssels aus.
    3. Stellen Sie sicher, dass Sie entweder **Windows-Zertifikatspeicher (Aktueller Benutzer oder lokaler Computer)** oder **Azure Key Vault** auswählen.
    4. Wählen Sie **Enclave-Berechnungen zulassen**.
    5. Wenn Sie Azure Key Vault ausgewählt haben, melden Sie sich bei Azure an, und wählen Sie Ihren Schlüsseltresor. Weitere Informationen zum Erstellen eines Schlüsseltresors für Always Encrypted finden Sie unter [Verwalten Ihrer Schlüsseltresore im Azure-Portal](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/).
    6. Wählen Sie Ihren Schlüssel aus, wenn er bereits vorhanden ist, oder folgen Sie den Anweisungen auf dem Formular, um einen neuen Schlüssel zu erstellen.
    7. Klicken Sie auf **OK**.

        ![Enclave-Berechnungen zulassen](./media/always-encrypted-enclaves/allow-enclave-computations.png)

4. Erstellen Sie einen neuen Enclave-fähigen Spaltenverschlüsselungsschlüssel:

    1. Klicken Sie mit der rechten Maustaste auf **Always Encrypted-Schlüssel**, und wählen Sie **Neuer Spaltenverschlüsselungsschlüssel**.
    2. Geben Sie einen Namen für den neuen Spaltenverschlüsselungsschlüssel ein.
    3. Wählen Sie in der Dropdownliste **Spaltenhauptschlüssel** den in den vorherigen Schritten erstellten Spaltenhauptschlüssel.
    4. Klicken Sie auf **OK**.

### <a name="provision-enclave-enabled-keys-using-powershell"></a>**Bereitstellen Enclave-fähiger Schlüssel mit PowerShell**

In den folgenden Abschnitten finden Sie Beispiele für PowerShell-Skripte zur Bereitstellung von Enclave-fähigen Schlüsseln. Die Schritte, die spezifisch (neu) für Always Encrypted mit Secure Enclaves sind, werden hervorgehoben. Weitere Informationen (nicht spezifisch für Always Encrypted mit Secure Enclaves) zur Bereitstellung von Schlüsseln mit PowerShell finden Sie unter [Konfigurieren von Always Encrypted-Schlüsseln mit PowerShell](https://docs.microsoft.com/sql/relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell).

**Bereitstellen Enclave-fähiger Schlüssel – Windows-Zertifikatspeicher**

Öffnen Sie auf dem Client-/Entwicklungscomputer Windows PowerShell ISE, und führen Sie das folgende Skript aus.

Dabei ist die Verwendung des `-AllowEnclaveComputations`-Parameters im [**New-SqlCertificateStoreColumnMasterKeySettings**](https://docs.microsoft.com/powershell/module/sqlserver/new-sqlcertificatestorecolumnmasterkeysettings)-Cmdlet wichtig.

```powershell
# Create a column master key in Windows Certificate Store.
$cert = New-SelfSignedCertificate -Subject "\<Subject Name\>" -CertStoreLocation Cert:CurrentUser\\My -KeyExportPolicy Exportable -Type DocumentEncryptionCert -KeyUsage DataEncipherment -KeySpec KeyExchange

# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database. Provide the server/db name. Modify the connection string, if needed.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " + $databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Create a SqlColumnMasterKeySettings object for your column master key
# using the -AllowEnclaveComputations parameter.
$cmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -Thumbprint $cert.Thumbprint -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "<column master key name in the database>"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database.
$cekName = "<column encryption key name in the database>"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```


### <a name="provisioning-enclave-enabled-keys---azure-key-vault"></a>Bereitstellen Enclave-fähiger Schlüssel – Azure Key Vault

Öffnen Sie auf dem Client-/Entwicklungscomputer Windows PowerShell ISE, und führen Sie das folgende Skript aus.

**Schritt 1: Stellen Sie den Spaltenhauptschlüssel im Azure Key Vault bereit**

Dies ist auch über das Azure-Portal möglich. Weitere Informationen finden Sie unter [Verwalten Ihrer Schlüsseltresore im Azure-Portal](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/).


```powershell
Import-Module Az
Connect-AzAccount

# User values
$SubscriptionId = "<Azure SubscriptionId>"
$resourceGroup = "<resource group name>"
$azureLocation = "<datacenter location>"
$akvName = "<key vault name>"
$akvKeyName = "<key name>"

# Set the context to the specified subscription.
$azureCtx = Set-AzContext -SubscriptionId $SubscriptionId

# Create a new resource group - skip, if your desired group already exists.
New-AzResourceGroup -Name $resourceGroup -Location $azureLocation

# Create a new key vault - skip if your vault already exists.
New-AzKeyVault -VaultName $akvName -ResourceGroupName $resourceGroup -Location $azureLocation

# Grant yourself permissions needed to create and use the column master key.
Set-AzKeyVaultAccessPolicy -VaultName $akvName -ResourceGroupName $resourceGroup -PermissionsToKeys get, create, list, update, wrapKey,unwrapKey, sign, verify -UserPrincipalName $azureCtx.Account

# Create a column master key in Azure Key Vault.
$akvKey = Add-AzureKeyVaultKey -VaultName $akvName -Name $akvKeyName -Destination "Software"
```

**Schritt 2: Erstellen Sie die Metadaten für den Spaltenhauptschlüssel in der Datenbank, erstellen Sie den Spaltenverschlüsselungsschlüssel und anschließend die dazugehörigen Metadaten in der Datenbank**


```powershell
# Import the SqlServer module.
Import-Module "SqlServer" -Version

# Connect to your database. Provide the server and db name. If needed, modify the connection string.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " + $databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Authenticate to Azure before calling New-SqlAzureKeyVaultColumnMasterKeySettings,
# because -AllowEnclaveComputations causes a call to Azure Key Vault
# to generate the signature of the column master key.
Add-SqlAzureAuthenticationContext -Interactive

# Create a SqlColumnMasterKeySettings object for your column master key.
$cmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyURL $akvKey.ID -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "<column master key name in the database>"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database.
$cekName = "<column encryption key name in the database>"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```


## <a name="identify-enclave-enabled-keys-and-columns"></a>Bestimmen von Enclave-fähigen Schlüsseln und Spalten

Um Spaltenhauptschlüssel aufzulisten, die in Ihrer Datenbank konfiguriert sind, können Sie die Katalogansicht [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md) abfragen (z.B. in SSMS). Die Ansicht wurde um die Spalte **allow_enclave_computations** erweitert. Damit wird angegeben, ob ein Spaltenhauptschlüssel Enclave-fähig ist.

```sql
SELECT name, allow_enclave_computations
FROM sys.column_master_keys
```

Um festzustellen, welche Spaltenverschlüsselungsschlüssel mit Enclave-fähigen Spaltenverschlüsselungsschlüsseln verschlüsselt sind (und somit Enclave-fähig sind), müssen Sie [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md), [sys.column_encryption_key_values](../../system-catalog-views/sys-column-encryption-key-values-transact-sql.md) und [sys.column_encryption_keys](../../system-catalog-views/sys-column-encryption-keys-transact-sql.md) verbinden.


```sql
SELECT cek.name AS [cek_name]
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
FROM sys.column_master_keys cmk
JOIN sys.column_encryption_key_values cekv
   ON cmk.column_master_key_id = cekv.column_master_key_id
JOIN sys.column_encryption_keys cek
   ON cekv.column_encryption_key_id = cek.column_encryption_key_id
```

Um festzustellen, welche Spalten Enclave-fähig sind (die Spalten, die mit Enclave-fähigen Spaltenverschlüsselungscodes verschlüsselt sind), verwenden Sie die folgende Abfrage:

```sql
SELECT c.name AS column_name
, cek.name AS cek_name
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
from sys.columns c
JOIN sys.column_encryption_keys cek 
ON c.column_encryption_key_id = cek.column_encryption_key_id 
JOIN sys.column_encryption_key_values cekv 
ON cekv.column_encryption_key_id = cek.column_encryption_key_id 
JOIN sys.column_master_keys cmk 
ON cmk.column_master_key_id = cekv.column_master_key_id
```


## <a name="manage-collations"></a>Verwalten von Sortierungen

Seit der ersten Version von Always Encrypted gibt es eine Einschränkung bei der Verwendung von Sortierungen: Nicht-BIN2-Sortierungen sind für Zeichenfolgenspalten, die mit deterministischer Verschlüsselung verschlüsselt wurden, nicht zulässig. Diese Einschränkung gilt auch für Enclave-fähige Zeichenfolgenspalten.

Die Verwendung von Nicht-BIN2-Sortierungen ist für Zeichenfolgenspalten zulässig, die mit Verschlüsselung nach dem Zufallsprinzip und Enclave-fähigen Spaltenverschlüsselungsschlüsseln verschlüsselt sind. Die einzige neue Funktionalität, die für solche Spalten aktiviert ist, ist jedoch die dirkte Verschlüsselung. Um umfangreiche Berechnungen (Musterabgleich, Vergleichsoperationen) zu ermöglichen, müssen Sie sicherstellen, dass die Spalte eine BIN2-Sortierung verwendet.

Die folgende Tabelle fasst die Funktionalität für Enclave-fähige Zeichenfolgenspalten zusammen, abhängig vom Verschlüsselungstyp und der Sortierreihenfolge der Sortierung.

| **Sortierreihenfolge für die Sortierung** | **Deterministische Verschlüsselung** | **Verschlüsselung nach dem Zufallsprinzip**                 |
| ------------------------ | ---------------------------- | ----------------------------------------- |
| **Nicht-BIN2**             | Nicht unterstützt                | Direkte Verschlüsselung                       |
| **BIN2**                 | Gleichheitsvergleich          | Direkte Verschlüsselung und umfangreiche Berechnungen |

### <a name="determining-and-changing-collations"></a>Festlegen und Ändern von Sortierungen

In SQL Server können Sortierungen auf Server-, Datenbank- oder Spaltenebene festgelegt werden. Allgemeine Anweisungen zum Bestimmen der aktuellen Sortierung und Ändern einer Sortierung auf Server-, Datenbank- oder Spaltenebene finden Sie unter [Sortierung und Unicode-Unterstützung](https://docs.microsoft.com/sql/relational-databases/collations/collation-and-unicode-support).

**Besondere Überlegungen für Nicht-Unicode-Zeichenfolgenspalten**:

Die folgende zusätzliche Einschränkung, die durch eine Einschränkung der SQL-Clienttreiber (nicht im Zusammenhang mit Always Encrypted) auferlegt wird, gilt für Nicht-UNICODE (ASCII)-Zeichenfolgenspalten. Wenn Sie die Datenbanksortierung für eine Nicht-UNICODE-Zeichenfolgenspalte (char, varchar) überschreiben, müssen Sie sicherstellen, dass die Spaltensortierung die gleiche Codepage verwendet wie die Datenbanksortierung.
Um alle Sortierungen zusammen mit deren Codepagebezeichnern aufzulisten, verwenden Sie die folgende Abfrage:

```sql
SELECT [Name]
   , [Description]
   , [CodePage] = COLLATIONPROPERTY([Name], 'CodePage')
FROM ::fn_helpcollations()
```

Beispielsweise haben Chinese_Traditional_Stroke_Order_100_CI_AI_WS und Chinese_Traditional_Stroke_Order_100_BIN2 die gleiche Codepage (950), aber Chinese_Traditional_Stroke_Order_100_CI_AI_WS und Latin1_General_100_BIN2 haben unterschiedliche Codepages (950 bzw. 1252). Die oben genannte Einschränkung gilt nicht für UNICODE- Zeichenfolgenspalten (nchar, nvarchar). Daher können Sie als Problemumgehung in Betracht ziehen, einen UNICODE-Datentyp für Ihre neuen verschlüsselten Spalten festzulegen, die Sie erstellen, oder den Typ in einen UNICODE-Typ ändern, bevor Sie eine bestehende Spalte verschlüsseln.


## <a name="create-a-new-table-with-enclave-enabled-columns"></a>Erstellen einer neuen Tabelle mit Enclave-fähigen Spalten

Sie können eine neue Tabelle mit verschlüsselten Spalten mit der Anweisung [CREATE TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/create-table-transact-sql) erstellen. Always Encrypted mit Secure Enclaves ändert die Syntax dieser Anweisung nicht.

1. Verbinden Sie sich mit SSMS mit Ihrer Datenbank und öffnen Sie ein Abfragefenster.
   
     > [!NOTE]
     > Always Encrypted muss für diese Aufgabe nicht in der Verbindungszeichenfolge aktiviert sein.

2. Geben Sie im Abfragefenster eine CREATE TABLE-Anweisung aus, um Ihre neue Tabelle zu erstellen, wobei Sie die ENCRYPTED WITH-Klausel in der [Spaltendefinition](https://docs.microsoft.com/sql/t-sql/statements/alter-table-column-definition-transact-sql) für jede zu verschlüsselnde Spalte angeben. Um eine Spalte Enclave-fähig zu machen, stellen Sie sicher, dass Sie einen Enclave-fähigen Spaltenverschlüsselungsschlüssel angeben. Möglicherweise müssen Sie auch eine BIN2-Sortierung für Zeichenfolgenspalten angeben, wenn die Standardsortierung für Ihre Datenbank keine BIN2-Sortierung ist. Weitere Informationen finden Sie im Abschnitt „Einrichten der Sortierung“.

### <a name="example"></a>Beispiel

Die folgende Anweisung erstellt eine neue Tabelle mit zwei verschlüsselten Spalten, „SSN“ und „Salary“. Vorausgesetzt, CEK1 ist ein Enclave-fähiger Spaltenverschlüsselungsschlüssel, unterstützt die SQL Server-Engine sowohl die direkte Verschlüsselung als auch umfangreiche Berechnungen für beide Spalten, da die Spalten die Verschlüsselung nach dem Zufallsprinzip verwenden. Die Anweisung legt eine Latin1\_General\_BIN2-Sortierung für die UNICODE SSN-Spalte fest, Dies ist erforderlich, wenn die standardmäßige Datenbanksortierung eine Nicht-BIN2-Latin1-Sortierung ist.

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [int] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY]
GO
```


## <a name="add-a-new-enclave-enabled-column-to-an-existing-table"></a>Hinzufügen einer neuen Enclave-fähigen Spalte zu einer vorhandenen Tabelle

Mit der [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) / ADD-Anweisung können Sie einer bestehenden Tabelle eine neue verschlüsselte Spalte hinzufügen. Always Encrypted mit Secure Enclaves ändert die Syntax dieser Anweisung nicht.

1. Verbinden Sie sich mit SSMS mit Ihrer Datenbank und öffnen Sie ein Abfragefenster.
    
   Always Encrypted muss für diese Aufgabe nicht in der Verbindungszeichenfolge aktiviert sein.

2. Geben Sie im Abfragefenster die ALTER TABLE-Anweisung mit der ADD-Klausel an, indem Sie die ENCRYPTED WITH-Klausel in der [Spaltendefinition](https://docs.microsoft.com/sql/t-sql/statements/alter-table-column-definition-transact-sql) angeben und einen Enclave-fähigen Spaltenverschlüsselungsschlüssel verwenden. Möglicherweise müssen Sie auch eine BIN2-Sortierung angeben, wenn Ihre neue Spalte eine Zeichenfolgenspalten und die Standardsortierung für Ihre Datenbank keine BIN2-Sortierung ist. Weitere Informationen finden Sie im Abschnitt „Einrichten der Sortierung“.

### <a name="example"></a>Beispiel

Vorausgesetzt, CEK1 ist ein Enclave-fähiger Spaltenverschlüsselungsschlüssel, fügt die folgende Anweisung eine neue verschlüsselte Spalte namens „BirthDate“ hinzu, die sowohl umfangreiche Abfragen als auch die direkte Verschlüsselung unterstützt (da die Spalte die Verschlüsselung nach dem Zufallsprinzip verwendet).

```sql
ALTER TABLE [dbo].[Employees]
ADD [BirthDate] [Date] ENCRYPTED WITH (
COLUMN_ENCRYPTION_KEY = [CEK1],
ENCRYPTION_TYPE = Randomized,
ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NULL
```


## <a name="prepare-an-ssms-query-window-with-always-encrypted-enabled"></a>Vorbereiten eines SSMS-Abfragefensters mit aktiviertem Always Encrypted

So fügen Sie die erforderlichen Verbindungsparameter hinzu, um Enclave-Berechnungen zu ermöglichen:

1. Öffnen Sie SSMS.
2. Nachdem Sie Ihren Servernamen und einen Datenbanknamen im Dialogfeld „Mit Server verbinden“ angegeben haben, klicken Sie auf **Optionen**. Navigieren Sie zur Registerkarte **Always Encrypted**, wählen Sie **Always Encrypted aktivieren**, und geben Sie die Enclave-Nachweis-URL an.
    
    ![Spaltenverschlüsselungseinstellung](./media/always-encrypted-enclaves/column-encryption-setting.png)

3. Klicken Sie auf „Verbinden“.
4. Öffnen Sie ein neues Abfragefenster.

Wenn Sie bereits ein Abfragefenster geöffnet haben, können Sie so alternativ die Datenbankverbindung aktualisieren, um Always Encrypted zu aktivieren:

1. Klicken Sie mit der rechten Sie Maustaste auf eine beliebige Stelle in einem vorhandenen Abfragefenster.
2. Wählen Sie „Verbindung“ \> „Verbindung ändern“ aus.
3. Klicken Sie auf **Optionen**. Navigieren Sie zur Registerkarte **Always Encrypted**, wählen Sie **Always Encrypted aktivieren**, und geben Sie die Enclave-Nachweis-URL an.
4. Klicken Sie auf „Verbinden“.


## <a name="work-with-encrypted-columns"></a>Arbeiten mit verschlüsselten Spalten

### <a name="encrypt-an-existing-plaintext-column-in-place"></a>Direkte Verschlüsselung einer vorhandene Klartextspalte

Sie können eine vorhandene Klartextspalte mit der Anweisung [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) / ALTER COLUMN mit direkter Verschlüsselung verschlüsseln, sofern Sie einen Enclave-fähigen Spaltenverschlüsselungsschlüssel verwenden.

Um eine Spalte mit einem Schlüssel zu verschlüsseln, der nicht Enclave-fähig ist, müssen Sie clientseitige Tools verwenden, wie beispielsweise den Always Encrypted-Assistenten in SSMS oder das Set-SqlColumnEncryption-Cmdlet im SqlServer PowerShell-Modul. Einzelheiten dazu finden Sie unter:

- [Always Encrypted-Assistent](always-encrypted-wizard.md)
- [Konfigurieren der Spaltenverschlüsselung mithilfe von PowerShell](configure-column-encryption-using-powershell.md)


### <a name="prerequisites"></a>Voraussetzungen

- Ihre vorhandene Spalte ist nicht verschlüsselt.
- Sie haben Enclave-fähige Schlüssel bereitgestellt.
- Sie haben Zugriff auf den Spaltenhauptschlüssel.

#### <a name="steps"></a>Schritte

1. Bereiten Sie ein SSMS-Abfragefenster mit Always Encrypted und Enclave-Berechnungen vor, die in der Datenbankverbindung aktiviert sind. Weitere Informationen finden Sie unter [Vorbereiten eines SSMS-Abfragefensters mit aktiviertem Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).
2. Geben Sie im Abfragefenster die ALTER TABLE-Anweisung mit der ALTER COLUMN-Klausel an, indem Sie einen Enclave-fähigen Spaltenverschlüsselungsschlüssel in der ENCRYPTED WITH-Klausel verwenden. Wenn Ihre Spalte eine Zeichenfolgenspalte ist (z.B. char, varchar, nchar, nchar, nvarchar), müssen Sie möglicherweise auch die Sortierung in eine BIN2-Sortierung ändern. Weitere Informationen finden Sie im Abschnitt „Einrichten der Sortierung“.
    
    > [!NOTE]
    > Wenn Ihr Spaltenhauptschlüssel in Azure Key Vault gespeichert ist, werden Sie ggf. dazu aufgefordert, sich bei Azure anzumelden.

3. Sie können (optional) den Plancache mit [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md) leeren, um sicherzustellen, dass die Pläne für jede Abfrage anhand der verschlüsselten Spalten bei der ersten Abfrageausführung neu erstellt werden.
  
    > [!NOTE]
    > Wenn Sie den Plan für die betroffene Abfrage nicht aus dem Cache entfernen, kann bei der ersten Abfrageausführung nach der Verschlüsselung ein Fehler auftreten.

    > [!NOTE]
    > Verwenden Sie DBCC FREEPROCCACHE, um den Plancache sorgfältig zu leeren, da dies zu einer vorübergehenden Verschlechterung der Abfrageleistung führen kann. Um die negativen Auswirkungen des Leerens des Caches zu minimieren, können Sie nur die Pläne für die betroffenen Abfragen selektiv entfernen.

4.  Sie können (optional) [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) aufrufen, um die Metadaten für die Parameter jedes Moduls (Stored Procedure, Function, View, Trigger) zu aktualisieren, die möglicherweise durch Verschlüsselung der Spalten ungültig wurden.

#### <a name="example"></a>Beispiel

Im Beispiel unten wird folgendes vorausgesetzt:

  - CEK1 ist ein Enclave-fähiger Spaltenverschlüsselungsschlüssel.

  - Die SSN-Spalte ist Klartext und verwendet derzeit eine Latin1, Nicht-BIN2-Sortierung (z.B. Latin1\_General\_CI\_AI\_KS\_WS).

Die Anweisung verschlüsselt die SSN-Spalte mit der Verschlüsselung nach dem Zufallsprinzip und Enclave-fähigem Spaltenverschlüsselungsschlüssel. Außerdem wird die standardmäßige Datenbanksortierung mit der entsprechenden (in der gleichen Codepage) BIN2-Sortierung überschrieben.

Der Vorgang erfolgt online (ONLINE = ON). Beachten Sie auch den Aufruf von **DBCC FREEPROCCACHE**, der die Pläne der Abfragen neu erstellt, die von der Änderung des Tabellenschemas betroffen sind.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char] COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
WITH
(ONLINE = ON)
GO
DBCC FREEPROCCACHE
GO
```


### <a name="make-an-existing-encrypted-column-enclave-enabled"></a>Aktivieren der Enclave-Funktionalität für eine verschlüsselte Spalte

Es gibt mehrere Möglichkeiten, die Enclave-Funktionalität für eine bestehende Spalte zu aktivieren, die nicht Enclave-fähig ist. Für welche Methode Sie sich entscheiden, hängt von verschiedenen Faktoren ab:

- **Bereich/Granularität:** Möchten Sie die Enclave-Funktionalität für eine Teilmenge von Spalten oder für alle mit einem bestimmten Spaltenhauptschlüssel geschützten Spalten aktivieren?
- **Datengröße:** Wie groß sind die Tabellen mit den Spalten, die enclavefähig sein sollen?
- Möchten Sie auch den Verschlüsselungstyp für Ihre Spalte(n) ändern? Denken Sie daran, dass nur die Verschlüsselung nach dem Zufallsprinzip umfangreiche Berechnungen (Musterabgleich, Vergleichsoperatoren) unterstützt. Wenn Ihre Spalte mit deterministischer Verschlüsselung verschlüsselt ist, müssen Sie sie auch mit der Verschlüsselung nach dem Zufallsprinzip neu verschlüsseln, um die gesamte Enclave-Funktionalität freizuschalten.

Hier sind die drei Ansätze für die Enclave-Freigabe für bestehende Spalten:

#### <a name="option-1-rotate-the-column-master-key-to-replace-it-with-an-enclave-enabled-column-master-key"></a>Option 1: Drehen Sie den Spaltenhauptschlüssel, um ihn durch einen enclavefähigen Spaltenhauptschlüssel zu ersetzen.
  
- Vorteile:
  - Erfordert keine erneute Verschlüsselung von Daten. Daher ist dies in der Regel der schnellste Ansatz. Dieser Ansatz wird für Spalten mit großen Datenmengen empfohlen. Voraussetzung ist, dass alle Spalten, für die Sie umfangreiche Berechnungen aktivieren müssen, bereits die deterministische Verschlüsselung verwenden und daher nicht erneut verschlüsselt werden müssen.
  - Kann die Enclave-Funktionalität für mehrere Spalten skalierbar aktivieren, da alle Spaltenverschlüsselungsschlüssel und alle verschlüsselten Spalten, die dem ursprünglichen Spaltenhauptschlüssel zugeordnet sind, Enclave-fähig sind.
  
- Nachteile:
  - Unterstützt nicht die Änderung des Verschlüsselungstyps von „deterministisch“ in „nach dem Zufallsprinzip“, sodass er zwar die direkte Verschlüsselung für deterministisch verschlüsselte Spalten aktiviert, aber keine umfangreichen Berechnungen ermöglicht.
  - Ermöglicht es Ihnen nicht, einige der Spalten, die einem bestimmten Spaltenhauptschlüssel zugeordnet sind, selektiv zu konvertieren.
  - Mehraufwand bei der Schlüsselverwaltung – Sie müssen einen neuen Spaltenhauptschlüssel erstellen und ihn Anwendungen zur Verfügung stellen, die die betroffenen Spalten abfragen.  


#### <a name="option-2-this-approach-involves-two-steps-1-rotating-the-column-master-key-as-in-option-1-and-2-re-encrypting-a-subset-of-deterministically-encrypted-columns-using-randomized-encryption-to-enable-rich-computations-for-those-columns"></a>Option 2: Diese Vorgehensweise umfasst zwei Schritte: 1) Drehen des Spaltenhauptschlüssels (wie in Option 1) und 2) erneutes Verschlüsseln einer Teilmenge deterministisch verschlüsselter Spalten unter Verwendung der Verschlüsselung nach dem Zufallsprinzip, um umfangreiche Berechnungen für diese Spalten zu ermöglichen.
  
- Vorteile:
  - Die Daten werden mit direkter Verschlüsselung erneut verschlüsselt. Daher ist dies eine empfohlene Methode, um umfangreiche Abfragen für deterministisch verschlüsselte Spalten mit großen Datenmengen zu ermöglichen. Beachten Sie, dass Schritt 1 die direkte Verschlüsselung für die Spalten unter Verwendung einer deterministischen Verschlüsselung aktiviert, sodass Schritt 2 per Vor-Ort-Verschlüsselung ausgeführt werden kann.
  - Kann die Enclave-Funktionalität für mehrere Spalten skalierbar aktivieren.
  
- Nachteile:
  - Ermöglicht es Ihnen nicht, einige der Spalten, die einem bestimmten Spaltenhauptschlüssel zugeordnet sind, selektiv zu konvertieren.
  - Mehraufwand bei der Schlüsselverwaltung – Sie müssen einen neuen Spaltenhauptschlüssel erstellen und ihn Anwendungen zur Verfügung stellen, die die betroffenen Spalten abfragen.

#### <a name="option-3-re-encrypting-selected-columns-with-a-new-enclave-enabled-column-encryption-key-and-randomized-encryption-if-needed-on-the-client-side"></a>Option 3: Clientseitige Neuverschlüsselung ausgewählter Spalten mit einem neuen enclavefähigen Spaltenverschlüsselungsschlüssel und Verschlüsselung nach dem Zufallsprinzip (falls erforderlich).
  
- Vorteile dieser Methode:
  - Ermöglicht es Ihnen, die Enclave-Funktionalität selektiv für eine Spalte oder eine kleine Teilmenge von Spalten zu aktivieren.
  - Es kann umfangreiche Berechnungen für eine deterministisch verschlüsselte Spalte in einem Schritt ermöglichen.
  - Es ist nicht erforderlich, einen neuen Spaltenhauptschlüssel zu erstellen, sodass die Auswirkungen auf Anwendungen geringer sind.
  
- Nachteile:
  - Der gesamte Inhalt der Tabelle, die die Spalte enthält, muss zur erneuten Verschlüsselung aus der Datenbank verschoben werden. Daher wird dies nur für kleine Tabellen empfohlen. 

Weitere Informationen finden Sie in den folgenden Abschnitten:
  - [Aktivieren der Enclave-Funktionalität für Spalten durch Rotieren des Spaltenhauptschlüssels](#make-columns-enclave-enabled-by-rotating-their-column-master-key)
  - [Erneute direkte Verschlüsselung von Spalten](#re-encrypt-columns-in-place)
  - [Clientseitige erneute Verschlüsselung von Spalten](#re-encrypt-columns-on-the-client-side)

### <a name="make-columns-enclave-enabled-by-rotating-their-column-master-key"></a>Aktivieren der Enclave-Funktionalität für Spalten durch Rotieren des Spaltenhauptschlüssels

Die Rotation eines Spaltenhauptschlüssels ist der Prozess des Ersetzens eines vorhandenen Spaltenhauptschlüssels durch einen neuen. Dabei werden die dem alten Spaltenhauptschlüssel zugeordneten Spaltenverschlüsselungsschlüssel mit dem neuen Spaltenhauptschlüssel neu verschlüsselt. Diesen Workflow gibt es bereits seit der ersten Version von Always Encrypted, um das Ersetzen eines Spaltenhauptschlüssels aus Compliance- oder Sicherheitsgründen zu unterstützen (falls der vorhandene Spaltenhauptschlüssel gefährdet wird).

Always Encrypted mit Enclaves fügt einen neuen Zweck für den Workflow der Hauptschlüsselrotation der Spalte hinzu. Vorausgesetzt, der alte Spaltenhauptschlüssel ist nicht Enclave-fähig, der neue Spaltenhauptschlüssel ist es jedoch, macht der Rotationsprozess alle dem Spaltenhauptschlüssel zugeordneten Spaltenverschlüsselungsschlüssel effektiv Enclave-fähig. Das Rotieren eines Spaltenhauptschlüssels erfordert keine erneute Verschlüsselung der Daten und ist daher ein empfohlenes Verfahren zur Aktivierung der Enclave-Funktionalität für bestehende Spalten.

Das Rotieren des Spaltenhauptschlüssels ändert nichts am Verschlüsselungstyp der betroffenen Spalten. Daher kann nur für deterministisch verschlüsselte Spalten die direkte Verschlüsselung aktiviert werden. Um umfangreiche Berechnungen für Spalten mit deterministischer Verschlüsselung zu aktivieren, müssen Sie die Verschlüsselung nach dem Rotieren des Spaltenhauptschlüssels wiederholen (direkte Verschlüsselung).

Möglicherweise müssen Sie auch die Sortierung für Zeichenfolgenspalten mit Verschlüsselung nach dem Zufallsprinzip in eine BIN2-Sortierung ändern, um umfangreiche Berechnungen zu aktivieren. Weitere Informationen finden Sie im Abschnitt „Einrichten der Sortierung“.

Der Prozess der Rotation eines Spaltenhauptschlüssels ist derselbe, unabhängig davon, ob einer der beiden beteiligten Schlüssel Enclave-fähig ist. Details zum Rotieren des Spaltenhauptschlüssels finden Sie in den folgenden Artikeln:

- [Rotieren eines Spaltenhauptschlüssels mit SSMS](configure-always-encrypted-using-sql-server-management-studio.md)
- [Rotieren eines Spaltenhauptschlüssels mit PowerShell](rotate-always-encrypted-keys-using-powershell.md)

Zur Vereinfachung finden Sie unten ein PowerShell-Beispielskript zum Rotieren eines Spaltenhauptschlüssels.

#### <a name="pre-requisites"></a>Voraussetzungen

- Stellen haben einen neuen Enclave-fähigen Spaltenhauptschlüssel bereitgestellt.
- Sie können sowohl auf den alten als auch den neuen Spaltenhauptschlüssel zugreifen.
- Alle Zeichenfolgenspalten, die mit dem alten Spaltenhauptschlüssel geschützt sind, verwenden BIN2-Sortierungen. (Hinweis: Alternativ können Sie die Sortierung von Zeichenfolgenspalten nach dem Rotieren des Spaltenhauptschlüssels ändern).

#### <a name="steps"></a>Schritte

Fügen Sie das folgende Skript in Windows PowerShell ISE ein, und ersetzen Sie die \<Platzhalter\> durch Ihre spezifischen Werte:


```powershell
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database. Modify server/db name or/and the connection string, if needed.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " +
$databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Set the names of the old/current column master key and the new/target enclave-enabled column master key. (Change the names, if needed).
$oldCmkName = "<old column master key name>"
$newCmkName = "<new column master key name>"

# Authenticate to Azure. Needed only of either column master key is stored in Azure Key Vault.
Add-SqlAzureAuthenticationContext -Interactive

# Initiate the rotation from the current column master key to the new column master key.
Invoke-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName $oldCmkName
-TargetColumnMasterKeyName $newCmkName -InputObject $database

# Complete the rotation of the old column master key.
Complete-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName
$oldCmkName -InputObject $database

# Remove the old column master key metadata.
Remove-SqlColumnMasterKey -Name $oldCmkName -InputObject $database
```


### <a name="re-encrypt-columns-in-place"></a>Erneute direkte Verschlüsselung von Spalten 

Nachdem Sie die Enclave-Funktionalität für Ihre Spalten aktiviert haben, können Sie die folgenden Operationen innerhalb der Enclave ausführen, ohne die Daten aus der Datenbank verschieben zu müssen:

- Rotieren des Spaltenverschlüsselungsschlüssels (um ihn durch einen neuen Schlüssel zu ersetzen), z.B. um Compliance-Vorschriften einzuhalten, von denen einige eine periodische Schlüsselrotation vorschreiben, oder aus Sicherheitsgründen (falls Ihr Spaltenverschlüsselungsschlüssel beeinträchtigt wird).
- Ändern des Verschlüsselungstyps, z.B. von deterministischer Verschlüsselung zu Verschlüsselung nach dem Zufallsprinzip, um umfangreiche Berechnungen für die Spalte zu aktivieren.

#### <a name="prerequisites"></a>Voraussetzungen

- Die Spalte wird mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt.
- Sie haben einen neuen Enclave-fähigen Spaltenverschlüsselungsschlüssel bereitgestellt (wenn es Ihr Ziel ist, den aktuellen Enclave-fähigen Spaltenverschlüsselungsschlüssel zu ersetzen und die Spalte zu schützen).
- Sie haben Zugriff auf den Spaltenhauptschlüssel.

#### <a name="steps"></a>Schritte

1. Bereiten Sie ein SSMS-Abfragefenster mit Always Encrypted und Enclave-Berechnungen vor, die in der Datenbankverbindung aktiviert sind. Weitere Informationen finden Sie unter [Vorbereiten eines SSMS-Abfragefensters mit aktiviertem Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2. Geben Sie im Abfragefenster die [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) mit der ALTER COLUMN-Klausel an, und geben Sie Folgendes in der ENCRYPTED WITH-Klausel an:
    
    1. Der Name des neuen Enclave-fähigen Spaltenverschlüsselungsschlüssels, wenn Sie den aktuellen Schlüssel rotieren. Wenn Sie den Spaltenverschlüsselungsschlüssel nicht ändern, müssen Sie den Namen des aktuellen Schlüssel angeben.
    
    2. Der neue Verschlüsselungstyp, wenn Sie diesen geändert haben. Wenn Sie den Verschlüsselungstyp nicht ändern, müssen Sie den aktuellen Typen angeben.
        
       Wenn die Spalte, die Sie neu verschlüsseln, eine Sortierung (BIN2) verwendet, die sich von der standardmäßigen Datenbanksortierung unterscheidet, müssen Sie den COLLATE-Ausdruck einbeziehen und die aktuelle Spaltensortierung in der Spaltendefinition angeben (um die Sortierung beizubehalten).
        
       > [!NOTE]
       > Wenn Ihr Spaltenhauptschlüssel in Azure Key Vault gespeichert ist, werden Sie ggf. dazu aufgefordert, sich bei Azure anzumelden.

3. Sie können (optional) den Plancache mit [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md) leeren, um sicherzustellen, dass die Pläne für jede Abfrage anhand der neu verschlüsselten Spalten bei der ersten Abfrageausführung neu erstellt werden.
    
    Wenn Sie den Plan für die betroffene Abfrage nicht aus dem Cache entfernen, kann bei der ersten Abfrageausführung nach der erneuten Verschlüsselung ein Fehler auftreten.
    
    > [!NOTE]
    > Verwenden Sie DBCC FREEPROCCACHE, um den Plancache sorgfältig zu leeren, da dies zu einer vorübergehenden Verschlechterung der Abfrageleistung führen kann. Um die negativen Auswirkungen des Leerens des Caches zu minimieren, können Sie nur die Pläne für die betroffenen Abfragen selektiv entfernen. Weitere Informationen finden Sie in der [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md).aspx).

4. Sie können (optional) [sp_refresh_parameter_encryption](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql) aufrufen, um die Metadaten für die Parameter jedes Moduls (Stored Procedure, Function, View, Trigger) zu aktualisieren, die möglicherweise durch eine erneute Verschlüsselung der Spalten ungültig wurden.

#### <a name="examples"></a>Beispiele

Vorausgesetzt, die SSN-Spalte ist derzeit mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel, genannt CEK1, und deterministischer Verschlüsselung verschlüsselt, und die aktuelle Sortierung, die auf Spaltenebene festgelegt ist, ist Latin1\_General\_BIN2, dann verschlüsselt die folgende Anweisung die Spalte erneut mit der Verschlüsselung nach dem Zufallsprinzip und dem gleichen Schlüssel.


```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
GO
DBCC FREEPROCCACHE
GO
```


Vorausgesetzt, die SSN-Spalte ist derzeit mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel, genannt CEK1, und deterministischer Verschlüsselung verschlüsselt, und die standardmäßige Datenbanksortierung ist eine BIN2-Sortierung (und sie wurde nicht auf Spaltenebene festgelegt), wird die Spalte mit der folgenden Anweisung mit einem neuen Enclave-fähigen Schlüssel, genannt CEK2, erneut verschlüsselt (ohne den Verschlüsselungstyp zu ändern).

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK2]
, ENCRYPTION\_TYPE = Deterministic
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
GO
DBCC FREEPROCCACHE
GO
```

Vorausgesetzt, die SSN-Spalte ist derzeit mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel, genannt CEK1, und deterministischer Verschlüsselung verschlüsselt, und die standardmäßige Datenbanksortierung ist eine BIN2-Sortierung (und sie wurde nicht auf Spaltenebene festgelegt), wird die Spalte mit der folgenden Anweisung mit einem neuen Enclave-fähigen Schlüssel, und der Verschlüsselung nach dem Zufallsprinzip erneut verschlüsselt. Darüber hinaus wird der Vorgang im Online-Modus ausgeführt.


```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL 
WITH (ONLINE = ON)
GO
DBCC FREEPROCCACHE
GO
```


### <a name="re-encrypt-columns-on-the-client-side"></a>Clientseitige erneute Verschlüsselung von Spalten 

Die alte Methode zum erneuten Verschlüsseln (und Verschlüsseln oder Entschlüsseln) von Spalten verwendet clientseitige Tools, wie beispielsweise den Always Encrypted-Assistenten oder PowerShell. Im Allgemeinen wird die Verwendung dieser Methode nicht empfohlen, es sei denn, die Tabelle mit den Spalten (die neu verschlüsselt wird) ist klein und Ihr Ziel ist es, die Neuverschlüsselung einer Spalte mit einem neuen Enclave-fähigen Schlüssel zu kombinieren und den Verschlüsselungstyp (von „deterministisch“ in „nach dem Zufallsprinzip“) zu ändern.

Beachten Sie, dass, wenn Sie eine Spalte erneut mit der Verschlüsselung nach dem Zufallsprinzip verschlüsseln, Sie ihre Sortierung möglicherweise in eine BIN2-Sortierung ändern müssen (vor oder nach der erneuten Verschlüsselung), um umfangreiche Berechnungen zu aktivieren. Weitere Informationen finden Sie im Abschnitt „Einrichten der Sortierung“.

Einzelheiten dazu finden Sie unter:

  - Rotieren von Spaltenverschlüsselungsschlüsseln mit SSMS:<https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-wizard>
  - Rotieren von Spaltenverschlüsselungsschlüsseln mit PowerShell:<https://docs.microsoft.com/sql/relational-databases/security/encryption/configure-column-encryption-using-powershell>

### <a name="decrypt-a-column-in-place"></a>Direkte Entschlüsselung einer Spalte

Wenn Ihre Spalte mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt ist, können Sie sie mit der ALTER TABLE-Anweisung direkt entschlüsseln (in eine Klartextspalte konvertieren). Darüber hinaus wird der Vorgang im Online-Modus ausgeführt.

#### <a name="prerequisites"></a>Voraussetzungen

- Die Spalte wird mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt.
- Sie haben Zugriff auf den Spaltenhauptschlüssel.



#### <a name="steps"></a>Schritte

1.  Bereiten Sie ein SSMS-Abfragefenster mit Always Encrypted und Enclave-Berechnungen vor, die in der Datenbankverbindung aktiviert sind. Weitere Informationen finden Sie unter [Vorbereiten eines SSMS-Abfragefensters mit aktiviertem Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2.  Geben Sie im Abfragefenster die [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) mit der ALTER COLUMN-Klausel an, und geben Sie die gewünschte Spaltenkonfiguration **ohne** die ENCRYPTED WITH-Klausel an.
    
    > [!NOTE]
    > Wenn Ihr Spaltenhauptschlüssel in Azure Key Vault gespeichert ist, werden Sie ggf. dazu aufgefordert, sich bei Azure anzumelden.

3.  Sie können (optional) den Plancache mit [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md) leeren, um sicherzustellen, dass die Pläne für jede Abfrage anhand der entschlüsselten Spalten bei der ersten Abfrageausführung neu erstellt werden.
    
    > [!NOTE]
    > Wenn Sie den Plan für die betroffene Abfrage nicht aus dem Cache entfernen, kann bei der ersten Abfrageausführung nach der Entschlüsselung ein Fehler auftreten.
    
    > [!NOTE]
    > Verwenden Sie DBCC FREEPROCCACHE, um den Plancache sorgfältig zu leeren, da dies zu einer vorübergehenden Verschlechterung der Abfrageleistung führen kann. Um die negativen Auswirkungen des Leerens des Caches zu minimieren, können Sie nur die Pläne für die betroffenen Abfragen selektiv entfernen. Weitere Informationen finden Sie in der [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md).

4.  Sie können (optional) [sp\_refresh\_parameter\_encryption](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql) aufrufen, um die Metadaten für die Parameter jedes Moduls (Stored Procedure, Function, View, Trigger) zu aktualisieren, die möglicherweise durch Entschlüsselung der Spalten ungültig wurden.

#### <a name="example"></a>Beispiel

Angenommen, die SSN-Spalte ist verschlüsselt und die aktuelle Sortierung auf Spaltenebene ist Latin1\_General\_BIN2, entschlüsselt die folgende Anweisung die Spalte (und hält die Sortierung unverändert bei – alternativ können Sie die Sortierung ändern, z.B. in eine Nicht-BIN2-Sortierung in derselben Anweisung).


```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
WITH (ONLINE = ON)
GO
DBCC FREEPROCCACHE
GO
```


## <a name="issue-rich-queries-against-encrypted-columns-using-ssms"></a>Erstellen von umfangreichen Abfragen für verschlüsselte Spalten mit SSMS

Der schnellste Weg, um umfangreiche Abfragen für Ihre Enclave-fähigen Spalten auszuprobieren, ist ein SSMS-Abfragefenster mit aktivierter Parametrisierung für Always Encrypted. Weitere Informationen zu dieser nützliche Funktionalität in SSMS finden Sie unter:

- [Parametrisierung für Always Encrypted – Verwenden von SSMS zum Einfügen in, Aktualisieren von und Filtern von verschlüsselten Spalten](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/)
- [Abfragen von verschlüsselten Spalten](configure-always-encrypted-using-sql-server-management-studio.md#querying-encrypted-columns)



### <a name="prerequisites"></a>Voraussetzungen

- Die abzufragenden Spalten sind Enclave-fähig.
- Sie haben Zugriff auf den/die Spaltenhauptschlüssel.

### <a name="steps"></a>Schritte

1.  Bereiten Sie ein SSMS-Abfragefenster mit Always Encrypted und Enclave-Berechnungen vor, die in der Datenbankverbindung aktiviert sind. Weitere Informationen finden Sie unter [Vorbereiten eines SSMS-Abfragefensters mit aktiviertem Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2.  Aktivieren Sie die Parametrisierung für Always Encrypted.
    
    1.  Wählen Sie im Hauptmenü von SSMS die Option **Abfrage** aus.
    2.  Wählen Sie **Abfrageoptionen...** aus.
    3.  Navigieren Sie zu **Ausführung** > **Erweitert**.
    4.  Aktivieren oder deaktivieren Sie „Parametrisierung für Always Encrypted aktivieren“.
    5.  Klicken Sie auf OK.

3.  Erstellen und führen Sie Ihre Abfragen mithilfe von umfangreichen Berechnungen auf verschlüsselten Spalten aus. Sie müssen eine Transact-SQL-Variable für jeden Wert deklarieren, der auf eine verschlüsselte Spalte in Ihrer Abfrage ausgerichtet ist. Die Variablen müssen Inline-Initialisierungen verwenden (kann nicht über die SET-Anweisung festgelegt werden).
    
    > [!NOTE]
    > Wenn Ihr Spaltenhauptschlüssel in Azure Key Vault gespeichert ist, werden Sie ggf. dazu aufgefordert, sich bei Azure anzumelden.

### <a name="example"></a>Beispiel

In diesem Beispiel wird davon ausgegangen, dass die Datenbank eine mit der folgenden Anweisung erstellten Tabelle enthält.

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [int] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY]
GO
```


CEK1 ist ein Enclave-fähiger Spaltenverschlüsselungsschlüssel.

Hier ist ein Beispiel für eine Abfrage dieser Tabelle, die den Richtlinien für die Parametrisierung entspricht:


```sql
DECLARE @SSNPattern CHAR(11) = '%1111%'
DECLARE @MinSalary INT = 1000
SELECT *
FROM [dbo].[Employees]
WHERE SSN LIKE @SSNPattern
    AND [Salary] >= @MinSalary;
GO;
```


## <a name="develop-applications-issuing-rich-queries-in-visual-studio"></a>Entwickeln von Anwendungen, die umfangreiche Abfragen in Visual Studio ausgeben

### <a name="set-up-your-you-visual-studio-project"></a>Einrichten Ihres Visual Studio-Projekts

Um Always Encrypted mit Secure Enclaves in einer.NET Framework-Anwendung verwenden zu können, müssen Sie sicherstellen, dass Ihre Anwendung auf dem.NET Framework 4.7.2 basiert und mit dem Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders-NuGet-Paket integriert ist. Wenn Sie Ihren Spaltenhauptschlüssel im Azure Key Vault speichern, müssen Sie Ihre Anwendung außerdem mit dem Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider -NuGet-Paket, Version 2.2.0 oder höher, integrieren. 

1. Öffnen Sie Visual Studio.
2. Erstellen Sie ein neues Visual C1\#-Projekt, oder öffnen Sie ein vorhandenes Projekt.
3. Stellen Sie sicher, dass das Projekt mindestens auf .NET Framework 4.7.2 ausgerichtet ist. Klicken Sie mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer, wählen Sie „Eigenschaften“ aus und setzen Sie das Zielframework auf .NET Framework 4.7.2.

4. Installieren Sie das folgende NuGet-Paket, indem Sie zu **Tools** (Hauptmenü) > **NuGet-Paket-Manager** > **Paket-Manager-Konsole** gehen. Führen Sie den folgenden Code in der Paket-Manager-Konsole aus.

  ```powershell
  Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider --IncludePrerelease 
  ```

5. Wenn Sie Azure Key Vault für die Speicherung Ihrer Spaltenhauptschlüssel verwenden, installieren Sie die folgenden NuGet-Pakete, indem Sie zu **Tools** (Hauptmenü) > **NuGet-Paket-Manager** > **Paket-Manager-Konsole** gehen. Führen Sie den folgenden Code in der Paket-Manager-Konsole aus.

  ```powershell
  Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider --IncludePrerelease -Version 2.2.0
  Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
  ```

6. Wählen Sie Ihr Projekt aus, und klicken Sie auf „Installieren“.
7. Öffnen Sie die Konfigurationsdatei aus Ihrem Projekt (z.B. App.config oder Web.config).
8. Suchen Sie den Abschnitt \<configuration\>. Suchen Sie im Abschnitt \<configuration\> den Abschnitt \<configSections\> auf. Fügen Sie folgenden Abschnitt innerhalb von \<configSections\> hinzu:

  ```
  <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /\>
  ```

9. Fügen Sie innerhalb des Abschnitts „configuration", unterhalb von \<configSections\>, den folgenden Abschnitt hinzu, der einen Enclave-Provider spezifiziert, der für die Bestätigung und Interaktion mit Intel SGX-Enclaves verwendet werden soll:

  ```
  \<SqlColumnEncryptionEnclaveProviders\>
      \<providers\>
      \<add name="VBS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.VirtualizationBasedSecurityEnclaveProvider, Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,   Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/\>
      \</SqlColumnEncryptionEnclaveProviders\>
  ```
 

### <a name="develop-and-test-your-app"></a>Entwickeln und Testen Ihrer Anwendung 

Um Always Encrypted und Enclave-Berechnungen verwenden zu können, muss sich Ihre Anwendung mit der Datenbank mit den folgenden beiden Schlüsselwörtern in der Verbindungszeichenfolge verbinden: `Column Encryption Setting = Enabled; Enclave Attestation Url=https://x.x.x.x/Attestation` (wobei xxxx eine IP-Adresse, eine Domäne usw. sein kann).

Darüber hinaus muss sich Ihre Anwendung an allgemeine Richtlinien halten, die für Anwendungen gelten, die Always Encrypted verwenden, z.B. muss Ihre Anwendung Zugriff auf Spaltenhauptschlüssel haben, die den Datenbankspalten zugeordnet sind, auf die in Anwendungsabfragen referenziert wird.

Einzelheiten zur Entwicklung von.NET Framework-Anwendungen mit Always Encrypted finden Sie in den folgenden Artikeln:

- [Entwickeln von Always Encrypted mit .NET Framework-Datenanbieter](develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Always Encrypted: Protect sensitive data in SQL Database and store your encryption keys in Azure Key Vault (Schützen vertraulicher Daten in SQL-Datenbank und Speichern von Verschlüsselungsschlüsseln im Azure Key Vault)](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

#### <a name="example"></a>Beispiel

Der folgende Code ist ein einfaches Beispiel für eine C\#-Konsolenanwendung, die eine LIKE-Abfrage für die Tabelle mit dem folgenden Schema ausgibt:

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [int] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY]
GO
```

Es wird vorausgesetzt, dass CEK1 ein Enclave-fähiger Spaltenverschlüsselungsschlüssel ist.


```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Data.SqlClient;
using System.Data;
namespace ConsoleApp1
{
   class Program
   {
      static void Main(string\[\] args)
   {

   string connectionString = "Data Source = myserver; Initial Catalog = ContosoHR; Column Encryption Setting = Enabled;Enclave Attestation Url = https://10.193.16.185/Attestation/attestationservice.svc/signingCertificates; Integrated Security = true";

using (SqlConnection connection = new SqlConnection(connectionString))
{
   connection.Open();
   
   SqlCommand cmd = connection.CreateCommand();
   cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [Salary] FROM [dbo].[Employees] WHERE [SSN] LIKE @SSNPattern AND [Salary] > @MinSalary;";
   
   SqlParameter paramSSNPattern = cmd.CreateParameter();
   
   paramSSNPattern.ParameterName = @"@SSNPattern";
   paramSSNPattern.DbType = DbType.AnsiStringFixedLength;
   paramSSNPattern.Direction = ParameterDirection.Input;
   paramSSNPattern.Value = "%1111";
   paramSSNPattern.Size = 11;
   
   cmd.Parameters.Add(paramSSNPattern);
   
   SqlParameter MinSalary = cmd.CreateParameter();
   
   MinSalary.ParameterName = @"@MinSalary";
   MinSalary.DbType = DbType.Int32;
   MinSalary.Direction = ParameterDirection.Input;
   MinSalary.Value = 900;
   
   cmd.Parameters.Add(MinSalary);
   cmd.ExecuteNonQuery();
   
   SqlDataReader reader = cmd.ExecuteReader();
   while (reader.Read())
   
   {
     Console.WriteLine(reader);
     Console.WriteLine(reader\[0\] + ", " + reader\[1\] + ", " + reader\[2\] + ", " + reader\[3\]);
   }

   Console.ReadKey();

   }
  }
 }
}
```
