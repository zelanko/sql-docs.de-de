---
title: SQLExtendedFetch-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285980"
---
# <a name="sqlextendedfetch-function"></a>SQLExtendedFetch-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Standards-Konformität: Veraltet  
  
 **Zusammenfassung**  
 **SQLExtendedFetch** ruft das angegebene Rowset von Daten aus dem Resultset ab und gibt Daten für alle gebundenen Spalten zurück. Rowsets können an einer absoluten oder relativen Position oder nach Lesezeichen angegeben werden.  
  
> [!NOTE]
>  In ODBC 3 *.x*wurde **SQLExtendedFetch** durch **SQLFetchScroll**ersetzt. ODBC 3 *.x-Anwendungen* sollten **SQLExtendedFetch**nicht aufrufen; Stattdessen sollten sie **SQLFetchScroll**aufrufen. Der Treiber-Manager ordnet **SQLFetchScroll** **SQLExtendedFetch** zu, wenn sie mit einem ODBC 2 *.x-Treiber* arbeiten. ODBC 3 *.x-Treiber* sollten **SQLExtendedFetch** unterstützen, wenn sie mit ODBC 2 *.x-Anwendungen* arbeiten möchten, die es aufrufen. Weitere Informationen finden Sie unter "Kommentare" und [Blockcursor, Scrollbare Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.  
  
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
 [Eingabe] Art des Abrufs. Dies ist das gleiche wie *FetchOrientation* in **SQLFetchScroll**.  
  
 *FetchOffset*  
 [Eingabe] Nummer der abzurufenden Zeile. Dies ist mit einer Ausnahme mit *FetchOffset* in **SQLFetchScroll**identisch. Wenn *FetchOrientation* SQL_FETCH_BOOKMARK ist, ist *FetchOffset* eine Textmarke mit fester Länge und kein Offset von einer Textmarke. Mit anderen Worten, **SQLExtendedFetch** ruft die Textmarke aus diesem Argument ab, nicht das attribut SQL_ATTR_FETCH_BOOKMARK_PTR.. Es unterstützt keine Lesezeichen variabler Länge und unterstützt nicht das Abrufen eines Rowsets mit einem Offset (außer 0) aus einer Textmarke.  
  
 *RowCountPtr*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die Anzahl der tatsächlich abgerufenen Zeilen zurückgegeben werden soll. Dieser Puffer wird auf die gleiche Weise wie der Puffer verwendet, der vom Attribut SQL_ATTR_ROWS_FETCHED_PTR-Anweisung angegeben wird. Dieser Puffer wird nur von **SQLExtendedFetch**verwendet. Es wird nicht von **SQLFetch** oder **SQLFetchScroll**verwendet.  
  
 *RowStatusArray*  
 [Ausgabe] Zeigen Sie auf ein Array, in dem der Status jeder Zeile zurückgegeben werden soll. Dieses Array wird auf die gleiche Weise wie das Array verwendet, das vom Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung angegeben wird.  
  
 Die Adresse dieses Arrays wird jedoch nicht im Feld SQL_DESC_STATUS_ARRAY_PTR im IRD gespeichert. Darüber hinaus wird dieses Array nur von **SQLExtendedFetch** und von **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD oder **SQLSetPos** verwendet, wenn es nach **SQLExtendedFetch**aufgerufen wird. Es wird nicht von **SQLFetch** oder **SQLFetchScroll**verwendet, und es wird nicht von **SQLBulkOperations** oder **SQLSetPos** verwendet, wenn sie nach **SQLFetch** oder **SQLFetchScroll**aufgerufen werden. Es wird auch nicht verwendet, wenn **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD aufgerufen wird, bevor eine Abruffunktion aufgerufen wird. Mit anderen Worten, es wird nur im Anweisungszustand S7 verwendet. Es wird nicht in den Anweisungszuständen S5 oder S6 verwendet. Weitere Informationen finden Sie unter [Anweisungsübergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Zustandsübergangstabellen.  
  
 Anwendungen sollten einen gültigen Zeiger im *RowStatusArray-Argument* bereitstellen. Wenn dies nicht der Fall ist, sind das Verhalten von **SQLExtendedFetch** und das Verhalten von Aufrufen von **SQLBulkOperations** oder **SQLSetPos,** nachdem ein Cursor von **SQLExtendedFetch** positioniert wurde, nicht definiert.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLExtendedFetch** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLError**aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLExtendedFetch** zurückgegeben werden, und es werden die SQLSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben. Wenn ein Fehler in einer einzelnen Spalte auftritt, kann **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_COLUMN_NUMBER aufgerufen werden, um die Spalte zu bestimmen, in der der Fehler aufgetreten ist. und **SQLGetDiagField** kann mit einem *DiagIdentifier* von SQL_DIAG_ROW_NUMBER aufgerufen werden, um die Zeile zu bestimmen, die diese Spalte enthält.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für eine Spalte zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht null sind. Wenn es sich um einen Zeichenfolgenwert handelte, wurde er rechts abgeschnitten. Wenn es sich um einen numerischen Wert handelt, wurde der Bruchteil der Zahl abgeschnitten.  (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S01|Fehler in Zeile|Beim Abrufen einer oder einer oder mehreren Zeilen ist ein Fehler aufgetreten. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S06|Versuch, abzurufen, bevor das Resultset das erste Rowset zurückgibt|Das angeforderte Rowset überlappte den Anfang des Resultsets, wenn die aktuelle Position über der ersten Zeile lag, und entweder war *FetchOrientation* SQL_PRIOR oder *FetchOrientation* wurde mit einem negativen *FetchOffset* SQL_RELATIVE, dessen absoluter Wert kleiner oder gleich dem aktuellen SQL_ROWSET_SIZE war. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Bruchschnitt|Die für eine Spalte zurückgegebenen Daten wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteil der Zahl abgeschnitten. Für Zeit-, Zeitstempel- und Intervalldatentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|Ein Datenwert konnte nicht in den von *TargetType* in **SQLBindCol**angegebenen C-Datentyp konvertiert werden.|  
|07009|Ungültiger Deskriptorindex|Spalte 0 wurde mit **SQLBindCol**gebunden, und das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung wurde auf SQL_UB_OFF festgelegt.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|22002|Indikatorvariable erforderlich, aber nicht mitgeliefert|NULL-Daten wurden in eine Spalte abgerufen, deren *StrLen_or_IndPtr* von **SQLBindCol** festgelegt wurde, ein Nullzeiger.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22003|Numerischer Wert aofc|Das Zurückgeben des numerischen Werts (als numerische oder Zeichenfolge) für eine oder mehrere Spalten hätte dazu geführt, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> Weitere Informationen finden Sie unter [Richtlinien für Intervall- und numerische Datentypen](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md) in Anhang D: Datentypen.|  
|22007|Ungültiges Datumszeitformat|Eine Zeichenspalte im Resultset war an eine Datums-, Uhrzeit- oder Zeitstempel-C-Struktur gebunden, und ein Wert in der Spalte war jeweils ein ungültiges Datum, eine ungültige Uhrzeit oder ein Zeitstempel.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22012|Division durch Null|Es wurde ein Wert aus einem arithmetischen Ausdruck zurückgegeben, der zu einer Division durch Null führte.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22015|Intervallfeldüberlauf|Das Zuweisen eines SQL-Typs aus einem exakten numerischen oder Intervall-SQL-Typ zu einem Intervall-C-Typ verursachte einen Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Beim Abrufen von Daten in einen Intervall-C-Typ gab es keine Darstellung des Wertes des SQL-Typs im Intervall-C-Typ.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|Der C-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. Der SQL-Typ der Spalte war ein Zeichendatentyp; und der Wert in der Spalte war kein gültiges Literal des gebundenen C-Typs.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|24.000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLError** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für den *StatementHandle*aufgerufen, und dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLExtendedFetch-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Der angegebene *StatementHandle* befand sich nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute**oder eine Katalogfunktion aufzurufen.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) **SQLExtendedFetch** wurde für das *StatementHandle* aufgerufen, nachdem **SQLFetch** oder **SQLFetchScroll** aufgerufen wurden und bevor **SQLFreeStmt** mit der Option SQL_CLOSE aufgerufen wurde.<br /><br /> (DM) **SQLBulkOperations** wurde für eine Anweisung aufgerufen, bevor **SQLFetch**, **SQLFetchScroll**oder **SQLExtendedFetch** aufgerufen wurde, und dann wurde **SQLExtendedFetch** aufgerufen, bevor **SQLFreeStmt** mit der Option SQL_CLOSE aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY106|Abruftyp anicht in Reichweite|(DM) Der für das Argument *FetchOrientation* angegebene Wert war ungültig. (Siehe "Kommentare.")<br /><br /> Das Argument *FetchOrientation* wurde SQL_FETCH_BOOKMARK, und das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung wurde auf SQL_UB_OFF festgelegt.<br /><br /> Der Wert der SQL_CURSOR_TYPE-Anweisungsoption wurde SQL_CURSOR_FORWARD_ONLY, und der Wert des Arguments *FetchOrientation* wurde nicht SQL_FETCH_NEXT.<br /><br /> Das Argument *FetchOrientation* wurde SQL_FETCH_RESUME.|  
|HY107|Zeilenwert a-range|Der mit der Option SQL_CURSOR_TYPE-Anweisung angegebene Wert wurde SQL_CURSOR_KEYSET_DRIVEN, aber der mit dem Attribut SQL_KEYSET_SIZE-Anweisung angegebene Wert war größer als 0 und kleiner als der mit dem Attribut SQL_ROWSET_SIZE-Anweisung angegebene Wert.|  
|HY111|Ungültiger Lesezeichenwert|Das Argument *FetchOrientation* wurde SQL_FETCH_BOOKMARK, und das im *FetchOffset-Argument* angegebene Lesezeichen war ungültig.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Treiber oder Datenquelle unterstützt den angegebenen Abruftyp nicht.<br /><br /> Der Treiber oder die Datenquelle unterstützt die Konvertierung, die durch die Kombination des *TargetType* in **SQLBindCol** und des SQL-Datentyps der entsprechenden Spalte angegeben wird, nicht. Dieser Fehler tritt nur zu, wenn der SQL-Datentyp der Spalte einem treiberspezifischen SQL-Datentyp zugeordnet wurde.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtOption**festgelegt, SQL_QUERY_TIMEOUT.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Das Verhalten von **SQLExtendedFetch** ist mit dem von **SQLFetchScroll**identisch, mit den folgenden Ausnahmen:  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** verwenden unterschiedliche Methoden, um die Anzahl der abgerufenen Zeilen zurückzugeben. **SQLExtendedFetch** gibt die Anzahl der in * \*RowCountPtr*abgerufenen Zeilen zurück. **SQLFetchScroll** gibt die Anzahl der Zeilen zurück, die direkt an den Puffer abgerufen werden, auf den SQL_ATTR_ROWS_FETCHED_PTR. Weitere Informationen finden Sie im *RowCountPtr-Argument.*  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** geben den Status jeder Zeile in verschiedenen Arrays zurück. Weitere Informationen finden Sie im *RowStatusArray-Argument.*  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** verwenden verschiedene Methoden, um das Lesezeichen abzurufen, wenn *FetchOrientation* SQL_FETCH_BOOKMARK ist. **SQLExtendedFetch** unterstützt keine Lesezeichen variabler Länge oder das Abrufen von Rowsets mit einem anderen Offset als 0 aus einer Textmarke. Weitere Informationen finden Sie im *Argument FetchOffset.*  
  
-   **SQLExtendedFetch** und **SQLFetchScroll** verwenden unterschiedliche Rowsetgrößen. **SQLExtendedFetch** verwendet den Wert des SQL_ROWSET_SIZE-Anweisungsattributs, und **SQLFetchScroll** verwendet den Wert des Attributs SQL_ATTR_ROW_ARRAY_SIZE.  
  
-   **SQLExtendedFetch** weist eine etwas andere Fehlerbehandlungssemantik als **SQLFetchScroll**auf. Weitere Informationen finden Sie unter "Fehlerbehandlung" im Abschnitt "Kommentare" von [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
-   **SQLExtendedFetch** unterstützt keine Bindungsoffsets (das Attribut SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisung).  
  
-   Aufrufe von **SQLExtendedFetch** können nicht mit Aufrufen von **SQLFetch** oder **SQLFetchScroll**gemischt werden, und wenn **SQLBulkOperations** aufgerufen wird, bevor eine Abruffunktion aufgerufen wird, kann **SQLExtendedFetch** erst aufgerufen werden, wenn der Cursor geschlossen und erneut geöffnet wird. Das heißt, **SQLExtendedFetch** kann nur im Anweisungszustand S7 aufgerufen werden. Weitere Informationen finden Sie unter [Anweisungsübergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Zustandsübergangstabellen.  
  
 Wenn eine Anwendung **SQLFetchScroll** aufruft, während sie einen ODBC 2 *.x-Treiber* verwendet, ordnet der Treiber-Manager diesen Aufruf **SQLExtendedFetch**zu. Weitere Informationen finden Sie unter "SQLFetchScroll und ODBC 2 *.x-Treiber"* in [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 In ODBC 2 *.x*wurde **SQLExtendedFetch** aufgerufen, um mehrere Zeilen abzurufen, und **SQLFetch** wurde aufgerufen, um eine einzelne Zeile abzurufen. In ODBC 3 *.x*kann **SQLFetch** hingegen aufgerufen werden, um mehrere Zeilen abzurufen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Masseneinfüge-, Aktualisierungs- oder Löschvorgängen|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einer Ergebnismenge|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Zurückgeben der Anzahl der Ergebnissatzspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset oder Aktualisieren oder Löschen von Daten im Resultset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Festlegen eines Anweisungsattributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
