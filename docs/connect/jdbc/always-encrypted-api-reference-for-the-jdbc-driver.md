---
title: 'Always Encrypted: API-Referenz für den JDBC-Treiber | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b305c9e42f1eb7dffec8bd00204723a142a6b2e
ms.sourcegitcommit: 50144371c9ee924e5c0b4b9d3d4860f531c27426
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39582166"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Always Encrypted – API-Referenz für den JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  „Immer verschlüsselt“ ermöglicht es Clients, sensible Daten in Clientanwendungen zu verschlüsseln und die Verschlüsselungsschlüssel niemals an SQL Server weiterzugeben. Ein auf dem Clientcomputer installierter Treiber, bei dem Always Encrypted aktiviert ist, erreicht diese Funktionalität durch die automatische Ver- und Entschlüsselung von sensiblen Daten in der SQL Server-Clientanwendung. Der Treiber verschlüsselt die Daten in vertraulichen Spalten, bevor er sie an SQL Server weitergibt, und schreibt Abfragen automatisch neu, sodass die Semantik der Anwendung beibehalten wird. Auf ähnliche Weise entschlüsselt der Treiber transparent Daten in verschlüsselten Datenbankspalten, die in Abfrageergebnissen enthalten sind. Weitere Informationen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und [Using Always Encrypted, mit dem JDBC-Treiber](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted wird nur vom Microsoft JDBC-Treiber 6.0 oder höher für SQL Server mit SQL Server 2016 unterstützt.  
  
 ## <a name="always-encrypted-api-references"></a>Always Encrypted: API-Referenzen
 
 Für Clientanwendungen, die „Immer verschlüsselt“ verwenden, sind mehrere neue Erweiterungen und Änderungen der JDBC-Treiber-API verfügbar.  
  
 **SQLServerConnection-Klasse**  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|Neues Verbindungszeichenfolgen-Schlüsselwort:<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled aktiviert die Always Encrypted-Funktionalität für die Verbindung, und columnEncryptionSetting=Disabled deaktiviert sie. Zulässige Werte sind „Enabled“/„Disabled“. Der Standardwert ist „Disabled“.|  
|Neue Methoden:<br /><br /> Öffentliche statische void SetColumnEncryptionTrustedMasterKeyPaths (Map < String, Liste\<Zeichenfolge >> TrustedKeyPaths)<br /><br /> Öffentliche statische void UpdateColumnEncryptionTrustedMasterKeyPaths (Zeichenfolge-Server, Liste\<Zeichenfolge > TrustedKeyPaths)<br /><br /> Öffentliche statische void RemoveColumnEncryptionTrustedMasterKeyPaths (Zeichenfolge Server)|Ermöglicht Ihnen, eine Liste von vertrauenswürdigen Schlüsselpfaden für einen Datenbankserver festzulegen bzw. zu aktualisieren oder zu entfernen. Wenn der Treiber während der Verarbeitung eine Anwendungsabfrage einen Schlüsselpfad erhält, der nicht in der Liste enthalten ist, schlägt die Abfrage fehl. Diese Eigenschaft bietet zusätzlichen Schutz vor Angriffen, bei denen ein kompromittierter SQL Server gefälschte Schlüsselpfade sendet, was zu Verlusten von Schlüsselspeicher-Anmeldeinformationen führen kann.|  
|Neue Methode:<br /><br /> public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()|Gibt eine Liste von vertrauenswürdigen Schlüsselpfaden für einen Datenbankserver zurück.|  
|Neue Methode:<br /><br /> public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)|Ermöglicht Ihnen, benutzerdefinierte Schlüsselspeicheranbieter zu registrieren. Dies ist ein Wörterbuch, das Anbieternamen von Schlüsselspeichern Implementierungen von Schlüsselspeicheranbietern zuordnet.<br /><br /> Um JVM Key Store zu verwenden, müssen Sie ein JSQLServerColumnEncryptionJVMKeyStoreProvider-Objekt mit Anmeldeinformationen von JVM Key Store instanziieren und beim Treiber registrieren. Der Name für diesen Anbieter muss „MSSQL_JVM_KEYSTORE“ sein.<br /><br /> Um die Azure Key Vault-Speicher verwenden zu können, müssen Sie ein SQLServerColumnEncryptionAzureKeyStoreProvider-Objekt instanziiert und mit dem Treiber zu registrieren. Der Name für diesen Anbieter muss es sich um "AZURE_KEY_VAULT" sein.|
|public final boolean getSendTimeAsDatetime()|Die Einstellung der-Verbindungseigenschaft SendTimeAsDatetime zurückgegeben.|
|Öffentliche void SetSendTimeAsDatetime (boolescher SendTimeAsDateTimeValue)|Ändert die Einstellung der-Verbindungseigenschaft SendTimeAsDatetime.|

 **SQLServerConnectionPoolProxy-Klasse**
|Name|und Beschreibung|  
|----------|-----------------|  
|public final boolean getSendTimeAsDatetime()|Die Einstellung der-Verbindungseigenschaft SendTimeAsDatetime zurückgegeben.|
|Öffentliche void SetSendTimeAsDatetime (boolescher SendTimeAsDateTimeValue)|Ändert die Einstellung der-Verbindungseigenschaft SendTimeAsDatetime.|
     
  
 **SQLServerDataSource-Klasse**  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|public void setColumnEncryptionSetting(String columnEncryptionSetting)|Aktiviert/deaktiviert die „Immer verschlüsselt“-Funktionalität für das Datenquellenobjekt.<br /><br /> Der Standardwert ist „Disabled“.|  
|Öffentliche Zeichenfolge getColumnEncryptionSetting()|Ruft die „Immer verschlüsselt“-Funktionalitätseinstellung für das Datenquellenobjekt ab.|
|Öffentliche void SetKeyStoreAuthentication (Zeichenfolge KeyStoreAuthentication)|Legt den Namen fest, der einen Schlüsselspeicher bezeichnet. Nur unterstützte Wert lautet die **JavaKeyStorePassword** zum Identifizieren der Java-Key Store.<br/><br/>Der Standardwert ist NULL.|
|Öffentliche Zeichenfolge getKeyStoreAuthentication()|Ruft den Wert für die KeyStoreAuthentication-Einstellung für das Datenquellenobjekt ab.|
|Öffentliche void SetKeyStoreSecret (KeyStoreSecret "Zeichenfolge")|Legt das Kennwort für den Java-Keystore. Das Kennwort für den Keystore und den Schlüssel muss identisch sein. Beachten Sie, KeyStoreAuthentication muss festgelegt werden, mit **JavaKeyStorePassword**.|
|Öffentliche void SetKeyStoreLocation (KeyStoreLocation "Zeichenfolge")|Wird der Standort, einschließlich des Dateinamens für den Java-Keystore. Beachten Sie, KeyStoreAuthentication muss festgelegt werden, mit **JavaKeyStorePassword**.|
|Öffentliche Zeichenfolge getKeyStoreLocation()|Ruft die KeyStoreLocation für die Java-Key Store ab.|
  
 **SQLServerColumnEncryptionJavaKeyStoreProvider-Klasse**  
  
 Die Implementierung der Schlüsselspeicheranbieters für Java Key Store. Diese Klasse ermöglicht die Verwendung von Zertifikaten, die als CMKs im Java Keystore gespeichert wurden.  
  
 Konstruktoren  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|Öffentliche SQLServerColumnEncryptionJavaKeyStoreProvider (Zeichenfolge KeyStoreLocation, Char [] KeyStoreSecret)|Schlüsselspeicheranbieter für die Java-Key Store.|  
  
 Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)|Entschlüsselt den angegebenen verschlüsselten Wert eines CEK. Es wird erwartet, dass der verschlüsselte Wert verschlüsselt wird, indem das Zertifikat mit dem angegebenen Schlüsselpfad sowie der angegebene Algorithmus verwendet wird.<br /><br /> **Das Format des Schlüsselpfads sollte eines der folgenden sein:**<br /><br /> Fingerabdruck: <certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Überschreibt SQLServerColumnEncryptionKeyStoreProvider. "decryptcolumnencryptionkey" (String, String, Byte[]).)|  
|public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)|Verschlüsselt einen CEK, indem das Zertifikat mit dem angegebenen Schlüsselpfad und der angegebene Algorithmus verwendet wird.<br /><br /> **Das Format des Schlüsselpfads sollte eines der folgenden sein:**<br /><br /> Fingerabdruck: <certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Überschreibt SQLServerColumnEncryptionKeyStoreProvider. Decryptcolumnencryptionkey (String, String, Byte[]).)|  
|Öffentliche void SetName (Zeichenfolgenname)|Legt den Namen des diesem Schlüsselspeicher-Anbieter.|
|public String getName ()|Ruft den Namen dieser Schlüsselspeicheranbieter ab.|
  
 **SQLServerColumnEncryptionAzureKeyVaultProvider-Klasse**  
  
 Die Implementierung der Schlüsselspeicheranbieters für Azure Key Vault. Diese Klasse ermöglicht die Verwendung von Schlüsseln, die als spaltenhauptschlüssel in Azure Key Vault gespeichert.  
  
 Konstruktoren  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|Öffentliche SQLServerColumnEncryptionAzureKeyVaultProvider (Zeichenfolge "ClientID", String leerem ClientKey)|Schlüsselspeicheranbieter für Azure Key Vault.  Sie müssen den Bezeichner und der Schlüssel des den Client, die das Token anfordert, zur Authentifizierung beim Azure Key Vault bereitstellen.|  
  
 Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
| public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey) | Generieren eines verschlüsselten Spaltenverschlüsselungsschlüssels Dieser Entschlüsselung erfolgt mit einem RSA-Verschlüsselungsalgorithmus, der den asymmetrischen Schlüssel, der durch den Pfad des spaltenhauptschlüssels angegeben verwendet.<br />(Überschreibt SQLServerColumnEncryptionKeyStoreProvider. "decryptcolumnencryptionkey" (String, String, Byte[]).) |  
| public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey) | Verschlüsselt einen spaltenverschlüsselungsschlüssel, erteilen Sie den Hauptschlüssel der angegebenen Spalte dem angegebenen Algorithmus.<br />(Überschreibt SQLServerColumnEncryptionKeyStoreProvider. Decryptcolumnencryptionkey (String, String, Byte[]).) |  
|Öffentliche void SetName (Zeichenfolgenname)|Legt den Namen des diesem Schlüsselspeicher-Anbieter.|
|public String getName ()|Ruft den Namen dieser Schlüsselspeicheranbieter ab.|  
  
  
 **SQLServerKeyVaultAuthenticationCallback-Schnittstelle**  
  
 Diese Schnittstelle enthält eine Methode für die Azure Key Vault-Authentifizierung, die vom Benutzer implementiert werden.  
  
 Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|Öffentliche Zeichenfolge GetAccessToken (Autorität für die Zeichenfolge, Zeichenfolge, Zeichenfolge-Bereich);|Die Methode muss überschrieben werden. Die Methode dient zum Abrufen von Zugriffstoken in Azure Key Vault.|  
  
 **SQLServerColumnEncryptionKeyStoreProvider-Klasse**  
  
 Erweitern Sie diese Klasse, um einen benutzerdefinierten Schlüsselspeicheranbieter zu implementieren.  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Basisklasse für alle Schlüsselspeicheranbieter. Ein benutzerdefinierter Anbieter muss von dieser Klasse abgeleitet werden, seine Memberfunktionen überschreiben und dann mithilfe von SQLServerConnection registriert werden. registerColumnEncryptionKeyStoreProviders().|  
  
 Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|Basisklassenmethode, um den angegebenen verschlüsselten Wert eines CEK zu entschlüsseln. Es wird erwartet, dass der verschlüsselte Wert verschlüsselt wird, indem der Spaltenhauptschlüssel mit dem angegebenen Schlüsselpfad sowie der angegebene Algorithmus verwendet wird.|  
|public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)|Basisklassenmethode, um einen CEK mithilfe eines CMK mit dem angegebenen Schlüsselpfad und mithilfe des angegebenen Algorithmus zu verschlüsseln.|
|öffentliche abstrakte "void" SetName (Zeichenfolgenname)|Legt den Namen des diesem Schlüsselspeicher-Anbieter.|
|öffentliche abstrakte Zeichenfolge GetName()"eingeben|Ruft den Namen dieser Schlüsselspeicheranbieter ab.|  
  
 Neue oder überladene Methoden in **SQLServerPreparedStatement** Klasse  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|Öffentliche void SetBigDecimal (Int ParameterIndex, BigDecimal x mit einfacher Genauigkeit Int, Int-Skalierung)<br /><br /> Öffentliche void SetObject (Int ParameterIndex, Objekt X, Int TargetSqlType, ganze Zahl mit einfacher Genauigkeit, Skalierung von Int)<br /><br /> Öffentliche void SetObject (Int ParameterIndex, Objekt X, SQLType TargetSqlType, ganze Zahl mit einfacher Genauigkeit, Skalierung für ganze Zahl)<br /><br /> Öffentliche void SetTime (ParameterIndex von Int, java.sql.Time x, Int-Skalierung)<br /><br /> Öffentliche void SetTimestamp (ParameterIndex von Int, java.sql.Timestamp, Int Skalierung x) <br />Öffentliche void SetDateTimeOffset (Int ParameterIndex, "Microsoft.SQL.DateTimeOffset" dar, x, Int-Skalierung)|Diese Methoden werden überladen, mit einer Genauigkeit oder ein Argument für Dezimalstellen Always Encrypted für bestimmte Datentypen unterstützt, müssen die Genauigkeit und Anzahl der Dezimalstellen.|  
|Öffentliche void SetMoney (Int ParameterIndex, BigDecimal X)<br /><br /> Öffentliche void SetSmallMoney (Int ParameterIndex, BigDecimal X)<br /><br /> Öffentliche void SetUniqueIdentifier (Int ParameterIndex, String, Guid)<br /><br /> Öffentliche void SetDateTime (ParameterIndex Int, java.sql.Timestamp X)<br /><br /> Öffentliche void SetSmallDateTime (ParameterIndex Int, java.sql.Timestamp X)|Diese Methoden werden zur Unterstützung von Always Encrypted für die Daten Datentypen Money, Smallmoney, Uniqueidentifier, Datetime und Smalldatetime hinzugefügt. <br/><br/>Beachten Sie, dass die vorhandene setTimestamp()-Methode für das Senden von Parameterwerten auf die verschlüsselten datetime2-Spalte verwendet wird. Verwenden Sie für verschlüsselte Datetime und Smalldatetime-Spalten die neuen Methoden setDateTime() und setSmallDateTime() ein.|  
|Öffentliche endgültige "void" SetBigDecimal (Int ParameterIndex, BigDecimal x mit einfacher Genauigkeit Int, Int Skalierung booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetMoney (Int ParameterIndex, BigDecimal x, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetSmallMoney (Int ParameterIndex, BigDecimal x, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetBoolean (Int ParameterIndex, booleschen X, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetByte (Int ParameterIndex, Byte, x, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetBytes (ParameterIndex von Int, Byte X[], booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetUniqueIdentifier (Int ParameterIndex, String, Guid, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetDouble (Int ParameterIndex, doppelte X, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetFloat (Int ParameterIndex, "float" X, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetInt (ParameterIndex von Int, Int-Wert, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetLong (Int ParameterIndex, lange X, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige SetObject (Int ParameterIndex, Objekt X, Int TargetSqlType, ganze Zahl mit einfacher Genauigkeit, Skalierung von Int, boolean ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetObject (Int ParameterIndex, Objekt X, SQLType TargetSqlType, ganze Zahl mit einfacher Genauigkeit, Skalierung für ganze Zahl, boolescher ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetShort (Int ParameterIndex, kurze X, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetString (Int ParameterIndex, str Zeichenfolge, boolescher ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetNString (Int ParameterIndex, String-Wert, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetTime (ParameterIndex von Int, java.sql.Time, x, Int Skalierung booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetTimestamp (ParameterIndex von Int, java.sql.Timestamp, Int-Skalierung x booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige void SetDateTimeOffset (Int ParameterIndex, "Microsoft.SQL.DateTimeOffset" dar, x, Int Skalierung booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetDateTime (ParameterIndex von Int, java.sql.Timestamp, x, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetSmallDateTime (ParameterIndex von Int, java.sql.Timestamp, x, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetDate (ParameterIndex von Int, java.sql.Date, java.util.Calendar cal x booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetTime (ParameterIndex von Int, java.sql.Time, java.util.Calendar cal x booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetTimestamp (ParameterIndex von Int, java.sql.Timestamp, java.util.Calendar cal x booleschen ForceEncrypt)|Legt den angegebenen Parameter auf den angegebenen Java-Wert fest.<br /><br /> Wenn der boolesche ForceEncrypt festgelegt ist auf "true", die Abfrage Parameter wird nur festgelegt, wenn die Bezeichnung-Spalte wird verschlüsselt, und Always Encrypted, für die Verbindung oder bei der Anweisung aktiviert ist.<br /><br /> Wenn der boolesche ForceEncrypt auf "false" festgelegt ist, wird nicht erzwingen der Treiber der Verschlüsselung auf Parameter.|  
  
 Neue oder überladene Methoden in **SQLServerCallableStatement** Klasse  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)<br /><br /> public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)<br /><br /> public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)<br /><br /> public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)<br />Öffentliche void SetBigDecimal (Zeichenfolge ParameterName, BigDecimal bd, mit einfacher Genauigkeit Int, Int-Skalierung)<br /><br /> Öffentliche void SetTime (Zeichenfolge ParameterName, java.sql.Time-t, Int-Skalierung)<br /><br /> Öffentliche void SetTimestamp (Zeichenfolge ParameterName, java.sql.Timestamp t, Int-Skalierung)<br /><br /> Öffentliche void SetDateTimeOffset (Zeichenfolge ParameterName, microsoft.sql.DateTimeOffset t, Int-Skalierung)<br/><br/>Öffentliche endgültige "void" SetObject (Zeichenfolge sCol, Objekt X, Int TargetSqlType, ganze Zahl mit einfacher Genauigkeit, Skalierung von Int)|Diese Methoden werden überladen, mit einer Genauigkeit oder ein Argument für Dezimalstellen Always Encrypted für bestimmte Datentypen unterstützt, müssen die Genauigkeit und Anzahl der Dezimalstellen.|  
|Öffentliche void SetDateTime (Zeichenfolge ParameterName, java.sql.Timestamp X)<br /><br /> Öffentliche void SetSmallDateTime (Zeichenfolge ParameterName, java.sql.Timestamp X)<br /><br /> Öffentliche void SetUniqueIdentifier (ParameterName für String, String, Guid)<br /><br /> Öffentliche void SetMoney (Zeichenfolge ParameterName, BigDecimal bd)<br /><br /> Öffentliche void SetSmallMoney (Zeichenfolge ParameterName, BigDecimal bd)<br/><br/>Öffentliche Zeitstempel GetDateTime (Int Index)<br/><br/>Öffentliche Zeitstempel GetDateTime (Zeichenfolge sCol)<br/><br/>Öffentliche Zeitstempel GetDateTime (Int Index, Kalender-cal)<br/><br/>Öffentliche Zeitstempel GetSmallDateTime (Int Index)<br/><br/>Öffentliche Zeitstempel GetSmallDateTime (Zeichenfolge sCol)<br/><br/>Öffentliche Zeitstempel GetSmallDateTime (Int Index, Kalender-cal)<br/><br/>Öffentliche Zeitstempel GetSmallDateTime (Zeichenfolgenname, Kalender-cal)<br/><br/>Öffentliche BigDecimal GetMoney (Int Index)<br/><br/>Öffentliche BigDecimal GetMoney (Zeichenfolge sCol)<br/><br/>Öffentliche BigDecimal GetSmallMoney (Int Index)<br/><br/>Öffentliche BigDecimal GetSmallMoney (Zeichenfolge sCol)|Diese Methoden werden zur Unterstützung von Always Encrypted für die Daten Datentypen Money, Smallmoney, Uniqueidentifier, Datetime und Smalldatetime hinzugefügt. <br/><br/>Beachten Sie, dass die vorhandene setTimestamp()-Methode für das Senden von Parameterwerten auf die verschlüsselten datetime2-Spalte verwendet wird. Verwenden Sie für verschlüsselte Datetime und Smalldatetime-Spalten die neuen Methoden setDateTime() und setSmallDateTime() ein.|  
|Öffentliche void SetObject (Zeichenfolge ParameterName, Objekt o, Int-n, m von Int, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetObject (ParameterName der Zeichenfolge, Objekt Obj, SQLType JdbcType, Int skalieren, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetDate (Zeichenfolge ParameterName, java.sql.Date, x, Kalender-c, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetTime (Zeichenfolge ParameterName, java.sql.Time-t, Int skalieren, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetTime (Zeichenfolge ParameterName, java.sql.Time, x, Kalender-c, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetDateTime (Zeichenfolge ParameterName, java.sql.Timestamp, x, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetDateTimeOffset (Zeichenfolge ParameterName, microsoft.sql.DateTimeOffset t, Int skalieren, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetSmallDateTime (Zeichenfolge ParameterName, java.sql.Timestamp, x, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetTimestamp (Zeichenfolge ParameterName, java.sql.Timestamp t, Int skalieren, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetTimestamp (Zeichenfolge ParameterName, java.sql.Timestamp, x, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetUniqueIdentifier (Zeichenfolge ParameterName, String, Guid, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetBytes (ParameterName der Zeichenfolge, Byte [] b, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetByte ("Zeichenfolge-ParameterName", "Byte-b", "boolean ForceEncrypt")<br /><br /> Öffentliche void SetString (Zeichenfolge ParameterName, zeichenfolgenzuordnungsvorgänge, booleschen ForceEncrypt)<br /><br /> Öffentliche endgültige "void" SetNString (Zeichenfolge ParameterName, String-Wert, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetMoney (Zeichenfolge ParameterName, BigDecimal bd, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetSmallMoney (Zeichenfolge ParameterName, BigDecimal bd, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetBigDecimal (Zeichenfolge ParameterName, BigDecimal bd, Int mit einfacher Genauigkeit, Int skalieren, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetDouble (Zeichenfolge ParameterName, doppelte d, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetFloat (Zeichenfolge ParameterName, "float"-f, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetInt (Zeichenfolge ParameterName, Int i, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetLong (Zeichenfolge ParameterName, Long l-Wert, booleschen ForceEncrypt)<br /><br /> Öffentliche void SetShort ("Zeichenfolge ParameterName", "Short" s "," boolean ForceEncrypt ")<br /><br /> Öffentliche void SetBoolean ("Zeichenfolge ParameterNames", "Boolean" b "," boolean ForceEncrypt ")<br/><br/>Öffentliche void SetTimeStamp (Zeichenfolge sCol, java.sql.Timestamp, x, Kalender-c, booleschen ForceEncrypt)|Legt den angegebenen Parameter auf den angegebenen Java-Wert fest.<br /><br /> Wenn der boolesche ForceEncrypt festgelegt ist auf "true", die Abfrage Parameter wird nur festgelegt, wenn die Bezeichnung-Spalte wird verschlüsselt, und Always Encrypted, für die Verbindung oder bei der Anweisung aktiviert ist.<br /><br /> Wenn der boolesche ForceEncrypt auf "false" festgelegt ist, wird nicht erzwingen der Treiber der Verschlüsselung auf Parameter.|
 

 Neue oder überladene Methoden in **SQLServerResultSet** Klasse  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|Öffentliche Zeichenfolge GetUniqueIdentifier (ColumnIndex "Int")<br/><br/>Öffentliche Zeichenfolge GetUniqueIdentifier (Zeichenfolge ColumnLabel)<br/><br/>   Öffentliche java.sql.Timestamp GetDateTime (ColumnIndex "Int") <br/><br/> Öffentliche java.sql.Timestamp GetDateTime (Zeichenfolge Spaltenname)   <br/><br/> Öffentliche java.sql.Timestamp GetDateTime ("Int" ColumnIndex "", "Kalender cal")   <br/><br/>Öffentliche java.sql.Timestamp GetDateTime (Zeichenfolge ColName, Kalender-cal)    <br/><br/>Öffentliche java.sql.Timestamp GetSmallDateTime (ColumnIndex "Int")    <br/><br/> Öffentliche java.sql.Timestamp GetSmallDateTime (Zeichenfolge Spaltenname)   <br/><br/> Öffentliche java.sql.Timestamp GetSmallDateTime ("Int" ColumnIndex "", "Kalender cal")   <br/><br/> Öffentliche java.sql.Timestamp GetSmallDateTime (Zeichenfolge ColName, Kalender-cal)   <br/><br/>  Öffentliche BigDecimal GetMoney (ColumnIndex "Int")  <br/><br/> Öffentliche BigDecimal GetMoney (Zeichenfolge Spaltenname)   <br/><br/> Öffentliche BigDecimal GetSmallMoney (ColumnIndex "Int")   <br/><br/>  Öffentliche BigDecimal GetSmallMoney (Zeichenfolge Spaltenname)  <br/><br/>Öffentliche void UpdateMoney (Zeichenfolge ColumnName, BigDecimal X)    <br/><br/>  Öffentliche void UpdateSmallMoney (Zeichenfolge ColumnName, BigDecimal X)  <br/><br/>     Öffentliche void UpdateDateTime (Index von Int, java.sql.Timestamp X) <br/><br/> Öffentliche void UpdateSmallDateTime (Index von Int, java.sql.Timestamp X) |Diese Methoden werden zur Unterstützung von Always Encrypted für die Daten Datentypen Money, Smallmoney, Uniqueidentifier, Datetime und Smalldatetime hinzugefügt. <br/><br/>Beachten Sie, dass die vorhandene updateTimestamp()-Methode zum Aktualisieren von verschlüsselten datetime2-Spalten verwendet wird. Verwenden Sie für verschlüsselte Datetime und Smalldatetime-Spalten die neuen Methoden updateDateTime() und updateSmallDateTime() ein.|
|Öffentliche void UpdateBoolean (Int Index, booleschen X, booleschen ForceEncrypt)  <br/><br/>  Öffentliche void UpdateByte ("Int Index", "Byte" x "," boolean ForceEncrypt ")  <br/><br/>  Öffentliche void UpdateShort (Int Index, kurze X, booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateInt ("Int Index", "Int x, booleschen ForceEncrypt")   <br/><br/>  Öffentliche void UpdateLong (Int Index, lange X, booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateFloat ("Int Index", "Float" X "," booleschen ForceEncrypt ")   <br/><br/> Öffentliche void UpdateDouble (Int Index, doppelte X, booleschen ForceEncrypt)   <br/><br/> Öffentliche void UpdateMoney (Int Index, BigDecimal x, booleschen ForceEncrypt)   <br/><br/>  Öffentliche void UpdateMoney (Zeichenfolge Spaltenname, BigDecimal x, booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateSmallMoney (Int Index, BigDecimal x, booleschen ForceEncrypt)   <br/><br/>  Öffentliche void UpdateSmallMoney (Zeichenfolge Spaltenname, BigDecimal x, booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateBigDecimal (Int Index BigDecimal x "," ganze Zahl mit einfacher Genauigkeit, Skalierung für ganze Zahl, boolescher ForceEncrypt)   <br/><br/>  Öffentliche void UpdateString (Int "ColumnIndex", String StringValue, booleschen ForceEncrypt)  <br/><br/>  Öffentliche void UpdateNString (Int "ColumnIndex", String Nzeichenfolge, booleschen ForceEncrypt)  <br/><br/>  Öffentliche void UpdateNString (ColumnLabel der Zeichenfolge, Zeichenfolge Nzeichenfolge, booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateBytes ("Int Index", "Byte X[]", "boolean ForceEncrypt")   <br/><br/>  Öffentliche void UpdateDate (Int Index, java.sql.Date, x, booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateTime (Index von Int, java.sql.Time x "," ganze Zahl Skalierung, booleschen ForceEncrypt)   <br/><br/> Öffentliche void UpdateTimestamp (Index von Int, java.sql.Timestamp, Int-Skalierung x booleschen ForceEncrypt)   <br/><br/> Öffentliche void UpdateDateTime (Index von Int, java.sql.Timestamp x "," ganze Zahl Skalierung, booleschen ForceEncrypt)   <br/><br/> Öffentliche void UpdateSmallDateTime (Index von Int, java.sql.Timestamp x "," ganze Zahl Skalierung, booleschen ForceEncrypt)   <br/><br/>  Öffentliche void UpdateDateTimeOffset (Int Index "Microsoft.SQL.DateTimeOffset" dar, x, Skalierung für ganze Zahl, boolescher ForceEncrypt)  <br/><br/> Öffentliche void UpdateUniqueIdentifier (Index Int, String, boolean ForceEncrypt x)    <br/><br/>  Öffentliche void UpdateObject (Int Index, Objekt X, Int mit einfacher Genauigkeit, Skalierung von Int, boolean ForceEncrypt)  <br/><br/>  Öffentliche void UpdateObject (Int Index, Objekt Obj, SQLType TargetSqlType, Int skalieren, booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateBoolean (ColumnName der Zeichenfolge, boolescher X, booleschen ForceEncrypt)    <br/><br/>  Öffentliche void UpdateByte (Zeichenfolge ColumnName, Byte, x, booleschen ForceEncrypt)  <br/><br/>  Öffentliche void UpdateShort (Zeichenfolge ColumnName, kurze X, booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateInt (Zeichenfolge ColumnName, Int x, booleschen ForceEncrypt)   <br/><br/>   Öffentliche void UpdateLong (Zeichenfolge ColumnName, lange X, booleschen ForceEncrypt) <br/><br/>  Öffentliche void UpdateFloat (Zeichenfolge ColumnName, "float" X, booleschen ForceEncrypt)  <br/><br/>  Öffentliche void UpdateDouble (Zeichenfolge ColumnName, doppelte X, booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateBigDecimal (Zeichenfolge Spaltenname, BigDecimal x, booleschen ForceEncrypt)   <br/><br/>  Öffentliche void UpdateBigDecimal (Zeichenfolge ColumnName, BigDecimal x "," ganze Zahl mit einfacher Genauigkeit, Skalierung für ganze Zahl, boolescher ForceEncrypt)  <br/><br/> Öffentliche void UpdateString (Spaltenname Zeichenfolge, Zeichenfolge, boolescher ForceEncrypt x)   <br/><br/>  Öffentliche void UpdateBytes (Zeichenfolge ColumnName, Byte X[], booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateDate (Zeichenfolge ColumnName, java.sql.Date, x, booleschen ForceEncrypt)   <br/><br/>  Öffentliche void UpdateTime (Zeichenfolge ColumnName, java.sql.Time, x, Int Skalierung booleschen ForceEncrypt)  <br/><br/>  Öffentliche void UpdateTimestamp (Zeichenfolge ColumnName, java.sql.Timestamp, Int-Skalierung x booleschen ForceEncrypt)  <br/><br/> Öffentliche void UpdateDateTime (Zeichenfolge ColumnName, java.sql.Timestamp, Int-Skalierung x booleschen ForceEncrypt)   <br/><br/>  Öffentliche void UpdateSmallDateTime (Zeichenfolge ColumnName, java.sql.Timestamp, Int-Skalierung x booleschen ForceEncrypt)  <br/><br/>  Öffentliche void UpdateDateTimeOffset (Zeichenfolge ColumnName, "Microsoft.SQL.DateTimeOffset" dar, x, Int Skalierung booleschen ForceEncrypt)  <br/><br/>  Öffentliche void UpdateUniqueIdentifier (Spaltenname Zeichenfolge, Zeichenfolge, boolescher ForceEncrypt x)<br/><br/>Öffentliche void UpdateObject (Zeichenfolge ColumnName, Objekt X, Int mit einfacher Genauigkeit, Skalierung von Int, boolean ForceEncrypt)<br/><br/>Öffentliche void UpdateObject (ColumnName der Zeichenfolge, Objekt Obj, SQLType TargetSqlType, Int skalieren, booleschen ForceEncrypt)|Aktualisieren Sie die angegebene Spalte, auf den angegebenen Java-Wert.<br/><br/>Wenn der boolesche ForceEncrypt festgelegt ist, auf "true", die Spalte wird nur festgelegt, wenn er verschlüsselt ist, und Always Encrypted, für die Verbindung oder bei der Anweisung aktiviert ist.<br/><br/>Wenn der boolesche ForceEncrypt auf "false" festgelegt ist, wird nicht erzwingen der Treiber der Verschlüsselung auf Parameter.|

  
Neue Typen in **microsoft.sql.Types** Klasse
|Name|und Beschreibung|  
|----------|-----------------|  
|"DATETIME", "SMALLDATETIME", "MONEY", "SMALLMONEY", "GUID|Verwenden Sie diese Typen als die Ziel-SQL-Datentypen beim Senden von Parameterwerten, die **verschlüsselte** Datetime, Smalldatetime, Money, Smallmoney, Uniqueidentifier-Spalten, die mit setObject()/updateObject()-API-Methoden.|  
  
  
 **Sqlserverstatementcolumnencryptionsetting darf-Enumeration**  
  
 Gibt an, wie Daten werden gesendet und empfangen beim Lesen und Schreiben von verschlüsselten Spalten. Je nach spezifischer Abfrage kann Auswirkungen auf die Leistung reduziert werden, indem Sie umgehen, die Always Encrypted-Clienttreiber zu verarbeiten, wenn nicht verschlüsselte Spalten verwendet werden. Beachten Sie, dass diese Einstellungen können nicht verwendet werden, um Verschlüsselung zu umgehen und den Zugriff auf Klartextdaten.  
  
 **Syntax**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Elemente**  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|UseConnectionSetting|Gibt an, dass der Befehl die Always Encrypted-Einstellung in der Verbindungszeichenfolge standardmäßig sollte.|  
|Aktiviert|Aktiviert die grundsätzliche Verschlüsselung für die Abfrage.|  
|ResultSetOnly|Gibt an, dass nur die Ergebnisse des Befehls von der Routine Always Encrypted im Treiber verarbeitet werden sollen. Verwenden Sie diesen Wert, wenn der Befehl keine Parameter enthält, die eine Verschlüsselung erfordern.|  
|Disabled|Deaktiviert die grundsätzliche Verschlüsselung für die Abfrage.|  
  
 Die Einstellung der Anweisung für AE ist der SQLServerConnection-Klasse und der SQLServerConnectionPoolProxy-Klasse hinzugefügt. Die folgenden Methoden in diesen Klassen werden mit der neuen Einstellung überladen.  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|Öffentliche Anweisung CreateStatement (Int nType, nConcur von Int, Int StatementHoldability, sqlserverstatementcolumnencryptionsetting darf StmtColEncSetting)|Erstellt ein Statement-Objekt, das ResultSet-Objekte mit der angegebenen Typs, die Parallelität, die holdability-Eigenschaft und die spaltenverschlüsselungseinstellung generiert.|  
|Öffentliche CallableStatement PrepareCall (Zeichenfolge Sql, Int nType, nConcur von Int, Int StatementHoldability, sqlserverstatementcolumnencryptionsetting darf StmtColEncSetiing)|Erstellt eine CallableStatement-Objekt mit bestimmten Column Encryption Setting, die ResultSet-Objekte mit den angegebenen Typ, Parallelität und Haltbarkeit generiert wird.|  
|Öffentliche "PreparedStatement" PrepareStatement ("Zeichenfolge-Sql", "Int AutogeneratedKeys", "sqlserverstatementcolumnencryptionsetting darf StmtColEncSetting")|Erstellt eine "PreparedStatement"-Objekt mit bestimmten Column Encryption Setting, das automatisch generierte Schlüssel abrufen kann.|  
|Öffentliche "PreparedStatement" PrepareStatement (Zeichenfolge Sql, String [] ColumnNames sqlserverstatementcolumnencryptionsetting darf StmtColEncSetting)|Erstellt eine "PreparedStatement"-Objekt mit bestimmten Column Encryption Setting, die ResultSet-Objekte mit den angegebenen Spaltennamen generiert wird.|  
|Öffentliche "PreparedStatement" PrepareStatement (Zeichenfolge Sql, Int [] ColumnIndexes, sqlserverstatementcolumnencryptionsetting darf stmtColEncSetting|Erstellt eine "PreparedStatement"-Objekt mit bestimmten Column Encryption Setting, die ResultSet-Objekte mit der angegebenen Spaltenindizes generieren.|  
|Öffentliche "PreparedStatement" PrepareStatement (Zeichenfolge Sql, Int nType, nConcur von Int, Int nHold, sqlserverstatementcolumnencryptionsetting darf StmtColEncSetting)|Erstellt eine "PreparedStatement"-Objekt mit bestimmten Column Encryption Setting, die ResultSet-Objekte mit den angegebenen Typ, Parallelität und Haltbarkeit generiert wird.|  
  
> [!NOTE]  
>  Wenn Always Encrypted für eine Abfrage deaktiviert ist, und die Abfrage enthält Parameter, die verschlüsselte (Parameter) sein, die den verschlüsselten Spalten entsprechen müssen, wird die Abfrage fehl.  
>   
>  Wenn Always Encrypted für eine Abfrage deaktiviert ist, und die Abfrage gibt Ergebnisse aus verschlüsselten Spalten zurück, gibt die Abfrage verschlüsselte Werte zurück. Die verschlüsselten Werte müssen den Varbinary-Datentyp.  
  
 ## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden von „Immer verschlüsselt“ mit dem JDBC-Treiber](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

