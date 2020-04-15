---
title: SQLFetch-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFetch
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFetch
helpviewer_keywords:
- SQLFetch function [ODBC]
ms.assetid: 6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc7e2da6996d8d6b2ee66befdc90794efec5617b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285970"
---
# <a name="sqlfetch-function"></a>SQLFetch-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLFetch** ruft das nächste Rowset von Daten aus dem Resultset ab und gibt Daten für alle gebundenen Spalten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFetch(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFetch** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem [sqlGetDiagRec Function](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLFetch** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben. Wenn ein Fehler in einer einzelnen Spalte auftritt, kann [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) mit einem *DiagIdentifier* von SQL_DIAG_COLUMN_NUMBER aufgerufen werden, um die Spalte zu bestimmen, in der der Fehler aufgetreten ist. und **SQLGetDiagField** kann mit einem *DiagIdentifier* von SQL_DIAG_ROW_NUMBER aufgerufen werden, um die Zeile zu bestimmen, die diese Spalte enthält.  
  
 Für alle SQLSTATEs, die SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgeben können (außer 01xxx SQLSTATEs), wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn ein Fehler bei einer oder mehreren Zeilen eines mehrreihigen Vorgangs auftritt, und SQL_ERROR wird zurückgegeben, wenn ein Fehler bei einem einzeiligen Vorgang auftritt.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für eine Spalte zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht null sind. Wenn es sich um einen Zeichenfolgenwert handelte, wurde er rechts abgeschnitten.|  
|01S01|Fehler in Zeile|Beim Abrufen einer oder einer oder mehreren Zeilen ist ein Fehler aufgetreten.<br /><br /> (Wenn diese SQLSTATE zurückgegeben wird, wenn eine ODBC 3 *.x-Anwendung* mit einem ODBC 2 *.x-Treiber* arbeitet, kann sie ignoriert werden.)|  
|01S07|Bruchschnitt|Die für eine Spalte zurückgegebenen Daten wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteil der Zahl abgeschnitten. Für Zeit-, Zeitstempel- und Intervalldatentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|Der Datenwert einer Spalte im Resultset konnte nicht in den von *TargetType* in **SQLBindCol**angegebenen Datentyp konvertiert werden.<br /><br /> Spalte 0 wurde mit einem Datentyp von SQL_C_BOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt.<br /><br /> Spalte 0 wurde mit einem Datentyp von SQL_C_VARBOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut wurde nicht auf SQL_UB_VARIABLE festgelegt.|  
|07009|Ungültiger Deskriptorindex|Der Treiber war ein ODBC 2 *.x-Treiber,* der **SQLExtendedFetch**nicht unterstützt, und eine Spaltennummer, die in der Bindung für eine Spalte angegeben wurde, war 0.<br /><br /> Spalte 0 wurde gebunden, und das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_OFF festgelegt.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|22001|String-Daten, rechts abgeschnitten|Eine für eine Spalte zurückgegebene Textmarke variabler Länge wurde abgeschnitten.|  
|22002|Indikatorvariable erforderlich, aber nicht mitgeliefert|NULL-Daten wurden in eine Spalte abgerufen, deren *StrLen_or_IndPtr* von **SQLBindCol** festgelegt wurde (oder SQL_DESC_INDICATOR_PTR von **SQLSetDescField** oder **SQLSetDescRec**festgelegt wurde).|  
|22003|Numerischer Wert aofc|Das Zurückgeben des numerischen Werts als numerische oder Zeichenfolge für eine oder mehrere gebundene Spalten hätte dazu geführt, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde.<br /><br /> Weitere Informationen finden Sie unter [Konvertieren von Daten aus SQL-In-C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in Anhang D: Datentypen.|  
|22007|Ungültiges Datumszeitformat|Eine Zeichenspalte im Resultset war an eine Datums-, Uhrzeit- oder Zeitstempel-C-Struktur gebunden, und ein Wert in der Spalte war jeweils ein ungültiges Datum, eine ungültige Uhrzeit oder ein Zeitstempel.|  
|22012|Division durch Null|Es wurde ein Wert aus einem arithmetischen Ausdruck zurückgegeben, der zu einer Division durch Null führte.|  
|22015|Intervallfeldüberlauf|Das Zuweisen eines SQL-Typs aus einem exakten numerischen oder Intervall-SQL-Typ zu einem Intervall-C-Typ verursachte einen Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Beim Abrufen von Daten in einen Intervall-C-Typ gab es keine Darstellung des Wertes des SQL-Typs im Intervall-C-Typ.|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|Eine Zeichenspalte im Resultset wurde an einen Zeichen-C-Puffer gebunden, und die Spalte enthielt ein Zeichen, für das der Zeichensatz des Puffers nicht dargestellt wurde.<br /><br /> Der C-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. Der SQL-Typ der Spalte war ein Zeichendatentyp; und der Wert in der Spalte war kein gültiges Literal des gebundenen C-Typs.|  
|24.000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.|  
|40001|Serialisierungsfehler|Die Transaktion, in der der Abruf ausgeführt wurde, wurde beendet, um einen Deadlock zu verhindern.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die **SQLFetch-Funktion** wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die **SQLFetch-Funktion** erneut für den *StatementHandle*aufgerufen.<br /><br /> Oder die **SQLFetch-Funktion** wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLFetch-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Der angegebene *StatementHandle* befand sich nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute** oder eine Katalogfunktion aufzurufen.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) **SQLFetch** wurde für das *StatementHandle* aufgerufen, nachdem **SQLExtendedFetch** aufgerufen wurde und bevor **SQLFreeStmt** mit der Option SQL_CLOSE aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|Das SQL_ATTR_USE_BOOKMARK Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und Spalte 0 wurde an einen Puffer gebunden, dessen Länge nicht der maximalen Länge für die Textmarke für dieses Resultset entspricht. (Diese Länge ist im Feld SQL_DESC_OCTET_LENGTH der IRD verfügbar und kann durch Aufrufen von **SQLDescribeCol**, **SQLColAttribute**oder **SQLGetDescField**abgerufen werden.)|  
|HY107|Zeilenwert a-range|Der mit dem Attribut SQL_ATTR_CURSOR_TYPE-Anweisung angegebene Wert wurde SQL_CURSOR_KEYSET_DRIVEN, aber der mit dem Attribut SQL_ATTR_KEYSET_SIZE-Anweisung angegebene Wert war größer als 0 und kleiner als der mit dem Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung angegebene Wert.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der Treiber oder die Datenquelle unterstützt die Konvertierung, die durch die Kombination des *TargetType* in **SQLBindCol** und des SQL-Datentyps der entsprechenden Spalte angegeben wird, nicht.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeoutzeitraum wird über SQLSetStmtAttr festgelegt, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLFetch** gibt das nächste Rowset im Resultset zurück. Sie kann nur aufgerufen werden, wenn ein Resultset vorhanden ist, d. h. nach einem Aufruf, der ein Resultset erstellt, und bevor der Cursor über diesem Resultset geschlossen wird. Wenn Spalten gebunden sind, werden die Daten in diesen Spalten zurückgegeben. Wenn die Anwendung einen Zeiger auf ein Zeilenstatusarray oder einen Puffer angegeben hat, in dem die Anzahl der abgerufenen Zeilen zurückgegeben werden soll, gibt **SQLFetch** auch diese Informationen zurück. Aufrufe von **SQLFetch** können mit Aufrufen von **SQLFetchScroll** gemischt werden, können jedoch nicht mit Aufrufen von **SQLExtendedFetch**gemischt werden. Weitere Informationen finden Sie unter [Abrufen einer Datenzeile](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 Wenn eine ODBC 3 *.x-Anwendung* mit einem ODBC 2 *.x-Treiber* arbeitet, ordnet der Treiber-Manager **SQLFetch-Aufrufe** **sqlExtendedFetch** für einen ODBC 2 *.x-Treiber* zu, der **SQLExtendedFetch**unterstützt. Wenn der ODBC 2 *.x-Treiber* **SQLExtendedFetch**nicht unterstützt, ordnet der Treiber-Manager **SQLFetch-Aufrufe** **SQLFetch** im ODBC 2 *.x-Treiber* zu, der nur eine einzelne Zeile abrufen kann.  
  
 Weitere Informationen finden Sie unter [Blockcursors, Scrollable Cursors und Backward Compatibility](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.  
  
## <a name="positioning-the-cursor"></a>Positionieren des Cursors  
 Wenn das Resultset erstellt wird, wird der Cursor vor dem Anfang des Resultsets positioniert. **SQLFetch** ruft das nächste Rowset ab. Es entspricht dem Aufrufen von **SQLFetchScroll** mit *FetchOrientation,* der auf SQL_FETCH_NEXT festgelegt ist. Weitere Informationen zu Cursorn finden Sie unter [Cursor](../../../odbc/reference/develop-app/cursors.md) und [Cursor blockieren](../../../odbc/reference/develop-app/block-cursors.md).  
  
 Das Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung gibt die Anzahl der Zeilen im Rowset an. Wenn das von **SQLFetch** abgerufene Rowset das Ende des Resultsets überlappt, gibt **SQLFetch** ein partielles Rowset zurück. Das heißt, wenn S + R - 1 größer als L ist, wobei S die Anfangszeile des abgerufenen Rowsets ist, R die Rowsetgröße und L die letzte Zeile im Resultset ist, dann sind nur die ersten L - S + 1 Zeilen des Rowsets gültig. Die verbleibenden Zeilen sind leer und haben den Status SQL_ROW_NOROW.  
  
 Nachdem **SQLFetch** zurückgegeben wurde, ist die aktuelle Zeile die erste Zeile des Rowsets.  
  
 Die in der folgenden Tabelle aufgeführten Regeln beschreiben die Cursorpositionierung nach einem Aufruf von **SQLFetch**, basierend auf den Bedingungen, die in der zweiten Tabelle in diesem Abschnitt aufgeführt sind.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|Vor dem Start|1|  
|*CurrRowsetStart* \< =  *LastResultRow - RowsetSize*[1]|*CurrRowsetStart* + *RowsetSize*[2]|  
|*CurrRowsetStart* > *LastResultRow - RowsetSize*[1]|Nach dem Ende|  
|Nach dem Ende|Nach dem Ende|  
  
 [1] Wenn die Rowsetgröße zwischen den Abrufen geändert wird, ist dies die Rowsetgröße, die mit dem vorherigen Abruf verwendet wurde.  
  
 [2] Wenn die Rowsetgröße zwischen den Abrufen geändert wird, ist dies die Rowsetgröße, die mit dem neuen Abruf verwendet wurde.  
  
|Notation|Bedeutung|  
|--------------|-------------|  
|Vor dem Start|Der Blockcursor wird vor dem Start des Resultsets positioniert. Wenn die erste Zeile des neuen Rowsets vor dem Anfang des Resultsets liegt, gibt **SQLFetch** SQL_NO_DATA zurück.|  
|Nach dem Ende|Der Blockcursor wird nach dem Ende des Resultsets positioniert. Wenn die erste Zeile des neuen Rowsets nach dem Ende des Resultsets liegt, gibt **SQLFetch** SQL_NO_DATA zurück.|  
|*CurrRowsetStart*|Die Nummer der ersten Zeile im aktuellen Rowset.|  
|*LastResultRow*|Die Nummer der letzten Zeile im Resultset.|  
|*RowsetSize*|Die Rowsetgröße.|  
  
 Angenommen, ein Resultset hat 100 Zeilen und die Rowsetgröße 5. Die folgende Tabelle zeigt das Rowset und den Rückgabecode, der von **SQLFetch** für verschiedene Startpositionen zurückgegeben wird.  
  
|Aktuelles Rowset|Rückgabecode|Neues Rowset|Anzahl der abgerufenen Zeilen|  
|--------------------|-----------------|----------------|------------------------|  
|Vor dem Start|SQL_SUCCESS|1 bis 5|5|  
|1 bis 5|SQL_SUCCESS|6 bis 10|5|  
|52 bis 56|SQL_SUCCESS|57 bis 61|5|  
|91 bis 95|SQL_SUCCESS|96 bis 100|5|  
|93 bis 97|SQL_SUCCESS|98 bis 100. Die Zeilen 4 und 5 des Zeilenstatusarrays sind auf SQL_ROW_NOROW festgelegt.|3|  
|96 bis 100|SQL_NO_DATA|Keine|0|  
|99 bis 100|SQL_NO_DATA|Keine|0|  
|Nach dem Ende|SQL_NO_DATA|Keine|0|  
  
## <a name="returning-data-in-bound-columns"></a>Zurückgeben von Daten in gebundenen Spalten  
 Wenn **SQLFetch** jede Zeile zurückgibt, werden die Daten für jede gebundene Spalte in den Anlaufraum für diese Spalte eingefügt. Wenn keine Spalten gebunden sind, gibt **SQLFetch** keine Daten zurück, verschiebt jedoch den Blockcursor vorwärts. Die Daten können weiterhin mit **SQLGetData**abgerufen werden. Wenn es sich bei dem Cursor um einen Cursor mit mehreren Zeilen handelt (d. h., der SQL_ATTR_ROW_ARRAY_SIZE größer als 1 ist), kann **SQLGetData** nur aufgerufen werden, wenn SQL_GD_BLOCK zurückgegeben wird, wenn **SQLGetInfo** mit einem *InfoType* von SQL_GETDATA_EXTENSIONS aufgerufen wird. (Weitere Informationen finden Sie unter [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).)  
  
 Für jede gebundene Spalte in einer Zeile führt **SQLFetch** die folgenden Schritte aus:  
  
1.  Legt den Längen-/Indikatorpuffer auf SQL_NULL_DATA und fährt mit der nächsten Spalte fort, wenn die Daten NULL sind. Wenn die Daten NULL sind und kein Längen-/Indikatorpuffer gebunden ist, gibt **SQLFetch** SQLSTATE 22002 (Indikatorvariable erforderlich, aber nicht angegeben) für die Zeile zurück und fährt mit der nächsten Zeile fort. Informationen zum Bestimmen der Adresse des Längen-/Indikatorpuffers finden Sie unter "Pufferadressen" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
     Wenn die Daten für die Spalte nicht NULL sind, fährt **SQLFetch** mit Schritt 2 fort.  
  
2.  Wenn das Attribut SQL_ATTR_MAX_LENGTH Anweisung auf einen Wert ungleich Null festgelegt ist und die Spalte Zeichen- oder Binärdaten enthält, werden die Daten auf SQL_ATTR_MAX_LENGTH Bytes abgeschnitten.  
  
    > [!NOTE]  
    >  Das Attribut SQL_ATTR_MAX_LENGTH-Anweisung soll den Netzwerkverkehr reduzieren. Sie wird in der Regel von der Datenquelle implementiert, die die Daten abkürt, bevor sie über das Netzwerk zurückgegeben werden. Treiber und Datenquellen sind nicht erforderlich, um sie zu unterstützen. Um zu gewährleisten, dass Daten auf eine bestimmte Größe abgeschnitten werden, sollte eine Anwendung daher einen Puffer dieser Größe zuweisen und die Größe im *Argument cbValueMax* in **SQLBindCol**angeben.  
  
3.  Konvertiert die Daten in den von *TargetType* in **SQLBindCol**angegebenen Typ.  
  
4.  Wenn die Daten in einen Datentyp variabler Länge konvertiert wurden, z. B. Zeichen oder Binärdaten, überprüft **SQLFetch,** ob die Länge der Daten die Länge des Datenpuffers überschreitet. Wenn die Länge der Zeichendaten (einschließlich des Nullbeendigungszeichens) die Länge des Datenpuffers überschreitet, kürst **SQLFetch** die Daten auf die Länge des Datenpuffers abzüglich der Länge eines Nullbeendigungszeichens. Anschließend werden die Daten auf null beendet. Wenn die Länge der Binärdaten die Länge des Datenpuffers überschreitet, wird sie **von SQLFetch** auf die Länge des Datenpuffers abgeschnitten. Die Länge des Datenpuffers wird mit *BufferLength* in **SQLBindCol**angegeben.  
  
     **SQLFetch** führt niemals Daten herunter, die in Datentypen fester Länge konvertiert wurden. Es wird immer davon ausgegangen, dass die Länge des Datenpuffers die Größe des Datentyps ist.  
  
5.  Fügt die konvertierten (und möglicherweise abgeschnittenen) Daten in den Datenpuffer ein. Informationen zum Bestimmen der Adresse des Datenpuffers finden Sie unter "Pufferadressen" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
6.  Fügt die Länge der Daten in den Längen-/Indikatorpuffer ein. Wenn der Indikatorzeiger und der Längenzeiger auf denselben Puffer festgelegt wurden (wie ein Aufruf von **SQLBindCol),** wird die Länge in den Puffer für gültige Daten geschrieben und SQL_NULL_DATA im Puffer für NULL-Daten geschrieben. Wenn kein Längen-/Indikatorpuffer gebunden war, gibt **SQLFetch** die Länge nicht zurück.  
  
    -   Bei Zeichen- oder Binärdaten ist dies die Länge der Daten nach der Konvertierung und vor dem Abschneiden, da der Datenpuffer zu klein ist. Wenn der Treiber die Länge der Daten nach der Konvertierung nicht bestimmen kann, wie dies manchmal bei langen Daten der Fall ist, legt er die Länge auf SQL_NO_TOTAL fest. Wenn Daten aufgrund des Attributs SQL_ATTR_MAX_LENGTH Anweisung abgeschnitten wurden, wird der Wert dieses Attributs in den Längen-/Indikatorpuffer anstelle der tatsächlichen Länge eingefügt. Dies liegt daran, dass dieses Attribut entworfen wurde, um Daten auf dem Server vor der Konvertierung zu abschneiden, sodass der Treiber keine Möglichkeit hat, herauszufinden, wie hoch die tatsächliche Länge ist.  
  
    -   Bei allen anderen Datentypen ist dies die Länge der Daten nach der Konvertierung; Das heißt, es ist die Größe des Typs, in den die Daten konvertiert wurden.  
  
     Informationen zum Bestimmen der Adresse des Längen-/Indikatorpuffers finden Sie unter "Pufferadressen" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
7.  Wenn die Daten während der Konvertierung abgeschnitten werden, ohne dass signifikante Ziffern verloren gehen (z. B. wird die reelle Zahl 1.234 bei der Konvertierung auf die ganze Zahl 1 abgeschnitten), gibt **SQLFetch** SQLSTATE 01S07 (Fractional-Abschneidung) und SQL_SUCCESS_WITH_INFO zurück. Wenn die Daten abgeschnitten werden, weil die Länge des Datenpuffers zu klein ist (z. B. wird die Zeichenfolge "abcdef" in einen 4-Byte-Puffer gesetzt), gibt **SQLFetch** SQLSTATE 01004 (Daten abgeschnitten) und SQL_SUCCESS_WITH_INFO zurück. Wenn Daten aufgrund des SQL_ATTR_MAX_LENGTH-Anweisungsattributs abgeschnitten werden, gibt **SQLFetch** SQL_SUCCESS zurück und gibt SQLSTATE 01S07 (Fractional-Abschneide) oder SQLSTATE 01004 (Daten abgeschnitten) nicht zurück. Wenn Daten während der Konvertierung mit einem Verlust signifikanter Ziffern abgeschnitten werden (z. B. wenn ein SQL_INTEGER Wert größer als 100.000 in ein SQL_C_TINYINT konvertiert wurde), gibt **SQLFetch** SQLSTATE 22003 (Numerischer Wert aout of range) und SQL_ERROR (wenn die Rowsetgröße 1 ist) oder SQL_SUCCESS_WITH_INFO (wenn die Rowsetgröße größer als 1 ist) zurück.  
  
 Der Inhalt des gebundenen Datenpuffers und des Längen-/Indikatorpuffers sind nicht definiert, wenn **SQLFetch** oder **SQLFetchScroll** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO nicht zurückgeben.  
  
## <a name="row-status-array"></a>Zeilenstatusarray  
 Das Zeilenstatusarray wird verwendet, um den Status jeder Zeile im Rowset zurückzugeben. Die Adresse dieses Arrays wird mit dem Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung angegeben. Das Array wird von der Anwendung zugewiesen und muss über so viele Elemente verfügen, wie vom attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung angegeben werden. Die Werte werden von **SQLFetch**, **SQLFetchScroll**und **SQLBulkOperations** oder **SQLSetPos** festgelegt (außer wenn sie aufgerufen wurden, nachdem der Cursor von **SQLExtendedFetch**positioniert wurde). Wenn der Wert des SQL_ATTR_ROW_STATUS_PTR-Anweisungsattributs ein Nullzeiger ist, geben diese Funktionen den Zeilenstatus nicht zurück.  
  
 Der Inhalt des Zeilenstatus-Arraypuffers ist nicht definiert, wenn **SQLFetch** oder **SQLFetchScroll** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO nicht zurückgeben.  
  
 Die folgenden Werte werden im Zeilenstatusarray zurückgegeben.  
  
|Zeilenstatus-Arraywert|Beschreibung|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|Die Zeile wurde erfolgreich abgerufen und hat sich seit dem letzten Abruf aus diesem Resultset nicht geändert.|  
|SQL_ROW_SUCCESS_WITH_INFO|Die Zeile wurde erfolgreich abgerufen und hat sich seit dem letzten Abruf aus diesem Resultset nicht geändert. Es wurde jedoch eine Warnung über die Zeile zurückgegeben.|  
|SQL_ROW_ERROR|Beim Abrufen der Zeile ist ein Fehler aufgetreten.|  
|SQL_ROW_UPDATED[1],[2] und [3]|Die Zeile wurde erfolgreich abgerufen und hat sich geändert, seit sie zuletzt aus diesem Resultset abgerufen wurde. Wenn die Zeile erneut aus diesem Resultset abgerufen oder von **SQLSetPos**aktualisiert wird, wird der Status in den neuen Status der Zeile geändert.|  
|SQL_ROW_DELETED[3]|Die Zeile wurde gelöscht, seit sie zuletzt aus diesem Resultset abgerufen wurde.|  
|SQL_ROW_ADDED[4]|Die Zeile wurde von **SQLBulkOperations**eingefügt. Wenn die Zeile erneut aus diesem Resultset abgerufen oder von **SQLSetPos**aktualisiert wird, lautet ihr Status SQL_ROW_SUCCESS.|  
|SQL_ROW_NOROW|Das Rowset überlappte das Ende des Resultsets, und es wurde keine Zeile zurückgegeben, die diesem Element des Zeilenstatusarrays entsprach.|  
  
 [1] Bei Keyset-, gemischten und dynamischen Cursorn gilt die Datenzeile als gelöscht und eine neue Zeile hinzugefügt, wenn ein Schlüsselwert aktualisiert wird.  
  
 [2] Einige Treiber können keine Aktualisierungen von Daten erkennen und geben daher diesen Wert nicht zurück. Um zu bestimmen, ob ein Treiber Aktualisierungen für neu abgerufene Zeilen erkennen kann, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_ROW_UPDATES auf.  
  
 [3] **SQLFetch** kann diesen Wert nur zurückgeben, wenn er mit Aufrufen von **SQLFetchScroll**vermischt wird. Dies liegt daran, dass **SQLFetch** durch das Resultset vorwärts bewegt wird und bei ausschließlicher Verwendung keine Zeilen erneut abruft. Da keine Zeilen erneut abgerufen werden, erkennt **SQLFetch** keine Änderungen, die an zuvor abgerufenen Zeilen vorgenommen wurden. Wenn **SQLFetchScroll** den Cursor jedoch vor zuvor abgerufenen Zeilen positioniert und **SQLFetch** zum Abrufen dieser Zeilen verwendet wird, kann **SQLFetch** alle Änderungen an diesen Zeilen erkennen.  
  
 [4] Nur von SQLBulkOperations zurückgegeben. Nicht von **SQLFetch** oder **SQLFetchScroll**festgelegt .  
  
### <a name="rows-fetched-buffer"></a>Zeilen Abgerufener Puffer  
 Der abgerufene Puffer für Zeilen wird verwendet, um die Anzahl der abgerufenen Zeilen zurückzugeben, einschließlich der Zeilen, für die keine Daten zurückgegeben wurden, weil beim Abrufen ein Fehler aufgetreten ist. Mit anderen Worten, es ist die Anzahl der Zeilen, für die der Wert im Zeilenstatusarray nicht SQL_ROW_NOROW ist. Die Adresse dieses Puffers wird mit dem Attribut SQL_ATTR_ROWS_FETCHED_PTR-Anweisung angegeben. Der Puffer wird von der Anwendung zugewiesen. Sie wird von **SQLFetch** und **SQLFetchScroll**festgelegt. Wenn der Wert des SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattributs ein Nullzeiger ist, geben diese Funktionen nicht die Anzahl der abgerufenen Zeilen zurück. Um die Nummer der aktuellen Zeile im Resultset zu bestimmen, kann eine Anwendung **SQLGetStmtAttr** mit dem Attribut SQL_ATTR_ROW_NUMBER aufrufen.  
  
 Der Inhalt des abgerufenen Zeilenpuffers ist nicht definiert, wenn **SQLFetch** oder **SQLFetchScroll** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO nicht zurückgibt, es sei denn, SQL_NO_DATA zurückgegeben wird, in diesem Fall ist der Wert in dem abgerufenen Zeilenpuffer auf 0 festgelegt.  
  
### <a name="error-handling"></a>Fehlerbehandlung  
 Fehler und Warnungen können auf einzelne Zeilen oder die gesamte Funktion angewendet werden. Weitere Informationen zu Diagnosedatensätzen finden Sie unter [Diagnostics](../../../odbc/reference/develop-app/diagnostics.md) und [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
#### <a name="errors-and-warnings-on-the-entire-function"></a>Fehler und Warnungen für die gesamte Funktion  
 Wenn ein Fehler auf die gesamte Funktion angewendet wird, z. B. SQLSTATE HYT00 (Timeout abgelaufen) oder SQLSTATE 24000 (Status ungültiger Cursor), gibt **SQLFetch** SQL_ERROR und die entsprechende SQLSTATE zurück. Der Inhalt der Rowsetpuffer ist nicht definiert, und die Cursorposition bleibt unverändert.  
  
 Wenn eine Warnung auf die gesamte Funktion angewendet wird, gibt **SQLFetch** SQL_SUCCESS_WITH_INFO und die entsprechende SQLSTATE zurück. Die Statusdatensätze für Warnungen, die für die gesamte Funktion gelten, werden vor den Statusdatensätzen zurückgegeben, die für einzelne Zeilen gelten.  
  
#### <a name="errors-and-warnings-in-individual-rows"></a>Fehler und Warnungen in einzelnen Zeilen  
 Wenn ein Fehler (z. B. SQLSTATE 22012 (Division durch Null)) oder eine Warnung (z. B. SQLSTATE 01004 (Data begekürzt)) auf eine einzelne Zeile zutrifft, führt **SQLFetch**die folgenden Schritte aus:  
  
-   Legt das entsprechende Element des Zeilenstatusarrays auf SQL_ROW_ERROR für Fehler oder SQL_ROW_SUCCESS_WITH_INFO für Warnungen fest.  
  
-   Fügt null oder mehr Statusdatensätze hinzu, die SQLSTATEs für den Fehler oder die Warnung enthalten.  
  
-   Legt die Zeilen- und Spaltennummernfelder in den Statusdatensätzen fest. Wenn **SQLFetch** eine Zeilen- oder Spaltennummer nicht bestimmen kann, legt es diese Zahl auf SQL_ROW_NUMBER_UNKNOWN bzw. SQL_COLUMN_NUMBER_UNKNOWN fest. Wenn der Statusdatensatz nicht für eine bestimmte Spalte gilt, legt **SQLFetch** die Spaltennummer auf SQL_NO_COLUMN_NUMBER fest.  
  
 **SQLFetch** ruft weiterhin Zeilen ab, bis alle Zeilen im Rowset abgerufen wurden. Es gibt SQL_SUCCESS_WITH_INFO zurück, es sei denn, in jeder Zeile des Rowsets (ohne Zeilen mit Status SQL_ROW_NOROW) wird ein Fehler zurückgegeben, in diesem Fall wird SQL_ERROR zurückgegeben. Wenn die Rowsetgröße 1 ist und in dieser Zeile ein Fehler auftritt, gibt **SQLFetch** SQL_ERROR zurück.  
  
 **SQLFetch** gibt die Statusdatensätze in Zeilennummernreihenfolge zurück. Das heißt, es gibt alle Statusdatensätze für unbekannte Zeilen zurück (falls vorhanden); Als nächstes gibt es alle Statusdatensätze für die erste Zeile (falls vorhanden) zurück, und dann gibt er alle Statusdatensätze für die zweite Zeile (falls vorhanden) usw. zurück. Die Statusdatensätze für jede Zeile werden gemäß den normalen Regeln für die Reihenfolge von Statusdatensätzen sortiert. Weitere Informationen finden Sie unter "Sequenz von Statusdatensätzen" in [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
### <a name="descriptors-and-sqlfetch"></a>Deskriptoren und SQLFetch  
 In den folgenden Abschnitten wird beschrieben, wie **SQLFetch** mit Deskriptoren interagiert.  
  
#### <a name="argument-mappings"></a>Argumentzuordnungen  
 Der Treiber setzt keine Deskriptorfelder basierend auf den Argumenten von **SQLFetch**.  
  
#### <a name="other-descriptor-fields"></a>Andere Deskriptorfelder  
 Die folgenden Deskriptorfelder werden von **SQLFetch**verwendet.  
  
|Deskriptorfeld|Desc.|Feld in|Durchsetzen|  
|----------------------|-----------|--------------|-----------------|  
|SQL_DESC_ARRAY_SIZE|Ard|Header|SQL_ATTR_ROW_ARRAY_SIZE Anweisungsattribut|  
|SQL_DESC_ARRAY_STATUS_PTR|Ird|Header|SQL_ATTR_ROW_STATUS_PTR Anweisungsattribut|  
|SQL_DESC_BIND_OFFSET_PTR|Ard|Header|SQL_ATTR_ROW_BIND_OFFSET_PTR Anweisungsattribut|  
|SQL_DESC_BIND_TYPE|Ard|Header|SQL_ATTR_ROW_BIND_TYPE Anweisungsattribut|  
|SQL_DESC_COUNT|Ard|Header|*ColumnNumber-Argument* von **SQLBindCol**|  
|SQL_DESC_DATA_PTR|Ard|records|*TargetValuePtr-Argument* von **SQLBindCol**|  
|SQL_DESC_INDICATOR_PTR|Ard|records|*StrLen_or_IndPtr* Argument in **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH|Ard|records|*BufferLength-Argument* in **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH_PTR|Ard|records|*StrLen_or_IndPtr* Argument in **SQLBindCol**|  
|SQL_DESC_ROWS_PROCESSED_PTR|Ird|Header|SQL_ATTR_ROWS_FETCHED_PTR Anweisungsattribut|  
|SQL_DESC_TYPE|Ard|records|*TargetType-Argument* in **SQLBindCol**|  
  
 Alle Deskriptorfelder können auch über **SQLSetDescField**festgelegt werden.  
  
#### <a name="separate-length-and-indicator-buffers"></a>Separate Längen- und Indikatorpuffer  
 Anwendungen können einen einzelnen Puffer oder zwei separate Puffer binden, die zum Halten von Längen- und Indikatorwerten verwendet werden können. Wenn eine Anwendung **SQLBindCol**aufruft, legt der Treiber die SQL_DESC_OCTET_LENGTH_PTR- und SQL_DESC_INDICATOR_PTR Felder der ARD auf dieselbe Adresse fest, die im *StrLen_or_IndPtr-Argument* übergeben wird. Wenn eine Anwendung **SQLSetDescField** oder **SQLSetDescRec**aufruft, kann sie diese beiden Felder auf unterschiedliche Adressen festlegen.  
  
 **SQLFetch** bestimmt, ob die Anwendung separate Längen- und Indikatorpuffer angegeben hat. In diesem Fall, wenn die Daten nicht NULL sind, setzt **SQLFetch** den Indikatorpuffer auf 0 und gibt die Länge im Längenpuffer zurück. Wenn die Daten NULL sind, legt **SQLFetch** den Indikatorpuffer auf SQL_NULL_DATA und ändert den Längenpuffer nicht.  
  
### <a name="code-example"></a>Codebeispiel  
 Siehe [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)und [SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md).  
  
### <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einer Ergebnismenge|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Schließen des Cursors für die Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Abrufen eines Teils oder der gesamten Datenspalte|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Zurückgeben der Anzahl der Ergebnissatzspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
