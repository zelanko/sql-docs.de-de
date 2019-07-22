---
title: Verwenden von Always Encrypted mit den PHP-Treibern für SQL Server | Microsoft-Dokumentation
ms.date: 01/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
manager: v-mabarw
ms.openlocfilehash: 08165bf0f60265e34f6b8022fd00e11dda47f672
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68258639"
---
# <a name="using-always-encrypted-with-the-php-drivers-for-sql-server"></a>Verwenden von Always Encrypted mit den PHP-Treibern für SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="applicable-to"></a>Anwendbar auf
 -   Microsoft-Treiber 5.2 für PHP für SQL Server
 
## <a name="introduction"></a>Einführung

Dieser Artikel enthält Informationen zum Entwickeln von PHP-Anwendungen mithilfe von [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und der [Microsoft-Treiber für PHP für SQL Server](../../connect/php/Microsoft-php-driver-for-sql-server.md).

Always Encrypted ermöglicht Clientanwendungen das Verschlüsseln von vertraulichen Daten in einer Weise, dass weder die Daten noch die Verschlüsselungsschlüssel zu irgendeinem Zeitpunkt gegenüber SQL Server oder Azure SQL-Datenbank offengelegt werden. Ein Treiber, bei dem Always Encrypted aktiviert ist, z. B. ODBC Driver for SQL Server, ver- und entschlüsselt sensible Daten in der Clientanwendung. Der Treiber ermittelt automatisch, welche Abfrageparameter vertraulichen Datenbankspalten (mit Always Encrypted geschützt) entsprechen. Die Werte dieser Parameter werden dann vor der Übergabe an SQL Server oder Azure SQL-Datenbank verschlüsselt. Auf ähnliche Weise entschlüsselt der Treiber die Daten transparent, die von verschlüsselten Datenbankspalten in Abfrageergebnissen empfangen werden. Weitere Informationen finden Sie unter [Immer verschlüsselt (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Die PHP-Treiber für SQL Server verwenden den ODBC-Treiber für die SQL Server, um sensible Daten zu verschlüsseln.

## <a name="prerequisites"></a>Voraussetzungen

 -   Konfigurieren Sie Always Encrypted in Ihrer Datenbank. Diese Konfiguration umfasst die Bereitstellung von Always Encrypted-Schlüsseln und die Einrichtung der Verschlüsselung für ausgewählte Datenbankspalten. Wenn Sie nicht bereits über eine Datenbank verfügen, für die Always Encrypted konfiguriert ist, befolgen Sie die Anweisungen in [Erste Schritte mit Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). Insbesondere sollte Ihre Datenbank die Metadatendefinitionen für einen Spaltenhauptschlüssel (Column Master Key, CMK), einen Spaltenverschlüsselungsschlüssel (Column Encryption Key, CEK) und eine Tabelle mit mindestens einer Spalte enthalten, die mit diesem CEK verschlüsselt ist.
 -   Stellen Sie sicher, dass der ODBC-Treiber für SQL Server Version 17 oder höher auf dem Entwicklungs Computer installiert ist. Weitere Informationen finden Sie unter [ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="enabling-always-encrypted-in-a-php-application"></a>Aktivieren von Always Encrypted in einer PHP-Anwendung

Die einfachste Möglichkeit zum Aktivieren der Verschlüsselung von Parametern, die auf verschlüsselte Spalten ausgerichtet sind, und der Entschlüsselung von Abfrageergebnissen besteht im Festlegen des Werts für die Verbindungszeichenfolge `ColumnEncryption` auf `Enabled`. Im folgenden finden Sie Beispiele für das Aktivieren von Always Encrypted in den sqlsrv-und PDO_SQLSRV-Treibern:

SQLSRV:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled");
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

Das Aktivieren von Always Encrypted für eine erfolgreiche Verschlüsselung oder Entschlüsselung ist nicht ausreichend. Sie müssen außerdem Folgendes sicherstellen:
 -   Die Anwendung verfügt über die Datenbankberechtigungen VIEW ANY COLUMN MASTER KEY DEFINITION und VIEW ANY COLUMN ENCRYPTION KEY DEFINITION, die für den Zugriff auf die Metadaten in der Datenbank über Always Encrypted-Schlüssel erforderlich sind. Einzelheiten hierzu finden Sie unter [Datenbankberechtigungen](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
 -   Die Anwendung muss auf den CMK zugreifen können, der die CEKs für die abgefragten verschlüsselten Spalten schützt. Diese Anforderung ist abhängig vom Schlüsselspeicher Anbieter, der den CMK speichert. Weitere Informationen finden Sie im Abschnitt [Arbeiten mit Spaltenhauptschlüsselspeichern](#working-with-column-master-key-stores).

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Abrufen und Ändern von Daten in verschlüsselten Spalten

Nachdem Sie Always Encrypted für eine Verbindung aktiviert haben, können Sie standardmäßige sqlsrv-APIs (siehe [Referenz zur sqlsrv-Treiber-API](../../connect/php/sqlsrv-driver-api-reference.md)) oder PDO_SQLSRV-APIs (siehe Referenz zur PDO_SQLSRV-Treiber- [API](../../connect/php/pdo-sqlsrv-driver-reference.md)) verwenden, um Daten in verschlüsselten Daten Bank Spalten abzurufen oder zu ändern. Wenn Ihre Anwendung über die erforderlichen Datenberechtigungen verfügt und auf den Spaltenhauptschlüssel zugreifen kann, verschlüsselt der Treiber alle Abfrageparameter für verschlüsselte Spalten und entschlüsselt Daten, die aus verschlüsselten Spalten abgefragt wurden. Dieser Vorgang erfolgt in der Anwendung transparent, als ob die Spalten nicht verschlüsselt wären.

Wenn Always Encrypted nicht aktiviert ist, tritt bei Abfragen mit Parametern, die auf verschlüsselte Spalten ausgerichtet sind, ein Fehler auf. Daten können weiterhin aus verschlüsselten Spalten abgerufen werden, solange die Abfrage keine Parameter für verschlüsselte Spalten enthält. Der Treiber versucht jedoch nicht, die Daten zu entschlüsseln. Daher erhält die Anwendung die verschlüsselten Binärdaten (als Bytearrays).

Die folgende Tabelle fasst das Verhalten von Abfragen in Abhängigkeit davon zusammen, ob Always Encrypted aktiviert ist:

|Abfragemerkmal|Always Encrypted ist aktiviert und die Anwendung kann auf die Schlüssel und Schlüsselmetadaten zugreifen.|Always Encrypted ist aktiviert und die Anwendung kann nicht auf die Schlüssel oder Schlüsselmetadaten zugreifen.|Always Encrypted ist deaktiviert|
|---|---|---|---|
|Parameter für verschlüsselte Spalten|Parameterwerte werden transparent verschlüsselt.|Fehler|Fehler|
|Daten von verschlüsselten Spalten ohne Parameter abrufen, die auf verschlüsselte Spalten ausgerichtet sind.|Ergebnisse von verschlüsselten Spalten werden transparent entschlüsselt. Die Anwendung erhält Klartextspaltenwerte. |Fehler|Ergebnisse von verschlüsselten Spalten werden nicht entschlüsselt. Die Anwendung erhält verschlüsselte Werte als Bytearrays.|
 
Die folgenden Beispiele veranschaulichen das Abrufen und Ändern von Daten in verschlüsselten Spalten. Dabei wird eine Tabelle mit dem folgenden Schema angenommen: Die Spalten „SSN“ und „BirthDate“ werden verschlüsselt.
```
CREATE TABLE [dbo].[Patients](
 [PatientId] [int] IDENTITY(1,1),
 [SSN] [char](11) COLLATE Latin1_General_BIN2
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL,
 [BirthDate] [date]
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

### <a name="data-insertion-example"></a>Beispiel für das Einfügen von Daten

In den folgenden Beispielen wird veranschaulicht, wie die sqlsrv-und PDO_SQLSRV-Treiber verwendet werden, um eine Zeile in die Patienten Tabelle einzufügen. Beachten Sie die folgenden Punkte:
 -   Es erfolgt keine spezielle Verschlüsselung im Beispielcode. Der Treiber erkennt und verschlüsselt automatisch die Werte der Parameter „SSN“ und „BirthDate“ für verschlüsselte Spalten. Durch diesen Mechanismus wird die Verschlüsselung für die Anwendung transparent.
 -   Die in die Datenbankspalten eingefügten Werte, einschließlich der verschlüsselten Spalten, werden als gebundene Parameter übergeben. Während die Verwendung von Parametern optional ist, wenn Werte an nicht verschlüsselte Spalten gesendet werden (obwohl es dringend empfohlen wird, da es dabei hilft, eine Einschleusung von SQL-Befehlen zu verhindern), ist sie für Werte erforderlich, die auf verschlüsselte Spalten ausgerichtet sind. Werden die in die Spalten „SSN“ oder „BirthDate“ eingefügten Werte als Literale übergeben, die in die Abfrageanweisung eingebettet sind, tritt ein Fehler auf, da der Treiber nicht versucht, Literale in Abfragen zu verschlüsseln oder anderweitig zu verarbeiten. Daher würde der Server sie zurückweisen, da sie mit den verschlüsselten Spalten inkompatibel sind.
 -   Beim Einfügen von Werten mithilfe von Bindungs Parametern muss ein SQL-Typ, der mit dem Datentyp der Ziel Spalte identisch ist oder dessen Konvertierung in den Datentyp der Ziel Spalte unterstützt wird, an die Datenbank übermittelt werden. Diese Anforderung liegt daran, dass Always Encrypted wenige Typkonvertierungen unterstützt (Weitere Informationen finden Sie unter [Always encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)). Die beiden PHP-Treiber sqlsrv und PDO_SQLSRV verfügen jeweils über einen Mechanismus, mit dessen Hilfe der Benutzer den SQL-Typ des Werts bestimmen kann. Daher muss der Benutzer den SQL-Typ nicht explizit angeben.
  -   Für den sqlsrv-Treiber verfügt der Benutzer über zwei Optionen:
   -   Setzen Sie den PHP-Treiber ein, um den richtigen SQL-Typ zu ermitteln und festzulegen. In diesem Fall muss der Benutzer und `sqlsrv_prepare` `sqlsrv_execute` verwenden, um eine parametrisierte Abfrage auszuführen.
   -   Legen Sie den SQL-Typ explizit fest.
  -   Für den PDO_SQLSRV-Treiber verfügt der Benutzer nicht über die Option, den SQL-Typ eines Parameters explizit festzulegen. Der PDO_SQLSRV-Treiber unterstützt den Benutzer beim Binden eines Parameters automatisch beim Festlegen des SQL-Typs.
 -   Damit die Treiber den SQL-Typ bestimmen können, gelten einige Einschränkungen:
  -   SQLSRV-Treiber:
   -   Wenn der Benutzer möchte, dass der Treiber die SQL-Typen für die verschlüsselten Spalten bestimmt, muss der `sqlsrv_prepare` Benutzer `sqlsrv_execute`und verwenden.
   -   Wenn `sqlsrv_query` bevorzugt wird, ist der Benutzer für die Angabe der SQL-Typen für alle Parameter verantwortlich. Der angegebene SQL-Typ muss die Zeichen folgen Länge für Zeichen folgen Typen sowie die Skalierung und Genauigkeit für Dezimal Typen enthalten.
  -   PDO_SQLSRV-Treiber:
   -   Das Anweisungs `PDO::SQLSRV_ATTR_DIRECT_QUERY` Attribut wird in einer parametrisierten Abfrage nicht unterstützt.
   -   Das Anweisungs `PDO::ATTR_EMULATE_PREPARES` Attribut wird in einer parametrisierten Abfrage nicht unterstützt.
   
SQLSRV-Treiber und [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel;
$birthDate = "1996-10-19";
$params = array($ssn, $firstName, $lastName, $birthDate);
// during sqlsrv_prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = sqlsrv_prepare($conn, $query, $params);
sqlsrv_execute($stmt);
```

SQLSRV-Treiber und [sqlsrv_query](../../connect/php/sqlsrv-query.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel";
$birthDate = "1996-10-19";
// need to provide the SQL types for ALL parameters  
// note the SQL types (including the string length) have to be the same at the column definition
$params = array(array(&$ssn, null, null, SQLSRV_SQLTYPE_CHAR(11)),
                array(&$firstName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$lastName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$birthDate, null, null, SQLSRV_SQLTYPE_DATE));
sqlsrv_query($conn, $query, $params);
```

PDO_SQLSRV Driver und [PDO::p repare](../../connect/php/pdo-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Able";
$birthDate = "1996-10-19";
// during PDO::prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
$stmt->bindParam(2, $firstName);
$stmt->bindParam(3, $lastName);
$stmt->bindParam(4, $birthDate);
$stmt->execute();
```

### <a name="plaintext-data-retrieval-example"></a>Beispiel für das Abrufen von Klartextdaten

Die folgenden Beispiele veranschaulichen das Filtern von Daten auf der Grundlage verschlüsselter Werte und das Abrufen von Klartext-Daten aus verschlüsselten Spalten mithilfe der sqlsrv-und PDO_SQLSRV-Treiber. Beachten Sie die folgenden Punkte:
 -   Der in der WHERE-Klausel zum Filtern der Spalte „SSN“ verwendete Wert muss mit dem bind-Parameter übergeben werden, damit ihn der Treiber vor dem Senden an die Datenbank transparent verschlüsseln kann.
 -   Beim Ausführen einer Abfrage mit gebundenen Parametern bestimmt der PHP-Treiber automatisch den SQL-Typ für den Benutzer, es sei denn, der Benutzer gibt den SQL-Typ explizit an, wenn der sqlsrv-Treiber verwendet wird.
 -   Alle Werte werden vom Programm als Klartext ausgegeben, da der Treiber die aus den Spalten „SSN“ und „BirthDate“ abgerufenen Daten transparent entschlüsselt.
 
Hinweis: Abfragen können Übereinstimmungsvergleiche für verschlüsselte Spalten nur bei deterministischer Verschlüsselung ausführen. Weitere Informationen finden Sie im Abschnitt [Auswählen der deterministischen oder zufälligen Verschlüsselung](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = sqlsrv_prepare($conn, $query, array(&$ssn));
// during sqlsrv_execute, the driver encrypts the ssn value and passes it to the database
sqlsrv_execute($stmt);
// fetch like usual
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
// during PDOStatement::execute, the driver encrypts the ssn value and passes it to the database
$stmt->execute();
// fetch like usual
$row = $stmt->fetch();
```

### <a name="ciphertext-data-retrieval-example"></a>Beispiel für das Abrufen von Chiffretextdaten

Wenn Always Encrypted nicht aktiviert ist, können Abfragen weiterhin Daten aus verschlüsselten Spalten abrufen, so lange die Abfrage keine Parameter für verschlüsselte Spalten enthält.

In den folgenden Beispielen wird das Abrufen von Binär verschlüsselten Daten aus verschlüsselten Spalten mithilfe der sqlsrv-und PDO_SQLSRV-Treiber veranschaulicht. Beachten Sie die folgenden Punkte:
 -   Da Always Encrypted in der Verbindungszeichenfolge nicht aktiviert ist, gibt die Abfrage verschlüsselte Werte von „SSN“ und „BirthDate“ als Bytearrays zurück (das Programm konvertiert die Werte in Zeichenfolgen).
 -   Eine Abfrage, die Daten aus verschlüsselten Spalten mit deaktiviertem Always Encrypted abruft, kann Parameter aufweisen, so lange keiner der Parameter auf eine verschlüsselte Spalte ausgerichtet ist. In der folgenden Abfrage wird nach der Spalte „LastName“ gefiltert, die in der Datenbank nicht verschlüsselt ist. Wenn in der Abfrage nach „SSN“ oder „BirthDate“ gefiltert wird, würde ein Fehler auftreten.
 
SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = sqlsrv_prepare($conn, $query, array(&$lastName));
sqlsrv_execute($stmt);
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $lastName);
$stmt->execute();
$row = $stmt->fetch();
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Vermeiden allgemeiner Probleme beim Abfragen von verschlüsselter Spalten

In diesem Abschnitt werden die allgemeinen Fehlerkategorien bei der Abfrage verschlüsselter Spalten über PHP-Anwendungen sowie einige Grundsätze zum Vermeiden dieser Fehler.

#### <a name="unsupported-data-type-conversion-errors"></a>Konvertierungsfehler durch nicht unterstützte Datentypen

Always Encrypted unterstützt einige Konvertierungen für verschlüsselte Datentypen. Eine ausführliche Liste der unterstützten Typkonvertierungen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Gehen Sie wie folgt vor, um Fehler bei Konvertierung des Datentyps zu vermeiden:
 -   Wenn der sqlsrv-Treiber mit `sqlsrv_prepare` und `sqlsrv_execute` dem SQL-Typ verwendet wird, wird zusammen mit der Spaltengröße und der Anzahl der Dezimalziffern des Parameters automatisch festgelegt.
 -   Wenn Sie den PDO_SQLSRV-Treiber verwenden, um eine Abfrage auszuführen, wird der SQL-Typ mit der Spaltengröße und der Anzahl der Dezimalziffern des Parameters ebenfalls automatisch festgelegt.
 -   Wenn Sie den sqlsrv-Treiber `sqlsrv_query` mit verwenden, um eine Abfrage auszuführen:
  -   Entweder ist der SQL-Typ des Parameters identisch mit dem Typ der Zielspalte oder die Konvertierung vom SQL-Typ in den Typ der Spalte wird unterstützt.
  -   Die Genauigkeit und Dezimalstellenanzahl von Parametern, die auf Spalten der SQL Server-Datentypen `decimal` und `numeric` ausgerichtet sind, ist mit der für die Zielspalte konfigurierten Genauigkeit und Dezimalstellenanzahl identisch.
  -   Die Genauigkeit von Parametern, die auf Spalten der SQL Server-Datentypen `datetime2`, `datetimeoffset` oder `time` ausgerichtet sind, ist in Abfragen, in denen die Zielspalte geändert wird, nicht größer als die Genauigkeit für die Zielspalte.
 -   Verwenden Sie keine PDO_SQLSRV-Anweisungs `PDO::ATTR_EMULATE_PREPARES` Attribute `PDO::SQLSRV_ATTR_DIRECT_QUERY` oder in einer parametrisierten Abfrage.
 
#### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Fehler aufgrund der Übergabe von Klartext anstelle von verschlüsselten Werten

Jeder Wert für verschlüsselte Spalten muss vor dem Senden an den Server verschlüsselt werden. Ein Versuch, einen Klartextwert einzufügen, zu ändern oder nach einem Klartextwert für eine verschlüsselte Spalte zu filtern, führt zu einem Fehler. Stellen Sie Folgendes sicher, um solche Fehler zu vermeiden:
 -   Always Encrypted aktiviert ist (legen Sie in der Verbindungs Zeichenfolge `ColumnEncryption` das `Enabled`-Schlüsselwort auf fest).
 -   Sie verwenden Bind-Parameter zum Senden von Daten, die auf verschlüsselte Spalten ausgerichtet sind. Das folgende Beispiel zeigt eine Abfrage, die fälschlicherweise nach einem literalen/Konstanten in einer verschlüsselten Spalte (SSN) filtert:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

## <a name="controlling-performance-impact-of-always-encrypted"></a>Kontrollieren der Auswirkungen von Always Encrypted auf die Leistung

Da Always Encrypted eine clientseitige Verschlüsselungstechnologie ist, werden die meisten Leistungseinbußen auf der Clientseite und nicht in der Datenbank beobachtet. Neben den Kosten für Verschlüsselungs- und Entschlüsselungsvorgänge ergeben sich die folgenden anderen Quellen für Leistungseinbußen auf der Clientseite:
 -   Zusätzliche Roundtrips zur Datenbank zum Abrufen von Metadaten für Abfrageparameter.
 -   Aufrufe an einen Spaltenhauptschlüsselspeicher für den Zugriff auf einen Spaltenhauptschlüssel.
 
### <a name="round-trips-to-retrieve-metadata-for-query-parameters"></a>Roundtrips zum Abrufen von Metadaten für Abfrageparameter

Wenn Always Encrypted für eine Verbindung aktiviert ist, ruft der ODBC-Treiber standardmäßig [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) für jede parametrisierte Abfrage auf, wobei die Abfrageanweisung (ohne Parameterwerte) an SQL Server übergeben wird. Die Abfrageanweisung wird von dieser gespeicherten Prozedur analysiert, um zu ermitteln, ob Parameter verschlüsselt werden müssen. In diesem Fall werden verschlüsselungsbezogene Informationen für jeden Parameter zurückgegeben, die der Treiber dann verschlüsseln kann.

Da der Benutzer mit den PHP-Treibern einen Parameter in einer vorbereiteten Anweisung binden kann, ohne den SQL-Typ bereitzustellen, wird beim Binden eines Parameters in einer Always Encrypted aktivierten Verbindung die PHP-Treiber [SQLDescribeParam](../../odbc/reference/syntax/sqldescribeparam-function.md) für den Parameter aufrufen, um den SQL-Typ abzurufen. Spaltengröße und Dezimalziffern. Die Metadaten werden dann zum Aufrufen von [SQLBindParameter]( ../../odbc/reference/syntax/sqlbindparameter-function.md)verwendet. Diese zusätzlichen `SQLDescribeParam` Anrufe erfordern keine zusätzlichen Roundtrips zur Datenbank, da der ODBC-Treiber die Informationen bereits auf der Clientseite gespeichert hat, als `sys.sp_describe_parameter_encryption` aufgerufen wurde.

Das oben beschriebene Verhalten stellt einen hohen Grad an Transparenz für die Clientanwendung sicher. Außerdem muss der Anwendungsentwickler nicht beachten, welche Abfragen auf verschlüsselte Spalten zugreifen, so lange die Werte für verschlüsselte Spalten in Parametern an den Treiber übergeben werden.

Im Gegensatz zum ODBC-Treiber für SQL Server wird das Aktivieren von Always Encrypted auf der Anweisung/Abfrage Ebene in den PHP-Treibern noch nicht unterstützt. 

### <a name="column-encryption-key-caching"></a>Zwischenspeicherung von Spaltenverschlüsselungsschlüsseln

Der Treiber speichert die Spaltenverschlüsselungsschlüssel (CEKs) unverschlüsselt im Zwischenspeicher, um die Anzahl der Aufrufe an einen Spaltenhauptschlüsselspeicher zum Entschlüsseln von CEKs zu verringern. Nach dem Erhalt des verschlüsselten CEK (ECEK) aus den Datenbankmetadaten versucht der Treiber zunächst, den unverschlüsselten CEK zu finden, der dem verschlüsselten Schlüsselwert im Cache entspricht. Der Treiber ruft den Schlüsselspeicher, der den CMK enthält, nur auf, wenn der entsprechende CEK im Klartext im Cache nicht gefunden werden kann.

Hinweis: Beim ODBC-Treiber für SQL Server werden die Einträge im Cache nach einem Zeitlimit von zwei Stunden entfernt. Dieses Verhalten bedeutet, dass der Treiber den Schlüsselspeicher für einen bestimmten ECEK während der Lebensdauer der Anwendung oder alle zwei Stunden (je nachdem, welches Intervall kürzer ist) nur einmal kontaktiert.

## <a name="working-with-column-master-key-stores"></a>Arbeiten mit Spaltenhauptschlüsselspeichern

Der Treiber benötigt zum Verschlüsseln oder Entschlüsseln von Daten einen CEK, der für die Zielspalte konfiguriert ist. CEKs werden in verschlüsselter Form (als ECEKs) in den Datenbankmetadaten gespeichert. Jeder CEK besitzt einen entsprechenden CMK, mit dem er verschlüsselt wurde. In den [Datenbankmetadaten](../../t-sql/statements/create-column-master-key-transact-sql.md) wird nicht der CMK selbst gespeichert, sondern nur der Name des Schlüsselspeichers sowie Informationen zur Suche nach dem CMK.

Wenn der Treiber den Klartextwert eines ECEK abrufen möchten, benötigt er zunächst die Metadaten für den CEK und den entsprechenden CMK. Mit diesen Informationen kontaktiert er den Schlüsselspeicher, der den CMK enthält, und fordert die Entschlüsselung des ECEK an. Die Kommunikation zwischen Treiber und Schlüsselspeicher erfolgt über einen Schlüsselspeicheranbieter.

Für Microsoft Driver 5.3.0 for PHP for SQL Server werden nur der Windows-Zertifikat Speicher Anbieter und Azure Key Vault unterstützt. Der andere Keystore-Anbieter, der vom ODBC-Treiber (Custom Keystore-Anbieter) unterstützt wird, wird noch nicht unterstützt.

### <a name="using-the-windows-certificate-store-provider"></a>Verwenden des Windows-Zertifikatspeicheranbieters

Unter Windows enthält ODBC Driver for SQL Server einen integrierten CMK-Speicheranbieter für den Windows-Zertifikatspeicher namens `MSSQL_CERTIFICATE_STORE`. (Dieser Anbieter ist nicht unter macOS oder Linux verfügbar.) Mit diesem Anbieter wird der CMK lokal auf dem Clientcomputer gespeichert, und es ist keine weitere Konfiguration durch die Anwendung erforderlich, um ihn mit dem Treiber zu verwenden. Die Anwendung muss jedoch auf das Zertifikat und den privaten Schlüssel im Speicher zugreifen können. Weitere Informationen finden Sie unter [Create and Store Column Master Keys (Always Encrypted)](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)(Erstellen und Speichern von Spaltenhauptschlüsseln (Always Encrypted)).

### <a name="using-azure-key-vault"></a>Verwenden von Azure Key Vault

Azure Key Vault bietet eine Möglichkeit zum Speichern von Verschlüsselungsschlüsseln, Kenn Wörtern und anderen Geheimnissen mit Azure und kann zum Speichern von Schlüsseln für Always Encrypted verwendet werden. Der ODBC-Treiber für SQL Server (Version 17 und höher) enthält einen integrierten Hauptschlüssel Speicher Anbieter für Azure Key Vault. Die folgenden Verbindungsoptionen behandeln die Azure Key Vault Konfiguration `KeyStoreAuthentication`: `KeyStorePrincipalId`, und `KeyStoreSecret`. 
 -   `KeyStoreAuthentication`kann einen von zwei möglichen Zeichen folgen Werten annehmen `KeyVaultPassword` : `KeyVaultClientSecret`und. Diese Werte steuern, welche Art von Authentifizierungs Anmelde Informationen mit den anderen beiden Schlüsselwörtern verwendet werden.
 -   `KeyStorePrincipalId`erfordert eine Zeichenfolge, die einen Bezeichner für das Konto darstellt, das auf den Azure Key Vault zugreifen möchte. 
     -   Wenn `KeyStoreAuthentication` `KeyStorePrincipalId` auf `KeyVaultPassword`festgelegt ist, muss der Name eines Azure ActiveDirectory-Benutzers sein.
     -   Wenn `KeyStoreAuthentication` `KeyStorePrincipalId` auf `KeyVaultClientSecret`festgelegt ist, muss eine Anwendungs Client-ID sein.
 -   `KeyStoreSecret`nimmt eine Zeichenfolge an, die einen geheimen Anmelde Informations Schlüssel darstellt. 
     -   Wenn `KeyStoreAuthentication` `KeyStoreSecret` auf `KeyVaultPassword`festgelegt ist, muss das Kennwort des Benutzers sein. 
     -   Wenn `KeyStoreAuthentication` `KeyStoreSecret` auf `KeyVaultClientSecret`festgelegt ist, muss dem Anwendungs Geheimnis entsprechen, das der Anwendungs Client-ID zugeordnet ist.

Alle drei Optionen müssen in der Verbindungs Zeichenfolge vorhanden sein, um Azure Key Vault zu verwenden. Außerdem `ColumnEncryption` muss auf `Enabled`festgelegt werden. Wenn `ColumnEncryption` auf`Disabled` festgelegt ist, aber die Azure Key Vault Optionen vorhanden sind, wird das Skript ohne Fehler fortgesetzt, es wird jedoch keine Verschlüsselung ausgeführt.

In den folgenden Beispielen wird gezeigt, wie Sie mithilfe von Azure Key Vault eine Verbindung mit SQL Server herstellen.

SQLSRV:

Verwenden eines Azure Active Directory Kontos:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultPassword", "KeyStorePrincipalId"=>$AADUsername, "KeyStoreSecret"=>$AADPassword);
$conn = sqlsrv_connect($server, $connectionInfo);
```
Verwenden der Client-ID und des geheimen Schlüssels einer Azure-Anwendung:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultClientSecret", "KeyStorePrincipalId"=>$applicationClientID, "KeyStoreSecret"=>$applicationClientSecret);
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV: Verwenden eines Azure Active Directory Kontos:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultPassword; KeyStorePrincipalId = $AADUsername; KeyStoreSecret = $AADPassword;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```
Verwenden der Client-ID und des geheimen Schlüssels einer Azure-Anwendung:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultClientSecret; KeyStorePrincipalId = $applicationClientID; KeyStoreSecret = $applicationClientSecret;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

## <a name="limitations-of-the-php-drivers-when-using-always-encrypted"></a>Einschränkungen des PHP-Treibers bei Verwendung von Always Encrypted

SQLSRV und PDO_SQLSRV:
 -   Linux/macOS unterstützt den Windows-Zertifikat Speicher Anbieter nicht
 -   Erzwingen von Parameterverschlüsselung
 -   Aktivieren von Always Encrypted auf Anweisungs Ebene 
 -   Bei Verwendung der Always Encrypted-Funktion und nicht-UTF8-Gebiets Schemas unter Linux und macOS (z. b. "en_US"). ISO-8859-1 ") das Einfügen von NULL-Daten oder einer leeren Zeichenfolge in eine verschlüsselte char (n)-Spalte funktioniert möglicherweise nicht, wenn die Codepage 1252 nicht auf Ihrem System installiert ist.
 
Nur sqlsrv:
 -   Verwenden `sqlsrv_query` von für Bindungs Parameter ohne Angabe des SQL-Typs
 -   Verwenden `sqlsrv_prepare` von zum Binden von Parametern in einem Batch von SQL-Anweisungen  
 
Nur PDO_SQLSRV:
 -   `PDO::SQLSRV_ATTR_DIRECT_QUERY`in einer parametrisierten Abfrage angegebenes Anweisungs Attribut
 -   `PDO::ATTR_EMULATE_PREPARE`in einer parametrisierten Abfrage angegebenes Anweisungs Attribut
 -   Binden von Parametern in einem Batch von SQL-Anweisungen
 
Die PHP-Treiber erben außerdem die Einschränkungen, die vom ODBC-Treiber für SQL Server und die Datenbank auferlegt werden. Weitere Informationen finden [Sie unter Einschränkungen des ODBC-Treibers bei Verwendung Always Encrypted](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) und [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#feature-details)Featuredetails.  
  
## <a name="see-also"></a>Weitere Informationen  
[Programmierhandbuch für den PHP-SQL-Treiber](../../connect/php/programming-guide-for-php-sql-driver.md)
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  
[API-Referenz für den PDO_SQLSRV-Treiber](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
