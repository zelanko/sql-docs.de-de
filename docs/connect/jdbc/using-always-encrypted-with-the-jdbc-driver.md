---
title: Verwenden von Always Encrypted mit dem JDBC-Treiber
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
caps.latest.revision: 64
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd5d3bb54c4587c177160cdf99f2f0dacc2bb086
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279281"
---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>Verwenden von Always Encrypted mit dem JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Diese Seite enthält Informationen zum Entwickeln von Java-Anwendungen mithilfe [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und der Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server.

Always Encrypted ermöglicht Clients das Verschlüsseln von vertraulichen Daten in einer Weise, dass weder die Daten noch die Verschlüsselungsschlüssel zu irgendeinem Zeitpunkt gegenüber SQL Server oder Azure SQL-Datenbank offengelegt werden. Ein Treiber, bei dem Always Encrypted aktiviert ist, z.B. der Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server, erreicht dieses Verhalten durch die transparente Ver- und Entschlüsselung von sensiblen Daten in der Clientanwendung. Der Treiber ermittelt automatisch, welche Abfrageparameter vertraulichen Datenbankspalten (mit Always Encrypted geschützt) entsprechen. Die Werte dieser Parameter werden dann vor der Übergabe an SQL Server oder Azure SQL-Datenbank verschlüsselt. Auf ähnliche Weise entschlüsselt der Treiber die Daten transparent, die von verschlüsselten Datenbankspalten in Abfrageergebnissen empfangen werden. Weitere Informationen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und [Always Encrypted-API-Referenz für den JDBC-Treiber](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

## <a name="prerequisites"></a>Voraussetzungen
- Stellen Sie Sie sicher, dass Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server auf dem Entwicklungscomputer installiert ist. 
- Laden Sie die Richtliniendateien Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction herunter und installieren Sie sie.  Achten Sie darauf, die in der ZIP-Datei enthaltene Infodatei zu lesen, um Installationsanweisungen und relevante Details zu möglichen Export-/Importproblemen zu erhalten.  

    - Wenn Sie die Datei „mssql-jdbc-X.X.X.jre7.jar“ oder die Datei „sqljdbc41.jar“ verwenden, können die Richtliniendateien von [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 7 Download](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html) heruntergeladen werden.

    - Wenn Sie die Datei „mssql-jdbc-X.X.X.jre8.jar“ oder die Datei „sqljdbc42.jar“ verwenden, können die Richtliniendateien von [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 8 Download](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) heruntergeladen werden.

    - Wenn Sie die Mssql-Jdbc-X.X.X.jre9.jar verwenden zu können, muss keine Datei heruntergeladen werden. Die Zuständigkeit-Richtlinie in Java 9 wird standardmäßig unbegrenzt Verschlüsselung.

## <a name="working-with-column-master-key-stores"></a>Arbeiten mit Spaltenhauptschlüsselspeichern
Zum Verschlüsseln und Entschlüsseln von Daten für verschlüsselte Spalten zu, behält SQL Server Verschlüsselung von spaltenverschlüsselungsschlüsseln. Spaltenverschlüsselungsschlüssel werden in der verschlüsselten Form in den Datenbankmetadaten gespeichert. Jeder Spaltenverschlüsselungsschlüssel weist einen entsprechenden Spaltenhauptschlüssel auf, mit dem der Spaltenverschlüsselungsschlüssel verschlüsselt wurde. Die Datenbank-Metadaten enthalten nicht die spaltenhauptschlüssel. Diese Schlüssel befinden sich nur durch den Client. Die Datenbank-Metadaten enthält jedoch Informationen, wo die spaltenhauptschlüssel relativ zu dem Client gespeichert werden. Die Datenbank-Metadaten kann, die z. B. des Schlüsselspeichers, der ein spaltenhauptschlüssel ist der Windows Certificate Store enthalten, und das spezifische Zertifikat zum Verschlüsseln und Entschlüsseln verwendet befindet sich in einem bestimmten Pfad innerhalb der Windows Certificate Store. Wenn der Client den Zugriff auf das Zertifikat in der Windows Certificate Store verfügt, können sie das Zertifikat abrufen. Das Zertifikat kann dann zum Entschlüsseln des spaltenverschlüsselungsschlüssels verwendet werden. Und klicken Sie dann, dass der Verschlüsselungsschlüssel zum Entschlüsseln oder Verschlüsseln von Daten für verschlüsselte Spalten auf, der Verschlüsselungsschlüssel für diese Spalte verwendet werden kann.

Der .NET Framework-Datenanbieter für SQL Server kommuniziert mit einem Schlüsselspeicher, wobei ein Spaltenhauptschlüssel-Speicheranbieter verwendet wird, der eine Instanz einer Klasse darstellt, die von der Klasse **SqlColumnEncryptionKeyStoreProvider**abgeleitet wird.

### <a name="using-built-in-column-master-key-store-providers"></a>Verwenden integrierter Spaltenhauptschlüssel-Speicheranbieter
Der Microsoft JDBC-Treiber für SQL Server enthält die folgenden integrierten Master Schlüsselspeicheranbieter. Einige dieser Anbieter registriert werden, vor den bestimmten Anbieternamen (verwendet, um den Anbieter zu suchen), und einige zusätzliche Anmeldeinformationen oder explizite Registrierung erforderlich.

| Class | und Beschreibung | Anbietername (Suche) |Ist bereits registriert?|
|:---|:---|:---|:---|
|**SQLServerColumnEncryptionAzureKeyVaultProvider**| Ein Anbieter für einen Schlüsselspeicher für Azure Key Vault.| AZURE_KEY_VAULT|nein|
|**SQLServerColumnEncryptionCertificateStoreProvider**| Ein Anbieter für den Windows-Zertifikatspeicher.|MSSQL_CERTIFICATE_STORE|Benutzerkontensteuerung
|**SQLServerColumnEncryptionJavaKeyStoreProvider**| Ein Anbieter für den Java-keystore|MSSQL_JAVA_KEYSTORE|Benutzerkontensteuerung|

Für den vorregistrierte Keystore-Anbieter müssen Sie alle Änderungen am Anwendungscode diese Anbieter verwenden, aber beachten Sie Folgendes vornehmen:

- Sie (oder Ihr Datenbankadministrator) müssen sicherstellen, dass der in den Metadaten des Spaltenhauptschlüssels konfigurierte Anbietername richtig ist und der Pfad des Spaltenhauptschlüssels dem Schlüsselpfadformat entspricht, das für einen angegebenen Anbieter gültig ist. Es wird empfohlen, dass Sie die Schlüssel mithilfe von Tools wie SQL Server Management Studio konfigurieren, die die gültigen Anbieternamen und Schlüsselpfade automatisch generieren, wenn die Anweisung CREATE COLUMN MASTER KEY (Transact-SQL) ausgegeben wird.
- Stellen Sie sicher, dass die Anwendung auf den Schlüssel im Schlüsselspeicher zugreifen kann. Diese Task kann das Gewähren des Zugriffs auf den Schlüssel und/oder Schlüsselspeicher für die Anwendung (abhängig vom Schlüsselspeicher) oder das Ausführen anderer wichtiger speicherspezifischer Konfigurationsschritte einbeziehen. Für die Verwendung der SQLServerColumnEncryptionJavaKeyStoreProvider, müssen Sie z. B. den Speicherort und das Kennwort des Keystores in den Verbindungseigenschaften angeben. 

Alle diese Keystore-Anbieter sind in den Abschnitten ausführlicher beschrieben. Sie müssen nur eine Keystore-Anbieters, damit Always Encrypted verwendet implementieren.

### <a name="using-azure-key-vault-provider"></a>Verwenden des Azure Key Vault-Anbieters
Azure Key Vault ist eine praktische Möglichkeit zum Speichern von Spaltenhauptschlüsseln für Always Encrypted (insbesondere, wenn Ihre Anwendung in Azure gehostet wird). Der Microsoft JDBC-Treiber für SQL Server umfasst einen integrierten Anbieter SQLServerColumnEncryptionAzureKeyVaultProvider, für Anwendungen, die in Azure Key Vault gespeicherten Schlüssel aufweisen. Der Name dieses Anbieters ist AZURE_KEY_VAULT. Damit den Azure Key Vault-Speicheranbieter verwenden zu können, muss der Anwendungsentwickler im Tresor und auf die Schlüssel in Azure Key Vault erstellen, und erstellen eine App-Registrierung in Azure Active Directory. Die registrierte Anwendung muss gewährt, entschlüsseln, verschlüsseln "," Schlüssel Entpacken "," Schlüssel packen "und" Überprüfen Sie Berechtigungen für den schlüsseltresor erstellt haben, für die Verwendung mit Always Encrypted definierten Richtlinien für den Zugriff zu erhalten. Weitere Informationen zum Einrichten von Key Vault, und erstellen einen spaltenhauptschlüssel finden Sie unter [Azure Key Vault – Schritt für Schritt](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/) und [Erstellen von Spaltenhauptschlüsseln in Azure Key Vault](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-azure-key-vault).

Für die Beispiele auf dieser Seite, wenn Sie einen Azure-Schlüsseltresor erstellt haben, spaltenhauptschlüssel und spaltenverschlüsselungsschlüssel mithilfe von SQL Server Management Studio basieren, die T-SQL-Skript, um sie neu zu erstellen kann Ähnlichkeit mit diesem Beispiel durch eigene spezielle **KEY_ Pfad** und **ENCRYPTED_VALUE**:

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',
    KEY_PATH = N'https://<MyKeyValutName>.vault.azure.net:443/keys/Always-Encrypted-Auto1/c61f01860f37302457fa512bb7e7f4e8'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x01BA000001680074507400700073003A002F002F006400610076006...
)
```

Um Azure Key Vault zu verwenden, müssen Clientanwendungen die SQLServerColumnEncryptionAzureKeyVaultProvider instanziieren und mit dem Treiber zu registrieren.

Hier ist ein Beispiel für die Initialisierung SQLServerColumnEncryptionAzureKeyVaultProvider:  

```java
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
```

**"ClientID"** ist die Anwendungs-ID einer App-Registrierung in einer Azure Active Directory-Instanz. **leerem ClientKey** ist ein Kennwort für den Schlüssel, die unter dieser Anwendung, die API-Zugriff auf Azure Key Vault bietet registriert.

Nachdem die Anwendung eine Instanz von SQLServerColumnEncryptionAzureKeyVaultProvider erstellt wurde, muss die Anwendung die Instanz mit dem Treiber, die mithilfe der sqlserverconnection.registercolumnencryptionkeystoreproviders()-Methode registrieren. Es wird dringend empfohlen, dass die Instanz registriert ist, mit dem Standardnamen des Suche, AZURE_KEY_VAULT, der durch Aufrufen der API SQLServerColumnEncryptionAzureKeyVaultProvider.getName() abgerufen werden können. Mithilfe des Standardnamens können Sie mit Tools wie SQL Server Management Studio oder PowerShell bereitstellen und Verwalten von Always Encrypted-Schlüssel (die Tools verwenden den Standardnamen zum Generieren des Metadatenobjekts auf spaltenhauptschlüssel). Das folgende Beispiel zeigt die Azure Key Vault-Anbieter zu registrieren. Weitere Informationen zu der sqlserverconnection.registercolumnencryptionkeystoreproviders()-Methode, finden Sie unter [Always Encrypted-API-Referenz für den JDBC-Treiber](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

```java
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(akvProvider.getName(), akvProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

> [!IMPORTANT]
>  Wenn Sie die Azure Key Vault-Keystore-Anbieter verwenden, hat die Azure Key Vault-Implementierung des JDBC-Treibers Abhängigkeiten von diesen Bibliotheken (aus GitHub), die in der Anwendung enthalten sein müssen:
>
>  [Azure Sdk für java](https://github.com/Azure/azure-sdk-for-java)
>
>  [Azure-Activedirectory-Library-for-Java-Bibliotheken](https://github.com/AzureAD/azure-activedirectory-library-for-java)
>
> Ein Beispiel dafür, wie diese Abhängigkeiten in ein Maven-Projekt eingeschlossen werden sollen, finden Sie unter [herunterladen ADAL4J und Azure-Schlüsseltresor-Abhängigkeiten mit Apache Maven](https://github.com/Microsoft/mssql-jdbc/wiki/Download-ADAL4J-And-AKV-Dependencies-with-Apache-Maven)

### <a name="using-windows-certificate-store-provider"></a>Ein Anbieter für den Windows-Zertifikatspeicher.
Mit „SqlColumnEncryptionCertificateStoreProvider“ können Spaltenhauptschlüssel im Windows-Zertifikatspeicher gespeichert werden. Verwenden Sie SQL Server Management Studio (SSMS) Always Encrypted-Assistenten oder anderer unterstützter Tools, um die spaltenhauptschlüssel und die spaltenverschlüsselung Definitionen in der Datenbank erstellen. Der gleiche Assistent kann verwendet werden, um ein selbstsigniertes Zertifikat in der Windows Certificate Store zu generieren, das als spaltenhauptschlüssel für die immer verschlüsselten Daten verwendet werden kann. Weitere Informationen zu den spaltenhauptschlüssel und Column Encryption Key T-SQL-Syntax, finden Sie unter [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) und [CREATE COLUMN Encryption KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) bzw.

Der Name des der SQLServerColumnEncryptionCertificateStoreProvider "mssql_certificate_store" ist und die GetName()"eingeben API des Anbieterobjekts abgefragt werden kann. Sie wird vom Treiber automatisch registriert und kann nahtlos ohne anwendungsänderung verwendet werden.

Für die Beispiele auf dieser Seite, wenn Sie eine Windows-Store-Zertifikat erstellt haben, spaltenhauptschlüssel und spaltenverschlüsselungsschlüssel mithilfe von SQL Server Management Studio basieren, die T-SQL-Skript, um sie neu zu erstellen kann Ähnlichkeit mit diesem Beispiel durch eigene spezielle **KEY_PATH** und **ENCRYPTED_VALUE**:

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/My/A2A91F59C461B559E4D962DA9D2BC6131B32CB91'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E0074007500730065007200...
)
```

> [!IMPORTANT]
> Während die anderen Keystore-Anbieter in diesem Artikel auf allen vom Treiber unterstützten Plattformen verfügbar sind, ist die SQLServerColumnEncryptionCertificateStoreProvider-Implementierung des JDBC-Treibers auf Windows-Betriebssystemen verfügbar. Es besteht eine Abhängigkeit auf "sqljdbc_auth.dll", die im Treiberpaket enthaltenen verfügbar ist. Wenn Sie diesen Anbieter verwenden möchten, müssen Sie die Datei „sqljdbc_auth.dll“ in ein Verzeichnis im Windows-Systempfad des Computers kopieren, auf dem der JDBC-Treiber installiert ist. Alternativ können Sie mit der java.libary.path-Systemeigenschaft das Verzeichnis von „sqljdbc_auth.dll“ angeben. Wenn Sie eine 32-Bit-JVM (Java Virtual Machine) ausführen, verwenden Sie die Datei „sqljdbc_auth.dll“ im Ordner „x86“, auch wenn es sich bei dem Betriebssystem um die x64-Version handelt. Wenn Sie eine 64-Bit-JVM mit einem x64-Prozessor ausführen, verwenden Sie die Datei „sqljdbc_auth.dll“ im Ordner „x64“. Wenn Sie beispielsweise die 32-Bit-JVM verwenden und der JDBC-Treiber im Standardverzeichnis installiert ist, können Sie den Speicherort der DLL beim Start der Java-Anwendung mit dem folgenden VM-Argument (Virtual Machine) angeben: `-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`

### <a name="using-java-key-store-provider"></a>Mithilfe von Java Key Store-Anbieter
Der JDBC-Treiber ist mit einer integrierten Schlüsselspeicheranbieter-Implementierung für den Java Key Store ausgestattet. Wenn die **KeyStoreAuthentication** Verbindungszeichenfolgen-Eigenschaft ist in der Verbindungszeichenfolge vorhanden und "JavaKeyStorePassword" festgelegt ist, der Treiber automatisch instanziiert und den Anbieter für Java Key Store registriert. Der Name des JVM-Schlüsselspeicheranbieters ist MSSQL_JVM_KEYSTORE. Dieser Name kann auch mithilfe der SQLServerColumnEncryptionJavaKeyStoreProvider.getName()-API abgefragt werden. 

Es gibt drei Verbindungszeichenfolgen-Eigenschaften, mit denen eine Client-Anwendung, um die Anmeldeinformationen anzugeben, die der Treiber benötigt, die Java-Key Store zu authentifizieren. Der Treiber initialisiert den Anbieter, die basierend auf den Werten für diese drei Eigenschaften in der Verbindungszeichenfolge.

**KeyStoreAuthentication:** identifiziert die Java Key Store zu verwenden. Mit Microsoft JDBC-Treiber 6.0 und höher für SQL Server können Sie auf der Java-Key-Store nur über diese Eigenschaft authentifizieren. Der Wert für diese Eigenschaft muss für die Java-Key-Store `JavaKeyStorePassword`.

**KeyStoreLocation:** den Pfad zu dem Java Key Store-Datei, in der die spaltenhauptschlüssel gespeichert. Der Pfad enthält den Dateinamen des Keystores.

**KeyStoreSecret:** die geheimen Schlüssel und Kennwort für den Keystore sowie für den Schlüssel zu verwenden. Für die Verwendung der Java-Key-Store, müssen den Keystore und das Kennwort für den Schlüssel übereinstimmen.

Hier ist ein Beispiel für die Bereitstellung dieser Anmeldeinformationen in der Verbindungszeichenfolge:

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
```

Sie können auch abrufen, oder legen Sie diese Einstellungen mithilfe der SQLServerDataSource-Objekts. Weitere Informationen finden Sie unter [Always Encrypted – API-Referenz für den JDBC-Treiber](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

Der JDBC-Treiber instanziiert die SQLServerColumnEncryptionJavaKeyStoreProvider automatisch, wenn diese Anmeldeinformationen in den Verbindungseigenschaften vorhanden sind.

### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Erstellen eines Spaltenhauptschlüssels (Column Master Key, CMK) für JVM Key Store
Die SQLServerColumnEncryptionJavaKeyStoreProvider kann mit JKS oder PKCS12-Keystore-Typen verwendet werden. Erstellen oder importieren ein Schlüssels für die Verwendung mit diesem Anbieter Java verwenden [Keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) Hilfsprogramm. Der Schlüssel muss es sich um dasselbe Kennwort wie der Keystore selbst haben. Hier wird verdeutlicht, wie Sie einen öffentlichen Schlüssel und den zugehörigen privaten Schlüsseln, die mit dem Keytool-Hilfsprogramm zu erstellen:

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks
```

Dieser Befehl erstellt einen öffentlichen Schlüssel und umschließt ihn in ein x. 509, selbstsigniertes Zertifikat, das im "keystore.jks" zusammen mit den zugehörigen privaten Schlüsseln-Schlüsselspeicher gespeichert ist. Dieser Eintrag im Schlüsselspeicher wird durch den Alias "AlwaysEncryptedKey" identifiziert.

Hier ist ein Beispiel für die gleiche mit einer PKCS12-Speichertyp:

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword
```

Ist der Keystore PKCS12-Typs, der Keytool-Hilfsprogramm nicht aufgefordert, für ein Kennwort für Schlüssel und Kennwort für der Schlüssel muss mit Keypass - Option angegeben werden, da die SQLServerColumnEncryptionJavaKeyStoreProvider ist erforderlich, den Keystore und den Schlüssel die gleiche haben das Kennwort.

Sie können auch ein Zertifikat aus dem Windows-Zertifikatspeicher im PFX-Format exportieren und verwenden, die mit der SQLServerColumnEncryptionJavaKeyStoreProvider. Das exportierte Zertifikat kann auch als eine JKS-Keystore-Typ auf der Java-Key-Store importiert werden.

Erstellen Sie nach dem Erstellen des Keytool-Eintrags, der Metadaten des spaltenhauptschlüssels in der Datenbank, die den Namen der Keystore-Anbieter und Schlüsselpfad benötigt. Weitere Informationen zum Erstellen von Hauptschlüssel-Spaltenmetadaten finden Sie unter [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md). Für SQLServerColumnEncryptionJavaKeyStoreProvider der Schlüsselpfad ist nur der Alias des Schlüssels, und die SQLServerColumnEncryptionJavaKeyStoreProvider heißt "MSSQL_JAVA_KEYSTORE". Sie können auch diesen Namen, die mit der öffentlichen API der GetName()"eingeben der Klasse SQLServerColumnEncryptionJavaKeyStoreProvider Abfragen. 

Die T-SQL-Syntax zum Erstellen des spaltenhauptschlüssels lautet:

```sql
CREATE COLUMN MASTER KEY [<CMK_name>]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'<key_alias>'
)
```

Für die 'AlwaysEncryptedKey"oben erstellt haben wäre der spaltenhauptschlüsseldefinition:

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
)
```

> [!NOTE]
> Die integrierte SQL Server Management Studio-Funktionalität kann nicht den Hauptschlüssel der Spaltendefinitionen für die Java-Key Store erstellen. T-SQL-Befehle müssen programmgesteuert verwendet werden.

### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Erstellen eines Spaltenverschlüsselungsschlüssels (Column Encryption Key, CEK) für JVM Key Store
SQL Server Management Studio oder ein anderes Tool kann nicht verwendet werden, um Spalte Verschlüsselungsschlüssel mithilfe der Hauptschlüssel für Spalten in der Java-Key Store zu erstellen. Die Clientanwendung muss den spaltenverschlüsselungsschlüssel, der programmgesteuert mithilfe der SQLServerColumnEncryptionJavaKeyStoreProvider-Klasse erstellen. Weitere Informationen finden Sie unter [mithilfe von Hauptschlüssel-Speicheranbieter für die programmgesteuerte schlüsselbereitstellung](#using-column-master-key-store-providers-for-programmatic-key-provisioning).

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
Beim Zugriff auf verschlüsselte Spalten sucht der Microsoft JDBC-Treiber für SQL Server den richtigen Speicheranbieter für Spaltenhauptschlüssel transparent und ruft ihn anschließend auf, um die Spaltenverschlüsselungsschlüssel zu entschlüsseln. In der Regel ruft der normale Anwendungscode die Speicheranbieter für Spaltenhauptschlüssel nicht direkt auf. Sie können jedoch zu instanziieren und rufen einen Anbieter programmgesteuert für das Bereitstellen und Verwalten von Always Encrypted-Schlüssel. Dieser Schritt kann zum Generieren eines verschlüsselten spaltenverschlüsselungsschlüssels und Entschlüsseln eines spaltenverschlüsselungsschlüssels als Teil die Rotation des spaltenhauptschlüssels, z. B. ausgeführt werden. Weitere Informationen finden Sie unter [Overview of Key Management for Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)(Übersicht über die Schlüsselverwaltung für Always Encrypted).

Die Implementierung Ihrer eigenen Schlüsselverwaltungstools ist möglicherweise erforderlich, wenn Sie einen benutzerdefinierten Schlüsselspeicheranbieter verwenden. Bei der Verwendung von Schlüsseln, die in Schlüsselspeichern (für die integrierte Anbieter vorhanden sind) und/oder in Azure Key Vault gespeichert werden, können Sie vorhandene Tools wie SQL Server Management Studio oder PowerShell verwenden, um Schlüssel zu verwalten und bereitzustellen. Wenn Sie in der Java-Key Store gespeicherten Schlüssel verwenden zu können, müssen Sie Schlüssel programmgesteuert bereitzustellen. Das folgende Beispiel veranschaulicht das Verwenden der SQLServerColumnEncryptionJavaKeyStoreProvider-Klasse zum Verschlüsseln des Schlüssels mit einem Schlüssel, die in der Java-Key Store gespeichert.

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
    private static String keyAlias = "<proide key alias>";

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

Die folgende Verbindungszeichenfolge ist ein Beispiel für die Aktivierung von Always Encrypted in der JDBC-Treiber:

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionUrl);
```

Der folgende Code ist ein entsprechendes Beispiel mithilfe der SQLServerDataSource-Objekts:

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

Always Encrypted kann auch für einzelne Abfragen aktiviert werden. Weitere Informationen finden Sie unter [Steuern der leistungsauswirkungen von Always Encrypted](#controlling-the-performance-impact-of-always-encrypted). Die Aktivierung von Always Encrypted ist für eine erfolgreiche Verschlüsselung und Entschlüsselung nicht ausreichend. Sie müssen auch Folgendes sicherstellen:
- Die Anwendung verfügt über die Datenbankberechtigungen *VIEW ANY COLUMN MASTER KEY DEFINITION* und *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* , die für den Zugriff auf die Metadaten in der Datenbank über Always Encrypted-Schlüssel erforderlich sind. Weitere Informationen finden Sie unter [Berechtigungen in Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
- Die Anwendung kann auf den Hauptschlüssel der Spalte zugreifen, der die Spaltenverschlüsselungsschlüssel schützt, mit denen die abgefragten Datenbankspalten verschlüsselt werden. Um den Anbieter Java Key Store zu verwenden, müssen Sie zusätzliche Anmeldeinformationen in der Verbindungszeichenfolge angeben. Weitere Informationen finden Sie unter [Using Java Key Store Anbieter](#using-java-key-store-provider).

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden
Die **SendTimeAsDatetime** Connection-Eigenschaft wird verwendet, um zu konfigurieren, die der java.sql.Time-Wert an den Server gesendet wird. Bei Festlegung auf False, wird der Zeitwert als einen Zeittyp für SQL Server gesendet. Wenn auf, die Zeit true festgelegt, die als Datetime-Typ-Wert gesendet wird. Wenn eine Time-Spalte verschlüsselt wird, die **SendTimeAsDatetime** -Eigenschaft muss "false" sein, wie verschlüsselte Spalten nicht die Konvertierung von Zeit zu "DateTime" unterstützen. Beachten Sie außerdem, dass diese Eigenschaft von der Standardeinstellung "true", damit die Verwendung von verschlüsselten Spalten Sie sie auf "false" festgelegt müssen. Andernfalls wird der Treiber eine Ausnahme ausgelöst. Ab Version 6.0 des Treibers, die SQLServerConnection-Klasse verfügt über zwei Methoden, um den Wert dieser Eigenschaft programmgesteuert zu konfigurieren:
 
* Öffentliche void SetSendTimeAsDatetime (boolescher SendTimeAsDateTimeValue)
* öffentlicher boolescher Wert getSendTimeAsDatetime()

Weitere Informationen zu dieser Eigenschaft finden Sie unter [konfigurieren wie java.sql.Time-Werte werden an den Server gesendet](configuring-how-java-sql-time-values-are-sent-to-the-server.md).

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>Konfigurieren, wie die Werte an den Server gesendet werden
Die **SendStringParametersAsUnicode** Connection-Eigenschaft wird verwendet, um zu konfigurieren, die Zeichenfolgenwerte in SQL Server gesendet werden. Wenn die Eigenschaft auf „TRUE“ festgelegt ist, werden String-Parameter im Unicode-Format an den Server gesendet. Festgelegt auf "false" Zeichenfolge-Parameter in nicht-Unicode-Format, z. B. ASCII oder MBCS, sondern gesendet werden. Der Standardwert dieser Eigenschaft ist „TRUE“. Wenn Always Encrypted aktiviert ist, und eine char/varchar/varchar(max)-Spalte wird verschlüsselt, der Wert der **SendStringParametersAsUnicode** muss auf "false" festgelegt werden. Wenn diese Eigenschaft festgelegt ist, auf "true", der Treiber löst eine Ausnahme beim Entschlüsseln von Daten aus einer verschlüsselten char/varchar/varchar(max)-Spalte, die Unicode-Zeichen enthält. Weitere Informationen zum Festlegen der Verbindungseigenschaften finden Sie unter [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Abrufen und Ändern von Daten in verschlüsselten Spalten
Nachdem Sie Always Encrypted für Anwendungsabfragen aktiviert haben, können Sie standard-JDBC-APIs verwenden, um Daten in verschlüsselten Datenbankspalten abrufen oder ändern. Wenn Ihre Anwendung die erforderlichen Datenbankberechtigungen verfügt und kann auf den spaltenhauptschlüssel zugreifen, wird der Treiber alle Abfrageparameter verschlüsselt, die auf verschlüsselte Spalten ausgerichtet, und entschlüsselt die Daten, die aus verschlüsselten Spalten abgerufen werden.

Wenn Always Encrypted nicht aktiviert ist, tritt bei Abfragen mit Parametern, die verschlüsselte Spalten anzielen, ein Fehler auf. Abfragen können weiterhin Daten aus verschlüsselten Spalten abrufen, solange die Abfrage keine Parameter für verschlüsselte Spalten enthält. Der Treiber versucht jedoch nicht, die aus verschlüsselten Spalten abgerufenen Werte zu entschlüsseln, deshalb erhält die Anwendung binär verschlüsselte Daten (als Bytearrays).

In der folgenden Tabelle wird das Verhalten von Abfragen in Abhängigkeit davon zusammengefasst, ob Always Encrypted aktiviert ist:

|Abfragemerkmal | Always Encrypted ist aktiviert und die Anwendung kann auf die Schlüssel und Schlüsselmetadaten zugreifen.|Always Encrypted ist aktiviert, und die Anwendung kann nicht auf die Schlüssel oder Schlüsselmetadaten zugreifen. | Always Encrypted ist deaktiviert|
|:---|:---|:---|:---|
| Abfragen mit Parametern, die auf verschlüsselte Spalten ausgerichtet sind. | Parameterwerte werden transparent verschlüsselt. | Fehler | Fehler|
| Abfragen, bei denen Daten von verschlüsselten Spalten ohne Parameter abgerufen werden, die auf verschlüsselte Spalten ausgerichtet sind.| Ergebnisse von verschlüsselten Spalten werden transparent entschlüsselt. Die Anwendung erhält Klartextwerte der JDBC-Datentypen, die den SQL Server-Datentypen entsprechen, die für die verschlüsselten Spalten konfiguriert wurden. | Fehler | Ergebnisse von verschlüsselten Spalten werden nicht entschlüsselt. Die Anwendung erhält verschlüsselte Werte als Bytearrays (byte[]).

### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Einfügen und Beispiele für verschlüsselte Daten werden abgerufen. 
Die folgenden Beispiele veranschaulichen das Abrufen und Ändern von Daten in verschlüsselten Spalten. In den Beispielen wird davon ausgegangen, die Zieltabelle mit dem folgenden Schema und den verschlüsselten Spalten von "ssn" und "BirthDate". Wenn Sie einen Spaltenhauptschlüssel mit dem Namen konfiguriert haben "MyCMK" sowie einen Verschlüsselungsschlüssel für die Spalte mit dem Namen "MyCEK" (wie in den vorherigen Abschnitten der Keystore-Anbieter beschrieben), können Sie die Tabelle, die mit diesem Skript erstellen:

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
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

Für jedes Java-Codebeispiel müssen Sie zum Einfügen von Keystore-spezifischen Code in den Speicherort notiert haben.

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

Wenn Sie einen Windows Certificate Store Keystore-Anbieter verwenden:

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";
```

Wenn Sie einen Java-Key Store Keystore-Anbieter verwenden:

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path to jks or pfx file>;keyStoreSecret=<keystore secret/password>";
```

### <a name="inserting-data-example"></a>Beispiel zum Einfügen von Daten
In diesem Beispiel wird eine Zeile in die Tabelle „Patients“ eingefügt. Beachten Sie Folgendes:
- Es erfolgt keine spezielle Verschlüsselung im Beispielcode. Der Microsoft JDBC-Treiber für SQL Server automatisch erkennt und verschlüsselt die Parameter, die verschlüsselte Spalten ausgerichtet. Durch dieses Verhalten wird die Verschlüsselung für die Anwendung transparent.
- Die in die Datenbankspalten eingefügten Werte, einschließlich der verschlüsselten Spalten, werden als gebundene Parameter übergeben. Während die Verwendung von Parametern optional ist, wenn Werte an nicht verschlüsselte Spalten gesendet werden (obwohl es dringend empfohlen wird, da es dabei hilft, eine Einschleusung von SQL-Befehlen zu verhindern), ist sie für Werte erforderlich, die verschlüsselte Spalten anzielen. Wenn in den verschlüsselten Spalten eingefügten Werte als Literale, die in der abfrageanweisung eingebettet übergeben wurden, würde die Abfrage fehl, da der Treiber wäre nicht in der Lage, die Werte in den verschlüsselten Zielspalten bestimmen, und es wäre nicht der Werte verschlüsseln. Daher würde der Server sie zurückweisen, da sie mit den verschlüsselten Spalten inkompatibel sind.
- Alle Werte werden vom Programm als Klartext ausgegeben, da der JDBC-Treiber für SQL Server die aus den verschlüsselten Spalten abgerufenen Daten transparent entschlüsselt.
- Wenn Sie eine Suche mit einer WHERE-Klausel den Wert durchführen in die WHERE-Klausel muss verwendet werden, als Parameter übergeben werden, sodass der Treiber transparent vor dem Senden an die Datenbank verschlüsseln kann. Im folgenden Beispiel wird die "ssn" als Parameter übergeben, aber die "LastName" wird als Literal übergeben, da "LastName" nicht verschlüsselt ist.
- Die Set-Methode, die für den Parameter für die Spalte "ssn" verwendet wird erstellt, die von SQL Server-Datentyp Char/Varchar zugeordnet wird. Wenn für diesen Parameter die setNString()-Methode verwendet wurde, die „nchar“ bzw. „nvarchar“ zugeordnet wird, würde bei der Abfrage ein Fehler auftreten, da Always Encrypted keine Konvertierungen von verschlüsselten nchar- und nvarchar-Werten in verschlüsselte char- und varchar-Werte unterstützt.

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

- Sie können beim Übergeben von Parameterwerten, die auf Spalten verschlüsselt die entsprechenden Setter-Methoden verwenden. Legen Sie die Typen der auf die verschlüsselten Spalten ausgerichteten Parameter so fest, dass der SQL Server-Datentyp des Parameters genau dem Typ der Zielspalte entspricht, oder dass eine Konvertierung des SQL Server-Datentyps des Parameters in den Zieltyp der Spalte unterstützt wird. API-Methoden wurden in die SQLServerResultSet, SQLServerPreparedStatement und SQLServerCallableStatement-Klassen zum Übergeben von Parametern, die für bestimmte SQL Server-Datentypen hinzugefügt. Wenn eine Spalte nicht verschlüsselt ist z. B. können Sie die setTimestamp()-Methode um einen Parameter oder eine Datetime-Spalte einen datetime2 zu übergeben. Aber wenn eine Spalte verschlüsselt wird besteht, verwenden Sie die genaue Methode, die den Typ der Spalte in der Datenbank darstellt. Verwenden Sie z. B. setTimestamp(), übergeben Sie Werte in einer verschlüsselten datetime2-Spalte und setDateTime() zum Übergeben von Werten in einer verschlüsselten "DateTime"-Spalte. Finden Sie unter [Always Encrypted-API-Referenz für den JDBC-Treiber](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) für eine vollständige Liste der neuen APIs.
- Die Genauigkeit und Dezimalstellenanzahl von Parametern, die auf Spalten der SQL Server-Datentypen „decimal“ und „numeric“ ausgerichtet sind, ist mit der für die Zielspalte konfigurierten Genauigkeit und Dezimalstellenanzahl identisch. API-Methoden wurden hinzugefügt, den SQLServerResultSet, SQLServerPreparedStatement und SQLServerCallableStatement-Klassen zum Akzeptieren von Genauigkeit und Dezimalstellenanzahl sowie Datenwerte für Parameter oder Spalten, die Datentypen decimal und numeric darstellt. Finden Sie unter [Always Encrypted-API-Referenz für den JDBC-Treiber](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) für eine vollständige Liste der APIs neue/überladen.  
- Die Genauigkeit von Parametern, die auf Spalten der SQL Server-Datentypen „datetime2“, „datetimeoffset“ oder „time“ ausgerichtet sind, ist in Abfragen, in denen Werte der Zielspalte geändert werden, nicht größer als die Genauigkeit für die Zielspalte. API-Methoden haben die SQLServerResultSet, SQLServerPreparedStatement und SQLServerCallableStatement-Klassen, die Millisekunden-Genauigkeit/Skalierung sowie Datenwerte für Parameter, die diese Datentypen darstellen akzeptieren hinzugefügt wurde. Eine vollständige Liste der neuen/überladene APIs, finden Sie unter [Always Encrypted-API-Referenz für den JDBC-Treiber](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).   

### <a name="errors-due-to-incorrect-connection-properties"></a>Fehler aufgrund von falschen Verbindungseigenschaften
Dieser Abschnitt beschreibt die Vorgehensweise: Konfigurieren der Verbindungseinstellungen richtig, um Always Encrypted Daten zu verwenden. Da Unterstützung für verschlüsselte Datentypen beschränkt Konvertierungen, die **SendTimeAsDatetime** und **sendstringparametersasunicode-Eigenschaft** Verbindungseinstellungen benötigen geeignete Konfiguration aus, wenn verschlüsselte Spalten verwenden. Stellen Sie Folgendes sicher: 
- [SendTimeAsDatetime](setting-the-connection-properties.md) verbindungseinstellung auf "false" festgelegt ist, wenn Daten in Spalten verschlüsselt. [Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden](configuring-how-java-sql-time-values-are-sent-to-the-server.md)
- [sendstringparametersasunicode-Eigenschaft](setting-the-connection-properties.md) verbindungseinstellung nastaven NA hodnotu true (oder als Standard bleibt) beim Einfügen von Daten in char/varchar/varchar(max) Spalten verschlüsselt.

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Fehler aufgrund der Übergabe von Klartext anstelle von verschlüsselten Werten
Jeder Wert, der auf eine verschlüsselte Spalte ausgerichtet ist, muss in der Anwendung verschlüsselt werden. Ein Versuch, einen Klartextwert einzufügen bzw. zu ändern oder nach einem Klartextwert für eine verschlüsselte Spalte zu filtern, führt zu einem Fehler wie dem folgenden:

```java
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Stellen Sie Folgendes sicher, um solche Fehler zu vermeiden:
- Always Encrypted ist für Anwendungsabfragen aktiviert, die auf verschlüsselte Spalten ausgerichtet sind (für die Verbindungszeichenfolge oder für eine bestimmte Abfrage).
- Verwenden Sie die vorbereitete Anweisungen aus, und Parameter zum Senden von Daten auf verschlüsselte Spalten. Das folgende Beispiel zeigt eine Abfrage, die falsch nach einem Literal bzw. einer Konstante einer verschlüsselten Spalte (SSN) filtert, anstatt das Literal innerhalb eines Parameters zu übergeben. Diese Abfrage schlägt fehl:

```java
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");
```

## <a name="force-encryption-on-input-parameters"></a>Erzwingen der Verschlüsselung auf Eingabeparameter
Das Feature für die Verschlüsselung erzwingen erzwingt die Verschlüsselung eines Parameters, bei Verwendung von Always Encrypted. Wenn das Erzwingen der Verschlüsselung verwendet wird und SQL Server den Treiber informiert, dass der Parameter nicht verschlüsselt werden muss, tritt bei der Abfrage, die diesen Parameter verwendet, ein Fehler auf. Diese Eigenschaft bietet zusätzlichen Schutz vor Angriffen, bei denen ein kompromittierter SQL Server falsche Verschlüsselungsmetadaten für den Client bereitstellt, was zur Offenlegung von Daten führen kann. Die Set *-Methoden in die Sqlserverpreparedstatement- und SQLServerCallableStatement-Klassen und das Update\* Methoden in der SQLServerResultSet-Klasse werden überladen, um ein boolesches Argument, um anzugeben, die Einstellung der Force-Verschlüsselung zu akzeptieren. Wenn der Wert dieses Arguments auf "false" festgelegt ist, wird nicht erzwingen der Treiber der Verschlüsselung auf Parameter. Wenn Force Encryption feststeht auf "true", die Abfrage Parameter wird nur gesendet, wenn die Zielspalte verschlüsselt ist, und Always Encrypted, für die Verbindung oder bei der Anweisung aktiviert ist. Mit dieser Eigenschaft können eine zusätzliche Sicherheitsebene, die sicherstellen, dass der Treiber versehentlich senden keine Daten an SQL Server als nur-Text, wenn er erwartungsgemäß verschlüsselt werden.

Weitere Informationen zu den Sqlserverpreparedstatement- und SQLServerCallableStatement-Methoden, die überladen werden mit der Force Encryption-Einstellung finden Sie unter [Always Encrypted-API-Referenz für den JDBC-Treiber](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Kontrollieren der Auswirkungen von Always Encrypted auf die Leistung
Da Always Encrypted eine clientseitige Verschlüsselungstechnologie ist, werden die meisten Leistungseinbußen auf der Clientseite und nicht in der Datenbank beobachtet. Neben den Kosten für Verschlüsselungs- und Entschlüsselungsvorgänge ergeben sich folgende andere Quellen für Leistungseinbußen auf der Clientseite:
- Zusätzliche Roundtrips zur Datenbank zum Abrufen von Metadaten für Abfrageparameter.
- Aufrufe an einen Spaltenhauptschlüsselspeicher für den Zugriff auf einen Spaltenhauptschlüssel.

In diesem Abschnitt werden die integrierten Leistungsoptimierungen JDBC-Treiber für SQL Server und die Steuerung der Auswirkungen der beiden oben genannten Faktoren auf die Leistung beschrieben.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Kontrollieren von Roundtrips zum Abrufen von Metadaten für Abfrageparameter
Wenn Always Encrypted für eine Verbindung aktiviert ist, ruft der Treiber standardmäßig [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) für jede parametrisierte Abfrage auf, wobei die Abfrageanweisung (ohne Parameterwerte) an SQL Server übergeben wird. Die Abfrageanweisung wird von[sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) analysiert, um zu ermitteln, ob Parameter verschlüsselt werden müssen. In diesem Fall gibt sie die verschlüsselungsbezogenen Informationen zurück, die dem Treiber das Verschlüsseln von Parameterwerten ermöglichen. Dieses Verhalten stellt einen hohen Grad an Transparenz für die Clientanwendung sicher. Solange die Anwendung Parameter zum Übergeben der Werte, die verschlüsselte Spalten an den Treiber als Ziel verwendet werden, müssen die Anwendung (und der Anwendungsentwickler) nicht wissen, welche Abfragen Zugriff auf verschlüsselte Spalten.

### <a name="setting-always-encrypted-at-the-query-level"></a>Festlegen von Always Encrypted auf Abfrageebene
Sie können Always Encrypted für einzelne Abfragen aktivieren, anstatt es für die Verbindung einzurichten, um beim Abrufen von Verschlüsselungsmetadaten für parametrisierte Abfragen die Auswirkung auf die Leistung zu steuern. Auf diese Weise können Sie sicherstellen, dass „sys.sp_describe_parameter_encryption“ nur für Abfragen aufgerufen wird, bei denen Ihnen bekannt ist, dass sie über Parameter verfügen, die auf verschlüsselte Spalten ausgerichtet sind. Beachten Sie jedoch, dass Sie auf diese Weise die Transparenz der Verschlüsselung reduzieren: Wenn Sie die Verschlüsselungseigenschaften der Datenbankspalten ändern, müssen Sie möglicherweise den Code der Anwendung ändern, um ihn mit den Schemaänderungen auszurichten.

Um Always Encrypted zu einzelner Abfragen steuern zu können, müssen Sie konfigurieren einzelne Statement-Objekte durch Übergeben einer Enumeration sqlserverstatementcolumnencryptionsetting darf, der angibt, wie Daten werden gesendet und empfangen beim Lesen und Schreiben verschlüsselte Spalten für diese bestimmte Anweisung. Hier sind einige nützliche Richtlinien:
- Wenn für die meisten Abfragen eine Clientanwendung über eine Datenbankverbindung auf verschlüsselte Spalten zugreift, verwenden Sie die folgenden Richtlinien:
    - Legen Sie für das Verbindungszeichenfolgen-Kennwort für **columnEncryptionSetting** den Wert **Aktiviert**fest.
    - Legen Sie „SqlCommandColumnEncryptionSetting.Disabled“ für einzelne Abfragen fest, die nicht auf verschlüsselte Spalten zugreifen müssen. Durch diese Einstellung werden sowohl der Aufruf von „sys.sp_describe_parameter_encryption“ als auch der Versuch deaktiviert, Werte im Resultset zu entschlüsseln.
    - Legen Sie „SqlCommandColumnEncryptionSetting.ResultSet“ für einzelne Abfragen fest, die keine Parameter besitzen, für die eine Verschlüsselung erforderlich ist, die aber Daten aus verschlüsselten Spalten abrufen. Durch diese Einstellung werden der Aufruf von „sys.sp_describe_parameter_encryption“ und die Parameterverschlüsselung deaktiviert. Die Abfrage ist in der Lage, die Ergebnisse von Spaltenverschlüsselungen zu entschlüsseln.
- Wenn für die meisten Abfragen eine Clientanwendung nicht über eine Datenbankverbindung auf verschlüsselte Spalten zugreift, verwenden Sie die folgenden Richtlinien:
    - Legen Sie für das Verbindungszeichenfolgen-Kennwort für **columnEncryptionSetting** den Wert **Deaktiviert**fest.
    - Legen Sie „SQLServerStatementColumnEncryptionSetting.Enabled“ für einzelne Abfragen mit Parametern fest, die verschlüsselt werden müssen. Durch diese Einstellung werden sowohl der Aufruf von „sys.sp_describe_parameter_encryption“ als auch die Entschlüsselung von Abfrageergebnissen aktiviert, die aus verschlüsselten Spalten abgerufen werden.
    - Legen Sie „SQLServerStatementColumnEncryptionSetting.ResultSet“ für Abfragen fest, die keine Parameter besitzen, für die eine Verschlüsselung erforderlich ist, die jedoch Daten aus verschlüsselten Spalten abrufen. Durch diese Einstellung werden der Aufruf von „sys.sp_describe_parameter_encryption“ und die Parameterverschlüsselung deaktiviert. Die Abfrage ist in der Lage, die Ergebnisse von Spaltenverschlüsselungen zu entschlüsseln.

Sqlserverstatementcolumnencryptionsetting darf Einstellungen können nicht verwendet werden, um Verschlüsselung zu umgehen und den Zugriff auf Klartextdaten. Weitere Informationen zum Konfigurieren der spaltenverschlüsselung in einer Anweisung finden Sie unter [Always Encrypted-API-Referenz für den JDBC-Treiber](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  

Im folgenden Beispiel ist Always Encrypted für die Datenbankverbindung deaktiviert. Die von der Anwendung ausgestellte Abfrage weist einen Parameter auf, der die nicht verschlüsselte Spalte „LastName“ anzielt. Die Abfrage ruft Daten aus den Spalten „SSN“ und „BirthDate“ ab, die beide verschlüsselt sind. In diesem Fall ist der Aufruf von „sys.sp_describe_parameter_encryption“ nicht erforderlich, um Verschlüsselungsmetadaten abzurufen. Die Entschlüsselung der Abfrageergebnisse muss jedoch aktiviert sein, damit die Anwendung Klartextwerte aus den beiden verschlüsselten Spalten erhalten kann. Um dies sicherzustellen, wird die Einstellung „SqlCommandColumnEncryptionSetting.ResultSet-Einstellung“ verwendet.

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

Sie können einen Time-to-live-Wert für den spaltenverschlüsselungsschlüssel-Einträge im Cache mithilfe der API setColumnEncryptionKeyCacheTtl(), in der SQLServerConnection-Klasse konfigurieren. Der Standardwert für Time-to-live für die Spalte spaltenverschlüsselungsschlüssel-Einträge im Cache ist zwei Stunden. Um das Zwischenspeichern zu deaktivieren, verwenden Sie den Wert 0. Um alle Time-to-live-Wert festzulegen, verwenden Sie die folgende API:

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
```

Z. B. um eine Time-to-live-Wert von 10 Minuten festzulegen, verwenden Sie:

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)
```

Nur Tage, Stunden, Minuten oder Sekunden werden als Zeiteinheit unterstützt.  

## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Kopieren von verschlüsselten Daten mithilfe von „SqlBulkCopy“
Mit „SQLServerBulkCopy“ können Sie Daten, die bereits verschlüsselt sind und in einer Tabelle gespeichert werden, in eine andere Tabelle kopieren, ohne die Daten zu entschlüsseln. Gehen Sie dazu wie folgt vor:

- Stellen Sie sicher, dass die Verschlüsselungskonfiguration der Zieltabelle mit der Konfiguration der Quelltabelle identisch ist. Insbesondere müssen für beide Tabellen dieselben Spalten verschlüsselt sein. Zudem müssen die Spalten mithilfe derselben Verschlüsselungstypen und mit denselben Verschlüsselungsschlüsseln verschlüsselt werden. Wenn eine der Zielspalten anders als die entsprechende Quellspalte verschlüsselt wurde, können Sie die Daten in der Zieltabelle nach dem Kopiervorgang nicht entschlüsseln. Die Daten werden beschädigt.
- Konfigurieren Sie beide Datenbankverbindungen, für die Quelltabelle und für die Zieltabelle, ohne Always Encrypted zu aktivieren.
- Legen Sie die Option "AllowEncryptedValueModifications". Weitere Informationen finden Sie unter [mithilfe von Massenkopieren mit dem JDBC-Treiber](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

> [!NOTE]
> Gehen Sie bei der Angabe von „AllowEncryptedValueModifications“ mit Bedacht vor, da dies möglicherweise zu einer Beschädigung der Datenbank führen kann, da der Microsoft JDBC-Treiber für SQL Server nicht überprüft, ob die Daten tatsächlich verschlüsselt oder mit demselben Verschlüsselungstyp, Algorithmus und Schlüssel wie die Zielspalte ordnungsgemäß verschlüsselt wurden.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

  [„Immer verschlüsselt“ (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
