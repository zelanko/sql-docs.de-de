---
title: SQLPrepare-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPrepare
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPrepare
helpviewer_keywords:
- SQLPrepare function [ODBC]
ms.assetid: 332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e9aedd665df2a943627207902d592d597c503c63
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306881"
---
# <a name="sqlprepare-function"></a>SQLPrepare-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLPrepare** bereitet eine SQL-Zeichenfolge für die Ausführung vor.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLPrepare(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     StatementText,  
     SQLINTEGER    TextLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *Status Text*  
 Der SQL-Text Zeichenfolge.  
  
 *TextLength*  
 Der Länge von **Status Text* in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLPrepare** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLPrepare** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s02 entsprechen|Optionswert geändert|Ein angegebenes Anweisungs Attribut war aufgrund von Implementierungs Arbeitsbedingungen ungültig, sodass ein ähnlicher Wert vorübergehend ersetzt wurde. (**SQLGetStmtAttr** kann aufgerufen werden, um zu bestimmen, was der temporär ersetzte Wert ist.) Der Ersatzwert ist für " *StatementHandle* " gültig, bis der Cursor geschlossen wird. Die Anweisungs Attribute, die geändert werden können, sind: SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE SQL_ATTR_KEYSET_SIZE SQL_ATTR_MAX_LENGTH SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT SQL_ATTR_SIMULATE_CURSOR<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|21s01|Die einfügewertliste stimmt nicht mit der Spaltenliste|\*" *Status Text* " enthielt eine **Insert** -Anweisung, und die Anzahl der einzufügenden Werte entsprach nicht dem Grad der abgeleiteten Tabelle.|  
|21s02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein.|\*" *Status Text* " enthielt eine **CREATE VIEW** -Anweisung, und die angegebene Anzahl von Namen entspricht nicht dem Grad der von der Abfrage Spezifikation definierten abgeleiteten Tabelle.|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|*" *Status Text* " enthielt eine SQL-Anweisung, die ein Literalzeichen oder einen Parameter enthielt, und der Wert war mit dem Datentyp der zugeordneten Tabellenspalte nicht kompatibel.|  
|22019|Ungültiges Escapezeichen|Das Argument " *Status Text* " enthielt ein **like** -Prädikat mit einem Escapezeichen **in der** **Where** -Klausel, und die Länge des Escape-Zeichens nach Escapezeichen **war nicht** gleich 1.|  
|22025|Ungültige Escape-Sequenz|Das Argument *"Status Text* " enthielt in der **Where** -Klausel "**like** _Pattern Value_ **Escape** _Escapezeichen_", und das Zeichen nach dem Escapezeichen im Muster Wert war weder "%" noch "_".|  
|24.000|Ungültiger Cursorstatus|(DM) ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen.<br /><br /> Ein Cursor war auf dem *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|34000|Ungültiger Cursorname|\*" *Status Text* " enthielt ein positioniertes **Löschen** oder ein positioniertes **Update**, und der Cursor, auf den von der vorbereiteten Anweisung verwiesen wird, war nicht geöffnet.|  
|3D000|Ungültiger Katalog Name.|Der in " *Status Text* " angegebene Katalog Name war ungültig.|  
|3F-|Ungültiger Schema Name.|Der in ' *Status Text* ' angegebene Schema Name war ungültig.|  
|42000|Syntax Fehler oder Zugriffsverletzung|\*" *Status Text* " enthielt eine SQL-Anweisung, die nicht vorbereit ist oder einen Syntax Fehler enthielt.<br /><br /> *" *Status Text* " enthielt eine Anweisung, für die der Benutzer nicht über die erforderlichen Berechtigungen verfügte.|  
|42s01|Die Basistabelle oder-Sicht ist bereits vorhanden.|\*" *Status Text* " enthielt eine **CREATE TABLE** -oder **CREATE VIEW** -Anweisung, und der angegebene Tabellen-oder Sichtname ist bereits vorhanden.|  
|42s02|Die Basistabelle oder-Sicht wurde nicht gefunden.|\*" *Status Text* " enthielt eine **DROP TABLE** -oder **Drop View** -Anweisung, und der angegebene Tabellen-oder Sichtname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **ALTER TABLE** -Anweisung, und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **CREATE VIEW** -Anweisung, und ein von der Abfrage Spezifikation definierter Tabellen-oder Sichtname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Create Index** -Anweisung, und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Grant** -oder **Widerruf** -Anweisung, und der angegebene Tabellen-oder Sichtname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Select** -Anweisung, und ein angegebener Tabellenname oder Sichtname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Delete**-, **Insert**-oder **Update** -Anweisung, und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **CREATE TABLE** -Anweisung, und eine Tabelle, die in einer Einschränkung angegeben ist (die auf eine andere Tabelle als die erstellte Tabelle verweist), ist nicht vorhanden.|  
|42s11|Index ist bereits vorhanden.|\*" *Status Text* " enthielt eine **Create Index** -Anweisung, und der angegebene Indexname war bereits vorhanden.|  
|42s12|Index nicht gefunden.|\*" *Status Text* " enthielt eine **Drop Index** -Anweisung, und der angegebene Indexname ist nicht vorhanden.|  
|42s21|Spalte ist bereits vorhanden.|\*" *Status Text* " enthielt eine **ALTER TABLE** -Anweisung, und die in der **Add** -Klausel angegebene Spalte ist nicht eindeutig oder identifiziert eine vorhandene Spalte in der Basistabelle.|  
|42s22|Spalte nicht gefunden|\*" *Status Text* " enthielt eine **Create Index** -Anweisung, und mindestens einer der in der Spaltenliste angegebenen Spaltennamen ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Grant** -oder **Widerruf** -Anweisung, und ein angegebener Spaltenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Select**-, **Delete**-, **Insert**-oder **Update** -Anweisung, und ein angegebener Spaltenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **CREATE TABLE** -Anweisung, und eine Spalte, die in einer Einschränkung angegeben ist (verweist auf eine andere Tabelle als die erstellte Tabelle), ist nicht vorhanden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen, und anschließend wurde die Funktion für " *StatementHandle*" erneut aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) *Status Text* war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLPrepare** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) das Argument *TextLength* war kleiner als oder gleich 0, aber nicht gleich SQL_NTS.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Die Parallelitäts Einstellung war für den Typ des definierten Cursors ungültig.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Timeout Zeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Die Anwendung ruft **SQLPrepare** auf, um eine SQL-Anweisung zur Vorbereitung an die Datenquelle zu senden. Weitere Informationen zur vorbereiteten Ausführung finden Sie unter [vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md). Die Anwendung kann einen oder mehrere Parametermarker in der SQL-Anweisung enthalten. Wenn Sie einen Parametermarker einschließen möchten, bettet die Anwendung ein Fragezeichen (?) an der entsprechenden Position in die SQL-Zeichenfolge ein. Weitere Informationen zu Parametern finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md).  
  
> [!NOTE]  
>  Wenn eine Anwendung **SQLPrepare** zum Vorbereiten und **SQLExecute** verwendet, um eine **Commit** -oder **Rollback** -Anweisung zu übermitteln, ist Sie zwischen DBMS-Produkten nicht interoperabel. Um einen Commit oder Rollback für eine Transaktion auszuführen, nennen Sie **SQLEndTran**.  
  
 Der Treiber kann die Anweisung ändern, um die von der Datenquelle verwendete SQL-Form zu verwenden, und Sie dann zur Vorbereitung an die Datenquelle zu senden. Insbesondere ändert der Treiber die Escapesequenzen, die zum Definieren der SQL-Syntax für bestimmte Features verwendet werden. (Eine Beschreibung der Grammatik der SQL-Anweisung finden Sie unter Escapesequenzen [in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) und [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).) Für den Treiber ähnelt ein Anweisungs Handle einem Anweisungs Bezeichner in eingebettetem SQL-Code. Wenn die Datenquelle Anweisungs Bezeichner unterstützt, kann der Treiber einen Anweisungs Bezeichner und Parameterwerte an die Datenquelle senden.  
  
 Nachdem eine-Anweisung vorbereitet wurde, verwendet die Anwendung das Anweisungs Handle, um in späteren Funktionsaufrufen auf die-Anweisung zu verweisen. Die dem Anweisungs Handle zugeordnete vorbereitete Anweisung kann durch Aufrufen von **SQLExecute** erneut ausgeführt werden, bis die Anwendung die Anweisung mit einem Aufruf von **SQLFreeStmt** mit der Option SQL_DROP freigibt oder bis das Anweisungs Handle in einem Aufruf von **SQLPrepare**, **SQLExecDirect**oder einer der Katalog Funktionen (**SQLColumns**, **SQLTables**usw.) verwendet wird. Nachdem die Anwendung eine-Anweisung vorbereitet hat, kann Sie Informationen zum Format des Resultsets anfordern. Bei einigen Implementierungen ist das Aufrufen von **SQLDescribeCol** oder **SQLDescribeParam** nach **SQLPrepare** möglicherweise nicht so effizient wie das Aufrufen der Funktion nach **SQLExecute** oder **SQLExecDirect**.  
  
 Einige Treiber können keine Syntax Fehler oder Zugriffs Verletzungen zurückgeben, wenn die Anwendung **SQLPrepare**aufruft. Ein Treiber kann Syntax Fehler und Zugriffs Verletzungen, nur Syntax Fehler oder weder Syntax Fehler noch Zugriffs Verletzungen verarbeiten. Daher muss eine Anwendung in der Lage sein, diese Bedingungen zu verarbeiten, wenn Sie nachfolgende verwandte Funktionen aufrufen, wie z. b. **SQLNumResultCols**, **SQLDescribeCol**, **SQLColAttribute**und **SQLExecute**.  
  
 Abhängig von den Funktionen des Treibers und der Datenquelle können Parameterinformationen (z. b. Datentypen) geprüft werden, wenn die Anweisung vorbereitet wird (wenn alle Parameter gebunden wurden) oder wenn Sie ausgeführt wird (wenn alle Parameter nicht gebunden wurden). Zur maximalen Interoperabilität sollte eine Anwendung die Bindung aller Parameter aufheben, die auf eine alte SQL-Anweisung angewendet wurden, bevor eine neue SQL-Anweisung für dieselbe Anweisung vorbereitet wird. Dadurch wird verhindert, dass Fehler aufgrund von alten Parameterinformationen auf die neue Anweisung angewendet werden.  
  
> [!IMPORTANT]  
>  Das Ausführen eines Commits für eine Transaktion durch explizites Aufrufen von **SQLEndTran** oder durcharbeiten im Autocommitmodus kann dazu führen, dass die Datenquelle die Zugriffs Pläne für alle Anweisungen in einer Verbindung löscht. Weitere Informationen finden Sie in den SQL_CURSOR_COMMIT_BEHAVIOR-und SQL_CURSOR_ROLLBACK_BEHAVIOR-Informationstypen in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [Auswirkung von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)und [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Zuordnen eines Anweisungs Handles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Binden eines Puffers an einen Parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen eines Commit-oder Rollback-Vorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Zurückgeben der Anzahl der von einer Anweisung betroffenen Zeilen|[SQLRowCount-Funktion](../../../odbc/reference/syntax/sqlrowcount-function.md)|  
|Festlegen eines Cursor namens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
