---
title: SQLTablePrivileges-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTablePrivileges
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTablePrivileges
helpviewer_keywords:
- SQLTablePrivileges function [ODBC]
ms.assetid: 8cfdb64f-64c5-47e6-ad57-0533ac630afa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e63677180cc86f022550477bd598eaa61013d694
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039519"
---
# <a name="sqltableprivileges-function"></a>SQLTablePrivileges-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLTablePrivileges** gibt eine Liste von Tabellen und den Berechtigungen zurück, die den einzelnen Tabellen zugeordnet sind. Der Treiber gibt die Informationen als Resultset für die angegebene Anweisung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLTablePrivileges(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *CatalogName*  
 Der Tabellen Katalog. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die nicht über Kataloge verfügen. *CatalogName* darf kein Zeichen folgen-Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *CatalogName* ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Der Länge in Zeichen von **CatalogName*.  
  
 *Schema Name*  
 Der Zeichen folgen Suchmuster für Schema Namen. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas aufweisen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird Schema *Name* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist Schema *Name* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength2*  
 Der Länge in Zeichen von * Schema*Name*.  
  
 *TableName*  
 Der Zeichen folgen Suchmuster für Tabellennamen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *TableName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *TableName* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength3*  
 Der Länge in Zeichen von **TableName*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLTablePrivileges** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLTablePrivileges** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben wurde und vom Treiber zurückgegeben wird, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor war auf dem *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde aufgrund eines Ressourcen Deadlocks mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die **SQLTablePrivileges** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die **SQLTablePrivileges** -Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die **SQLTablePrivileges** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, das *CatalogName* -Argument war ein NULL-Zeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, und das Schema *Name* -oder *TableName* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLTablePrivileges** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der Wert eines der namens Längen Argumente war kleiner als 0 (null), aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der namens Längen Argumente hat den maximalen Längen Wert für den entsprechenden Qualifizierer oder Namen überschritten.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Es wurde ein Katalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Für das Tabellen Schema, den Tabellennamen oder den Spaltennamen wurde ein Zeichen folgen Suchmuster angegeben, und die Datenquelle unterstützt keine Suchmuster für mindestens ein Argument.<br /><br /> Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Die *SchemaName* -und *TableName* -Argumente akzeptieren Suchmuster. Weitere Informationen zu gültigen Suchmustern finden Sie unter [Muster Wert Argumente](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 **SQLTablePrivileges** gibt die Ergebnisse als Standardresultset zurück, geordnet nach TABLE_CAT, TABLE_SCHEM, TABLE_NAME, Berechtigungen und Empfänger.  
  
 Zum Bestimmen der tatsächlichen Längen der Spalten TABLE_CAT, TABLE_SCHEM und table_name kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN und SQL_MAX_TABLE_NAME_LEN aufrufen.  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumente und zurückgegebene Daten von ODBC-Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Die folgenden Spalten wurden für ODBC *3. x*umbenannt. Die Spaltennamen Änderungen wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer gebunden werden.  
  
|ODBC 2,0-Spalte|ODBC *3. x* -Spalte|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 In der folgenden Tabelle werden die Spalten im Resultset aufgelistet. Zusätzliche Spalten, die über die Spalte 7 (IS_GRANTABLE) hinausgehen, können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf Treiber spezifische Spalten erhalten, indem Sie vom Ende des Resultsets abzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1,0)|1|Varchar|Katalog Name; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Tabellen zurückgegeben, die über keine Kataloge verfügen.|  
|TABLE_SCHEM (ODBC 1,0)|2|Varchar|Schema Name; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für Tabellen zurückgegeben, die keine Schemas aufweisen.|  
|Table_name (ODBC 1,0)|3|Varchar not NULL|Tabellenname.|  
|GRANTOR (ODBC 1,0)|4|Varchar|Der Name des Benutzers, der die Berechtigung gewährt hat. NULL, wenn nicht auf die Datenquelle anwendbar.<br /><br /> Für alle Zeilen, in denen der Wert in der Spalte "Empfänger" der Besitzer des Objekts ist, wird die GRANTOR-Spalte "_SYSTEM" sein.|  
|Empfänger (ODBC 1,0)|5|Varchar not NULL|Der Name des Benutzers, dem die Berechtigung gewährt wurde.|  
|Berechtigung (ODBC 1,0)|6|Varchar not NULL|Die Tabellen Berechtigung. Kann eines der folgenden oder eine Datenquellen spezifische Berechtigung sein.<br /><br /> Select: der Empfänger darf Daten für eine oder mehrere Spalten der Tabelle abrufen.<br /><br /> INSERT: der Empfänger darf neue Zeilen mit Daten für eine oder mehrere Spalten in die Tabelle einfügen.<br /><br /> Update: der Empfänger darf die Daten in einer oder mehreren Spalten der Tabelle aktualisieren.<br /><br /> DELETE: der Empfänger darf Daten Zeilen aus der Tabelle löschen.<br /><br /> Verweise: der Empfänger darf auf eine oder mehrere Spalten der Tabelle innerhalb einer Einschränkung verweisen (z. b. eine Unique-Einschränkung, eine referenzielle Einschränkung oder eine Table Check-Einschränkung).<br /><br /> Der Aktionsbereich, dem der Empfänger durch ein bestimmtes Tabellen Privileg gestattet wurde, ist Datenquellen abhängig. Beispielsweise kann der Empfänger aufgrund der Update Berechtigung alle Spalten in einer Tabelle in einer Datenquelle aktualisieren, und nur die Spalten, für die der GRANTOR über die Berechtigung aktualisieren für eine andere Datenquelle verfügt.|  
|IS_GRANTABLE (ODBC 1,0)|7|Varchar|Gibt an, ob der Empfänger berechtigt ist, anderen Benutzern die Berechtigung zu erteilen. "Yes", "No" oder NULL, wenn unbekannt oder nicht auf die Datenquelle anwendbar.<br /><br /> Eine Berechtigung ist entweder erteilbaren oder nicht erteilbaren, aber nicht beides. Das von **SQLColumnPrivileges** zurückgegebene Resultset enthält niemals zwei Zeilen, für die alle Spalten mit Ausnahme der Spalte IS_GRANTABLE denselben Wert enthalten.|  
  
## <a name="code-example"></a>Codebeispiel  
 Ein Codebeispiel für eine ähnliche Funktion finden Sie unter [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Berechtigungen für eine Spalte oder Spalten|[SQLColumnPrivileges-Funktion](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Zurückgeben der Spalten in einer Tabelle oder in Tabellen|[SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben von Tabellenstatistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Zurückgeben einer Liste von Tabellen in einer Datenquelle|[SQLTables-Funktion](../../../odbc/reference/syntax/sqltables-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
