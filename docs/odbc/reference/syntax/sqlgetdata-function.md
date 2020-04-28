---
title: SQLGetData-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetData
helpviewer_keywords:
- SQLGetData function [ODBC]
ms.assetid: e3c1356a-5db7-4186-85fd-8b74633317e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac11505b8e47dae8df53af27c64a7ee6372b3f28
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285506"
---
# <a name="sqlgetdata-function"></a>SQLGetData-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetData** Ruft Daten für eine einzelne Spalte im Resultset oder für einen einzelnen Parameter ab, nachdem **SQLParamData** SQL_PARAM_DATA_AVAILABLE zurückgegeben hat. Sie kann mehrmals aufgerufen werden, um Daten variabler Länge in Teilen abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetData(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   Col_or_Param_Num,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_IndPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *Col_or_Param_Num*  
 Der Zum Abrufen von Spaltendaten ist dies die Nummer der Spalte, für die Daten zurückgegeben werden sollen. Die Resultsetspalten werden in steigender Spaltenreihenfolge beginnend bei 1 nummeriert. Die Lesezeichen Spalte ist die Spaltennummer 0; Dies kann nur angegeben werden, wenn Lesezeichen aktiviert sind.  
  
 Zum Abrufen von Parameterdaten ist dies die Ordnungszahl des Parameters, die bei 1 beginnt.  
  
 *TargetType*  
 Der Der Typbezeichner des C-Datentyps des **targetvalueptr* -Puffers. Eine Liste gültiger c-Datentypen und-Typbezeichner finden Sie im Abschnitt [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen.  
  
 Wenn *TargetType* SQL_ARD_TYPE ist, verwendet der Treiber den im Feld SQL_DESC_CONCISE_TYPE der ARD angegebenen Typbezeichner. Wenn *TargetType* SQL_APD_TYPE ist, verwendet **SQLGetData** denselben C-Datentyp, der in **SQLBindParameter**angegeben wurde. Andernfalls überschreibt der in **SQLGetData** angegebene c-Datentyp den in **SQLBindParameter**angegebenen c-Datentyp. Wenn Sie SQL_C_DEFAULT ist, wählt der Treiber den C-Standard Datentyp basierend auf dem SQL-Datentyp der Quelle aus.  
  
 Sie können auch einen erweiterten C-Datentyp angeben. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *Targetvalueptr*  
 Ausgeben Zeiger auf den Puffer, in den die Daten zurückgegeben werden sollen.  
  
 *Targetvalueptr* darf nicht NULL sein.  
  
 *Pufferlänge*  
 Der Länge des **targetvalueptr* -Puffers in Bytes.  
  
 Der Treiber verwendet *BufferLength* , um das Schreiben über das Ende des \* *targetvalueptr* -Puffers zu vermeiden, wenn Daten variabler Länge zurückgegeben werden, z. b. Zeichen-oder Binärdaten. Beachten Sie, dass der Treiber beim Zurückgeben von Zeichendaten an \* *targetvalueptr*das NULL-Terminierungs Zeichen zählt. **Targetvalueptr* muss daher Leerzeichen für das NULL-Terminierungs Zeichen enthalten, oder der Treiber schneidet die Daten ab.  
  
 Wenn der Treiber Daten fester Länge zurückgibt, wie z. b. eine ganze Zahl oder eine Datums Struktur, ignoriert der Treiber *BufferLength* und geht davon aus, dass der Puffer groß genug ist, um die Daten zu speichern. Daher ist es wichtig, dass die Anwendung einen ausreichend großen Puffer für Daten fester Länge zuweist oder dass der Treiber über das Ende des Puffers hinaus schreibt.  
  
 **SQLGetData** gibt SQLSTATE HY090 (ungültige Zeichen folgen-oder Pufferlänge) zurück, wenn *BufferLength* kleiner als 0 (null) ist, aber nicht, wenn *BufferLength* gleich 0 ist  
  
 *StrLen_or_IndPtr*  
 Ausgeben Zeiger auf den Puffer, in den die Länge oder der Indikator Wert zurückgegeben werden soll. Wenn dies ein NULL-Zeiger ist, wird keine Längen-oder Indikatorwerte zurückgegeben. Dadurch wird ein Fehler zurückgegeben, wenn die abgerufenen Daten NULL sind.  
  
 **SQLGetData** kann die folgenden Werte im Längen-/Indikatorpuffer zurückgeben:  
  
-   Die Länge der Daten, die zurückgegeben werden können.  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Weitere Informationen finden Sie unter [Verwenden von Längen-/indikatorenwerten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md) und "Kommentaren" in diesem Thema.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetData** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die häufig von **SQLGetData** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Nicht alle Daten für die angegebene Spalte ( *Col_or_Param_Num*) können in einem einzelnen aufrufsbefehl abgerufen werden. SQL_NO_TOTAL oder die Länge der Daten, die in der angegebenen Spalte vor dem aktuellen **SQLGetData** -Befehl verbleiben, wird \*in *StrLen_or_IndPtr*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> Weitere Informationen zur Verwendung mehrerer Aufrufe von **SQLGetData** für eine einzelne Spalte finden Sie unter "comments".|  
|01S07|Abschneiden von Sekundenbruchteilen|Die für eine oder mehrere Spalten zurückgegebenen Daten wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteile der Zahl abgeschnitten. Bei Zeit-, Zeitstempel-und Intervall Datentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|Der Datenwert einer Spalte im Resultset kann nicht in den C-Datentyp konvertiert werden, der durch das *TargetType*-Argument angegeben wird.|  
|07009|Ungültiger deskriptorindex.|Der für das Argument angegebene Wert *Col_or_Param_Num* 0 und das Attribut der SQL_ATTR_USE_BOOKMARKS Anweisung auf SQL_UB_OFF festgelegt.<br /><br /> Der für das Argument angegebene Wert *Col_or_Param_Num* war größer als die Anzahl der Spalten im Resultset.<br /><br /> Der *Col_or_Param_Num* Wert war nicht gleich der Ordinalzahl des verfügbaren Parameters.<br /><br /> (DM) die angegebene Spalte wurde gebunden. Diese Beschreibung gilt nicht für Treiber, die die SQL_GD_BOUND Bitmaske für die SQL_GETDATA_EXTENSIONS-Option in **SQLGetInfo**zurückgeben.<br /><br /> (DM) die Nummer der angegebenen Spalte ist kleiner oder gleich der Nummer der höchsten gebundenen Spalte. Diese Beschreibung gilt nicht für Treiber, die die SQL_GD_ANY_COLUMN Bitmaske für die SQL_GETDATA_EXTENSIONS-Option in **SQLGetInfo**zurückgeben.<br /><br /> (DM) die Anwendung hat bereits **SQLGetData** für die aktuelle Zeile aufgerufen. die im aktuellen-Aufrufwert angegebene Nummer der Spalte war kleiner als die Nummer der Spalte, die im vorhergehenden-Befehl angegeben wurde. der Treiber gibt die SQL_GD_ANY_ORDER Bitmaske für die SQL_GETDATA_EXTENSIONS-Option in **SQLGetInfo**nicht zurück.<br /><br /> (DM) das *TargetType* -Argument wurde SQL_ARD_TYPE, und der *Col_or_Param_Num* Deskriptordatensatz in der ARD hat die Konsistenzprüfung nicht bestanden.<br /><br /> (DM) das *TargetType* -Argument wurde SQL_ARD_TYPE, und der Wert im Feld SQL_DESC_COUNT der ARD war kleiner als das Argument *Col_or_Param_Num* .|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|22002|Die Indikator Variable ist erforderlich, aber nicht angegeben.|*StrLen_or_IndPtr* war ein NULL-Zeiger, und NULL-Daten wurden abgerufen.|  
|22003|Numerischer Wert außerhalb des zulässigen Bereichs|Das Zurückgeben des numerischen Werts (als numerisch oder Zeichenfolge) für die Spalte hätte zur Folge, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wurde.<br /><br /> Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Ungültiges datetime-Format.|Die Zeichenspalte im Resultset wurde an eine C-Datums-, Uhrzeit-oder Zeitstempel Struktur gebunden, und der Wert in der Spalte war ein ungültiges Datum, eine Uhrzeit oder ein ungültiges Zeitstempel. Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22012|Division durch Null|Ein Wert aus einem arithmetischen Ausdruck, der zur Division durch Null geführt hat, wurde zurückgegeben.|  
|22015|Überlauf des Intervall Felds|Das Zuweisen eines exakten numerischen oder Interval-SQL-Typs zu einem Interval-C-Typ verursachte den Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Beim Zurückgeben von Daten an einen Interval-c-Typ gab es keine Darstellung des Werts des SQL-Typs im Interval-c-Typ.|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|Eine Zeichenspalte im Resultset wurde an einen C-Zeichen Puffer zurückgegeben, und die Spalte enthielt ein Zeichen, für das es keine Darstellung im Zeichensatz des Puffers gab.<br /><br /> Der C-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der SQL-Typ der Spalte war ein Zeichen Datentyp. und der Wert in der Spalte war kein gültiges Literale des gebundenen C-Typs.|  
|24.000|Ungültiger Cursorstatus|(DM) die Funktion wurde aufgerufen, ohne zuerst **SQLFetch** oder **SQLFetchScroll** aufzurufen, um den Cursor in der Zeile der erforderlichen Daten zu positionieren.<br /><br /> (DM) das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.<br /><br /> Ein Cursor war auf dem *StatementHandle* geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen, aber der Cursor befand sich vor dem Anfang des Resultsets oder nach dem Ende des Resultsets.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im *MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY003|Programmtyp außerhalb des gültigen Bereichs|(DM) das Argument *TargetType* war kein gültiger Datentyp, SQL_C_DEFAULT SQL_ARD_TYPE (beim Abrufen von Spaltendaten) oder SQL_APD_TYPE (beim Abrufen von Parameterdaten).<br /><br /> (DM) das Argument *Col_or_Param_Num* 0 ist, und das Argument *TargetType* wurde für ein Lesezeichen mit fester Länge oder SQL_C_VARBOOKMARK für ein Lesezeichen mit variabler Länge nicht SQL_C_BOOKMARK.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen, und anschließend wurde die Funktion für " *StatementHandle*" erneut aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle* " von einem anderen Thread in einer Multithreadanwendung aufgerufen, und die Funktion wurde dann erneut für " *StatementHandle*" aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) das Argument *targetvalueptr* war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) das angegebene *StatementHandle* war nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute** oder eine Katalog Funktion aufzurufen.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLGetData** -Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.<br /><br /> Ein Aufruf von **sqlexeceute**, **SQLExecDirect**oder **SQLMoreResults** wurde SQL_PARAM_DATA_AVAILABLE zurückgegeben, aber **SQLGetData** wurde anstelle von **SQLParamData**aufgerufen.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der für das Argument *BufferLength* angegebene Wert war kleiner als 0 (null).<br /><br /> Der für das Argument *BufferLength* angegebene Wert war kleiner als 4, das *Col_or_Param_Num* -Argument wurde auf 0 festgelegt, und der Treiber war ein ODBC 2 *. x* -Treiber.|  
|HY109|Ungültige Cursorposition|Der Cursor wurde (von **SQLSetPos**, **SQLFetch**, **SQLFetchScroll**oder **SQLBulkOperations**) für eine Zeile positioniert, die gelöscht wurde oder nicht abgerufen werden konnte.<br /><br /> Der Cursor war ein Vorwärts Cursor, und die Rowsetgröße war größer als 1.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Der Treiber oder die Datenquelle unterstützt nicht die Verwendung von **SQLGetData** mit mehreren Zeilen in **SQLFetchScroll**. Diese Beschreibung gilt nicht für Treiber, die die SQL_GD_BLOCK Bitmaske für die SQL_GETDATA_EXTENSIONS-Option in **SQLGetInfo**zurückgeben.<br /><br /> Der Treiber oder die Datenquelle unterstützt nicht die Konvertierung, die durch die Kombination aus dem *TargetType* -Argument und dem SQL-Datentyp der entsprechenden Spalte angegeben wird. Dieser Fehler tritt nur dann auf, wenn der SQL-Datentyp der Spalte einem treiberspezifischen SQL-Datentyp zugeordnet wurde.<br /><br /> Der Treiber unterstützt nur ODBC 2 *. x*, und das Argument *TargetType* war eines der folgenden:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> und eines der in [c-Daten](../../../odbc/reference/appendixes/c-data-types.md) Typen aufgelisteten Interval c-Datentypen in Anhang D: Datentypen.<br /><br /> Der Treiber unterstützt nur ODBC-Versionen vor 3,50, und das *TargetType* -Argument wurde SQL_C_GUID.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der der *StatementHandle* entsprechende Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLGetData** gibt die Daten in einer angegebenen Spalte zurück. **SQLGetData** kann erst aufgerufen werden, nachdem eine oder mehrere Zeilen von **SQLFetch**, **SQLFetchScroll**oder **sqlextendecodfetch**aus dem Resultset abgerufen wurden. Wenn Daten variabler Länge zu groß sind, um in einem einzelnen **SQLGetData** -Befehl zurückgegeben zu werden (aufgrund einer Einschränkung in der Anwendung), kann **SQLGetData** Sie in Teilen abrufen. Es ist möglich, einige Spalten in einer Zeile zu binden und **SQLGetData** für andere aufzurufen, obwohl dies einigen Einschränkungen unterliegt. Weitere Informationen finden Sie unter [erhalten von langen Daten](../../../odbc/reference/develop-app/getting-long-data.md).  
  
 Weitere Informationen zur Verwendung von **SQLGetData** mit gestreuten Ausgabeparametern finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-sqlgetdata"></a>Verwenden von SQLGetData  
 Wenn der Treiber keine Erweiterungen von **SQLGetData**unterstützt, kann die Funktion nur Daten für ungebundene Spalten mit einer Zahl zurückgeben, die größer als die der letzten gebundenen Spalte ist. Außerdem muss in einer Daten Zeile der Wert des *Col_or_Param_Num* -Arguments in jedem **SQLGetData** -Befehl größer oder gleich dem Wert von *Col_or_Param_Num* im vorherigen-Befehl sein. Das heißt, dass Daten in steigender Reihenfolge der Spalten Nummern abgerufen werden müssen. Wenn keine Erweiterungen unterstützt werden, kann **SQLGetData** nicht aufgerufen werden, wenn die Rowsetgröße größer als 1 ist.  
  
 Treiber können diese Einschränkungen lockern. Um zu ermitteln, welche Einschränkungen ein Treiber entspannt, ruft eine Anwendung **SQLGetInfo** mit einer der folgenden SQL_GETDATA_EXTENSIONS Optionen auf:  
  
-   SQL_GD_OUTPUT_PARAMS = **SQLGetData** kann aufgerufen werden, um Ausgabeparameter Werte zurückzugeben. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_GD_ANY_COLUMN. Wenn diese Option zurückgegeben wird, kann **SQLGetData** für jede nicht gebundene Spalte aufgerufen werden, einschließlich derjenigen vor der letzten gebundenen Spalte.  
  
-   SQL_GD_ANY_ORDER. Wenn diese Option zurückgegeben wird, kann **SQLGetData** für ungebundene Spalten in beliebiger Reihenfolge aufgerufen werden.  
  
-   SQL_GD_BLOCK. Wenn diese Option von **SQLGetInfo** für den SQL_GETDATA_EXTENSIONS infotype zurückgegeben wird, unterstützt der Treiber Aufrufe von **SQLGetData** , wenn die Rowsetgröße größer als 1 ist, und die Anwendung kann **SQLSetPos** mit der SQL_POSITION-Option aufrufen, um den Cursor vor dem Aufrufen von **SQLGetData** in der richtigen Zeile zu positionieren.  
  
-   SQL_GD_BOUND. Wenn diese Option zurückgegeben wird, kann **SQLGetData** sowohl für gebundene Spalten als auch für ungebundene Spalten aufgerufen werden.  
  
 Es gibt zwei Ausnahmen für diese Einschränkungen und die Fähigkeit eines Treibers, Sie zu lockern. Zuerst sollte **SQLGetData** nie für einen Vorwärts Cursor aufgerufen werden, wenn die Rowsetgröße größer als 1 ist. Wenn ein Treiber z. b. Lesezeichen unterstützt, muss er immer die Möglichkeit unterstützen, **SQLGetData** für Spalte 0 aufzurufen, auch wenn es nicht zulässt, dass Anwendungen **SQLGetData** für andere Spalten aufrufen, bevor die letzte gebundene Spalte verwendet wird. (Wenn eine Anwendung mit einem ODBC 2 *. x* -Treiber arbeitet, gibt **SQLGetData** nach einem Aufruf von **SQLFetch**erfolgreich ein Lesezeichen zurück, wenn *Col_or_Param_Num* gleich 0 ist. da **SQLFetch** vom ODBC 3 *. x* -Treiber-Manager zu **SQLExtendedFetch** mit einem *FetchOrientation* von SQL_FETCH_NEXT zugeordnet wird und **SQLGetData** mit einem *Col_or_Param_Num* 0 vom ODBC 3 *. x* -Treiber-Manager zu **SQLGetStmtOption** mit einer *fOption* von SQL_GET_BOOKMARK zugeordnet wird.)  
  
 **SQLGetData** kann nicht zum Abrufen des Lesezeichens für eine gerade eingefügte Zeile verwendet werden, indem **SQLBulkOperations** mit der Option SQL_ADD aufgerufen wird, da der Cursor nicht in der Zeile positioniert ist. Eine Anwendung kann das Lesezeichen für eine solche Zeile abrufen, indem Sie die Spalte 0 bindet, bevor **SQLBulkOperations** mit SQL_ADD aufgerufen wird. in diesem Fall gibt **SQLBulkOperations** das Lesezeichen im gebundenen Puffer zurück. **SQLFetchScroll** kann dann mit SQL_FETCH_BOOKMARK aufgerufen werden, um den Cursor in dieser Zeile neu zu positionieren.  
  
 Wenn das *TargetType* -Argument ein Interval-Datentyp ist, werden die standardmäßige Intervall Genauigkeit (2) und die Standardgenauigkeit für Sekundenbruchteilen (6), wie in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION und SQL_DESC_PRECISION der ARD festgelegt, für die Daten verwendet. Wenn das *TargetType* -Argument ein SQL_C_NUMERIC-Datentyp ist, werden die Standardgenauigkeit (Treiber definiert) und die Standardskala (0), die in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE der ARD festgelegt sind, für die Daten verwendet. Wenn eine Standardgenauigkeit oder Dezimalstellen Angabe nicht angemessen ist, muss die Anwendung das entsprechende Deskriptorfeld explizit durch einen **SQLSetDescField** -oder **SQLSetDescRec**-Befehl festlegen. Sie kann das SQL_DESC_CONCISE_TYPE-Feld auf SQL_C_NUMERIC festlegen und **SQLGetData** mit einem *TargetType* -Argument von SQL_ARD_TYPE aufrufen, was dazu führt, dass die Genauigkeits-und Skalierungs Werte in den Deskriptorfeldern verwendet werden.  
  
> [!NOTE]
>  In ODBC 2 *. x*legen Anwendungen *TargetType* auf "SQL_C_DATE", "SQL_C_TIME" oder "SQL_C_TIMESTAMP \*" fest, um anzugeben, dass *targetvalueptr* eine Datums-, Uhrzeit-oder Zeitstempel Struktur ist. In ODBC 3 *. x*legen Anwendungen *TargetType* auf SQL_C_TYPE_DATE, SQL_C_TYPE_TIME oder SQL_C_TYPE_TIMESTAMP fest. Der Treiber-Manager nimmt ggf. geeignete Zuordnungen basierend auf der Anwendungs-und Treiber Version vor.  
  
## <a name="retrieving-variable-length-data-in-parts"></a>Abrufen von Daten variabler Länge in Teilen  
 **SQLGetData** kann zum Abrufen von Daten aus einer Spalte verwendet werden, die Daten variabler Länge enthält, d. h. wenn der Bezeichner des SQL-Datentyps der Spalte SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_WCHAR, SQL_WVARCHAR, SQL_WLONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY oder ein Treiber spezifischer Bezeichner für einen Typ variabler Länge ist.  
  
 Zum Abrufen von Daten aus einer Spalte in Teilen Ruft die Anwendung **SQLGetData** mehrmals nacheinander für dieselbe Spalte auf. Bei jedem-Befehl gibt **SQLGetData** den nächsten Teil der Daten zurück. Es liegt an der Anwendung, die Teile wieder zusammenzusetzen. dabei wird darauf geachtet, das NULL-Beendigungs Zeichen aus zwischen Teilen von Zeichendaten zu entfernen. Wenn mehr Daten zurückgegeben werden müssen oder nicht genügend Puffer für das abschließende Zeichen zugeordnet wurden, gibt **SQLGetData** SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 (Daten abgeschnitten) zurück. Wenn der letzte Teil der Daten zurückgegeben wird, gibt **SQLGetData** SQL_SUCCESS zurück. Weder SQL_NO_TOTAL noch 0 (null) können beim letzten gültigen aufrufen zum Abrufen von Daten aus einer Spalte zurückgegeben werden, da die Anwendung dann nicht weiß, wie viele der Daten im Anwendungs Puffer gültig sind. Wenn **SQLGetData** nach diesem aufgerufen wird, wird SQL_NO_DATA zurückgegeben. Weitere Informationen finden Sie im nächsten Abschnitt "Abrufen von Daten mit SQLGetData".  
  
 Lesezeichen mit variabler Länge können in Teilen von **SQLGetData**zurückgegeben werden. Wie bei anderen Daten wird beim Aufrufen von **SQLGetData** zum Zurückgeben von Lesezeichen variabler Länge in Teilen SQLSTATE 01004 (String Data, Right truncated) zurückgegeben und SQL_SUCCESS_WITH_INFO, wenn mehr Daten zurückgegeben werden müssen. Dies unterscheidet sich von der Groß-/Kleinschreibung, wenn ein Lesezeichen variabler Länge durch einen-Befehl von **SQLFetch** oder **SQLFetchScroll**abgeschnitten wird, das SQL_ERROR und SQLSTATE 22001 (Zeichen folgen Daten, rechts abgeschnitten) zurückgibt.  
  
 **SQLGetData** kann nicht zum Zurückgeben von Daten fester Länge in Teilen verwendet werden. Wenn **SQLGetData** mehr als einmal in einer Zeile für eine Spalte mit Daten fester Länge aufgerufen wird, wird SQL_NO_DATA für alle Aufrufe nach dem ersten-Wert zurückgegeben.  
  
## <a name="retrieving-streamed-output-parameters"></a>Abrufen von gestreuten Ausgabeparametern  
 Wenn ein Treiber Streaming-Ausgabeparameter unterstützt, kann eine Anwendung **SQLGetData** mehrmals mit einem kleinen Puffer aufrufen, um einen großen Parameterwert abzurufen. Weitere Informationen zum gestreuten Ausgabeparameter finden [Sie unter Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="retrieving-data-with-sqlgetdata"></a>Abrufen von Daten mit SQLGetData  
 Zum Zurückgeben von Daten für die angegebene Spalte führt **SQLGetData** die folgenden Schritte aus:  
  
1.  Gibt SQL_NO_DATA zurück, wenn bereits alle Daten für die Spalte zurückgegeben wurden.  
  
2.  Legt \* *StrLen_or_IndPtr* SQL_NULL_DATA fest, wenn die Daten NULL sind. Wenn die Daten NULL sind und *StrLen_or_IndPtr* ein NULL-Zeiger war, gibt **SQLGetData** SQLSTATE 22002 (Indikator Variable erforderlich, aber nicht angegeben) zurück.  
  
     Wenn die Daten für die Spalte nicht NULL sind, fährt **SQLGetData** mit Schritt 3 fort.  
  
3.  Wenn das SQL_ATTR_MAX_LENGTH-Anweisungs Attribut auf einen Wert ungleich 0 (null) festgelegt ist, und wenn die Spalte Zeichen-oder Binärdaten enthält und **SQLGetData** zuvor nicht für die Spalte aufgerufen wurde, werden die Daten auf SQL_ATTR_MAX_LENGTH Bytes abgeschnitten.  
  
    > [!NOTE]  
    >  Das Attribut SQL_ATTR_MAX_LENGTH Anweisung dient zum Reduzieren des Netzwerkverkehrs. Sie wird in der Regel durch die Datenquelle implementiert, wodurch die Daten abgeschnitten werden, bevor Sie über das Netzwerk zurückgegeben werden. Treiber und Datenquellen müssen nicht unterstützt werden. Um sicherzustellen, dass Daten auf eine bestimmte Größe gekürzt werden, sollte eine Anwendung daher einen Puffer dieser Größe zuordnen und die Größe im *BufferLength* -Argument angeben.  
  
4.  Konvertiert die Daten in den in *TargetType*angegebenen Typ. Die Daten erhalten die Standardgenauigkeit und-Skala für diesen Datentyp. Wenn *TargetType* SQL_ARD_TYPE ist, wird der Datentyp im Feld SQL_DESC_CONCISE_TYPE der ARD verwendet. Wenn *TargetType* SQL_ARD_TYPE ist, erhalten die Daten die Genauigkeit und Skalierung in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION und SQL_DESC_SCALE der ARD, abhängig vom Datentyp im Feld SQL_DESC_CONCISE_TYPE. Wenn eine Standardgenauigkeit oder Dezimalstellen Angabe nicht angemessen ist, muss die Anwendung das entsprechende Deskriptorfeld explizit durch einen **SQLSetDescField** -oder **SQLSetDescRec**-Befehl festlegen.  
  
5.  Wenn die Daten in einen Datentyp variabler Länge (z. b. Zeichen oder Binärdateien) konvertiert wurden, prüft **SQLGetData** , ob die Länge der Daten den Wert *BufferLength*überschreitet. Wenn die Länge der Zeichendaten (einschließlich des NULL-Beendigungs Zeichens) *BufferLength*überschreitet, verkürzt **SQLGetData** die Daten in die *BufferLength* -Länge abzüglich der Länge eines NULL-Beendigungs Zeichens. Anschließend werden die Daten von Null beendet. Wenn die Länge der Binärdaten die Länge des Daten Puffers überschreitet, wird Sie von **SQLGetData** auf die *Pufferlänge* gekürzt.  
  
     Wenn der angegebene Datenpuffer zu klein ist, um das NULL-Terminierungs Zeichen zu speichern, gibt **SQLGetData** SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 zurück.  
  
     **SQLGetData** verkürzt niemals Daten, die in Datentypen mit fester Länge konvertiert wurden. Es wird immer davon ausgegangen, dass die Länge von **targetvalueptr* die Größe des Datentyps ist.  
  
6.  Platziert die konvertierten (und möglicherweise abgeschnittene) \*Daten in " *targetvalueptr*". Beachten Sie, dass **SQLGetData** keine Daten außerhalb der Zeile zurückgeben kann.  
  
7.  Legt die Länge der Daten in \* *StrLen_or_IndPtr*ab. Wenn *StrLen_or_IndPtr* ein NULL-Zeiger war, gibt **SQLGetData** die Länge nicht zurück.  
  
    -   Für Zeichen-oder Binärdaten ist dies die Länge der Daten nach der Konvertierung und vor dem Abschneiden aufgrund von *BufferLength*. Wenn der Treiber die Länge der Daten nach der Konvertierung nicht ermitteln kann, was manchmal bei langen Daten der Fall ist, wird SQL_SUCCESS_WITH_INFO zurückgegeben und die Länge auf SQL_NO_TOTAL festgelegt. (Der letzte **SQLGetData** -Befehl muss immer die Länge der Daten zurückgeben, nicht NULL oder SQL_NO_TOTAL.) Wenn Daten aufgrund des SQL_ATTR_MAX_LENGTH Anweisungs Attributs abgeschnitten wurden, wird der Wert dieses Attributs (im Gegensatz zur tatsächlichen Länge) in \* *StrLen_or_IndPtr*platziert. Dies liegt daran, dass dieses Attribut so konzipiert ist, dass Daten auf dem Server vor der Konvertierung abgeschnitten werden, sodass der Treiber nicht ermitteln kann, was die tatsächliche Länge ist. Wenn **SQLGetData** mehrmals nacheinander für dieselbe Spalte aufgerufen wird, ist dies die Länge der Daten, die zu Beginn des aktuellen Aufrufs verfügbar sind. Das heißt, die Länge wird bei jedem nachfolgenden-Aufrufwert verringert.  
  
    -   Bei allen anderen Datentypen ist dies die Länge der Daten nach der Konvertierung. Das heißt, es ist die Größe des Typs, in den die Daten konvertiert wurden.  
  
8.  Wenn die Daten während der Konvertierung ohne Bedeutungsverlust abgeschnitten werden (z. b. wenn die reelle Zahl 1,234 beim Konvertieren in die ganze Zahl 1 abgeschnitten wird) oder weil *BufferLength* zu klein ist (z. b. wird die Zeichenfolge "abcdef" in einen 4-Byte-Puffer eingefügt), gibt **SQLGetData** SQLSTATE 01004 (abgeschnittene Daten) und SQL_SUCCESS_WITH_INFO Wenn Daten aufgrund des SQL_ATTR_MAX_LENGTH Anweisungs Attributs ohne Bedeutungsverlust abgeschnitten werden, gibt **SQLGetData** SQL_SUCCESS zurück und gibt nicht SQLSTATE 01004 (abgeschnittene Daten) zurück.  
  
 Der Inhalt des gebundenen Daten Puffers (wenn **SQLGetData** für eine gebundene Spalte aufgerufen wird), und der Längen-/Indikatorpuffer ist nicht definiert, wenn **SQLGetData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO nicht zurückgibt.  
  
 Bei aufeinander folgenden Aufrufen von **SQLGetData** werden Daten aus der letzten angeforderten Spalte abgerufen. vorherige Offsets werden ungültig. Wenn z. b. die folgende Sequenz ausgeführt wird:  
  
```cpp  
SQLGetData(icol=n), SQLGetData(icol=m), SQLGetData(icol=n)  
```  
  
 beim zweiten SQLGetData (iCol = n)-Befehl werden Daten vom Anfang der n-Spalte abgerufen. Jeder Offset in den Daten aufgrund früherer Aufrufe von **SQLGetData** für die Spalte ist nicht mehr gültig.  
  
## <a name="descriptors-and-sqlgetdata"></a>Deskriptoren und SQLGetData  
 **SQLGetData** interagiert nicht direkt mit den Deskriptorfeldern.  
  
 Wenn *TargetType* SQL_ARD_TYPE ist, wird der Datentyp im Feld SQL_DESC_CONCISE_TYPE der ARD verwendet. Wenn *TargetType* entweder SQL_ARD_TYPE oder SQL_C_DEFAULT ist, erhalten die Daten die Genauigkeit und Skalierung in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION und SQL_DESC_SCALE der ARD, abhängig vom Datentyp im Feld SQL_DESC_CONCISE_TYPE.  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel führt eine Anwendung eine **Select** -Anweisung aus, um ein Resultset der Kunden-IDs,-Namen und Telefonnummern nach Name, ID und Telefonnummer sortiert zurückzugeben. Für jede Daten Zeile wird **SQLFetch** aufgerufen, um den Cursor in der nächsten Zeile zu positionieren. Er ruft **SQLGetData** auf, um die abgerufenen Daten abzurufen. die Puffer für die Daten und die zurückgegebene Anzahl von Bytes werden im **SQLGetData**-aufrufswert angegeben. Schließlich druckt Sie den Namen, die ID und die Telefonnummer der einzelnen Mitarbeiter.  
  
```cpp  
#define NAME_LEN 50  
#define PHONE_LEN 50  
  
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];  
SQLINTEGER   sCustID, cbName, cbAge, cbBirthday;  
SQLRETURN    retcode;  
SQLHSTMT     hstmt;  
  
retcode = SQLExecDirect(hstmt,  
   "SELECT CUSTID, NAME, PHONE FROM CUSTOMERS ORDER BY 2, 1, 3",  
   SQL_NTS);  
  
if (retcode == SQL_SUCCESS) {  
   while (TRUE) {  
      retcode = SQLFetch(hstmt);  
      if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO) {  
         show_error();  
      }  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){  
  
         /* Get data for columns 1, 2, and 3 */  
  
         SQLGetData(hstmt, 1, SQL_C_ULONG, &sCustID, 0, &cbCustID);  
         SQLGetData(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
         SQLGetData(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN,  
            &cbPhone);  
  
         /* Print the row of data */  
  
         fprintf(out, "%-5d %-*s %*s", sCustID, NAME_LEN-1, szName,   
            PHONE_LEN-1, szPhone);  
      } else {  
         break;  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Zuweisen von Speicher für eine Spalte in einem Resultset|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Massen Vorgängen, die sich nicht auf die Position des Block Cursors beziehen|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen einer einzelnen Daten Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Senden von Parameterdaten zur Ausführungszeit|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset oder aktualisieren oder Löschen von Daten im Rowset|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Header Dateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
