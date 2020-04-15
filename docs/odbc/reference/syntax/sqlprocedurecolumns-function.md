---
title: SQLProcedureColumns-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLProcedureColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLProcedureColumns
helpviewer_keywords:
- SQLProcedureColumns function [ODBC]
ms.assetid: 4ca37b28-a6df-465b-8988-d422d37fc025
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d81e44b116ed6f26319d31430999a61a8a17f21
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306851"
---
# <a name="sqlprocedurecolumns-function"></a>SQLProcedureColumns-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLProcedureColumns** gibt die Liste der Eingabe- und Ausgabeparameter sowie die Spalten zurück, aus denen das Resultset für die angegebenen Prozeduren besteht. Der Treiber gibt die Informationen als Ergebnissatz für die angegebene Anweisung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLProcedureColumns(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     ProcName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *Catalogname*  
 [Eingabe] Prozedurkatalogname. Wenn ein Treiber Kataloge für einige Prozeduren unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Prozeduren, die keine Kataloge haben. *CatalogName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *CatalogName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen von **CatalogName*.  
  
 *Schemaname*  
 [Eingabe] Zeichenfolgensuche-Muster für Prozedurschemanamen. Wenn ein Treiber Schemas für einige Prozeduren unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Prozeduren, die keine Schemas haben.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *SchemaName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *SchemaName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen von **SchemaName*.  
  
 *ProcName*  
 [Eingabe] Zeichenfolgensuche-Muster für Prozedurnamen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *ProcName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *ProcName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen von **ProcName*.  
  
 *ColumnName*  
 [Eingabe] Zeichenfolgensuchmuster für Spaltennamen.  
  
 Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *ColumnName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE, ist *ColumnName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength4*  
 [Eingabe] Länge in Zeichen von **ColumnName*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLProcedureColumns** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von SQLProcedureColumns zurückgegeben werden, und es werden die **SQLSTATE-Werte** im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|24.000|Ungültiger Cursorstatus|Im *StatementHandle*wurde ein Cursor geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Im *StatementHandle*wurde ein Cursor geöffnet, **SQLFetch** oder **SQLFetchScroll** wurden jedoch nicht aufgerufen.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcenstillstands mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLError** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das attribut SQL_ATTR_METADATA_ID Anweisung wurde auf SQL_TRUE festgelegt, das *Argument CatalogName* war ein Nullzeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) Das SQL_ATTR_METADATA_ID-Anweisungsattribut wurde auf SQL_TRUE festgelegt, und das Argument *SchemaName*, *ProcName*oder *ColumnName* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese aynschronous-Funktion wurde noch ausgeführt, als die SQLProcedureColumns-Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der Wert eines der Argumente für die Namenslänge war kleiner als 0, aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der Namenslängenargumente hat den maximalen Längenwert für den entsprechenden Katalog-, Schema-, Prozedur- oder Spaltennamen überschritten.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Es wurde ein Prozedurkatalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Prozedurschema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Für das Prozedurschema, den Prozedurnamen oder den Spaltennamen wurde ein Zeichenfolgensuchmuster angegeben, und die Datenquelle unterstützt keine Suchmuster für eines oder mehrere dieser Argumente.<br /><br /> Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Timeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird in der Regel vor der Anweisungsausführung verwendet, um Informationen zu Prozedurparametern und den Spalten abzurufen, aus denen das Resultset oder die von der Prozedur zurückgegebenen Sätze (falls vorhanden) besteht. Weitere Informationen finden Sie unter [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
> [!NOTE]  
>  **SQLProcedureColumns** gibt möglicherweise nicht alle Spalten zurück, die von einer Prozedur verwendet werden. Ein Treiber gibt z. B. möglicherweise nur Informationen zu den Parametern zurück, die von einer Prozedur verwendet werden, und nicht zu den Spalten in einem von ihm generierten Resultset.  
  
 Die Argumente *SchemaName*, *ProcName*und *ColumnName* akzeptieren Suchmuster. Weitere Informationen zu gültigen Suchmustern finden Sie unter [Pattern Value Arguments](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Weitere Informationen zur allgemeinen Verwendung, Argumente und zurückgegebenen Daten von ODBC-Katalogfunktionen finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLProcedureColumns** gibt die Ergebnisse als Standardergebnissatz zurück, sortiert nach PROCEDURE_CAT, PROCEDURE_SCHEM, PROCEDURE_NAME und COLUMN_TYPE. Spaltennamen werden für jede Prozedur in der folgenden Reihenfolge zurückgegeben: der Name des Rückgabewerts, die Namen der einzelnen Parameter im Prozeduraufruf (in Aufrufreihenfolge) und dann die Namen jeder Spalte im Resultset, die von der Prozedur zurückgegeben werden (in Spaltenreihenfolge).  
  
 Anwendungen sollten treiberspezifische Spalten relativ zum Ende des Resultsets binden. Weitere Informationen finden Sie unter [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
 Um die tatsächlichen Längen der Spalten PROCEDURE_CAT, PROCEDURE_SCHEM, PROCEDURE_NAME und COLUMN_NAME zu bestimmen, kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_PROCEDURE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN aufrufen.  
  
 Die folgenden Spalten wurden für ODBC 3 umbenannt. *x*. Die Änderungen des Spaltennamens wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer binden.  
  
|ODBC 2.0-Säule|ODBC 3. *x-Spalte*|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|PROCEDURE _OWNER|PROCEDURE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Die folgenden Spalten wurden dem Von **SQLProcedureColumns** für ODBC 3 zurückgegebenen Ergebnissatz hinzugefügt. *x*:  
  
-   COLUMN_DEF  
  
-   DATETIME_CODE  
  
-   CHAR_OCTET_LENGTH  
  
-   ORDINAL_POSITION  
  
-   IS_NULLABLE  
  
 In der folgenden Tabelle sind die Spalten im Resultset aufgeführt. Zusätzliche Spalten über Spalte 19 (IS_NULLABLE) hinaus können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifische Spalten erhalten, indem sie vom Ende des Resultsets herunterzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|Prozedurkatalogname; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Kataloge für einige Prozeduren unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für die Prozeduren zurück, die keine Kataloge haben.|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|Prozedurschemaname; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Schemas für einige Prozeduren unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für prozedursfreie Prozeduren zurück, die keine Schemas haben.|  
|PROCEDURE_NAME (ODBC 2.0)|3|Varchar nicht NULL|Der Name der Prozedur. Eine leere Zeichenfolge wird für eine Prozedur zurückgegeben, die keinen Namen hat.|  
|COLUMN_NAME (ODBC 2.0)|4|Varchar nicht NULL|Prozedurspaltenname. Der Treiber gibt eine leere Zeichenfolge für eine Prozedurspalte zurück, die keinen Namen hat.|  
|COLUMN_TYPE (ODBC 2.0)|5|Smallint nicht NULL|Definiert die Prozedurspalte als Parameter oder Als Ergebnissatzspalte:<br /><br /> SQL_PARAM_TYPE_UNKNOWN: Die Prozedurspalte ist ein Parameter, dessen Typ unbekannt ist. (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT: Die Prozedurspalte ist ein Eingabeparameter. (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT_OUTPUT: Die Prozedurspalte ist ein Eingabe-/Ausgabeparameter. (ODBC 1.0)<br /><br /> SQL_PARAM_OUTPUT: Die Prozedurspalte ist ein Ausgabeparameter. (ODBC 2.0)<br /><br /> SQL_RETURN_VALUE: Die Prozedurspalte ist der Rückgabewert der Prozedur. (ODBC 2.0)<br /><br /> SQL_RESULT_COL: Die Prozedurspalte ist eine Ergebnissatzspalte. (ODBC 1.0)|  
|DATA_TYPE (ODBC 2.0)|6|Smallint nicht NULL|SQL-Datentyp. Dies kann ein ODBC SQL-Datentyp oder ein treiberspezifischer SQL-Datentyp sein. Bei Datums- und Intervalldatentypen gibt diese Spalte die knappen Datentypen zurück (z. B. SQL_TYPE_TIME oder SQL_INTERVAL_YEAR_TO_MONTH). Eine Liste gültiger ODBC SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.|  
|TYPE_NAME (ODBC 2.0)|7|Varchar nicht NULL|Datenquellenabhängiger Datentypname; z. B. "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY" oder "CHAR ( ) FOR BIT DATA".|  
|COLUMN_SIZE (ODBC 2.0)|8|Integer|Die Spaltengröße der Prozedurspalte in der Datenquelle. NULL wird für Datentypen zurückgegeben, für die die Spaltengröße nicht anwendbar ist. Weitere Informationen zur Genauigkeit finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|BUFFER_LENGTH (ODBC 2.0)|9|Integer|Die Länge in Bytes von Daten, die für einen **SQLGetData-** oder **SQLFetch-Vorgang** übertragen werden, wenn SQL_C_DEFAULT angegeben ist. Bei numerischen Daten kann diese Größe von der Größe der in der Datenquelle gespeicherten Daten abweichen. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)in Anhang D: Datentypen.|  
|DECIMAL_DIGITS (ODBC 2.0)|10|Smallint|Die Dezimalstellen der Prozedurspalte in der Datenquelle. NULL wird für Datentypen zurückgegeben, für die Dezimalstellen nicht anwendbar sind. Weitere Informationen zu Dezimalstellen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)in Anhang D: Datentypen.|  
|NUM_PREC_RADIX (ODBC 2.0)|11|Smallint|Für numerische Datentypen entweder 10 oder 2.<br /><br /> Wenn 10, geben die Werte in COLUMN_SIZE und DECIMAL_DIGITS die Anzahl der für die Spalte zulässigen Dezimalstellen an. Beispielsweise würde eine SPALTE DECIMAL(12,5) eine NUM_PREC_RADIX von 10, eine COLUMN_SIZE von 12 und eine DECIMAL_DIGITS von 5 zurückgeben. Eine FLOAT-Spalte könnte eine NUM_PREC_RADIX von 10, eine COLUMN_SIZE von 15 und eine DECIMAL_DIGITS von NULL zurückgeben.<br /><br /> Wenn 2, geben die Werte in COLUMN_SIZE und DECIMAL_DIGITS die Anzahl der in der Spalte zulässigen Bits an. Beispielsweise kann eine FLOAT-Spalte eine NUM_PREC_RADIX von 2, eine COLUMN_SIZE von 53 und eine DECIMAL_DIGITS von NULL zurückgeben.<br /><br /> NULL wird für Datentypen zurückgegeben, für die NUM_PREC_RADIX nicht anwendbar ist.|  
|NULLABLE (ODBC 2.0)|12|Smallint nicht NULL|Gibt an, ob die Prozedurspalte einen NULL-Wert akzeptiert:<br /><br /> SQL_NO_NULLS: Die Prozedurspalte akzeptiert keine NULL-Werte.<br /><br /> SQL_NULLABLE: Die Prozedurspalte akzeptiert NULL-Werte.<br /><br /> SQL_NULLABLE_UNKNOWN: Es ist nicht bekannt, ob die Prozedurspalte NULL-Werte akzeptiert.|  
|BEMERKUNGEN (ODBC 2.0)|13|Varchar|Eine Beschreibung der Prozedurspalte.|  
|COLUMN_DEF (ODBC 3.0)|14|Varchar|Der Standardwert der Spalte.<br /><br /> Wenn NULL als Standardwert angegeben wurde, ist diese Spalte das Wort NULL, das nicht in Anführungszeichen eingeschlossen ist. Wenn der Standardwert nicht ohne Abschneide dargestellt werden kann, enthält diese Spalte TRUNCATED ohne einschließende einfache Anführungszeichen. Wenn kein Standardwert angegeben wurde, lautet diese Spalte NULL.<br /><br /> Der Wert von COLUMN_DEF kann zum Generieren einer neuen Spaltendefinition verwendet werden, es sei denn, er enthält den Wert TRUNCATED.|  
|SQL_DATA_TYPE (ODBC 3.0)|15|Smallint nicht NULL|Der Wert des SQL-Datentyps, wie er im SQL_DESC_TYPE Feld des Deskriptors angezeigt wird. Diese Spalte entspricht der Spalte DATA_TYPE, mit Ausnahme von Datumszeit- und Intervalldatentypen.<br /><br /> Bei Datumszeit- und Intervalldatentypen gibt das Feld SQL_DATA_TYPE im Resultset SQL_INTERVAL oder SQL_DATETIME zurück, und das Feld SQL_DATETIME_SUB gibt den Untercode für den spezifischen Intervall- oder Datumszeitdatentyp zurück. (Siehe [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3.0)|16|Smallint|Der Subtype-Code für Datumszeit- und Intervalldatentypen. Für andere Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|17|Integer|Die maximale Länge in Bytes eines Zeichens oder einer binären Datentypspalte. Bei allen anderen Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|ORDINAL_POSITION (ODBC 3.0)|18|Integer nicht NULL|Bei Eingabe- und Ausgabeparametern die Ordinalposition des Parameters in der Prozedurdefinition (in steigender Parameterreihenfolge, beginnend bei 1). Für einen Rückgabewert (falls vorhanden) wird 0 zurückgegeben. Bei Ergebnisspalten ist die Ordinalposition der Spalte im Resultset, wobei die erste Spalte im Resultset die Nummer 1 ist. Wenn mehrere Resultsets vorhanden sind, werden die Positions positionen der Spalte auf fahrerspezifische Weise zurückgegeben.|  
|IS_NULLABLE (ODBC 3.0)|19|Varchar|"NO", wenn die Spalte keine NULLs enthält.<br /><br /> "YES", wenn die Spalte NULLs enthalten kann.<br /><br /> Die Spalte gibt eine leere Zeichenfolge zurück, wenn die NULL-Zulässigkeit unbekannt ist.<br /><br /> Die NULL-Zulässigkeit wird gemäß den ISO-Regeln bestimmt. Ein DBMS nach ISO SQL kann keine leere Zeichenfolge zurückgeben.<br /><br /> Der für diese Spalte zurückgegebene Wert ist ein anderer als der für die NULLABLE-Spalte zurückgegebene Wert. (Siehe die Beschreibung der Spalte NULLABLE.)|  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [Prozeduraufrufe](../../../odbc/reference/develop-app/procedure-calls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in einer vorwärtsgerichteten Richtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben einer Liste von Prozeduren in einer Datenquelle|[SQLProcedures-Funktion](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
