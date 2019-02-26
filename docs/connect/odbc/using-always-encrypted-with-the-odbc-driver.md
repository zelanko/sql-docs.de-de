---
title: Verwenden von Always Encrypted mit ODBC Driver for SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/01/2018
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02e306b8-9dde-4846-8d64-c528e2ffe479
ms.author: v-chojas
manager: craigg
author: MightyPen
ms.openlocfilehash: 1ba94395acad1aec8717c570cc4b6e30ed7a12a4
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662854"
---
# <a name="using-always-encrypted-with-the-odbc-driver-for-sql-server"></a>Verwenden von Always Encrypted mit ODBC Driver for SQL Server
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

### <a name="applicable-to"></a>Anwendbar auf

- ODBC-Treiber 13.1 für SQLServer
- Odbcdriver 17 for SQLServer

### <a name="introduction"></a>Einführung

Dieser Artikel enthält Informationen zum Entwickeln von ODBC-Anwendungen mit [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und [ODBC-Treiber für SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

Always Encrypted ermöglicht Clientanwendungen das Verschlüsseln von vertraulichen Daten in einer Weise, dass weder die Daten noch die Verschlüsselungsschlüssel zu irgendeinem Zeitpunkt gegenüber SQL Server oder Azure SQL-Datenbank offengelegt werden. Ein Treiber, bei dem Always Encrypted aktiviert ist, z.B. ODBC Driver for SQL Server, erreicht dies durch die transparente Ver- und Entschlüsselung von sensiblen Daten in der Clientanwendung. Der Treiber ermittelt automatisch, welche Abfrageparameter vertraulichen Datenbankspalten (mit Always Encrypted geschützt) entsprechen. Die Werte dieser Parameter werden dann vor der Übergabe an SQL Server oder Azure SQL-Datenbank verschlüsselt. Auf ähnliche Weise entschlüsselt der Treiber die Daten transparent, die von verschlüsselten Datenbankspalten in Abfrageergebnissen empfangen werden. Weitere Informationen finden Sie unter [Immer verschlüsselt (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md).

### <a name="prerequisites"></a>Voraussetzungen

Konfigurieren Sie Always Encrypted in Ihrer Datenbank. Dies umfasst die Bereitstellung von Always Encrypted-Schlüsseln und die Einrichtung der Verschlüsselung für ausgewählte Datenbankspalten. Wenn Sie nicht bereits über eine Datenbank verfügen, für die Always Encrypted konfiguriert ist, befolgen Sie die Anweisungen in [Erste Schritte mit Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). Insbesondere sollten Ihre Datenbank die Metadatendefinitionen für eine Zertifizierungsstelle (Column Master Key, CMK), (Spalte Encryption Key, CEK) und eine Tabelle mit einer oder mehreren Spalten, die mit diesem CEK verschlüsselt enthalten.

### <a name="enabling-always-encrypted-in-an-odbc-application"></a>Aktivieren von "immer verschlüsselt" in einer ODBC-Anwendung

Die einfachste Möglichkeit zum Aktivieren der parameterverschlüsselung und Entschlüsselung von Resultsets, die verschlüsselte Spalte wird durch Festlegen des Werts, der die `ColumnEncryption` verbindungszeichenfolgenkennwort **aktiviert**. Im Folgenden finden Sie ein Beispiel für eine Verbindungszeichenfolge, mit der Always Encrypted aktiviert wird:

```
SQLWCHAR *connString = L"Driver={ODBC Driver 13 for SQL Server};Server={myServer};Trusted_Connection=yes;ColumnEncryption=Enabled;";
```

Always Encrypted kann ebenfalls aktiviert werden in der DSN-Konfiguration, die mit dem gleichen Schlüssel und Wert (der überschrieben werden, wird die Verbindung Zeichenfolge festlegen, wenn vorhanden) oder programmgesteuert über die `SQL_COPT_SS_COLUMN_ENCRYPTION` vorverbindungsattribut. Auf diese Weise festlegen, überschreibt den Wert in der Verbindungszeichenfolge oder DSN festgelegt:

```
 SQLSetConnectAttr(hdbc, SQL_COPT_SS_COLUMN_ENCRYPTION, (SQLPOINTER)SQL_COLUMN_ENCRYPTION_ENABLE, 0);
```

Nachdem für die Verbindung aktiviert ist, kann das Verhalten von Always Encrypted für einzelne Abfragen angepasst werden. Finden Sie unter [steuern die Leistung Auswirkungen von Always Encrypted](#controlling-the-performance-impact-of-always-encrypted) unten Weitere Informationen.

Beachten Sie, dass die Aktivierung von Always Encrypted nicht ausreichend für die Verschlüsselung oder Entschlüsselung erfolgreich ist. Sie müssen auch sicherstellen, dass:

- Die Anwendung verfügt über die Datenbankberechtigungen *VIEW ANY COLUMN MASTER KEY DEFINITION* und *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* , die für den Zugriff auf die Metadaten in der Datenbank über Always Encrypted-Schlüssel erforderlich sind. Weitere Informationen finden Sie unter [Datenbankberechtigungen](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).

- Die Anwendung kann den CMK zugreifen, die schützt, der die CEKs für die abgefragten verschlüsselte Spalten. Dies ist abhängig von der Keystore-Anbieter der CMK gespeichert. Finden Sie unter [arbeiten mit Spaltenhauptschlüsselspeichern](#working-with-column-master-key-stores) für Weitere Informationen.

### <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Abrufen und Ändern von Daten in verschlüsselten Spalten

Nachdem Sie Always Encrypted für eine Verbindung aktiviert haben, können Sie standard-ODBC-APIs (finden Sie unter [ODBC-Beispielcode](https://code.msdn.microsoft.com/windowsapps/ODBC-sample-191624ae/sourcecode?fileId=51137&pathId=1980325953) oder [ODBC Programmer's Reference](https://msdn.microsoft.com/library/ms714177(v=vs.85).aspx)) auf Daten in verschlüsselten Datenbankspalten abrufen oder ändern. Angenommen, Ihre Anwendung verfügt über die erforderlichen Berechtigungen und können auf den spaltenhauptschlüssel zugreifen, der Treiber verschlüsselt die Abfrageparameter, die auf verschlüsselte Spalten ausgerichtet und Entschlüsseln von Daten aus verschlüsselten Spalten, verhält sich transparent auf abgerufen der Anwendung, als ob die Spalten nicht verschlüsselt wurden.

Wenn Always Encrypted nicht aktiviert ist, tritt bei Abfragen mit Parametern, die auf verschlüsselte Spalten ausgerichtet sind, ein Fehler auf. Daten können weiterhin aus verschlüsselten Spalten abgerufen werden, solange die Abfrage keine Parameter für verschlüsselte Spalten enthält. Allerdings versucht der Treiber Entschlüsselung nicht aus, und die Anwendung, die verschlüsselte Binärdaten (als Bytearrays) empfängt.

In der folgenden Tabelle wird das Verhalten von Abfragen in Abhängigkeit davon zusammengefasst, ob Always Encrypted aktiviert ist:

|Abfragemerkmal | Always Encrypted ist aktiviert und die Anwendung kann auf die Schlüssel und Schlüsselmetadaten zugreifen.|Always Encrypted ist aktiviert und die Anwendung kann nicht auf die Schlüssel oder Schlüsselmetadaten zugreifen. | Always Encrypted ist deaktiviert|
|:---|:---|:---|:---|
| Parameter, die auf verschlüsselte Spalten ausgerichtet sind. | Parameterwerte werden transparent verschlüsselt. | Fehler | Fehler|
| Daten von verschlüsselten Spalten ohne Parameter abrufen, die auf verschlüsselte Spalten ausgerichtet sind.| Ergebnisse von verschlüsselten Spalten werden transparent entschlüsselt. Die Anwendung erhält klartextwerte der Spalte. | Fehler | Ergebnisse von verschlüsselten Spalten werden nicht entschlüsselt. Die Anwendung erhält verschlüsselte Werte als Bytearrays.

Die folgenden Beispiele veranschaulichen das Abrufen und Ändern von Daten in verschlüsselten Spalten. In den Beispielen wird davon ausgegangen, eine Tabelle mit dem folgenden Schema. Beachten Sie, dass die Spalten „SSN“ und „BirthDate“ verschlüsselt werden.

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
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY] )
 GO
```

#### <a name="data-insertion-example"></a>Einfügen von Daten (Beispiel)

In diesem Beispiel wird eine Zeile in die Tabelle „Patients“ eingefügt. Beachten Sie Folgendes:

- Es erfolgt keine spezielle Verschlüsselung im Beispielcode. Der Treiber automatisch erkennt und verschlüsselt die Werte von den "ssn" und die Date-Parameter, die verschlüsselte Spalten ausgerichtet. Dadurch wird die Verschlüsselung für die Anwendung transparent.

- Die in die Datenbankspalten eingefügten Werte, einschließlich der verschlüsselten Spalten, werden als gebundene Parameter übergeben (siehe [SQLBindParameter-Funktion](https://msdn.microsoft.com/library/ms710963(v=vs.85).aspx)). Während die Verwendung von Parametern optional ist, wenn Werte an nicht verschlüsselte Spalten gesendet werden (obwohl es dringend empfohlen wird, da es dabei hilft, eine Einschleusung von SQL-Befehlen zu verhindern), ist sie für Werte erforderlich, die auf verschlüsselte Spalten ausgerichtet sind. Wenn die in den Spalten "ssn" oder "BirthDate" eingefügten Werte als Literale, die in der abfrageanweisung eingebettet übergeben wurden, würde die Abfrage fehl, da der Treiber nicht versucht, zu verschlüsseln oder anderweitig Literale in Abfragen zu verarbeiten. Daher würde der Server sie zurückweisen, da sie mit den verschlüsselten Spalten inkompatibel sind.

- Die SQL-Typ, der in der Spalte "ssn" eingefügten Parameters nastaven NA hodnotu SQL_CHAR, die zugeordnet wird die **Char** SQL Server-Datentyp (`rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);`). Wenn der Typ des Parameters auf SQL_WCHAR, festgelegt wurde, der zuordnet **Nchar**, würde die Abfrage fehl, da Always Encrypted serverseitige-Konvertierungen von verschlüsselten Nchar-Werte in verschlüsselten Char-Werten nicht unterstützt. Finden Sie unter [ODBC Programmer's Reference: Anhang D: Datentypen](https://msdn.microsoft.com/library/ms713607.aspx) Informationen zu den datentypzuordnungen.

```
    SQL_DATE_STRUCT date;
    SQLLEN cbdate;   // size of date structure  

    SQLCHAR SSN[12];
    strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

    SQLWCHAR* firstName = L"Catherine";
    SQLWCHAR* lastName = L"Abel";
    SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

    // Initialize the date structure  
    date.day = 10;
    date.month = 9;
    date.year = 1996;

    // Size of structures   
    cbdate = sizeof(SQL_DATE_STRUCT);

    SQLRETURN rc = 0;

    string queryText = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?) ";

    rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

    //SSN
    rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);
    //FirstName
    rc = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)firstName, 0, &cbFirstName);
    //LastName
    rc = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)lastName, 0, &cbLastName);
    //BirthDate
    rc = SQLBindParameter(hstmt, 4, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 10, 0, (SQLPOINTER)&date, 0, &cbdate);

    rc = SQLExecute(hstmt);
```

#### <a name="plaintext-data-retrieval-example"></a>Beispiel für nur-Text abrufen

Im folgenden Beispiel wird das Filtern von Daten auf Basis verschlüsselter Werte und das Abrufen von Klartextdaten aus verschlüsselten Spalten veranschaulicht. Beachten Sie Folgendes:

- Der in der WHERE-Klausel zum Filtern der Spalte „SSN“ verwendete Wert muss mit dem SQLBindParameter-Parameter übergeben werden, damit ihn der Treiber vor dem Senden an die Datenbank transparent verschlüsseln kann.

- Alle Werte werden vom Programm als Klartext ausgegeben, da der Treiber die aus den Spalten „SSN“ und „BirthDate“ abgerufenen Daten transparent entschlüsselt.

> [!NOTE]
> Abfragen können die Durchführung von Gleichheitsvergleichen für verschlüsselte Spalten ausführen, nur dann, wenn die Verschlüsselung deterministisch ist. Weitere Informationen finden Sie im Abschnitt [Auswählen der deterministischen oder zufälligen Verschlüsselung](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

```
SQLCHAR SSN[12];
strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

SQLWCHAR* firstName = L"Catherine";
SQLWCHAR* lastName = L"Abel";
SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

SQLRETURN rc = 0;
string empty = "";
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] " + empty +
    "FROM  [dbo].[Patients]" +
    "WHERE " +
    "[SSN] = ? ";

rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

//SSN
rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);

rc = SQLExecute(hstmt);
HandleDiagnosticRecord(hstmt, SQL_HANDLE_STMT, rc);

SQL_DATE_STRUCT dateVal;
SQLWCHAR firstNameVal[50];
SQLWCHAR lastNameVal[50];
SQLCHAR SSNVal[12];
SQLLEN cbdate;   // size of date structure  

int rowcount = 0;
while (SQL_SUCCEEDED(SQLFetch(hstmt)))
{
    rowcount++;
    SQLGetData(hstmt, 1, SQL_C_CHAR, &SSNVal, 11, &cbSSN);
    SQLGetData(hstmt, 2, SQL_C_WCHAR, &firstNameVal, 50, &cbFirstName);
    SQLGetData(hstmt, 3, SQL_C_WCHAR, &lastNameVal, 50, &cbLastName);
    SQLGetData(hstmt, 4, SQL_C_TYPE_DATE, &dateVal, 10, &cbdate);        
}
```

#### <a name="ciphertext-data-retrieval-example"></a>Beispiel für Daten des verschlüsselten Texts abrufen

Wenn Always Encrypted nicht aktiviert ist, können Abfragen weiterhin Daten aus verschlüsselten Spalten abrufen, so lange die Abfrage keine Parameter für verschlüsselte Spalten enthält.

In den folgenden Beispielen wird das Abrufen von binär verschlüsselten Daten aus verschlüsselten Spalten veranschaulicht. Beachten Sie Folgendes:

- Da Always Encrypted in der Verbindungszeichenfolge nicht aktiviert ist, gibt die Abfrage verschlüsselte Werte von „SSN“ und „BirthDate“ als Bytearrays zurück (das Programm konvertiert die Werte in Zeichenfolgen).
- Eine Abfrage, die Daten aus verschlüsselten Spalten mit deaktiviertem Always Encrypted abruft, kann Parameter aufweisen, so lange keiner der Parameter auf eine verschlüsselte Spalte ausgerichtet ist. Die obige Abfrage filtert nach der Spalte „LastName“, die in der Datenbank nicht verschlüsselt ist. Wenn die Abfrage nach „SSN“ oder „BirthDate“ filtert, würde ein Fehler auftreten.


```
SQLCHAR SSN[12];
strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

SQLWCHAR* firstName = L"Catherine";
SQLWCHAR* lastName = L"Abel";
SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

SQLRETURN rc = 0;
string empty = "";
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] " + empty +
    "FROM  [dbo].[Patients]" +
    "WHERE " +
    "[LastName] = ?";

rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

//LastName
rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)lastName, 0, &cbLastName);

rc = SQLExecute(hstmt);
HandleDiagnosticRecord(hstmt, SQL_HANDLE_STMT, rc);

SQL_DATE_STRUCT dateVal;
SQLWCHAR firstNameVal[50];
SQLWCHAR lastNameVal[50];
SQLCHAR SSNVal[12];
SQLLEN cbdate;   // size of date structure  

int rowcount = 0;
while (SQL_SUCCEEDED(SQLFetch(hstmt)))
{
    rowcount++;
    SQLGetData(hstmt, 1, SQL_C_CHAR, &SSNVal, 11, &cbSSN);
    SQLGetData(hstmt, 2, SQL_C_WCHAR, &firstNameVal, 50, &cbFirstName);
    SQLGetData(hstmt, 3, SQL_C_WCHAR, &lastNameVal, 50, &cbLastName);
    SQLGetData(hstmt, 4, SQL_C_TYPE_DATE, &dateVal, 10, &cbdate);        
}
```

#### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Vermeiden allgemeiner Probleme beim Abfragen von verschlüsselter Spalten

In diesem Abschnitt werden die allgemeinen Fehlerkategorien bei der Abfrage verschlüsselter Spalten über ODBC-Anwendungen sowie einige Grundsätze zum Vermeiden dieser Fehler beschrieben.

##### <a name="unsupported-data-type-conversion-errors"></a>Konvertierungsfehler durch nicht unterstützte Datentypen

Always Encrypted unterstützt einige Konvertierungen für verschlüsselte Datentypen. Eine ausführliche Liste der unterstützten Typkonvertierungen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Um Fehler bei der datentypkonvertierung zu vermeiden, stellen Sie sicher, dass Sie die folgenden Punkte beachten Sie, wenn Parameter für verschlüsselte Spalten SQLBindParameter mit:

- Der SQL-Typ des Parameters ist entweder genau identisch mit den Typ der entsprechenden Spalte, oder die Konvertierung von der SQL-Typ in den Typ der Spalte wird unterstützt.

- Die Genauigkeit und Dezimalstellenanzahl von Parametern, die auf Spalten der SQL Server-Datentypen `decimal` und `numeric` ausgerichtet sind, ist mit der für die Zielspalte konfigurierten Genauigkeit und Dezimalstellenanzahl identisch.

- Die Genauigkeit von Parametern, die auf Spalten der SQL Server-Datentypen `datetime2`, `datetimeoffset` oder `time` ausgerichtet sind, ist in Abfragen, in denen die Zielspalte geändert wird, nicht größer als die Genauigkeit für die Zielspalte.  

##### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Fehler aufgrund der Übergabe von Klartext anstelle von verschlüsselten Werten

Jeder Wert, der eine verschlüsselte Spalte ausgerichtet ist, muss vor dem Senden an den Server verschlüsselt werden. Ein Versuch, einen Klartextwert einzufügen, zu ändern oder nach einem Klartextwert für eine verschlüsselte Spalte zu filtern, führt zu einem Fehler. Stellen Sie Folgendes sicher, um solche Fehler zu vermeiden:

- Always Encrypted ist aktiviert (in der DSN ist die Verbindungszeichenfolge und vor dem Herstellen einer Verbindung durch Festlegen der `SQL_COPT_SS_COLUMN_ENCRYPTION` Verbindungsattribut für eine bestimmte Verbindung, oder die `SQL_SOPT_SS_COLUMN_ENCRYPTION` Anweisungsattribut für eine bestimmte Anweisung).

- Sie verwenden „SQLBindParameter“ zum Senden von Daten, die auf verschlüsselte Spalten ausgerichtet sind. Das folgende Beispiel zeigt eine Abfrage, in der auf falsche Weise nach einem Literal bzw. einer Konstante einer verschlüsselten Spalte (SSN) gefiltert wird, anstatt das Literal als Argument an SQLBindParameter zu übergeben.

```
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

### <a name="precautions-when-using-sqlsetpos-and-sqlmoreresults"></a>Vorsichtsmaßnahmen bei der Verwendung von SQLSetPos und SQLMoreResults

#### <a name="sqlsetpos"></a>SQLSetPos

Die `SQLSetPos` -API ermöglicht es eine Anwendung zum Aktualisieren von Zeilen in ein Resultset mit der Puffer, die mit SQLBindCol gebunden wurden und in welcher Zeile der Daten wurde zuvor abgerufen. Aufgrund des Verhaltens der asymmetrischen Auffüllung des verschlüsselten Typen mit fester Länge ist es möglich, unerwartet die Daten dieser Spalten ändern, während der Durchführung von Updates auf andere Spalten in der Zeile. Mit AE werden mit fester Länge Zeichenwerten enthalten, die aufgefüllt werden, wenn der Wert kleiner als die Größe des Puffers ist.

Um dieses Verhalten zu vermeiden, verwenden die `SQL_COLUMN_IGNORE` Flag Spalten ignorieren, die nicht als Teil des aktualisiert werden `SQLBulkOperations` und Verwendung von `SQLSetPos` für Cursor basierend Updates.  Alle Spalten, die von der Anwendung nicht direkt geändert werden sollte ignoriert werden, sowohl für Leistung und um das Abschneiden von Spalten zu vermeiden, die auf einen Puffer gebunden sind *kleinere* als die tatsächliche Größe der (DB). Weitere Informationen finden Sie unter [SQLSetPos Funktionsverweis](https://msdn.microsoft.com/library/ms713507(v=vs.85).aspx).

#### <a name="sqlmoreresults--sqldescribecol"></a>SQLMoreResults und SQLDescribeCol

Anwendungsprogramme können Aufrufen [SQLDescribeCol](https://msdn.microsoft.com/library/ms716289(v=vs.85).aspx) Metadaten zu den Spalten in der vorbereiteten Anweisungen zurückgegeben.  Wenn Always Encrypted aktiviert ist, Aufrufen `SQLMoreResults` *vor* Aufrufen `SQLDescribeCol` bewirkt, dass [Sp_describe_first_result_set](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) um aufgerufen werden, das ist nicht ordnungsgemäß zurück nur-Text Metadaten für verschlüsselte Spalten. Um dieses Problem zu vermeiden, rufen Sie `SQLDescribeCol` für vorbereitete Anweisungen *vor* Aufrufen `SQLMoreResults`.

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Kontrollieren der Auswirkungen von Always Encrypted auf die Leistung

Da Always Encrypted eine clientseitige Verschlüsselungstechnologie ist, werden die meisten Leistungseinbußen auf der Clientseite und nicht in der Datenbank beobachtet. Neben den Kosten für Verschlüsselungs- und Entschlüsselungsvorgänge ergeben sich die folgenden anderen Quellen für Leistungseinbußen auf der Clientseite:

- Zusätzliche Roundtrips zur Datenbank zum Abrufen von Metadaten für Abfrageparameter.

- Aufrufe an einen Spaltenhauptschlüsselspeicher für den Zugriff auf einen Spaltenhauptschlüssel.

In diesem Abschnitt werden die integrierten Leistungsoptimierungen in ODBC Driver for SQL Server und die Steuerung der Auswirkung der beiden oben genannten Faktoren auf die Leistung beschrieben.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Kontrollieren von Roundtrips zum Abrufen von Metadaten für Abfrageparameter

Wenn Always Encrypted für eine Verbindung aktiviert ist, ruft der Treiber standardmäßig [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) für jede parametrisierte Abfrage auf, wobei die Abfrageanweisung (ohne Parameterwerte) an SQL Server übergeben wird. Diese gespeicherte Prozedur analysiert die Query-Anweisung, um herauszufinden, ob Parameter müssen verschlüsselt werden, und wenn Ja, gibt die verschlüsselungsbezogenen Informationen für jeden Parameter, um den Treiber verschlüsseln zu ermöglichen. Das oben beschriebene Verhalten stellt sicher ein hohes Maß an Transparenz für die Client-Anwendung: die Anwendung (und der Anwendungsentwickler) muss nicht zu beachten, welche Abfragen Zugriff auf verschlüsselte Spalten, solange die Werte, die auf verschlüsselte Spalten ausgerichtet sind, übergeben werden der Treiber in-Parameter.

### <a name="per-statement-always-encrypted-behavior"></a>Always Encrypted Verhalten pro Anweisung

Um die Auswirkungen auf die Leistung beim Abrufen von verschlüsselungsmetadaten für parametrisierte Abfragen zu steuern, können Sie das Always Encrypted-Verhalten für einzelne Abfragen ändern, wenn es für die Verbindung aktiviert wurde. Auf diese Weise Sie können sicherstellen, dass `sys.sp_describe_parameter_encryption` erfolgt nur für Abfragen, die Sie kennen die Parameter für verschlüsselte Spalten haben. Beachten Sie jedoch, dass Sie auf diese Weise die Transparenz der Verschlüsselung reduzieren: Wenn Sie zusätzliche Spalten in Ihrer Datenbank verschlüsseln, müssen Sie möglicherweise den Code der Anwendung ändern, um ihn auf die Schemaänderungen auszurichten.

Rufen Sie zum Steuern des Verhaltens von einer Anweisung mit Always Encrypted SQLSetStmtAttr Festlegen der `SQL_SOPT_SS_COLUMN_ENCRYPTION` -Anweisungsattribut auf einen der folgenden Werte:

|value|und Beschreibung|
|-|-|
|`SQL_CE_DISABLED` (0)|Always ist Encrypted für die Anweisung deaktiviert|
|`SQL_CE_RESULTSETONLY` (1)|Nur zur Entschlüsselung. Resultsets und Rückgabewerte werden entschlüsselt und Parameter werden nicht verschlüsselt.|
|`SQL_CE_ENABLED` (3) | Always Encrypted aktiviert und für die Parameter und die Ergebnisse verwendet|

Neue Anweisungshandles erstellt, die von einer Verbindung mit Always Encrypted aktiviert standardmäßig SQL_CE_ENABLED. Von einer Verbindung mit ihm erstellten SQL_CE_DISABLED standardmäßig deaktiviert (und es ist nicht möglich, zum Aktivieren von Always Encrypted für sie.)

Wenn die meisten Abfragen einer Clientanwendung auf verschlüsselte Spalten zugreifen, wird Folgendes empfohlen:

- Legen Sie das Schlüsselwort für die `ColumnEncryption`-Verbindungszeichenfolge auf `Enabled` fest.

- Legen Sie die `SQL_SOPT_SS_COLUMN_ENCRYPTION` Attribut `SQL_CE_DISABLED` auf Anweisungen, die kein verschlüsselte Spalten zugreifen müssen. Dadurch wird sowohl aufrufen deaktiviert `sys.sp_describe_parameter_encryption` festgelegt und versucht, die Werte im Resultset zu entschlüsseln.
    
- Legen Sie die `SQL_SOPT_SS_COLUMN_ENCRYPTION` Attribut `SQL_CE_RESULTSETONLY` auf Anweisungen, die müssen keine Parameter, die eine Verschlüsselung erforderlich ist, aber Daten aus verschlüsselten Spalten abrufen. Dadurch wird der Aufruf deaktiviert `sys.sp_describe_parameter_encryption` und die parameterverschlüsselung. Ergebnisse, die mit verschlüsselten Spalten weiterhin entschlüsselt werden.

## <a name="always-encrypted-security-settings"></a>Always Encrypted Sicherheitseinstellungen

### <a name="force-column-encryption"></a>Spaltenverschlüsselung erzwingt

Um die Verschlüsselung eines Parameters zu erzwingen, legen Sie die `SQL_CA_SS_FORCE_ENCRYPT` IPD (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) Feld durch einen Aufruf an die SQLSetDescField-Funktion. Ein Wert ungleich 0 bewirkt, dass den Treiber einen Fehler zurück, wenn keine verschlüsselungsmetadaten für den zugeordneten Parameter zurückgegeben wird.

```
SQLHDESC ipd;
SQLGetStmtAttr(hStmt, SQL_ATTR_IMP_PARAM_DESC, &ipd, 0, 0);
SQLSetDescField(ipd, paramNum, SQL_CA_SS_FORCE_ENCRYPT, (SQLPOINTER)TRUE, SQL_IS_SMALLINT);   
```

Wenn SQL Server den Treiber informiert, dass der Parameter nicht verschlüsselt werden muss, tritt bei Abfragen, die diesen Parameter verwenden, ein Fehler auf. Dies bietet zusätzlichen Schutz vor Angriffen, bei denen ein kompromittierter SQL Server falsche Verschlüsselungsmetadaten für den Client bereitstellt, was zur Offenlegung von Daten führen kann.

### <a name="column-encryption-key-caching"></a>Zwischenspeicherung von Spaltenverschlüsselungsschlüsseln

Um die Anzahl der Aufrufe an einen spaltenhauptschlüsselspeicher spaltenhauptschlüsselspeicher zu verringern, wird der Treiber den nur-Text-CEKs im Arbeitsspeicher zwischengespeichert. Der CEK-Cache ist für den Treiber global und keine Verbindung zugeordnet. Nach dem Empfang von ECEK aus den Datenbankmetadaten, versucht der Treiber zunächst gefunden, die nur-Text CEK, entspricht des verschlüsselten Schlüssel-Wert im Cache. Der Treiber Ruft den Schlüsselspeicher mit dem CMK, nur dann, wenn er die entsprechenden Klartext-CEK im Cache nicht finden kann.

> [!NOTE]
> In den ODBC-Treiber für SQL Server werden die Einträge im Cache nach einem Timeout von zwei Stunden entfernt. Dies bedeutet, dass für einen bestimmten ECEK, der Treiber kontaktiert den Schlüsselspeicher nur einmal während der Lebensdauer der Anwendung oder alle zwei Stunden, je nachdem, was kleiner ist.

17.1 der ODBC-Treiber für SQL Server ab, das Timeout des Anmeldeinformationscaches CEK angepasst werden, mithilfe der `SQL_COPT_SS_CEKCACHETTL` Verbindungsattribut, das die Anzahl der Sekunden angibt, wird ein CEK im Cache verbleiben. Aufgrund der globalen Eigenschaften des Caches kann dieses Attribut aus jeder Verbindungshandles, die für den Treiber angepasst werden. Wenn der Cache, die Gültigkeitsdauer (TTL) verringert wird, vorhandenen CEKs, die die neue TTL überschreiten würde auch entfernt werden. Wenn dies 0 ist, werden keine CEKs zwischengespeichert.

### <a name="trusted-key-paths"></a>Vertrauenswürdigen Schlüsselpfaden

Beginnend mit der ODBC-Treiber 17.1 für SQL Server, die `SQL_COPT_SS_TRUSTEDCMKPATHS` Verbindungsattribut ermöglicht einer Anwendung, erfordern die Verwendung von Always Encrypted-Vorgänge nur einer angegebenen Liste von CMKs, durch deren Schlüsselpfade identifiziert wird. Standardmäßig ist dieses Attribut NULL, dies bedeutet, dass der Treiber alle Schlüsselpfad akzeptiert. Um dieses Feature verwenden zu können, legen `SQL_COPT_SS_TRUSTEDCMKPATHS` , die auf eine Null getrennte, Null-terminierte Zeichenfolge mit Breitzeichen verweisen, die die zulässigen Key keine(n) aufgeführt. Zeigt, in das von diesem Attribut muss während der Verschlüsselung oder Entschlüsselung Vorgänge, die mit dem Verbindungshandle auf dem sie festgelegt ist---auf dem der Treiber überprüft, ob es sich bei gemäß den Metadaten des CMK-Pfad in dieser wird während gültig bleiben Liste. Wenn die CMK-Pfad nicht in der Liste enthalten ist, schlägt der Vorgang fehl. Die Anwendung kann den Speicherinhalt ändern, die dieses Attribut auf, zeigt, die Liste der vertrauenswürdigen CMKs, zu ändern, ohne das Attribut erneut festzulegen.

## <a name="working-with-column-master-key-stores"></a>Arbeiten mit Spaltenhauptschlüsselspeichern

Zum Verschlüsseln und Entschlüsseln von Daten, muss der Treiber einen CEK zu erhalten, die für die Zielspalte konfiguriert ist. CEKs werden in verschlüsselter Form (ECEKs) in den Datenbankmetadaten gespeichert. Jede CEK verfügt über einen entsprechenden Spaltenhauptschlüssels, der zum Verschlüsseln verwendet wurde. Die [Datenbankmetadaten](../../t-sql/statements/create-column-master-key-transact-sql.md) speichert nicht den CMK selbst enthält nur den Namen des Keystore und Informationen, die der Keystore verwenden kann, um den CMK zu suchen.

Um den nur-Text-Wert, der eine ECEK zu erhalten, ruft der Treiber die Metadaten über den CEK und die entsprechenden CMK zuerst ab und dann anhand dieser Informationen den Schlüsselspeicher mit dem CMK wenden Sie sich an und fordert er zum Entschlüsseln von ECEK. Der Treiber kommuniziert mit einem Keystore aus, mit einer Keystore-Anbieter.

### <a name="built-in-keystore-providers"></a>Integrierte Keystore-Anbieter

Der ODBC-Treiber für SQL Server enthält die folgenden integrierten Keystore-Anbieter:

| Name | und Beschreibung | Name des Anbieters (Metadaten) |Verfügbarkeit|
|:---|:---|:---|:---|
|Azure-Schlüsseltresor |Speichern von CMKs in einem Azure-Schlüsseltresor | `AZURE_KEY_VAULT` |Windows, macOS, Linux|
|Windows-Zertifikatspeicher|CMKs lokal gespeichert, in der Windows-keystore| `MSSQL_CERTIFICATE_STORE`|Windows|

- Sie (oder der Datenbankadministrator) müssen sicherstellen, dass der in den Metadaten des Spaltenhauptschlüssels konfigurierte Anbietername richtig ist und der Pfad des Spaltenhauptschlüssels dem Schlüsselpfadformat für den angegebenen Anbieter entspricht. Es wird empfohlen, dass Sie die Schlüssel mithilfe von Tools wie SQL Server Management Studio konfigurieren, die die gültigen Anbieternamen und Schlüsselpfade automatisch generieren, wenn die Anweisung [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md) ausgegeben wird.

- Sie müssen sicherstellen, dass die Anwendung auf den Schlüssel im Schlüsselspeicher zugreifen kann. Dies kann das Gewähren des Zugriffs auf den Schlüssel und/oder Schlüsselspeicher für die Anwendung (abhängig vom Schlüsselspeicher) oder das Ausführen anderer wichtiger speicherspezifischer Konfigurationsschritte beinhalten. Für den Zugriff auf Azure Key Vault, müssen Sie z. B. Geben Sie die richtigen Anmeldeinformationen zum Keystore ein.

### <a name="using-the-azure-key-vault-provider"></a>Verwenden des Azure Key Vault-Anbieters

Azure Key Vault ist eine praktische Möglichkeit zum Speichern von Spaltenhauptschlüsseln für Always Encrypted (insbesondere, wenn Ihre Anwendungen in Azure gehostet werden). Der ODBC-Treiber für SQL Server unter Linux, MacOS und Windows enthält einen integrierten Speicheranbieter für spaltenhauptschlüssel für Azure Key Vault. Finden Sie unter [Azure Key Vault – Schritt für Schritt](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/), [erste Schritte mit Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/), und [Erstellen von Spaltenhauptschlüsseln in Azure Key Vault](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2) für Weitere Informationen zum Konfigurieren eines Azure-Schlüssels Tresor für Always Encrypted.

> [!NOTE]
> Unter Linux und MacOS für Driver, Version 17.2 und spätere `libcurl` ist erforderlich, um diesen Anbieter nutzen können, ist jedoch nicht explizite Abhängigkeit, da er nicht von anderen Vorgängen mit dem Treiber erforderlich ist. Wenn ein Fehler aufgetreten ist im Hinblick auf `libcurl`, sicherzustellen, dass es installiert ist.

Der Treiber unterstützt die Authentifizierung bei Azure Key Vault mithilfe der folgenden Typen von Anmeldeinformationen:

- Benutzername/Kennwort - sind die Anmeldeinformationen den Namen des Azure Active Directory-Benutzer und das zugehörige Kennwort mit dieser Methode.

- Client-ID/Geheimnis - mit dieser Methode sind die Anmeldeinformationen ein Anwendungsclient-ID und einen geheimen Anwendungsschlüssel.

- Verwaltete Dienstidentität - Anmeldeinformationen mit dieser Methode sind, vom System zugewiesener Identität oder vom Benutzer zugewiesene Identität. Für die vom Benutzer zugewiesene Identität wird Benutzer-ID auf die Objekt-ID, der die Identität des Benutzers festgelegt.

Damit um den Treiber CMKs in AKV gespeichert werden, für die spaltenverschlüsselung verwenden zu können, verwenden Sie die folgenden Connection-String-only-Schlüsselwörter:

|Anmeldeinformationen| `KeyStoreAuthentication` |`KeyStorePrincipalId`| `KeyStoreSecret` |
|-|-|-|-|
|Benutzername/Kennwort| `KeyVaultPassword`|Benutzerprinzipalname|Kennwort|
|Client-ID /-Geheimnis| `KeyVaultClientSecret`|Client-ID|Secret|

#### <a name="example-connection-strings"></a>Exemplarische Verbindungszeichenfolgen

Die folgenden Verbindungszeichenfolgen zeigen, wie Azure Key Vault mit den zwei Anmeldeinformationstypen zu authentifizieren:

**Client-ID/geheimer Schlüssel**:

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultClientSecret;KeyStorePrincipalId=<clientId>;KeyStoreSecret=<secret>
```

**Benutzername/Kennwort**:

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultPassword;KeyStorePrincipalId=<username>;KeyStoreSecret=<password>
```

Keine weiteren ODBC-anwendungsänderungen sind erforderlich, auf die Azure-Schlüsseltresor für die CMK-Speicherung verwenden.

### <a name="using-the-windows-certificate-store-provider"></a>Verwenden des Windows-Zertifikatspeicheranbieters

Der ODBC-Treiber für SQL Server unter Windows enthält einen integrierten Speicheranbieter für spaltenhauptschlüssel für den Windows Store-Zertifikat, mit dem Namen `MSSQL_CERTIFICATE_STORE`. (Dieser Anbieter ist nicht unter MacOS oder Linux verfügbar.) Mit diesem Anbieter der CMK lokal auf dem Clientcomputer gespeichert, und ist keine zusätzliche Konfiguration von der Anwendung für die Verwendung mit dem Treiber erforderlich. Allerdings muss die Anwendung auf das Zertifikat und seinen privaten Schlüssel im Speicher zugreifen. Weitere Informationen finden Sie unter [Erstellen und Speichern von Spaltenhauptschlüsseln (Always Encrypted)](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted).

### <a name="using-custom-keystore-providers"></a>Verwenden benutzerdefinierter Keystore-Anbieter

Der ODBC-Treiber für SQL Server unterstützt auch benutzerdefinierte Drittanbieter-Keystore-Anbieter mithilfe der CEKeystoreProvider-Schnittstelle. Dadurch wird eine Anwendung zu laden, Abfragen und die Keystore-Anbieter so konfigurieren, dass sie vom Treiber verwendet werden können, um Zugriff auf verschlüsselte Spalten. Anwendungen können auch direkt mit einer Keystore-Anbieter zum Verschlüsseln CEKs, für die in SQL Server zu speichern und Ausführen von Aufgaben über den Zugriff auf verschlüsselte Spalten mit dem ODBC-interagieren; Weitere Informationen finden Sie unter [benutzerdefinierte Keystore-Anbieter](../../connect/odbc/custom-keystore-providers.md).

Zwei Verbindungsattribute werden verwendet, für die Interaktion mit benutzerdefinierten Keystore-Anbieter. Die Überladungen sind:

- `SQL_COPT_SS_CEKEYSTOREPROVIDER`

- `SQL_COPT_SS_CEKEYSTOREDATA`

Ersteres dient zum Laden und Auflisten von geladenen Keystore-Anbieter, während letztere ermöglicht das Anwendungsanbieter Kommunikation. Diese Verbindungsattribute können jederzeit verwendet werden, vor oder nach dem Herstellen einer Verbindungs, da die Interaktion mit dem Application-Dienstanbieter keine Kommunikation mit SQL Server verbunden ist. Jedoch, da der Treiber noch nicht geladen wurde, festlegen und Abrufen dieser Attribute vor dem Herstellen einer Verbindung bewirkt, dass vom Treiber-Manager verarbeitet werden und möglicherweise nicht die erwarteten Ergebnisse liefern.

#### <a name="loading-a-keystore-provider"></a>Laden einen Keystore-Anbieter.

Festlegen der `SQL_COPT_SS_CEKEYSTOREPROVIDER` Verbindungsattribut kann eine Clientanwendung eine Anbieterbibliothek, die darin enthaltenen Keystore-Anbieter für die Verwendung zur Verfügung stellen zu laden.

```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```

| Argument | und Beschreibung |
|:---|:---|
|`ConnectionHandle`|[Eingabe] Verbindungshandle. Muss eine gültige Verbindung-Handle, jedoch über ein Verbindungshandle geladen Anbieter zugegriffen werden von einer anderen im selben Prozess.|
|`Attribute`|[Eingabe] Attribut: die `SQL_COPT_SS_CEKEYSTOREPROVIDER` Konstanten.|
|`ValuePtr`|[Eingabe] Zeiger auf eine Null-terminierte Zeichenfolge, die den Dateinamen des der Anbieterbibliothek angibt. Für SQLSetConnectAttrA ist dies eine ANSI-Zeichenfolge ("multibyte"). Für SQLSetConnectAttrW ist dies eine Unicodezeichenfolge (Wchar_t).|
|`StringLength`|[Eingabe] Die Länge der Zeichenfolge der ValuePtr oder SQL_NTS.|

Versucht, dass der Treiber beim Laden der Bibliothek, die durch den mit der Plattform definierte dynamische Bibliothek Lademechanismus ValuePtr-Parameter identifizierte (`dlopen()` unter Linux und MacOS, `LoadLibrary()` für Windows), und alle darin definiert, um die Liste der Anbieter hinzugefügt der Anbieter bekannt, dass der Treiber. Die folgenden Fehler können auftreten:

| Fehler | und Beschreibung |
|:--|:--|
|`CE203`|Die dynamische Bibliothek konnte nicht geladen werden.|
|`CE203`|Das Symbol "CEKeyStoreProvider" exportiert wurde in der Bibliothek nicht gefunden.|
|`CE203`|Eine oder mehrere Anbieter in der Bibliothek sind bereits geladen.|

`SQLSetConnectAttr` Gibt zurück, der üblichen Fehler oder Erfolg-Werte, und zusätzliche Informationen finden Sie auf Fehler, die über die standardmäßigen ODBC-Mechanismus Diagnose erfolgt sind.

> [!NOTE]
> Der Programmierer muss stellen Sie sicher, dass alle benutzerdefinierten Anbieter geladen werden, vor dem Senden einer Abfrage aus, dass diese über eine Verbindung. Andernfalls wird folgender Fehler ausgelöst:

| Fehler | und Beschreibung |
|:--|:--|
|`CE200`|Keystore-Anbieter %1 wurde nicht gefunden. Stellen Sie sicher, dass die entsprechenden Keystore-Anbieterbibliothek geladen wurde.|

> [!NOTE]
> Keystore-Anbieter in einer Implementierung sollten die Verwendung von `MSSQL` den Namen ihrer benutzerdefinierten Anbietern. Dieser Begriff ist ausschließlich für die Verwendung durch Microsoft reserviert und kann dazu führen, dass Konflikte mit zukünftigen integrierte Anbieter. Mithilfe dieser Begriff, den Namen eines benutzerdefinierten Anbieters, möglicherweise in eine ODBC-Warnung.

#### <a name="getting-the-list-of-loaded-providers"></a>Abrufen der Liste der geladenen Anbieter

Dieses Verbindungsattribut abrufen kann eine Clientanwendung, um zu bestimmen, die Keystore-Anbieter, die derzeit geladen, im Treiber (einschließlich derer erstellt.) Dies kann nur nach dem Herstellen einer Verbindung ausgeführt werden.

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```

| Argument | und Beschreibung |
|:---|:---|
|`ConnectionHandle`|[Eingabe] Verbindungshandle. Muss eine gültige Verbindung-Handle, jedoch über ein Verbindungshandle geladen Anbieter zugegriffen werden von einer anderen im selben Prozess.|
|`Attribute`|[Eingabe] Attribut zum Abrufen: die `SQL_COPT_SS_CEKEYSTOREPROVIDER` Konstanten.|
|`ValuePtr`|[Ausgabe] Ein Zeiger auf Speicher, an den nächsten geladenen Anbieternamen zurück.|
|`BufferLength`|[Eingabe] Die Länge des Puffers ValuePtr.|
|`StringLengthPtr`|[Ausgabe] Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen) zurückgegeben. verfügbar für die zurückzugebenden in \*ValuePtr. Wenn ValuePtr ein null-Zeiger ist, wird keine Länge zurückgegeben. Wenn Sie den Wert des Attributs ist eine Zeichenfolge, und die Anzahl der Bytes, die für die Rückgabe verfügbar ist größer als die Pufferlänge abzüglich der Länge von Null-Terminierung vorliegt Zeichen, die Daten in \*ValuePtr auf die Pufferlänge abzüglich der Länge des abgeschnitten der NULL-Terminierungszeichen und Null-terminiert ist vom Treiber.|

Damit wird die gesamte Liste abrufen, alle Get-Vorgang gibt den aktuellen Anbieter Namen zurück, und erhöht einen internen Indikator mit dem nächsten fort. Sobald diese Zähler am Ende der Liste, eine leere Zeichenfolge ist ("") zurückgegeben wird, und der Zähler wird zurückgesetzt; aufeinander folgende Get-Vorgängen fortzufahren vom Anfang der Liste klicken Sie dann erneut.

### <a name="communicating-with-keystore-providers"></a>Kommunikation mit einer Keystore-Anbieter

Die `SQL_COPT_SS_CEKEYSTOREDATA` Verbindungsattribut es einer Clientanwendung mit geladenen Keystore-Anbieter zu kommunizieren, für die Konfiguration zusätzlicher Parameter Erstellen neuer Materialien usw. ermöglicht. Die Kommunikation zwischen einer Clientanwendung und eines Anbieters folgt eine einfache Anforderung / Antwort-Protokoll basiert auf Get und Set-Anforderungen mithilfe dieses Verbindungsattribut. Nur von der Clientanwendung wird die Kommunikation initiiert.

> [!NOTE]
> Aufgrund die Art der ODBC-Aufrufe CEKeyStoreProviders reagieren, (SQLGet/SetConnectAttr), die ODBC-Schnittstelle unterstützt nur das Festlegen von Daten in der Auflösung des den Verbindungskontext.

Die Anwendung kommuniziert mit Keystore-Anbieter über den Treiber über die CEKeystoreData-Struktur:

```
typedef struct CEKeystoreData {
wchar_t *name;
unsigned int dataSize;
char data[];
} CEKEYSTOREDATA;
```

| Argument | und Beschreibung |
|:---|:---|
|`name`|[Eingabe] Bei festgelegt ist, den Namen des Anbieters auf dem die Daten gesendet werden. Bei den Get ignoriert. Null-terminiert, Breitzeichen-Zeichenfolge.|
|`dataSize`|[Eingabe] Die Größe des Datenarrays der Struktur nach.|
|`data`|[InOut] Nach der Menge der Daten an den Anbieter gesendet werden. Dies kann beliebige Daten sein. der Treiber versucht nicht, um es zu interpretieren. Bei den Get Lesen der Puffer zum Empfangen der Daten vom Anbieter.|

#### <a name="writing-data-to-a-provider"></a>Schreiben von Daten an einen Anbieter

Ein `SQLSetConnectAttr` rufen mithilfe der `SQL_COPT_SS_CEKEYSTOREDATA` Attribut schreibt ein "Datenpaket" in der angegebenen Keystore-Anbieter.
```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```

| Argument | und Beschreibung |
|:---|:---|
|`ConnectionHandle`| [Eingabe] Verbindungshandle. Muss eine gültige Verbindung-Handle, jedoch über ein Verbindungshandle geladen Anbieter zugegriffen werden von einer anderen im selben Prozess.|
|`Attribute`|[Eingabe] Attribut: die `SQL_COPT_SS_CEKEYSTOREDATA` Konstanten.|
|`ValuePtr`|[Eingabe] Zeiger auf eine CEKeystoreData-Struktur. Das Feld "Name" der Struktur identifiziert den Anbieter für den die Daten vorgesehen ist.|
|`StringLength`|[Eingabe] SQL_IS_POINTER-Konstante|

Zusätzliche detaillierte Fehlerinformationen abgerufen werden kann, über [SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx).

> [!NOTE]
> Der Anbieter können das Verbindungshandle ordnen Sie die geschriebenen Daten zu einer bestimmten Verbindung, wenn er möchte. Dies ist nützlich für die Implementierung von pro-Verbindungskonfiguration. Außerdem kann den Verbindungskontext ignorieren und behandeln Sie die Daten identisch, unabhängig von die Verbindung verwendet, um die Daten zu senden. Finden Sie unter [Zuordnung Kontext](../../connect/odbc/custom-keystore-providers.md#context-association) für Weitere Informationen.

#### <a name="reading-data-from-a-provider"></a>Lesen von Daten von einem Anbieter

Ein Aufruf von `SQLGetConnectAttr` mithilfe der `SQL_COPT_SS_CEKEYSTOREDATA` Attribut liest Daten aus einem "Paket" *der letzten-geschrieben-to* Anbieter. Wenn keine vorhanden war, tritt ein Fehler bei Funktionssequenz. Keystore-Anbieter während der Implementierung werden empfohlen, die Unterstützung von "Dummy Schreibvorgängen" von 0 Bytes als eine Möglichkeit, ohne dass andere Nebenwirkungen, Anbieter für Lesevorgänge auswählen, wenn es sinnvoll, die dazu.

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```

| Argument | und Beschreibung |
|:---|:---|
|`ConnectionHandle`|[Eingabe] Verbindungshandle. Muss eine gültige Verbindung-Handle, jedoch über ein Verbindungshandle geladen Anbieter zugegriffen werden von einer anderen im selben Prozess.|
|`Attribute`|[Eingabe] Attribut zum Abrufen: die `SQL_COPT_SS_CEKEYSTOREDATA` Konstanten.|
|`ValuePtr`|[Ausgabe] Ein Zeiger auf eine CEKeystoreData-Struktur, in dem die Daten aus dem Anbieter gelesen, wird eingefügt.|
|`BufferLength`|[Eingabe] SQL_IS_POINTER-Konstante|
|`StringLengthPtr`|[Ausgabe] Ein Zeiger auf einen Puffer, in die Pufferlänge zurückgegeben werden sollen. Wenn * ValuePtr ist ein null-Zeiger ist, wird keine Länge zurückgegeben.|

Der Aufrufer muss stellen Sie sicher, dass der Anbieter zum Schreiben in ein Puffer mit einer ausreichenden Länge, die nach der Struktur CEKEYSTOREDATA zugeordnet ist. Bei der Rückgabe wird der DataSize-Feld mit der tatsächlichen Länge der Daten, die vom Anbieter gelesen aktualisiert. Zusätzliche detaillierte Fehlerinformationen abgerufen werden kann, über [SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx).

Diese Schnittstelle stellt keine zusätzlichen Anforderungen an die auf das Format der Daten zwischen einer Anwendung und einer Keystore-Anbieter übertragen. Jeder Anbieter kann eigene Format Protokoll-/Daten nach Bedarf definieren.

Ein Beispiel für einen eigenen Keystore-Anbieter implementieren, finden Sie unter [benutzerdefinierte Keystore-Anbieter](../../connect/odbc/custom-keystore-providers.md)

## <a name="limitations-of-the-odbc-driver-when-using-always-encrypted"></a>Einschränkungen des ODBC-Treibers bei Verwendung von Always Encrypted

### <a name="asynchronous-operations"></a>Asynchrone Vorgänge
Während der ODBC-Treiber die Verwendung von kann [asynchrone Vorgänge](../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md) mit Always Encrypted ist vorhanden Auswirkungen auf die Leistung der Vorgänge Wenn Always Encrypted aktiviert ist. Der Aufruf von `sys.sp_describe_parameter_encryption` zum verschlüsselungsmetadaten zu ermitteln, für die Anweisung blockiert wird, und dazu, den Treiber den Server dass führt zurückgeben die Metadaten vor der Rückgabe wartet `SQL_STILL_EXECUTING`.

### <a name="retrieve-data-in-parts-with-sqlgetdata"></a>Abrufen von Daten in Webparts mit SQLGetData
Bevor ODBC Driver 17 for SQL Server, verschlüsselt werden nicht Zeichen- und Binärspalten in Teilen mit SQLGetData abgerufen. Nur ein Aufruf von SQLGetData kann vorgenommen werden, mit einem Puffer von ausreichender Größe die gesamte Spalte Daten enthalten.

### <a name="send-data-in-parts-with-sqlputdata"></a>Senden von Daten in Webparts mit SQLPutData
Daten einfügen oder Vergleich können nicht in Teile mit SQLPutData gesendet werden. Nur einen Aufruf von SQLPutData kann vorgenommen werden, mit einem Puffer, der die gesamten Daten enthält. Verwenden Sie zum Einfügen von long-Daten in verschlüsselte Spalten ein, die API für Massenkopieren, im nächsten Abschnitt beschrieben, mit einer Eingabedaten-Datei ein.

### <a name="encrypted-money-and-smallmoney"></a>Verschlüsselte Money und smallmoney
Verschlüsselt **Geld** oder **Smallmoney** Spalten können nicht durch Parameter angewendet werden, da es ist nicht spezifisch ODBC-Datentyp der Zuordnungen, die diese Typen, was zu Fehlern Operanden Typ in Konflikt stehen.

## <a name="bulk-copy-of-encrypted-columns"></a>Massenkopieren von verschlüsselten Spalten

Verwenden der [Funktionen von SQL-Massenkopieren](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md) und **Bcp** -Hilfsprogramm wird seit ODBC Driver 17 for SQL Server mit Always Encrypted unterstützt. Sowohl als nur-Text (auf verschlüsselte einfügen und entschlüsselter auf-Abruf) verschlüsselten Text (wörtlich übertragen) eingefügt werden kann und mit den Massenkopiervorgang abgerufen (Bcp_&#42;) APIs und die **Bcp** Hilfsprogramm.

- Chiffretext 'varbinary(max)'-Format (z. B. für das Laden von Massendaten in eine andere Datenbank) abgerufen werden, ohne eine Verbindung herstellen die `ColumnEncryption` Option (oder legen ihn auf `Disabled`) und eine BCP OUT-Vorgang aus.

- Zum Einfügen und Abrufen von nur-Text und können den Treiber transparent Durchführen von Verschlüsselung und Entschlüsselung als erforderlich festlegen `ColumnEncryption` zu `Enabled` ist ausreichend. Die Funktionalität der BCP-API ist anderweitig nicht geändert.

- Zum Einfügen von Chiffretext 'varbinary(max)'-Format (z. B. im oben abgerufenen) legen Sie die `BCPMODIFYENCRYPTED` option auf "true", und führen Sie einen IN der BCP-Vorgang. Sicherstellen Sie in der Reihenfolge für die resultierenden Daten zu entschlüsselnden werden, dass das Ziel CEK mit der Spalte identisch, die von dem der verschlüsselte Text, die ursprünglich abgerufen wurde.

Bei Verwendung der **Bcp** Dienstprogramm: Steuern der `ColumnEncryption` festlegen, verwenden Sie die Option-d, und geben Sie einen DSN, der den gewünschten Wert enthält. Um verschlüsselte Text einzufügen, stellen Sie sicher die `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` des Benutzers aktiviert ist.

Die folgende Tabelle enthält eine Zusammenfassung der Aktionen, bei einer verschlüsselten Spalte:

|`ColumnEncryption`|BCP-Richtung|und Beschreibung|
|----------------|-------------|-----------|
|`Disabled`|OUT (zum Client)|Ruft die Chiffretext ab. Ist der beobachtete Datentyp **'varbinary(max)'**.|
|`Enabled`|OUT (zum Client)|Ruft nur-Text ab. Der Treiber wird die Spaltendaten zu entschlüsseln.|
|`Disabled`|(Beim Server)|Fügt ein verschlüsselten Text. Dies ist für den Clientkontext verschlüsselte Daten verschieben, ohne dass es vorgesehen, entschlüsselt werden. Der Vorgang schlägt fehl, wenn die `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` Option ist für den Benutzer nicht festgelegt oder BCPMODIFYENCRYPTED ist nicht auf dem Verbindungshandle festgelegt. Weitere Informationen finden Sie weiter unten.|
|`Enabled`|(Beim Server)|Fügt ein nur-Text. Der Treiber verschlüsselt die Daten der Spalte.|

### <a name="the-bcpmodifyencrypted-option"></a>Die BCPMODIFYENCRYPTED-option

Um datenbeschädigung zu verhindern, die Server normalerweise lässt keine verschlüsselten Text direkt in eine verschlüsselte Spalte eingefügt, und daher dazu nicht möglich; allerdings für das Massenladen von verschlüsselten Daten, die die BCP-API, Festlegen der `BCPMODIFYENCRYPTED` [Bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) Option auf "true" ermöglicht Chiffretext direkt eingefügt werden soll und reduziert das Risiko einer Beschädigung der verschlüsselte Daten über die Einstellung der `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` Option für das Benutzerkonto auf. Dennoch die Schlüssel müssen die Daten übereinstimmen, und es ist eine gute Idee, führen Sie einige schreibgeschützte Überprüfungen der eingefügten Daten nach der Einfügemarke Bulk und vor der weiteren Verwendung.

Weitere Informationen finden Sie unter [Migrieren von durch Always Encrypted geschützten sensiblen Daten](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md).

## <a name="always-encrypted-api-summary"></a>Always Encrypted-API-Zusammenfassung

### <a name="connection-string-keywords"></a>Schlüsselwörter für Verbindungszeichenfolgen

|Name|und Beschreibung|  
|----------|-----------------|  
|`ColumnEncryption`|Gültige Werte sind `Enabled` / `Disabled`.<br>`Enabled`: aktiviert Always Encrypted-Funktionen für die Verbindung.<br>`Disabled`: deaktiviert Always Encrypted-Funktionen für die Verbindung. <br><br>Der Standardwert ist `Disabled`.|  
|`KeyStoreAuthentication` | Gültige Werte: `KeyVaultPassword`, `KeyVaultClientSecret` |
|`KeyStorePrincipalId` | Wenn `KeyStoreAuthentication`  =  `KeyVaultPassword`, legen Sie diesen Wert in einen gültigen Namen der Azure Active Directory-Benutzer-Dienstprinzipal. <br>Wenn `KeyStoreAuthetication`  =  `KeyVaultClientSecret` legen diesen Wert auf einen gültigen Azure Active Directory-Anwendung Client-ID |
|`KeyStoreSecret` | Wenn `KeyStoreAuthentication`  =  `KeyVaultPassword` legen Sie diesen Wert auf das Kennwort für den entsprechenden Benutzernamen. <br>Wenn `KeyStoreAuthentication`  =  `KeyVaultClientSecret` legen diesen Wert auf das Anwendungsgeheimnis, das mit einem gültigen Azure Active Directory-Anwendung Client-ID verknüpft ist |


### <a name="connection-attributes"></a>Verbindungsattribute

|Name|Typ|und Beschreibung|  
|----------|-------|----------|  
|`SQL_COPT_SS_COLUMN_ENCRYPTION`|Vor dem Verbinden|`SQL_COLUMN_ENCRYPTION_DISABLE` (0) – deaktivieren, die Always Encrypted <br>`SQL_COLUMN_ENCRYPTION_ENABLE` (1): Aktivieren von Always Encrypted|
|`SQL_COPT_SS_CEKEYSTOREPROVIDER`|Nach Herstellen der Verbindung|[Set] Beim Laden von CEKeystoreProvider<br>[Get] Gibt den Namen einer CEKeystoreProvider zurück|
|`SQL_COPT_SS_CEKEYSTOREDATA`|Nach Herstellen der Verbindung|[Set] Schreiben von Daten in CEKeystoreProvider<br>[Get] Lesen von Daten aus CEKeystoreProvider|
|`SQL_COPT_SS_CEKCACHETTL`|Nach Herstellen der Verbindung|[Set] Legen Sie den CEK-Cache-Gültigkeitsdauer (TTL)<br>[Get] Abrufen der aktuellen CEK Caches Gültigkeitsdauer (TTL)|
|`SQL_COPT_SS_TRUSTEDCMKPATHS`|Nach Herstellen der Verbindung|[Set] Legen Sie den vertrauenswürdigen Zeiger des CMK-Pfade<br>[Get] Abrufen des aktuellen vertrauenswürdigen CMK-Pfade Zeigers|

### <a name="statement-attributes"></a>Anweisungsattribute

|Name|und Beschreibung|  
|----------|-----------------|  
|`SQL_SOPT_SS_COLUMN_ENCRYPTION`|`SQL_CE_DISABLED` (0) – always Encrypted ist für die Anweisung deaktiviert <br>`SQL_CE_RESULTSETONLY` (1) – nur entschlüsseln. Resultsets und Rückgabewerte werden entschlüsselt und Parameter werden nicht verschlüsselt. <br>`SQL_CE_ENABLED` (3) – always Encrypted ist aktiviert und für Parameter und die Ergebnisse|

### <a name="descriptor-fields"></a>Deskriptorfelder

|IPD-Feld|Instanzgröße bzw.-Typ|Standardwert|und Beschreibung|
|-|-|-|-|  
|`SQL_CA_SS_FORCE_ENCRYPT` (1236)|WORD (2 Byte)|0|Wenn 0 (Standard): Entscheidung, ob dieser Parameter verschlüsseln richtet sich nach der Verfügbarkeit von Metadaten.<br><br>Wenn ungleich NULL: Wenn verschlüsselungsmetadaten für diesen Parameter verfügbar ist, wird sie verschlüsselt. Andernfalls die Anforderung schlägt fehl, Fehlercode: [CE300] [Microsoft] [ODBC Driver 13 für SQL Server], die obligatorische Verschlüsselung wurde für einen Parameter angegeben, jedoch keine verschlüsselungsmetadaten wurde vom Server bereitgestellt wird.|

### <a name="bcpcontrol-options"></a>Bcp_control-Optionen

|Optionsname|Standardwert|und Beschreibung|
|-|-|-|
|`BCPMODIFYENCRYPTED` (21)|FALSE|Bei "true", können varbinary(max)-Werte in eine verschlüsselte Spalte eingefügt werden soll. Bei "FALSE" wird verhindert, dass einfügen, wenn richtigen Typ und die Verschlüsselung Metadaten angegeben wird.|

## <a name="see-also"></a>Weitere Informationen

- [„Immer verschlüsselt“ (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Always Encrypted-Blog](https://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/)

