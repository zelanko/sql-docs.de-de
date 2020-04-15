---
title: SQLColumns-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumns
helpviewer_keywords:
- SQLColumns function [ODBC]
ms.assetid: 4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36293c1f2393e9a57351fc8cd19dcc6e3338f5cc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301256"
---
# <a name="sqlcolumns-function"></a>SQLColumns-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0 Standards Compliance: Open Group  
  
 **Zusammenfassung**  
 **SQLColumns** gibt die Liste der Spaltennamen in angegebenen Tabellen zurück. Der Treiber gibt diese Informationen als Ergebnissatz für das angegebene *StatementHandle*zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLColumns(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      ColumnName,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *Catalogname*  
 [Eingabe] Katalogname. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Kataloge haben. *CatalogName* darf kein Zeichenfolgensuchmuster enthalten.  
  
> [!NOTE]  
>  Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *CatalogName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen von **CatalogName*.  
  
 *Schemaname*  
 [Eingabe] Zeichenfolgensuchmuster für Schemanamen. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas haben.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *SchemaName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *SchemaName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen von **SchemaName*.  
  
 *TableName*  
 [Eingabe] Zeichenfolgensuchmuster für Tabellennamen.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *TableName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE, ist *TableName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen von **TableName*.  
  
 *ColumnName*  
 [Eingabe] Zeichenfolgensuchmuster für Spaltennamen.  
  
> [!NOTE]  
>  Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *ColumnName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE, ist *ColumnName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength4*  
 [Eingabe] Länge in Zeichen von **ColumnName*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLColumns** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von SQLColumns zurückgegeben werden, und es werden die **SQLSTATE-Werte** im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|24.000|Ungültiger Cursorstatus|Im *StatementHandle*wurde ein Cursor geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Im StatementHandle wurde ein Cursor *geöffnet,* **SQLFetch** oder **SQLFetchScroll** wurden jedoch nicht aufgerufen.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcendeadlocks mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das attribut SQL_ATTR_METADATA_ID Anweisung wurde auf SQL_TRUE festgelegt, das *Argument CatalogName* war ein Nullzeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) Das SQL_ATTR_METADATA_ID-Anweisungsattribut wurde auf SQL_TRUE festgelegt, und das Argument *SchemaName*, *TableName*oder *ColumnName* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLColumns-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der Wert eines der Argumente für die Namenslänge war kleiner als 0, aber nicht gleich SQL_NTS.|  
|||Der Wert eines der Namenslängenargumente hat den maximalen Längenwert für den entsprechenden Katalog oder Namen überschritten. Die maximale Länge jedes Katalogs oder Namens kann abgerufen werden, indem **SQLGetInfo** mit den *InfoType-Werten* aufgerufen wird. (Siehe "Kommentare.")|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Es wurde ein Katalogname angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schemaname angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Für den Schemanamen, den Tabellennamen oder den Spaltennamen wurde ein Zeichenfolgensuchmuster angegeben, und die Datenquelle unterstützt keine Suchmuster für eines oder mehrere dieser Argumente.<br /><br /> Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird in der Regel vor der Anweisungsausführung verwendet, um Informationen zu Spalten für eine Tabelle oder Tabellen aus dem Katalog der Datenquelle abzurufen. **SQLColumns** kann verwendet werden, um Daten für alle Arten von Elementen abzurufen, die von **SQLTables**zurückgegeben werden. Zusätzlich zu Basistabellen kann dies Ansichten, Synonyme, Systemtabellen usw. umfassen (aber nicht beschränkt auf). Im Gegensatz dazu beschreiben die Funktionen **SQLColAttribute** und **SQLDescribeCol** die Spalten in einem Resultset, und die Funktion **SQLNumResultCols** gibt die Anzahl der Spalten in einem Resultset zurück. Weitere Informationen finden Sie unter [Verwendung von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Weitere Informationen zur allgemeinen Verwendung, Argumente und zurückgegebenen Daten von ODBC-Katalogfunktionen finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLColumns** gibt die Ergebnisse als Standardergebnissatz zurück, sortiert nach TABLE_CAT, TABLE_SCHEM, TABLE_NAME und ORDINAL_POSITION.  
  
> [!NOTE]  
>  Wenn eine Anwendung mit einem ODBC 2 arbeitet. *x-Treiber* wird im Resultset keine ORDINAL_POSITION Spalte zurückgegeben. Daher bei der Arbeit mit ODBC 2. *x-Treiber,* die Reihenfolge der Spalten in der Spaltenliste, die von **SQLColumns** zurückgegeben werden, entspricht nicht unbedingt der Reihenfolge der Spalten, die zurückgegeben werden, wenn die Anwendung eine SELECT-Anweisung für alle Spalten in dieser Tabelle ausführt.  
  
> [!NOTE]  
>  **SQLColumns** gibt möglicherweise nicht alle Spalten zurück. Ein Treiber gibt z. B. möglicherweise keine Informationen zu Pseudospalten zurück, z. B. Oracle ROWID. Anwendungen können eine beliebige gültige Spalte verwenden, unabhängig davon, ob sie von **SQLColumns**zurückgegeben wird.  
>   
>  Einige Spalten, die von **SQLStatistics** zurückgegeben werden können, werden von **SQLColumns**nicht zurückgegeben. **SQLColumns** gibt z. B. die Spalten in einem Index, der über einen Ausdruck oder Filter erstellt wurde, wie SALARY + BENEFITS oder DEPT = 0012, nicht zurück.  
  
 Die Längen der VARCHAR-Spalten werden in der Tabelle nicht angezeigt. die tatsächlichen Längen hängen von der Datenquelle ab. Um die tatsächlichen Längen der TABLE_CAT-, TABLE_SCHEM-, TABLE_NAME- und COLUMN_NAME-Spalten zu bestimmen, kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN aufrufen.  
  
 Die folgenden Spalten wurden für ODBC 3 umbenannt. *x*. Die Änderungen des Spaltennamens wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer binden.  
  
|ODBC 2.0-Säule|ODBC 3. *x-Spalte*|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Die folgenden Spalten wurden dem von **SQLColumns** für ODBC 3 zurückgegebenen Resultset hinzugefügt. *x*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 In der folgenden Tabelle sind die Spalten im Resultset aufgeführt. Zusätzliche Spalten jenseits von Spalte 18 (IS_NULLABLE) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifische Spalten erhalten, indem sie vom Ende des Resultsets herunterzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Column<br /><br /> number|Datentyp|Kommentare|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Katalogname; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für tabellen zurück, die keine Kataloge haben.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Schemaname; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für Tabellen zurück, die keine Schemas haben.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar nicht NULL|Tabellenname.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar nicht NULL|Spaltenname. Der Treiber gibt eine leere Zeichenfolge für eine Spalte zurück, die keinen Namen hat.|  
|DATA_TYPE (ODBC 1.0)|5|Smallint nicht NULL|SQL-Datentyp. Dies kann ein ODBC SQL-Datentyp oder ein treiberspezifischer SQL-Datentyp sein. Bei Datums- und Intervalldatentypen gibt diese Spalte den präzisen Datentyp zurück (z. B. SQL_TYPE_DATE oder SQL_INTERVAL_YEAR_TO_MONTH anstelle des nicht präzisen Datentyps wie SQL_DATETIME oder SQL_INTERVAL). Eine Liste gültiger ODBC SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.<br /><br /> Die für ODBC 3 zurückgegebenen Datentypen. *x* und ODBC 2. *x-Anwendungen* können unterschiedlich sein. Weitere Informationen finden Sie unter [Abwärtskompatibilität und Konformität von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|TYPE_NAME (ODBC 1.0)|6|Varchar nicht NULL|Datenquellenabhängiger Datentypname; z. B. "CHAR", "VARCHAR", "MONEY", "LONG VARBINAR" oder "CHAR ( ) FOR BIT DATA".|  
|COLUMN_SIZE (ODBC 1.0)|7|Integer|Wenn DATA_TYPE SQL_CHAR oder SQL_VARCHAR ist, enthält diese Spalte die maximale Länge in Zeichen der Spalte. Bei Datetime-Datentypen ist dies die Gesamtzahl der Zeichen, die erforderlich sind, um den Wert anzuzeigen, wenn er in Zeichen konvertiert wird. Bei numerischen Datentypen ist dies entweder die Gesamtzahl der Ziffern oder die Gesamtzahl der in der Spalte zulässigen Bits gemäß der Spalte NUM_PREC_RADIX. Bei Intervalldatentypen ist dies die Anzahl der Zeichen in der Zeichendarstellung des Intervallliterals (wie durch die Intervallführungsgenauigkeit definiert, siehe [Intervalldatentyplänge](../../../odbc/reference/appendixes/interval-data-type-length.md) in Anhang D: Datentypen). Weitere Informationen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|BUFFER_LENGTH (ODBC 1.0)|8|Integer|Die Länge in Bytes von Daten, die für einen SQLGetData-, SQLFetch- oder SQLFetchScroll-Vorgang übertragen werden, wenn SQL_C_DEFAULT angegeben ist. Bei numerischen Daten kann diese Größe von der Größe der in der Datenquelle gespeicherten Daten abweichen. Dieser Wert kann von COLUMN_SIZE Spalte für Zeichendaten abweichen. Weitere Informationen zur Länge finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|DECIMAL_DIGITS (ODBC 1.0)|9|Smallint|Die Gesamtanzahl der signifikanten Ziffern rechts vom Dezimaltrennzeichen. Für SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP enthält diese Spalte die Anzahl der Ziffern in der Komponente Bruchsekunden. Bei den anderen Datentypen sind dies die Dezimalstellen der Spalte in der Datenquelle. Bei Intervalldatentypen, die eine Zeitkomponente enthalten, enthält diese Spalte die Anzahl der Ziffern rechts vom Dezimaltrennzeichen (Bruchsekunden). Bei Intervalldatentypen, die keine Zeitkomponente enthalten, lautet diese Spalte 0. Weitere Informationen zu Dezimalstellen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen. NULL wird für Datentypen zurückgegeben, für die DECIMAL_DIGITS nicht anwendbar ist.|  
|NUM_PREC_RADIX (ODBC 1.0)|10|Smallint|Für numerische Datentypen entweder 10 oder 2. Wenn es 10 ist, geben die Werte in COLUMN_SIZE und DECIMAL_DIGITS die Anzahl der Dezimalstellen an, die für die Spalte zulässig sind. Beispielsweise würde eine SPALTE DECIMAL(12,5) eine NUM_PREC_RADIX von 10, eine COLUMN_SIZE von 12 und eine DECIMAL_DIGITS von 5 zurückgeben. Eine FLOAT-Spalte könnte eine NUM_PREC_RADIX von 10, eine COLUMN_SIZE von 15 und eine DECIMAL_DIGITS von NULL zurückgeben.<br /><br /> Wenn es 2 ist, geben die Werte in COLUMN_SIZE und DECIMAL_DIGITS die Anzahl der in der Spalte zulässigen Bits an. Beispielsweise könnte eine FLOAT-Spalte einen RADIX von 2, einen COLUMN_SIZE von 53 und einen DECIMAL_DIGITS von NULL zurückgeben.<br /><br /> NULL wird für Datentypen zurückgegeben, für die NUM_PREC_RADIX nicht anwendbar ist.|  
|NULLABLE (ODBC 1.0)|11|Smallint nicht NULL|SQL_NO_NULLS, wenn die Spalte keine NULL-Werte enthalten konnte.<br /><br /> SQL_NULLABLE, wenn die Spalte NULL-Werte akzeptiert.<br /><br /> SQL_NULLABLE_UNKNOWN, ob nicht bekannt ist, ob die Spalte NULL-Werte akzeptiert.<br /><br /> Der für diese Spalte zurückgegebene Wert unterscheidet sich von dem für die Spalte IS_NULLABLE zurückgegebenen Wert. Die Spalte NULLABLE gibt mit Sicherheit an, dass eine Spalte NULLs akzeptieren kann, kann jedoch nicht mit Sicherheit angeben, dass eine Spalte keine NULLs akzeptiert. Die Spalte IS_NULLABLE zeigt mit Sicherheit an, dass eine Spalte keine NULLs akzeptieren kann, aber nicht mit Sicherheit angeben kann, dass eine Spalte NULLs akzeptiert.|  
|BEMERKUNGEN (ODBC 1.0)|12|Varchar|Eine Beschreibung der Spalte.|  
|COLUMN_DEF (ODBC 3.0)|13|Varchar|Der Standardwert der Spalte. Der Wert in dieser Spalte sollte als Zeichenfolge interpretiert werden, wenn er in Anführungszeichen eingeschlossen ist.<br /><br /> Wenn NULL als Standardwert angegeben wurde, ist diese Spalte das Wort NULL, das nicht in Anführungszeichen eingeschlossen ist. Wenn der Standardwert nicht ohne Abschneide dargestellt werden kann, enthält diese Spalte TRUNCATED, ohne einzelne Anführungszeichen einzuschließen. Wenn kein Standardwert angegeben wurde, lautet diese Spalte NULL.<br /><br /> Der Wert von COLUMN_DEF kann zum Generieren einer neuen Spaltendefinition verwendet werden, es sei denn, er enthält den Wert TRUNCATED.|  
|SQL_DATA_TYPE (ODBC 3.0)|14|Smallint nicht NULL|SQL-Datentyp, wie er im SQL_DESC_TYPE Datensatzfeld in der IRD angezeigt wird. Dies kann ein ODBC SQL-Datentyp oder ein treiberspezifischer SQL-Datentyp sein. Diese Spalte entspricht der Spalte DATA_TYPE, mit Ausnahme von Datumszeit- und Intervalldatentypen. Diese Spalte gibt den nicht präzisen Datentyp (z. B. SQL_DATETIME oder SQL_INTERVAL) anstelle des präzisen Datentyps (z. B. SQL_TYPE_DATE oder SQL_INTERVAL_YEAR_TO_MONTH) für Datums- und Intervalldatentypen zurück. Wenn diese Spalte SQL_DATETIME oder SQL_INTERVAL zurückgibt, kann der spezifische Datentyp aus der Spalte SQL_DATETIME_SUB ermittelt werden. Eine Liste gültiger ODBC SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.<br /><br /> Die für ODBC 3 zurückgegebenen Datentypen. *x* und ODBC 2. *x-Anwendungen* können unterschiedlich sein. Weitere Informationen finden Sie unter [Abwärtskompatibilität und Konformität von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|SQL_DATETIME_SUB (ODBC 3.0)|15|Smallint|Der Subtype-Code für Datumszeit- und Intervalldatentypen. Für andere Datentypen gibt diese Spalte einen NULL-Wert zurück. Weitere Informationen zu Datetime- und Intervall-Untercodes finden Sie unter "SQL_DESC_DATETIME_INTERVAL_CODE" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|16|Integer|Die maximale Länge in Bytes eines Zeichens oder einer binären Datentypspalte. Bei allen anderen Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|ORDINAL_POSITION (ODBC 3.0)|17|Integer nicht NULL|Die Ordnungsposition einer Spalte innerhalb der Tabelle. Die erste Spalte in der Tabelle ist Die Nummer 1.|  
|IS_NULLABLE (ODBC 3.0)|18|Varchar|"NO", wenn die Spalte keine NULLs enthält.<br /><br /> "YES", wenn die Spalte NULLs enthalten könnte.<br /><br /> Die Spalte gibt eine leere Zeichenfolge zurück, wenn die NULL-Zulässigkeit unbekannt ist.<br /><br /> Die NULL-Zulässigkeit wird gemäß den ISO-Regeln bestimmt. Ein DBMS nach ISO SQL kann keine leere Zeichenfolge zurückgeben.<br /><br /> Der für diese Spalte zurückgegebene Wert unterscheidet sich von dem für die Spalte NULLABLE zurückgegebenen Wert. (Siehe die Beschreibung der Spalte NULLABLE.)|  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel deklariert eine Anwendung Puffer für das von **SQLColumns**zurückgegebene Resultset . Es ruft **SQLColumns** auf, um ein Resultset zurückzugeben, das jede Spalte in der EMPLOYEE-Tabelle beschreibt. Anschließend wird **SQLBindCol** aufgerufen, um die Spalten im Resultset an die Puffer zu binden. Schließlich ruft die Anwendung jede Datenzeile mit **SQLFetch** ab und verarbeitet sie.  
  
```cpp  
// SQLColumns_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#define STR_LEN 128 + 1  
#define REM_LEN 254 + 1  
  
// Declare buffers for result set data  
SQLCHAR szSchema[STR_LEN];  
SQLCHAR szCatalog[STR_LEN];  
SQLCHAR szColumnName[STR_LEN];  
SQLCHAR szTableName[STR_LEN];  
SQLCHAR szTypeName[STR_LEN];  
SQLCHAR szRemarks[REM_LEN];  
SQLCHAR szColumnDefault[STR_LEN];  
SQLCHAR szIsNullable[STR_LEN];  
  
SQLINTEGER ColumnSize;  
SQLINTEGER BufferLength;  
SQLINTEGER CharOctetLength;  
SQLINTEGER OrdinalPosition;  
  
SQLSMALLINT DataType;  
SQLSMALLINT DecimalDigits;  
SQLSMALLINT NumPrecRadix;  
SQLSMALLINT Nullable;  
SQLSMALLINT SQLDataType;  
SQLSMALLINT DatetimeSubtypeCode;  
  
SQLHSTMT hstmt = NULL;  
  
// Declare buffers for bytes available to return  
SQLINTEGER cbCatalog;  
SQLINTEGER cbSchema;  
SQLINTEGER cbTableName;  
SQLINTEGER cbColumnName;  
SQLINTEGER cbDataType;  
SQLINTEGER cbTypeName;  
SQLINTEGER cbColumnSize;  
SQLLEN cbBufferLength;  
SQLINTEGER cbDecimalDigits;  
SQLINTEGER cbNumPrecRadix;  
SQLINTEGER cbNullable;  
SQLINTEGER cbRemarks;  
SQLINTEGER cbColumnDefault;  
SQLINTEGER cbSQLDataType;  
SQLINTEGER cbDatetimeSubtypeCode;  
SQLINTEGER cbCharOctetLength;  
SQLINTEGER cbOrdinalPosition;  
SQLINTEGER cbIsNullable;  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retcode = SQLColumns(hstmt, NULL, 0, NULL, 0, (SQLCHAR*)"CUSTOMERS", SQL_NTS, NULL, 0);  
  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      // Bind columns in result set to buffers  
      SQLBindCol(hstmt, 1, SQL_C_CHAR, szCatalog, STR_LEN,&cbCatalog);  
      SQLBindCol(hstmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &cbSchema);  
      SQLBindCol(hstmt, 3, SQL_C_CHAR, szTableName, STR_LEN,&cbTableName);  
      SQLBindCol(hstmt, 4, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);  
      SQLBindCol(hstmt, 5, SQL_C_SSHORT, &DataType, 0, &cbDataType);  
      SQLBindCol(hstmt, 6, SQL_C_CHAR, szTypeName, STR_LEN, &cbTypeName);  
      SQLBindCol(hstmt, 7, SQL_C_SLONG, &ColumnSize, 0, &cbColumnSize);  
      SQLBindCol(hstmt, 8, SQL_C_SLONG, &BufferLength, 0, &cbBufferLength);  
      SQLBindCol(hstmt, 9, SQL_C_SSHORT, &DecimalDigits, 0, &cbDecimalDigits);  
      SQLBindCol(hstmt, 10, SQL_C_SSHORT, &NumPrecRadix, 0, &cbNumPrecRadix);  
      SQLBindCol(hstmt, 11, SQL_C_SSHORT, &Nullable, 0, &cbNullable);  
      SQLBindCol(hstmt, 12, SQL_C_CHAR, szRemarks, REM_LEN, &cbRemarks);  
      SQLBindCol(hstmt, 13, SQL_C_CHAR, szColumnDefault, STR_LEN, &cbColumnDefault);  
      SQLBindCol(hstmt, 14, SQL_C_SSHORT, &SQLDataType, 0, &cbSQLDataType);  
      SQLBindCol(hstmt, 15, SQL_C_SSHORT, &DatetimeSubtypeCode, 0, &cbDatetimeSubtypeCode);  
      SQLBindCol(hstmt, 16, SQL_C_SLONG, &CharOctetLength, 0, &cbCharOctetLength);  
      SQLBindCol(hstmt, 17, SQL_C_SLONG, &OrdinalPosition, 0, &cbOrdinalPosition);  
      SQLBindCol(hstmt, 18, SQL_C_CHAR, szIsNullable, STR_LEN, &cbIsNullable);  
  
      while (SQL_SUCCESS == retcode) {  
         retcode = SQLFetch(hstmt);  
         /*  
         if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // show_error();  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // Process fetched data  
         else  
            break;  
        */  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Berechtigungen für eine Spalte oder Spalten|[SQLColumnPrivileges-Funktion](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen mehrerer Datenzeilen|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Zurückgeben von Spalten, die eine Zeile eindeutig identifizieren, oder Spalten, die automatisch durch eine Transaktion aktualisiert werden|[SQLSpecialColumns-Funktion](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|Zurückgeben von Tabellenstatistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Zurückgeben einer Liste von Tabellen in einer Datenquelle|[SQLTables-Funktion](../../../odbc/reference/syntax/sqltables-function.md)|  
|Zurückgeben von Berechtigungen für eine Tabelle oder Tabellen|[SQLTablePrivileges-Funktion](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
