---
title: SQLGetInfo-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303342"
---
# <a name="sqlgetinfo-function"></a>SQLGetInfo-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
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
  
 *Infotype*  
 Der Informationstyp.  
  
 *Infovalueptr*  
 Ausgeben Zeiger auf einen Puffer, in den die Informationen zurückgegeben werden sollen. Abhängig vom angeforderten *InfoType* sind die zurückgegebenen Informationen eine der folgenden: eine auf NULL endende Zeichenfolge, ein sqlusmallint-Wert, eine SQLUINTEGER-Bitmaske, ein SQLUINTEGER-Flag, ein SQLUINTEGER-Binärwert oder ein SQLULEN-Wert.  
  
 Wenn das *InfoType* -Argument SQL_DRIVER_HDESC oder SQL_DRIVER_HSTMT ist, ist das *infovalueptr* -Argument sowohl Input als auch Output. (Weitere Informationen finden Sie in den SQL_DRIVER_HDESC-oder SQL_DRIVER_HSTMT Deskriptoren weiter unten in dieser Funktionsbeschreibung.)  
  
 Wenn *infovalueptr* gleich NULL ist, gibt *stringlengthptr* weiterhin die Gesamtzahl der Bytes (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten) zurück, die im Puffer zurückgegeben werden können, auf den *infovalueptr*zeigt.  
  
 *Pufferlänge*  
 Der Länge des \* *infovalueptr* -Puffers. Wenn der Wert in * \*infovalueptr* keine Zeichenfolge ist oder wenn *infovalueptr* ein NULL-Zeiger ist, wird das *BufferLength* -Argument ignoriert. Der Treiber geht davon aus, dass die Größe von * \*infovalueptr* basierend auf dem *InfoType*auf sqlusmallint oder SQLUINTEGER festgelegt ist. Wenn * \*infovalueptr* eine Unicode-Zeichenfolge ist (beim Aufrufen von **sqlgetinfow**), muss das *BufferLength* -Argument eine gerade Zahl sein. Andernfalls wird SQLSTATE HY090 (ungültige Zeichen folgen-oder Pufferlänge) zurückgegeben.  
  
 *Stringlengthptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten) zurückgegeben werden soll, die in **infovalueptr*zurückgegeben werden können.  
  
 Wenn die Anzahl von Bytes, die für die Rückgabe verfügbar sind, größer oder gleich *BufferLength*ist, werden die Informationen in \* *infovalueptr* auf *BufferLength* -Bytes abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt und vom Treiber auf NULL-terminiert.  
  
 Für alle anderen Datentypen wird der Wert von *BufferLength* ignoriert, und der Treiber geht davon aus, dass \*die Größe von *infovalueptr* abhängig vom *InfoType*sqlusmallint oder SQLUINTEGER ist.  
  
## <a name="return-value"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetInfo** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_DBC und einem *handle* von *connectionHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLGetInfo** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Der \* *infovalueptr* -Puffer war nicht groß genug, um alle angeforderten Informationen zurückzugeben. Aus diesem Grund wurden die Informationen abgeschnitten. Die Länge der angeforderten Informationen in der nicht abgeschnittene Form wird in **stringlengthptr*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) für den in *InfoType* angeforderten Informationstyp ist eine geöffnete Verbindung erforderlich. Von den Informationstypen, die von ODBC reserviert werden, können nur SQL_ODBC_VER ohne geöffnete Verbindung zurückgegeben werden.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY024|Ungültiger Attribut Wert|(DM) das *InfoType* -Argument wurde SQL_DRIVER_HSTMT, und der Wert, auf den von *infovalueptr* verwiesen wird, war kein gültiges Anweisungs Handle.<br /><br /> (DM) das *InfoType* -Argument wurde SQL_DRIVER_HDESC, und der Wert, auf den von *infovalueptr* verwiesen wird, war kein gültiges Deskriptorhandle.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der für das Argument *BufferLength* angegebene Wert war kleiner als 0 (null).<br /><br /> (DM) der für *BufferLength* angegebene Wert war eine ungerade Zahl, und * \*infovalueptr* war von einem Unicode-Datentyp.|  
|HY096|Informationstyp außerhalb des gültigen Bereichs|Der für den Argument *InfoType* angegebene Wert war für die Version von ODBC, die vom Treiber unterstützt wird, ungültig.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feld nicht implementiert|Der für das Argument *InfoType* angegebene Wert war ein Treiber spezifischer Wert, der vom Treiber nicht unterstützt wird.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der Treiber, der dem *connectionHandle* entspricht, unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Die derzeit definierten Informationstypen werden in diesem Abschnitt unter "Informationstypen" angezeigt. Es wird erwartet, dass mehr Datenquellen definiert werden, um unterschiedliche Datenquellen zu nutzen. Ein Bereich von Informationstypen wird von ODBC reserviert. Treiber Entwickler müssen Werte für Ihre eigene Treiber spezifische Verwendung in der geöffneten Gruppe reservieren. **SQLGetInfo** führt keine Unicode-Konvertierung oder- *Thunking* durch (siehe [Anhang A: ODBC-Fehler Codes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) der *ODBC-Programmier Referenz*) für Treiber definierte *INFOTYPES*. Weitere Informationen finden Sie unter [Treiber spezifische Datentypen, deskriptortypen, Informationstypen, Diagnose Typen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Das Format der Informationen, die in \* *infovalueptr* zurückgegeben werden, hängt vom angeforderten *InfoType* ab. **SQLGetInfo** gibt Informationen in einem von fünf verschiedenen Formaten zurück:  
  
-   Eine NULL terminierte Zeichenfolge.  
  
-   Einen sqlusmallint-Wert  
  
-   Eine SQLUINTEGER-Bitmaske  
  
-   Einen SQLUINTEGER-Wert  
  
-   Ein SQLUINTEGER-Binärwert  
  
 Das Format der folgenden Informationstypen wird in der Beschreibung des Typs angegeben. Die Anwendung muss den in **infovalueptr* zurückgegebenen Wert entsprechend umwandeln. Ein Beispiel dafür, wie eine Anwendung Daten aus einer SQLUINTEGER-Bitmaske abrufen kann, finden Sie unter "Code Beispiel".  
  
 Ein Treiber muss für jeden Informationstyp, der in den folgenden Tabellen definiert ist, einen Wert zurückgeben. Wenn ein Informationstyp nicht auf den Treiber oder die Datenquelle angewendet wird, gibt der Treiber einen der in der folgenden Tabelle aufgeführten Werte zurück.  
  
 Zeichenfolge ("Y" oder "N")  
 "N"  
  
 Zeichenfolge (nicht "Y" oder "N")  
 leere Zeichenfolge  
  
 Sqlusmallint  
 0  
  
 SQLUINTEGER-Bitmaske oder SQLUINTEGER-Binärwert  
 0L  
  
 Wenn eine Datenquelle z. b. keine Prozeduren unterstützt, gibt **SQLGetInfo** die in der folgenden Tabelle aufgeführten Werte für die Werte von *InfoType* zurück, die mit Prozeduren verknüpft sind.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 leere Zeichenfolge  
  
 **SQLGetInfo** gibt SQLSTATE HY096 (Ungültiger Argument Wert) für die *InfoType* -Werte zurück, die im Bereich von Informationstypen liegen, die für die Verwendung durch ODBC reserviert sind, aber nicht durch die vom Treiber unterstützte Version von ODBC definiert sind. Um zu ermitteln, welche Version von ODBC ein Treiber erfüllt, ruft eine Anwendung **SQLGetInfo** mit dem SQL_DRIVER_ODBC_VER Informationstyp auf. **SQLGetInfo** gibt SQLSTATE HYC00 (optionales Feature nicht implementiert) für die *InfoType* -Werte zurück, die sich im Bereich von Informationstypen befinden, die für die Treiber spezifische Verwendung reserviert sind, jedoch nicht vom Treiber unterstützt werden.  
  
 Alle Aufrufe von **SQLGetInfo** erfordern eine geöffnete Verbindung, außer wenn der *InfoType* SQL_ODBC_VER ist, der die Version des Treiber-Managers zurückgibt.  
  
## <a name="information-types"></a>Informationstypen  
 In diesem Abschnitt werden die von **SQLGetInfo**unterstützten Informationstypen aufgelistet. Informationstypen werden kategorisch gruppiert und alphabetisch aufgelistet. Informationstypen, die für ODBC 3 *. x* hinzugefügt oder umbenannt wurden, werden ebenfalls aufgelistet.  
  
## <a name="driver-information"></a>Treiber Informationen  
 Die folgenden Werte des *InfoType* -Arguments geben Informationen zum ODBC-Treiber zurück, z. b. die Anzahl aktiver Anweisungen, den Datenquellen Namen und die Kompatibilitäts Ebene der Schnittstellenstandards:  
  
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
>  Bei der Implementierung von **SQLGetInfo**kann ein Treiber die Leistung verbessern, indem die Anzahl der vom Server gesendeten oder angeforderten Informationen minimiert wird.  
  
## <a name="dbms-product-information"></a>DBMS-Produktinformationen  
 Die folgenden Werte des *InfoType* -Arguments geben Informationen zum DBMS-Produkt zurück, z. b. DBMS-Name und-Version:  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Datenquellen Informationen  
 Die folgenden Werte des *InfoType* -Arguments geben Informationen über die Datenquelle zurück, z. b. Cursor Merkmale und Transaktionsfunktionen:  
  
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
  
## <a name="supported-sql"></a>Unterstützte SQL-  
 Die folgenden Werte des *InfoType* -Arguments geben Informationen über die SQL-Anweisungen zurück, die von der Datenquelle unterstützt werden. Die SQL-Syntax der einzelnen Features, die von diesen Informationstypen beschrieben werden, ist die SQL-92-Syntax. Diese Informationstypen beschreiben nicht die gesamte SQL-92-Grammatik. Stattdessen beschreiben Sie die Teile der Grammatik, für die Datenquellen in der Regel unterschiedliche Ebenen der Unterstützung bieten. Insbesondere werden die meisten DDL-Anweisungen in SQL-92 abgedeckt.  
  
 Anwendungen sollten die allgemeine Ebene der unterstützten Grammatik aus dem SQL_SQL_CONFORMANCE Informationstyp ermitteln und die anderen Informationstypen verwenden, um Abweichungen von der angegebenen Standards-Kompatibilitäts Stufe zu ermitteln.  
  
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
  
## <a name="sql-limits"></a>SQL-Limits  
 Die folgenden Werte des *InfoType* -Arguments geben Informationen zu den Grenzwerten zurück, die auf Bezeichner und Klauseln in SQL-Anweisungen angewendet werden, z. b. die maximale Länge von bezeichnerwerten und die maximale Anzahl von Spalten in einer Auswahlliste. Einschränkungen können durch den Treiber oder die Datenquelle auferlegt werden.  
  
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
  
## <a name="scalar-function-information"></a>Informationen zur Skalarfunktion  
 Die folgenden Werte des *InfoType* -Arguments geben Informationen über die skalaren Funktionen zurück, die von der Datenquelle und dem Treiber unterstützt werden. Weitere Informationen zu skalaren Funktionen finden Sie unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Konvertierungs Informationen  
 Die folgenden Werte des *InfoType* -Arguments geben eine Liste der SQL-Datentypen zurück, in die die Datenquelle den angegebenen SQL-Datentyp mit der **Convert** -Skalarfunktion konvertieren kann:  
  
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
  
## <a name="information-types-added-for-odbc-3x"></a>Für ODBC 3. x hinzugefügte Informationstypen  
 Die folgenden Werte des *InfoType* -Arguments wurden für ODBC 3 *. x*hinzugefügt:  
  
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
  
## <a name="information-types-renamed-for-odbc-3x"></a>Für ODBC 3. x umbenannte Informationstypen  
 Die folgenden Werte des *InfoType* -Arguments wurden für ODBC 3 *. x*umbenannt.  
  
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
  
## <a name="information-types-deprecated-in-odbc-3x"></a>In ODBC 3. x veraltete Informationstypen  
 Die folgenden Werte des *InfoType* -Arguments wurden in ODBC 3 *. x*als veraltet markiert. ODBC 3 *. x* -Treiber müssen diese Informationstypen für die Abwärtskompatibilität mit ODBC 2 *. x* -Anwendungen weiterhin unterstützen. (Weitere Informationen zu diesen Typen finden Sie [unter SQLGetInfo-Unterstützung](../../../odbc/reference/appendixes/sqlgetinfo-support.md) in Anhang G: Treiber Richtlinien zur Abwärtskompatibilität.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Beschreibungen von Informationstypen  
 In der folgenden Tabelle sind die einzelnen Informationstypen, die Version von ODBC, in der Sie eingeführt wurde, und ihre Beschreibung alphabetisch aufgeführt.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1,0)  
 Eine Zeichenfolge: "Y", wenn der Benutzer alle Prozeduren ausführen kann, die von **SQLProcedures**zurückgegeben werden. "N", wenn möglicherweise Prozeduren zurückgegeben werden, die der Benutzer nicht ausführen kann.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1,0)  
 Eine Zeichenfolge: "Y", wenn dem **Benutzer garantiert wird** , dass er Berechtigungen für alle von **SQLTables**zurückgegebenen Tabellen hat. "N", wenn möglicherweise Tabellen zurückgegeben werden, auf die der Benutzer nicht zugreifen kann.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl aktiver Umgebungen angibt, die der Treiber unterstützen kann. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung für Aggregations Funktionen aufzählt:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Ein mit SQL-92 Eintrags Level übergebender Treiber gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_ALTER_DOMAIN (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Alter Domain** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird. Ein vollständig kompatibler SQL-92-Treiber gibt immer alle Bitmasken zurück. Der Rückgabewert "0" bedeutet, dass die **Alter Domain** -Anweisung nicht unterstützt wird.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = das Hinzufügen einer Domänen Einschränkung wird unterstützt (vollständig)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<Alter Domain> \<Set Domain default-Klausel> wird unterstützt (vollständig)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<Einschränkungs Name-Definitions Klausel> wird für Benennungs Domänen Einschränkung unterstützt (Zwischenebene)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<Drop Domain-Einschränkungs Klausel> wird unterstützt (vollständig)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<Alter Domain> \<Drop Domain default-Klausel> wird unterstützt (vollständig)  
  
 In den folgenden Bits werden die \<unterstützten Einschränkungs \<Attribute> angegeben, wenn Add Domain-Einschränkungs> unterstützt wird (das SQL_AD_ADD_DOMAIN_CONSTRAINT Bit ist festgelegt):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (vollständig) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (vollständig) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (vollständig) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (vollständig)  
  
 SQL_ALTER_TABLE (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die die-Klauseln in der **ALTER TABLE** -Anweisung auflistet, die von der Datenquelle unterstützt wird.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<Spalte> Klausel hinzufügen wird unterstützt, mit der Funktion zum Angeben der Spalten Sortierung (vollständig) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<Spalte> Klausel hinzufügen wird unterstützt, mit der Funktion zum Angeben von 3,0 Spalten Standardwerten  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<Spalte hinzufügen> wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_ADD_CONSTRAINT = \<Spalte zum Hinzufügen von Spalten> wird unterstützt, mit der Funktion zum Angeben von Spalten Einschränkungen (über die Übergangsstufe "Fi") (ODBC 3,0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<Table-Einschränkung hinzufügen> Klausel wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<Einschränkungs Name Definition> wird für das Benennen von Spalten-und Tabellen Einschränkungen (Zwischenebene) unterstützt (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<Drop Column> Cascade wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<Alter Column> \<Drop Column default-Klausel> wird unterstützt (Zwischenstufe) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<Drop Column> Einschränkung wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<Drop Column> Einschränkung wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<Alter Column> \<Set Column default-Klausel> wird unterstützt (Zwischenstufe) (ODBC 3,0)  
  
 Die folgenden Bits geben die Unterstützungs \<Einschränkungs Attribute> an, wenn die Angabe von Spalten-oder Tabellen Einschränkungen unterstützt wird (das SQL_AT_ADD_CONSTRAINT Bit ist festgelegt):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (vollständig) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (vollständig) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (vollständig) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (vollständig) (ODBC 3,0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3,8)  
 Ein SQLUINTEGER-Wert, der angibt, ob der Treiberfunktionen asynchron auf dem Verbindungs Handle ausführen kann.  
  
 SQL_ASYNC_DBC_CAPABLE = der Treiber kann Verbindungsfunktionen asynchron ausführen.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = der Treiber kann Verbindungsfunktionen nicht asynchron ausführen.  
  
 SQL_ASYNC_MODE (ODBC 3,0)  
 Ein SQLUINTEGER-Wert, der die Ebene der asynchronen Unterstützung im Treiber angibt:  
  
 SQL_AM_CONNECTION = asynchrone Ausführung auf Verbindungs Ebene wird unterstützt. Entweder sind alle Anweisungs Handles, die einem gegebenen Verbindungs Handle zugeordnet sind, im asynchronen Modus, oder alle sind im synchronen Modus. Ein Anweisungs Handle für eine Verbindung kann sich nicht im asynchronen Modus befinden, während ein anderes Anweisungs Handle für dieselbe Verbindung im synchronen Modus ist und umgekehrt.  
  
 SQL_AM_STATEMENT = asynchrone Ausführung auf Anweisungs Ebene wird unterstützt. Einige Anweisungs Handles, die einem Verbindungs Handle zugeordnet sind, können sich im asynchronen Modus befinden, während sich andere Anweisungs Handles auf derselben Verbindung im synchronen Modus befinden.  
  
 SQL_AM_NONE = der asynchrone Modus wird nicht unterstützt.  
  
 SQL_ASYNC_NOTIFICATION  
 Ein SQLUINTEGER-Wert, der angibt, ob der Treiber die asynchrone Benachrichtigung unterstützt:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** Die asynchrone Ausführungs Benachrichtigung wird vom Treiber unterstützt.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** Die asynchrone Ausführungs Benachrichtigung wird vom Treiber nicht unterstützt.  
  
 Es gibt zwei Kategorien von asynchronen ODBC-Vorgängen: asynchrone Vorgänge auf Verbindungs Ebene und asynchrone Vorgänge auf Anweisungs Ebene.  Wenn ein Treiber SQL_ASYNC_NOTIFICATION_CAPABLE zurückgibt, muss er Benachrichtigungen für alle APIs unterstützen, die er asynchron ausführen kann.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die das Verhalten des Treibers in Bezug auf die Verfügbarkeit der Zeilen Anzahl auflistet. Die folgenden Bitmasken werden in Verbindung mit dem Informationstyp verwendet:  
  
 SQL_BRC_ROLLED_UP = die Zeilen Anzahl für aufeinander folgende INSERT-, DELETE-oder Update-Anweisungen werden in einen Rollup ausgeführt. Wenn dieses Bit nicht festgelegt ist, sind die Zeilen Anzahl für jede Anweisung verfügbar.  
  
 SQL_BRC_PROCEDURES = die Zeilen Anzahl, sofern vorhanden, sind verfügbar, wenn ein Batch in einer gespeicherten Prozedur ausgeführt wird. Wenn die Anzahl der Zeilen verfügbar ist, können Sie je nach SQL_BRC_ROLLED_UP Bit ein Rollup oder eine individuelle Verfügbarkeit durchgeführt werden.  
  
 SQL_BRC_EXPLICIT = Zeilen Anzahl, sofern vorhanden, sind verfügbar, wenn ein Batch direkt durch Aufrufen von **SQLExecute** oder **SQLExecDirect**ausgeführt wird. Wenn die Anzahl der Zeilen verfügbar ist, können Sie je nach SQL_BRC_ROLLED_UP Bit ein Rollup oder eine individuelle Verfügbarkeit durchgeführt werden.  
  
 SQL_BATCH_SUPPORT (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung für Batches des Treibers auflistet. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Ebene unterstützt wird:  
  
 SQL_BS_SELECT_EXPLICIT = der Treiber unterstützt explizite Batches, die Resultset-Generierungs Anweisungen aufweisen können.  
  
 SQL_BS_ROW_COUNT_EXPLICIT = der Treiber unterstützt explizite Batches, die Anweisungen zum Erstellen von Zeilen Anzahl haben können.  
  
 SQL_BS_SELECT_PROC = der Treiber unterstützt explizite Prozeduren, die Resultset-Generierungs Anweisungen aufweisen können.  
  
 SQL_BS_ROW_COUNT_PROC = der Treiber unterstützt explizite Prozeduren, die Anweisungen zum Erstellen von Zeilen Anzahl aufweisen können.  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die die Vorgänge auflistet, über die Lesezeichen persistent gespeichert werden.  
  
 Die folgenden Bitmasken werden mit dem-Flag verwendet, um zu bestimmen, welche Optionen Lesezeichen beibehalten:  
  
 SQL_BP_CLOSE = Lesezeichen sind gültig, nachdem eine Anwendung **SQLFreeStmt** mit der SQL_CLOSE-Option oder **SQLCloseCursor** aufgerufen hat, um den mit einer Anweisung verknüpften Cursor zu schließen.  
  
 SQL_BP_DELETE = das Lesezeichen für eine Zeile ist gültig, nachdem diese Zeile gelöscht wurde.  
  
 SQL_BP_DROP = Lesezeichen sind gültig, nachdem eine Anwendung **SQLFreeHandle** mit dem *Handlertyp* SQL_HANDLE_STMT aufgerufen hat, um eine Anweisung zu löschen.  
  
 SQL_BP_TRANSACTION = Lesezeichen sind gültig, nachdem eine Anwendung einen Commit oder Rollback für eine Transaktion ausgeführt hat.  
  
 SQL_BP_UPDATE = das Lesezeichen für eine Zeile ist gültig, nachdem alle Spalten in dieser Zeile aktualisiert wurden, einschließlich Schlüssel Spalten.  
  
 SQL_BP_OTHER_HSTMT = ein Lesezeichen, das einer Anweisung zugeordnet ist, kann mit einer anderen Anweisung verwendet werden. Wenn SQL_BP_CLOSE oder SQL_BP_DROP nicht angegeben wird, muss der Cursor für die erste Anweisung geöffnet sein.  
  
 SQL_CATALOG_LOCATION (ODBC 2,0)  
 Ein sqlusmallint-Wert, der die Position des Katalogs in einem qualifizierten Tabellennamen angibt:  
  
 SQL_CL_STARTSQL_CL_END  
  
 Ein xbase-Treiber gibt z. b. SQL_CL_START zurück, da sich der Verzeichnisname (Katalog Name) am Anfang des Tabellennamens befindet, wie in \empdata\emp. DBF. Ein Oracle-Server Treiber gibt SQL_CL_END zurück, da sich der Katalog am Ende des Tabellennamens befindet, ADMIN.EMP@EMPDATAwie in.  
  
 Ein vollständig konformen SQL-92-Treiber gibt immer SQL_CL_START zurück. Der Wert 0 wird zurückgegeben, wenn Kataloge von der Datenquelle nicht unterstützt werden. Um zu ermitteln, ob Kataloge unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_CATALOG_NAME Informationstyp auf.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_QUALIFIER_LOCATION ODBC 2,0 umbenannt.  
  
 SQL_CATALOG_NAME (ODBC 3,0)  
 Eine Zeichenfolge: "Y", wenn der Server Katalognamen unterstützt, oder "N", wenn dies nicht der Fall ist.  
  
 Ein vollständig konformitäteter SQL-92-Treiber gibt immer "Y" zurück.  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1,0)  
 Eine Zeichenfolge: das Zeichen oder die Zeichen, die von der Datenquelle als Trennzeichen zwischen einem Katalognamen und dem qualifizierten Namenselement definiert werden, das folgt bzw. diesem vorangestellt ist.  
  
 Eine leere Zeichenfolge wird zurückgegeben, wenn Kataloge von der Datenquelle nicht unterstützt werden. Um zu ermitteln, ob Kataloge unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_CATALOG_NAME Informationstyp auf. Ein vollständig konformen SQL-92-Treiber gibt immer "." zurück.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_QUALIFIER_NAME_SEPARATOR ODBC 2,0 umbenannt.  
  
 SQL_CATALOG_TERM (ODBC 1,0)  
 Eine Zeichenfolge mit dem Namen des Datenquellen Herstellers für einen Katalog. Beispiel: "Database" oder "Directory". Diese Zeichenfolge kann groß, klein oder gemischt sein.  
  
 Eine leere Zeichenfolge wird zurückgegeben, wenn Kataloge von der Datenquelle nicht unterstützt werden. Um zu ermitteln, ob Kataloge unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_CATALOG_NAME Informationstyp auf. Ein vollständig konformitäteter SQL-92-Treiber gibt immer "catalog" zurück.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_QUALIFIER_TERM ODBC 2,0 umbenannt.  
  
 SQL_CATALOG_USAGE (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die die-Anweisungen auflistet, in denen Kataloge verwendet werden können.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, wo Kataloge verwendet werden können:  
  
 SQL_CU_DML_STATEMENTS = Kataloge werden in allen Anweisungen für die Daten Bearbeitungs Sprache unterstützt: **Select**, **Insert**, **Update**, **Delete**und falls unterstützt, **Wählen Sie für Update** -und positionierte UPDATE-und DELETE-Anweisungen aus.  
  
 SQL_CU_PROCEDURE_INVOCATION = Kataloge werden in der Anweisung "ODBC Procedure invoation" unterstützt.  
  
 SQL_CU_TABLE_DEFINITION = Kataloge werden in allen Tabellen Definitions Anweisungen unterstützt: **CREATE TABLE**, **CREATE VIEW**, **ALTER TABLE**, **DROP TABLE**und **Drop View**.  
  
 SQL_CU_INDEX_DEFINITION = Kataloge werden in allen Index Definitions Anweisungen unterstützt: **Create Index** und **Drop Index**.  
  
 SQL_CU_PRIVILEGE_DEFINITION = Kataloge werden in allen Berechtigungs Definitions Anweisungen unterstützt: **Grant** und **Widerruf**.  
  
 Der Wert 0 wird zurückgegeben, wenn Kataloge von der Datenquelle nicht unterstützt werden. Um zu ermitteln, ob Kataloge unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_CATALOG_NAME Informationstyp auf. Ein vollständig konformen SQL-92-Treiber gibt immer eine Bitmaske zurück, bei der alle diese Bits festgelegt sind.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_QUALIFIER_USAGE ODBC 2,0 umbenannt.  
  
 SQL_COLLATION_SEQ (ODBC 3,0)  
 Der Name der Sortierreihenfolge. Dies ist eine Zeichenfolge, die den Namen der Standardsortierung für den Standardzeichensatz für diesen Server angibt (z. b. "ISO 8859-1" oder EBCDIC). Wenn dies unbekannt ist, wird eine leere Zeichenfolge zurückgegeben. Ein vollständig konformen SQL-92-Treiber gibt immer eine nicht leere Zeichenfolge zurück.  
  
 SQL_COLUMN_ALIAS (ODBC 2,0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle Spalten Aliase unterstützt. andernfalls "N".  
  
 Ein Spaltenalias ist ein alternativer Name, der für eine Spalte in der Auswahlliste mit einer As-Klausel angegeben werden kann. Ein mit SQL-92 Entry Level-konformitäger Treiber gibt immer "Y" zurück.  
  
 SQL_CONCAT_NULL_BEHAVIOR (ODBC 1,0)  
 Ein sqlusmallint-Wert, der angibt, wie die Datenquelle die Verkettung von Spalten mit NULL-Wert-Zeichen Datentypen mit nicht-NULL-Zeichen Datentyp Spalten behandelt:  
  
 SQL_CB_NULL = Ergebnis ist NULL-Wert.  
  
 SQL_CB_NON_NULL = Ergebnis ist die Verkettung von nicht-NULL-Wert Spalten oder-Spalten.  
  
 Ein mit SQL-92 Entry Level-konformitäer Treibers gibt immer SQL_CB_NULL zurück.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1,0)  
 Eine SQLUINTEGER-Bitmaske. Die Bitmaske gibt die von der Datenquelle unterstützten Konvertierungen mit der **Convert** skalare-Funktion für Daten des Typs an, der im *InfoType*benannt ist. Wenn die Bitmaske gleich 0 (null) ist, unterstützt die Datenquelle keine Konvertierungen von Daten des benannten Typs, einschließlich der Konvertierung in denselben Datentyp.  
  
 Um z. b. zu ermitteln, ob eine Datenquelle die Konvertierung von SQL_INTEGER Daten in den SQL_BIGINT-Datentyp unterstützt, ruft eine Anwendung **SQLGetInfo** mit dem *InfoType* SQL_CONVERT_INTEGER auf. Die Anwendung führt eine **and-** Operation mit der zurückgegebenen Bitmaske und SQL_CVT_BIGINT aus. Wenn der resultierende Wert ungleich 0 (null) ist, wird die Konvertierung unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Konvertierungen unterstützt werden:  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) SQL_CVT_BIT (ODBC 1,0) SQL_CVT_GUID (ODBC 3.5) SQL_CVT_CHAR (ODBC 1,0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC) 1.0) SQL_CVT_FLOAT (ODBC 1.0) SQL_CVT_INTEGER (ODBC 1.0) SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 3.0) SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0) SQL_CVT_LONGVARBINARY (ODBC 1.0) SQL_CVT_LONGVARCHAR (ODBC 1.0) SQL_CVT_NUMERIC (ODBC 1.0) SQL_ CVT_REAL ODBC 1.0) SQL_CVT_SMALLINT (ODBC 1.0) SQL_CVT_TIME (ODBC 1.0) SQL_CVT_TIMESTAMP (ODBC 1.0) SQL_CVT_TINYINT (ODBC 1.0) SQL_CVT_VARBINARY (ODBC 1.0) SQL_CVT_VARCHAR (ODBC 1,0)  
  
 SQL_CONVERT_FUNCTIONS (ODBC 1,0)  
 Eine SQLUINTEGER-Bitmaske, die die vom Treiber und der zugeordneten Datenquelle unterstützten skalarkonvertierungs Funktionen auflistet.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Konvertierungs Funktionen unterstützt werden:  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1,0)  
 Ein sqlusmallint-Wert, der angibt, ob Tabellen Korrelations Namen unterstützt werden:  
  
 SQL_CN_NONE = Korrelations Namen werden nicht unterstützt.  
  
 SQL_CN_DIFFERENT = Korrelations Namen werden unterstützt, müssen sich jedoch von den Namen der Tabellen unterscheiden, die Sie darstellen.  
  
 SQL_CN_ANY = Korrelations Namen werden unterstützt und können ein beliebiger gültiger benutzerdefinierter Name sein.  
  
 Ein mit SQL-92 Entry Level-konformitäer Treibers gibt immer SQL_CN_ANY zurück.  
  
 SQL_CREATE_ASSERTION (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Create** Assert-Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CA_CREATE_ASSERTION  
  
 Die folgenden Bits geben das unterstützte Einschränkungs Attribut an, wenn die Möglichkeit zum expliziten Angeben von Einschränkungs Attributen unterstützt wird (siehe SQL_ALTER_TABLE-und SQL_CREATE_TABLE-Informationstypen):  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Ein vollständig konformen SQL-92-Treiber gibt immer alle diese Optionen zurück, die unterstützt werden. Der Rückgabewert "0" bedeutet, dass die **Create** Assert-Anweisung nicht unterstützt wird.  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Create Character Set** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Ein vollständig konformen SQL-92-Treiber gibt immer alle diese Optionen zurück, die unterstützt werden. Der Rückgabewert "0" bedeutet, dass die **Create Character Set** -Anweisung nicht unterstützt wird.  
  
 SQL_CREATE_COLLATION (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Create Collation** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Bei einem vollständig kompatiblen SQL-92-Treiber wird diese Option immer als unterstützt zurückgegeben. Der Rückgabewert "0" bedeutet, dass die **Create COLLATIONS** -Anweisung nicht unterstützt wird.  
  
 SQL_CREATE_DOMAIN (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Create Domain** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CDO_CREATE_DOMAIN = die CREATE DOMAIN-Anweisung wird unterstützt (Zwischenebene).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<Einschränkungs Name Definition> wird für Benennungs Domänen Einschränkungen (Zwischenebene) unterstützt.  
  
 Die folgenden Bits geben die Fähigkeit zum Erstellen von Spalten Einschränkungen an: SQL_CDO_DEFAULT = angeben von Domänen Einschränkungen wird unterstützt (Zwischenebene) SQL_CDO_CONSTRAINT = angeben von Domänen Standardwerten wird unterstützt (Zwischenebene) SQL_CDO_COLLATION = angeben der Domänen Sortierung wird unterstützt (vollständig)  
  
 Die folgenden Bits geben die unterstützten Einschränkungs Attribute an, wenn die Angabe von Domänen Einschränkungen unterstützt wird (SQL_CDO_DEFAULT festgelegt ist)  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (vollständig) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (vollständig) SQL_CDO_CONSTRAINT_DEFERRABLE (vollständig) SQL_CDO_CONSTRAINT_NON_DEFERRABLE (vollständig)  
  
 Der Rückgabewert "0" bedeutet, dass die **Create Domain** -Anweisung nicht unterstützt wird.  
  
 SQL_CREATE_SCHEMA (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Create Schema** -Anweisung auflistet, wie in SQL-92 definiert, von der Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 Ein SQL-92-Intermediate Level-konformitäter-Treiber gibt immer die SQL_CS_CREATE_SCHEMA-und SQL_CS_AUTHORIZATION Optionen zurück, die unterstützt werden. Diese müssen auch auf der SQL-92-Einstiegsebene unterstützt werden, jedoch nicht unbedingt als SQL-Anweisungen. Ein vollständig konformen SQL-92-Treiber gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_CREATE_TABLE (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE TABLE** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CT_CREATE_TABLE = die CREATE TABLE-Anweisung wird unterstützt. (Einstiegsebene)  
  
 SQL_CT_TABLE_CONSTRAINT = angeben von Tabellen Einschränkungen wird unterstützt (fps-Übergangs Ebene)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = die \<Einschränkungs Namen Definition>-Klausel wird für das Benennen von Spalten-und Tabellen Einschränkungen (Zwischenebene) unterstützt.  
  
 Die folgenden Bits geben an, wie temporäre Tabellen erstellt werden können:  
  
 SQL_CT_COMMIT_PRESERVE = gelöschte Zeilen werden bei Commit beibehalten. (Vollständig) SQL_CT_COMMIT_DELETE = gelöschte Zeilen werden bei Commit gelöscht. (Vollständig) SQL_CT_GLOBAL_TEMPORARY = globale temporäre Tabellen können erstellt werden. (Vollständig) SQL_CT_LOCAL_TEMPORARY = lokale temporäre Tabellen können erstellt werden. (Vollständig)  
  
 Die folgenden Bits geben die Fähigkeit an, Spalten Einschränkungen zu erstellen:  
  
 SQL_CT_COLUMN_CONSTRAINT = angeben von Spalten Einschränkungen wird unterstützt (fps-Übergangs Ebene) SQL_CT_COLUMN_DEFAULT = das Angeben von Spalten Standardwerten wird unterstützt (fps-Übergangs Ebene) SQL_CT_COLUMN_COLLATION = das Angeben der Spalten Sortierung wird unterstützt (vollständig)  
  
 In den folgenden Bits werden die unterstützten Einschränkungs Attribute angegeben, wenn Spalten-oder Tabellen Einschränkungen angegeben werden:  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (vollständig) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (vollständig) SQL_CT_CONSTRAINT_DEFERRABLE (vollständig) SQL_CT_CONSTRAINT_NON_DEFERRABLE (vollständig)  
  
 SQL_CREATE_TRANSLATION (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Create Translation** -Anweisung, wie in SQL-92 definiert, auflistet, die von der Datenquelle unterstützt wird.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Ein vollständig konformen SQL-92-Treiber gibt diese Optionen immer als unterstützt zurück. Der Rückgabewert "0" bedeutet, dass die **Create Translation** -Anweisung nicht unterstützt wird.  
  
 SQL_CREATE_VIEW (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **CREATE VIEW** -Anweisung, wie in SQL-92 definiert, auflistet, die von der Datenquelle unterstützt wird.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Der Rückgabewert "0" bedeutet, dass die **CREATE VIEW** -Anweisung nicht unterstützt wird.  
  
 Ein mit der SQL-92-Übereinstimmung übergebender Treiber gibt immer die SQL_CV_CREATE_VIEW-und SQL_CV_CHECK_OPTION Optionen zurück, die unterstützt werden.  
  
 Ein vollständig konformen SQL-92-Treiber gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1,0)  
 Ein sqlusmallint-Wert, der angibt, wie sich ein **Commitvorgang auf** Cursor und vorbereitete Anweisungen in der Datenquelle auswirkt (das Verhalten der Datenquelle, wenn Sie einen Commit für eine Transaktion durchsetzen).  
  
 Der Wert dieses Attributs gibt den aktuellen Status der nächsten Einstellung an: SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE = Cursor schließen und vorbereitete Anweisungen löschen. Um den Cursor erneut zu verwenden, muss die Anwendung die Anweisung erneut vorbereiten und erneut ausführen.  
  
 SQL_CB_CLOSE = schließen von Cursorn. Bei vorbereiteten Anweisungen kann die Anwendung **SQLExecute** für die Anweisung aufrufen, ohne dass **SQLPrepare** erneut aufgerufen wird. Der Standardwert für den SQL-ODBC-Treiber ist SQL_CB_CLOSE. Dies bedeutet, dass der SQL-ODBC-Treiber die Cursor schließt, wenn Sie einen Commit für eine Transaktion durchsetzen.  
  
 SQL_CB_PRESERVE = Cursor an derselben Position wie **vor dem** Commitvorgang beibehalten. Die Anwendung kann weiterhin Daten abrufen, oder Sie kann den Cursor schließen und die Anweisung erneut ausführen, ohne Sie erneut vorzubereiten.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1,0)  
 Ein sqlusmallint-Wert, der angibt, wie sich ein **Rollback** -Vorgang auf Cursor und vorbereitete Anweisungen in der Datenquelle auswirkt:  
  
 SQL_CB_DELETE = Cursor schließen und vorbereitete Anweisungen löschen. Um den Cursor erneut zu verwenden, muss die Anwendung die Anweisung erneut vorbereiten und erneut ausführen.  
  
 SQL_CB_CLOSE = schließen von Cursorn. Bei vorbereiteten Anweisungen kann die Anwendung **SQLExecute** für die Anweisung aufrufen, ohne dass **SQLPrepare** erneut aufgerufen wird.  
  
 SQL_CB_PRESERVE = Cursor an derselben Position wie vor dem **Rollback** -Vorgang beibehalten. Die Anwendung kann weiterhin Daten abrufen, oder Sie kann den Cursor schließen und die Anweisung erneut ausführen, ohne Sie erneut zu erstellen.  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3,0)  
 Ein SQLUINTEGER-Wert, der die Unterstützung der Cursor Sensitivität angibt:  
  
 SQL_INSENSITIVE = alle Cursor im Anweisungs Handle zeigen das Resultset an, ohne dass Änderungen reflektiert werden, die von einem anderen Cursor innerhalb derselben Transaktion vorgenommen wurden.  
  
 SQL_UNSPECIFIED = es ist nicht angegeben, ob Cursor im Anweisungs Handle die Änderungen sichtbar machen, die von einem anderen Cursor innerhalb derselben Transaktion an einem Resultset vorgenommen wurden. Cursor im Anweisungs Handle können sichtbar machen, dass keine, einige oder alle Änderungen sichtbar sind.  
  
 SQL_SENSITIVE = Cursor sind von Änderungen abhängig, die von anderen Cursorn innerhalb derselben Transaktion vorgenommen wurden.  
  
 Ein in SQL-92 Eintrags Level übergebender Treiber gibt die SQL_UNSPECIFIED Option immer wie unterstützt zurück.  
  
 Ein vollständig konformen SQL-92-Treiber gibt die SQL_INSENSITIVE-Option immer wie unterstützt zurück.  
  
 SQL_DATA_SOURCE_NAME (ODBC 1,0)  
 Eine Zeichenfolge mit dem Datenquellen Namen, der während der Verbindung verwendet wurde. Wenn die Anwendung **SQLCONNECT**heißt, ist dies der Wert des *szdsn* -Arguments. Wenn die Anwendung **SQLDriverConnect** oder **sqlbrowseconnetct**heißt, ist dies der Wert des DSN-Schlüssel Worts in der Verbindungs Zeichenfolge, die an den Treiber weitergeleitet wird. Wenn die Verbindungs Zeichenfolge das **DSN** -Schlüsselwort nicht enthielt (z. b. Wenn Sie das **Treiber** Schlüsselwort enthält), handelt es sich um eine leere Zeichenfolge.  
  
 SQL_DATA_SOURCE_READ_ONLY (ODBC 1,0)  
 Eine Zeichenfolge. "Y", wenn die Datenquelle auf den schreibgeschützten Modus festgelegt ist, andernfalls "N".  
  
 Diese Eigenschaft bezieht sich nur auf die Datenquelle selbst. Es ist kein Merkmal des Treibers, der den Zugriff auf die Datenquelle ermöglicht. Ein Lese-/Schreibzugriff kann mit einer Datenquelle verwendet werden, die schreibgeschützt ist. Wenn ein Treiber schreibgeschützt ist, müssen alle Datenquellen schreibgeschützt sein und müssen SQL_DATA_SOURCE_READ_ONLY zurückgeben.  
  
 SQL_DATABASE_NAME (ODBC 1,0)  
 Eine Zeichenfolge mit dem Namen der aktuellen Datenbank, die verwendet wird, wenn die Datenquelle ein benanntes Objekt mit dem Namen "Database" definiert.  
  
> [!NOTE]
>  In ODBC 3 *. x*kann der Wert, der für diesen *InfoType* zurückgegeben wird, auch durch Aufrufen von **SQLGetConnectAttr** mit dem *Attribut* Argument SQL_ATTR_CURRENT_CATALOG zurückgegeben werden.  
  
 SQL_DATETIME_LITERALS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die SQL-92 datetime-Literale auflistet, die von der Datenquelle unterstützt werden. Beachten Sie, dass es sich hierbei um die in der SQL-92-Spezifikation aufgelisteten datetime-Literale handelt, die von ODBC definierte DateTime-literalescapeklauseln getrennt sind. Weitere Informationen zu den ODBC DateTime-literalescapeklauseln finden Sie unter [Datums-, Uhrzeit-und Timestamp-Literale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Ein mit der Anwendung übereinstellender PPS-Operator gibt immer den Wert "1" in der Bitmaske für die Bits in der folgenden Liste zurück. Der Wert "0" bedeutet, dass SQL-92 datetime-Literale nicht unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Literale unterstützt werden:  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME (ODBC 1,0)  
 Eine Zeichenfolge mit dem Namen des DBMS-Produkts, auf das der Treiber zugreift.  
  
 SQL_DBMS_VER (ODBC 1,0)  
 Eine Zeichenfolge, die die Version des DBMS-Produkts angibt, auf das der Treiber zugreift. Die Version hat das Format # #. # #. # # # #, wobei die ersten beiden Ziffern die Hauptversion sind, die nächsten zwei Ziffern die neben Version sind und die letzten vier Ziffern die Releaseversion sind. Der Treiber muss die DBMS-Produktversion in diesem Formular darstellen, kann jedoch auch die produktspezifische DBMS-Version anfügen. Beispiel: "04.01.0000 RDB 4,1".  
  
 SQL_DDL_INDEX (ODBC 3,0)  
 Ein SQLUINTEGER-Wert, der die Unterstützung für das Erstellen und Löschen von Indizes angibt:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION (ODBC 1,0)  
 Ein SQLUINTEGER-Wert, der die vom Treiber oder der Datenquelle unterstützte Standard Transaktions Isolationsstufe angibt, oder 0 (null), wenn die Datenquelle keine Transaktionen unterstützt. Die folgenden Begriffe werden verwendet, um Transaktions Isolations Stufen zu definieren:  
  
 **Dirty Read** Transaktion 1 ändert eine Zeile. Transaktion 2 liest die geänderte Zeile, bevor Transaktion 1 einen Commit für die Änderung ausführt. Wenn Transaktion 1 ein Rollback der Änderung ausführt, hat Transaction 2 eine Zeile gelesen, die als nie vorhanden angesehen wird.  
  
 **Nicht wiederholbarer Lese** Vorgang Transaktion 1 liest eine Zeile. Transaktion 2 aktualisiert oder löscht diese Zeile und führt einen Commit für diese Änderung aus. Wenn Transaktion 1 versucht, die Zeile erneut zu lesen, empfängt Sie andere Zeilen Werte oder ermittelt, dass die Zeile gelöscht wurde.  
  
 **Phantom** Transaktion 1 liest eine Reihe von Zeilen, die einige Suchkriterien erfüllen. Transaktion 2 generiert eine oder mehrere Zeilen (entweder über Einfügungen oder Updates), die den Suchkriterien entsprechen. Wenn Transaktion 1 die Anweisung, die die Zeilen liest, erneut ausführt, empfängt Sie einen anderen Satz von Zeilen.  
  
 Wenn die Datenquelle Transaktionen unterstützt, gibt der Treiber eine der folgenden Bitmasks zurück:  
  
 SQL_TXN_READ_UNCOMMITTED = Dirty Reads, nicht wiederholbare Lesevorgänge und Phantome sind möglich.  
  
 SQL_TXN_READ_COMMITTED = Dirty Reads sind nicht möglich. Nicht wiederholbare Lesevorgänge und Phantome sind möglich.  
  
 SQL_TXN_REPEATABLE_READ = Dirty Reads und nicht wiederholbare Lesevorgänge sind nicht möglich. Phantome sind möglich.  
  
 SQL_TXN_SERIALIZABLE = Transaktionen sind serialisierbar. Serialisierbare Transaktionen lassen keine Dirty Reads, nicht wiederholbare Lesevorgänge oder Phantome zu.  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3,0)  
 Eine Zeichenfolge: "Y", wenn Parameter beschrieben werden können. "N", falls nicht.  
  
 Ein vollständig konformitäteter SQL-92-Treiber gibt normalerweise "Y" zurück, da er die **Beschreibung der Eingabe** Anweisung unterstützt. Da dies die zugrunde liegende SQL-Unterstützung nicht direkt angibt, wird das Beschreiben von Parametern möglicherweise nicht unterstützt, auch in einem vollständig kompatiblen SQL-92-Treiber.  
  
 SQL_DM_VER (ODBC 3,0)  
 Eine Zeichenfolge mit der Version des Treiber-Managers. Die Version hat das Format # #. # #. # # # #. # # # #, wobei:  
  
 Der erste Satz von zwei Ziffern ist die Hauptversion von ODBC, wie vom Konstanten SQL_SPEC_MAJOR angegeben.  
  
 Der zweite Satz von zwei Ziffern ist die kleinere ODBC-Version, die vom Konstanten SQL_SPEC_MINOR angegeben wird.  
  
 Der dritte Satz von vier Ziffern ist die Hauptbuildnummer des Treiber-Managers.  
  
 Der letzte Satz von vier Ziffern ist die untergeordnete Buildnummer des Treiber-Managers.  
  
 Die Version des Windows 7-Treiber-Managers ist 03,80. Windows 8 Driver Manager Version ist 03,81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3,8)  
 Ein SQLUINTEGER-Wert, der angibt, ob der Treiber Treiber fähiges Pooling unterstützt. (Weitere Informationen finden Sie unter [Treiber fähiges Verbindungs Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE gibt an, dass der Treiber den Treiber fähigen Pooling-Mechanismus unterstützen kann.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE gibt an, dass der Treiber den Treiber fähigen Pooling-Mechanismus nicht unterstützen kann.  
  
 Ein Treiber muss SQL_DRIVER_AWARE_POOLING_SUPPORTED nicht implementieren, und der Treiber-Manager berücksichtigt nicht den Rückgabewert des Treibers.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1,0)  
 Ein SQLULEN-Wert, das Umgebungs Handle oder Verbindungs Handle des Treibers, der durch das-Argument *InfoType*bestimmt wird.  
  
 Diese Informationstypen werden allein vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_HDESC (ODBC 3,0)  
 Ein SQLULEN-Wert, der vom Deskriptorhandle des Treiber-Managers festgelegte Deskriptorhandle des Treibers, das von der Anwendung \*in *infovalueptr* eingegeben werden muss. In diesem Fall ist *infovalueptr* ein Eingabe-und ein Ausgabe Argument. Das an \* *infovalueptr* weiter gegebene Eingabe Deskriptorhandle muss dem *connectionHandle*entweder explizit oder implizit zugeordnet worden sein.  
  
 Die Anwendung sollte eine Kopie des Deskriptorhandles des Treiber-Managers erstellen, bevor **SQLGetInfo** mit diesem Informationstyp aufgerufen wird, um sicherzustellen, dass das Handle bei der Ausgabe nicht überschrieben wird.  
  
 Dieser Informationstyp wird nur vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_HLIB (ODBC 2,0)  
 Ein SQLULEN-Wert, der *hInst* aus der Load-Bibliothek, der beim Laden der Treiber-DLL auf einem Microsoft Windows-Betriebssystem oder einem anderen Betriebssystem an den Treiber-Manager zurückgegeben wurde. Das Handle ist nur für das beim Aufrufen von **SQLGetInfo**angegebene Verbindungs Handle gültig.  
  
 Dieser Informationstyp wird nur vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_HSTMT (ODBC 1,0)  
 Ein SQLULEN-Wert, der vom Treiber-Manager-Anweisungs Handle festgelegte Anweisungs Handle des Treibers, das \*von der Anwendung in *infovalueptr* eingegeben werden muss. In diesem Fall ist *infovalueptr* sowohl ein Eingabe-als auch ein Output-Argument. Das an \* *infovalueptr* weiter gegebene Eingabe Anweisungs Handle muss dem Argument *connectionHandle*zugeordnet worden sein.  
  
 Die Anwendung sollte eine Kopie des Anweisungs Handles des Treiber-Managers erstellen, bevor **SQLGetInfo** mit diesem Informationstyp aufgerufen wird, um sicherzustellen, dass das Handle bei der Ausgabe nicht überschrieben wird.  
  
 Dieser Informationstyp wird nur vom Treiber-Manager implementiert.  
  
 SQL_DRIVER_NAME (ODBC 1,0)  
 Eine Zeichenfolge mit dem Dateinamen des Treibers, der für den Zugriff auf die Datenquelle verwendet wird.  
  
 SQL_DRIVER_ODBC_VER (ODBC 2,0)  
 Eine Zeichenfolge mit der Version von ODBC, die der Treiber unterstützt. Die Version hat das Format # #. # #, wobei die ersten beiden Ziffern die Hauptversion und die nächsten zwei Ziffern die neben Version sind. SQL_SPEC_MAJOR und SQL_SPEC_MINOR definieren die Haupt-und neben Versionsnummern. Bei der in diesem Handbuch beschriebenen Version von ODBC sind diese 3 und 0, und der Treiber sollte "03,00" zurückgeben.  
  
 Der ODBC-Treiber-Manager ändert den Rückgabewert von SQLGetInfo (SQL_DRIVER_ODBC_VER) nicht, um die Abwärtskompatibilität für vorhandene Anwendungen aufrechtzuerhalten. Der Treiber gibt an, welcher Wert zurückgegeben wird. Ein Treiber, der die Erweiterbarkeit des C-Datentyps unterstützt, muss jedoch 3,8 (oder höher) zurückgeben, wenn eine Anwendung **SQLSetEnvAttr** aufruft, um SQL_ATTR_ODBC_VERSION auf 3,8 festzulegen. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER (ODBC 1,0)  
 Eine Zeichenfolge mit der Version des Treibers und optional eine Beschreibung des Treibers. Die Version hat mindestens das Format # #. # #. # # # #, wobei die ersten beiden Ziffern die Hauptversion sind, die nächsten zwei Ziffern die neben Version sind und die letzten vier Ziffern die Releaseversion sind.  
  
 SQL_DROP_ASSERTION (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Drop** Assert-Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DA_DROP_ASSERTION  
  
 Bei einem vollständig kompatiblen SQL-92-Treiber wird diese Option immer als unterstützt zurückgegeben.  
  
 SQL_DROP_CHARACTER_SET (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Drop Character Set** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Bei einem vollständig kompatiblen SQL-92-Treiber wird diese Option immer als unterstützt zurückgegeben.  
  
 SQL_DROP_COLLATION (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Drop Collation** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DC_DROP_COLLATION  
  
 Bei einem vollständig kompatiblen SQL-92-Treiber wird diese Option immer als unterstützt zurückgegeben.  
  
 SQL_DROP_DOMAIN (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Drop Domain** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 Ein SQL-92-Intermediate Level-konformitäter-Treiber gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_DROP_SCHEMA (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Drop Schema** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 Ein SQL-92-Intermediate Level-konformitäter-Treiber gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_DROP_TABLE (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **DROP TABLE** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Ein mit der Anwendung für die Übergangs Ebene übergebender PPS gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_DROP_TRANSLATION (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Drop Translation** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Bei einem vollständig kompatiblen SQL-92-Treiber wird diese Option immer als unterstützt zurückgegeben.  
  
 SQL_DROP_VIEW (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Drop View** -Anweisung auflistet, wie in SQL-92 definiert, von der Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Ein mit der Anwendung für die Übergangs Ebene übergebender PPS gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines dynamischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die erste Teilmenge von Attributen. die zweite Teilmenge finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXT = ein *FetchOrientation* -Argument von SQL_FETCH_NEXT wird in einem Befehl von **SQLFetchScroll** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_ABSOLUTE = *FetchOrientation* -Argumente von SQL_FETCH_FIRST, SQL_FETCH_LAST und SQL_FETCH_ABSOLUTE werden bei einem-Befehl von **SQLFetchScroll** unterstützt, wenn der Cursor ein dynamischer Cursor ist. (Das Rowset, das abgerufen wird, ist unabhängig von der aktuellen Cursorposition.)  
  
 SQL_CA1_RELATIVE = *FetchOrientation* -Argumente von SQL_FETCH_PRIOR und SQL_FETCH_RELATIVE werden bei einem-Befehl von **SQLFetchScroll** unterstützt, wenn der Cursor ein dynamischer Cursor ist. (Das Rowset, das abgerufen wird, hängt von der aktuellen Cursorposition ab. Beachten Sie, dass dies von SQL_FETCH_NEXT getrennt ist, da in einem Vorwärts Cursor nur SQL_FETCH_NEXT unterstützt wird.)  
  
 SQL_CA1_BOOKMARK = ein *FetchOrientation* -Argument von SQL_FETCH_BOOKMARK wird in einem Befehl von **SQLFetchScroll** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_LOCK_EXCLUSIVE = ein *LockType* -Argument von SQL_LOCK_EXCLUSIVE wird in einem-Befehl von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_LOCK_NO_CHANGE = ein *LockType* -Argument von SQL_LOCK_NO_CHANGE wird in einem-Befehl von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_LOCK_UNLOCK = ein *LockType* -Argument von SQL_LOCK_UNLOCK wird in einem-Befehl von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POS_POSITION = ein *Vorgangs* Argument SQL_POSITION wird in einem Aufrufen von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POS_UPDATE = ein *Vorgangs* Argument SQL_UPDATE wird in einem Aufrufen von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POS_DELETE = ein *Vorgangs* Argument SQL_DELETE wird in einem Aufrufen von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POS_REFRESH = ein *Vorgangs* Argument SQL_REFRESH wird in einem Aufrufen von **SQLSetPos** unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_POSITIONED_UPDATE = ein Update, bei dem die Current of SQL-Anweisung unterstützt wird, wenn der Cursor ein dynamischer Cursor ist. (Ein SQL-92 Entry Level-konformitäter Treiber gibt diese Option immer als unterstützt zurück.)  
  
 SQL_CA1_POSITIONED_DELETE = eine DELETE WHERE CURRENT of SQL-Anweisung wird unterstützt, wenn der Cursor ein dynamischer Cursor ist. (Ein SQL-92 Entry Level-konformitäter Treiber gibt diese Option immer als unterstützt zurück.)  
  
 SQL_CA1_SELECT_FOR_UPDATE = eine SELECT for Update-SQL-Anweisung wird unterstützt, wenn der Cursor ein dynamischer Cursor ist. (Ein SQL-92 Entry Level-konformitäter Treiber gibt diese Option immer als unterstützt zurück.)  
  
 SQL_CA1_BULK_ADD = ein *Vorgangs* Argument SQL_ADD wird in einem **SQLBulkOperations** -Befehl unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = ein *Vorgangs* Argument SQL_UPDATE_BY_BOOKMARK wird in einem **SQLBulkOperations** -Befehl unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = ein *Vorgangs* Argument SQL_DELETE_BY_BOOKMARK wird in einem **SQLBulkOperations** -Befehl unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = ein *Vorgangs* Argument SQL_FETCH_BY_BOOKMARK wird in einem **SQLBulkOperations** -Befehl unterstützt, wenn der Cursor ein dynamischer Cursor ist.  
  
 Ein mit SQL-92 zwischenebenenkonformen Treiber gibt in der Regel die Optionen SQL_CA1_NEXT, SQL_CA1_ABSOLUTE und SQL_CA1_RELATIVE als unterstützt zurück, da er scrollbare Cursor durch die eingebettete SQL-FETCH-Anweisung unterstützt. Da dadurch die zugrunde liegende SQL-Unterstützung nicht direkt bestimmt wird, werden scrollfähige Cursor möglicherweise nicht unterstützt, auch für einen zwischengeschalteten SQL-92-untergeordneten Treiber.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines dynamischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die zweite Teilmenge von Attributen. die erste Teilmenge finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = ein Schreib geschützter dynamischer Cursor, bei dem keine Updates zulässig sind, wird unterstützt. (Das SQL_ATTR_CONCURRENCY Statement-Attribut kann für einen dynamischen Cursor SQL_CONCUR_READ_ONLY werden).  
  
 SQL_CA2_LOCK_CONCURRENCY = ein dynamischer Cursor, der die niedrigste Sperr Ebene verwendet, um sicherzustellen, dass die Zeile aktualisiert werden kann, wird unterstützt. (Das SQL_ATTR_CONCURRENCY Statement-Attribut kann für einen dynamischen Cursor SQL_CONCUR_LOCK werden.) Diese Sperren müssen mit der Transaktions Isolationsstufe übereinstimmen, die vom SQL_ATTR_TXN_ISOLATION-Verbindungs Attribut festgelegt wird.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = ein dynamischer Cursor, der das Steuerelement für die vollständige Parallelität verwendet, bei dem die Zeilen Versionen verglichen werden (Das SQL_ATTR_CONCURRENCY Statement-Attribut kann für einen dynamischen Cursor SQL_CONCUR_ROWVER werden.)  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = ein dynamischer Cursor, der den Vergleich von Werten mit optimistischer Parallelität verwendet, wird unterstützt. (Das SQL_ATTR_CONCURRENCY Statement-Attribut kann für einen dynamischen Cursor SQL_CONCUR_VALUES werden.)  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = hinzugefügte Zeilen sind für einen dynamischen Cursor sichtbar. der Cursor kann einen Bildlauf zu diesen Zeilen durchführen. (Wobei diese Zeilen dem Cursor hinzugefügt werden, ist Treiber abhängig.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS = gelöschte Zeilen sind nicht mehr für einen dynamischen Cursor verfügbar und lassen kein "Loch" im Resultset aus. Nachdem der dynamische Cursor einen Bildlauf aus einer gelöschten Zeile durchgeführt hat, kann er nicht zu dieser Zeile zurückkehren  
  
 SQL_CA2_SENSITIVITY_UPDATES = Aktualisierungen von Zeilen sind für einen dynamischen Cursor sichtbar. Wenn der dynamische Cursor einen Bildlauf durchführt und zu einer aktualisierten Zeile zurückkehrt, sind die vom Cursor zurückgegebenen Daten die aktualisierten Daten, nicht die ursprünglichen Daten.  
  
 SQL_CA2_MAX_ROWS_SELECT = das Attribut der SQL_ATTR_MAX_ROWS Anweisung wirkt sich auf **Select** -Anweisungen aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_INSERT = das Attribut der SQL_ATTR_MAX_ROWS Anweisung wirkt sich auf **Insert** -Anweisungen aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_DELETE = das Attribut der SQL_ATTR_MAX_ROWS Anweisung wirkt sich auf **Delete** -Anweisungen aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_UPDATE = das Attribut der SQL_ATTR_MAX_ROWS Anweisung wirkt sich auf **Update** -Anweisungen aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_CATALOG = das Attribut der SQL_ATTR_MAX_ROWS Anweisung wirkt sich auf die **Katalog** Resultsets aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = das Attribut der SQL_ATTR_MAX_ROWS Anweisung wirkt sich auf **Select**-, **Insert**-, **Delete**-und **Update** -Anweisungen sowie auf **Katalog** Resultsets aus, wenn der Cursor ein dynamischer Cursor ist.  
  
 SQL_CA2_CRC_EXACT = die genaue Zeilen Anzahl ist im SQL_DIAG_CURSOR_ROW_COUNT Diagnose Feld verfügbar, wenn es sich um einen dynamischen Cursor handelt.  
  
 SQL_CA2_CRC_APPROXIMATE = eine ungefähre Zeilen Anzahl ist im SQL_DIAG_CURSOR_ROW_COUNT Diagnose Feld verfügbar, wenn es sich um einen dynamischen Cursor handelt.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = der Treiber garantiert nicht, dass simulierte positionierte UPDATE-oder DELETE-Anweisungen nur eine Zeile betreffen, wenn der Cursor ein dynamischer Cursor ist. Es liegt in der Verantwortung der Anwendung, dies zu gewährleisten. (Wenn eine-Anweisung mehr als eine Zeile betrifft, gibt **SQLExecute** oder **SQLExecDirect** SQLSTATE 01001 [Cursor Vorgangs Konflikt] zurück.) Um dieses Verhalten festzulegen, ruft die Anwendung **SQLSetStmtAttr** auf, wobei das SQL_ATTR_SIMULATE_CURSOR-Attribut auf SQL_SC_NON_UNIQUE festgelegt ist.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = der Treiber versucht sicherzustellen, dass sich simulierte positionierte UPDATE-oder DELETE-Anweisungen nur auf eine Zeile auswirken, wenn der Cursor ein dynamischer Cursor ist. Der Treiber führt diese Anweisungen immer aus, auch wenn Sie sich auf mehr als eine Zeile auswirken können, z. b. Wenn kein eindeutiger Schlüssel vorhanden ist. (Wenn eine-Anweisung mehr als eine Zeile betrifft, gibt **SQLExecute** oder **SQLExecDirect** SQLSTATE 01001 [Cursor Vorgangs Konflikt] zurück.) Um dieses Verhalten festzulegen, ruft die Anwendung **SQLSetStmtAttr** auf, wobei das SQL_ATTR_SIMULATE_CURSOR-Attribut auf SQL_SC_TRY_UNIQUE festgelegt ist.  
  
 SQL_CA2_SIMULATE_UNIQUE = der Treiber gewährleistet, dass sich simulierte positionierte UPDATE-oder DELETE-Anweisungen nur auf eine Zeile auswirken, wenn der Cursor ein dynamischer Cursor ist. Wenn der Treiber dies für eine bestimmte Anweisung nicht garantieren kann, geben **SQLExecDirect** oder **SQLPrepare** SQLSTATE 01001 (Cursor Vorgangs Konflikt) zurück. Um dieses Verhalten festzulegen, ruft die Anwendung **SQLSetStmtAttr** auf, wobei das SQL_ATTR_SIMULATE_CURSOR-Attribut auf SQL_SC_UNIQUE festgelegt ist.  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1,0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle Ausdrücke in der **Order by** -Liste unterstützt. "N", wenn dies nicht der Fall ist.  
  
 SQL_FILE_USAGE (ODBC 2,0)  
 Ein sqlusmallint-Wert, der angibt, wie ein Single-Tier-Treiberdateien in einer Datenquelle direkt behandelt:  
  
 SQL_FILE_NOT_SUPPORTED = der Treiber ist kein Single-Tier-Treiber. Ein Oracle-Treiber ist beispielsweise ein Treiber mit zwei Ebenen.  
  
 SQL_FILE_TABLE = ein Single-Tier-Treiber behandelt Dateien in einer Datenquelle als Tabellen. Ein xbase-Treiber behandelt z. b. die einzelnen xbase-Dateien als Tabelle.  
  
 SQL_FILE_CATALOG = ein Single-Tier-Treiber behandelt Dateien in einer Datenquelle als Katalog. Beispielsweise behandelt ein Microsoft Access-Treiber jede Microsoft Access-Datei als eine komplette Datenbank.  
  
 Diese kann von einer Anwendung verwendet werden, um zu bestimmen, wie Benutzerdaten auswählen. Xbase-Benutzer betrachten beispielsweise häufig Daten, die in Dateien gespeichert sind, während Oracle-und Microsoft Access-Benutzer in der Regel Daten als in Tabellen gespeicherten Daten betrachten.  
  
 Wenn ein Benutzer eine xbase-Datenquelle auswählt, kann die Anwendung das Dialogfeld "Windows- **Datei öffnen** (allgemein)" anzeigen. Wenn der Benutzer eine Microsoft Access-oder Oracle-Datenquelle auswählt, kann die Anwendung ein benutzerdefiniertes Dialogfeld **Tabelle auswählen** anzeigen.  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines vorwärts Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die erste Teilmenge von Attributen. die zweite Teilmenge finden Sie unter SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Beschreibungen dieser Bitmasks finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und Ersetzen des vorwärts Cursors für "Dynamic Cursor" in den Beschreibungen).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines vorwärts Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die zweite Teilmenge von Attributen. die erste Teilmenge finden Sie unter SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Beschreibungen dieser Bitmasks finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (und Ersetzen des vorwärts Cursors für "Dynamic Cursor" in den Beschreibungen).  
  
 SQL_GETDATA_EXTENSIONS (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die Erweiterungen für **SQLGetData**auflistet.  
  
 Die folgenden Bitmasken werden gemeinsam mit dem-Flag verwendet, um zu bestimmen, welche allgemeinen Erweiterungen der Treiber für **SQLGetData**unterstützt:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData** kann für jede nicht gebundene Spalte aufgerufen werden, einschließlich derjenigen vor der letzten gebundenen Spalte. Beachten Sie, dass die Spalten in Reihenfolge der aufsteigenden Spaltennummer aufgerufen werden müssen, es sei denn, SQL_GD_ANY_ORDER ebenfalls zurückgegeben wird  
  
 SQL_GD_ANY_ORDER = **SQLGetData** kann für ungebundene Spalten in beliebiger Reihenfolge aufgerufen werden. Beachten Sie, dass **SQLGetData** nur für Spalten nach der letzten gebundenen Spalte aufgerufen werden kann, es sei denn, SQL_GD_ANY_COLUMN wird ebenfalls zurückgegeben.  
  
 SQL_GD_BLOCK = **SQLGetData** kann für eine ungebundene Spalte in einer Zeile in einem-Block (in der die Rowsetgröße größer als 1 ist) von Daten nach der Positionierung in dieser Zeile mit **SQLSetPos**aufgerufen werden.  
  
 SQL_GD_BOUND = **SQLGetData** kann nicht nur für ungebundene Spalten, sondern auch für gebundene Spalten aufgerufen werden. Ein Treiber kann diesen Wert nur zurückgeben, wenn er auch SQL_GD_ANY_COLUMN zurückgibt.  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData** kann aufgerufen werden, um Ausgabeparameter Werte zurückzugeben. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** ist erforderlich, um nur Daten aus ungebundenen Spalten zurückzugeben, die nach der letzten gebundenen Spalte auftreten, in der Reihenfolge der zunehmenden Spaltennummer aufgerufen werden und sich nicht in einer Zeile in einem Zeilen Block befinden.  
  
 Wenn ein Treiber Lesezeichen (mit fester oder variabler Länge) unterstützt, muss er das Aufrufen von **SQLGetData** für Spalte 0 unterstützen. Diese Unterstützung ist unabhängig davon erforderlich, was der Treiber für einen **SQLGetInfo-Befehl** mit dem SQL_GETDATA_EXTENSIONS *InfoType*zurückgibt.  
  
 SQL_GROUP_BY (ODBC 2,0)  
 Ein sqlusmallint-Wert, der die Beziehung zwischen den Spalten in der **Group by** -Klausel und den nicht aggregierten Spalten in der SELECT-Liste angibt:  
  
 SQL_GB_COLLATE = eine **COLLATE** -Klausel kann am Ende jeder Gruppierungs Spalte angegeben werden. (ODBC 3,0)  
  
 SQL_GB_NOT_SUPPORTED = **Group by** -Klauseln werden nicht unterstützt. (ODBC 2,0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = die **Group by** -Klausel muss alle nicht aggregierten Spalten in der SELECT-Liste enthalten. Er darf keine anderen Spalten enthalten. Wählen Sie z. b. die Option "out" **, "Max (Gehalt)" von Employee Group by de aus**. (ODBC 2,0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = die **Group by** -Klausel muss alle nicht aggregierten Spalten in der SELECT-Liste enthalten. Sie kann Spalten enthalten, die nicht in der SELECT-Liste enthalten sind. Wählen Sie z. b. die Option " **de", "Max (Gehalt)" aus Employee Group by de, Age aus**. (ODBC 2,0)  
  
 SQL_GB_NO_RELATION = die Spalten in der **Group by** -Klausel und die SELECT-Liste sind nicht verknüpft. Die Bedeutung von nicht gruppierten, nicht aggregierten Spalten in der SELECT-Liste ist Datenquellen abhängig. Wählen Sie z. b. die Option " **de", "Gehalt von Employee Group by de", "Age**" (ODBC 2,0)  
  
 Ein in SQL-92 Eintrags Level übergebender Treiber gibt die SQL_GB_GROUP_BY_EQUALS_SELECT Option immer wie unterstützt zurück. Ein vollständig konformen SQL-92-Treiber gibt die SQL_GB_COLLATE-Option immer wie unterstützt zurück. Wenn keine der Optionen unterstützt wird, wird die **Group by** -Klausel von der Datenquelle nicht unterstützt.  
  
 SQL_IDENTIFIER_CASE (ODBC 1,0)  
 Einen sqlusmallint-Wert wie folgt:  
  
 Bei SQL_IC_UPPER =-Bezeichner in SQL wird die Groß-/Kleinschreibung nicht beachtet, und Sie werden in Großbuchstaben im System Katalog gespeichert.  
  
 Bei SQL_IC_LOWER =-Bezeichner in SQL wird die Groß-/Kleinschreibung nicht beachtet und in Kleinbuchstaben im System Katalog gespeichert.  
  
 Bei SQL_IC_SENSITIVE = Bezeichner in SQL wird die Groß-/Kleinschreibung beachtet und in einem gemischten Fall im System Katalog gespeichert.  
  
 Bei SQL_IC_MIXED = Bezeichner in SQL wird die Groß-/Kleinschreibung nicht beachtet, und Sie werden in einem gemischten Fall im System Katalog gespeichert.  
  
 Da bei bezeichgern in SQL-92 die Groß-/Kleinschreibung nicht beachtet wird, gibt ein Treiber, der genau SQL-92 (Any Level) entspricht, niemals die SQL_IC_SENSITIVE-Option wie unterstützt zurück.  
  
 SQL_IDENTIFIER_QUOTE_CHAR (ODBC 1,0)  
 Die Zeichenfolge, die als Anfangs-und endtrennzeichen eines Bezeichners in Anführungszeichen (getrennt) in SQL-Anweisungen verwendet wird. (Bezeichner, die als Argumente an ODBC-Funktionen übermittelt wurden, müssen nicht in Anführungszeichen gesetzt werden.) Wenn die Datenquelle keine Bezeichner in Anführungszeichen unterstützt, wird eine leere zurückgegeben.  
  
 Diese Zeichenfolge kann auch zum Zitieren von Katalog Funktions Argumenten verwendet werden, wenn das Verbindungs Attribut SQL_ATTR_METADATA_ID auf SQL_TRUE festgelegt ist.  
  
 Da es sich bei dem bezeichneranführungs Zeichen in SQL-92 um das doppelte Anführungszeichen (") handelt, gibt ein Treiber, der genau SQL-92 entspricht, immer das doppelte Anführungszeichen zurück.  
  
 SQL_INDEX_KEYWORDS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die Schlüsselwörter in der CREATE INDEX-Anweisung auflistet, die vom Treiber unterstützt werden:  
  
 SQL_IK_NONE = keines der Schlüsselwörter wird unterstützt.  
  
 SQL_IK_ASC = ASC-Schlüsselwort wird unterstützt.  
  
 SQL_IK_DESC = DESC-Schlüsselwort wird unterstützt.  
  
 SQL_IK_ALL = Alle Schlüsselwörter werden unterstützt.  
  
 Um festzustellen, ob die CREATE INDEX-Anweisung unterstützt wird, ruft eine Anwendung **SQLGetInfo** mit dem SQL_DLL_INDEX Informationstyp auf.  
  
 SQL_INFO_SCHEMA_VIEWS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Sichten in den INFORMATION_SCHEMA auflistet, die vom Treiber unterstützt werden. Die Sichten in und der Inhalt von INFORMATION_SCHEMA sind wie in SQL-92 definiert.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Sichten unterstützt werden:  
  
 SQL_ISV_ASSERTIONS = identifiziert die Assertionen des Katalogs, die sich im Besitz eines bestimmten Benutzers befinden. (Vollständig)  
  
 SQL_ISV_CHARACTER_SETS = identifiziert die Zeichensätze des Katalogs, auf die ein bestimmter Benutzer zugreifen kann. (Zwischenebene)  
  
 SQL_ISV_CHECK_CONSTRAINTS = identifiziert die Check-Einschränkungen, die sich im Besitz eines bestimmten Benutzers befinden. (Zwischenebene)  
  
 SQL_ISV_COLLATIONS = identifiziert die Zeichen Sortierungen für den Katalog, auf die ein bestimmter Benutzer zugreifen kann. (Vollständig)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = identifiziert die Spalten für den Katalog, die von den im Katalog definierten Domänen abhängen und im Besitz eines bestimmten Benutzers sind. (Zwischenebene)  
  
 SQL_ISV_COLUMN_PRIVILEGES = identifiziert die Berechtigungen für Spalten von permanenten Tabellen, die für einen bestimmten Benutzer verfügbar sind oder von diesem erteilt wurden. (Übergangs Ebene für den PPS)  
  
 SQL_ISV_COLUMNS = identifiziert die Spalten von permanenten Tabellen, auf die ein bestimmter Benutzer zugreifen kann. (Übergangs Ebene für den PPS)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = ähnlich wie Constraint_Table_Usage Sicht werden Spalten für die verschiedenen Einschränkungen identifiziert, die einem bestimmten Benutzer gehören. (Zwischenebene)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = identifiziert die Tabellen, die von Einschränkungen (referenziell, eindeutig und Assertionen) verwendet werden und im Besitz eines bestimmten Benutzers sind. (Zwischenebene)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = identifiziert die Domänen Einschränkungen (der Domänen im Katalog), auf die ein bestimmter Benutzer zugreifen kann. (Zwischenebene)  
  
 SQL_ISV_DOMAINS = identifiziert die Domänen, die in einem Katalog definiert sind und auf die der Benutzer zugreifen kann. (Zwischenebene)  
  
 SQL_ISV_KEY_COLUMN_USAGE = identifiziert die im Katalog definierten Spalten, die von einem bestimmten Benutzer als Schlüssel eingeschränkt werden. (Zwischenebene)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = identifiziert die referenziellen Einschränkungen, die sich im Besitz eines bestimmten Benutzers befinden. (Zwischenebene)  
  
 SQL_ISV_SCHEMATA = identifiziert die Schemas, die sich im Besitz eines bestimmten Benutzers befinden. (Zwischenebene)  
  
 SQL_ISV_SQL_LANGUAGES = identifiziert die von der SQL-Implementierung unterstützten SQL-Konformitäts Ebenen, Optionen und Dialekte. (Zwischenebene)  
  
 SQL_ISV_TABLE_CONSTRAINTS = identifiziert die Tabellen Einschränkungen, die sich im Besitz eines bestimmten Benutzers befinden. (Zwischenebene)  
  
 SQL_ISV_TABLE_PRIVILEGES = identifiziert die Berechtigungen für persistente Tabellen, die für einen bestimmten Benutzer verfügbar sind oder von diesem erteilt wurden. (Übergangs Ebene für den PPS)  
  
 SQL_ISV_TABLES = identifiziert die permanenten Tabellen, die in einem Katalog definiert sind und auf die ein bestimmter Benutzer zugreifen kann. (Übergangs Ebene für den PPS)  
  
 SQL_ISV_TRANSLATIONS = identifiziert Zeichen Übersetzungen für den Katalog, auf die ein bestimmter Benutzer zugreifen kann. (Vollständig)  
  
 SQL_ISV_USAGE_PRIVILEGES = identifiziert die Nutzungs Berechtigungen für Katalog Objekte, die für einen bestimmten Benutzer verfügbar sind oder dessen Besitzer Sie sind. (Übergangs Ebene für den PPS)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = identifiziert die Spalten, für die die Katalog Sichten, deren Besitzer ein angegebener Benutzer ist, abhängig sind. (Zwischenebene)  
  
 SQL_ISV_VIEW_TABLE_USAGE = identifiziert die Tabellen, auf die sich die Katalog Sichten im Besitz eines bestimmten Benutzers von richten. (Zwischenebene)  
  
 SQL_ISV_VIEWS = identifiziert die in diesem Katalog definierten angezeigten Tabellen, auf die ein bestimmter Benutzer zugreifen kann. (Übergangs Ebene für den PPS)  
  
 SQL_INSERT_STATEMENT (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung für **Insert** -Anweisungen angibt:  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Ein mit SQL-92 Eintrags Level übergebender Treiber gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_INTEGRITY (ODBC 1,0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle die Integritäts Erweiterungs Funktion unterstützt. "N", wenn dies nicht der Fall ist.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_ODBC_SQL_OPT_IEF ODBC 2,0 umbenannt.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines Keysetcursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die erste Teilmenge von Attributen. die zweite Teilmenge finden Sie unter SQL_KEYSET_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Beschreibungen dieser Bitmasks finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und Ersetzen des keysetgesteuerten Cursors für "dynamischer Cursor" in den Beschreibungen).  
  
 Ein SQL-92-zwischen Ebenen-konformen Treiber gibt in der Regel die Optionen SQL_CA1_NEXT, SQL_CA1_ABSOLUTE und SQL_CA1_RELATIVE zurück, die unterstützt werden, da der Treiber scrollbare Cursor durch die eingebettete SQL FETCH-Anweisung unterstützt. Da dadurch die zugrunde liegende SQL-Unterstützung nicht direkt bestimmt wird, werden scrollfähige Cursor möglicherweise nicht unterstützt, auch für einen zwischengeschalteten SQL-92-untergeordneten Treiber.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines Keysetcursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die zweite Teilmenge von Attributen. die erste Teilmenge finden Sie unter SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Beschreibungen dieser Bitmasks finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und Ersetzen des keysetgesteuerten Cursors für "dynamischer Cursor" in den Beschreibungen).  
  
 SQL_KEYWORDS (ODBC 2,0)  
 Eine Zeichenfolge, die eine durch Trennzeichen getrennte Liste aller Datenquellen spezifischen Schlüsselwörter enthält. Diese Liste enthält keine Schlüsselwörter speziell für ODBC oder Schlüsselwörter, die von der Datenquelle und von ODBC verwendet werden. Diese Liste stellt alle reservierten Schlüsselwörter dar. interoperable Anwendungen sollten diese Wörter nicht in Objektnamen verwenden.  
  
 Eine Liste der ODBC-Schlüsselwörter finden Sie unter [reservierte Schlüsselwörter](../../../odbc/reference/appendixes/reserved-keywords.md) in [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Der **#define** Wert SQL_ODBC_KEYWORDS enthält eine durch Trennzeichen getrennte Liste von ODBC-Schlüsselwörtern.  
  
 Anhang C: SQL-Grammatik  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2,0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle ein Escapezeichen für das Prozentzeichen (%) unterstützt. und Unterstrich Zeichen (_) in einem **like** -Prädikat, und der Treiber unterstützt die ODBC-Syntax zum Definieren eines **like** -Prädikat-Escapezeichens. Andernfalls "N".  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS (ODBC 3,0)  
 Ein SQLUINTEGER-Wert, der die maximale Anzahl aktiver gleichzeitiger Anweisungen im asynchronen Modus angibt, die der Treiber für eine bestimmte Verbindung unterstützen kann. Wenn kein bestimmtes Limit vorliegt oder der Grenzwert unbekannt ist, ist dieser Wert 0 (null).  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2,0)  
 Ein SQLUINTEGER-Wert, der die maximale Länge (Anzahl von hexadezimalen Zeichen, ausgenommen das literalpräfix und das von **sqlgettypinfo**zurückgegebene Suffix) eines binären Literals in einer SQL-Anweisung angibt. Beispielsweise hat das binäre Literale 0xffaa eine Länge von 4. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1,0)  
 Ein sqlusmallint-Wert, der die maximale Länge eines Katalog namens in der Datenquelle angibt. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein vollständig konformen conps-Treiber gibt mindestens 128 zurück.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_MAX_QUALIFIER_NAME_LEN ODBC 2,0 umbenannt.  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2,0)  
 Ein SQLUINTEGER-Wert, der die maximale Länge (Anzahl der Zeichen, ausgenommen das literalpräfix und das von **sqlgettypinfo**zurückgegebene Suffix) eines Zeichenliterals in einer SQL-Anweisung angibt. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_COLUMN_NAME_LEN (ODBC 1,0)  
 Ein sqlusmallint-Wert, der die maximale Länge eines Spaltennamens in der Datenquelle angibt. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 18 zurück. Ein mit der conps-Konformität zwischen Ebenen-konformen Treiber gibt mindestens 128 zurück.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl von Spalten angibt, die in einer **Group by** -Klausel zulässig sind. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 6 zurück. Ein mit dem conps-konformen und-konformen Treiber gibt mindestens 15 zurück.  
  
 SQL_MAX_COLUMNS_IN_INDEX (ODBC 2,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl von Spalten angibt, die in einem Index zulässig sind. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl von Spalten angibt, die in einer **Order by** -Klausel zulässig sind. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 6 zurück. Ein mit dem conps-konformen und-konformen Treiber gibt mindestens 15 zurück.  
  
 SQL_MAX_COLUMNS_IN_SELECT (ODBC 2,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl von Spalten angibt, die in einer SELECT-Liste zulässig sind. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 100 zurück. Ein mit der conps-Konformität zwischen Ebenen-konformen Treiber gibt mindestens 250 zurück.  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl von Spalten angibt, die in einer Tabelle zulässig sind. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 100 zurück. Ein mit der conps-Konformität zwischen Ebenen-konformen Treiber gibt mindestens 250 zurück.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl aktiver Anweisungen angibt, die der Treiber für eine Verbindung unterstützen kann. Eine-Anweisung wird als aktiv definiert, wenn Ergebnisse ausstehen. der Begriff "Ergebnisse" bedeutet, dass Zeilen aus einem **Select** -Vorgang oder Zeilen, die von einem **Insert**-, **Update**-oder **Delete** -Vorgang betroffen sind (z. b. eine Zeilen Anzahl), oder wenn Sie sich in einem NEED_DATA Zustand befindet. Dieser Wert kann eine Einschränkung widerspiegeln, die vom Treiber oder der Datenquelle festgelegt wird. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_ACTIVE_STATEMENTS ODBC 2,0 umbenannt.  
  
 SQL_MAX_CURSOR_NAME_LEN (ODBC 1,0)  
 Ein sqlusmallint-Wert, der die maximale Länge eines Cursor namens in der Datenquelle angibt. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 18 zurück. Ein mit der conps-Konformität zwischen Ebenen-konformen Treiber gibt mindestens 128 zurück.  
  
 SQL_MAX_DRIVER_CONNECTIONS (ODBC 1,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl aktiver Verbindungen angibt, die der Treiber für eine Umgebung unterstützen kann. Dieser Wert kann eine Einschränkung widerspiegeln, die vom Treiber oder der Datenquelle festgelegt wird. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_ACTIVE_CONNECTIONS ODBC 2,0 umbenannt.  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3,0)  
 Ein sqlusmallint-Wert, der die maximale Größe in Zeichen angibt, die von der Datenquelle für benutzerdefinierte Namen unterstützt wird.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 18 zurück. Ein mit der conps-Konformität zwischen Ebenen-konformen Treiber gibt mindestens 128 zurück.  
  
 SQL_MAX_INDEX_SIZE (ODBC 2,0)  
 Ein SQLUINTEGER-Wert, der die maximale Anzahl von Bytes angibt, die in den kombinierten Feldern eines Indexes zulässig sind. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 SQL_MAX_PROCEDURE_NAME_LEN (ODBC 1,0)  
 Ein sqlusmallint-Wert, der die maximale Länge eines Prozedur namens in der Datenquelle angibt. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_ROW_SIZE (ODBC 2,0)  
 Ein SQLUINTEGER-Wert, der die maximale Länge einer einzelnen Zeile in einer Tabelle angibt. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 2.000 zurück. Ein mit der conps-Konformität zwischen Ebenen-konformen Treiber gibt mindestens 8.000 zurück.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3,0)  
 Eine Zeichenfolge: "Y", wenn die maximale Zeilengröße, die für den SQL_MAX_ROW_SIZE informationentyp zurückgegeben wird, die Länge aller SQL_LONGVARCHAR und SQL_LONGVARBINARY Spalten in der Zeile enthält. Andernfalls "N".  
  
 SQL_MAX_SCHEMA_NAME_LEN (ODBC 1,0)  
 Ein sqlusmallint-Wert, der die maximale Länge eines Schema namens in der Datenquelle angibt. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 18 zurück. Ein mit der conps-Konformität zwischen Ebenen-konformen Treiber gibt mindestens 128 zurück.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_MAX_OWNER_NAME_LEN ODBC 2,0 umbenannt.  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2,0)  
 Ein SQLUINTEGER-Wert, der die maximale Länge (Anzahl der Zeichen, einschließlich Leerzeichen) einer SQL-Anweisung angibt. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_TABLE_NAME_LEN (ODBC 1,0)  
 Ein sqlusmallint-Wert, der die maximale Länge eines Tabellennamens in der Datenquelle angibt. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 18 zurück. Ein mit der conps-Konformität zwischen Ebenen-konformen Treiber gibt mindestens 128 zurück.  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl von Tabellen angibt, die in der **from** -Klausel einer **Select** -Anweisung zulässig sind. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 Ein mit der PPS-Eintrags Ebene übereinter Treiber gibt mindestens 15 zurück. Ein mit der conps-Konformität zwischen Ebenen-konformen Treiber gibt mindestens 50 zurück.  
  
 SQL_MAX_USER_NAME_LEN (ODBC 2,0)  
 Ein sqlusmallint-Wert, der die maximale Länge eines Benutzernamens in der Datenquelle angibt. Wenn keine maximale Länge vorliegt oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MULT_RESULT_SETS (ODBC 1,0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle mehrere Resultsets unterstützt, "N", wenn dies nicht der Fall ist.  
  
 Weitere Informationen zu mehreren Resultsets finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN (ODBC 1,0)  
 Eine Zeichenfolge "Y", wenn der Treiber mehr als eine aktive Transaktion gleichzeitig unterstützt, "N", wenn jeweils nur eine Transaktion aktiv sein kann.  
  
 Die für diesen Informationstyp zurückgegebenen Informationen gelten nicht für verteilte Transaktionen.  
  
 SQL_NEED_LONG_DATA_LEN (ODBC 2,0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle die Länge eines Long-Datenwerts (der Datentyp ist SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer Datenquellen spezifischer Datentyp) benötigt, bevor dieser Wert an die Datenquelle gesendet wird, andernfalls "N", wenn dies nicht der Fall ist. Weitere Informationen finden Sie unter [SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md) und [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS (ODBC 1,0)  
 Ein sqlusmallint-Wert, der angibt, ob die Datenquelle in Spalten not NULL unterstützt:  
  
 SQL_NNC_NULL = alle Spalten müssen NULL-Werte zulassen.  
  
 SQL_NNC_NON_NULL = Spalten dürfen keine NULL-Werte zulassen. (Die Datenquelle unterstützt die **not NULL** -Spalten Einschränkung in **CREATE TABLE** -Anweisungen.)  
  
 Ein mit SQL-92 Entry Level-konformitäer Treibers wird SQL_NNC_NON_NULL zurückgegeben.  
  
 SQL_NULL_COLLATION (ODBC 2,0)  
 Ein sqlusmallint-Wert, der angibt, wo NULL-Werte in einem Resultset sortiert werden:  
  
 SQL_NC_END = NULL-Werten werden am Ende des Resultsets sortiert, unabhängig von den Schlüsselwörtern ASC oder Entsc.  
  
 SQL_NC_HIGH = NULL-Werten werden abhängig von den Schlüsselwörtern ASC oder Debug am höchsten Ende des Resultsets sortiert.  
  
 SQL_NC_LOW = NULL-Werten werden am unteren Ende des Resultsets sortiert, abhängig von den Schlüsselwörtern ASC oder Entsc.  
  
 SQL_NC_START = NULL-Werten werden am Anfang des Resultsets sortiert, unabhängig von den Schlüsselwörtern ASC oder Entsc.  
  
 SQL_NUMERIC_FUNCTIONS (ODBC 1,0)  
 Hinweis: der Informationstyp wurde in ODBC 1,0 eingeführt. jede Bitmaske ist mit der Version gekennzeichnet, in der Sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske, die die numerischen Skalarfunktionen auflistet, die vom Treiber und der zugeordneten Datenquelle unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche numerischen Funktionen unterstützt werden:  
  
 SQL_FN_NUM_ABS (ODBC 1.0) SQL_FN_NUM_ACOS (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ATAN (ODBC 1.0) SQL_FN_NUM_ATAN2 (ODBC 1.0) SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC) 1.0) SQL_FN_NUM_COT (ODBC 1.0) SQL_FN_NUM_DEGREES (ODBC 2.0) SQL_FN_NUM_EXP (ODBC 1.0) SQL_FN_NUM_FLOOR (ODBC 1.0) SQL_FN_NUM_LOG (ODBC 1.0) SQL_FN_NUM_LOG10 (ODBC 2.0) SQL_FN_ NUM_MOD (ODBC 1.0) SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) SQL_FN_NUM_RADIANS (ODBC 2.0) SQL_FN_NUM_RAND (ODBC 1.0) SQL_FN_NUM_ROUND (ODBC 2.0) SQL_FN_NUM_SIGN (ODBC 1.0) SQL_FN_NUM_SIN (ODBC 1.0) SQL_FN_NUM_SQRT (ODBC 1.0) SQL_FN_NUM_TAN (ODBC 1.0) SQL_FN_NUM_TRUNCATE (ODBC 2,0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE (ODBC 3,0)  
 Ein SQLUINTEGER-Wert, der die Ebene der ODBC 3 *. x* -Schnittstelle angibt, der der Treiber entspricht.  
  
 SQL_OIC_CORE: die minimale Ebene, der alle ODBC-Treiber entsprechen sollen. Diese Ebene umfasst grundlegende Schnittstellen Elemente, wie z. b. Verbindungsfunktionen, Funktionen zum Vorbereiten und Ausführen einer SQL-Anweisung, grundlegende resultsetmetadatenfunktionen, grundlegende Katalog Funktionen usw.  
  
 SQL_OIC_LEVEL1: eine Ebene, einschließlich der Kernfunktionen der Kompatibilitäts Ebene, sowie scrollfähige Cursor, Lesezeichen, positionierte Updates und Löschungen usw.  
  
 SQL_OIC_LEVEL2: eine Ebene, einschließlich der Standardfunktionen der Kompatibilitäts Ebene der Ebene 1 sowie erweiterter Features wie z. b. sensible Cursor aktualisieren, löschen und aktualisieren nach Lesezeichen Unterstützung für gespeicherte Prozeduren Katalog Funktionen für Primär-und Fremdschlüssel; Unterstützung für mehrere Kataloge; Und so weiter.  
  
 Weitere Informationen finden Sie unter [Schnittstellen](../../../odbc/reference/develop-app/interface-conformance-levels.md)Übereinstimmungs Ebenen.  
  
 SQL_ODBC_VER (ODBC 1,0)  
 Eine Zeichenfolge mit der Version von ODBC, der der Treiber-Manager entspricht. Die Version hat das Format # #. # #. 0000, wobei die ersten beiden Ziffern die Hauptversion und die nächsten zwei Ziffern die neben Version sind. Dies wird nur im Treiber-Manager implementiert.  
  
 SQL_OJ_CAPABILITIES (ODBC 2,01)  
 Eine SQLUINTEGER-Bitmaske, die die Typen von äußeren Joins auflistet, die vom Treiber und der Datenquelle unterstützt werden. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Typen unterstützt werden:  
  
 SQL_OJ_LEFT = Left Outer Joins werden unterstützt.  
  
 SQL_OJ_RIGHT = Rechte äußere Joins werden unterstützt.  
  
 SQL_OJ_FULL = vollständige äußere Joins werden unterstützt.  
  
 SQL_OJ_NESTED = eingefügte äußere Joins werden unterstützt.  
  
 SQL_OJ_NOT_ORDERED = die Spaltennamen in der ON-Klausel des äußeren Joins müssen sich nicht in derselben Reihenfolge wie die entsprechenden Tabellennamen in der **äußeren Join** -Klausel befinden.  
  
 SQL_OJ_INNER = die innere Tabelle (die Rechte Tabelle in einem Left Outer Join oder in der linken Tabelle in einem rechten äußeren Join) kann auch in einem inneren Join verwendet werden. Dies gilt nicht für vollständige äußere Joins, die keine innere Tabelle aufweisen.  
  
 SQL_OJ_ALL_COMPARISON_OPS = der Vergleichs Operator in der ON-Klausel kann einer der ODBC-Vergleichs Operatoren sein. Wenn dieses Bit nicht festgelegt ist, kann nur der Vergleichs Operator "gleich" (=) in äußeren Joins verwendet werden.  
  
 Wenn keine dieser Optionen als unterstützt zurückgegeben wird, wird keine Outer Join-Klausel unterstützt.  
  
 Informationen zur Unterstützung von relationalen joinoperatoren in einer SELECT-Anweisung, wie von SQL-92 definiert, finden Sie unter SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT (ODBC 2,0)  
 Eine Zeichenfolge: "Y", wenn die Spalten in der **Order by** -Klausel in der SELECT-Liste enthalten sein müssen. andernfalls "N".  
  
 SQL_PARAM_ARRAY_ROW_COUNTS (ODBC 3,0)  
 Ein SQLUINTEGER-Element, das die Eigenschaften des Treibers bezüglich der Verfügbarkeit der Zeilen Anzahl in einer parametrisierten Ausführung auflistet. Weist die folgenden Werte auf:  
  
 SQL_PARC_BATCH = einzelne Zeilen Anzahl ist für jeden Parametersatz verfügbar. Dies entspricht konzeptionell dem Treiber, der einen Batch von SQL-Anweisungen erzeugt, eine für jeden Parametersatz im Array. Erweiterte Fehlerinformationen können mit dem Feld SQL_PARAM_STATUS_PTR Deskriptor abgerufen werden.  
  
 SQL_PARC_NO_BATCH = es ist nur eine Zeilen Anzahl verfügbar. Dies ist die kumulierte Zeilen Anzahl, die sich aus der Ausführung der-Anweisung für das gesamte Array von Parametern ergibt. Dies entspricht konzeptionell der Behandlung der Anweisung und des kompletten Parameter Arrays als eine atomarische Einheit. Fehler werden genauso behandelt, als wenn eine-Anweisung ausgeführt wurde.  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3,0)  
 Ein SQLUINTEGER-Element, das die Eigenschaften des Treibers in Bezug auf die Verfügbarkeit von Resultsets in einer parametrisierten Ausführung auflistet. Weist die folgenden Werte auf:  
  
 SQL_PAS_BATCH = es ist ein Resultset pro Parametersatz verfügbar. Dies entspricht konzeptionell dem Treiber, der einen Batch von SQL-Anweisungen erzeugt, eine für jeden Parametersatz im Array.  
  
 SQL_PAS_NO_BATCH = es ist nur ein Resultset verfügbar, das das kumulative Resultset darstellt, das sich aus der Ausführung der-Anweisung für das vollständige Array von Parametern ergibt. Dies entspricht konzeptionell der Behandlung der Anweisung und des kompletten Parameter Arrays als eine atomarische Einheit.  
  
 SQL_PAS_NO_SELECT = ein Treiber lässt nicht zu, dass eine Resultset-Generierungs Anweisung mit einem Array von Parametern ausgeführt wird.  
  
 SQL_PROCEDURE_TERM (ODBC 1,0)  
 Eine Zeichenfolge mit dem Namen des Datenquellen Herstellers für eine Prozedur. Beispiel: "Daten Bank Prozedur", "gespeicherte Prozedur", "Prozedur", "Paket" oder "gespeicherte Abfrage".  
  
 SQL_PROCEDURES (ODBC 1,0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle Prozeduren unterstützt und der Treiber die ODBC-Prozedur Aufruf Syntax unterstützt. Andernfalls "N".  
  
 SQL_POS_OPERATIONS (ODBC 2,0)  
 Eine SQLINTEGER-Bitmaske, die die Unterstützungs Vorgänge in **SQLSetPos**auflistet.  
  
 Die folgenden Bitmasken werden mit dem-Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden.  
  
 SQL_POS_POSITION (ODBC 2,0) SQL_POS_REFRESH (ODBC 2,0) SQL_POS_UPDATE (ODBC 2,0) SQL_POS_DELETE (ODBC 2,0) SQL_POS_ADD (ODBC-2,0)  
  
 SQL_QUOTED_IDENTIFIER_CASE (ODBC 2,0)  
 Einen sqlusmallint-Wert wie folgt:  
  
 Bei SQL_IC_UPPER = Bezeichner in Anführungszeichen in SQL wird die Groß-/Kleinschreibung nicht beachtet, und Sie werden in Großbuchstaben im System Katalog gespeichert.  
  
 Bei SQL_IC_LOWER = Bezeichner in Anführungszeichen in SQL wird die Groß-/Kleinschreibung nicht beachtet und in Kleinbuchstaben im System Katalog gespeichert.  
  
 Bei SQL_IC_SENSITIVE = Bezeichner in Anführungszeichen in SQL wird die Groß-/Kleinschreibung beachtet, und Sie werden im System Katalog gemischt gespeichert. (In einer SQL-92-kompatiblen Datenbank wird bei Bezeichnern in Anführungszeichen immer die Groß-/Kleinschreibung beachtet.)  
  
 Bei SQL_IC_MIXED = Bezeichner in Anführungszeichen in SQL wird die Groß-/Kleinschreibung nicht beachtet, und die Daten werden in gemischten Fällen im System Katalog gespeichert.  
  
 Ein mit SQL-92 Entry Level-konformitäer Treibers gibt immer SQL_IC_SENSITIVE zurück.  
  
 SQL_ROW_UPDATES (ODBC 1,0)  
 Eine Zeichenfolge: "Y", wenn ein keysetgesteuerter oder gemischter Cursor Zeilen Versionen oder Werte für alle abgerufenen Zeilen beibehält und daher alle Updates erkennen kann, die von einem Benutzer seit dem letzten Abruf der Zeile an einer Zeile vorgenommen wurden. (Dies gilt nur für Updates, nicht für Löschungen oder Einfügungen.) Der Treiber kann das SQL_ROW_UPDATED-Flag zum Zeilen Status Array zurückgeben, wenn **SQLFetchScroll** aufgerufen wird. Andernfalls "N".  
  
 SQL_SCHEMA_TERM (ODBC 1,0)  
 Eine Zeichenfolge mit dem Namen des Datenquellen Herstellers für ein Schema. Beispiel: "Owner", "Authorization ID" oder "Schema".  
  
 Die Zeichenfolge kann in groß-, klein-oder gemischter Groß-/Kleinschreibung zurückgegeben werden.  
  
 Ein mit SQL-92 Entry Level-konformitäer Treibers gibt immer "Schema" zurück.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_OWNER_TERM ODBC 2,0 umbenannt.  
  
 SQL_SCHEMA_USAGE (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die die-Anweisungen auflistet, in denen Schemas verwendet werden können:  
  
 SQL_SU_DML_STATEMENTS = Schemas werden in allen Anweisungen für die Daten Bearbeitungs Sprache unterstützt: **Select**, **Insert**, **Update**, **Delete**und falls unterstützt, **Wählen Sie für Update** -und positionierte UPDATE-und DELETE-Anweisungen aus.  
  
 SQL_SU_PROCEDURE_INVOCATION = Schemas werden in der Anweisung zum Aufrufen von ODBC-Prozeduren unterstützt.  
  
 SQL_SU_TABLE_DEFINITION = Schemas werden in allen Tabellen Definitions Anweisungen unterstützt: **CREATE TABLE**, **CREATE VIEW**, **ALTER TABLE**, **DROP TABLE**und **Drop View**.  
  
 SQL_SU_INDEX_DEFINITION = Schemas werden in allen Index Definitions Anweisungen unterstützt: **Create Index** und **Drop Index**.  
  
 SQL_SU_PRIVILEGE_DEFINITION = Schemas werden in allen Berechtigungs Definitions Anweisungen unterstützt: **Grant** und **Widerruf**.  
  
 Ein in SQL-92 Eintrags Level übergebender Treiber gibt immer die Optionen SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION und SQL_SU_PRIVILEGE_DEFINITION zurück, wie unterstützt.  
  
 Dieser *InfoType* wurde für ODBC 3,0 von der *InfoType* -SQL_OWNER_USAGE ODBC 2,0 umbenannt.  
  
 SQL_SCROLL_OPTIONS (ODBC 1,0)  
 Hinweis: der Informationstyp wurde in ODBC 1,0 eingeführt. jede Bitmaske ist mit der Version gekennzeichnet, in der Sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske, die die Bild Lauf Optionen auflistet, die für scrollbare Cursor unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen unterstützt werden:  
  
 SQL_SO_FORWARD_ONLY = der Cursor führt einen Bildlauf nach oben aus. (ODBC 1,0)  
  
 SQL_SO_STATIC = die Daten im Resultset sind statisch. (ODBC 2,0)  
  
 SQL_SO_KEYSET_DRIVEN = der Treiber speichert und verwendet die Schlüssel für jede Zeile im Resultset. (ODBC 1,0)  
  
 SQL_SO_DYNAMIC = der Treiber behält die Schlüssel für jede Zeile im Rowset bei (die Keysetgröße ist identisch mit der Rowsetgröße). (ODBC 1,0)  
  
 SQL_SO_MIXED = der Treiber behält die Schlüssel für jede Zeile im Keyset bei, und die Keysetgröße ist größer als die Rowsetgröße. Der Cursor ist keysetgesteuert innerhalb des Keysets und dynamisch außerhalb des Keysets. (ODBC 1,0)  
  
 Informationen zu scrollfähigen Cursorn finden Sie unter [scrollfähige Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE (ODBC 1,0)  
 Eine Zeichenfolge, die angibt, was der Treiber als Escapezeichen unterstützt, das die Verwendung des Muster Vergleichs Metazeichen Unterstrich (_) und Prozentzeichen (%) ermöglicht. als gültige Zeichen in Suchmustern. Dieses Escapezeichen gilt nur für die Katalog Funktionsargumente, die Such Zeichenfolgen unterstützen. Wenn diese Zeichenfolge leer ist, unterstützt der Treiber kein Escapezeichen für das Suchmuster.  
  
 Da dieser Informationstyp keine allgemeine Unterstützung für das Escapezeichen im **like** -Prädikat angibt, enthält SQL-92 keine Anforderungen für diese Zeichenfolge.  
  
 Dieser *InfoType* ist auf Katalog Funktionen beschränkt. Eine Beschreibung der Verwendung des Escapezeichens in Suchmuster Zeichenfolgen finden Sie unter [Muster Wert Argumente](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER_NAME (ODBC 1,0)  
 Eine Zeichenfolge mit dem tatsächlichen Datenquellen spezifischen Servernamen; nützlich, wenn ein Datenquellen Name während **SQLCONNECT**, **SQLDriverConnect**und **sqlbrowseconnetct**verwendet wird.  
  
 SQL_SPECIAL_CHARACTERS (ODBC 2,0)  
 Eine Zeichenfolge, die alle Sonderzeichen enthält (d. h. alle Zeichen mit Ausnahme von a bis z, a bis z, 0 bis 9 und Unterstriche), die in einem Bezeichnernamen (z. b. Tabellenname, Spaltenname oder Indexname) für die Datenquelle verwendet werden können. Beispiel: "# $ ^". Wenn ein Bezeichner mindestens ein Zeichen enthält, muss der Bezeichner ein Begrenzungs Bezeichner sein.  
  
 SQL_SQL_CONFORMANCE (ODBC 3,0)  
 Ein SQLUINTEGER-Wert, der die Ebene von SQL-92 angibt, die vom Treiber unterstützt wird:  
  
 SQL_SC_SQL92_ENTRY = Eintrags Ebene SQL-92-kompatibel.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = mit der Übergangsstufe 127-2 = mit der Übergangsstufe kompatibel.  
  
 SQL_SC_SQL92_FULL = vollständig SQL-92-kompatibel.  
  
 SQL_SC_ SQL92_INTERMEDIATE = Zwischenstufe SQL-92-kompatibel.  
  
 SQL_SQL92_DATETIME_FUNCTIONS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die DateTime-Skalarfunktionen auflistet, die vom Treiber und der zugeordneten Datenquelle unterstützt werden, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche datetime-Funktionen unterstützt werden:  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Regeln auflistet, die für einen Fremdschlüssel in einer **Delete** -Anweisung unterstützt werden, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln von der Datenquelle unterstützt werden:  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Ein mit der Anwendung für die Übergangs Ebene übergebender PPS gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Regeln auflistet, die für einen Fremdschlüssel in einer **Update** -Anweisung unterstützt werden, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln von der Datenquelle unterstützt werden:  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Ein vollständig konformen SQL-92-Treiber gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_SQL92_GRANT (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die in der **Grant** -Anweisung unterstützten Klauseln auflistet, wie in SQL-92 definiert.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln von der Datenquelle unterstützt werden:  
  
 SQL_SG_DELETE_TABLE (Einstiegsebene) SQL_SG_INSERT_COLUMN (Zwischenebene) SQL_SG_INSERT_TABLE (Einstiegsebene) SQL_SG_REFERENCES_TABLE (Eintrags Ebene) SQL_SG_REFERENCES_COLUMN (Einstiegsebene) SQL_SG_SELECT_TABLE (Eintrags Ebene) SQL_SG_UPDATE_COLUMN (Einstiegsebene) SQL_SG_UPDATE_TABLE (Eintrags Ebene) SQL_SG_USAGE_ON_DOMAIN (der übergeordneten Ebene) SQL_SG_USAGE_ON_CHARACTER_SET (FI-Übergangs Ebene) SQL_SG_USAGE_ON_COLLATION (FI-Übergangsstufe) SQL_SG_USAGE_ON_TRANSLATION (PPS-Übergangs) Ebene) SQL_SG_WITH_GRANT_OPTION (Einstiegsebene)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Skalarfunktionen des numerischen Werts auflistet, die vom Treiber und der zugeordneten Datenquelle unterstützt werden, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche numerischen Funktionen unterstützt werden:  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Prädikate auflistet, die in einer **Select** -Anweisung unterstützt werden, wie in SQL-92 definiert.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SP_BETWEEN (Einstiegsebene) SQL_SP_COMPARISON (Einstiegsebene) SQL_SP_EXISTS (Einstiegsebene) SQL_SP_IN (Einstiegsebene) SQL_SP_ISNOTNULL (Einstiegsebene) SQL_SP_ISNULL (Einstiegsebene) SQL_SP_LIKE (Eintrags Ebene) SQL_SP_MATCH_FULL (vollständig) SQL_SP_MATCH_PARTIAL (vollständig) SQL_SP_MATCH_UNIQUE_FULL (vollständig) SQL_SP_MATCH_UNIQUE_PARTIAL (vollständig) SQL_SP_OVERLAPS (über die Übergangs Ebene) SQL_SP_QUANTIFIED_COMPARISON (Eintrags Ebene) SQL_SP_UNIQUE (Einstiegsebene)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die in einer **Select** -Anweisung unterstützten relationalen joinoperatoren auflistet, wie in SQL-92 definiert.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (Zwischenebene) SQL_SRJO_CROSS_JOIN (vollständig) SQL_SRJO_EXCEPT_JOIN (Zwischenebene) SQL_SRJO_FULL_OUTER_JOIN (Zwischenebene) SQL_SRJO_INNER_JOIN (der übergeordneten Ebene) SQL_SRJO_INTERSECT_JOIN (Zwischenebene) SQL_SRJO_LEFT_OUTER_JOIN (der über-Übergangs Ebene) SQL_SRJO_NATURAL_JOIN (der über-Übergangs Ebene) SQL_SRJO_RIGHT_OUTER_JOIN (Vollmaß)  
  
 SQL_SRJO_INNER_JOIN gibt die Unterstützung für die **innere** joinsyntax an, nicht für die innere joinfunktion. Die Unterstützung für die **innere** joinsyntax ist "PPS Transition", wohingegen die Unterstützung für die innere joinfunktion " **Entry**" ist.  
  
 SQL_SQL92_REVOKE (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln aufzählt, die in der von der Datenquelle unterstützten Anweisung " **Widerruf** " unterstützt werden, wie in SQL-92 definiert.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln von der Datenquelle unterstützt werden:  
  
 SQL_SR_CASCADE (SQL_SR_DELETE_TABLE der Übergangs Ebene) (Eintrags Ebene) SQL_SR_GRANT_OPTION_FOR (Zwischenebene) SQL_SR_INSERT_COLUMN (Zwischenebene) SQL_SR_INSERT_TABLE (Eintrags Ebene) SQL_SR_REFERENCES_COLUMN (Einstiegsebene) SQL_SR_REFERENCES_TABLE (Eintrags Ebene) SQL_SR_RESTRICT (über die Übergangs Ebene) SQL_SR_SELECT_TABLE (Eintrags Ebene) SQL_SR_UPDATE_COLUMN (Einstiegsebene) SQL_SR_UPDATE_TABLE (Eintrags Ebene) SQL_SR_USAGE_ON_DOMAIN (fps-Übergangs Ebene) SQL_SR_USAGE_ON_CHARACTER_ Set (fps-Übergangs Ebene) SQL_SR_USAGE_ON_COLLATION (SQL_SR_USAGE_ON_TRANSLATION der übergeordneten Ebene) (fps-Übergangs Ebene)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die in einer **Select** -Anweisung unterstützten Zeilen Wert-konstruktorausdrücke auflistet, wie in SQL-92 definiert. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die skalaren Zeichen folgen Funktionen auflistet, die vom Treiber und der zugeordneten Datenquelle unterstützt werden, wie in SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Zeichen folgen Funktionen unterstützt werden:  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die unterstützten Wert Ausdrücke auflistet, wie in SQL-92 definiert.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SVE_CASE (Zwischenebene) SQL_SVE_CAST (SQL_SVE_COALESCE Übergangs Ebene) (Zwischenebene) SQL_SVE_NULLIF (Zwischenebene)  
  
 SQL_STANDARD_CLI_CONFORMANCE (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die den CLI-Standard-oder-Standardwert auflistet, dem der Treiber entspricht. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Ebenen der Treiber erfüllt:  
  
 SQL_SCC_XOPEN_CLI_VERSION1: der Treiber entspricht der Open Group CLI-Version 1.  
  
 SQL_SCC_ISO92_CLI: der Treiber entspricht der ISO 92-CLI.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1 (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines statischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die erste Teilmenge von Attributen. die zweite Teilmenge finden Sie unter SQL_STATIC_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Beschreibungen dieser Bitmasks finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und Ersetzen des "statischen Cursors" für "dynamischer Cursor" in den Beschreibungen).  
  
 Ein SQL-92-zwischen Ebenen-konformen Treiber gibt in der Regel die Optionen SQL_CA1_NEXT, SQL_CA1_ABSOLUTE und SQL_CA1_RELATIVE zurück, die unterstützt werden, da der Treiber scrollbare Cursor durch die eingebettete SQL FETCH-Anweisung unterstützt. Da dadurch die zugrunde liegende SQL-Unterstützung nicht direkt bestimmt wird, werden scrollfähige Cursor möglicherweise nicht unterstützt, auch für einen zwischengeschalteten SQL-92-untergeordneten Treiber.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2 (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines statischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält die zweite Teilmenge von Attributen. die erste Teilmenge finden Sie unter SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 Beschreibungen dieser Bitmasks finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (und Ersetzen des "statischen Cursors" für "dynamischer Cursor" in den Beschreibungen).  
  
 SQL_STRING_FUNCTIONS (ODBC 1,0)  
 Hinweis: der Informationstyp wurde in ODBC 1,0 eingeführt. jede Bitmaske ist mit der Version gekennzeichnet, in der Sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske, die die skalaren Zeichen folgen Funktionen auflistet, die vom Treiber und der zugeordneten Datenquelle unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Zeichen folgen Funktionen unterstützt werden:  
  
 SQL_FN_STR_ASCII (ODBC 1.0) SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 2.0) SQL_FN_STR_INSERT (ODBC 1.0) SQL_FN_STR_LCASE (ODBC 1.0) SQL_FN_STR_LEFT (ODBC 1.0) SQL_FN_STR_LENGTH (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1,0) SQL_FN_STR_LTRIM (ODBC) 1,0) SQL_FN_STR_OCTET_LENGTH (ODBC 3,0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_REPEAT (ODBC 1.0) SQL_FN_STR_REPLACE (ODBC 1.0) SQL_FN_STR_RIGHT (ODBC 1.0) SQL_FN_STR_RTRIM (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 2.0) SQL_FN_STR_SPACE (ODBC 2.0) SQL_FN_STR_SUBSTRING (ODBC 1.0) SQL_FN_STR_UCASE (ODBC 1,0)  
  
 Wenn eine Anwendung die "Skalarfunktion **Suchen** " mit den Argumenten " *string_exp1*", " *string_exp2*" und " *Start* " abrufen kann, gibt der Treiber die SQL_FN_STR_LOCATE Bitmaske zurück. Wenn eine Anwendung die Skalarfunktion suchen nur mit den *string_exp1* -und *string_exp2* -Argumenten aufzurufen kann, gibt der Treiber die SQL_FN_STR_LOCATE_2 Bitmaske zurück. Treiber, die die Skalarfunktion **Suchen** vollständig unterstützen, geben beide Bitmasken zurück.  
  
 (Weitere Informationen finden Sie unter [Zeichen folgen Funktionen](../../../odbc/reference/appendixes/string-functions.md) in Anhang E, "skalare Funktionen".)  
  
 SQL_SUBQUERIES (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die die Prädikate auflistet, die Unterabfragen unterstützen:  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 Die SQL_SQ_CORRELATED_SUBQUERIES Bitmaske gibt an, dass alle Prädikate, die Unterabfragen unterstützen, korrelierte Unterabfragen unterstützen  
  
 Ein mit SQL-92 Entry Level-konformitäer Treibers gibt immer eine Bitmaske zurück, in der alle diese Bits festgelegt sind.  
  
 SQL_SYSTEM_FUNCTIONS (ODBC 1,0)  
 Eine SQLUINTEGER-Bitmaske, die die skalaren Systemfunktionen auflistet, die vom Treiber und der zugehörigen Datenquelle unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Systemfunktionen unterstützt werden:  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM (ODBC 1,0)  
 Eine Zeichenfolge mit dem Namen des Datenquellen Herstellers für eine Tabelle. Beispiel: "Table" oder "file".  
  
 Diese Zeichenfolge kann groß, klein oder gemischt sein.  
  
 Ein mit SQL-92 Entry Level-konformitäer Treibers gibt immer "Table" zurück.  
  
 SQL_TIMEDATE_ADD_INTERVALS (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die die Zeitstempel Intervalle auflistet, die vom Treiber und der zugehörigen Datenquelle für die timestampadd-Skalarfunktion unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Intervalle unterstützt werden:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Ein mit dem Operator für die Übergangs Ebene Übereinstimmung mit PPS gibt immer eine Bitmaske zurück, in der alle diese Bits festgelegt sind.  
  
 SQL_TIMEDATE_DIFF_INTERVALS (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die die Zeitstempel Intervalle auflistet, die vom Treiber und der zugeordneten Datenquelle für die timestampdiff-Skalarfunktion unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Intervalle unterstützt werden:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Ein mit dem Operator für die Übergangs Ebene Übereinstimmung mit PPS gibt immer eine Bitmaske zurück, in der alle diese Bits festgelegt sind.  
  
 SQL_TIMEDATE_FUNCTIONS (ODBC 1,0)  
 Hinweis: der Informationstyp wurde in ODBC 1,0 eingeführt. jede Bitmaske ist mit der Version gekennzeichnet, in der Sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske, die die skalaren Datums-und Uhrzeit Funktionen auflistet, die vom Treiber und der zugehörigen Datenquelle unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Datums-und Uhrzeit Funktionen unterstützt werden:  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_CURTIME (ODBC 1,0) SQL_FN_TD_DAYNAME (ODBC 2.0) SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_DAYOFWEEK (ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1,0) SQL_FN_TD_EXTRACT (ODBC 3.0) SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTH (ODBC) 1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) SQL_FN_TD_NOW (ODBC 1.0) SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_SECOND (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0) SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0) SQL_FN_TD_WEEK (ODBC 1.0) SQL_FN_TD_YEAR (ODBC 1,0)  
  
 SQL_TXN_CAPABLE (ODBC 1,0)  
 Hinweis: der Informationstyp wurde in ODBC 1,0 eingeführt. jeder Rückgabewert wird mit der Version bezeichnet, in der er eingeführt wurde.  
  
 Ein sqlusmallint-Wert, der die Transaktionsunterstützung im Treiber oder in der Datenquelle beschreibt:  
  
 SQL_TC_NONE = Transaktionen werden nicht unterstützt. (ODBC 1,0)  
  
 SQL_TC_DML = Transaktionen können nur DML-Anweisungen (Data Manipulation Language, Daten Bearbeitungs Sprache) enthalten (**Select**, **Insert**, **Update**, **Delete**). In einer Transaktion aufgetretene DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) verursachen einen Fehler. (ODBC 1,0)  
  
 SQL_TC_DDL_COMMIT = Transaktionen dürfen nur DML-Anweisungen enthalten. DDL-Anweisungen (**CREATE TABLE**, **Drop Index**usw.), die in einer Transaktion auftreten, bewirken, dass für die Transaktion ein Commit ausgeführt wird. (ODBC 2,0)  
  
 SQL_TC_DDL_IGNORE = Transaktionen dürfen nur DML-Anweisungen enthalten. In einer Transaktion aufgetretene DDL-Anweisungen werden ignoriert. (ODBC 2,0)  
  
 SQL_TC_ALL = Transaktionen können DDL-Anweisungen und DML-Anweisungen in beliebiger Reihenfolge enthalten. (ODBC 1,0)  
  
 (Da die Unterstützung von Transaktionen in SQL-92 obligatorisch ist, wird ein SQL-92-konformen Treiber [any Level] niemals SQL_TC_NONE zurückgegeben.)  
  
 SQL_TXN_ISOLATION_OPTION (ODBC 1,0)  
 Eine SQLUINTEGER-Bitmaske, die die Transaktions Isolations Stufen auflistet, die für den Treiber oder die Datenquelle verfügbar sind.  
  
 Die folgenden Bitmasken werden mit dem-Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden:  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Beschreibungen dieser Isolations Stufen finden Sie in der Beschreibung SQL_DEFAULT_TXN_ISOLATION.  
  
 Zum Festlegen der Transaktions Isolationsstufe Ruft eine Anwendung **SQLSetConnectAttr** auf, um das SQL_ATTR_TXN_ISOLATION-Attribut festzulegen. Weitere Informationen finden Sie unter [SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Ein mit SQL-92 Entry Level-konformitäter Treiber gibt immer SQL_TXN_SERIALIZABLE zurück, wie er unterstützt wird. Ein mit der Anwendung für die Übergangs Ebene übergebender PPS gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_UNION (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung für die **Union** -Klausel aufzählt:  
  
 SQL_U_UNION = die Datenquelle unterstützt die **Union** -Klausel.  
  
 SQL_U_UNION_ALL = die Datenquelle unterstützt das **all** -Schlüsselwort in der **Union** -Klausel. (**SQLGetInfo** gibt in diesem Fall sowohl SQL_U_UNION als auch SQL_U_UNION_ALL zurück.)  
  
 Ein mit SQL-92 Entry Level-konformitäter Treiber gibt immer beide Optionen zurück, die unterstützt werden.  
  
 SQL_USER_NAME (ODBC 1,0)  
 Eine Zeichenfolge mit dem Namen, der in einer bestimmten Datenbank verwendet wird, der sich von dem Anmelde Namen unterscheiden kann.  
  
 SQL_XOPEN_CLI_YEAR (ODBC 3,0)  
 Eine Zeichenfolge, die das Jahr der Veröffentlichung der Open Group-Spezifikation angibt, mit der die Version des ODBC-Treiber-Managers vollständig konform ist.  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1,0)  
 Eine Zeichenfolge: "Y", wenn der Benutzer alle Prozeduren ausführen kann, die von **SQLProcedures**zurückgegeben werden. "N", wenn möglicherweise Prozeduren zurückgegeben werden, die der Benutzer nicht ausführen kann.  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1,0)  
 Eine Zeichenfolge: "Y", wenn dem **Benutzer garantiert wird** , dass er Berechtigungen für alle von **SQLTables**zurückgegebenen Tabellen hat. "N", wenn möglicherweise Tabellen zurückgegeben werden, auf die der Benutzer nicht zugreifen kann.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3,0)  
 Ein sqlusmallint-Wert, der die maximale Anzahl aktiver Umgebungen angibt, die der Treiber unterstützen kann. Wenn kein angegebenes Limit vorliegt oder das Limit unbekannt ist, wird dieser Wert auf 0 festgelegt.  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung für Aggregations Funktionen aufzählt:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Ein mit SQL-92 Eintrags Level übergebender Treiber gibt immer alle diese Optionen zurück, die unterstützt werden.  
  
 SQL_ALTER_DOMAIN (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in der **Alter Domain** -Anweisung auflistet, wie in SQL-92 definiert, die von der Datenquelle unterstützt wird. Ein vollständig kompatibler SQL-92-Treiber gibt immer alle Bitmasken zurück. Der Rückgabewert "0" bedeutet, dass die **Alter Domain** -Anweisung nicht unterstützt wird.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = das Hinzufügen einer Domänen Einschränkung wird unterstützt (vollständig)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<Alter Domain> \<Set Domain default-Klausel> wird unterstützt (vollständig)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<Einschränkungs Name-Definitions Klausel> wird für Benennungs Domänen Einschränkung unterstützt (Zwischenebene)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<Drop Domain-Einschränkungs Klausel> wird unterstützt (vollständig)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<Alter Domain> \<Drop Domain default-Klausel> wird unterstützt (vollständig)  
  
 In den folgenden Bits werden die \<unterstützten Einschränkungs \<Attribute> angegeben, wenn Add Domain-Einschränkungs> unterstützt wird (das SQL_AD_ADD_DOMAIN_CONSTRAINT Bit ist festgelegt):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (vollständig) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (vollständig) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (vollständig) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (vollständig)  
  
 SQL_ALTER_TABLE (ODBC 2,0)  
 Eine SQLUINTEGER-Bitmaske, die die-Klauseln in der **ALTER TABLE** -Anweisung auflistet, die von der Datenquelle unterstützt wird.  
  
 Die SQL-92-oder FPS-Konformitätsstufe, bei der diese Funktion unterstützt werden muss, wird in Klammern neben den einzelnen Bitmasken angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<Spalte> Klausel hinzufügen wird unterstützt, mit der Funktion zum Angeben der Spalten Sortierung (vollständig) (ODBC 3,0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<Spalte> Klausel hinzufügen wird unterstützt, mit der Funktion zum Angeben von 3,0 Spalten Standardwerten  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<Spalte hinzufügen> wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_ADD_CONSTRAINT = \<Spalte zum Hinzufügen von Spalten> wird unterstützt, mit der Funktion zum Angeben von Spalten Einschränkungen (über die Übergangsstufe "Fi") (ODBC 3,0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<Table-Einschränkung hinzufügen> Klausel wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<Einschränkungs Name Definition> wird für das Benennen von Spalten-und Tabellen Einschränkungen (Zwischenebene) unterstützt (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<Drop Column> Cascade wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<Alter Column> \<Drop Column default-Klausel> wird unterstützt (Zwischenstufe) (ODBC 3,0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<Drop Column> Einschränkung wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3,0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<Drop Column> Einschränkung wird unterstützt (fps-Übergangs Ebene) (ODBC 3,0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<Alter Column> \<Set Column default-Klausel> wird unterstützt (Zwischenstufe) (ODBC 3,0)  
  
 Die folgenden Bits geben die Unterstützungs \<Einschränkungs Attribute> an, wenn die Angabe von Spalten-oder Tabellen Einschränkungen unterstützt wird (das SQL_AT_ADD_CONSTRAINT Bit ist festgelegt):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (vollständig) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (vollständig) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (vollständig) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (vollständig) (ODBC 3,0)  
  
 SQL_ASYNC_MODE (ODBC 3,0)  
 Ein SQLUINTEGER-Wert, der die Ebene der asynchronen Unterstützung im Treiber angibt:  
  
 SQL_AM_CONNECTION = asynchrone Ausführung auf Verbindungs Ebene wird unterstützt. Entweder sind alle Anweisungs Handles, die einem gegebenen Verbindungs Handle zugeordnet sind, im asynchronen Modus, oder alle sind im synchronen Modus. Ein Anweisungs Handle für eine Verbindung kann sich nicht im asynchronen Modus befinden, während ein anderes Anweisungs Handle für dieselbe Verbindung im synchronen Modus ist und umgekehrt.  
  
 SQL_AM_STATEMENT = asynchrone Ausführung auf Anweisungs Ebene wird unterstützt. Einige Anweisungs Handles, die einem Verbindungs Handle zugeordnet sind, können sich im asynchronen Modus befinden, während sich andere Anweisungs Handles auf derselben Verbindung im synchronen Modus befinden.  
  
 SQL_AM_NONE = der asynchrone Modus wird nicht unterstützt.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3,0)  
 Eine SQLUINTEGER-Bitmaske, die das Verhalten des Treibers in Bezug auf die Verfügbarkeit der Zeilen Anzahl auflistet. Die folgenden Bitmasken werden in Verbindung mit dem Informationstyp verwendet:  
  
 SQL_BRC_ROLLED_UP = die Zeilen Anzahl für aufeinander folgende INSERT-, DELETE-oder Update-Anweisungen werden in einen Rollup ausgeführt. Wenn dieses Bit nicht festgelegt ist, sind die Zeilen Anzahl für jede Anweisung verfügbar.  
  
 SQL_BRC_PROCEDURES = die Zeilen Anzahl, sofern vorhanden, sind verfügbar, wenn ein Batch in einer gespeicherten Prozedur ausgeführt wird. Wenn die Anzahl der Zeilen verfügbar ist, können Sie je nach SQL_BRC_ROLLED_UP Bit ein Rollup oder eine individuelle Verfügbarkeit durchgeführt werden.  
  
 SQL_BRC_EXPLICIT = Zeilen Anzahl, sofern vorhanden, sind verfügbar, wenn ein Batch direkt durch Aufrufen von **SQLExecute** oder **SQLExecDirect**ausgeführt wird. Wenn die Anzahl der Zeilen verfügbar ist, können Sie je nach SQL_BRC_ROLLED_UP Bit ein Rollup oder eine individuelle Verfügbarkeit durchgeführt werden.  
  
## <a name="example"></a>Beispiel  
 **SQLGetInfo** gibt Listen der unterstützten Optionen als SQLUINTEGER-Bitmaske in **infovalueptr*zurück. Die Bitmaske für jede Option wird in Verbindung mit dem-Flag verwendet, um zu bestimmen, ob die Option unterstützt wird.  
  
 Beispielsweise könnte eine Anwendung den folgenden Code verwenden, um zu bestimmen, ob die Skalarfunktion der Teil Zeichenfolge von dem Treiber unterstützt wird, der der Verbindung zugeordnet ist.  
  
 Ein weiteres Beispiel für die Verwendung von **SQLGetInfo**finden Sie unter [SQLTables-Funktion](../../../odbc/reference/syntax/sqltables-function.md).  
  
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
 Zurückgeben der Einstellung eines Verbindungs Attributs  
 [SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Bestimmen, ob ein Treiber eine Funktion unterstützt  
 [SQLGetFunctions-Funktion](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Zurückgeben der Einstellung eines Anweisungs Attributs  
 [SQLGetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Zurückgeben von Informationen zu den Datentypen einer Datenquelle  
 [SQLGetTypeInfo-Funktion](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
