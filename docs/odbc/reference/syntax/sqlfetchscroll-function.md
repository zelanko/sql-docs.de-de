---
title: SQLFetchScroll-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fb75ebceb1f70ddc8b517a3dc94af97a18965939
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345194"
---
# <a name="sqlfetchscroll-function"></a>SQLFetchScroll-Funktion
**Konformitäts**  
 Eingeführte Version: Konformität der ODBC 3,0-Standards: ISO 92  
  
 **Zusammenfassung**  
 **SQLFetchScroll** Ruft das angegebene Rowset von Daten aus dem Resultset ab und gibt Daten für alle gebundenen Spalten zurück. Rowsets können an einer absoluten oder relativen Position oder durch ein Lesezeichen angegeben werden.  
  
 Beim Arbeiten mit einem ODBC 2. x-Treiber ordnet der Treiber-Manager diese Funktion **sqlextendecodfetch**zu. Weitere Informationen finden Sie unter [Mapping Replace Functions for abwärts Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFetchScroll(  
      SQLHSTMT      StatementHandle,  
      SQLSMALLINT   FetchOrientation,  
      SQLLEN        FetchOffset);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *FetchOrientation*  
 Der  
  
 Art des Abruf Vorgangs:  
  
 SQL_FETCH_NEXT  
  
 SQL_FETCH_PRIOR  
  
 SQL_FETCH_FIRST  
  
 SQL_FETCH_LAST  
  
 SQL_FETCH_ABSOLUTE  
  
 SQL_FETCH_RELATIVE  
  
 SQL_FETCH_BOOKMARK  
  
 Weitere Informationen finden Sie unter "Positionieren des Cursors" im Abschnitt "comments".  
  
 *FetchOffset*  
 Der  
  
 Die Nummer der abzurufenden Zeile. Die Interpretation dieses Arguments hängt vom Wert des *FetchOrientation* -Arguments ab. Weitere Informationen finden Sie unter "Positionieren des Cursors" im Abschnitt "comments".  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFetchScroll** entweder "SQL_ERROR" oder "SQL_SUCCESS_WITH_INFO" zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem Typ "SQL_HANDLE_STMT" und einem Handle von "StatementHandle" abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die häufig von **SQLFetchScroll** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, lautet SQL_ERROR, sofern nichts anderes angegeben ist. Wenn ein Fehler in einer einzelnen Spalte auftritt, kann **SQLGetDiagField** mit einem DiagIdentifier von SQL_DIAG_COLUMN_NUMBER aufgerufen werden, um die Spalte zu bestimmen, in der der Fehler aufgetreten ist. und **SQLGetDiagField** können mit einem DiagIdentifier von SQL_DIAG_ROW_NUMBER aufgerufen werden, um die Zeile zu ermitteln, die diese Spalte enthält.  
  
 Für alle Sqlstates, die SQL_SUCCESS_WITH_INFO oder SQL_ERROR (außer 01xxx Sqlstates) zurückgeben können, wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn ein Fehler in einer oder mehreren, aber nicht in allen Zeilen eines mehr Zeilen Vorgangs auftritt, und SQL_ERROR zurückgegeben wird, wenn ein Fehler in einem Einzel Zeilen Vorgang.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Zeichen folgen-oder Binärdaten, die für eine Spalte zurückgegeben wurden, ergaben das Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind. Wenn es sich um einen Zeichen folgen Wert handelt, wurde er rechts abgeschnitten.|  
|01S01|Fehler in Zeile|Fehler beim Abrufen einer oder mehrerer Zeilen.<br /><br /> (Wenn dieser SQLSTATE zurückgegeben wird, wenn eine ODBC 3 *. x* -Anwendung mit einem ODBC 2 *. x* -Treiber arbeitet, kann er ignoriert werden.)|  
|01S06|Es wurde versucht, abzurufen, bevor das Resultset das erste Rowset zurückgegeben hat|Das angeforderte Rowset hat den Anfang des Resultsets überschritten, als "FetchOrientation" SQL_FETCH_PRIOR war, die aktuelle Position war außerhalb der ersten Zeile, und die Nummer der aktuellen Zeile ist kleiner oder gleich der Rowsetgröße.<br /><br /> Das angeforderte Rowset hat den Anfang des Resultsets überschritten, als "FetchOrientation" SQL_FETCH_PRIOR war, die aktuelle Position lag hinter dem Ende des Resultsets, und die Rowsetgröße war größer als die Größe des Resultsets.<br /><br /> Das angeforderte Rowset hat den Anfang des Resultsets überschritten, als "FetchOrientation" SQL_FETCH_RELATIVE, "FetchOffset" negativ war und der absolute Wert von "FetchOffset" kleiner oder gleich der Rowsetgröße war.<br /><br /> Das angeforderte Rowset hat den Anfang des Resultsets überschritten, als "FetchOrientation" SQL_FETCH_ABSOLUTE, "FetchOffset" negativ war und der absolute Wert von "FetchOffset" größer als die resultsetgröße, aber kleiner oder gleich der Rowsetgröße war.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Abschneiden von Sekundenbruchteilen|Die für eine Spalte zurückgegebenen Daten wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteile der Zahl abgeschnitten. Bei Zeit-, Zeitstempel-und Intervall Datentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|Der Datenwert einer Spalte im Resultset konnte nicht in den Datentyp konvertiert werden, der von *TargetType* in **SQLBindCol**festgelegt wurde.<br /><br /> Die Spalte 0 wurde mit dem Datentyp SQL_C_BOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut wurde auf SQL_UB_VARIABLE festgelegt.<br /><br /> Die Spalte 0 wurde mit dem Datentyp SQL_C_VARBOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut wurde nicht auf SQL_UB_VARIABLE festgelegt.|  
|07009|Ungültiger deskriptorindex.|Der Treiber war ein ODBC 2 *. x* -Treiber, der **SQLExtendedFetch**nicht unterstützt, und eine in der Bindung für eine Spalte angegebene Spaltennummer war 0.<br /><br /> Die Spalte 0 wurde gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut wurde auf SQL_UB_OFF festgelegt.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|22001|Zeichen folgen Daten, rechts abgeschnitten|Ein Lesezeichen variabler Länge, das für eine Spalte zurückgegeben wurde, wurde abgeschnitten.|  
|22002|Die Indikator Variable ist erforderlich, aber nicht angegeben.|NULL-Daten wurden in eine Spalte abgerufen, deren *StrLen_or_IndPtr* von **SQLBindCol** (oder SQL_DESC_INDICATOR_PTR festgelegt von **SQLSetDescField** oder **SQLSetDescRec**) ein NULL-Zeiger war.|  
|22003|Numerischer Wert außerhalb des zulässigen Bereichs|Das Zurückgeben des numerischen Werts (als numerisch oder Zeichenfolge) für eine oder mehrere gebundene Spalten hätte dazu geführt, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wird.<br /><br /> Weitere Informationen finden Sie unter "Daten [Typen aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) " in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Ungültiges datetime-Format.|Eine Zeichenspalte im Resultset wurde an eine Datums-, Uhrzeit-oder Zeitstempel-C-Struktur gebunden, und ein Wert in der Spalte war, bzw. ein ungültiges Datum, eine Uhrzeit oder ein ungültiger Zeitstempel.|  
|22012|Division durch Null|Es wurde ein Wert aus einem arithmetischen Ausdruck zurückgegeben, der zu einer Division durch 0 geführt hat.|  
|22015|Überlauf des Intervall Felds|Das Zuweisen eines exakten numerischen oder Interval-SQL-Typs zu einem Interval-C-Typ verursachte den Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Beim Abrufen von Daten in einen Interval-c-Typ gab es keine Darstellung des Werts des SQL-Typs im Interval-c-Typ.|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|Eine Zeichenspalte im Resultset wurde an einen C-Zeichen Puffer gebunden, und die Spalte enthielt ein Zeichen, für das es keine Darstellung im Zeichensatz des Puffers gab.<br /><br /> Der C-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der SQL-Typ der Spalte war ein Zeichen Datentyp. und der Wert in der Spalte war kein gültiges Literale des gebundenen C-Typs.|  
|24000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.|  
|40001|Serialisierungsfehler|Die Transaktion, in der der Abruf ausgeführt wurde, wurde beendet, um einen Deadlock zu verhindern.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im  *\*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLFetchScroll** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und hat SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) das angegebene *StatementHandle* war nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute** oder eine Katalog Funktion aufzurufen.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) **SQLFetch** wurde für das *StatementHandle* aufgerufen, nachdem **SQLExtendedFetch** aufgerufen wurde und bevor **SQLFreeStmt** mit der SQL_CLOSE-Option aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|Das SQL_ATTR_USE_BOOKMARK-Anweisungs Attribut wurde auf SQL_UB_VARIABLE festgelegt, und die Spalte 0 wurde an einen Puffer gebunden, dessen Länge nicht der maximalen Länge für das Lesezeichen für dieses Resultset entspricht. (Diese Länge ist im SQL_DESC_OCTET_LENGTH-Feld von IRD verfügbar und kann durch Aufrufen von **SQLDescribeCol**, **SQLColAttribute**oder **SQLGetDescField**abgerufen werden.)|  
|HY106|FETCH-Typ außerhalb des gültigen Bereichs|DM) der für das Argument "FetchOrientation" angegebene Wert ist ungültig.<br /><br /> (DM) das Argument FetchOrientation lautete SQL_FETCH_BOOKMARK, und das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut wurde auf SQL_UB_OFF festgelegt.<br /><br /> Der Wert des SQL_ATTR_CURSOR_TYPE-Anweisungs Attributs war SQL_CURSOR_FORWARD_ONLY, und der Wert von Argument FetchOrientation war nicht SQL_FETCH_NEXT.<br /><br /> Der Wert des SQL_ATTR_CURSOR_SCROLLABLE-Anweisungs Attributs war SQL_NONSCROLLABLE, und der Wert von Argument FetchOrientation war nicht SQL_FETCH_NEXT.|  
|HY107|Zeilen Wert außerhalb des zulässigen Bereichs|Der mit dem SQL_ATTR_CURSOR_TYPE-Anweisungs Attribut angegebene Wert war SQL_CURSOR_KEYSET_DRIVEN, aber der mit dem SQL_ATTR_KEYSET_SIZE-Anweisungs Attribut angegebene Wert war größer als 0 und kleiner als der mit SQL_ATTR_ROW_ARRAY_ angegebene Wert. Size-Anweisungs Attribut.|  
|HY111|Ungültiger Lesezeichen Wert|Das Argument FetchOrientation war SQL_FETCH_BOOKMARK, und das Lesezeichen, auf das der Wert im SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungs Attribut verweist, war ungültig oder war ein NULL-Zeiger.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Der Treiber oder die Datenquelle unterstützt nicht die Konvertierung, die durch die Kombination von *TargetType* in **SQLBindCol** und dem SQL-Datentyp der entsprechenden Spalte angegeben wird.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von SQLSetStmtAttr, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLFetchScroll** gibt ein angegebenes Rowset aus dem Resultset zurück. Rowsets können durch absolute oder relative Position oder durch Lesezeichen angegeben werden. **SQLFetchScroll** kann nur aufgerufen werden, wenn ein Resultset vorhanden ist, d. h. nach einem Aufruf, der ein Resultset erstellt und vor dem Cursor über diesem Resultset geschlossen wird. Wenn Spalten gebunden sind, werden die Daten in diesen Spalten zurückgegeben. Wenn die Anwendung einen Zeiger auf ein Zeilen Status Array oder einen Puffer angegeben hat, in dem die Anzahl der abgerufenen Zeilen zurückgegeben werden soll, gibt **SQLFetchScroll** diese Informationen ebenfalls zurück. Aufrufe von **SQLFetchScroll** können mit Aufrufen von **SQLFetch** gemischt, jedoch nicht mit Aufrufen von **SQLExtendedFetch**gemischt werden.  
  
 Weitere Informationen finden Sie unter [verwenden](../../../odbc/reference/develop-app/using-block-cursors.md) von Blockcursorn und [Verwenden von scrollfähigen](../../../odbc/reference/develop-app/using-scrollable-cursors.md)Cursorn.  
  
## <a name="positioning-the-cursor"></a>Positionieren des Cursors  
 Wenn das Resultset erstellt wird, wird der Cursor vor dem Anfang des Resultsets positioniert. **SQLFetchScroll** positioniert den Block Cursor basierend auf den Werten der Argumente " *FetchOrientation* " und " *FetchOffset* ", wie in der folgenden Tabelle gezeigt. Die genauen Regeln zum Bestimmen des Starts des neuen Rowsets werden im nächsten Abschnitt angezeigt.  
  
|FetchOrientation|Bedeutung|  
|----------------------|-------------|  
|SQL_FETCH_NEXT|Gibt das nächste Rowset zurück. Dies entspricht dem Aufrufen von **SQLFetch**.<br /><br /> **SQLFetchScroll** ignoriert den Wert von *FetchOffset*.|  
|SQL_FETCH_PRIOR|Gibt das vorherige Rowset zurück.<br /><br /> **SQLFetchScroll** ignoriert den Wert von *FetchOffset*.|  
|SQL_FETCH_RELATIVE|Gibt das Rowset- *FetchOffset* vom Beginn des aktuellen Rowsets zurück.|  
|SQL_FETCH_ABSOLUTE|Gibt das Rowset zurück, beginnend bei der Zeile *FetchOffset*.|  
|SQL_FETCH_FIRST|Gibt das erste Rowset im Resultset zurück.<br /><br /> **SQLFetchScroll** ignoriert den Wert von *FetchOffset*.|  
|SQL_FETCH_LAST|Gibt das letzte komplette Rowset im Resultset zurück.<br /><br /> **SQLFetchScroll** ignoriert den Wert von *FetchOffset*.|  
|SQL_FETCH_BOOKMARK|Rückgabe der Rowset-FetchOffset-Zeilen aus dem Lesezeichen, das durch das SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungs Attribut angegeben wird|  
  
 Treiber sind nicht erforderlich, um alle Abruf Ausrichtungen zu unterstützen. eine Anwendung ruft **SQLGetInfo** mit dem Informationstyp SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 (abhängig vom Typ des Cursors) auf, um zu bestimmen, welche Abruf Ausrichtungen wird vom Treiber unterstützt. Die Anwendung sollte die Bitmasken SQL_CA1_NEXT, SQL_CA1_RELATIVE, SQL_CA1_ABSOLUTE und WQL_CA1_BOOKMARK in diesen Informationstypen sehen. Außerdem gibt **SQLFetchScroll** SQLSTATE HY106 (fetch-Typ außerhalb des gültigen Bereichs) zurück, wenn der Cursor vorwärts ist und FetchOrientation nicht SQL_FETCH_NEXT ist.  
  
 Das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungs Attribut gibt die Anzahl der Zeilen im Rowset an. Wenn das Rowset, das von **SQLFetchScroll** abgerufen wird, das Ende des Resultsets überlappt, gibt **SQLFetchScroll** ein partielles Rowset zurück. Das heißt, wenn s + R-1 größer als L ist, wobei s die Anfangs Zeile des abgerufenen Rowsets ist, R die Rowsetgröße und L die letzte Zeile im Resultset ist, dann sind nur die ersten L-S + 1 Zeilen des Rowsets gültig. Die verbleibenden Zeilen sind leer und weisen den Status SQL_ROW_NOROW auf.  
  
 Nach der Rückgabe von **SQLFetchScroll** ist die aktuelle Zeile die erste Zeile des Rowsets.  
  
## <a name="cursor-positioning-rules"></a>Cursor Positionierungs Regeln  
 In den folgenden Abschnitten werden die genauen Regeln für die einzelnen Werte von FetchOrientation beschrieben. Diese Regeln verwenden die folgende Notation.  
  
|Notation|Bedeutung|  
|--------------|-------------|  
|*Vor dem Start*|Der Block Cursor befindet sich vor dem Anfang des Resultsets. Wenn sich die erste Zeile des neuen Rowsets vor dem Anfang des Resultsets befindet, gibt **SQLFetchScroll** SQL_NO_DATA zurück.|  
|*Nach dem Ende*|Der Block Cursor befindet sich hinter dem Ende des Resultsets. Wenn sich die erste Zeile des neuen Rowsets hinter das Ende des Resultsets befindet, gibt **SQLFetchScroll** SQL_NO_DATA zurück.|  
|*CurrRowsetStart*|Die Nummer der ersten Zeile im aktuellen Rowset.|  
|*Lastresultrow*|Die Nummer der letzten Zeile im Resultset.|  
|*Rowsetsize*|Die Rowsetgröße.|  
|*FetchOffset*|Der Wert des *FetchOffset* -Arguments.|  
|*Bookmarkrow*|Die Zeile, die dem Lesezeichen entspricht, das vom SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungs Attribut angegeben wird.|  
  
## <a name="sqlfetchnext"></a>SQL_FETCH_NEXT  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Vor dem Start*|1|  
|*Currrowsetstart + rowsetsize* [1]  *\<= lastresultrow*|*Currrowsetstart + rowsetsize* 1|  
|*Currrowsetstart + rowsetsize* 1 *> Lastresultrow*|*Nach dem Ende*|  
|*Nach dem Ende*|*Nach dem Ende*|  
  
 [1] Wenn die Rowsetgröße seit dem vorherigen Abruf von Zeilen abgerufen wurde, handelt es sich hierbei um die Rowsetgröße, die mit dem vorherigen-Befehl verwendet wurde.  
  
## <a name="sqlfetchprior"></a>SQL_FETCH_PRIOR  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Vor dem Start*|*Vor dem Start*|  
|*CurrRowsetStart = 1*|*Vor dem Start*|  
|*1 < currrowsetstart < = rowsetsize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*Currrowsetstart > rowsetsize* <sup>[2]</sup>|*Currrowsetstart-rowsetsize* <sup>[2]</sup>|  
|*Nach Ende und lastresultrow < rowsetsize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*Nach Ende und lastresultrow > = rowsetsize* <sup>[2]</sup>|*Lastresultrow-rowsetsize + 1* <sup>[2]</sup>|  
  
 [1] **SQLFetchScroll** gibt SQLSTATE 01s06 zurück (der Versuch, den Abruf Vorgang durchzuführen, bevor das Resultset das erste Rowset zurückgegeben hat) und SQL_SUCCESS_WITH_INFO.  
  
 [2] Wenn die Rowsetgröße seit dem vorherigen Abruf von Zeilen abgerufen wurde, ist dies die neue Rowsetgröße.  
  
## <a name="sqlfetchrelative"></a>SQL_FETCH_RELATIVE  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*(Vor Start und FetchOffset > 0) Oder (nach Ende und FetchOffset < 0)*|*--* <sup>[1]</sup>|  
|*Beforestart und FetchOffset < = 0*|*Vor dem Start*|  
|*Currrowsetstart = 1 und FetchOffset < 0*|*Vor dem Start*|  
|*Currrowsetstart > 1 und currrowsetstart + FetchOffset < 1 und &#124; FetchOffset &#124; > rowsetsize* <sup>[3]</sup>|*Vor dem Start*|  
|*Currrowsetstart > 1 und currrowsetstart + FetchOffset < 1 und &#124; FetchOffset &#124; < = rowsetsize* <sup>[3]</sup>|*1* <sup>[2]</sup>|  
|*1 < = currrowsetstart + FetchOffset \<= lastresultrow*|*Currrowsetstart + FetchOffset*|  
|*Currrowsetstart + FetchOffset > lastresultrow*|*Nach dem Ende*|  
|*Nach Ende und FetchOffset > = 0*|*Nach dem Ende*|  
  
 [1] ***SQLFetchScroll*** gibt dasselbe Rowset zurück, als wenn es mit "FetchOrientation" auf "SQL_FETCH_ABSOLUTE" festgelegt wurde. Weitere Informationen finden Sie im Abschnitt "SQL_FETCH_ABSOLUTE".  
  
 [2] **SQLFetchScroll** gibt SQLSTATE 01s06 zurück (der Versuch, den Abruf Vorgang durchzuführen, bevor das Resultset das erste Rowset zurückgegeben hat) und SQL_SUCCESS_WITH_INFO.  
  
 [3] Wenn die Rowsetgröße seit dem vorherigen Abruf von Zeilen abgerufen wurde, ist dies die neue Rowsetgröße.  
  
## <a name="sqlfetchabsolute"></a>SQL_FETCH_ABSOLUTE  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*FetchOffset < 0 und &#124; FetchOffset &#124; < = lastresultrow*|*Lastresultrow + FetchOffset + 1*|  
|*FetchOffset < 0 und &#124; FetchOffset &#124; > lastresultrow und &#124; FetchOffset &#124; > rowsetsize* <sup>[2]</sup>|*Vor dem Start*|  
|*FetchOffset < 0 und &#124; FetchOffset &#124; > lastresultrow und &#124; FetchOffset &#124; < = rowsetsize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*FetchOffset = 0*|*Vor dem Start*|  
|*1 < = FetchOffset \<= lastresultrow*|*FetchOffset*|  
|*FetchOffset > lastresultrow*|*Nach dem Ende*|  
  
 [1] **SQLFetchScroll** gibt SQLSTATE 01s06 zurück (der Versuch, den Abruf Vorgang durchzuführen, bevor das Resultset das erste Rowset zurückgegeben hat) und SQL_SUCCESS_WITH_INFO.  
  
 [2] Wenn die Rowsetgröße seit dem vorherigen Abruf von Zeilen abgerufen wurde, ist dies die neue Rowsetgröße.  
  
 Ein absoluter Abruf Vorgang, der für einen dynamischen Cursor ausgeführt wird, kann das erforderliche Ergebnis nicht bereitstellen, da Zeilen Positionen in einem dynamischen Cursor nicht bestimmt werden. Ein solcher Vorgang entspricht einem Abruf Vorgang, gefolgt von einem relativen Abruf Vorgang. Es handelt sich nicht um eine atomarische Operation, da es sich um einen absoluten Abruf Vorgang für einen statischen Cursor handelt.  
  
## <a name="sqlfetchfirst"></a>SQL_FETCH_FIRST  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Irgendeiner*|*1*|  
  
## <a name="sqlfetchlast"></a>SQL_FETCH_LAST  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Rowsetsize* <sup>[1]</sup> < = lastresultrow|*Lastresultrow-rowsetsize + 1* <sup>[1]</sup>|  
|*Rowsetsize* <sup>[1]</sup> > lastresultrow|*1*|  
  
 [1] Wenn die Rowsetgröße seit dem vorherigen Abruf von Zeilen abgerufen wurde, handelt es sich hierbei um die neue Rowsetgröße.  
  
## <a name="sqlfetchbookmark"></a>SQL_FETCH_BOOKMARK  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Bookmarkrow + FetchOffset < 1*|*Vor dem Start*|  
|*1 < = bookmarkrow + FetchOffset \<= lastresultrow*|*Bookmarkrow und FetchOffset*|  
|*Bookmarkrow + FetchOffset > lastresultrow*|*Nach dem Ende*|  
  
 Weitere Informationen zu Lesezeichen finden Sie unter [Lesezeichen (ODBC)](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
## <a name="effect-of-deleted-added-and-error-rows-on-cursor-movement"></a>Auswirkungen von gelöschten, hinzugefügten und Fehler Zeilen bei der Cursor Bewegung  
 Statische und keysetgesteuerte Cursor erkennen manchmal Zeilen, die dem Resultset hinzugefügt wurden, und entfernen Zeilen, die aus dem Resultset gelöscht wurden. Durch Aufrufen von **SQLGetInfo** mit den Optionen SQL_STATIC_CURSOR_ATTRIBUTES2 und SQL_KEYSET_CURSOR_ATTRIBUTES2 und untersuchen der Bitmasks SQL_CA2_SENSITIVITY_ADDITIONS, SQL_CA2_SENSITIVITY_DELETIONS und SQL_CA2_SENSITIVITY_UPDATES, eine die Anwendung bestimmt, ob die von einem bestimmten Treiber implementierten Cursor dies tun. Für Treiber, die gelöschte Zeilen erkennen und entfernen können, werden die Auswirkungen dieses Verhaltens in den folgenden Abschnitten beschrieben. Für Treiber, die gelöschte Zeilen erkennen, aber nicht entfernen können, haben Löschungen keine Auswirkung auf Cursor Bewegungen, und die folgenden Absätze sind nicht anwendbar.  
  
 Wenn der Cursor die dem Resultset hinzugefügten Zeilen erkennt oder aus dem Resultset gelöschte Zeilen entfernt, wird er so angezeigt, als ob diese Änderungen nur beim Abrufen von Daten erkannt werden. Dies gilt auch für den Fall, dass **SQLFetchScroll** aufgerufen wird, wobei "FetchOrientation" auf "SQL_FETCH_RELATIVE" und "FetchOffset" auf 0 festgelegt ist, um das gleiche Rowset erneut abzurufen, aber nicht die Groß-/Kleinschreibung, in der SQLSetPos aufgerufen wird, wobei fOption auf SQL_REFRESH Im letzteren Fall werden die Daten in den rowsetpuffern aktualisiert, aber nicht erneut abgerufen, und gelöschte Zeilen werden nicht aus dem Resultset entfernt. Wenn eine Zeile aus dem aktuellen Rowset gelöscht oder in das aktuelle Rowset eingefügt wird, werden die rowsetpuffer vom Cursor nicht geändert. Stattdessen wird die Änderung erkannt, wenn ein Rowset abgerufen wird, das zuvor die gelöschte Zeile enthielt oder nun die eingefügte Zeile enthält.  
  
 Zum Beispiel:  
  
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
  
 Wenn **SQLFetchScroll** ein neues Rowset zurückgibt, das eine Position relativ zum aktuellen Rowset hat, d. h. FetchOrientation ist SQL_FETCH_NEXT, SQL_FETCH_PRIOR oder SQL_FETCH_RELATIVE, enthält es beim Berechnen von keine Änderungen am aktuellen Rowset. die Anfangsposition des neuen Rowsets. Sie enthält jedoch Änderungen außerhalb des aktuellen Rowsets, wenn Sie in der Lage sind, Sie zu erkennen. Wenn **SQLFetchScroll** ein neues Rowset zurückgibt, das über eine vom aktuellen Rowset unabhängige Position verfügt, d. h. FetchOrientation ist SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE oder SQL_FETCH_BOOKMARK, enthält es alle Änderungen, die es enthält. kann erkennen, auch wenn Sie sich im aktuellen Rowset befinden.  
  
 Wenn Sie bestimmen, ob sich neu hinzugefügte Zeilen innerhalb oder außerhalb des aktuellen Rowsets befinden, wird ein partielles Rowset als Ende der letzten gültigen Zeile betrachtet. Das heißt, die letzte Zeile, für die der Zeilen Status nicht SQL_ROW_NOROW lautet. Angenommen, der Cursor kann neu hinzugefügte Zeilen erkennen, das aktuelle Rowset ist ein partielles Rowset, die Anwendung fügt neue Zeilen hinzu, und der Cursor fügt diese Zeilen am Ende des Resultsets hinzu. Wenn die Anwendung **SQLFetchScroll** aufruft, bei der FetchOrientation auf SQL_FETCH_NEXT festgelegt ist, gibt **SQLFetchScroll** das Rowset zurück, beginnend mit der ersten neu hinzugefügten Zeile.  
  
 Angenommen, das aktuelle Rowset besteht aus den Zeilen 21 bis 30, die Rowsetgröße ist 10, der Cursor entfernt aus dem Resultset gelöschte Zeilen und erkennt die dem Resultset hinzugefügten Zeilen. In der folgenden Tabelle werden die Zeilen angezeigt, die **SQLFetchScroll** in verschiedenen Situationen zurückgibt.  
  
|Ändern|FETCH-Typ|FetchOffset|Neues Rowset [1]|  
|------------|----------------|-----------------|---------------------|  
|Zeile 21 löschen|NEXT|0|31 bis 40|  
|Zeile 31 löschen|NEXT|0|32 bis 41|  
|Zeile zwischen den Zeilen 21 und 22 einfügen|NEXT|0|31 bis 40|  
|Zeile zwischen den Zeilen 30 und 31 einfügen|NEXT|0|Eingefügte Zeile, 31 bis 39|  
|Zeile 21 löschen|PRIOR|0|11 bis 20|  
|Zeile 20 löschen|PRIOR|0|10 bis 19|  
|Zeile zwischen den Zeilen 21 und 22 einfügen|PRIOR|0|11 bis 20|  
|Zeile zwischen den Zeilen 20 und 21 einfügen|PRIOR|0|12 bis 20, eingefügte Zeile|  
|Zeile 21 löschen|RELATIVE|0|22 bis 31<sup>[2]</sup>|  
|Zeile 21 löschen|RELATIVE|1|22 bis 31|  
|Zeile zwischen den Zeilen 21 und 22 einfügen|RELATIVE|0|21, Zeile eingefügt, 22 bis 29|  
|Zeile zwischen den Zeilen 21 und 22 einfügen|RELATIVE|1|22 bis 31|  
|Zeile 21 löschen|ABSOLUTE|21|22 bis 31<sup>[2]</sup>|  
|Zeile löschen 22|ABSOLUTE|21|21, 23 bis 31|  
|Zeile zwischen den Zeilen 21 und 22 einfügen|ABSOLUTE|22|Eingefügte Zeile, 22 bis 29|  
  
 [1] Diese Spalte verwendet die Zeilennummern, bevor Zeilen eingefügt oder gelöscht wurden.  
  
 [2] in diesem Fall versucht der Cursor, Zeilen zurückzugeben, die mit Zeile 21 beginnen. Da Zeile 21 gelöscht wurde, handelt es sich bei der ersten zurückgegebenen Zeile um Zeile 22.  
  
 Fehler Zeilen (d. h. Zeilen mit dem Status SQL_ROW_ERROR) haben keine Auswirkung auf die Cursor Bewegung. Wenn z. b. das aktuelle Rowset mit Zeile 11 beginnt und der Status von Zeile 11 SQL_ROW_ERROR ist, wird beim Aufrufen von **SQLFetchScroll** mit FetchOrientation auf SQL_FETCH_RELATIVE und bei Festlegung von FetchOffset auf 5 das Rowset zurückgegeben, das mit Zeile 16 beginnt, genauso wie bei der der Status für Zeile 11 lautete SQL_SUCCESS.  
  
## <a name="returning-data-in-bound-columns"></a>Zurückgeben von Daten in gebundenen Spalten  
 **SQLFetchScroll** gibt Daten in gebundenen Spalten auf dieselbe Weise zurück wie **SQLFetch**. Weitere Informationen finden Sie unter "zurückgeben von Daten in gebundenen Spalten" in der [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Wenn keine Spalten gebunden sind, gibt **SQLFetchScroll** keine Daten zurück, sondern verschiebt den Block Cursor an die angegebene Position. Ob Daten aus ungebundenen Spalten eines Block Cursors mit **SQLGetData** abgerufen werden können, hängt vom Treiber ab. Diese Funktion wird unterstützt, wenn ein- **Befehl von SQLGetInfo** das SQL_GD_BLOCK-Bit für den SQL_GETDATA_EXTENSIONS-Informationstyp zurückgibt.  
  
## <a name="buffer-addresses"></a>Puffer Adressen  
 **SQLFetchScroll** verwendet dieselbe Formel, um die Adresse der Daten-und Längen-/Indikatorpuffer als **SQLFetch**zu ermitteln. Weitere Informationen finden Sie unter "Puffer Adressen" in der [SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="row-status-array"></a>Zeilenstatusarray  
 **SQLFetchScroll** legt Werte im Zeilen Status Array auf die gleiche Weise wie SQLFetch fest. Weitere Informationen finden Sie unter "Row Status Array" in der [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="rows-fetched-buffer"></a>Abgerufene Zeilen Puffer  
 **SQLFetchScroll** gibt die Anzahl der Zeilen zurück, die in dem abgerufenen Zeilen Puffer auf die gleiche Weise wie **SQLFetch**abgerufen wurden. Weitere Informationen finden Sie unter "Zeilen abgerufene Puffer" in der [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 Wenn eine Anwendung **SQLFetchScroll** in einem ODBC 3. x-Treiber aufruft, ruft der Treiber-Manager **SQLFetchScroll** im Treiber auf. Wenn eine Anwendung **SQLFetchScroll** in einem ODBC 2. x-Treiber aufruft, ruft der Treiber-Manager SQLExtendedFetch im Treiber auf. Da **SQLFetchScroll** und SQLExtendedFetch Fehler auf etwas andere Weise behandeln, sieht die Anwendung etwas anderes Fehler Verhalten, wenn **SQLFetchScroll** in ODBC 2. x-und ODBC 3. x-Treibern aufgerufen wird.  
  
 **SQLFetchScroll** gibt Fehler und Warnungen auf die gleiche Weise zurück wie **SQLFetch**; Weitere Informationen finden Sie unter "Fehlerbehandlung" in **SQLFetch**. **SQLExtendedFetch** gibt Fehler auf die gleiche Weise wie **SQLFetch**zurück, mit den folgenden Ausnahmen:  
  
 Wenn eine Warnung auftritt, die für eine bestimmte Zeile im Rowset gilt, legt SQLExtendedFetch den entsprechenden Eintrag im Zeilen Status Array auf SQL_ROW_SUCCESS und nicht auf SQL_ROW_SUCCESS_WITH_INFO fest.  
  
 Wenn Fehler in jeder Zeile im Rowset auftreten, gibt SQLExtendedFetch SQL_SUCCESS_WITH_INFO und nicht SQL_ERROR zurück.  
  
 In jeder Gruppe von Statusdaten Sätzen, die für eine einzelne Zeile gilt, muss der erste von SQLExtendedFetch zurückgegebene Statusdaten Satz SQLSTATE 01s01 (Fehler in Zeile) enthalten. **SQLFetchScroll** gibt diesen SQLSTATE nicht zurück. Wenn sqlextendebug keine zusätzlichen Sqlstates zurückgeben kann, muss dieser SQLSTATE weiterhin zurückgegeben werden.  
  
## <a name="sqlfetchscroll-and-optimistic-concurrency"></a>SQLFetchScroll und optimistische Parallelität  
 Wenn ein Cursor vollständige Parallelität verwendet, d. h., das SQL_ATTR_CONCURRENCY-Anweisungs Attribut hat den Wert SQL_CONCUR_VALUES oder SQL_CONCUR_ROWVER- **SQLFetchScroll** aktualisiert die vollständigen Parallelitäts Werte, die von der Datenquelle verwendet werden, um zu erkennen, ob eine Zeile wurde geändert. Dies geschieht, wenn **SQLFetchScroll** ein neues Rowset abruft, auch wenn das aktuelle Rowset wiederholt wird. (Es wird aufgerufen, wenn "FetchOrientation" auf "SQL_FETCH_RELATIVE" und "FetchOffset" auf 0 festgelegt ist.)  
  
## <a name="sqlfetchscroll-and-odbc-2x-drivers"></a>SQLFetchScroll-und ODBC 2. x-Treiber  
 Wenn eine Anwendung **SQLFetchScroll** in einem ODBC 2. x-Treiber aufruft, ordnet der Treiber-Manager diesen Aufruf **SQLExtendedFetch**zu. Sie übergibt die folgenden Werte für die Argumente von **sqlextendecodfetch**.  
  
|Sqlextendebug-Argument|Wert|  
|-------------------------------|-----------|  
|StatementHandle|StatementHandle in **SQLFetchScroll**.|  
|FetchOrientation|FetchOrientation in **SQLFetchScroll**.|  
|FetchOffset|Wenn FetchOrientation nicht SQL_FETCH_BOOKMARK ist, wird der Wert des FetchOffset-Arguments in **SQLFetchScroll** verwendet.<br /><br /> Wenn FetchOrientation auf SQL_FETCH_BOOKMARK festgelegt ist, wird der Wert verwendet, der an der durch das SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungs Attribut angegebenen Adresse gespeichert wird.|  
|RowCountPtr|Die durch das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungs Attribut angegebene Adresse.|  
|RowStatusArray|Die durch das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut angegebene Adresse.|  
  
 Weitere Informationen finden Sie unter [Blockieren von Cursorn, scrollfähigen Cursorn und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiber Richtlinien für die Abwärtskompatibilität.  
  
## <a name="descriptors-and-sqlfetchscroll"></a>Deskriptoren und SQLFetchScroll  
 **SQLFetchScroll** interagiert mit Deskriptoren auf die gleiche Weise wie **SQLFetch**. Weitere Informationen finden Sie im Abschnitt "Deskriptoren und SQLFetchScroll" in der [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Weitere Informationen finden Sie unter [spaltenweise Bindung](../../../odbc/reference/develop-app/column-wise-binding.md), [Zeilen weises binden](../../../odbc/reference/develop-app/row-wise-binding.md), [positionierte UPDATE-und DELETE-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)und [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von BULK INSERT-, Update-oder DELETE-Vorgängen|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Schließen des Cursors in der Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Zurückgeben der Anzahl von Resultsetspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset oder aktualisieren oder Löschen von Daten im Resultset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Festlegen eines Anweisungs Attributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
