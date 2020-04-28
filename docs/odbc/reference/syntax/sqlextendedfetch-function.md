---
title: Sqlextendecodfetch-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLExtendedFetch
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLExtendedFetch
helpviewer_keywords:
- SQLExtendedFetch function [ODBC]
ms.assetid: 940b5cf7-581c-4ede-8533-c67d5e9ef488
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dc832e5a20b1d3c0a1ad63b3e2a070563de2b46d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285980"
---
# <a name="sqlextendedfetch-function"></a>SQLExtendedFetch-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: deprecated  
  
 **Zusammenfassung**  
 **Sqlextendebug** Ruft das angegebene Rowset von Daten aus dem Resultset ab und gibt Daten für alle gebundenen Spalten zurück. Rowsets können an einer absoluten oder relativen Position oder durch ein Lesezeichen angegeben werden.  
  
> [!NOTE]
>  In ODBC 3 *. x*wurde **sqlextendecodfetch** durch **SQLFetchScroll**ersetzt. ODBC 3 *. x* -Anwendungen sollten **sqlextendebug**; nicht aufzurufen. Stattdessen sollte **SQLFetchScroll**aufgerufen werden. Der Treiber-Manager ordnet **SQLFetchScroll** zu **sqlextendecodfetch** zu, wenn er mit einem ODBC 2 *. x* -Treiber arbeitet. ODBC 3 *. x* -Treiber sollten **SQLExtendedFetch** unterstützen, wenn Sie mit ODBC 2 *. x* -Anwendungen arbeiten möchten, die Sie anrufen. Weitere Informationen finden Sie unter "Kommentare" und [Block Cursor, scrollfähige Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiber Richtlinien für Abwärtskompatibilität.  
  
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
 Der Anweisungs Handle.  
  
 *FetchOrientation*  
 Der Der Typ des Abruf Vorgangs. Dies ist das gleiche wie *FetchOrientation* in **SQLFetchScroll**.  
  
 *FetchOffset*  
 Der Die Nummer der abzurufenden Zeile. Dies ist mit dem *FetchOffset* in **SQLFetchScroll**identisch, mit einer Ausnahme. Wenn *FetchOrientation* SQL_FETCH_BOOKMARK ist, ist *FetchOffset* ein Lesezeichen mit fester Länge und kein Offset von einem Lesezeichen. Mit anderen Worten: **sqlextendebug** Ruft das Lesezeichen aus diesem Argument, nicht das SQL_ATTR_FETCH_BOOKMARK_PTR Anweisungs Attribut ab. Er unterstützt keine Lesezeichen mit variabler Länge und unterstützt nicht das Abrufen eines Rowsets in einem Offset (mit Ausnahme von 0) aus einem Lesezeichen.  
  
 *RowCountPtr*  
 Ausgeben Zeiger auf einen Puffer, in den die Anzahl der tatsächlich abgerufenen Zeilen zurückgegeben werden soll. Dieser Puffer wird auf die gleiche Weise verwendet wie der Puffer, der durch das SQL_ATTR_ROWS_FETCHED_PTR Statement-Attribut angegeben wird. Dieser Puffer wird nur von **sqlextendecodfetch**verwendet. Sie wird von **SQLFetch** oder **SQLFetchScroll**nicht verwendet.  
  
 *Rowstatus Array*  
 Ausgeben Ein Zeiger auf ein Array, in dem der Status jeder Zeile zurückgegeben werden soll. Dieses Array wird auf die gleiche Weise wie das Array verwendet, das vom SQL_ATTR_ROW_STATUS_PTR Statement-Attribut angegeben wird.  
  
 Die Adresse dieses Arrays wird jedoch nicht im SQL_DESC_STATUS_ARRAY_PTR Feld im IRD gespeichert. Außerdem wird dieses Array nur von **SQLExtendedFetch** und **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD oder **SQLSetPos** verwendet, wenn es nach **SQLExtendedFetch**aufgerufen wird. Sie wird nicht von **SQLFetch** oder **SQLFetchScroll**verwendet und wird nicht von **SQLBulkOperations** oder **SQLSetPos** verwendet, wenn Sie nach **SQLFetch** oder **SQLFetchScroll**aufgerufen werden. Sie wird auch nicht verwendet, wenn **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD aufgerufen wird, bevor eine Fetch-Funktion aufgerufen wird. Das heißt, Sie wird nur im Anweisungs Zustand "S7" verwendet. Sie wird in den Anweisungs Zuständen S5 oder S6 nicht verwendet. Weitere Informationen finden Sie unter [Anweisungs Übergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Status Übergangs Tabellen.  
  
 Anwendungen sollten einen gültigen Zeiger im *rowstatus Array* -Argument bereitstellen. Andernfalls sind das Verhalten von **SQLExtendedFetch** und das Verhalten von Aufrufen von **SQLBulkOperations** oder **SQLSetPos** , nachdem ein Cursor von **SQLExtendedFetch** positioniert wurde, nicht definiert.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLExtendedFetch** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLError**abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die häufig von **SQLExtendedFetch** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist. Wenn ein Fehler in einer einzelnen Spalte auftritt, kann **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_COLUMN_NUMBER aufgerufen werden, um die Spalte zu bestimmen, in der der Fehler aufgetreten ist. und **SQLGetDiagField** können mit einem *DiagIdentifier* von SQL_DIAG_ROW_NUMBER aufgerufen werden, um die Zeile zu ermitteln, die diese Spalte enthält.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Zeichen folgen-oder Binärdaten, die für eine Spalte zurückgegeben wurden, ergaben das Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind. Wenn es sich um einen Zeichen folgen Wert handelt, wurde er rechts abgeschnitten. Wenn es sich um einen numerischen Wert handelt, wurde der Bruchteile der Zahl abgeschnitten.  (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s01|Fehler in Zeile|Fehler beim Abrufen einer oder mehrerer Zeilen. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s06|Es wurde versucht, abzurufen, bevor das Resultset das erste Rowset zurückgegeben hat|Das angeforderte Rowset hat den Anfang des Resultsets überschritten, als die aktuelle Position außerhalb der ersten Zeile lag, und entweder wurde entweder *FetchOrientation* SQL_PRIOR, oder *FetchOrientation* wurde mit einem negativen *FetchOffset* SQL_RELATIVE, dessen absoluter Wert kleiner oder gleich dem aktuellen SQL_ROWSET_SIZE war. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Abschneiden von Sekundenbruchteilen|Die für eine Spalte zurückgegebenen Daten wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteile der Zahl abgeschnitten. Bei Zeit-, Zeitstempel-und Intervall Datentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|Ein Datenwert konnte nicht in den C-Datentyp konvertiert werden, der von *TargetType* in **SQLBindCol**angegeben wurde.|  
|07009|Ungültiger deskriptorindex.|Die Spalte 0 wurde mit **SQLBindCol**gebunden, und das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_OFF festgelegt.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|22002|Die Indikator Variable ist erforderlich, aber nicht angegeben.|NULL-Daten wurden in eine Spalte abgerufen, deren *StrLen_or_IndPtr* von **SQLBindCol** festgelegt war, ein NULL-Zeiger war.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22003|Numerischer Wert außerhalb des zulässigen Bereichs|Das Zurückgeben des numerischen Werts (als numerisch oder Zeichenfolge) für eine oder mehrere Spalten hätte dazu geführt, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wird.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> Weitere Informationen finden Sie unter [Richtlinien für Intervall-und numerische Datentypen](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md) in Anhang D: Datentypen.|  
|22007|Ungültiges datetime-Format.|Eine Zeichenspalte im Resultset wurde an eine Datums-, Uhrzeit-oder Zeitstempel-C-Struktur gebunden, und ein Wert in der Spalte war, bzw. ein ungültiges Datum, eine Uhrzeit oder ein ungültiger Zeitstempel.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22012|Division durch Null|Es wurde ein Wert aus einem arithmetischen Ausdruck zurückgegeben, der zu einer Division durch 0 geführt hat.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22015|Überlauf des Intervall Felds|Das Zuweisen eines exakten numerischen oder Interval-SQL-Typs zu einem Interval-C-Typ verursachte den Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Beim Abrufen von Daten in einen Interval-c-Typ gab es keine Darstellung des Werts des SQL-Typs im Interval-c-Typ.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|Der C-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der SQL-Typ der Spalte war ein Zeichen Datentyp. und der Wert in der Spalte war kein gültiges Literale des gebundenen C-Typs.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|24.000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLError** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen, und anschließend wurde die Funktion für " *StatementHandle*" erneut aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **sqlextendebug** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) das angegebene *StatementHandle* war nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute**oder eine Katalog Funktion aufzurufen.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) **SQLExtendedFetch** wurde für das *StatementHandle* aufgerufen, nachdem **SQLFetch** oder **SQLFetchScroll** aufgerufen wurde und bevor **SQLFreeStmt** mit der SQL_CLOSE-Option aufgerufen wurde.<br /><br /> (DM) **SQLBulkOperations** wurde vor dem Aufrufen von **SQLFetch**, **SQLFetchScroll**oder **SQLExtendedFetch** für eine-Anweisung aufgerufen. Anschließend wurde **SQLExtendedFetch** aufgerufen, bevor **SQLFreeStmt** mit der SQL_CLOSE-Option aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY106|FETCH-Typ außerhalb des gültigen Bereichs|(DM) der für das Argument *FetchOrientation* angegebene Wert war ungültig. (Siehe "Kommentare")<br /><br /> Das Argument " *FetchOrientation* " wurde SQL_FETCH_BOOKMARK, und das Attribut der SQL_ATTR_USE_BOOKMARKS Anweisung wurde auf "SQL_UB_OFF" festgelegt.<br /><br /> Der Wert der Option SQL_CURSOR_TYPE Anweisung war SQL_CURSOR_FORWARD_ONLY, und der Wert von Argument *FetchOrientation* war nicht SQL_FETCH_NEXT.<br /><br /> Das Argument " *FetchOrientation* " wurde SQL_FETCH_RESUME.|  
|HY107|Zeilen Wert außerhalb des zulässigen Bereichs|Der mit der Option SQL_CURSOR_TYPE Anweisung angegebene Wert wurde SQL_CURSOR_KEYSET_DRIVEN, aber der mit dem Attribut der SQL_KEYSET_SIZE-Anweisung angegebene Wert war größer als 0 und kleiner als der mit dem SQL_ROWSET_SIZE Statement-Attribut angegebene Wert.|  
|HY111|Ungültiger Lesezeichen Wert|Das Argument *FetchOrientation* wurde SQL_FETCH_BOOKMARK, und das im *FetchOffset* -Argument angegebene Lesezeichen war nicht gültig.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Der Treiber oder die Datenquelle unterstützt den angegebenen Abruf Datentyp nicht.<br /><br /> Der Treiber oder die Datenquelle unterstützt nicht die Konvertierung, die durch die Kombination von *TargetType* in **SQLBindCol** und dem SQL-Datentyp der entsprechenden Spalte angegeben wird. Dieser Fehler tritt nur dann auf, wenn der SQL-Datentyp der Spalte einem treiberspezifischen SQL-Datentyp zugeordnet wurde.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtOption**, SQL_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Das Verhalten von **SQLExtendedFetch** ist mit dem von **SQLFetchScroll**identisch, mit den folgenden Ausnahmen:  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** verwenden verschiedene Methoden, um die Anzahl der abgerufenen Zeilen zurückzugeben. **Sqlextendebug** gibt die Anzahl von Zeilen zurück, die in * \*ROWCOUNT*abgerufen wurden. **SQLFetchScroll** gibt die Anzahl der Zeilen zurück, die direkt in den Puffer abgerufen werden, auf den SQL_ATTR_ROWS_FETCHED_PTR zeigt. Weitere Informationen finden Sie im *ROWCOUNT* -Argument.  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** geben den Status der einzelnen Zeilen in unterschiedlichen Arrays zurück. Weitere Informationen finden Sie unter dem *rowstatus Array* -Argument.  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** verwenden verschiedene Methoden zum Abrufen des Lesezeichens, wenn *FetchOrientation* SQL_FETCH_BOOKMARK ist. **SQLExtendedFetch** unterstützt keine Lesezeichen mit variabler Länge oder das Abrufen von Rowsets mit einem anderen Offset als 0 (null) aus Lesezeichen. Weitere Informationen finden Sie unter dem *FetchOffset* -Argument.  
  
-   **Sqlextendebug** und **SQLFetchScroll** verwenden unterschiedliche rowsetgrößen. **Sqlextendebug** verwendet den Wert des Attributs der SQL_ROWSET_SIZE-Anweisung, und **SQLFetchScroll** verwendet den Wert des Attributs der SQL_ATTR_ROW_ARRAY_SIZE Anweisung.  
  
-   **Sqlextendebug** hat eine etwas andere Fehler Behandlungs Semantik als **SQLFetchScroll**. Weitere Informationen finden Sie unter "Fehlerbehandlung" im Abschnitt "Kommentare" von [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
-   **SQLExtendedFetch** unterstützt keine Bindungs Offsets (das SQL_ATTR_ROW_BIND_OFFSET_PTR Anweisungs Attribut).  
  
-   Aufrufe von **SQLExtendedFetch** können nicht mit Aufrufen von **SQLFetch** oder **SQLFetchScroll**gemischt werden, und wenn **SQLBulkOperations** aufgerufen wird, bevor eine Fetch-Funktion aufgerufen wird, kann **SQLExtendedFetch** erst aufgerufen werden, wenn der Cursor geschlossen und wieder geöffnet wurde. Das heißt, **sqlextendebug** kann nur im Anweisungs Zustand "S7" aufgerufen werden. Weitere Informationen finden Sie unter [Anweisungs Übergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Status Übergangs Tabellen.  
  
 Wenn eine Anwendung **SQLFetchScroll** bei Verwendung eines ODBC 2 *. x* -Treibers aufruft, ordnet der Treiber-Manager diesen Aufruf **SQLExtendedFetch**zu. Weitere Informationen finden Sie unter "SQLFetchScroll und ODBC 2 *. x* -Treiber" in [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 In ODBC 2 *. x*wurde **SQLExtendedFetch** aufgerufen, um mehrere Zeilen abzurufen, und **SQLFetch** wurde aufgerufen, um eine einzelne Zeile abzurufen. In ODBC 3 *. x*kann hingegen **SQLFetch** aufgerufen werden, um mehrere Zeilen abzurufen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von BULK INSERT-, Update-oder DELETE-Vorgängen|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Zurückgeben der Anzahl von Resultsetspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset oder aktualisieren oder Löschen von Daten im Resultset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Festlegen eines Anweisungs Attributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
