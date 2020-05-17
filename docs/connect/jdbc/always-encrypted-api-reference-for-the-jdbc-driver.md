---
title: 'Always Encrypted: API-Referenz für den JDBC-Treiber | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7b5e17a6b7a98101eac8e3ddbb29a8438bc10075
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75681701"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Always Encrypted: API-Referenz für den JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  „Immer verschlüsselt“ ermöglicht es Clients, sensible Daten in Clientanwendungen zu verschlüsseln und die Verschlüsselungsschlüssel niemals an SQL Server weiterzugeben. Ein auf dem Clientcomputer installierter Treiber, bei dem Always Encrypted aktiviert ist, erreicht diese Funktionalität durch die automatische Ver- und Entschlüsselung von sensiblen Daten in der SQL Server-Clientanwendung. Der Treiber verschlüsselt die Daten in vertraulichen Spalten, bevor er sie an SQL Server weitergibt, und schreibt Abfragen automatisch neu, sodass die Semantik der Anwendung beibehalten wird. Auf ähnliche Weise entschlüsselt der Treiber transparent Daten in verschlüsselten Datenbankspalten, die in Abfrageergebnissen enthalten sind. Weitere Informationen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und [Verwenden von Always Encrypted mit dem JDBC-Treiber](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted wird nur vom Microsoft JDBC-Treiber 6.0 oder höher für SQL Server mit SQL Server 2016 unterstützt.  
  
 ## <a name="always-encrypted-api-references"></a>Always Encrypted: API-Referenzen
 
 Für Clientanwendungen, die „Immer verschlüsselt“ verwenden, sind mehrere neue Erweiterungen und Änderungen der JDBC-Treiber-API verfügbar.  
  
 **SQLServerConnection-Klasse**  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|Neues Verbindungszeichenfolgen-Schlüsselwort:<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled aktiviert die Always Encrypted-Funktionalität für die Verbindung, und columnEncryptionSetting=Disabled deaktiviert sie. Zulässige Werte sind „Enabled“/„Disabled“. Der Standardwert ist „Disabled“.|  
|Neues Schlüsselwort für Verbindungszeichenfolgen (ab MS JDBC 7.4)<br /><br /> keyVaultProviderClientId <br /><br /> keyVaultProviderClientKey |keyVaultProviderClientId=\<ClientID>;keyVaultProviderClientKey=\<ClientKey> <br/><br/> Registriert den SQLServerColumnEncryptionAzureKeyVaultProvider und verwendet die Werte von ClientID und ClientKey zum Abrufen des Spaltenhauptschlüssel aus Azure Key Vault.|  
|Neue Methoden:<br /><br /> `public static void setColumnEncryptionTrustedMasterKeyPaths(Map<String, List\<String>> trustedKeyPaths)`<br /><br /> `public static void updateColumnEncryptionTrustedMasterKeyPaths(String server, List\<String> trustedKeyPaths)`<br /><br /> `public static void removeColumnEncryptionTrustedMasterKeyPaths(String server)`|Ermöglicht Ihnen, eine Liste von vertrauenswürdigen Schlüsselpfaden für einen Datenbankserver festzulegen bzw. zu aktualisieren oder zu entfernen. Wenn der Treiber während der Verarbeitung eine Anwendungsabfrage einen Schlüsselpfad erhält, der nicht in der Liste enthalten ist, schlägt die Abfrage fehl. Diese Eigenschaft bietet zusätzlichen Schutz vor Angriffen, bei denen ein kompromittierter SQL Server gefälschte Schlüsselpfade sendet, was zu Verlusten von Schlüsselspeicher-Anmeldeinformationen führen kann.|  
|Neue Methode:<br /><br /> `public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()`|Gibt eine Liste von vertrauenswürdigen Schlüsselpfaden für einen Datenbankserver zurück.|  
|Neue Methode:<br /><br /> `public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)`|Ermöglicht Ihnen, benutzerdefinierte Schlüsselspeicheranbieter zu registrieren. Dies ist ein Wörterbuch, das Anbieternamen von Schlüsselspeichern Implementierungen von Schlüsselspeicheranbietern zuordnet.<br /><br /> Um JVM Key Store zu verwenden, müssen Sie ein JSQLServerColumnEncryptionJVMKeyStoreProvider-Objekt mit Anmeldeinformationen von JVM Key Store instanziieren und beim Treiber registrieren. Der Name für diesen Anbieter muss „MSSQL_JVM_KEYSTORE“ sein.<br /><br /> Um den Azure Key Vault-Speicher zu verwenden, müssen Sie ein SQLServerColumnEncryptionAzureKeyStoreProvider-Objekt instanziieren und beim Treiber registrieren. Der Name für diesen Anbieter muss „AZURE_KEY_VAULT“ lauten.|
|`public final boolean getSendTimeAsDatetime()`|Gibt die Einstellung der sendTimeAsDatetime-Verbindungseigenschaft zurück.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)`|Ändert die Einstellung der sendTimeAsDatetime-Verbindungseigenschaft.|

 **SQLServerConnectionPoolProxy-Klasse**
 
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public final boolean getSendTimeAsDatetime()` | Gibt die Einstellung der sendTimeAsDatetime-Verbindungseigenschaft zurück.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)` | Ändert die Einstellung der sendTimeAsDatetime-Verbindungseigenschaft.|
     
  
 **SQLServerDataSource-Klasse**  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public void setColumnEncryptionSetting(String columnEncryptionSetting)`|Aktiviert/deaktiviert die „Immer verschlüsselt“-Funktionalität für das Datenquellenobjekt.<br /><br /> Der Standardwert ist „Disabled“.|  
|`public String getColumnEncryptionSetting()`|Ruft die „Immer verschlüsselt“-Funktionalitätseinstellung für das Datenquellenobjekt ab.|
|`public void setKeyStoreAuthentication(String keyStoreAuthentication)`|Legt den Namen fest, der einen Schlüsselspeicher bezeichnet. Der einzige unterstützte Wert ist das **JavaKeyStorePassword** zum Identifizieren des Java-Keystores.<br/><br/>Der Standardwert ist NULL.|
|`public String getKeyStoreAuthentication()`|Ruft den Wert der keyStoreAuthentication-Einstellung für das Datenquellenobjekt ab.|
|`public void setKeyStoreSecret(String keyStoreSecret)`|Legt das Kennwort für den Java-Keystore fest. Das Kennwort für den Keystore und für den Schlüssel müssen übereinstimmen. Beachten Sie das keyStoreAuthentication mit **JavaKeyStorePassword** festgelegt werden muss.|
|`public void setKeyStoreLocation(String keyStoreLocation)`|Legt den Speicherort einschließlich des Dateinamens für den Java-Keystore fest. Beachten Sie das keyStoreAuthentication mit **JavaKeyStorePassword** festgelegt werden muss.|
|`public String getKeyStoreLocation()`|Ruft den keyStoreLocation für den Java-Keystore ab.|
  
 **SQLServerColumnEncryptionJavaKeyStoreProvider-Klasse**  
  
 Die Implementierung der Schlüsselspeicheranbieters für Java Key Store. Diese Klasse ermöglicht die Verwendung von Zertifikaten, die als CMKs im Java Keystore gespeichert wurden.  
  
 Konstruktoren  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionJavaKeyStoreProvider (String keyStoreLocation, char[] keyStoreSecret)`|Keystoreanbieter für den Java-Keystore.|  
  
 Methoden  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)`|Entschlüsselt den angegebenen verschlüsselten Wert eines CEK. Es wird erwartet, dass der verschlüsselte Wert verschlüsselt wird, indem das Zertifikat mit dem angegebenen Schlüsselpfad sowie der angegebene Algorithmus verwendet wird.<br /><br /> **Das Format des Schlüsselpfads sollte eines der folgenden sein:**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Überschreibt SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)`|Verschlüsselt einen CEK, indem das Zertifikat mit dem angegebenen Schlüsselpfad und der angegebene Algorithmus verwendet wird.<br /><br /> **Das Format des Schlüsselpfads sollte eines der folgenden sein:**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Überschreibt SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public void setName (String name)`|Legt den Namen dieses Keystoreanbieters fest.|
|`public String getName ()`|Ruft den Namen dieses Keystoreanbieters ab.|
  
 **SQLServerColumnEncryptionAzureKeyVaultProvider-Klasse**  
  
 Die Implementierung der Schlüsselspeicheranbieters für Azure Key Vault. Diese Klasse ermöglicht die Verwendung von Schlüsseln, die als Spaltenhauptschlüssel in Azure Key Vault gespeichert sind.  
  
 Konstruktoren  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionAzureKeyVaultProvider (String clientId, String clientKey)`|Keystoreanbieter für Azure Key Vault.  Sie müssen den Bezeichner und den Schlüssel des Clients angeben, der das Token zur Authentifizierung bei Azure Key Vault anfordert.|  
  
 Methoden  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
| `public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)` | Entschlüsselt einen verschlüsselten Spaltenverschlüsselungsschlüssel (Column Encryption Key, CEK). Diese Entschlüsselung wird mithilfe eines RSA-Verschlüsselungsalgorithmus durchgeführt, der den durch den Hauptschlüsselpfad angegebenen asymmetrischen Schlüssel verwendet.<br />(Überschreibt SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).) |  
| `public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)` | Verschlüsselt einen Spaltenverschlüsselungsschlüssel, indem der angegebene Spaltenhauptschlüssel an den angegebenen Algorithmus übergeben wird.<br />(Überschreibt SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).) |  
|`public void setName (String name)`|Legt den Namen dieses Keystoreanbieters fest.|
|`public String getName ()`|Ruft den Namen dieses Keystoreanbieters ab.|  
  
  
 **SQLServerKeyVaultAuthenticationCallback-Schnittstelle**  
  
 Diese Schnittstelle enthält eine Methode für die Authentifizierung bei Azure Key Vault, die vom Benutzer implementiert werden muss.  
  
 Methoden  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public String getAccessToken(String authority, String resource, String scope);`|Die Methode muss überschrieben werden. Die Methode wird zum Abrufen des Zugriffstokens für Azure Key Vault verwendet.|  
  
 **SQLServerColumnEncryptionKeyStoreProvider-Klasse**  
  
 Erweitern Sie diese Klasse, um einen benutzerdefinierten Schlüsselspeicheranbieter zu implementieren.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Basisklasse für alle Schlüsselspeicheranbieter. Ein benutzerdefinierter Anbieter muss von dieser Klasse abgeleitet werden, seine Memberfunktionen überschreiben und dann mithilfe von SQLServerConnection registriert werden. registerColumnEncryptionKeyStoreProviders().|  
  
 Methoden  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)`|Basisklassenmethode, um den angegebenen verschlüsselten Wert eines CEK zu entschlüsseln. Es wird erwartet, dass der verschlüsselte Wert verschlüsselt wird, indem der Spaltenhauptschlüssel mit dem angegebenen Schlüsselpfad sowie der angegebene Algorithmus verwendet wird.|  
|`public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)`|Basisklassenmethode, um einen CEK mithilfe eines CMK mit dem angegebenen Schlüsselpfad und mithilfe des angegebenen Algorithmus zu verschlüsseln.|
|`public abstract void setName(String name)`|Legt den Namen dieses Keystoreanbieters fest.|
|`public abstract String getName()`|Ruft den Namen dieses Keystoreanbieters ab.|  
  
 Neue oder überladene Methoden in der **SQLServerPreparedStatement**-Klasse  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale)`<br /><br /> `public void setTime(int parameterIndex, java.sql.Time x, int scale)`<br /><br /> `public void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale)` <br />`public void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale)`|Diese Methoden werden mit einem Argument für Genauigkeit oder Anzahl von Dezimalstellen oder beidem überladen, um Always Encrypted für bestimmte Datentypen zu unterstützen, die Informationen zu Genauigkeit und Skalierung erfordern.|  
|`public void setMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setSmallMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setUniqueIdentifier(int parameterIndex, String guid)`<br /><br /> `public void setDateTime(int parameterIndex, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(int parameterIndex, java.sql.Timestamp x)`|Diese Methoden werden hinzugefügt, um Always Encrypted für die Datentypen „money“, „smallmoney“, „uniqueidentifier“, „datetime“ und „smalldatetime“ zu unterstützen. <br/><br/>Beachten Sie, dass die vorhandene `setTimestamp()`-Methode zum Senden von Parameterwerten an die verschlüsselte datetime2-Spalte verwendet wird. Für verschlüsselte DateTime- und Smalldatetime-Spalten verwenden Sie die neuen Methoden `setDateTime()` und `setSmallDateTime()` bzw.|  
|`public final void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setSmallMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setBoolean(int parameterIndex, boolean x, boolean forceEncrypt)`<br /><br /> `public final void setByte(int parameterIndex, byte x, boolean forceEncrypt)`<br /><br /> `public final void setBytes(int parameterIndex, byte x[], boolean forceEncrypt)`<br /><br /> `public final void setUniqueIdentifier(int parameterIndex, String guid, boolean forceEncrypt)`<br /><br /> `public final void setDouble(int parameterIndex, double x, boolean forceEncrypt)`<br /><br /> `public final void setFloat(int parameterIndex, float x, boolean forceEncrypt)`<br /><br /> `public final void setInt(int parameterIndex, int value, boolean forceEncrypt)`<br /><br /> `public final void setLong(int parameterIndex, long x, boolean forceEncrypt)`<br /><br /> `public final setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale, boolean forceEncrypt)`<br /><br /> `public final void setShort(int parameterIndex, short x, boolean forceEncrypt)`<br /><br /> `public final void setString(int parameterIndex, String str, boolean forceEncrypt)`<br /><br /> `public final void setNString(int parameterIndex, String value, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setSmallDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setDate(int parameterIndex, java.sql.Date x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, java.util.Calendar cal, boolean forceEncrypt)`|Legt den angegebenen Parameter auf den angegebenen Java-Wert fest.<br /><br /> Wenn der boolesche forceEncrypt-Typ auf „true“ festgelegt ist, wird der Abfrageparameter nur festgelegt, wenn die Bezeichnungsspalte verschlüsselt und Always Encrypted in der Verbindung oder Anweisung aktiviert ist.<br /><br /> Wenn der boolesche forceEncryption-Typ auf „false“ festgelegt ist, erzwingt der Treiber die Verschlüsselung in Parametern nicht.|  
  
 Neue oder überladene Methoden in der **SQLServerCallableStatement**-Klasse  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)`<br />`public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale)`<br/><br/>`public final void setObject(String sCol, Object x, int targetSqlType, Integer precision, int scale)`|Diese Methoden werden mit einem Argument für Genauigkeit oder Anzahl von Dezimalstellen oder beidem überladen, um Always Encrypted für bestimmte Datentypen zu unterstützen, die Informationen zu Genauigkeit und Skalierung erfordern.|  
|`public void setDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid)`<br /><br /> `public void setMoney(String parameterName, BigDecimal bd)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd)`<br/><br/>`public Timestamp getDateTime(int index)`<br/><br/>`public Timestamp getDateTime(String sCol)`<br/><br/>`public Timestamp getDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(int index)`<br/><br/>`public Timestamp getSmallDateTime(String sCol)`<br/><br/>`public Timestamp getSmallDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(String name, Calendar cal)`<br/><br/>`public BigDecimal getMoney(int index)`<br/><br/>`public BigDecimal getMoney(String sCol)`<br/><br/>`public BigDecimal getSmallMoney(int index)`<br/><br/>`public BigDecimal getSmallMoney(String sCol)`|Diese Methoden werden hinzugefügt, um Always Encrypted für die Datentypen „money“, „smallmoney“, „uniqueidentifier“, „datetime“ und „smalldatetime“ zu unterstützen. <br/><br/>Beachten Sie, dass die vorhandene `setTimestamp()`-Methode zum Senden von Parameterwerten an die verschlüsselte datetime2-Spalte verwendet wird. Für verschlüsselte DateTime- und Smalldatetime-Spalten verwenden Sie die neuen Methoden `setDateTime()` und `setSmallDateTime()` bzw.|  
|`public void setObject(String parameterName, Object o, int n, int m, boolean forceEncrypt)`<br /><br /> `public void setObject(String parameterName, Object obj, SQLType jdbcType, int scale, boolean forceEncrypt)`<br /><br /> `public void setDate(String parameterName, java.sql.Date x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale, boolean forceEncrypt)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid, boolean forceEncrypt)`<br /><br /> `public void setBytes(String parameterName, byte[] b, boolean forceEncrypt)`<br /><br /> `public void setByte(String parameterName, byte b, boolean forceEncrypt)`<br /><br /> `public void setString(String parameterName, String s, boolean forceEncrypt)`<br /><br /> `public final void setNString(String parameterName, String value, boolean forceEncrypt)<br /><br /> public void setMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public void setDouble(String parameterName, double d, boolean forceEncrypt)`<br /><br /> `public void setFloat(String parameterName, float f, boolean forceEncrypt)`<br /><br /> `public void setInt(String parameterName, int i, boolean forceEncrypt)`<br /><br /> `public void setLong(String parameterName, long l, boolean forceEncrypt)`<br /><br /> `public void setShort(String parameterName, short s, boolean forceEncrypt)`<br /><br /> `public void setBoolean(String parameterNames, boolean b, boolean forceEncrypt)`<br/><br/>`public void setTimeStamp(String sCol, java.sql.Timestamp x, Calendar c, Boolean forceEncrypt)`|Legt den angegebenen Parameter auf den angegebenen Java-Wert fest.<br /><br /> Wenn der boolesche forceEncrypt-Typ auf „true“ festgelegt ist, wird der Abfrageparameter nur festgelegt, wenn die Bezeichnungsspalte verschlüsselt und Always Encrypted in der Verbindung oder Anweisung aktiviert ist.<br /><br /> Wenn der boolesche forceEncryption-Typ auf „false“ festgelegt ist, erzwingt der Treiber die Verschlüsselung in Parametern nicht.|
 

 Neue oder überladene Methoden in der **SQLServerResultSet**-Klasse  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public String getUniqueIdentifier(int columnIndex)`<br/><br/>`public String getUniqueIdentifier(String columnLabel)`<br/><br/>   `public java.sql.Timestamp getDateTime(int columnIndex)` <br/><br/> `public java.sql.Timestamp getDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getDateTime(int columnIndex, Calendar cal)`   <br/><br/>`public java.sql.Timestamp getDateTime(String colName, Calendar cal)`    <br/><br/>`public java.sql.Timestamp getSmallDateTime(int columnIndex)`    <br/><br/> `public java.sql.Timestamp getSmallDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(int columnIndex, Calendar cal)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(String colName, Calendar cal)`   <br/><br/>  `public BigDecimal getMoney(int columnIndex)`  <br/><br/> `public BigDecimal getMoney(String columnName)`   <br/><br/> `public BigDecimal getSmallMoney(int columnIndex)`   <br/><br/>  `public BigDecimal getSmallMoney(String columnName)`  <br/><br/>`public void updateMoney(String columnName, BigDecimal x)`    <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x)`  <br/><br/>     `public void updateDateTime(int index, java.sql.Timestamp x)` <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x)` |Diese Methoden werden hinzugefügt, um Always Encrypted für die Datentypen „money“, „smallmoney“, „uniqueidentifier“, „datetime“ und „smalldatetime“ zu unterstützen. <br/><br/>Beachten Sie, dass die vorhandene `updateTimestamp()`-Methode zum Aktualisieren von verschlüsselten datetime2-Spalten verwendet wird. Für verschlüsselte DateTime- und Smalldatetime-Spalten verwenden Sie die neuen Methoden `updateDateTime()` und `updateSmallDateTime()` bzw.|
|`public void updateBoolean(int index, boolean x, boolean forceEncrypt)`  <br/><br/>  `public void updateByte(int index, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(int index, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(int index, int x, boolean forceEncrypt)`   <br/><br/>  `public void updateLong(int index, long x, boolean forceEncrypt)`  <br/><br/> `public void updateFloat(int index, float x, boolean forceEncrypt)`   <br/><br/> `public void updateDouble(int index, double x, boolean forceEncrypt)`   <br/><br/> `public void updateMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateSmallMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateBigDecimal(int index, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateString(int columnIndex, String stringValue, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(int columnIndex, String nString, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(String columnLabel, String nString, boolean forceEncrypt)`  <br/><br/> `public void updateBytes(int index, byte x[], boolean forceEncrypt)   <br/><br/>  public void updateDate(int index, java.sql.Date x, boolean forceEncrypt)`  <br/><br/> `public void updateTime(int index, java.sql.Time x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateTimestamp(int index, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/> `public void updateDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateUniqueIdentifier(int index, String x, boolean forceEncrypt)`    <br/><br/>  `public void updateObject(int index, Object x, int precision, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateObject(int index, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateBoolean(String columnName, boolean x, boolean forceEncrypt)`    <br/><br/>  `public void updateByte(String columnName, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(String columnName, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(String columnName, int x, boolean forceEncrypt)`   <br/><br/>   `public void updateLong(String columnName, long x, boolean forceEncrypt)` <br/><br/>  `public void updateFloat(String columnName, float x, boolean forceEncrypt)`  <br/><br/>  `public void updateDouble(String columnName, double x, boolean forceEncrypt)  <br/><br/> public void updateBigDecimal(String columnName, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateBigDecimal(String columnName, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateString(String columnName, String x, boolean forceEncrypt)`   <br/><br/>  `public void updateBytes(String columnName, byte x[], boolean forceEncrypt)`  <br/><br/> `public void updateDate(String columnName, java.sql.Date x, boolean forceEncrypt)`   <br/><br/>  `public void updateTime(String columnName, java.sql.Time x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateTimestamp(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateDateTimeOffset(String columnName, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateUniqueIdentifier(String columnName, String x, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object x, int precision, int scale, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`|Aktualisieren Sie die angegebene Spalte auf den angegebenen Java-Wert.<br/><br/>Wenn der boolesche forceEncrypt-Typ auf „true“ festgelegt ist, wird die Spalte nur festgelegt, wenn sie verschlüsselt und Always Encrypted in der Verbindung oder Anweisung aktiviert ist.<br/><br/>Wenn der boolesche forceEncryption-Typ auf „false“ festgelegt ist, erzwingt der Treiber die Verschlüsselung in Parametern nicht.|

  
Neue Typen in der **microsoft.sql.Types**-Klasse

|Name|BESCHREIBUNG|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Verwenden Sie diese Typen als SQL-Zieltypen, wenn Sie Parameterwerte mithilfe von **-API-Methoden an** verschlüsselte`setObject()/updateObject()` datetime-, smalldatetime-, money-, smallmoney- oder uniqueidentifier-Spalten senden.|  
  
  
 **SQLServerStatementColumnEncryptionSetting-Enumeration**  
  
 Gibt an, wie Daten beim Lesen und Schreiben von verschlüsselten Spalten gesendet und empfangen werden. Je nach Abfrage können Leistungseinbußen möglicherweise durch Umgehen der Verarbeitung des Always Encrypted-Treibers verringert werden, wenn nicht verschlüsselte Spalten verwendet werden. Beachten Sie, dass diese Einstellungen nicht dazu verwendet werden können, um die Verschlüsselung zu umgehen und Zugriff auf Klartextdaten zu erhalten.  
  
 **Syntax**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Mitglieder**  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|UseConnectionSetting|Gibt an, dass der Befehl in der Verbindungszeichenfolge standardmäßig die Always Encrypted-Einstellung verwenden soll.|  
|Enabled|Aktiviert Always Encrypted für die Abfrage.|  
|ResultSetOnly|Gibt an, dass nur die Ergebnisse des Befehls von der Always Encrypted-Routine im Treiber verarbeitet werden sollen. Verwenden Sie diesen Wert, wenn der Befehl keine Parameter aufweist, die eine Verschlüsselung erfordern.|  
|Disabled|Deaktiviert Always Encrypted für die Abfrage.|  
  
 Die Einstellung für Always Encrypted auf Anweisungsebene wird zur SQLServerConnection- und zur SQLServerConnectionPoolProxy-Klasse hinzugefügt. Die folgenden Methoden in diesen Klassen werden mit der neuen Einstellung überladen.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|`public Statement createStatement(int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Erstellt ein Statement-Objekt, das ResultSet-Objekte mit den angegebenen Werten für Typ, Parallelität, Haltbarkeit und Einstellung für die Spaltenverschlüsselung generiert.|  
|`public CallableStatement prepareCall(String sql, int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)`|Erstellt ein CallableStatement-Objekt mit der angegebenen Einstellung für die Spaltenverschlüsselung, das ResultSet-Objekte mit den angegebenen Werten für Typ, Parallelität und Haltbarkeit generiert.|  
|`public PreparedStatement prepareStatement(String sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Erstellt ein PreparedStatement-Objekt mit der angegebenen Einstellung für die Spaltenverschlüsselung, das automatisch generierte Schlüssel abrufen kann.|  
|`public PreparedStatement prepareStatement(String sql, String[] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Erstellt ein PreparedStatement-Objekt mit der angegebenen Einstellung für die Spaltenverschlüsselung, das ResultSet-Objekte mit den angegebenen Spaltennamen generiert.|  
|`public PreparedStatement prepareStatement(String sql, int[] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting`|Erstellt ein PreparedStatement-Objekt mit der angegebenen Einstellung für die Spaltenverschlüsselung, das ResultSet-Objekte mit den angegebenen Spaltenindizes generiert.|  
|`public PreparedStatement prepareStatement(String sql, int nType, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Erstellt ein PreparedStatement-Objekt mit der angegebenen Einstellung für die Spaltenverschlüsselung, das ResultSet-Objekte mit den angegebenen Werten für Typ, Parallelität und Haltbarkeit generiert.|  
  
> [!NOTE]  
>  Wenn Always Encrypted für eine Abfrage deaktiviert ist und die Abfrage Parameter enthält, die verschlüsselt werden müssen (also Parameter, die verschlüsselten Spalten entsprechen), tritt bei der Abfrage ein Fehler auf.  
>   
>  Wenn Always Encrypted für eine Abfrage deaktiviert ist und die Abfrage Ergebnisse aus verschlüsselten Spalten zurückgibt, gibt die Abfrage verschlüsselte Werte zurück. Die verschlüsselten Werte weisen den Datentyp „varbinary“ auf.  
  
 ## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Always Encrypted mit dem JDBC-Treiber](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

