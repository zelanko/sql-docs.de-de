---
title: SQLFetch-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5c5d2d14786080f665e488acf2bfa888f09a5df4
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345197"
---
# <a name="sqlfetch-function"></a>SQLFetch-Funktion
**Konformitäts**  
 Eingeführte Version: Konformität der ODBC 1,0-Standards: ISO 92  
  
 **Zusammenfassung**  
 **SQLFetch** Ruft das nächste Rowset von Daten aus dem Resultset ab und gibt Daten für alle gebundenen Spalten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFetch(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFetch** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem die [SQLGetDiagRec-Funktion](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) mit dem Handlertyp SQL_HANDLE_STMT und einem *handle* von  *StatementHandle aufgerufen wird.* . In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLFetch** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, lautet SQL_ERROR, sofern nichts anderes angegeben ist. Wenn ein Fehler in einer einzelnen Spalte auftritt, kann [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) mit einem *DiagIdentifier* von SQL_DIAG_COLUMN_NUMBER aufgerufen werden, um die Spalte zu bestimmen, in der der Fehler aufgetreten ist. und **SQLGetDiagField** können mit einem *DiagIdentifier* von SQL_DIAG_ROW_NUMBER aufgerufen werden, um die Zeile zu ermitteln, die diese Spalte enthält.  
  
 Für alle Sqlstates, die SQL_SUCCESS_WITH_INFO oder SQL_ERROR (außer 01xxx Sqlstates) zurückgeben können, wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn ein Fehler in einer oder mehreren, aber nicht in allen Zeilen eines mehr Zeilen Vorgangs auftritt, und SQL_ERROR zurückgegeben wird, wenn ein Fehler in einem Einzel Zeilen Vorgang.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Zeichen folgen-oder Binärdaten, die für eine Spalte zurückgegeben wurden, ergaben das Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind. Wenn es sich um einen Zeichen folgen Wert handelt, wurde er rechts abgeschnitten.|  
|01S01|Fehler in Zeile|Fehler beim Abrufen einer oder mehrerer Zeilen.<br /><br /> (Wenn dieser SQLSTATE zurückgegeben wird, wenn eine ODBC 3 *. x* -Anwendung mit einem ODBC 2 *. x* -Treiber arbeitet, kann er ignoriert werden.)|  
|01S07|Abschneiden von Sekundenbruchteilen|Die für eine Spalte zurückgegebenen Daten wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteile der Zahl abgeschnitten. Bei Zeit-, Zeitstempel-und Intervall Datentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|Der Datenwert einer Spalte im Resultset konnte nicht in den Datentyp konvertiert werden, der von *TargetType* in **SQLBindCol**festgelegt wurde.<br /><br /> Die Spalte 0 wurde mit dem Datentyp SQL_C_BOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut wurde auf SQL_UB_VARIABLE festgelegt.<br /><br /> Die Spalte 0 wurde mit dem Datentyp SQL_C_VARBOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut wurde nicht auf SQL_UB_VARIABLE festgelegt.|  
|07009|Ungültiger deskriptorindex.|Der Treiber war ein ODBC 2 *. x* -Treiber, der **SQLExtendedFetch**nicht unterstützt, und eine in der Bindung für eine Spalte angegebene Spaltennummer war 0.<br /><br /> Die Spalte 0 wurde gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungs Attribut wurde auf SQL_UB_OFF festgelegt.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|22001|Zeichen folgen Daten, rechts abgeschnitten|Ein Lesezeichen variabler Länge, das für eine Spalte zurückgegeben wurde, wurde abgeschnitten.|  
|22002|Die Indikator Variable ist erforderlich, aber nicht angegeben.|NULL-Daten wurden in eine Spalte abgerufen, deren *StrLen_or_IndPtr* von **SQLBindCol** (oder SQL_DESC_INDICATOR_PTR festgelegt von **SQLSetDescField** oder **SQLSetDescRec**) ein NULL-Zeiger war.|  
|22003|Numerischer Wert außerhalb des zulässigen Bereichs|Das Zurückgeben des numerischen Werts als numerisch oder Zeichenfolge für eine oder mehrere gebundene Spalten hätte dazu geführt, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wird.<br /><br /> Weitere Informationen finden Sie unter "Daten [Typen aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) " in Anhang D: Datentypen.|  
|22007|Ungültiges datetime-Format.|Eine Zeichenspalte im Resultset wurde an eine Datums-, Uhrzeit-oder Zeitstempel-C-Struktur gebunden, und ein Wert in der Spalte war, bzw. ein ungültiges Datum, eine Uhrzeit oder ein ungültiger Zeitstempel.|  
|22012|Division durch Null|Es wurde ein Wert aus einem arithmetischen Ausdruck zurückgegeben, der zu einer Division durch 0 geführt hat.|  
|22015|Überlauf des Intervall Felds|Das Zuweisen eines exakten numerischen oder Interval-SQL-Typs zu einem Interval-C-Typ verursachte den Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Beim Abrufen von Daten in einen Interval-c-Typ gab es keine Darstellung des Werts des SQL-Typs im Interval-c-Typ.|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|Eine Zeichenspalte im Resultset wurde an einen C-Zeichen Puffer gebunden, und die Spalte enthielt ein Zeichen, für das es keine Darstellung im Zeichensatz des Puffers gab.<br /><br /> Der C-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der SQL-Typ der Spalte war ein Zeichen Datentyp. und der Wert in der Spalte war kein gültiges Literale des gebundenen C-Typs.|  
|24000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.|  
|40001|Serialisierungsfehler|Die Transaktion, in der der Abruf ausgeführt wurde, wurde beendet, um einen Deadlock zu verhindern.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im  *\*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die **SQLFetch** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die **SQLFetch** -Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Oder die **SQLFetch** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLFetch** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und hat SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) das angegebene *StatementHandle* war nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute** oder eine Katalog Funktion aufzurufen.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) **SQLFetch** wurde für das *StatementHandle* aufgerufen, nachdem **SQLExtendedFetch** aufgerufen wurde und bevor **SQLFreeStmt** mit der SQL_CLOSE-Option aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|Das SQL_ATTR_USE_BOOKMARK-Anweisungs Attribut wurde auf SQL_UB_VARIABLE festgelegt, und die Spalte 0 wurde an einen Puffer gebunden, dessen Länge nicht der maximalen Länge für das Lesezeichen für dieses Resultset entspricht. (Diese Länge ist im SQL_DESC_OCTET_LENGTH-Feld von IRD verfügbar und kann durch Aufrufen von **SQLDescribeCol**, **SQLColAttribute**oder **SQLGetDescField**abgerufen werden.)|  
|HY107|Zeilen Wert außerhalb des zulässigen Bereichs|Der mit dem SQL_ATTR_CURSOR_TYPE-Anweisungs Attribut angegebene Wert war SQL_CURSOR_KEYSET_DRIVEN, aber der mit dem SQL_ATTR_KEYSET_SIZE-Anweisungs Attribut angegebene Wert war größer als 0 und kleiner als der mit SQL_ATTR_ROW_ARRAY_ angegebene Wert. Size-Anweisungs Attribut.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Der Treiber oder die Datenquelle unterstützt nicht die Konvertierung, die durch die Kombination von *TargetType* in **SQLBindCol** und dem SQL-Datentyp der entsprechenden Spalte angegeben wird.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von SQLSetStmtAttr, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLFetch** gibt das nächste Rowset im Resultset zurück. Sie kann nur aufgerufen werden, wenn ein Resultset vorhanden ist, d. h. nach einem Aufruf, der ein Resultset erstellt und vor dem Cursor über diesem Resultset geschlossen wird. Wenn Spalten gebunden sind, werden die Daten in diesen Spalten zurückgegeben. Wenn die Anwendung einen Zeiger auf ein Zeilen Status Array oder einen Puffer angegeben hat, in dem die Anzahl der abgerufenen Zeilen zurückgegeben werden soll, gibt **SQLFetch** diese Informationen ebenfalls zurück. Aufrufe von **SQLFetch** können mit Aufrufen von **SQLFetchScroll** gemischt, jedoch nicht mit Aufrufen von **SQLExtendedFetch**gemischt werden. Weitere Informationen finden Sie unter [Abrufen einer Daten Zeile](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 Wenn eine ODBC 3 *. x* -Anwendung mit einem ODBC 2 *. x* -Treiber funktioniert, ordnet der Treiber-Manager SQLFetch-Aufrufe **SQLExtendedFetch** für einen ODBC 2 *. x* -Treiber zu, der **SQLExtendedFetch**unterstützt. Wenn der ODBC 2 *. x* -Treiber **SQLExtendedFetch**nicht unterstützt, ordnet der Treiber-Manager SQLFetch **-Aufrufe** **SQLFetch** im ODBC 2 *. x* -Treiber zu, der nur eine einzelne Zeile abrufen kann.  
  
 Weitere Informationen finden Sie unter [Blockieren von Cursorn, scrollfähigen Cursorn und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiber Richtlinien für die Abwärtskompatibilität.  
  
## <a name="positioning-the-cursor"></a>Positionieren des Cursors  
 Wenn das Resultset erstellt wird, wird der Cursor vor dem Anfang des Resultsets positioniert. **SQLFetch** Ruft das nächste Rowset ab. Dies entspricht dem Aufrufen von **SQLFetchScroll** , bei dem *FetchOrientation* auf SQL_FETCH_NEXT festgelegt ist. Weitere Informationen zu Cursorn finden Sie unter [Cursor](../../../odbc/reference/develop-app/cursors.md) und [Blockcursorn](../../../odbc/reference/develop-app/block-cursors.md).  
  
 Das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungs Attribut gibt die Anzahl der Zeilen im Rowset an. Wenn das Rowset, das von **SQLFetch** abgerufen wird, das Ende des Resultsets überlappt, gibt **SQLFetch** ein partielles Rowset zurück. Das heißt, wenn s + R-1 größer als L ist, wobei s die Anfangs Zeile des abgerufenen Rowsets ist, R die Rowsetgröße und L die letzte Zeile im Resultset ist, dann sind nur die ersten L-S + 1 Zeilen des Rowsets gültig. Die verbleibenden Zeilen sind leer und weisen den Status SQL_ROW_NOROW auf.  
  
 Nachdem **SQLFetch** zurückgegeben wurde, ist die aktuelle Zeile die erste Zeile des Rowsets.  
  
 Die in der folgenden Tabelle aufgeführten Regeln beschreiben die Cursor Positionierung nach einem **SQLFetch**-Aufrufs, basierend auf den Bedingungen, die in der zweiten Tabelle in diesem Abschnitt aufgeführt sind.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|Vor dem Start|1|  
|*Currrowsetstart* Lastresultrow *-rowsetsize*[1] \< = |*Currrowsetstart* + -*rowsetsize*[2]|  
|*Currrowsetstart* > *lastresultrow-rowsetsize*[1]|Nach dem Ende|  
|Nach dem Ende|Nach dem Ende|  
  
 [1] Wenn die Rowsetgröße zwischen den Abruf Vorgängen geändert wird, ist dies die Rowsetgröße, die mit dem vorherigen Abruf Vorgang verwendet wurde.  
  
 [2] Wenn die Rowsetgröße zwischen den Abruf Vorgängen geändert wird, ist dies die Rowsetgröße, die mit dem neuen Abruf Vorgang verwendet wurde.  
  
|Notation|Bedeutung|  
|--------------|-------------|  
|Vor dem Start|Der Block Cursor befindet sich vor dem Anfang des Resultsets. Wenn sich die erste Zeile des neuen Rowsets vor dem Anfang des Resultsets befindet, gibt **SQLFetch** SQL_NO_DATA zurück.|  
|Nach dem Ende|Der Block Cursor befindet sich hinter dem Ende des Resultsets. Wenn sich die erste Zeile des neuen Rowsets hinter das Ende des Resultsets befindet, gibt **SQLFetch** SQL_NO_DATA zurück.|  
|*CurrRowsetStart*|Die Nummer der ersten Zeile im aktuellen Rowset.|  
|*Lastresultrow*|Die Nummer der letzten Zeile im Resultset.|  
|*Rowsetsize*|Die Rowsetgröße.|  
  
 Nehmen wir beispielsweise an, ein Resultset hat 100 Zeilen, und die Rowsetgröße beträgt 5. In der folgenden Tabelle werden das von **SQLFetch** zurückgegebene Rowset und der Rückgabecode für unterschiedliche Startpositionen angezeigt.  
  
|Aktuelles Rowset|Rückgabecode|Neues Rowset|Anzahl der abgerufenen Zeilen|  
|--------------------|-----------------|----------------|------------------------|  
|Vor dem Start|SQL_SUCCESS|1 bis 5|5|  
|1 bis 5|SQL_SUCCESS|6 bis 10|5|  
|52 bis 56|SQL_SUCCESS|57 bis 61|5|  
|91 bis 95|SQL_SUCCESS|96 bis 100|5|  
|93 bis 97|SQL_SUCCESS|98 bis 100. Die Zeilen 4 und 5 des Rows-Status Arrays werden auf SQL_ROW_NOROW festgelegt.|3|  
|96 bis 100|SQL_NO_DATA|Keine|0|  
|99 bis 100|SQL_NO_DATA|Keine|0|  
|Nach dem Ende|SQL_NO_DATA|Keine|0|  
  
## <a name="returning-data-in-bound-columns"></a>Zurückgeben von Daten in gebundenen Spalten  
 Wenn **SQLFetch** jede Zeile zurückgibt, werden die Daten für jede gebundene Spalte im Puffer, der an diese Spalte gebunden ist, eingefügt. Wenn keine Spalten gebunden sind, gibt **SQLFetch** keine Daten zurück, sondern verschiebt den Block Cursor vorwärts. Die Daten können weiterhin mithilfe von **SQLGetData**abgerufen werden. Wenn der Cursor ein mehr zeiliges Cursor ist (d. h., der SQL_ATTR_ROW_ARRAY_SIZE ist größer als 1), kann **SQLGetData** nur aufgerufen werden, wenn "SQL_GD_BLOCK" zurückgegeben wird, wenn " **SQLGetInfo** " mit dem *InfoType* "SQL_GETDATA_EXTENSIONS" aufgerufen wird. (Weitere Informationen finden Sie unter [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).)  
  
 Für jede gebundene Spalte in einer Zeile führt **SQLFetch** Folgendes aus:  
  
1.  Legt den Längen-/indikatorenpuffer auf SQL_NULL_DATA fest und geht mit der nächsten Spalte fort, wenn die Daten NULL sind. Wenn die Daten NULL sind und kein Längen-/Indikatorpuffer gebunden wurde, gibt **SQLFetch** SQLSTATE 22002 (Indikator Variable erforderlich, aber nicht angegeben) für die Zeile zurück und geht mit der nächsten Zeile fort. Informationen dazu, wie Sie die Adresse des Längen-/Indikatorpuffers ermitteln, finden Sie unter "Puffer Adressen" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
     Wenn die Daten für die Spalte nicht NULL sind, fährt **SQLFetch** mit Schritt 2 fort.  
  
2.  Wenn das SQL_ATTR_MAX_LENGTH-Anweisungs Attribut auf einen Wert ungleich 0 (null) festgelegt ist und die Spalte Zeichen-oder Binärdaten enthält, werden die Daten auf SQL_ATTR_MAX_LENGTH Byte gekürzt.  
  
    > [!NOTE]  
    >  Das SQL_ATTR_MAX_LENGTH-Anweisungs Attribut dient dazu, den Netzwerk Datenverkehr zu reduzieren. Sie wird in der Regel durch die Datenquelle implementiert, wodurch die Daten abgeschnitten werden, bevor Sie über das Netzwerk zurückgegeben werden. Treiber und Datenquellen müssen nicht unterstützt werden. Um sicherzustellen, dass Daten auf eine bestimmte Größe gekürzt werden, sollte eine Anwendung daher einen Puffer dieser Größe zuordnen und die Größe im *cbvaluemax* -Argument in **SQLBindCol**angeben.  
  
3.  Konvertiert die Daten in den Typ, der von *TargetType* in **SQLBindCol**angegeben wird.  
  
4.  Wenn die Daten in einen Datentyp variabler Länge (z. b. Zeichen oder Binärdateien) konvertiert wurden, prüft **SQLFetch** , ob die Länge der Daten die Länge des Daten Puffers überschreitet. Wenn die Länge der Zeichendaten (einschließlich des NULL-Beendigungs Zeichens) die Länge des Daten Puffers überschreitet, verkürzt **SQLFetch** die Daten auf die Länge des Daten Puffers abzüglich der Länge eines NULL-Beendigungs Zeichens. Anschließend werden die Daten von Null beendet. Wenn die Länge der Binärdaten die Länge des Daten Puffers überschreitet, verkürzt **SQLFetch** Sie auf die Länge des Daten Puffers. Die Länge des Daten Puffers wird mit *BufferLength* in **SQLBindCol**angegeben.  
  
     **SQLFetch** verkürzt niemals Daten, die in Datentypen mit fester Länge konvertiert wurden. Dabei wird immer davon ausgegangen, dass die Länge des Daten Puffers die Größe des Datentyps ist.  
  
5.  Versetzt die konvertierten (und möglicherweise abgeschnittene) Daten in den Datenpuffer. Informationen dazu, wie Sie die Adresse des Daten Puffers ermitteln, finden Sie unter "Puffer Adressen" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
6.  Legt die Länge der Daten im Längen-/Indikatorpuffer ab. Wenn der Indikator Zeiger und der Längen Zeiger beide auf denselben Puffer festgelegt wurden (wie es beim Aufrufen von **SQLBindCol** der gibt), wird die Länge im Puffer für gültige Daten geschrieben, und SQL_NULL_DATA wird im Puffer für NULL-Daten geschrieben. Wenn kein Längen-/Indikatorpuffer gebunden wurde, gibt **SQLFetch** die Länge nicht zurück.  
  
    -   Für Zeichen-oder Binärdaten ist dies die Länge der Daten nach der Konvertierung und vor dem Abschneiden, weil der Datenpuffer zu klein ist. Wenn der Treiber die Länge der Daten nach der Konvertierung nicht ermitteln kann, wie es bei Long-Daten der Fall ist, wird die Länge auf SQL_NO_TOTAL festgelegt. Wenn Daten aufgrund des SQL_ATTR_MAX_LENGTH-Anweisungs Attributs abgeschnitten wurden, wird der Wert dieses Attributs anstelle der tatsächlichen Länge in den Längen-/Indikatorpuffer eingefügt. Dies liegt daran, dass dieses Attribut so konzipiert ist, dass Daten auf dem Server vor der Konvertierung abgeschnitten werden, damit der Treiber nicht ermitteln kann, was die tatsächliche Länge ist.  
  
    -   Bei allen anderen Datentypen ist dies die Länge der Daten nach der Konvertierung. Das heißt, es ist die Größe des Typs, in den die Daten konvertiert wurden.  
  
     Informationen dazu, wie Sie die Adresse des Längen-/Indikatorpuffers ermitteln, finden Sie unter "Puffer Adressen" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
7.  Wenn die Daten während der Konvertierung abgeschnitten werden, ohne dass signifikante Ziffern verloren gehen (z. b. wird die reelle Zahl 1,234 bei der Konvertierung auf die Ganzzahl 1 gekürzt), gibt **SQLFetch** SQLSTATE 01s07 (Bruchteil der Dezimalstellen) und SQL_SUCCESS_WITH_INFO zurück. Wenn die Daten abgeschnitten werden, weil die Länge des Daten Puffers zu klein ist (z. b. wird die Zeichenfolge "abcdef" in einen 4-Byte-Puffer eingefügt), gibt **SQLFetch** SQLSTATE 01004 (abgeschnittene Daten) und SQL_SUCCESS_WITH_INFO zurück. Wenn Daten aufgrund des SQL_ATTR_MAX_LENGTH-Anweisungs Attributs abgeschnitten werden, gibt **SQLFetch** SQL_SUCCESS zurück und gibt nicht SQLSTATE 01s07 (Bruchteil der Bruchteil) oder SQLSTATE 01004 (abgeschnittene Daten) zurück. Wenn Daten während der Konvertierung mit einem Verlust signifikanter Ziffern abgeschnitten werden (z. b. Wenn ein SQL_INTEGER-Wert, der größer als 100.000 ist, in einen SQL_C_TINYINT-Wert konvertiert wurde), gibt **SQLFetch** SQLSTATE 22003 (numerischer Wert außerhalb des gültigen Bereichs) und SQL_ERROR zurück (wenn die die Rowsetgröße ist 1) oder SQL_SUCCESS_WITH_INFO (wenn die Rowsetgröße größer als 1 ist).  
  
 Der Inhalt des gebundenen Daten Puffers und der Länge/Indikator Puffer sind nicht definiert, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt.  
  
## <a name="row-status-array"></a>Zeilenstatusarray  
 Das Array Row Status wird verwendet, um den Status der einzelnen Zeilen im Rowset zurückzugeben. Die Adresse dieses Arrays wird mit dem SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut angegeben. Das Array wird von der Anwendung zugeordnet und muss über so viele Elemente verfügen, wie Sie durch das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungs Attribut angegeben werden. Die Werte werden von **SQLFetch**, **SQLFetchScroll**und **SQLBulkOperations** oder **SQLSetPos** festgelegt (außer wenn Sie aufgerufen wurden, nachdem der Cursor von **SQLExtendedFetch**positioniert wurde). Wenn der Wert des SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attributs ein NULL-Zeiger ist, geben diese Funktionen den Zeilen Status nicht zurück.  
  
 Der Inhalt des Zeilen Status-Array Puffers ist nicht definiert, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt.  
  
 Die folgenden Werte werden im Zeilen Status-Array zurückgegeben.  
  
|Array Wert für Zeilen Status|Beschreibung|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|Die Zeile wurde erfolgreich abgerufen und wurde nicht geändert, seit Sie zuletzt aus diesem Resultset abgerufen wurde.|  
|SQL_ROW_SUCCESS_WITH_INFO|Die Zeile wurde erfolgreich abgerufen und wurde nicht geändert, seit Sie zuletzt aus diesem Resultset abgerufen wurde. Es wurde jedoch eine Warnung zur Zeile zurückgegeben.|  
|SQL_ROW_ERROR|Fehler beim Abrufen der Zeile.|  
|SQL_ROW_UPDATED [1], [2] und [3]|Die Zeile wurde erfolgreich abgerufen und geändert, seit Sie zuletzt aus diesem Resultset abgerufen wurde. Wenn die Zeile erneut aus diesem Resultset abgerufen oder von **SQLSetPos**aktualisiert wird, wird der Status in den neuen Status der Zeile geändert.|  
|SQL_ROW_DELETED[3]|Die Zeile wurde gelöscht, seit Sie zuletzt aus diesem Resultset abgerufen wurde.|  
|SQL_ROW_ADDED[4]|Die Zeile wurde von **SQLBulkOperations**eingefügt. Wenn die Zeile erneut aus diesem Resultset abgerufen oder von **SQLSetPos**aktualisiert wird, lautet der Status SQL_ROW_SUCCESS.|  
|SQL_ROW_NOROW|Das Rowset hat das Ende des Resultsets überlappen, und es wurde keine Zeile zurückgegeben, die diesem Element des Zeilen Status Arrays entsprach.|  
  
 [1] für Keyset-, Mixed-und Dynamic-Cursor wird die Daten Zeile als gelöscht angesehen und eine neue Zeile hinzugefügt, wenn ein Schlüsselwert aktualisiert wird.  
  
 [2] Einige Treiber können keine Updates für Daten erkennen und können daher diesen Wert nicht zurückgeben. Um zu ermitteln, ob ein Treiber Updates für wiederholte Zeilen erkennen kann, ruft eine Anwendung **SQLGetInfo** mit der SQL_ROW_UPDATES-Option auf.  
  
 [3] **SQLFetch** kann diesen Wert nur zurückgeben, wenn er mit Aufrufen von **SQLFetchScroll**gemischt ist. Dies liegt daran, dass **SQLFetch** durch das Resultset vorwärts bewegt wird und wenn es exklusiv verwendet wird, ruft keine Zeilen erneut ab. Da keine Zeilen erneut abgerufen werden, erkennt **SQLFetch** keine Änderungen, die an zuvor abgerufenen Zeilen vorgenommen wurden. Wenn jedoch **SQLFetchScroll** den Cursor vor zuvor abgerufenen Zeilen positioniert und **SQLFetch** zum Abrufen dieser Zeilen verwendet wird, kann **SQLFetch** alle Änderungen an diesen Zeilen erkennen.  
  
 [4] nur von SQLBulkOperations zurückgegeben. Nicht von **SQLFetch** oder **SQLFetchScroll**festgelegt.  
  
### <a name="rows-fetched-buffer"></a>Abgerufene Zeilen Puffer  
 Der Puffer "abgerufene Zeilen" wird verwendet, um die Anzahl der abgerufenen Zeilen zurückzugeben, einschließlich der Zeilen, für die keine Daten zurückgegeben wurden, weil beim Abrufen ein Fehler aufgetreten ist. Das heißt, es ist die Anzahl der Zeilen, für die der Wert im Zeilen Status Array nicht SQL_ROW_NOROW ist. Die Adresse dieses Puffers wird mit dem SQL_ATTR_ROWS_FETCHED_PTR-Anweisungs Attribut angegeben. Der Puffer wird von der Anwendung zugeordnet. Sie wird von **SQLFetch** und **SQLFetchScroll**festgelegt. Wenn der Wert des SQL_ATTR_ROWS_FETCHED_PTR-Anweisungs Attributs ein NULL-Zeiger ist, geben diese Funktionen nicht die Anzahl der abgerufenen Zeilen zurück. Um die Nummer der aktuellen Zeile im Resultset zu ermitteln, kann eine Anwendung **SQLGetStmtAttr** mit dem SQL_ATTR_ROW_NUMBER-Attribut aufrufen.  
  
 Der Inhalt des Puffers zum Abrufen von Zeilen ist nicht definiert, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt, es sei denn, es wird SQL_NO_DATA zurückgegeben. in diesem Fall wird der Wert im Puffer "Zeilen abgerufen" auf "0" festgelegt.  
  
### <a name="error-handling"></a>Fehlerbehandlung  
 Fehler und Warnungen können auf einzelne Zeilen oder auf die gesamte Funktion angewendet werden. Weitere Informationen zu Diagnosedaten Sätzen finden Sie unter [Diagnostics](../../../odbc/reference/develop-app/diagnostics.md) und [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
#### <a name="errors-and-warnings-on-the-entire-function"></a>Fehler und Warnungen für die gesamte Funktion  
 Wenn für die gesamte Funktion ein Fehler auftritt, z. b. SQLSTATE HYT00 (Timeout abgelaufen) oder SQLSTATE 24000 (Ungültiger Cursor Zustand), gibt **SQLFetch** SQL_ERROR und den anwendbaren SQLSTATE zurück. Der Inhalt der rowsetpuffer ist nicht definiert, und die Cursorposition bleibt unverändert.  
  
 Wenn eine Warnung für die gesamte Funktion gilt, gibt **SQLFetch** SQL_SUCCESS_WITH_INFO und den anwendbaren SQLSTATE zurück. Die Statusdaten Sätze für Warnungen, die auf die gesamte Funktion zutreffen, werden vor den Statusdaten Sätzen zurückgegeben, die für einzelne Zeilen gelten.  
  
#### <a name="errors-and-warnings-in-individual-rows"></a>Fehler und Warnungen in einzelnen Zeilen  
 Wenn ein Fehler (z. b. SQLSTATE 22012 (Division durch null)) oder eine Warnung (z. b. SQLSTATE 01004 (abgeschnittene Daten)) auf eine einzelne Zeile angewendet wird, führt **SQLFetch**Folgendes aus:  
  
-   Legt das entsprechende Element des Zeilen Status Arrays auf SQL_ROW_ERROR für Fehler oder SQL_ROW_SUCCESS_WITH_INFO auf Warnungen fest.  
  
-   Fügt NULL oder mehr Statusdaten Sätze hinzu, die SQLStates für den Fehler oder die Warnung enthalten.  
  
-   Legt die Zeilen-und Spalten Nummern Felder in den Statusdaten Sätzen fest. Wenn **SQLFetch** eine Zeilen-oder Spaltennummer nicht bestimmen kann, wird diese Zahl auf SQL_ROW_NUMBER_UNKNOWN bzw. SQL_COLUMN_NUMBER_UNKNOWN festgelegt. Wenn der Statusdaten Satz für eine bestimmte Spalte nicht gilt, legt **SQLFetch** die Spaltennummer auf SQL_NO_COLUMN_NUMBER fest.  
  
 **SQLFetch** setzt das Abrufen von Zeilen fort, bis alle Zeilen im Rowset abgerufen wurden. Sie gibt SQL_SUCCESS_WITH_INFO zurück, es sei denn, es tritt ein Fehler in jeder Zeile des Rowsets auf (ohne die Zeilen mit dem Status SQL_ROW_NOROW). in diesem Fall wird SQL_ERROR zurückgegeben. Insbesondere, wenn die Rowsetgröße 1 beträgt und in dieser Zeile ein Fehler auftritt, gibt **SQLFetch** SQL_ERROR zurück.  
  
 **SQLFetch** gibt die Statusdaten Sätze in der Reihenfolge der Zeilennummern zurück. Das heißt, es werden alle Statusdaten Sätze für unbekannte Zeilen (sofern vorhanden) zurückgegeben. Anschließend werden alle Statusdaten Sätze für die erste Zeile (sofern vorhanden) zurückgegeben, und anschließend werden alle Statusdaten Sätze für die zweite Zeile (sofern vorhanden) zurückgegeben. Die Statusdaten Sätze für jede Zeile werden nach den normalen Regeln zum Anordnen von Statusdaten Sätzen geordnet. Weitere Informationen finden Sie unter "Sequenz von Status Datensätzen" in [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
### <a name="descriptors-and-sqlfetch"></a>Deskriptoren und SQLFetch  
 In den folgenden Abschnitten wird beschrieben, wie **SQLFetch** mit Deskriptoren interagiert.  
  
#### <a name="argument-mappings"></a>Argument Zuordnungen  
 Der Treiber legt keine Deskriptorfelder auf der Grundlage der Argumente von **SQLFetch**fest.  
  
#### <a name="other-descriptor-fields"></a>Andere Deskriptorfelder  
 Die folgenden Deskriptorfelder werden von **SQLFetch**verwendet.  
  
|Deskriptorfeld|DESC.|Feld in|Festgelegt durch|  
|----------------------|-----------|--------------|-----------------|  
|SQL_DESC_ARRAY_SIZE|ARD|Header|SQL_ATTR_ROW_ARRAY_SIZE-Anweisungs Attribut|  
|SQL_DESC_ARRAY_STATUS_PTR|IRD|Header|SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut|  
|SQL_DESC_BIND_OFFSET_PTR|ARD|Header|SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungs Attribut|  
|SQL_DESC_BIND_TYPE|ARD|Header|SQL_ATTR_ROW_BIND_TYPE-Anweisungs Attribut|  
|SQL_DESC_COUNT|ARD|Header|*ColumnNumber* -Argument von **SQLBindCol**|  
|SQL_DESC_DATA_PTR|ARD|Best|*Targetvalueptr* -Argument von **SQLBindCol**|  
|SQL_DESC_INDICATOR_PTR|ARD|Best|*StrLen_or_IndPtr* -Argument in **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH|ARD|Best|*BufferLength* -Argument in **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH_PTR|ARD|Best|*StrLen_or_IndPtr* -Argument in **SQLBindCol**|  
|SQL_DESC_ROWS_PROCESSED_PTR|IRD|Header|SQL_ATTR_ROWS_FETCHED_PTR-Anweisungs Attribut|  
|SQL_DESC_TYPE|ARD|Best|*TargetType* -Argument in **SQLBindCol**|  
  
 Alle Deskriptorfelder können auch über **SQLSetDescField**festgelegt werden.  
  
#### <a name="separate-length-and-indicator-buffers"></a>Separate Längen-und Indikator Puffer  
 Anwendungen können einen einzelnen Puffer oder zwei separate Puffer binden, die zum Speichern der Längen-und Indikatorwerte verwendet werden können. Wenn eine Anwendung **SQLBindCol**aufruft, legt der Treiber die Felder SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_INDICATOR_PTR der ARD auf die gleiche Adresse fest, die im *StrLen_or_IndPtr* -Argument weitergegeben wird. Wenn eine Anwendung **SQLSetDescField** oder **SQLSetDescRec**aufruft, können diese beiden Felder auf verschiedene Adressen festgelegt werden.  
  
 **SQLFetch** bestimmt, ob die Anwendung separate Längen-und Indikator Puffer angegeben hat. Wenn die Daten in diesem Fall nicht NULL sind, legt **SQLFetch** den Indikator Puffer auf 0 fest und gibt die Länge im Längenpuffer zurück. Wenn die Daten NULL sind, legt **SQLFetch** den Indikator Puffer auf SQL_NULL_DATA fest und ändert nicht den Längenpuffer.  
  
### <a name="code-example"></a>Codebeispiel  
 Siehe [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)und [SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md).  
  
### <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Schließen des Cursors in der Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Abrufen eines Teils oder aller Datenspalten|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Zurückgeben der Anzahl von Resultsetspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
