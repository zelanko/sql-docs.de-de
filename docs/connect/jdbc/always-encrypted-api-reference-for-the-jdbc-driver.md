---
title: 'Always Encrypted: API-Referenz für den JDBC-Treiber | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66f659f5fbb2daa0b0a9969c3e7cde75dccc53d0
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361670"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Always Encrypted – API-Referenz für den JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  „Immer verschlüsselt“ ermöglicht es Clients, sensible Daten in Clientanwendungen zu verschlüsseln und die Verschlüsselungsschlüssel niemals an SQL Server weiterzugeben. Ein auf dem Clientcomputer installierter Treiber, bei dem Always Encrypted aktiviert ist, erreicht diese Funktionalität durch die automatische Ver- und Entschlüsselung von sensiblen Daten in der SQL Server-Clientanwendung. Der Treiber verschlüsselt die Daten in vertraulichen Spalten, bevor er sie an SQL Server weitergibt, und schreibt Abfragen automatisch neu, sodass die Semantik der Anwendung beibehalten wird. Auf ähnliche Weise entschlüsselt der Treiber transparent Daten in verschlüsselten Datenbankspalten, die in Abfrageergebnissen enthalten sind. Weitere Informationen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und [Using Always Encrypted, mit dem JDBC-Treiber](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted wird nur vom Microsoft JDBC-Treiber 6.0 oder höher für SQL Server mit SQL Server 2016 unterstützt.  
  
 ## <a name="always-encrypted-api-references"></a>Always Encrypted: API-Referenzen
 
 Für Clientanwendungen, die „Immer verschlüsselt“ verwenden, sind mehrere neue Erweiterungen und Änderungen der JDBC-Treiber-API verfügbar.  
  
 **SQLServerConnection-Klasse**  
  
|Name|Beschreibung|  
|----------|-----------------|  
|Neues Verbindungszeichenfolgen-Schlüsselwort:<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled aktiviert die Always Encrypted-Funktionalität für die Verbindung, und columnEncryptionSetting=Disabled deaktiviert sie. Zulässige Werte sind „Enabled“/„Disabled“. Der Standardwert ist „Disabled“.|  
|Neue Methoden:<br /><br /> `public static void setColumnEncryptionTrustedMasterKeyPaths(Map<String, List\<String>> trustedKeyPaths)`<br /><br /> `public static void updateColumnEncryptionTrustedMasterKeyPaths(String server, List\<String> trustedKeyPaths)`<br /><br /> `public static void removeColumnEncryptionTrustedMasterKeyPaths(String server)`|Ermöglicht Ihnen, eine Liste von vertrauenswürdigen Schlüsselpfaden für einen Datenbankserver festzulegen bzw. zu aktualisieren oder zu entfernen. Wenn der Treiber während der Verarbeitung eine Anwendungsabfrage einen Schlüsselpfad erhält, der nicht in der Liste enthalten ist, schlägt die Abfrage fehl. Diese Eigenschaft bietet zusätzlichen Schutz vor Angriffen, bei denen ein kompromittierter SQL Server gefälschte Schlüsselpfade sendet, was zu Verlusten von Schlüsselspeicher-Anmeldeinformationen führen kann.|  
|Neue Methode:<br /><br /> `public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()`|Gibt eine Liste von vertrauenswürdigen Schlüsselpfaden für einen Datenbankserver zurück.|  
|Neue Methode:<br /><br /> `public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)`|Ermöglicht Ihnen, benutzerdefinierte Schlüsselspeicheranbieter zu registrieren. Dies ist ein Wörterbuch, das Anbieternamen von Schlüsselspeichern Implementierungen von Schlüsselspeicheranbietern zuordnet.<br /><br /> Um JVM Key Store zu verwenden, müssen Sie ein JSQLServerColumnEncryptionJVMKeyStoreProvider-Objekt mit Anmeldeinformationen von JVM Key Store instanziieren und beim Treiber registrieren. Der Name für diesen Anbieter muss „MSSQL_JVM_KEYSTORE“ sein.<br /><br /> Um die Azure Key Vault-Speicher verwenden zu können, müssen Sie ein SQLServerColumnEncryptionAzureKeyStoreProvider-Objekt instanziiert und mit dem Treiber zu registrieren. Der Name für diesen Anbieter muss es sich um "AZURE_KEY_VAULT" sein.|
|`public final boolean getSendTimeAsDatetime()`|Die Einstellung der-Verbindungseigenschaft SendTimeAsDatetime zurückgegeben.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)`|Ändert die Einstellung der-Verbindungseigenschaft SendTimeAsDatetime.|

 **SQLServerConnectionPoolProxy-Klasse**
 
|Name|Beschreibung|  
|----------|-----------------|  
|`public final boolean getSendTimeAsDatetime()` | Die Einstellung der-Verbindungseigenschaft SendTimeAsDatetime zurückgegeben.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)` | Ändert die Einstellung der-Verbindungseigenschaft SendTimeAsDatetime.|
     
  
 **SQLServerDataSource-Klasse**  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public void setColumnEncryptionSetting(String columnEncryptionSetting)`|Aktiviert/deaktiviert die „Immer verschlüsselt“-Funktionalität für das Datenquellenobjekt.<br /><br /> Der Standardwert ist „Disabled“.|  
|`public String getColumnEncryptionSetting()`|Ruft die „Immer verschlüsselt“-Funktionalitätseinstellung für das Datenquellenobjekt ab.|
|`public void setKeyStoreAuthentication(String keyStoreAuthentication)`|Legt den Namen fest, der einen Schlüsselspeicher bezeichnet. Nur unterstützte Wert lautet die **JavaKeyStorePassword** zum Identifizieren der Java-Key Store.<br/><br/>Der Standardwert ist NULL.|
|`public String getKeyStoreAuthentication()`|Ruft den Wert für die KeyStoreAuthentication-Einstellung für das Datenquellenobjekt ab.|
|`public void setKeyStoreSecret(String keyStoreSecret)`|Legt das Kennwort für den Java-Keystore. Das Kennwort für den Keystore und den Schlüssel muss identisch sein. Beachten Sie, KeyStoreAuthentication muss festgelegt werden, mit **JavaKeyStorePassword**.|
|`public void setKeyStoreLocation(String keyStoreLocation)`|Wird der Standort, einschließlich des Dateinamens für den Java-Keystore. Beachten Sie, KeyStoreAuthentication muss festgelegt werden, mit **JavaKeyStorePassword**.|
|`public String getKeyStoreLocation()`|Ruft die KeyStoreLocation für die Java-Key Store ab.|
  
 **SQLServerColumnEncryptionJavaKeyStoreProvider-Klasse**  
  
 Die Implementierung der Schlüsselspeicheranbieters für Java Key Store. Diese Klasse ermöglicht die Verwendung von Zertifikaten, die als CMKs im Java Keystore gespeichert wurden.  
  
 Konstruktoren  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionJavaKeyStoreProvider (String keyStoreLocation, char[] keyStoreSecret)`|Schlüsselspeicheranbieter für die Java-Key Store.|  
  
 Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)`|Entschlüsselt den angegebenen verschlüsselten Wert eines CEK. Es wird erwartet, dass der verschlüsselte Wert verschlüsselt wird, indem das Zertifikat mit dem angegebenen Schlüsselpfad sowie der angegebene Algorithmus verwendet wird.<br /><br /> **Das Format des Schlüsselpfads sollte eines der folgenden sein:**<br /><br /> Fingerabdruck: <certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Überschreibt SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)`|Verschlüsselt einen CEK, indem das Zertifikat mit dem angegebenen Schlüsselpfad und der angegebene Algorithmus verwendet wird.<br /><br /> **Das Format des Schlüsselpfads sollte eines der folgenden sein:**<br /><br /> Fingerabdruck: <certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Überschreibt SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public void setName (String name)`|Legt den Namen des diesem Schlüsselspeicher-Anbieter.|
|`public String getName ()`|Ruft den Namen dieser Schlüsselspeicheranbieter ab.|
  
 **SQLServerColumnEncryptionAzureKeyVaultProvider-Klasse**  
  
 Die Implementierung der Schlüsselspeicheranbieters für Azure Key Vault. Diese Klasse ermöglicht die Verwendung von Schlüsseln, die als spaltenhauptschlüssel in Azure Key Vault gespeichert.  
  
 Konstruktoren  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionAzureKeyVaultProvider (String clientId, String clientKey)`|Schlüsselspeicheranbieter für Azure Key Vault.  Sie müssen den Bezeichner und der Schlüssel des den Client, die das Token anfordert, zur Authentifizierung beim Azure Key Vault bereitstellen.|  
  
 Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
| `public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)` | Decryptes eines verschlüsselten spaltenverschlüsselungsschlüssels (CEK). Dieser Entschlüsselung erfolgt mit einem RSA-Verschlüsselungsalgorithmus, der den asymmetrischen Schlüssel, der durch den Pfad des spaltenhauptschlüssels angegeben verwendet.<br />(Überschreibt SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).) |  
| `public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)` | Verschlüsselt einen spaltenverschlüsselungsschlüssel, erteilen Sie den Hauptschlüssel der angegebenen Spalte dem angegebenen Algorithmus.<br />(Überschreibt SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).) |  
|`public void setName (String name)`|Legt den Namen des diesem Schlüsselspeicher-Anbieter.|
|`public String getName ()`|Ruft den Namen dieser Schlüsselspeicheranbieter ab.|  
  
  
 **SQLServerKeyVaultAuthenticationCallback-Schnittstelle**  
  
 Diese Schnittstelle enthält eine Methode für die Azure Key Vault-Authentifizierung, die vom Benutzer implementiert werden.  
  
 Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public String getAccessToken(String authority, String resource, String scope);`|Die Methode muss überschrieben werden. Die Methode dient zum Abrufen von Zugriffstoken in Azure Key Vault.|  
  
 **SQLServerColumnEncryptionKeyStoreProvider-Klasse**  
  
 Erweitern Sie diese Klasse, um einen benutzerdefinierten Schlüsselspeicheranbieter zu implementieren.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Basisklasse für alle Schlüsselspeicheranbieter. Ein benutzerdefinierter Anbieter muss von dieser Klasse abgeleitet werden, seine Memberfunktionen überschreiben und dann mithilfe von SQLServerConnection registriert werden. registerColumnEncryptionKeyStoreProviders().|  
  
 Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)`|Basisklassenmethode, um den angegebenen verschlüsselten Wert eines CEK zu entschlüsseln. Es wird erwartet, dass der verschlüsselte Wert verschlüsselt wird, indem der Spaltenhauptschlüssel mit dem angegebenen Schlüsselpfad sowie der angegebene Algorithmus verwendet wird.|  
|`public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)`|Basisklassenmethode, um einen CEK mithilfe eines CMK mit dem angegebenen Schlüsselpfad und mithilfe des angegebenen Algorithmus zu verschlüsseln.|
|`public abstract void setName(String name)`|Legt den Namen des diesem Schlüsselspeicher-Anbieter.|
|`public abstract String getName()`|Ruft den Namen dieser Schlüsselspeicheranbieter ab.|  
  
 Neue oder überladene Methoden in **SQLServerPreparedStatement** Klasse  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale)`<br /><br /> `public void setTime(int parameterIndex, java.sql.Time x, int scale)`<br /><br /> `public void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale)` <br />`public void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale)`|Diese Methoden werden überladen, mit einer Genauigkeit oder ein Argument für Dezimalstellen Always Encrypted für bestimmte Datentypen unterstützt, müssen die Genauigkeit und Anzahl der Dezimalstellen.|  
|`public void setMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setSmallMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setUniqueIdentifier(int parameterIndex, String guid)`<br /><br /> `public void setDateTime(int parameterIndex, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(int parameterIndex, java.sql.Timestamp x)`|Diese Methoden werden zur Unterstützung von Always Encrypted für die Daten Datentypen Money, Smallmoney, Uniqueidentifier, Datetime und Smalldatetime hinzugefügt. <br/><br/>Beachten Sie, dass die vorhandene `setTimestamp()` Methode dient zum Senden von Parameterwerten an die verschlüsselte datetime2-Spalte. Für verschlüsselte DateTime- und Smalldatetime-Spalten verwenden Sie die neuen Methoden `setDateTime()` und `setSmallDateTime()` bzw.|  
|`public final void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setSmallMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setBoolean(int parameterIndex, boolean x, boolean forceEncrypt)`<br /><br /> `public final void setByte(int parameterIndex, byte x, boolean forceEncrypt)`<br /><br /> `public final void setBytes(int parameterIndex, byte x[], boolean forceEncrypt)`<br /><br /> `public final void setUniqueIdentifier(int parameterIndex, String guid, boolean forceEncrypt)`<br /><br /> `public final void setDouble(int parameterIndex, double x, boolean forceEncrypt)`<br /><br /> `public final void setFloat(int parameterIndex, float x, boolean forceEncrypt)`<br /><br /> `public final void setInt(int parameterIndex, int value, boolean forceEncrypt)`<br /><br /> `public final void setLong(int parameterIndex, long x, boolean forceEncrypt)`<br /><br /> `public final setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale, boolean forceEncrypt)`<br /><br /> `public final void setShort(int parameterIndex, short x, boolean forceEncrypt)`<br /><br /> `public final void setString(int parameterIndex, String str, boolean forceEncrypt)`<br /><br /> `public final void setNString(int parameterIndex, String value, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setSmallDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setDate(int parameterIndex, java.sql.Date x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, java.util.Calendar cal, boolean forceEncrypt)`|Legt den angegebenen Parameter auf den angegebenen Java-Wert fest.<br /><br /> Wenn der boolesche ForceEncrypt festgelegt ist auf "true", die Abfrage Parameter wird nur festgelegt, wenn die Bezeichnung-Spalte wird verschlüsselt, und Always Encrypted, für die Verbindung oder bei der Anweisung aktiviert ist.<br /><br /> Wenn der boolesche ForceEncrypt auf "false" festgelegt ist, wird nicht erzwingen der Treiber der Verschlüsselung auf Parameter.|  
  
 Neue oder überladene Methoden in **SQLServerCallableStatement** Klasse  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)`<br />`public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale)`<br/><br/>`public final void setObject(String sCol, Object x, int targetSqlType, Integer precision, int scale)`|Diese Methoden werden überladen, mit einer Genauigkeit oder ein Argument für Dezimalstellen Always Encrypted für bestimmte Datentypen unterstützt, müssen die Genauigkeit und Anzahl der Dezimalstellen.|  
|`public void setDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid)`<br /><br /> `public void setMoney(String parameterName, BigDecimal bd)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd)`<br/><br/>`public Timestamp getDateTime(int index)`<br/><br/>`public Timestamp getDateTime(String sCol)`<br/><br/>`public Timestamp getDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(int index)`<br/><br/>`public Timestamp getSmallDateTime(String sCol)`<br/><br/>`public Timestamp getSmallDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(String name, Calendar cal)`<br/><br/>`public BigDecimal getMoney(int index)`<br/><br/>`public BigDecimal getMoney(String sCol)`<br/><br/>`public BigDecimal getSmallMoney(int index)`<br/><br/>`public BigDecimal getSmallMoney(String sCol)`|Diese Methoden werden zur Unterstützung von Always Encrypted für die Daten Datentypen Money, Smallmoney, Uniqueidentifier, Datetime und Smalldatetime hinzugefügt. <br/><br/>Beachten Sie, dass die vorhandene `setTimestamp()` Methode dient zum Senden von Parameterwerten an die verschlüsselte datetime2-Spalte. Für verschlüsselte DateTime- und Smalldatetime-Spalten verwenden Sie die neuen Methoden `setDateTime()` und `setSmallDateTime()` bzw.|  
|`public void setObject(String parameterName, Object o, int n, int m, boolean forceEncrypt)`<br /><br /> `public void setObject(String parameterName, Object obj, SQLType jdbcType, int scale, boolean forceEncrypt)`<br /><br /> `public void setDate(String parameterName, java.sql.Date x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale, boolean forceEncrypt)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid, boolean forceEncrypt)`<br /><br /> `public void setBytes(String parameterName, byte[] b, boolean forceEncrypt)`<br /><br /> `public void setByte(String parameterName, byte b, boolean forceEncrypt)`<br /><br /> `public void setString(String parameterName, String s, boolean forceEncrypt)`<br /><br /> `public final void setNString(String parameterName, String value, boolean forceEncrypt)<br /><br /> public void setMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public void setDouble(String parameterName, double d, boolean forceEncrypt)`<br /><br /> `public void setFloat(String parameterName, float f, boolean forceEncrypt)`<br /><br /> `public void setInt(String parameterName, int i, boolean forceEncrypt)`<br /><br /> `public void setLong(String parameterName, long l, boolean forceEncrypt)`<br /><br /> `public void setShort(String parameterName, short s, boolean forceEncrypt)`<br /><br /> `public void setBoolean(String parameterNames, boolean b, boolean forceEncrypt)`<br/><br/>`public void setTimeStamp(String sCol, java.sql.Timestamp x, Calendar c, Boolean forceEncrypt)`|Legt den angegebenen Parameter auf den angegebenen Java-Wert fest.<br /><br /> Wenn der boolesche ForceEncrypt festgelegt ist auf "true", die Abfrage Parameter wird nur festgelegt, wenn die Bezeichnung-Spalte wird verschlüsselt, und Always Encrypted, für die Verbindung oder bei der Anweisung aktiviert ist.<br /><br /> Wenn der boolesche ForceEncrypt auf "false" festgelegt ist, wird nicht erzwingen der Treiber der Verschlüsselung auf Parameter.|
 

 Neue oder überladene Methoden in **SQLServerResultSet** Klasse  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public String getUniqueIdentifier(int columnIndex)`<br/><br/>`public String getUniqueIdentifier(String columnLabel)`<br/><br/>   `public java.sql.Timestamp getDateTime(int columnIndex)` <br/><br/> `public java.sql.Timestamp getDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getDateTime(int columnIndex, Calendar cal)`   <br/><br/>`public java.sql.Timestamp getDateTime(String colName, Calendar cal)`    <br/><br/>`public java.sql.Timestamp getSmallDateTime(int columnIndex)`    <br/><br/> `public java.sql.Timestamp getSmallDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(int columnIndex, Calendar cal)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(String colName, Calendar cal)`   <br/><br/>  `public BigDecimal getMoney(int columnIndex)`  <br/><br/> `public BigDecimal getMoney(String columnName)`   <br/><br/> `public BigDecimal getSmallMoney(int columnIndex)`   <br/><br/>  `public BigDecimal getSmallMoney(String columnName)`  <br/><br/>`public void updateMoney(String columnName, BigDecimal x)`    <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x)`  <br/><br/>     `public void updateDateTime(int index, java.sql.Timestamp x)` <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x)` |Diese Methoden werden zur Unterstützung von Always Encrypted für die Daten Datentypen Money, Smallmoney, Uniqueidentifier, Datetime und Smalldatetime hinzugefügt. <br/><br/>Beachten Sie, dass die vorhandene `updateTimestamp()` Methode dient zum Aktualisieren von verschlüsselten datetime2-Spalten. Für verschlüsselte DateTime- und Smalldatetime-Spalten verwenden Sie die neuen Methoden `updateDateTime()` und `updateSmallDateTime()` bzw.|
|`public void updateBoolean(int index, boolean x, boolean forceEncrypt)`  <br/><br/>  `public void updateByte(int index, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(int index, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(int index, int x, boolean forceEncrypt)`   <br/><br/>  `public void updateLong(int index, long x, boolean forceEncrypt)`  <br/><br/> `public void updateFloat(int index, float x, boolean forceEncrypt)`   <br/><br/> `public void updateDouble(int index, double x, boolean forceEncrypt)`   <br/><br/> `public void updateMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateSmallMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateBigDecimal(int index, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateString(int columnIndex, String stringValue, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(int columnIndex, String nString, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(String columnLabel, String nString, boolean forceEncrypt)`  <br/><br/> `public void updateBytes(int index, byte x[], boolean forceEncrypt)   <br/><br/>  public void updateDate(int index, java.sql.Date x, boolean forceEncrypt)`  <br/><br/> `public void updateTime(int index, java.sql.Time x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateTimestamp(int index, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/> `public void updateDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateUniqueIdentifier(int index, String x, boolean forceEncrypt)`    <br/><br/>  `public void updateObject(int index, Object x, int precision, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateObject(int index, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateBoolean(String columnName, boolean x, boolean forceEncrypt)`    <br/><br/>  `public void updateByte(String columnName, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(String columnName, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(String columnName, int x, boolean forceEncrypt)`   <br/><br/>   `public void updateLong(String columnName, long x, boolean forceEncrypt)` <br/><br/>  `public void updateFloat(String columnName, float x, boolean forceEncrypt)`  <br/><br/>  `public void updateDouble(String columnName, double x, boolean forceEncrypt)  <br/><br/> public void updateBigDecimal(String columnName, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateBigDecimal(String columnName, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateString(String columnName, String x, boolean forceEncrypt)`   <br/><br/>  `public void updateBytes(String columnName, byte x[], boolean forceEncrypt)`  <br/><br/> `public void updateDate(String columnName, java.sql.Date x, boolean forceEncrypt)`   <br/><br/>  `public void updateTime(String columnName, java.sql.Time x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateTimestamp(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateDateTimeOffset(String columnName, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateUniqueIdentifier(String columnName, String x, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object x, int precision, int scale, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`|Aktualisieren Sie die angegebene Spalte, auf den angegebenen Java-Wert.<br/><br/>Wenn der boolesche ForceEncrypt festgelegt ist, auf "true", die Spalte wird nur festgelegt, wenn er verschlüsselt ist, und Always Encrypted, für die Verbindung oder bei der Anweisung aktiviert ist.<br/><br/>Wenn der boolesche ForceEncrypt auf "false" festgelegt ist, wird nicht erzwingen der Treiber der Verschlüsselung auf Parameter.|

  
Neue Typen in **microsoft.sql.Types** Klasse

|Name|Beschreibung|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Verwenden Sie diese Typen als die Ziel-SQL-Datentypen beim Senden von Parameterwerten, die **verschlüsselte** Datetime, Smalldatetime, Money, Smallmoney, Uniqueidentifier-Spalten, die mit `setObject()/updateObject()` -API-Methoden.|  
  
  
 **Sqlserverstatementcolumnencryptionsetting darf-Enumeration**  
  
 Gibt an, wie Daten werden gesendet und empfangen beim Lesen und Schreiben von verschlüsselten Spalten. Je nach spezifischer Abfrage kann Auswirkungen auf die Leistung reduziert werden, indem Sie umgehen, die Always Encrypted-Clienttreiber zu verarbeiten, wenn nicht verschlüsselte Spalten verwendet werden. Beachten Sie, dass diese Einstellungen können nicht verwendet werden, um Verschlüsselung zu umgehen und den Zugriff auf Klartextdaten.  
  
 **Syntax**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Elemente**  
  
|Name|Beschreibung|  
|----------|-----------------|  
|UseConnectionSetting|Gibt an, dass der Befehl die Always Encrypted-Einstellung in der Verbindungszeichenfolge standardmäßig sollte.|  
|Aktiviert|Aktiviert die grundsätzliche Verschlüsselung für die Abfrage.|  
|ResultSetOnly|Gibt an, dass nur die Ergebnisse des Befehls von der Routine Always Encrypted im Treiber verarbeitet werden sollen. Verwenden Sie diesen Wert, wenn der Befehl keine Parameter enthält, die eine Verschlüsselung erfordern.|  
|Disabled|Deaktiviert die grundsätzliche Verschlüsselung für die Abfrage.|  
  
 Die Einstellung der Anweisung für AE ist der SQLServerConnection-Klasse und der SQLServerConnectionPoolProxy-Klasse hinzugefügt. Die folgenden Methoden in diesen Klassen werden mit der neuen Einstellung überladen.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`public Statement createStatement(int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Erstellt ein Statement-Objekt, das ResultSet-Objekte mit der angegebenen Typs, die Parallelität, die holdability-Eigenschaft und die spaltenverschlüsselungseinstellung generiert.|  
|`public CallableStatement prepareCall(String sql, int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)`|Erstellt eine CallableStatement-Objekt mit bestimmten Column Encryption Setting, die ResultSet-Objekte mit den angegebenen Typ, Parallelität und Haltbarkeit generiert wird.|  
|`public PreparedStatement prepareStatement(String sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Erstellt eine "PreparedStatement"-Objekt mit bestimmten Column Encryption Setting, das automatisch generierte Schlüssel abrufen kann.|  
|`public PreparedStatement prepareStatement(String sql, String[] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Erstellt eine "PreparedStatement"-Objekt mit bestimmten Column Encryption Setting, die ResultSet-Objekte mit den angegebenen Spaltennamen generiert wird.|  
|`public PreparedStatement prepareStatement(String sql, int[] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting`|Erstellt eine "PreparedStatement"-Objekt mit bestimmten Column Encryption Setting, die ResultSet-Objekte mit der angegebenen Spaltenindizes generieren.|  
|`public PreparedStatement prepareStatement(String sql, int nType, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Erstellt eine "PreparedStatement"-Objekt mit bestimmten Column Encryption Setting, die ResultSet-Objekte mit den angegebenen Typ, Parallelität und Haltbarkeit generiert wird.|  
  
> [!NOTE]  
>  Wenn Always Encrypted für eine Abfrage deaktiviert ist, und die Abfrage enthält Parameter, die verschlüsselte (Parameter) sein, die den verschlüsselten Spalten entsprechen müssen, wird die Abfrage fehl.  
>   
>  Wenn Always Encrypted für eine Abfrage deaktiviert ist, und die Abfrage gibt Ergebnisse aus verschlüsselten Spalten zurück, gibt die Abfrage verschlüsselte Werte zurück. Die verschlüsselten Werte müssen den Varbinary-Datentyp.  
  
 ## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von „Immer verschlüsselt“ mit dem JDBC-Treiber](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

