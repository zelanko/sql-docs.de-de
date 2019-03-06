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
manager: mbarwin
ms.openlocfilehash: 5c82c32922712b377fd732b6745b1761e9f32a82
ms.sourcegitcommit: afc0c3e46a5fec6759fe3616e2d4ba10196c06d1
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55890001"
---
# <a name="using-always-encrypted-with-the-php-drivers-for-sql-server"></a>Verwenden von Always Encrypted mit den PHP-Treibern für SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="applicable-to"></a>Anwendbar auf
 -   Microsoft-Treiber 5.2 für PHP für SQL Server
 
## <a name="introduction"></a>Einführung

Dieser Artikel enthält Informationen zum Entwickeln von PHP-Anwendungen mit [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und [PHP-Treiber für SQL Server](../../connect/php/Microsoft-php-driver-for-sql-server.md).

Always Encrypted ermöglicht Clientanwendungen das Verschlüsseln von vertraulichen Daten in einer Weise, dass weder die Daten noch die Verschlüsselungsschlüssel zu irgendeinem Zeitpunkt gegenüber SQL Server oder Azure SQL-Datenbank offengelegt werden. Ein Treiber, bei dem Always Encrypted aktiviert ist, z. B. ODBC Driver for SQL Server, ver- und entschlüsselt sensible Daten in der Clientanwendung. Der Treiber ermittelt automatisch, welche Abfrageparameter vertraulichen Datenbankspalten (mit Always Encrypted geschützt) entsprechen. Die Werte dieser Parameter werden dann vor der Übergabe an SQL Server oder Azure SQL-Datenbank verschlüsselt. Auf ähnliche Weise entschlüsselt der Treiber die Daten transparent, die von verschlüsselten Datenbankspalten in Abfrageergebnissen empfangen werden. Weitere Informationen finden Sie unter [Immer verschlüsselt (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Die PHP-Treiber für SQL Server nutzen Sie den ODBC-Treiber für SQL Server zum Verschlüsseln vertraulicher Daten.

## <a name="prerequisites"></a>Voraussetzungen

 -   Konfigurieren Sie Always Encrypted in Ihrer Datenbank. Diese Konfiguration umfasst die Bereitstellung von Always Encrypted-Schlüsseln und die Einrichtung der Verschlüsselung für ausgewählte Datenbankspalten. Wenn Sie nicht bereits über eine Datenbank verfügen, für die Always Encrypted konfiguriert ist, befolgen Sie die Anweisungen in [Erste Schritte mit Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). Insbesondere sollten Ihre Datenbank die Metadatendefinitionen für eine Zertifizierungsstelle (Column Master Key, CMK), (Spalte Encryption Key, CEK) und eine Tabelle mit einer oder mehreren Spalten, die mit diesem CEK verschlüsselt enthalten.
 -   Stellen Sie sicher, dass ODBC-Treiber für SQL Server, Version 17 oder höher auf dem Entwicklungscomputer installiert ist. Weitere Informationen finden Sie unter [ODBC-Treiber für SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="enabling-always-encrypted-in-a-php-application"></a>Aktivieren von "immer verschlüsselt" in einer PHP-Anwendung

Die einfachste Möglichkeit zum Aktivieren der Verschlüsselung von Parametern, die auf verschlüsselte Spalten ausgerichtet sind, und der Entschlüsselung von Abfrageergebnissen besteht im Festlegen des Werts für die Verbindungszeichenfolge `ColumnEncryption` auf `Enabled`. Es folgen Beispiele für die Aktivierung von Always Encrypted in die SQLSRV- und PDO_SQLSRV-Treiber:

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

Aktivieren von Always Encrypted reicht nicht aus, für die Verschlüsselung oder Entschlüsselung erfolgreich ausgeführt werden kann; Sie müssen auch sicherstellen, dass:
 -   Die Anwendung verfügt über die Datenbankberechtigungen VIEW ANY COLUMN MASTER KEY DEFINITION und VIEW ANY COLUMN ENCRYPTION KEY DEFINITION, die für den Zugriff auf die Metadaten in der Datenbank über Always Encrypted-Schlüssel erforderlich sind. Weitere Informationen finden Sie unter [Datenbankberechtigung](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
 -   Die Anwendung kann den CMK zugreifen, die die CEKs für die abgefragten verschlüsselte Spalten schützt. Diese Anforderung ist abhängig von den Schlüsselspeicheranbieter aus, in dem den CMK gespeichert. Weitere Informationen finden Sie unter [arbeiten mit Spaltenhauptschlüsselspeichern](#working-with-column-master-key-stores).

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Abrufen und Ändern von Daten in verschlüsselten Spalten

Nachdem Sie Always Encrypted für eine Verbindung aktiviert haben, können Sie standard-SQLSRV-APIs (finden Sie unter [SQLSRV-Treiber-API-Referenz](../../connect/php/sqlsrv-driver-api-reference.md)) oder PDO_SQLSRV-APIs (finden Sie unter [-API-Referenz zum Treiber PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)) zum Abrufen oder Ändern von Daten in verschlüsselten Datenbankspalten. Wenn Ihre Anwendung die erforderlichen Datenbankberechtigungen verfügt und kann auf den spaltenhauptschlüssel zugreifen, der Treiber verschlüsselt alle Abfrageparameter, die auf verschlüsselte Spalten ausgerichtet und Entschlüsseln von Daten aus verschlüsselten Spalten, die transparent zu verhält abgerufenen der Anwendung, als ob die Spalten nicht verschlüsselt wurden.

Wenn Always Encrypted nicht aktiviert ist, tritt bei Abfragen mit Parametern, die auf verschlüsselte Spalten ausgerichtet sind, ein Fehler auf. Daten können weiterhin aus verschlüsselten Spalten abgerufen werden, solange die Abfrage keine Parameter für verschlüsselte Spalten enthält. Allerdings versucht des Treibers Entschlüsselung nicht aus, und die Anwendung empfängt die verschlüsselte Binärdaten (als Bytearrays).

Die folgende Tabelle fasst das Verhalten von Abfragen in Abhängigkeit davon zusammen, ob Always Encrypted aktiviert ist:

|Abfragemerkmal|Always Encrypted ist aktiviert und die Anwendung kann auf die Schlüssel und Schlüsselmetadaten zugreifen.|Always Encrypted ist aktiviert und die Anwendung kann nicht auf die Schlüssel oder Schlüsselmetadaten zugreifen.|Always Encrypted ist deaktiviert|
|---|---|---|---|
|Parameter, die auf verschlüsselte Spalten ausgerichtet sind.|Parameterwerte werden transparent verschlüsselt.|Fehler|Fehler|
|Daten von verschlüsselten Spalten ohne Parameter abrufen, die auf verschlüsselte Spalten ausgerichtet sind.|Ergebnisse von verschlüsselten Spalten werden transparent entschlüsselt. Die Anwendung erhält klartextwerte der Spalte. |Fehler|Ergebnisse von verschlüsselten Spalten werden nicht entschlüsselt. Die Anwendung erhält verschlüsselte Werte als Bytearrays.|
 
Die folgenden Beispiele veranschaulichen das Abrufen und Ändern von Daten in verschlüsselten Spalten. In den Beispielen wird davon ausgegangen, eine Tabelle mit dem folgenden Schema. Die Spalten „SSN“ und „BirthDate“ werden verschlüsselt.
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

### <a name="data-insertion-example"></a>Einfügen von Daten (Beispiel)

Die folgenden Beispiele veranschaulichen, wie Sie die SQLSRV- und PDO_SQLSRV-Treiber verwenden, um eine Zeile in die Patienten-Tabelle einzufügen. Beachten Sie folgende Punkte:
 -   Es erfolgt keine spezielle Verschlüsselung im Beispielcode. Der Treiber automatisch erkennt und verschlüsselt die Werte der Parameter "ssn" und "BirthDate", die verschlüsselte Spalten ausgerichtet. Durch diesen Mechanismus wird die Verschlüsselung für die Anwendung transparent.
 -   Die in die Datenbankspalten eingefügten Werte, einschließlich der verschlüsselten Spalten, werden als gebundene Parameter übergeben. Während die Verwendung von Parametern optional ist, wenn Werte an nicht verschlüsselte Spalten gesendet werden (obwohl es dringend empfohlen wird, da es dabei hilft, eine Einschleusung von SQL-Befehlen zu verhindern), ist sie für Werte erforderlich, die auf verschlüsselte Spalten ausgerichtet sind. Wenn die in den Spalten "ssn" oder "BirthDate" eingefügten Werte als Literale, die in der abfrageanweisung eingebettet übergeben wurden, würde die Abfrage fehl, da der Treiber nicht versucht, zu verschlüsseln oder anderweitig Literale in Abfragen zu verarbeiten. Daher würde der Server sie zurückweisen, da sie mit den verschlüsselten Spalten inkompatibel sind.
 -   Beim Einfügen von Werten, die Bind-Parameter verwenden, muss ein SQL-Typ, die in den Datentyp der Zielspalte identisch ist, oder, dessen Konvertierung in den Datentyp der Zielspalte unterstützt wird, an die Datenbank übergeben werden. Diese Anforderung ist, da einige Typumwandlungen Always Encrypted unterstützt werden. (Weitere Informationen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)). Die zwei PHP-Treiber, SQLSRV- und PDO_SQLSRV, jede hat es sich um einen Mechanismus, um dem Benutzer, die den SQL-Typ des Werts zu ermitteln helfen. Aus diesem Grund muss der Benutzer keine den SQL-Typ explizit angeben.
  -   Für den SQLSRV-Treiber hat der Benutzer zwei Optionen zur Verfügung:
   -   Basieren Sie auf der PHP-Treiber, um zu bestimmen, und legen Sie den richtigen SQL-Typ. Der Benutzer muss in diesem Fall verwenden `sqlsrv_prepare` und `sqlsrv_execute` zum Ausführen einer parametrisierten Abfrage.
   -   Legen Sie den SQL-Typ explizit fest.
  -   Für den PDO_SQLSRV-Treiber besitzt der Benutzer nicht die Möglichkeit, den SQL-Typ eines Parameters explizit festlegen. Der PDO_SQLSRV-Treiber kann automatisch die Benutzer, die den SQL-Typ zu bestimmen, beim Binden eines.
 -   Die zum Bestimmen des Typs SQL-Treiber gelten einige Einschränkungen:
  -   SQLSRV-Treiber:
   -   Wenn der Benutzer den Treiber, um zu bestimmen, die SQL-Typen für den verschlüsselten Spalten will, muss der Benutzer verwenden `sqlsrv_prepare` und `sqlsrv_execute`.
   -   Wenn `sqlsrv_query` wird bevorzugt, der Benutzer ist verantwortlich für die SQL-Typen für alle Parameter angeben. Der angegebene SQL-Typ muss es sich um die Länge der Zeichenfolge für Zeichenfolgen-Datentypen, und die Skalierung und die Genauigkeit für Dezimaltypen enthalten.
  -   PDO_SQLSRV-Treiber:
   -   Das Anweisungsattribut `PDO::SQLSRV_ATTR_DIRECT_QUERY` wird in eine parametrisierte Abfrage nicht unterstützt.
   -   Das Anweisungsattribut `PDO::ATTR_EMULATE_PREPARES` wird in eine parametrisierte Abfrage nicht unterstützt.
   
SQLSRV-Treiber und [Sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md):
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

SQLSRV-Treiber und [Sqlsrv_query](../../connect/php/sqlsrv-query.md):
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

PDO_SQLSRV-Treiber und [PDO:: Prepare](../../connect/php/pdo-prepare.md):
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

### <a name="plaintext-data-retrieval-example"></a>Beispiel für nur-Text abrufen

Die folgenden Beispiele veranschaulichen Filtern von Daten basierend auf verschlüsselten Werten und Abrufen von Klartextdaten aus verschlüsselten Spalten, die über die SQLSRV- und PDO_SQLSRV-Treiber. Beachten Sie folgende Punkte:
 -   Der in der WHERE-Klausel zum Filtern der Spalte „SSN“ verwendete Wert muss mit dem bind-Parameter übergeben werden, damit ihn der Treiber vor dem Senden an die Datenbank transparent verschlüsseln kann.
 -   Beim Ausführen der Abfrage mit gebundenen Parametern, die PHP-Treibern bestimmt automatisch die SQL-Typ für den Benutzer, wenn der Benutzer explizit den SQL-Typ gibt an, wenn der SQLSRV-Treiber verwenden.
 -   Alle Werte werden vom Programm als Klartext ausgegeben, da der Treiber die aus den Spalten „SSN“ und „BirthDate“ abgerufenen Daten transparent entschlüsselt.
 
Hinweis: Abfragen können die Durchführung von Gleichheitsvergleichen für verschlüsselte Spalten ausführen, nur dann, wenn die Verschlüsselung deterministisch ist. Weitere Informationen finden Sie im Abschnitt [Auswählen der deterministischen oder zufälligen Verschlüsselung](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

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

### <a name="ciphertext-data-retrieval-example"></a>Beispiel für Daten des verschlüsselten Texts abrufen

Wenn Always Encrypted nicht aktiviert ist, können Abfragen weiterhin Daten aus verschlüsselten Spalten abrufen, so lange die Abfrage keine Parameter für verschlüsselte Spalten enthält.

Die folgenden Beispiele veranschaulichen das Abrufen von Binär verschlüsselten Daten aus verschlüsselten Spalten, die über die SQLSRV- und PDO_SQLSRV-Treiber. Beachten Sie folgende Punkte:
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
 -   Bei Verwendung des SQLSRV-Treibers mit `sqlsrv_prepare` und `sqlsrv_execute` der SQL-Typ, sowie die Spaltengröße und die Anzahl der Dezimalstellen des Parameters wird automatisch bestimmt.
 -   Wenn Sie den PDO_SQLSRV-Treiber zum Ausführen einer Abfrage verwenden, wird der SQL-Typ, mit die Spaltengröße und die Anzahl der Dezimalstellen des Parameters ebenfalls automatisch bestimmt.
 -   Bei Verwendung des SQLSRV-Treibers mit `sqlsrv_query` zum Ausführen einer Abfrage:
  -   Der SQL-Typ des Parameters ist entweder genau identisch mit den Typ der entsprechenden Spalte, oder die Konvertierung von der SQL-Typ in den Typ der Spalte wird unterstützt.
  -   Die Genauigkeit und Dezimalstellenanzahl von Parametern, die auf Spalten der SQL Server-Datentypen `decimal` und `numeric` ausgerichtet sind, ist mit der für die Zielspalte konfigurierten Genauigkeit und Dezimalstellenanzahl identisch.
  -   Die Genauigkeit von Parametern, die auf Spalten der SQL Server-Datentypen `datetime2`, `datetimeoffset` oder `time` ausgerichtet sind, ist in Abfragen, in denen die Zielspalte geändert wird, nicht größer als die Genauigkeit für die Zielspalte.
 -   Verwenden Sie keine PDO_SQLSRV Anweisungsattribute `PDO::SQLSRV_ATTR_DIRECT_QUERY` oder `PDO::ATTR_EMULATE_PREPARES` in einer parametrisierten Abfrage
 
#### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Fehler aufgrund der Übergabe von Klartext anstelle von verschlüsselten Werten

Jeder Wert, der eine verschlüsselte Spalte ausgerichtet ist, muss vor dem Senden an den Server verschlüsselt werden. Ein Versuch, einen Klartextwert einzufügen, zu ändern oder nach einem Klartextwert für eine verschlüsselte Spalte zu filtern, führt zu einem Fehler. Stellen Sie Folgendes sicher, um solche Fehler zu vermeiden:
 -   Always Encrypted ist aktiviert (Legen Sie in der Verbindungszeichenfolge, die `ColumnEncryption` Schlüsselwort `Enabled`).
 -   Sie verwenden Bind-Parameter zum Senden von Daten, die auf verschlüsselte Spalten ausgerichtet sind. Das folgende Beispiel zeigt eine Abfrage, die falsch nach einem Literal bzw. einer Konstante einer verschlüsselten Spalte (SSN) filtert:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

## <a name="controlling-performance-impact-of-always-encrypted"></a>Kontrollieren der Auswirkungen von Always Encrypted auf die Leistung

Da Always Encrypted eine clientseitige Verschlüsselungstechnologie ist, werden die meisten Leistungseinbußen auf der Clientseite und nicht in der Datenbank beobachtet. Neben den Kosten für Verschlüsselungs- und Entschlüsselungsvorgänge ergeben sich die folgenden anderen Quellen für Leistungseinbußen auf der Clientseite:
 -   Zusätzliche Roundtrips zur Datenbank zum Abrufen von Metadaten für Abfrageparameter.
 -   Aufrufe an einen Spaltenhauptschlüsselspeicher für den Zugriff auf einen Spaltenhauptschlüssel.
 
### <a name="round-trips-to-retrieve-metadata-for-query-parameters"></a>Roundtrips zum Abrufen von Metadaten für Abfrageparameter

Wenn Always Encrypted für eine Verbindung aktiviert ist, ruft der ODBC-Treiber standardmäßig [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) für jede parametrisierte Abfrage auf, wobei die Abfrageanweisung (ohne Parameterwerte) an SQL Server übergeben wird. Diese gespeicherte Prozedur analysiert die Query-Anweisung, um herauszufinden, ob Parameter müssen verschlüsselt werden, und wenn Ja, gibt die verschlüsselungsbezogenen Informationen für jeden Parameter, um den Treiber verschlüsseln zu ermöglichen.

Da die PHP-Treiber einen Parameter gebunden werden können, geben Sie eine vorbereitete Anweisung ohne Angabe der SQL, rufen Sie die PHP-Treiber beim Binden eines Parameters in einer Verbindung mit Always Encrypted aktiviert [SQLDescribeParam](../../odbc/reference/syntax/sqldescribeparam-function.md) auf der Parameter, um die SQL-Typ, Spaltengröße und Dezimalstellen abzurufen. Die Metadaten wird dann zum Aufrufen [SQLBindParameter]( ../../odbc/reference/syntax/sqlbindparameter-function.md). Diese zusätzlichen `SQLDescribeParam` Aufrufe erfordern keine zusätzliche Roundtrips zur Datenbank, wie die ODBC-Treiber bereits die Informationen auf der Clientseite gespeichert hat beim `sys.sp_describe_parameter_encryption` aufgerufen wurde.

Die vorherigen Verhalten sicherzustellen, eine hohe Ebene der Transparenz für die Client-Anwendung (und der Anwendungsentwickler) muss nicht zu beachten, welche Abfragen Zugriff auf verschlüsselte Spalten, solange die Werte, die auf verschlüsselte Spalten ausgerichtet sind, an den Treiber in übergeben werden Parameter.

Im Gegensatz zu den ODBC-Treiber für SQL Server wird die Aktivierung von Always Encrypted auf die Anweisung/Abfrage noch nicht in den PHP-Treibern unterstützt. 

### <a name="column-encryption-key-caching"></a>Zwischenspeicherung von Spaltenverschlüsselungsschlüsseln

Um die Anzahl der Aufrufe an einen spaltenhauptschlüsselspeicher zum Entschlüsseln von spaltenverschlüsselungsschlüsseln (CEK) zu reduzieren, wird der Treiber den nur-Text-CEKs im Arbeitsspeicher zwischengespeichert. Nach dem Empfang der verschlüsselte CEK (ECEK) aus den Datenbankmetadaten an, versucht der ODBC-Treiber zuerst, suchen, die nur-Text CEK, entspricht des verschlüsselten Schlüssel-Wert im Cache. Der Treiber Ruft den Schlüsselspeicher mit dem CMK, nur dann, wenn er die entsprechenden Klartext-CEK im Cache nicht finden kann.

Hinweis: In den ODBC-Treiber für SQL Server werden die Einträge im Cache nach einem Timeout von zwei Stunden entfernt. Dieses Verhalten bedeutet, dass für einen bestimmten ECEK, der Treiber kontaktiert den Schlüsselspeicher nur einmal während der Lebensdauer der Anwendung oder alle zwei Stunden, je nachdem, was kleiner ist.

## <a name="working-with-column-master-key-stores"></a>Arbeiten mit Spaltenhauptschlüsselspeichern

Zum Verschlüsseln und Entschlüsseln von Daten, muss der Treiber einen CEK zu erhalten, die für die Zielspalte konfiguriert ist. CEKs werden in verschlüsselter Form (ECEKs) in den Datenbankmetadaten gespeichert. Jede CEK verfügt über einen entsprechenden Spaltenhauptschlüssels, der zum Verschlüsseln verwendet wurde. Die [Datenbankmetadaten](../../t-sql/statements/create-column-master-key-transact-sql.md) speichert nicht den CMK selbst enthält nur den Namen des Schlüsselspeichers und Informationen, die der Schlüsselspeicher verwenden können, um den CMK zu suchen.

Um den nur-Text-Wert, der eine ECEK zu erhalten, ruft der Treiber die Metadaten über den CEK und die entsprechenden CMK zuerst ab und dann anhand dieser Informationen den Schlüsselspeicher mit dem CMK wenden Sie sich an und fordert er zum Entschlüsseln von ECEK. Der Treiber kommuniziert mit einem Schlüsselspeicher, der über einen Schlüsselspeicheranbieter.

Microsoft Driver 5.3.0 für PHP für SQL Server werden nur für Windows Store-Zertifikatanbieter und Azure Key Vault unterstützt. Die anderen Keystore-Anbieter unterstützt, die vom ODBC-Treiber (benutzerdefinierte Keystore-Anbieter) wird noch nicht unterstützt.

### <a name="using-the-windows-certificate-store-provider"></a>Verwenden des Windows-Zertifikatspeicheranbieters

Der ODBC-Treiber für SQL Server unter Windows enthält einen integrierten Speicheranbieter für spaltenhauptschlüssel für den Windows Store-Zertifikat, mit dem Namen `MSSQL_CERTIFICATE_STORE`. (Dieser Anbieter ist nicht unter MacOS oder Linux verfügbar.) Mit diesem Anbieter der CMK lokal auf dem Clientcomputer gespeichert, und ist keine zusätzliche Konfiguration von der Anwendung für die Verwendung mit dem Treiber erforderlich. Allerdings muss die Anwendung auf das Zertifikat und seinen privaten Schlüssel im Speicher zugreifen. Weitere Informationen finden Sie unter [Create and Store Column Master Keys (Always Encrypted)](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)(Erstellen und Speichern von Spaltenhauptschlüsseln (Always Encrypted)).

### <a name="using-azure-key-vault"></a>Verwenden von Azure Key Vault

Azure Key Vault bietet eine Möglichkeit zum Speichern von Verschlüsselungsschlüsseln, Kennwörter und andere Geheimnisse mithilfe von Azure und zum Speichern von Schlüsseln für Always Encrypted verwendet werden können. Der ODBC-Treiber für SQL Server (Version 17 und höher) enthält einen integrierten spaltenhauptschlüssel-Speicheranbieter für Azure Key Vault. Die folgenden Verbindungsoptionen Behandeln von Azure Key Vault-Konfiguration: `KeyStoreAuthentication`, `KeyStorePrincipalId`, und `KeyStoreSecret`. 
 -   `KeyStoreAuthentication` kann einen von zwei mögliche Werte annehmen: `KeyVaultPassword` und `KeyVaultClientSecret`. Diese Werte steuern, welche Art von Anmeldeinformationen für die Authentifizierung mit den beiden anderen Schlüsselwörtern verwendet werden.
 -   `KeyStorePrincipalId` akzeptiert eine Zeichenfolge, die einen Bezeichner für das Konto, Azure Key Vault den Zugriff auf Suchvorgänge darstellt. 
     -   Wenn `KeyStoreAuthentication` nastaven NA hodnotu `KeyVaultPassword`, klicken Sie dann `KeyStorePrincipalId` muss der Name von einem Azure Active Directory-Benutzer sein.
     -   Wenn `KeyStoreAuthentication` nastaven NA hodnotu `KeyVaultClientSecret`, klicken Sie dann `KeyStorePrincipalId` muss eine Anwendung Client-ID sein.
 -   `KeyStoreSecret` akzeptiert eine Zeichenfolge, die eine Anmeldeinformation darstellt. 
     -   Wenn `KeyStoreAuthentication` nastaven NA hodnotu `KeyVaultPassword`, klicken Sie dann `KeyStoreSecret` muss das Kennwort des Benutzers. 
     -   Wenn `KeyStoreAuthentication` nastaven NA hodnotu `KeyVaultClientSecret`, klicken Sie dann `KeyStoreSecret` muss das anwendungsgeheimnis, das die Anwendungsclient-ID zugeordnet

Alle drei Optionen müssen in der Verbindungszeichenfolge zur Verwendung von Azure Key Vault vorhanden sein. Darüber hinaus `ColumnEncryption` muss festgelegt werden, um `Enabled`. Wenn `ColumnEncryption` nastaven NA hodnotu `Disabled` der Azure Key Vault-Optionen stehen zur Verfügung, das Skript wird fortgesetzt, ohne Fehler aber keine Verschlüsselung wird ausgeführt.

Die folgenden Beispiele zeigen, wie für die Verbindung mit SQL Server mit Azure Key Vault.

SQLSRV:

Verwenden von Azure Active Directory-Konto:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultPassword", "KeyStorePrincipalId"=>$AADUsername, "KeyStoreSecret"=>$AADPassword);
$conn = sqlsrv_connect($server, $connectionInfo);
```
Verwenden ein Azure-Anwendung-Client-ID und geheimen Schlüssel ein:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultClientSecret", "KeyStorePrincipalId"=>$applicationClientID, "KeyStoreSecret"=>$applicationClientSecret);
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV: Verwenden von Azure Active Directory-Konto:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultPassword; KeyStorePrincipalId = $AADUsername; KeyStoreSecret = $AADPassword;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```
Verwenden ein Azure-Anwendung-Client-ID und geheimen Schlüssel ein:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultClientSecret; KeyStorePrincipalId = $applicationClientID; KeyStoreSecret = $applicationClientSecret;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

## <a name="limitations-of-the-php-drivers-when-using-always-encrypted"></a>Einschränkungen für den PHP-Treibern, die Verwendung von Always Encrypted

SQLSRV und PDO_SQLSRV:
 -   Linux/MacOS unterstützen keine Windows Store-Zertifikatanbieter
 -   Erzwingen von Parameterverschlüsselung
 -   Aktivieren von Always Encrypted auf Anweisungsebene 
 -   Bei Verwendung der Always Encrypted-Feature und nicht-UTF8-Gebietsschemas unter Linux und MacOS (z. B. "en_US"". ISO-8859-1 "), Einfügen von null-Daten oder eine leere Zeichenfolge in eine verschlüsselte char-Spalte funktionieren nicht, wenn die Codepage 1252 auf Ihrem System installiert wurde
 
Nur SQLSRV:
 -   Mithilfe von `sqlsrv_query` für die bindenden Parameter ohne Angabe des SQL-Typs
 -   Mithilfe von `sqlsrv_prepare` zum Binden von Parametern in einem Batch von SQL-Anweisungen  
 
Nur PDO_SQLSRV:
 -   `PDO::SQLSRV_ATTR_DIRECT_QUERY` Anweisungsattribut angegeben, die in einer parametrisierten Abfrage
 -   `PDO::ATTR_EMULATE_PREPARE` Anweisungsattribut angegeben, die in einer parametrisierten Abfrage
 -   Binden von Parametern in einem Batch von SQL-Anweisungen
 
Die PHP-Treiber erbt auch die Einschränkungen, die vom ODBC-Treiber für SQL Server und die Datenbank. Finden Sie unter [Einschränkungen des ODBC-Treibers bei Verwendung von Always Encrypted](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) und [Featuredetails Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#feature-details).  
  
## <a name="see-also"></a>Weitere Informationen  
[Programmierhandbuch für den PHP-SQL-Treiber](../../connect/php/programming-guide-for-php-sql-driver.md)
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  
[API-Referenz für den PDO_SQLSRV-Treiber](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
