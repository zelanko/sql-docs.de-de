---
title: SQLSetPos-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetPos
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetPos
helpviewer_keywords:
- SQLSetPos function [ODBC]
ms.assetid: 80190ee7-ae3b-45e5-92a9-693eb558f322
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 80f14b99d2c7dac91116186fdcf53ff77ee6c2c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68343073"
---
# <a name="sqlsetpos-function"></a>SQLSetPos-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLSetPos** legt die Cursorposition in einem Rowset fest und ermöglicht es einer Anwendung, Daten im Rowset zu aktualisieren oder Daten im Resultset zu aktualisieren oder zu löschen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetPos(  
      SQLHSTMT        StatementHandle,  
      SQLSETPOSIROW   RowNumber,  
      SQLUSMALLINT    Operation,  
      SQLUSMALLINT    LockType);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *RowNumber*  
 Der Die Position der Zeile im Rowset, für die der mit dem *Vorgangs* Argument angegebene Vorgang durchgeführt werden soll. Wenn *RowNumber* 0 ist, gilt der Vorgang für jede Zeile im Rowset.  
  
 Weitere Informationen finden Sie unter "comments".  
  
 *Vorgang*  
 Der Auszuführenden Vorgang:  
  
 SQL_POSITION SQL_REFRESH SQL_UPDATE SQL_DELETE  
  
> [!NOTE]
>  Der SQL_ADD Wert für das *Vorgangs* Argument wurde für ODBC *3. x*als veraltet markiert. ODBC *3. x* -Treiber müssen SQL_ADD aus Gründen der Abwärtskompatibilität unterstützen. Diese Funktion wurde durch einen **SQLBulkOperations** -Vorgang durch einen SQL_ADD *Vorgang* ersetzt. Wenn eine ODBC *3. x* -Anwendung mit einem ODBC *2. x* -Treiber verwendet wird, ordnet der Treiber-Manager **SQLBulkOperations einen SQLBulkOperations** - *Vorgang* mit einem Vorgang SQL_ADD zu **SQLSetPos** mit einem SQL_ADD *Vorgang* zu.  
  
 Weitere Informationen finden Sie unter "comments".  
  
 *LockType*  
 Der Gibt an, wie die Zeile gesperrt wird, nachdem der im *Vorgangs* Argument angegebene Vorgang durchgeführt wurde.  
  
 SQL_LOCK_NO_CHANGE SQL_LOCK_EXCLUSIVE SQL_LOCK_UNLOCK  
  
 Weitere Informationen finden Sie unter "comments".  
  
 **Rückgabe**  
  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetPos** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLSetPos** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
 Für alle Sqlstates-Werte, die SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgeben können (außer 01xxx Sqlstates), wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn ein Fehler in einer oder mehreren, aber nicht in allen Zeilen eines mehr Zeilen Vorgangs auftritt, und SQL_ERROR zurückgegeben, wenn ein Fehler in einem Einzel Zeilen Vorgang.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01001|Konflikt beim Cursor Vorgang|Das *Vorgangs* Argument wurde SQL_DELETE oder SQL_UPDATE, und es wurden keine Zeilen oder mehr als eine Zeile gelöscht oder aktualisiert. (Weitere Informationen zu Updates für mehr als eine Zeile finden Sie in der Beschreibung des SQL_ATTR_SIMULATE_CURSOR- *Attributs* in **SQLSetStmtAttr**.) (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> Das *Vorgangs* Argument war SQL_DELETE oder SQL_UPDATE, und der Vorgang konnte aufgrund der vollständigen Parallelität nicht ausgeführt werden. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Abkürzen von Zeichen folgen Daten|Das *Vorgangs* Argument wurde SQL_REFRESH, und Zeichen folgen-oder Binärdaten, die für eine Spalte oder Spalten mit dem Datentyp SQL_C_CHAR oder SQL_C_BINARY zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind.|  
|01s01|Fehler in Zeile|Das *RowNumber* -Argument war 0, und in einer oder mehreren Zeilen ist ein Fehler aufgetreten, während der mit dem *Vorgangs* Argument angegebene Vorgang durchgeführt wurde.<br /><br /> (SQL_SUCCESS_WITH_INFO wird zurückgegeben, wenn ein Fehler in einer oder mehreren Zeilen, jedoch nicht in allen Zeilen eines mehr Zeilen Vorgangs auftritt, und SQL_ERROR zurückgegeben wird, wenn ein Fehler bei einem einzeiligen Vorgang auftritt.)<br /><br /> (Dieser SQLSTATE wird nur zurückgegeben, wenn **SQLSetPos** nach **SQLExtendedFetch**aufgerufen wird, wenn es sich bei dem Treiber um einen ODBC *2. x* -Treiber handelt und die Cursor Bibliothek nicht verwendet wird.)|  
|01S07|Abschneiden von Sekundenbruchteilen|Das *Vorgangs* Argument wurde SQL_REFRESH, der Datentyp des Anwendungs Puffers wurde nicht SQL_C_CHAR oder SQL_C_BINARY, und die Daten, die an Anwendungs Puffer für eine oder mehrere Spalten zurückgegeben wurden, wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteile der Zahl abgeschnitten. Bei Zeit-, Zeitstempel-und Intervall Datentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|Der Datenwert einer Spalte im Resultset konnte nicht in den Datentyp konvertiert werden, der von *TargetType* beim Aufrufen von **SQLBindCol**angegeben wurde.|  
|07009|Ungültiger deskriptorindex.|Der Argument *Vorgang* war SQL_REFRESH oder SQL_UPDATE, und eine Spalte wurde mit einer Spaltennummer gebunden, die größer als die Anzahl der Spalten im Resultset ist.|  
|21s02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein.|Der Argument *Vorgang* wurde SQL_UPDATE, und es wurden keine Spalten aktualisiert, da alle Spalten entweder ungebunden, schreibgeschützt oder der Wert im gebundenen Längen-/Indikatorpuffer SQL_COLUMN_IGNORE wurden.|  
|22001|Zeichen folgen Daten, rechter Abschneiden|Das *Vorgangs* Argument wurde SQL_UPDATE, und die Zuweisung eines Zeichens oder Binärwerts zu einer Spalte führte zum Abschneiden von nicht leeren (für Zeichen) oder nicht-NULL-Zeichen (für Binär Zeichen) oder Bytes.|  
|22003|Numerischer Wert außerhalb des zulässigen Bereichs|Der Argument *Vorgang* wurde SQL_UPDATE, und die Zuweisung eines numerischen Werts zu einer Spalte im Resultset führte dazu, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wurde.<br /><br /> Der Argument *Vorgang* wurde SQL_REFRESH, und das Zurückgeben des numerischen Werts für eine oder mehrere gebundene Spalten hätte zu einem Verlust signifikanter Ziffern geführt.|  
|22007|Ungültiges datetime-Format.|Der Argument *Vorgang* wurde SQL_UPDATE, und die Zuweisung eines Datums-oder Zeitstempel-Werts zu einer Spalte im Resultset hat bewirkt, dass das Feld "Year", "Month" oder "Day" außerhalb des gültigen Bereichs liegt.<br /><br /> Der Argument *Vorgang* wurde SQL_REFRESH, und das Zurückgeben des Datums-oder Zeitstempel-Werts für eine oder mehrere gebundene Spalten hätte dazu geführt, dass das Feld "Year", "Month" oder "Day" außerhalb des gültigen Bereichs liegt.|  
|22008|Überlauf bei Datum/Uhrzeit-Feld|Das *Vorgangs* Argument wurde SQL_UPDATE, und die Leistung von DateTime-Arithmetik für Daten, die an eine Spalte im Resultset gesendet werden, führte zu einem DateTime-Feld (Jahr, Monat, Tag, Stunde, Minute oder zweites Feld), das sich außerhalb des zulässigen Bereichs von Werten für das Feld befindet oder aufgrund der natürlichen Regeln des gregorianischen Kalenders für DateTime ungültig ist<br /><br /> Das *Vorgangs* Argument wurde SQL_REFRESH, und die Leistung der DateTime-Arithmetik für Daten, die aus dem Resultset abgerufen werden, führte zu einem DateTime-Feld (Jahr, Monat, Tag, Stunde, Minute oder zweites Feld), das sich außerhalb des zulässigen Wertebereichs für das Feld befindet, oder auf der Grundlage der natürlichen Regeln des gregorianischen Kalenders für datetimes.|  
|22015|Überlauf des Intervall Felds|Das *Vorgangs* Argument wurde SQL_UPDATE, und die Zuweisung eines exakten numerischen oder Interval C-Typs zu einem Interval-SQL-Datentyp verursachte einen Verlust signifikanter Ziffern.<br /><br /> Das *Vorgangs* Argument wurde SQL_UPDATE. bei der Zuweisung zu einem Interval-SQL-Typ gab es keine Darstellung des Werts des C-Typs im Intervall-SQL-Typ.<br /><br /> Das *Vorgangs* Argument wurde SQL_REFRESH, und das Zuweisen von einem exakten numerischen oder Interval-SQL-Typ zu einem Interval-C-Typ verursachte einen Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Das *Vorgangs* Argument wurde SQL_ Refresh. bei der Zuweisung zu einem Interval-c-Typ gab es keine Darstellung des Werts des SQL-Typs im Interval-c-Typ.|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|Das *Vorgangs* Argument wurde SQL_REFRESH. der C-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der SQL-Typ der Spalte war ein Zeichen Datentyp. und der Wert in der Spalte war kein gültiges Literale des gebundenen C-Typs.<br /><br /> Der Argument *Vorgang* war SQL_UPDATE. der SQL-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der C-Typ war SQL_C_CHAR. und der Wert in der Spalte war kein gültiges Literale des gebundenen SQL-Typs.|  
|23000|Verletzung der Integritäts Einschränkung|Der Argument *Vorgang* war SQL_DELETE oder SQL_UPDATE, und eine Integritäts Einschränkung wurde verletzt.|  
|24.000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.<br /><br /> (DM) ein Cursor war auf dem *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.<br /><br /> Ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen, aber der Cursor befand sich vor dem Anfang des Resultsets oder nach dem Ende des Resultsets.<br /><br /> Der Argument *Vorgang* war SQL_DELETE, SQL_REFRESH oder SQL_UPDATE, und der Cursor befand sich vor dem Anfang des Resultsets oder nach dem Ende des Resultsets.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde aufgrund eines Ressourcen Deadlocks mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntax Fehler oder Zugriffsverletzung|Der Treiber konnte die Zeile nicht nach Bedarf sperren, um den im Argument *Vorgang*angeforderten Vorgang auszuführen.<br /><br /> Der Treiber konnte die Zeile nicht wie im Argument *LockType*angefordert sperren.|  
|44000|WITH CHECK OPTION-Verstoß|Das *Vorgangs* Argument wurde SQL_UPDATE, und das Update wurde für eine angezeigte Tabelle oder eine Tabelle ausgeführt, die von der angezeigten Tabelle abgeleitet wurde, die durch die Angabe von **with Check Option**erstellt wurde, sodass mindestens eine von der Aktualisierung betroffene Zeile nicht mehr in der angezeigten Tabelle enthalten ist.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen, und anschließend wurde die Funktion für " *StatementHandle*" erneut aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die SQLSetPos-Funktion aufgerufen wurde.<br /><br /> (DM) das angegebene *StatementHandle* war nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute**oder eine Katalog Funktion aufzurufen.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) der Treiber war ein ODBC *2. x* -Treiber, und **SQLSetPos** wurde für ein *StatementHandle* aufgerufen, nachdem **SQLFetch** aufgerufen wurde.|  
|HY011|Das Attribut kann jetzt nicht festgelegt werden|(DM) der Treiber war ein ODBC *2. x* -Treiber. Das SQL_ATTR_ROW_STATUS_PTR Anweisungs Attribut wurde festgelegt. Anschließend wurde **SQLSetPos** aufgerufen, bevor **SQLFetch**, **SQLFetchScroll**oder **sqlextendebug** aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|Das *Vorgangs* Argument wurde SQL_UPDATE, ein Datenwert war ein NULL-Zeiger, und der Spalten Längen Wert war nicht 0, SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NULL_DATA oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Das *Vorgangs* Argument wurde SQL_UPDATE. ein Datenwert war kein NULL-Zeiger. der C-Datentyp war SQL_C_BINARY oder SQL_C_CHAR. und der Spalten Längen Wert war kleiner als 0 (null), aber nicht gleich SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS oder SQL_NULL_DATA oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Der Wert in einem Längen-/Indikatorpuffer wurde SQL_DATA_AT_EXEC. der SQL-Typ war entweder SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer Datenquellen spezifischer Datentyp. und der SQL_NEED_LONG_DATA_LEN Informationstyp in **SQLGetInfo** lautete "Y".|  
|HY092|Ungültiger Attribut Bezeichner|(DM) der für das *Vorgangs* Argument angegebene Wert ist ungültig.<br /><br /> (DM) der Wert, der für das *LockType* -Argument angegeben wurde, war ungültig.<br /><br /> Das *Vorgangs* Argument war SQL_UPDATE oder SQL_DELETE, und das Attribut der SQL_ATTR_CONCURRENCY-Anweisung war SQL_ATTR_CONCUR_READ_ONLY.|  
|HY107|Zeilen Wert außerhalb des zulässigen Bereichs|Der für die Argument- *RowNumber* angegebene Wert ist größer als die Anzahl der Zeilen im Rowset.|  
|HY109|Ungültige Cursorposition|Der dem *StatementHandle* zugeordnete Cursor wurde als Vorwärts Cursor definiert, sodass der Cursor nicht innerhalb des Rowsets positioniert werden konnte. Weitere Informationen finden Sie in der Beschreibung für das SQL_ATTR_CURSOR_TYPE-Attribut in **SQLSetStmtAttr**.<br /><br /> Das *Vorgangs* Argument war SQL_UPDATE, SQL_DELETE oder SQL_REFRESH, und die durch das *RowNumber* -Argument identifizierte Zeile wurde gelöscht oder nicht abgerufen.<br /><br /> (DM) das *RowNumber* -Argument war 0, und das *Vorgangs* Argument wurde SQL_POSITION.<br /><br /> **SQLSetPos** wurde aufgerufen, nachdem **SQLBulkOperations** aufgerufen und vor dem Aufruf von **SQLFetchScroll** oder **SQLFetch** aufgerufen wurde.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Der Treiber oder die Datenquelle unterstützt nicht den Vorgang, der im *Vorgangs* Argument oder im *LockType* -Argument angefordert wurde.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird über **SQLSetStmtAttr** mit dem *Attribut* SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
  
> [!CAUTION]
>  Informationen zur-Anweisung, in der **SQLSetPos** aufgerufen werden kann, und zu deren Kompatibilität mit ODBC *2. x* -Anwendungen erforderlich ist, finden Sie unter [Block Cursor, scrollbare Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md).  
  
## <a name="rownumber-argument"></a>RowNumber-Argument  
 Das *RowNumber* -Argument gibt die Nummer der Zeile im Rowset an, für die der vom *Vorgangs* Argument angegebene Vorgang durchgeführt werden soll. Wenn *RowNumber* 0 ist, gilt der Vorgang für jede Zeile im Rowset. *RowNumber* muss ein Wert zwischen 0 und der Anzahl der Zeilen im Rowset sein.  
  
> [!NOTE]  
>  In der Programmiersprache C sind Arrays 0-basiert, und das *RowNumber* -Argument ist 1-basiert. Zum Aktualisieren der fünften Zeile des Rowsets ändert eine Anwendung z. b. die rowsetpuffer am Array Index 4, gibt jedoch eine *RowNumber* von 5 an.  
  
 Alle Vorgänge positionieren den Cursor in der Zeile, die durch *RowNumber*angegeben wird. Die folgenden Vorgänge erfordern eine Cursorposition:  
  
-   Positionierte UPDATE-und DELETE-Anweisungen.  
  
-   Aufrufe von **SQLGetData**.  
  
-   Aufrufe von **SQLSetPos** mit den Optionen SQL_DELETE, SQL_REFRESH und SQL_UPDATE.  
  
 Wenn z. b. *RowNumber* für einen-Befehl von **SQLSetPos** bei einem *Vorgang* von SQL_DELETE den Wert 2 hat, wird der Cursor in der zweiten Zeile des Rowsets positioniert und diese Zeile gelöscht. Der Eintrag im Array der Implementierungs Zeilen Status (auf das durch das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut verwiesen wird) für die zweite Zeile wird in SQL_ROW_DELETED geändert.  
  
 Eine Anwendung kann eine Cursorposition angeben, wenn Sie **SQLSetPos**aufruft. Im allgemeinen ruft Sie **SQLSetPos** mit dem SQL_POSITION oder SQL_REFRESH Vorgang auf, um den Cursor vor dem Ausführen einer positionierten Update-oder DELETE-Anweisung oder des Aufrufs von **SQLGetData**zu positionieren.  
  
## <a name="operation-argument"></a>Vorgangs Argument  
 Das *Vorgangs* Argument unterstützt die folgenden Vorgänge. Um zu ermitteln, welche Optionen von einer Datenquelle unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 Informationstyp (abhängig vom Cursortyp) auf.  
  
|*Vorgang*<br /><br /> Argument|Vorgang|  
|------------------------------|---------------|  
|SQL_POSITION|Der Treiber positioniert den Cursor in der Zeile, die durch *RowNumber*angegeben wird.<br /><br /> Der Inhalt des Zeilen Status Arrays, auf das durch das SQL_ATTR_ROW_OPERATION_PTR Statement-Attribut verwiesen wird, wird für den SQL_POSITION *Vorgang*ignoriert.|  
|SQL_REFRESH|Der Treiber positioniert den Cursor in der Zeile, die durch *RowNumber* angegeben wird, und aktualisiert die Daten in den rowsetpuffern für diese Zeile. Weitere Informationen dazu, wie der Treiber Daten in den rowsetpuffern zurückgibt, finden Sie in den Beschreibungen der Zeilen weisen und der Spalten bezogenen Bindung in **SQLBindCol**.<br /><br /> **SQLSetPos** mit einem *Vorgang* von SQL_REFRESH aktualisiert den Status und den Inhalt der Zeilen innerhalb des aktuellen abgerufenen Rowsets. Dies schließt das Aktualisieren der Lesezeichen ein. Da die Daten in den Puffern aktualisiert, aber nicht erneut abgerufen werden, wird die Mitgliedschaft im Rowset korrigiert. Dies unterscheidet sich von der Aktualisierung, die durch einen **SQLFetchScroll** -Befehl mit der *FetchOrientation* -SQL_FETCH_RELATIVE und einer *RowNumber* gleich 0 durchgeführt wird. Dadurch wird das Rowset aus dem Resultset wiederholt, sodass es hinzugefügte Daten anzeigen und gelöschte Daten entfernen kann, wenn diese Vorgänge vom Treiber und dem Cursor unterstützt werden.<br /><br /> Bei einer erfolgreichen Aktualisierung mit **SQLSetPos** wird der Zeilen Status SQL_ROW_DELETED nicht geändert. Gelöschte Zeilen im Rowset werden bis zum nächsten Abruf Vorgang weiterhin als gelöscht markiert. Die Zeilen werden beim nächsten Abruf Vorgang nicht mehr angezeigt, wenn der Cursor das Verpacken unterstützt (in dem eine nachfolgende **SQLFetch** -oder **SQLFetchScroll** -Abfrage keine gelöschten Zeilen zurückgibt).<br /><br /> Hinzugefügte Zeilen werden nicht angezeigt, wenn eine Aktualisierung mit **SQLSetPos** ausgeführt wird. Dieses Verhalten unterscheidet sich von **SQLFetchScroll** durch einen *FetchType* von SQL_FETCH_RELATIVE und eine *RowNumber* gleich 0, wodurch auch das aktuelle Rowset aktualisiert wird, aber es werden hinzugefügte Datensätze angezeigt, oder es werden Datensätze gelöscht, wenn diese Vorgänge vom Cursor unterstützt werden.<br /><br /> Bei einer erfolgreichen Aktualisierung mit **SQLSetPos** wird der Zeilen Status SQL_ROW_ADDED in SQL_ROW_SUCCESS geändert (wenn das Zeilen Status Array vorhanden ist).<br /><br /> Bei einer erfolgreichen Aktualisierung mit **SQLSetPos** wird der Zeilen Status SQL_ROW_UPDATED in den neuen Status der Zeile geändert (wenn das Zeilen Status Array vorhanden ist).<br /><br /> Wenn bei einem **SQLSetPos** -Vorgang in einer Zeile ein Fehler auftritt, wird der Zeilen Status auf SQL_ROW_ERROR festgelegt (wenn das Zeilen Status Array vorhanden ist).<br /><br /> Bei einem Cursor, der mit einem SQL_ATTR_CONCURRENCY-Anweisungs Attribut SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES geöffnet wird, kann eine Aktualisierung mit **SQLSetPos** die Werte der vollständigen Parallelität aktualisieren, die von der Datenquelle verwendet werden, um zu erkennen, dass die Zeile geändert wurde. Wenn dies der Fall ist, werden die Zeilen Versionen oder Werte, die zum Sicherstellen der Cursor Parallelität verwendet werden, immer dann aktualisiert, wenn die rowsetpuffer vom Server aktualisiert werden. Dies geschieht für jede Zeile, die aktualisiert wird.<br /><br /> Der Inhalt des Zeilen Status Arrays, auf das durch das SQL_ATTR_ROW_OPERATION_PTR Statement-Attribut verwiesen wird, wird für den SQL_REFRESH *Vorgang*ignoriert.|  
|SQL_UPDATE|Der Treiber positioniert den Cursor in der Zeile, die durch *RowNumber* angegeben wird, und aktualisiert die zugrunde liegende Daten Zeile mit den Werten in den rowsetpuffern (das *targetvalueptr* -Argument in **SQLBindCol**). Er ruft die Längen der Daten aus den Längen-/indikatorenpuffern (das *StrLen_or_IndPtr* Argument in **SQLBindCol**) ab. Wenn die Länge einer Spalte SQL_COLUMN_IGNORE ist, wird die Spalte nicht aktualisiert. Nach dem Aktualisieren der Zeile ändert der Treiber das entsprechende Element des Zeilen Status Arrays in SQL_ROW_UPDATED oder SQL_ROW_SUCCESS_WITH_INFO (wenn das Zeilen Status Array vorhanden ist).<br /><br /> Der Treiber definiert das Verhalten, wenn **SQLSetPos** mit einem *Vorgangs* Argument von SQL_UPDATE für einen Cursor aufgerufen wird, der doppelte Spalten enthält. Der Treiber kann einen Treiber definierten SQLSTATE zurückgeben, kann die erste Spalte aktualisieren, die im Resultset angezeigt wird, oder ein anderes Treiber definiertes Verhalten ausführen.<br /><br /> Das Zeilen Vorgangs Array, auf das das SQL_ATTR_ROW_OPERATION_PTR Statement-Attribut verweist, kann verwendet werden, um anzugeben, dass eine Zeile im aktuellen Rowset während einer Massen Aktualisierung ignoriert werden soll. Weitere Informationen finden Sie unter "Status-und Vorgangs Arrays" weiter unten in dieser Funktionsreferenz.|  
|SQL_DELETE|Der Treiber positioniert den Cursor in der durch *RowNumber* angegebenen Zeile und löscht die zugrunde liegende Daten Zeile. Das entsprechende Element des Rows-Status Arrays wird in SQL_ROW_DELETED geändert. Nachdem die Zeile gelöscht wurde, sind die folgenden Zeilen für die Zeile ungültig: positionierte UPDATE-und DELETE-Anweisungen, Aufrufe von **SQLGetData**und Aufrufe von **SQLSetPos** , bei denen der *Vorgang* auf alles außer SQL_POSITION festgelegt ist. Für Treiber, die das Verpacken unterstützen, wird die Zeile aus dem Cursor gelöscht, wenn neue Daten aus der Datenquelle abgerufen werden.<br /><br /> Ob die Zeile sichtbar bleibt, hängt vom Cursortyp ab. Beispielsweise sind gelöschte Zeilen für statische und keysetgesteuerte Cursor sichtbar, sind jedoch für dynamische Cursor unsichtbar.<br /><br /> Das Zeilen Vorgangs Array, auf das das SQL_ATTR_ROW_OPERATION_PTR Statement-Attribut verweist, kann verwendet werden, um anzugeben, dass eine Zeile im aktuellen Rowset während einer Massen Löschung ignoriert werden soll. Weitere Informationen finden Sie unter "Status-und Vorgangs Arrays" weiter unten in dieser Funktionsreferenz.|  
  
## <a name="locktype-argument"></a>LockType-Argument  
 Das *LockType* -Argument bietet Anwendungen die Möglichkeit, Parallelität zu steuern. In den meisten Fällen unterstützen Datenquellen, von denen Parallelitäts Stufen und Transaktionen unterstützt werden, nur den SQL_LOCK_NO_CHANGE Wert des *LockType* -Arguments. Das *LockType* -Argument wird im Allgemeinen nur für dateibasierte Unterstützung verwendet.  
  
 Das *LockType* -Argument gibt den Sperr Status der Zeile nach dem Ausführen von **SQLSetPos** an. Wenn der Treiber die Zeile nicht sperren kann, um den angeforderten Vorgang auszuführen oder das *LockType* -Argument zu erfüllen, wird SQL_ERROR und SQLSTATE 42000 (Syntax Fehler oder Zugriffsverletzung) zurückgegeben.  
  
 Obwohl das *LockType* -Argument für eine einzelne Anweisung angegeben wird, weist die Sperre allen Anweisungen für die Verbindung dieselben Berechtigungen zu. Vor allem kann eine Sperre, die von einer Anweisung für eine Verbindung abgerufen wird, durch eine andere Anweisung für dieselbe Verbindung entsperrt werden.  
  
 Eine Zeile, die über **SQLSetPos** gesperrt ist, bleibt gesperrt, bis die Anwendung **SQLSetPos** für die Zeile aufruft, bei der der *LockType* auf SQL_LOCK_UNLOCK festgelegt ist, oder bis die Anwendung **SQLFreeHandle** für die-Anweisung oder **SQLFreeStmt** mit der SQL_CLOSE-Option aufruft. Bei einem Treiber, der Transaktionen unterstützt, wird eine Zeile, die über **SQLSetPos** gesperrt ist, entsperrt, wenn die Anwendung **SQLEndTran** aufruft, um einen Commit oder Rollback für eine Transaktion auf der Verbindung auszuführen (wenn ein Cursor beim Commit oder Rollback einer Transaktion geschlossen wird, wie in den von **SQLGetInfo**zurückgegebenen SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR.  
  
 Das *LockType* -Argument unterstützt die folgenden Arten von Sperren. Um zu ermitteln, welche Sperren von einer Datenquelle unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem Datentyp SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 (abhängig vom Cursor) auf.  
  
|*LockType* -Argument|Sperrtyp|  
|-------------------------|---------------|  
|SQL_LOCK_NO_CHANGE|Der Treiber oder die Datenquelle stellt sicher, dass sich die Zeile in demselben gesperrten oder ungesperrten Zustand befindet wie vor dem Aufruf von **SQLSetPos** . Dieser Wert von *LockType* ermöglicht es Datenquellen, die explizite Sperren auf Zeilenebene nicht unterstützen, die für die aktuelle Parallelität und Transaktions Isolations Stufen erforderliche Sperre zu verwenden.|  
|SQL_LOCK_EXCLUSIVE|Der Treiber oder die Datenquelle sperrt die Zeile exklusiv. Eine-Anweisung in einer anderen Verbindung oder in einer anderen Anwendung kann nicht zum Abrufen von Sperren in der Zeile verwendet werden.|  
|SQL_LOCK_UNLOCK|Der Treiber oder die Datenquelle entsperrt die Zeile.|  
  
 Wenn ein Treiber SQL_LOCK_EXCLUSIVE unterstützt, aber SQL_LOCK_UNLOCK nicht unterstützt, bleibt eine gesperrte Zeile gesperrt, bis einer der im vorherigen Absatz beschriebenen Funktionsaufrufe auftritt.  
  
 Wenn ein Treiber SQL_LOCK_EXCLUSIVE unterstützt, aber SQL_LOCK_UNLOCK nicht unterstützt, bleibt eine gesperrte Zeile gesperrt, bis die Anwendung **SQLFreeHandle** für die-Anweisung oder **SQLFreeStmt** mit der SQL_CLOSE-Option aufruft. Wenn der Treiber Transaktionen unterstützt und den Cursor nach dem Commit oder Rollback der Transaktion schließt, ruft die Anwendung **SQLEndTran**auf.  
  
 Für die Aktualisierungs-und Löschvorgänge in **SQLSetPos**verwendet die Anwendung das *LockType* -Argument wie folgt:  
  
-   Um sicherzustellen, dass eine Zeile nach dem Abrufen nicht geändert wird, ruft eine Anwendung **SQLSetPos** auf, wobei *Operation* auf SQL_REFRESH und *LockType* auf SQL_LOCK_EXCLUSIVE festgelegt ist.  
  
-   Wenn die Anwendung *LockType* auf SQL_LOCK_NO_CHANGE festlegt, gewährleistet der Treiber, dass ein Update-oder DELETE-Vorgang nur erfolgreich ist, wenn die Anwendung SQL_CONCUR_LOCK für das SQL_ATTR_CONCURRENCY Statement-Attribut angegeben wurde.  
  
-   Wenn die Anwendung SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES für das SQL_ATTR_CONCURRENCY-Anweisungs Attribut angibt, vergleicht der Treiber die Zeilen Versionen oder-Werte und lehnt den Vorgang ab, wenn die Zeile geändert wurde, seit die Anwendung die Zeile abgerufen hat.  
  
-   Wenn die Anwendung SQL_CONCUR_READ_ONLY für das SQL_ATTR_CONCURRENCY Statement-Attribut angibt, lehnt der Treiber jeden Update-oder DELETE-Vorgang ab.  
  
 Weitere Informationen zum SQL_ATTR_CONCURRENCY-Anweisungs Attribut finden Sie unter [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="status-and-operation-arrays"></a>Status-und Vorgangs Arrays  
 Die folgenden Status-und Vorgangs Arrays werden beim Aufrufen von **SQLSetPos**verwendet:  
  
-   Das Zeilen Status Array (wie das SQL_DESC_ARRAY_STATUS_PTR-Feld im IRD und das SQL_ATTR_ROW_STATUS_ARRAY Statement-Attribut zeigt) enthält Statuswerte für jede Daten Zeile im Rowset. Der Treiber legt die Statuswerte in diesem Array nach einem Aufrufen von **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**oder **SQLSetPos**fest. Auf dieses Array wird durch das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut verwiesen.  
  
-   Das Zeilen Vorgangs Array (wie auf das SQL_DESC_ARRAY_STATUS_PTR-Feld in der ARD und das SQL_ATTR_ROW_OPERATION_ARRAY Statement-Attribut gezeigt) enthält einen Wert für jede Zeile im Rowset, die angibt, ob ein **SQLSetPos** -Aufrufvorgang für einen Massen Vorgang ignoriert oder ausgeführt wird. Jedes Element im Array wird entweder auf SQL_ROW_PROCEED (Standard) oder SQL_ROW_IGNORE festgelegt. Auf dieses Array wird durch das SQL_ATTR_ROW_OPERATION_PTR-Anweisungs Attribut verwiesen.  
  
 Die Anzahl der Elemente in den Status-und Vorgangs Arrays muss der Anzahl der Zeilen im Rowset entsprechen (wie durch das SQL_ATTR_ROW_ARRAY_SIZE Statement-Attribut definiert).  
  
 Weitere Informationen zum Zeilen Status Array finden Sie unter [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md). Weitere Informationen zum Zeilen Vorgangs Array finden Sie unter "ignorieren einer Zeile in einem Massen Vorgang" weiter unten in diesem Abschnitt.  
  
## <a name="using-sqlsetpos"></a>Verwenden von SQLSetPos  
 Bevor eine Anwendung **SQLSetPos**aufruft, muss Sie die folgenden Schritte ausführen:  
  
1.  Wenn die Anwendung **SQLSetPos** aufruft, wobei *Operation* auf SQL_UPDATE festgelegt ist, wird **SQLBindCol** (oder **SQLSetDescRec**) für jede Spalte aufgerufen, um den Datentyp anzugeben und Puffer für die Daten und die Länge der Spalte zu binden.  
  
2.  Wenn die Anwendung **SQLSetPos** aufruft, wobei *Operation* auf SQL_DELETE oder SQL_UPDATE festgelegt ist, muss **SQLColAttribute** aufgerufen werden, um sicherzustellen, dass die zu löschenden oder zu aktualisierenden Spalten aktualisierbar sind.  
  
3.  Rufen Sie **SQLExecDirect**, **SQLExecute**oder eine Katalog Funktion auf, um ein Resultset zu erstellen.  
  
4.  Rufen Sie **SQLFetch** oder **SQLFetchScroll** auf, um die Daten abzurufen.  
  
 Weitere Informationen zum Verwenden von **SQLSetPos**finden Sie unter [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
## <a name="deleting-data-using-sqlsetpos"></a>Löschen von Daten mithilfe von SQLSetPos  
 Zum Löschen von Daten mit **SQLSetPos**Ruft eine Anwendung **SQLSetPos** auf, wobei *RowNumber* auf die Nummer der zu löschenden Zeile und der *Vorgang* auf SQL_DELETE festgelegt ist.  
  
 Nachdem die Daten gelöscht wurden, ändert der Treiber den Wert im Array der Implementierungs Zeilen Status für die entsprechende Zeile in SQL_ROW_DELETED (oder SQL_ROW_ERROR).  
  
## <a name="updating-data-using-sqlsetpos"></a>Aktualisieren von Daten mithilfe von SQLSetPos  
 Eine Anwendung kann den Wert für eine Spalte entweder im gebundenen Datenpuffer oder mit einem oder mehreren Aufrufen von **SQLPutData**übergeben. Spalten, deren Daten mit **SQLPutData** übermittelt werden, werden als *Data-at-Execution-* *Spalten*bezeichnet. Diese werden häufig zum Senden von Daten für SQL_LONGVARBINARY und SQL_LONGVARCHAR Spalten verwendet und können mit anderen Spalten gemischt werden.  
  
#### <a name="to-update-data-with-sqlsetpos-an-application"></a>Zum Aktualisieren von Daten mit SQLSetPos wird eine Anwendung:  
  
1.  Platziert Werte in den Daten-und Längen-/indikatorpuffern, die mit **SQLBindCol**gebunden sind:  
  
    -   Für normale Spalten fügt die Anwendung den neuen Spaltenwert in den * \*targetvalueptr* -Puffer und die Länge dieses Werts im * \*StrLen_or_IndPtr* Puffer ein. Wenn die Zeile nicht aktualisiert werden soll, fügt die Anwendung SQL_ROW_IGNORE in das-Element der Zeile des Zeilen Vorgangs Arrays ein.  
  
    -   Bei Data-at-Execution-Spalten platziert die Anwendung einen Anwendungs definierten Wert, z. b. die Spaltennummer, im * \*targetvalueptr* -Puffer. Der Wert kann später verwendet werden, um die Spalte zu identifizieren.  
  
         Die Anwendung platziert das Ergebnis des SQL_LEN_DATA_AT_EXEC (*length*)-Makros im **StrLen_or_IndPtr* Puffer. Wenn der SQL-Datentyp der Spalte SQL_LONGVARBINARY, SQL_LONGVARCHAR oder ein langer Datenquellen spezifischer Datentyp ist und der Treiber "Y" für den SQL_NEED_LONG_DATA_LEN Informationstyp in **SQLGetInfo**zurückgibt, ist *length* die Anzahl der Daten bytes, die für den Parameter gesendet werden sollen. Andernfalls muss Sie ein nicht negativer Wert sein und wird ignoriert.  
  
2.  Ruft **SQLSetPos** auf, wobei das *Vorgangs* Argument auf SQL_UPDATE festgelegt ist, um die Daten Zeile zu aktualisieren.  
  
    -   Wenn keine Data-at-Execution-Spalten vorhanden sind, ist der Prozess vollständig.  
  
    -   Wenn Data-at-Execution-Spalten vorhanden sind, gibt die Funktion SQL_NEED_DATA zurück und geht mit Schritt 3 fort.  
  
3.  Ruft **SQLParamData** auf, um die Adresse des * \*targetvalueptr* -Puffers für die erste zu verarbeitende Data-at-Execution-Spalte abzurufen. **SQLParamData** gibt SQL_NEED_DATA zurück. Die Anwendung ruft den von der Anwendung definierten Wert aus dem * \*targetvalueptr* -Puffer ab.  
  
    > [!NOTE]  
    >  Obwohl Data-at-Execution-Parameter mit Data-at-Execution-Spalten vergleichbar sind, ist der von **SQLParamData** zurückgegebene Wert für jeden Wert anders.  
  
    > [!NOTE]  
    >  Data-at-Execution-Parameter sind Parameter in einer SQL-Anweisung, für die Daten mit **SQLPutData** gesendet werden, wenn die Anweisung mit **SQLExecDirect** oder **SQLExecute**ausgeführt wird. Sie werden mit **SQLBindParameter** oder durch Festlegen von Deskriptoren mit **sqlsetdebug**gebunden. Der von **SQLParamData** zurückgegebene Wert ist ein 32-Bit-Wert, der im *ParameterValuePtr* -Argument an **SQLBindParameter** übergeben wird.  
  
    > [!NOTE]  
    >  Data-at-Execution-Spalten sind Spalten in einem Rowset, für die Daten mit **SQLPutData** gesendet werden, wenn eine Zeile mit **SQLSetPos**aktualisiert wird. Sie sind mit **SQLBindCol**gebunden. Der von **SQLParamData** zurückgegebene Wert ist die Adresse der Zeile im **targetvalueptr* -Puffer, der verarbeitet wird.  
  
4.  Ruft **SQLPutData** ein oder mehrere Male auf, um Daten für die Spalte zu senden. Wenn alle Datenwerte nicht im in **SQLPutData**angegebenen * \*targetvalueptr* -Puffer zurückgegeben werden können, ist mehr als ein-Rückruf erforderlich. mehrere Aufrufe von **SQLPutData** für die gleiche Spalte sind nur zulässig, wenn Zeichen-c-Daten an eine Spalte mit einem Zeichen-, Binär-oder Datenquellen spezifischen Datentyp gesendet werden oder wenn binäre C-Daten an eine Spalte mit einem Zeichen-, Binär-oder Datenquellen spezifischen Datentyp gesendet werden.  
  
5.  Ruft **SQLParamData** erneut auf, um zu signalisieren, dass alle Daten für die Spalte gesendet wurden.  
  
    -   Wenn mehr Data-at-Execution-Spalten vorhanden sind, gibt **SQLParamData** SQL_NEED_DATA und die Adresse des *targetvalueptr* -Puffers für die nächste Data-at-Execution-Spalte zurück, die verarbeitet werden soll. Die Anwendung wiederholt die Schritte 4 und 5.  
  
    -   Wenn keine weiteren Data-at-Execution-Spalten vorhanden sind, ist der Prozess vollständig. Wenn die Anweisung erfolgreich ausgeführt wurde, gibt **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück. Wenn bei der Ausführung ein Fehler aufgetreten ist, wird SQL_ERROR zurückgegeben. An diesem Punkt können **SQLParamData** beliebige SQLSTATE-Objekte zurückgeben, die von **SQLSetPos**zurückgegeben werden können.  
  
 Wenn die Daten aktualisiert wurden, ändert der Treiber den Wert im Array der Implementierungs Zeilen Status für die entsprechende Zeile in SQL_ROW_UPDATED.  
  
 Wenn der Vorgang abgebrochen wird oder ein Fehler in **SQLParamData** oder **SQLPutData**auftritt, **Wenn SQLSetPos** SQL_NEED_DATA zurückgibt und bevor Daten für alle Data-at-Execution-Spalten gesendet werden, kann die Anwendung nur **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**oder **SQLPutData** für die-Anweisung oder die Verbindung aufrufen, die der Anweisung zugeordnet ist. Wenn eine andere Funktion für die-Anweisung oder die mit der-Anweisung verknüpfte Verbindung aufgerufen wird, gibt die Funktion SQL_ERROR und SQLSTATE HY010 (Funktions Sequenz Fehler) zurück.  
  
 Wenn die Anwendung **SQLCancel** aufruft, während der Treiber weiterhin Daten für Data-at-Execution-Spalten benötigt, bricht der Treiber den Vorgang ab. Die Anwendung kann dann **SQLSetPos** erneut aufrufen. Das Abbrechen wirkt sich nicht auf den Cursor Zustand oder die aktuelle Cursorposition aus.  
  
 Wenn die SELECT-Liste der Abfrage Spezifikation, die dem Cursor zugeordnet ist, mehr als einen Verweis auf dieselbe Spalte enthält, wird unabhängig davon, ob ein Fehler generiert wurde oder der Treiber die duplizierten Verweise ignoriert und die angeforderten Vorgänge durchgeführt, Treiber definiert.  
  
## <a name="performing-bulk-operations"></a>Ausführen von Massen Vorgängen  
 Wenn das *RowNumber* -Argument 0 ist, führt der Treiber den im *Vorgangs* Argument angegebenen Vorgang für jede Zeile im Rowset aus, die den Wert SQL_ROW_PROCEED in seinem Feld im Zeilen Vorgangs Array aufweist, auf das durch SQL_ATTR_ROW_OPERATION_PTR Statement-Attribut verwiesen wird. Dies ist ein gültiger Wert des *RowNumber* -Arguments für ein *Vorgangs* Argument von SQL_DELETE, SQL_REFRESH oder SQL_UPDATE, jedoch nicht SQL_POSITION. **SQLSetPos** mit einem *Vorgang* SQL_POSITION und eine *RowNumber* gleich 0 gibt SQLSTATE HY109 (ungültige Cursor Position) zurück.  
  
 Wenn ein Fehler auftritt, der sich auf das gesamte Rowset bezieht, z. b. SQLSTATE HYT00 (Timeout abgelaufen), gibt der Treiber SQL_ERROR und den entsprechenden SQLSTATE zurück. Der Inhalt der rowsetpuffer ist nicht definiert, und die Cursorposition bleibt unverändert.  
  
 Wenn ein Fehler auftritt, der sich auf eine einzelne Zeile bezieht, wird der Treiber:  
  
-   Legt das-Element für die Zeile im Zeilen Status Array fest, auf das durch das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut SQL_ROW_ERROR verwiesen wird.  
  
-   Sendet mindestens einen zusätzlichen Sqlstates-Wert für den Fehler in der Fehler Warteschlange und legt das Feld "SQL_DIAG_ROW_NUMBER" in der Diagnosedaten Struktur fest.  
  
 Wenn der Treiber den Vorgang für die verbleibenden Zeilen im Rowset abgeschlossen hat, wird er nach der Verarbeitung des Fehlers oder der Warnung SQL_SUCCESS_WITH_INFO zurückgegeben. Daher enthält die Fehler Warteschlange für jede Zeile, die einen Fehler zurückgegeben hat, 0 (null) oder mehr zusätzliche Sqlstates. Wenn der Treiber den Vorgang beendet, nachdem er den Fehler oder die Warnung verarbeitet hat, wird SQL_ERROR zurückgegeben.  
  
 Wenn der Treiber Warnungen zurückgibt, wie z. b. SQLSTATE 01004 (abgeschnittene Daten), gibt er Warnungen zurück, die auf das gesamte Rowset oder auf unbekannte Zeilen im Rowset zutreffen, bevor es die Fehlerinformationen zurückgibt, die für bestimmte Zeilen gelten. Sie gibt Warnungen für bestimmte Zeilen zusammen mit allen anderen Fehlerinformationen zu diesen Zeilen zurück.  
  
 Wenn *RowNumber* gleich 0 und *Operation* SQL_UPDATE, SQL_REFRESH oder SQL_DELETE ist, zeigt die Anzahl der Zeilen, auf die **SQLSetPos** angewendet wird, das SQL_ATTR_ROWS_FETCHED_PTR Statement-Attribut an.  
  
 Wenn *RowNumber* gleich 0 und *Operation* SQL_DELETE, SQL_REFRESH oder SQL_UPDATE ist, ist die aktuelle Zeile nach dem Vorgang mit der aktuellen Zeile vor dem Vorgang identisch.  
  
## <a name="ignoring-a-row-in-a-bulk-operation"></a>Ignorieren einer Zeile in einem Massen Vorgang  
 Das Row Operation-Array kann verwendet werden, um anzugeben, dass eine Zeile im aktuellen Rowset bei einem Massen Vorgang mithilfe von **SQLSetPos**ignoriert werden soll. Um den Treiber anzuweisen, eine oder mehrere Zeilen während eines Massen Vorgangs zu ignorieren, sollte eine Anwendung die folgenden Schritte ausführen:  
  
1.  Aufrufen von **SQLSetStmtAttr** , um das SQL_ATTR_ROW_OPERATION_PTR-Anweisungs Attribut so festzulegen, dass es auf ein Array von sqlusmallints verweist. Dieses Feld kann auch durch Aufrufen von **SQLSetDescField** festgelegt werden, um das SQL_DESC_ARRAY_STATUS_PTR Header-Feld der ARD festzulegen. Dies erfordert, dass eine Anwendung das Deskriptorhandle erhält.  
  
2.  Legen Sie jedes Element des Zeilen Vorgangs Arrays auf einen von zwei Werten fest:  
  
    -   SQL_ROW_IGNORE, um anzugeben, dass die Zeile für den Massen Vorgang ausgeschlossen wird.  
  
    -   SQL_ROW_PROCEED, um anzugeben, dass die Zeile im Massen Vorgang enthalten ist. (Dies ist der Standardwert.)  
  
3.  Aufrufen von **SQLSetPos** zum Ausführen des Massen Vorgangs.  
  
 Die folgenden Regeln gelten für das Array Row Operation:  
  
-   SQL_ROW_IGNORE und SQL_ROW_PROCEED wirken sich nur auf Massen Vorgänge mithilfe von **SQLSetPos** mit einem *Vorgang* von SQL_DELETE oder SQL_UPDATE aus. Sie haben keine Auswirkung auf Aufrufe von **SQLSetPos** mit einem *Vorgang* von SQL_REFRESH oder SQL_POSITION.  
  
-   Der Zeiger ist standardmäßig auf NULL festgelegt.  
  
-   Wenn der Zeiger NULL ist, werden alle Zeilen so aktualisiert, als wären alle Elemente auf SQL_ROW_PROCEED festgelegt.  
  
-   Wenn ein Element auf SQL_ROW_PROCEED festgelegt wird, wird nicht sichergestellt, dass der Vorgang für die jeweilige Zeile ausgeführt wird. Wenn beispielsweise eine bestimmte Zeile im Rowset den Status SQL_ROW_ERROR aufweist, kann der Treiber diese Zeile möglicherweise nicht aktualisieren, unabhängig davon, ob die Anwendung SQL_ROW_PROCEED angegeben wurde. Eine Anwendung muss immer das Array Zeilen Status überprüfen, um festzustellen, ob der Vorgang erfolgreich war.  
  
-   SQL_ROW_PROCEED ist in der Header Datei als 0 definiert. Eine Anwendung kann das Zeilen Vorgangs Array mit 0 initialisieren, um alle Zeilen zu verarbeiten.  
  
-   Wenn die Element Nummer "n" im Zeilen Vorgangs Array auf SQL_ROW_IGNORE festgelegt ist und **SQLSetPos** aufgerufen wird, um einen Massen Aktualisierungs-oder Löschvorgang auszuführen, bleibt die n-te Zeile im Rowset nach dem Aufruf von **SQLSetPos**unverändert.  
  
-   Eine Anwendung sollte automatisch eine schreibgeschützte Spalte auf SQL_ROW_IGNORE festlegen.  
  
## <a name="ignoring-a-column-in-a-bulk-operation"></a>Ignorieren einer Spalte in einem Massen Vorgang  
 Um unnötige Verarbeitungs Diagnosen zu vermeiden, die durch die Aktualisierung einer oder mehrerer Schreib geschützter Spalten generiert wurden, kann eine Anwendung den Wert im gebundenen Längen-/Indikatorpuffer auf SQL_COLUMN_IGNORE festlegen. Weitere Informationen finden Sie unter [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel kann ein Benutzer mit einer Anwendung die Orders-Tabelle durchsuchen und den Auftragsstatus aktualisieren. Der Cursor ist mit einer Rowsetgröße von 20 keysetgesteuert und verwendet die Steuerung der vollständigen Parallelität, um Zeilen Versionen zu vergleichen. Nachdem jedes Rowset abgerufen wurde, gibt die Anwendung es aus und ermöglicht es dem Benutzer, den Status eines Auftrags auszuwählen und zu aktualisieren. Die Anwendung verwendet **SQLSetPos** , um den Cursor in der ausgewählten Zeile zu positionieren, und führt ein positioniertes Update der Zeile aus. (Die Fehlerbehandlung wird aus Gründen der Übersichtlichkeit ausgelassen.)  
  
```cpp  
#define ROWS 20  
#define STATUS_LEN 6  
  
SQLCHAR        szStatus[ROWS][STATUS_LEN], szReply[3];  
SQLINTEGER     cbStatus[ROWS], cbOrderID;  
SQLUSMALLINT   rgfRowStatus[ROWS];  
SQLUINTEGER    sOrderID, crow = ROWS, irow;  
SQLHSTMT       hstmtS, hstmtU;  
  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CONCURRENCY, (SQLPOINTER) SQL_CONCUR_ROWVER, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER) SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_STATUS_PTR, (SQLPOINTER) rgfRowStatus, 0);  
SQLSetCursorName(hstmtS, "C1", SQL_NTS);  
SQLExecDirect(hstmtS, "SELECT ORDERID, STATUS FROM ORDERS ", SQL_NTS);  
  
SQLBindCol(hstmtS, 1, SQL_C_ULONG, &sOrderID, 0, &cbOrderID);  
SQLBindCol(hstmtS, 2, SQL_C_CHAR, szStatus, STATUS_LEN, &cbStatus);  
  
while ((retcode == SQLFetchScroll(hstmtS, SQL_FETCH_NEXT, 0)) != SQL_ERROR) {  
   if (retcode == SQL_NO_DATA_FOUND)  
      break;  
   for (irow = 0; irow < crow; irow++) {  
      if (rgfRowStatus[irow] != SQL_ROW_DELETED)  
         printf("%2d %5d %*s\n", irow+1, sOrderID, NAME_LEN-1, szStatus[irow]);  
   }  
   while (TRUE) {  
      printf("\nRow number to update?");  
      gets_s(szReply, 3);  
      irow = atoi(szReply);  
      if (irow > 0 && irow <= crow) {  
         printf("\nNew status?");  
         gets_s(szStatus[irow-1], (ROWS * STATUS_LEN));  
         SQLSetPos(hstmtS, irow, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
         SQLPrepare(hstmtU,  
          "UPDATE ORDERS SET STATUS=? WHERE CURRENT OF C1", SQL_NTS);  
         SQLBindParameter(hstmtU, 1, SQL_PARAM_INPUT,  
            SQL_C_CHAR, SQL_CHAR,  
            STATUS_LEN, 0, szStatus[irow], 0, NULL);  
         SQLExecute(hstmtU);  
      } else if (irow == 0) {  
         break;  
      }  
   }  
}  
```  
  
 Weitere Beispiele finden Sie unter [positionierte UPDATE-und DELETE-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) und [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Massen Vorgängen, die sich nicht auf die Position des Block Cursors beziehen|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Ein einzelnes Feld eines Deskriptors wird abgerufen.|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Mehrere Felder eines Deskriptors werden abgerufen.|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen Felds eines Deskriptors|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen mehrerer Felder eines Deskriptors|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Festlegen eines Anweisungs Attributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
