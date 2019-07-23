---
title: Konfigurieren von Always Encrypted mit Secure Enclaves | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 7fd710359f6a2d97bebd9785dd010ff586f43cd1
ms.sourcegitcommit: 3be14342afd792ff201166e6daccc529c767f02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307583"
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

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

> [!NOTE]
> Ein ausführliches Tutorial zum Einrichten Ihrer Testumgebung mit anschließendem Testen der Funktionalität von Always Encrypted mit Secure Enclaves in SSMS finden Sie unter [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="configure-your-environment"></a>Konfigurieren Ihrer Umgebung

Um Secure Enclaves mit Always Encrypted verwenden zu können, benötigt Ihre Umgebung Windows Server 2019 Preview und SQL Server Management Studio (SSMS) 18.0, .NET Framework und verschiedene andere Komponenten. In den folgenden Abschnitten finden Sie Details und Links zu den erforderlichen Komponenten.

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

Beim Testen und Erstellen von Prototypen ist ein einzelner HGS-Computer ausreichend. Für die Produktion wird ein Windows-Failovercluster mit drei Computern empfohlen.

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
   WHERE [name] = 'column encryption enclave type';
   ```

    Die Abfrage sollte eine Zeile zurückgeben, die wie folgt aussieht:  

    | NAME                           | Wert | value_in_use |
    | ------------------------------ | ----- | -------------|
    | column encryption enclave type | 0     | 0            |

3. Konfigurieren Sie den Secure Enclave-Typen als VBS-Enclaves.

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1;
   RECONFIGURE;
   ```

4. Starten Sie Ihre SQL Server-Instanz neu, damit die vorherige Änderung übernommen wird. Sie können die Instanz in SSMS neu starten, indem Sie im Objekt-Explorer mit der rechten Maustaste darauf klicken und „Neustart“ auswählen. Stellen Sie nach dem Neustart der Instanz eine neue Verbindung her.

5. Vergewissern Sie sich, dass die Secure Enclave geladen ist, indem Sie die folgende Abfrage ausführen:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type';
   ```   

    Die Abfrage sollte eine Zeile zurückgeben, die wie folgt aussieht:  

    | NAME                           | Wert | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | column encryption enclave type | 1     | 1              |

6. Um umfangreiche Berechnungen mit verschlüsselten Spalten zu aktivieren, führen Sie die folgende Abfrage aus:

   ```sql
   DBCC traceon(127,-1);
   ```

    > [!NOTE]
    > Umfangreiche Berechnungen sind in [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] standardmäßig deaktiviert. Sie müssen über die oben genannte Anweisung nach jedem Neustart der SQL Server-Instanz aktiviert werden.

## <a name="provision-enclave-enabled-keys"></a>Bereitstellen Enclave-fähiger Schlüssel

Die Einführung von Enclave-fähigen Schlüsseln ändert nichts an den [Workflows für die Schlüsselbereitstellung und -verwaltung für Always Encrypted](overview-of-key-management-for-always-encrypted.md). Es wird lediglich der Bereitstellungsworkflow für den Spaltenhauptschlüssel geändert. Sie können den Schlüssel nun als Enclave-fähig markieren. Standardmäßig sind Spaltenhauptschlüssel nicht Enclave-fähig. Wenn Sie angeben, dass der neue Spaltenhauptschlüssel Enclave-fähig sein soll (mit SSMS oder PowerShell), geschieht Folgendes:

- Die Eigenschaft `ENCLAVE_COMPUTATIONS` in den Metadaten des Spaltenschlüssels in der Datenbank wird gesetzt.
- Die Eigenschaftswerte des Spaltenhauptschlüssels (einschließlich der Einstellung von `ENCLAVE_COMPUTATIONS`) werden digital signiert. Das Tool fügt den Metadaten die Signatur hinzu, die mit dem eigentlichen Spaltenhauptschlüssel erzeugt wird. Die Signatur verhindert böswillige Änderungen mit der Einstellung `ENCLAVE_COMPUTATIONS`. Der SQL-Clienttreiber überprüft die Signaturen, bevor die Enclave-Nutzung zugelassen wird. Dadurch haben Sicherheitsadministratoren die Kontrolle darüber, welche Spaltendaten innerhalb der Enclave berechnet werden können.

Die `ENCLAVE_COMPUTATIONS`-Eigenschaft eines Spaltenhauptschlüssels ist unveränderlich. Sie kann nach dem Bereitstellen des Schlüssels nicht geändert werden. Sie können jedoch den Spaltenhauptschlüssel durch einen neuen Schlüssel ersetzen, der einen anderen Wert der Eigenschaft `ENCLAVE_COMPUTATIONS` als der ursprüngliche Schlüssel hat. Um den Spaltenhauptschlüssel zu ersetzen, [rotieren Sie ihn](#make-columns-enclave-enabled-by-rotating-their-column-master-key). Weitere Informationen zur Eigenschaft `ENCLAVE_COMPUTATIONS` finden Sie unter [ERSTELLEN DES SPALTENHAUPTSCHLÜSSELS](../../../t-sql/statements/create-column-master-key-transact-sql.md).

Um einen Enclave-fähigen Spaltenverschlüsselungsschlüssel bereitzustellen, müssen Sie sicherstellen, dass der Spaltenhauptschlüssel, der den Spaltenverschlüsselungsschlüssel verschlüsselt, Enclave-fähig ist.

Derzeit gelten die folgenden Einschränkungen für die Bereitstellung Enclave-fähiger Schlüssel:

- Enclave-fähige Spaltenhauptschlüssel müssen im [Windows-Zertifikatspeicher](/windows/desktop/seccrypto/managing-certificates-with-certificate-stores) oder im [Azure Key Vault](/azure/key-vault/key-vault-whatis/) gespeichert sein. Das Speichern von Enclave-fähigen Spaltenhauptschlüsseln in anderen Arten von Schlüsselspeichern (z.B. Hardwaresicherheitsmodule oder kundenspezifische Schlüsselspeicher) wird derzeit nicht unterstützt.

### <a name="provision-enclave-enabled-keys-using-sql-server-management-studio-ssms"></a>Bereitstellen von Enclave-fähigen-Schlüsseln mithilfe von SQL Server Management Studio (SSMS)

Die folgenden Schritte erstellen Enclave-fähige Schlüssel (erfordert SSMS 18.0 oder höher):

1. Stellen Sie mit SSMS eine Datenbankverbindung her.
2. Erweitern Sie Ihre Datenbank im **Objekt-Explorer**, und navigieren Sie zu **Sicherheit** > **Always Encrypted-Schlüssel**.
3. Stellen Sie einen neuen Enclave-fähigen Spaltenhauptschlüssel bereit:

    1. Klicken Sie mit der rechten Maustaste auf **Always Encrypted-Schlüssel**, und wählen Sie **Neuer Spaltenhauptschlüssel** aus.
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

### <a name="provision-enclave-enabled-keys-using-powershell"></a>Bereitstellen Enclave-fähiger Schlüssel mit PowerShell

In den folgenden Abschnitten finden Sie Beispiele für PowerShell-Skripte zur Bereitstellung von Enclave-fähigen Schlüsseln. Die Schritte, die spezifisch (neu) für Always Encrypted mit Secure Enclaves sind, werden hervorgehoben. Weitere Informationen (nicht spezifisch für Always Encrypted mit Secure Enclaves) zur Bereitstellung von Schlüsseln mit PowerShell finden Sie unter [Konfigurieren von Always Encrypted-Schlüsseln mit PowerShell](configure-always-encrypted-keys-using-powershell.md).

#### <a name="provisioning-enclave-enabled-keys---windows-certificate-store"></a>Bereitstellen Enclave-fähiger Schlüssel – Windows-Zertifikatspeicher

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

#### <a name="provisioning-enclave-enabled-keys---azure-key-vault"></a>Bereitstellen Enclave-fähiger Schlüssel – Azure Key Vault

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

Um Spaltenhauptschlüssel aufzulisten, die in Ihrer Datenbank konfiguriert sind, rufen Sie die Katalogansicht [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md) ab (z.B. in SSMS). Die neue Spalte **allow_enclave_computations** gibt an, ob ein Spaltenhauptschlüssel Enclave-fähig ist oder nicht.

```sql
SELECT name, allow_enclave_computations
FROM sys.column_master_keys;
```

Wenn ein Spaltenverschlüsselungsschlüssel mit Enclave-fähigen Spaltenverschlüsselungsschlüsseln verschlüsselt wird, ist er Enclave-fähig. Um Enclave-fähige Spaltenverschlüsselungsschlüssel zurückzugeben, verbindet die folgende Abfrage [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md), [sys.column_encryption_key_values](../../system-catalog-views/sys-column-encryption-key-values-transact-sql.md) und [sys.column_encryption_keys](../../system-catalog-views/sys-column-encryption-keys-transact-sql.md).

```sql
SELECT cek.name AS [cek_name]
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
FROM sys.column_master_keys cmk
JOIN sys.column_encryption_key_values cekv
   ON cmk.column_master_key_id = cekv.column_master_key_id
JOIN sys.column_encryption_keys cek
   ON cekv.column_encryption_key_id = cek.column_encryption_key_id;
```

Spalten, die mit Enclave-fähigen Schlüsseln verschlüsselt werden, sind Enclave-fähig. Um zu bestimmen, welche Spalten Enclave-fähig sind, verwenden Sie die folgende Abfrage:

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
ON cmk.column_master_key_id = cekv.column_master_key_id;
```

## <a name="manage-collations"></a>Verwalten von Sortierungen

Always Encrypted schränkt Sortierungen ein. Nicht-BIN2-Sortierungen sind für Zeichenfolgenspalten mit die deterministische Verschlüsselung verschlüsselt wurden, nicht zulässig. Diese Einschränkung gilt auch für Enclave-fähige Zeichenfolgenspalten.

Die Verwendung von Nicht-BIN2-Sortierungen ist für Zeichenfolgenspalten zulässig, die mit Verschlüsselung nach dem Zufallsprinzip und Enclave-fähigen Spaltenverschlüsselungsschlüsseln verschlüsselt sind. Die einzige neue Funktionalität, die für solche Spalten aktiviert ist, ist jedoch die dirkte Verschlüsselung. Um umfangreiche Berechnungen (Musterabgleich, Vergleichsoperationen) zu ermöglichen, ist für die Spalte eine BIN2-Sortierung erforderlich.

Die folgende Tabelle fasst die Funktionalität für Enclave-fähige Zeichenfolgenspalten zusammen, abhängig vom Verschlüsselungstyp und der Sortierreihenfolge der Sortierung.

| **Sortierreihenfolge für die Sortierung** | **Deterministische Verschlüsselung** | **Verschlüsselung nach dem Zufallsprinzip**                 |
| ------------------------ | ---------------------------- | ----------------------------------------- |
| **Nicht-BIN2**             | Nicht unterstützt                | Direkte Verschlüsselung                       |
| **BIN2**                 | Gleichheitsvergleich          | Direkte Verschlüsselung und umfangreiche Berechnungen |

### <a name="determining-and-changing-collations"></a>Festlegen und Ändern von Sortierungen

In SQL Server können Sortierungen auf Server-, Datenbank- oder Spaltenebene festgelegt werden. Allgemeine Anweisungen zum Bestimmen der aktuellen Sortierung und Ändern einer Sortierung auf Server-, Datenbank- oder Spaltenebene finden Sie unter [Sortierung und Unicode-Unterstützung](../../collations/collation-and-unicode-support.md).

### <a name="special-considerations-for-non-unicode-string-columns"></a>Besondere Überlegungen für Nicht-Unicode-Zeichenfolgenspalten

Die folgende zusätzliche Einschränkung, die durch eine Einschränkung der SQL-Clienttreiber (nicht im Zusammenhang mit Always Encrypted) auferlegt wird, gilt für Nicht-UNICODE (ASCII)-Zeichenfolgenspalten. Wenn Sie die Datenbanksortierung für eine Nicht-UNICODE-Zeichenfolgenspalte (char, varchar) überschreiben, müssen Sie sicherstellen, dass die Spaltensortierung die gleiche Codepage verwendet wie die Datenbanksortierung.
Um alle Sortierungen zusammen mit deren Codepagebezeichnern aufzulisten, verwenden Sie die folgende Abfrage:

```sql
SELECT [Name]
   , [Description]
   , [CodePage] = COLLATIONPROPERTY([Name], 'CodePage')
FROM ::fn_helpcollations();
```

Zum Beispiel haben `Chinese_Traditional_Stroke_Order_100_CI_AI_WS` und `Chinese_Traditional_Stroke_Order_100_BIN2` dieselbe Codepage (950), aber `Chinese_Traditional_Stroke_Order_100_CI_AI_WS` und `Latin1_General_100_BIN2` haben unterschiedliche Codepages (950 bzw. 1252). Die oben genannte Einschränkung gilt nicht für UNICODE-Zeichenfolgenspalten (`nchar`, `nvarchar`). Ziehen Sie in Betracht, einen UNICODE-Datentyp für Ihre neuen verschlüsselten Spalten festzulegen, die Sie erstellen, oder den Typ in einen UNICODE-Typ ändern, bevor Sie eine bestehende Spalte verschlüsseln.

## <a name="create-a-new-table-with-enclave-enabled-columns"></a>Erstellen einer neuen Tabelle mit Enclave-fähigen Spalten

Sie können eine neue Tabelle mit verschlüsselten Spalten mit der Anweisung [CREATE TABLE (Transact-SQL)](../../../t-sql/statements/create-table-transact-sql.md) erstellen. Always Encrypted mit Secure Enclaves ändert die Syntax dieser Anweisung nicht.

1. Verbinden Sie sich mit SSMS mit Ihrer Datenbank und öffnen Sie ein Abfragefenster.

     > [!NOTE]
     > Always Encrypted muss für diese Aufgabe nicht in der Verbindungszeichenfolge aktiviert sein.

2. Geben Sie im Abfragefenster eine `CREATE TABLE`-Anweisung aus, um Ihre neue Tabelle zu erstellen, wobei Sie die `ENCRYPTED WITH`-Klausel in der [Spaltendefinition](../../../t-sql/statements/alter-table-column-definition-transact-sql.md) für jede zu verschlüsselnde Spalte angeben. Um eine Spalte Enclave-fähig zu machen, stellen Sie sicher, dass Sie einen Enclave-fähigen Spaltenverschlüsselungsschlüssel angeben. Möglicherweise müssen Sie auch eine BIN2-Sortierung für Zeichenfolgenspalten angeben, wenn die Standardsortierung für Ihre Datenbank keine BIN2-Sortierungen ist. Weitere Informationen finden Sie im Abschnitt „Einrichten der Sortierung“.

### <a name="example-of-creating-a-new-table-with-enclave-enabled-columns"></a>Beispiel für das Erstellen einer neuen Tabelle mit Enclave-fähigen Spalten

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
) ON [PRIMARY];
GO
```

## <a name="add-a-new-enclave-enabled-column-to-an-existing-table"></a>Hinzufügen einer neuen Enclave-fähigen Spalte zu einer vorhandenen Tabelle

Mit der [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) / ADD-Anweisung können Sie einer bestehenden Tabelle eine neue verschlüsselte Spalte hinzufügen. Always Encrypted mit Secure Enclaves ändert die Syntax dieser Anweisung nicht.

1. Verbinden Sie sich mit SSMS mit Ihrer Datenbank und öffnen Sie ein Abfragefenster.

   Always Encrypted muss für diese Aufgabe nicht in der Verbindungszeichenfolge aktiviert sein.

2. Geben Sie im Abfragefenster die ALTER TABLE-Anweisung mit der ADD-Klausel an, indem Sie die ENCRYPTED WITH-Klausel in der [Spaltendefinition](../../../t-sql/statements/alter-table-column-definition-transact-sql.md) angeben und einen Enclave-fähigen Spaltenverschlüsselungsschlüssel verwenden. Möglicherweise müssen Sie auch eine BIN2-Sortierung angeben, wenn Ihre neue Spalte eine Zeichenfolgenspalten und die Standardsortierung für Ihre Datenbank keine BIN2-Sortierung ist. Weitere Informationen finden Sie im Abschnitt „Einrichten der Sortierung“.

### <a name="example-of-adding-a-new-enclave-enabled-column-to-an-existing-table"></a>Beispiel für das Hinzufügen einer neuen Enclave-fähigen Spalte zu einer vorhandenen Tabelle

Vorausgesetzt, CEK1 ist ein Enclave-fähiger Spaltenverschlüsselungsschlüssel, fügt die folgende Anweisung eine neue verschlüsselte Spalte namens „BirthDate“ hinzu, die sowohl umfangreiche Abfragen als auch die direkte Verschlüsselung unterstützt (da die Spalte die Verschlüsselung nach dem Zufallsprinzip verwendet).

```sql
ALTER TABLE [dbo].[Employees]
ADD [BirthDate] [Date] ENCRYPTED WITH (
COLUMN_ENCRYPTION_KEY = [CEK1],
ENCRYPTION_TYPE = Randomized,
ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NULL;
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

Sie können eine vorhandene Klartextspalte mit der Anweisung [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) / ALTER COLUMN mit direkter Verschlüsselung verschlüsseln, sofern Sie einen Enclave-fähigen Spaltenverschlüsselungsschlüssel verwenden.

Um eine Spalte mit einem Schlüssel zu verschlüsseln, der nicht Enclave-fähig ist, müssen Sie clientseitige Tools verwenden, wie beispielsweise den Always Encrypted-Assistenten in SSMS oder das Set-SqlColumnEncryption-Cmdlet im SqlServer PowerShell-Modul. Einzelheiten dazu finden Sie unter:

- [Always Encrypted-Assistent](always-encrypted-wizard.md)
- [Konfigurieren der Spaltenverschlüsselung mithilfe von PowerShell](configure-column-encryption-using-powershell.md)


#### <a name="prerequisites-for-encrypting-an-existing-plaintext-column-in-place"></a>Voraussetzungen für die direkte Verschlüsselung einer vorhandene Klartextspalte

- Ihre vorhandene Spalte ist nicht verschlüsselt.
- Sie haben Enclave-fähige Schlüssel bereitgestellt.
- Sie haben Zugriff auf den Spaltenhauptschlüssel.

#### <a name="steps-for-encrypting-existing-plaintext-column-in-place"></a>Schritte für die direkte Verschlüsselung einer vorhandene Klartextspalte

1. Bereiten Sie ein SSMS-Abfragefenster mit Always Encrypted und Enclave-Berechnungen vor, die in der Datenbankverbindung aktiviert sind. Weitere Informationen finden Sie unter [Vorbereiten eines SSMS-Abfragefensters mit aktiviertem Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).
2. Geben Sie im Abfragefenster die ALTER TABLE-Anweisung mit der ALTER COLUMN-Klausel an, indem Sie einen Enclave-fähigen Spaltenverschlüsselungsschlüssel in der ENCRYPTED WITH-Klausel verwenden. Wenn Ihre Spalte eine Zeichenfolgenspalte ist (z.B. char, varchar, nchar, nchar, nvarchar), müssen Sie möglicherweise auch die Sortierung in eine BIN2-Sortierung ändern. Weitere Informationen finden Sie im Abschnitt „Einrichten der Sortierung“.
    
    > [!NOTE]
    > Wenn Ihr Spaltenhauptschlüssel in Azure Key Vault gespeichert ist, werden Sie ggf. dazu aufgefordert, sich bei Azure anzumelden.

3. Leeren Sie den Plancache für alle Batches und gespeicherten Prozeduren, die Zugriff auf die Tabelle haben, um die Informationen für die Parameterverschlüsselung zu aktualisieren. 
 
    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```
    > [!NOTE]
    > Wenn Sie den Plan für die betroffene Abfrage nicht aus dem Cache entfernen, kann bei der ersten Abfrageausführung nach der Verschlüsselung ein Fehler auftreten.

    > [!NOTE]
    > Verwenden Sie `ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE` oder `DBCC FREEPROCCACHE`, um den Plancache sorgfältig zu leeren, da dies zu einer vorübergehenden Verschlechterung der Abfrageleistung führen kann. Um die negativen Auswirkungen des Leerens des Caches zu minimieren, können Sie nur die Pläne für die betroffenen Abfragen selektiv entfernen.

4.  Rufen Sie [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) auf, um die Metadaten für die Parameter jedes Moduls (Stored Procedure, Function, View, Trigger) zu aktualisieren, die in [sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) beibehalten werden und möglicherweise durch Verschlüsselung der Spalten ungültig wurden.

#### <a name="example-of-encrypting-existing-plaintext-column-in-place"></a>Beispiel für die direkte Verschlüsselung einer vorhandene Klartextspalte

Im Beispiel unten wird folgendes vorausgesetzt:

- CEK1 ist ein Enclave-fähiger Spaltenverschlüsselungsschlüssel.

- Die SSN-Spalte ist Klartext und verwendet derzeit eine Latin1, Nicht-BIN2-Sortierung (z.B. Latin1\_General\_CI\_AI\_KS\_WS).

Die Anweisung verschlüsselt die SSN-Spalte mit der Verschlüsselung nach dem Zufallsprinzip und Enclave-fähigem Spaltenverschlüsselungsschlüssel. Außerdem wird die standardmäßige Datenbanksortierung mit der entsprechenden (in der gleichen Codepage) BIN2-Sortierung überschrieben.

Der Vorgang erfolgt online (ONLINE = ON). Beachten Sie auch den Aufruf von **ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE**, der die Pläne der Abfragen neu erstellt, die von der Änderung des Tabellenschemas betroffen sind.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char] COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
WITH
(ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
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
  - Unterstützt nicht die Änderung des Verschlüsselungstyps von „deterministisch“ in „zufällig“, sodass er zwar die direkte Verschlüsselung für deterministisch verschlüsselte Spalten aktiviert, aber keine umfangreichen Berechnungen ermöglicht.
  - Ermöglicht es Ihnen nicht, einige der Spalten, die einem bestimmten Spaltenhauptschlüssel zugeordnet sind, selektiv zu konvertieren.
  - Mehraufwand bei der Schlüsselverwaltung – Sie müssen einen neuen Spaltenhauptschlüssel erstellen und ihn Anwendungen zur Verfügung stellen, die die betroffenen Spalten abfragen.  

#### <a name="option-2-this-approach-involves-two-steps-1-rotating-the-column-master-key-as-in-option-1-and-2-re-encrypting-a-subset-of-deterministically-encrypted-columns-using-randomized-encryption-to-enable-rich-computations-for-those-columns"></a>Option 2: Diese Vorgehensweise umfasst zwei Schritte: 1) Drehen des Spaltenhauptschlüssels (wie in Option 1) und 2) erneutes Verschlüsseln einer Teilmenge deterministisch verschlüsselter Spalten unter Verwendung der Verschlüsselung nach dem Zufallsprinzip, um umfangreiche Berechnungen für diese Spalten zu ermöglichen.
  
- Vorteile:
  - Die Daten werden mit direkter Verschlüsselung erneut verschlüsselt. Daher ist dies eine empfohlene Methode, um umfangreiche Abfragen für deterministisch verschlüsselte Spalten mit großen Datenmengen zu ermöglichen. Schritt 1 aktiviert die direkte Verschlüsselung für die Spalten unter Verwendung einer deterministischen Verschlüsselung, sodass Schritt 2 per direkter Verschlüsselung ausgeführt werden kann.
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

#### <a name="prerequisites-of-rotating-the-column-master-key-for-enclave-enabled-columns"></a>Voraussetzungen für die Rotation der Spaltenhauptschlüssel für Enclave-fähige Spalten

- Stellen haben einen neuen Enclave-fähigen Spaltenhauptschlüssel bereitgestellt.
- Sie können sowohl auf den alten als auch den neuen Spaltenhauptschlüssel zugreifen.
- Alle Zeichenfolgenspalten, die mit dem alten Spaltenhauptschlüssel geschützt sind, verwenden BIN2-Sortierungen.

> [!NOTE]
> Alternativ können Sie die Sortierung von Zeichenfolgenspalten nach dem Rotieren des Spaltenhauptschlüssels ändern.

#### <a name="steps-for-rotating-the-column-master-key-for-enclave-enabled-columns"></a>Schritte für die Rotation der Spaltenhauptschlüssel für Enclave-fähige Spalten

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

#### <a name="prerequisites-for-re-encrypting-columns-in-place"></a>Voraussetzungen für die erneute direkte Verschlüsselung von Spalten

- Die Spalte wird mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt.
- Sie haben einen neuen Enclave-fähigen Spaltenverschlüsselungsschlüssel bereitgestellt (wenn es Ihr Ziel ist, den aktuellen Enclave-fähigen Spaltenverschlüsselungsschlüssel zu ersetzen und die Spalte zu schützen).
- Sie haben Zugriff auf den Spaltenhauptschlüssel.

#### <a name="steps-for-re-encrypting-columns-in-place"></a>Schritte für die erneute direkte Verschlüsselung von Spalten

1. Bereiten Sie ein SSMS-Abfragefenster mit Always Encrypted und Enclave-Berechnungen vor, die in der Datenbankverbindung aktiviert sind. Weitere Informationen finden Sie unter [Vorbereiten eines SSMS-Abfragefensters mit aktiviertem Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2. Geben Sie im Abfragefenster die [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) mit der ALTER COLUMN-Klausel an, und geben Sie Folgendes in der ENCRYPTED WITH-Klausel an:
    
    1. Der Name des neuen Enclave-fähigen Spaltenverschlüsselungsschlüssels, wenn Sie den aktuellen Schlüssel rotieren. Wenn Sie den Spaltenverschlüsselungsschlüssel nicht ändern, müssen Sie den Namen des aktuellen Schlüssel angeben.
    
    2. Der neue Verschlüsselungstyp, wenn Sie diesen geändert haben. Wenn Sie den Verschlüsselungstyp nicht ändern, müssen Sie den aktuellen Typen angeben.
        
       Wenn die Spalte, die Sie neu verschlüsseln, eine Sortierung (BIN2) verwendet, die sich von der standardmäßigen Datenbanksortierung unterscheidet, müssen Sie den COLLATE-Ausdruck einbeziehen und die aktuelle Spaltensortierung in der Spaltendefinition angeben (um die Sortierung beizubehalten).
        
       > [!NOTE]
       > Wenn Ihr Spaltenhauptschlüssel in Azure Key Vault gespeichert ist, werden Sie ggf. dazu aufgefordert, sich bei Azure anzumelden.

3. Leeren Sie den Plancache für alle Batches und gespeicherten Prozeduren, die Zugriff auf die Tabelle haben, um die Informationen für die Parameterverschlüsselung zu aktualisieren. 
 
    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```
    > [!NOTE]
    > Wenn Sie den Plan für die betroffene Abfrage nicht aus dem Cache entfernen, kann bei der ersten Abfrageausführung nach der Verschlüsselung ein Fehler auftreten.

    > [!NOTE]
    > Verwenden Sie ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE oder DBCC FREEPROCCACHE, um den Plancache sorgfältig zu leeren, da dies zu einer vorübergehenden Verschlechterung der Abfrageleistung führen kann. Um die negativen Auswirkungen des Leerens des Caches zu minimieren, können Sie nur die Pläne für die betroffenen Abfragen selektiv entfernen.

4.  Rufen Sie [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) auf, um die Metadaten für die Parameter jedes Moduls (Stored Procedure, Function, View, Trigger) zu aktualisieren, die in [sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) beibehalten werden und möglicherweise durch die erneute Verschlüsselung der Spalten ungültig wurden.

#### <a name="examples-of-re-encrypting-columns-in-place"></a>Beispiele für die erneute direkte Verschlüsselung von Spalten

Vorausgesetzt, die SSN-Spalte ist derzeit mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel, genannt CEK1, und deterministischer Verschlüsselung verschlüsselt, und die aktuelle Sortierung, die auf Spaltenebene festgelegt ist, ist Latin1\_General\_BIN2, dann verschlüsselt die folgende Anweisung die Spalte erneut mit der Verschlüsselung nach dem Zufallsprinzip und dem gleichen Schlüssel.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

Vorausgesetzt, die SSN-Spalte ist derzeit mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel, genannt CEK1, und deterministischer Verschlüsselung verschlüsselt, und die standardmäßige Datenbanksortierung ist eine BIN2-Sortierung (und sie wurde nicht auf Spaltenebene festgelegt), wird die Spalte mit der folgenden Anweisung mit einem neuen Enclave-fähigen Schlüssel, genannt CEK2, erneut verschlüsselt (ohne den Verschlüsselungstyp zu ändern).

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK2]
, ENCRYPTION\_TYPE = Deterministic
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

Vorausgesetzt, die SSN-Spalte ist derzeit mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel, genannt CEK1, und deterministischer Verschlüsselung verschlüsselt, und die standardmäßige Datenbanksortierung ist eine BIN2-Sortierung (und sie wurde nicht auf Spaltenebene festgelegt), wird die Spalte mit der folgenden Anweisung mit einem neuen Enclave-fähigen Schlüssel, und der Verschlüsselung nach dem Zufallsprinzip erneut verschlüsselt. Darüber hinaus wird der Vorgang im Online-Modus ausgeführt.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL 
WITH (ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

### <a name="re-encrypt-columns-on-the-client-side"></a>Clientseitige erneute Verschlüsselung von Spalten

Die alte Methode zum erneuten Verschlüsseln (und Verschlüsseln oder Entschlüsseln) von Spalten verwendet clientseitige Tools, wie beispielsweise den Always Encrypted-Assistenten oder PowerShell. Im Allgemeinen wird die Verwendung dieser Methode nicht empfohlen, es sei denn, die Tabelle mit den Spalten (die neu verschlüsselt wird) ist klein und Ihr Ziel ist es, die Neuverschlüsselung einer Spalte mit einem neuen Enclave-fähigen Schlüssel zu kombinieren und den Verschlüsselungstyp (von „deterministisch“ in „zufällig“) zu ändern.

Wenn Sie eine Spalte erneut mit der zufälligen Verschlüsselung verschlüsseln, müssen Sie ihre Sortierung möglicherweise in eine BIN2-Sortierung ändern (vor oder nach der erneuten Verschlüsselung), um umfangreiche Berechnungen zu aktivieren. Weitere Informationen finden Sie im Abschnitt „Einrichten der Sortierung“.

Einzelheiten dazu finden Sie unter:

  - Rotieren von Spaltenverschlüsselungsschlüsseln mit SSMS:<https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-wizard>
  - Rotieren von Spaltenverschlüsselungsschlüsseln mit PowerShell:<https://docs.microsoft.com/sql/relational-databases/security/encryption/configure-column-encryption-using-powershell>

### <a name="decrypt-a-column-in-place"></a>Direkte Entschlüsselung einer Spalte

Wenn Ihre Spalte mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt ist, können Sie sie mit der ALTER TABLE-Anweisung direkt entschlüsseln (in eine Klartextspalte konvertieren). Darüber hinaus wird der Vorgang im Online-Modus ausgeführt.

#### <a name="prerequisites-for-decrypting-a-column-in-place"></a>Voraussetzungen für die direkte Entschlüsselung einer Spalte

- Die Spalte wird mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt.
- Sie haben Zugriff auf den Spaltenhauptschlüssel.

#### <a name="steps-for-decrypting-a-column-in-place"></a>Schritte für die direkte Entschlüsselung einer Spalte

1. Bereiten Sie ein SSMS-Abfragefenster mit Always Encrypted und Enclave-Berechnungen vor, die in der Datenbankverbindung aktiviert sind. Weitere Informationen finden Sie unter [Vorbereiten eines SSMS-Abfragefensters mit aktiviertem Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2. Geben Sie im Abfragefenster die [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) mit der ALTER COLUMN-Klausel an, und geben Sie die gewünschte Spaltenkonfiguration **ohne** die ENCRYPTED WITH-Klausel an.
    
    > [!NOTE]
    > Wenn Ihr Spaltenhauptschlüssel in Azure Key Vault gespeichert ist, werden Sie ggf. dazu aufgefordert, sich bei Azure anzumelden.

3. Leeren Sie den Plancache für alle Batches und gespeicherten Prozeduren, die Zugriff auf die Tabelle haben, um die Informationen für die Parameterverschlüsselung zu aktualisieren. 

    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```

    > [!NOTE]
    > Wenn Sie den Plan für die betroffene Abfrage nicht aus dem Cache entfernen, kann bei der ersten Abfrageausführung nach der Verschlüsselung ein Fehler auftreten.

    > [!NOTE]
    > Verwenden Sie ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE oder DBCC FREEPROCCACHE, um den Plancache sorgfältig zu leeren, da dies zu einer vorübergehenden Verschlechterung der Abfrageleistung führen kann. Um die negativen Auswirkungen des Leerens des Caches zu minimieren, können Sie nur die Pläne für die betroffenen Abfragen selektiv entfernen.

4. Rufen Sie [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) auf, um die Metadaten für die Parameter jedes Moduls (Stored Procedure, Function, View, Trigger) zu aktualisieren, die in [sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) beibehalten werden und möglicherweise durch Entschlüsselung der Spalten ungültig wurden.

#### <a name="example-for-decrypting-a-column-in-place"></a>Beispiel für die direkte Entschlüsselung einer Spalte

Angenommen, die SSN-Spalte ist verschlüsselt und die aktuelle Sortierung auf Spaltenebene ist Latin1\_General\_BIN2, entschlüsselt die folgende Anweisung die Spalte (und hält die Sortierung unverändert bei – alternativ können Sie die Sortierung ändern, z.B. in eine Nicht-BIN2-Sortierung in derselben Anweisung).

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
WITH (ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

## <a name="issue-rich-queries-against-encrypted-columns-using-ssms"></a>Erstellen von umfangreichen Abfragen für verschlüsselte Spalten mit SSMS

Der schnellste Weg, um umfangreiche Abfragen für Ihre Enclave-fähigen Spalten auszuprobieren, ist ein SSMS-Abfragefenster mit aktivierter Parametrisierung für Always Encrypted. Weitere Informationen zu dieser nützliche Funktionalität in SSMS finden Sie unter:

- [Parametrisierung für Always Encrypted – Verwenden von SSMS zum Einfügen in, Aktualisieren von und Filtern von verschlüsselten Spalten](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/)
- [Abfragen von verschlüsselten Spalten](configure-always-encrypted-using-sql-server-management-studio.md#querying-encrypted-columns)

### <a name="prerequisites-for-issuing-rich-queries-against-encrypted-columns-using-ssms"></a>Voraussetzungen für das Erstellen von umfangreichen Abfragen für verschlüsselte Spalten mit SSMS

- Die abzufragenden Spalten sind Enclave-fähig.
- Sie haben Zugriff auf den/die Spaltenhauptschlüssel.

### <a name="steps-for-issuing-rich-queries-against-encrypted-columns-using-ssms"></a>Schritte für das Erstellen von umfangreichen Abfragen für verschlüsselte Spalten mit SSMS

1. Bereiten Sie ein SSMS-Abfragefenster mit Always Encrypted und Enclave-Berechnungen vor, die in der Datenbankverbindung aktiviert sind. Weitere Informationen finden Sie unter [Vorbereiten eines SSMS-Abfragefensters mit aktiviertem Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2. Aktivieren Sie die Parametrisierung für Always Encrypted.

    1. Wählen Sie im Hauptmenü von SSMS die Option **Abfrage** aus.
    2. Wählen Sie **Abfrageoptionen...** aus.
    3. Navigieren Sie zu **Ausführung** > **Erweitert**.
    4. Aktivieren oder deaktivieren Sie „Parametrisierung für Always Encrypted aktivieren“.
    5. Klicken Sie auf OK.

3. Erstellen und führen Sie Ihre Abfragen mithilfe von umfangreichen Berechnungen auf verschlüsselten Spalten aus. Sie müssen eine Transact-SQL-Variable für jeden Wert deklarieren, der auf eine verschlüsselte Spalte in Ihrer Abfrage ausgerichtet ist. Die Variablen müssen Inline-Initialisierungen verwenden (kann nicht über die SET-Anweisung festgelegt werden).

    > [!NOTE]
    > Wenn Ihr Spaltenhauptschlüssel in Azure Key Vault gespeichert ist, werden Sie ggf. dazu aufgefordert, sich bei Azure anzumelden.

### <a name="example-of-rich-queries-against-encrypted-columns"></a>Beispiel für umfangreiche Abfragen für verschlüsselte Spalten

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
) ON [PRIMARY];
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

## <a name="create-and-use-indexes-on-enclave-enabled-columns-using-randomized-encryption"></a>Erstellen und Verwenden von Indizes für Enclave-fähige Spalten mit zufälliger Verschlüsselung

Da ein Index in einer Enclave-fähigen Spalte mit zufälliger Verschlüsselung die verschlüsselten Indexschlüsselwerte speichert und die Werte nach Klartext sortiert werden, muss die SQL Server-Engine die Enclave für jeden Vorgang verwenden, bei dem ein Index erstellt oder aktualisiert wird, einschließlich:

- Erstellen oder Neuerstellen eines Index.
- Einfügen, Aktualisieren oder Löschen einer Zeile in der Tabelle (die eine indizierte/verschlüsselte Spalte enthält), wodurch das Einfügen oder/und Entfernen eines Indexschlüssels in den/aus dem Index ausgelöst wird.
- Ausführen von DBCC-Befehle, bei denen eine Integritätsprüfung der Indizes durchgeführt wird, z.B. [DBCC CHECKDB (Transact-SQL)](../../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) oder [DBCC CHECKTABLE (Transact-SQL)](../../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md).
- Datenbankwiederherstellung (z.B. nach einem Ausfall von SQL Server und Neustarts), wenn SQL Server Änderungen am Index rückgängig machen muss (siehe weitere Details unten).

Bei allen oben genannten Vorgängen benötigt die Enclave den Spaltenverschlüsselungsschlüssel für die indizierte Spalte, damit sie die Indexschlüssel entschlüsseln kann. Im Allgemeinen kann die Enclave einen Spaltenverschlüsselungsschlüssel auf zwei Arten abrufen:
- Direkt über die Clientanwendung.
- Aus dem Cache des Spaltenverschlüsselungsschlüssels.

### <a name="invoke-indexing-operations-with-column-encryption-keys-provided-directly-by-the-client"></a>Aufrufen von Indizierungsvorgänge mit direkt vom Client bereitgestellten Spaltenverschlüsselungsschlüsseln

Damit diese Methode zum Aufrufen von Indizierungsvorgängen funktioniert, muss die Anwendung, die eine Abfrage ausgibt, die einen Vorgang auf einem Index auslöst, folgende Vorgaben erfüllen:

- Sie muss eine Verbindung zur Datenbank mit Always Encrypted und Enclave-Berechnungen herstellen, die in der Datenbankverbindung aktiviert sind.
- Die Anwendung muss Zugriff auf den Spaltenhauptschlüssel haben, der den Spaltenverschlüsselungsschlüssel für die indizierte Spalte schützt.

Sobald die SQL Server-Engine die Anwendungsabfrage analysiert und feststellt, dass ein Index in einer verschlüsselten Spalte aktualisiert werden muss, um die Abfrage auszuführen, weist sie den Clienttreiber an, der Enclave den erforderlichen CEK über einen sicheren Kanal bereitzustellen. Beachten Sie, dass dies genau derselbe Mechanismus ist, der verwendet wird, um der Enclave Spaltenverschlüsselungsschlüssel für die Verarbeitung von Abfragen zur Verfügung zu stellen, die keine Indizierungsvorgänge beinhalten.

Diese Methode ist sinnvoll, um sicherzustellen, dass das Vorhandensein von Indizes auf verschlüsselten Spalten für Anwendungen, die bereits mit der Datenbank verbunden sind, transparent ist, wobei Always Encrypted- und Enclave-Berechnungen für die Verbindung aktiviert sind und die Enclave für die Anfrageverarbeitung verwendet wird. Nachdem Sie einen Index für eine Spalte erstellt haben, stellt der Treiber in Ihrer Anwendung der Enclave transparent Spaltenverschlüsselungscodes für Indizierungsvorgänge zur Verfügung. Beachten Sie, dass das Erstellen von Indizes die Anzahl der Abfragen erhöhen kann, bei denen die Anwendung die Spaltenverschlüsselungsschlüssel an die Enclave senden muss.

Schritt-für-Schritt-Anweisungen zur Verwendung dieser Methode finden Sie im [Tutorial: Erstellen und Verwenden von Indizes für Enclave-fähige Spalten mit zufälliger Verschlüsselung](../tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md).

### <a name="invoke-indexing-operations-using-cached-column-encryption-keys"></a>Aufrufen der Indizierungsvorgänge mit zwischengespeicherten Spaltenverschlüsselungsschlüsseln

Sobald eine Clientanwendung einen Spaltenverschlüsselungsschlüssel an die Enclave sendet (zur Verarbeitung jeder Abfrage, die Enclave-Berechnungen erfordert), speichert die Enclave den Spaltenverschlüsselungsschlüssel in einem internen Cache (innerhalb der Enclave und von außen nicht zugänglich).

Wenn die gleiche oder eine andere Clientanwendung (die von demselben oder einem anderen Benutzer verwendet wird) einen Vorgang auf einem Index auslöst, ohne die erforderliche Spaltenverschlüsselung direkt bereitzustellen, sucht die Enclave im Cache nach dem Spaltenverschlüsselungsschlüssel. Infolgedessen ist der Vorgang auf dem Index erfolgreich, obwohl die Clientanwendung den Schlüssel nicht bereitstellt hat.

Damit diese Methode zum Aufrufen von Indizierungsvorgängen funktioniert, muss die Anwendung eine Verbindung zur Datenbank herstellen, ohne dass für die Verbindung Always Encrypted aktiviert ist, und der erforderliche Spaltenverschlüsselungsschlüssel muss im Cache innerhalb der Enclave vorhanden sein.

Diese Methode zum Aufrufen von Vorgängen wird nur für Abfragen unterstützt, die keine Spaltenverschlüsselungsschlüssel für andere Vorgänge erfordern, die sich nicht auf Indizes beziehen. Beispielsweise muss eine Anwendung, die eine Zeile mit einer INSERT-Anweisung in eine Tabelle einfügt, die eine verschlüsselte Spalte enthält, eine Verbindung zur Datenbank herstellen, wobei Always Encrypted in der Verbindungszeichenfolge aktiviert ist und sie Zugriff auf die Schlüssel haben muss, unabhängig davon, ob die verschlüsselte Spalte einen Index hat oder nicht.

Diese Methode ist in folgenden Fällen sinnvoll:

- Sie können sicherstellen, dass das Vorhandensein von Indizes in Enclave-fähigen Spalten mit zufälliger Verschlüsselung für Anwendungen und Benutzer, die keinen Zugriff auf die Schlüssel und Daten im Klartext haben, transparent ist. Dadurch wird sichergestellt, dass die Erstellung eines Index auf einer verschlüsselten Spalte keine bestehenden Abfragen blockiert, d.h. wenn eine Anwendung eine Abfrage auf einer Tabelle mit verschlüsselten Spalten ausgibt, ohne auf die Schlüssel zugreifen zu müssen, kann die Anwendung weiterlaufen, ohne Zugriff auf die Schlüssel zu haben, nachdem ein DBA einen Index erstellt hat. Stellen Sie sich beispielsweise eine Anwendung vor, die die folgende Abfrage auf der im vorherigen Beispiel verwendeten Tabelle **Employee** ausführt, bevor ein DBA einen Index auf einer verschlüsselten Spalte erstellt. 

   ```sql
   DELETE FROM [dbo].[Employees] WHERE [EmployeeID] = 1;
   GO
   ```

   Wenn die Anwendung die Abfrage über eine Verbindung ohne aktiviertem Always Encrypted und Enclave-Berechnungen sendet, wird die Abfrage erfolgreich durchgeführt, da sie keine Berechnungen auf verschlüsselten Spalten auslöst. Nachdem ein DBA einen Index für alle verschlüsselten Spalten erstellt hat, löst die Abfrage das Entfernen von Indexschlüsseln aus Indizes aus, für die die Enclave die Spaltenverschlüsselungsschlüssel benötigt. Die Anwendung kann diese Abfrage jedoch weiterhin über dieselbe Verbindung ausführen, sofern ein Datenbesitzer die Spaltenverschlüsselungsschlüssel an die Enclave weitergegeben hat.

- Sie können damit bei der Verwaltung von Indizes eine Rollentrennung realisieren, da sie es DBAs ermöglicht, Indizes auf verschlüsselten Spalten zu erstellen und zu ändern, ohne Zugriff auf sensible Daten zu haben. 

Schritt-für-Schritt-Anweisungen zur Verwendung dieser Methode finden Sie im [Tutorial: Erstellen und Verwenden von Indizes für Enclave-fähige Spalten mit zufälliger Verschlüsselung](../tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md).

## <a name="develop-applications-issuing-rich-queries-in-visual-studio"></a>Entwickeln von Anwendungen, die umfangreiche Abfragen in Visual Studio ausgeben

### <a name="set-up-your-visual-studio-project"></a>Einrichten Ihres Visual Studio-Projekts

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
   Install-Package  Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider  --IncludePrerelease -Version 2.2.0
   Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
   ```

6. Wählen Sie Ihr Projekt aus, und klicken Sie auf „Installieren“.
7. Öffnen Sie die Konfigurationsdatei aus Ihrem Projekt (z.B. App.config oder Web.config).
8. Suchen Sie den Abschnitt \<configuration\>. Suchen Sie im Abschnitt \<configuration\> den Abschnitt \<configSections\> auf. Fügen Sie folgenden Abschnitt innerhalb von \<configSections\> hinzu:

   ```xml
   <section name="SqlColumnEncryptionEnclaveProviders"  type="System.Data.SqlClient. SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data,  Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /\>
   ```

9. Fügen Sie innerhalb des Abschnitts „configuration", unterhalb von \<configSections\>, den folgenden Abschnitt hinzu, der einen Enclave-Provider spezifiziert, der für die Bestätigung und Interaktion mit Intel SGX-Enclaves verwendet werden soll:

   ```xml
   \<SqlColumnEncryptionEnclaveProviders\>
       \<providers\>
       \<add name="VBS"  type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders. VirtualizationBasedSecurityEnclaveProvider,  Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,    Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/\>
       \</SqlColumnEncryptionEnclaveProviders\>
   ```

### <a name="develop-and-test-your-app"></a>Entwickeln und Testen Ihrer Anwendung

Um Always Encrypted und Enclave-Berechnungen verwenden zu können, muss sich Ihre Anwendung mit der Datenbank mit den folgenden beiden Schlüsselwörtern in der Verbindungszeichenfolge verbinden: `Column Encryption Setting = Enabled; Enclave Attestation Url=https://x.x.x.x/Attestation` (wobei xxxx eine IP-Adresse, eine Domäne usw. sein kann).

Darüber hinaus muss sich Ihre Anwendung an allgemeine Richtlinien halten, die für Anwendungen gelten, die Always Encrypted verwenden, z.B. muss Ihre Anwendung Zugriff auf Spaltenhauptschlüssel haben, die den Datenbankspalten zugeordnet sind, auf die in Anwendungsabfragen referenziert wird.

Einzelheiten zur Entwicklung von.NET Framework-Anwendungen mit Always Encrypted finden Sie in den folgenden Artikeln:

- [Entwickeln von Always Encrypted mit .NET Framework-Datenanbieter](develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Always Encrypted: Protect sensitive data in SQL Database and store your encryption keys in Azure Key Vault (Schützen vertraulicher Daten in SQL-Datenbank und Speichern von Verschlüsselungsschlüsseln im Azure Key Vault)](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

#### <a name="example-of-simple-application"></a>Beispiel für eine einfache Anwendung

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
) ON [PRIMARY];
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
