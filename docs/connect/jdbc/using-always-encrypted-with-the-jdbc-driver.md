---
title: Verwenden von Always Encrypted mit dem JDBC-Treiber
description: Erfahren Sie, wie Sie Always Encrypted in Ihrer Java-Anwendung mit dem JDBC-Treiber für SQL Server verwenden, um sensible Daten auf dem Server zu verschlüsseln.
ms.custom: ''
ms.date: 08/24/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 52fc716acb62ea82a6a29c1cceaa73a30cc93c44
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727505"
---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>Verwenden von Always Encrypted mit dem JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Dieser Artikel enthält Informationen zum Entwickeln von Java-Anwendungen mithilfe von [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und dem Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server.

Always Encrypted ermöglicht Clients das Verschlüsseln von vertraulichen Daten in einer Weise, dass weder die Daten noch die Verschlüsselungsschlüssel zu irgendeinem Zeitpunkt gegenüber SQL Server oder Azure SQL-Datenbank offengelegt werden. Ein Treiber, bei dem Always Encrypted aktiviert ist, z.B. der Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server, erreicht dieses Verhalten durch die transparente Ver- und Entschlüsselung von sensiblen Daten in der Clientanwendung. Der Treiber ermittelt automatisch, welche Abfrageparameter Always Encrypted-Datenbankspalten entsprechen, und verschlüsselt die Werte dieser Parameter, bevor sie an SQL Server oder Azure SQL-Datenbank gesendet werden. Auf ähnliche Weise entschlüsselt der Treiber die Daten transparent, die von verschlüsselten Datenbankspalten in Abfrageergebnissen empfangen werden. Weitere Informationen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und [Always Encrypted: API-Referenz für den JDBC-Treiber](always-encrypted-api-reference-for-the-jdbc-driver.md).

## <a name="prerequisites"></a>Voraussetzungen
- Stellen Sie sicher, dass der Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server auf dem Entwicklungscomputer installiert ist. 
- Laden Sie die Richtliniendateien Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction herunter und installieren Sie sie.  Achten Sie darauf, die in der ZIP-Datei enthaltene Infodatei zu lesen, um Installationsanweisungen und relevante Details zu möglichen Export-/Importproblemen zu erhalten.  

    - Wenn Sie die Datei „mssql-jdbc-X.X.X.jre7.jar“ oder die Datei „sqljdbc41.jar“ verwenden, können die Richtliniendateien von [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 7 Download](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html) heruntergeladen werden.

    - Wenn Sie die Datei „mssql-jdbc-X.X.X.jre8.jar“ oder die Datei „sqljdbc42.jar“ verwenden, können die Richtliniendateien von [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 8 Download](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) heruntergeladen werden.

    - Wenn Sie die Datei „mssql-jdbc-X.X.X.jre9.jar“ verwenden, muss keine Richtliniendatei heruntergeladen werden. In der Zuständigkeitsrichtlinie in Java 9 ist die Stärke der Verschlüsselung standardmäßig unbegrenzt.

## <a name="working-with-column-master-key-stores"></a>Arbeiten mit Spaltenhauptschlüsselspeichern
Zum Verschlüsseln oder Entschlüsseln von Daten für verschlüsselte Spalten verwaltet SQL Server die Spaltenverschlüsselungsschlüssel. Spaltenverschlüsselungsschlüssel werden in der verschlüsselten Form in den Datenbankmetadaten gespeichert. Jeder Spaltenverschlüsselungsschlüssel weist einen entsprechenden Spaltenhauptschlüssel auf, mit dem der Spaltenverschlüsselungsschlüssel verschlüsselt wurde. Die Datenbankmetadaten enthalten die Spaltenhauptschlüssel nicht. Diese Schlüssel werden nur vom Client gespeichert. Die Datenbankmetadaten enthalten jedoch Informationen dazu, wo die Spaltenhauptschlüssel relativ zum Client gespeichert werden. Beispielsweise können die Datenbankmetadaten die Information enthalten, dass der Keystore, der einen Spaltenhauptschlüssel enthält, der Windows-Zertifikatspeicher ist, und das zum Verschlüsseln und Entschlüsseln verwendete Zertifikat sich in einem bestimmten Pfad innerhalb des Windows-Zertifikatspeichers befindet. Wenn der Client Zugriff auf dieses Zertifikat im Windows-Zertifikatspeicher hat, kann er das Zertifikat abrufen. Das Zertifikat kann dann verwendet werden, um den Spaltenverschlüsselungsschlüssel zu entschlüsseln. Dieser Verschlüsselungsschlüssel kann dann zum Entschlüsseln oder Verschlüsseln von Daten für verschlüsselte Spalten verwendet werden, die diesen Spaltenverschlüsselungsschlüssel verwenden.

Der Microsoft JDBC-Treiber für SQL Server kommuniziert mit einem Keystore, wobei ein Spaltenhauptschlüssel-Speicheranbieter verwendet wird, der eine Instanz einer Klasse darstellt, die von der Klasse **SqlColumnEncryptionKeyStoreProvider** abgeleitet wird.

### <a name="using-built-in-column-master-key-store-providers"></a>Verwenden integrierter Spaltenhauptschlüssel-Speicheranbieter
Der Microsoft JDBC-Treiber für SQL Server verfügt über die folgenden integrierten Spaltenhauptschlüssel-Speicheranbieter. Einige dieser Anbieter sind bereits mit den spezifischen (für die Suche nach dem Anbieter verwendeten) Anbieternamen registriert, und einige erfordern entweder zusätzliche Anmeldeinformationen oder eine explizite Registrierung.

| Klasse                                                 | BESCHREIBUNG                                        | Anbietername (Suche)  | Bereits registriert? | Plattform |
| :---------------------------------------------------- | :------------------------------------------------- | :---------------------- | :----------------- | :------- |
| **SQLServerColumnEncryptionAzureKeyVaultProvider**    | Ein Anbieter für einen Keystore für die Azure Key Vault-Instanz. | AZURE_KEY_VAULT         | Vor der JDBC-Treiberversion 7.4.1 _nicht_, aber _ab_ Version 7.4.1 des JDBC-Treibers. | Windows, Linux, macOS |
| **SQLServerColumnEncryptionCertificateStoreProvider** | Ein Anbieter für den Windows-Zertifikatspeicher.      | MSSQL_CERTIFICATE_STORE | _Ja_                | Windows |
| **SQLServerColumnEncryptionJavaKeyStoreProvider**     | Ein Anbieter für den Java-Keystore.                  | MSSQL_JAVA_KEYSTORE     | _Ja_                | Windows, Linux, macOS |
|||||

Um bereits registrierte Keystore-Anbieter zu verwenden, müssen Sie keine Änderungen am Anwendungscode vornehmen, aber beachten Sie folgende Punkte:

- Sie (oder Ihr Datenbankadministrator) müssen sicherstellen, dass der in den Metadaten des Spaltenhauptschlüssels konfigurierte Anbietername richtig ist und der Pfad des Spaltenhauptschlüssels dem Schlüsselpfadformat entspricht, das für einen angegebenen Anbieter gültig ist. Es wird empfohlen, dass Sie die Schlüssel mithilfe von Tools wie SQL Server Management Studio konfigurieren, die die gültigen Anbieternamen und Schlüsselpfade automatisch generieren, wenn die Anweisung CREATE COLUMN MASTER KEY (Transact-SQL) ausgegeben wird.
- Stellen Sie sicher, dass die Anwendung auf den Schlüssel im Schlüsselspeicher zugreifen kann. Diese Task kann das Gewähren des Zugriffs auf den Schlüssel und/oder Schlüsselspeicher für die Anwendung (abhängig vom Schlüsselspeicher) oder das Ausführen anderer wichtiger speicherspezifischer Konfigurationsschritte einbeziehen. Beispielsweise müssen Sie für die Verwendung von SQLServerColumnEncryptionJavaKeyStoreProvider den Speicherort und das Kennwort des Keystores in den Verbindungseigenschaften angeben. 

Alle diese Keystore-Anbieter werden in den folgenden Abschnitten ausführlicher beschrieben. Sie müssen nur einen einzigen Keystore-Anbieter implementieren, um Always Encrypted zu verwenden.

### <a name="using-azure-key-vault-provider"></a>Verwenden des Azure Key Vault-Anbieters

Azure Key Vault ist eine praktische Möglichkeit zum Speichern von Spaltenhauptschlüsseln für Always Encrypted (insbesondere, wenn Ihre Anwendung in Azure gehostet wird). Der Microsoft JDBC-Treiber für SQL Server enthält den integrierten Anbieter SQLServerColumnEncryptionAzureKeyVaultProvider für Anwendungen, die über in Azure Key Vault gespeicherte Schlüssel verfügen. Der Name dieses Anbieters ist AZURE_KEY_VAULT. Um den Azure Key Vault-Storeanbieter zu verwenden, muss ein Anwendungsentwickler den Tresor und die Schlüssel in Azure Key Vault und eine App-Registrierung in Azure Active Directory erstellen. Der registrierten Anwendung müssen in den Zugriffsrichtlinien die Berechtigungen „Abrufen“, „Entschlüsseln“, „Verschlüsseln“, „Schlüssel entpacken“, „Schlüssel packen“ und „Überprüfen“ gewährt werden, die für den Schlüsseltresor zur Verwendung mit Always Encrypted definiert sind. Weitere Informationen zum Einrichten des Schlüsseltresors und zum Erstellen eines Spaltenhauptschlüssels finden Sie unter [Azure Key Vault – Step by Step](/archive/blogs/kv/azure-key-vault-step-by-step) (Azure Key Vault – Schritt für Schritt) und [Erstellen von Spaltenhauptschlüsseln in Azure Key Vault](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-azure-key-vault).

Bei Verwendung eines Azure Key Vault-Anbieters gleicht der JDBC-Treiber den Pfad des Spaltenhauptschlüssels mit der Liste vertrauenswürdiger Endpunkte ab. Ab der Treiberversion 8.2.2 kann diese Liste konfiguriert werden: Erstellen Sie dazu die Datei „mssql-jdbc.properties“ im Arbeitsverzeichnis der Anwendung, und legen Sie die `AKVTrustedEndpoints`-Eigenschaft auf eine durch Semikolons getrennte Liste fest. Wenn der Wert mit einem Semikolon beginnt, wird die Standardliste erweitert. Andernfalls wird die Standardliste ersetzt.

Wenn Sie in den Beispielen auf dieser Seite mit SQL Server Management Studio einen auf Azure Key Vault basierenden Spaltenhauptschlüssel und einen Spaltenverschlüsselungsschlüssel erstellt haben, könnte das T-SQL-Skript zum erneuten Erstellen in etwa wie in diesem Beispiel mit seinem eigenen spezifischen **KEY_PATH** und **ENCRYPTED_VALUE** aussehen:

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',
    KEY_PATH = N'https://<MyKeyValutName>.vault.azure.net:443/keys/Always-Encrypted-Auto1/c61f01860f37302457fa512bb7e7f4e8'
);

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x01BA000001680074507400700073003A002F002F006400610076006...
);
```

Eine Anwendung, die den JDBC-Treiber verwendet, kann die Azure Key Vault-Instanz verwenden. Die Syntax oder Anweisungen für diese Verwendung von Azure Key Vault wurden ab der JDBC-Treiberversion 7.4.1 geändert.

#### <a name="jdbc-driver-741-or-later"></a>JDBC-Treiber 7.4.1 oder höher

Dieser Abschnitt umfasst die JDBC-Treiberversion 7.4.1 oder höher.

Um eine Clientanwendung, die den JDBC-Treiber verwendet, für die Verwendung von Azure Key Vault zu konfigurieren, muss `keyVaultProviderClientId=<ClientId>;keyVaultProviderClientKey=<ClientKey>` in der JDBC-Verbindungszeichenfolge enthalten sein.

Im Folgenden finden Sie ein Beispiel für die Aufnahme dieser Konfigurationsinformationen in eine JDBC-Verbindungszeichenfolge.

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyVaultProviderClientId=<ClientId>;keyVaultProviderClientKey=<ClientKey>";
```
Der JDBC-Treiber instanziiert automatisch ein **SQLServerColumnEncryptionAzureKeyVaultProvider**-Objekt, wenn diese Anmeldeinformationen in den Verbindungseigenschaften vorhanden sind.

> [!IMPORTANT]
> Die Verbindungseigenschaften **keyVaultProviderClientId** und **keyVaultProviderClientKey** sind ab v8.4.1 veraltet. Benutzern wird empfohlen, stattdessen **keyStoreAuthentication**, **KeyStorePrincipalId** und **KeyStoreSecret** zu verwenden.

#### <a name="jdbc-driver-version-prior-to-741"></a>JDBC-Treiberversion vor 7.4.1

Dieser Abschnitt umfasst die JDBC-Treiberversionen vor 7.4.1.

Eine Clientanwendung, die den JDBC-Treiber verwendet, muss ein **SQLServerColumnEncryptionAzureKeyVaultProvider**-Objekt instanziieren und das Objekt dann beim Treiber registrieren.

```java
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
```

**clientID** ist die Anwendungs-ID einer App-Registrierung in einer Azure Active Directory-Instanz. **clientKey** ist ein Schlüsselkennwort, das unter dieser Anwendung registriert ist und API-Zugriff auf die Azure Key Vault-Instanz ermöglicht.

Nachdem die Anwendung eine Instanz von SQLServerColumnEncryptionAzureKeyVaultProvider erstellt hat, muss sie die Instanz mit der SQLServerConnection.registerColumnEncryptionKeyStoreProviders()-Methode bei dem Treiber registrieren. Sie sollten die Instanz unbedingt mit dem Standardnamen AZURE_KEY_VAULT für die Suche registrieren, der durch Aufrufen der SQLServerColumnEncryptionAzureKeyVaultProvider.getName()-API abgerufen werden kann. Wenn Sie den Standardnamen verwenden, können Sie Tools wie SQL Server Management Studio oder PowerShell verwenden, um Always Encrypted-Schlüssel bereitzustellen und zu verwalten (die Tools verwenden den Standardnamen, um das Metadatenobjekt für den Spaltenhauptschlüssel zu generieren). Im folgenden Beispiel wird die Registrierung des Azure Key Vault-Anbieters veranschaulicht. Weitere Informationen zur SQLServerConnection.registerColumnEncryptionKeyStoreProviders()-Methode finden Sie unter [Always Encrypted: API-Referenz für den JDBC-Treiber](always-encrypted-api-reference-for-the-jdbc-driver.md).

```java
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(akvProvider.getName(), akvProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

> [!IMPORTANT]
>  Wenn Sie den Azure Key Vault-Keystore-Anbieter verwenden, müssen Sie die Abhängigkeiten der Azure Key Vault-Implementierung des JDBC-Treibers von diesen Bibliotheken (von GitHub) in die Anwendung einbeziehen:
>
>  [azure-sdk-for-java](https://github.com/Azure/azure-sdk-for-java)
>
>  [azure-activedirectory-library-for-java libraries](https://github.com/AzureAD/azure-activedirectory-library-for-java)
>
> Ein Beispiel für das Einbeziehen dieser Abhängigkeiten in ein Maven-Projekt finden Sie unter [Download ADAL4J And AKV Dependencies with Apache Maven](https://github.com/Microsoft/mssql-jdbc/wiki/Download-ADAL4J-And-AKV-Dependencies-with-Apache-Maven) (Herunterladen von ADAL4J- und AKV-Abhängigkeiten mit Apache Maven).

### <a name="using-azure-key-vault-authentication-with-managed-identities"></a>Verwenden der Azure Key Vault-Authentifizierung mit verwalteten Identitäten

Ab Version **8.4.1** bietet der JDBC-Treiber Unterstützung für die Azure Key Vault-Authentifizierung mithilfe von verwalteten Identitäten.

Wenn die Anwendung in Azure gehostet wird, kann der Benutzer [verwaltete Identitäten](/azure/active-directory/managed-identities-azure-resources/overview) verwenden, um sich bei Azure Key Vault zu authentifizieren, sodass es nicht mehr erforderlich ist, Anmeldeinformationen im Code bereitzustellen und verfügbar zu machen. 

#### <a name="connection-properties-for-key-vault-authentication-with-managed-identities"></a>Verbindungseigenschaften für die Key Vault-Authentifizierung mit verwalteten Identitäten

Ab Version 8.4.1 des JDBC-Treibers wurden die folgenden Verbindungseigenschaften eingeführt:

| ConnectionProperty    | Mögliche Wertpaare 1 | Mögliche Wertpaare 2 | Mögliche Wertpaare 3 |
| ---|---|---|----|
| keyStoreAuthentication| KeyVaultClientSecret   |KeyVaultManagedIdentity |JavaKeyStorePassword |  
| keyStorePrincipalId   | \<Azure AD Application Client ID\>    | \<Azure AD Application object ID\> (optional)| – |
| keyStoreSecret        | \<Azure AD Application Client Secret\>|–|\<secret/password for the Java Key Store\> |

In den folgenden Beispielen wird veranschaulicht, wie die Verbindungseigenschaften in einer Verbindungszeichenfolge verwendet werden.

#### <a name="use-managed-identity-to-authenticate-to-akv"></a>Verwenden einer verwalteten Identität zur Authentifizierung bei AKV
```
"jdbc:sqlserver://<server>:<port>;columnEncryptionSetting=Enabled;keyStoreAuthentication=KeyVaultManagedIdentity;"
```
#### <a name="use-managed-identity-and-the-principal-id-to-authenticate-to-akv"></a>Verwenden einer verwalteten Identität und der Prinzipal-ID zur Authentifizierung bei AKV
```
"jdbc:sqlserver://<server>:<port>;columnEncryptionSetting=Enabled;keyStoreAuthentication=KeyVaultManagedIdentity;keyStorePrincipal=<principalId>"
```
#### <a name="use-clientid-and-clientsecret-to-authentication-to-akv"></a>Verwenden von clientID und clientSecret zur Authentifizierung bei AKV
```
"jdbc:sqlserver://<server>:<port>;columnEncryptionSetting=Enabled;keyStoreAuthentication=KeyVaultClientSecret;keyStorePrincipalId=<clientId>;keyStoreSecret=<clientSecret>"
```
Benutzern wird empfohlen, diese Verbindungseigenschaften zu verwenden, um den für die Schlüsselspeicher verwendeten Authentifizierungstyp anzugeben, anstatt `SQLServerColumnEncryptionAzureKeyVaultProvider` zu nutzen.

Beachten Sie, dass die zuvor hinzugefügten Verbindungseigenschaften `keyVaultProviderClientId` und `keyVaultProviderClientKey` veraltet sind und durch die oben beschriebenen Verbindungseigenschaften ersetzt wurden.

Informationen zum Konfigurieren verwalteter Identitäten finden Sie unter [Konfigurieren von verwalteten Identitäten für Azure-Ressourcen auf einem virtuellen Computer über das Azure-Portal](/azure/active-directory/managed-identities-azure-resources/qs-configure-portal-windows-vm).

### <a name="using-windows-certificate-store-provider"></a>Verwenden des Windows-Zertifikatspeicheranbieters
Mit „SqlColumnEncryptionCertificateStoreProvider“ können Spaltenhauptschlüssel im Windows-Zertifikatspeicher gespeichert werden. Verwenden Sie den SQL Server Management Studio Always Encrypted-Assistenten (SSMS) oder andere unterstützte Tools, um die Spaltenhauptschlüssel- und Spaltenverschlüsselungsschlüssel-Definitionen in der Datenbank zu erstellen. Der gleiche Assistent kann verwendet werden, um ein selbstsigniertes Zertifikat im Windows-Zertifikatspeicher zu generieren, das als Spaltenhauptschlüssel für die Always Encrypted-Daten verwendet werden kann. Weitere Informationen zum Spaltenhauptschlüssel und der T-SQL-Syntax für den Spaltenverschlüsselungsschlüssel finden Sie unter [ERSTELLEN DES SPALTENHAUPTSCHLÜSSELS](../../t-sql/statements/create-column-master-key-transact-sql.md) bzw. [ERSTELLEN DES SPALTENVERSCHLÜSSELUNGSSCHLÜSSELS](../../t-sql/statements/create-column-encryption-key-transact-sql.md).

Der Name des SQLServerColumnEncryptionCertificateStoreProvider ist MSSQL_CERTIFICATE_STORE und kann von der getName()-API des Anbieterobjekts abgefragt werden. Er wird automatisch vom Treiber registriert und kann nahtlos ohne Änderung der Anwendung verwendet werden.

Wenn Sie in den Beispielen auf dieser Seite mit SQL Server Management Studio einen auf dem Windows-Zertifikatspeicher basierenden Spaltenhauptschlüssel und einen Spaltenverschlüsselungsschlüssel erstellt haben, könnte das T-SQL-Skript zum erneuten Erstellen in etwa wie in diesem Beispiel mit seinem eigenen spezifischen **KEY_PATH** und **ENCRYPTED_VALUE** aussehen:

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/My/A2A91F59C461B559E4D962DA9D2BC6131B32CB91'
);

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E0074007500730065007200...
);
```

> [!IMPORTANT]
> Während die anderen Keystore-Anbieter in diesem Artikel auf allen Plattformen verfügbar sind, die vom Treiber unterstützt werden, ist die SQLServerColumnEncryptionCertificateStoreProvider-Implementierung des JDBC-Treibers nur auf Windows-Betriebssystemen verfügbar. Es besteht eine Abhängigkeit von der „mssql-jdbc_auth-\<version>-\<arch>.dll“, die im Treiberpaket verfügbar ist. Wenn Sie diesen Anbieter verwenden möchten, müssen Sie die Datei „mssql-jdbc_auth-\<version>-\<arch>.dll“ in ein Verzeichnis im Windows-Systempfad des Computers kopieren, auf dem der JDBC-Treiber installiert ist. Alternativ können Sie mit der java.libary.path-Systemeigenschaft das Verzeichnis von „mssql-jdbc_auth-\<version>-\<arch>.dll“ angeben. Wenn Sie eine 32-Bit-JVM (Java Virtual Machine) ausführen, verwenden Sie die Datei „mssql-jdbc_auth-\<version>-x86.dll“ im Ordner x86, auch wenn es sich bei dem Betriebssystem um die x64-Version handelt. Wenn Sie eine 64-Bit-JVM mit einem x64-Prozessor ausführen, verwenden Sie die Datei „mssql-jdbc_auth-\<version>-x64.dll“ im Ordner x64. Wenn Sie beispielsweise die 32-Bit-JVM verwenden und der JDBC-Treiber im Standardverzeichnis installiert ist, können Sie den Speicherort der DLL beim Start der Java-Anwendung mit dem folgenden VM-Argument (Virtual Machine) angeben: `-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`

### <a name="using-java-key-store-provider"></a>Verwenden des Java Key Store-Anbieters
Der JDBC-Treiber ist mit einer integrierten Schlüsselspeicheranbieter-Implementierung für den Java Key Store ausgestattet. Wenn die Eigenschaft **keyStoreAuthentication** der Verbindungszeichenfolge vorhanden und auf „JavaKeyStorePassword“ festgelegt ist, instanziiert und registriert der Treiber automatisch den Anbieter für Java Key Store. Der Name des Java Key Store-Anbieters ist MSSQL_JAVA_KEYSTORE. Dieser Name kann auch mit der SQLServerColumnEncryptionJavaKeyStoreProvider.getName()-API abgefragt werden. 

Es gibt drei Eigenschaften der Verbindungszeichenfolge, die einer Clientanwendung ermöglichen, die Anmeldeinformationen anzugeben, die der Treiber für die Authentifizierung beim Java Key Store benötigt. Der Treiber initialisiert den Anbieter auf der Grundlage der Werte dieser drei Eigenschaften in der Verbindungszeichenfolge.

**keyStoreAuthentication:** Identifiziert den zu verwendenden Java Key Store. Mit dem Microsoft JDBC-Treiber 6.0 und höher für SQL Server können Sie sich nur über diese Eigenschaft beim Java Key Store authentifizieren. Für den Java Key Store muss der Wert für diese Eigenschaft `JavaKeyStorePassword` sein.

**keyStoreLocation:** Der Pfad zur Java Key Store-Datei, in der der Spaltenhauptschlüssel gespeichert wird. Der Pfad enthält den Keystoredateinamen.

**keyStoreSecret:** Das Geheimnis/Kennwort, das sowohl für den Keystore als auch für den Schlüssel verwendet werden soll. Beachten Sie, dass zur Verwendung des Java Key Store der Keystore und das Schlüsselkennwort übereinstimmen müssen.

Im Folgenden finden Sie ein Beispiel für die Angabe dieser Anmeldeinformationen in der Verbindungszeichenfolge:

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
```

Sie können diese Einstellungen auch mit dem SQLServerDataSource-Objekt abrufen oder festlegen. Weitere Informationen finden Sie unter [Always Encrypted – API-Referenz für den JDBC-Treiber](always-encrypted-api-reference-for-the-jdbc-driver.md).

Der JDBC-Treiber instanziiert automatisch den SQLServerColumnEncryptionJavaKeyStoreProvider, wenn diese Anmeldeinformationen in den Verbindungseigenschaften vorhanden sind.

### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Erstellen eines Spaltenhauptschlüssels für den Java Key Store
Der SQLServerColumnEncryptionJavaKeyStoreProvider kann mit dem Keystoretyp JKS oder PKCS12 verwendet werden. Um einen Schlüssel zu erstellen oder zu importieren, der mit diesem Anbieter verwendet werden soll, verwenden Sie das Java-Hilfsprogramm [keytool](https://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html). Der Schlüssel muss das gleiche Kennwort wie der Keystore selbst aufweisen. Im Folgenden finden Sie ein Beispiel für das Erstellen eines öffentlichen Schlüssels und des zugehörigen privaten Schlüssels mit dem Hilfsprogramm „keytool“:

```console
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks
```

Mit diesem Befehl wird ein öffentlicher Schlüssel erstellt und von einem selbstsignierten X.509-Zertifikat umschlossen, das im Keystore `keystore.jks` zusammen mit dem zugehörigen privaten Schlüssel gespeichert wird. Dieser Eintrag im Keystore wird durch den Alias `AlwaysEncryptedKey` identifiziert.

Im Folgenden finden Sie ein Beispiel für das Gleiche mit einem PKCS12-Speichertyp:

```console
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword
```

Bei einem Keystore des Typs PKCS12 fordert das keytool-Hilfsprogramm nicht zur Eingabe eines Schlüsselkennworts auf, und das Schlüsselkennwort muss mit der `-keypass`-Option angegeben werden, weil der **SQLServerColumnEncryptionJavaKeyStoreProvider** erfordert, dass Keystore und Schlüssel das gleiche Kennwort aufweisen.

Sie können auch ein Zertifikat aus dem Windows-Zertifikatspeicher im PFX-Format exportieren und mit dem **SQLServerColumnEncryptionJavaKeyStoreProvider** verwenden. Das exportierte Zertifikat kann auch als JKS-Keystoretyp in den Java Key Store importiert werden.

Nachdem Sie den keytool-Eintrag erstellt haben, erstellen Sie die Metadaten des Spaltenhauptschlüssels in der Datenbank, die den Namen des Keystore-Anbieters und den Schlüsselpfad benötigt. Weitere Informationen zum Erstellen von Spaltenhauptschlüssel-Metadaten finden Sie unter [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md). Für SQLServerColumnEncryptionJavaKeyStoreProvider ist der Schlüsselpfad nur der Alias des Schlüssels, und der Name des SQLServerColumnEncryptionJavaKeyStoreProvider ist `MSSQL_JAVA_KEYSTORE`. Sie können diesen Namen auch mit der öffentlichen getName()-API der SQLServerColumnEncryptionJavaKeyStoreProvider-Klasse abfragen. 

Die T-SQL-Syntax zum Erstellen des Spaltenhauptschlüssels lautet:

```sql
CREATE COLUMN MASTER KEY [<CMK_name>]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'<key_alias>'
);
```

Für den oben erstellten „AlwaysEncryptedKey“ lautet die Definition des Spaltenhauptschlüssels wie folgt:

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
);
```

> [!NOTE]
> Mit der integrierten SQL Server Management Studio-Funktionalität können keine Spaltenhauptschlüssel-Definitionen für den Java Key Store erstellt werden. T-SQL-Befehle müssen programmgesteuert verwendet werden.

### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Erstellen eines Spaltenverschlüsselungsschlüssels für den Java Key Store
SQL Server Management Studio oder andere Tools können nicht zum Erstellen von Spaltenverschlüsselungsschlüsseln verwendet werden, die Spaltenhauptschlüssel im Java Key Store verwenden. Die Clientanwendung muss den Spaltenverschlüsselungsschlüssel programmgesteuert mithilfe der SQLServerColumnEncryptionJavaKeyStoreProvider-Klasse erstellen. Weitere Informationen finden Sie unter [mithilfe von Hauptschlüssel-Speicheranbieter für die programmgesteuerte schlüsselbereitstellung](#using-column-master-key-store-providers-for-programmatic-key-provisioning).

### <a name="implementing-a-custom-column-master-key-store-provider"></a>Implementieren eines benutzerdefinierten Speicheranbieters für den Spaltenhauptschlüssel
Wenn Sie Spaltenhauptschlüssel in einem Schlüsselspeicher speichern möchten, der nicht von einem vorhandenen Anbieter unterstützt wird, können Sie einen benutzerdefinierten Anbieter implementieren, indem Sie die SQLServerColumnEncryptionKeyStoreProvider-Klasse erweitern und den Anbieter mithilfe der SQLServerConnection.registerColumnEncryptionKeyStoreProviders()-Methode registrieren.

```java
public class MyCustomKeyStore extends SQLServerColumnEncryptionKeyStoreProvider{  
    private String name = "MY_CUSTOM_KEYSTORE";

    public void setName(String name)
    {
        this.name = name;
    }

    public String getName()
    {
        return name;
    }

    public byte[] encryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)
    {
        // Logic for encrypting the column encryption key
    }

    public byte[] decryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)
    {
        // Logic for decrypting the column encryption key
    }
}
```

Registrieren Sie den Anbieter:

```java
SQLServerColumnEncryptionKeyStoreProvider storeProvider = new MyCustomKeyStore();
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(storeProvider.getName(), storeProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

## <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>Verwenden von Spaltenhauptschlüssel-Speicheranbietern für die programmgesteuerte Schlüsselbereitstellung
Beim Zugriff auf verschlüsselte Spalten sucht der Microsoft JDBC-Treiber für SQL Server den richtigen Speicheranbieter für Spaltenhauptschlüssel transparent und ruft ihn anschließend auf, um die Spaltenverschlüsselungsschlüssel zu entschlüsseln. In der Regel ruft der normale Anwendungscode die Speicheranbieter für Spaltenhauptschlüssel nicht direkt auf. Sie können einen Anbieter jedoch programmgesteuert instanziieren und abrufen, um Always Encrypted-Schlüssel bereitzustellen und zu verwalten. Dieser Schritt kann z. B. ausgeführt werden, um einen verschlüsselten Spaltenverschlüsselungsschlüssel zu generieren und einen Spaltenverschlüsselungsschlüssel als Teil der Spaltenhauptschlüssel-Rotation zu entschlüsseln. Weitere Informationen finden Sie unter [Overview of Key Management for Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)(Übersicht über die Schlüsselverwaltung für Always Encrypted).

Die Implementierung Ihrer eigenen Schlüsselverwaltungstools ist möglicherweise erforderlich, wenn Sie einen benutzerdefinierten Schlüsselspeicheranbieter verwenden. Bei der Verwendung von Schlüsseln, die im Windows-Zertifikatspeicher oder in Azure Key Vault gespeichert werden, können Sie vorhandene Tools wie SQL Server Management Studio oder PowerShell verwenden, um Schlüssel zu verwalten und bereitzustellen. Wenn Sie Schlüssel verwenden, die im Java Key Store gespeichert sind, müssen Sie Schlüssel programmgesteuert bereitstellen. Das folgende Beispiel veranschaulicht die Verwendung der SQLServerColumnEncryptionJavaKeyStoreProvider-Klasse, um den Schlüssel mit einem Schlüssel zu verschlüsseln, der im Java Key Store gespeichert ist.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programmatically for the Java Key Store.
 */
public class AlwaysEncrypted {
    // Alias of the key stored in the keystore.
    private static String keyAlias = "<provide key alias>";

    // Name by which the column master key will be known in the database.
    private static String columnMasterKeyName = "MyCMK";

    // Name by which the column encryption key will be known in the database.
    private static String columnEncryptionKey = "MyCEK";

    // The location of the keystore.
    private static String keyStoreLocation = "C:\\Dev\\Always Encrypted\\keystore.jks";

    // The password of the keystore and the key.
    private static char[] keyStoreSecret = "********".toCharArray();

    /**
     * Name of the encryption algorithm used to encrypt the value of the column encryption key. The algorithm for the system providers must be
     * RSA_OAEP.
     */
    private static String algorithm = "RSA_OAEP";

    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";

        try (Connection connection = DriverManager.getConnection(connectionUrl);
                Statement statement = connection.createStatement();) {

            // Instantiate the Java Key Store provider.
            SQLServerColumnEncryptionKeyStoreProvider storeProvider = new SQLServerColumnEncryptionJavaKeyStoreProvider(keyStoreLocation,
                    keyStoreSecret);

            byte[] encryptedCEK = getEncryptedCEK(storeProvider);

            /**
             * Create column encryption key For more details on the syntax, see:
             * https://docs.microsoft.com/sql/t-sql/statements/create-column-encryption-key-transact-sql Encrypted column encryption key first needs
             * to be converted into varbinary_literal from bytes, for which byteArrayToHex() is used.
             */
            String createCEKSQL = "CREATE COLUMN ENCRYPTION KEY "
                    + columnEncryptionKey
                    + " WITH VALUES ( "
                    + " COLUMN_MASTER_KEY = "
                    + columnMasterKeyName
                    + " , ALGORITHM =  '"
                    + algorithm
                    + "' , ENCRYPTED_VALUE =  0x"
                    + byteArrayToHex(encryptedCEK)
                    + " ) ";
            statement.executeUpdate(createCEKSQL);
            System.out.println("Column encryption key created with name : " + columnEncryptionKey);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static byte[] getEncryptedCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider) throws SQLServerException {
        String plainTextKey = "You need to give your plain text";

        // plainTextKey has to be 32 bytes with current algorithm supported
        byte[] plainCEK = plainTextKey.getBytes();

        // This will give us encrypted column encryption key in bytes
        byte[] encryptedCEK = storeProvider.encryptColumnEncryptionKey(keyAlias, algorithm, plainCEK);

        return encryptedCEK;
    }

    public static String byteArrayToHex(byte[] a) {
        StringBuilder sb = new StringBuilder(a.length * 2);
        for (byte b : a)
            sb.append(String.format("%02x", b).toUpperCase());
        return sb.toString();
    }
}
```

## <a name="enabling-always-encrypted-for-application-queries"></a>Aktivieren von Always Encrypted für Anwendungsabfragen
Die einfachste Möglichkeit zum Aktivieren der Verschlüsselung von Parametern und der Entschlüsselung von Abfrageergebnissen, die auf verschlüsselte Spalten ausgerichtet sind, besteht im Festlegen des Werts für das Kennwort der **columnEncryptionSetting**-Verbindungszeichenfolge auf **Enabled**.

Die folgende Verbindungszeichenfolge ist ein Beispiel für das Aktivieren von Always Encrypted im JDBC-Speicher:

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionUrl);
```

Der folgende Code ist ein entsprechendes Beispiel bei Verwendung des SQLServerDataSource-Objekts:

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(<port>);
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");
SQLServerConnection con = (SQLServerConnection) ds.getConnection();
```

Always Encrypted kann auch für einzelne Abfragen aktiviert werden. Weitere Informationen finden Sie weiter unten im Abschnitt [Kontrollieren der Auswirkungen von Always Encrypted auf die Leistung](#controlling-the-performance-impact-of-always-encrypted). Die Aktivierung von Always Encrypted ist für eine erfolgreiche Verschlüsselung und Entschlüsselung nicht ausreichend. Sie müssen auch Folgendes sicherstellen:
- Die Anwendung verfügt über die Datenbankberechtigungen *VIEW ANY COLUMN MASTER KEY DEFINITION* und *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* , die für den Zugriff auf die Metadaten in der Datenbank über Always Encrypted-Schlüssel erforderlich sind. Weitere Informationen finden Sie unter [Berechtigungen in Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
- Die Anwendung kann auf den Hauptschlüssel der Spalte zugreifen, der die Spaltenverschlüsselungsschlüssel schützt, mit denen die abgefragten Datenbankspalten verschlüsselt werden. Wenn Sie den Java Key Store-Anbieter verwenden möchten, müssen Sie zusätzliche Anmeldeinformationen in der Verbindungszeichenfolge angeben. Weitere Informationen finden Sie unter [Verwenden des Java Key Store-Anbieters](#using-java-key-store-provider).

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden
Die **sendTimeAsDatetime**-Verbindungseigenschaft wird dazu verwendet, die Art und Weise zu konfigurieren, auf die der java.sql.Time-Wert an den Server gesendet wird. Wenn der Wert auf „false“ festgelegt ist, wird der Zeitwert als SQL Server-Zeittyp gesendet. Wenn der Wert auf „true“ festgelegt ist, wird der Zeitwert als datetime-Typ gesendet. Wenn eine Zeitspalte verschlüsselt wird, muss die **sendTimeAsDatetime**-Eigenschaft „false“ sein, da verschlüsselte Spalten die Konvertierung von „time“ in „datetime“ nicht unterstützen. Beachten Sie auch, dass diese Eigenschaft standardmäßig „true“ ist. Wenn Sie also verschlüsselte Zeitspalten verwenden, müssen Sie für diese Eigenschaft „false“ festlegen. Andernfalls löst der Treiber eine Ausnahme aus. Ab Version 6.0 des Treibers verfügt die SQLServerConnection-Klasse über zwei Methoden, um den Wert dieser Eigenschaft programmgesteuert zu konfigurieren:
 
* public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
* öffentlicher boolescher Wert getSendTimeAsDatetime()

Weitere Informationen zu dieser Eigenschaft finden Sie unter [Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden](configuring-how-java-sql-time-values-are-sent-to-the-server.md).

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>Konfigurieren der Art und Weise, wie Zeichenfolgenwerte an den Server gesendet werden
Mit der **sendStringParametersAsUnicode**-Verbindungseigenschaft wird konfiguriert, wie Zeichenfolgenwerte an SQL Server gesendet werden. Wenn die Eigenschaft auf „TRUE“ festgelegt ist, werden String-Parameter im Unicode-Format an den Server gesendet. Wenn die Eigenschaft auf „false“ festgelegt ist, werden Zeichenfolgenparameter nicht im Unicode-Format, sondern in einem anderen Format wie z. B. ASCII oder MBCS an den Server gesendet. Der Standardwert dieser Eigenschaft ist „TRUE“. Wenn Always Encrypted aktiviert ist und eine char-/varchar-/varchar(max)-Spalte verschlüsselt wird, muss **sendStringParametersAsUnicode-** auf „false“ festgelegt werden. Wenn diese Eigenschaft auf „true“ festgelegt ist, löst der Treiber eine Ausnahme aus, wenn Daten aus einer verschlüsselten char-/varchar-/varchar(max)-Spalte mit Unicode-Zeichen entschlüsselt werden. Weitere Informationen zu dieser Eigenschaft finden Sie unter [Festlegen von Verbindungseigenschaften](setting-the-connection-properties.md).
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Abrufen und Ändern von Daten in verschlüsselten Spalten
Nachdem Sie Always Encrypted für Anwendungsabfragen aktiviert haben, können Sie JDBC-Standard-APIs verwenden, um Daten in verschlüsselten Datenbankspalten abzurufen oder zu ändern. Wenn Ihre Anwendung über die erforderlichen Datenbankberechtigungen verfügt und auf den Spaltenhauptschlüssel zugreifen kann, verschlüsselt der Treiber alle Abfrageparameter für verschlüsselte Spalten und entschlüsselt Daten, die aus verschlüsselten Spalten abgerufen werden.

Wenn Always Encrypted nicht aktiviert ist, tritt bei Abfragen mit Parametern, die verschlüsselte Spalten anzielen, ein Fehler auf. Abfragen können weiterhin Daten aus verschlüsselten Spalten abrufen, solange die Abfrage keine Parameter für verschlüsselte Spalten enthält. Der Treiber versucht jedoch nicht, die aus verschlüsselten Spalten abgerufenen Werte zu entschlüsseln, deshalb erhält die Anwendung binär verschlüsselte Daten (als Bytearrays).

In der folgenden Tabelle wird das Verhalten von Abfragen in Abhängigkeit davon zusammengefasst, ob Always Encrypted aktiviert ist:

| Abfragemerkmal                                                                           | Always Encrypted ist aktiviert und die Anwendung kann auf die Schlüssel und Schlüsselmetadaten zugreifen.                                                                                                                        | Always Encrypted ist aktiviert, und die Anwendung kann nicht auf die Schlüssel oder Schlüsselmetadaten zugreifen. | Always Encrypted ist deaktiviert                                                                                        |
| :--------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------ |
| Abfragen mit Parametern, die auf verschlüsselte Spalten ausgerichtet sind.                                           | Parameterwerte werden transparent verschlüsselt.                                                                                                                                                           | Fehler                                                                             | Fehler                                                                                                               |
| Abfragen, bei denen Daten von verschlüsselten Spalten ohne Parameter abgerufen werden, die auf verschlüsselte Spalten ausgerichtet sind. | Ergebnisse von verschlüsselten Spalten werden transparent entschlüsselt. Die Anwendung erhält Klartextwerte der JDBC-Datentypen, die den SQL Server-Datentypen entsprechen, die für die verschlüsselten Spalten konfiguriert wurden. | Fehler                                                                             | Ergebnisse von verschlüsselten Spalten werden nicht entschlüsselt. Die Anwendung erhält verschlüsselte Werte als Bytearrays (byte[]). |

### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Beispiel zum Einfügen und Abrufen von verschlüsselten Daten

Die folgenden Beispiele veranschaulichen das Abrufen und Ändern von Daten in verschlüsselten Spalten. In den Beispielen wird davon ausgegangen, dass die Zieltabelle das folgende Schema und die verschlüsselten Spalten „SSN“ und BirthDate aufweist. Wenn Sie einen Spaltenhauptschlüssel mit dem Namen „MyCMK“ und einen Spaltenverschlüsselungsschlüssel mit dem Namen „MyCEK“ konfiguriert haben (wie in den vorherigen Abschnitten zu Keystore-Anbietern beschrieben), können Sie die Tabelle mit diesem Skript erstellen:

```sql
CREATE TABLE [dbo].[Patients]([PatientId] [int] IDENTITY(1,1),
 [SSN] [char](11) COLLATE Latin1_General_BIN2
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL,
 [BirthDate] [date]
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY]);
 GO
```

Für jedes Java-Codebeispiel müssen Sie für den Keystore spezifischen Code an der angegebenen Position einfügen.

Wenn Sie einen Azure Key Vault-Keystore-Anbieter verwenden:

```java
    String clientID = "<Azure Application ID>";
    String clientKey = "<Azure Application API Key Password>";
    SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
    Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
    keyStoreMap.put(akvProvider.getName(), akvProvider);
    SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";
```

Wenn Sie einen Windows-Zertifikatspeicher-Keystore-Anbieter verwenden:

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";
```

Wenn Sie einen Java Key Store-Keystore-Anbieter verwenden:

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path to jks or pfx file>;keyStoreSecret=<keystore secret/password>";
```

### <a name="inserting-data-example"></a>Beispiel zum Einfügen von Daten

In diesem Beispiel wird eine Zeile in die Tabelle „Patients“ eingefügt. Beachten Sie Folgendes:

- Es erfolgt keine spezielle Verschlüsselung im Beispielcode. Der Microsoft JDBC-Treiber für SQL Server erkennt und verschlüsselt automatisch die Parameter, die auf verschlüsselte Spalten ausgerichtet sind. Durch dieses Verhalten wird die Verschlüsselung für die Anwendung transparent.
- Die in die Datenbankspalten eingefügten Werte, einschließlich der verschlüsselten Spalten, werden mit SQLServerPreparedStatement als Parameter übergeben. Während die Verwendung von Parametern optional ist, wenn Werte an nicht verschlüsselte Spalten gesendet werden (obwohl es dringend empfohlen wird, da es dabei hilft, eine Einschleusung von SQL-Befehlen zu verhindern), ist sie für Werte erforderlich, die verschlüsselte Spalten anzielen. Wenn die in die verschlüsselten Spalten eingefügten Werte als Literale übergeben würden, die in die Abfrageanweisung eingebettet sind, würde bei der Abfrage ein Fehler auftreten, da der Treiber die Werte in den verschlüsselten Zielspalten nicht ermitteln könnte und nicht verschlüsseln würde. Daher würde der Server sie zurückweisen, da sie mit den verschlüsselten Spalten inkompatibel sind.
- Alle Werte werden vom Programm als Klartext ausgegeben, da der JDBC-Treiber für SQL Server die aus den verschlüsselten Spalten abgerufenen Daten transparent entschlüsselt.
- Wenn Sie eine Suche mit einer WHERE-Klausel durchführen, muss der in der WHERE-Klausel verwendete Wert als Parameter übergeben werden, damit ihn der Treiber vor dem Senden an die Datenbank transparent verschlüsseln kann. Im folgenden Beispiel wird die SSN als Parameter übergeben, aber LastName als Literalwert, da LastName nicht verschlüsselt ist.
- Für den auf die Spalte „SSN“ ausgerichteten Parameter wird die Settermethode setString() verwendet, die dem SQL Server-Datentyp „char/varchar“ zugeordnet wird. Wenn für diesen Parameter die Settermethode setNString() verwendet wurde, die nchar bzw. nvarchar zugeordnet wird, würde bei der Abfrage ein Fehler auftreten, da Always Encrypted keine Konvertierungen von verschlüsselten nchar- und nvarchar-Werten in verschlüsselte char- und varchar-Werte unterstützt.

```java
// <Insert keystore-specific code here>
try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
        PreparedStatement insertStatement = sourceConnection.prepareStatement("INSERT INTO [dbo].[Patients] VALUES (?, ?, ?, ?)")) {
    insertStatement.setString(1, "795-73-9838");
    insertStatement.setString(2, "Catherine");
    insertStatement.setString(3, "Abel");
    insertStatement.setDate(4, Date.valueOf("1996-09-10"));
    insertStatement.executeUpdate();
    System.out.println("1 record inserted.\n");
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="retrieving-plaintext-data-example"></a>Beispiel zum Abrufen von Klartextdaten

Im folgenden Beispiel wird das Filtern von Daten auf Basis verschlüsselter Werte und das Abrufen von Klartextdaten aus verschlüsselten Spalten veranschaulicht. Beachten Sie Folgendes:

- Der in der WHERE-Klausel zum Filtern der Spalte „SSN“ verwendete Wert muss als Parameter übergeben werden, damit ihn der Microsoft JDBC-Treiber für SQL Server vor dem Senden an die Datenbank transparent verschlüsseln kann.
- Alle Werte werden vom Programm als Klartext ausgegeben, da der JDBC-Treiber für SQL Server die aus den Spalten „SSN“ und „BirthDate“ abgerufenen Daten transparent entschlüsselt.

> [!NOTE]
> Abfragen können für Spalten Übereinstimmungsvergleiche ausführen, wenn diese mittels deterministischer Verschlüsselung verschlüsselt sind. Weitere Informationen finden Sie unter [Auswählen der deterministischen oder zufälligen Verschlüsselung in Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

```java
// <Insert keystore-specific code here>
try (Connection connection = DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = connection
                .prepareStatement("\"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN = ?;\"");) {
    selectStatement.setString(1, "795-73-9838");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("SSN: " + rs.getString("SSN") + ", FirstName: " + rs.getString("FirstName") + ", LastName:"
                + rs.getString("LastName") + ", Date of Birth: " + rs.getString("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="retrieving-encrypted-data-example"></a>Beispiel zum Abrufen von verschlüsselten Daten

Wenn Always Encrypted nicht aktiviert ist, können Abfragen weiterhin Daten aus verschlüsselten Spalten abrufen, so lange die Abfrage keine Parameter für verschlüsselte Spalten enthält.

In den folgenden Beispielen wird das Abrufen von binär verschlüsselten Daten aus verschlüsselten Spalten veranschaulicht. Beachten Sie Folgendes:

- Da Always Encrypted in der Verbindungszeichenfolge nicht aktiviert ist, gibt die Abfrage verschlüsselte Werte von „SSN“ und „BirthDate“ als Bytearrays zurück (das Programm konvertiert die Werte in Zeichenfolgen).
- Eine Abfrage, die Daten aus verschlüsselten Spalten mit deaktiviertem Always Encrypted abruft, kann Parameter aufweisen, so lange keiner der Parameter auf eine verschlüsselte Spalte ausgerichtet ist. In der folgenden Abfrage wird nach der Spalte „LastName“ gefiltert, die in der Datenbank nicht verschlüsselt ist. Wenn die Abfrage nach „SSN“ oder „BirthDate“ filtert, würde ein Fehler auftreten.

```java
try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = sourceConnection
                .prepareStatement("SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;");) {

    selectStatement.setString(1, "Abel");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("SSN: " + rs.getString("SSN") + ", FirstName: " + rs.getString("FirstName") + ", LastName:"
                + rs.getString("LastName") + ", Date of Birth: " + rs.getString("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Vermeiden allgemeiner Probleme beim Abfragen von verschlüsselten Spalten

Dieser Abschnitt beschreibt die allgemeinen Kategorien von Fehlern bei der Abfrage verschlüsselter Spalten über Java-Anwendungen sowie einige Grundsätze zum Vermeiden dieser Fehler.

### <a name="unsupported-data-type-conversion-errors"></a>Konvertierungsfehler durch nicht unterstützte Datentypen

Always Encrypted unterstützt einige Konvertierungen für verschlüsselte Datentypen. Eine ausführliche Liste der unterstützten Typkonvertierungen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Auf folgende Weise können Sie Fehler bei der Datentypkonvertierung vermeiden: Stellen Sie Folgendes sicher:

- Verwenden Sie beim Übergeben von Werten für Parameter, die auf verschlüsselte Spalten abzielen, die richtigen Settermethoden. Stellen Sie sicher, dass der SQL Server-Datentyp des Parameters genau dem Typ der Zielspalte entspricht, oder dass eine Konvertierung des SQL Server-Datentyps des Parameters in den Zieltyp der Spalte unterstützt wird. API-Methoden wurden den Klassen SQLServerPreparedStatement, SQLServerCallableStatement und SQLServerResultSet hinzugefügt, um Parameter zu übergeben, die bestimmten SQL Server-Datentypen entsprechen. Wenn eine Spalte z. B. nicht verschlüsselt ist, können Sie mit der setTimestamp()-Methode einen Parameter an eine datetime2- oder datetime-Spalte übergeben. Wenn eine Spalte jedoch verschlüsselt ist, müssen Sie die exakte Methode verwenden, die den Typ der Spalte in der Datenbank darstellt. Verwenden Sie z. B. setTimestamp(), um Werte an eine verschlüsselte datetime2-Spalte zu übergeben, und SetDateTime(), um Werte an eine verschlüsselte datetime-Spalte zu übergeben. Eine vollständige Liste neuer APIs finden Sie unter [Always Encrypted – API-Referenz für den JDBC-Treiber](always-encrypted-api-reference-for-the-jdbc-driver.md).
- Die Genauigkeit und Dezimalstellenanzahl von Parametern, die auf Spalten der SQL Server-Datentypen „decimal“ und „numeric“ ausgerichtet sind, ist mit der für die Zielspalte konfigurierten Genauigkeit und Dezimalstellenanzahl identisch. API-Methoden wurden den Klassen SQLServerPreparedStatement, SQLServerCallableStatement und SQLServerResultSet hinzugefügt, um Genauigkeit und Skalierung zusammen mit Datenwerten für Parameter/Spalten zu akzeptieren, die die Datentypen „dezimal“ und „numerisch“ darstellen. Eine vollständige Liste neuer/überladener APIs finden Sie unter [Always Encrypted – API-Referenz für den JDBC-Treiber](always-encrypted-api-reference-for-the-jdbc-driver.md).  
- Die Sekundenbruchteil-Genauigkeit/-Skalierung von Parametern, die auf Spalten der SQL Server-Datentypen „datetime2“, „datetimeoffset“ oder „time“ ausgerichtet sind, ist in Abfragen, in denen Werte der Zielspalte geändert werden, nicht größer als die Sekundenbruchteil-Genauigkeit/-Skalierung für die Zielspalte. API-Methoden wurden den Klassen SQLServerPreparedStatement, SQLServerCallableStatement und SQLServerResultSet hinzugefügt, um Sekundenbruchteil-Genauigkeit/-Skalierung zusammen mit Datenwerten für Parameter zu akzeptieren, die diese Datentypen darstellen. Eine vollständige Liste neuer/überladener APIs finden Sie unter [Always Encrypted – API-Referenz für den JDBC-Treiber](always-encrypted-api-reference-for-the-jdbc-driver.md).

### <a name="errors-due-to-incorrect-connection-properties"></a>Fehler aufgrund falscher Verbindungseigenschaften

In diesem Abschnitt wird beschrieben, wie Verbindungseinstellungen ordnungsgemäß zur Verwendung von Always Encrypted-Daten konfiguriert werden. Da verschlüsselte Datentypen eingeschränkte Konvertierungen unterstützen, müssen die Verbindungseinstellungen **sendTimeAsDatetime** und **sendStringParametersAsUnicode** bei Verwendung verschlüsselter Spalten ordnungsgemäß konfiguriert werden. Stellen Sie Folgendes sicher:

- Die Verbindungseinstellung [sendTimeAsDatetime](setting-the-connection-properties.md) ist beim Einfügen von Daten in verschlüsselte Zeitspalten auf „false“ festgelegt. [Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden](configuring-how-java-sql-time-values-are-sent-to-the-server.md)
- Die Verbindungseinstellung [sendStringParametersAsUnicode](setting-the-connection-properties.md) ist beim Einfügen von Daten in verschlüsselte char-/varchar-/varchar(max)-Spalten auf „true“ festgelegt (oder als Standard belassen).

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Fehler aufgrund der Übergabe von Klartext anstelle von verschlüsselten Werten

Jeder Wert, der auf eine verschlüsselte Spalte ausgerichtet ist, muss in der Anwendung verschlüsselt werden. Ein Versuch, einen Klartextwert einzufügen bzw. zu ändern oder nach einem Klartextwert für eine verschlüsselte Spalte zu filtern, führt zu einem Fehler wie dem folgenden:

```java
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Stellen Sie Folgendes sicher, um solche Fehler zu vermeiden:

- Always Encrypted ist für Anwendungsabfragen aktiviert, die auf verschlüsselte Spalten ausgerichtet sind (für die Verbindungszeichenfolge oder für eine bestimmte Abfrage).
- Sie verwenden vorbereitete Anweisungen und Parameter zum Senden von Daten, die auf verschlüsselte Spalten ausgerichtet sind. Das folgende Beispiel zeigt eine Abfrage, die falsch nach einem Literal bzw. einer Konstante einer verschlüsselten Spalte (SSN) filtert, anstatt das Literal innerhalb eines Parameters zu übergeben. Diese Abfrage kann unter folgenden Voraussetzungen nicht ausgeführt werden:

```java
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");
```

## <a name="force-encryption-on-input-parameters"></a>Erzwingen der Verschlüsselung von Eingabeparametern

Das Feature „Verschlüsselung erzwingen“ erzwingt die Verschlüsselung eines Parameters bei Verwendung von Always Encrypted. Wenn das Erzwingen der Verschlüsselung verwendet wird und SQL Server den Treiber informiert, dass der Parameter nicht verschlüsselt werden muss, tritt bei der Abfrage, die diesen Parameter verwendet, ein Fehler auf. Diese Eigenschaft bietet zusätzlichen Schutz vor Angriffen, bei denen ein kompromittierter SQL Server falsche Verschlüsselungsmetadaten für den Client bereitstellt, was zur Offenlegung von Daten führen kann. Die set*-Methoden in der SQLServerPreparedStatement- und SQLServerCallableStatement-Klasse sowie die update\*-Methoden in der SQLServerResultSet-Klasse sind überladen, um ein boolesches Argument zum Angeben der Einstellung „Verschlüsselung erzwingen“ zu akzeptieren. Wenn der Wert dieses Arguments „false“ ist, wird die Verschlüsselung von Parametern vom Treiber nicht erzwungen. Wenn „Verschlüsselung erzwingen“ auf „true“ festgelegt ist, wird der Abfrageparameter nur festgelegt, wenn die Zielspalte verschlüsselt und Always Encrypted in der Verbindung oder Anweisung aktiviert ist. Die Verwendung dieser Eigenschaft bietet eine zusätzliche Sicherheitsebene, die sicherstellt, dass der Treiber nicht versehentlich Daten als Klartext an SQL Server sendet, wenn die Verschlüsselung erwartet wird.

Weitere Informationen zu den Methoden SQLServerPreparedStatement und SQLServerCallableStatement, die mit der Einstellung „Verschlüsselung erzwingen“ überladen werden, finden Sie unter [Always Encrypted – API-Referenz für den JDBC-Treiber](always-encrypted-api-reference-for-the-jdbc-driver.md).  

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Kontrollieren der Auswirkungen von Always Encrypted auf die Leistung

Da Always Encrypted eine clientseitige Verschlüsselungstechnologie ist, werden die meisten Leistungseinbußen auf der Clientseite und nicht in der Datenbank beobachtet. Neben den Kosten für Verschlüsselungs- und Entschlüsselungsvorgänge ergeben sich folgende andere Quellen für Leistungseinbußen auf der Clientseite:

- Zusätzliche Roundtrips zur Datenbank zum Abrufen von Metadaten für Abfrageparameter.
- Aufrufe an einen Spaltenhauptschlüsselspeicher für den Zugriff auf einen Spaltenhauptschlüssel.

In diesem Abschnitt werden die integrierten Leistungsoptimierungen JDBC-Treiber für SQL Server und die Steuerung der Auswirkungen der beiden oben genannten Faktoren auf die Leistung beschrieben.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Kontrollieren von Roundtrips zum Abrufen von Metadaten für Abfrageparameter

Wenn Always Encrypted für eine Verbindung aktiviert ist, ruft der Treiber standardmäßig [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) für jede parametrisierte Abfrage auf, wobei die Abfrageanweisung (ohne Parameterwerte) an SQL Server übergeben wird. Die Abfrageanweisung wird von[sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) analysiert, um zu ermitteln, ob Parameter verschlüsselt werden müssen. In diesem Fall gibt sie die verschlüsselungsbezogenen Informationen zurück, die dem Treiber das Verschlüsseln von Parameterwerten ermöglichen. Dieses Verhalten stellt einen hohen Grad an Transparenz für die Clientanwendung sicher. So lange die Anwendung Parameter verwendet, um auf verschlüsselte Spalten ausgerichteten Werte an den Treiber zu übergeben, muss die Anwendung (und der Anwendungsentwickler) nicht wissen, welche Abfragen Zugriff auf verschlüsselte Spalten haben.

### <a name="setting-always-encrypted-at-the-query-level"></a>Festlegen von Always Encrypted auf Abfrageebene

Sie können Always Encrypted für einzelne Abfragen aktivieren, anstatt es für die Verbindung einzurichten, um beim Abrufen von Verschlüsselungsmetadaten für parametrisierte Abfragen die Auswirkung auf die Leistung zu steuern. Auf diese Weise können Sie sicherstellen, dass „sys.sp_describe_parameter_encryption“ nur für Abfragen aufgerufen wird, bei denen Ihnen bekannt ist, dass sie über Parameter verfügen, die auf verschlüsselte Spalten ausgerichtet sind. Beachten Sie jedoch, dass Sie auf diese Weise die Transparenz der Verschlüsselung reduzieren: Wenn Sie die Verschlüsselungseigenschaften der Datenbankspalten ändern, müssen Sie möglicherweise den Code der Anwendung ändern, um ihn mit den Schemaänderungen auszurichten.

Um das Verhalten von Always Encrypted für einzelne Abfragen zu steuern, müssen Sie einzelne Anweisungsobjekte durch Übergabe einer Enumeration, SQLServerStatementColumnEncryptionSetting, konfigurieren, die festlegt, wie Daten beim Lesen und Schreiben verschlüsselter Spalten für diese spezifische Anweisung gesendet und empfangen werden. Hier sind einige nützliche Richtlinien:

- Wenn für die meisten Abfragen eine Clientanwendung über eine Datenbankverbindung auf verschlüsselte Spalten zugreift, verwenden Sie die folgenden Richtlinien:

    - Legen Sie für das Verbindungszeichenfolgen-Kennwort für **columnEncryptionSetting** den Wert **Aktiviert**fest.
    - Legen Sie „SqlCommandColumnEncryptionSetting.Disabled“ für einzelne Abfragen fest, die nicht auf verschlüsselte Spalten zugreifen müssen. Durch diese Einstellung werden sowohl der Aufruf von „sys.sp_describe_parameter_encryption“ als auch der Versuch deaktiviert, Werte im Resultset zu entschlüsseln.
    - Legen Sie „SqlCommandColumnEncryptionSetting.ResultSet“ für einzelne Abfragen fest, die keine Parameter besitzen, für die eine Verschlüsselung erforderlich ist, die aber Daten aus verschlüsselten Spalten abrufen. Durch diese Einstellung werden der Aufruf von „sys.sp_describe_parameter_encryption“ und die Parameterverschlüsselung deaktiviert. Die Abfrage ist in der Lage, die Ergebnisse von Spaltenverschlüsselungen zu entschlüsseln.

- Wenn für die meisten Abfragen eine Clientanwendung nicht über eine Datenbankverbindung auf verschlüsselte Spalten zugreift, verwenden Sie die folgenden Richtlinien:

    - Legen Sie für das Verbindungszeichenfolgen-Kennwort für **columnEncryptionSetting** den Wert **Deaktiviert**fest.
    - Legen Sie „SQLServerStatementColumnEncryptionSetting.Enabled“ für einzelne Abfragen mit Parametern fest, die verschlüsselt werden müssen. Durch diese Einstellung werden sowohl der Aufruf von „sys.sp_describe_parameter_encryption“ als auch die Entschlüsselung von Abfrageergebnissen aktiviert, die aus verschlüsselten Spalten abgerufen werden.
    - Legen Sie „SQLServerStatementColumnEncryptionSetting.ResultSet“ für Abfragen fest, die keine Parameter besitzen, für die eine Verschlüsselung erforderlich ist, die jedoch Daten aus verschlüsselten Spalten abrufen. Durch diese Einstellung werden der Aufruf von „sys.sp_describe_parameter_encryption“ und die Parameterverschlüsselung deaktiviert. Die Abfrage ist in der Lage, die Ergebnisse von Spaltenverschlüsselungen zu entschlüsseln.

Die SQLServerStatementColumnEncryptionSetting-Einstellungen können nicht dazu verwendet werden, die Verschlüsselung zu umgehen und Zugriff auf Klartextdaten zu erhalten. Weitere Informationen zum Konfigurieren der Spaltenverschlüsselung für eine Anweisung finden Sie unter [Always Encrypted – API-Referenz für den JDBC-Treiber](always-encrypted-api-reference-for-the-jdbc-driver.md).  

Im folgenden Beispiel ist Always Encrypted für die Datenbankverbindung deaktiviert. Die von der Anwendung ausgestellte Abfrage weist einen Parameter auf, der die nicht verschlüsselte Spalte „LastName“ anzielt. Die Abfrage ruft Daten aus den Spalten „SSN“ und „BirthDate“ ab, die beide verschlüsselt sind. In diesem Fall ist der Aufruf von „sys.sp_describe_parameter_encryption“ nicht erforderlich, um Verschlüsselungsmetadaten abzurufen. Die Entschlüsselung der Abfrageergebnisse muss jedoch aktiviert sein, damit die Anwendung Klartextwerte aus den beiden verschlüsselten Spalten erhalten kann. Um dies sicherzustellen, wird die Einstellung SQLServerStatementColumnEncryptionSetting.ResultSet verwendet.

```java
// Assumes the same table definition as in Section "Retrieving and modifying data in encrypted columns"
// where only SSN and BirthDate columns are encrypted in the database.
String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>;" 
        + "keyStoreAuthentication=JavaKeyStorePassword;"
        + "keyStoreLocation=<keyStoreLocation>" 
        + "keyStoreSecret=<keyStoreSecret>;";

String filterRecord = "SELECT FirstName, LastName, SSN, BirthDate FROM " + tableName + " WHERE LastName = ?";

try (SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = connection.prepareStatement(filterRecord, ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_READ_ONLY,
                connection.getHoldability(), SQLServerStatementColumnEncryptionSetting.ResultSetOnly);) {

    selectStatement.setString(1, "Abel");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("First name: " + rs.getString("FirstName"));
        System.out.println("Last name: " + rs.getString("LastName"));
        System.out.println("SSN: " + rs.getString("SSN"));
        System.out.println("Date of Birth: " + rs.getDate("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="column-encryption-key-caching"></a>Zwischenspeicherung von Spaltenverschlüsselungsschlüsseln

Der Microsoft JDBC-Treiber für SQL Server speichert die Spaltenverschlüsselungsschlüssel im Klartext im Speicher zwischen, um die Anzahl der Aufrufe an einen Spaltenhauptschlüsselspeicher zu verringern. Nach dem Erhalt des Verschlüsselungsschlüsselwerts für die verschlüsselte Spalte von den Datenbankmetadaten versucht der Treiber zunächst, den Spaltenverschlüsselungsschlüssel im Klartext zu finden, der dem verschlüsselten Schlüsselwert entspricht. Der Treiber ruft den Schlüsselspeicher, der den Spaltenhauptschlüssel enthält, nur dann auf, wenn er den verschlüsselten Spaltenverschlüsselungsschlüssel im Cache nicht finden kann.

Sie können einen Gültigkeitsdauerwert für die Spaltenverschlüsselungsschlüssel-Einträge im Cache mithilfe der API, setColumnEncryptionKeyCacheTtl(), in der SQLServerConnection-Klasse konfigurieren. Der Standardwert für die Gültigkeitsdauer der Spaltenverschlüsselungsschlüssel-Einträge im Cache beträgt zwei Stunden. Um das Zwischenspeichern zu deaktivieren, verwenden Sie den Wert 0. Verwenden Sie die folgende API, um einen beliebigen Wert für die Gültigkeitsdauer festzulegen:

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
```

Um beispielsweise für die Gültigkeitsdauer einen Wert von 10 Minuten festzulegen, verwenden Sie Folgendes:

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)
```

Nur TAGE, STUNDEN, MINUTEN oder SEKUNDEN werden als Zeiteinheit unterstützt.  

## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Kopieren von verschlüsselten Daten mit SQLServerBulkCopy

Mit „SQLServerBulkCopy“ können Sie Daten, die bereits verschlüsselt sind und in einer Tabelle gespeichert werden, in eine andere Tabelle kopieren, ohne die Daten zu entschlüsseln. Gehen Sie dafür folgendermaßen vor:

- Stellen Sie sicher, dass die Verschlüsselungskonfiguration der Zieltabelle mit der Konfiguration der Quelltabelle identisch ist. Insbesondere müssen für beide Tabellen dieselben Spalten verschlüsselt sein. Zudem müssen die Spalten mithilfe derselben Verschlüsselungstypen und mit denselben Verschlüsselungsschlüsseln verschlüsselt werden. Wenn eine der Zielspalten anders als die entsprechende Quellspalte verschlüsselt wurde, können Sie die Daten in der Zieltabelle nach dem Kopiervorgang nicht entschlüsseln. Die Daten werden beschädigt.
- Konfigurieren Sie beide Datenbankverbindungen, für die Quelltabelle und für die Zieltabelle, ohne Always Encrypted zu aktivieren.
- Legen Sie die Option allowEncryptedValueModifications fest. Weitere Informationen finden Sie unter [Verwenden von Massenkopieren mit dem JDBC Driver](using-bulk-copy-with-the-jdbc-driver.md).

> [!NOTE]
> Gehen Sie bei der Angabe von „AllowEncryptedValueModifications“ mit Bedacht vor, da dies möglicherweise zu einer Beschädigung der Datenbank führen kann, da der Microsoft JDBC-Treiber für SQL Server nicht überprüft, ob die Daten tatsächlich verschlüsselt oder mit demselben Verschlüsselungstyp, Algorithmus und Schlüssel wie die Zielspalte ordnungsgemäß verschlüsselt wurden.

## <a name="see-also"></a>Weitere Informationen

[„Immer verschlüsselt“ (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)