---
title: SQLExtendedFetch-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLExtendedFetch
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExtendedFetch
helpviewer_keywords:
- SQLExtendedFetch function [ODBC]
ms.assetid: 940b5cf7-581c-4ede-8533-c67d5e9ef488
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63030b34e4b607b850f25a67357d62a7184467c8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537175"
---
# <a name="sqlextendedfetch-function"></a>SQLExtendedFetch-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: Als veraltet markiert  
  
 **Zusammenfassung**  
 **SQLExtendedFetch** angegebene Rowset von Daten aus dem Resultset abruft, und gibt Daten für alle gebundenen Spalten zurück. Rowsets können an eine absolute oder relative Position oder durch Lesezeichen angegeben werden.  
  
> [!NOTE]
>  In ODBC 3. *.x*, **SQLExtendedFetch** wurde ersetzt durch **SQLFetchScroll**. ODBC 3. *.x* Anwendungen sollten nicht aufrufen **SQLExtendedFetch**; sie sollten stattdessen Aufrufen **SQLFetchScroll**. Der Treiber-Manager zugeordnet **SQLFetchScroll** zu **SQLExtendedFetch** bei der Arbeit mit einer ODBC 2. *.x* Treiber. ODBC 3. *.x* Treiber unterstützen sollten **SQLExtendedFetch** bei Bedarf zum Arbeiten mit ODBC 2. *.x* Anwendungen, die sie aufrufen. Weitere Informationen finden Sie unter "Kommentare" und [Blockcursor, scrollbare Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLExtendedFetch(  
      SQLHSTMT         StatementHandle,  
      SQLUSMALLINT     FetchOrientation,  
      SQLLEN           FetchOffset,  
      SQLULEN *        RowCountPtr,  
      SQLUSMALLINT *   RowStatusArray);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *FetchOrientation*  
 [Eingabe] Der Typ des Abrufs. Dies entspricht dem *FetchOrientation* in **SQLFetchScroll**.  
  
 *FetchOffset*  
 [Eingabe] Die Nummer der Zeile abgerufen. Dies entspricht dem *FetchOffset* in **SQLFetchScroll**, mit einer Ausnahme. Wenn *FetchOrientation* ist SQL_FETCH_BOOKMARK, *FetchOffset* ist ein fester Länge Lesezeichen, die nicht in einem Lesezeichen als Offset. Das heißt, **SQLExtendedFetch** des Lesezeichens aus diesem Argument und nicht das SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungsattribut abgerufen. Er unterstützt keine Lesezeichen mit variabler Länge und unterstützt nicht das Abrufen eines Rowsets mit einem Offset (ungleich 0) in einem Lesezeichen.  
  
 *RowCountPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in die die Anzahl der tatsächlich abgerufenen Zeilen zurückgegeben werden sollen. Dieser Puffer wird auf die gleiche Weise als durch das SQL_ATTR_ROWS_FETCHED_PTR-Attribut-Anweisung angegebene Puffer verwendet. Dieser Puffer wird verwendet, nur von **SQLExtendedFetch**. Er wird nicht verwendet, indem **SQLFetch** oder **SQLFetchScroll**.  
  
 *RowStatusArray*  
 [Ausgabe] Zeiger auf ein Array, in dem den Status der einzelnen Zeilen zurückgegeben. Dieses Array wird in die gleiche Weise wie das Array, das durch das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR angegeben verwendet.  
  
 Die Adresse dieses Arrays ist jedoch nicht in das Feld SQL_DESC_STATUS_ARRAY_PTR IRD gespeichert werden. Darüber hinaus diesem Array werden nur von **SQLExtendedFetch** und **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD oder **SQLSetPos**bei Aufruf nach **SQLExtendedFetch**. Er wird nicht verwendet, indem **SQLFetch** oder **SQLFetchScroll**, und es ist nicht vom verwendet **SQLBulkOperations** oder **SQLSetPos** bei ihrem Aufruf nach **SQLFetch** oder **SQLFetchScroll**. Es ist auch nicht verwendet, wenn **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD wird aufgerufen, bevor alle Fetch-Funktion aufgerufen wird. Das heißt, ist es nur in der Anweisung Zustand S7 verwendet. Es wird nicht in der Anweisung Zustände S5 oder S6 verwendet. Weitere Informationen finden Sie unter [Statusübergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Übergang Statustabellen.  
  
 Anwendungen sollten Geben Sie einen gültigen Zeiger in den *RowStatusArray* -Argument; Falls nicht, das Verhalten der **SQLExtendedFetch** und das Verhalten von Aufrufen an **SQLBulkOperations**oder **SQLSetPos** nachdem durch ein Cursor positioniert ist **SQLExtendedFetch** sind nicht definiert.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLExtendedFetch** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLError**. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLExtendedFetch** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben. Bei einem für eine einzelne Spalte Fehler, **SQLGetDiagField** kann aufgerufen werden, wobei eine *DiagIdentifier* von SQL_DIAG_COLUMN_NUMBER, um die Spalte zu bestimmen, der Fehler aufgetreten ist, und  **SQLGetDiagField** kann aufgerufen werden, wobei eine *DiagIdentifier* von SQL_DIAG_ROW_NUMBER, um zu bestimmen, die Zeile, die diese Spalte enthält.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für eine Spalte zurückgegeben, führte das Abschneiden von nicht leeren Zeichen oder binäre Daten ungleich NULL. Falls es sich um einen Zeichenfolgenwert handelt, war es, rechts abgeschnitten. Falls es sich um einen numerischen Wert handelt, wurde die Nachkommastellen der Zahl abgeschnitten.  (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S01|Fehler in Zeile|Fehler beim Abrufen von ein oder mehrere Zeilen. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S06|Versucht, Daten abzurufen, bevor das Resultset das erste Rowset zurückgegeben.|Das angeforderte Rowset überlappende Anfang, wenn die aktuelle Position nach der ersten Zeile, und entweder ist das Resultset *FetchOrientation* SQL_PRIOR wurde oder *FetchOrientation* SQL_RELATIVE mit wurde ein negative *FetchOffset* , deren absoluten Wert war kleiner oder gleich der aktuellen SQL_ROWSET_SIZE setzen. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Teilbereiche wurden abgeschnitten|Die für eine Spalte zurückgegebenen Daten wurden abgeschnitten. Für numerische Datentypen wurde die Nachkommastellen der Zahl abgeschnitten. Für die Zeit, Zeitstempel und Interval-Datentypen, die eine Komponente enthält wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|Ein Datenwert konnte nicht konvertiert werden, in den C-Datentyp, der anhand des *TargetType* in **SQLBindCol**.|  
|07009|Ungültiger Deskriptorindex|Spalte 0 gebunden wurde **SQLBindCol**, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF festgelegt wurde.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|22002|Anzeigevariable erforderlich, aber nicht angegeben|NULL-Daten wurde abgerufen in einer Spalte, deren *StrLen_or_IndPtr* festlegen, indem **SQLBindCol** wurde ein null-Zeiger.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22003|Numerischer Wert außerhalb des gültigen Bereichs|Den numerischen Wert (als numerisch oder Zeichenfolge) zurückgegeben, für eine oder mehrere Spalten würde den gesamten (im Gegensatz zu Bruch) Teil der Zahl abgeschnitten wird verursacht.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> Weitere Informationen finden Sie unter [Richtlinien für das Intervall und numerische Datentypen](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md) in Anhang D: Datentypen.|  
|22007|Ungültiges Datetime-format|Im Resultset eine Spalte mit dem Zeichen um ein Datum, Uhrzeit oder Zeitstempel C-Struktur gebunden wurde, und ein Wert in der Spalte wurde, bzw. ein ungültiges Datum, Uhrzeit oder Zeitstempel.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22012|Division durch 0 (null)|Ein Wert aus einem arithmetischen Ausdruck wurde von 0 (null) zurückgegeben Division geführt hat.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22015|Überlauf bei Intervallfeld|Intervalltyp C aus einer genauen numerischen oder Intervall SQL-Typ zuweisen, verursacht einen Verlust signifikanter Ziffern im Feld führende.<br /><br /> Beim Abrufen von Daten in ein C-Intervalltyp, gab es keine Darstellung des Werts von der SQL-Typ in den Intervalltyp C.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|Der C-Typ war eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp. der SQL-Typ der Spalte konnte einen Zeichendatentyp; und kein Wert in der Spalte wurde ein gültiger Literal des gebundenen Typen aus C#.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|24000|Ungültiger Cursorstatus|Die *StatementHandle* wurde in einem ausgeführten Zustand befindet, aber kein Resultset zugeordnet wurde die *StatementHandle*.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLError** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*, und klicken Sie dann die Funktion aufgerufen wurde erneut auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLExtendedFetch** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) der angegebenen *StatementHandle* war nicht in einem ausgeführten Zustand befindet. Die Funktion wurde aufgerufen, ohne den ersten Aufruf **SQLExecDirect**, **SQLExecute**, oder eine Katalogfunktion auf.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) **SQLExtendedFetch** wurde aufgerufen, die *StatementHandle* nach **SQLFetch** oder **SQLFetchScroll** aufgerufen wurde und bevor  **SQLFreeStmt** mit der Option SQL_CLOSE aufgerufen wurde.<br /><br /> (DM) **SQLBulkOperations** wurde aufgerufen, eine Anweisung vor dem **SQLFetch**, **SQLFetchScroll**, oder **SQLExtendedFetch** aufgerufen wurde, und Klicken Sie dann **SQLExtendedFetch** war aufgerufen, bevor **SQLFreeStmt** mit der Option SQL_CLOSE aufgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY106|Fetchtyp außerhalb des gültigen Bereichs|(DM) der Wert für das Argument angegebene *FetchOrientation* war ungültig. (Siehe "Kommentare".)<br /><br /> Das Argument *FetchOrientation* SQL_FETCH_BOOKMARK wurde und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF festgelegt wurde.<br /><br /> Der Wert der Option-Anweisung SQL_CURSOR_TYPE war SQL_CURSOR_FORWARD_ONLY und der Wert des Arguments *FetchOrientation* war nicht SQL_FETCH_NEXT.<br /><br /> Das Argument *FetchOrientation* SQL_FETCH_RESUME wurde.|  
|HY107|Zeilenwert außerhalb des gültigen Bereichs|Mit der Option SQL_CURSOR_TYPE-Anweisung angegebene Wert war SQL_CURSOR_KEYSET_DRIVEN, jedoch mit dem Attribut der SQL_KEYSET_SIZE-Anweisung angegebene Wert größer als 0 und kleiner als der Wert, der durch das Anweisungsattribut SQL_ROWSET_SIZE setzen angegeben .|  
|HY111|Ungültiger Wert für Lesezeichen|Das Argument *FetchOrientation* SQL_FETCH_BOOKMARK wurde angegeben, und die Textmarke in der *FetchOffset* Argument war ungültig.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Treiber oder der Datenquelle unterstützt nicht den angegebenen Fetchtyp.<br /><br /> Die Treiber oder die Datenquelle unterstützt nicht die Konvertierung angegeben wird, durch die Kombination der *TargetType* in **SQLBindCol** und dem SQL-Datentyp der entsprechenden Spalte. Dieser Fehler tritt nur bei der SQL-Datentyp der Spalte mit einem treiberspezifischen SQL-Datentyp zugeordnet war.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtOption**, SQL_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Das Verhalten der **SQLExtendedFetch** ist identisch mit der **SQLFetchScroll**, mit den folgenden Ausnahmen:  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** unterschiedliche Methoden verwenden, um die Anzahl der abgerufenen Zeilen zurückzugeben. **SQLExtendedFetch** gibt die Anzahl der Zeilen, die abgerufen werden  *\*RowCountPtr*; **SQLFetchScroll** gibt die Anzahl der Zeilen, die direkt in den Puffer, der auf SQL_ATTR_ROWS_FETCHED_PTR abgerufen. Weitere Informationen finden Sie unter den *RowCountPtr* Argument.  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** den Status der einzelnen Zeilen in verschiedenen Arrays zurückgeben. Weitere Informationen finden Sie unter den *RowStatusArray* Argument.  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** unterschiedliche Methoden zum Abrufen von Lesezeichen verwenden, wenn *FetchOrientation* SQL_FETCH_BOOKMARK wird. **SQLExtendedFetch** variabler Länge, die Lesezeichen bzw. Abrufen von Rowsets mit einem Offset ungleich 0 in einem Lesezeichen wird nicht unterstützt. Weitere Informationen finden Sie unter den *FetchOffset* Argument.  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** anderes Rowset Größen zu verwenden. **SQLExtendedFetch** verwendet den Wert des Attributs Anweisung SQL_ROWSET_SIZE setzen, und **SQLFetchScroll** verwendet den Wert des Attributs SQL_ATTR_ROW_ARRAY_SIZE-Anweisung.  
  
-   **SQLExtendedFetch** verfügt über etwas andere Semantik, als für die Fehlerbehandlung **SQLFetchScroll**. Weitere Informationen finden Sie unter "Fehlerbehandlung" im Abschnitt "Kommentare" [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
-   **SQLExtendedFetch** Bindung-Offsets (das SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattribut) wird nicht unterstützt.  
  
-   Aufrufe von **SQLExtendedFetch** können nicht kombiniert werden, mit Aufrufen von **SQLFetch** oder **SQLFetchScroll**, und wenn **SQLBulkOperations** aufgerufen wird vor jede Fetch-Funktion aufgerufen wird, **SQLExtendedFetch** kann nicht aufgerufen werden, bis der Cursor geschlossen und erneut geöffnet wird. D. h. **SQLExtendedFetch** können nur auf Anweisung Zustand S7 aufgerufen werden. Weitere Informationen finden Sie unter [Statusübergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Übergang Statustabellen.  
  
 Wenn eine Anwendung ruft **SQLFetchScroll** bei der Verwendung von einer ODBC 2. *.x* -Treiber verwenden, der Treiber-Manager zugeordnet wird dieser Aufruf **SQLExtendedFetch**. Weitere Informationen finden Sie unter "SQLFetchScroll und ODBC 2 *.x* Treiber" im [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 In ODBC 2. *.x*, **SQLExtendedFetch** war aufgerufen, um mehrere Zeilen abzurufen und **SQLFetch** war aufgerufen, um eine einzelne Zeile abrufen. In ODBC 3. *.x*, auf der anderen Seite **SQLFetch** aufgerufen werden, um mehrere Zeilen abzurufen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Bulk Insert, Update oder Delete-Vorgänge|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Die Anzahl der Resultsets zurückgeben von Resultsetspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset, oder aktualisieren oder Löschen von Daten im Resultset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Wenn eine Anweisungsattribut|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
