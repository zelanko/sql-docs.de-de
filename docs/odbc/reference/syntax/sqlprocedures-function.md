---
title: SQLProcedures-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLProcedures
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLProcedures
helpviewer_keywords:
- SQLProcedures function [ODBC]
ms.assetid: d0d9ef10-2fd4-44a5-9334-649f186f4ba0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bdaf63313a339d2b25ca6648ad25c1b4466b3f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005734"
---
# <a name="sqlprocedures-function"></a>SQLProcedures-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLProcedures** gibt die Liste der in einer bestimmten Datenquelle gespeicherten Prozedur Namen zurück. *Prozedur* ist ein allgemeiner Begriff, der zum Beschreiben eines *ausführbaren Objekts*verwendet wird, oder eine benannte Entität, die mithilfe von Eingabe-und Ausgabeparametern aufgerufen werden kann. Weitere Informationen zu Verfahren finden Sie in den [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLProcedures(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      ProcName,  
     SQLSMALLINT    NameLength3);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *CatalogName*  
 Der Prozedur Katalog. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die nicht über Kataloge verfügen. *CatalogName* darf kein Zeichen folgen-Suchmuster enthalten.  
  
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
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLProcedures** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLProcedures** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor war auf dem *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde aufgrund eines Ressourcen Deadlocks mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, das *CatalogName* -Argument war ein NULL-Zeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM *) das SQL_ATTR_METADATA_ID* Statement-Attribut wurde auf SQL_TRUE festgelegt, und das Schema Name-oder *procname* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der Wert eines der namens Längen Argumente war kleiner als 0 (null), aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der namens Längen Argumente hat den maximalen Längen Wert für den entsprechenden Namen überschritten.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Es wurde ein Prozedur Katalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Prozedur Schema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Für das Prozedur Schema oder den Prozedur Namen wurde ein Muster für die Zeichen folgen Suche angegeben, und die Datenquelle unterstützt keine Suchmuster für mindestens ein Argument.<br /><br /> Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt diese Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLProcedures** listet alle Prozeduren im angeforderten Bereich auf. Ein Benutzer verfügt möglicherweise nicht über die Berechtigung zum Ausführen dieser Prozeduren. Zum Überprüfen der Barrierefreiheit kann eine Anwendung **SQLGetInfo** aufrufen und den Wert der SQL_ACCESSIBLE_PROCEDURES Informationen überprüfen. Andernfalls muss die Anwendung in der Lage sein, eine Situation zu behandeln, in der der Benutzer eine Prozedur auswählt, die nicht ausgeführt werden kann. Informationen dazu, wie diese Informationen verwendet werden können, finden Sie unter [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumente und zurückgegebene Daten von ODBC-Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLProcedures** gibt die Ergebnisse als Standardresultset zurück, geordnet nach PROCEDURE_CAT, PROCEDURE_SCHEMA und PROCEDURE_NAME.  
  
> [!NOTE]  
>  **SQLProcedures** gibt möglicherweise nicht alle Prozeduren zurück. Anwendungen können beliebige gültige Prozeduren verwenden, unabhängig davon, ob Sie von **SQLProzeduren**zurückgegeben werden.  
  
 Die folgenden Spalten wurden für ODBC 3 *. x*umbenannt. Die Spaltennamen Änderungen wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer gebunden werden.  
  
|ODBC 2,0-Spalte|ODBC 3 *. x* -Spalte|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|Prozedur _OWNER|Prozedur _SCHEM|  
  
 Zum Bestimmen der tatsächlichen Längen der Spalten PROCEDURE_CAT, PROCEDURE_SCHEM und PROCEDURE_NAME kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN und SQL_MAX_PROCEDURE_NAME_LEN aufrufen.  
  
 In der folgenden Tabelle werden die Spalten im Resultset aufgelistet. Zusätzliche Spalten, die über die Spalte 8 (PROCEDURE_TYPE) hinausgehen, können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf Treiber spezifische Spalten erhalten, indem Sie vom Ende des Resultsets abzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2,0)|1|Varchar|Prozedur Katalog Bezeichner; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Kataloge für einige Prozeduren unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Prozeduren zurückgegeben, für die keine Kataloge vorhanden sind.|  
|PROCEDURE_SCHEM (ODBC 2,0)|2|Varchar|Prozedur Schema Bezeichner; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Schemas für einige Prozeduren unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Prozeduren zurückgegeben, für die keine Schemas vorhanden sind.|  
|Procedure_name (ODBC 2,0)|3|Varchar not NULL|Prozedur Bezeichner.|  
|NUM_INPUT_PARAMS (ODBC 2,0)|4|–|Für die zukünftige Verwendung reserviert. Anwendungen sollten sich nicht auf die in diesen Ergebnis Spalten zurückgegebenen Daten stützen.|  
|NUM_OUTPUT_PARAMS (ODBC 2,0)|5|–|Für die zukünftige Verwendung reserviert. Anwendungen sollten sich nicht auf die in diesen Ergebnis Spalten zurückgegebenen Daten stützen.|  
|NUM_RESULT_SETS (ODBC 2,0)|6|–|Für die zukünftige Verwendung reserviert. Anwendungen sollten sich nicht auf die in diesen Ergebnis Spalten zurückgegebenen Daten stützen.|  
|Hinweise (ODBC 2,0)|7|Varchar|Eine Beschreibung der Prozedur.|  
|PROCEDURE_TYPE (ODBC 2,0)|8|Smallint|Definiert den Prozedurtyp:<br /><br /> SQL_PT_UNKNOWN: Es kann nicht bestimmt werden, ob die Prozedur einen Wert zurückgibt.<br /><br /> SQL_PT_PROCEDURE: das zurückgegebene Objekt ist eine Prozedur. Dies bedeutet, dass Sie keinen Rückgabewert hat.<br /><br /> SQL_PT_FUNCTION: das zurückgegebene Objekt ist eine Funktion. Das heißt, Sie verfügt über einen Rückgabewert.|  
  
 Die *SchemaName* -und *procname* -Argumente akzeptieren Suchmuster. Weitere Informationen zu gültigen Suchmustern finden Sie unter [Muster Wert Argumente](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [Prozedur Aufrufe](../../../odbc/reference/develop-app/procedure-calls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben von Informationen zu einem Treiber oder einer Datenquelle|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Zurückgeben der Parameter und Resultsetspalten einer Prozedur|[SQLProcedureColumns-Funktion](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|  
|Syntax zum Aufrufen gespeicherter Prozeduren|[Ausführen von Anweisungen](../../../odbc/reference/develop-app/executing-statements-odbc.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
