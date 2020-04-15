---
title: SQLPrepare-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306881"
---
# <a name="sqlprepare-function"></a>SQLPrepare-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
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
 [Eingabe] Anweisungshandle.  
  
 *StatementText*  
 [Eingabe] SQL-Textzeichenfolge.  
  
 *TextLength*  
 [Eingabe] Länge von **StatementText* in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLPrepare** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLPrepare** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Ein angegebenes Anweisungsattribut war aufgrund von Implementierungsarbeitsbedingungen ungültig, sodass ein ähnlicher Wert vorübergehend ersetzt wurde. (**SQLGetStmtAttr** kann aufgerufen werden, um zu bestimmen, was der vorübergehend ersetzte Wert ist.) Der Ersatzwert ist für das *StatementHandle gültig,* bis der Cursor geschlossen wird. Die Anweisungsattribute, die geändert werden können, sind: SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE SQL_ATTR_KEYSET_SIZE SQL_ATTR_MAX_LENGTH SQL_ATTR_MAX_LENGTH SQL_ATTR_MAX_ROWS SQL_ATTR_MAX_LENGTH SQL_ATTR_QUERY_TIMEOUT SQL_ATTR_SIMULATE_CURSOR<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|21S01|Wertliste einfügen stimmt nicht mit der Spaltenliste überein|\**StatementText* enthielt eine **INSERT-Anweisung,** und die Anzahl der einzufügenden Werte stimmt nicht mit dem Grad der abgeleiteten Tabelle überein.|  
|21S02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|\**StatementText* enthielt eine **CREATE VIEW-Anweisung,** und die Angegebene Anzahl von Namen entspricht nicht dem Grad der abgeleiteten Tabelle, die durch die Abfragespezifikation definiert ist.|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|**StatementText* enthielt eine SQL-Anweisung, die ein Literal oder einen Parameter enthielt, und der Wert war mit dem Datentyp der zugeordneten Tabellenspalte nicht kompatibel.|  
|22019|Ungültiges Escapezeichen|Das Argument *StatementText* enthielt ein LIKE-Prädikat mit einem **ESCAPE-Zeichen** in der **WHERE-Klausel,** und die Länge des Escapezeichens nach **ESCAPE** war nicht gleich 1. **LIKE**|  
|22025|Ungültige Escapesequenz|Das Argument *StatementText* enthielt "**LIKE** _pattern value_ **ESCAPE** _escape character_" in der **WHERE-Klausel,** und das Zeichen, das dem Escapezeichen im Musterwert folgt, war weder "%" noch "_".|  
|24.000|Ungültiger Cursorstatus|(DM) Ein Cursor wurde für *das StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen.<br /><br /> Im *StatementHandle*wurde ein Cursor geöffnet, **SQLFetch** oder **SQLFetchScroll** wurden jedoch nicht aufgerufen.|  
|34000|Ungültiger Cursorname|\**StatementText* enthielt einen positionierten **DELETE** oder ein positioniertes **UPDATE**, und der Cursor, auf den von der vorbereiteten Anweisung verwiesen wurde, war nicht geöffnet.|  
|3D000|Ungültiger Katalogname|Der in *StatementText* angegebene Katalogname war ungültig.|  
|3F000|Ungültiger Schemaname|Der in *StatementText* angegebene Schemaname war ungültig.|  
|42000|Syntaxfehler oder Zugriffsverletzung|\**StatementText* enthielt eine SQL-Anweisung, die nicht präparierbar war oder einen Syntaxfehler enthielt.<br /><br /> **StatementText* enthielt eine Anweisung, für die der Benutzer nicht über die erforderlichen Berechtigungen verfügte.|  
|42S01|Basistabelle oder -ansicht ist bereits vorhanden|\**StatementText* enthielt eine **CREATE TABLE-** oder **CREATE VIEW-Anweisung,** und der angegebene Tabellenname oder Ansichtsname ist bereits vorhanden.|  
|42S02|Basistabelle oder Ansicht nicht gefunden|\**StatementText* enthielt eine **DROP TABLE** oder eine **DROP VIEW-Anweisung,** und der angegebene Tabellenname oder Ansichtsname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **ALTER TABLE-Anweisung,** und der angegebene Tabellenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE VIEW-Anweisung,** und ein tabellen- oder ansichtsname, der von der Abfragespezifikation definiert wurde, war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE INDEX-Anweisung,** und der angegebene Tabellenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **GRANT-** oder **REVOKE-Anweisung,** und der angegebene Tabellenname oder Ansichtsname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **SELECT-Anweisung,** und ein angegebener Tabellenname oder Ansichtsname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **DELETE-Anweisung**, **INSERT**oder **UPDATE-Anweisung,** und der angegebene Tabellenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE TABLE-Anweisung,** und eine in einer Einschränkung angegebene Tabelle (die auf eine andere Tabelle als die erstellte verweist) war nicht vorhanden.|  
|42S11|Index ist bereits vorhanden|\**StatementText* enthielt eine **CREATE INDEX-Anweisung,** und der angegebene Indexname war bereits vorhanden.|  
|42S12|Index nicht gefunden|\**StatementText* enthielt eine **DROP INDEX-Anweisung,** und der angegebene Indexname war nicht vorhanden.|  
|42S21|Spalte ist bereits vorhanden|\**StatementText* enthielt eine **ALTER TABLE-Anweisung,** und die in der **ADD-Klausel** angegebene Spalte ist nicht eindeutig oder identifiziert eine vorhandene Spalte in der Basistabelle.|  
|42S22|Spalte nicht gefunden|\**StatementText* enthielt eine **CREATE INDEX-Anweisung,** und einer oder mehrere der in der Spaltenliste angegebenen Spaltennamen waren nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **GRANT-** oder **REVOKE-Anweisung,** und ein angegebener Spaltenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **SELECT**-, **DELETE**- **INSERT**- oder **UPDATE-Anweisung,** und ein angegebener Spaltenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE TABLE-Anweisung,** und eine in einer Einschränkung angegebene Spalte (die auf eine andere Tabelle als die erstellte verweist) war nicht vorhanden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für den *StatementHandle*aufgerufen, und dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) *StatementText* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLPrepare-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Das Argument *TextLength* war kleiner oder gleich 0, aber nicht gleich SQL_NTS.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Die Parallelitätseinstellung war für den definierten Cursortyp ungültig.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Timeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Die Anwendung ruft **SQLPrepare** auf, um eine SQL-Anweisung zur Vorbereitung an die Datenquelle zu senden. Weitere Informationen zur vorbereiteten Ausführung finden Sie unter [Vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md). Die Anwendung kann eine oder mehrere Parametermarkierungen in der SQL-Anweisung enthalten. Um eine Parametermarkierung einzuschließen, bettet die Anwendung ein Fragezeichen (?) an der entsprechenden Position in die SQL-Zeichenfolge ein. Informationen zu Parametern finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md).  
  
> [!NOTE]  
>  Wenn eine Anwendung **SQLPrepare** zum Vorbereiten und **SQLExecute** zum Übermitteln einer **COMMIT-** oder **ROLLBACK-Anweisung** verwendet, ist sie zwischen DBMS-Produkten nicht interoperabel. Um eine Transaktion festzuschreiben oder zurückzusetzen, rufen Sie **SQLEndTran**auf.  
  
 Der Treiber kann die Anweisung so ändern, dass sie die von der Datenquelle verwendete SQL-Form verwendet und sie dann zur Vorbereitung an die Datenquelle sendet. Insbesondere ändert der Treiber die Escapesequenzen, die zum Definieren der SQL-Syntax für bestimmte Features verwendet werden. (Eine Beschreibung der SQL-Anweisungsgrammatik finden Sie [unter Escape-Sequenzen in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) und [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).) Für den Treiber ähnelt ein Anweisungshandle einem Anweisungsbezeichner im eingebetteten SQL-Code. Wenn die Datenquelle Anweisungsbezeichner unterstützt, kann der Treiber einen Anweisungsbezeichner und Parameterwerte an die Datenquelle senden.  
  
 Nachdem eine Anweisung vorbereitet wurde, verwendet die Anwendung das Anweisungshandle, um in späteren Funktionsaufrufen auf die Anweisung zu verweisen. Die vorbereitete Anweisung, die dem Anweisungshandle zugeordnet ist, kann durch Aufrufen von **SQLExecute** erneut ausgeführt werden, bis die Anwendung die Anweisung mit einem Aufruf von **SQLFreeStmt** mit der Option SQL_DROP oder bis das Anweisungshandle in einem Aufruf von **SQLPrepare**, **SQLExecDirect**oder einer der Katalogfunktionen (**SQLColumns**, **SQLTables**usw.) freigibt. Sobald die Anwendung eine Anweisung vorbereitet hat, kann sie Informationen über das Format des Resultsets anfordern. Bei einigen Implementierungen ist der Aufruf von **SQLDescribeCol** oder **SQLDescribeParam** nach **SQLPrepare** möglicherweise nicht so effizient wie das Aufrufen der Funktion nach **SQLExecute** oder **SQLExecDirect**.  
  
 Einige Treiber können keine Syntaxfehler oder Zugriffsverletzungen zurückgeben, wenn die Anwendung **SQLPrepare**aufruft. Ein Treiber kann Syntaxfehler und Zugriffsverletzungen behandeln, nur Syntaxfehler oder weder Syntaxfehler noch Zugriffsverletzungen. Daher muss eine Anwendung in der Lage sein, diese Bedingungen zu behandeln, wenn sie nachfolgende verwandte Funktionen wie **SQLNumResultCols**, **SQLDescribeCol**, **SQLColAttribute**und **SQLExecute**aufruft.  
  
 Abhängig von den Funktionen des Treibers und der Datenquelle können Parameterinformationen (z. B. Datentypen) überprüft werden, wenn die Anweisung vorbereitet wird (wenn alle Parameter gebunden wurden) oder wenn sie ausgeführt wird (wenn nicht alle Parameter gebunden wurden). Für maximale Interoperabilität sollte eine Anwendung die Bindung aller Parameter aufkleben, die auf eine alte SQL-Anweisung angewendet wurden, bevor eine neue SQL-Anweisung für dieselbe Anweisung vorbereitet wird. Dadurch werden Fehler verhindert, die darauf zurückzuführen sind, dass alte Parameterinformationen auf die neue Anweisung angewendet werden.  
  
> [!IMPORTANT]  
>  Das Festizieren einer Transaktion, entweder durch explizites Aufrufen von **SQLEndTran** oder durch Arbeiten im Autocommit-Modus, kann dazu führen, dass die Datenquelle die Zugriffspläne für alle Anweisungen in einer Verbindung löscht. Weitere Informationen finden Sie unter SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Informationstypen in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)und [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuweisen eines Anweisungshandles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Binden eines Puffers an einen Parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen eines Commit- oder Rollbackvorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Zurückgeben der Anzahl der Zeilen, die von einer Anweisung betroffen sind|[SQLRowCount-Funktion](../../../odbc/reference/syntax/sqlrowcount-function.md)|  
|Festlegen eines Cursornamens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
