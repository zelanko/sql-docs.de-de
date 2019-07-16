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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b0e62e7aaba276643a2874a22e74a08214cfe51e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030657"
---
# <a name="sqlgetinfo-function"></a>SQLGetInfo-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetInfo** Gibt allgemeine Informationen zu den Treiber und die Datenquelle eine Verbindung zugeordnet.  
  
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
  
 *InfoType*  
 [Eingabe] Typ der Informationen.  
  
 *InfoValuePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Informationen zurückgegeben werden sollen. Je die *Informationsart* angefordert, die zurückgegebenen Informationen werden einer der folgenden: eine Null-terminierte Zeichenfolge, ein SQLUSMALLINT-Wert, eine SQLUINTEGER-Bitmaske, eine SQLUINTEGER-Flag, eine SQLUINTEGER-Binärwert, oder ein Wert der SQLULEN erstellt wurde.  
  
 Wenn die *Informationsart* Argument ist SQL_DRIVER_HDESC oder SQL_DRIVER_HSTMT, die *InfoValuePtr* Argument ist sowohl ein- und Ausgabe. (Siehe die Deskriptoren SQL_DRIVER_HDESC oder SQL_DRIVER_HSTMT weiter unten in diesem funktionsbeschreibung für Weitere Informationen.)  
  
 Wenn *InfoValuePtr* NULL ist, *StringLengthPtr* gibt die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *InfoValuePtr*.  
  
 *BufferLength*  
 [Eingabe] Länge der \* *InfoValuePtr* Puffer. Wenn der Wert in  *\*InfoValuePtr* ist es sich nicht um eine Zeichenfolge oder, wenn *InfoValuePtr* ist ein null-Zeiger der *Pufferlänge* Argument wird ignoriert. Der Treiber setzt voraus, dass die Größe des  *\*InfoValuePtr* ist SQLUSMALLINT oder SQLUINTEGER, basierend auf den *Informationsart*. Wenn  *\*InfoValuePtr* ist eine Unicodezeichenfolge (beim Aufrufen von **SQLGetInfoW**), wird die *Pufferlänge* Argument muss eine gerade Zahl; sein, wenn nicht der Fall, SQLSTATE HY090 () Ungültige Zeichenfolgen- oder Pufferlänge) wird zurückgegeben.  
  
 *StringLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) zurück in zurück zur Verfügung **InfoValuePtr*.  
  
 Für Daten im Zeichenformat, wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *Pufferlänge*, die Informationen in \* *InfoValuePtr* auf abgeschnitten  *BufferLength* Bytes abzüglich der Länge von Null-Terminierung vorliegt, Zeichen und Null-terminiert ist vom Treiber.  
  
 Für alle anderen Typen von Daten, die den Wert der *Pufferlänge* wird ignoriert, und der Treiber geht davon aus, die Größe des \* *InfoValuePtr* ist SQLUSMALLINT oder SQLUINTEGER, je nach den  *Informationsart*.  
  
## <a name="return-value"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetInfo** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, zurück ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DBC auf, und eine *behandeln* von *ConnectionHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLGetInfo** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Puffer \* *InfoValuePtr* nicht groß genug war, um alle angeforderten Informationen zurückzugeben. Aus diesem Grund wurden die Informationen abgeschnitten. Die Länge der angeforderten Informationen in den ungekürzten Form wird zurückgegeben, **StringLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) die Art der Informationen im angeforderten *Informationsart* ist eine geöffnete Verbindung erforderlich. Von den Informationstypen, die von ODBC reserviert wird können nur SQL_ODBC_VER ohne eine geöffnete Verbindung zurückgegeben werden.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY024|Ungültiger Attributwert|(DM) die *Informationsart* Argument war SQL_DRIVER_HSTMT und der Wert verweist *InfoValuePtr* war keinem gültigen Anweisungshandle.<br /><br /> (DM) die *Informationsart* Argument war SQL_DRIVER_HDESC und der Wert verweist *InfoValuePtr* war es sich nicht um eine gültige Deskriptorhandles.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) für Argument angegebene Wert *Pufferlänge* war kleiner als 0.<br /><br /> (DM) der angegebene Wert für *Pufferlänge* wurde eine ungerade Zahl ist, und  *\*InfoValuePtr* wurde von einem Unicode-Datentyp.|  
|HY096|Informationstyp außerhalb des gültigen Bereichs|Der angegebene Wert für das Argument *Informationsart* war nicht gültig für die Version von ODBC, die vom Treiber unterstützt werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feld, die nicht implementiert.|Der angegebene Wert für das Argument *Informationsart* wurde ein treiberspezifische-Wert, der vom Treiber nicht unterstützt wird.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber, der die entspricht der *ConnectionHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 In "Informationstypen" weiter unten in diesem Abschnitt werden die aktuell definierten Informationstypen angezeigt. Es wird erwartet, dass mehr zur Nutzung von unterschiedlichen Datenquellen definiert werden. ODBC ist eine Palette an Informationstypen reserviert. Treiberentwickler müssen Werte für die eigene Verwendung treiberspezifische aus Open Group reservieren. **SQLGetInfo** führt keine Unicode-Konvertierung oder *thunking* (finden Sie unter [Anhang A: ODBC-Fehlercodes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md) von der *ODBC Programmer's Reference*) für treiberdefinierten *Infotypen*. Weitere Informationen finden Sie unter [treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md). Das Format der Informationen in zurückgegebenen \* *InfoValuePtr* hängt von der *Informationsart* angefordert. **SQLGetInfo** Informationen in einem der fünf verschiedenen Formaten zurück:  
  
-   Eine Null-terminierte Zeichenfolge  
  
-   Ein Wert SQLUSMALLINT  
  
-   Eine Bitmaske SQLUINTEGER  
  
-   Eine SQLUINTEGER-Wert  
  
-   Ein Binärwert SQLUINTEGER  
  
 Das Format für jedes der folgenden Informationen wird in der Beschreibung des aufgeführt. Die Anwendung muss den zurückgegebenen Wert umgewandelt **InfoValuePtr* entsprechend. Ein Beispiel dafür, wie eine Anwendung Daten von einer Bitmaske SQLUINTEGER abrufen kann finden Sie unter "Code Example."  
  
 Ein Treiber muss es sich um einen Wert für jeden Datentyp zurückgeben, die in der folgenden Tabelle definiert ist. Wenn ein Typ von Informationen an den Treiber oder die Datenquelle nicht anwendbar ist, gibt der Treiber einen der in der folgenden Tabelle aufgeführten Werte zurück.  
  
 Zeichenfolge ("Y" oder "N")  
 "N"  
  
 Zeichenfolge (nicht "Y" oder "N")  
 Leere Zeichenfolge  
  
 SQLUSMALLINT  
 0  
  
 SQLUINTEGER Bitmaske oder SQLUINTEGER Binärwert  
 0L  
  
 Angenommen, eine Datenquelle Prozeduren nicht unterstützt **SQLGetInfo** gibt zurück, in der folgenden Tabelle die Werte der aufgeführten Werte *Informationsart* , beziehen sich auf Verfahren.  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 Leere Zeichenfolge  
  
 **SQLGetInfo** SQLSTATE HY096 zurückgegeben (ungültiges Argument-Wert) für die Werte der *Informationsart* , liegen im Bereich der Informationstypen, die für die Verwendung von ODBC reserviert, jedoch sind nicht definiert, von der Version von ODBC, die vom Treiber unterstützt werden. Um zu bestimmen, welche Version der ODBC-Treiber entspricht, eine Anwendung ruft **SQLGetInfo** mit dem Typ der SQL_DRIVER_ODBC_VER-Informationen. **SQLGetInfo** SQLSTATE HYC00 zurückgibt (optionales Feature nicht implementiert) für die Werte der *Informationsart* , liegen im Bereich der Informationstypen, die für die Treiber-spezifische Verwendung reserviert, jedoch werden vom Treiber nicht unterstützt.  
  
 Alle Aufrufe von **SQLGetInfo** erfordert eine offene Verbindung, außer wenn die *Informationsart* SQL_ODBC_VER, wodurch die Version des Treiber-Managers ist.  
  
## <a name="information-types"></a>Informationstypen  
 Dieser Abschnitt enthält von unterstützten Informationstypen **SQLGetInfo**. Informationstypen sind kategorisch gruppiert und alphabetisch sortiert. Typen von Informationen, die hinzugefügt oder ODBC 3. umbenannt wurden *.x* sind ebenfalls aufgeführt.  
  
## <a name="driver-information"></a>Treiberinformationen  
 Die folgenden Werte aus der *Informationsart* Argument Zurückgeben von Informationen zu den ODBC-Treiber, z. B. die Anzahl der aktiven Anweisungen, der Name der Datenquelle und die Kompatibilitätsstufe aus Interface-Standards:  
  
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
>  Bei der Implementierung **SQLGetInfo**, ein Treiber kann die Leistung verbessern, indem minimiert die Anzahl der Fälle, in denen Informationen gesendet oder vom Server angefordert wird.  
  
## <a name="dbms-product-information"></a>DBMS-Produktinformationen  
 Die folgenden Werte aus der *Informationsart* Argument Zurückgeben von Informationen zu den DBMS-Produkten wie DBMS-Name und Version:  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>Datenquelleninformationen  
 Die folgenden Werte aus der *Informationsart* Argument Zurückgeben von Informationen über die Datenquelle, z. B. Cursoreigenschaften und Transaktionsfunktionen:  
  
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
 Die folgenden Werte aus der *Informationsart* Argument Zurückgeben von Informationen zu den SQL-Anweisungen, die von der Datenquelle unterstützt. Die SQL-Syntax der einzelnen Funktionen beschrieben, die nach diesen Informationstypen ist die SQL-92-Syntax. Solche Informationen werden die gesamte SQL-92-Grammatik nicht ausführlich beschrieben. Stattdessen beschreiben sie die Teile der Grammatik, die Quellen für die Daten in der Regel verschiedene Ebenen der Unterstützung bieten. Insbesondere werden die meisten der DDL-Anweisung in SQL-92 behandelt.  
  
 Anwendungen sollten bestimmen die allgemeine Ebene der unterstützten Grammatik von den Informationstyp SQL_SQL_CONFORMANCE und der anderen Typen von Informationen verwenden, um Variationen aus der angegebenen Standards-Compliance-Ebene zu bestimmen.  
  
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
  
## <a name="sql-limits"></a>Einschränkungen für SQL  
 Die folgenden Werte aus der *Informationsart* Argument Zurückgeben von Informationen zu den Grenzwerten für Bezeichner und Klauseln in SQL-Anweisungen, z. B. die maximale Länge von IDs und die maximale Anzahl von Spalten in einer select-Liste angewendet. Einschränkungen können durch den Treiber oder die Datenquelle festgelegt werden.  
  
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
  
## <a name="scalar-function-information"></a>Skalarfunktion-Informationen  
 Die folgenden Werte aus der *Informationsart* Argument Zurückgeben von Informationen zu den skalaren Funktionen, die von der Datenquelle und der Treiber unterstützt werden. Weitere Informationen zu den skalaren Funktionen, finden Sie unter [Anhang E: Skalare Funktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>Informationen zur Konvertierung  
 Die folgenden Werte aus der *Informationsart* Argument zurück, eine Liste der SQL-Datentypen, kann die Datenquelle mit den angegebenen SQL-Datentyp konvertieren, die **konvertieren** skalare Funktion:  
  
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
  
## <a name="information-types-added-for-odbc-3x"></a>Informationstypen hinzugefügt für ODBC 3.x  
 Die folgenden Werte aus der *Informationsart* Argument wurde für ODBC 3. *.x*:  
  
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
  
## <a name="information-types-renamed-for-odbc-3x"></a>Informationstypen, die umbenannt für ODBC 3.x  
 Die folgenden Werte aus der *Informationsart* Argument wurde für ODBC 3. umbenannt *.x*.  
  
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
  
## <a name="information-types-deprecated-in-odbc-3x"></a>Informationstypen, die als veraltet markiert, in ODBC 3.x  
 Die folgenden Werte aus der *Informationsart* Argument sind veraltet in ODBC 3. *.x*. ODBC 3. *.x* Treiber müssen weiterhin unterstützen diese Typen von Informationen zur Abwärtskompatibilität mit ODBC 2. *.x* Anwendungen. (Weitere Informationen zu diesen Projekttypen finden Sie unter [SQLGetInfo-Unterstützung](../../../odbc/reference/appendixes/sqlgetinfo-support.md) in Anhang G: Treiber-Richtlinien für Abwärtskompatibilität.)  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>Informationen von Typbeschreibungen  
 Die folgende Tabelle enthält alphabetisch jeden Datentyp, der Version von ODBC in der sie eingeführt wurde und eine Beschreibung ein.  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 Eine Zeichenfolge: Wenn der Benutzer alle Prozeduren, die vom ausgeführt werden können "J" **SQLProcedures**; "N", wenn Prozeduren möglicherweise zurückgegeben, dass der Benutzer nicht ausgeführt werden kann.  
  
 SQL_ACCESSIBLE_TABLES(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn der Benutzer **wählen** Berechtigungen, um alle Tabellen, die vom **SQLTables**; "N", wenn Tabellen möglicherweise zurückgegeben, dass der Benutzer zugreifen kann.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Ein SQLUSMALLINT-Wert, der angibt, die maximale Anzahl von aktiven Umgebungen, die der Treiber unterstützt werden. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die Unterstützung für Aggregationsfunktionen auflisten:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer alle diese Optionen zurückgegeben, da unterstützt.  
  
 SQL_ALTER_DOMAIN(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **ALTER DOMAIN** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert. Ein vollständige SQL-92-Ebene-kompatiblen Treiber wird alle die Bitmasken immer zurückgegeben werden. Ein Rückgabewert von "0" bedeutet, dass die **ALTER DOMAIN** Anweisung wird nicht unterstützt.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = hinzufügen, die eine Einschränkung wird unterstützt (vollständige Ebene)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter der Domäne > \<Set Domain Default-Klausel > wird unterstützt (vollständige Ebene)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<Definition von Einschränkungsklausel-Name > wird unterstützt, für die Benennung von Einschränkung (mittlere Ebene)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<Drop Domäne Constraint-Klausel > wird unterstützt (vollständige Ebene)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter der Domäne > \<Drop Domain Default-Klausel > wird unterstützt (vollständige Ebene)  
  
 Geben Sie die folgenden Bits unterstützten \<Einschränkung Attribute > Wenn \<Einschränkung hinzufügen > unterstützt wird (das SQL_AD_ADD_DOMAIN_CONSTRAINT Bit festgelegt ist):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (vollständige Stufe) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (vollständige Stufe) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (vollständige Stufe) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (vollständige Stufe)  
  
 SQL_ALTER_TABLE(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **ALTER TABLE** -Anweisung von der Datenquelle unterstützt.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<Spalte hinzufügen >-Klausel wird unterstützt, mit der Funktion zum Angeben der spaltensortierung (vollständige Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<Spalte hinzufügen >-Klausel wird unterstützt, mit der Funktion an die Spalte ist standardmäßig (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<Spalte hinzufügen > wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<Spalte hinzufügen >-Klausel wird unterstützt, mit der Einrichtung spalteneinschränkungen (FIPS Transitional Stufe) angeben (ODBC-Version 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<tabelleneinschränkung hinzufügen >-Klausel wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<Einschränkungsdefinition-Name > ist für die Benennung von Spalten- und tabelleneinschränkungen (mittlere Ebene) unterstützt (ODBC-Version 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<Drop Spalte > CASCADE wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<onlinespaltenänderung > \<Drop Column-Standard-Klausel > wird unterstützt (mittlere Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<Drop Spalte > RESTRICT wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<Drop Spalte > RESTRICT wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<onlinespaltenänderung > \<Satz Spalte Default-Klausel > wird unterstützt (mittlere Ebene) (ODBC-Version 3.0)  
  
 Die folgenden Bits Geben Sie die Unterstützung \<Einschränkung Attribute > Wenn angeben von Spalten- oder tabelleneinschränkungen unterstützt wird (das SQL_AT_ADD_CONSTRAINT Bit festgelegt ist):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (vollständige Ebene) (ODBC-Version 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (vollständige Ebene) (ODBC-Version 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (vollständige Ebene) (ODBC-Version 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (vollständige Ebene) (ODBC-Version 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 Eine SQLUINTEGER-Wert, der angibt, ob der Treiber Funktionen asynchron auf dem Verbindungshandle ausgeführt werden kann.  
  
 SQL_ASYNC_DBC_CAPABLE = der Treiber kann die Verbindungsfunktionen asynchron ausgeführt.  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = der Treiber kann nicht ausgeführt werden Verbindungsfunktionen asynchron.  
  
 SQL_ASYNC_MODE(ODBC 3.0)  
 Eine SQLUINTEGER-Wert, der die asynchrone Unterstützung im Treiber angibt:  
  
 SQL_AM_CONNECTION = Verbindung wird auf asynchrone Ausführung unterstützt. Alle Anweisungshandles, die ein Handle für die angegebene Verbindung zugeordnet sind, im asynchronen Modus oder alle im synchronen Modus sind. Ein Anweisungshandle für eine Verbindung darf nicht im asynchronen Modus sein, während ein anderes Anweisungshandle für dieselbe Verbindung im synchronen Modus (und umgekehrt) ist.  
  
 SQL_AM_STATEMENT =-Anweisung auf asynchrone Ausführung unterstützt wird. Im asynchronen Modus können einige Anweisungshandle eines Verbindungshandles zugeordnet sein, während andere Anweisungshandles auf die gleiche Verbindung im synchronen Modus sind.  
  
 SQL_AM_NONE = asynchroner Modus wird nicht unterstützt.  
  
 SQL_ASYNC_NOTIFICATION  
 Eine SQLUINTEGER-Wert, der angibt, ob der Treiber die asynchrone Benachrichtigung unterstützt:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE** asynchrone Ausführung Benachrichtigung wird vom Treiber unterstützt.  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE** asynchrone Ausführung Benachrichtigung wird vom Treiber nicht unterstützt.  
  
 Es gibt zwei Kategorien von asynchronen Vorgängen ODBC: Verbindung asynchrone Vorgänge und -Anweisung auf der Ebene asynchrone Vorgänge.  Wenn ein Treiber SQL_ASYNC_NOTIFICATION_CAPABLE zurückgibt, muss es Benachrichtigung für alle APIs unterstützen, die sie asynchron ausgeführt werden kann.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die das Verhalten des Treibers in Bezug auf die Verfügbarkeit der Zeile listet zählt. Die folgenden Bitmasken werden zusammen mit den Informationstyp verwendet:  
  
 SQL_BRC_ROLLED_UP = der Zeilenanzahl für aufeinander folgende INSERT-, DELETE- oder UPDATE-Anweisungen in einem Rollup enthalten sind. Wenn dieses Bit nicht festgelegt ist, sind die Zeilenanzahl für jede Anweisung verfügbar.  
  
 SQL_BRC_PROCEDURES Zeilenanzahl, =, sind ggf. verfügbar, wenn ein Batch in einer gespeicherten Prozedur ausgeführt wird. Wenn Zeilenanzahl verfügbar sind, können sie nach oben oder einzeln verfügbar sind, abhängig von der SQL_BRC_ROLLED_UP Bit ein Rollback ausgeführt werden.  
  
 SQL_BRC_EXPLICIT Zeilenanzahl, =, sind ggf. verfügbar, wenn ein Batch ausgeführt wird, direkt durch Aufrufen **SQLExecute** oder **SQLExecDirect**. Wenn Zeilenanzahl verfügbar sind, können sie nach oben oder einzeln verfügbar sind, abhängig von der SQL_BRC_ROLLED_UP Bit ein Rollback ausgeführt werden.  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die treiberunterstützung für Batches auflisten. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Ebene unterstützt wird:  
  
 SQL_BS_SELECT_EXPLICIT = der Treiber unterstützt die explizite Batches, die Resultsets können haben Generieren von Anweisungen.  
  
 SQL_BS_ROW_COUNT_EXPLICIT = der Treiber unterstützt explizite Batches, die Anzahl von Zeilen Generieren von Anweisungen haben kann.  
  
 SQL_BS_SELECT_PROC = der Treiber unterstützt explizite Prozeduren, die Resultsets können haben Generieren von Anweisungen.  
  
 SQL_BS_ROW_COUNT_PROC = der Treiber unterstützt explizite Prozeduren, die Anzahl von Zeilen Generieren von Anweisungen haben können.  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Vorgänge, die über denen Lesezeichen beibehalten auflisten.  
  
 Die folgenden Bitmasken werden zusammen mit dem Flag verwendet, um zu bestimmen, über die Optionen Lesezeichen speichern:  
  
 SQL_BP_CLOSE = Lesezeichen sind gültig, nachdem eine Anwendung ruft **SQLFreeStmt** mit der Option SQL_CLOSE oder **SQLCloseCursor** auf den mit einer Anweisung verknüpften Cursor zu schließen.  
  
 SQL_BP_DELETE = das Lesezeichen, eine Zeile ist ungültig, nachdem die Zeile gelöscht wurde.  
  
 SQL_BP_DROP = Lesezeichen sind gültig, nachdem eine Anwendung ruft **SQLFreeHandle** mit einem *HandleType* SQL_HANDLE_STMT auf, um eine Anweisung zu löschen.  
  
 SQL_BP_TRANSACTION = Lesezeichen sind gültig, nachdem eine Anwendung ein Commit oder Rollback einer Transaktion.  
  
 SQL_BP_UPDATE = das Lesezeichen, eine Zeile ist ungültig, nachdem eine Spalte in dieser Zeile aktualisiert worden ist, einschließlich der Schlüsselspalten.  
  
 SQL_BP_OTHER_HSTMT = ein Lesezeichen, das eine zugeordnete Anweisung kann mit einer anderen Anweisung verwendet werden. Es sei denn, SQL_BP_CLOSE oder SQL_BP_DROP angegeben ist, muss der Cursor für die erste Anweisung geöffnet sein.  
  
 SQL_CATALOG_LOCATION(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die Position des Katalogs in einem qualifizierten Tabellennamen angibt:  
  
 SQL_CL_STARTSQL_CL_END  
  
 Beispielsweise gibt ein Xbase-Treiber SQL_CL_START zurück, da der Name des Verzeichnisses (Katalog) am Anfang der Tabellenname, wie \EMPDATA\EMP ist. DBF. Ein ORACLE-Server-Treiber gibt SQL_CL_END zurück, da es sich bei der Katalog am Ende den Namen der Tabelle in diesem Beispiel ist ADMIN.EMP@EMPDATA.  
  
 Ein vollständige SQL-92 Level-konformen Treiber wird SQL_CL_START immer zurückgegeben werden. Der Wert 0 wird zurückgegeben, wenn Kataloge nicht von der Datenquelle unterstützt werden. Um zu bestimmen, ob Kataloge unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit dem Typ der SQL_CATALOG_NAME-Informationen.  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_QUALIFIER_LOCATION.  
  
 SQL_CATALOG_NAME(ODBC 3.0)  
 Eine Zeichenfolge: "Y", wenn der Server Katalognamen oder "N" unterstützt, wenn dies nicht der Fall.  
  
 Ein vollständige SQL-92 Level-konformen-Treiber wird immer mit "Y" zurückgegeben.  
  
 SQL_CATALOG_NAME_SEPARATOR(ODBC 1.0)  
 Eine Zeichenfolge: das Zeichen oder Zeichen an, die die Datenquelle definiert wird, als Trennzeichen zwischen einen Katalognamen und der qualifizierte Name-Element, das folgt, oder er vorangestellt ist.  
  
 Wenn Kataloge nicht von der Datenquelle unterstützt werden, wird eine leere Zeichenfolge zurückgegeben. Um zu bestimmen, ob Kataloge unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit dem Typ der SQL_CATALOG_NAME-Informationen. Ein vollständige SQL-92-Level-konformen-Treiber gibt immer zurück. ".".  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_QUALIFIER_NAME_SEPARATOR.  
  
 SQL_CATALOG_TERM(ODBC 1.0)  
 Eine Zeichenfolge mit den Datenquelle Herstellernamen für einen Katalog; z. B. "Datenbank" oder "Directory". Diese Zeichenfolge kann in der oberen, unteren, oder eine gemischte Groß-sein.  
  
 Wenn Kataloge nicht von der Datenquelle unterstützt werden, wird eine leere Zeichenfolge zurückgegeben. Um zu bestimmen, ob Kataloge unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit dem Typ der SQL_CATALOG_NAME-Informationen. Ein vollständige SQL-92 Level-konformen-Treiber wird immer zurückgegeben "catalog".  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_QUALIFIER_TERM.  
  
 SQL_CATALOG_USAGE(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske aufzählen die Anweisungen in denen Kataloge verwendet werden können.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, wo die Kataloge verwendet werden kann:  
  
 SQL_CU_DML_STATEMENTS = Volltextkataloge werden in allen Data Manipulation Language-Anweisungen unterstützt: **Wählen Sie**, **einfügen**, **aktualisieren**, **löschen**, und falls unterstützt, **wählen Sie für UPDATE** und positioniert, Update- und Delete -Anweisungen.  
  
 SQL_CU_PROCEDURE_INVOCATION = Volltextkataloge werden in der aufrufanweisung für ODBC-Prozeduren unterstützt.  
  
 SQL_CU_TABLE_DEFINITION = Volltextkataloge werden in allen Table-Anweisungen der Definition unterstützt: **ERSTELLT eine Tabelle**, **ERSTELLUNGSANSICHT**, **ALTER TABLE**, **TABELLENLÖSCHUNG**, und **DROP VIEW**.  
  
 SQL_CU_INDEX_DEFINITION = Volltextkataloge werden in alle indexanweisungen Definition unterstützt: **INDEXERSTELLUNG** und **DROP INDEX**.  
  
 SQL_CU_PRIVILEGE_DEFINITION = Volltextkataloge werden in alle Berechtigungen datendefinitionsanweisungen unterstützt: **GRANT** und **widerrufen**.  
  
 Der Wert 0 wird zurückgegeben, wenn Kataloge nicht von der Datenquelle unterstützt werden. Um zu bestimmen, ob Kataloge unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit dem Typ der SQL_CATALOG_NAME-Informationen. Ein vollständige SQL-92 Level-konformen-Treiber gibt immer eine Bitmaske mit allen diesen festgelegten Bits zurück.  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_QUALIFIER_USAGE.  
  
 SQL_COLLATION_SEQ (ODBC 3.0)  
 Der Name der die Sortierreihenfolge. Dies ist eine Zeichenfolge, die den Namen der standardsortierung für den Standardzeichensatz für diesen Server angibt (z. B. "ISO 8859-1" oder EBCDIC). Wenn dies nicht bekannt ist, wird eine leere Zeichenfolge zurückgegeben. Ein vollständige SQL-92 Level-konformen-Treiber wird immer eine nicht leere Zeichenfolge zurückgegeben.  
  
 SQL_COLUMN_ALIAS(ODBC 2.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle Spaltenaliase unterstützt; andernfalls "N".  
  
 Ein Spaltenalias ist ein alternativer Name, der für eine Spalte in der select-Liste mit einer AS-Klausel angegeben werden kann. Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer mit "Y" zurückgegeben.  
  
 SQL_CONCAT_NULL_BEHAVIOR(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der angibt, wie die Datenquelle für die Verkettung von NULL behandelt valued Zeichendatenspalten mit Werten ungleich NULL-Zeichen-datentypspalten:  
  
 SQL_CB_NULL = Ergebnis NULL-Werten ist.  
  
 SQL_CB_NON_NULL = Ergebnis ist die Verkettung von Werten ungleich NULL-Spalte oder Spalten.  
  
 Ein SQL-92-Eintrag auf konformen Treiber wird SQL_CB_NULL immer zurückgegeben werden.  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_ DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 Eine Bitmaske SQLUINTEGER. Die Bitmaske gibt an, die Konvertierungen, die von der Datenquelle unterstützten Daten mit der **konvertieren** Skalarfunktion für Daten des Typs mit dem Namen in der *Informationsart*. Wenn die Bitmaske gleich NULL ist, unterstützt die Datenquelle eine Konvertierung von Daten des genannten Typs, einschließlich der Konvertierung in den gleichen Datentyp nicht.  
  
 Um festzustellen, ob eine Datenquelle die Konvertierung von SQL_INTEGER Daten in den SQL_BIGINT-Datentyp unterstützt, z. B. eine Anwendung ruft **SQLGetInfo** mit der *Informationsart* von SQL_CONVERT_INTEGER. Die Anwendung führt eine **und** Vorgang mit dem zurückgegebene Bitmaske und SQL_CVT_BIGINT. Wenn der resultierende Wert ungleich NULL ist, wird die Konvertierung unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Konvertierungen unterstützt werden:  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5) SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) SQL_CVT_FLOAT (ODBC 1.0) SQL_CVT_INTEGER (ODBC 1.0) SQL _CVT_INTERVAL_YEAR_MONTH (ODBC 3.0) SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0) SQL_CVT_LONGVARBINARY (ODBC 1.0) SQL_CVT_LONGVARCHAR (ODBC 1.0) SQL_CVT_NUMERIC (ODBC 1.0) SQL_CVT_REAL ODBC 1.0) SQL_CVT_SMALLINT (ODBC 1.0) SQL_CVT_TIME (ODBC 1.0) SQL_CVT_ ZEITSTEMPEL (ODBC 1.0) SQL_CVT_TINYINT (ODBC 1.0) SQL_CVT_VARBINARY (ODBC 1.0) SQL_CVT_VARCHAR (ODBC 1.0)  
  
 SQL_CONVERT_FUNCTIONS(ODBC 1.0)  
 Eine SQLUINTEGER-Bitmaske Aufzählen der skalaren Konvertierungsfunktionen, die von der Treiber und der zugeordneten Datenquelle unterstützt.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Funktionen für die typkonvertierung unterstützt werden:  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der angibt, ob abhängige Tabellennamen unterstützt werden:  
  
 SQL_CN_NONE = Korrelation, die Namen werden nicht unterstützt.  
  
 SQL_CN_DIFFERENT = Korrelation Namen werden unterstützt, jedoch müssen sich von den Namen der Tabellen Währungseinheiten unterscheiden.  
  
 SQL_CN_ANY = Korrelation Namen werden unterstützt und können einen beliebigen gültigen benutzerdefinierten Namen.  
  
 Ein SQL-92-Eintrag auf konformen Treiber wird SQL_CN_ANY immer zurückgegeben werden.  
  
 SQL_CREATE_ASSERTION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **erstellen ASSERTION** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CA_CREATE_ASSERTION  
  
 Die folgenden Bits das unterstützte Einschränkung-Attribut angeben, wenn die Möglichkeit, die Attribute der Einschränkung explizit angeben unterstützt wird (siehe die Informationstypen SQL_ALTER_TABLE und SQL_CREATE_TABLE):  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 Ein vollständige SQL-92 Level-konformen-Treiber wird immer all diese Optionen zurückgegeben, als unterstützt. Ein Rückgabewert von "0" bedeutet, dass die **erstellen ASSERTION** Anweisung wird nicht unterstützt.  
  
 SQL_CREATE_CHARACTER_SET(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **ZEICHENSATZ erstellen** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 Ein vollständige SQL-92 Level-konformen-Treiber wird immer all diese Optionen zurückgegeben, als unterstützt. Ein Rückgabewert von "0" bedeutet, dass die **ZEICHENSATZ erstellen** Anweisung wird nicht unterstützt.  
  
 SQL_CREATE_COLLATION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **erstellen SORTIERUNG** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CCOL_CREATE_COLLATION  
  
 Diese Option wird ein vollständige SQL-92 Level-konformen Treiber wie unterstützt immer zurückgegeben werden. Ein Rückgabewert von "0" bedeutet, dass die **SORTIERREIHENFOLGE erstellen** Anweisung wird nicht unterstützt.  
  
 SQL_CREATE_DOMAIN(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **Domäne erstellen** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CDO_CREATE_DOMAIN = der erstellen-DOMAIN-Anweisung wird unterstützt (Intermediate-Stufe).  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<Einschränkungsdefinition-Name > ist für die Benennung von Einschränkungen (mittlere Ebene) unterstützt.  
  
 Die folgenden Bits Geben Sie die Möglichkeit zum Erstellen der Spalte Einschränkungen: SQL_CDO_DEFAULT = angeben von Einschränkungen wird unterstützt (Intermediate-Stufe) SQL_CDO_CONSTRAINT = angeben von Standardwerten für Domäne unterstützt wird (Intermediate-Stufe) SQL_CDO_COLLATION = Angeben einer Sortierung der Domäne wird unterstützt (vollständige Ebene)  
  
 Die folgenden Bits geben die Einschränkung der unterstützten Attribute aus, wenn das Angeben von Einschränkungen unterstützt wird (SQL_CDO_DEFAULT festgelegt ist):  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (vollständige Stufe) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (vollständige Stufe) SQL_CDO_CONSTRAINT_DEFERRABLE (vollständige Stufe) SQL_CDO_CONSTRAINT_NON_DEFERRABLE (vollständige Stufe)  
  
 Ein Rückgabewert von "0" bedeutet, dass die **Domäne erstellen** Anweisung wird nicht unterstützt.  
  
 SQL_CREATE_SCHEMA(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **CREATE SCHEMA** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 Ein SQL-92-Intermediate-Ebene-konformen-Treiber wird immer die Optionen SQL_CS_CREATE_SCHEMA und SQL_CS_AUTHORIZATION zurückgegeben, als unterstützt. Diese müssen auch auf der Ebene der SQL-92-Eintrag, aber nicht unbedingt als SQL-Anweisungen unterstützt werden. Ein vollständige SQL-92 Level-konformen-Treiber wird immer all diese Optionen zurückgegeben, als unterstützt.  
  
 SQL_CREATE_TABLE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **CREATE TABLE** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CT_CREATE_TABLE = die CREATE TABLE-Anweisung wird unterstützt. (Entry Level)  
  
 SQL_CT_TABLE_CONSTRAINT = tabelleneinschränkungen angeben wird unterstützt (FIPS Transitional Stufe)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = die \<Einschränkungsdefinition-Name >-Klausel wird für die Benennung von Spalten- und tabelleneinschränkungen (mittlere Ebene) unterstützt.  
  
 Die folgenden Bits Geben Sie die Möglichkeit zum Erstellen von temporären Tabellen:  
  
 SQL_CT_COMMIT_PRESERVE = der gelöschte Zeilen werden nach dem Commit beibehalten. (Vollständige Stufe) SQL_CT_COMMIT_DELETE = der gelöschte Zeilen werden nach dem Commit gelöscht. (Vollständige Stufe) SQL_CT_GLOBAL_TEMPORARY = globale temporäre Tabellen erstellt werden können. (Vollständige Stufe) SQL_CT_LOCAL_TEMPORARY = lokale temporäre Tabellen erstellt werden können. (Vollständige Stufe)  
  
 Die folgenden Bits Geben Sie die Möglichkeit, spalteneinschränkungen zu erstellen:  
  
 SQL_CT_COLUMN_CONSTRAINT = spalteneinschränkungen angeben wird unterstützt (FIPS Transitional Stufe) SQL_CT_COLUMN_DEFAULT = Standardwerte für Spalten angeben, wird unterstützt (FIPS Transitional Stufe) SQL_CT_COLUMN_COLLATION = angeben der spaltensortierung ist unterstützt (vollständige Stufe)  
  
 Die folgenden Bits geben die Einschränkung der unterstützten Attribute aus, wenn das Angeben von Spalten- oder tabelleneinschränkungen unterstützt wird:  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (vollständige Stufe) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (vollständige Stufe) SQL_CT_CONSTRAINT_DEFERRABLE (vollständige Stufe) SQL_CT_CONSTRAINT_NON_DEFERRABLE (vollständige Stufe)  
  
 SQL_CREATE_TRANSLATION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **erstellen Übersetzung** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 Ein vollständige SQL-92 Level-konformen-Treiber wird immer diese Optionen zurückgegeben, als unterstützt. Ein Rückgabewert von "0" bedeutet, dass die **erstellen Übersetzung** Anweisung wird nicht unterstützt.  
  
 SQL_CREATE_VIEW(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **CREATE VIEW** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 Ein Rückgabewert von "0" bedeutet, dass die **CREATE VIEW** Anweisung wird nicht unterstützt.  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer die Optionen SQL_CV_CREATE_VIEW und SQL_CV_CHECK_OPTION zurückgegeben, da unterstützt.  
  
 Ein vollständige SQL-92 Level-konformen-Treiber wird immer all diese Optionen zurückgegeben, als unterstützt.  
  
 SQL_CURSOR_COMMIT_BEHAVIOR(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der angibt wie eine **COMMIT** Vorgang wirkt sich auf Cursor und vorbereitete Anweisungen in der Datenquelle (das Verhalten der Datenquelle beim commit einer Transaktion).  
  
 Der Wert dieses Attributs spiegeln den aktuellen Status der Einstellung für die nächsten: SQL_COPT_SS_PRESERVE_CURSORS.  
  
 SQL_CB_DELETE = Close Cursor und vorbereitete Anweisungen zu löschen. Um den Cursor zu verwenden. in diesem Fall die Anwendung muss reprepare und führen Sie die Anweisung erneut aus.  
  
 SQL_CB_CLOSE = Close Cursor. Die Anwendung kann für vorbereitete Anweisungen Aufrufen **SQLExecute** für die Anweisung ohne **SQLPrepare** erneut aus. Der Standardwert für den SQL ODBC-Treiber ist SQL_CB_CLOSE. Dies bedeutet, dass der SQL-ODBC-Treiber die Cursor schließt, beim commit einer Transaktion geschlossen wird.  
  
 SQL_CB_PRESERVE Preserve-Cursor in der gleichen Position wie zuvor = die **COMMIT** Vorgang. Die Anwendung kann weiterhin zum Abrufen von Daten, oder schließen Sie den Cursor kann und die Anweisung erneut ausführen, ohne neu vorbereiten.  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der gibt an, wie eine **ROLLBACK** Vorgang wirkt sich auf Cursor und vorbereitete Anweisungen in der Datenquelle:  
  
 SQL_CB_DELETE = Close Cursor und vorbereitete Anweisungen zu löschen. Um den Cursor zu verwenden. in diesem Fall die Anwendung muss reprepare und führen Sie die Anweisung erneut aus.  
  
 SQL_CB_CLOSE = Close Cursor. Die Anwendung kann für vorbereitete Anweisungen Aufrufen **SQLExecute** für die Anweisung ohne **SQLPrepare** erneut aus.  
  
 SQL_CB_PRESERVE Preserve-Cursor in der gleichen Position wie zuvor = die **ROLLBACK** Vorgang. Die Anwendung kann weiterhin zum Abrufen von Daten, oder schließen Sie den Cursor und führen Sie die Anweisung erneut aus, ohne repreparing es werden können.  
  
 SQL_CURSOR_SENSITIVITY FEST (ODBC 3.0)  
 Eine SQLUINTEGER-Wert, der die Unterstützung für Cursor Vertraulichkeit angibt:  
  
 SQL_INSENSITIVE = alle Cursor auf die Anweisung Handle anzeigen, die das Resultset ohne spiegeln alle Änderungen, die vorgenommen wurden, durch einen anderen Cursor innerhalb der gleichen Transaktion ausgeführt.  
  
 SQL_UNSPECIFIED = ist nicht angegeben, ob Cursor über das Anweisungshandle die Änderungen sichtbar, die ein Resultset, die von einem anderen Cursor innerhalb der gleichen Transaktion vorgenommen wurden. Cursor für das Anweisungshandle möglicherweise keine, einige oder alle diese Änderungen sichtbar.  
  
 SQL_SENSITIVE = Cursor sind empfindlich gegenüber Änderungen, die von anderen Cursorn innerhalb derselben Transaktion vorgenommen wurden.  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer die Option SQL_UNSPECIFIED zurückgegeben, da unterstützt.  
  
 Ein vollständige SQL-92 Level-konformen-Treiber wird immer die Option SQL_INSENSITIVE zurückgegeben, unterstützt.  
  
 SQL_DATA_SOURCE_NAME(ODBC 1.0)  
 Eine Zeichenfolge mit dem-Datenquellennamen, die während der Verbindung verwendet wurde. Wenn die Anwendung aufgerufen **SQLConnect**, dies ist der Wert, der die *SzDSN* Argument. Wenn die Anwendung namens **SQLDriverConnect** oder **SQLBrowseConnect**, dies ist der Wert, der das DSN-Schlüsselwort in der Verbindungszeichenfolge, die an den Treiber übergeben. Wenn die Verbindungszeichenfolge nicht enthalten hat der **DSN** Schlüsselwort (z. B. wenn es enthält die **Treiber** Schlüsselwort), dies ist eine leere Zeichenfolge.  
  
 SQL_DATA_SOURCE_READ_ONLY(ODBC 1.0)  
 Eine Zeichenfolge. "Y", wenn die Datenquelle in den READ ONLY-Modus ist, wird "N" festgelegt ist, ist dies andernfalls.  
  
 Diese Eigenschaft bezieht sich nur auf die Datenquelle selbst; Es ist kein Merkmal des Treibers, der Zugriff auf die Datenquelle ermöglicht. Ein Treiber, der Lese-/Schreibeigenschaft handelt, kann mit einer Datenquelle verwendet werden, die schreibgeschützt ist. Wenn ein Treiber schreibgeschützt ist, alle zugehörigen Datenquellen müssen schreibgeschützt sein und muss SQL_DATA_SOURCE_READ_ONLY zurückgeben.  
  
 SQL_DATABASE_NAME(ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen der aktuellen Datenbank verwendet werden, wenn die Datenquelle ein benanntes Objekt, das Namen "Database" definiert.  
  
> [!NOTE]
>  In ODBC 3. *.x*, der zurückgegebene Wert für diesen *Informationsart* kann auch zurückgegeben werden, indem **SQLGetConnectAttr** mit einer *Attribut* ein Argument vom SQL_ATTR_CURRENT_CATALOG.  
  
 SQL_DATETIME_LITERALS (ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske Aufzählen der SQL-92-Datetime-Literale, die von der Datenquelle unterstützt. Beachten Sie, dass diese die Datetime-Literale, die in der SQL-92-Spezifikation aufgelistet werden und sind getrennt von der mit "DateTime" literal Escape-Klauseln von ODBC definiert. Weitere Informationen zu Literalen ODBC Datetime-Escape-Klauseln, finden Sie unter [Date, Time und Timestamp-Literale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Ein FIPS Transitional Level-konformen-Treiber gibt immer den Wert "1" in der Bitmaske für die Bits in der folgenden Liste zurück. Ein Wert von "0" bedeutet, dass SQL-92-Datetime-Literale nicht unterstützt werden.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Literale unterstützt werden:  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_ SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME(ODBC 1.0)  
 Eine Zeichenfolge, durch den Namen des DBMS-Produkts, das auf die vom Treiber zugegriffen werden soll.  
  
 SQL_DBMS_VER(ODBC 1.0)  
 Eine Zeichenfolge, die die Version des Produkts DBMS zugegriffen, die vom Treiber angibt. Die Version des Formulars wird ##. ##. ###, wobei die ersten beiden Ziffern die Hauptversion sind, die nächsten beiden Ziffern die Nebenversion sind, und die letzten vier Ziffern die endgültige Produktversion werden. Der Treiber die DBMS-Produktversion, in diesem Format gerendert werden muss, aber es kann auch die Version der DBMS-produktspezifische angefügt. Z. B. "04.01.0000 Rdb 4.1".  
  
 SQL_DDL_INDEX(ODBC 3.0)  
 Eine SQLUINTEGER-Wert, der Unterstützung für das Erstellen und Löschen von Indizes angibt:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION(ODBC 1.0)  
 Ein SQLUINTEGER-Wert, der angibt, dass die standardmäßige Transaktionsisolationsstufe von das Treiber oder die Datenquelle unterstützt, oder NULL, wenn die Datenquelle unterstützt keine Transaktionen. Die folgenden Begriffe werden verwendet, um Transaktionsisolationsstufen zu definieren:  
  
 **Dirty Read** Transaktion 1 wird eine Zeile geändert. Transaktion 2 liest die geänderte Zeile vor dem Commit der Transaktion 1-Änderung. Wenn Transaktion 1 die Änderung ein Rollback, wird Transaktion 2 eine Zeile gelesen haben, die berücksichtigt werden, um nie vorhanden sind.  
  
 **Nicht wiederholbarer Lesevorgang** Transaktion 1 liest eine Zeile. Transaktion 2 aktualisiert oder löscht die Zeile, und führt einen Commit für diese Änderung. Wenn Transaktion 1 versucht, die die Zeile erneut zu lesen, wird es anderen Zeilenwerte empfangen oder feststellen, dass die Zeile gelöscht wurde.  
  
 **Berührte** Transaktion 1 liest eine Gruppe von Zeilen, die einige Suchkriterien erfüllen. Transaktion 2 generiert eine oder mehrere Zeilen (durch einfügungen oder Updates), die den Suchkriterien entsprechen. Wenn die Transaktion 1 die Anweisung reexecutes, die die Zeilen liest, erhält sie einen anderen Satz von Zeilen.  
  
 Wenn die Datenquelle Transaktionen unterstützt, gibt der Treiber einen der folgenden Bitmasks zurück:  
  
 SQL_TXN_READ_UNCOMMITTED = Dirty Reads, nicht wiederholbarer Lesevorgänge und Phantome sind möglich.  
  
 SQL_TXN_READ_COMMITTED = Dirty Reads sind nicht möglich. Nicht wiederholbarer Lesevorgänge und Phantome geben sind möglich.  
  
 SQL_TXN_REPEATABLE_READ = Dirty Reads und nicht wiederholbaren Lesevorgängen sind nicht möglich. Phantome sind möglich.  
  
 Sql_txn_serializable festgelegt sind = Transaktionen sind serialisierbar. Dirty Reads, nicht wiederholbaren Lesevorgängen oder Phantome zulassen Serializable-Transaktionen nicht.  
  
 SQL_DESCRIBE_PARAMETER(ODBC 3.0)  
 Eine Zeichenfolge: "Y", wenn die Parameter beschrieben werden können; "N", ist dies nicht.  
  
 Ein vollständige SQL-92 Level-konformen-Treiber gibt "Y" in der Regel zurück, da unterstützt wird die **BESCHREIBEN Eingabe** Anweisung. Da dies die zugrunde liegenden SQL-Unterstützung nicht direkt angegeben ist, kann jedoch, die Parameter beschreibt nicht, auch in einen vollständigen SQL-92-Level-konformen-Treiber unterstützt.  
  
 SQL_DM_VER(ODBC 3.0)  
 Eine Zeichenfolge mit der Version des Treiber-Managers. Die Version des Formulars wird ##. ##. ###. ###, wobei:  
  
 Der erste Satz von zwei Ziffern ist die Hauptversion von ODBC gemäß Angabe durch die Konstante SQL_SPEC_MAJOR.  
  
 Die zweite Gruppe von zwei Ziffern ist die Nebenversion von ODBC gemäß Angabe durch die Konstante SQL_SPEC_MINOR.  
  
 Die dritte Gruppe vier Ziffern ist die Hauptversion des Treiber-Manager-Buildnummer.  
  
 Der letzte Satz von vier Ziffern ist die Anzahl der Treiber-Manager-Nebenversionsnummer des Builds.  
  
 Windows 7-Treiber-Manager-Version ist 03.80. Die Windows 8-Treiber-Manager-Version ist 03.81.  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 Eine SQLUINTEGER-Wert, der angibt, wenn der Treiber treiberfähiges Verbindungspooling zu unterstützen. (Weitere Informationen finden Sie unter [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE gibt an, dass der Treiber treiberfähiges Verbindungspooling Mechanismus unterstützen kann.  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE gibt an, dass der Treiber treiberfähiges Verbindungspooling Mechanismus unterstützen kann.  
  
 Muss ein Treiber nicht SQL_DRIVER_AWARE_POOLING_SUPPORTED implementieren, und der Treiber-Manager hat keine Auswirkungen auf den Rückgabewert des Treibers.  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV(ODBC 1.0)  
 Ein SQLULEN Wert, des Treibers Umgebungshandle oder Verbindungshandles, die durch das Argument bestimmt *Informationsart*.  
  
 Solche Informationen werden vom Treiber-Manager allein implementiert.  
  
 SQL_DRIVER_HDESC(ODBC 3.0)  
 Ein SQLULEN Wert des Treibers Deskriptorhandles ermittelt der Treiber-Manager Deskriptorhandle, das Eingaben in übergeben werden muss \* *InfoValuePtr* aus der Anwendung. In diesem Fall *InfoValuePtr* ist ein Eingabe- und Argument. Das Handle Eingabedeskriptor übergeben \* *InfoValuePtr* müssen entweder explizit oder implizit zugeteilt wurde auf die *ConnectionHandle*.  
  
 Die Anwendung sollte, eine Kopie der Treiber-Manager-Deskriptor verarbeiten, bevor sie ruft **SQLGetInfo** mit dieser Informationsart, um sicherzustellen, dass das Handle für die Ausgabe nicht überschrieben werden.  
  
 Dieser Informationstyp wird vom Treiber-Manager allein implementiert.  
  
 SQL_DRIVER_HLIB(ODBC 2.0)  
 Ein Wert SQLULEN erstellt wurde, die *Hinst* aus der Bibliothek laden zurückgegeben an den Treiber-Manager, wenn es sich um die Treiber-DLL für ein Microsoft Windows-Betriebssystem oder dessen Entsprechung auf einem anderen Betriebssystem geladen. Das Handle ist nur gültig für das Verbindungshandle im Aufruf angegeben **SQLGetInfo**.  
  
 Dieser Informationstyp wird vom Treiber-Manager allein implementiert.  
  
 SQL_DRIVER_HSTMT(ODBC 1.0)  
 Ein SQLULEN Wert des Treibers Anweisungshandle bestimmt, indem das Anweisungshandle-Treiber-Manager, die Eingaben in übergeben werden muss \* *InfoValuePtr* aus der Anwendung. In diesem Fall *InfoValuePtr* ist sowohl Eingabe-als auch ein ausgabeargument. Das Eingabe-Anweisungshandle übergeben \* *InfoValuePtr* muss für das Argument zugeordnet worden sein *ConnectionHandle*.  
  
 Die Anwendung sollte, eine Kopie der Treiber-Manager-Anweisung verarbeiten, bevor sie ruft **SQLGetInfo** mit dieser Informationsart, um sicherzustellen, dass das Handle für die Ausgabe nicht überschrieben werden.  
  
 Dieser Informationstyp wird vom Treiber-Manager allein implementiert.  
  
 SQL_DRIVER_NAME (ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen der Datei des Treibers, der Zugriff auf die Datenquelle.  
  
 SQL_DRIVER_ODBC_VER(ODBC 2.0)  
 Eine Zeichenfolge mit der Version von ODBC, die der Treiber unterstützt. Die Version des Formulars wird ##. ##, wobei die ersten beiden Ziffern die Hauptversionsnummer sind und die nächsten beiden Ziffern die Nebenversion sind. SQL_SPEC_MAJOR und SQL_SPEC_MINOR definieren die Nummern für Haupt-und Nebenversion. Die Version von ODBC, die in diesem Handbuch beschriebenen sind 3 und 0, und der Treiber sollte "03.00" zurück.  
  
 Der ODBC-Treiber-Manager ändert sich nicht auf den Rückgabewert der SQLGetInfo(SQL_DRIVER_ODBC_VER) Abwärtskompatibilität für vorhandene Anwendungen aus. Der Treiber gibt an, welcher Wert zurückgegeben wird. Allerdings muss ein Treiber, der C-Typ datenerweiterung unterstützt 3.8 (oder höher) bei zurückgeben eine Anwendung ruft **SQLSetEnvAttr** SQL_ATTR_ODBC_VERSION auf 3.8 festgelegt. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 SQL_DRIVER_VER(ODBC 1.0)  
 Eine Zeichenfolge mit der Version des Treibers und optional eine Beschreibung des Treibers. Minimal, ist die Version des Formulars ##. ##. ###, wobei die ersten beiden Ziffern die Hauptversion sind, die nächsten beiden Ziffern die Nebenversion sind, und die letzten vier Ziffern die endgültige Produktversion werden.  
  
 SQL_DROP_ASSERTION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **löschen ASSERTION** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DA_DROP_ASSERTION  
  
 Diese Option wird ein vollständige SQL-92 Level-konformen Treiber wie unterstützt immer zurückgegeben werden.  
  
 SQL_DROP_CHARACTER_SET(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **ZEICHENSATZ löschen** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 Diese Option wird ein vollständige SQL-92 Level-konformen Treiber wie unterstützt immer zurückgegeben werden.  
  
 SQL_DROP_COLLATION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **ablegen-SORTIERUNG** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DC_DROP_COLLATION  
  
 Diese Option wird ein vollständige SQL-92 Level-konformen Treiber wie unterstützt immer zurückgegeben werden.  
  
 SQL_DROP_DOMAIN(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **DROP DOMAIN** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 Ein Treiber für SQL-92-Intermediate Level-konformen wird immer all diese Optionen zurückgegeben, da unterstützt.  
  
 SQL_DROP_SCHEMA(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **DROP SCHEMA** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 Ein Treiber für SQL-92-Intermediate Level-konformen wird immer all diese Optionen zurückgegeben, da unterstützt.  
  
 SQL_DROP_TABLE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **DROP TABLE** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 Ein FIPS Transitional Level-konformen-Treiber wird immer all diese Optionen zurückgegeben, als unterstützt.  
  
 SQL_DROP_TRANSLATION(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **löschen Übersetzung** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgende Bitmaske wird verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DTR_DROP_TRANSLATION  
  
 Diese Option wird ein vollständige SQL-92 Level-konformen Treiber wie unterstützt immer zurückgegeben werden.  
  
 SQL_DROP_VIEW(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **DROP VIEW** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 Ein FIPS Transitional Level-konformen-Treiber wird immer all diese Optionen zurückgegeben, als unterstützt.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines dynamischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält der ersten Teilmenge von Attributen. die zweite Untergruppe finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXT = A *FetchOrientation* Argument sql_fetch_next wird unterstützt, in einem Aufruf von **SQLFetchScroll** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_ABSOLUTE = *FetchOrientation* Argumente der SQL_FETCH_FIRST SQL_FETCH_LAST und SQL_FETCH_ABSOLUTE unterstützt werden in einem Aufruf von **SQLFetchScroll** Wenn der Cursor ist ein dynamischer Cursor. (Das Rowset, das übernommen werden, ist unabhängig von der aktuellen Cursorposition.)  
  
 SQL_CA1_RELATIVE = *FetchOrientation* Argumente SQL_FETCH_PRIOR und SQL_FETCH_RELATIVE unterstützt werden in einem Aufruf von **SQLFetchScroll** Wenn der Cursor ist ein dynamischer Cursor. (Das Rowset, das übernommen werden, hängt von der aktuellen Cursorposition ab. Beachten Sie, dass dies von SQL_FETCH_NEXT getrennt ist, da in einem Vorwärtscursor nur SQL_FETCH_NEXT unterstützt wird.)  
  
 SQL_CA1_BOOKMARK = A *FetchOrientation* Argument von SQL_FETCH_BOOKMARK wird unterstützt, in einem Aufruf von **SQLFetchScroll** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_LOCK_EXCLUSIVE = A *LockType* Argument SQL_LOCK_EXCLUSIVE wird unterstützt, in einem Aufruf von **SQLSetPos** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_LOCK_NO_CHANGE = A *LockType* Argument SQL_LOCK_NO_CHANGE wird unterstützt, in einem Aufruf von **SQLSetPos** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_LOCK_UNLOCK = A *LockType* Argument SQL_LOCK_UNLOCK wird unterstützt, in einem Aufruf von **SQLSetPos** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_POS_POSITION = ein *Vorgang* Argument SQL_POSITION wird unterstützt, in einem Aufruf von **SQLSetPos** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_POS_UPDATE = ein *Vorgang* Argument SQL_UPDATE wird unterstützt, in einem Aufruf von **SQLSetPos** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_POS_DELETE = ein *Vorgang* Argument SQL_DELETE wird unterstützt, in einem Aufruf von **SQLSetPos** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_POS_REFRESH = ein *Vorgang* Argument SQL_REFRESH wird unterstützt, in einem Aufruf von **SQLSetPos** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_POSITIONED_UPDATE = ein UPDATE, in dem aktuellen der SQL-Anweisung wird unterstützt, wenn der Cursor befindet sich ein dynamic-Cursor. (Ein Level-konformen-Treiber für SQL-92-Eintrag diese Option gibt stets als unterstützt.)  
  
 SQL_CA1_POSITIONED_DELETE = A löschen, in dem aktuellen der SQL-Anweisung wird unterstützt, wenn der Cursor befindet sich ein dynamic-Cursor. (Ein Level-konformen-Treiber für SQL-92-Eintrag diese Option gibt stets als unterstützt.)  
  
 SQL_CA1_SELECT_FOR_UPDATE = eine SELECT-Anweisung aus, für die UPDATE-SQL-Anweisung unterstützt wird, wenn der Cursor befindet sich ein dynamic-Cursor. (Ein Level-konformen-Treiber für SQL-92-Eintrag diese Option gibt stets als unterstützt.)  
  
 SQL_CA1_BULK_ADD = ein *Vorgang* Argument SQL_ADD wird unterstützt, in einem Aufruf von **SQLBulkOperations** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = ein *Vorgang* Argument SQL_UPDATE_BY_BOOKMARK wird unterstützt, in einem Aufruf von **SQLBulkOperations** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = ein *Vorgang* Argument SQL_DELETE_BY_BOOKMARK wird unterstützt, in einem Aufruf von **SQLBulkOperations** Wenn der Cursor ist ein dynamischer Cursor.  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = ein *Vorgang* Argument SQL_FETCH_BY_BOOKMARK wird unterstützt, in einem Aufruf von **SQLBulkOperations** Wenn der Cursor ist ein dynamischer Cursor.  
  
 Ein SQL-92-Intermediate-Ebene-konformen-Treiber wird in der Regel die SQL_CA1_NEXT SQL_CA1_ABSOLUTE und SQL_CA1_RELATIVE Optionen wie zurückgegeben werden unterstützt, da scrollfähige Cursor über die eingebettete SQL FETCH-Anweisung unterstützt. Da dies nicht der zugrunde liegenden SQL-Unterstützung direkt bestimmt, möglicherweise jedoch scrollfähige Cursor nicht, auch für einen SQL-92-Intermediate-Ebene-konformen-Treiber unterstützt.  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines dynamischen Cursors beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält der zweite Teilmenge von Attributen. die erste Untergruppe finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = eine nur-Lese-dynamic-Cursor, in denen keine Updates zulässig sind, wird unterstützt. (Das SQL_ATTR_CONCURRENCY-Anweisungsattribut auf SQL_CONCUR_READ_ONLY für einen dynamischen Cursor möglich).  
  
 SQL_CA2_LOCK_CONCURRENCY = einen dynamic-Cursor, die die niedrigste Ebene verwendet Sperren ausreichen, um sicherzustellen, dass die Zeile aktualisiert werden kann wird unterstützt. (Das SQL_ATTR_CONCURRENCY-Anweisungsattribut SQL_CONCUR_LOCK für einen dynamischen Cursor möglich.) Diese Sperren müssen konsistent mit die Isolationsstufe der Transaktion, die durch das Verbindungsattribut SQL_ATTR_TXN_ISOLATION festgelegt sein.  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = ein dynamisches Cursors verwendet die vollständige Parallelität Steuerelement Vergleichen von Zeilenversionen unterstützt wird. (Das SQL_ATTR_CONCURRENCY-Anweisungsattribut SQL_CONCUR_ROWVER für einen dynamischen Cursor möglich.)  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = ein dynamisches Cursors verwendet die vollständige Parallelität Vergleichen von Control-Werte unterstützt wird. (Das SQL_ATTR_CONCURRENCY-Anweisungsattribut SQL_CONCUR_VALUES für einen dynamischen Cursor möglich.)  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = hinzugefügte Zeilen sind sichtbar, in einen dynamischen Cursor; der Cursor kann auf jene Zeilen scrollen. (Das, in denen diese Zeilen hinzugefügt werden, bis des Cursors ist treiberabhängig.)  
  
 SQL_CA2_SENSITIVITY_DELETIONS = der gelöschte Zeilen sind nicht mehr verfügbar ist, in einen dynamischen Cursor, und lassen sich nicht auf eine "Lücke" im Resultset; Nachdem der dynamische-Cursor aus einer gelöschten Zeile einen Bildlauf durchführt, können keine Zeile zurückgegeben werden.  
  
 SQL_CA2_SENSITIVITY_UPDATES = Updates von Zeilen in einen dynamischen Cursor; angezeigt werden Wenn der dynamische Cursor führt einen Bildlauf aus, und es auf eine aktualisierte Zeile zurückgibt, ist die vom Cursor zurückgegebenen Daten die aktualisierten Daten, nicht die ursprünglichen Daten.  
  
 SQL_CA2_MAX_ROWS_SELECT = die SQL_ATTR_MAX_ROWS Anweisung Attribut wirkt sich auf **wählen** Anweisungen, wenn der Cursor befindet sich ein dynamic-Cursor.  
  
 SQL_CA2_MAX_ROWS_INSERT = die SQL_ATTR_MAX_ROWS Anweisung Attribut wirkt sich auf **einfügen** Anweisungen, wenn der Cursor befindet sich ein dynamic-Cursor.  
  
 SQL_CA2_MAX_ROWS_DELETE = die SQL_ATTR_MAX_ROWS Anweisung Attribut wirkt sich auf **löschen** Anweisungen, wenn der Cursor befindet sich ein dynamic-Cursor.  
  
 SQL_CA2_MAX_ROWS_UPDATE = die SQL_ATTR_MAX_ROWS Anweisung Attribut wirkt sich auf **UPDATE** Anweisungen, wenn der Cursor befindet sich ein dynamic-Cursor.  
  
 SQL_CA2_MAX_ROWS_CATALOG = die SQL_ATTR_MAX_ROWS Anweisung Attribut wirkt sich auf **Katalog** Resultsets aus, wenn der Cursor befindet sich ein dynamic-Cursor.  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = die SQL_ATTR_MAX_ROWS Anweisung Attribut wirkt sich auf **wählen**, **einfügen**, **löschen**, und **UPDATE** Anweisungen und **Katalog** Resultsets, wenn der Cursor befindet sich ein dynamic-Cursor.  
  
 SQL_CA2_CRC_EXACT = der Zeilenanzahl im Feld SQL_DIAG_CURSOR_ROW_COUNT Diagnose verfügbar ist, wenn der Cursor befindet sich ein dynamic-Cursor.  
  
 SQL_CA2_CRC_APPROXIMATE = geschätzte Zeilenanzahl im Feld SQL_DIAG_CURSOR_ROW_COUNT Diagnose verfügbar ist, wenn der Cursor befindet sich ein dynamic-Cursor.  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = den Treiber ist nicht garantiert, die simulierte positioniert Update oder Delete-Anweisungen wirken nur eine Zeile, wenn der Cursor befindet sich ein dynamischer Cursor; Es ist Aufgabe der Anwendung, um dies zu gewährleisten. (Wenn eine Anweisung mehrere Zeilen betrifft **SQLExecute** oder **SQLExecDirect** SQLSTATE 01001 [Konflikt beim Cursorvorgang] zurückgibt.) Dieses Verhalten, die Anwendung ruft festzulegende **SQLSetStmtAttr** -Attribut Sie mit der SQL_ATTR_SIMULATE_CURSOR auf SQL_SC_NON_UNIQUE festgelegt.  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = versucht der Treiber, um sicherzustellen, dass die simulierten positionierte Update- oder Delete-Anweisungen nur eine Zeile auswirken, wenn es sich bei der Cursor befindet sich ein dynamic-Cursor. Der Treiber führt immer solchen Aussagen ist, auch wenn sie mehr als eine Zeile, z. B. wenn beeinflussen können keine eindeutiger Schlüssel vorhanden ist. (Wenn eine Anweisung mehrere Zeilen betrifft **SQLExecute** oder **SQLExecDirect** SQLSTATE 01001 [Konflikt beim Cursorvorgang] zurückgibt.) Dieses Verhalten, die Anwendung ruft festzulegende **SQLSetStmtAttr** -Attribut Sie mit der SQL_ATTR_SIMULATE_CURSOR auf SQL_SC_TRY_UNIQUE festgelegt.  
  
 SQL_CA2_SIMULATE_UNIQUE = den Treiber gewährleistet, dass die simulierte positioniert, Update oder Delete-Anweisungen wirken nur eine Zeile, wenn der Cursor befindet sich ein dynamic-Cursor. Wenn der Treiber dies für eine angegebene Anweisung nicht garantieren kann **SQLExecDirect** oder **SQLPrepare** SQLSTATE 01001 (Konflikt beim Cursorvorgang) zurück. Dieses Verhalten, die Anwendung ruft festzulegende **SQLSetStmtAttr** -Attribut Sie mit der SQL_ATTR_SIMULATE_CURSOR auf SQL_SC_UNIQUE festgelegt.  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle Ausdrücke in unterstützt die **ORDER BY** auflisten. "N", wenn dies nicht der Fall.  
  
 SQL_FILE_USAGE (ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der angibt, wie ein ein-Ebenen-Treiber-Dateien in eine Datenquelle direkt behandelt:  
  
 SQL_FILE_NOT_SUPPORTED = der Treiber ist nicht nur einer Ebene Treiber. Beispielsweise ist ein ORACLE-Treiber ein zwei-Ebenen-Treiber.  
  
 SQL_FILE_TABLE = ein ein-Ebenen-Treiber behandelt Dateien in einer Datenquelle als Tabellen. Ein Xbase-Treiber werden z. B. jede Xbase-Datei als Tabelle behandelt.  
  
 SQL_FILE_CATALOG = ein ein-Ebenen-Treiber behandelt Dateien in einer Datenquelle als Katalog. Ein Microsoft Access-Treiber werden z. B. jeder Microsoft Access-Datei als eine vollständige Datenbank behandelt.  
  
 Eine Anwendung kann diese verwenden, um zu bestimmen, wie Benutzer Daten auswählen. Beispielsweise denken Xbase-Benutzer häufig von Daten in Dateien gespeichert, während ORACLE und Microsoft Access-Benutzer im Allgemeinen von Daten vorstellen, wie Sie in Tabellen gespeichert.  
  
 Wenn ein Benutzer eine Xbase-Datenquelle auswählt, kann die Anwendung der Windows anzeigen **Datei öffnen** Standarddialogfeld; Wenn der Benutzer eine Microsoft Access oder ORACLE-Datenquelle, wählt die Anwendung konnte eine benutzerdefinierte anzeigen  **Wählen Sie die Tabelle** Dialogfeld.  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines Cursors Vorwärtscursor beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält der ersten Teilmenge von Attributen. die zweite Untergruppe finden Sie unter SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_ UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und Ersetzen Sie "Forward-only-Cursor" für "dynamische Cursor" in den Beschreibungen).  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines Cursors Vorwärtscursor beschreibt, die vom Treiber unterstützt werden. Diese Bitmaske enthält der zweite Teilmenge von Attributen. die erste Untergruppe finden Sie unter SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (und Ersetzen Sie "Forward-only-Cursor" für "dynamische Cursor" in den Beschreibungen).  
  
 SQL_GETDATA_EXTENSIONS(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die Erweiterungen auflisten **SQLGetData**.  
  
 Die folgenden Bitmasken werden zusammen mit dem Flag verwendet, um zu bestimmen, welche häufig verwendete Erweiterungen der Treiber zum unterstützt **SQLGetData**:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData** kann bei jeder ungebundenen Spalte, einschließlich der vor der letzten Spalte gebundenen aufgerufen werden. Beachten Sie, dass die Spalten in der Reihenfolge der Spaltennummer aufsteigend, es sei denn, Sie wird auch zurückgegeben, SQL_GD_ANY_ORDER aufgerufen werden müssen.  
  
 SQL_GD_ANY_ORDER = **SQLGetData** für ungebundene Spalten in einer beliebigen Reihenfolge aufgerufen werden können. Beachten Sie, dass **SQLGetData** kann nur für Spalten aufgerufen werden, nach der letzten gebundenen Spalte auf, es sei denn, SQL_GD_ANY_COLUMN wird ebenfalls zurückgegeben.  
  
 SQL_GD_BLOCK = **SQLGetData** kann bei einer ungebundenen Spalte in einer Zeile in einem Block (wobei die Größe des Rowsets ist größer als 1) der Daten aufgerufen werden, nach der Zeile mit Positionierung **SQLSetPos**.  
  
 SQL_GD_BOUND = **SQLGetData** für gebundene Spalten zusätzlich zu ungebundenen Spalten aufgerufen werden können. Ein Treiber kann nicht dieser Wert zurückgegeben werden, es sei denn, es gibt auch SQL_GD_ANY_COLUMN zurück.  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData** aufgerufen werden, um die Werte der Ausgabeparameter zurückgeben. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
 **SQLGetData** ist erforderlich, um die Daten nur von ungebundenen Spalten, die nach der letzten Spalte gebundenen, auftreten, die in der Reihenfolge zunehmender spaltenzahlfolge aufgerufen werden und sind nicht in einer Zeile in einem Block von Zeilen zurück.  
  
 Wenn ein Treiber Lesezeichen (fester oder variabler Länge) unterstützt, muss er aufrufen unterstützen **SQLGetData** für die Spalte 0. Diese Unterstützung ist erforderlich, unabhängig davon, was der Treiber für einen Aufruf von gibt **SQLGetInfo** mit der SQL_GETDATA_EXTENSIONS *Informationsart*.  
  
 SQL_GROUP_BY (ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der angibt, die Beziehung zwischen den Spalten in der **GROUP BY** -Klausel und den nicht zusammengesetzten Spalten in der select-Liste:  
  
 SQL_GB_COLLATE = A **COLLATE** -Klausel angegeben werden kann, am Ende der einzelnen Spalten gruppieren. (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED = **GROUP BY** Klauseln werden nicht unterstützt. ODBC (2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = die **GROUP BY** -Klausel muss alle nicht zusammengesetzten Spalten in der select-Liste enthalten. Sie können keine anderen Spalten enthalten. Z. B. **wählen DEPT, MAX(SALARY) aus Mitarbeiter GROUP BY Abteilung**. ODBC (2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = die **GROUP BY** -Klausel muss alle nicht zusammengesetzten Spalten in der select-Liste enthalten. Sie können Spalten enthalten, die nicht in der Auswahlliste sind. Z. B. **wählen DEPT, MAX(SALARY) aus Mitarbeiter GROUP BY Abteilung, dem Alter**. ODBC (2.0)  
  
 SQL_GB_NO_RELATION = die Spalten in der **GROUP BY** -Klausel und die select-Liste beziehen sich nicht. Die Bedeutung der nongrouped, zusammengesetzten Spalten in der select-Liste ist datenquellenabhängig. Z. B. **wählen DEPT, Gehalt von EMPLOYEE-Gruppe BY DEPT, dem Alter**. ODBC (2.0)  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer die Option SQL_GB_GROUP_BY_EQUALS_SELECT zurückgegeben, da unterstützt. Ein vollständige SQL-92 Level-konformen-Treiber wird immer die Option SQL_GB_COLLATE zurückgegeben, unterstützt. Wenn keine der Optionen unterstützt wird, die **GROUP BY** -Klausel wird von der Datenquelle nicht unterstützt.  
  
 SQL_IDENTIFIER_CASE(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert wie folgt aus:  
  
 SQL_IC_UPPER = Bezeichner in SQL Groß-/Kleinschreibung nicht und befinden sich in Großbuchstaben im Systemkatalog.  
  
 SQL_IC_LOWER = Bezeichner in SQL Groß-/Kleinschreibung nicht und werden in Kleinbuchstaben im Systemkatalog gespeichert.  
  
 SQL_IC_SENSITIVE = Bezeichner in SQL wird die Groß-/Kleinschreibung beachtet, und werden in gemischter Schreibung im Systemkatalog gespeichert.  
  
 SQL_IC_MIXED = Bezeichner in SQL Groß-/Kleinschreibung nicht und werden in gemischter Schreibung im Systemkatalog gespeichert.  
  
 Da Bezeichner in SQL-92 nie Groß-/Kleinschreibung beachtet werden, gibt ein Treiber, der ausschließlich SQL-92 (einer beliebigen Ebene) entspricht die Option SQL_IC_SENSITIVE unterstützt nie zurück.  
  
 SQL_IDENTIFIER_QUOTE_CHAR(ODBC 1.0)  
 Die Zeichenfolge, die als Trennzeichen Anfangs- und Endposition des eine in Anführungszeichen verwendet wird (-Begrenzungsbezeichner) in SQL-Anweisungen. (Bezeichner, die als Argumente übergeben werden, um ODBC-Funktionen nicht müssen in Anführungszeichen gesetzt werden.) Wenn Bezeichner in Anführungszeichen in die Datenquelle nicht unterstützt wird, wird ein leerer Wert zurückgegeben.  
  
 Diese Zeichenfolge kann auch verwendet werden, für die Katalog-Funktionsargumente Anführungszeichen, wenn das Verbindungsattribut SQL_ATTR_METADATA_ID auf SQL_TRUE festgelegt ist.  
  
 Da Anführungszeichen Bezeichner in SQL-92 das doppelte Anführungszeichen (") ist, wird ein Treiber, der entspricht streng auf SQL-92 immer das doppelte Anführungszeichen zurückgegeben.  
  
 SQL_INDEX_KEYWORDS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die Schlüsselwörter in der CREATE INDEX-Anweisung auflistet, die vom Treiber unterstützt werden:  
  
 SQL_IK_NONE = keines der Schlüsselwörter wird unterstützt.  
  
 SQL_IK_ASC = ASC-Schlüsselwort wird unterstützt.  
  
 SQL_IK_DESC = DESC-Schlüsselwort wird unterstützt.  
  
 SQL_IK_ALL = alle Schlüsselwörter werden unterstützt.  
  
 Um festzustellen, ob die CREATE INDEX-Anweisung unterstützt wird, eine Anwendung ruft **SQLGetInfo** mit dem Typ der SQL_DLL_INDEX-Informationen.  
  
 SQL_INFO_SCHEMA_VIEWS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske Auflisten von Ansichten im INFORMATION_SCHEMA, die vom Treiber unterstützt werden. Die Ansichten in und den Inhalt von INFORMATION_SCHEMA in SQL-92 definiert sind.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um festzustellen, welche Ansichten unterstützt:  
  
 SQL_ISV_ASSERTIONS = identifiziert des Katalogs Assertionen, die von einem bestimmten Benutzer gehören. (Vollständige Stufe)  
  
 SQL_ISV_CHARACTER_SETS = identifiziert des Katalogs Zeichensätze, die ein angegebener Benutzer zugreifen kann. (Mittlere Ebene)  
  
 SQL_ISV_CHECK_CONSTRAINTS = identifiziert die CHECK-Einschränkungen, die von einem bestimmten Benutzer gehören. (Mittlere Ebene)  
  
 SQL_ISV_COLLATIONS = identifiziert die Zeichensortierreihenfolgen für den Katalog, die ein angegebener Benutzer zugreifen kann. (Vollständige Stufe)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = identifiziert Spalten für den Katalog, die abhängig von Domänen, die im Katalog definierten und von einem bestimmten Benutzer gehören. (Mittlere Ebene)  
  
 SQL_ISV_COLUMN_PRIVILEGES = gibt die Berechtigungen für die Spalten der persistente Tabellen, die verfügbar sind oder von diesem erteilt, die von einem bestimmten Benutzer sind. (FIPS Transitional Stufe)  
  
 SQL_ISV_COLUMNS = identifiziert die Spalten der persistente Tabellen, die ein angegebener Benutzer zugreifen können. (FIPS Transitional Stufe)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = ähnlich wie Spalten werden identifiziert, CONSTRAINT_TABLE_USAGE-Sicht, für die verschiedenen Einschränkungen, die von einem bestimmten Benutzer gehören. (Mittlere Ebene)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = identifiziert die Tabellen, die durch Einschränkungen verwendet werden (referenzielle, eindeutig ist, und Assertionen), und von einem bestimmten Benutzer gehören. (Mittlere Ebene)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = gibt die Einschränkungen für Domäne (der Domänen im Katalog), die ein angegebener Benutzer zugreifen können. (Mittlere Ebene)  
  
 SQL_ISV_DOMAINS = identifiziert die Domänen definiert, in einem Katalog, die vom Benutzer zugegriffen werden kann. (Mittlere Ebene)  
  
 SQL_ISV_KEY_COLUMN_USAGE = im Katalog definierten identifiziert Spalten, die von einem bestimmten Benutzer als Schlüssel eingeschränkt werden. (Mittlere Ebene)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = gibt die referenziellen Einschränkungen, die von einem bestimmten Benutzer gehören. (Mittlere Ebene)  
  
 SQL_ISV_SCHEMATA = gibt die Schemas an, die von einem bestimmten Benutzer gehören. (Mittlere Ebene)  
  
 SQL_ISV_SQL_LANGUAGES = identifiziert, die die SQL-Übereinstimmungsebenen, Optionen und Dialekte von SQL-Implementierung unterstützt werden. (Mittlere Ebene)  
  
 SQL_ISV_TABLE_CONSTRAINTS = gibt die tabelleneinschränkungen an, die von einem bestimmten Benutzer gehören. (Mittlere Ebene)  
  
 SQL_ISV_TABLE_PRIVILEGES = gibt die Berechtigungen für persistente Tabellen, die verfügbar sind oder von diesem erteilt, die von einem bestimmten Benutzer sind. (FIPS Transitional Stufe)  
  
 SQL_ISV_TABLES = identifiziert, die die dauerhaften Tabellen definiert werden, in einem Katalog, die ein angegebener Benutzer zugreifen kann. (FIPS Transitional Stufe)  
  
 SQL_ISV_TRANSLATIONS = Zeichenübersetzungen identifiziert, für den Katalog, die ein angegebener Benutzer zugreifen kann. (Vollständige Stufe)  
  
 SQL_ISV_USAGE_PRIVILEGES = identifiziert, die die Nutzung für Katalogobjekte, die verfügbar sind oder im Besitz des Benutzers von einem bestimmten Benutzer Berechtigungen. (FIPS Transitional Stufe)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = identifiziert die Spalten des Katalogs auf die Ansichten, die von einem bestimmten Benutzer gehören hängen. (Mittlere Ebene)  
  
 SQL_ISV_VIEW_TABLE_USAGE = identifiziert, die in den Tabellen des Katalogs auf die Ansichten, die von einem bestimmten Benutzer gehören hängen. (Mittlere Ebene)  
  
 SQL_ISV_VIEWS = identifiziert, die die angezeigten Tabellen definiert werden, in diesem Katalog, die ein angegebener Benutzer zugreifen kann. (FIPS Transitional Stufe)  
  
 SQL_INSERT_STATEMENT(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die Unterstützung für angibt **einfügen** Anweisungen:  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer alle diese Optionen zurückgegeben, da unterstützt.  
  
 SQL_INTEGRITY(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle die Integritätserweiterungsfunktion unterstützt; "N", wenn dies nicht der Fall.  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_ODBC_SQL_OPT_IEF.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute des ein Keyset-Cursor wird beschrieben, die vom Treiber unterstützt werden. Diese Bitmaske enthält der ersten Teilmenge von Attributen. die zweite Untergruppe finden Sie unter SQL_KEYSET_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und Ersetzen Sie "keysetgesteuerte Cursor" für "dynamische Cursor" in den Beschreibungen).  
  
 Ein Treiber für SQL-92-Intermediate Level-konformen wird in der Regel die SQL_CA1_NEXT SQL_CA1_ABSOLUTE und SQL_CA1_RELATIVE Optionen wie zurückgegeben werden unterstützt, da der Treiber scrollfähige Cursor über die eingebettete SQL FETCH-Anweisung unterstützt. Da dies nicht der zugrunde liegenden SQL-Unterstützung direkt bestimmt, möglicherweise jedoch scrollfähige Cursor nicht, auch für einen SQL-92-Intermediate-Ebene-konformen-Treiber unterstützt.  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute des ein Keyset-Cursor wird beschrieben, die vom Treiber unterstützt werden. Diese Bitmaske enthält der zweite Teilmenge von Attributen. die erste Untergruppe finden Sie unter SQL_KEYSET_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und Ersetzen Sie "keysetgesteuerte Cursor" für "dynamische Cursor" in den Beschreibungen).  
  
 SQL_KEYWORDS(ODBC 2.0)  
 Eine Zeichenfolge, die eine durch Trennzeichen getrennte Liste aller Data Source-spezifische Schlüsselwörter enthält. Diese Liste enthält keine Schlüsselwörter, die speziell für ODBC oder Schlüsselwörter, die von der Datenquelle und die ODBC verwendet. Diese Liste stellt die reservierten Schlüsselwörter alle; interoperable Anwendungen ausführen können sollten diese Wörter nicht in Objektnamen verwenden.  
  
 Eine Liste mit Schlüsselwörtern für ODBC, finden Sie unter [reservierte Schlüsselwörter](../../../odbc/reference/appendixes/reserved-keywords.md) in [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Die **#define** Wert SQL_ODBC_KEYWORDS enthält eine durch Trennzeichen getrennte Liste von Schlüsselwörtern für ODBC.  
  
 Anhang C: SQL-Grammatik  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle ein Escapezeichen unterstützt, für das Prozentzeichen (%) und Unterstrich (_) in einem **wie** Prädikat und der Treiber die ODBC-Syntax zum Definieren von unterstützt eine **wie** Prädikat Escapezeichen; "N" andernfalls.  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS(ODBC 3.0)  
 Eine SQLUINTEGER-Wert, der die maximale Anzahl der aktiven gleichzeitigen Anweisungen im asynchronen Modus gibt an, die der Treiber auf eine bestimmte Verbindung unterstützt. Wenn es keine bestimmte Beschränkung gibt oder der Grenzwert unbekannt ist, ist dieser Wert 0 (null).  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2.0)  
 Eine SQLUINTEGER-Wert, der angibt, die maximale Länge (Anzahl von hexadezimalen Zeichen, mit Ausnahme von Zeichenfolgenliteral-Präfix und Suffix zurückgegebenes **SQLGetTypeInfo**) der ein binäres literal in einer SQL-Anweisung. Die binäre Literale 0xFFAA hat z. B. eine Länge von 4. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_CATALOG_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge des ein Katalogname in der Datenquelle angibt. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein vollständige FIPS Level-konformen-Treiber wird mindestens 128 zurückgegeben.  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_MAX_QUALIFIER_NAME_LEN.  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2.0)  
 Eine SQLUINTEGER-Wert, der angibt, die maximale Länge (Anzahl von Zeichen, mit Ausnahme von Zeichenfolgenliteral-Präfix und Suffix zurückgegebenes **SQLGetTypeInfo**) von einem Zeichenliteral in einer SQL­Anweisung. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_COLUMN_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge für einen Spaltennamen in der Datenquelle angibt. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 18 zurück. Ein Intermediate FIPS-Level-konformen-Treiber wird mindestens 128 zurückgegeben.  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der angibt, die maximale Anzahl zulässiger Spalten in einer **GROUP BY** Klausel. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 6 zurück. Ein Intermediate FIPS-Level-konformen-Treiber gibt mindestens 15 zurück.  
  
 SQL_MAX_COLUMNS_IN_INDEX(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl zulässiger Spalten in einem Index angibt. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der angibt, die maximale Anzahl zulässiger Spalten in einer **ORDER BY** Klausel. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 6 zurück. Ein Intermediate FIPS-Level-konformen-Treiber gibt mindestens 15 zurück.  
  
 SQL_MAX_COLUMNS_IN_SELECT(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl der zulässigen Spalten in einer select-Liste angibt. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 100 zurück. Ein Intermediate FIPS-Level-konformen-Treiber gibt mindestens 250 zurück.  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl zulässiger Spalten in einer Tabelle angibt. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 100 zurück. Ein Intermediate FIPS-Level-konformen-Treiber gibt mindestens 250 zurück.  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl aktiver Anweisungen angibt, die der Treiber für eine Verbindung unterstützt werden. Eine Anweisung als aktiv definiert ist, wenn sie die Ergebnisse wartet, mit dem Begriff "Ergebnisse" Bedeutung Zeilen verfügt eine **wählen** Vorgang oder von betroffenen Zeilen eine **einfügen**, **UPDATE**, oder **Löschen** Vorgang (z. B. eine Zeilenanzahl) oder in einem NEED_DATA Zustand ist. Dieser Wert kann es sich um eine Einschränkung auferlegt, indem Sie entweder den Treiber oder der Datenquelle widerspiegeln. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_ACTIVE_STATEMENTS.  
  
 SQL_MAX_CURSOR_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der maximal ein Cursorname in der Datenquelle angibt. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 18 zurück. Ein Intermediate FIPS-Level-konformen-Treiber wird mindestens 128 zurückgegeben.  
  
 SQL_MAX_DRIVER_CONNECTIONS(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Anzahl der aktiven Verbindungen angibt, die der Treiber für eine Umgebung unterstützen kann. Dieser Wert kann es sich um eine Einschränkung auferlegt, indem Sie entweder den Treiber oder der Datenquelle widerspiegeln. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_ACTIVE_CONNECTIONS.  
  
 SQL_MAX_IDENTIFIER_LEN(ODBC 3.0)  
 Ein SQLUSMALLINT, der die maximale Größe in Zeichen angibt, die die Datenquelle für den benutzerdefinierten Namen unterstützt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 18 zurück. Ein Intermediate FIPS-Level-konformen-Treiber wird mindestens 128 zurückgegeben.  
  
 SQL_MAX_INDEX_SIZE(ODBC 2.0)  
 Eine SQLUINTEGER-Wert, der die maximale Anzahl von Bytes in den kombinierten Feldern eines Index angibt. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_PROCEDURE_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge des Namen einer Prozedur in der Datenquelle angibt. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_ROW_SIZE(ODBC 2.0)  
 Eine SQLUINTEGER-Wert, der die maximale Länge einer einzelnen Zeile in einer Tabelle angibt. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 2.000 zurück. Ein Intermediate FIPS-Level-konformen-Treiber gibt mindestens 8.000 zurück.  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG(ODBC 3.0)  
 Eine Zeichenfolge: "Y", wenn die maximale Zeilengröße für den Informationstyp SQL_MAX_ROW_SIZE zurückgegeben umfasst die Länge der Spalten für alle SQL_LONGVARCHAR und SQL_LONGVARBINARY in der Zeile. "N" andernfalls.  
  
 SQL_MAX_SCHEMA_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge des Namens eines Schemas in der Datenquelle angibt. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 18 zurück. Ein Intermediate FIPS-Level-konformen-Treiber wird mindestens 128 zurückgegeben.  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_MAX_OWNER_NAME_LEN.  
  
 SQL_MAX_STATEMENT_LEN(ODBC 2.0)  
 Eine SQLUINTEGER-Wert, der die maximale Länge (Anzahl der Zeichen, einschließlich Leerzeichen), die von einer SQL-Anweisung angibt. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MAX_TABLE_NAME_LEN(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge des Namen einer Tabelle in der Datenquelle angibt. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 18 zurück. Ein Intermediate FIPS-Level-konformen-Treiber wird mindestens 128 zurückgegeben.  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der angibt, die maximale Anzahl von Tabellen, die innerhalb der **FROM** -Klausel eine **wählen** Anweisung. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 Ein FIPS-Eintrag-Level-konformen-Treiber gibt mindestens 15 zurück. Ein Intermediate FIPS-Level-konformen-Treiber gibt mindestens 50 zurück.  
  
 SQL_MAX_USER_NAME_LEN(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der die maximale Länge des einen Benutzernamen in der Datenquelle angibt. Wenn keine maximale Länge oder die Länge unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_MULT_RESULT_SETS (ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle mehrere Resultsets "N" unterstützt, wenn dies nicht der Fall.  
  
 Weitere Informationen über mehrere Resultsets finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 SQL_MULTIPLE_ACTIVE_TXN(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn der Treiber mehr als eine aktive Transaktion zur gleichen Zeit, "N" unterstützt, wenn nur eine Transaktion zu einem beliebigen Zeitpunkt aktiv sein kann.  
  
 Die Informationen zurückgegeben, die für diesen Informationstyp gilt nicht bei verteilten Transaktionen.  
  
 SQL_NEED_LONG_DATA_LEN(ODBC 2.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle, die Länge eines long-Daten-Werts benötigt (der Datentyp ist SQL_LONGVARCHAR, SQL_LONGVARBINARY oder einen long-Daten datenquellenspezifische-Datentyp), bevor Sie diesen Wert wird an die Datenquelle "N" gesendet, wenn dies nicht der Fall. Weitere Informationen finden Sie unter [SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md) und [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 SQL_NON_NULLABLE_COLUMNS(ODBC 1.0)  
 Ein SQLUSMALLINT-Wert, der angibt, ob die Datenquelle NOT NULL in Spalten unterstützt:  
  
 SQL_NNC_NULL = alle Spalten muss NULL-Werte zulässt.  
  
 SQL_NNC_NON_NULL = Spalten darf nicht NULL sein. (Die Datenquelle unterstützt die **NOT NULL** spalteneinschränkung in **CREATE TABLE** Anweisungen.)  
  
 Ein SQL-92-Eintrag-Level-konformen-Treiber gibt SQL_NNC_NON_NULL zurück.  
  
 SQL_NULL_COLLATION (ODBC 2.0)  
 Ein SQLUSMALLINT-Wert, der angibt, in denen NULL-Werte in einem Resultset sortiert werden:  
  
 SQL_NC_END = NULL-Werte werden am Ende des Resultsets, unabhängig von den ASC oder DESC-Schlüsselwörter sortiert.  
  
 SQL_NC_HIGH = NULL-Werte werden am oberen Ende des Resultsets, je nach den Schlüsselwörtern ASC oder DESC sortiert.  
  
 SQL_NC_LOW = NULL-Werte werden am unteren Ende des Resultsets, je nach den Schlüsselwörtern ASC oder DESC sortiert.  
  
 SQL_NC_START = NULL-Werte werden am Anfang des Resultsets festgelegt, unabhängig von den ASC oder DESC-Schlüsselwörter sortiert.  
  
 SQL_NUMERIC_FUNCTIONS(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC-1.0 eingeführt. Jede Bitmaske ist mit der Version mit der Bezeichnung in der sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske Auflisten von den skalaren numerischen Funktionen, die von der Treiber und der zugeordneten Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche numerischen Funktionen unterstützt werden:  
  
 SQL_FN_NUM_ABS (ODBC 1.0) SQL_FN_NUM_ACOS (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ATAN (ODBC 1.0) SQL_FN_NUM_ATAN2 (ODBC 1.0) SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_COT (ODBC 1.0) SQL_FN_NUM_DEGREES (ODBC 2.0) SQL_ FN_NUM_EXP (ODBC 1.0) SQL_FN_NUM_FLOOR (ODBC 1.0) SQL_FN_NUM_LOG (ODBC 1.0) SQL_FN_NUM_LOG10 (ODBC 2.0) SQL_FN_NUM_MOD (ODBC 1.0) SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) SQL_FN_NUM_RADIANS (ODBC 2.0) SQL_FN_NUM_RAND (ODBC 1.0) SQL_FN_ NUM_ROUND (ODBC 2.0) SQL_FN_NUM_SIGN (ODBC 1.0) SQL_FN_NUM_SIN (ODBC 1.0) SQL_FN_NUM_SQRT (ODBC 1.0) SQL_FN_NUM_TAN (ODBC 1.0) SQL_FN_NUM_TRUNCATE (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE(ODBC 3.0)  
 Eine SQLUINTEGER-Wert, der das Maß der ODBC 3. angibt *.x* -Schnittstelle, die mit der Treiber kompatibel ist.  
  
 SQL_OIC_CORE: Die Mindestebene, die alle ODBC-Treiber sind zur Einhaltung erwartet. Diese Ebene enthält grundlegende Benutzeroberflächenelemente wie z. B. das Verbindungsfunktionen, Funktionen für das Vorbereiten und Ausführen einer SQL-Anweisung, grundlegenden Satz Metadatenfunktionen, grundlegende Katalogfunktionen und So weiter.  
  
 SQL_OIC_LEVEL1: Eine Ebene, einschließlich Core Standards Compliance-Level-Funktionen sowie bildlauffähige Cursor, Lesezeichen, positioniert aktualisiert und löscht und so weiter.  
  
 SQL_OIC_LEVEL2: Eine Ebene, einschließlich der Ebene 1 Standards Compliance-Level-Funktionen sowie erweiterte Features wie z. B. Sensitivcursor; Aktualisieren Sie, löschen Sie und aktualisieren Sie, indem Sie Lesezeichen; Unterstützung für gespeicherte Prozeduren; Katalogfunktionen für die Primär-und Fremdschlüssel; Unterstützung von Multi-Katalog Und so weiter.  
  
 Weitere Informationen finden Sie unter [Schnittstelle Übereinstimmungsebenen](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 SQL_ODBC_VER(ODBC 1.0)  
 Eine Zeichenfolge mit der Version von ODBC, der der Treiber-Manager entspricht. Die Version des Formulars wird ##. ##. 0000, wobei die ersten beiden Ziffern sind die Hauptversionsnummer und die nächsten beiden Ziffern sind die Nebenversion. Dies wird nur im Treiber-Manager implementiert.  
  
 SQL_OJ_CAPABILITIES (ODBC 2.01)  
 Eine SQLUINTEGER-Bitmaske Auflisten der Typen von äußeren Verknüpfungen, die von der Treiber und die Datenquelle unterstützt werden. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Typen werden unterstützt:  
  
 SQL_OJ_LEFT = Left outer Joins werden unterstützt.  
  
 SQL_OJ_RIGHT = Right outer-Joins werden unterstützt.  
  
 SQL_OJ_FULL = vollständige äußere Joins werden unterstützt.  
  
 SQL_OJ_NESTED = geschachtelte äußere Joins werden unterstützt.  
  
 SQL_OJ_NOT_ORDERED = die Spalte mit dem Namen in der ON-Klausel der äußeren Joins müssen keine in der gleichen Reihenfolge wie ihre entsprechenden Tabellennamen in der **INKLUSIONSVERKNÜPFUNGS** Klausel.  
  
 SQL_OJ_INNER = den inneren Tabelle (die rechte Tabelle in einen left outer Join) oder die linke Tabelle in einem rechten äußeren Join kann auch in einem inner Join verwendet werden. Dies gilt nicht für vollständige äußere Joins, die nicht über eine interne Tabelle verfügen.  
  
 SQL_OJ_ALL_COMPARISON_OPS Vergleich =-Operator in der ON-Klausel möglich die ODBC-Vergleichsoperatoren. Wenn dieses Bit nicht festgelegt ist, kann nur der Vergleichsoperator gleich (=) in einem äußeren Join verwendet werden.  
  
 Wenn keine dieser Optionen zurückgegeben wird, unterstützt, wird keine äußeren Join-Klausel unterstützt.  
  
 Informationen zur Unterstützung von relationalen Operatoren in einer SELECT-Anweisung von SQL-92 definiert wird, finden Sie unter SQL_SQL92_RELATIONAL_JOIN_OPERATORS.  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT(ODBC 2.0)  
 Eine Zeichenfolge: "Y" Wenn die Spalten in der **ORDER BY** -Klausel in der select-Liste vorhanden sein muss, andernfalls "N".  
  
 SQL_PARAM_ARRAY_ROW_COUNTS(ODBC 3.0)  
 Eine SQLUINTEGER Aufzählen des Treibers Eigenschaften in Bezug auf die Verfügbarkeit der Zeile wird in einer parametrisierten Ausführung. Hat die folgenden Werte an:  
  
 SQL_PARC_BATCH = einzelner Verbraucher Zeilenanzahl stehen für jeden Satz von Parametern. Dies ist der Treiber generiert einen Batch von SQL-Anweisungen, eine für jeden Parameter legen Sie in das Array vergleichbar. Erweiterte Fehlerinformationen kann mithilfe der SQL_PARAM_STATUS_PTR Deskriptorfeld abgerufen werden.  
  
 SQL_PARC_NO_BATCH = es ist nur eine Zeilenanzahl verfügbar ist, wird die Anzahl der kumulativen Zeilen, die durch die Ausführung der Anweisung für das gesamte Array von Parametern. Dies entspricht vom Konzept her, die die Anweisung zusammen mit der vollständigen Parameter-Array als eine unteilbare Einheit behandelt. Fehler werden gleich behandelt, als ob eine Anweisung ausgeführt wurden.  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3.0)  
 Legt fest, eine SQLUINTEGER Aufzählen des Treibers Eigenschaften in Bezug auf die Verfügbarkeit des Ergebnisses in einer parametrisierten Ausführung. Hat die folgenden Werte an:  
  
 SQL_PAS_BATCH = es gibt ein Resultset pro Satz von Parametern zur Verfügung. Dies ist der Treiber generiert einen Batch von SQL-Anweisungen, eine für jeden Parameter legen Sie in das Array vergleichbar.  
  
 SQL_PAS_NO_BATCH = es ist nur ein Resultset verfügbar ist, steht das kumulierte Ergebnis aus der Ausführung der Anweisung für das gesamte Array von Parametern. Dies entspricht vom Konzept her, die die Anweisung zusammen mit der vollständigen Parameter-Array als eine unteilbare Einheit behandelt.  
  
 SQL_PAS_NO_SELECT = A Treiber lässt sich nicht auf eine Anweisung Resultset generieren, als ein Array von Parametern ausgeführt wird.  
  
 SQL_PROCEDURE_TERM (ODBC 1.0)  
 Eine Zeichenfolge mit den Datenquelle Herstellernamen für eine Prozedur; z. B. "Datenbankprozedur", "gespeicherte Prozedur", "Procedure", "Package" oder "gespeicherte Abfrage".  
  
 SQL_PROCEDURES (ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn die Datenquelle, Prozeduren unterstützt und der Treiber die ODBC-Prozedur der Aufrufsyntax unterstützt; "N" andernfalls.  
  
 SQL_POS_OPERATIONS (ODBC 2.0)  
 Eine SQLINTEGER-Bitmaske, die die Supportvorgänge in auflisten **SQLSetPos**.  
  
 Die folgenden Bitmasken werden zusammen mit dem Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden.  
  
 SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE(ODBC 2.0)  
 Ein SQLUSMALLINT-Wert wie folgt aus:  
  
 SQL_IC_UPPER = in Anführungszeichen Bezeichner in SQL Groß-/Kleinschreibung nicht und befinden sich in Großbuchstaben im Systemkatalog.  
  
 SQL_IC_LOWER = in Anführungszeichen Bezeichner in SQL Groß-/Kleinschreibung nicht und werden in Kleinbuchstaben im Systemkatalog gespeichert.  
  
 SQL_IC_SENSITIVE = in Anführungszeichen Bezeichner in SQL wird die Groß-/Kleinschreibung beachtet, und werden in gemischter Schreibung im Systemkatalog gespeichert. (In einer SQL-92-kompatible Datenbank sind Bezeichner in Anführungszeichen immer Groß-/Kleinschreibung berücksichtigt.)  
  
 SQL_IC_MIXED = in Anführungszeichen Bezeichner in SQL Groß-/Kleinschreibung nicht und werden in gemischter Schreibung im Systemkatalog gespeichert.  
  
 Ein SQL-92-Eintrag auf konformen Treiber wird SQL_IC_SENSITIVE immer zurückgegeben werden.  
  
 SQL_ROW_UPDATES(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn ein keysetgesteuerter oder eine gemischter Cursor Zeilenversionen oder Werte für alle verwaltet abgerufenen Zeilen und erkennt daher alle Updates, die auf eine Zeile von einem Benutzer vorgenommen wurden, seitdem die Zeile zuletzt abgerufen wurde. (Dies gilt nur für Updates, löschungen oder einfügungen). Der Treiber kann das SQL_ROW_UPDATED Flag zurück, auf den Zeilenstatus bei array **SQLFetchScroll** aufgerufen wird. Andernfalls "N".  
  
 SQL_SCHEMA_TERM(ODBC 1.0)  
 Eine Zeichenfolge mit den Datenquelle Herstellernamen für ein Schema; beispielsweise "Besitzer", "Autorisierungs-ID" oder "Schema".  
  
 Die Zeichenfolge kann in der oberen, unteren, oder eine gemischte Groß-zurückgegeben werden.  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer auf "Schema" zurückgegeben.  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_OWNER_TERM.  
  
 SQL_SCHEMA_USAGE(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske aufzählen die Anweisungen in denen Schemas verwendet werden können:  
  
 SQL_SU_DML_STATEMENTS = Schemas werden in allen Data Manipulation Language-Anweisungen unterstützt: **Wählen Sie**, **einfügen**, **aktualisieren**, **löschen**, und falls unterstützt, **wählen Sie für UPDATE** und positioniert, Update- und Delete -Anweisungen.  
  
 SQL_SU_PROCEDURE_INVOCATION = Schemas werden in der aufrufanweisung für ODBC-Prozeduren unterstützt.  
  
 SQL_SU_TABLE_DEFINITION = Schemas werden in allen Table-Anweisungen der Definition unterstützt: **ERSTELLT eine Tabelle**, **ERSTELLUNGSANSICHT**, **ALTER TABLE**, **TABELLENLÖSCHUNG**, und **DROP VIEW**.  
  
 SQL_SU_INDEX_DEFINITION = Schemas werden in alle indexanweisungen Definition unterstützt: **INDEXERSTELLUNG** und **DROP INDEX**.  
  
 SQL_SU_PRIVILEGE_DEFINITION = Schemas werden in alle Berechtigungen datendefinitionsanweisungen unterstützt: **GRANT** und **widerrufen**.  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer die SQL_SU_DML_STATEMENTS SQL_SU_TABLE_DEFINITION und SQL_SU_PRIVILEGE_DEFINITION Optionen zurückgegeben, da unterstützt.  
  
 Dies *Informationsart* für ODBC 3.0 von der ODBC 2.0 umbenannt wurde *Informationsart* SQL_OWNER_USAGE.  
  
 SQL_SCROLL_OPTIONS(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC-1.0 eingeführt. Jede Bitmaske ist mit der Version mit der Bezeichnung in der sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske, die die Bildlauf-Optionen für scrollfähige Cursor unterstützt auflisten.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen unterstützt werden:  
  
 SQL_SO_FORWARD_ONLY = der Cursor nur einen Bildlauf vorwärts. ODBC (1.0)  
  
 SQL_SO_STATIC = die Daten in das Ergebnis ist statisch. ODBC (2.0)  
  
 SQL_SO_KEYSET_DRIVEN = der Treiber speichert und den Schlüssel für jede Zeile im Resultset verwendet. ODBC (1.0)  
  
 SQL_SO_DYNAMIC = der Treiber behält die Schlüssel für jede Zeile im Rowset (die Keysetgröße ist identisch mit die Größe des Rowsets). ODBC (1.0)  
  
 SQL_SO_MIXED = der Treiber wird der Schlüssel, für jede Zeile in das Keyset, und die Keysetgröße die Rowsetgröße größer ist. Der Cursor ist in das Keyset keysetgesteuerte und dynamische außerhalb das Keyset. ODBC (1.0)  
  
 Informationen über bildlauffähigen Cursor finden Sie unter [scrollfähige Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 SQL_SEARCH_PATTERN_ESCAPE (ODBC 1.0)  
 Eine Zeichenfolge, die angeben, was der Treiber als Escapezeichen unterstützt, die die Verwendung des Musters Übereinstimmung Metazeichen Unterstrich (_) und Prozentzeichen (%) ermöglicht. als gültige Zeichen in Suchmuster. Dieses Escape-Zeichen gilt nur für die Katalog-Funktionsargumente, die die Suchzeichenfolgen zu unterstützen. Wenn diese Zeichenfolge leer ist, unterstützt der Treiber ein Suchmuster Escape-Zeichen nicht.  
  
 Da dieses Typs nicht allgemeinen Unterstützung von Escape-Zeichen im angegeben die **wie** -Prädikats SQL-92 enthält keine Anforderungen für diese Zeichenfolge.  
  
 Dies *Informationsart* auf Katalogfunktionen beschränkt ist. Eine Beschreibung der Verwendung des Escapezeichens in Suchzeichenfolgen-Muster finden Sie unter [Musterwerts](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 SQL_SERVER-NAME (ODBC 1.0)  
 Eine Zeichenfolge mit dem Namen der tatsächlichen Daten datenquellenspezifische Server; ist nützlich, wenn der Name der Datenquelle verwendet wird, während der **SQLConnect**, **SQLDriverConnect**, und **SQLBrowseConnect**.  
  
 SQL_SPECIAL_CHARACTERS(ODBC 2.0)  
 Eine Zeichenfolge, die alle Sonderzeichen (d. h. alle Zeichen mit Ausnahme von a bis Z, A bis Z, 0 bis 9 und Unterstrich) enthält, die in einem ID-Namen, wie z. B. einen Tabellennamen, Spaltennamen oder Indexname, für die Datenquelle verwendet werden können. Z. B. "#$^". Wenn ein Bezeichner über eine oder mehrere der folgenden Zeichen enthält, muss der Bezeichner ein Begrenzungsbezeichner sein.  
  
 SQL_SQL_CONFORMANCE(ODBC 3.0)  
 Eine SQLUINTEGER-Wert, der die Ebene der SQL-92-vom Treiber unterstützten angibt:  
  
 SQL_SC_SQL92_ENTRY = Eintrag auf SQL-92 kompatibel.  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = Sie FIPS 127-2-transitional-Level kompatibel.  
  
 SQL_SC_SQL92_FULL = vollständige Level SQL-92 kompatibel.  
  
 SQL_SC_ SQL92_INTERMEDIATE = Intermediate auf SQL-92 kompatibel.  
  
 SQL_SQL92_DATETIME_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske Auflisten von die Datetime-Skalarfunktionen, die vom Treiber und der zugeordneten Datenquelle unterstützt werden, wie in der SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Datetime-Funktionen unterstützt werden:  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske Auflisten von den Regeln für einen Fremdschlüssel in unterstützt eine **löschen** gemäß SQL-92-Anweisung.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln, die von der Datenquelle unterstützt werden:  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 Ein FIPS Transitional Level-konformen-Treiber wird immer all diese Optionen zurückgegeben, als unterstützt.  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske Auflisten von den Regeln für einen Fremdschlüssel in unterstützt eine **UPDATE** gemäß SQL-92-Anweisung.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln, die von der Datenquelle unterstützt werden:  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 Ein vollständige SQL-92 Level-konformen-Treiber wird immer all diese Optionen zurückgegeben, als unterstützt.  
  
 SQL_SQL92_GRANT(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in unterstützt Aufzählen der **GRANT** gemäß SQL-92-Anweisung.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln, die von der Datenquelle unterstützt werden:  
  
 Die SQL_SG_INSERT_COLUMN (mittlere Ebene) SQL_SG_INSERT_TABLE (Entry Level) SQL_SG_REFERENCES_TABLE (Entry Level) SQL_SG_REFERENCES_COLUMN (Entry Level) SQL_SG_SELECT_TABLE (Entry Level) SQL_SG_UPDATE_COLUMN (SQL_SG_DELETE_TABLE (Entry Level) Entry Level) SQL_SG_UPDATE_TABLE (Entry Level) SQL_SG_USAGE_ON_DOMAIN (FIPS Transitional Stufe) SQL_SG_USAGE_ON_CHARACTER_SET (FIPS Transitional Stufe) SQL_SG_USAGE_ON_COLLATION (FIPS Transitional Stufe) SQL_SG_USAGE_ON_TRANSLATION (FIPS Transitional Stufe) SQL_SG_WITH_GRANT_OPTION (Entry Level)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske Aufzählen der numerische Wert skalaren Funktionen, die vom Treiber und der zugeordneten Datenquelle unterstützt werden, gemäß SQL-92.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche numerischen Funktionen unterstützt werden:  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Prädikate in unterstützt aufzählen einer **wählen** gemäß SQL-92-Anweisung.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SP_BETWEEN (Entry Level) SQL_SP_COMPARISON (Entry Level) SQL_SP_EXISTS (Entry Level) SQL_SP_IN (Entry Level) SQL_SP_ISNOTNULL (Entry Level) SQL_SP_ISNULL (Entry Level) SQL_SP_LIKE (Entry Level) SQL_SP_MATCH_PARTIAL SQL_SP_MATCH_FULL (vollständige Stufe) (Vollständige Stufe) SQL_SP_MATCH_UNIQUE_FULL (vollständige Stufe) SQL_SP_MATCH_UNIQUE_PARTIAL (vollständige Stufe) SQL_SP_OVERLAPS (FIPS Transitional Stufe) SQL_SP_QUANTIFIED_COMPARISON (Entry Level) SQL_SP_UNIQUE (Entry Level)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die den relationalen Join-Operatoren in unterstützt aufzählen einer **wählen** gemäß SQL-92-Anweisung.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (mittlere Ebene) SQL_SRJO_CROSS_JOIN (vollständige Stufe) SQL_SRJO_EXCEPT_JOIN (mittlere Ebene) SQL_SRJO_FULL_OUTER_JOIN (mittlere Ebene) SQL_SRJO_INNER_JOIN (FIPS Transitional Stufe) SQL_SRJO_INTERSECT_JOIN (Mittlere Ebene) SQL_SRJO_LEFT_OUTER_JOIN (FIPS Transitional Stufe) SQL_SRJO_NATURAL_JOIN (FIPS Transitional Stufe) SQL_SRJO_RIGHT_OUTER_JOIN (FIPS Transitional Stufe) SQL_SRJO_UNION_JOIN (vollständige Stufe)  
  
 SQL_SRJO_INNER_JOIN gibt Unterstützung für die **INNER JOIN** Syntax und Beispielen für die inneren Join-Funktion nicht. Unterstützung für die **INNER JOIN** Syntax ist FIPS TRANSITIONAL, während die Unterstützung für die inneren Join-Funktion ist **Eintrag**.  
  
 SQL_SQL92_REVOKE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in unterstützt Aufzählen der **widerrufen** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln, die von der Datenquelle unterstützt werden:  
  
 SQL_SR_CASCADE (FIPS Transitional Stufe) SQL_SR_DELETE_TABLE (Entry Level) SQL_SR_GRANT_OPTION_FOR (mittlere Ebene) SQL_SR_INSERT_COLUMN (mittlere Ebene) SQL_SR_INSERT_TABLE (Entry Level) SQL_SR_REFERENCES_COLUMN (Entry Level) SQL_SR_ REFERENCES_TABLE (Entry Level) SQL_SR_RESTRICT (FIPS Transitional Stufe) SQL_SR_SELECT_TABLE (Entry Level) SQL_SR_UPDATE_COLUMN (Entry Level) SQL_SR_UPDATE_TABLE (Entry Level) SQL_SR_USAGE_ON_DOMAIN (FIPS Transitional Stufe) SQL_SR_USAGE_ON_ CHARACTER_SET (FIPS Transitional Stufe) SQL_SR_USAGE_ON_COLLATION (FIPS Transitional Stufe) SQL_SR_USAGE_ON_TRANSLATION (FIPS Transitional Stufe)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske Aufzählen der Konstruktor zeilenwertausdrücke in unterstützt eine **wählen** gemäß SQL-92-Anweisung. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske Auflisten von die Zeichenfolge skalaren Funktionen, die vom Treiber und der zugeordneten Datenquelle unterstützt werden, wie in der SQL-92 definiert.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Funktionen für Zeichenfolgen unterstützt werden:  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die Wertausdrücke unterstützt, auflisten, wie in der SQL-92 definiert.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen von der Datenquelle unterstützt werden:  
  
 SQL_SVE_CASE (mittlere Ebene) SQL_SVE_CAST (FIPS Transitional Stufe) SQL_SVE_COALESCE (mittlere Ebene) SQL_SVE_NULLIF (mittlere Ebene)  
  
 SQL_STANDARD_CLI_CONFORMANCE(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, auflisten, die CLI-Standard oder Standards, zu denen der Treiber entspricht. Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Ebenen der Treiber erfüllt:  
  
 SQL_SCC_XOPEN_CLI_VERSION1: Der Treiber entspricht die Open Group-CLI-Version 1.  
  
 SQL_SCC_ISO92_CLI: Der Treiber ist mit der ISO-92-CLI.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines statischen Cursors wird beschrieben, die vom Treiber unterstützt werden. Diese Bitmaske enthält der ersten Teilmenge von Attributen. die zweite Untergruppe finden Sie unter SQL_STATIC_CURSOR_ATTRIBUTES2.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_ UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (und Ersetzen Sie "statische Cursor" für "dynamische Cursor" in den Beschreibungen).  
  
 Ein Treiber für SQL-92-Intermediate Level-konformen wird in der Regel die SQL_CA1_NEXT SQL_CA1_ABSOLUTE und SQL_CA1_RELATIVE Optionen wie zurückgegeben werden unterstützt, da der Treiber scrollfähige Cursor über die eingebettete SQL FETCH-Anweisung unterstützt. Da dies nicht der zugrunde liegenden SQL-Unterstützung direkt bestimmt, möglicherweise jedoch scrollfähige Cursor nicht, auch für einen SQL-92-Intermediate-Ebene-konformen-Treiber unterstützt.  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Attribute eines statischen Cursors wird beschrieben, die vom Treiber unterstützt werden. Diese Bitmaske enthält der zweite Teilmenge von Attributen. die erste Untergruppe finden Sie unter SQL_STATIC_CURSOR_ATTRIBUTES1.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Attribute unterstützt werden:  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_ CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_ SIMULATE_UNIQUE  
  
 Beschreibungen dieser Bitmasken finden Sie unter SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (und Ersetzen Sie "statische Cursor" für "dynamische Cursor" in den Beschreibungen).  
  
 SQL_STRING_FUNCTIONS(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC-1.0 eingeführt. Jede Bitmaske ist mit der Version mit der Bezeichnung in der sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske Aufzählen der skalaren String-Funktionen, die von der Treiber und der zugeordneten Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Funktionen für Zeichenfolgen unterstützt werden:  
  
 SQL_FN_STR_ASCII (ODBC 1.0) SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 2.0) SQL_FN_STR_INSERT (ODBC 1.0) SQL_FN_STR_LCASE (ODBC 1.0) SQL_FN_STR_LEFT (ODBC 1.0) SQL_FN_STR_LENGTH (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_REPEAT (ODBC 1.0) SQL_FN_ STR_REPLACE (ODBC 1.0) SQL_FN_STR_RIGHT (ODBC 1.0) SQL_FN_STR_RTRIM (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 2.0) SQL_FN_STR_SPACE (ODBC 2.0) SQL_FN_STR_SUBSTRING (ODBC 1.0) SQL_FN_STR_UCASE (ODBC 1.0)  
  
 Wenn eine Anwendung aufrufen kann die **suchen** Skalarfunktion mit der *string_exp1*, *string_exp2 und*, und *starten* Argumente, die der Treiber Gibt die Bitmaske SQL_FN_STR_LOCATE zurück. Wenn eine Anwendung die suchen-Skalarfunktion nur aufrufen, kann die *string_exp1* und *string_exp2 und* Argumente, gibt der Treiber die SQL_FN_STR_LOCATE_2 Bitmaske. Treiber, die vollständig unterstützen die **suchen** skalare Funktion geben beide Bitmasken zurück.  
  
 (Weitere Informationen finden Sie unter [Zeichenfolgenfunktionen](../../../odbc/reference/appendixes/string-functions.md) in Anhang E, "Skalarfunktionen.")  
  
 SQL_SUBQUERIES (ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske Aufzählen der Prädikate, die Unterabfragen unterstützen:  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 Die Bitmaske SQL_SQ_CORRELATED_SUBQUERIES gibt an, dass alle Prädikate, die Unterabfragen unterstützen die korrelierte Unterabfragen unterstützt.  
  
 Ein SQL-92-Eintrag-Level-konformen-Treiber gibt immer eine Bitmaske zurück, in der alle diese Bits festgelegt sind.  
  
 SQL_SYSTEM_FUNCTIONS(ODBC 1.0)  
 Eine SQLUINTEGER-Bitmaske Aufzählen der skalare Systemfunktionen, die von der Treiber und der zugeordneten Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Systemfunktionen unterstützt werden:  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM(ODBC 1.0)  
 Eine Zeichenfolge mit den Datenquelle Herstellernamen für eine Tabelle; beispielsweise "Table" oder "Datei".  
  
 Diese Zeichenfolge kann in der oberen, unteren, oder eine gemischte Groß-sein.  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer zurückgegeben "table".  
  
 SQL_TIMEDATE_ADD_INTERVALS(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die Timestamp-Intervalle, die vom Treiber und zugeordnete Datenquelle für die Skalarfunktion TIMESTAMPADD unterstützt auflisten.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Intervalle unterstützt werden:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Ein FIPS Transitional Level-konformen-Treiber gibt immer eine Bitmaske zurück, in der alle diese Bits festgelegt sind.  
  
 SQL_TIMEDATE_DIFF_INTERVALS (ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die Timestamp-Intervalle, die vom Treiber und zugeordnete Datenquelle für die Skalarfunktion TIMESTAMPDIFF unterstützt auflisten.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Intervalle unterstützt werden:  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 Ein FIPS Transitional Level-konformen-Treiber gibt immer eine Bitmaske zurück, in der alle diese Bits festgelegt sind.  
  
 SQL_TIMEDATE_FUNCTIONS(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC-1.0 eingeführt. Jede Bitmaske ist mit der Version mit der Bezeichnung in der sie eingeführt wurde.  
  
 Eine SQLUINTEGER-Bitmaske Auflisten von der skalaren Datum und Uhrzeit-Funktionen, die von der Treiber und der zugeordneten Datenquelle unterstützt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Datums- und Uhrzeitfunktionen unterstützt werden:  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_CURTIME (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0) SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_DAYOFWEEK () ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT (ODBC 3.0) SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTH (ODBC 1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) SQL_FN_TD_NOW (ODBC 1.0) SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_ ZWEITE (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0) SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0) SQL_FN_TD_WEEK (ODBC 1.0) SQL_FN_TD_YEAR (ODBC 1.0)  
  
 SQL_TXN_CAPABLE(ODBC 1.0)  
 Hinweis: Der Informationstyp wurde in ODBC-1.0 eingeführt. jede zurückgegebene Wert ist mit der Version mit der Bezeichnung in der sie eingeführt wurde.  
  
 Ein SQLUSMALLINT-Wert, der die transaktionsunterstützung in das Treiber oder die Datenquelle beschreibt:  
  
 SQL_TC_NONE = Transaktionen nicht unterstützt. ODBC (1.0)  
  
 SQL_TC_DML = Transaktionen können nur die Anweisungen (Data Manipulation Language, DML) enthalten (**wählen**, **einfügen**, **UPDATE**, **löschen** ). Anweisungen der Data Definition Language (DDL) ist ein Fehler in eine Ursache für die Transaktion aus. ODBC (1.0)  
  
 SQL_TC_DDL_COMMIT = Transaktionen können nur DML-Anweisungen enthalten. DDL-Anweisungen (**CREATE TABLE**, **DROP INDEX**usw.) bei der eine Transaktion Ursache die Transaktion ein Commit ausgeführt werden. ODBC (2.0)  
  
 SQL_TC_DDL_IGNORE = Transaktionen können nur DML-Anweisungen enthalten. DDL-Anweisungen, die in einer Transaktion auftreten, werden ignoriert. ODBC (2.0)  
  
 SQL_TC_ALL = Transaktionen können DDL-Anweisungen und DML-Anweisungen in beliebiger Reihenfolge enthalten. ODBC (1.0)  
  
 (Da Unterstützung für Transaktionen in SQL-92 obligatorisch ist, wird ein SQL-92-konforme Funktion Treiber [jeder Ebene] nie SQL_TC_NONE zurückgegeben.)  
  
 SQL_TXN_ISOLATION_OPTION(ODBC 1.0)  
 Eine SQLUINTEGER-Bitmaske Auflisten von Transaktionsisolationsstufen aus die Treiber oder die Datenquelle.  
  
 Die folgenden Bitmasken werden zusammen mit dem Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden:  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 Beschreibungen der folgenden Isolationsstufen finden Sie unter der Beschreibung der SQL_DEFAULT_TXN_ISOLATION.  
  
 Zum Festlegen der Isolationsstufe für Transaktionen, die eine Anwendung ruft **SQLSetConnectAttr** das SQL_ATTR_TXN_ISOLATION-Attribut festgelegt. Weitere Informationen finden Sie unter [SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Ein SQL-92-Eintrag-Level-konformen-Treiber gibt stets sql_txn_serializable festgelegt sind, unterstützt. Ein FIPS Transitional Level-konformen-Treiber wird immer all diese Optionen zurückgegeben, als unterstützt.  
  
 SQL_UNION(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Unterstützung für Aufzählen der **UNION** Klausel:  
  
 SQL_U_UNION = der Datenquelle unterstützt die **UNION** Klausel.  
  
 SQL_U_UNION_ALL = der Datenquelle unterstützt die **alle** -Schlüsselwort in der **UNION** Klausel. (**SQLGetInfo** sowohl SQL_U_UNION und SQL_U_UNION_ALL in diesem Fall gibt.)  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer diese beiden Optionen zurückgegeben, da unterstützt.  
  
 SQL_USER_NAME (ODBC 1.0)  
 Eine Zeichenfolge, mit dem Namen in einer bestimmten Datenbank, die sich von der Anmeldename möglicherweise verwendet werden soll.  
  
 SQL_XOPEN_CLI_YEAR(ODBC 3.0)  
 Eine Zeichenfolge, die das Jahr der Veröffentlichung ab, der Open Group-Spezifikation gibt an, mit denen die Version des ODBC-Treiber-Managers vollständig kompatibel ist.  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 Eine Zeichenfolge: Wenn der Benutzer alle Prozeduren, die vom ausgeführt werden können "J" **SQLProcedures**; "N", wenn Prozeduren möglicherweise zurückgegeben, dass der Benutzer nicht ausgeführt werden kann.  
  
 SQL_ACCESSIBLE_TABLES(ODBC 1.0)  
 Eine Zeichenfolge: "Y", wenn der Benutzer **wählen** Berechtigungen, um alle Tabellen, die vom **SQLTables**; "N", wenn Tabellen möglicherweise zurückgegeben, dass der Benutzer zugreifen kann.  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 Ein SQLUSMALLINT-Wert, der angibt, die maximale Anzahl von aktiven Umgebungen, die der Treiber unterstützt werden. Wenn es keine angegebenen Beschränkung gibt oder der Grenzwert unbekannt ist, wird dieser Wert auf 0 (null) festgelegt.  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die Unterstützung für Aggregationsfunktionen auflisten:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 Ein Level-konformen-Treiber für SQL-92-Eintrag wird immer alle diese Optionen zurückgegeben, da unterstützt.  
  
 SQL_ALTER_DOMAIN(ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **ALTER DOMAIN** -Anweisung, wie in der SQL-92, von der Datenquelle unterstützten Daten definiert. Ein vollständige SQL-92-Ebene-kompatiblen Treiber wird immer mit all den Bitmasken zurückgegeben. Ein Rückgabewert von "0" bedeutet, dass die **ALTER DOMAIN** Anweisung wird nicht unterstützt.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = hinzufügen, die eine Einschränkung wird unterstützt (vollständige Ebene)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter der Domäne > \<Set Domain Default-Klausel > wird unterstützt (vollständige Ebene)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<Definition von Einschränkungsklausel-Name > wird unterstützt, für die Benennung von Einschränkung (mittlere Ebene)  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<Drop Domäne Constraint-Klausel > wird unterstützt (vollständige Ebene)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter der Domäne > \<Drop Domain Default-Klausel > wird unterstützt (vollständige Ebene)  
  
 Geben Sie die folgenden Bits unterstützten \<Einschränkung Attribute > Wenn \<Einschränkung hinzufügen > unterstützt wird (das SQL_AD_ADD_DOMAIN_CONSTRAINT Bit festgelegt ist):  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (vollständige Stufe) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (vollständige Stufe) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (vollständige Stufe) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (vollständige Stufe)  
  
 SQL_ALTER_TABLE(ODBC 2.0)  
 Eine SQLUINTEGER-Bitmaske, die die Klauseln in Aufzählen der **ALTER TABLE** -Anweisung von der Datenquelle unterstützt.  
  
 Der SQL-92 oder FIPS-Konformitätsgrad, an dem diese Funktion unterstützt werden muss, wird neben jeder Bitmaske in Klammern angezeigt.  
  
 Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<Spalte hinzufügen >-Klausel wird unterstützt, mit der Funktion zum Angeben der spaltensortierung (vollständige Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<Spalte hinzufügen >-Klausel wird unterstützt, mit der Funktion an die Spalte ist standardmäßig (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<Spalte hinzufügen > wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<Spalte hinzufügen >-Klausel wird unterstützt, mit der Einrichtung spalteneinschränkungen (FIPS Transitional Stufe) angeben (ODBC-Version 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<tabelleneinschränkung hinzufügen >-Klausel wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<Einschränkungsdefinition-Name > ist für die Benennung von Spalten- und tabelleneinschränkungen (mittlere Ebene) unterstützt (ODBC-Version 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<Drop Spalte > CASCADE wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<onlinespaltenänderung > \<Drop Column-Standard-Klausel > wird unterstützt (mittlere Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<Drop Spalte > RESTRICT wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<Drop Spalte > RESTRICT wird unterstützt (FIPS Transitional Ebene) (ODBC-Version 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<onlinespaltenänderung > \<Satz Spalte Default-Klausel > wird unterstützt (mittlere Ebene) (ODBC-Version 3.0)  
  
 Die folgenden Bits Geben Sie die Unterstützung \<Einschränkung Attribute > Wenn angeben von Spalten- oder tabelleneinschränkungen unterstützt wird (das SQL_AT_ADD_CONSTRAINT Bit festgelegt ist):  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (vollständige Ebene) (ODBC-Version 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (vollständige Ebene) (ODBC-Version 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (vollständige Ebene) (ODBC-Version 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (vollständige Ebene) (ODBC-Version 3.0)  
  
 SQL_ASYNC_MODE(ODBC 3.0)  
 Eine SQLUINTEGER-Wert, der die asynchrone Unterstützung im Treiber angibt:  
  
 SQL_AM_CONNECTION = Verbindung wird auf asynchrone Ausführung unterstützt. Alle Anweisungshandles, die ein Handle für die angegebene Verbindung zugeordnet sind, im asynchronen Modus oder alle im synchronen Modus sind. Ein Anweisungshandle für eine Verbindung darf nicht im asynchronen Modus sein, während ein anderes Anweisungshandle für dieselbe Verbindung im synchronen Modus (und umgekehrt) ist.  
  
 SQL_AM_STATEMENT =-Anweisung auf asynchrone Ausführung unterstützt wird. Im asynchronen Modus können einige Anweisungshandle eines Verbindungshandles zugeordnet sein, während andere Anweisungshandles auf die gleiche Verbindung im synchronen Modus sind.  
  
 SQL_AM_NONE = asynchroner Modus wird nicht unterstützt.  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 Eine SQLUINTEGER-Bitmaske, die das Verhalten des Treibers in Bezug auf die Verfügbarkeit der Zeile aufzählen zählt. Die folgenden Bitmasken werden zusammen mit den Informationstyp verwendet:  
  
 SQL_BRC_ROLLED_UP = der Zeilenanzahl für aufeinander folgende INSERT-, DELETE- oder UPDATE-Anweisungen in einem Rollup enthalten sind. Wenn dieses Bit nicht festgelegt ist, sind die Zeilenanzahl für jede Anweisung verfügbar.  
  
 SQL_BRC_PROCEDURES Zeilenanzahl, =, sind ggf. verfügbar, wenn ein Batch in einer gespeicherten Prozedur ausgeführt wird. Wenn Zeilenanzahl verfügbar sind, können sie nach oben oder einzeln verfügbar sind, abhängig von der SQL_BRC_ROLLED_UP Bit ein Rollback ausgeführt werden.  
  
 SQL_BRC_EXPLICIT Zeilenanzahl, =, sind ggf. verfügbar, wenn ein Batch ausgeführt wird, direkt durch Aufrufen **SQLExecute** oder **SQLExecDirect**. Wenn Zeilenanzahl verfügbar sind, können sie nach oben oder einzeln verfügbar sind, abhängig von der SQL_BRC_ROLLED_UP Bit ein Rollback ausgeführt werden.  
  
## <a name="example"></a>Beispiel  
 **SQLGetInfo** Listen der unterstützten Optionen gibt, als eine SQLUINTEGER-Bitmaske in **InfoValuePtr*. Die Bitmaske für jede Option wird zusammen mit dem Flag verwendet, um festzustellen, ob die Option unterstützt wird.  
  
 Beispielsweise könnte eine Anwendung den folgenden Code verwenden, um zu bestimmen, ob die skalare SUBSTRING-Funktion, vom Treiber der Verbindung zugeordnet unterstützt wird.  
  
 Ein weiteres Beispiel der Verwendung von **SQLGetInfo**, finden Sie unter [SQLTables-Funktion](../../../odbc/reference/syntax/sqltables-function.md).  
  
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
 Die Einstellung ein Verbindungsattribut zurückgeben  
 [SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 Bestimmt, ob ein Treiber eine Funktion unterstützt.  
 [SQLGetFunctions-Funktion](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 Die Einstellung für ein Anweisungsattribut zurückgeben  
 [SQLGetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 Zurückgeben von Informationen zu Datentypen für eine Datenquelle  
 [SQLGetTypeInfo-Funktion](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
