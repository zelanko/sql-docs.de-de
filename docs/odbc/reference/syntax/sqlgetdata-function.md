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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0dc0e57356c972797cbd72fa4ce3427a0e473dad
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538000"
---
# <a name="sqlgetdata-function"></a>SQLGetData-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetData** Ruft Daten für eine einzelne Spalte im Resultset oder für einen einzelnen Parameter nach **SQLParamData** SQL_PARAM_DATA_AVAILABLE zurückgibt. Es kann mehrere Male aufgerufen werden zum Abrufen von Daten mit variabler Länge in Teilen.  
  
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
 [Eingabe] Anweisungshandle.  
  
 *Col_or_Param_Num*  
 [Eingabe] Zum Abrufen von Daten der Spalte, ist es die Anzahl der Spalte, für die Daten zurückgegeben werden sollen. Resultset-Spalten werden in zunehmenden Reihenfolge von Spalten beginnend mit 1 nummeriert. Die Lesezeichenspalte ist die Nummer der Spalte 0; Dies liegt möglicherweise nur angegeben werden, wenn Lesezeichen aktiviert sind.  
  
 Zum Abrufen von Daten von Parametern, ist es die Ordnungszahl des Parameters, der bei 1 beginnt.  
  
 *TargetType*  
 [Eingabe] Der Typ-ID für die C-Datentyp, der die **TargetValuePtr* Puffer. Eine Liste der gültigen C-Datentypen und Typ-IDs, finden Sie unter den [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) Abschnitt in Anhang D: Datentypen.  
  
 Wenn *TargetType* SQL_ARD_TYPE, verwendet der Treiber, die Typ-ID im Feld SQL_DESC_CONCISE_TYPE der ARD angegeben, ist. Wenn *TargetType* ist SQL_APD_TYPE, **SQLGetData** verwendet die gleichen C-Datentyp, der im angegebenen **SQLBindParameter**. Andernfalls die C-Datentyp angegeben, **SQLGetData** überschreibt die C-Datentyp, der im angegebenen **SQLBindParameter**. Wenn es sich um SQL_C_DEFAULT ist, wählt der Treiber die Standard-C-Datentyp basierend auf dem SQL-Datentyp, der die Quelle an.  
  
 Sie können auch einen erweiterte C-Datentyp angeben. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *TargetValuePtr*  
 [Ausgabe] Zeiger auf den Puffer, in dem die Daten zurückgeben.  
  
 *TargetValuePtr* darf nicht NULL sein.  
  
 *BufferLength*  
 [Eingabe] Länge der **TargetValuePtr* Puffers in Byte.  
  
 Der Treiber verwendet *Pufferlänge* zu schreiben, die nach dem Ende zu vermeiden der \* *TargetValuePtr* beim Zurückgeben von Daten mit variabler Länge, wie z. B. Zeichen- oder Binärdaten gepuffert werden sollen. Beachten Sie, dass der Treiber die Null-Terminierungszeichen zählt, bei der Rückgabe von Zeichendaten in \* *TargetValuePtr*. **TargetValuePtr* darf daher Speicherplatz für die Null-Terminierungszeichen, oder der Treiber werden die Daten abgeschnitten.  
  
 Beenden der Treiber Daten fester Länge, z. B. eine ganze Zahl oder einen Datumsstruktur, ignoriert der Treiber die *Pufferlänge* und nimmt an, dass der Puffer groß genug zum Speichern der Daten. Daher ist es wichtig, für die Anwendung einen ausreichenden Puffer für Daten fester Länge zugewiesen werden, oder der Treiber wird nach dem Ende des Puffers geschrieben.  
  
 **SQLGetData** SQLSTATE HY090 zurückgegeben (ungültige Zeichenfolgen- oder Pufferlänge.) Wenn *Pufferlänge* ist kleiner als 0, aber nicht, wenn *Pufferlänge* ist 0.  
  
 *StrLen_or_IndPtr*  
 [Ausgabe] Zeiger auf den Puffer, in dem die Länge bzw. der Indikatorwert Wert zurückgegeben. Wenn dies ein null-Zeiger ist, wird keine Länge bzw. der Indikatorwert Wert zurückgegeben. Dadurch wird ein Fehler zurückgegeben, wenn die abgerufenen Daten NULL sind.  
  
 **SQLGetData** können die folgenden Werte in den Längen-/Indikatorpuffer zurück:  
  
-   Die Länge der zurückzugebenden verfügbaren Daten  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Weitere Informationen finden Sie unter [mit Längenindikator/Werten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md) und "Kommentare" in diesem Thema.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetData** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, zurück ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und eine *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLGetData** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Nicht alle Daten für die angegebene Spalte *Col_or_Param_Num*, in einem einzigen Aufruf der Funktion abgerufen werden konnte. SQL_NO_TOTAL oder die Länge der Daten in der angegebenen Spalte vor dem aktuellen Aufruf verbleibenden **SQLGetData** wird zurückgegeben, \* *StrLen_or_IndPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> Weitere Informationen zur Verwendung von mehreren Aufrufen an **SQLGetData** finden Sie eine einzelne Spalte "Kommentare".|  
|01S07|Teilbereiche wurden abgeschnitten|Die Daten, die für eine oder mehrere Spalten zurückgegeben wurden abgeschnitten. Für numerische Datentypen wurde die Nachkommastellen der Zahl abgeschnitten. Für die Zeit, Zeitstempel und Interval-Datentypen, die eine Komponente enthält wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|Der Datenwert einer Spalte im Resultset kann nicht konvertiert werden, in den C-Datentyp, der durch das Argument angegebenen *TargetType*.|  
|07009|Ungültiger Deskriptorindex|Der angegebene Wert für das Argument *Col_or_Param_Num* wurde 0 und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF festgelegt wurde.<br /><br /> Der angegebene Wert für das Argument *Col_or_Param_Num* war größer als die Anzahl der Spalten im Resultset.<br /><br /> Die *Col_or_Param_Num* Wert war nicht gleich auf die Ordnungszahl des Parameters, der verfügbar ist.<br /><br /> (DM) die angegebene Spalte gebunden. Diese Beschreibung wird nicht für Treiber, die die Bitmaske SQL_GD_BOUND SQL_GETDATA_EXTENSIONS Option wird im zurückgeben **SQLGetInfo**.<br /><br /> Die Anzahl der angegebenen Spalte (DM) war kleiner als oder gleich der Anzahl der gebundenen Spalte mit der höchsten. Diese Beschreibung wird nicht für Treiber, die die Bitmaske SQL_GD_ANY_COLUMN SQL_GETDATA_EXTENSIONS Option wird im zurückgeben **SQLGetInfo**.<br /><br /> (DM) die Anwendung wurde bereits aufgerufen. **SQLGetData** der aktuellen Zeile; die Anzahl der im aktuellen Aufruf angegebenen Spalte war kleiner als die Anzahl der in den vorherigen Aufruf angegebenen Spalte und der Treiber gibt nicht den SQL_ zurück GD_ANY_ORDER Bitmaske für die Option SQL_GETDATA_EXTENSIONS in **SQLGetInfo**.<br /><br /> (DM) die *TargetType* Argument war SQL_ARD_TYPE, und die *Col_or_Param_Num* anwendungsparameterdeskriptor-Datensatz in die ARD Fehler bei der konsistenzprüfung.<br /><br /> (DM) die *TargetType* Argument SQL_ARD_TYPE, und der Wert im Feld SQL_DESC_COUNT der ARD war kleiner als der *Col_or_Param_Num* Argument.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|22002|Anzeigevariable erforderlich, aber nicht angegeben|*StrLen_or_IndPtr* wurde ein null-Zeiger, und NULL-Daten abgerufen wurde.|  
|22003|Numerischer Wert außerhalb des gültigen Bereichs|Den numerischen Wert (als numerisch oder Zeichenfolge) zurückgegeben, für die Spalte wird den gesamten (im Gegensatz zu Bruch) Teil der Zahl abgeschnitten wird verursacht.<br /><br /> Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Ungültiges Datetime-format|Die Zeichenspalte im Resultset wurde an eine C-Datum, Uhrzeit oder Zeitstempel-Struktur gebunden, und der Wert in der Spalte wurde ein ungültiges Datum, Uhrzeit oder Zeitstempel. Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22012|Division durch 0 (null)|Es wurde ein Wert aus einem arithmetischen Ausdruck mit der Division durch 0 (null) zurückgegeben.|  
|22015|Überlauf bei Intervallfeld|Intervalltyp C aus einer genauen numerischen oder Intervall SQL-Typ zuweisen, verursacht einen Verlust signifikanter Ziffern im Feld führende.<br /><br /> Beim Zurückgeben von Daten in ein C-Intervalltyp, gab es keine Darstellung des Werts von der SQL-Typ in den Intervalltyp C.|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|Im Resultset eine Spalte mit dem Zeichen, die auf einen Zeichenpuffer C zurückgegeben wurde, und die Spalte enthalten, ein Zeichen, die für die gab es keine Entsprechung in den Zeichensatz des Puffers.<br /><br /> Der C-Typ war eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp. der SQL-Typ der Spalte konnte einen Zeichendatentyp; und kein Wert in der Spalte wurde ein gültiger Literal des gebundenen Typen aus C#.|  
|24000|Ungültiger Cursorstatus|(DM) die Funktion wurde aufgerufen, ohne den ersten Aufruf **SQLFetch** oder **SQLFetchScroll** zur Positionierung des Cursors in der Zeile mit Daten, die erforderlich sind.<br /><br /> (DM) die *StatementHandle* wurde in einem ausgeführten Zustand befindet, aber kein Resultset zugeordnet wurde die *StatementHandle*.<br /><br /> Ein Cursor geöffnet, auf war der *StatementHandle* und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde, aber der Cursor positioniert wurde, vor dem Start des Resultsets oder nach der das Ende des Resultsets.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die *MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY003|Typ des Programms außerhalb des gültigen Bereichs|(DM) das Argument *TargetType* war keinen gültigen Datentyp, SQL_C_DEFAULT, SQL_ARD_TYPE (im Falle von Abrufen von Spaltendaten) oder SQL_APD_TYPE (im Falle von Abrufen von Parameterdaten).<br /><br /> (DM) das Argument *Col_or_Param_Num* wurde 0 und das Argument *TargetType* war nicht SQL_C_BOOKMARK für ein Lesezeichen mit fester Länge oder SQL_C_VARBOOKMARK für ein Lesezeichen variabler Länge.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*, und klicken Sie dann die Funktion aufgerufen wurde erneut auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung, und klicken Sie dann die Funktion wurde erneut aufgerufen, auf die *StatementHandle*.|  
|HY009|Ungültige Verwendung eines null-Zeiger|(DM) das Argument *TargetValuePtr* wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) der angegebenen *StatementHandle* war nicht in einem ausgeführten Zustand befindet. Die Funktion wurde aufgerufen, ohne den ersten Aufruf **SQLExecDirect**, **SQLExecute** oder einer Katalogfunktion.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLGetData** Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) die *StatementHandle* wurde in einem ausgeführten Zustand befindet, aber kein Resultset zugeordnet wurde die *StatementHandle*.<br /><br /> Ein Aufruf von **SQLExeceute**, **SQLExecDirect**, oder **SQLMoreResults** zurückgegebenen SQL_PARAM_DATA_AVAILABLE, aber **SQLGetData** aufgerufen wurde , anstelle von **SQLParamData**.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) für Argument angegebene Wert *Pufferlänge* war kleiner als 0.<br /><br /> Für Argument angegebene Wert *Pufferlänge* kleiner als 4 wurde die *Col_or_Param_Num* Argument auf 0 festgelegt wurde, und der Treiber wurde von einer ODBC 2.*.x* Treiber.|  
|HY109|Ungültige Cursorposition|Der Cursor positioniert wurde (durch **SQLSetPos**, **SQLFetch**, **SQLFetchScroll**, oder **SQLBulkOperations**) in einer Zeile, die gelöscht wurde oder konnte nicht abgerufen werden.<br /><br /> Der Cursor wurde ein Vorwärtscursor, und die Rowsetgröße war größer als 1.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Treiber oder die Datenquelle unterstützt keine Verwendung von **SQLGetData** mit mehreren Zeilen in **SQLFetchScroll**. Diese Beschreibung wird nicht für Treiber, die die Bitmaske SQL_GD_BLOCK SQL_GETDATA_EXTENSIONS Option wird im zurückgeben **SQLGetInfo**.<br /><br /> Die Treiber oder die Datenquelle unterstützt nicht die Konvertierung angegeben wird, durch die Kombination der *TargetType* Argument und der SQL-Datentyp der entsprechenden Spalte. Dieser Fehler tritt nur bei der SQL-Datentyp der Spalte mit einem treiberspezifischen SQL-Datentyp zugeordnet war.<br /><br /> Der Treiber unterstützt nur ODBC 2.*.x*, und das Argument *TargetType* war eines der folgenden:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> und keines der Intervalldatentypen C im [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen.<br /><br /> Der Treiber unterstützt nur die ODBC-Versionen vor, und das Argument zum Preis von 3,50 *TargetType* SQL_C_GUID wurde.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber entspricht der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLGetData** gibt die Daten in einer angegebenen Spalte zurück. **SQLGetData** kann aufgerufen werden, erst nach einer oder mehreren Zeilen aus dem Resultset von abgerufen wurden **SQLFetch**, **SQLFetchScroll**, oder **SQLExtendedFetch**. Wenn Daten mit variabler Länge zu groß, um in einem einzelnen Aufruf zurückgegeben werden **SQLGetData** (aufgrund einer Einschränkung in der Anwendung) **SQLGetData** in Teilen abrufen können. Es ist möglich, einige Spalten in einer Zeile und der Aufruf binden **SQLGetData** für andere, obwohl dies unterliegt einigen Einschränkungen ist. Weitere Informationen finden Sie unter [Abrufen von Long-Daten](../../../odbc/reference/develop-app/getting-long-data.md).  
  
 Informationen zur Verwendung **SQLGetData** mit gestreamte Output-Parameter finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-sqlgetdata"></a>Mithilfe von SQLGetData  
 Wenn der Treiber keine Erweiterungen unterstützt **SQLGetData**, die Funktion kann zurückgeben nur Daten für ungebundene Spalten mit einer Zahl größer ist als der letzten gebundenen Spalte. Darüber hinaus in eine Zeile mit Daten, die den Wert des der *Col_or_Param_Num* Argument in jedem Aufruf von **SQLGetData** muss größer als oder gleich dem Wert des *Col_or_Param_Num*in den vorherigen Aufruf d. h. müssen Daten abgerufen werden, in aufsteigender Reihenfolge für die Anzahl der Spalten. Schließlich, wenn keine Erweiterungen unterstützt, **SQLGetData** kann nicht aufgerufen werden, wenn die Rowsetgröße größer als 1 ist.  
  
 Treiber können diese Einschränkungen lockern. Um zu bestimmen, welche Einschränkungen lockert die Treiber, eine Anwendung ruft **SQLGetInfo** mit einem der folgenden SQL_GETDATA_EXTENSIONS Optionen:  
  
-   SQL_GD_OUTPUT_PARAMS = **SQLGetData** aufgerufen werden, um die Werte der Ausgabeparameter zurückgeben. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_GD_ANY_COLUMN. Wenn diese Option zurückgegeben wird, **SQLGetData** kann bei jeder ungebundenen Spalte, einschließlich der vor der letzten Spalte gebundenen aufgerufen werden.  
  
-   SQL_GD_ANY_ORDER. Wenn diese Option zurückgegeben wird, **SQLGetData** für ungebundene Spalten in einer beliebigen Reihenfolge aufgerufen werden können.  
  
-   SQL_GD_BLOCK. Wenn diese Option aus, die von zurückgegeben wird **SQLGetInfo** für die Informationsart SQL_GETDATA_EXTENSIONS unterstützt der Treiber Aufrufe **SQLGetData** Wenn die Rowsetgröße größer als 1 ist, und die Anwendung kann **SQLSetPos** mit der Option SQL_POSITION zur Positionierung des Cursors in der richtigen Zeile vor dem Aufruf **SQLGetData.**  
  
-   SQL_GD_BOUND. Wenn diese Option zurückgegeben wird, **SQLGetData** kann aufgerufen werden, für die gebundenen Spalten als auch von nicht gebundenen Spalten.  
  
 Es gibt zwei Ausnahmen von dieser Einschränkungen sowie des Treibers Möglichkeit, diese zu lockern. Zuerst **SQLGetData** sollte nie für einen vorwärtsgerichteten Cursor aufgerufen werden, wenn die Rowsetgröße größer als 1 ist. Zweitens: Wenn ein Treiber Lesezeichen unterstützt, es muss immer unterstützen die Möglichkeit zum Aufrufen **SQLGetData** für die Spalte 0 ist, auch wenn dies nicht zulässt, dass Anwendungen Aufrufen **SQLGetData** für andere Spalten vor dem letzten gebundene Spalte. (Wenn eine Anwendung mit einer ODBC 2. arbeitet *.x* Treiber **SQLGetData** gibt erfolgreich ein Lesezeichen, die bei einem Aufruf mit *Col_or_Param_Num* gleich 0, nach einem Aufruf von **SQLFetch**, da **SQLFetch** wird zugeordnet, indem die ODBC 3.*.x* Treiber-Manager, um **SQLExtendedFetch** mit einem  *FetchOrientation* sql_fetch_next, und **SQLGetData** mit einem *Col_or_Param_Num* 0 wird zugeordnet, indem die ODBC 3.*.x* Treiber-Manager zu **SQLGetStmtOption** mit einer *fOption* von SQL_GET_BOOKMARK.)  
  
 **SQLGetData** kann nicht verwendet werden, um das Lesezeichen für eine Zeile, die durch den Aufruf das soeben eingefügt rufen **SQLBulkOperations** mit der Option sql_add, da sich der Cursor nicht in der Zeile positioniert ist. Eine Anwendung kann das Lesezeichen für eine solche Zeile abrufen, durch Bindung Spalte 0 vor dem Aufruf **SQLBulkOperations** mit SQL_ADD, in diesem Fall **SQLBulkOperations** das Lesezeichen in den gebundenen Puffer zurückgegeben. **SQLFetchScroll** kann dann aufgerufen werden, mit sql_fetch_bookmark auf, um den Cursor in dieser Zeile zu verschieben.  
  
 Wenn die *TargetType* Argument ist ein Intervall Datentyp für die standardmäßige Intervall führende Genauigkeit (2) und die standardmäßige Intervall Sekunden Genauigkeit (6), wie in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION und SQL_DESC_PRECISION des festgelegt die ARD sind verwendet bzw. für die Daten. Wenn die *TargetType* Argument ist ein SQL_C_NUMERIC-Datentyp, der die standardmäßige Genauigkeit von (treiberdefinierten) und Standard skalieren (0), wie in die Felder der ARD SQL_DESC_PRECISION und SQL_DESC_SCALE festgelegt, für die Daten verwendet werden. Wenn alle Standardwerte für die Genauigkeit oder Dezimalstellenanzahl nicht geeignet ist, die Anwendung sollte explizit festlegen der entsprechenden Deskriptorfeld durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**. Er kann das Feld "SQL_DESC_CONCISE_TYPE" festgelegt, auf SQL_C_NUMERIC, und rufen **SQLGetData** mit eine *TargetType* Argument SQL_ARD_TYPE, der die Genauigkeit und Dezimalstellenanzahl Werte in die deskriptorfelder verursacht verwendet werden.  
  
> [!NOTE]
>  In ODBC 2.*.x*, Anwendungen legen *TargetType* SQL_C_DATE, SQL_C_TIME oder SQL_C_TIMESTAMP an, dass \* *TargetValuePtr* ist ein Datum und die Uhrzeit oder Timestamp-Struktur. In ODBC 3.*.x*, Anwendungen legen *TargetType* SQL_C_TYPE_DATE, SQL_C_TYPE_TIME oder SQL_C_TYPE_TIMESTAMP. Der Treiber-Manager macht passenden Zuordnungen bei Bedarf basierend auf der Anwendungs- und Treiberinstallation-Version.  
  
## <a name="retrieving-variable-length-data-in-parts"></a>Abrufen von Daten mit variabler Länge in Teilen  
 **SQLGetData** kann zum Abrufen von Daten aus einer Spalte, die Daten mit variabler Länge in Teilen –, also enthält, wenn der Bezeichner der dem SQL-Datentyp der Spalte SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_WCHAR, SQL_WVARCHAR, SQL_ ist verwendet werden WLONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY oder ein Treiber-spezifischen Bezeichner für einen Typ mit variabler Länge.  
  
 Ruft die Anwendung zum Abrufen von Daten aus einer Spalte in Teilen **SQLGetData** mehrmals hintereinander für dieselbe Spalte. Bei jedem Aufruf **SQLGetData** gibt zurück, den nächsten Teil der Daten. Es ist Aufgabe der Anwendung, die Teile, die Null-Terminierungszeichen aus intermediate Teilen von Zeichendaten entfernen wieder zusammensetzen. Wenn weitere Daten, die zurückgegeben wird oder nicht genügend Puffer für das abschließende Zeichen, belegt wurde **SQLGetData** SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 (Daten wurden abgeschnitten). Bei der Rückgabe des letzten Teils der Daten **SQLGetData** gibt SQL_SUCCESS zurück. Weder SQL_NO_TOTAL als auch 0 (null) kann auf dem letzten gültigen Aufruf zum Abrufen von Daten aus einer Spalte, zurückgegeben werden, da die Anwendung dann, dass keine Möglichkeit festzustellen müsste, welcher Anteil der Daten in den Anwendungspuffer gültig ist. Wenn **SQLGetData** wird aufgerufen, anschließend, es gibt SQL_NO_DATA zurück. Weitere Informationen finden Sie im nächsten Abschnitt, "Abrufen von Daten mit SQLGetData".  
  
 Lesezeichen mit variabler Länge zurückgegeben werden können, in Schritten von **SQLGetData**. Wie bei anderen Daten, die einen Aufruf von **SQLGetData** zurückzugebenden variabler Länge, die Lesezeichen in Teilen gibt SQLSTATE 01004 (Zeichenfolgendaten, rechts abgeschnitten) und SQL_SUCCESS_WITH_INFO zurück, wenn weitere Daten zurückgegeben werden. Dies ist die Groß-/Kleinschreibung unterscheiden, wenn ein Lesezeichen variabler Länge, durch einen Aufruf von abgeschnitten wird **SQLFetch** oder **SQLFetchScroll**, womit SQL_ERROR und SQLSTATE 22001 (Zeichenfolgendaten, rechts abgeschnitten).  
  
 **SQLGetData** kann nicht in Teilen die zurückzugebenden Daten fester Länge verwendet werden. Wenn **SQLGetData** ist mehr als einmal in einer Zeile für eine Spalte mit fester Länge aufgerufen, es gibt SQL_NO_DATA zurück, für alle Aufrufe nach dem ersten.  
  
## <a name="retrieving-streamed-output-parameters"></a>Abrufen von Ausgabeparametern gestreamte  
 Wenn ein Treiber gestreamte Output-Parameter unterstützt, kann eine Anwendung aufrufen **SQLGetData** mit einem kleinen Puffer oft einen großen Parameterwert abzurufen. Weitere Informationen zu Stream Output-Parameter, finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="retrieving-data-with-sqlgetdata"></a>Abrufen von Daten mit SQLGetData  
 Daten für die angegebene Spalte zurückgeben **SQLGetData** führt die folgende Sequenz von Schritten:  
  
1.  Gibt SQL_NO_DATA zurück, wenn sie bereits alle Daten für die Spalte zurückgegeben wurden.  
  
2.  Legt \* *StrLen_or_IndPtr* auf SQL_NULL_DATA, wenn die Daten NULL sind. Wenn die Daten NULL sind und *StrLen_or_IndPtr* wurde ein null-Zeiger **SQLGetData** SQLSTATE 22002 (Indikatorvariable erforderlich, aber nicht angegeben) zurückgibt.  
  
     Wenn die Daten für die Spalte nicht NULL ist, **SQLGetData** fährt Sie fort mit Schritt 3 fort.  
  
3.  Wenn das SQL_ATTR_MAX_LENGTH-Anweisungsattribut auf einen Wert ungleich NULL festgelegt ist, wenn die Spalte enthält, Zeichen- oder Binärdaten darstellen und **SQLGetData** zuvor nicht aufgerufen wurde für die Spalte, die Daten auf SQL_ATTR_MAX_LENGTH abgeschnitten Bytes.  
  
    > [!NOTE]  
    >  Das Anweisungsattribut SQL_ATTR_MAX_LENGTH soll den Netzwerkverkehr zu reduzieren. Es ist in der Regel von der Datenquelle implementiert, die die Daten abgeschnitten werden, bevor Sie Sie über das Netzwerk zurückgeben. Treibern und Datenquellen sind nicht erforderlich, um es zu unterstützen. Aus diesem Grund, um sicherzustellen, dass Daten, um eine bestimmte Größe abgeschnitten werden, eine Anwendung sollte ein Puffer dieser Größe und geben Sie die Größe in der *Pufferlänge* Argument.  
  
4.  Konvertiert die Daten in den Typ im angegebenen *TargetType*. Die Daten erhält die standardmäßige Genauigkeit und Dezimalstellenanzahl für diesen Datentyp. Wenn *TargetType* ist SQL_ARD_TYPE, die Daten in das Feld "SQL_DESC_CONCISE_TYPE" die ARD wird verwendet. Wenn *TargetType* SQL_ARD_TYPE ist, die Daten die Genauigkeit und Dezimalstellen in der SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION, angegeben werden und SQL_DESC_SCALE Felder der ARD, abhängig von den Daten zu geben, in der SQL_DESC_CONCISE _Typ-Feld. Wenn alle Standardwerte für die Genauigkeit oder Dezimalstellenanzahl nicht geeignet ist, die Anwendung sollte explizit festlegen der entsprechenden Deskriptorfeld durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**.  
  
5.  Wenn die Daten in ein variabler Länge, Datentyp, z. B. oder binärzeichenfolgenkonstante konvertiert wurde **SQLGetData** überprüft, ob die Länge der Daten überschreitet *Pufferlänge*. Überschreitet die Länge der Zeichendaten enthalten sind (einschließlich der Null-Terminierungszeichen) *Pufferlänge*, **SQLGetData** schneidet die Daten in *Pufferlänge* weniger die Länge von einer Null-Terminierungszeichen. Es terminiert Null-klicken Sie dann die Daten. Die Länge des binären Daten überschreitet die Länge des Datenpuffers **SQLGetData** schneidet, *Pufferlänge* Bytes.  
  
     Wenn der angegebene Datenpuffer zu klein für die Null-Terminierungszeichen ist **SQLGetData** SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 zurückgegeben.  
  
     **SQLGetData** nie abgeschnitten. Daten, der in-Daten fester Länge Typen konvertiert; es immer setzt voraus, dass die Länge des **TargetValuePtr* ist die Größe des Datentyps.  
  
6.  Die konvertierte (und möglicherweise abgeschnitten) zurückgegebenen Daten in \* *TargetValuePtr*. Beachten Sie, dass **SQLGetData** können keine Daten aus der Zeile zurück.  
  
7.  Legt die Länge der Daten in \* *StrLen_or_IndPtr*. Wenn *StrLen_or_IndPtr* wurde ein null-Zeiger **SQLGetData** gibt nicht die Länge zurück.  
  
    -   Für Zeichen- oder Binärdaten, dies ist die Länge der Daten nach der Konvertierung und vor der Kürzung aufgrund von *Pufferlänge*. Wenn der Treiber die Länge der Daten nach der Konvertierung nicht ermitteln kann als manchmal bei long-Daten der Fall ist, gibt SQL_SUCCESS_WITH_INFO zurück und legt die Länge um SQL_NO_TOTAL fest. (Dem letzten Aufruf von **SQLGetData** muss immer die Länge der Daten, nicht 0 (null) oder SQL_NO_TOTAL zurück.) Wenn Daten aufgrund der SQL_ATTR_MAX_LENGTH-Anweisungsattribut abgeschnitten wurde, befindet sich der Wert dieses Attributs - im Gegensatz zu die tatsächliche Länge: \* *StrLen_or_IndPtr*. Dies ist dieses Attribut ist darauf ausgelegt, zum Abschneiden von Daten auf dem Server vor der Konvertierung, damit der Treiber keine Möglichkeit herauszufinden hat, welche die tatsächliche Länge ist. Wenn **SQLGetData** ist die gleiche Spalte mehrmals nacheinander aufgerufen, dies ist die Länge der Daten, die zu Beginn des aktuellen Aufrufs zur Verfügung, d. h., die Länge verringert mit jedem nachfolgenden Aufruf.  
  
    -   Für alle anderen Datentypen ist dies die Länge der Daten, nach der Konvertierung; Das heißt, ist es die Größe des Typs, der die Daten konvertiert wurden.  
  
8.  Wenn die Daten ohne Verlust von "significance" während der Konvertierung abgeschnitten werden (z. B. die reelle Zahl-1,234 wird abgeschnitten, wenn auf die ganze Zahl 1 konvertiert) oder weil *Pufferlänge* ist zu klein (z. B. die Zeichenfolge "Abcdef" befindet in einem 4-Byte-Puffer) **SQLGetData** SQLSTATE 01004 (Daten wurden abgeschnitten) und SQL_SUCCESS_WITH_INFO zurückgegeben. Wenn Daten, ohne Verlust von "significance", aufgrund der Anweisungsattribut SQL_ATTR_MAX_LENGTH abgeschnitten werden **SQLGetData** gibt SQL_SUCCESS zurück, und gibt keinen SQLSTATE 01004 (Daten wurden abgeschnitten) zurück.  
  
 Der Inhalt des Puffers an Sie gebundenen Daten (Wenn **SQLGetData** für eine gebundene Spalte aufgerufen wird) und den Längen-/Indikatorpuffer sind nicht definiert, wenn **SQLGetData** gibt keine SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück.  
  
 Aufeinander folgende Aufrufe von **SQLGetData** Abrufen von Daten aus der letzten Spalte angefordert werden; frühere Offsets werden ungültig. Z. B. wenn die folgende Sequenz ausgeführt wird:  
  
```cpp  
SQLGetData(icol=n), SQLGetData(icol=m), SQLGetData(icol=n)  
```  
  
 der zweite Aufruf von SQLGetData(icol=n) Ruft Daten ab, ab dem Anfang der n-Spalte. Alle Offset der Daten durch frühere Aufrufe **SQLGetData** für die Spalte nicht mehr gültig ist.  
  
## <a name="descriptors-and-sqlgetdata"></a>Deskriptoren und SQLGetData  
 **SQLGetData** interagiert nicht direkt mit jedem Descriptor-Felder.  
  
 Wenn *TargetType* ist SQL_ARD_TYPE, die Daten in das Feld "SQL_DESC_CONCISE_TYPE" die ARD wird verwendet. Wenn *TargetType* ist SQL_ARD_TYPE oder SQL_C_DEFAULT, die Daten die Genauigkeit und Dezimalstellen in der SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION, angegeben werden, und geben Sie die SQL_DESC_SCALE Felder der ARD, abhängig von den Daten im Feld SQL_DESC_CONCISE_TYPE.  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel führt eine Anwendung eine **wählen** Anweisung, um ein Resultset des Kunden-IDs, Namen und Telefonnummern, sortiert nach Name, ID und Telefonnummer. Für jede Zeile der Daten, ruft **SQLFetch** zur Positionierung des Cursors zur nächsten Zeile. Ruft **SQLGetData** zum Abrufen der abgerufenen Daten, die Puffer für die Daten und die zurückgegebene Anzahl von Bytes in den Aufruf von angegeben sind **SQLGetData**. Schließlich gibt es des jeweiligen Mitarbeiters Name, ID und Telefonnummer.  
  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Zuweisen von Speicher für eine Spalte in einem Resultset|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Massenvorgängen, die nicht auf die Position des Blocks beziehen|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen der eine einzelne Zeile von Daten oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Senden von Daten von Parametern zum Zeitpunkt der Ausführung|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset, oder aktualisieren oder Löschen von Daten im rowset|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
