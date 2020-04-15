---
title: SQLGetInfo-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInfo
helpviewer_keywords:
- SQLGetInfo function [ODBC]
ms.assetid: 49dceccc-d816-4ada-808c-4c6138dccb64
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 514922fd085cfd2ba19eb5c07dd844db82d55202
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303342"
---
# <a name="sqlgetinfo-function"></a>SQLGetInfo-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetInfo** gibt allgemeine Informationen über den Treiber und die Datenquelle zurück, die einer Verbindung zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetInfo(  
     SQLHDBC         ConnectionHandle,  
     SQLUSMALLINT    InfoType,  
     SQLPOINTER      InfoValuePtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *Infotyp*  
 [Eingabe] Art der Informationen.  
  
 *InfoValuePtr*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die Informationen zurückgegeben werden sollen. Je nach *angefordertem InfoType* handelt es sich bei den zurückgegebenen Informationen um eine der folgenden Informationen: eine null-terminierte Zeichenfolge, einen SQLUSMALLINT-Wert, eine SQLUINTEGER-Bitmaske, ein SQLUINTEGER-Flag, einen SQLUINTEGER-Binärwert oder einen SQLULEN-Wert.  
  
 Wenn das *InfoType-Argument* SQL_DRIVER_HDESC oder SQL_DRIVER_HSTMT ist, ist das *InfoValuePtr-Argument* sowohl Eingabe als auch Ausgabe. (Weitere Informationen finden Sie in den SQL_DRIVER_HDESC oder SQL_DRIVER_HSTMT Deskriptoren weiter unten in dieser Funktionsbeschreibung.)  
  
 Wenn *InfoValuePtr* NULL ist, gibt *StringLengthPtr* weiterhin die Gesamtzahl der Bytes zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer von *InfoValuePtr*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Länge des \* *InfoValuePtr-Puffers.* Wenn der Wert in * \*InfoValuePtr* keine Zeichenfolge ist oder *wenn InfoValuePtr* ein Nullzeiger ist, wird das *BufferLength-Argument* ignoriert. Der Treiber geht davon aus, dass die Größe von * \*InfoValuePtr* SQLUSMALLINT oder SQLUINTEGER ist, basierend auf dem *InfoType*. Wenn * \*InfoValuePtr* eine Unicode-Zeichenfolge ist (beim Aufrufen von **SQLGetInfoW**), muss das *BufferLength-Argument* eine gerade Zahl sein. Wenn dies nicht der Fall ist, wird SQLSTATE HY090 (Ungültige Zeichenfolge oder Pufferlänge) zurückgegeben.  
  
 *StringLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten) zurückgegeben werden soll, die in **InfoValuePtr*zurückgegeben werden können.  
  
 Wenn bei Zeichendaten die Anzahl der zurückzugebenden Bytes größer oder gleich \* *BufferLength*ist, werden die Informationen in *InfoValuePtr* auf *BufferLength-Bytes* abzüglich der Länge eines Null-Beendigungszeichens abgeschnitten und vom Treiber null beendet.  
  
 Bei allen anderen Datentypen wird der Wert von *BufferLength* ignoriert, und der Treiber geht davon aus, dass die Größe von \* *InfoValuePtr* SQLUSMALLINT oder SQLUINTEGER ist, abhängig vom *InfoType*.  
  
## <a name="return-value"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetInfo** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DBC und einem *Handle* von *ConnectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLGetInfo** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der \*Puffer *InfoValuePtr* war nicht groß genug, um alle angeforderten Informationen zurückzugeben. Daher wurden die Informationen abgeschnitten. Die Länge der angeforderten Informationen in der nicht abgeschnittenen Form wird in **StringLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) Die Art der in *InfoType* angeforderten Informationen erfordert eine offene Verbindung. Von den von ODBC reservierten Informationstypen können nur SQL_ODBC_VER ohne offene Verbindung zurückgegeben werden.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY010|Funktionssequenzfehler|(DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY024|Ungültiger Attributwert|(DM) Das *InfoType-Argument* wurde SQL_DRIVER_HSTMT, und der von *InfoValuePtr* hervorgehobene Wert war kein gültiges Anweisungshandle.<br /><br /> (DM) Das *InfoType-Argument* wurde SQL_DRIVER_HDESC, und der von *InfoValuePtr* hervorgehobene Wert war kein gültiges Deskriptor-Handle.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der für das Argument *BufferLength* angegebene Wert war kleiner als 0.<br /><br /> (DM) Der für *BufferLength* angegebene Wert war eine ungerade Zahl, und * \*InfoValuePtr* hatte einen Unicode-Datentyp.|  
|HY096|Informationstyp a-range|Der für das Argument *InfoType* angegebene Wert war für die vom Treiber unterstützte ODBC-Version ungültig.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feld nicht implementiert|Der für das Argument *InfoType* angegebene Wert war ein treiberspezifischer Wert, der vom Treiber nicht unterstützt wird.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der Treiber, der dem *ConnectionHandle* entspricht, unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Die aktuell definierten Informationstypen werden weiter unten in diesem Abschnitt unter "Informationstypen" angezeigt. Es wird erwartet, dass mehr definiert wird, um die Vorteile verschiedener Datenquellen zu nutzen. OdBC reserviert eine Reihe von Informationstypen. Treiberentwickler müssen Werte für ihre eigene treiberspezifische Verwendung von Open Group reservieren. **SQLGetInfo** führt keine Unicode-Konvertierung oder *Thunking* (siehe [Anhang A: ODBC-Fehlercodes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) der *ODBC-Programmiererreferenz*) für treiberdefinierte *InfoTypes*durch. Weitere Informationen finden Sie unter [Treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Das Format der in \* *InfoValuePtr* zurückgegebenen Informationen hängt vom angeforderten *InfoType* ab. **SQLGetInfo** gibt Informationen in einem von fünf verschiedenen Formaten zurück:  
  
-   Eine null-terminierte Zeichenfolge  
  
-   Ein SQLUSMALLINT-Wert  
  
-   Eine SQLUINTEGER-Bitmaske  
  
-   Ein SQLUINTEGER-Wert  
  
-   Ein SQLUINTEGER-Binärwert  
  
 Das Format der folgenden Informationstypen wird in der Beschreibung des Typs angegeben. Die Anwendung muss den in **InfoValuePtr* zurückgegebenen Wert entsprechend umwerfen. Ein Beispiel dafür, wie eine Anwendung Daten von einer SQLUINTEGER-Bitmaske abrufen kann, finden Sie unter "Codebeispiel".  
  
 Ein Treiber muss einen Wert für jeden Informationstyp zurückgeben, der in den folgenden Tabellen definiert ist. Wenn ein Informationstyp nicht für den Treiber oder die Datenquelle gilt, gibt der Treiber einen der in der folgenden Tabelle aufgeführten Werte zurück.  
  
 Zeichenkette ("Y" oder "N")  
 "N"  
  
 Zeichenkette (nicht "Y" oder "N")  
 leere Zeichenfolge  
  
 SQLUSMALLINT  
 0  
  
 SQLUINTEGER-Bitmaske oder SQLUINTEGER-Binärwert  
 0L  
  
 Wenn eine Datenquelle z. B. keine Prozeduren unterstützt, gibt **SQLGetInfo** die in der folgenden Tabelle aufgeführten Werte für die Werte von *InfoType* zurück, die sich auf Prozeduren beziehen.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 leere Zeichenfolge  
  
 **SQLGetInfo** gibt SQLSTATE HY096 (Ungültiger Argumentwert) für Werte von *InfoType* zurück, die sich im Bereich der Informationstypen befinden, die für die Verwendung durch ODBC reserviert sind, aber nicht von der vom Treiber unterstützten ODBC-Version definiert werden. Um zu ermitteln, welche Version von ODBC ein Treiber erfüllt, ruft eine Anwendung **SQLGetInfo** mit dem SQL_DRIVER_ODBC_VER-Informationstyp auf. **SQLGetInfo** gibt SQLSTATE HYC00 (Optionale Funktion nicht implementiert) für Werte von *InfoType* zurück, die sich im Bereich der Informationstypen befinden, die für die treiberspezifische Verwendung reserviert sind, aber vom Treiber nicht unterstützt werden.  
  
 Alle Aufrufe von **SQLGetInfo** erfordern eine offene Verbindung, außer wenn der *InfoType* SQL_ODBC_VER ist, der die Version des Treiber-Managers zurückgibt.  
  
## <a name="information-types"></a>Informationstypen  
 In diesem Abschnitt werden die von **SQLGetInfo**unterstützten Informationstypen aufgeführt. Informationstypen werden kategorial gruppiert und alphabetisch aufgelistet. Informationstypen, die für ODBC 3 *.x* hinzugefügt oder umbenannt wurden, werden ebenfalls aufgeführt.  
  
## <a name="driver-information"></a>Treiberinformationen  
 Die folgenden Werte des *InfoType-Arguments* geben Informationen über den ODBC-Treiber zurück, z. B. die Anzahl der aktiven Anweisungen, den Datenquellennamen und die Compliance-Ebene für Schnittstellenstandards:  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_FILE_USAGE|  
|SQL_ASYNC_MODE|SQL_GETDATA_EXTENSIONS|  
|SQL_ASYNC_NOTIFICATION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_BATCH_ROW_COUNT|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_BATCH_SUPPORT|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_DATA_SOURCE_NAME|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_DRIVER_AWARE_POOLING_SUPPORTED|SQL_MAX_CONCURRENT_ACTIVITIES|  
|SQL_DRIVER_HDBC|SQL_MAX_DRIVER_CONNECTIONS|  
|SQL_DRIVER_HDESC|SQL_ODBC_INTERFACE_CONFORMANCE|  
|SQL_DRIVER_HENV|SQL_ODBC_STANDARD_CLI_CONFORMANCE|  
|SQL_DRIVER_HLIB|SQL_ODBC_VER|  
|SQL_DRIVER_HSTMT|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_DRIVER_NAME|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DRIVER_ODBC_VER|SQL_ROW_UPDATES|  
|SQL_DRIVER_VER|SQL_SEARCH_PATTERN_ESCAPE|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|SQL_SERVER_NAME|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_STATIC_CURSOR_ATTRIBUTES2|  
  
> [!NOTE]  
>  Beim Implementieren von **SQLGetInfo**kann ein Treiber die Leistung verbessern, indem er die Häufigkeit minimiert, mit der Informationen vom Server gesendet oder angefordert werden.  
  
## <a name="dbms-product-information"></a>DBMS-Produktinformationen  
 Die folgenden Werte des *InfoType-Arguments* geben Informationen zum DBMS-Produkt zurück, z. B. den DBMS-Namen und die DBMS-Version:  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Datenquelleninformationen  
 Die folgenden Werte des *InfoType-Arguments* geben Informationen zur Datenquelle zurück, z. B. Cursoreigenschaften und Transaktionsfunktionen:  
  
|||  
|-|-|  
|SQL_ACCESSIBLE_PROCEDURES|SQL_MULT_RESULT_SETS|  
|SQL_ACCESSIBLE_TABLES|SQL_MULTIPLE_ACTIVE_TXN|  
|SQL_BOOKMARK_PERSISTENCE|SQL_NEED_LONG_DATA_LEN|  
|SQL_CATALOG_TERM|SQL_NULL_COLLATION|  
|SQL_COLLATION_SEQ|SQL_PROCEDURE_TERM|  
|SQL_CONCAT_NULL_BEHAVIOR|SQL_SCHEMA_TERM|  
|SQL_CURSOR_COMMIT_BEHAVIOR|SQL_SCROLL_OPTIONS|  
|SQL_CURSOR_ROLLBACK_BEHAVIOR|SQL_TABLE_TERM|  
|SQL_CURSOR_SENSITIVITY|SQL_TXN_CAPABLE|  
|SQL_DATA_SOURCE_READ_ONLY|SQL_TXN_ISOLATION_OPTION|  
|SQL_DEFAULT_TXN_ISOLATION|SQL_USER_NAME|  
|SQL_DESCRIBE_PARAMETER||  
  
## <a name="supported-sql"></a>Unterstützte SQL  
 Die folgenden Werte des *InfoType-Arguments* geben Informationen zu den SQL-Anweisungen zurück, die von der Datenquelle unterstützt werden. Die SQL-Syntax jedes Features, das von diesen Informationstypen beschrieben wird, ist die SQL-92-Syntax. Diese Informationstypen beschreiben nicht ausführlich die gesamte SQL-92-Grammatik. Stattdessen beschreiben sie die Teile der Grammatik, für die Datenquellen in der Regel unterschiedliche Unterstützungsebenen bieten. Insbesondere werden die meisten DDL-Anweisungen in SQL-92 behandelt.  
  
 Anwendungen sollten die allgemeine Ebene der unterstützten Grammatik aus dem SQL_SQL_CONFORMANCE-Informationstyp bestimmen und die anderen Informationstypen verwenden, um Abweichungen von der angegebenen Standardkonformitätsebene zu bestimmen.  
  
|||  
|-|-|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DROP_TABLE|  
|SQL_ALTER_DOMAIN|SQL_DROP_TRANSLATION|  
|SQL_ALTER_SCHEMA|SQL_DROP_VIEW|  
|SQL_ALTER_TABLE|SQL_EXPRESSIONS_IN_ORDERBY|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_GROUP_BY|  
|SQL_CATALOG_LOCATION|SQL_IDENTIFIER_CASE|  
|SQL_CATALOG_NAME|SQL_IDENTIFIER_QUOTE_CHAR|  
|SQL_CATALOG_NAME_SEPARATOR|SQL_INDEX_KEYWORDS|  
|SQL_CATALOG_USAGE|SQL_INSERT_STATEMENT|  
|SQL_COLUMN_ALIAS|SQL_INTEGRITY|  
|SQL_CORRELATION_NAME|SQL_KEYWORDS|  
|SQL_CREATE_ASSERTION|SQL_LIKE_ESCAPE_CLAUSE|  
|SQL_CREATE_CHARACTER_SET|SQL_NON_NULLABLE_COLUMNS|  
|SQL_CREATE_COLLATION|SQL_SQL_CONFORMANCE|  
|SQL_CREATE_DOMAIN|SQL_OJ_CAPABILITIES|  
|SQL_CREATE_SCHEMA|SQL_ORDER_BY_COLUMNS_IN_SELECT|  
|SQL_CREATE_TABLE|SQL_OUTER_JOINS|  
|SQL_CREATE_TRANSLATION|SQL_PROCEDURES|  
|SQL_DDL_INDEX|SQL_QUOTED_IDENTIFIER_CASE|  
|SQL_DROP_ASSERTION|SQL_SCHEMA_USAGE|  
|SQL_DROP_CHARACTER_SET|SQL_SPECIAL_CHARACTERS|  
|SQL_DROP_COLLATION|SQL_SUBQUERIES|  
|SQL_DROP_DOMAIN|SQL_UNION|  
|SQL_DROP_SCHEMA||  
  
## <a name="sql-limits"></a>SQL-Grenzwerte  
 Die folgenden Werte des *InfoType-Arguments* geben Informationen zu den Grenzwerten zurück, die auf Bezeichner und Klauseln in SQL-Anweisungen angewendet werden, z. B. die maximale Länge von Bezeichnern und die maximale Anzahl von Spalten in einer Auswahlliste. Einschränkungen können entweder vom Treiber oder von der Datenquelle auferlegt werden.  
  
|||  
|-|-|  
|SQL_MAX_BINARY_LITERAL_LEN|SQL_MAX_IDENTIFIER_LEN|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAX_INDEX_SIZE|  
|SQL_MAX_CHAR_LITERAL_LEN|SQL_MAX_PROCEDURE_NAME_LEN|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAX_ROW_SIZE|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAX_ROW_SIZE_INCLUDES_LONG|  
|SQL_MAX_COLUMNS_IN_INDEX|SQL_MAX_SCHEMA_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAX_STATEMENT_LEN|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAX_TABLE_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAX_TABLES_IN_SELECT|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAX_USER_NAME_LEN|  
  
## <a name="scalar-function-information"></a>Scalar-Funktionsinformationen  
 Die folgenden Werte des *InfoType-Arguments* geben Informationen zu den skalaren Funktionen zurück, die von der Datenquelle und dem Treiber unterstützt werden. Weitere Informationen zu skalaren Funktionen finden Sie in [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Konvertierungsinformationen  
 Die folgenden Werte des *InfoType-Arguments* geben eine Liste der SQL-Datentypen zurück, in die die Datenquelle den angegebenen SQL-Datentyp mit der scalar-Funktion **CONVERT** konvertieren kann:  
  
|||  
|-|-|  
|SQL_CONVERT_BIGINT|SQL_CONVERT_LONGVARBINARY|  
|SQL_CONVERT_BINARY|SQL_CONVERT_LONGVARCHAR|  
|SQL_CONVERT_BIT|SQL_CONVERT_NUMERIC|  
|SQL_CONVERT_CHAR|SQL_CONVERT_REAL|  
|SQL_CONVERT_DATE|SQL_CONVERT_SMALLINT|  
|SQL_CONVERT_DECIMAL|SQL_CONVERT_TIME|  
|SQL_CONVERT_DOUBLE|SQL_CONVERT_TIMESTAMP|  
|SQL_CONVERT_FLOAT|SQL_CONVERT_TINYINT|  
|SQL_CONVERT_INTEGER|SQL_CONVERT_VARBINARY|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_CONVERT_VARCHAR|  
|SQL_CONVERT_INTERVAL_DAY_TIME||  
  
## <a name="information-types-added-for-odbc-3x"></a>Hinzugefügte Informationstypen für ODBC 3.x  
 Die folgenden Werte des *InfoType-Arguments* wurden für ODBC 3 *.x*hinzugefügt:  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_DRIVER_AWARE_POOLING_SUPPORTED|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DRIVER_HDESC|  
|SQL_ALTER_DOMAIN|SQL_DROP_ASSERTION|  
|SQL_ALTER_SCHEMA|SQL_DROP_CHARACTER_SET|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_DROP_COLLATION|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_DROP_DOMAIN|  
|SQL_ASYNC_MODE|SQL_DROP_SCHEMA|  
|SQL_ASYNC_NOTIFICATION|SQL_DROP_TABLE|  
|SQL_BATCH_ROW_COUNT|SQL_DROP_TRANSLATION|  
|SQL_BATCH_SUPPORT|SQL_DROP_VIEW|  
|SQL_CATALOG_NAME|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|  
|SQL_COLLATION_SEQ|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|  
|SQL_CONVERT_INTERVAL_DAY_TIME|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_ASSERTION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_CREATE_CHARACTER_SET|SQL_INSERT_STATEMENT|  
|SQL_CREATE_COLLATION|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_CREATE_DOMAIN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_SCHEMA|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_CREATE_TABLE|SQL_MAX_IDENTIFIER_LEN|  
|SQL_CREATE_TRANSLATION|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_CURSOR_SENSITIVITY|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DDL_INDEX|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_DESCRIBE_PARAMETER|SQL_STATIC_CURSOR_ATTRIBUTES2|  
|SQL_DM_VER|SQL_XOPEN_CLI_YEAR|  
  
## <a name="information-types-renamed-for-odbc-3x"></a>Informationstypen umbenannt für ODBC 3.x  
 Die folgenden Werte des *InfoType-Arguments* wurden für ODBC 3 *.x*umbenannt.  
  
 SQL_ACTIVE_CONNECTIONS  
 SQL_MAX_DRIVER_CONNECTIONS  
  
 SQL_ACTIVE_STATEMENTS  
 SQL_MAX_CONCURRENT_ACTIVITIES  
  
 SQL_MAX_OWNER_NAME_LEN  
 SQL_MAX_SCHEMA_NAME_LEN  
  
 SQL_MAX_QUALIFIER_NAME_LEN  
 SQL_MAX_CATALOG_NAME_LEN  
  
 SQL_ODBC_SQL_OPT_IEF  
 SQL_INTEGRITY  
  
 SQL_OWNER_TERM  
 SQL_SCHEMA_TERM  
  
 SQL_OWNER_USAGE  
 SQL_SCHEMA_USAGE  
  
 SQL_QUALIFIER_LOCATION  
 SQL_CATALOG_LOCATION  
  
 SQL_QUALIFIER_NAME_SEPARATOR  
 SQL_CATALOG_NAME_SEPARATOR  
  
 SQL_QUALIFIER_TERM  
 SQL_CATALOG_TERM  
  
 SQL_QUALIFIER_USAGE  
 SQL_CATALOG_USAGE  
  
## <a name="information-types-deprecated-in-odbc-3x"></a>In ODBC 3.x veraltete Informationstypen  
 Die folgenden Werte des *InfoType-Arguments* sind in ODBC 3 *.x*veraltet. ODBC 3 *.x-Treiber* müssen diese Informationstypen weiterhin unterstützen, um die Abwärtskompatibilität mit ODBC 2 *.x-Anwendungen* zu ermöglichen. (Weitere Informationen zu diesen Typen finden Sie unter [SQLGetInfo-Support](../../../odbc/reference/appendixes/sqlgetinfo-support.md) in Anhang G: Treiberrichtlinien für Die Abwärtskompatibilität.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Beschreibungen des Informationstyps  
 In der folgenden Tabelle werden die einzelnen Informationstypen, die Version von ODBC, in der sie eingeführt wurde, und ihre Beschreibung alphabetisch aufgelistet.  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn der Benutzer alle von **SQLProcedures**zurückgegebenen Prozeduren ausführen kann; "N", wenn prozedursgebunden werden kann, die der Benutzer nicht ausführen kann.  
  
 SQL_ACCESSIBLE_TABLES(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn dem Benutzer **SELECT-Berechtigungen** für alle von **SQLTables**zurückgegebenen Tabellen garantiert werden; "N", wenn Möglicherweise Tabellen zurückgegeben werden, auf die der Benutzer nicht zugreifen kann.  
  
 SQL_ACTIVE_ENVIRONMENTS(ODBC 3.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl aktiver Umgebungen angibt, die der Treiber unterstützen kann. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung für Aggregationsfunktionen aufgibt:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer alle diese Optionen als unterstützt zurück.  
  
 SQL_ALTER_DOMAIN(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **ALTER DOMAIN-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle. Ein SQL-92 Full Level-kompatibler Treiber gibt immer alle Bitmasken zurück. Der Rückgabewert "0" bedeutet, dass die **ALTER DOMAIN-Anweisung** nicht unterstützt wird.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = Hinzufügen einer Domäneneinschränkung wird unterstützt (Vollständige Ebene)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT \<= Domänenändern> \<Festlegen von Domänenstandardklauseln> wird unterstützt (Vollständige Ebene)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION \<= Einschränkungsnamensdefinitionsklausel> wird für das Benennen von Domäneneinschränkung (Zwischenebene) unterstützt.  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT \<= Drop-Domain-Einschränkungsklausel> wird unterstützt (Vollständige Ebene)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT \<= Domain \<ändern> Domain-Standardklausel> wird unterstützt (Vollebene)  
  
 Die folgenden Bits \<geben die unterstützten Einschränkungsattribute> an, wenn \<die> hinzufügen von Domäneneinschränkungen unterstützt wird (das SQL_AD_ADD_DOMAIN_CONSTRAINT Bit ist festgelegt):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (Vollständige Stufe)SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (Vollständige Ebene)SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (Vollständige Stufe)SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (Vollständige Ebene)  
  
 SQL_ALTER_TABLE(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **ALTER TABLE-Anweisung** aufgibt, die von der Datenquelle unterstützt wird.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AT_ADD_COLUMN_COLLATION \<= Spaltenhinzufügen>-Klausel unterstützt wird, mit der Möglichkeit, die Spaltensortierung (Vollständige Ebene) anzugeben (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT \<= Spalten>-Klausel hinzufügen unterstützt wird, mit der Möglichkeit, Spaltenstandards (FIPS-Übergangsebene) anzugeben (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE \<= Spalte hinzufügen,> unterstützt wird (FIPS-Übergangsstufe) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT \<= Spalten>-Klausel hinzufügen unterstützt wird, mit der Möglichkeit, Spalteneinschränkungen (FIPS-Übergangsebene) anzugeben (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT \<= Tabelleneinschränkung hinzufügen>-Klausel unterstützt wird (FIPS-Übergangsebene) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION \<= Einschränkungsnamensdefinition> wird für Dasnamenspalten- und Tabelleneinschränkungen (Zwischenebene) (ODBC 3.0) unterstützt.  
  
 SQL_AT_DROP_COLUMN_CASCADE \<= Ablagespalte> CASCADE unterstützt wird (FIPS-Übergangsstufe) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT \<= Spalte \<ändern> Drop-Spalten-Standardklausel> unterstützt wird (Zwischenstufe) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT \<= Ablagespalte> RESTRICT wird unterstützt (FIPS-Übergangsstufe) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT \<= Ablagespalte> RESTRICT unterstützt wird (FIPS-Übergangsstufe) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT \<= Spalte \<ändern> Satzspaltenstandardklausel> unterstützt wird (Zwischenstufe) (ODBC 3.0)  
  
 Die folgenden Bits \<geben die Support-Einschränkungsattribute> an, wenn die Angabe von Spalten- oder Tabelleneinschränkungen unterstützt wird (das SQL_AT_ADD_CONSTRAINT Bit festgelegt ist):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (Vollstufe) (ODBC 3.0)SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (Vollstufe) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (Vollebene) (ODBC 3.0)SQL_AT_CONSTRAINT_NON_DEFERRABLE (Vollebene) (ODBC 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 Ein SQLUINTEGER-Wert, der angibt, ob der Treiber Funktionen asynchron auf dem Verbindungshandle ausführen kann.  
  
 SQL_ASYNC_DBC_CAPABLE = Der Treiber kann Verbindungsfunktionen asynchron ausführen.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = Der Treiber kann Verbindungsfunktionen nicht asynchron ausführen.  
  
 SQL_ASYNC_MODE(ODBC 3.0)  
 Ein SQLUINTEGER-Wert, der den Grad der asynchronen Unterstützung im Treiber angibt:  
  
 SQL_AM_CONNECTION = Asynchrone Ausführung auf Verbindungsebene wird unterstützt. Entweder befinden sich alle Anweisungshandles, die einem bestimmten Verbindungshandle zugeordnet sind, im asynchronen Modus oder alle befinden sich im synchronen Modus. Ein Anweisungshandle für eine Verbindung kann sich nicht im asynchronen Modus befinden, während sich ein anderes Anweisungshandle auf derselben Verbindung im synchronen Modus befindet und umgekehrt.  
  
 SQL_AM_STATEMENT = Asynchrone Ausführung auf Anweisungsebene wird unterstützt. Einige Anweisungshandles, die einem Verbindungshandle zugeordnet sind, können sich im asynchronen Modus befinden, während andere Anweisungshandles auf derselben Verbindung sich im synchronen Modus befinden.  
  
 SQL_AM_NONE = Der asynchrone Modus wird nicht unterstützt.  
  
 SQL_ASYNC_NOTIFICATION  
 Ein SQLUINTEGER-Wert, der angibt, ob der Treiber asynchrone Benachrichtigungen unterstützt:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** Die asynchrone Ausführungsbenachrichtigung wird vom Treiber unterstützt.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** Die asynchrone Ausführungsbenachrichtigung wird vom Treiber nicht unterstützt.  
  
 Es gibt zwei Kategorien von asynchronen ODBC-Vorgängen: asynchrone Vorgänge auf Verbindungsebene und asynchrone Vorgänge auf Anweisungsebene.  Wenn ein Treiber SQL_ASYNC_NOTIFICATION_CAPABLE zurückgibt, muss er die Benachrichtigung für alle APIs unterstützen, die er asynchron ausführen kann.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die das Verhalten des Treibers in Bezug auf die Verfügbarkeit von Zeilenanzahlen aufzählt. Die folgenden Bitmasken werden zusammen mit dem Informationstyp verwendet:  
  
 SQL_BRC_ROLLED_UP = Zeilenanzahlen für aufeinander folgende INSERT-, DELETE- oder UPDATE-Anweisungen werden in einer zusammengerollt. Wenn dieses Bit nicht festgelegt ist, sind Zeilenanzahlen für jede Anweisung verfügbar.  
  
 SQL_BRC_PROCEDURES = Zeilenanzahlen, falls vorhanden, sind verfügbar, wenn ein Batch in einer gespeicherten Prozedur ausgeführt wird. Wenn Zeilenanzahlen verfügbar sind, können sie je nach SQL_BRC_ROLLED_UP Bit aufgerollt oder einzeln verfügbar sein.  
  
 SQL_BRC_EXPLICIT = Zeilenanzahlen, falls vorhanden, sind verfügbar, wenn ein Batch direkt durch Aufrufen von **SQLExecute** oder **SQLExecDirect**ausgeführt wird. Wenn Zeilenanzahlen verfügbar sind, können sie je nach SQL_BRC_ROLLED_UP Bit aufgerollt oder einzeln verfügbar sein.  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung des Treibers für Batches aufgibt. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Ebene unterstützt wird:  
  
 SQL_BS_SELECT_EXPLICIT = Der Treiber unterstützt explizite Batches, die Ergebnis-Set-Generierungsanweisungen haben können.  
  
 SQL_BS_ROW_COUNT_EXPLICIT = Der Treiber unterstützt explizite Batches, die Zeilenanzahl generierende Anweisungen haben können.  
  
 SQL_BS_SELECT_PROC = Der Treiber unterstützt explizite Prozeduren, die Ergebnis-Set-Generierungsanweisungen haben können.  
  
 SQL_BS_ROW_COUNT_PROC = Der Treiber unterstützt explizite Prozeduren, die Zeilenzähl-Generierungsanweisungen haben können.  
  
 SQL_BOOKMARK_PERSISTENCE(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Vorgänge aufgibt, durch die Lesezeichen beibehalten werden.  
  
 Die folgenden Bitmasken werden zusammen mit dem Flag verwendet, um zu bestimmen, durch welche Optionen Lesezeichen beibehalten werden:  
  
 SQL_BP_CLOSE = Lesezeichen sind gültig, nachdem eine Anwendung **SQLFreeStmt** mit der Option SQL_CLOSE oder **SQLCloseCursor** aufruft, um den Cursor zu schließen, der einer Anweisung zugeordnet ist.  
  
 SQL_BP_DELETE = Die Textmarke für eine Zeile ist gültig, nachdem diese Zeile gelöscht wurde.  
  
 SQL_BP_DROP = Lesezeichen sind gültig, nachdem eine Anwendung **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_STMT aufruft, um eine Anweisung zu löschen.  
  
 SQL_BP_TRANSACTION = Lesezeichen sind gültig, nachdem eine Anwendung eine Transaktion festschreibt oder zurücksetzt.  
  
 SQL_BP_UPDATE = Die Textmarke für eine Zeile ist gültig, nachdem eine Spalte in dieser Zeile aktualisiert wurde, einschließlich Schlüsselspalten.  
  
 SQL_BP_OTHER_HSTMT = Eine Einer Anweisung zugeordnete Textmarke kann mit einer anderen Anweisung verwendet werden. Sofern nicht SQL_BP_CLOSE oder SQL_BP_DROP angegeben ist, muss der Cursor der ersten Anweisung geöffnet sein.  
  
 SQL_CATALOG_LOCATION(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die Position des Katalogs in einem qualifizierten Tabellennamen angibt:  
  
 SQL_CL_STARTSQL_CL_END  
  
 Ein Xbase-Treiber gibt z. B. SQL_CL_START zurück, da sich der Verzeichnisname (Katalogname) am Anfang des Tabellennamens befindet, wie in der Datei "EMPDATA". Dbf. Ein ORACLE Server-Treiber gibt SQL_CL_END zurück, da sich der ADMIN.EMP@EMPDATAKatalog am Ende des Tabellennamens befindet, wie in .  
  
 Ein SQL-92 Full Level-conformant-Treiber gibt immer SQL_CL_START zurück. Der Wert 0 wird zurückgegeben, wenn Kataloge von der Datenquelle nicht unterstützt werden. Um zu bestimmen, ob Kataloge unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_CATALOG_NAME-Informationstyp auf.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_QUALIFIER_LOCATION* für ODBC 3.0 umbenannt.  
  
 SQL_CATALOG_NAME(ODBC 3.0)  
 Eine Zeichenfolge: "Y", wenn der Server Katalognamen unterstützt, oder "N", wenn dies nicht der Fall ist.  
  
 Ein SQL-92 Full level-conformant Treiber gibt immer "Y" zurück.  
  
 SQL_CATALOG_NAME_SEPARATOR(ODBC 1.0)  
 Eine Zeichenfolge: das Zeichen oder die Zeichen, die die Datenquelle als Trennzeichen zwischen einem Katalognamen und dem qualifizierten Namenselement definiert, das ihm folgt oder ihm vorangeht.  
  
 Eine leere Zeichenfolge wird zurückgegeben, wenn Kataloge von der Datenquelle nicht unterstützt werden. Um zu bestimmen, ob Kataloge unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_CATALOG_NAME-Informationstyp auf. Ein SQL-92 Full level-conformant-Treiber gibt immer "." zurück.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_QUALIFIER_NAME_SEPARATOR* für ODBC 3.0 umbenannt.  
  
 SQL_CATALOG_TERM(ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen des Datenquellenanbieters für einen Katalog; z. B. "Datenbank" oder "Verzeichnis". Diese Zeichenfolge kann in Groß-, Klein- oder Mischfällen sein.  
  
 Eine leere Zeichenfolge wird zurückgegeben, wenn Kataloge von der Datenquelle nicht unterstützt werden. Um zu bestimmen, ob Kataloge unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_CATALOG_NAME-Informationstyp auf. Ein SQL-92 Full level-conformant Treiber gibt immer "Katalog" zurück.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_QUALIFIER_TERM* für ODBC 3.0 umbenannt.  
  
 SQL_CATALOG_USAGE(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Anweisungen aufgibt, in denen Kataloge verwendet werden können.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, wo Kataloge verwendet werden können:  
  
 SQL_CU_DML_STATEMENTS = Kataloge werden in allen Anweisungen zur Datenmanipulationssprache unterstützt: **SELECT**, **INSERT**, **UPDATE**, **DELETE**, und wenn unterstützt, SELECT **FOR UPDATE** und positionierte Update- und Löschanweisungen.  
  
 SQL_CU_PROCEDURE_INVOCATION = Kataloge werden in der Aufrufanweisung der ODBC-Prozedur unterstützt.  
  
 SQL_CU_TABLE_DEFINITION = Kataloge werden in allen Tabellendefinitionsanweisungen unterstützt: **CREATE TABLE**, **CREATE VIEW**, ALTER **TABLE**, **DROP TABLE**und DROP **VIEW**.  
  
 SQL_CU_INDEX_DEFINITION = Kataloge werden in allen Indexdefinitionsanweisungen unterstützt: **CREATE INDEX** und **DROP INDEX**.  
  
 SQL_CU_PRIVILEGE_DEFINITION = Kataloge werden in allen Berechtigungsdefinitionsanweisungen unterstützt: **GRANT** und **REVOKE**.  
  
 Der Wert 0 wird zurückgegeben, wenn Kataloge von der Datenquelle nicht unterstützt werden. Um zu bestimmen, ob Kataloge unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_CATALOG_NAME-Informationstyp auf. Ein SQL-92 Full level-conformant Treiber gibt immer eine Bitmaske mit all diesen Bits zurück.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_QUALIFIER_USAGE* für ODBC 3.0 umbenannt.  
  
 SQL_COLLATION_SEQ(ODBC 3.0)  
 Der Name der Sortierungssequenz. Dies ist eine Zeichenfolge, die den Namen der Standardsortierung für den Standardzeichensatz für diesen Server angibt (z. B. 'ISO 8859-1' oder EBCDIC). Wenn dies unbekannt ist, wird eine leere Zeichenfolge zurückgegeben. Ein SQL-92 Full level-conformant-Treiber gibt immer eine nicht leere Zeichenfolge zurück.  
  
 SQL_COLUMN_ALIAS(ODBC 2.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle Spaltenaliase unterstützt; andernfalls "N".  
  
 Ein Spaltenalias ist ein alternativer Name, der mithilfe einer AS-Klausel für eine Spalte in der Auswahlliste angegeben werden kann. Ein SQL-92 Entry-Level-konformer Treiber gibt immer "Y" zurück.  
  
 SQL_CONCAT_NULL_BEHAVIOR(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der angibt, wie die Datenquelle die Verkettung von NULL-Wertzeichendatentypspalten mit Nicht-NULL-Wertzeichendatentypspalten verarbeitet:  
  
 SQL_CB_NULL = Ergebnis ist NULL bewertet.  
  
 SQL_CB_NON_NULL = Ergebnis ist die Verkettung von Nicht-NULL-Bewerteten Spalten oder Spalten.  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer SQL_CB_NULL zurück.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 Eine SQLUINTEGER-Bitmaske. Die Bitmaske gibt die Konvertierungen an, die von der Datenquelle mit der **scalar-Funktion CONVERT** für Daten des im *InfoType*genannten Typs unterstützt werden. Wenn die Bitmaske gleich Null ist, unterstützt die Datenquelle keine Konvertierungen aus Daten des benannten Typs, einschließlich der Konvertierung in denselben Datentyp.  
  
 Um beispielsweise zu ermitteln, ob eine Datenquelle die Konvertierung SQL_INTEGER Daten in den SQL_BIGINT Datentyp unterstützt, ruft eine Anwendung **SQLGetInfo** mit dem *InfoType* von SQL_CONVERT_INTEGER auf. Die Anwendung führt einen **UND-Vorgang** mit der zurückgegebenen Bitmaske und SQL_CVT_BIGINT aus. Wenn der resultierende Wert ungleich Null ist, wird die Konvertierung unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Konvertierungen unterstützt werden:  
  
 SQL_CVT_BIGINT (ODBC 1.0)SQL_CVT_BINARY (ODBC 1.0)SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5)SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0)SQL_CVT_DECIMAL (ODBC 1.0)SQL_CVT_DOUBLE (ODBC 1 0)SQL_CVT_FLOAT (ODBC 1.0)SQL_CVT_INTEGER (ODBC 1.0)SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 3.0)SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARCHAR (ODBC 1.0)SQL_CVT_NUMERIC (ODBC 1.0)SQL_ CVT_REAL ODBC 1.0)SQL_CVT_SMALLINT (ODBC 1.0)SQL_CVT_TIME (ODBC 1.0)SQL_CVT_TIMESTAMP (ODBC 1.0)SQL_CVT_TINYINT (ODBC 1.0)SQL_CVT_VARBINARY (ODBC 1.0)SQL_CVT_VARCHAR (ODBC 1.0))  
  
 SQL_CONVERT_FUNCTIONS(ODBC 1.0)  
 Eine SQLUINTEGER-Bitmaske, die die vom Treiber und der zugehörigen Datenquelle unterstützten skalaren Konvertierungsfunktionen aufgibt.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Konvertierungsfunktionen unterstützt werden:  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der angibt, ob Tabellenkorrelationsnamen unterstützt werden:  
  
 SQL_CN_NONE = Korrelationsnamen werden nicht unterstützt.  
  
 SQL_CN_DIFFERENT = Korrelationsnamen werden unterstützt, müssen sich jedoch von den Namen der Tabellen unterscheiden, die sie darstellen.  
  
 SQL_CN_ANY = Korrelationsnamen werden unterstützt und können ein beliebiger gültiger benutzerdefinierter Name sein.  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer SQL_CN_ANY zurück.  
  
 SQL_CREATE_ASSERTION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE ASSERTION-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CA_CREATE_ASSERTION  
  
 Die folgenden Bits geben das unterstützte Einschränkungsattribut an, wenn die Möglichkeit, Einschränkungsattribute explizit anzugeben, unterstützt wird (siehe SQL_ALTER_TABLE und SQL_CREATE_TABLE Informationstypen):  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Ein SQL-92 Full level-conformant-Treiber gibt immer alle diese Optionen als unterstützt zurück. Der Rückgabewert "0" bedeutet, dass die **CREATE ASSERTION-Anweisung** nicht unterstützt wird.  
  
 SQL_CREATE_CHARACTER_SET(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE CHARACTER SET-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Ein SQL-92 Full level-conformant-Treiber gibt immer alle diese Optionen als unterstützt zurück. Ein Rückgabewert von "0" bedeutet, dass die **CREATE CHARACTER SET-Anweisung** nicht unterstützt wird.  
  
 SQL_CREATE_COLLATION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE COLLATION-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Ein SQL-92 Full level-conformant-Treiber gibt diese Option immer als unterstützt zurück. Der Rückgabewert "0" bedeutet, dass die **CREATE COLLATION-Anweisung** nicht unterstützt wird.  
  
 SQL_CREATE_DOMAIN(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE DOMAIN-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CDO_CREATE_DOMAIN = Die CREATE DOMAIN-Anweisung wird unterstützt (Zwischenstufe).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION \<= Einschränkungsnamensdefinition> wird für das Benennen von Domäneneinschränkungen (Zwischenebene) unterstützt.  
  
 Die folgenden Bits geben die Möglichkeit an, Spalteneinschränkungen zu erstellen:SQL_CDO_DEFAULT = Angeben von Domäneneinschränkungen wird unterstützt (Zwischenstufe)SQL_CDO_CONSTRAINT = Angeben von Domänenstandards wird unterstützt (Zwischenstufe)SQL_CDO_COLLATION = Angeben der Domänensortierung wird unterstützt (Vollständige Ebene)  
  
 Die folgenden Bits geben die unterstützten Einschränkungsattribute an, wenn die Angabe von Domäneneinschränkungen unterstützt wird (SQL_CDO_DEFAULT festgelegt ist):  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (Vollständige Stufe)SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (Vollständige Ebene)SQL_CDO_CONSTRAINT_DEFERRABLE (Vollständige Ebene)SQL_CDO_CONSTRAINT_NON_DEFERRABLE (Vollständige Ebene)  
  
 Der Rückgabewert "0" bedeutet, dass die **CREATE DOMAIN-Anweisung** nicht unterstützt wird.  
  
 SQL_CREATE_SCHEMA(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE SCHEMA-Anweisung** aufgibt, wie in SQL-92 definiert, wird von der Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 Ein SQL-92 Intermediate Level-conformant-Treiber gibt immer die SQL_CS_CREATE_SCHEMA- und SQL_CS_AUTHORIZATION-Optionen als unterstützt zurück. Diese müssen auch auf SQL-92-Einstiegsebene unterstützt werden, jedoch nicht unbedingt als SQL-Anweisungen. Ein SQL-92 Full level-conformant-Treiber gibt immer alle diese Optionen als unterstützt zurück.  
  
 SQL_CREATE_TABLE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE TABLE-Anweisung** aufgibt, wie in SQL-92 definiert, wird von der Datenquelle unterstützt.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CT_CREATE_TABLE = Die CREATE TABLE-Anweisung wird unterstützt. (Einstiegsstufe)  
  
 SQL_CT_TABLE_CONSTRAINT = Angeben von Tabelleneinschränkungen wird unterstützt (FIPS-Übergangsebene)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = \<Die Einschränkungsnamendefinition>-Klausel wird für das Benennen von Spalten- und Tabelleneinschränkungen (Zwischenebene) unterstützt.  
  
 Die folgenden Bits geben die Möglichkeit an, temporäre Tabellen zu erstellen:  
  
 SQL_CT_COMMIT_PRESERVE = Gelöschte Zeilen werden beim Commit beibehalten. (Vollständige Ebene) SQL_CT_COMMIT_DELETE = Gelöschte Zeilen werden beim Commit gelöscht. (Vollständige Ebene) SQL_CT_GLOBAL_TEMPORARY = Globale temporäre Tabellen können erstellt werden. (Vollständige Ebene) SQL_CT_LOCAL_TEMPORARY = Lokale temporäre Tabellen können erstellt werden. (Vollständige Ebene)  
  
 Die folgenden Bits geben die Möglichkeit an, Spalteneinschränkungen zu erstellen:  
  
 SQL_CT_COLUMN_CONSTRAINT = Das Angeben von Spalteneinschränkungen wird unterstützt (FIPS-Übergangsstufe)SQL_CT_COLUMN_DEFAULT = Angeben von Spaltenstandards wird unterstützt (FIPS-Übergangsstufe)SQL_CT_COLUMN_COLLATION = Angeben der Spaltensortierung wird unterstützt (Vollständige Ebene)  
  
 Die folgenden Bits geben die unterstützten Einschränkungsattribute an, wenn die Angabe von Spalten- oder Tabelleneinschränkungen unterstützt wird:  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (Vollständige Stufe)SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (Vollständige Stufe)SQL_CT_CONSTRAINT_DEFERRABLE (Vollständige Ebene)SQL_CT_CONSTRAINT_NON_DEFERRABLE (Vollständige Ebene)  
  
 SQL_CREATE_TRANSLATION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE TRANSLATION-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Ein SQL-92 Full level-conformant-Treiber gibt diese Optionen immer als unterstützt zurück. Der Rückgabewert "0" bedeutet, dass die **CREATE TRANSLATION-Anweisung** nicht unterstützt wird.  
  
 SQL_CREATE_VIEW(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE VIEW-Anweisung** aufgibt, wie in SQL-92 definiert, wird von der Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Der Rückgabewert "0" bedeutet, dass die **CREATE VIEW-Anweisung** nicht unterstützt wird.  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer die SQL_CV_CREATE_VIEW- und SQL_CV_CHECK_OPTION-Optionen als unterstützt zurück.  
  
 Ein SQL-92 Full level-conformant-Treiber gibt immer alle diese Optionen als unterstützt zurück.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der angibt, wie sich ein **COMMIT-Vorgang** auf Cursor und vorbereitete Anweisungen in der Datenquelle auswirkt (das Verhalten der Datenquelle beim Commit einer Transaktion).  
  
 Der Wert dieses Attributs spiegelt den aktuellen Status der nächsten Einstellung wider: SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE = Cursor schließen und vorbereitete Anweisungen löschen. Um den Cursor erneut zu verwenden, muss die Anwendung die Anweisung neu vorbereiten und erneut ausführen.  
  
 SQL_CB_CLOSE = Cursor schließen. Für vorbereitete Anweisungen kann die Anwendung **SQLExecute** für die Anweisung aufrufen, ohne **SQLPrepare** erneut aufzurufen. Die Standardeinstellung für den SQL ODBC-Treiber ist SQL_CB_CLOSE. Dies bedeutet, dass der SQL ODBC-Treiber den Cursor(n) schließt, wenn Sie eine Transaktion übertragen.  
  
 SQL_CB_PRESERVE = Cursor an der gleichen Position wie vor dem **COMMIT-Vorgang** beibehalten. Die Anwendung kann weiterhin Daten abrufen, oder sie kann den Cursor schließen und die Anweisung erneut ausführen, ohne sie erneut vorzubereiten.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der angibt, wie sich ein **ROLLBACK-Vorgang** auf Cursor und vorbereitete Anweisungen in der Datenquelle auswirkt:  
  
 SQL_CB_DELETE = Cursor schließen und vorbereitete Anweisungen löschen. Um den Cursor erneut zu verwenden, muss die Anwendung die Anweisung neu vorbereiten und erneut ausführen.  
  
 SQL_CB_CLOSE = Cursor schließen. Für vorbereitete Anweisungen kann die Anwendung **SQLExecute** für die Anweisung aufrufen, ohne **SQLPrepare** erneut aufzurufen.  
  
 SQL_CB_PRESERVE = Cursor an der gleichen Position wie vor dem **ROLLBACK-Vorgang** beibehalten. Die Anwendung kann weiterhin Daten abrufen, oder sie kann den Cursor schließen und die Anweisung erneut ausführen, ohne sie erneut vorzubereiten.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 Ein SQLUINTEGER-Wert, der die Unterstützung für die Cursorempfindlichkeit angibt:  
  
 SQL_INSENSITIVE = Alle Cursor im Anweisungshandle zeigen das Resultset an, ohne dass Änderungen widergespiegelt werden, die von einem anderen Cursor innerhalb derselben Transaktion vorgenommen wurden.  
  
 SQL_UNSPECIFIED = Es ist nicht angegeben, ob Cursor im Anweisungshandle die Änderungen sichtbar machen, die von einem anderen Cursor innerhalb derselben Transaktion an einem Ergebnissatz vorgenommen wurden. Cursor im Anweisungshandle können keine, keine oder alle derartigen Änderungen sichtbar machen.  
  
 SQL_SENSITIVE = Cursor reagieren empfindlich auf Änderungen, die von anderen Cursorn innerhalb derselben Transaktion vorgenommen wurden.  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer die SQL_UNSPECIFIED Option als unterstützt zurück.  
  
 Ein SQL-92 Full level-conformant-Treiber gibt immer die SQL_INSENSITIVE Option als unterstützt zurück.  
  
 SQL_DATA_SOURCE_NAME(ODBC 1.0)  
 Eine Zeichenfolge mit dem Datenquellennamen, der während der Verbindung verwendet wurde. Wenn die Anwendung **SQLConnect**heißt, ist dies der Wert des *szDSN-Arguments.* Wenn die Anwendung **SQLDriverConnect** oder **SQLBrowseConnect**heißt, ist dies der Wert des DSN-Schlüsselworts in der Verbindungszeichenfolge, die an den Treiber übergeben wird. Wenn die Verbindungszeichenfolge das **DSN-Schlüsselwort** nicht enthält (z. B. wenn sie das **SCHLÜSSELwort DRIVER** enthält), handelt es sich um eine leere Zeichenfolge.  
  
 SQL_DATA_SOURCE_READ_ONLY(ODBC 1.0)  
 Eine Zeichenfolge. "Y", wenn die Datenquelle auf READ ONLY-Modus eingestellt ist, "N", wenn es anders ist.  
  
 Dieses Merkmal bezieht sich nur auf die Datenquelle selbst; Es ist kein Merkmal des Treibers, das den Zugriff auf die Datenquelle ermöglicht. Ein Lese-/Schreibtreiber kann mit einer schreibgeschützten Datenquelle verwendet werden. Wenn ein Treiber schreibgeschützt ist, müssen alle Datenquellen schreibgeschützt sein und SQL_DATA_SOURCE_READ_ONLY zurückgeben.  
  
 SQL_DATABASE_NAME(ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen der aktuellen Datenbank, die verwendet wird, wenn die Datenquelle ein benanntes Objekt namens "Datenbank" definiert.  
  
> [!NOTE]
>  In ODBC 3 *.x*kann der für diesen *InfoType* zurückgegebene Wert auch zurückgegeben werden, indem **SQLGetConnectAttr** mit dem *Attributargument* SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die VON der Datenquelle unterstützten SQL-92-Datumszeitliterale aufgibt. Beachten Sie, dass dies die in der SQL-92-Spezifikation aufgeführten Datumszeitliterale sind und von den von ODBC definierten Datumsliteral-Escapeklauseln getrennt sind. Weitere Informationen zu den ODBC datetime-Literal-Escape-Klauseln finden Sie unter [Datum, Uhrzeit und Zeitstempelliterale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Ein FIPS Transitional Level-conformant Treiber gibt immer den Wert "1" in der Bitmaske für die Bits in der folgenden Liste zurück. Der Wert "0" bedeutet, dass SQL-92-Datumszeitliterale nicht unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Literale unterstützt werden:  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME(ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen des DBMS-Produkts, auf das der Treiber zugreift.  
  
 SQL_DBMS_VER(ODBC 1.0)  
 Eine Zeichenfolge, die die Version des DBMS-Produkts angibt, auf das der Treiber zugreift. Die Version ist von der Form ... . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . Der Treiber muss die DBMS-Produktversion in diesem Formular rendern, kann aber auch die produktspezifische DBMS-Version anhängen. Beispiel: "04.01.0000 Rdb 4.1".  
  
 SQL_DDL_INDEX(ODBC 3.0)  
 Ein SQLUINTEGER-Wert, der die Unterstützung für das Erstellen und Ablegen von Indizes angibt:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION(ODBC 1.0)  
 Ein SQLUINTEGER-Wert, der die standardmäßige Transaktionsisolationsstufe angibt, die vom Treiber oder der Datenquelle unterstützt wird, oder Null, wenn die Datenquelle Keine Transaktionen unterstützt. Die folgenden Begriffe werden verwendet, um Transaktionsisolationsstufen zu definieren:  
  
 **Dirty Read** Transaktion 1 ändert eine Zeile. Transaktion 2 liest die geänderte Zeile, bevor Transaktion 1 die Änderung feststellt. Wenn Transaktion 1 einen Rollback für die Änderung vorschreibt, hat Transaktion 2 eine Zeile gelesen, die als nie vorhanden gilt.  
  
 **Nicht wiederholbares Lesen** Transaktion 1 liest eine Zeile. Transaktion 2 aktualisiert oder löscht diese Zeile und überträgt diese Änderung. Wenn Transaktion 1 versucht, die Zeile erneut zu lesen, erhält sie unterschiedliche Zeilenwerte oder stellt fest, dass die Zeile gelöscht wurde.  
  
 **Phantom** Transaktion 1 liest eine Reihe von Zeilen, die einige Suchkriterien erfüllen. Transaktion 2 generiert eine oder mehrere Zeilen (durch Einfügungen oder Aktualisierungen), die den Suchkriterien entsprechen. Wenn Transaktion 1 die Anweisung, die die Zeilen liest, erneut ausführt, erhält sie einen anderen Satz von Zeilen.  
  
 Wenn die Datenquelle Transaktionen unterstützt, gibt der Treiber eine der folgenden Bitmasken zurück:  
  
 SQL_TXN_READ_UNCOMMITTED = Schmutzige Lesevorgänge, nicht wiederholbare Lesevorgänge und Phantome sind möglich.  
  
 SQL_TXN_READ_COMMITTED = Schmutzige Lesevorgänge sind nicht möglich. Nicht wiederholbare Lesevorgänge und Phantome sind möglich.  
  
 SQL_TXN_REPEATABLE_READ = Schmutzige Lesevorgänge und nicht wiederholbare Lesevorgänge sind nicht möglich. Phantome sind möglich.  
  
 SQL_TXN_SERIALIZABLE = Transaktionen sind serialisierbar. Serialisierbare Transaktionen lassen keine schmutzigen Lesevorgänge, nicht wiederholbaren Lesevorgänge oder Phantome zu.  
  
 SQL_DESCRIBE_PARAMETER(ODBC 3.0)  
 Eine Zeichenfolge: "Y", wenn Parameter beschrieben werden können; "N", wenn nicht.  
  
 Ein SQL-92 Full level-conformant-Treiber gibt normalerweise "Y" zurück, da er die **DESCRIBE INPUT-Anweisung** unterstützt. Da dadurch die zugrunde liegende SQL-Unterstützung nicht direkt angegeben wird, wird die Beschreibung von Parametern möglicherweise nicht unterstützt, selbst in einem SQL-92 Full level-conformant-Treiber.  
  
 SQL_DM_VER(ODBC 3.0)  
 Eine Zeichenfolge mit der Version des Treiber-Managers. Die Version ist von der Form ... . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .  
  
 Der erste Satz von zwei Ziffern ist die Haupt-ODBC-Version, wie durch die konstante SQL_SPEC_MAJOR angegeben.  
  
 Der zweite Satz von zwei Ziffern ist die kleinere ODBC-Version, wie durch die konstante SQL_SPEC_MINOR angegeben.  
  
 Der dritte Satz von vier Ziffern ist die Hauptbuildnummer des Treiber-Managers.  
  
 Der letzte Satz von vier Ziffern ist die untergeordnete Buildnummer des Treiber-Managers.  
  
 Die Windows 7 Driver Manager-Version ist 03.80. Die Windows 8 Driver Manager Version ist 03.81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 Ein SQLUINTEGER-Wert, der angibt, ob der Treiber das treiberorientierte Pooling unterstützt. (Weitere Informationen finden Sie unter [Treiber-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE gibt an, dass der Treiber den fahrerbewussten Pooling-Mechanismus unterstützen kann.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE gibt an, dass der Treiber den treiberbewussten Pooling-Mechanismus nicht unterstützen kann.  
  
 Ein Treiber muss keine SQL_DRIVER_AWARE_POOLING_SUPPORTED implementieren, und der Treiber-Manager wird den Rückgabewert des Treibers nicht berücksichtigen.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV(ODBC 1.0)  
 Ein SQLULEN-Wert, das Umgebungshandle oder verbindungshandle des Treibers, bestimmt durch das Argument *InfoType*.  
  
 Diese Informationstypen werden nur vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_HDESC(ODBC 3.0)  
 Ein SQLULEN-Wert, das Deskriptorhandle des Treibers, das durch das Deskriptorhandle \*des Treiber-Managers bestimmt wird, das an die Eingabe in *InfoValuePtr* aus der Anwendung übergeben werden muss. In diesem Fall ist *InfoValuePtr* sowohl ein Eingabe- als auch ein Ausgabeargument. Das in \* *InfoValuePtr* übergebene Eingabedeskriptorhandle muss entweder explizit oder implizit im *ConnectionHandle*zugewiesen worden sein.  
  
 Die Anwendung sollte eine Kopie des Deskriptor-Handles des Treiber-Managers erstellen, bevor sie **SQLGetInfo** mit diesem Informationstyp aufruft, um sicherzustellen, dass das Handle bei der Ausgabe nicht überschrieben wird.  
  
 Dieser Informationstyp wird nur vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_HLIB(ODBC 2.0)  
 Ein SQLULEN-Wert, der *Hinweis* aus der Ladebibliothek, die an den Treiber-Manager zurückgegeben wurde, wenn er die Treiber-DLL auf ein Microsoft Windows-Betriebssystem geladen hat, oder das entsprechende auf einem anderen Betriebssystem. Das Handle ist nur für das Verbindungshandle gültig, das im Aufruf von **SQLGetInfo**angegeben ist.  
  
 Dieser Informationstyp wird nur vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_HSTMT(ODBC 1.0)  
 Ein SQLULEN-Wert, das Anweisungshandle des Treibers, das durch das \*Driver Manager-Anweisungshandle bestimmt wird, das an die Eingabe in *InfoValuePtr* aus der Anwendung übergeben werden muss. In diesem Fall ist *InfoValuePtr* sowohl ein Eingabe- als auch ein Ausgabeargument. Das in \* *InfoValuePtr* übergebene Eingabeanweisungshandle muss dem Argument *ConnectionHandle*zugeordnet worden sein.  
  
 Die Anwendung sollte eine Kopie des Anweisungshandles des Treiber-Managers erstellen, bevor sie **SQLGetInfo** mit diesem Informationstyp aufruft, um sicherzustellen, dass das Handle bei der Ausgabe nicht überschrieben wird.  
  
 Dieser Informationstyp wird nur vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_NAME(ODBC 1.0)  
 Eine Zeichenfolge mit dem Dateinamen des Treibers, der für den Zugriff auf die Datenquelle verwendet wird.  
  
 SQL_DRIVER_ODBC_VER(ODBC 2.0)  
 Eine Zeichenfolge mit der ODBC-Version, die vom Treiber unterstützt wird. Die Version ist von der Form ,,."""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""" SQL_SPEC_MAJOR und SQL_SPEC_MINOR die Haupt- und Nebenversionsnummern definieren. Für die in diesem Handbuch beschriebene Version von ODBC sind diese 3 und 0, und der Treiber sollte "03.00" zurückgeben.  
  
 Der ODBC-Treiber-Manager ändert den Rückgabewert von SQLGetInfo(SQL_DRIVER_ODBC_VER) nicht, um die Abwärtskompatibilität für vorhandene Anwendungen beizubehalten. Der Treiber gibt an, welcher Wert zurückgegeben wird. Ein Treiber, der die Erweiterbarkeit des C-Datentyps unterstützt, muss jedoch 3.8 (oder höher) zurückgeben, wenn eine Anwendung **SQLSetEnvAttr** aufruft, um SQL_ATTR_ODBC_VERSION auf 3.8 festzulegen. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER(ODBC 1.0)  
 Eine Zeichenfolge mit der Version des Treibers und optional eine Beschreibung des Treibers. Die Version ist mindestens von der Form "." und hat die erste zweite Ziffer die Hauptversion, die nächsten beiden Ziffern sind die Nebenversion und die letzten vier Ziffern die Release-Version.  
  
 SQL_DROP_ASSERTION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **DROP ASSERTION-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DA_DROP_ASSERTION  
  
 Ein SQL-92 Full level-conformant-Treiber gibt diese Option immer als unterstützt zurück.  
  
 SQL_DROP_CHARACTER_SET(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **DROP CHARACTER SET-Anweisung** aufgibt, wie in SQL-92 definiert, wird von der Datenquelle unterstützt.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Ein SQL-92 Full level-conformant-Treiber gibt diese Option immer als unterstützt zurück.  
  
 SQL_DROP_COLLATION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **DROP COLLATION-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DC_DROP_COLLATION  
  
 Ein SQL-92 Full level-conformant-Treiber gibt diese Option immer als unterstützt zurück.  
  
 SQL_DROP_DOMAIN(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **DROP DOMAIN-Anweisung** aufgibt, wie in SQL-92 definiert, wird von der Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 Ein SQL-92 Intermediate Level-conformant-Treiber gibt immer alle diese Optionen als unterstützt zurück.  
  
 SQL_DROP_SCHEMA(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **DROP SCHEMA-Anweisung** aufgibt, wie in SQL-92 definiert, wird von der Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 Ein SQL-92 Intermediate Level-conformant-Treiber gibt immer alle diese Optionen als unterstützt zurück.  
  
 SQL_DROP_TABLE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **DROP TABLE-Anweisung** aufgibt, wie in SQL-92 definiert, wird von der Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Ein FIPS Transitional Level-conformant Treiber gibt immer alle diese Optionen wie unterstützt zurück.  
  
 SQL_DROP_TRANSLATION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **DROP TRANSLATION-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Ein SQL-92 Full level-conformant-Treiber gibt diese Option immer als unterstützt zurück.  
  
 SQL_DROP_VIEW(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **DROP VIEW-Anweisung** aufgibt, wie in SQL-92 definiert, wird von der Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Ein FIPS Transitional Level-conformant Treiber gibt immer alle diese Optionen wie unterstützt zurück.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines dynamischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die erste Teilmenge von Attributen. für die zweite Teilmenge siehe SQL_DYNAMIC_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXT = Ein *FetchOrientation-Argument* von SQL_FETCH_NEXT wird in einem Aufruf von **SQLFetchScroll** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_ABSOLUTE = *FetchOrientation-Argumente* von SQL_FETCH_FIRST, SQL_FETCH_LAST und SQL_FETCH_ABSOLUTE werden in einem Aufruf von **SQLFetchScroll** unterstützt, wenn der Cursor ein dynamischer Cursor ist. (Das Rowset, das abgerufen wird, ist unabhängig von der aktuellen Cursorposition.)  
  
 SQL_CA1_RELATIVE = *FetchOrientation-Argumente* von SQL_FETCH_PRIOR und SQL_FETCH_RELATIVE werden in einem Aufruf von **SQLFetchScroll** unterstützt, wenn der Cursor ein dynamischer Cursor ist. (Das Rowset, das abgerufen wird, hängt von der aktuellen Cursorposition ab. Beachten Sie, dass dies von SQL_FETCH_NEXT getrennt ist, da in einem Vorwärtscursor nur SQL_FETCH_NEXT unterstützt wird.)  
  
 SQL_CA1_BOOKMARK = Ein *FetchOrientation-Argument* von SQL_FETCH_BOOKMARK wird in einem Aufruf von **SQLFetchScroll** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_LOCK_EXCLUSIVE = Ein *LockType-Argument* von SQL_LOCK_EXCLUSIVE wird in einem Aufruf von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_LOCK_NO_CHANGE = Ein *LockType-Argument* von SQL_LOCK_NO_CHANGE wird in einem Aufruf von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_LOCK_UNLOCK = Ein *LockType-Argument* von SQL_LOCK_UNLOCK wird in einem Aufruf von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POS_POSITION = Ein *Operation-Argument* von SQL_POSITION wird in einem Aufruf von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POS_UPDATE = Ein *Operation-Argument* von SQL_UPDATE wird in einem Aufruf von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POS_DELETE = Ein *Operation-Argument* von SQL_DELETE wird in einem Aufruf von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POS_REFRESH = Ein *Operation-Argument* von SQL_REFRESH wird in einem Aufruf von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POSITIONED_UPDATE = Eine UPDATE WHERE CURRENT OF SQL-Anweisung wird unterstützt, wenn der Cursor ein dynamischer Cursor ist. (Ein SQL-92 Entry-Level-konformer Treiber gibt diese Option immer als unterstützt zurück.)  
  
 SQL_CA1_POSITIONED_DELETE = Eine DELETE WHERE CURRENT OF SQL-Anweisung wird unterstützt, wenn der Cursor ein dynamischer Cursor ist. (Ein SQL-92 Entry-Level-konformer Treiber gibt diese Option immer als unterstützt zurück.)  
  
 SQL_CA1_SELECT_FOR_UPDATE = Eine SELECT FOR UPDATE SQL-Anweisung wird unterstützt, wenn der Cursor ein dynamischer Cursor ist. (Ein SQL-92 Entry-Level-konformer Treiber gibt diese Option immer als unterstützt zurück.)  
  
 SQL_CA1_BULK_ADD = Ein *Operation-Argument* von SQL_ADD wird in einem Aufruf von **SQLBulkOperations** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = Ein *Operation-Argument* von SQL_UPDATE_BY_BOOKMARK wird in einem Aufruf von **SQLBulkOperations** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = Ein *Operation-Argument* von SQL_DELETE_BY_BOOKMARK wird in einem Aufruf von **SQLBulkOperations** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = Ein *Operation-Argument* von SQL_FETCH_BY_BOOKMARK wird in einem Aufruf von **SQLBulkOperations** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 Ein SQL-92 Intermediate Level-conformant-Treiber gibt in der Regel die SQL_CA1_NEXT-, SQL_CA1_ABSOLUTE- und SQL_CA1_RELATIVE-Optionen als unterstützt zurück, da er scrollbare Cursor durch die eingebettete SQL FETCH-Anweisung unterstützt. Da dies jedoch nicht direkt die zugrunde liegende SQL-Unterstützung bestimmt, werden scrollbare Cursor möglicherweise nicht unterstützt, selbst für einen SQL-92 Intermediate Level-conformant-Treiber.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines dynamischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die zweite Teilmenge von Attributen. für die erste Teilmenge siehe SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = Ein schreibgeschützter dynamischer Cursor, bei dem keine Aktualisierungen zulässig sind, wird unterstützt. (Das SQL_ATTR_CONCURRENCY Anweisungsattribut kann für einen dynamischen Cursor SQL_CONCUR_READ_ONLY werden).  
  
 SQL_CA2_LOCK_CONCURRENCY = Ein dynamischer Cursor, der die niedrigste Sperrebene verwendet, die ausreicht, um sicherzustellen, dass die Zeile aktualisiert werden kann, wird unterstützt. (Das SQL_ATTR_CONCURRENCY-Anweisungsattribut kann für einen dynamischen Cursor SQL_CONCUR_LOCK werden.) Diese Sperren müssen mit der Vom SQL_ATTR_TXN_ISOLATION-Verbindungsattribut festgelegten Transaktionsisolationsstufe übereinstimmen.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = Ein dynamischer Cursor, der das optimistische Parallelitätssteuerelement zum Vergleich von Zeilenversionen verwendet, wird unterstützt. (Das SQL_ATTR_CONCURRENCY Anweisungsattribut kann für einen dynamischen Cursor SQL_CONCUR_ROWVER werden.)  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = Ein dynamischer Cursor, der das optimistische Parallelitätssteuerelement zum Vergleichen von Werten verwendet, wird unterstützt. (Das Attribut SQL_ATTR_CONCURRENCY Anweisung kann für einen dynamischen Cursor SQL_CONCUR_VALUES werden.)  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = Hinzugefügte Zeilen sind für einen dynamischen Cursor sichtbar. Der Cursor kann zu diesen Zeilen scrollen. (Wo diese Zeilen dem Cursor hinzugefügt werden, ist treiberabhängig.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS = Gelöschte Zeilen sind für einen dynamischen Cursor nicht mehr verfügbar und hinterlassen keine "Bohrung" im Resultset. nachdem der dynamische Cursor aus einer gelöschten Zeile gescrollt hat, kann er nicht zu dieser Zeile zurückkehren.  
  
 SQL_CA2_SENSITIVITY_UPDATES = Aktualisierungen von Zeilen sind für einen dynamischen Cursor sichtbar. Wenn der dynamische Cursor von einer aktualisierten Zeile aus scrollt und zu einer aktualisierten Zeile zurückkehrt, sind die vom Cursor zurückgegebenen Daten die aktualisierten Daten und nicht die ursprünglichen Daten.  
  
 SQL_CA2_MAX_ROWS_SELECT = Das Attribut SQL_ATTR_MAX_ROWS-Anweisung wirkt sich auf **SELECT-Anweisungen** aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_INSERT = Das Attribut SQL_ATTR_MAX_ROWS-Anweisung wirkt sich auf **INSERT-Anweisungen** aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_DELETE = Das Attribut SQL_ATTR_MAX_ROWS-Anweisung wirkt sich auf **DELETE-Anweisungen** aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_UPDATE = Das Attribut SQL_ATTR_MAX_ROWS-Anweisung wirkt sich auf **UPDATE-Anweisungen** aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_CATALOG = Das Attribut **CATALOG** SQL_ATTR_MAX_ROWS-Anweisung wirkt sich auf CATALOG-Ergebnissätze aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = Das Attribut SQL_ATTR_MAX_ROWS-Anweisung wirkt sich auf die Anweisungen **SELECT**, **INSERT**, **DELETE**und **UPDATE** sowie **CATALOG-Resultsets** aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_CRC_EXACT = Die genaue Zeilenanzahl ist im Diagnosefeld SQL_DIAG_CURSOR_ROW_COUNT verfügbar, wenn es sich bei dem Cursor um einen dynamischen Cursor handelt.  
  
 SQL_CA2_CRC_APPROXIMATE = Eine ungefähre Zeilenanzahl ist im SQL_DIAG_CURSOR_ROW_COUNT Diagnosefeld verfügbar, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = Der Treiber garantiert nicht, dass simulierte positionierte Aktualisierungs- oder Löschanweisungen nur eine Zeile beeinflussen, wenn der Cursor ein dynamischer Cursor ist. es liegt in der Verantwortung der Anwendung, dies zu gewährleisten. (Wenn eine Anweisung mehr als eine Zeile betrifft, gibt **SQLExecute** oder **SQLExecDirect** SQLSTATE 01001 [Cursor-Vorgangskonflikt] zurück.) Um dieses Verhalten festzulegen, ruft die Anwendung **SQLSetStmtAttr** auf, wobei das Attribut SQL_ATTR_SIMULATE_CURSOR auf SQL_SC_NON_UNIQUE festgelegt ist.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = Der Treiber versucht sicherzustellen, dass simulierte positionierte Aktualisierungs- oder Löschanweisungen nur eine Zeile beeinflussen, wenn der Cursor ein dynamischer Cursor ist. Der Treiber führt solche Anweisungen immer aus, auch wenn sie mehr als eine Zeile betreffen können, z. B. wenn kein eindeutiger Schlüssel vorhanden ist. (Wenn eine Anweisung mehr als eine Zeile betrifft, gibt **SQLExecute** oder **SQLExecDirect** SQLSTATE 01001 [Cursor-Vorgangskonflikt] zurück.) Um dieses Verhalten festzulegen, ruft die Anwendung **SQLSetStmtAttr** auf, wobei das attribut SQL_ATTR_SIMULATE_CURSOR auf SQL_SC_TRY_UNIQUE festgelegt ist.  
  
 SQL_CA2_SIMULATE_UNIQUE = Der Treiber garantiert, dass simulierte positionierte Aktualisierungs- oder Löschanweisungen nur eine Zeile beeinflussen, wenn der Cursor ein dynamischer Cursor ist. Wenn der Treiber dies für eine bestimmte Anweisung nicht garantieren kann, geben **SQLExecDirect** oder **SQLPrepare** SQLSTATE 01001 (Cursor-Vorgangskonflikt) zurück. Um dieses Verhalten festzulegen, ruft die Anwendung **SQLSetStmtAttr** auf, wobei das Attribut SQL_ATTR_SIMULATE_CURSOR auf SQL_SC_UNIQUE festgelegt ist.  
  
 SQL_EXPRESSIONS_IN_ORDERBY(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle Ausdrücke in der **ORDER BY-Liste** unterstützt; "N", wenn dies nicht der Fall ist.  
  
 SQL_FILE_USAGE(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der angibt, wie ein einstufiger Treiber Dateien in einer Datenquelle direkt behandelt:  
  
 SQL_FILE_NOT_SUPPORTED = Der Treiber ist kein einstufiger Treiber. Ein ORACLE-Treiber ist z. B. ein zweistufiger Treiber.  
  
 SQL_FILE_TABLE = Ein einstufiger Treiber behandelt Dateien in einer Datenquelle als Tabellen. Ein Xbase-Treiber behandelt z. B. jede Xbase-Datei als Tabelle.  
  
 SQL_FILE_CATALOG = Ein einstufiger Treiber behandelt Dateien in einer Datenquelle als Katalog. Ein Microsoft Access-Treiber behandelt z. B. jede Microsoft Access-Datei als vollständige Datenbank.  
  
 Eine Anwendung kann dies verwenden, um zu bestimmen, wie Benutzer Daten auswählen. Beispielsweise betrachten Xbase-Benutzer Daten häufig als in Dateien gespeichert, während ORACLE- und Microsoft Access-Benutzer Daten im Allgemeinen als in Tabellen gespeichert betrachten.  
  
 Wenn ein Benutzer eine Xbase-Datenquelle auswählt, kann die Anwendung das allgemeine Dialogfeld Windows **File Open** anzeigen. Wenn der Benutzer eine Microsoft Access- oder ORACLE-Datenquelle auswählt, kann die Anwendung ein benutzerdefiniertes Dialogfeld Tabelle **auswählen** anzeigen.  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines Vorwärtscursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die erste Teilmenge von Attributen. für die zweite Teilmenge siehe SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und ersetzen Sie den "Forward-only-Cursor" durch "dynamischen Cursor" in den Beschreibungen).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines Vorwärtscursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die zweite Teilmenge von Attributen. für die erste Teilmenge siehe SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (und ersetzen Sie "Forward-only-Cursor" durch "dynamic cursor" in den Beschreibungen).  
  
 SQL_GETDATA_EXTENSIONS(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die Erweiterungen für **SQLGetData**aufgibt.  
  
 Die folgenden Bitmasken werden zusammen mit dem Flag verwendet, um zu bestimmen, welche allgemeinen Erweiterungen der Treiber für **SQLGetData**unterstützt:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData** kann für jede ungebundene Spalte aufgerufen werden, einschließlich der Spalten vor der letzten gebundenen Spalte. Beachten Sie, dass die Spalten in der Reihenfolge der aufsteigenden Spaltennummer aufgerufen werden müssen, es sei denn, SQL_GD_ANY_ORDER wird ebenfalls zurückgegeben.  
  
 SQL_GD_ANY_ORDER = **SQLGetData** kann für ungebundene Spalten in beliebiger Reihenfolge aufgerufen werden. Beachten Sie, dass **SQLGetData** nur für Spalten nach der letzten gebundenen Spalte aufgerufen werden kann, es sei denn, SQL_GD_ANY_COLUMN wird ebenfalls zurückgegeben.  
  
 SQL_GD_BLOCK = **SQLGetData** kann für eine ungebundene Spalte in einer beliebigen Zeile in einem Block (wobei die Rowsetgröße größer als 1) der Daten aufgerufen werden, nachdem sie mit **SQLSetPos**in diese Zeile positioniert wurden.  
  
 SQL_GD_BOUND = **SQLGetData** kann zusätzlich zu ungebundenen Spalten für gebundene Spalten aufgerufen werden. Ein Treiber kann diesen Wert nur zurückgeben, wenn er auch SQL_GD_ANY_COLUMN zurückgibt.  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData** kann aufgerufen werden, um Ausgabeparameterwerte zurückzugeben. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** ist erforderlich, um Daten nur aus ungebundenen Spalten zurückzugeben, die nach der letzten gebundenen Spalte auftreten, in der Reihenfolge der steigenden Spaltennummer aufgerufen werden und sich nicht in einer Zeile in einem Zeilenblock befinden.  
  
 Wenn ein Treiber Lesezeichen unterstützt (entweder feste oder variable Länge), muss er den Aufruf von **SQLGetData** in Spalte 0 unterstützen. Diese Unterstützung ist unabhängig davon erforderlich, was der Treiber für einen Aufruf von **SQLGetInfo** mit dem SQL_GETDATA_EXTENSIONS *InfoType*zurückgibt.  
  
 SQL_GROUP_BY(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die Beziehung zwischen den Spalten in der **GROUP BY-Klausel** und den nicht aggregierten Spalten in der Auswahlliste angibt:  
  
 SQL_GB_COLLATE = Eine **COLLATE-Klausel** kann am Ende jeder Gruppierungsspalte angegeben werden. (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED = **GROUP BY-Klauseln** werden nicht unterstützt. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = Die **GROUP BY-Klausel** muss alle nicht aggregierten Spalten in der Auswahlliste enthalten. Es kann keine anderen Spalten enthalten. Zum Beispiel **SELECT DEPT, MAX(SALARY) VON EMPLOYEE GROUP VON DEPT**. (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = Die **GROUP BY-Klausel** muss alle nicht aggregierten Spalten in der Auswahlliste enthalten. Sie kann Spalten enthalten, die nicht in der Auswahlliste enthalten sind. Beispiel: **SELECT DEPT, MAX(SALARY) FROM EMPLOYEE GROUP BY DEPT, AGE**. (ODBC 2.0)  
  
 SQL_GB_NO_RELATION = Die Spalten in der **GROUP BY-Klausel** und der Auswahlliste sind nicht verknüpft. Die Bedeutung nicht gruppierter, nicht aggregierter Spalten in der Auswahlliste ist datenquellenabhängig. Beispiel: **SELECT DEPT, SALARY FROM EMPLOYEE GROUP BY DEPT, AGE**. (ODBC 2.0)  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer die SQL_GB_GROUP_BY_EQUALS_SELECT Option als unterstützt zurück. Ein SQL-92 Full level-conformant-Treiber gibt immer die SQL_GB_COLLATE Option als unterstützt zurück. Wenn keine der Optionen unterstützt wird, wird die **GROUP BY-Klausel** von der Datenquelle nicht unterstützt.  
  
 SQL_IDENTIFIER_CASE(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert wie folgt:  
  
 SQL_IC_UPPER = Bezeichner in SQL werden nicht mit großsteinen Groß-/Kleinschreibungen im Systemkatalog gespeichert.  
  
 SQL_IC_LOWER = Bezeichner in SQL werden nicht mit großschreibungsabhängiger Groß- und Kleinschreibung im Systemkatalog gespeichert.  
  
 SQL_IC_SENSITIVE = Bezeichner in SQL werden die Groß-/Kleinschreibung beachtet und in gemischter Groß-/Kleinschreibung im Systemkatalog gespeichert.  
  
 SQL_IC_MIXED = Bezeichner in SQL werden nicht mit großschreibungsabhängiger Groß- und Kleinschreibung angezeigt und in gemischter Groß-/Kleinschreibung im Systemkatalog gespeichert.  
  
 Da bei Bezeichnern in SQL-92 nie die Groß-/Kleinschreibung beachtet wird, gibt ein Treiber, der sql-92 (jede Ebene) strikt entspricht, niemals die SQL_IC_SENSITIVE Option als unterstützt zurück.  
  
 SQL_IDENTIFIER_QUOTE_CHAR(ODBC 1.0)  
 Die Zeichenfolge, die als Anfangs- und Endtrennzeichen eines zitierten (getrennten) Bezeichners in SQL-Anweisungen verwendet wird. (Bezeichner, die als Argumente an ODBC-Funktionen übergeben werden, müssen nicht zitiert werden.) Wenn die Datenquelle keine in Anführungszeichen gesetzten Bezeichner unterstützt, wird ein Leerzeichen zurückgegeben.  
  
 Diese Zeichenfolge kann auch zum Anzitieren von Katalogfunktionsargumenten verwendet werden, wenn das Verbindungsattribut SQL_ATTR_METADATA_ID auf SQL_TRUE festgelegt ist.  
  
 Da das Bezeichneranführungszeichen in SQL-92 das doppelte Anführungszeichen (" ist", gibt ein Treiber, der sql-92 strikt entspricht, immer das doppelte Anführungszeichen zurück.  
  
 SQL_INDEX_KEYWORDS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die Schlüsselwörter in der CREATE INDEX-Anweisung aufzählt, die vom Treiber unterstützt werden:  
  
 SQL_IK_NONE = Keines der Schlüsselwörter wird unterstützt.  
  
 SQL_IK_ASC = ASC-Schlüsselwort wird unterstützt.  
  
 SQL_IK_DESC = DESC-Schlüsselwort wird unterstützt.  
  
 SQL_IK_ALL = Alle Schlüsselwörter werden unterstützt.  
  
 Um festzustellen, ob die CREATE INDEX-Anweisung unterstützt wird, ruft eine Anwendung **SQLGetInfo** mit dem SQL_DLL_INDEX-Informationstyp auf.  
  
 SQL_INFO_SCHEMA_VIEWS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Ansichten in den INFORMATION_SCHEMA aufgibt, die vom Treiber unterstützt werden. Die Ansichten in und der Inhalt von INFORMATION_SCHEMA sind wie in SQL-92 definiert.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Ansichten unterstützt werden:  
  
 SQL_ISV_ASSERTIONS = Identifiziert die Assertionen des Katalogs, die einem bestimmten Benutzer gehören. (Vollständige Ebene)  
  
 SQL_ISV_CHARACTER_SETS = Identifiziert die Zeichensätze des Katalogs, auf die ein benutzergegebener Benutzer zugreifen kann. (Zwischenstufe)  
  
 SQL_ISV_CHECK_CONSTRAINTS = Identifiziert die CHECK-Einschränkungen, die einem bestimmten Benutzer gehören. (Zwischenstufe)  
  
 SQL_ISV_COLLATIONS = Identifiziert die Zeichensortierungen für den Katalog, auf die ein benutzergegebener Benutzer zugreifen kann. (Vollständige Ebene)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = Identifiziert Spalten für den Katalog, die von im Katalog definierten Domänen abhängen und im Besitz eines bestimmten Benutzers sind. (Zwischenstufe)  
  
 SQL_ISV_COLUMN_PRIVILEGES = Identifiziert die Berechtigungen für Spalten persistenter Tabellen, die einem bestimmten Benutzer zur Verfügung stehen oder von ihm gewährt werden. (FIPS-Übergangsebene)  
  
 SQL_ISV_COLUMNS = Identifiziert die Spalten persistenter Tabellen, auf die ein bestimmter Benutzer zugreifen kann. (FIPS-Übergangsebene)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = Ähnlich wie CONSTRAINT_TABLE_USAGE Ansicht werden Spalten für die verschiedenen Einschränkungen identifiziert, die einem bestimmten Benutzer gehören. (Zwischenstufe)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = Identifiziert die Tabellen, die von Einschränkungen (referenzielle, eindeutige und Assertionen) verwendet werden und im Besitz eines bestimmten Benutzers sind. (Zwischenstufe)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = Identifiziert die Domäneneinschränkungen (der Domänen im Katalog), auf die ein bestimmter Benutzer zugreifen kann. (Zwischenstufe)  
  
 SQL_ISV_DOMAINS = Identifiziert die in einem Katalog definierten Domänen, auf die der Benutzer zugreifen kann. (Zwischenstufe)  
  
 SQL_ISV_KEY_COLUMN_USAGE = Identifiziert im Katalog definierte Spalten, die von einem bestimmten Benutzer als Schlüssel eingeschränkt sind. (Zwischenstufe)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = Identifiziert die referenziellen Einschränkungen, die einem bestimmten Benutzer gehören. (Zwischenstufe)  
  
 SQL_ISV_SCHEMATA = Identifiziert die Schemas, die einem bestimmten Benutzer gehören. (Zwischenstufe)  
  
 SQL_ISV_SQL_LANGUAGES = Identifiziert die SQL-Konformitätsebenen, -optionen und -dialekte, die von der SQL-Implementierung unterstützt werden. (Zwischenstufe)  
  
 SQL_ISV_TABLE_CONSTRAINTS = Identifiziert die Tabelleneinschränkungen, die einem bestimmten Benutzer gehören. (Zwischenstufe)  
  
 SQL_ISV_TABLE_PRIVILEGES = Identifiziert die Berechtigungen für persistente Tabellen, die einem bestimmten Benutzer zur Verfügung stehen oder von ihm gewährt werden. (FIPS-Übergangsebene)  
  
 SQL_ISV_TABLES = Identifiziert die persistenten Tabellen, die in einem Katalog definiert sind und auf die ein benutzergegebener Benutzer zugreifen kann. (FIPS-Übergangsebene)  
  
 SQL_ISV_TRANSLATIONS = Identifiziert Zeichenübersetzungen für den Katalog, auf die ein benutzergegebener Benutzer zugreifen kann. (Vollständige Ebene)  
  
 SQL_ISV_USAGE_PRIVILEGES = Identifiziert die USAGE-Berechtigungen für Katalogobjekte, die einem bestimmten Benutzer zur Verfügung stehen oder sich im Besitz eines bestimmten Benutzers befinden. (FIPS-Übergangsebene)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = Identifiziert die Spalten, von denen die Ansichten des Katalogs abhängig sind, die einem bestimmten Benutzer gehören. (Zwischenstufe)  
  
 SQL_ISV_VIEW_TABLE_USAGE = Identifiziert die Tabellen, von denen die Ansichten des Katalogs abhängig sind, die einem bestimmten Benutzer gehören. (Zwischenstufe)  
  
 SQL_ISV_VIEWS = Identifiziert die in diesem Katalog definierten angezeigten Tabellen, auf die ein benutzergegebener Benutzer zugreifen kann. (FIPS-Übergangsebene)  
  
 SQL_INSERT_STATEMENT(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die unterstützungsmittelweisen **INSERT-Anweisungen** angibt:  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer alle diese Optionen als unterstützt zurück.  
  
 SQL_INTEGRITY(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle die Integritätsverbesserungsfunktion unterstützt; "N", wenn dies nicht der Fall ist.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_ODBC_SQL_OPT_IEF* für ODBC 3.0 umbenannt.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines Keyset-Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die erste Teilmenge von Attributen. für die zweite Teilmenge siehe SQL_KEYSET_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und ersetzen Sie "keyset-gesteuerter Cursor" durch "dynamischen Cursor" in den Beschreibungen).  
  
 Ein SQL-92 Intermediate Level-conformant-Treiber gibt in der Regel die SQL_CA1_NEXT-, SQL_CA1_ABSOLUTE- und SQL_CA1_RELATIVE-Optionen als unterstützt zurück, da der Treiber scrollbare Cursor durch die eingebettete SQL FETCH-Anweisung unterstützt. Da dies jedoch nicht direkt die zugrunde liegende SQL-Unterstützung bestimmt, werden scrollbare Cursor möglicherweise nicht unterstützt, selbst für einen SQL-92 Intermediate Level-conformant-Treiber.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines Keyset-Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die zweite Teilmenge von Attributen. für die erste Teilmenge siehe SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und ersetzen Sie "keyset-gesteuerter Cursor" durch "dynamischen Cursor" in den Beschreibungen).  
  
 SQL_KEYWORDS(ODBC 2.0)  
 Eine Zeichenfolge, die eine durch Kommas getrennte Liste aller datenquellenspezifischen Schlüsselwörter enthält. Diese Liste enthält keine ODBC-spezifischen Schlüsselwörter oder Schlüsselwörter, die sowohl von der Datenquelle als auch von ODBC verwendet werden. Diese Liste stellt alle reservierten Schlüsselwörter dar. interoperable Anwendungen sollten diese Wörter nicht in Objektnamen verwenden.  
  
 Eine Liste der ODBC-Schlüsselwörter finden Sie unter [Reservierte Schlüsselwörter](../../../odbc/reference/appendixes/reserved-keywords.md) in [Anhang C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Der **#define-Wert** SQL_ODBC_KEYWORDS enthält eine durch Kommas getrennte Liste von ODBC-Schlüsselwörtern.  
  
 Anhang C: SQL-Grammatik  
  
 SQL_LIKE_ESCAPE_CLAUSE(ODBC 2.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle ein Escapezeichen für das Prozentzeichen unterstützt (%) und unterstrichen Zeichen (_) in einem LIKE-Prädikat und der Treiber unterstützt die ODBC-Syntax zum Definieren eines **LIKE** **LIKE-Prädikat-Escapezeichens;** "N" sonst.  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS(ODBC 3.0)  
 Ein SQLUINTEGER-Wert, der die maximale Anzahl aktiver gleichzeitiger Anweisungen im asynchronen Modus angibt, die der Treiber für eine bestimmte Verbindung unterstützen kann. Wenn es keinen bestimmten Grenzwert gibt oder der Grenzwert unbekannt ist, ist dieser Wert Null.  
  
 SQL_MAX_BINARY_LITERAL_LEN(ODBC 2.0)  
 Ein SQLUINTEGER-Wert, der die maximale Länge (Anzahl der hexadezimalen Zeichen, ohne das literale Präfix und suffix, das von **SQLGetTypeInfo**zurückgegeben wird) eines binären Literals in einer SQL-Anweisung angibt. Das binäre Literal 0xFFAA hat beispielsweise eine Länge von 4. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 SQL_MAX_CATALOG_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge eines Katalognamens in der Datenquelle angibt. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Full Level-conformant Treiber gibt mindestens 128 zurück.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_MAX_QUALIFIER_NAME_LEN* für ODBC 3.0 umbenannt.  
  
 SQL_MAX_CHAR_LITERAL_LEN(ODBC 2.0)  
 Ein SQLUINTEGER-Wert, der die maximale Länge (Anzahl der Zeichen, ohne das literale Präfix und suffix, das von **SQLGetTypeInfo**zurückgegeben wird) eines Zeichenliterals in einer SQL-Anweisung angibt. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 SQL_MAX_COLUMN_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge eines Spaltennamens in der Datenquelle angibt. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 18 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 128 zurück.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl von Spalten angibt, die in einer **GROUP BY-Klausel** zulässig sind. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 6 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 15 zurück.  
  
 SQL_MAX_COLUMNS_IN_INDEX(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl von Spalten angibt, die in einem Index zulässig sind. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl von Spalten angibt, die in einer **ORDER BY-Klausel** zulässig sind. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 6 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 15 zurück.  
  
 SQL_MAX_COLUMNS_IN_SELECT(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximal zulässige Anzahl von Spalten in einer Auswahlliste angibt. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 100 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 250 zurück.  
  
 SQL_MAX_COLUMNS_IN_TABLE(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximal zulässige Anzahl von Spalten in einer Tabelle angibt. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 100 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 250 zurück.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl aktiver Anweisungen angibt, die der Treiber für eine Verbindung unterstützen kann. Eine Anweisung wird als aktiv definiert, wenn Ergebnisse ausstehen, wobei der Begriff "Ergebnisse" Zeilen aus einem **SELECT-Vorgang** oder Zeilen bedeutet, die von einem **INSERT-,** **UPDATE-** oder **DELETE-Vorgang** betroffen sind (z. B. eine Zeilenanzahl), oder wenn sie sich in einem NEED_DATA-Status befindet. Dieser Wert kann eine Einschränkung widerspiegeln, die entweder vom Treiber oder von der Datenquelle auferlegt wird. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_ACTIVE_STATEMENTS* für ODBC 3.0 umbenannt.  
  
 SQL_MAX_CURSOR_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge eines Cursornamens in der Datenquelle angibt. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 18 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 128 zurück.  
  
 SQL_MAX_DRIVER_CONNECTIONS(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl aktiver Verbindungen angibt, die der Treiber für eine Umgebung unterstützen kann. Dieser Wert kann eine Einschränkung widerspiegeln, die entweder vom Treiber oder von der Datenquelle auferlegt wird. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_ACTIVE_CONNECTIONS* für ODBC 3.0 umbenannt.  
  
 SQL_MAX_IDENTIFIER_LEN(ODBC 3.0)  
 Ein SQLUSMALLINT, das die maximale Größe in Zeichen angibt, die die Datenquelle für benutzerdefinierte Namen unterstützt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 18 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 128 zurück.  
  
 SQL_MAX_INDEX_SIZE(ODBC 2.0)  
 Ein SQLUINTEGER-Wert, der die maximale Anzahl von Bytes angibt, die in den kombinierten Feldern eines Indexzulässigen zulässig sind. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 SQL_MAX_PROCEDURE_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge eines Prozedurnamens in der Datenquelle angibt. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 SQL_MAX_ROW_SIZE(ODBC 2.0)  
 Ein SQLUINTEGER-Wert, der die maximale Länge einer einzelnen Zeile in einer Tabelle angibt. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry-Level-konformer Treiber gibt mindestens 2.000 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 8.000 zurück.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG(ODBC 3.0)  
 Eine Zeichenfolge: "Y", wenn die maximale Zeilengröße, die für den SQL_MAX_ROW_SIZE-Informationstyp zurückgegeben wird, die Länge aller SQL_LONGVARCHAR und SQL_LONGVARBINARY Spalten in der Zeile enthält. "N" sonst.  
  
 SQL_MAX_SCHEMA_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge eines Schemanamens in der Datenquelle angibt. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 18 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 128 zurück.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_MAX_OWNER_NAME_LEN* für ODBC 3.0 umbenannt.  
  
 SQL_MAX_STATEMENT_LEN(ODBC 2.0)  
 Ein SQLUINTEGER-Wert, der die maximale Länge (Anzahl der Zeichen, einschließlich Leerzeichen) einer SQL-Anweisung angibt. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 SQL_MAX_TABLE_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge eines Tabellennamens in der Datenquelle angibt. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 18 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 128 zurück.  
  
 SQL_MAX_TABLES_IN_SELECT(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl von Tabellen angibt, die in der **FROM-Klausel** einer **SELECT-Anweisung** zulässig sind. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 Ein FIPS Entry Level-konformer Treiber gibt mindestens 15 zurück. Ein FIPS Intermediate Level-conformant Treiber gibt mindestens 50 zurück.  
  
 SQL_MAX_USER_NAME_LEN(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge eines Benutzernamens in der Datenquelle angibt. Wenn keine maximale Länge vorhanden ist oder die Länge unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 SQL_MULT_RESULT_SETS(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle mehrere Resultsets unterstützt, "N", wenn dies nicht der Fall ist.  
  
 Weitere Informationen zu mehreren Resultsets finden Sie unter [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn der Treiber mehr als eine aktive Transaktion gleichzeitig unterstützt, "N", wenn nur eine Transaktion jederzeit aktiv sein kann.  
  
 Die für diesen Informationstyp zurückgegebenen Informationen gelten nicht für verteilte Transaktionen.  
  
 SQL_NEED_LONG_DATA_LEN(ODBC 2.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle die Länge eines langen Datenwerts benötigt (der Datentyp ist SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer datenquellenspezifischer Datentyp), bevor dieser Wert an die Datenquelle gesendet wird, "N", wenn dies nicht der Fall ist. Weitere Informationen finden Sie unter [SQLBindParameter Function](../../../odbc/reference/syntax/sqlbindparameter-function.md) und [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der angibt, ob die Datenquelle NOT NULL in Spalten unterstützt:  
  
 SQL_NNC_NULL = Alle Spalten müssen nullsein.  
  
 SQL_NNC_NON_NULL = Spalten können nicht null. (Die Datenquelle unterstützt die **NOT NULL-Spalteneinschränkung** in CREATE TABLE-Anweisungen.) **CREATE TABLE**  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt SQL_NNC_NON_NULL zurück.  
  
 SQL_NULL_COLLATION(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der angibt, wo NULLs in einer Ergebnismenge sortiert werden:  
  
 SQL_NC_END = NULLs werden am Ende des Resultsets sortiert, unabhängig von den SCHLÜSSELwörtern ASC oder DESC.  
  
 SQL_NC_HIGH = NULLs werden am ende des Resultsets sortiert, abhängig von den SCHLÜSSELwörtern ASC oder DESC.  
  
 SQL_NC_LOW = NULLs werden am unteren Ende des Resultsets sortiert, abhängig von den SCHLÜSSELwörtern ASC oder DESC.  
  
 SQL_NC_START = NULLs werden am Anfang des Resultsets sortiert, unabhängig von den SCHLÜSSELwörtern ASC oder DESC.  
  
 SQL_NUMERIC_FUNCTIONS(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC 1.0 eingeführt; jede Bitmaske wird mit der Version beschriftet, in der sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske, die die skalaren numerischen Funktionen aufgibt, die vom Treiber und der zugehörigen Datenquelle unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche numerischen Funktionen unterstützt werden:  
  
 SQL_FN_NUM_ABS (ODBC 1.0)SQL_FN_NUM_ACOS (ODBC 1.0)SQL_FN_NUM_ASIN (ODBC 1.0)SQL_FN_NUM_ATAN (ODBC 1.0)SQL_FN_NUM_ATAN2 (ODBC 1.0)SQL_FN_NUM_CEILING (ODBC 1.0)SQL_FN_NUM_COS (ODBC 1.0)SQL_FN_NUM_COT (ODBC 1.0)SQL_FN_NUM_DEGREES (ODBC 2.0)SQL_FN_NUM_EXP (ODBC 1.0)SQL_FN_NUM_FLOOR (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 2.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_ (ODBC 2.0)SQL_FN_ (ODBC 2 NUM_MOD (ODBC 1.0)SQL_FN_NUM_PI (ODBC 1.0)SQL_FN_NUM_POWER (ODBC 2.0)SQL_FN_NUM_RADIANS (ODBC 2.0)SQL_FN_NUM_RAND (ODBC 1.0)SQL_FN_NUM_ROUND (ODBC 2.0)SQL_FN_NUM_SIGN (ODBC 1.0)SQL_FN_NUM_SIN (ODBC 1.0)SQL_FN_NUM_SQRT (ODBC 1.0)SQL_FN_NUM_TAN (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 1.0)SQL_FN_NUM_TRUNCATE (  
  
 SQL_ODBC_INTERFACE_CONFORMANCE(ODBC 3.0)  
 Ein SQLUINTEGER-Wert, der die Ebene der ODBC 3 *.x-Schnittstelle* angibt, die der Treiber erfüllt.  
  
 SQL_OIC_CORE: Der Mindestwert, den alle ODBC-Treiber erfüllen sollen. Diese Ebene umfasst grundlegende Schnittstellenelemente wie Verbindungsfunktionen, Funktionen zum Vorbereiten und Ausführen einer SQL-Anweisung, grundlegende Metadatenfunktionen für Ergebnissatz, grundlegende Katalogfunktionen usw.  
  
 SQL_OIC_LEVEL1: Eine Ebene, die die Funktionalität der Standard-Compliance-Ebene sowie scrollbare Cursor, Lesezeichen, positionierte Aktualisierungen und Löschungen usw. einschließt.  
  
 SQL_OIC_LEVEL2: Eine Ebene mit Funktionen der Standards der Stufe 1 sowie erweiterte Funktionen wie empfindliche Cursor; Aktualisieren, Löschen und Aktualisieren nach Lesezeichen; Unterstützung gespeicherter Prozeduren; Katalogfunktionen für Primär- und Fremdschlüssel; Multi-Katalog-Unterstützung; Und so weiter.  
  
 Weitere Informationen finden Sie unter [Schnittstellenkonformitätsstufen](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 SQL_ODBC_VER(ODBC 1.0)  
 Eine Zeichenfolge mit der ODBC-Version, der der Treiber-Manager entspricht. Die Version ist von der Form ..0000, wobei die ersten beiden Ziffern die Hauptversion und die nächsten beiden Ziffern die Nebenversion sind. Dies wird nur im Treiber-Manager implementiert.  
  
 SQL_OJ_CAPABILITIES(ODBC 2.01)  
 Eine SQLUINTEGER-Bitmaske, die die Typen von äußeren Verknüpfungen aufgibt, die vom Treiber und der Datenquelle unterstützt werden. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Typen unterstützt werden:  
  
 SQL_OJ_LEFT = Linke äußere Verknüpfungen werden unterstützt.  
  
 SQL_OJ_RIGHT = Rechte äußere Verknüpfungen werden unterstützt.  
  
 SQL_OJ_FULL = Vollständige äußere Verknüpfungen werden unterstützt.  
  
 SQL_OJ_NESTED = Verschachtelte äußere Verknüpfungen werden unterstützt.  
  
 SQL_OJ_NOT_ORDERED = Die Spaltennamen in der ON-Klausel der äußeren Verknüpfung müssen nicht in der gleichen Reihenfolge wie ihre jeweiligen Tabellennamen in der **OUTER JOIN-Klausel** sein.  
  
 SQL_OJ_INNER = Die innere Tabelle (die rechte Tabelle in einer linken äußeren Verknüpfung oder die linke Tabelle in einer rechten äußeren Verknüpfung) kann auch in einer inneren Verknüpfung verwendet werden. Dies gilt nicht für vollständige äußere Verknüpfungen, die keine innere Tabelle haben.  
  
 SQL_OJ_ALL_COMPARISON_OPS = Der Vergleichsoperator in der ON-Klausel kann einer der ODBC-Vergleichsoperatoren sein. Wenn dieses Bit nicht gesetzt ist, kann nur der Vergleichsoperator "Equals" (=) in äußeren Verknüpfungen verwendet werden.  
  
 Wenn keine dieser Optionen als unterstützt zurückgegeben wird, wird keine äußere Join-Klausel unterstützt.  
  
 Informationen zur Unterstützung relationaler Join-Operatoren in einer SELECT-Anweisung gemäß SQL-92 finden Sie unter SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT(ODBC 2.0)  
 Eine Zeichenfolge: "Y", wenn die Spalten in der **ORDER BY-Klausel** in der Auswahlliste enthalten sein müssen; andernfalls "N".  
  
 SQL_PARAM_ARRAY_ROW_COUNTS(ODBC 3.0)  
 Ein SQLUINTEGER, das die Eigenschaften des Treibers in Bezug auf die Verfügbarkeit von Zeilenanzahlen in einer parametrisierten Ausführung aufzählt. Hat die folgenden Werte:  
  
 SQL_PARC_BATCH = Für jeden Parametersatz stehen einzelne Zeilenanzahlen zur Verfügung. Dies entspricht konzeptionell dem Treiber, der einen Batch von SQL-Anweisungen generiert, eine für jeden Parameter, der im Array festgelegt ist. Erweiterte Fehlerinformationen können mithilfe des SQL_PARAM_STATUS_PTR-Deskriptorfelds abgerufen werden.  
  
 SQL_PARC_NO_BATCH = Es ist nur eine Zeilenanzahl verfügbar, d. h. die kumulative Zeilenanzahl, die sich aus der Ausführung der Anweisung für das gesamte Array von Parametern ergibt. Dies entspricht konzeptionell der Behandlung der Anweisung zusammen mit dem vollständigen Parameterarray als eine atomare Einheit. Fehler werden genauso behandelt, als ob eine Anweisung ausgeführt würde.  
  
 SQL_PARAM_ARRAY_SELECTS(ODBC 3.0)  
 Ein SQLUINTEGER, das die Eigenschaften des Treibers in Bezug auf die Verfügbarkeit von Resultsets in einer parametrisierten Ausführung aufzählung. Hat die folgenden Werte:  
  
 SQL_PAS_BATCH = Pro Parametersatz steht ein Resultset zur Verfügung. Dies entspricht konzeptionell dem Treiber, der einen Batch von SQL-Anweisungen generiert, eine für jeden Parameter, der im Array festgelegt ist.  
  
 SQL_PAS_NO_BATCH = Es ist nur ein Resultset verfügbar, das das kumulative Resultset darstellt, das sich aus der Ausführung der Anweisung für das gesamte Array von Parametern ergibt. Dies entspricht konzeptionell der Behandlung der Anweisung zusammen mit dem vollständigen Parameterarray als eine atomare Einheit.  
  
 SQL_PAS_NO_SELECT = Ein Treiber lässt nicht zu, dass eine ergebnisabhängige Generierungsanweisung mit einem Array von Parametern ausgeführt wird.  
  
 SQL_PROCEDURE_TERM(ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen des Datenquellenanbieters für eine Prozedur; z. B. "Datenbankprozedur", "gespeicherte Prozedur", "Prozedur", "Paket" oder "gespeicherte Abfrage".  
  
 SQL_PROCEDURES(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle Prozeduren unterstützt und der Treiber die ODBC-Prozeduraufrufsyntax unterstützt. "N" sonst.  
  
 SQL_POS_OPERATIONS(ODBC 2.0)  
 Eine SQLINTEGER-Bitmaske, die die Supportvorgänge in **SQLSetPos**aufgibt.  
  
 Die folgenden Bitmasken werden zusammen mit dem Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden.  
  
 SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert wie folgt:  
  
 SQL_IC_UPPER = In Anführungszeichen in SQL werden keine Groß-/Kleinschreibung berücksichtigt und in Großbuchstaben im Systemkatalog gespeichert.  
  
 SQL_IC_LOWER = In Anführungszeichen in SQL werden keine Groß-/Kleinschreibung berücksichtigt und in Kleinbuchstaben im Systemkatalog gespeichert.  
  
 SQL_IC_SENSITIVE = In Anführungszeichen in SQL werden die Groß-/Kleinschreibung beachtet und in gemischter Groß-/Kleinschreibung im Systemkatalog gespeichert. (In einer SQL-92-kompatiblen Datenbank wird bei in Anführungszeichen angegebenen Bezeichnern immer die Groß-/Kleinschreibung beachtet.)  
  
 SQL_IC_MIXED = In Anführungszeichen in SQL werden keine Groß-/Kleinschreibung berücksichtigt und in gemischter Groß-/Kleinschreibung im Systemkatalog gespeichert.  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer SQL_IC_SENSITIVE zurück.  
  
 SQL_ROW_UPDATES(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn ein keyset-gesteuerter oder gemischter Cursor Zeilenversionen oder Werte für alle abgerufenen Zeilen beibehält und daher alle Aktualisierungen erkennen kann, die von einem Benutzer an einer Zeile vorgenommen wurden, seit die Zeile zuletzt abgerufen wurde. (Dies gilt nur für Aktualisierungen, nicht für Löschungen oder Einfügungen.) Der Treiber kann das SQL_ROW_UPDATED-Flag an das Zeilenstatusarray zurückgeben, wenn **SQLFetchScroll** aufgerufen wird. Andernfalls "N".  
  
 SQL_SCHEMA_TERM(ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen des Datenquellenanbieters für ein Schema; z. B. "Owner", "Authorization ID" oder "Schema".  
  
 Die Zeichenfolge kann in Groß-, Klein- oder Mischfällen zurückgegeben werden.  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer "Schema" zurück.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_OWNER_TERM* für ODBC 3.0 umbenannt.  
  
 SQL_SCHEMA_USAGE(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Anweisungen aufgibt, in denen Schemas verwendet werden können:  
  
 SQL_SU_DML_STATEMENTS = Schemas werden in allen Anweisungen zur Datenmanipulationssprache unterstützt: **SELECT**, **INSERT**, **UPDATE**, **DELETE**, und wenn unterstützt, SELECT **FOR UPDATE** und positionierte Update- und Löschanweisungen.  
  
 SQL_SU_PROCEDURE_INVOCATION = Schemas werden in der Aufrufanweisung der ODBC-Prozedur unterstützt.  
  
 SQL_SU_TABLE_DEFINITION = Schemas werden in allen Tabellendefinitionsanweisungen unterstützt: **CREATE TABLE**, **CREATE VIEW**, ALTER **TABLE**, **DROP TABLE**und DROP **VIEW**.  
  
 SQL_SU_INDEX_DEFINITION = Schemas werden in allen Indexdefinitionsanweisungen unterstützt: **CREATE INDEX** und **DROP INDEX**.  
  
 SQL_SU_PRIVILEGE_DEFINITION = Schemas werden in allen Berechtigungsdefinitionsanweisungen unterstützt: **GRANT** und **REVOKE**.  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer die SQL_SU_DML_STATEMENTS-, SQL_SU_TABLE_DEFINITION- und SQL_SU_PRIVILEGE_DEFINITION-Optionen zurück, wie unterstützt.  
  
 Dieser *InfoType* wurde von der ODBC 2.0 *InfoType-SQL_OWNER_USAGE* für ODBC 3.0 umbenannt.  
  
 SQL_SCROLL_OPTIONS(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC 1.0 eingeführt; jede Bitmaske wird mit der Version beschriftet, in der sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske, die die Für scrollbare Cursor unterstützten Bildlaufoptionen aufgibt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen unterstützt werden:  
  
 SQL_SO_FORWARD_ONLY = Der Cursor scrollt nur vorwärts. (ODBC 1.0)  
  
 SQL_SO_STATIC = Die Daten im Resultset sind statisch. (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN = Der Treiber speichert und verwendet die Tasten für jede Zeile im Resultset. (ODBC 1.0)  
  
 SQL_SO_DYNAMIC = Der Treiber behält die Schlüssel für jede Zeile im Rowset bei (die Größe des Keysets entspricht der Größe des Rowsets). (ODBC 1.0)  
  
 SQL_SO_MIXED = Der Treiber behält die Schlüssel für jede Zeile im Keyset bei, und die Größe des Keysets ist größer als die Rowsetgröße. Der Cursor ist keyset-gesteuert innerhalb des Keysets und dynamisch außerhalb des Keysets. (ODBC 1.0)  
  
 Informationen zu scrollbaren Cursorn finden Sie unter [Scrollbare Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE(ODBC 1.0)  
 Eine Zeichenfolge, die angibt, was der Treiber als Escapezeichen unterstützt, das die Verwendung der Musterübereinstimmungsmetazeichen unter-Wert (_) und Prozentzeichen (%) ermöglicht. als gültige Zeichen in Suchmustern. Dieses Escapezeichen gilt nur für die Katalogfunktionsargumente, die Suchzeichenfolgen unterstützen. Wenn diese Zeichenfolge leer ist, unterstützt der Treiber kein Escapezeichen für Suchmuster.  
  
 Da dieser Informationstyp keine allgemeine Unterstützung des **LIKE** Escapezeichens im LIKE-Prädikat angibt, enthält SQL-92 keine Anforderungen für diese Zeichenfolge.  
  
 Dieser *InfoType* ist auf Katalogfunktionen beschränkt. Eine Beschreibung der Verwendung des Escapezeichens in Suchmusterzeichenfolgen finden Sie unter [Pattern Value Arguments](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER_NAME(ODBC 1.0)  
 Eine Zeichenfolge mit dem tatsächlichen datenquellenspezifischen Servernamen; nützlich, wenn ein Datenquellenname während **SQLConnect**, **SQLDriverConnect**und **SQLBrowseConnect**verwendet wird.  
  
 SQL_SPECIAL_CHARACTERS(ODBC 2.0)  
 Eine Zeichenfolge, die alle Sonderzeichen (d. h. alle Zeichen außer z, A bis Z, 0 bis 9 und Unterstrich) enthält, die in einem Bezeichnernamen, z. B. einem Tabellennamen, Spaltennamen oder Indexnamen, in der Datenquelle verwendet werden können. Zum Beispiel , " . Wenn ein Bezeichner eines oder mehrerer dieser Zeichen enthält, muss es sich bei dem Bezeichner um einen beschriftete Bezeichner handelt.  
  
 SQL_SQL_CONFORMANCE(ODBC 3.0)  
 Ein SQLUINTEGER-Wert, der die vom Treiber unterstützte SQL-92-Ebene angibt:  
  
 SQL_SC_SQL92_ENTRY = SQL-92-kompatibel auf Einstiegsebene.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = FIPS 127-2 Übergangsstufe konform.  
  
 SQL_SC_SQL92_FULL = SQL-92-kompatibel auf voller Ebene.  
  
 SQL_SC_ SQL92_INTERMEDIATE = SQL-92-kompatibel auf Zwischenebene.  
  
 SQL_SQL92_DATETIME_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die datumszeitlichen Skalarfunktionen aufgibt, die vom Treiber und der zugehörigen Datenquelle unterstützt werden, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Datetime-Funktionen unterstützt werden:  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die für einen Fremdschlüssel unterstützten Regeln in einer **DELETE-Anweisung** aufschlüsselt, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln von der Datenquelle unterstützt werden:  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Ein FIPS Transitional Level-conformant Treiber gibt immer alle diese Optionen wie unterstützt zurück.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die für einen Fremdschlüssel unterstützten Regeln in einer **UPDATE-Anweisung** aufschlüsselt, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln von der Datenquelle unterstützt werden:  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Ein SQL-92 Full level-conformant-Treiber gibt immer alle diese Optionen als unterstützt zurück.  
  
 SQL_SQL92_GRANT(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die in der **GRANT-Anweisung** unterstützten Klauseln aufgibt, wie in SQL-92 definiert.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln von der Datenquelle unterstützt werden:  
  
 SQL_SG_DELETE_TABLE (Einstiegsstufe)SQL_SG_INSERT_COLUMN (Zwischenstufe)SQL_SG_INSERT_TABLE (Einstiegsstufe) SQL_SG_REFERENCES_TABLE (Einstiegsstufe)SQL_SG_REFERENCES_COLUMN (Einstiegsstufe)SQL_SG_SELECT_TABLE (Einstiegsstufe)SQL_SG_UPDATE_COLUMN (Einstiegsstufe)SQL_SG_UPDATE_TABLE (Einstiegsstufe) SQL_SG_USAGE_ON_DOMAIN (FIPS-Übergangsstufe)SQL_SG_USAGE_ON_CHARACTER_SET (FIPS-Übergangsstufe)SQL_SG_USAGE_ON_COLLATION (FIPS-Übergangsstufe)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsebene)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsebene)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsstufe)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsebene)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsebene)(FIPS-Übergangsebene)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsebene)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsebene)(FIPS-Übergangsebene)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsebene)(FIPS-Übergangsstufe)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsebene)(FIPS-Übergangsebene)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsebene)(FIPS-Übergangsstufe)(FIPS-Übergangsebene)SQL_SG_USAGE_ON_TRANSLATION (FIPS-Übergangsstufe Stufe)SQL_SG_WITH_GRANT_OPTION (Einstiegsstufe)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die numerischen Wertskalafunktionen aufgibt, die vom Treiber und der zugehörigen Datenquelle unterstützt werden, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche numerischen Funktionen unterstützt werden:  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die prädikaten, die in einer **SELECT-Anweisung** unterstützt werden, wie in SQL-92 definiert.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SP_BETWEEN (Einstiegsstufe)SQL_SP_COMPARISON (Einstiegsstufe)SQL_SP_EXISTS (Einstiegsstufe)SQL_SP_IN (Einstiegsstufe)SQL_SP_ISNOTNULL (Einstiegsstufe)SQL_SP_ISNULL (Einstiegsstufe)SQL_SP_LIKE (Einstiegsstufe)SQL_SP_MATCH_FULL (Vollstufe)SQL_SP_MATCH_PARTIAL(Vollstufe)SQL_SP_MATCH_UNIQUE_FULL (Vollstufe)SQL_SP_MATCH_UNIQUE_PARTIAL (Vollstufe)SQL_SP_OVERLAPS (FIPS-Übergangsstufe)SQL_SP_QUANTIFIED_COMPARISON (Einstiegsstufe)SQL_SP_UNIQUE (Einstiegsstufe)SQL_SP_UNIQUE(Einstiegsstufe))  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die relationalen Join-Operatoren aufgibt, die in einer **SELECT-Anweisung** unterstützt werden, wie in SQL-92 definiert.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (Zwischenstufe)SQL_SRJO_CROSS_JOIN (Vollebene)SQL_SRJO_EXCEPT_JOIN (Zwischenstufe)SQL_SRJO_FULL_OUTER_JOIN (Zwischenstufe) SQL_SRJO_INNER_JOIN (FIPS-Übergangsstufe)SQL_SRJO_INTERSECT_JOIN (Zwischenstufe)SQL_SRJO_LEFT_OUTER_JOIN (FIPS-Übergangsstufe)SQL_SRJO_NATURAL_JOIN (FIPS-Übergangsstufe)SQL_SRJO_RIGHT_OUTER_JOIN (FIPS-Übergangsstufe)SQL_SRJO_UNION_JOIN (Vollebene))  
  
 SQL_SRJO_INNER_JOIN gibt unterstützungfür die **INNER JOIN-Syntax** an, nicht für die innere Join-Funktion. Die Unterstützung für die **INNER JOIN-Syntax** ist FIPS TRANSITIONAL, während die Unterstützung für die innere Join-Funktion **ENTRY**ist.  
  
 SQL_SQL92_REVOKE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die in der **REVOKE-Anweisung** unterstützten Klauseln aufgibt, wie in SQL-92 definiert, wird von der Datenquelle unterstützt.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln von der Datenquelle unterstützt werden:  
  
 SQL_SR_CASCADE (FIPS-Übergangsstufe) SQL_SR_DELETE_TABLE (Einstiegsstufe)SQL_SR_GRANT_OPTION_FOR (Zwischenstufe) SQL_SR_INSERT_COLUMN (Zwischenstufe)SQL_SR_INSERT_TABLE (Einstiegsstufe)SQL_SR_REFERENCES_COLUMN (Einstiegsstufe)SQL_SR_REFERENCES_TABLE (Einstiegsstufe)SQL_SR_RESTRICT (FIPS-Übergangsstufe)SQL_SR_SELECT_TABLE (Einstiegsstufe)SQL_SR_UPDATE_COLUMN (Einstiegsstufe)SQL_SR_UPDATE_TABLE (Einstiegsstufe)SQL_SR_USAGE_ON_DOMAIN (FIPS-Übergangsstufe)SQL_SR_USAGE_ON_CHARACTER_ SET (FIPS-Übergangsstufe)SQL_SR_USAGE_ON_COLLATION (FIPS-Übergangsstufe)SQL_SR_USAGE_ON_TRANSLATION (FIPS-Übergangsebene))  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Zeilenwertkonstruktorausdrücke aufgibt, die in einer **SELECT-Anweisung** unterstützt werden, wie in SQL-92 definiert. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Zeichenfolgenskalarfunktionen aufgibt, die vom Treiber und der zugehörigen Datenquelle unterstützt werden, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Zeichenfolgenfunktionen unterstützt werden:  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die unterstützten Wertausdrücke aufgibt, wie in SQL-92 definiert.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SVE_CASE (Zwischenstufe)SQL_SVE_CAST (FIPS-Übergangsstufe)SQL_SVE_COALESCE (Zwischenstufe)SQL_SVE_NULLIF (Zwischenstufe)  
  
 SQL_STANDARD_CLI_CONFORMANCE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die den CLI-Standard oder die CLI-Standards aufgibt, denen der Treiber entspricht. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Ebenen der Fahrer erfüllt:  
  
 SQL_SCC_XOPEN_CLI_VERSION1: Der Treiber entspricht der Open Group CLI Version 1.  
  
 SQL_SCC_ISO92_CLI: Der Treiber entspricht der ISO 92 CLI.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines statischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die erste Teilmenge von Attributen. für die zweite Teilmenge siehe SQL_STATIC_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und ersetzen Sie "statischer Cursor" durch "dynamischen Cursor" in den Beschreibungen).  
  
 Ein SQL-92 Intermediate Level-conformant-Treiber gibt in der Regel die SQL_CA1_NEXT-, SQL_CA1_ABSOLUTE- und SQL_CA1_RELATIVE-Optionen als unterstützt zurück, da der Treiber scrollbare Cursor durch die eingebettete SQL FETCH-Anweisung unterstützt. Da dies jedoch nicht direkt die zugrunde liegende SQL-Unterstützung bestimmt, werden scrollbare Cursor möglicherweise nicht unterstützt, selbst für einen SQL-92 Intermediate Level-conformant-Treiber.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines statischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die zweite Teilmenge von Attributen. für die erste Teilmenge siehe SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (und ersetzen Sie "statischer Cursor" durch "dynamischen Cursor" in den Beschreibungen).  
  
 SQL_STRING_FUNCTIONS(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC 1.0 eingeführt; jede Bitmaske wird mit der Version beschriftet, in der sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske, die die skalaren Zeichenfolgenfunktionen aufgibt, die vom Treiber und der zugehörigen Datenquelle unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Zeichenfolgenfunktionen unterstützt werden:  
  
 SQL_FN_STR_ASCII (ODBC 1.0)SQL_FN_STR_BIT_LENGTH (ODBC 3.0)SQL_FN_STR_CHAR (ODBC 1.0)SQL_FN_STR_CHAR_LENGTH (ODBC 3.0)SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0)SQL_FN_STR_CONCAT (ODBC 1.0)SQL_FN_STR_DIFFERENCE (ODBC 2.0)SQL_FN_STR_INSERT (ODBC 1.0)SQL_FN_STR_LCASE (ODBC 1.0)SQL_FN_STR_LEFT (ODBC 1.0)SQL_FN_STR_LENGTH (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LTRIM SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LEFT (ODBC 1.0)SQL_FN_STR_LENGTH (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LEFT (ODBC 1.0)SQL_FN_STR_LENGTH (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LENGTH (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1. 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0)SQL_FN_STR_REPEAT (ODBC 1.0)SQL_FN_STR_REPLACE (ODBC 1.0)SQL_FN_STR_RIGHT (ODBC 1.0)SQL_FN_STR_RTRIM (ODBC 1.0)SQL_FN_STR_SOUNDEX (ODBC 2.0)SQL_FN_STR_SPACE (ODBC 2.0)SQL_FN_STR_SUBSTRING (ODBC 1.0)SQL_FN_STR_UCASE (ODBC 1.0)SQL_FN_STR_UCASE (ODBC 1.0)  
  
 Wenn eine Anwendung die LOCATE-Skalarfunktion mit den Argumenten *string_exp1*, *string_exp2*und *Startaufrufen* aufrufen kann, gibt der Treiber die SQL_FN_STR_LOCATE Bitmaske zurück. **LOCATE** Wenn eine Anwendung die LOCATE-Skalarfunktion nur mit den *Argumenten string_exp1* und *string_exp2* aufrufen kann, gibt der Treiber die SQL_FN_STR_LOCATE_2 Bitmaske zurück. Treiber, die **LOCATE** die LOCATE-Skalafunktion vollständig unterstützen, geben beide Bitmasken zurück.  
  
 (Weitere Informationen finden Sie unter [String-Funktionen](../../../odbc/reference/appendixes/string-functions.md) in Anhang E, "Skalare Funktionen.")  
  
 SQL_SUBQUERIES(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Prädikate aufgibt, die Unterabfragen unterstützen:  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 Die SQL_SQ_CORRELATED_SUBQUERIES Bitmaske gibt an, dass alle Prädikate, die Unterabfragen unterstützen, korrelierte Unterabfragen unterstützen.  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer eine Bitmaske zurück, in der alle diese Bits festgelegt sind.  
  
 SQL_SYSTEM_FUNCTIONS(ODBC 1.0)  
 Eine SQLUINTEGER-Bitmaske, die die skalaren Systemfunktionen aufgibt, die vom Treiber und der zugehörigen Datenquelle unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Systemfunktionen unterstützt werden:  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM(ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen des Datenquellenanbieters für eine Tabelle; z. B. "Tabelle" oder "Datei".  
  
 Diese Zeichenfolge kann in Groß-, Klein- oder Mischfällen sein.  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer "Table" zurück.  
  
 SQL_TIMEDATE_ADD_INTERVALS(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die vom Treiber und der zugehörigen Datenquelle für die Scalar-Funktion TIMESTAMPADD unterstützten Zeitstempelintervalle aufgibt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Intervalle unterstützt werden:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Ein FIPS Transitional Level-conformant Treiber gibt immer eine Bitmaske zurück, in der alle diese Bits gesetzt sind.  
  
 SQL_TIMEDATE_DIFF_INTERVALS(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die vom Treiber und der zugehörigen Datenquelle für die Scalar-Funktion TIMESTAMPDIFF unterstützten Zeitstempelintervalle aufgibt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Intervalle unterstützt werden:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Ein FIPS Transitional Level-conformant Treiber gibt immer eine Bitmaske zurück, in der alle diese Bits gesetzt sind.  
  
 SQL_TIMEDATE_FUNCTIONS(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC 1.0 eingeführt; jede Bitmaske wird mit der Version beschriftet, in der sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske, die die vom Treiber und der zugehörigen Datenquelle unterstützten skalaren Datums- und Uhrzeitfunktionen aufgibt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Datums- und Uhrzeitfunktionen unterstützt werden:  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0)SQL_FN_TD_CURRENT_TIME (ODBC 3.0)SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0)SQL_FN_TD_CURDATE (ODBC 1.0)SQL_FN_TD_CURTIME (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0)SQL_FN_TD_DAYOFMONTH (ODBC 1.0)SQL_FN_TD_DAYOFWEEK (ODBC 1.0)SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT (ODBC 3.0)SQL_FN_TD_HOUR (ODBC 1.0)SQL_FN_TD_MINUTE (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MINUTE (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTHNAME (ODBC 2.0)SQL_FN_TD_NOW (ODBC 1.0)SQL_FN_TD_QUARTER (ODBC 1.0)SQL_FN_TD_SECOND (ODBC 1.0)SQL_FN_TD_TIMESTAMPADD (ODBC 2.0)SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0)SQL_FN_TD_WEEK (ODBC 1.0)SQL_FN_TD_YEAR (ODBC 1.0))  
  
 SQL_TXN_CAPABLE(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC 1.0 eingeführt; jeder Rückgabewert wird mit der Version beschriftet, in der er eingeführt wurde.  
  
 Ein SQLUSMALLINT-Wert, der die Transaktionsunterstützung im Treiber oder in der Datenquelle beschreibt:  
  
 SQL_TC_NONE = Transaktionen werden nicht unterstützt. (ODBC 1.0)  
  
 SQL_TC_DML = Transaktionen können nur DML-Anweisungen (Data Manipulation Language) enthalten (**SELECT**, **INSERT**, **UPDATE**, **DELETE**). DDL-Anweisungen (Data Definition Language) in einer Transaktion verursachen einen Fehler. (ODBC 1.0)  
  
 SQL_TC_DDL_COMMIT = Transaktionen können nur DML-Anweisungen enthalten. DDL-Anweisungen (**CREATE TABLE**, **DROP INDEX**usw.), die in einer Transaktion gefunden wurden, führen dazu, dass die Transaktion festgeschrieben wird. (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE = Transaktionen können nur DML-Anweisungen enthalten. DDL-Anweisungen, die in einer Transaktion gefunden wurden, werden ignoriert. (ODBC 2.0)  
  
 SQL_TC_ALL = Transaktionen können DDL-Anweisungen und DML-Anweisungen in beliebiger Reihenfolge enthalten. (ODBC 1.0)  
  
 (Da die Unterstützung von Transaktionen in SQL-92 obligatorisch ist, wird ein SQL-92-konformer Treiber [jede Ebene] niemals SQL_TC_NONE zurückgeben.)  
  
 SQL_TXN_ISOLATION_OPTION(ODBC 1.0)  
 Eine SQLUINTEGER-Bitmaske, die die Transaktionsisolationsebenen aufgibt, die vom Treiber oder der Datenquelle verfügbar sind.  
  
 Die folgenden Bitmasken werden zusammen mit dem Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden:  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Beschreibungen dieser Isolationsstufen finden Sie in der Beschreibung von SQL_DEFAULT_TXN_ISOLATION.  
  
 Um die Transaktionsisolationsstufe festzulegen, ruft eine Anwendung **SQLSetConnectAttr auf,** um das SQL_ATTR_TXN_ISOLATION-Attribut festzulegen. Weitere Informationen finden Sie unter [SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer SQL_TXN_SERIALIZABLE als unterstützt zurück. Ein FIPS Transitional Level-conformant Treiber gibt immer alle diese Optionen als unterstützt zurück.  
  
 SQL_UNION(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung für die **UNION-Klausel** aufgibt:  
  
 SQL_U_UNION = Die Datenquelle **UNION** unterstützt die UNION-Klausel.  
  
 SQL_U_UNION_ALL = Die Datenquelle **ALL** unterstützt das ALL-Schlüsselwort in der **UNION-Klausel.** (**SQLGetInfo** gibt in diesem Fall sowohl SQL_U_UNION als auch SQL_U_UNION_ALL zurück.)  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer beide Optionen als unterstützt zurück.  
  
 SQL_USER_NAME(ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen, der in einer bestimmten Datenbank verwendet wird, die sich vom Anmeldenamen unterscheiden kann.  
  
 SQL_XOPEN_CLI_YEAR(ODBC 3.0)  
 Eine Zeichenfolge, die das Jahr der Veröffentlichung der Open Group-Spezifikation angibt, mit dem die Version des ODBC-Treiber-Managers vollständig übereinstimmt.  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn der Benutzer alle von **SQLProcedures**zurückgegebenen Prozeduren ausführen kann; "N", wenn prozedursgebunden werden kann, die der Benutzer nicht ausführen kann.  
  
 SQL_ACCESSIBLE_TABLES(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn dem Benutzer **SELECT-Berechtigungen** für alle von **SQLTables**zurückgegebenen Tabellen garantiert werden; "N", wenn Möglicherweise Tabellen zurückgegeben werden, auf die der Benutzer nicht zugreifen kann.  
  
 SQL_ACTIVE_ENVIRONMENTS(ODBC 3.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl aktiver Umgebungen angibt, die der Treiber unterstützen kann. Wenn kein angegebener Grenzwert vorhanden ist oder der Grenzwert unbekannt ist, wird dieser Wert auf Null gesetzt.  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung für Aggregationsfunktionen aufgibt:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Ein SQL-92 Entry-Level-konformer Treiber gibt immer alle diese Optionen als unterstützt zurück.  
  
 SQL_ALTER_DOMAIN(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **ALTER DOMAIN-Anweisung** aufgibt, wie in SQL-92 definiert, unterstützt von der Datenquelle. Ein SQL-92 Full Level-kompatibler Treiber gibt immer alle Bitmasken zurück. Der Rückgabewert "0" bedeutet, dass die **ALTER DOMAIN-Anweisung** nicht unterstützt wird.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = Hinzufügen einer Domäneneinschränkung wird unterstützt (Vollständige Ebene)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT \<= Domänenändern> \<Festlegen von Domänenstandardklauseln> wird unterstützt (Vollständige Ebene)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION \<= Einschränkungsnamensdefinitionsklausel> wird für das Benennen von Domäneneinschränkung (Zwischenebene) unterstützt.  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT \<= Drop-Domain-Einschränkungsklausel> wird unterstützt (Vollständige Ebene)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT \<= Domain \<ändern> Domain-Standardklausel> wird unterstützt (Vollebene)  
  
 Die folgenden Bits \<geben die unterstützten Einschränkungsattribute> an, wenn \<die> hinzufügen von Domäneneinschränkungen unterstützt wird (das SQL_AD_ADD_DOMAIN_CONSTRAINT Bit ist festgelegt):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (Vollständige Stufe)SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (Vollständige Ebene)SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (Vollständige Stufe)SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (Vollständige Ebene)  
  
 SQL_ALTER_TABLE(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **ALTER TABLE-Anweisung** aufgibt, die von der Datenquelle unterstützt wird.  
  
 Die SQL-92- oder FIPS-Konformitätsebene, auf der dieses Feature unterstützt werden muss, wird in Klammern neben jeder Bitmaske angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AT_ADD_COLUMN_COLLATION \<= Spaltenhinzufügen>-Klausel unterstützt wird, mit der Möglichkeit, die Spaltensortierung (Vollständige Ebene) anzugeben (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT \<= Spalten>-Klausel hinzufügen unterstützt wird, mit der Möglichkeit, Spaltenstandards (FIPS-Übergangsebene) anzugeben (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE \<= Spalte hinzufügen,> unterstützt wird (FIPS-Übergangsstufe) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT \<= Spalten>-Klausel hinzufügen unterstützt wird, mit der Möglichkeit, Spalteneinschränkungen (FIPS-Übergangsebene) anzugeben (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT \<= Tabelleneinschränkung hinzufügen>-Klausel unterstützt wird (FIPS-Übergangsebene) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION \<= Einschränkungsnamensdefinition> wird für Dasnamenspalten- und Tabelleneinschränkungen (Zwischenebene) (ODBC 3.0) unterstützt.  
  
 SQL_AT_DROP_COLUMN_CASCADE \<= Ablagespalte> CASCADE unterstützt wird (FIPS-Übergangsstufe) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT \<= Spalte \<ändern> Drop-Spalten-Standardklausel> unterstützt wird (Zwischenstufe) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT \<= Ablagespalte> RESTRICT wird unterstützt (FIPS-Übergangsstufe) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT \<= Ablagespalte> RESTRICT unterstützt wird (FIPS-Übergangsstufe) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT \<= Spalte \<ändern> Satzspaltenstandardklausel> unterstützt wird (Zwischenstufe) (ODBC 3.0)  
  
 Die folgenden Bits \<geben die Support-Einschränkungsattribute> an, wenn die Angabe von Spalten- oder Tabelleneinschränkungen unterstützt wird (das SQL_AT_ADD_CONSTRAINT Bit festgelegt ist):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (Vollstufe) (ODBC 3.0)SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (Vollstufe) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (Vollebene) (ODBC 3.0)SQL_AT_CONSTRAINT_NON_DEFERRABLE (Vollebene) (ODBC 3.0)  
  
 SQL_ASYNC_MODE(ODBC 3.0)  
 Ein SQLUINTEGER-Wert, der den Grad der asynchronen Unterstützung im Treiber angibt:  
  
 SQL_AM_CONNECTION = Asynchrone Ausführung auf Verbindungsebene wird unterstützt. Entweder befinden sich alle Anweisungshandles, die einem bestimmten Verbindungshandle zugeordnet sind, im asynchronen Modus oder alle befinden sich im synchronen Modus. Ein Anweisungshandle für eine Verbindung kann sich nicht im asynchronen Modus befinden, während sich ein anderes Anweisungshandle auf derselben Verbindung im synchronen Modus befindet und umgekehrt.  
  
 SQL_AM_STATEMENT = Asynchrone Ausführung auf Anweisungsebene wird unterstützt. Einige Anweisungshandles, die einem Verbindungshandle zugeordnet sind, können sich im asynchronen Modus befinden, während andere Anweisungshandles auf derselben Verbindung sich im synchronen Modus befinden.  
  
 SQL_AM_NONE = Der asynchrone Modus wird nicht unterstützt.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die das Verhalten des Treibers in Bezug auf die Verfügbarkeit von Zeilenanzahlen aufzählt. Die folgenden Bitmasken werden zusammen mit dem Informationstyp verwendet:  
  
 SQL_BRC_ROLLED_UP = Zeilenanzahlen für aufeinander folgende INSERT-, DELETE- oder UPDATE-Anweisungen werden in einer zusammengerollt. Wenn dieses Bit nicht festgelegt ist, sind Zeilenanzahlen für jede Anweisung verfügbar.  
  
 SQL_BRC_PROCEDURES = Zeilenanzahlen, falls vorhanden, sind verfügbar, wenn ein Batch in einer gespeicherten Prozedur ausgeführt wird. Wenn Zeilenanzahlen verfügbar sind, können sie je nach SQL_BRC_ROLLED_UP Bit aufgerollt oder einzeln verfügbar sein.  
  
 SQL_BRC_EXPLICIT = Zeilenanzahlen, falls vorhanden, sind verfügbar, wenn ein Batch direkt durch Aufrufen von **SQLExecute** oder **SQLExecDirect**ausgeführt wird. Wenn Zeilenanzahlen verfügbar sind, können sie je nach SQL_BRC_ROLLED_UP Bit aufgerollt oder einzeln verfügbar sein.  
  
## <a name="example"></a>Beispiel  
 **SQLGetInfo** gibt Listen mit unterstützten Optionen als SQLUINTEGER-Bitmaske in **InfoValuePtr*zurück. Die Bitmaske für jede Option wird zusammen mit dem Flag verwendet, um zu bestimmen, ob die Option unterstützt wird.  
  
 Eine Anwendung kann z. B. den folgenden Code verwenden, um zu bestimmen, ob die SUBSTRING-Skalafunktion von dem der Verbindung zugeordneten Treiber unterstützt wird.  
  
 Ein weiteres Beispiel für die Verwendung von **SQLGetInfo**finden Sie unter [SQLTables Function](../../../odbc/reference/syntax/sqltables-function.md).  
  
```cpp  
SQLUINTEGER fFuncs;  
  
SQLGetInfo(hdbc,   
           SQL_STRING_FUNCTIONS,  
           (SQLPOINTER)&fFuncs,  
           sizeof(fFuncs),  
           NULL);  
  
// SUBSTRING supported  
if (fFuncs & SQL_FN_STR_SUBSTRING)   
   ;   // do something  
  
// SUBSTRING not supported  
else  
   ;   // do something else  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
 Zurückgeben der Einstellung eines Verbindungsattributs  
 [SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Bestimmen, ob ein Treiber eine Funktion unterstützt  
 [SQLGetFunctions-Funktion](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Zurückgeben der Einstellung eines Anweisungsattributs  
 [SQLGetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Zurückgeben von Informationen zu den Datentypen einer Datenquelle  
 [SQLGetTypeInfo-Funktion](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
