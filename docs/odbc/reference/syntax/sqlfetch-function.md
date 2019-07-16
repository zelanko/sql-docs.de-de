---
title: SQLFetch-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFetch
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFetch
helpviewer_keywords:
- SQLFetch function [ODBC]
ms.assetid: 6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f9b3171d496f54942e7ac1005acea1b3566ff76
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003069"
---
# <a name="sqlfetch-function"></a>SQLFetch-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLFetch** des nächsten Rowsets von Daten aus dem Resultset abruft, und gibt Daten für alle gebundenen Spalten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFetch(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFetch** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf [SQLGetDiagRec-Funktion](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) mit eine *HandleType*von SQL_HANDLE_STMT auf, und ein *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLFetch** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben. Bei einem für eine einzelne Spalte Fehler, [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) kann aufgerufen werden, wobei eine *DiagIdentifier* von SQL_DIAG_COLUMN_NUMBER, um die Spalte zu bestimmen, der Fehler aufgetreten ist, und  **SQLGetDiagField** kann aufgerufen werden, wobei eine *DiagIdentifier* von SQL_DIAG_ROW_NUMBER Bestimmen der Zeile, die diese Spalte enthält.  
  
 Für alle diese SQLSTATEs, der SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück (mit Ausnahme der 01xxx SQLSTATEs) zurückgeben kann, wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn bei ein oder mehrere, aber nicht alle Zeilen eines mehrzeiligen-Vorgangs ein Fehler auftritt, und SQL_ERROR zurückgegeben wird, wenn es sich bei Auftreten eines Fehlers auf einem einzeiliges-Vorgang.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für eine Spalte zurückgegeben, führte das Abschneiden von nicht leeren Zeichen oder binäre Daten ungleich NULL. Falls es sich um einen Zeichenfolgenwert handelt, war es, rechts abgeschnitten.|  
|01S01|Fehler in Zeile|Fehler beim Abrufen von ein oder mehrere Zeilen.<br /><br /> (Wenn diese SQLSTATE zurückgegeben, wenn eine ODBC 3. *.x* Anwendung arbeitet mit einer ODBC 2. *.x* -Treiber verwenden, kann es ignoriert werden.)|  
|01S07|Teilbereiche wurden abgeschnitten|Die für eine Spalte zurückgegebenen Daten wurden abgeschnitten. Für numerische Datentypen wurde die Nachkommastellen der Zahl abgeschnitten. Für die Zeit, Zeitstempel und Interval-Datentypen, die eine Komponente enthalten, wurden der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|Der Datenwert einer Spalte im Resultset konnte nicht konvertiert werden, um den angegebenen Datentyp *TargetType* in **SQLBindCol**.<br /><br /> Spalte 0 wurde mit dem Datentyp SQL_C_BOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde.<br /><br /> Spalte 0 wurde mit dem Datentyp SQL_C_VARBOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut nicht auf SQL_UB_VARIABLE festgelegt wurde.|  
|07009|Ungültiger Deskriptorindex|Der Treiber wurde von einer ODBC 2. *.x* Treiber, der nicht unterstützt. **SQLExtendedFetch**, und eine Spaltennummer in der Bindung für eine Spalte angegeben wurde, 0.<br /><br /> Spalte 0 gebunden wurde, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF festgelegt wurde.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|22001|Zeichenfolgendaten, rechts abgeschnitten|Lesezeichen zurückgegeben, die für eine Spalte variabler Länge wurden abgeschnitten.|  
|22002|Anzeigevariable erforderlich, aber nicht angegeben|NULL-Daten wurde abgerufen in einer Spalte, deren *StrLen_or_IndPtr* festlegen, indem **SQLBindCol** (oder festlegen, indem SQL_DESC_INDICATOR_PTR **SQLSetDescField** oder  **SQLSetDescRec**) wurde ein null-Zeiger.|  
|22003|Numerischer Wert außerhalb des gültigen Bereichs|Zurückgeben von dem numerischen Wert als numerische Werte oder die Zeichenfolge für eine oder mehrere gebundene Spalten würde den gesamten (im Gegensatz zu Bruch) Teil der Zahl abgeschnitten wird verursacht.<br /><br /> Weitere Informationen finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in Anhang D: Datentypen.|  
|22007|Ungültiges Datetime-format|Im Resultset eine Spalte mit dem Zeichen um ein Datum, Uhrzeit oder Zeitstempel C-Struktur gebunden wurde, und ein Wert in der Spalte wurde, bzw. ein ungültiges Datum, Uhrzeit oder Zeitstempel.|  
|22012|Division durch 0 (null)|Ein Wert aus einem arithmetischen Ausdruck wurde von 0 (null) zurückgegeben Division geführt hat.|  
|22015|Überlauf bei Intervallfeld|Intervalltyp C aus einer genauen numerischen oder Intervall SQL-Typ zuweisen, verursacht einen Verlust signifikanter Ziffern im Feld führende.<br /><br /> Beim Abrufen von Daten in ein C-Intervalltyp, gab es keine Darstellung des Werts von der SQL-Typ in den Intervalltyp C.|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|Im Resultset eine Spalte mit dem Zeichen wurde auf einen Zeichenpuffer C gebunden, und die Spalte enthalten, ein Zeichen, die für die gab es keine Entsprechung in den Zeichensatz des Puffers.<br /><br /> Der C-Typ war eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp. der SQL-Typ der Spalte konnte einen Zeichendatentyp; und kein Wert in der Spalte wurde ein gültiger Literal des gebundenen Typen aus C#.|  
|24000|Ungültiger Cursorstatus|Die *StatementHandle* in einem ausgeführten Zustand wurde jedoch kein Resultset zugeordnet wurde die *StatementHandle*.|  
|40001|Serialisierungsfehler|Die Transaktion, in der der Abruf ausgeführt wurde, wurde beendet, um Deadlocks zu verhindern.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die **SQLFetch** Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Die **SQLFetch** Funktion wurde erneut aufgerufen, auf die *StatementHandle*.<br /><br /> Or **SQLFetch** Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*  von einem anderen Thread in einer multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLFetch** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) der angegebenen *StatementHandle* war nicht in einem ausgeführten Zustand befindet. Die Funktion wurde aufgerufen, ohne den ersten Aufruf **SQLExecDirect**, **SQLExecute** oder einer Katalogfunktion.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) **SQLFetch** wurde aufgerufen, die *StatementHandle* nach **SQLExtendedFetch** aufgerufen wurde und bevor **SQLFreeStmt** mit den SQL_ Option "Schließen" wurde aufgerufen.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|Das SQL_ATTR_USE_BOOKMARK-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und Spalte 0 in einen Puffer, dessen Länge nicht gleich die maximale Länge für das Lesezeichen für dieses Resultset war, gebunden wurde. (Diese Länge finden Sie im Feld SQL_DESC_OCTET_LENGTH IRD und erhalten Sie durch Aufrufen von **SQLDescribeCol**, **SQLColAttribute**, oder **SQLGetDescField**.)|  
|HY107|Zeilenwert außerhalb des gültigen Bereichs|Mit dem SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung angegebene Wert war SQL_CURSOR_KEYSET_DRIVEN, jedoch mit dem Attribut der SQL_ATTR_KEYSET_SIZE-Anweisung angegebene Wert größer als 0 und kleiner als der Wert, der mit der SQL_ATTR_ROW_ARRAY_ angegeben SIZE-Anweisungsattribut.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Treiber oder die Datenquelle unterstützt nicht die Konvertierung angegeben wird, durch die Kombination der *TargetType* in **SQLBindCol** und dem SQL-Datentyp der entsprechenden Spalte.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Abfragetimeout abgelaufen, bevor Sie die Datenquelle, die das angeforderte Resultset zurückgegeben. Der Timeoutzeitraum wird durch, SQLSetStmtAttr SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLFetch** des nächsten Rowsets im Ergebnis zurückgegeben. Es kann nur verwendet werden, während ein Resultset vorhanden ist aufgerufen werden:, also nach einem Aufruf, der ein Resultset erstellt und vor dem Cursor Failover, das Resultset geschlossen ist. Wenn alle Spalten gebunden sind, werden die Daten in diesen Spalten zurückgegeben. Wenn die Anwendung einen Zeiger auf ein zeilenstatusarray oder einen Puffer, in dem Zurückgeben der Anzahl der Zeilen abgerufen, angegeben hat **SQLFetch** gibt auch diese Informationen zurück. Aufrufe von **SQLFetch** können kombiniert werden, mit Aufrufen von **SQLFetchScroll** kann nicht mit Aufrufen von kombiniert werden, aber **SQLExtendedFetch**. Weitere Informationen finden Sie unter [Abrufen einer Zeile mit Daten](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 Wenn eine ODBC 3. *.x* Anwendung funktioniert mit einer ODBC 2. *.x* -Treiber verwenden, die der Treiber-Manager zugeordnet **SQLFetch** Aufrufe von **SQLExtendedFetch** für ein ODBC 2. *.x* Treiber, unterstützt **SQLExtendedFetch**. Wenn die ODBC 2. *.x* Treiber unterstützt keine **SQLExtendedFetch**, ordnet der Treiber-Manager **SQLFetch** Aufrufe von **SQLFetch** in die ODBC 2. *.x* Treiber, der nur eine einzelne Zeile abrufen kann.  
  
 Weitere Informationen finden Sie unter [Blockcursor, scrollbare Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
  
## <a name="positioning-the-cursor"></a>Positionieren des Cursors  
 Wenn das Resultset erstellt wird, wird der Cursor vor dem Start des Resultsets positioniert. **SQLFetch** wird die nächste Rowset abgerufen. Dies entspricht dem Aufruf **SQLFetchScroll** mit *FetchOrientation* SQL_FETCH_NEXT festgelegt. Weitere Informationen zu Cursorn finden Sie unter [Cursor](../../../odbc/reference/develop-app/cursors.md) und [Blockcursor](../../../odbc/reference/develop-app/block-cursors.md).  
  
 Die Anweisung SQL_ATTR_ROW_ARRAY_SIZE-Attribut gibt die Anzahl der Zeilen im Rowset an. Wenn das Rowset abgerufen wird, von **SQLFetch** überschneidet sich mit dem Ende des Resultsets, **SQLFetch** gibt eine partielle Rowset zurück. D. h. wenn S + R – 1 ist größer als L, wobei S der Startzeile des Rowsets wird abgerufen, R ist die Größe des Rowsets ist und L ist die letzte im Resultset, klicken Sie dann nur die ersten L - Zeile sind S + 1 Zeilen des Rowsets gültig. Die verbleibenden Zeilen sind leer und haben den Status der SQL_ROW_NOROW.  
  
 Nach dem **SQLFetch** zurückgegeben wird, die aktuelle Zeile ist die erste Zeile des Rowsets.  
  
 Die in der folgenden Tabelle aufgeführten Regeln beschreiben cursorpositionierung nach einem Aufruf von **SQLFetch**, die in der zweiten Tabelle in diesem Abschnitt aufgeführten Bedingungen abhängig.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|Vor dem start|1|  
|*CurrRowsetStart* \< =  *LastResultRow - RowsetSize*[1]|*CurrRowsetStart* + *RowsetSize*[2]|  
|*CurrRowsetStart* > *LastResultRow - RowsetSize*[1]|Nach Ende|  
|Nach Ende|Nach Ende|  
  
 [1] ist zwischen Abrufvorgängen die Rowsetgröße geändert wird, dies die Größe des Rowsets, die mit der vorhergehenden Abrufvorgang verwendet wurde.  
  
 [2] if zwischen Abrufvorgängen die Rowsetgröße geändert wird, ist dies die Größe des Rowsets, die mit der neuen Abrufoperation verwendet wurde.  
  
|Notation|Bedeutung|  
|--------------|-------------|  
|Vor dem start|Der Blockcursor wird vor dem Start des Resultsets positioniert. Vor dem Start des Resultsets, ist die erste Zeile des neuen Rowsets **SQLFetch** SQL_NO_DATA zurückgibt.|  
|Nach Ende|Der Blockcursor wird hinter das Ende des Resultsets festgelegt. Nach dem Ende des Resultsets, ist die erste Zeile des neuen Rowsets **SQLFetch** SQL_NO_DATA zurückgibt.|  
|*CurrRowsetStart*|Die Anzahl der ersten Zeile im aktuellen Rowset.|  
|*LastResultRow*|Die Anzahl der letzten Zeile im Resultset.|  
|*RowsetSize*|Die Größe des Rowsets.|  
  
 Nehmen wir beispielsweise an ein Resultset enthält 100 Zeilen und die Größe des Rowsets ist 5. Die folgende Tabelle zeigt die zurückgegebene Rowset und Rückgabe-Code **SQLFetch** für verschiedene ab Positionen.  
  
|Aktuelle rowset|Rückgabecode|Neue rowset|Anzahl der abgerufenen Zeilen|  
|--------------------|-----------------|----------------|------------------------|  
|Vor dem start|SQL_SUCCESS|1 bis 5|5|  
|1 bis 5|SQL_SUCCESS|6 bis 10|5|  
|52 bis 56|SQL_SUCCESS|57 um 61|5|  
|91 bis 95|SQL_SUCCESS|96 bis 100|5|  
|93 bis 97|SQL_SUCCESS|98 bis 100. Zeilen 4 und 5 die zeilenstatusarray werden SQL_ROW_NOROW festgelegt.|3|  
|96 bis 100|SQL_NO_DATA|Keine|0|  
|99 bis 100|SQL_NO_DATA|Keine|0|  
|Nach Ende|SQL_NO_DATA|Keine|0|  
  
## <a name="returning-data-in-bound-columns"></a>Zurückgeben von Daten in gebundenen Spalten  
 Als **SQLFetch** gibt jede Zeile, die Daten für jede gebundene Spalte im Puffer für diese Spalte gebunden wird. Wenn keine Spalten gebunden sind, **SQLFetch** keine Daten zurückgibt, jedoch Vorwärtsbewegen des Blockcursors. Die Daten können dennoch abgerufen werden, mithilfe von **SQLGetData**. Wenn der Cursor befindet sich eine Falls Cursor (d. h. SQL_ATTR_ROW_ARRAY_SIZE ist größer als 1), **SQLGetData** kann nur aufgerufen, wenn SQL_GD_BLOCK, wenn zurückgegeben wird **SQLGetInfo** aufgerufen wird und ein  *Informationsart* von SQL_GETDATA_EXTENSIONS. (Weitere Informationen finden Sie unter [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).)  
  
 Für jede gebundene Spalte in einer Zeile **SQLFetch** bewirkt Folgendes:  
  
1.  Die Längen-/Indikatorpuffers auf SQL_NULL_DATA festgelegt, und der nächsten Spalte fortgesetzt wird, wenn die Daten NULL sind. Wenn die Daten NULL ist, und es keine Längen-/Indikatorpuffer gebunden wurde, **SQLFetch** gibt SQLSTATE 22002 (Indikatorvariable erforderlich, aber nicht angegeben) für die Zeile zurück und geht zur nächsten Zeile. Informationen dazu, wie Sie die Adresse der Längen-/Indikatorpuffer zu bestimmen, finden Sie unter "Pufferadressen" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
     Wenn die Daten für die Spalte nicht NULL ist, **SQLFetch** fährt Sie fort mit Schritt 2 fort.  
  
2.  Wenn das SQL_ATTR_MAX_LENGTH-Anweisungsattribut auf einen Wert ungleich NULL festgelegt ist, und die Spalte, Zeichen- oder Binärdaten darstellen enthält, werden die Daten auf SQL_ATTR_MAX_LENGTH Byte abgeschnitten.  
  
    > [!NOTE]  
    >  Das Anweisungsattribut SQL_ATTR_MAX_LENGTH soll den Netzwerkverkehr zu reduzieren. Es ist in der Regel von der Datenquelle implementiert, die die Daten abgeschnitten werden, bevor sie über das Netzwerk zurückgegeben wird. Treibern und Datenquellen sind nicht erforderlich, um es zu unterstützen. Aus diesem Grund, um sicherzustellen, dass Daten, um eine bestimmte Größe abgeschnitten werden, eine Anwendung sollte ein Puffer dieser Größe und geben Sie die Größe in der *CbValueMax* -Argument in **SQLBindCol**.  
  
3.  Konvertiert die Daten in den vom angegebenen Typ *TargetType* in **SQLBindCol**.  
  
4.  Wenn die Daten in ein variabler Länge, Datentyp, z. B. oder binärzeichenfolgenkonstante konvertiert wurde **SQLFetch** überprüft, ob die Länge der Daten die Länge des Datenpuffers überschreitet. Die Länge der Zeichendaten enthalten sind (einschließlich der Null-Terminierungszeichen) überschreitet die Länge des Datenpuffers **SQLFetch** schneidet die Daten der Länge des Datenpuffers weniger die Länge eines Zeichens Null-Terminierung vorliegt. Es terminiert Null-klicken Sie dann die Daten. Die Länge des binären Daten überschreitet die Länge des Datenpuffers **SQLFetch** auf die Länge des Datenpuffers schneidet. Die Länge des Datenpuffers wird angegeben, mit *Pufferlänge* in **SQLBindCol**.  
  
     **SQLFetch** nie abgeschnitten. Daten, der in-Daten fester Länge Typen konvertiert; es wird immer davon ausgegangen, dass die Länge des Datenpuffers die Größe des Datentyps.  
  
5.  Legt die Daten konvertiert (und möglicherweise abgeschnitten) im Datenpuffer. Informationen zum Ermitteln der Adresse des Datenpuffers, finden Sie unter "Pufferadressen" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
6.  Legt die Länge der Daten in den Längen-/Indikatorpuffer an. Wenn der Indikatorzeiger und den datenlängenzeigern auf den gleichen Puffer festgelegt wurden (wie ein Aufruf von **SQLBindCol** ist), die Länge ist in den Puffer für gültige Daten geschrieben und SQL_NULL_DATA ist in den Puffer für NULL-Daten geschrieben. Wenn keine Längen-/Indikatorpuffer gebunden wurde, **SQLFetch** gibt nicht die Länge zurück.  
  
    -   Für Zeichen- oder Binärdaten darstellen ist dies die Länge der Daten nach der Konvertierung und vor der Kürzung aufgrund der Datenpuffer zu klein ist. Wenn der Treiber die Länge der Daten nach der Konvertierung nicht ermitteln kann als manchmal bei long-Daten der Fall ist, wird die Länge auf SQL_NO_TOTAL. Wenn Daten aufgrund der SQL_ATTR_MAX_LENGTH-Anweisungsattribut abgeschnitten wurde, wird der Wert dieses Attributs im den Längen-/Indikatorpuffer anstelle der tatsächlichen Länge gespeichert. Dies ist dieses Attribut ist darauf ausgelegt, Daten auf dem Server vor der Konvertierung abgeschnitten, damit der Treiber hat keine Möglichkeit herauszufinden, welche die tatsächliche Länge ist.  
  
    -   Für alle anderen Datentypen ist dies die Länge der Daten, nach der Konvertierung; Das heißt, ist es die Größe des Typs, der die Daten konvertiert wurden.  
  
     Informationen dazu, wie Sie die Adresse der Längen-/Indikatorpuffer zu bestimmen, finden Sie unter "Pufferadressen" in [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
7.  Wenn die Daten, während der Konvertierung ohne einen Verlust signifikanter Ziffern abgeschnitten werden (z. B. die reelle Zahl-1,234 auf die ganze Zahl 1, bei der Konvertierung abgeschnitten ist), **SQLFetch** SQLSTATE 01 s 07 zurückgibt (Teilbereiche wurden abgeschnitten) und SQL_ SUCCESS_WITH_INFO. Wenn die Daten abgeschnitten werden, da die Länge des Datenpuffers zu klein ist (z. B. die Zeichenfolge "Abcdef" in einem 4-Byte-Puffer eingefügt wird), **SQLFetch** SQLSTATE 01004 (Daten wurden abgeschnitten) und SQL_SUCCESS_WITH_INFO zurückgegeben. Wenn Daten, da das SQL_ATTR_MAX_LENGTH-Anweisungsattribut abgeschnitten werden **SQLFetch** gibt SQL_SUCCESS zurück, und keinen SQLSTATE 01 s 07 zurückgibt (Teilbereiche wurden abgeschnitten) oder SQLSTATE 01004 (Daten wurden abgeschnitten). Wenn Daten abgeschnitten werden, während der Konvertierung mit einem Verlust der signifikanten Ziffern (z. B., wenn ein SQL_INTEGER-Wert, der größer als 100.000 in einer SQL_C_TINYINT konvertiert wurden), **SQLFetch** gibt SQLSTATE 22003 (numerischer Wert außerhalb des gültigen Bereichs) und SQL_ERROR (wenn die Rowsetgröße 1 ist) oder SQL_SUCCESS_WITH_INFO zurück (wenn die Rowsetgröße größer als 1 ist).  
  
 Den Inhalt der gebundenen Datenpuffer und Längen-/Indikatorpuffers sind nicht definiert, wenn **SQLFetch** oder **SQLFetchScroll** gibt keine SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück.  
  
## <a name="row-status-array"></a>Zeilenstatusarray  
 Die zeilenstatusarray wird verwendet, um den Status der einzelnen Zeilen im Rowset zurückgegeben. Die Adresse dieses Array wird mit der SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut angegeben. Das Array wird von der Anwendung zugeordnet und muss so viele Elemente, die von dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut-Anweisung angegeben werden. Die Werte werden festgelegt, indem **SQLFetch**, **SQLFetchScroll**, und **SQLBulkOperations** oder **SQLSetPos** (außer wenn sie aufgerufen wurden nach dem von der Cursor positioniert ist **SQLExtendedFetch**). Wenn der Wert des Attributs Anweisung SQL_ATTR_ROW_STATUS_PTR ein null-Zeiger ist, geben diese Funktionen nicht den Zeilenstatus zurück.  
  
 Der Inhalt des Array den Zeilenpuffer-Status sind nicht definiert, wenn **SQLFetch** oder **SQLFetchScroll** gibt keine SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück.  
  
 Die folgenden Werte werden in der zeilenstatusarray zurückgegeben.  
  
|Array-Statuswert Zeile|Beschreibung|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|Die Zeile wurde erfolgreich abgerufen und wurde nicht geändert, seit sie zuletzt in diesem Resultset abgerufen wurde.|  
|SQL_ROW_SUCCESS_WITH_INFO|Die Zeile wurde erfolgreich abgerufen und wurde nicht geändert, seit sie zuletzt in diesem Resultset abgerufen wurde. Allerdings wurde eine Warnung zur Zeile zurückgegeben.|  
|SQL_ROW_ERROR|Fehler beim Abrufen der Zeile.|  
|SQL_ROW_UPDATED [1], [2] und [3]|Die Zeile wurde erfolgreich abgerufen, und es hat sich seit dem letzten aus dieses Resultset Abruf geändert. Wenn die Zeile erneut aus der dieses Resultset abgerufen oder, indem aktualisiert wird **SQLSetPos**, der Status wird geändert, um den neuen Status der Zeile.|  
|SQL_ROW_DELETED[3]|Die Zeile wurde seit dem letzten aus dieses Resultset Abruf gelöscht.|  
|SQL_ROW_ADDED[4]|Die Zeile eingefügt wurde, indem **SQLBulkOperations**. Wenn die Zeile erneut aus der dieses Resultset abgerufen oder, indem aktualisiert wird **SQLSetPos**, dessen Status ist SQL_ROW_SUCCESS.|  
|SQL_ROW_NOROW|Das Rowset überlappende das Ende des Resultsets und keine Zeile zurückgegeben wurde, dass, die für dieses Element von der zeilenstatusarray entsprach.|  
  
 [1] für Keyset, gemischten und dynamische Cursor, wenn ein Schlüssel-Wert aktualisiert wird, gilt die Zeile der Daten gelöscht wurden und eine neue Zeile hinzugefügt.  
  
 [2] einige Treiber können nicht feststellen, Updates für Daten und aus diesem Grund können dieser Wert zurückgeben. Um zu bestimmen, ob ein Treiber, Updates von Zeilen erneut abgerufen erkennen kann, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_ROW_UPDATES.  
  
 [3] **SQLFetch** können diesen Wert zurückgeben, nur wenn sie mit ist-Aufrufe **SQLFetchScroll**. Grund hierfür ist, **SQLFetch** weiterleiten über das Resultset verschoben werden und wenn er exklusiv verwendet wird, nicht erneut Zeilen abzurufen. Da keine Zeilen erneut abgerufen werden, **SQLFetch** erkennt keine Änderungen, die zuvor abgerufenen Zeilen vorgenommen wurden. Aber wenn **SQLFetchScroll** platziert den Cursor, bevor alle zuvor Zeilen abgerufen und **SQLFetch** dient zum Abrufen von Zeilen, **SQLFetch** kann erkennen alle Änderungen an die Zeilen.  
  
 [4] zurückgegeben nur durch SQLBulkOperations. Nicht von festgelegt **SQLFetch** oder **SQLFetchScroll**.  
  
### <a name="rows-fetched-buffer"></a>Die Zeilen abgerufen, Puffer  
 Puffer abgerufenen Zeilen wird verwendet, um die Anzahl der Zeilen, die auch diese Zeilen, die für die keine Daten zurückgegeben wurden, da ein Fehler aufgetreten, während sie abgerufen werden, wurden abgerufen, zurückzugeben. Das heißt, ist es die Anzahl der Zeilen, die für die der Wert in der zeilenstatusarray SQL_ROW_NOROW nicht ist. Die Adresse dieses Puffers wird mit der Anweisung SQL_ATTR_ROWS_FETCHED_PTR-Attribut angegeben. Der Puffer wird von der Anwendung zugewiesen. Es wird festgelegt, indem **SQLFetch** und **SQLFetchScroll**. Wenn der Wert des Attributs SQL_ATTR_ROWS_FETCHED_PTR-Anweisung ein null-Zeiger ist, geben diese Funktionen nicht die Anzahl der abgerufenen Zeilen zurück. Um die Anzahl der aktuellen Zeile im Resultset zu ermitteln, kann eine Anwendung aufrufen **SQLGetStmtAttr** mit dem SQL_ATTR_ROW_NUMBER-Attribut.  
  
 Der Inhalt des Puffers abgerufenen Zeilen sind nicht definiert, wenn **SQLFetch** oder **SQLFetchScroll** keinen zurückgibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, außer wenn SQL_NO_DATA, in diesem Fall zurückgegeben wird die in den Puffer abgerufenen Zeilen ist auf 0 festgelegt.  
  
### <a name="error-handling"></a>Fehlerbehandlung  
 Fehler und Warnungen können auf einzelne Zeilen oder die gesamte Funktion gelten. Weitere Informationen zu DiagnoseDatensätze, finden Sie unter [Diagnose](../../../odbc/reference/develop-app/diagnostics.md) und [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
#### <a name="errors-and-warnings-on-the-entire-function"></a>Fehler und Warnungen für die gesamte Funktion  
 Wenn ein Fehler für den gesamten Funktion, z. B. SQLSTATE HYT00 gilt (Timeout ist abgelaufen) oder SQLSTATE 24000 (Ungültiger Cursorstatus), **SQLFetch** gibt SQL_ERROR zurück, und die entsprechenden SQLSTATE. Der Inhalt der Rowset-Puffer ist nicht definiert, und die Cursorposition bleibt unverändert.  
  
 Wenn eine Warnung für den gesamten Funktion gilt **SQLFetch** SQL_SUCCESS_WITH_INFO und SQLSTATE anwendbar. Die Status-Einträge für Warnungen, die für die gesamte Funktion gelten werden vor den statusdatensätzen zurückgegeben, die auf einzelne Zeilen angewendet.  
  
#### <a name="errors-and-warnings-in-individual-rows"></a>Fehler und Warnungen in einzelne Zeilen  
 Wenn ein Fehler (z. B. SQLSTATE 22012 (Division durch 0 (null))) oder eine Warnung (z. B. SQLSTATE 01004 (Daten wurden abgeschnitten.)) für eine einzelne Zeile gilt **SQLFetch**bewirkt Folgendes:  
  
-   Legt das entsprechende Element von der zeilenstatusarray, SQL_ROW_ERROR auf Fehler oder SQL_ROW_SUCCESS_WITH_INFO für Warnungen fest.  
  
-   Fügt keine oder mehrere Statusdatensätze, die SQLSTATEs für den Fehler oder Warnung enthalten.  
  
-   Legt die Zeilen- und Zahlenfelder in den statusdatensätzen fest. Wenn **SQLFetch** kann nicht bestimmt werden eine Zeile oder Spalte Zahl ist, wird diese Zahl auf SQL_ROW_NUMBER_UNKNOWN oder SQL_COLUMN_NUMBER_UNKNOWN, bzw. Wenn der Status-Datensatz nicht für eine bestimmte Spalte gilt **SQLFetch** legt die Nummer der Spalte um SQL_NO_COLUMN_NUMBER fest.  
  
 **SQLFetch** wird fortgesetzt, Abrufen von Zeilen, bis sie alle Zeilen im Rowset abgerufen hat. Es gibt SQL_SUCCESS_WITH_INFO zurück, es sei denn, ein Fehler in jeder Zeile des Rowsets (nicht einschließlich Zeilen mit dem Status SQL_ROW_NOROW), tritt ein, in diesem Fall wird SQL_ERROR zurückgegeben. Insbesondere wenn die Rowsetgröße 1 und ein Fehler auftritt, in dieser Zeile **SQLFetch** gibt SQL_ERROR zurück.  
  
 **SQLFetch** die Statusdatensätze in der Reihenfolge für die Anzahl der Zeilen zurückgegeben. Wird zurückgegeben, also alle Statusdatensätze für unbekannte Zeilen (sofern vorhanden); als Nächstes gibt alle Statusdatensätze für die erste Zeile (sofern vorhanden), und gibt dann alle Statusdatensätze für die zweite Zeile (sofern vorhanden), und So weiter zurück. Die Statusdatensätze für jede Zeile werden gemäß den normalen Regeln für die Sortierung der Statusdatensätze sortiert; Weitere Informationen finden Sie unter "Sequenz der Statusdatensätze" in [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
### <a name="descriptors-and-sqlfetch"></a>Deskriptoren und SQLFetch  
 In den folgenden Abschnitten wird beschrieben wie **SQLFetch** interagiert mit Deskriptoren.  
  
#### <a name="argument-mappings"></a>Argument-Zuordnungen  
 Der Treiber keine basierend auf den Argumenten von deskriptorfelder festlegt **SQLFetch**.  
  
#### <a name="other-descriptor-fields"></a>Andere Deskriptorfelder  
 Die folgenden deskriptorfelder werden verwendet, indem **SQLFetch**.  
  
|Deskriptorfeld|DESC.|Feld in|Durch Festlegen|  
|----------------------|-----------|--------------|-----------------|  
|SQL_DESC_ARRAY_SIZE|ARD|Header|Anweisung SQL_ATTR_ROW_ARRAY_SIZE-Attribut|  
|SQL_DESC_ARRAY_STATUS_PTR|IRD|Header|SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut|  
|SQL_DESC_BIND_OFFSET_PTR|ARD|Header|SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattribut|  
|SQL_DESC_BIND_TYPE|ARD|Header|SQL_ATTR_ROW_BIND_TYPE-Anweisungsattribut|  
|SQL_DESC_COUNT|ARD|Header|*ColumnNumber* Argument **SQLBindCol**|  
|SQL_DESC_DATA_PTR|ARD|Datensätze|*TargetValuePtr* Argument **SQLBindCol**|  
|SQL_DESC_INDICATOR_PTR|ARD|Datensätze|*StrLen_or_IndPtr* -Argument in **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH|ARD|Datensätze|*BufferLength* -Argument in **SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH_PTR|ARD|Datensätze|*StrLen_or_IndPtr* -Argument in **SQLBindCol**|  
|SQL_DESC_ROWS_PROCESSED_PTR|IRD|Header|Anweisung SQL_ATTR_ROWS_FETCHED_PTR-Attribut|  
|SQL_DESC_TYPE|ARD|Datensätze|*TargetType* -Argument in **SQLBindCol**|  
  
 Alle deskriptorfelder können auch festgelegt werden, über **SQLSetDescField**.  
  
#### <a name="separate-length-and-indicator-buffers"></a>Länge und Indikator Puffer trennen  
 Anwendungen können binden, einen einzelnen Puffer oder in zwei verschiedenen Puffern, die verwendet werden können, um Werte für Länge und den Indikator zu speichern. Wenn eine Anwendung ruft **SQLBindCol**, der Treiber setzt die SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_INDICATOR_PTR Felder der ARD in die gleiche Adresse an, der übergeben wird, in der *StrLen_or_IndPtr* Argument. Wenn eine Anwendung ruft **SQLSetDescField** oder **SQLSetDescRec**, kann diese zwei Felder an unterschiedliche Adressen festgelegt.  
  
 **SQLFetch** bestimmt, ob die Anwendung separate Länge und Indikator Puffer angegeben wurde. In diesem Fall, wenn die Daten ist nicht NULL, **SQLFetch** legt die Indikatorpuffers auf 0 fest und gibt die Länge der Puffer der Länge zurück. Wenn die Daten NULL **SQLFetch** der Indikatorpuffers auf SQL_NULL_DATA festgelegt, und ändert sich nicht auf den Puffer der Länge.  
  
### <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md), und [SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md).  
  
### <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Schließen des Cursors in der Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Abrufen von teilweise oder vollständig eine Spalte mit Daten|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Die Anzahl der Resultsets zurückgeben von Resultsetspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
