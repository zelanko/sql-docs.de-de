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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c77f8e6bd137b557b150ba91c143abb5438778c8
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536629"
---
# <a name="sqlprepare-function"></a>SQLPrepare-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLPrepare** eine SQL-Zeichenfolge für die Ausführung vorbereitet.  
  
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
 [Eingabe] SQL-Text-Zeichenfolge.  
  
 *TextLength*  
 [Eingabe] Länge der **StatementText* in Zeichen.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLPrepare** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLPrepare** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Ein Attribut für die angegebene Anweisung ist ungültig aufgrund der Implementierung Arbeitsbedingungen, also ein ähnlichen Wert vorübergehend ersetzt wurde. (**SQLGetStmtAttr** aufgerufen werden, um zu bestimmen, welche vorübergehend ersetzten Werts ist.) Der Ersatzwert ist gültig für die *StatementHandle* bis der Cursor geschlossen wird. Die Anweisungsattribute, die geändert werden können, sind: SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE SQL_ATTR_KEYSET_SIZE SQL_ATTR_MAX_LENGTH SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT SQL_ATTR_SIMULATE_CURSOR<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|21S01|Die Liste einzufügender Werte entspricht nicht der Spaltenliste.|\**StatementText* enthalten eine **einfügen** -Anweisung, und die Anzahl der einzufügenden Werte entsprach nicht den Grad der abgeleiteten Tabelle.|  
|21S02|Spaltenzahl der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|\**StatementText* enthalten eine **CREATE VIEW** -Anweisung, und die Anzahl der angegebenen Namen ist nicht den gleichen Grad an, wie die abgeleitete Tabelle, die durch die Query-Spezifikation definiert.|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|**StatementText* enthalten eine SQL-Anweisung, die ein Literal oder die Parameter enthalten, und der Wert ist nicht kompatibel mit dem Datentyp der Spalte zugeordnete Tabelle.|  
|22019|Ungültiges Escapezeichen|Das Argument *StatementText* enthalten eine **wie** Prädikat mit einer **ESCAPE** in die **, in denen** -Klausel und die Länge der-Escapesequenz folgende Zeichen **ESCAPEZEICHEN** war nicht gleich 1.|  
|22025|Ungültige Escapesequenz|Das Argument *StatementText* enthaltenen "**wie** _Musterwert_ **ESCAPE** _Escapezeichen_"in der **, in denen** -Klausel und das Zeichen folgt das Escape-Zeichen in der Pattern-Wert wurde weder"%"noch"_".|  
|24000|Ungültiger Cursorstatus|(DM) ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|34000|Ungültiger Cursorname|\**StatementText* enthalten eine positionierte **löschen** oder eine positionierte **UPDATE**, und der Cursor die vorbereitete Anweisung verweist auf konnte nicht geöffnet werden.|  
|3D000|Ungültiger Katalogname|Der Name des Katalogs im angegebenen *StatementText* war ungültig.|  
|3F000|Ungültiger Schemaname|Der Schemaname, der im angegebenen *StatementText* war ungültig.|  
|42000|Syntaxfehler oder zugriffsverletzung|\**StatementText* enthielt eine SQL­Anweisung, die nicht vorbereitbaren war oder einen Syntaxfehler enthalten.<br /><br /> **StatementText* enthielt eine Anweisung, die für die der Benutzer nicht über die erforderlichen Berechtigungen.|  
|42S01|Basistabelle oder-Sicht ist bereits vorhanden.|\**StatementText* enthalten eine **CREATE TABLE** oder **CREATE VIEW** -Anweisung und der Tabellenname oder Ansicht, die Namen bereits vorhanden ist.|  
|42S02|Die Basistabelle oder-Sicht wurde nicht gefunden|\**StatementText* enthalten eine **DROP TABLE** oder **DROP VIEW** -Anweisung und der angegebenen Tabelle oder Sichtname Name ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **ALTER TABLE** Anweisung und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE VIEW** -Anweisung und einem Tabellennamen oder Ansicht, die von der Abfragespezifikation definierten Namen ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE INDEX** Anweisung und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **GRANT** oder **widerrufen** -Anweisung und der angegebenen Tabelle oder Sichtname Name ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **wählen** -Anweisung und eine angegebene Tabelle oder Sichtname Name ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **löschen**, **einfügen**, oder **UPDATE** Anweisung und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE TABLE** -Anweisung und eine Tabelle in einer Einschränkung (Verweis auf eine Tabelle außer der erstellt wird) angegeben war nicht vorhanden.|  
|42S11|Index ist bereits vorhanden.|\**StatementText* enthalten eine **CREATE INDEX** -Anweisung und der angegebene Indexname bereits vorhanden war.|  
|42S12|Der Index wurde nicht gefunden.|\**StatementText* enthalten eine **DROP INDEX** -Anweisung und der angegebene Indexname ist nicht vorhanden.|  
|42S21|Spalte ist bereits vorhanden.|\**StatementText* enthalten eine **ALTER TABLE** -Anweisung und die Spalte angegeben wird, der **hinzufügen** -Klausel ist nicht eindeutig oder identifiziert eine vorhandene Spalte in der Basistabelle.|  
|42S22|Spalte wurde nicht gefunden|\**StatementText* enthalten eine **CREATE INDEX** -Anweisung, und mindestens eine der Spalte in der Spaltenliste angegebene Namen ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **GRANT** oder **widerrufen** -Anweisung und einen Namen für die angegebene Spalte ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **wählen**, **löschen**, **einfügen**, oder **UPDATE** -Anweisung und einen angegebenen Spaltennamen war nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE TABLE** -Anweisung und eine Spalte in einer Einschränkung (Verweis auf eine Tabelle außer der erstellt wird) angegeben war nicht vorhanden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*, und klicken Sie dann die Funktion aufgerufen wurde erneut auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|(DM) *StatementText* wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLPrepare** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) das Argument *TextLength* war kleiner oder gleich 0, aber nicht SQL_NTS gleich.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Einstellung für die Parallelität ist ungültig für den Typ des Cursors definiert.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Ruft die Anwendung **SQLPrepare** senden Sie eine SQL-Anweisung mit der Datenquelle für die datenvorbereitung. Weitere Informationen über die vorbereitete Ausführung finden Sie unter [vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md). Die Anwendung kann eine oder mehrere parametermarkierungen in der SQL-Anweisung enthalten. Um eine parametermarkierung einzuschließen, bettet die Anwendung ein Fragezeichen (?), in der SQL-Zeichenfolge, die gewünschte Position. Weitere Informationen zu Parametern finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md).  
  
> [!NOTE]  
>  Wenn eine Anwendung verwendet **SQLPrepare** vorbereiten und **SQLExecute** Übermitteln einer **COMMIT** oder **ROLLBACK** -Anweisung ist nicht möglich Interoperabilität zwischen DBMS-Produkte. Rufen Sie einen commit oder Rollback einer Transaktions, **SQLEndTran**.  
  
 Der Treiber kann ändern Sie die Anweisung zum Verwenden Sie das Format von SQL, die von der Datenquelle verwendet, und klicken Sie dann an die Datenquelle für die datenvorbereitung zu übermitteln. Insbesondere ändert der Treiber die Escapesequenzen, die zum Definieren von SQL-Syntax für bestimmte Funktionen verwendet. (Eine Beschreibung der Grammatik der SQL-Anweisung, finden Sie unter [Escapesequenzen in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) und [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).) Für den Treiber ähnelt einem Anweisungshandle ein anweisungs-ID im eingebetteten SQL-Code. Wenn die Datenquelle Anweisung-IDs unterstützt, kann der Treiber ein anweisungs-ID und die Parameterwerte an die Datenquelle senden.  
  
 Nachdem eine Anweisung vorbereitet wurde, verwendet die Anwendung das Anweisungshandle zum Verweisen auf die Anweisung in späteren Funktionsaufrufen. Die vorbereitete Anweisung, die das Anweisungshandle zugeordneten kann erneut ausgeführt werden, durch den Aufruf **SQLExecute** bis die Anwendung die Anweisung mit einem Aufruf von freigibt **SQLFreeStmt** mit der Option SQL_DROP oder bis das Anweisungshandle, in einem Aufruf von verwendet wird **SQLPrepare**, **SQLExecDirect**, mindestens die Katalogfunktionen (**SQLColumns**,  **SQLTables**und so weiter). Sobald die Anwendung eine Anweisung vorbereitet, können sie Informationen zum Format des Resultsets anfordern. Bei einigen Implementierungen Aufrufen **SQLDescribeCol** oder **SQLDescribeParam** nach **SQLPrepare** möglicherweise nicht so effizient wie das Aufrufen der Funktion nach **SQLExecute** oder **SQLExecDirect**.  
  
 Einige Treiber können keine Syntaxfehler zurückgegeben oder zugriffsverletzungen, wenn die Anwendung aufruft **SQLPrepare**. Ein Treiber behandeln Syntaxfehler und zugriffsverletzungen, kann nur Syntaxfehler, oder Syntaxfehler weder zugriffsverletzungen. Aus diesem Grund muss eine Anwendung diese Bedingungen zu verarbeiten, wenn durch das Aufrufen weiterer Funktionen wie z. B. verwandte **SQLNumResultCols**, **SQLDescribeCol**, **SQLColAttribute**, und **SQLExecute**.  
  
 Abhängig von den Funktionen des Treibers und der Datenquelle Informationen zu den Parametern (z. B. Datentypen) kann überprüft werden, wenn die Anweisung vorbereitet ist, (wenn alle Parameter gebunden wurden), oder wenn er ausgeführt wird (wenn nicht alle Parameter gebunden wurden). Für eine optimale Interoperabilität sollte eine Anwendung alle Parameter Aufheben der Bindung, die auf eine alte SQL-Anweisung vor der Vorbereitung einer neuen SQL-Anweisung in derselben Anweisung angewendet. Dies verhindert Fehler, die aufgrund von alten Parameterinformationen, die auf die neue Anweisung angewendet wird.  
  
> [!IMPORTANT]  
>  Durchführen eines Transaktionscommit, entweder durch explizites Aufrufen von **SQLEndTran** oder im Autocommit-Modus arbeiten, können dazu führen, dass die Datenquelle aus, um die Zugriffspläne für alle Anweisungen für eine Verbindung zu löschen. Weitere Informationen finden Sie unter den SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Informationstypen in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [Auswirkung von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), und [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Zuordnen eines Anweisungshandles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Binden einen Puffer, an einen parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen eines Commit- oder Rollback-Vorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Die Anzahl der von einer Anweisung betroffenen Zeilen zurückgibt|[SQLRowCount-Funktion](../../../odbc/reference/syntax/sqlrowcount-function.md)|  
|Ein Cursorname festlegen|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
