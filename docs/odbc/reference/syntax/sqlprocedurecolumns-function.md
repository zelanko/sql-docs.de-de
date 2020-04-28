---
title: Sqlprocedurecolrens-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306851"
---
# <a name="sqlprocedurecolumns-function"></a>SQLProcedureColumns-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **Sqlprocedurecolrens** gibt die Liste der Eingabe-und Ausgabeparameter sowie die Spalten zurück, aus denen das Resultset für die angegebenen Prozeduren besteht. Der Treiber gibt die Informationen als Resultset für die angegebene Anweisung zurück.  
  
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
 Der Anweisungs Handle.  
  
 *CatalogName*  
 Der Der Name des Prozedur Katalogs. Wenn ein Treiber Kataloge für einige Prozeduren unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Prozeduren an, die nicht über Kataloge verfügen. *CatalogName* darf kein Zeichen folgen-Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *CatalogName* ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Der Länge in Zeichen von **CatalogName*.  
  
 *Schema Name*  
 Der Zeichen folgen Suchmuster für Prozedur Schema Namen. Wenn ein Treiber Schemas für einige Prozeduren unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Prozeduren an, die keine Schemas aufweisen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird Schema *Name* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist Schema *Name* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength2*  
 Der Länge in Zeichen von * Schema*Name*.  
  
 *ProcName*  
 Der Zeichen folgen Suchmuster für Prozedur Namen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *procname* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *procname* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength3*  
 Der Länge in Zeichen von **procname*.  
  
 *ColumnName*  
 Der Zeichen folgen Suchmuster für Spaltennamen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *ColumnName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *ColumnName* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength4*  
 Der Länge in Zeichen von **ColumnName*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLProcedureColumns** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die häufig von **sqlprocedurecolrens** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor war auf dem *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde aufgrund eines Ressourcen Deadlocks mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLError** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, das *CatalogName* -Argument war ein NULL-Zeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, und das *Schema Name-,* *procname*-oder *ColumnName* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese aynschronous-Funktion wurde noch ausgeführt, als die sqlprocedurecolrens-Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der Wert eines der namens Längen Argumente war kleiner als 0 (null), aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der namens Längen Argumente hat den maximalen Längen Wert für den entsprechenden Katalog, das Schema, die Prozedur oder den Spaltennamen überschritten.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Es wurde ein Prozedur Katalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Prozedur Schema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Ein Muster für die Zeichen folgen Suche wurde für das Prozedur Schema, den Prozedur Namen oder den Spaltennamen angegeben, und die Datenquelle unterstützt keine Suchmuster für mindestens ein Argument.<br /><br /> Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Timeout Zeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird in der Regel vor der Anweisungs Ausführung verwendet, um Informationen zu Prozedur Parametern und den Spalten abzurufen, die das Resultset oder die von der Prozedur zurückgegebenen Sätze bilden, sofern vorhanden. Weitere Informationen finden Sie unter [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
> [!NOTE]  
>  **Sqlprocedurecolumschlag** gibt möglicherweise nicht alle Spalten zurück, die von einer Prozedur verwendet werden. Beispielsweise kann ein Treiber nur Informationen zu den Parametern zurückgeben, die von einer Prozedur verwendet werden, und nicht zu den Spalten in einem Resultset, das Sie generiert.  
  
 Die *SchemaName*-, *procname*-und *ColumnName* -Argumente akzeptieren Suchmuster. Weitere Informationen zu gültigen Suchmustern finden Sie unter [Muster Wert Argumente](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumente und zurückgegebene Daten von ODBC-Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **Sqlprocedurecolrens** gibt die Ergebnisse als Standardresultset zurück, geordnet nach PROCEDURE_CAT, PROCEDURE_SCHEM, procedure_name und column_type. Spaltennamen werden für jede Prozedur in der folgenden Reihenfolge zurückgegeben: der Name des Rückgabewerts, die Namen der einzelnen Parameter im Prozedur Aufruf (in der Aufruf Reihenfolge) und dann die Namen der einzelnen Spalten im Resultset, das von der Prozedur zurückgegeben wird (in der Reihenfolge der Spalten).  
  
 Anwendungen sollten Treiber spezifische Spalten in Relation zum Ende des Resultsets binden. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
 Zum Bestimmen der tatsächlichen Längen der Spalten PROCEDURE_CAT, PROCEDURE_SCHEM, procedure_name und column_name kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_PROCEDURE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN aufrufen.  
  
 Die folgenden Spalten wurden für ODBC 3 umbenannt. *x*. Die Spaltennamen Änderungen wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer gebunden werden.  
  
|ODBC 2,0-Spalte|ODBC 3. *x* -Spalte|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|Prozedur _OWNER|PROCEDURE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Die folgenden Spalten wurden dem von **sqlprocedurecolrens** für ODBC 3 zurückgegebenen Resultset hinzugefügt. *x*:  
  
-   COLUMN_DEF  
  
-   DATETIME_CODE  
  
-   CHAR_OCTET_LENGTH  
  
-   ORDINAL_POSITION  
  
-   IS_NULLABLE  
  
 In der folgenden Tabelle werden die Spalten im Resultset aufgelistet. Zusätzliche Spalten, die über die Spalte 19 (IS_NULLABLE) hinausgehen, können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf Treiber spezifische Spalten erhalten, indem Sie vom Ende des Resultsets abzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2,0)|1|Varchar|Name des Prozedur Katalogs; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Kataloge für einige Prozeduren unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Prozeduren zurückgegeben, für die keine Kataloge vorhanden sind.|  
|PROCEDURE_SCHEM (ODBC 2,0)|2|Varchar|Prozedur Schema Name; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Schemas für einige Prozeduren unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Prozeduren zurückgegeben, für die keine Schemas vorhanden sind.|  
|Procedure_name (ODBC 2,0)|3|Varchar not NULL|Der Name der Prozedur. Für eine Prozedur, die keinen Namen hat, wird eine leere Zeichenfolge zurückgegeben.|  
|Column_name (ODBC 2,0)|4|Varchar not NULL|Der Name der Prozedur Spalte. Der Treiber gibt eine leere Zeichenfolge für eine Prozedur Spalte ohne Namen zurück.|  
|Column_type (ODBC 2,0)|5|Smallint nicht NULL|Definiert die Prozedur Spalte als Parameter oder Resultsetspalte:<br /><br /> SQL_PARAM_TYPE_UNKNOWN: die Prozedur Spalte ist ein Parameter, dessen Typ unbekannt ist. (ODBC 1,0)<br /><br /> SQL_PARAM_INPUT: die Prozedur Spalte ist ein Eingabeparameter. (ODBC 1,0)<br /><br /> SQL_PARAM_INPUT_OUTPUT: die Prozedur Spalte ist ein Eingabe-/Ausgabeparameter. (ODBC 1,0)<br /><br /> SQL_PARAM_OUTPUT: die Prozedur Spalte ist ein Output-Parameter. (ODBC 2,0)<br /><br /> SQL_RETURN_VALUE: die Prozedur Spalte ist der Rückgabewert der Prozedur. (ODBC 2,0)<br /><br /> SQL_RESULT_COL: die Prozedur Spalte ist eine Resultsetspalte. (ODBC 1,0)|  
|Data_type (ODBC 2,0)|6|Smallint nicht NULL|SQL-Datentyp. Hierbei kann es sich um einen ODBC-SQL-Datentyp oder um einen treiberspezifischen SQL-Datentyp handeln. Für DateTime-und interval-Datentypen gibt diese Spalte die präzisen Datentypen zurück (z. b. SQL_TYPE_TIME oder SQL_INTERVAL_YEAR_TO_MONTH). Eine Liste der gültigen ODBC-SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.|  
|Type_name (ODBC 2,0)|7|Varchar not NULL|Datenquellen abhängiger Datentyp Name; Beispiel: "char", "varchar", "Money", "Long varbinary" oder "char () for Bit Data".|  
|COLUMN_SIZE (ODBC 2,0)|8|Integer|Die Spaltengröße der Prozedur Spalte in der Datenquelle. NULL wird für Datentypen zurückgegeben, bei denen die Spaltengröße nicht anwendbar ist. Weitere Informationen zur Genauigkeit finden Sie unter [Spaltengröße, Dezimalstellen, Länge von Oktett übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|BUFFER_LENGTH (ODBC 2,0)|9|Integer|Die Länge der Daten in Bytes, die für einen **SQLGetData** -oder **SQLFetch** -Vorgang übertragen werden, wenn SQL_C_DEFAULT angegeben wird. Bei numerischen Daten unterscheidet sich diese Größe möglicherweise von der Größe der Daten, die in der Datenquelle gespeichert sind. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)in Anhang D: Datentypen.|  
|DECIMAL_DIGITS (ODBC 2,0)|10|Smallint|Die Dezimalstellen der Prozedur Spalte in der Datenquelle. NULL wird für Datentypen zurückgegeben, bei denen Dezimalziffern nicht zutreffend sind. Weitere Informationen zu Dezimalziffern finden Sie unter [Spaltengröße, Dezimalstellen, Länge des Oktetts übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)in Anhang D: Datentypen.|  
|NUM_PREC_RADIX (ODBC 2,0)|11|Smallint|Für numerische Datentypen, entweder 10 oder 2.<br /><br /> Wenn der Wert 10 ist, gibt die Werte in COLUMN_SIZE und DECIMAL_DIGITS die Anzahl der für die Spalte zulässigen Dezimalstellen an. Beispielsweise würde eine dezimale Spalte (12, 5) eine NUM_PREC_RADIX von 10, eine COLUMN_SIZE von 12 und eine DECIMAL_DIGITS von 5 zurückgeben. eine float-Spalte kann eine NUM_PREC_RADIX von 10, eine COLUMN_SIZE 15 und eine DECIMAL_DIGITS NULL zurückgeben.<br /><br /> Bei 2 gibt die Werte in COLUMN_SIZE und DECIMAL_DIGITS die Anzahl der in der Spalte zulässigen Bits an. Eine float-Spalte könnte z. b. eine NUM_PREC_RADIX 2, eine COLUMN_SIZE 53 und eine DECIMAL_DIGITS NULL zurückgeben.<br /><br /> NULL wird für Datentypen zurückgegeben, bei denen NUM_PREC_RADIX nicht anwendbar ist.|  
|Nullable (ODBC 2,0)|12|Smallint nicht NULL|Gibt an, ob die Prozedur Spalte einen NULL-Wert akzeptiert:<br /><br /> SQL_NO_NULLS: die Prozedur Spalte akzeptiert keine NULL-Werte.<br /><br /> SQL_NULLABLE: die Prozedur Spalte akzeptiert NULL-Werte.<br /><br /> SQL_NULLABLE_UNKNOWN: Es ist nicht bekannt, ob die Prozedur Spalte NULL-Werte akzeptiert.|  
|Hinweise (ODBC 2,0)|13|Varchar|Eine Beschreibung der Prozedur Spalte.|  
|COLUMN_DEF (ODBC 3,0)|14|Varchar|Der Standardwert der Spalte.<br /><br /> Wenn NULL als Standardwert angegeben wurde, ist diese Spalte das Wort NULL und nicht in Anführungszeichen eingeschlossen. Wenn der Standardwert nicht ohne Abschneiden dargestellt werden kann, enthält diese Spalte abgeschnitten und enthält keine einschließenden einfachen Anführungszeichen. Wenn kein Standardwert angegeben wurde, ist diese Spalte NULL.<br /><br /> Der Wert COLUMN_DEF kann verwendet werden, um eine neue Spaltendefinition zu erstellen, außer wenn Sie den abgeschnittene Wert enthält.|  
|SQL_DATA_TYPE (ODBC 3,0)|15|Smallint nicht NULL|Der Wert des SQL-Datentyps, wie er im SQL_DESC_TYPE-Feld des Deskriptors angezeigt wird. Diese Spalte ist mit Ausnahme der Datentypen datetime und Interval identisch mit der Spalte data_type.<br /><br /> Für DateTime-und interval-Datentypen gibt das SQL_DATA_TYPE-Feld im Resultset SQL_INTERVAL oder SQL_DATETIME zurück, und das SQL_DATETIME_SUB Feld gibt den Subcode für den spezifischen Interval-oder DateTime-Datentyp zurück. (Siehe [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3,0)|16|Smallint|Der Untertyp Code für DateTime-und interval-Datentypen. Für andere Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|CHAR_OCTET_LENGTH (ODBC 3,0)|17|Integer|Die maximale Länge in Bytes für eine Zeichen-oder Binär Datentyp Spalte. Bei allen anderen Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|ORDINAL_POSITION (ODBC 3,0)|18|Integer nicht NULL|Für Eingabe-und Ausgabeparameter die Ordinalposition des Parameters in der Prozedur Definition (in zunehmender Parameterreihenfolge, beginnend bei 1). Für einen Rückgabewert (sofern vorhanden) wird 0 zurückgegeben. Für Resultsetspalten die Ordinalposition der Spalte im Resultset, wobei die erste Spalte im Resultset den Wert 1 hat. Wenn mehrere Resultsets vorhanden sind, werden Spalten Ordinalpositionen in einer treiberspezifischen Weise zurückgegeben.|  
|IS_NULLABLE (ODBC 3,0)|19|Varchar|"No", wenn die Spalte keine Nullen enthält.<br /><br /> "Yes", wenn die Spalte NULL-Werten enthalten kann.<br /><br /> Die Spalte gibt eine leere Zeichenfolge zurück, wenn die NULL-Zulässigkeit unbekannt ist.<br /><br /> Die NULL-Zulässigkeit wird gemäß den ISO-Regeln bestimmt. Ein DBMS nach ISO SQL kann keine leere Zeichenfolge zurückgeben.<br /><br /> Der für diese Spalte zurückgegebene Wert ist ein anderer als der für die NULLABLE-Spalte zurückgegebene Wert. (Siehe die Beschreibung der Spalte, die NULL-Werte zulässt.)|  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [Prozedur Aufrufe](../../../odbc/reference/develop-app/procedure-calls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben einer Liste von Prozeduren in einer Datenquelle|[SQLProcedures-Funktion](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
