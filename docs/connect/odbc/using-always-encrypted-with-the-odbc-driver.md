---
title: Verwenden von Always Encrypted mit ODBC Driver for SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/01/2018
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02e306b8-9dde-4846-8d64-c528e2ffe479
ms.author: v-chojas
author: MightyPen
ms.openlocfilehash: cc6deae9a2ddcb11675586ffd8777644aff00672
ms.sourcegitcommit: e821cd8e5daf95721caa1e64c2815a4523227aa4
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702705"
---
# <a name="using-always-encrypted-with-the-odbc-driver-for-sql-server"></a>Verwenden von Always Encrypted mit ODBC Driver for SQL Server
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

### <a name="applicable-to"></a>Anwendbar auf

- ODBC Driver 13.1 for SQL Server
- ODBC Driver 17 for SQL Server

### <a name="introduction"></a>Einführung

Dieser Artikel bietet Informationen zum Entwickeln von ODBC-Anwendungen mithilfe von [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) oder [Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves.md) und dem [ODBC-Treiber für SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

Always Encrypted ermöglicht Clientanwendungen das Verschlüsseln von vertraulichen Daten in einer Weise, dass weder die Daten noch die Verschlüsselungsschlüssel zu irgendeinem Zeitpunkt gegenüber SQL Server oder Azure SQL-Datenbank offengelegt werden. Ein Treiber, bei dem Always Encrypted aktiviert ist, z.B. ODBC Driver for SQL Server, erreicht dies durch die transparente Ver- und Entschlüsselung von sensiblen Daten in der Clientanwendung. Der Treiber ermittelt automatisch, welche Abfrageparameter vertraulichen Datenbankspalten (mit Always Encrypted geschützt) entsprechen. Die Werte dieser Parameter werden dann vor der Übergabe an SQL Server oder Azure SQL-Datenbank verschlüsselt. Auf ähnliche Weise entschlüsselt der Treiber die Daten transparent, die von verschlüsselten Datenbankspalten in Abfrageergebnissen empfangen werden. *Always Encrypted mit Secure Enclaves* erweitert dieses Feature um umfangreichere Funktionen für vertrauliche Daten und sorgt gleichzeitig dafür, dass diese Daten vertraulich bleiben.

Weitere Informationen finden Sie unter [Always encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) und [Always Encrypted mit sicheren Enklaven](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

### <a name="prerequisites"></a>Voraussetzungen

Konfigurieren Sie Always Encrypted in Ihrer Datenbank. Dies umfasst die Bereitstellung von Always Encrypted-Schlüsseln und die Einrichtung der Verschlüsselung für ausgewählte Datenbankspalten. Wenn Sie nicht bereits über eine Datenbank verfügen, für die Always Encrypted konfiguriert ist, befolgen Sie die Anweisungen in [Erste Schritte mit Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). Insbesondere sollte Ihre Datenbank die Metadatendefinitionen für einen Spaltenhauptschlüssel (Column Master Key, CMK), einen Spaltenverschlüsselungsschlüssel (Column Encryption Key, CEK) und eine Tabelle mit mindestens einer Spalte enthalten, die mit diesem CEK verschlüsselt ist.

### <a name="enabling-always-encrypted-in-an-odbc-application"></a>Aktivieren von Always Encrypted in einer ODBC-Anwendung

Die einfachste Möglichkeit zum Aktivieren von sowohl Parameterverschlüsselung als auch Spaltenentschlüsselung in verschlüsselten Resultsets besteht darin, den Wert für das Schlüsselwort der Verbindungszeichenfolge `ColumnEncryption` auf **Aktiviert** festzulegen. Im Folgenden finden Sie ein Beispiel für eine Verbindungszeichenfolge, mit der Always Encrypted aktiviert wird:

```
SQLWCHAR *connString = L"Driver={ODBC Driver 13 for SQL Server};Server={myServer};Trusted_Connection=yes;ColumnEncryption=Enabled;";
```

Always Encrypted kann auch in der DSN-Konfiguration mit demselben Schlüssel und demselben Wert (die durch die Einstellung der Verbindungszeichenfolge, falls vorhanden, überschrieben werden) oder programmgesteuert über das Attribut `SQL_COPT_SS_COLUMN_ENCRYPTION` zur Verbindungsherstellung aktiviert werden. Wird es auf diese Weise festgelegt, wird der in der Verbindungszeichenfolge oder im DSN festgelegte Wert überschrieben:

```
 SQLSetConnectAttr(hdbc, SQL_COPT_SS_COLUMN_ENCRYPTION, (SQLPOINTER)SQL_COLUMN_ENCRYPTION_ENABLE, 0);
```

Nachdem Always Encrypted für die Verbindung aktiviert wurde, kann das Verhalten für einzelne Abfragen angepasst werden. Weitere Informationen finden Sie weiter unten im Abschnitt [Kontrollieren der Auswirkungen von Always Encrypted auf die Leistung](#controlling-the-performance-impact-of-always-encrypted).

Beachten Sie, dass das Aktivieren von Always Encrypted für eine erfolgreiche Verschlüsselung oder Entschlüsselung nicht ausreichend ist. Stellen Sie außerdem Folgendes sicher:

- Die Anwendung verfügt über die Datenbankberechtigungen *VIEW ANY COLUMN MASTER KEY DEFINITION* und *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* , die für den Zugriff auf die Metadaten in der Datenbank über Always Encrypted-Schlüssel erforderlich sind. Einzelheiten hierzu finden Sie unter [Datenbankberechtigungen](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).

- Die Anwendung muss auf den CMK zugreifen können, der die CEKs für die abgefragten verschlüsselten Spalten schützt. Dies hängt vom Schlüsselspeicheranbieter ab, bei dem der CMK gespeichert wird. Weitere Informationen finden Sie im Abschnitt [Arbeiten mit Spaltenhauptschlüsselspeichern](#working-with-column-master-key-stores).

### <a name="enabling-always-encrypted-with-secure-enclaves"></a>Aktivieren von Always Encrypted mit Secure Enclaves

Ab Version 17,4 unterstützt der Treiber Always Encrypted mit sicheren Enklaven. Wenn Sie die Verwendung von Enclave beim Herstellen einer Verbindung mit SQL Server 2019 oder höher aktivieren `ColumnEncryption` möchten, legen Sie den DSN, die Verbindungs Zeichenfolge oder das Verbindungs Attribut auf den Namen des Enclave-und Nachweis Protokolls sowie die zugehörigen Nachweis Daten durch ein Komma getrennt fest. In Version 17,4 wird nur der [virtualisierungsbasierte Sicherheits](https://www.microsoft.com/security/blog/2018/06/05/virtualization-based-security-vbs-memory-enclaves-data-protection-through-isolation/) Enclave- Typ und das von `VBS-HGS`angegebene [Host-Überwachungsdienst-Nachweis](https://docs.microsoft.com/windows-server/security/set-up-hgs-for-always-encrypted-in-sql-server) Protokoll unterstützt. Geben Sie die URL des Nachweis Servers an, um Sie zu verwenden. Beispiel:

```
Driver=ODBC Driver 17 for SQL Server;Server=yourserver.yourdomain;Trusted_Connection=Yes;ColumnEncryption=VBS-HGS,http://attestationserver.yourdomain/Attestation
```

Wenn der Server und der Nachweis Dienst ordnungsgemäß konfiguriert sind, sowie für Enclave-aktivierte CMAS und ceert für die gewünschten Spalten, sollten Sie nun Abfragen ausführen können, die die Enclave verwenden, wie z. b. direkte Verschlüsselung und umfangreiche Berechnungen, zusätzlich zum vorhandene Funktionen, die von Always Encrypted bereitgestellt werden. Weitere Informationen finden Sie [unter Konfigurieren von Always Encrypted mit sicheren Enklaven](../../relational-databases/security/encryption/configure-always-encrypted-enclaves.md) .


### <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Abrufen und Ändern von Daten in verschlüsselten Spalten

Nachdem Sie Always Encrypted für eine Verbindung aktiviert haben, können Sie ODBC-Standard-APIs verwenden. Die ODBC-APIs können Daten in verschlüsselten Daten Bank Spalten abrufen oder ändern. Die folgenden Dokumentations Elemente können dabei helfen:

- [ODBC-Beispielcode](cpp-code-example-app-connect-access-sql-db.md)
- [ODBC-Programmierreferenz](../../odbc/reference/odbc-programmer-s-reference.md)

Die Anwendung muss über die erforderlichen Daten Bank Berechtigungen verfügen, und Sie muss in der Lage sein, auf den Spalten Hauptschlüssel zuzugreifen. Anschließend verschlüsselt der Treiber alle Abfrage Parameter, die auf verschlüsselte Spalten ausgerichtet sind. Der Treiber entschlüsselt auch Daten, die aus verschlüsselten Spalten abgerufen wurden. Der Treiber führt diese Verschlüsselung und Entschlüsselung ohne Unterstützung durch den Quellcode aus. Das Programm ist so, als ob die Spalten nicht verschlüsselt sind.

Wenn Always Encrypted nicht aktiviert ist, tritt bei Abfragen mit Parametern, die auf verschlüsselte Spalten ausgerichtet sind, ein Fehler auf. Daten können weiterhin aus verschlüsselten Spalten abgerufen werden, solange die Abfrage keine Parameter für verschlüsselte Spalten enthält. Der Treiber versucht jedoch nicht, die Daten zu entschlüsseln. Daher erhält die Anwendung die verschlüsselten Binärdaten (als Bytearrays).

In der folgenden Tabelle wird das Verhalten von Abfragen in Abhängigkeit davon zusammengefasst, ob Always Encrypted aktiviert ist:

|Abfragemerkmal | Always Encrypted ist aktiviert und die Anwendung kann auf die Schlüssel und Schlüsselmetadaten zugreifen.|Always Encrypted ist aktiviert und die Anwendung kann nicht auf die Schlüssel oder Schlüsselmetadaten zugreifen. | Always Encrypted ist deaktiviert|
|:---|:---|:---|:---|
| Parameter für verschlüsselte Spalten | Parameterwerte werden transparent verschlüsselt. | Fehler | Fehler|
| Daten von verschlüsselten Spalten ohne Parameter abrufen, die auf verschlüsselte Spalten ausgerichtet sind.| Ergebnisse von verschlüsselten Spalten werden transparent entschlüsselt. Die Anwendung erhält Klartextspaltenwerte. | Fehler | Ergebnisse von verschlüsselten Spalten werden nicht entschlüsselt. Die Anwendung erhält verschlüsselte Werte als Bytearrays.

Die folgenden Beispiele veranschaulichen das Abrufen und Ändern von Daten in verschlüsselten Spalten. Dabei wird eine Tabelle mit dem folgenden Schema angenommen: Beachten Sie, dass die Spalten „SSN“ und „BirthDate“ verschlüsselt werden.

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

#### <a name="data-insertion-example"></a>Beispiel für das Einfügen von Daten

In diesem Beispiel wird eine Zeile in die Tabelle „Patients“ eingefügt. Beachten Sie Folgendes:

- Es erfolgt keine spezielle Verschlüsselung im Beispielcode. Der Treiber erkennt und verschlüsselt automatisch die Werte der SSN- und Datumsparameter für verschlüsselte Spalten. Dadurch wird die Verschlüsselung für die Anwendung transparent.

- Die in die Datenbankspalten eingefügten Werte, einschließlich der verschlüsselten Spalten, werden als gebundene Parameter übergeben (siehe [SQLBindParameter-Funktion](https://msdn.microsoft.com/library/ms710963(v=vs.85).aspx)). Während die Verwendung von Parametern optional ist, wenn Werte an nicht verschlüsselte Spalten gesendet werden (obwohl es dringend empfohlen wird, da es dabei hilft, eine Einschleusung von SQL-Befehlen zu verhindern), ist sie für Werte erforderlich, die auf verschlüsselte Spalten ausgerichtet sind. Werden die in die Spalten „SSN“ oder „BirthDate“ eingefügten Werte als Literale übergeben, die in die Abfrageanweisung eingebettet sind, tritt ein Fehler auf, da der Treiber nicht versucht, Literale in Abfragen zu verschlüsseln oder anderweitig zu verarbeiten. Daher würde der Server sie zurückweisen, da sie mit den verschlüsselten Spalten inkompatibel sind.

- Der in die SSN-Spalte eingefügte SQL-Typ des Parameters wird auf „SQL_CHAR“ festgelegt, der dem SQL Server-Datentyp **char** zugeordnet wird (`rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);`). Wird der Typ des Parameters auf „SQL_WCHAR“ festgelegt, der **nchar** zugeordnet wird, tritt bei der Abfrage ein Fehler auf, da Always Encrypted keine serverseitigen Konvertierungen von verschlüsselten nchar-Werten in verschlüsselte char-Werte unterstützt. Informationen zur Zuordnung von Datentypen finden Sie unter [ODBC-Programmierreferenz – Anhang D: Datentypen](https://msdn.microsoft.com/library/ms713607.aspx).

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

#### <a name="plaintext-data-retrieval-example"></a>Beispiel für das Abrufen von Klartextdaten

Im folgenden Beispiel wird das Filtern von Daten auf Basis verschlüsselter Werte und das Abrufen von Klartextdaten aus verschlüsselten Spalten veranschaulicht. Beachten Sie Folgendes:

- Der in der WHERE-Klausel zum Filtern der Spalte „SSN“ verwendete Wert muss mit dem SQLBindParameter-Parameter übergeben werden, damit ihn der Treiber vor dem Senden an die Datenbank transparent verschlüsseln kann.

- Alle Werte werden vom Programm als Klartext ausgegeben, da der Treiber die aus den Spalten „SSN“ und „BirthDate“ abgerufenen Daten transparent entschlüsselt.

> [!NOTE]
> Abfragen können Gleichheits Vergleiche für verschlüsselte Spalten nur dann durchführen, wenn die Verschlüsselung deterministisch ist oder wenn die sichere Enclave aktiviert ist. Weitere Informationen finden Sie im Abschnitt [Auswählen der deterministischen oder zufälligen Verschlüsselung](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

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

#### <a name="ciphertext-data-retrieval-example"></a>Beispiel für das Abrufen von Chiffretextdaten

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

Always Encrypted unterstützt einige Konvertierungen für verschlüsselte Datentypen. Eine ausführliche Liste der unterstützten Typkonvertierungen finden Sie unter [Always Encrypted (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Beachten Sie die folgenden Punkte, wenn Sie „SQLBindParameter“ mit Parametern für verschlüsselte Spalten verwenden, um Fehler bei der Datentypkonvertierung zu vermeiden:

- Entweder ist der SQL-Typ des Parameters identisch mit dem Typ der Zielspalte oder die Konvertierung vom SQL-Typ in den Typ der Spalte wird unterstützt.

- Die Genauigkeit und Dezimalstellenanzahl von Parametern, die auf Spalten der SQL Server-Datentypen `decimal` und `numeric` ausgerichtet sind, ist mit der für die Zielspalte konfigurierten Genauigkeit und Dezimalstellenanzahl identisch.

- Die Genauigkeit von Parametern, die auf Spalten der SQL Server-Datentypen `datetime2`, `datetimeoffset` oder `time` ausgerichtet sind, ist in Abfragen, in denen die Zielspalte geändert wird, nicht größer als die Genauigkeit für die Zielspalte.  

##### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Fehler aufgrund der Übergabe von Klartext anstelle von verschlüsselten Werten

Jeder Wert für verschlüsselte Spalten muss vor dem Senden an den Server verschlüsselt werden. Ein Versuch, einen Klartextwert einzufügen, zu ändern oder nach einem Klartextwert für eine verschlüsselte Spalte zu filtern, führt zu einem Fehler. Stellen Sie Folgendes sicher, um solche Fehler zu vermeiden:

- Always Encrypted muss aktiviert sein (im DSN, in der Verbindungszeichenfolge, vor der Verbindungsherstellung durch Festlegen des Verbindungsattributs `SQL_COPT_SS_COLUMN_ENCRYPTION` für eine bestimmte Verbindung oder durch Festlegen des Anweisungsattributs `SQL_SOPT_SS_COLUMN_ENCRYPTION` für eine bestimmte Anweisung).

- Sie verwenden „SQLBindParameter“ zum Senden von Daten, die auf verschlüsselte Spalten ausgerichtet sind. Das folgende Beispiel zeigt eine Abfrage, in der auf falsche Weise nach einem Literal bzw. einer Konstante einer verschlüsselten Spalte (SSN) gefiltert wird, anstatt das Literal als Argument an SQLBindParameter zu übergeben.

```
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

### <a name="precautions-when-using-sqlsetpos-and-sqlmoreresults"></a>Vorsichtsmaßnahmen bei der Verwendung von „SQLSetPos“ und „SQLMoreResults“

#### <a name="sqlsetpos"></a>SQLSetPos

Mit der API `SQLSetPos` kann eine Anwendung Zeilen in einem Resultset mithilfe von Puffern aktualisieren, die mit „SQLBindCol“ gebunden sind und in die zuvor Zeilendaten abgerufen wurden. Aufgrund des asymmetrischen Verhaltens von verschlüsselten Typen mit fester Länge beim Auffüllen mit Leerstellen ist es möglich, die Daten in diesen Spalten unerwartet zu ändern, während andere Spalten in der Zeile aktualisiert werden. Mit Always Encrypted werden Zeichenwerte mit fester Länge mit Leerzeichen aufgefüllt, wenn der Wert kleiner als die Puffergröße ist.

Wenn Sie dieses Verhalten verhindern möchten, verwenden Sie das Flag `SQL_COLUMN_IGNORE` zum Ignorieren von Spalten, die nicht als Teil von `SQLBulkOperations` und bei Verwendung von `SQLSetPos` für cursorbasierte Updates aktualisiert werden.  Sie sollten alle Spalten ignorieren, die nicht direkt von der Anwendung geändert werden. Damit verhindern Sie Leistungseinbußen und die Kürzung von Spalten, die an einen Puffer gebunden sind, der *kleiner* als die tatsächliche Größe (der Datenbank) ist. Weitere Informationen finden Sie in der [SQLSetPos-Funktionsreferenz](https://msdn.microsoft.com/library/ms713507(v=vs.85).aspx).

#### <a name="sqlmoreresults--sqldescribecol"></a>SQLMoreResults und SQLDescribeCol

Anwendungsprogramme können [SQLDescribeCol](https://msdn.microsoft.com/library/ms716289(v=vs.85).aspx) aufrufen, um Metadaten zu Spalten in vorbereiteten Anweisungen zurückzugeben.  Wenn Always Encrypted aktiviert ist, wird durch Aufrufen von `SQLMoreResults` *vor* dem Aufrufen von `SQLDescribeCol` stattdessen [sp_describe_first_result_set](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) aufgerufen. Damit werden die Klartextmetadaten für verschlüsselte Spalten nicht korrekt zurückgegeben. Rufen Sie daher `SQLDescribeCol` für vorbereitete Anweisungen *vor* dem Aufrufen von `SQLMoreResults` auf, wenn Sie dies vermeiden möchten.

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Kontrollieren der Auswirkungen von Always Encrypted auf die Leistung

Da Always Encrypted eine clientseitige Verschlüsselungstechnologie ist, werden die meisten Leistungseinbußen auf der Clientseite und nicht in der Datenbank beobachtet. Neben den Kosten für Verschlüsselungs- und Entschlüsselungsvorgänge ergeben sich die folgenden anderen Quellen für Leistungseinbußen auf der Clientseite:

- Zusätzliche Roundtrips zur Datenbank zum Abrufen von Metadaten für Abfrageparameter.

- Aufrufe an einen Spaltenhauptschlüsselspeicher für den Zugriff auf einen Spaltenhauptschlüssel.

In diesem Abschnitt werden die integrierten Leistungsoptimierungen in ODBC Driver for SQL Server und die Steuerung der Auswirkung der beiden oben genannten Faktoren auf die Leistung beschrieben.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Kontrollieren von Roundtrips zum Abrufen von Metadaten für Abfrageparameter

Wenn Always Encrypted für eine Verbindung aktiviert ist, ruft der Treiber standardmäßig [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) für jede parametrisierte Abfrage auf, wobei die Abfrageanweisung (ohne Parameterwerte) an SQL Server übergeben wird. Die Abfrageanweisung wird von dieser gespeicherten Prozedur analysiert, um zu ermitteln, ob Parameter verschlüsselt werden müssen. In diesem Fall werden verschlüsselungsbezogene Informationen für jeden Parameter zurückgegeben, die der Treiber dann verschlüsseln kann. Das oben beschriebene Verhalten stellt einen hohen Grad an Transparenz für die Clientanwendung sicher: Die Anwendung (und der Anwendungsentwickler) muss nicht beachten, welche Abfragen auf verschlüsselte Spalten zugreifen, so lange die Werte für verschlüsselte Spalten in Parametern an den Treiber übergeben werden.

### <a name="per-statement-always-encrypted-behavior"></a>Verhalten von Always Encrypted für einzelne Anweisungen

Sie können das Verhalten von Always Encrypted für einzelne Abfragen ändern, wenn Sie es für die Verbindung aktiviert haben, um beim Abrufen von Verschlüsselungsmetadaten für parametrisierte Abfragen die Auswirkungen auf die Leistung zu steuern. Auf diese Weise können Sie sicherstellen, dass `sys.sp_describe_parameter_encryption` nur für Abfragen aufgerufen wird, bei denen Ihnen bekannt ist, dass sie über Parameter für verschlüsselte Spalten verfügen. Beachten Sie jedoch, dass Sie auf diese Weise die Transparenz der Verschlüsselung reduzieren: Wenn Sie zusätzliche Spalten in Ihrer Datenbank verschlüsseln, müssen Sie möglicherweise den Code der Anwendung ändern, um ihn auf die Schemaänderungen auszurichten.

Rufen Sie zum Steuern des Verhaltens von Always Encrypted für eine Anweisung „SQLSetStmtAttr“ auf, um das Anweisungsattribut `SQL_SOPT_SS_COLUMN_ENCRYPTION` auf einen der folgenden Werte festzulegen:

|value|und Beschreibung|
|-|-|
|`SQL_CE_DISABLED` (0)|Always Encrypted ist für die Anweisung deaktiviert.|
|`SQL_CE_RESULTSETONLY` (1)|Nur Entschlüsselung. Resultsets und Rückgabewerte werden entschlüsselt, und Parameter werden nicht verschlüsselt.|
|`SQL_CE_ENABLED` (3) | Always Encrypted ist aktiviert und wird für Parameter und Ergebnisse verwendet.|

Neue Anweisungshandles, die über eine Verbindung mit aktiviertem Always Encrypted erstellt wurden, sind standardmäßig auf „SQL_CE_ENABLED“ festgelegt. Wurden die Handles über eine Verbindung mit deaktivierter Always Encrypted-Option erstellt, ist die Standardeinstellung „SQL_CE_DISABLED“ (und es ist nicht möglich, Always Encrypted zu aktivieren).

Greifen die meisten Abfragen einer Clientanwendung auf verschlüsselte Spalten zu, wird folgende Vorgehensweise empfohlen:

- Legen Sie das Schlüsselwort für die `ColumnEncryption`-Verbindungszeichenfolge auf `Enabled` fest.

- Legen Sie für Anweisungen, die nicht auf verschlüsselte Spalten zugreifen, das Attribut `SQL_SOPT_SS_COLUMN_ENCRYPTION` auf `SQL_CE_DISABLED` fest. Dadurch wird der Aufruf von `sys.sp_describe_parameter_encryption` deaktiviert, und es werden auch keine Werte im Resultset entschlüsselt.
    
- Legen Sie für Anweisungen ohne Parameter, für die eine Verschlüsselung erforderlich wäre, und die Daten aus verschlüsselten Spalten abrufen, das Attribut `SQL_SOPT_SS_COLUMN_ENCRYPTION` auf `SQL_CE_RESULTSETONLY` fest. Dadurch werden der Aufruf von `sys.sp_describe_parameter_encryption` und die Parameterverschlüsselung deaktiviert. Ergebnisse mit verschlüsselten Spalten werden weiterhin entschlüsselt.

## <a name="always-encrypted-security-settings"></a>Always Encrypted-Sicherheitseinstellungen

### <a name="force-column-encryption"></a>Erzwingen von Spaltenverschlüsselung

Wenn Sie die Verschlüsselung eines Parameters erzwingen möchten, legen Sie das IPD-Feld `SQL_CA_SS_FORCE_ENCRYPT` (Implementierungsparameterdeskriptor) fest, indem Sie die Funktion „SQLSetDescField“ aufrufen. Bei einem Wert ungleich 0 (null) wird ein Fehler zurückgegeben, wenn für den zugeordneten Parameter keine Verschlüsselungsmetadaten zurückgegeben werden.

```
SQLHDESC ipd;
SQLGetStmtAttr(hStmt, SQL_ATTR_IMP_PARAM_DESC, &ipd, 0, 0);
SQLSetDescField(ipd, paramNum, SQL_CA_SS_FORCE_ENCRYPT, (SQLPOINTER)TRUE, SQL_IS_SMALLINT);   
```

Wenn SQL Server den Treiber informiert, dass der Parameter nicht verschlüsselt werden muss, tritt bei Abfragen, die diesen Parameter verwenden, ein Fehler auf. Dies bietet zusätzlichen Schutz vor Angriffen, bei denen ein kompromittierter SQL Server falsche Verschlüsselungsmetadaten für den Client bereitstellt, was zur Offenlegung von Daten führen kann.

### <a name="column-encryption-key-caching"></a>Zwischenspeicherung von Spaltenverschlüsselungsschlüsseln

Der Treiber speichert die Spaltenverschlüsselungsschlüssel (CEKs) im Klartext im Zwischenspeicher, um die Anzahl der Aufrufe an einen Spaltenhauptschlüsselspeicher zum Entschlüsseln von CEKs zu verringern. Der CEK-Cache ist für den Treiber global und keiner Verbindung zugeordnet. Nach dem Erhalt des verschlüsselten CEK (ECEK) aus den Datenbankmetadaten versucht der Treiber zunächst, den CEK im Klartext zu finden, der dem verschlüsselten Schlüsselwert im Cache entspricht. Der Treiber ruft den Schlüsselspeicher, der den CMK enthält, nur auf, wenn der entsprechende CEK im Klartext im Cache nicht gefunden werden kann.

> [!NOTE]
> Bei ODBC Driver for SQL Server werden die Einträge im Cache nach einem Zeitlimit von zwei Stunden entfernt. Dies bedeutet, dass der Treiber den Schlüsselspeicher für einen bestimmten ECEK während der Lebensdauer der Anwendung oder alle zwei Stunden (je nachdem, welches Intervall kürzer ist) nur einmal kontaktiert.

Ab ODBC Driver 17.1 for SQL Server kann das Zeitlimit für den CEK-Cache mithilfe des Verbindungsattributs `SQL_COPT_SS_CEKCACHETTL` angepasst werden. Dabei wird die Anzahl der Sekunden angegeben, die ein CEK im Cache bleiben soll. Da der Cache global ist, kann das Attribut von jedem für den Treiber gültigen Verbindungshandle angepasst werden. Wird die Gültigkeitsdauer des Caches verringert, werden auch vorhandene CEKs, die die neue Gültigkeitsdauer überschreiten würden, entfernt. Bei einer Gültigkeitsdauer von 0 (null) werden keine CEKs zwischengespeichert.

### <a name="trusted-key-paths"></a>Vertrauenswürdige Schlüsselpfade

Ab ODBC Driver 17.1 for SQL Server ist es mithilfe des Verbindungsattributs `SQL_COPT_SS_TRUSTEDCMKPATHS` zulässig, dass eine Anwendung für Always Encrypted-Vorgänge die ausschließliche Verwendung einer angegebenen Liste mit CMKs anfordert, die anhand ihrer Schlüsselpfade identifiziert werden. Die Standardeinstellung für dieses Attribut ist NULL, d. h. der Treiber akzeptiert jeden beliebigen Schlüsselpfad. Wenn Sie diese Funktion verwenden möchten, legen Sie `SQL_COPT_SS_TRUSTEDCMKPATHS` so fest, dass auf eine durch NULL getrennte und mit NULL endende Zeichenfolge für breite Zeichen gezeigt wird, die den bzw. die zulässigen Schlüsselpfad/e auflistet. Der Speicher, auf den das Attribut zeigt, muss mithilfe des Verbindungshandles, für das es festgelegt wurde, während der Verschlüsselungs- oder Entschlüsselungsvorgänge gültig bleiben. Auf diesem Weg überprüft der Treiber ohne Beachtung von Groß-/Kleinschreibung, ob der CMK-Pfad wie in den Servermetadaten angegeben in dieser Liste zu finden ist. Befindet sich der CMK-Pfad nicht in der Liste, tritt ein Fehler auf. Der Inhalt des Speichers, auf den das Attribut zeigt, kann durch die Anwendung geändert werden. So kann die Liste der vertrauenswürdigen CMKs geändert werden, ohne das Attribut erneut festzulegen.

## <a name="working-with-column-master-key-stores"></a>Arbeiten mit Spaltenhauptschlüsselspeichern

Der Treiber benötigt zum Verschlüsseln oder Entschlüsseln von Daten einen CEK, der für die Zielspalte konfiguriert ist. CEKs werden in verschlüsselter Form (als ECEKs) in den Datenbankmetadaten gespeichert. Jeder CEK besitzt einen entsprechenden CMK, mit dem er verschlüsselt wurde. In den [Datenbankmetadaten](../../t-sql/statements/create-column-master-key-transact-sql.md) wird nicht der CMK selbst gespeichert, sondern nur der Name des Schlüsselspeichers sowie Informationen zur Suche nach dem CMK.

Wenn der Treiber den Klartextwert eines ECEK abrufen möchten, benötigt er zunächst die Metadaten für den CEK und den entsprechenden CMK. Mit diesen Informationen kontaktiert er den Schlüsselspeicher, der den CMK enthält, und fordert die Entschlüsselung des ECEK an. Die Kommunikation zwischen Treiber und Schlüsselspeicher erfolgt über einen Schlüsselspeicheranbieter.

### <a name="built-in-keystore-providers"></a>Integrierte Schlüsselspeicheranbieter

ODBC Driver for SQL Server verfügt über die folgenden integrierten Schlüsselspeicheranbieter:

| Name | und Beschreibung | Name des Anbieters (Metadaten) |Verfügbarkeit|
|:---|:---|:---|:---|
|Azure-Schlüsseltresor |Speichert CMKs im Azure Key Vault. | `AZURE_KEY_VAULT` |Windows, macOS, Linux|
|Windows-Zertifikatspeicher|Speichert CMKs lokal im Windows-Schlüsselspeicher.| `MSSQL_CERTIFICATE_STORE`|Windows|

- Sie (oder der Datenbankadministrator) müssen sicherstellen, dass der in den Metadaten des Spaltenhauptschlüssels konfigurierte Anbietername richtig ist und der Pfad des Spaltenhauptschlüssels dem Schlüsselpfadformat für den angegebenen Anbieter entspricht. Es wird empfohlen, dass Sie die Schlüssel mithilfe von Tools wie SQL Server Management Studio konfigurieren, die die gültigen Anbieternamen und Schlüsselpfade automatisch generieren, wenn die Anweisung [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md) ausgegeben wird.

- Sie müssen sicherstellen, dass die Anwendung auf den Schlüssel im Schlüsselspeicher zugreifen kann. Dies kann das Gewähren des Zugriffs auf den Schlüssel und/oder Schlüsselspeicher für die Anwendung (abhängig vom Schlüsselspeicher) oder das Ausführen anderer wichtiger speicherspezifischer Konfigurationsschritte beinhalten. Zum Zugreifen auf den Azure Key Vault müssen Sie beispielsweise im Keystore die korrekten Anmeldeinformationen angeben.

### <a name="using-the-azure-key-vault-provider"></a>Verwenden des Azure Key Vault-Anbieters

Azure Key Vault (AKV) ist eine praktische Möglichkeit zum Speichern und Verwalten von Spaltenhauptschlüsseln für Always Encrypted (insbesondere, wenn Ihre Anwendungen in Azure gehostet werden). Unter Linux, macOS und Windows enthält ODBC Driver for SQL Server einen integrierten CMK-Speicheranbieter für den Azure Key Vault. Weitere Informationen zum Konfigurieren von Azure Key Vault für Always Encrypted finden Sie unter [Azure Key Vault – Step by Step (Ausführliche Anleitung zu Azure Key Vault)](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/), [Getting Started with Key Vault (Erste Schritte mit dem Azure Key Vault)](https://azure.microsoft.com/documentation/articles/key-vault-get-started/) und [Erstellen und Speichern von Spaltenhauptschlüsseln (Always Encrypted)](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2).

> [!NOTE]
> Der ODBC-Treiber unterstützt keine Active Directory-Verbunddienste (AD FS) für die AKV-Authentifizierung. Wenn Sie Azure Active Directory Authentifizierung bei AKV verwenden und die Active Directory Konfiguration Verbund Dienste umfasst, kann die Authentifizierung fehlschlagen.
> Unter Linux und macOS ist ab ODBC Driver 17.2 for SQL Server für die Verwendung dieses Anbieters `libcurl` erforderlich. Dabei handelt es sich jedoch nicht um eine explizite Abhängigkeit, da es für andere Vorgänge mit dem Treiber nicht erforderlich ist. Wenn im Bezug zu `libcurl` ein Fehler auftritt, überprüfen Sie ob es installiert ist.

Der Treiber unterstützt die Authentifizierung beim Azure Key Vault mithilfe der folgenden Typen von Anmeldeinformationen:

- Benutzername/Kennwort: Bei dieser Methode bestehen die Anmeldeinformationen aus dem Namen eines Azure Active Directory-Benutzers und dessen Kennwort.

- Client-ID/Geheimnis: Bei dieser Methode bestehen die Anmeldeinformationen aus einer Anwendungsclient-ID und einem Anwendungsgeheimnis.

Verwenden Sie die folgenden Schlüsselwörter bestehend aus Verbindungszeichenfolgen, um dem Treiber für die Spaltenverschlüsselung die Verwendung der im Azure Key Vault gespeicherten CMKs zu erlauben:

|Anmeldeinformationen| `KeyStoreAuthentication` |`KeyStorePrincipalId`| `KeyStoreSecret` |
|-|-|-|-|
|Benutzername/Kennwort| `KeyVaultPassword`|Benutzerprinzipalname|Kennwort|
|Client-ID/Geheimnis| `KeyVaultClientSecret`|Client-ID|Secret|

#### <a name="example-connection-strings"></a>Exemplarische Verbindungszeichenfolgen

Die folgenden Verbindungszeichenfolgen veranschaulichen die Authentifizierung beim Azure Key Vault mit den beiden Anmeldeinformationstypen:

**Client-ID/geheimer Schlüssel**:

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultClientSecret;KeyStorePrincipalId=<clientId>;KeyStoreSecret=<secret>
```

**Benutzername/Kennwort**:

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultPassword;KeyStorePrincipalId=<username>;KeyStoreSecret=<password>
```

Zum Speichern von CMKs im Azure Key Vault sind keine weiteren Änderungen der ODBC-Anwendung erforderlich.

### <a name="using-the-windows-certificate-store-provider"></a>Verwenden des Windows-Zertifikatspeicheranbieters

Unter Windows enthält ODBC Driver for SQL Server einen integrierten CMK-Speicheranbieter für den Windows-Zertifikatspeicher namens `MSSQL_CERTIFICATE_STORE`. (Dieser Anbieter ist nicht unter macOS oder Linux verfügbar.) Mit diesem Anbieter wird der CMK lokal auf dem Clientcomputer gespeichert, und es ist keine weitere Konfiguration durch die Anwendung erforderlich, um ihn mit dem Treiber zu verwenden. Die Anwendung muss jedoch auf das Zertifikat und den privaten Schlüssel im Speicher zugreifen können. Weitere Informationen finden Sie unter [Erstellen und Speichern von Spaltenhauptschlüsseln (Always Encrypted)](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted).

### <a name="using-custom-keystore-providers"></a>Verwenden benutzerdefinierter Keystore-Anbieter

Über die CEKeystoreProvider-Oberfläche unterstützt ODBC Driver for SQL Server auch benutzerdefinierte Schlüsselspeicheranbieter von Drittanbietern. Dadurch kann eine Anwendung Schlüsselspeicheranbieter laden, abfragen und konfigurieren, damit sie vom Treiber zum Zugreifen auf verschlüsselte Spalten verwendet werden können. Anwendungen können auch direkt mit einem Schlüsselspeicheranbieter interagieren, um CEKs für die Speicherung in SQL Server zu verschlüsseln und weitere Aufgaben auszuführen, die über das Zugreifen auf verschlüsselte Spalten mit ODBC hinausgehen. Weitere Informationen finden Sie unter [Custom Keystore Providers (Benutzerdefinierte Schlüsselspeicheranbieter)](../../connect/odbc/custom-keystore-providers.md).

Zur Interaktion mit benutzerdefinierten Schlüsselspeicheranbietern werden zwei Verbindungsattribute verwendet. Die Überladungen sind:

- `SQL_COPT_SS_CEKEYSTOREPROVIDER`

- `SQL_COPT_SS_CEKEYSTOREDATA`

Das erste Attribut wird zum Laden und Aufzählen geladener Schlüsselspeicheranbieter verwendet, das zweite für die Kommunikation zwischen Anwendung und Anbieter. Diese Verbindungsattribute können jederzeit, also vor und nach dem Herstellen einer Verbindung, verwendet werden, da die Interaktion zwischen Anwendung und Anbieter keine Kommunikation mit SQL Server beinhaltet. Da der Treiber jedoch noch nicht geladen wurde, werden die Attribute durch das Festlegen und Abrufen vor einer Verbindungsherstellung vom Treiber-Manager verarbeitet, was möglicherweise nicht zu den erwarteten Ergebnissen führt.

#### <a name="loading-a-keystore-provider"></a>Laden eines Schlüsselspeicheranbieters

Durch das Festlegen des Verbindungsattributs `SQL_COPT_SS_CEKEYSTOREPROVIDER` kann eine Clientanwendung eine Anbieterbibliothek laden und die darin enthaltenen Schlüsselspeicheranbieter bereitstellen.

```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```

| Argument | und Beschreibung |
|:---|:---|
|`ConnectionHandle`|[Eingabe] Verbindungshandle. Es muss sich um ein gültiges Verbindungshandle handeln, jedoch kann auf Anbieter, die über ein Verbindungshandle geladen werden, von jedem anderen Handle im selben Vorgang aus zugegriffen werden.|
|`Attribute`|[Eingabe] Festzulegendes Attribut: die Konstante `SQL_COPT_SS_CEKEYSTOREPROVIDER`.|
|`ValuePtr`|[Eingabe] Zeiger auf eine Zeichenfolge, die mit NULL endet und den Dateinamen der Anbieterbibliothek angibt. Für „SQLSetConnectAttrA“ handelt es sich dabei um eine ANSI-(Multibyte-)Zeichenfolge. Für „SQLSetConnectAttrW“ handelt es sich um eine Unicode-Zeichenfolge (vom Typ „wchar_t“).|
|`StringLength`|[Eingabe] Länge der Zeichenfolge „ValuePtr“ oder von „SQL_NTS“.|

Der Treiber versucht, mithilfe des von der Plattform definierten Lademechanismus für dynamische Bibliotheken (`dlopen()` unter Linux und macOS, `LoadLibrary()` unter Windows) die vom ValuePtr-Parameter identifizierte Bibliothek zu laden. Anschließend werden alle darin definierten Anbieter der Liste mit Anbietern hinzugefügt, die dem Treiber bekannt sind. Die folgenden Fehler können auftreten:

| Fehler | und Beschreibung |
|:--|:--|
|`CE203`|Die dynamische Bibliothek konnte nicht geladen werden.|
|`CE203`|Das exportierte Symbol „CEKeyStoreProvider“ wurde in der Bibliothek nicht gefunden.|
|`CE203`|Ein oder mehrere Anbieter in der Bibliothek wurden bereits geladen.|

`SQLSetConnectAttr` gibt die üblichen Fehler- oder Erfolgswerte zurück. Weitere Informationen sind zu allen Fehlern verfügbar, die über den ODBC-Standarddiagnosemechanismus aufgetreten sind.

> [!NOTE]
> Der Programmierer der Anwendung muss sicherstellen, dass alle benutzerdefinierten Anbieter geladen werden, bevor über eine beliebige Verbindung eine Abfrage gesendet wird, mit der die Anbieter angefordert werden. Andernfalls wird folgender Fehler ausgelöst:

| Fehler | und Beschreibung |
|:--|:--|
|`CE200`|Schlüsselspeicheranbieter %1 wurde nicht gefunden. Stellen Sie sicher, dass die entsprechende Bibliothek für Schlüsselspeicheranbieter geladen wurde.|

> [!NOTE]
> Ausführende des Schlüsselspeicheranbieters sollten es vermeiden, `MSSQL` im Namen der benutzerdefinierten Anbieter zu verwenden. Dieser Begriff ist für die ausschließliche Verwendung mit Microsoft reserviert, und seine Verwendung könnte zu Konflikten mit künftigen integrierten Anbietern führen. Die Verwendung des Begriffs im Namen eines benutzerdefinierten Anbieters könnte eine ODBC-Warnung verursachen.

#### <a name="getting-the-list-of-loaded-providers"></a>Abrufen der Liste mit geladenen Anbietern

Durch Abrufen des Verbindungsattributs kann eine Clientanwendung die aktuell im Treiber geladenen Schlüsselspeicheranbieter (einschließlich der integrierten) bestimmen. Dies ist erst nach dem Herstellen einer Verbindung möglich.

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```

| Argument | und Beschreibung |
|:---|:---|
|`ConnectionHandle`|[Eingabe] Verbindungshandle. Es muss sich um ein gültiges Verbindungshandle handeln, jedoch kann auf Anbieter, die über ein Verbindungshandle geladen werden, von jedem anderen Handle im selben Vorgang aus zugegriffen werden.|
|`Attribute`|[Eingabe] Abzurufendes Attribut: die Konstante `SQL_COPT_SS_CEKEYSTOREPROVIDER`.|
|`ValuePtr`|[Ausgabe] Zeiger auf den Speicher, an den der nächste geladene Anbietername zurückgegeben werden soll.|
|`BufferLength`|[Eingabe] Länge des Puffers „ValuePtr“.|
|`StringLengthPtr`|[Ausgabe] Zeiger auf einen Puffer, an den die Gesamtzahl der zur Rückgabe in \*ValuePtr verfügbaren Bytes (ausgenommen das mit NULL endende Zeichen) zurückgegeben wird. Handelt es sich bei „ValuePtr“ um einen NULL-Zeiger, wird keine Länge zurückgegeben. Handelt es sich bei dem Attributwert um eine Zeichenfolge und ist die Anzahl der zur Rückgabe verfügbaren Bytes größer als die Pufferlänge abzüglich der Länge des mit NULL endenden Zeichens, werden die Daten in \*ValuePtr auf diese Länge gekürzt und vom Treiber mit NULL beendet.|

Damit die gesamte Liste abgerufen werden kann, wird bei jedem GET-Vorgang der Name des aktuellen Anbieters zurückgegeben und der interne Zähler auf den nächsten Anbieter vorgerückt. Ist das Ende der Liste erreicht, wird eine leere Zeichenfolge ("") zurückgegeben und der Zähler zurückgesetzt. Nachfolgende GET-Vorgänge beginnen dann wieder am Anfang der Liste.

### <a name="communicating-with-keystore-providers"></a>Kommunizieren mit Schlüsselspeicheranbietern

Mit dem Verbindungsattribut `SQL_COPT_SS_CEKEYSTOREDATA` ist es einer Clientanwendung möglich, mit geladenen Schlüsselspeicheranbietern zur Konfiguration von zusätzlichen Parametern, Schlüsselerstellungsmaterial usw. zu kommunizieren. Die Kommunikation zwischen einer Clientanwendung und einem Anbieter folgt einem einfachen Protokoll aus Anforderung und Antwort basierend auf GET- und SET-Anforderungen, die dieses Verbindungsattribut verwenden. Die Kommunikation geht immer von der Clientanwendung aus.

> [!NOTE]
> Aufgrund der Art der Antwort von ODBC-Aufrufen über „CEKeyStoreProvider“ auf (SQLGet/SetConnectAttr) unterstützt die ODBC-Oberfläche nur das Festlegen von Daten bei der Auflösung des Verbindungskontexts.

Die Kommunikation zwischen Anwendung und Schlüsselspeicheranbietern erfolgt über den Treiber mithilfe der CEKeystoreData-Struktur:

```
typedef struct CEKeystoreData {
wchar_t *name;
unsigned int dataSize;
char data[];
} CEKEYSTOREDATA;
```

| Argument | und Beschreibung |
|:---|:---|
|`name`|[Eingabe] Bei SET-Vorgängen: Name des Anbieters, an den die Daten gesendet werden. Wird bei GET-Vorgängen ignoriert. Auf NULL endende Zeichenfolge für breite Zeichen.|
|`dataSize`|[Eingabe] Größe des Datenarrays gemäß der Struktur.|
|`data`|[Eingabe/Ausgabe] Bei SET-Vorgängen: Daten, die an den Anbieter gesendet werden sollen. Dabei kann es sich um willkürliche Daten handeln. Der Treiber versucht nicht, die Daten zu interpretieren. Bei GET-Vorgängen: Puffer, der die gelesenen Daten vom Anbieter empfängt.|

#### <a name="writing-data-to-a-provider"></a>Schreiben von Daten an einen Anbieter

Bei einem mithilfe des Attributs `SQL_COPT_SS_CEKEYSTOREDATA` ausgeführten Aufrufs von `SQLSetConnectAttr` wird ein Datenpaket an den angegebenen Schlüsselspeicheranbieter geschrieben.
```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```

| Argument | und Beschreibung |
|:---|:---|
|`ConnectionHandle`| [Eingabe] Verbindungshandle. Es muss sich um ein gültiges Verbindungshandle handeln, jedoch kann auf Anbieter, die über ein Verbindungshandle geladen werden, von jedem anderen Handle im selben Vorgang aus zugegriffen werden.|
|`Attribute`|[Eingabe] Festzulegendes Attribut: die Konstante `SQL_COPT_SS_CEKEYSTOREDATA`.|
|`ValuePtr`|[Eingabe] Zeiger auf eine CEKeystoreData-Struktur. Der Anbieter, für den die Daten vorgesehen sind, wird vom Namensfeld der Struktur identifiziert.|
|`StringLength`|[Eingabe] Konstante „SQL_IS_POINTER“.|

Zusätzliche detaillierte Fehlerinformationen können über [SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx) abgerufen werden.

> [!NOTE]
> Der Anbieter kann mithilfe des Verbindungshandles, sofern gewünscht, die geschriebenen Daten einer bestimmten Verbindung zuordnen. Dies ist beim Implementieren von Konfigurationen für einzelne Verbindungen nützlich. Außerdem kann er den Verbindungskontext ignorieren und alle Daten identisch verarbeiten, unabhängig davon, welche Verbindung zum Senden der Daten verwendet wurde. Weitere Informationen finden Sie unter [Context Association (Kontextzuordnung)](../../connect/odbc/custom-keystore-providers.md#context-association).

#### <a name="reading-data-from-a-provider"></a>Lesen von Daten von einem Anbieter

Bei einem mithilfe des Attributs `SQL_COPT_SS_CEKEYSTOREDATA` ausgeführten Aufrufs von `SQLGetConnectAttr` wird ein Datenpaket vom Anbieter gelesen, *an den zuletzt geschrieben wurde*. Ist kein solcher Anbieter vorhanden, tritt ein Fehler in der Funktionsreihenfolge auf. Für Ausführende des Schlüsselspeicheranbieters ist es sinnvoll, Pseudoschreibvorgänge mit 0 Bytes zu unterstützen. Damit kann der Anbieter ohne weitere Auswirkungen für Schreibvorgänge ausgewählt werden.

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```

| Argument | und Beschreibung |
|:---|:---|
|`ConnectionHandle`|[Eingabe] Verbindungshandle. Es muss sich um ein gültiges Verbindungshandle handeln, jedoch kann auf Anbieter, die über ein Verbindungshandle geladen werden, von jedem anderen Handle im selben Vorgang aus zugegriffen werden.|
|`Attribute`|[Eingabe] Abzurufendes Attribut: die Konstante `SQL_COPT_SS_CEKEYSTOREDATA`.|
|`ValuePtr`|[Ausgabe] Zeiger auf eine CEKeystoreData-Struktur, in die die vom Anbieter gelesenen Daten platziert werden.|
|`BufferLength`|[Eingabe] Konstante „SQL_IS_POINTER“.|
|`StringLengthPtr`|[Ausgabe] Zeiger auf einen Puffer, an den die Pufferlänge zurückgegeben werden soll. Handelt es sich bei *ValuePtr um einen NULL-Zeiger, wird keine Länge zurückgegeben.|

Der Aufrufer muss sicherstellen, dass dem Anbieter zum Schreiben der Daten ein Puffer mit ausreichender Länge gemäß der CEKEYSTOREDATA-Struktur zur Verfügung steht. Bei der Rückgabe wird das Feld „dataSize“ mit der tatsächlichen Länge der vom Anbieter gelesenen Daten aktualisiert. Zusätzliche detaillierte Fehlerinformationen können über [SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx) abgerufen werden.

Die Oberfläche stellt keine weiteren Anforderungen an das Format der zwischen Anwendung und Schlüsselspeicheranbieter übertragenen Daten. Jeder Anbieter kann je nach Anforderungen ein eigenes Protokoll bzw. Datenformat definieren.

Ein Beispiel für das Implementieren eines eigenen Schlüsselspeicheranbieters finden Sie unter [Custom Keystore Providers (Benutzerdefinierte Schlüsselspeicheranbieter)](../../connect/odbc/custom-keystore-providers.md).

## <a name="limitations-of-the-odbc-driver-when-using-always-encrypted"></a>Einschränkungen des ODBC-Treibers bei Verwendung von Always Encrypted

### <a name="asynchronous-operations"></a>Asynchrone Vorgänge
Zwar lässt der Treiber die Verwendung von [asynchronen Vorgängen](../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md) mit Always Encrypted zu, doch kommt es zu Leistungsauswirkungen auf die Vorgänge, wenn Always Encrypted aktiviert ist. Der Aufruf von `sys.sp_describe_parameter_encryption` zum Bestimmen von Verschlüsselungsmetadaten für die Anweisung blockiert, weshalb der Treiber auf die Rückgabe der Metadaten vom Server warten muss, bevor er `SQL_STILL_EXECUTING` zurückgibt.

### <a name="retrieve-data-in-parts-with-sqlgetdata"></a>Abrufen von Teildaten mit „SQLGetData“
Vor ODBC Driver 17 for SQL Server konnten verschlüsselte Zeichen und Binärspalten mit „SQLGetData“ nicht in Teilen abgerufen werden. Es kann nur ein Aufruf von „SQLGetData“ vorgenommen werden, der einen Puffer mit ausreichender Länge für die gesamten Daten der Spalte enthält.

### <a name="send-data-in-parts-with-sqlputdata"></a>Senden von Teildaten mit „SQLPutData“
Vor ODBC Driver 17.3 for SQL Server war es nicht möglich, Teildaten mit „SQLPutData“ zum Einfügen oder Vergleichen zu senden. Es kann nur ein Aufruf von „SQLPutData“ vorgenommen werden, der einen Puffer mit allen Daten enthält. Wenn Sie Long-Daten in verschlüsselte Spalten einfügen möchten, verwenden Sie die API für das Massenkopieren mit einer Eingabedatendatei, die im nächsten Abschnitt beschrieben wird.

### <a name="encrypted-money-and-smallmoney"></a>Verschlüsselte Daten vom Typ „money“ und „smallmoney“
Parameter können nicht auf verschlüsselte Spalten vom Typ **money** oder **smallmoney** ausgerichtet sein, da es keinen bestimmten ODBC-Datentyp gibt, der diesen Typen zugeordnet wird. Daher tritt in diesem Fall ein Fehler vom Typ „Operandentypkollision“ auf.

## <a name="bulk-copy-of-encrypted-columns"></a>Massenkopieren von verschlüsselten Spalten

Ab ODBC Driver 17 for SQL Server wird die Verwendung der [SQL-Massenkopierfunktionen](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md) und des **BCP-Hilfsprogramms** mit Always Encrypted unterstützt. Mit den APIs für das Massenkopieren (bcp_&#42;) und dem **BCP-Hilfsprogramm** können Sie sowohl Klartext (beim Einfügen in verschlüsselter Form, beim Abrufen entschlüsselt) als auch Chiffretext (im genauen Wortlaut übertragen) einfügen und abrufen.

- Wenn Sie Chiffretext im Format „varbinary(max)“ abrufen möchten (z. B. beim Massenladen in eine andere Datenbank), stellen Sie ohne die Option `ColumnEncryption` eine Verbindung her (oder legen Sie sie auf `Disabled` fest), und führen Sie einen BCP OUT-Vorgang aus.

- Wenn Sie Klartext einfügen und abrufen möchten und den Treiber die erforderliche Verschlüsselung und Entschlüsselung transparent ausführen lassen, ist es ausreichend, `ColumnEncryption` auf `Enabled` festzulegen. Die sonstigen Funktionen der BCP-API bleiben unverändert.

- Wenn Sie Chiffretext im Format „varbinary(max)“ einfügen möchten (z. B. wie beim Abrufen oben), legen Sie die Option `BCPMODIFYENCRYPTED` auf TRUE fest, und führen Sie einen BCP IN-Vorgang aus. Damit die resultierenden Daten entschlüsselt werden können, vergewissern Sie sich, dass der CEK der Zielspalte und der CEK der ursprünglichen Spalte, aus der der Chiffretext abgerufen wurde, identisch sind.

Wenn Sie das **BCP-Hilfsprogramm** verwenden, verwenden Sie die Option -D, und geben Sie einen DSN mit dem gewünschten Wert an, um die Einstellung `ColumnEncryption` zu verwalten. Vergewissern Sie sich, dass zum Einfügen von Chiffretext die Einstellung `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` des Benutzers aktiviert ist.

In der folgenden Tabelle werden die Aktionen beim Verarbeiten einer verschlüsselten Spalte zusammengefasst:

|`ColumnEncryption`|BCP-Richtung|und Beschreibung|
|----------------|-------------|-----------|
|`Disabled`|OUT (zum Client)|Ruft Chiffretext ab. Der observierte Datentyp lautet **varbinary(max)** .|
|`Enabled`|OUT (zum Client)|Ruft Klartext ab. Die Spaltendaten werden vom Treiber entschlüsselt.|
|`Disabled`|IN (zum Server)|Fügt Chiffretext ein. Wird für sichtbar verschobene verschlüsselte Daten verwendet, die nicht entschlüsselt werden müssen. Es tritt dabei ein Fehler auf, wenn die Option `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` beim Benutzer nicht festgelegt ist oder „BCPMODIFYENCRYPTED“ beim Verbindungshandle nicht festgelegt ist. Weitere Informationen finden Sie weiter unten.|
|`Enabled`|IN (zum Server)|Fügt Klartext ein. Die Spaltendaten werden vom Treiber verschlüsselt.|

### <a name="the-bcpmodifyencrypted-option"></a>Option „BCPMODIFYENCRYPTED“

Damit die Daten nicht beschädigt werden, lässt der Server normalerweise das direkte Einfügen von Chiffretext in eine verschlüsselte Spalte nicht zu, und ein solcher Versuch schlägt fehl. Beim Massenladen von verschlüsselten Daten mithilfe der BCP-API kann Chiffretext jedoch direkt eingefügt werden, wenn die [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)-Option `BCPMODIFYENCRYPTED` auf TRUE festgelegt wird. Damit ist das Risiko der Beschädigung von verschlüsselten Daten geringer als beim Festlegen der Option `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` für das Benutzerkonto. Trotzdem müssen die Schlüssel mit den Daten übereinstimmen, weshalb es sinnvoll ist, nach dem Masseneinfügen und vor der weiteren Verwendung schreibgeschützte Überprüfungen der eingefügten Daten vorzunehmen.

Weitere Informationen finden Sie unter [Migrieren von durch Always Encrypted geschützten sensiblen Daten](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md).

## <a name="always-encrypted-api-summary"></a>Zusammenfassung der Always Encrypted-API

### <a name="connection-string-keywords"></a>Schlüsselwörter für Verbindungszeichenfolgen

|Name|und Beschreibung|  
|----------|-----------------|  
|`ColumnEncryption`|Zulässige Werte sind `Enabled`/`Disabled`.<br>`Enabled`: aktiviert Always Encrypted-Funktionen für die Verbindung.<br>`Disabled`: deaktiviert Always Encrypted-Funktionen für die Verbindung.<br>*Type*,*Data* -(Version 17,4 und höher) ermöglicht Always Encrypted mit dem sicheren Enclave-und Nachweis *Protokolltyp* sowie den zugehörigen Nachweis *Daten*. <br><br>Der Standardwert ist `Disabled`.|
|`KeyStoreAuthentication` | Gültige Werte: `KeyVaultPassword`, `KeyVaultClientSecret` |
|`KeyStorePrincipalId` | Wenn `KeyStoreAuthentication` = `KeyVaultPassword`, legen Sie diesen Wert auf einen gültigen Benutzerprinzipalnamen in Azure Active Directory fest. <br>Wenn `KeyStoreAuthetication` = `KeyVaultClientSecret`, legen Sie diesen Wert auf eine gültige Anwendungsclient-ID in Azure Active Directory fest. |
|`KeyStoreSecret` | Wenn `KeyStoreAuthentication` = `KeyVaultPassword`, legen Sie diesen Wert auf das Kennwort für den entsprechenden Benutzernamen fest. <br>Wenn `KeyStoreAuthentication` = `KeyVaultClientSecret`, legen Sie diesen Wert auf das Anwendungsgeheimnis fest, das einer gültigen Anwendungsclient-ID in Azure Active Directory zugeordnet wird. |


### <a name="connection-attributes"></a>Verbindungsattribute

|Name|Typ|und Beschreibung|  
|----------|-------|----------|  
|`SQL_COPT_SS_COLUMN_ENCRYPTION`|Vor dem Herstellen einer Verbindung|`SQL_COLUMN_ENCRYPTION_DISABLE` (0): Always Encrypted wird deaktiviert. <br>`SQL_COLUMN_ENCRYPTION_ENABLE` (1): Always Encrypted wird aktiviert.<br> Zeiger auf *Typ*,*Daten* Zeichenfolge--(Version 17,4 und höher) mit sicherer Enclave aktivieren|
|`SQL_COPT_SS_CEKEYSTOREPROVIDER`|Nach dem Herstellen einer Verbindung|[SET] Es wird versucht, „CEKeystoreProvider“ zu laden.<br>[GET] Ein CEKeystoreProvider-Name wird zurückgegeben.|
|`SQL_COPT_SS_CEKEYSTOREDATA`|Nach dem Herstellen einer Verbindung|[SET] Daten werden in „CEKeystoreProvider“ geschrieben.<br>[GET] Daten werden aus „CEKeystoreProvider“ gelesen.|
|`SQL_COPT_SS_CEKCACHETTL`|Nach dem Herstellen einer Verbindung|[SET] Gültigkeitsdauer des CEK-Caches wird festgelegt.<br>[GET] Gültigkeitsdauer des aktuellen CEK-Caches wird abgerufen.|
|`SQL_COPT_SS_TRUSTEDCMKPATHS`|Nach dem Herstellen einer Verbindung|[SET] Zeiger auf vertrauenswürdige CMK-Pfade wird festgelegt.<br>[GET] Zeiger auf aktuelle vertrauenswürdige CMK-Pfade wird abgerufen.|

### <a name="statement-attributes"></a>Anweisungsattribute

|Name|und Beschreibung|  
|----------|-----------------|  
|`SQL_SOPT_SS_COLUMN_ENCRYPTION`|`SQL_CE_DISABLED` (0): Always Encrypted ist für die Anweisung deaktiviert. <br>`SQL_CE_RESULTSETONLY` (1): Nur Entschlüsselung. Resultsets und Rückgabewerte werden entschlüsselt, und Parameter werden nicht verschlüsselt. <br>`SQL_CE_ENABLED` (3): Always Encrypted ist aktiviert und wird für Parameter und Ergebnisse verwendet.|

### <a name="descriptor-fields"></a>Deskriptorfelder

|IPD-Feld|Größe/Typ|Standardwert|und Beschreibung|
|-|-|-|-|  
|`SQL_CA_SS_FORCE_ENCRYPT` (1236)|WORD (2 Bytes)|0|Bei 0 (Standardeinstellung): Entscheidung, ob dieser Parameter verschlüsselt wird, basiert auf der Verfügbarkeit von Verschlüsselungsmetadaten.<br><br>Bei ungleich 0: Parameter wird verschlüsselt, wenn Verschlüsselungsmetadaten dafür verfügbar sind. Andernfalls schlägt die Anforderung fehl [CE300] [Microsoft][ODBC Driver 13 for SQL Server] Die obligatorische Verschlüsselung wurde für einen Parameter angegeben, es wurden vom Server jedoch keine Verschlüsselungsmetadaten bereitgestellt.|

### <a name="bcp_control-options"></a>Optionen für „bcp_control“

|Optionsname|Standardwert|und Beschreibung|
|-|-|-|
|`BCPMODIFYENCRYPTED` (21)|FALSE|Bei TRUE können Werte vom Typ „varbinary(max)“ in eine verschlüsselte Spalte eingefügt werden. Bei FALSE wird das Einfügen verhindert, solange die korrekten Typ- und Verschlüsselungsmetadaten nicht bereitgestellt werden.|

## <a name="see-also"></a>Weitere Informationen

- [„Immer verschlüsselt“ (Datenbank-Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves.md)
- [Always Encrypted-Blog](https://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/)

