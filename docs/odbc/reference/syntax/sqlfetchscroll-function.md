---
title: SQLFetchScroll-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFetchScroll
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFetchScroll
helpviewer_keywords:
- SQLFetchScroll function [ODBC]
ms.assetid: c0243667-428c-4dda-ae91-3c307616a1ac
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6c65ef71f5c2cb9202ab788cac5e00357674f4a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285880"
---
# <a name="sqlfetchscroll-function"></a>SQLFetchScroll-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLFetchScroll** ruft das angegebene Rowset von Daten aus dem Resultset ab und gibt Daten für alle gebundenen Spalten zurück. Rowsets können an einer absoluten oder relativen Position oder nach Lesezeichen angegeben werden.  
  
 Wenn Sie mit einem ODBC 2.x-Treiber arbeiten, ordnet der Treiber-Manager diese Funktion **SQLExtendedFetch**zu. Weitere Informationen finden Sie unter [Zuordnen von Ersetzungsfunktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFetchScroll(  
      SQLHSTMT      StatementHandle,  
      SQLSMALLINT   FetchOrientation,  
      SQLLEN        FetchOffset);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *FetchOrientation*  
 [Eingabe]  
  
 Art des Abrufs:  
  
 SQL_FETCH_NEXT  
  
 SQL_FETCH_PRIOR  
  
 SQL_FETCH_FIRST  
  
 SQL_FETCH_LAST  
  
 SQL_FETCH_ABSOLUTE  
  
 SQL_FETCH_RELATIVE  
  
 SQL_FETCH_BOOKMARK  
  
 Weitere Informationen finden Sie unter "Positionieren des Cursors" im Abschnitt "Kommentare".  
  
 *FetchOffset*  
 [Eingabe]  
  
 Nummer der abzurufenden Zeile. Die Interpretation dieses Arguments hängt vom Wert des *FetchOrientation-Arguments* ab. Weitere Informationen finden Sie unter "Positionieren des Cursors" im Abschnitt "Kommentare".  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFetchScroll** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem HandleType von SQL_HANDLE_STMT und einem Handle von StatementHandle aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLFetchScroll** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben. Wenn ein Fehler in einer einzelnen Spalte auftritt, kann **SQLGetDiagField** mit einem DiagIdentifier von SQL_DIAG_COLUMN_NUMBER aufgerufen werden, um die Spalte zu bestimmen, auf der der Fehler aufgetreten ist. und **SQLGetDiagField** kann mit einem DiagIdentifier von SQL_DIAG_ROW_NUMBER aufgerufen werden, um die Zeile zu bestimmen, die diese Spalte enthält.  
  
 Für alle SQLSTATEs, die SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgeben können (außer 01xxx SQLSTATEs), wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn ein Fehler bei einer oder mehreren Zeilen eines mehrreihigen Vorgangs auftritt, und SQL_ERROR wird zurückgegeben, wenn ein Fehler bei einem einzeiligen Vorgang auftritt.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für eine Spalte zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht null sind. Wenn es sich um einen Zeichenfolgenwert handelte, wurde er rechts abgeschnitten.|  
|01S01|Fehler in Zeile|Beim Abrufen einer oder einer oder mehreren Zeilen ist ein Fehler aufgetreten.<br /><br /> (Wenn diese SQLSTATE zurückgegeben wird, wenn eine ODBC 3 *.x-Anwendung* mit einem ODBC 2 *.x-Treiber* arbeitet, kann sie ignoriert werden.)|  
|01S06|Versuch, abzurufen, bevor das Resultset das erste Rowset zurückgibt|Das angeforderte Rowset überlappte den Anfang des Resultsets, wenn FetchOrientation SQL_FETCH_PRIOR wurde, die aktuelle Position über der ersten Zeile lag und die Nummer der aktuellen Zeile kleiner oder gleich der Rowsetgröße ist.<br /><br /> Das angeforderte Rowset überlappte den Anfang des Resultsets, wenn FetchOrientation SQL_FETCH_PRIOR wurde, die aktuelle Position über das Ende des Resultsets hinausging und die Rowsetgröße größer als die Größe des Resultsets war.<br /><br /> Das angeforderte Rowset überlappte den Anfang des Resultsets, als FetchOrientation SQL_FETCH_RELATIVE wurde, FetchOffset negativ war und der absolute Wert von FetchOffset kleiner oder gleich der Rowsetgröße war.<br /><br /> Das angeforderte Rowset überlappte den Anfang des Resultsets, als FetchOrientation SQL_FETCH_ABSOLUTE war, FetchOffset negativ war und der absolute Wert von FetchOffset größer als die Größe des Resultsets war, aber kleiner oder gleich der Rowsetgröße.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Bruchschnitt|Die für eine Spalte zurückgegebenen Daten wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteil der Zahl abgeschnitten. Für Zeit-, Zeitstempel- und Intervalldatentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|Der Datenwert einer Spalte im Resultset konnte nicht in den von *TargetType* in **SQLBindCol**angegebenen Datentyp konvertiert werden.<br /><br /> Spalte 0 wurde mit einem Datentyp von SQL_C_BOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt.<br /><br /> Spalte 0 wurde mit einem Datentyp von SQL_C_VARBOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut wurde nicht auf SQL_UB_VARIABLE festgelegt.|  
|07009|Ungültiger Deskriptorindex|Der Treiber war ein ODBC 2 *.x-Treiber,* der **SQLExtendedFetch**nicht unterstützt, und eine Spaltennummer, die in der Bindung für eine Spalte angegeben wurde, war 0.<br /><br /> Spalte 0 wurde gebunden, und das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_OFF festgelegt.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|22001|String-Daten, rechts abgeschnitten|Eine für eine Spalte zurückgegebene Textmarke variabler Länge wurde abgeschnitten.|  
|22002|Indikatorvariable erforderlich, aber nicht mitgeliefert|NULL-Daten wurden in eine Spalte abgerufen, deren *StrLen_or_IndPtr* von **SQLBindCol** festgelegt wurde (oder SQL_DESC_INDICATOR_PTR von **SQLSetDescField** oder **SQLSetDescRec**festgelegt wurde).|  
|22003|Numerischer Wert aofc|Das Zurückgeben des numerischen Werts (als numerische oder Zeichenfolge) für eine oder mehrere gebundene Spalten hätte dazu geführt, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde.<br /><br /> Weitere Informationen finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in Anhang [D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Ungültiges Datumszeitformat|Eine Zeichenspalte im Resultset war an eine Datums-, Uhrzeit- oder Zeitstempel-C-Struktur gebunden, und ein Wert in der Spalte war jeweils ein ungültiges Datum, eine ungültige Uhrzeit oder ein Zeitstempel.|  
|22012|Division durch Null|Es wurde ein Wert aus einem arithmetischen Ausdruck zurückgegeben, der zu einer Division durch Null führte.|  
|22015|Intervallfeldüberlauf|Das Zuweisen eines SQL-Typs aus einem exakten numerischen oder Intervall-SQL-Typ zu einem Intervall-C-Typ verursachte einen Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Beim Abrufen von Daten in einen Intervall-C-Typ gab es keine Darstellung des Wertes des SQL-Typs im Intervall-C-Typ.|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|Eine Zeichenspalte im Resultset wurde an einen Zeichen-C-Puffer gebunden, und die Spalte enthielt ein Zeichen, für das der Zeichensatz des Puffers nicht dargestellt wurde.<br /><br /> Der C-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. Der SQL-Typ der Spalte war ein Zeichendatentyp; und der Wert in der Spalte war kein gültiges Literal des gebundenen C-Typs.|  
|24.000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.|  
|40001|Serialisierungsfehler|Die Transaktion, in der der Abruf ausgeführt wurde, wurde beendet, um einen Deadlock zu verhindern.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLFetchScroll-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Der angegebene *StatementHandle* befand sich nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute** oder eine Katalogfunktion aufzurufen.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) **SQLFetch** wurde für das *StatementHandle* aufgerufen, nachdem **SQLExtendedFetch** aufgerufen wurde und bevor **SQLFreeStmt** mit der Option SQL_CLOSE aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|Das SQL_ATTR_USE_BOOKMARK Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und Spalte 0 wurde an einen Puffer gebunden, dessen Länge nicht der maximalen Länge für die Textmarke für dieses Resultset entspricht. (Diese Länge ist im Feld SQL_DESC_OCTET_LENGTH der IRD verfügbar und kann durch Aufrufen von **SQLDescribeCol**, **SQLColAttribute**oder **SQLGetDescField**abgerufen werden.)|  
|HY106|Abruftyp anicht in Reichweite|DM) Der für das Argument FetchOrientation angegebene Wert war ungültig.<br /><br /> (DM) Das Argument FetchOrientation wurde SQL_FETCH_BOOKMARK, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut wurde auf SQL_UB_OFF festgelegt.<br /><br /> Der Wert des SQL_ATTR_CURSOR_TYPE-Anweisungsattributs wurde SQL_CURSOR_FORWARD_ONLY, und der Wert des Arguments FetchOrientation wurde nicht SQL_FETCH_NEXT.<br /><br /> Der Wert des SQL_ATTR_CURSOR_SCROLLABLE-Anweisungsattributs wurde SQL_NONSCROLLABLE, und der Wert des Arguments FetchOrientation wurde nicht SQL_FETCH_NEXT.|  
|HY107|Zeilenwert a-range|Der mit dem Attribut SQL_ATTR_CURSOR_TYPE-Anweisung angegebene Wert wurde SQL_CURSOR_KEYSET_DRIVEN, aber der mit dem Attribut SQL_ATTR_KEYSET_SIZE-Anweisung angegebene Wert war größer als 0 und kleiner als der mit dem Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung angegebene Wert.|  
|HY111|Ungültiger Lesezeichenwert|Das Argument FetchOrientation wurde SQL_FETCH_BOOKMARK, und die Textmarke, auf die der Wert im SQL_ATTR_FETCH_BOOKMARK_PTR Anweisungsattribut zeigt, war ungültig oder war ein Nullzeiger.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der Treiber oder die Datenquelle unterstützt die Konvertierung, die durch die Kombination des *TargetType* in **SQLBindCol** und des SQL-Datentyps der entsprechenden Spalte angegeben wird, nicht.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeoutzeitraum wird über SQLSetStmtAttr festgelegt, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLFetchScroll** gibt ein angegebenes Rowset aus dem Resultset zurück. Rowsets können durch absolute oder relative Position oder durch Lesezeichen angegeben werden. **SQLFetchScroll** kann nur aufgerufen werden, wenn ein Resultset vorhanden ist, d. h. nach einem Aufruf, der ein Resultset erstellt, und bevor der Cursor über diesem Resultset geschlossen wird. Wenn Spalten gebunden sind, werden die Daten in diesen Spalten zurückgegeben. Wenn die Anwendung einen Zeiger auf ein Zeilenstatusarray oder einen Puffer angegeben hat, in dem die Anzahl der abgerufenen Zeilen zurückgegeben werden soll, gibt **SQLFetchScroll** auch diese Informationen zurück. Aufrufe von **SQLFetchScroll** können mit Aufrufen von **SQLFetch** gemischt werden, können jedoch nicht mit Aufrufen von **SQLExtendedFetch**gemischt werden.  
  
 Weitere Informationen finden Sie unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md) und [Scrollable Cursors](../../../odbc/reference/develop-app/using-scrollable-cursors.md).  
  
## <a name="positioning-the-cursor"></a>Positionieren des Cursors  
 Wenn das Resultset erstellt wird, wird der Cursor vor dem Anfang des Resultsets positioniert. **SQLFetchScroll** positioniert den Blockcursor basierend auf den Werten der *Argumente FetchOrientation* und *FetchOffset,* wie in der folgenden Tabelle dargestellt. Die genauen Regeln für die Bestimmung des Beginns des neuen Rowsets werden im nächsten Abschnitt angezeigt.  
  
|FetchOrientation|Bedeutung|  
|----------------------|-------------|  
|SQL_FETCH_NEXT|Geben Sie das nächste Rowset zurück. Dies entspricht dem Aufrufen von **SQLFetch**.<br /><br /> **SQLFetchScroll** ignoriert den Wert von *FetchOffset*.|  
|SQL_FETCH_PRIOR|Geben Sie das vorherige Rowset zurück.<br /><br /> **SQLFetchScroll** ignoriert den Wert von *FetchOffset*.|  
|SQL_FETCH_RELATIVE|Geben Sie das Rowset *FetchOffset* vom Anfang des aktuellen Rowsets zurück.|  
|SQL_FETCH_ABSOLUTE|Geben Sie das Rowset ab Zeile *FetchOffset*zurück.|  
|SQL_FETCH_FIRST|Geben Sie das erste Rowset im Resultset zurück.<br /><br /> **SQLFetchScroll** ignoriert den Wert von *FetchOffset*.|  
|SQL_FETCH_LAST|Geben Sie das letzte vollständige Rowset im Resultset zurück.<br /><br /> **SQLFetchScroll** ignoriert den Wert von *FetchOffset*.|  
|SQL_FETCH_BOOKMARK|Geben Sie das Rowset FetchOffset-Zeilen aus der Textmarke zurück, die durch das Attribut SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisung angegeben wird.|  
  
 Treiber müssen nicht alle Abrufausrichtungen unterstützen. Eine Anwendung ruft **SQLGetInfo** mit einem Informationstyp SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 auf (je nach Typ des Cursors), um zu bestimmen, welche Abrufausrichtungen vom Treiber unterstützt werden. Die Anwendung sollte sich die SQL_CA1_NEXT, SQL_CA1_RELATIVE, SQL_CA1_ABSOLUTE und WQL_CA1_BOOKMARK Bitmasken in diesen Informationstypen ansehen. Wenn der Cursor nur Vorwärts und FetchOrientation nicht SQL_FETCH_NEXT ist, gibt **SQLFetchScroll** SQLSTATE HY106 (Fetch-Typ a-range) zurück.  
  
 Das Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung gibt die Anzahl der Zeilen im Rowset an. Wenn das von **SQLFetchScroll** abgerufene Rowset das Ende des Resultsets überlappt, gibt **SQLFetchScroll** ein partielles Rowset zurück. Das heißt, wenn S + R - 1 größer als L ist, wobei S die Anfangszeile des abgerufenen Rowsets ist, R die Rowsetgröße und L die letzte Zeile im Resultset ist, dann sind nur die ersten L - S + 1 Zeilen des Rowsets gültig. Die verbleibenden Zeilen sind leer und haben den Status SQL_ROW_NOROW.  
  
 Nachdem **SQLFetchScroll** zurückgegeben wurde, ist die aktuelle Zeile die erste Zeile des Rowsets.  
  
## <a name="cursor-positioning-rules"></a>Cursor-Positionierungsregeln  
 In den folgenden Abschnitten werden die genauen Regeln für jeden Wert von FetchOrientation beschrieben. Diese Regeln verwenden die folgende Notation.  
  
|Notation|Bedeutung|  
|--------------|-------------|  
|*Vor dem Start*|Der Blockcursor wird vor dem Start des Resultsets positioniert. Wenn die erste Zeile des neuen Rowsets vor dem Start des Resultsets liegt, gibt **SQLFetchScroll** SQL_NO_DATA zurück.|  
|*Nach dem Ende*|Der Blockcursor wird nach dem Ende des Resultsets positioniert. Wenn die erste Zeile des neuen Rowsets nach dem Ende des Resultsets liegt, gibt **SQLFetchScroll** SQL_NO_DATA zurück.|  
|*CurrRowsetStart*|Die Nummer der ersten Zeile im aktuellen Rowset.|  
|*LastResultRow*|Die Nummer der letzten Zeile im Resultset.|  
|*RowsetSize*|Die Rowsetgröße.|  
|*FetchOffset*|Der Wert des *FetchOffset-Arguments.*|  
|*BookmarkRow*|Die Zeile, die der Textmarke entspricht, die durch das Attribut SQL_ATTR_FETCH_BOOKMARK_PTR angegeben wird.|  
  
## <a name="sql_fetch_next"></a>SQL_FETCH_NEXT  
 Es gelten die folgenden Regeln.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Vor dem Start*|1|  
|*CurrRowsetStart + RowsetSize*[1] * \<= LastResultRow*|*CurrRowsetStart + RowsetSize*[1]|  
|*CurrRowsetStart + RowsetSize*[1]*> LastResultRow*|*Nach dem Ende*|  
|*Nach dem Ende*|*Nach dem Ende*|  
  
 [1] Wenn die Rowsetgröße seit dem vorherigen Aufruf zum Abrufen von Zeilen geändert wurde, ist dies die Rowsetgröße, die beim vorherigen Aufruf verwendet wurde.  
  
## <a name="sql_fetch_prior"></a>SQL_FETCH_PRIOR  
 Es gelten die folgenden Regeln.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Vor dem Start*|*Vor dem Start*|  
|*CurrRowsetStart = 1*|*Vor dem Start*|  
|*1 < CurrRowsetStart <= RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*CurrRowsetStart > RowsetSize* <sup>[2]</sup>|*CurrRowsetStart - RowsetGröße* <sup>[2]</sup>|  
|*Nach Ende und LastResultRow < RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*Nach Ende UND LastResultRow >= RowsetSize* <sup>[2]</sup>|*LastResultRow - RowsetSize + 1* <sup>[2]</sup>|  
  
 [1] **SQLFetchScroll** gibt SQLSTATE 01S06 zurück (Versuch, abzurufen, bevor das Resultset das erste Rowset zurückgegeben hat) und SQL_SUCCESS_WITH_INFO.  
  
 [2] Wenn die Rowsetgröße seit dem vorherigen Aufruf zum Abrufen von Zeilen geändert wurde, ist dies die neue Rowsetgröße.  
  
## <a name="sql_fetch_relative"></a>SQL_FETCH_RELATIVE  
 Es gelten die folgenden Regeln.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*(Vor dem Start UND FetchOffset > 0) ODER (Nach dem Ende UND FetchOffset < 0)*|*--*<sup>[1]</sup>|  
|*BeforeStart UND FetchOffset <= 0*|*Vor dem Start*|  
|*CurrRowsetStart = 1 UND FetchOffset < 0*|*Vor dem Start*|  
|*CurrRowsetStart > 1 UND CurrRowsetStart + FetchOffset < 1 UND &#124; FetchOffset &#124; > RowsetSize* <sup>[3]</sup>|*Vor dem Start*|  
|*CurrRowsetStart > 1 UND CurrRowsetStart + FetchOffset < 1 UND &#124; FetchOffset &#124; <= RowsetSize* <sup>[3]</sup>|*1* <sup>[2]</sup>|  
|*1 <= CurrRowsetStart \<+ FetchOffset = LastResultRow*|*CurrRowsetStart + FetchOffset*|  
|*CurrRowsetStart + FetchOffset > LastResultRow*|*Nach dem Ende*|  
|*Nach dem Ende UND FetchOffset >= 0*|*Nach dem Ende*|  
  
 [1] ***SQLFetchScroll*** gibt dasselbe Rowset zurück, als ob es aufgerufen wurde, wenn FetchOrientation auf SQL_FETCH_ABSOLUTE festgelegt wurde. Weitere Informationen finden Sie im Abschnitt "SQL_FETCH_ABSOLUTE".  
  
 [2] **SQLFetchScroll** gibt SQLSTATE 01S06 zurück (Versuch, abzurufen, bevor das Resultset das erste Rowset zurückgibt) und SQL_SUCCESS_WITH_INFO.  
  
 [3] Wenn die Rowsetgröße seit dem vorherigen Aufruf zum Abrufen von Zeilen geändert wurde, ist dies die neue Rowsetgröße.  
  
## <a name="sql_fetch_absolute"></a>SQL_FETCH_ABSOLUTE  
 Es gelten die folgenden Regeln.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*FetchOffset < 0 UND &#124; FetchOffset &#124; <= LastResultRow*|*LastResultRow + FetchOffset + 1*|  
|*FetchOffset < 0 und &#124; FetchOffset &#124; > LastResultRow UND &#124; FetchOffset &#124; > RowsetSize* <sup>[2]</sup>|*Vor dem Start*|  
|*FetchOffset < 0 und &#124; FetchOffset &#124; > LastResultRow UND &#124; FetchOffset &#124; <= RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*FetchOffset = 0*|*Vor dem Start*|  
|*1 <= \<FetchOffset = LastResultRow*|*FetchOffset*|  
|*FetchOffset > LastResultRow*|*Nach dem Ende*|  
  
 [1] **SQLFetchScroll** gibt SQLSTATE 01S06 zurück (Versuch, abzurufen, bevor das Resultset das erste Rowset zurückgegeben hat) und SQL_SUCCESS_WITH_INFO.  
  
 [2] Wenn die Rowsetgröße seit dem vorherigen Aufruf zum Abrufen von Zeilen geändert wurde, ist dies die neue Rowsetgröße.  
  
 Ein absoluter Abruf, der für einen dynamischen Cursor ausgeführt wird, kann nicht das erforderliche Ergebnis liefern, da Zeilenpositionen in einem dynamischen Cursor nicht bestimmt sind. Eine solche Operation entspricht einem Abruf zuerst gefolgt von einem Abruf-Verwandten. es handelt sich nicht um einen atomaren Vorgang, sondern um einen absoluten Abruf auf einem statischen Cursor.  
  
## <a name="sql_fetch_first"></a>SQL_FETCH_FIRST  
 Es gelten die folgenden Regeln.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Alle*|*1*|  
  
## <a name="sql_fetch_last"></a>SQL_FETCH_LAST  
 Es gelten die folgenden Regeln.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*RowsetSize* <sup>[1]</sup> <= LastResultRow|*LastResultRow - RowsetSize + 1* <sup>[1]</sup>|  
|*RowsetSize* <sup>[1]</sup> > LastResultRow|*1*|  
  
 [1] Wenn die Rowsetgröße seit dem vorherigen Aufruf zum Abrufen von Zeilen geändert wurde, ist dies die neue Rowsetgröße.  
  
## <a name="sql_fetch_bookmark"></a>SQL_FETCH_BOOKMARK  
 Es gelten die folgenden Regeln.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*BookmarkRow + FetchOffset < 1*|*Vor dem Start*|  
|*1 <= BookmarkRow \<+ FetchOffset = LastResultRow*|*BookmarkRow + FetchOffset*|  
|*BookmarkRow + FetchOffset > LastResultRow*|*Nach dem Ende*|  
  
 Informationen zu Lesezeichen finden Sie unter [Lesezeichen (ODBC)](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
## <a name="effect-of-deleted-added-and-error-rows-on-cursor-movement"></a>Auswirkungen von gelöschten, hinzugefügten und fehlerhaften Zeilen auf die Cursorbewegung  
 Statische und Keyset-gesteuerte Cursor erkennen manchmal Zeilen, die dem Resultset hinzugefügt wurden, und entfernen Ausdematon gelöschte Zeilen aus dem Resultset. Durch Aufrufen von **SQLGetInfo** mit den Optionen SQL_STATIC_CURSOR_ATTRIBUTES2 und SQL_KEYSET_CURSOR_ATTRIBUTES2 und Betrachten der SQL_CA2_SENSITIVITY_ADDITIONS, SQL_CA2_SENSITIVITY_DELETIONS und SQL_CA2_SENSITIVITY_UPDATES Bitmasken bestimmt eine Anwendung, ob die von einem bestimmten Treiber implementierten Cursor dies tun. Für Treiber, die gelöschte Zeilen erkennen und entfernen können, beschreiben die folgenden Absätze die Auswirkungen dieses Verhaltens. Für Treiber, die gelöschte Zeilen erkennen, aber nicht entfernen können, haben Löschungen keine Auswirkungen auf Cursorbewegungen, und die folgenden Absätze gelten nicht.  
  
 Wenn der Cursor Zeilen erkennt, die dem Resultset hinzugefügt wurden, oder Zeilen entfernt, die aus dem Resultset gelöscht wurden, wird angezeigt, als ob er diese Änderungen nur erkennt, wenn daten abgerufen werden. Dies schließt den Fall ein, wenn SQLFetchScroll aufgerufen wird, wobei FetchOrientation auf SQL_FETCH_RELATIVE und FetchOffset auf 0 festgelegt ist, um dasselbe Rowset erneut abzurufen, aber nicht die Groß-/Kleinschreibung, wenn **SQLSetPos** aufgerufen wird und fOption auf SQL_REFRESH festgelegt ist. Im letzteren Fall werden die Daten in den Rowsetpuffern aktualisiert, aber nicht erneut abgerufen, und gelöschte Zeilen werden nicht aus dem Resultset entfernt. Wenn also eine Zeile aus dem aktuellen Rowset gelöscht oder in das aktuelle Rowset eingefügt wird, ändert der Cursor die Rowsetpuffer nicht. Stattdessen erkennt es die Änderung, wenn ein Rowset abgerufen wird, das zuvor die gelöschte Zeile oder jetzt die eingefügte Zeile enthält.  
  
 Beispiel:  
  
```cpp  
// Fetch the next rowset.  
SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
// Delete third row of the rowset. Does not modify the rowset buffers.  
SQLSetPos(hstmt, 3, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
// The third row has a status of SQL_ROW_DELETED after this call.  
SQLSetPos(hstmt, 3, SQL_REFRESH, SQL_LOCK_NO_CHANGE);  
// Refetch the same rowset. The third row is removed, replaced by what  
// was previously the fourth row.  
SQLFetchScroll(hstmt, SQL_FETCH_RELATIVE, 0);  
```  
  
 Wenn **SQLFetchScroll** ein neues Rowset zurückgibt, das eine Position relativ zum aktuellen Rowset hat , d. h. FetchOrientation ist SQL_FETCH_NEXT, SQL_FETCH_PRIOR oder SQL_FETCH_RELATIVE - enthält es keine Änderungen am aktuellen Rowset, wenn die Startposition des neuen Rowsets berechnet wird. Es enthält jedoch Änderungen außerhalb des aktuellen Rowsets, wenn es in der Lage ist, sie zu erkennen. Wenn SQLFetchScroll außerdem ein neues Rowset **zurückgibt,** das eine Position unabhängig vom aktuellen Rowset hat , d. h. FetchOrientation ist SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE oder SQL_FETCH_BOOKMARK - enthält es alle Änderungen, die es erkennen kann, auch wenn sie sich im aktuellen Rowset befinden.  
  
 Beim Bestimmen, ob sich neu hinzugefügte Zeilen innerhalb oder außerhalb des aktuellen Rowsets befinden, wird ein teiles Rowset als Endfolge der letzten gültigen Zeile betrachtet. Das heißt, die letzte Zeile, für die der Zeilenstatus nicht SQL_ROW_NOROW ist. Angenommen, der Cursor kann neu hinzugefügte Zeilen erkennen, das aktuelle Rowset ist ein partielles Rowset, die Anwendung fügt neue Zeilen hinzu, und der Cursor fügt diese Zeilen am Ende des Resultsets hinzu. Wenn die Anwendung **SQLFetchScroll** aufruft und FetchOrientation auf SQL_FETCH_NEXT festgelegt ist, gibt **SQLFetchScroll** das Rowset zurück, das mit der ersten neu hinzugefügten Zeile beginnt.  
  
 Angenommen, das aktuelle Rowset umfasst die Zeilen 21 bis 30, die Rowsetgröße 10, der Cursor entfernt aus dem Resultset gelöschte Zeilen und der Cursor erkennt Zeilen, die dem Resultset hinzugefügt wurden. Die folgende Tabelle zeigt die Zeilen, die SQLFetchScroll in verschiedenen Situationen **zurückgibt.**  
  
|Change|Abruftyp|FetchOffset|Neues Rowset[1]|  
|------------|----------------|-----------------|---------------------|  
|Zeile 21 löschen|NEXT|0|31 bis 40|  
|Zeile löschen 31|NEXT|0|32 bis 41|  
|Einfügen einer Zeile zwischen den Zeilen 21 und 22|NEXT|0|31 bis 40|  
|Einfügen einer Zeile zwischen den Zeilen 30 und 31|NEXT|0|Eingefügte Zeile, 31 bis 39|  
|Zeile 21 löschen|PRIOR|0|11 bis 20|  
|Zeile 20 löschen|PRIOR|0|10 bis 19|  
|Einfügen einer Zeile zwischen den Zeilen 21 und 22|PRIOR|0|11 bis 20|  
|Einfügen einer Zeile zwischen den Zeilen 20 und 21|PRIOR|0|12 bis 20, eingefügte Zeile|  
|Zeile 21 löschen|RELATIVE|0|22 bis 31<sup>[2]</sup>|  
|Zeile 21 löschen|RELATIVE|1|22 bis 31|  
|Einfügen einer Zeile zwischen den Zeilen 21 und 22|RELATIVE|0|21, eingelegte Reihe, 22 bis 29|  
|Einfügen einer Zeile zwischen den Zeilen 21 und 22|RELATIVE|1|22 bis 31|  
|Zeile 21 löschen|ABSOLUTE|21|22 bis 31<sup>[2]</sup>|  
|Zeile 22 löschen|ABSOLUTE|21|21, 23 bis 31|  
|Einfügen einer Zeile zwischen den Zeilen 21 und 22|ABSOLUTE|22|Eingefügte Zeile, 22 bis 29|  
  
 [1] Diese Spalte verwendet die Zeilennummern, bevor Zeilen eingefügt oder gelöscht wurden.  
  
 [2] In diesem Fall versucht der Cursor, Zeilen zurückzugeben, die mit Zeile 21 beginnen. Da Zeile 21 gelöscht wurde, ist die erste Zeile, die sie zurückgibt, Zeile 22.  
  
 Fehlerzeilen (d. h. Zeilen mit dem Status SQL_ROW_ERROR) wirken sich nicht auf die Cursorbewegung aus. Wenn z. B. das aktuelle Rowset mit Zeile 11 beginnt und der Status von Zeile 11 SQL_ROW_ERROR ist, gibt der Aufruf von **SQLFetchScroll** mit FetchOrientation auf SQL_FETCH_RELATIVE und FetchOffset auf 5 festgelegtes Rowset zurück, das mit Zeile 16 beginnt, so wie es wäre, wenn der Status für Zeile 11 SQL_SUCCESS wäre.  
  
## <a name="returning-data-in-bound-columns"></a>Zurückgeben von Daten in gebundenen Spalten  
 **SQLFetchScroll** gibt Daten in gebundenen Spalten auf die gleiche Weise wie **SQLFetch zurück.** Weitere Informationen finden Sie unter "Zurückgeben von Daten in gebundenen Spalten" in der [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Wenn keine Spalten gebunden sind, gibt **SQLFetchScroll** keine Daten zurück, verschiebt den Blockcursor jedoch an die angegebene Position. Ob Daten aus ungebundenen Spalten eines Blockcursors mit **SQLGetData** abgerufen werden können, hängt vom Treiber ab. Diese Funktion wird unterstützt, wenn ein Aufruf von **SQLGetInfo** das SQL_GD_BLOCK-Bit für den SQL_GETDATA_EXTENSIONS-Informationstyp zurückgibt.  
  
## <a name="buffer-addresses"></a>Pufferadressen  
 **SQLFetchScroll** verwendet dieselbe Formel, um die Adresse von Daten- und Längen-/Indikatorpuffern wie **SQLFetch**zu bestimmen. Weitere Informationen finden Sie unter "Pufferadressen" in [der SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="row-status-array"></a>Zeilenstatusarray  
 **SQLFetchScroll** legt Werte im Zeilenstatusarray auf die gleiche Weise wie SQLFetch fest. Weitere Informationen finden Sie unter "Zeilenstatusarray" in [der SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="rows-fetched-buffer"></a>Zeilen Abgerufener Puffer  
 **SQLFetchScroll** gibt die Anzahl der Zeilen zurück, die in den abgerufenen Zeilen auf die gleiche Weise wie **SQLFetch**abgerufen wurden. Weitere Informationen finden Sie unter "Zeilen abgerufener Puffer" in [der SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 Wenn eine Anwendung **SQLFetchScroll** in einem ODBC 3.x-Treiber aufruft, ruft der Treiber-Manager **SQLFetchScroll** im Treiber auf. Wenn eine Anwendung **SQLFetchScroll** in einem ODBC 2.x-Treiber aufruft, ruft der Treiber-Manager SQLExtendedFetch im Treiber auf. Da **SQLFetchScroll** und SQLExtendedFetch Fehler auf eine etwas andere Weise behandeln, sieht die Anwendung ein etwas anderes Fehlerverhalten, wenn sie **SQLFetchScroll** in ODBC 2.x- und ODBC 3.x-Treibern aufruft.  
  
 **SQLFetchScroll** gibt Fehler und Warnungen auf die gleiche Weise wie **SQLFetch**zurück. Weitere Informationen finden Sie unter "Fehlerbehandlung" in **SQLFetch**. **SQLExtendedFetch** gibt Fehler auf die gleiche Weise wie **SQLFetch**zurück, mit den folgenden Ausnahmen:  
  
 Wenn eine Warnung auftritt, die für eine bestimmte Zeile im Rowset gilt, legt SQLExtendedFetch den entsprechenden Eintrag im Zeilenstatusarray auf SQL_ROW_SUCCESS und nicht auf SQL_ROW_SUCCESS_WITH_INFO fest.  
  
 Wenn in jeder Zeile des Rowsets Fehler auftreten, gibt SQLExtendedFetch SQL_SUCCESS_WITH_INFO zurück, nicht SQL_ERROR.  
  
 In jeder Gruppe von Statusdatensätzen, die für eine einzelne Zeile gelten, muss der erste von SQLExtendedFetch zurückgegebene Statusdatensatz SQLSTATE 01S01 (Fehler in Zeile) enthalten. **SQLFetchScroll** gibt diesen SQLSTATE nicht zurück. Wenn SQLExtendedFetch keine zusätzlichen SQLSTATEs zurückgeben kann, muss es diesen SQLSTATE dennoch zurückgeben.  
  
## <a name="sqlfetchscroll-and-optimistic-concurrency"></a>SQLFetchScroll und optimistische Parallelität  
 Wenn ein Cursor eine optimistische Parallelität verwendet, d. h. das Attribut SQL_ATTR_CONCURRENCY Anweisung hat den Wert SQL_CONCUR_VALUES oder SQL_CONCUR_ROWVER - aktualisiert **SQLFetchScroll** die optimistischen Parallelitätswerte, die von der Datenquelle verwendet werden, um festzustellen, ob sich eine Zeile geändert hat. Dies geschieht immer dann, wenn **SQLFetchScroll** ein neues Rowset abruft, auch wenn das aktuelle Rowset erneut abgerufen wird. (Es wird aufgerufen, wobei FetchOrientation auf SQL_FETCH_RELATIVE und FetchOffset auf 0 gesetzt ist.)  
  
## <a name="sqlfetchscroll-and-odbc-2x-drivers"></a>SQLFetchScroll- und ODBC 2.x-Treiber  
 Wenn eine Anwendung **SQLFetchScroll** in einem ODBC 2.x-Treiber aufruft, ordnet der Treiber-Manager diesen Aufruf **SQLExtendedFetch**zu. Es übergibt die folgenden Werte für die Argumente von **SQLExtendedFetch**.  
  
|SQLExtendedFetch-Argument|Wert|  
|-------------------------------|-----------|  
|StatementHandle|StatementHandle in **SQLFetchScroll**.|  
|FetchOrientation|FetchOrientation in **SQLFetchScroll**.|  
|FetchOffset|Wenn FetchOrientation nicht SQL_FETCH_BOOKMARK ist, wird der Wert des FetchOffset-Arguments in **SQLFetchScroll** verwendet.<br /><br /> Wenn FetchOrientation SQL_FETCH_BOOKMARK ist, wird der Wert verwendet, der an der vom Attribut SQL_ATTR_FETCH_BOOKMARK_PTR -anweisung angegebenen Adresse gespeichert ist.|  
|RowCountPtr|Die vom SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut angegebene Adresse.|  
|RowStatusArray|Die vom SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut angegebene Adresse.|  
  
 Weitere Informationen finden Sie unter [Blockcursors, Scrollable Cursors und Backward Compatibility](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.  
  
## <a name="descriptors-and-sqlfetchscroll"></a>Deskriptoren und SQLFetchScroll  
 **SQLFetchScroll** interagiert mit Deskriptoren auf die gleiche Weise wie **SQLFetch**. Weitere Informationen finden Sie im Abschnitt "Deskriptoren und SQLFetchScroll" in [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [Column-Wise Binding](../../../odbc/reference/develop-app/column-wise-binding.md), [Row-Wise Binding](../../../odbc/reference/develop-app/row-wise-binding.md), Position Update and Delete [Statements](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md), and Updating Rows in [the Rowset with SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Masseneinfüge-, Aktualisierungs- oder Löschvorgängen|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einer Ergebnismenge|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in einer vorwärtsgerichteten Richtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Schließen des Cursors für die Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Zurückgeben der Anzahl der Ergebnissatzspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset oder Aktualisieren oder Löschen von Daten im Resultset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Festlegen eines Anweisungsattributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
