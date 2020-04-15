---
title: SQLSetPos-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a8839f1ae540ac9e5f29e144f7f57fb754e50ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287330"
---
# <a name="sqlsetpos-function"></a>SQLSetPos-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ODBC  
  
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
 [Eingabe] Anweisungshandle.  
  
 *Rownumber*  
 [Eingabe] Position der Zeile im Rowset, auf der der mit dem *Argument Operation* angegebene Vorgang ausgeführt werden soll. Wenn *RowNumber* 0 ist, gilt der Vorgang für jede Zeile im Rowset.  
  
 Weitere Informationen finden Sie unter "Kommentare".  
  
 *Vorgang*  
 [Eingabe] Vorgang zum Ausführen von:  
  
 SQL_POSITION SQL_REFRESH SQL_UPDATE SQL_DELETE  
  
> [!NOTE]
>  Der SQL_ADD Wert für das *Operation-Argument* wurde für ODBC *3.x*veraltet. ODBC *3.x-Treiber* müssen SQL_ADD für Abwärtskompatibilität unterstützen. Diese Funktionalität wurde durch einen Aufruf von **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD ersetzt. Wenn eine ODBC *3.x-Anwendung* mit einem ODBC *2.x-Treiber* arbeitet, ordnet der Treiber-Manager einen Aufruf von **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD **sqlSetPos** mit einem *Vorgang* von SQL_ADD zu.  
  
 Weitere Informationen finden Sie unter "Kommentare".  
  
 *LockType*  
 [Eingabe] Gibt an, wie die Zeile gesperrt werden soll, nachdem der im *Argument Operation* angegebene Vorgang ausgeführt wurde.  
  
 SQL_LOCK_NO_CHANGE SQL_LOCK_EXCLUSIVE SQL_LOCK_UNLOCK  
  
 Weitere Informationen finden Sie unter "Kommentare".  
  
 **Rückgabe**  
  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetPos** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLSetPos** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
 Für alle SQLSTATEs, die SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgeben können (außer 01xxx SQLSTATEs), wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn ein Fehler bei einer oder mehreren Zeilen eines mehrreihigen Vorgangs auftritt, und SQL_ERROR wird zurückgegeben, wenn ein Fehler bei einem einzeiligen Vorgang auftritt.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01001|Cursor-Operation-Konflikt|Das *Operation-Argument* wurde SQL_DELETE oder SQL_UPDATE, und es wurden keine Zeilen oder mehr als eine Zeile gelöscht oder aktualisiert. (Weitere Informationen zu Aktualisierungen in mehr als einer Zeile finden Sie in der Beschreibung des SQL_ATTR_SIMULATE_CURSOR *Attributs* in **SQLSetStmtAttr**.) (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> Das *Argument "Vorgang"* wurde SQL_DELETE oder SQL_UPDATE, und der Vorgang ist aufgrund einer optimistischen Parallelität fehlgeschlagen. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten-Rechts-Abschneiden|Das *Operation-Argument* wurde SQL_REFRESH, und Zeichenfolgen- oder Binärdaten, die für eine Spalte oder Spalten mit einem Datentyp von SQL_C_CHAR oder SQL_C_BINARY zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind.|  
|01S01|Fehler in Zeile|Das *RowNumber-Argument* war 0, und ein Fehler ist in einer oder mehreren Zeilen aufgetreten, während der Vorgang ausgeführt wurde, der mit dem *Argument Operation* angegeben wurde.<br /><br /> (SQL_SUCCESS_WITH_INFO wird zurückgegeben, wenn bei einer oder mehreren, aber nicht allen Zeilen eines mehrreihigen Vorgangs ein Fehler auftritt, und SQL_ERROR zurückgegeben wird, wenn bei einem einzeiligen Vorgang ein Fehler auftritt.)<br /><br /> (Dieser SQLSTATE wird nur zurückgegeben, wenn **SQLSetPos** nach **SQLExtendedFetch**aufgerufen wird, wenn der Treiber ein ODBC *2.x-Treiber* ist und die Cursorbibliothek nicht verwendet wird.)|  
|01S07|Bruchschnitt|Das *Argument Operation* wurde SQL_REFRESH, der Datentyp des Anwendungspuffers war nicht SQL_C_CHAR oder SQL_C_BINARY, und die Anstellungsdaten für eine oder mehrere Spalten wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteil der Zahl abgeschnitten. Für Zeit-, Zeitstempel- und Intervalldatentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|Der Datenwert einer Spalte im Resultset konnte nicht in den von *TargetType* beim Aufruf von **SQLBindCol**angegebenen Datentyp konvertiert werden.|  
|07009|Ungültiger Deskriptorindex|Das Argument *Operation* wurde SQL_REFRESH oder SQL_UPDATE, und eine Spalte wurde mit einer Spaltennummer gebunden, die größer als die Anzahl der Spalten im Resultset ist.|  
|21S02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|Das Argument *Operation* wurde SQL_UPDATE, und keine Spalten waren aufrüstbar, da alle Spalten entweder ungebunden, schreibgeschützt waren oder der Wert im gebundenen Längen-/Indikatorpuffer SQL_COLUMN_IGNORE war.|  
|22001|Zeichenfolgendaten, rechtes Abschneiden|Das *Argument Operation* wurde SQL_UPDATE, und die Zuweisung eines Zeichens oder Binärwerts zu einer Spalte führte zum Abschneiden von nicht leeren (für Zeichen) oder nicht NULL (für binären) Zeichen oder Bytes.|  
|22003|Numerischer Wert aofc|Das Argument *Operation* wurde SQL_UPDATE, und die Zuweisung eines numerischen Werts zu einer Spalte in der Ergebnismenge führte dazu, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde.<br /><br /> Das Argument *Operation* wurde SQL_REFRESH, und das Zurückgeben des numerischen Werts für eine oder mehrere gebundene Spalten hätte zu einem Verlust signifikanter Ziffern geführt.|  
|22007|Ungültiges Datumszeitformat|Das Argument *Vorgang* wurde SQL_UPDATE, und die Zuordnung eines Datums- oder Zeitstempelwerts zu einer Spalte im Resultset führte dazu, dass das Feld "Jahr", "Monat" oder "Tag" anicht in Reichweite lag.<br /><br /> Das Argument *Operation* wurde SQL_REFRESH, und das Zurückgeben des Datums- oder Zeitstempelwerts für eine oder mehrere gebundene Spalten hätte dazu geführt, dass das Feld "Jahr", "Monat" oder "Tag" anicht in den Bereich gefallen wäre.|  
|22008|Datums-/Uhrzeitfeldüberlauf|Das *Argument Operation* wurde SQL_UPDATE, und die Leistung der Datetime-Arithmetik für Daten, die an eine Spalte im Resultset gesendet wurden, führte zu einem Datumszeitfeld (Jahr, Monat, Tag, Stunde, Minute oder zweites Feld), das außerhalb des zulässigen Wertebereichs für das Feld liegt oder aufgrund der natürlichen Regeln des Gregorianischen Kalenders für Datumszeiten ungültig ist.<br /><br /> Das *Operation-Argument* wurde SQL_REFRESH, und die Leistung der Datetime-Arithmetik für Daten, die aus dem Resultset abgerufen wurden, führte zu einem Datumszeitfeld (Jahr, Monat, Tag, Stunde, Minute oder zweites Feld), das außerhalb des zulässigen Wertebereichs für das Feld liegt oder aufgrund der natürlichen Regeln des Gregorianischen Kalenders für Datumszeiten ungültig ist.|  
|22015|Intervallfeldüberlauf|Das *Argument Operation* wurde SQL_UPDATE, und die Zuweisung eines genauen numerischen oder Intervall-C-Typs zu einem Intervall-SQL-Datentyp verursachte einen Verlust signifikanter Ziffern.<br /><br /> Das *Argument Operation* wurde SQL_UPDATE; Beim Zuweisen eines INTERVALL-SQL-Typs gab es keine Darstellung des Wertes des Typs C im Intervall-SQL-Typ.<br /><br /> Das *Argument Operation* wurde SQL_REFRESH, und das Zuweisen eines SQL-Typs aus einem exakten numerischen oder Intervall-SQL-Typ zu einem Intervall-C-Typ verursachte einen Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Das *Argument Operation* wurde SQL_ REFRESH; Beim Zuweisen zu einem Intervall-C-Typ gab es keine Darstellung des Wertes des SQL-Typs im Intervall-C-Typ.|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|Das *Argument Operation* wurde SQL_REFRESH; Der C-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp; Der SQL-Typ der Spalte war ein Zeichendatentyp; und der Wert in der Spalte war kein gültiges Literal des gebundenen C-Typs.<br /><br /> Das Argument *Operation* war SQL_UPDATE; Der SQL-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. der Typ C wurde SQL_C_CHAR; und der Wert in der Spalte war kein gültiges Literal des gebundenen SQL-Typs.|  
|23000|Verletzung der Integritätseinschränkung|Das Argument *Operation* wurde SQL_DELETE oder SQL_UPDATE, und eine Integritätseinschränkung wurde verletzt.|  
|24.000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.<br /><br /> (DM) Ein Cursor wurde für das *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurden nicht aufgerufen.<br /><br /> Ein Cursor wurde für *das StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen, aber der Cursor wurde vor dem Anfang des Resultsets oder nach dem Ende des Resultsets positioniert.<br /><br /> Das Argument *Operation* wurde SQL_DELETE, SQL_REFRESH oder SQL_UPDATE, und der Cursor wurde vor dem Anfang des Resultsets oder nach dem Ende des Resultsets positioniert.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcenstillstands mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntaxfehler oder Zugriffsverletzung|Der Treiber konnte die Zeile nicht nach Bedarf sperren, um den im Argument *Operation*angeforderten Vorgang auszuführen.<br /><br /> Der Treiber konnte die Zeile nicht wie im Argument *LockType*angefordert sperren.|  
|44000|WITH CHECK OPTION-Verstoß|Das *Argument Vorgang* wurde SQL_UPDATE, und die Aktualisierung wurde für eine angezeigte Tabelle oder eine Tabelle durchgeführt, die von der angezeigten Tabelle abgeleitet wurde, die durch Angabe von WITH CHECK **OPTION**erstellt wurde, sodass eine oder mehrere Zeilen, die von der Aktualisierung betroffen sind, nicht mehr in der angezeigten Tabelle vorhanden sind.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für den *StatementHandle*aufgerufen, und dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die SQLSetPos-Funktion aufgerufen wurde.<br /><br /> (DM) Der angegebene *StatementHandle* befand sich nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute**oder eine Katalogfunktion aufzurufen.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Der Treiber war ein ODBC *2.x-Treiber,* und **SQLSetPos** wurde für einen *StatementHandle* aufgerufen, nachdem **SQLFetch** aufgerufen wurde.|  
|HY011|Attribut kann jetzt nicht festgelegt werden|(DM) Der Treiber war ein ODBC *2.x-Treiber;* das SQL_ATTR_ROW_STATUS_PTR Anweisungsattribut festgelegt wurde; dann wurde **SQLSetPos** aufgerufen, bevor **SQLFetch**, **SQLFetchScroll**oder **SQLExtendedFetch** aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|Das *Argument Operation* wurde SQL_UPDATE, ein Datenwert war ein Nullzeiger, und der Spaltenlängenwert war nicht 0, SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NULL_DATA oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Das *Argument Operation* wurde SQL_UPDATE; ein Datenwert war kein Nullzeiger; der C-Datentyp SQL_C_BINARY oder SQL_C_CHAR; und der Wert für die Spaltenlänge war kleiner als 0, aber nicht gleich SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS oder SQL_NULL_DATA oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Der Wert in einem Längen-Indikator-Puffer wurde SQL_DATA_AT_EXEC; Der SQL-Typ war entweder SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer datenquellenspezifischer Datentyp. und der SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo** war "Y".|  
|HY092|Ungültiger Attributbezeichner|(DM) Der für das *Operation-Argument* angegebene Wert war ungültig.<br /><br /> (DM) Der für das *LockType-Argument* angegebene Wert war ungültig.<br /><br /> Das *Argument Operation* wurde SQL_UPDATE oder SQL_DELETE, und das Attribut SQL_ATTR_CONCURRENCY-Anweisung wurde SQL_ATTR_CONCUR_READ_ONLY.|  
|HY107|Zeilenwert a-range|Der für das Argument *RowNumber* angegebene Wert war größer als die Anzahl der Zeilen im Rowset.|  
|HY109|Ungültige Cursorposition|Der dem *StatementHandle* zugeordnete Cursor wurde als vorwärtsgerichtet definiert, sodass der Cursor nicht innerhalb des Rowsets positioniert werden konnte. Siehe Beschreibung für das SQL_ATTR_CURSOR_TYPE-Attribut in **SQLSetStmtAttr**.<br /><br /> Das *Argument Operation* wurde SQL_UPDATE, SQL_DELETE oder SQL_REFRESH, und die durch das *RowNumber-Argument* identifizierte Zeile wurde gelöscht oder nicht abgerufen.<br /><br /> (DM) Das *RowNumber-Argument* war 0, und das *Argument Operation* wurde SQL_POSITION.<br /><br /> **SQLSetPos** wurde aufgerufen, nachdem **SQLBulkOperations** aufgerufen wurde und bevor **SQLFetchScroll** oder **SQLFetch** aufgerufen wurde.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der Treiber oder die Datenquelle unterstützt den im *Operation-Argument* oder im *LockType-Argument* angeforderten Vorgang nicht.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr** mit einem *Attribut* von SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
  
> [!CAUTION]
>  Informationen zur Anweisung finden **SQLSetPos** Sie unter [Blockcursors, Scrollable Cursors und Backward Compatibility](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md). *2.x*  
  
## <a name="rownumber-argument"></a>RowNumber-Argument  
 Das *RowNumber-Argument* gibt die Nummer der Zeile im Rowset an, für die der durch das *Argument Operation* angegebene Vorgang ausgeführt werden soll. Wenn *RowNumber* 0 ist, gilt der Vorgang für jede Zeile im Rowset. *RowNumber* muss ein Wert von 0 bis zur Anzahl der Zeilen im Rowset sein.  
  
> [!NOTE]  
>  In der Sprache C sind Arrays 0-basiert und das *RowNumber-Argument* 1-basiert. Um beispielsweise die fünfte Zeile des Rowsets zu aktualisieren, ändert eine Anwendung die Rowsetpuffer im Arrayindex 4, gibt jedoch eine *RowNumber* von 5 an.  
  
 Alle Operationen positionieren den Cursor in der zeile, die von *RowNumber*angegeben wird. Die folgenden Vorgänge erfordern eine Cursorposition:  
  
-   Positionierte Aktualisierungs- und Löschanweisungen.  
  
-   Aufrufe von **SQLGetData**.  
  
-   Ruft **SQLSetPos** mit den Optionen SQL_DELETE, SQL_REFRESH und SQL_UPDATE auf.  
  
 Wenn *RowNumber* z. B. 2 für einen Aufruf von **SQLSetPos** mit einem *Vorgang* von SQL_DELETE ist, wird der Cursor in der zweiten Zeile des Rowsets positioniert und diese Zeile gelöscht. Der Eintrag im Statusarray der Implementierungszeile (auf den das Attribut SQL_ATTR_ROW_STATUS_PTR Anweisung zeigt) für die zweite Zeile wird in SQL_ROW_DELETED geändert.  
  
 Eine Anwendung kann beim Aufrufen von **SQLSetPos**eine Cursorposition angeben. Im Allgemeinen ruft es **SQLSetPos** mit dem SQL_POSITION oder SQL_REFRESH-Vorgang auf, um den Cursor zu positionieren, bevor eine positionierte Aktualisierung oder Löschanweisung ausgeführt oder **SQLGetData**aufgerufen wird.  
  
## <a name="operation-argument"></a>Operation Argument  
 Das *Argument Operation* unterstützt die folgenden Vorgänge. Um zu bestimmen, welche Optionen von einer Datenquelle unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_DYNAMIC_CURSOR_ATTRIBUTES1-, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1-, SQL_KEYSET_CURSOR_ATTRIBUTES1- oder SQL_STATIC_CURSOR_ATTRIBUTES1 -Typ auf (je nach Typ des Cursors).  
  
|*Vorgang*<br /><br /> Argument|Vorgang|  
|------------------------------|---------------|  
|SQL_POSITION|Der Treiber positioniert den Cursor in der zeile, die von *RowNumber*angegeben wird.<br /><br /> Der Inhalt des Zeilenstatusarrays, auf das durch das Attribut SQL_ATTR_ROW_OPERATION_PTR -anweisung verwiesen wird, wird für den SQL_POSITION *Vorgang*ignoriert.|  
|SQL_REFRESH|Der Treiber positioniert den Cursor in der von *RowNumber* angegebenen Zeile und aktualisiert Daten in den Rowsetpuffern für diese Zeile. Weitere Informationen dazu, wie der Treiber Daten in den Rowsetpuffern zurückgibt, finden Sie in den Beschreibungen der zeilen- und spaltenweisen Bindung in **SQLBindCol**.<br /><br /> **SQLSetPos** mit einem *Vorgang* von SQL_REFRESH aktualisiert den Status und Inhalt der Zeilen innerhalb des aktuellen abgerufenen Rowsets. Dazu gehört auch das Aktualisieren der Lesezeichen. Da die Daten in den Puffern aktualisiert, aber nicht erneut abgerufen werden, ist die Mitgliedschaft im Rowset behoben. Dies unterscheidet sich von der Aktualisierung, die von einem Aufruf von **SQLFetchScroll** mit einem *FetchOrientation* von SQL_FETCH_RELATIVE und einer *RowNumber* gleich 0 durchgeführt wird, wodurch das Rowset aus dem Resultset erneut abgerufen wird, sodass hinzugefügte Daten angezeigt und gelöschte Daten entfernt werden können, wenn diese Vorgänge vom Treiber und dem Cursor unterstützt werden.<br /><br /> Eine erfolgreiche Aktualisierung mit **SQLSetPos** ändert keinen Zeilenstatus von SQL_ROW_DELETED. Gelöschte Zeilen innerhalb des Rowsets werden bis zum nächsten Abruf weiterhin als gelöscht markiert. Die Zeilen werden beim nächsten Abruf ausgeblendet, wenn der Cursor das Packen unterstützt (in dem ein nachfolgender **SQLFetch** oder **SQLFetchScroll** keine gelöschten Zeilen zurückgibt).<br /><br /> Hinzugefügte Zeilen werden nicht angezeigt, wenn eine Aktualisierung mit **SQLSetPos** durchgeführt wird. Dieses Verhalten unterscheidet sich von **SQLFetchScroll** mit einem *FetchType* von SQL_FETCH_RELATIVE und einer *RowNumber* gleich 0, die auch das aktuelle Rowset aktualisiert, aber hinzugefügte Datensätze anzeigt oder gelöschte Datensätze packt, wenn diese Vorgänge vom Cursor unterstützt werden.<br /><br /> Eine erfolgreiche Aktualisierung mit **SQLSetPos** ändert den Zeilenstatus von SQL_ROW_ADDED in SQL_ROW_SUCCESS (falls das Zeilenstatusarray vorhanden ist).<br /><br /> Eine erfolgreiche Aktualisierung mit **SQLSetPos** ändert einen Zeilenstatus von SQL_ROW_UPDATED in den neuen Status der Zeile (falls das Zeilenstatusarray vorhanden ist).<br /><br /> Wenn bei einem **SQLSetPos-Vorgang** in einer Zeile ein Fehler auftritt, wird der Zeilenstatus auf SQL_ROW_ERROR festgelegt (falls das Zeilenstatusarray vorhanden ist).<br /><br /> Bei einem Cursor, der mit einem SQL_ATTR_CONCURRENCY Anweisungsattribut von SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES geöffnet wird, kann eine Aktualisierung mit **SQLSetPos** die optimistischen Parallelitätswerte aktualisieren, die von der Datenquelle verwendet werden, um festzustellen, dass sich die Zeile geändert hat. In diesem Fall werden die Zeilenversionen oder -werte aktualisiert, die verwendet werden, um die Cursorparallelität sicherzustellen, wenn die Rowsetpuffer vom Server aktualisiert werden. Dies gilt für jede Zeile, die aktualisiert wird.<br /><br /> Der Inhalt des Zeilenstatusarrays, auf das durch das Attribut SQL_ATTR_ROW_OPERATION_PTR -anweisung verwiesen wird, wird für den SQL_REFRESH *Vorgang*ignoriert.|  
|SQL_UPDATE|Der Treiber positioniert den Cursor in der von *RowNumber* angegebenen Zeile und aktualisiert die zugrunde liegende Datenzeile mit den Werten in den Rowset-Puffern (das *TargetValuePtr-Argument* in **SQLBindCol**). Es ruft die Längen der Daten aus den Längen-/Indikatorpuffern ab (das *StrLen_or_IndPtr-Argument* in **SQLBindCol**). Wenn die Länge einer Spalte SQL_COLUMN_IGNORE ist, wird die Spalte nicht aktualisiert. Nach dem Aktualisieren der Zeile ändert der Treiber das entsprechende Element des Zeilenstatusarrays in SQL_ROW_UPDATED oder SQL_ROW_SUCCESS_WITH_INFO (falls das Zeilenstatusarray vorhanden ist).<br /><br /> Es ist treiberdefiniert, wie das Verhalten ist, wenn **SQLSetPos** mit einem *Operation-Argument* von SQL_UPDATE auf einem Cursor aufgerufen wird, der doppelte Spalten enthält. Der Treiber kann einen treiberdefinierten SQLSTATE zurückgeben, die erste Spalte aktualisieren, die im Resultset angezeigt wird, oder andere treiberdefinierte Verhaltensweisen ausführen.<br /><br /> Das Zeilenoperationarray, auf das das SQL_ATTR_ROW_OPERATION_PTR Anweisungsattribut zeigt, kann verwendet werden, um anzugeben, dass eine Zeile im aktuellen Rowset während einer Massenaktualisierung ignoriert werden soll. Weitere Informationen finden Sie weiter unten in dieser Funktionsreferenz unter "Status- und Vorgangs-Arrays".|  
|SQL_DELETE|Der Treiber positioniert den Cursor in der von *RowNumber* angegebenen Zeile und löscht die zugrunde liegende Datenzeile. Das entsprechende Element des Zeilenstatusarrays wird in SQL_ROW_DELETED geändert. Nachdem die Zeile gelöscht wurde, sind die folgenden Zeilen für die Zeile ungültig: positionierte Aktualisierungs- und Löschanweisungen, Aufrufe von **SQLGetData**und Aufrufe von **SQLSetPos** mit *Operation,* der auf alles außer SQL_POSITION festgelegt ist. Bei Treibern, die das Packen unterstützen, wird die Zeile aus dem Cursor gelöscht, wenn neue Daten aus der Datenquelle abgerufen werden.<br /><br /> Ob die Zeile sichtbar bleibt, hängt vom Cursortyp ab. Gelöschte Zeilen sind z. B. für statische und Keyset-gesteuerte Cursor sichtbar, für dynamische Cursor jedoch nicht sichtbar.<br /><br /> Das Zeilenoperationarray, auf das das Attribut SQL_ATTR_ROW_OPERATION_PTR Anweisung zeigt, kann verwendet werden, um anzugeben, dass eine Zeile im aktuellen Rowset während eines Massenlöschvorgangs ignoriert werden soll. Weitere Informationen finden Sie weiter unten in dieser Funktionsreferenz unter "Status- und Vorgangs-Arrays".|  
  
## <a name="locktype-argument"></a>LockType-Argument  
 Das *LockType-Argument* bietet Anwendungen die Möglichkeit, parallele Informationen zu steuern. In den meisten Fällen unterstützen Datenquellen, die Parallelitätsebenen und Transaktionen unterstützen, nur den SQL_LOCK_NO_CHANGE Wert des *LockType-Arguments.* Das *LockType-Argument* wird im Allgemeinen nur für dateibasierte Unterstützung verwendet.  
  
 Das *LockType-Argument* gibt den Sperrstatus der Zeile an, nachdem **SQLSetPos** ausgeführt wurde. Wenn der Treiber die Zeile nicht sperren kann, um den angeforderten Vorgang auszuführen oder das *LockType-Argument* zu erfüllen, gibt er SQL_ERROR und SQLSTATE 42000 (Syntaxfehler oder Zugriffsverletzung) zurück.  
  
 Obwohl das *LockType-Argument* für eine einzelne Anweisung angegeben ist, gewährt die Sperre allen Anweisungen in der Verbindung dieselben Berechtigungen. Insbesondere kann eine Sperre, die von einer Anweisung für eine Verbindung erfasst wird, durch eine andere Anweisung für dieselbe Verbindung entsperrt werden.  
  
 Eine zeile, die über **SQLSetPos** gesperrt ist, bleibt gesperrt, bis die Anwendung **SQLSetPos** für die Zeile aufruft, deren *LockType* auf SQL_LOCK_UNLOCK festgelegt ist, oder bis die Anwendung **SQLFreeHandle** für die Anweisung oder **SQLFreeStmt** mit der Option SQL_CLOSE aufruft. Bei einem Treiber, der Transaktionen unterstützt, wird eine über **SQLSetPos** gesperrte Zeile entsperrt, wenn die Anwendung **SQLEndTran** aufruft, um eine Transaktion für die Verbindung festzuschreiben oder zurückzusetzen (wenn ein Cursor geschlossen wird, wenn eine Transaktion festgeschrieben oder zurückgesetzt wird, wie durch die SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR von **SQLGetInfo**zurückgegebenen Informationstypen angegeben).  
  
 Das *LockType-Argument* unterstützt die folgenden Arten von Sperren. Um zu bestimmen, welche Sperren von einer Datenquelle unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_DYNAMIC_CURSOR_ATTRIBUTES1-, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1-, SQL_KEYSET_CURSOR_ATTRIBUTES1- oder SQL_STATIC_CURSOR_ATTRIBUTES1 -Typ auf (je nach Typ des Cursors).  
  
|*LockType-Argument*|Sperrtyp|  
|-------------------------|---------------|  
|SQL_LOCK_NO_CHANGE|Der Treiber oder die Datenquelle stellt sicher, dass sich die Zeile im gleichen gesperrten oder entsperrten Zustand befindet wie vor dem Aufruf von **SQLSetPos.** Dieser Wert von *LockType* ermöglicht Datenquellen, die keine explizite Sperrung auf Zeilenebene unterstützen, die Verwendung der Sperrung, die für die aktuellen Parallelitäts- und Transaktionsisolationsstufen erforderlich ist.|  
|SQL_LOCK_EXCLUSIVE|Der Treiber oder die Datenquelle sperrt die Zeile ausschließlich. Eine Anweisung für eine andere Verbindung oder in einer anderen Anwendung kann nicht verwendet werden, um Sperren für die Zeile zu erhalten.|  
|SQL_LOCK_UNLOCK|Der Treiber oder die Datenquelle entsperrt die Zeile.|  
  
 Wenn ein Treiber SQL_LOCK_EXCLUSIVE, aber nicht SQL_LOCK_UNLOCK unterstützt, bleibt eine gesperrte Zeile gesperrt, bis einer der im vorherigen Absatz beschriebenen Funktionsaufrufe erfolgt.  
  
 Wenn ein Treiber SQL_LOCK_EXCLUSIVE, aber keine SQL_LOCK_UNLOCK unterstützt, bleibt eine gesperrte Zeile gesperrt, bis die Anwendung **SQLFreeHandle** für die Anweisung oder **SQLFreeStmt** mit der Option SQL_CLOSE aufruft. Wenn der Treiber Transaktionen unterstützt und den Cursor beim Übertragen oder Zurückrollen der Transaktion schließt, ruft die Anwendung **SQLEndTran**auf.  
  
 Für die Aktualisierungs- und Löschvorgänge in **SQLSetPos**verwendet die Anwendung das *LockType-Argument* wie folgt:  
  
-   Um sicherzustellen, dass sich eine Zeile nach dem Abrufen nicht ändert, ruft eine Anwendung **SQLSetPos** *auf,* wobei Operation auf SQL_REFRESH festgelegt ist und *LockType* auf SQL_LOCK_EXCLUSIVE festgelegt ist.  
  
-   Wenn die Anwendung *LockType* auf SQL_LOCK_NO_CHANGE setzt, garantiert der Treiber, dass ein Aktualisierungs- oder Löschvorgang nur erfolgreich ist, wenn die für das Attribut SQL_ATTR_CONCURRENCY-Anweisung angegebene Anwendung SQL_CONCUR_LOCK.  
  
-   Wenn die Anwendung SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES für das Attribut SQL_ATTR_CONCURRENCY-Anweisung angibt, vergleicht der Treiber Zeilenversionen oder -werte und lehnt den Vorgang ab, wenn sich die Zeile seit dem Abrufen der Zeile durch die Anwendung geändert hat.  
  
-   Wenn die Anwendung SQL_CONCUR_READ_ONLY für das Attribut SQL_ATTR_CONCURRENCY -Anweisung angibt, lehnt der Treiber einen Aktualisierungs- oder Löschvorgang ab.  
  
 Weitere Informationen zum SQL_ATTR_CONCURRENCY-Anweisungsattribut finden Sie unter [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="status-and-operation-arrays"></a>Status- und Operation-Arrays  
 Beim Aufrufen von **SQLSetPos**werden die folgenden Status- und Vorgangsarrays verwendet:  
  
-   Das Zeilenstatusarray (wie durch das Feld SQL_DESC_ARRAY_STATUS_PTR im IRD und im SQL_ATTR_ROW_STATUS_ARRAY-Anweisungsattribut) bezeichnet, enthält Statuswerte für jede Datenzeile im Rowset. Der Treiber legt die Statuswerte in diesem Array nach einem Aufruf von **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**oder **SQLSetPos**fest. Auf dieses Array weist das attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung hin.  
  
-   Das Zeilenoperationarray (wie vom Feld SQL_DESC_ARRAY_STATUS_PTR in der ARD und dem Attribut SQL_ATTR_ROW_OPERATION_ARRAY-Anweisung) hervorgehoben wird, enthält einen Wert für jede Zeile im Rowset, der angibt, ob ein Aufruf von **SQLSetPos** für einen Massenvorgang ignoriert oder ausgeführt wird. Jedes Element im Array wird entweder auf SQL_ROW_PROCEED (Standard) oder SQL_ROW_IGNORE festgelegt. Auf dieses Array weist das Attribut SQL_ATTR_ROW_OPERATION_PTR-Anweisung hin.  
  
 Die Anzahl der Elemente in den Status- und Vorgangsarrays muss der Anzahl der Zeilen im Rowset entsprechen (wie durch das Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung definiert).  
  
 Informationen zum Zeilenstatusarray finden Sie unter [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md). Weitere Informationen zum Zeilenoperation-Array finden Sie weiter unten in diesem Abschnitt unter "Ignorieren einer Zeile in einem Massenvorgang".  
  
## <a name="using-sqlsetpos"></a>Verwenden von SQLSetPos  
 Bevor eine Anwendung **SQLSetPos**aufruft, muss sie die folgenden Schritte ausführen:  
  
1.  Wenn die Anwendung **SQLSetPos** aufruft, wobei *der Vorgang* auf SQL_UPDATE festgelegt ist, rufen Sie **SQLBindCol** (oder **SQLSetDescRec**) für jede Spalte auf, um ihren Datentyp anzugeben und Puffer für die Daten und die Länge der Spalte zu binden.  
  
2.  Wenn die Anwendung **SQLSetPos** aufruft, wenn *der Vorgang* auf SQL_DELETE oder SQL_UPDATE festgelegt ist, rufen Sie **SQLColAttribute** auf, um sicherzustellen, dass die zu löschenden oder zu aktualisierenden Spalten aufdemweiterbar sind.  
  
3.  Rufen Sie **SQLExecDirect**, **SQLExecute**oder eine Katalogfunktion auf, um ein Resultset zu erstellen.  
  
4.  Rufen Sie **SQLFetch** oder **SQLFetchScroll** auf, um die Daten abzurufen.  
  
 Weitere Informationen zur Verwendung von **SQLSetPos**finden Sie unter [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
## <a name="deleting-data-using-sqlsetpos"></a>Löschen von Daten mithilfe von SQLSetPos  
 Um Daten mit **SQLSetPos**zu löschen, ruft eine Anwendung **SQLSetPos** auf, wobei *RowNumber* auf die Nummer der zu löschenden Zeile festgelegt ist und *der Vorgang* auf SQL_DELETE festgelegt ist.  
  
 Nachdem die Daten gelöscht wurden, ändert der Treiber den Wert im Statusarray der Implementierungszeile für die entsprechende Zeile in SQL_ROW_DELETED (oder SQL_ROW_ERROR).  
  
## <a name="updating-data-using-sqlsetpos"></a>Aktualisieren von Daten mithilfe von SQLSetPos  
 Eine Anwendung kann den Wert für eine Spalte entweder im gebundenen Datenpuffer oder mit einem oder mehreren Aufrufen von **SQLPutData**übergeben. Spalten, deren Daten mit **SQLPutData** übergeben werden, werden als *Data-at-Execution-Spalten* *columns*bezeichnet. Diese werden häufig zum Senden von Daten für SQL_LONGVARBINARY und SQL_LONGVARCHAR Spalten verwendet und können mit anderen Spalten gemischt werden.  
  
#### <a name="to-update-data-with-sqlsetpos-an-application"></a>So aktualisieren Sie Daten mit SQLSetPos, einer Anwendung:  
  
1.  Platziert Werte in den Daten- und Längen-/Indikatorpuffern, die mit **SQLBindCol**verbunden sind:  
  
    -   Bei normalen Spalten platziert die Anwendung den neuen Spaltenwert im * \*TargetValuePtr-Puffer* und die Länge dieses Werts im * \*StrLen_or_IndPtr* Puffer. Wenn die Zeile nicht aktualisiert werden soll, platziert die Anwendung SQL_ROW_IGNORE im Element des Zeilenoperationarrays dieser Zeile.  
  
    -   Für Data-at-Execution-Spalten platziert die Anwendung einen anwendungsdefinierten Wert, z. B. die Spaltennummer, im * \*TargetValuePtr-Puffer.* Der Wert kann später verwendet werden, um die Spalte zu identifizieren.  
  
         Die Anwendung platziert das Ergebnis des*SQL_LEN_DATA_AT_EXEC(Länge*) Makros im **StrLen_or_IndPtr* Puffer. Wenn der SQL-Datentyp der Spalte SQL_LONGVARBINARY, SQL_LONGVARCHAR oder ein langer datenquellenspezifischer Datentyp ist und der Treiber "Y" für den SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo**zurückgibt, ist *Länge* die Anzahl der Bytes an Daten, die für den Parameter gesendet werden sollen. Andernfalls muss es sich um einen nicht negativen Wert handelt und wird ignoriert.  
  
2.  Ruft **SQLSetPos** auf, wobei das *Argument Operation* auf SQL_UPDATE festgelegt ist, um die Datenzeile zu aktualisieren.  
  
    -   Wenn keine Data-at-Execution-Spalten vorhanden sind, ist der Vorgang abgeschlossen.  
  
    -   Wenn Daten-bei-Ausführung-Spalten vorhanden sind, gibt die Funktion SQL_NEED_DATA zurück und fährt mit Schritt 3 fort.  
  
3.  Ruft **SQLParamData** auf, um die Adresse des * \*TargetValuePtr-Puffers* für die erste zu verarbeitende Data-at-Execution-Spalte abzurufen. **SQLParamData** gibt SQL_NEED_DATA zurück. Die Anwendung ruft den anwendungsdefinierten Wert aus dem * \*TargetValuePtr-Puffer* ab.  
  
    > [!NOTE]  
    >  Obwohl die Parameter für die Ausführung von Daten bei der Ausführung den Data-at-Execution-Spalten ähneln, ist der von **SQLParamData** zurückgegebene Wert für jeden Wert unterschiedlich.  
  
    > [!NOTE]  
    >  Data-at-Execution-Parameter sind Parameter in einer SQL-Anweisung, für die Daten mit **SQLPutData** gesendet werden, wenn die Anweisung mit **SQLExecDirect** oder **SQLExecute**ausgeführt wird. Sie sind mit **SQLBindParameter** oder durch Festlegen von Deskriptoren mit **SQLSetDescRec**gebunden. Der von **SQLParamData** zurückgegebene Wert ist ein 32-Bit-Wert, der im *ParameterValuePtr-Argument* an **SQLBindParameter** übergeben wird.  
  
    > [!NOTE]  
    >  Data-at-Execution-Spalten sind Spalten in einem Rowset, für die Daten mit **SQLPutData** gesendet werden, wenn eine Zeile mit **SQLSetPos**aktualisiert wird. Sie sind mit **SQLBindCol**gebunden. Der von **SQLParamData** zurückgegebene Wert ist die Adresse der Zeile im **TargetValuePtr-Puffer,* der verarbeitet wird.  
  
4.  Ruft **SQLPutData** ein oder mehrere Male auf, um Daten für die Spalte zu senden. Es ist mehr als ein Aufruf erforderlich, wenn nicht alle Datenwerte **SQLPutData**im * \*in* SQLPutData angegebenen TargetValuePtr-Puffer zurückgegeben werden können. Mehrere Aufrufe von **SQLPutData** für dieselbe Spalte sind nur zulässig, wenn Zeichen-C-Daten an eine Spalte mit einem zeichen-, binären oder datenquellenspezifischen Datentyp gesendet werden oder wenn binäre C-Daten an eine Spalte mit einem Zeichen-, Binär- oder Datenquellentyp gesendet werden.  
  
5.  Ruft **SQLParamData** erneut auf, um zu signalisieren, dass alle Daten für die Spalte gesendet wurden.  
  
    -   Wenn mehr Data-at-Execution-Spalten vorhanden sind, gibt **SQLParamData** SQL_NEED_DATA und die Adresse des *TargetValuePtr-Puffers* für die nächste zu verarbeitende Data-at-Execution-Spalte zurück. Die Anwendung wiederholt die Schritte 4 und 5.  
  
    -   Wenn keine weiteren Data-at-Execution-Spalten vorhanden sind, ist der Vorgang abgeschlossen. Wenn die Anweisung erfolgreich ausgeführt wurde, gibt **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück. Wenn die Ausführung fehlgeschlagen ist, wird SQL_ERROR zurückgegeben. An diesem Punkt kann **SQLParamData** jede SQLSTATE zurückgeben, die von **SQLSetPos**zurückgegeben werden kann.  
  
 Wenn Daten aktualisiert wurden, ändert der Treiber den Wert im Statusarray der Implementierungszeile für die entsprechende Zeile in SQL_ROW_UPDATED.  
  
 Wenn der Vorgang abgebrochen wird oder ein Fehler in **SQLParamData** oder **SQLPutData**auftritt, nachdem **SQLSetPos** SQL_NEED_DATA zurückgegeben hat und bevor Daten für alle Data-at-Execution-Spalten gesendet werden, kann die Anwendung nur **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**oder **SQLPutData** für die Anweisung oder die mit der Anweisung verknüpfte Verbindung aufrufen. Wenn eine andere Funktion für die Anweisung oder die verbindung, die der Anweisung zugeordnet ist, aufruft, gibt die Funktion SQL_ERROR und SQLSTATE HY010 (Funktionssequenzfehler) zurück.  
  
 Wenn die Anwendung **SQLCancel** aufruft, während der Treiber weiterhin Daten für Daten-bei-Ausführung-Spalten benötigt, bricht der Treiber den Vorgang ab. Die Anwendung kann dann **SQLSetPos** erneut aufrufen. der Abbruch wirkt sich nicht auf den Cursorzustand oder die aktuelle Cursorposition aus.  
  
 Wenn die SELECT-Liste der abfragespezifikation, die dem Cursor zugeordnet ist, mehr als einen Verweis auf dieselbe Spalte enthält, ist es treiberdefiniert, ob ein Fehler generiert wird oder der Treiber die duplizierten Verweise ignoriert und die angeforderten Vorgänge ausführt.  
  
## <a name="performing-bulk-operations"></a>Ausführen von Massenvorgängen  
 Wenn das *RowNumber-Argument* 0 ist, führt der Treiber den im *Operation-Argument* angegebenen Vorgang für jede Zeile im Rowset aus, die den Wert SQL_ROW_PROCEED in ihrem Feld im Zeilenvorgangsarray hat, auf das durch SQL_ATTR_ROW_OPERATION_PTR Anweisungsattribut verwiesen wird. Dies ist ein gültiger Wert des *RowNumber-Arguments* für ein *Operation-Argument* von SQL_DELETE, SQL_REFRESH oder SQL_UPDATE, aber nicht SQL_POSITION. **SQLSetPos** mit einem *Vorgang* von SQL_POSITION und einer *RowNumber* gleich 0 gibt SQLSTATE HY109 (Ungültige Cursorposition) zurück.  
  
 Wenn ein Fehler auftritt, der sich auf das gesamte Rowset bezieht, z. B. SQLSTATE HYT00 (Timeout abgelaufen), gibt der Treiber SQL_ERROR und die entsprechende SQLSTATE zurück. Der Inhalt der Rowsetpuffer ist nicht definiert, und die Cursorposition bleibt unverändert.  
  
 Wenn ein Fehler auftritt, der sich auf eine einzelne Zeile bezieht, muss der Treiber:  
  
-   Legt das Element für die Zeile im Zeilenstatusarray fest, auf das durch das SQL_ATTR_ROW_STATUS_PTR Anweisungsattribut auf SQL_ROW_ERROR.  
  
-   Gibt eine oder mehrere zusätzliche SQLSTATEs für den Fehler in der Fehlerwarteschlange und legt das SQL_DIAG_ROW_NUMBER Feld in der Diagnosedatenstruktur fest.  
  
 Nachdem der Fehler oder die Warnung verarbeitet wurde und der Treiber den Vorgang für die verbleibenden Zeilen im Rowset abgeschlossen hat, gibt er SQL_SUCCESS_WITH_INFO zurück. Daher enthält die Fehlerwarteschlange für jede Zeile, die einen Fehler zurückgegeben hat, null oder mehr zusätzliche SQLSTATEs. Wenn der Treiber den Vorgang beendet, nachdem er den Fehler oder die Warnung verarbeitet hat, gibt er SQL_ERROR zurück.  
  
 Wenn der Treiber Warnungen zurückgibt, z. B. SQLSTATE 01004 (Daten abgeschnitten), gibt er Warnungen zurück, die für das gesamte Rowset oder für unbekannte Zeilen im Rowset gelten, bevor er die Fehlerinformationen zurückgibt, die für bestimmte Zeilen gelten. Es gibt Warnungen für bestimmte Zeilen zusammen mit anderen Fehlerinformationen zu diesen Zeilen zurück.  
  
 Wenn *RowNumber* gleich 0 ist und *Operation* SQL_UPDATE, SQL_REFRESH oder SQL_DELETE ist, wird auf die Anzahl der Zeilen verwiesen, auf die **SQLSetPos** ausgeführt wird, durch das Attribut SQL_ATTR_ROWS_FETCHED_PTR Anweisung.  
  
 Wenn *RowNumber* gleich 0 ist und *Der Vorgang* SQL_DELETE, SQL_REFRESH oder SQL_UPDATE ist, entspricht die aktuelle Zeile nach dem Vorgang der aktuellen Zeile vor dem Vorgang.  
  
## <a name="ignoring-a-row-in-a-bulk-operation"></a>Ignorieren einer Zeile in einem Massenvorgang  
 Das Zeilenoperationarray kann verwendet werden, um anzugeben, dass eine Zeile im aktuellen Rowset während eines Massenvorgangs mit **SQLSetPos**ignoriert werden soll. Um den Treiber anzuweisen, eine oder mehrere Zeilen während eines Massenvorgangs zu ignorieren, sollte eine Anwendung die folgenden Schritte ausführen:  
  
1.  Rufen Sie **SQLSetStmtAttr** auf, um das SQL_ATTR_ROW_OPERATION_PTR-Anweisungsattribut so festzulegen, dass es auf ein Array von SQLUSMALLINTs verweisen soll. Dieses Feld kann auch durch Aufrufen von **SQLSetDescField** festgelegt werden, um das SQL_DESC_ARRAY_STATUS_PTR Headerfeld der ARD festzulegen, das erfordert, dass eine Anwendung das Deskriptorhandle abruft.  
  
2.  Legen Sie jedes Element des Zeilenoperation-Arrays auf einen von zwei Werten fest:  
  
    -   SQL_ROW_IGNORE, um anzugeben, dass die Zeile für den Massenvorgang ausgeschlossen ist.  
  
    -   SQL_ROW_PROCEED, um anzugeben, dass die Zeile in den Massenvorgang einbezogen ist. (Dies ist der Standardwert.)  
  
3.  Rufen Sie **SQLSetPos** auf, um den Massenvorgang auszuführen.  
  
 Die folgenden Regeln gelten für das Zeilenoperation-Array:  
  
-   SQL_ROW_IGNORE und SQL_ROW_PROCEED wirken sich nur auf Massenvorgänge aus, die **SQLSetPos** mit einem *Vorgang* von SQL_DELETE oder SQL_UPDATE verwenden. Sie wirken sich nicht auf Aufrufe von **SQLSetPos** mit einem *Vorgang* von SQL_REFRESH oder SQL_POSITION aus.  
  
-   Der Zeiger ist standardmäßig auf null gesetzt.  
  
-   Wenn der Zeiger null ist, werden alle Zeilen aktualisiert, als ob alle Elemente auf SQL_ROW_PROCEED festgelegt wären.  
  
-   Das Festlegen eines Elements auf SQL_ROW_PROCEED garantiert nicht, dass der Vorgang in dieser bestimmten Zeile ausgeführt wird. Wenn z. B. eine bestimmte Zeile im Rowset den Status SQL_ROW_ERROR hat, kann der Treiber diese Zeile möglicherweise nicht aktualisieren, unabhängig davon, ob die angegebene Anwendung SQL_ROW_PROCEED. Eine Anwendung muss immer das Zeilenstatusarray überprüfen, um festzustellen, ob der Vorgang erfolgreich war.  
  
-   SQL_ROW_PROCEED ist in der Headerdatei als 0 definiert. Eine Anwendung kann das Zeilenoperationarray auf 0 initialisieren, um alle Zeilen zu verarbeiten.  
  
-   Wenn die Elementnummer "n" im Zeilenbetriebsarray auf SQL_ROW_IGNORE festgelegt ist und **SQLSetPos** aufgerufen wird, um einen Massenaktualisierungs- oder Löschvorgang auszuführen, bleibt die n. Zeile im Rowset nach dem Aufruf von **SQLSetPos**unverändert.  
  
-   Eine Anwendung sollte automatisch eine schreibgeschützte Spalte auf SQL_ROW_IGNORE festlegen.  
  
## <a name="ignoring-a-column-in-a-bulk-operation"></a>Ignorieren einer Spalte in einem Massenvorgang  
 Um unnötige Verarbeitungsdiagnosen zu vermeiden, die durch versuchte Aktualisierungen einer oder mehreren schreibgeschützten Spalten generiert werden, kann eine Anwendung den Wert im gebundenen Längen-/Indikatorpuffer auf SQL_COLUMN_IGNORE festlegen. Weitere Informationen finden Sie unter [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel ermöglicht eine Anwendung einem Benutzer, die Tabelle ORDERS zu durchsuchen und den Auftragsstatus zu aktualisieren. Der Cursor ist keyset-gesteuert mit einer Rowsetgröße von 20 und verwendet ein optimistisches Parallelitätssteuerelement zum Vergleich von Zeilenversionen. Nachdem jedes Rowset abgerufen wurde, druckt die Anwendung es aus und ermöglicht es dem Benutzer, den Status einer Bestellung auszuwählen und zu aktualisieren. Die Anwendung verwendet **SQLSetPos,** um den Cursor auf der ausgewählten Zeile zu positionieren, und führt eine positionierte Aktualisierung der Zeile durch. (Die Fehlerbehandlung wird aus Gründen der Übersichtlichkeit weggelassen.)  
  
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
  
 Weitere Beispiele finden Sie unter [Positionierte Aktualisierungs- und Löschanweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) und [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Massenvorgängen, die sich nicht auf die Blockcursorposition beziehen|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen eines einzelnen Feldes eines Deskriptors|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Abrufen mehrerer Felder eines Deskriptors|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen Felds eines Deskriptors|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen mehrerer Felder eines Deskriptors|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Festlegen eines Anweisungsattributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
