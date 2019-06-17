---
title: SQLFetchScroll-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFetchScroll
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFetchScroll
helpviewer_keywords:
- SQLFetchScroll function [ODBC]
ms.assetid: c0243667-428c-4dda-ae91-3c307616a1ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20a1580503ad141817edcf8e01772dfcc8dc39a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537358"
---
# <a name="sqlfetchscroll-function"></a>SQLFetchScroll-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLFetchScroll** angegebene Rowset von Daten aus dem Resultset abruft, und gibt Daten für alle gebundenen Spalten zurück. Rowsets können an eine absolute oder relative Position oder durch Lesezeichen angegeben werden.  
  
 Bei der Arbeit mit einem ODBC 2.x-Treiber ordnet der Treiber-Manager diese Funktion **SQLExtendedFetch**. Weitere Informationen finden Sie unter [Zuordnen von Ersatzfunktionen für Abwärtskompatibilität-Kompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
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
  
 Der Typ des abrufen:  
  
 SQL_FETCH_NEXT  
  
 SQL_FETCH_PRIOR  
  
 SQL_FETCH_FIRST  
  
 SQL_FETCH_LAST  
  
 SQL_FETCH_ABSOLUTE  
  
 SQL_FETCH_RELATIVE  
  
 SQL_FETCH_BOOKMARK  
  
 Weitere Informationen finden Sie unter "Positionierung der Cursor" im Abschnitt "Kommentare".  
  
 *FetchOffset*  
 [Eingabe]  
  
 Die Nummer der Zeile abgerufen. Die Interpretation dieses Arguments hängt des Werts des der *FetchOrientation* Argument. Weitere Informationen finden Sie unter "Positionierung der Cursor" im Abschnitt "Kommentare".  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFetchScroll** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit einem HandleType von SQL_HANDLE_STMT auf, und ein Handle StatementHandle. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLFetchScroll** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben. Wenn es sich bei Auftreten eines Fehlers in einer einzelnen Spalte **SQLGetDiagField** kann mit einem DiagIdentifier SQL_DIAG_COLUMN_NUMBER auf die Spalte zu bestimmen, der Fehler aufgetreten ist, aufgerufen werden und **SQLGetDiagField** aufgerufen werden kann mit einem DiagIdentifier SQL_DIAG_ROW_NUMBER Bestimmen der Zeile, die diese Spalte enthält.  
  
 Für alle diese SQLSTATEs, der SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück (mit Ausnahme der 01xxx SQLSTATEs) zurückgeben kann, wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn bei ein oder mehrere, aber nicht alle Zeilen eines mehrzeiligen-Vorgangs ein Fehler auftritt, und SQL_ERROR zurückgegeben wird, wenn es sich bei Auftreten eines Fehlers auf einem einzeiliges-Vorgang.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für eine Spalte zurückgegeben, führte das Abschneiden von nicht leeren Zeichen oder binäre Daten ungleich NULL. Falls es sich um einen Zeichenfolgenwert handelt, war es, rechts abgeschnitten.|  
|01S01|Fehler in Zeile|Fehler beim Abrufen von ein oder mehrere Zeilen.<br /><br /> (Wenn diese SQLSTATE zurückgegeben, wenn eine ODBC 3. *.x* Anwendung arbeitet mit einer ODBC 2. *.x* -Treiber verwenden, kann es ignoriert werden.)|  
|01S06|Versucht, Daten abzurufen, bevor das Resultset das erste Rowset zurückgegeben.|Das angeforderte Rowset überlappende Anfang des Resultsets FetchOrientation wurde SQL_FETCH_PRIOR, die aktuelle Position wurde nach der ersten Zeile und die Anzahl der aktuellen Zeile ist kleiner als oder gleich der Rowsetgröße.<br /><br /> Das angeforderte Rowset überlappende Anfang des Resultsets bei FetchOrientation SQL_FETCH_PRIOR war, die aktuelle Position hinter dem Ende des Resultsets wurde und die Rowsetgröße größer als die Größe des Resultsets.<br /><br /> Das angeforderte Rowset überlappende Anfang des Resultsets FetchOrientation wurde SQL_FETCH_RELATIVE, FetchOffset negativ war und der Absolute Wert des FetchOffset war kleiner oder gleich der Rowsetgröße.<br /><br /> Das angeforderte Rowset überlappende Anfang des Resultsets FetchOrientation wurde SQL_FETCH_ABSOLUTE, FetchOffset negativ war und der Absolute Wert des FetchOffset war größer als die Größe des Resultsets, aber kleiner oder gleich der Größe des Rowsets.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Teilbereiche wurden abgeschnitten|Die für eine Spalte zurückgegebenen Daten wurden abgeschnitten. Für numerische Datentypen wurde die Nachkommastellen der Zahl abgeschnitten. Für die Zeit, Zeitstempel und Interval-Datentypen, die eine Komponente enthält wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|Der Datenwert einer Spalte im Resultset konnte nicht konvertiert werden, um den angegebenen Datentyp *TargetType* in **SQLBindCol**.<br /><br /> Spalte 0 wurde mit dem Datentyp SQL_C_BOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde.<br /><br /> Spalte 0 wurde mit dem Datentyp SQL_C_VARBOOKMARK gebunden, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut nicht auf SQL_UB_VARIABLE festgelegt wurde.|  
|07009|Ungültiger Deskriptorindex|Der Treiber wurde von einer ODBC 2. *.x* Treiber, der nicht unterstützt. **SQLExtendedFetch**, und eine Spaltennummer in der Bindung für eine Spalte angegeben wurde, 0.<br /><br /> Spalte 0 gebunden wurde, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF festgelegt wurde.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|22001|Zeichenfolgendaten, rechts abgeschnitten|Lesezeichen zurückgegeben, die für eine Spalte variabler Länge wurden abgeschnitten.|  
|22002|Anzeigevariable erforderlich, aber nicht angegeben|NULL-Daten wurde abgerufen in einer Spalte, deren *StrLen_or_IndPtr* festlegen, indem **SQLBindCol** (oder festlegen, indem SQL_DESC_INDICATOR_PTR **SQLSetDescField** oder  **SQLSetDescRec**) wurde ein null-Zeiger.|  
|22003|Numerischer Wert außerhalb des gültigen Bereichs|Den numerischen Wert (als numerisch oder Zeichenfolge) zurückgegeben, für mindestens eine gebundene Spalten würde den gesamten (im Gegensatz zu Bruch) Teil der Zahl abgeschnitten wird verursacht.<br /><br /> Weitere Informationen finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Ungültiges Datetime-format|Im Resultset eine Spalte mit dem Zeichen um ein Datum, Uhrzeit oder Zeitstempel C-Struktur gebunden wurde, und ein Wert in der Spalte wurde, bzw. ein ungültiges Datum, Uhrzeit oder Zeitstempel.|  
|22012|Division durch 0 (null)|Ein Wert aus einem arithmetischen Ausdruck wurde von 0 (null) zurückgegeben Division geführt hat.|  
|22015|Überlauf bei Intervallfeld|Intervalltyp C aus einer genauen numerischen oder Intervall SQL-Typ zuweisen, verursacht einen Verlust signifikanter Ziffern im Feld führende.<br /><br /> Beim Abrufen von Daten in ein C-Intervalltyp, gab es keine Darstellung des Werts von der SQL-Typ in den Intervalltyp C.|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|Im Resultset eine Spalte mit dem Zeichen wurde auf einen Zeichenpuffer C gebunden, und die Spalte enthalten, ein Zeichen, die für die gab es keine Entsprechung in den Zeichensatz des Puffers.<br /><br /> Der C-Typ war eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp. der SQL-Typ der Spalte konnte einen Zeichendatentyp; und kein Wert in der Spalte wurde ein gültiger Literal des gebundenen Typen aus C#.|  
|24000|Ungültiger Cursorstatus|Die *StatementHandle* in einem ausgeführten Zustand wurde jedoch kein Resultset zugeordnet wurde die *StatementHandle*.|  
|40001|Serialisierungsfehler|Die Transaktion, in der der Abruf ausgeführt wurde, wurde beendet, um Deadlocks zu verhindern.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLFetchScroll** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) der angegebenen *StatementHandle* war nicht in einem ausgeführten Zustand befindet. Die Funktion wurde aufgerufen, ohne den ersten Aufruf **SQLExecDirect**, **SQLExecute** oder einer Katalogfunktion.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) **SQLFetch** wurde aufgerufen, die *StatementHandle* nach **SQLExtendedFetch** aufgerufen wurde und bevor **SQLFreeStmt** mit den SQL_ Option "Schließen" wurde aufgerufen.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|Das SQL_ATTR_USE_BOOKMARK-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und Spalte 0 in einen Puffer, dessen Länge nicht gleich die maximale Länge für das Lesezeichen für dieses Resultset war, gebunden wurde. (Diese Länge finden Sie im Feld SQL_DESC_OCTET_LENGTH IRD und erhalten Sie durch Aufrufen von **SQLDescribeCol**, **SQLColAttribute**, oder **SQLGetDescField**.)|  
|HY106|Fetchtyp außerhalb des gültigen Bereichs|DM) war für das Argument FetchOrientation angegebene Wert ungültig.<br /><br /> (DM) das Argument FetchOrientation war sql_fetch_bookmark auf, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF festgelegt wurde.<br /><br /> Der Wert des Attributs SQL_ATTR_CURSOR_TYPE-Anweisung war SQL_CURSOR_FORWARD_ONLY und der Wert des Arguments, dass FetchOrientation nicht SQL_FETCH_NEXT war.<br /><br /> Der Wert des Attributs SQL_ATTR_CURSOR_SCROLLABLE-Anweisung war SQL_NONSCROLLABLE und der Wert des Arguments, dass FetchOrientation nicht SQL_FETCH_NEXT war.|  
|HY107|Zeilenwert außerhalb des gültigen Bereichs|Mit dem SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung angegebene Wert war SQL_CURSOR_KEYSET_DRIVEN, jedoch mit dem Attribut der SQL_ATTR_KEYSET_SIZE-Anweisung angegebene Wert größer als 0 und kleiner als der Wert, der mit der SQL_ATTR_ROW_ARRAY_ angegeben SIZE-Anweisungsattribut.|  
|HY111|Ungültiger Wert für Lesezeichen|Das Argument FetchOrientation war sql_fetch_bookmark auf, und das Lesezeichen, um mit dem Wert in das SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungsattribut auf war ungültig oder wurde ein null-Zeiger.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Treiber oder die Datenquelle unterstützt nicht die Konvertierung angegeben wird, durch die Kombination der *TargetType* in **SQLBindCol** und dem SQL-Datentyp der entsprechenden Spalte.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Abfragetimeout abgelaufen, bevor Sie die Datenquelle, die das angeforderte Resultset zurückgegeben. Der Timeoutzeitraum wird durch, SQLSetStmtAttr SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLFetchScroll** gibt ein Rowset angegebenen aus dem Resultset zurück. Rowsets können anhand der absolute oder relative Position oder durch Lesezeichen angegeben werden. **SQLFetchScroll** aufgerufen werden kann, nur während ein Resultset vorhanden ist – d. h. nach einem Aufruf, der ein Resultset erstellt und vor dem Cursor Failover, das Resultset geschlossen wird. Wenn alle Spalten gebunden sind, werden die Daten in diesen Spalten zurückgegeben. Wenn die Anwendung einen Zeiger auf ein zeilenstatusarray oder einen Puffer, in dem Zurückgeben der Anzahl der Zeilen abgerufen, angegeben hat **SQLFetchScroll** gibt diese Informationen auch zurück. Aufrufe von **SQLFetchScroll** können kombiniert werden, mit Aufrufen von **SQLFetch** kann nicht mit Aufrufen von kombiniert werden, aber **SQLExtendedFetch**.  
  
 Weitere Informationen finden Sie unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md) und [bildlauffähigen Cursor verwenden](../../../odbc/reference/develop-app/using-scrollable-cursors.md).  
  
## <a name="positioning-the-cursor"></a>Positionieren des Cursors  
 Wenn das Resultset erstellt wird, wird der Cursor vor dem Start des Resultsets positioniert. **SQLFetchScroll** positioniert die Blockcursor anhand der Werte von der *FetchOrientation* und *FetchOffset* Argumente wie in der folgenden Tabelle gezeigt. Die genauen Regeln zur Bestimmung der Start des neuen Rowsets werden im nächsten Abschnitt angezeigt.  
  
|FetchOrientation|Bedeutung|  
|----------------------|-------------|  
|SQL_FETCH_NEXT|Zurückgeben des nächsten Rowsets. Dies entspricht dem Aufruf **SQLFetch**.<br /><br /> **SQLFetchScroll** ignoriert den Wert der *FetchOffset*.|  
|SQL_FETCH_PRIOR|Geben Sie das vorherige Rowset zurück.<br /><br /> **SQLFetchScroll** ignoriert den Wert der *FetchOffset*.|  
|SQL_FETCH_RELATIVE|Zurückgeben des Rowsets *FetchOffset* vom Beginn des aktuellen Rowsets.|  
|SQL_FETCH_ABSOLUTE|Zurückgeben des Rowsets ab Zeile *FetchOffset*.|  
|SQL_FETCH_FIRST|Geben Sie im Resultset das erste Rowset zurück.<br /><br /> **SQLFetchScroll** ignoriert den Wert der *FetchOffset*.|  
|SQL_FETCH_LAST|Geben Sie in das Resultset auf die letzte vollständige Rowset zurück.<br /><br /> **SQLFetchScroll** ignoriert den Wert der *FetchOffset*.|  
|SQL_FETCH_BOOKMARK|Zurückgegeben Sie das Rowset FetchOffset Zeilen aus das Lesezeichen, das das SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungsattribut gemäß.|  
  
 Treiber sind nicht erforderlich, um alle Fetch-Ausrichtungen unterstützen. Ruft die Anwendung **SQLGetInfo** mit dem Datentyp Informationen SQL_DYNAMIC_CURSOR_ATTRIBUTES1 SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 (je nach Art des Cursors) um zu bestimmen, welche abrufen Ausrichtungen werden vom Treiber unterstützt. Die Anwendung sollte den SQL_CA1_NEXT, SQL_CA1_RELATIVE, SQL_CA1_ABSOLUTE und WQL_CA1_BOOKMARK Bitmasken solche Informationen betrachten. Darüber hinaus, wenn der Cursor, vorwärts gerichtete befindet und FetchOrientation nicht SQL_FETCH_NEXT, **SQLFetchScroll** SQLSTATE HY106 zurückgibt (Fetchtyp außerhalb des gültigen Bereichs).  
  
 Die Anweisung SQL_ATTR_ROW_ARRAY_SIZE-Attribut gibt die Anzahl der Zeilen im Rowset an. Wenn das Rowset abgerufen wird, von **SQLFetchScroll** überschneidet sich mit dem Ende des Resultsets, **SQLFetchScroll** gibt eine partielle Rowset zurück. D. h. wenn S + R – 1 ist größer als L, wobei S der Startzeile des Rowsets wird abgerufen, R ist die Größe des Rowsets ist und L ist die letzte im Resultset, klicken Sie dann nur die ersten L - Zeile sind S + 1 Zeilen des Rowsets gültig. Die verbleibenden Zeilen sind leer und haben den Status der SQL_ROW_NOROW.  
  
 Nach dem **SQLFetchScroll** zurückgegeben wird, die aktuelle Zeile ist die erste Zeile des Rowsets.  
  
## <a name="cursor-positioning-rules"></a>Cursorpositionierungsaufruf Regeln  
 Den folgenden Abschnitten werden die genauen Regeln für jeden Wert von FetchOrientation. Diese Regeln verwenden, die folgende Notation wird.  
  
|Notation|Bedeutung|  
|--------------|-------------|  
|*Vor dem start*|Der Blockcursor wird vor dem Start des Resultsets positioniert. Vor dem Start des Resultsets, ist die erste Zeile des neuen Rowsets **SQLFetchScroll** SQL_NO_DATA zurückgibt.|  
|*Nach Ende*|Der Blockcursor wird hinter das Ende des Resultsets festgelegt. Nach dem Ende des Resultsets, ist die erste Zeile des neuen Rowsets **SQLFetchScroll** SQL_NO_DATA zurückgibt.|  
|*CurrRowsetStart*|Die Anzahl der ersten Zeile im aktuellen Rowset.|  
|*LastResultRow*|Die Anzahl der letzten Zeile im Resultset.|  
|*RowsetSize*|Die Größe des Rowsets.|  
|*FetchOffset*|Der Wert des der *FetchOffset* Argument.|  
|*BookmarkRow*|Die Zeile, die für das Lesezeichen, das durch das SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungsattribut angegeben wird.|  
  
## <a name="sqlfetchnext"></a>SQL_FETCH_NEXT  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Vor dem start*|1|  
|*CurrRowsetStart + RowsetSize*[1]  *\<LastResultRow =*|*CurrRowsetStart + RowsetSize*[1]|  
|*CurrRowsetStart + RowsetSize*[1] *> LastResultRow*|*Nach Ende*|  
|*Nach Ende*|*Nach Ende*|  
  
 [1] Wenn seit dem vorherigen Aufruf von Zeilen abzurufen, die Rowsetgröße geändert wurde, ist dies die Größe des Rowsets, die mit dem vorherigen Aufruf verwendet wurde.  
  
## <a name="sqlfetchprior"></a>SQL_FETCH_PRIOR  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Vor dem start*|*Vor dem start*|  
|*CurrRowsetStart = 1*|*Vor dem start*|  
|*1 < CurrRowsetStart < = RowsetSize* <sup>[2].</sup>|*1* <sup>[1]</sup>|  
|*CurrRowsetStart > RowsetSize* <sup>[2]</sup>|*CurrRowsetStart - RowsetSize* <sup>[2]</sup>|  
|*Nach dem Ende und LastResultRow < RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*Nach dem Ende und LastResultRow > = RowsetSize* <sup>[2]</sup>|*LastResultRow - RowsetSize + 1* <sup>[2].</sup>|  
  
 [1] **SQLFetchScroll** SQLSTATE 01S06 zurückgibt (versucht abzurufen, bevor das Resultset das erste Rowset zurückgegeben) und SQL_SUCCESS_WITH_INFO.  
  
 [2] if seit dem vorherigen Aufruf von Zeilen abzurufen, die Rowsetgröße geändert wurde, ist dies die neue Rowsetgröße.  
  
## <a name="sqlfetchrelative"></a>SQL_FETCH_RELATIVE  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*(Vor dem start und FetchOffset > 0) ODER (nach dem Ende und FetchOffset < 0)*|*--* <sup>[1]</sup>|  
|*BeforeStart und FetchOffset < = 0*|*Vor dem start*|  
|*CurrRowsetStart = 1 AND FetchOffset < 0*|*Vor dem start*|  
|*CurrRowsetStart > 1 AND CurrRowsetStart + FetchOffset < 1 AND &#124; FetchOffset &#124; > RowsetSize* <sup>[3]</sup>|*Vor dem start*|  
|*CurrRowsetStart > 1 AND CurrRowsetStart + FetchOffset < 1 AND &#124; FetchOffset &#124; <= RowsetSize* <sup>[3]</sup>|*1* <sup>[2]</sup>|  
|*1 < = CurrRowsetStart + FetchOffset \<LastResultRow =*|*CurrRowsetStart + FetchOffset*|  
|*CurrRowsetStart + FetchOffset > LastResultRow*|*Nach Ende*|  
|*Nach dem Ende und FetchOffset > = 0*|*Nach Ende*|  
  
 [1] ***SQLFetchScroll*** dasselbe Rowset zurückgibt, als ob aufgerufen und FetchOrientation SQL_FETCH_ABSOLUTE festgelegt wurde. Weitere Informationen finden Sie im Abschnitt "SQL_FETCH_ABSOLUTE".  
  
 [2] **SQLFetchScroll** SQLSTATE 01S06 zurückgibt (versucht abzurufen, bevor das Resultset das erste Rowset zurückgegeben) und SQL_SUCCESS_WITH_INFO.  
  
 [3] Wenn seit dem vorherigen Aufruf von Zeilen abzurufen, die Rowsetgröße geändert wurde, ist dies die neue Rowsetgröße.  
  
## <a name="sqlfetchabsolute"></a>SQL_FETCH_ABSOLUTE  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*FetchOffset < 0 AND &#124; FetchOffset &#124; <= LastResultRow*|*LastResultRow + FetchOffset + 1*|  
|*FetchOffset < 0 AND &#124; FetchOffset &#124; > LastResultRow und &#124; FetchOffset &#124; > RowsetSize* <sup>[2]</sup>|*Vor dem start*|  
|*FetchOffset < 0 AND &#124; FetchOffset &#124; > LastResultRow und &#124; FetchOffset &#124; < = RowsetSize* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*FetchOffset = 0*|*Vor dem start*|  
|*1 < = FetchOffset \<LastResultRow =*|*FetchOffset*|  
|*FetchOffset > LastResultRow*|*Nach Ende*|  
  
 [1] **SQLFetchScroll** SQLSTATE 01S06 zurückgibt (versucht abzurufen, bevor das Resultset das erste Rowset zurückgegeben) und SQL_SUCCESS_WITH_INFO.  
  
 [2] if seit dem vorherigen Aufruf von Zeilen abzurufen, die Rowsetgröße geändert wurde, ist dies die neue Rowsetgröße.  
  
 Ein absoluter Abruf für einen dynamischen Cursor ausgeführt kann nicht das erforderliche Ergebnis bereitstellen, da Zeilenpositionen in einem dynamischen Cursor nicht festgelegt werden. Solcher Vorgang entspricht der auf einen Abruf, zuerst eine fetchrelative gefolgt. Es ist nicht atomischer Vorgang, da ein absoluter Abruf in einem statischen Cursor ist.  
  
## <a name="sqlfetchfirst"></a>SQL_FETCH_FIRST  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*Any*|*1*|  
  
## <a name="sqlfetchlast"></a>SQL_FETCH_LAST  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*RowsetSize* <sup>[1]</sup> < = LastResultRow|*LastResultRow - RowsetSize + 1* <sup>[1]</sup>|  
|*RowsetSize* <sup>[1]</sup> > LastResultRow|*1*|  
  
 [1] Wenn seit dem vorherigen Aufruf von Zeilen abzurufen, die Rowsetgröße geändert wurde, ist dies die neue Rowsetgröße.  
  
## <a name="sqlfetchbookmark"></a>SQL_FETCH_BOOKMARK  
 Die folgenden Regeln gelten.  
  
|Bedingung|Erste Zeile des neuen Rowsets|  
|---------------|-----------------------------|  
|*BookmarkRow + FetchOffset < 1*|*Vor dem start*|  
|*1 < = BookmarkRow + FetchOffset \<LastResultRow =*|*BookmarkRow + FetchOffset*|  
|*BookmarkRow + FetchOffset > LastResultRow*|*Nach Ende*|  
  
 Weitere Informationen über Lesezeichen finden Sie unter [Lesezeichen (ODBC)](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
## <a name="effect-of-deleted-added-and-error-rows-on-cursor-movement"></a>Auswirkungen der gelöschten, hinzugefügt und Fehlerzeilen in Bewegung des Cursors  
 Statische und keysetgesteuerte Cursor erkennen manchmal Zeilen hinzugefügt werden, auf das Ergebnis festgelegt, und Entfernen von Zeilen, die aus dem Resultset gelöscht. Durch Aufrufen von **SQLGetInfo** mit dem SQL_STATIC_CURSOR_ATTRIBUTES2 und SQL_KEYSET_CURSOR_ATTRIBUTES2 "Optionen", und betrachten die SQL_CA2_SENSITIVITY_ADDITIONS SQL_CA2_SENSITIVITY_DELETIONS und SQL_CA2_SENSITIVITY_ UPDATES Bitmasken, eine Anwendung bestimmt, ob hierzu Cursor von einem bestimmten Treiber implementiert. Treiber, die gelöschte Zeilen zu erkennen und entfernen können, beschreiben in den folgenden Abschnitten die Auswirkungen dieses Verhaltens. Für den Treiber, die gelöschte Zeilen erkannt, aber sie können nicht entfernt werden, Löschvorgänge wirken sich nicht auf Cursor Bewegungen und in den folgenden Abschnitten gelten nicht.  
  
 Wenn der Cursor Zeilen zum Resultset hinzugefügt erkennt oder Zeilen aus dem Resultset gelöscht entfernt, wird es angezeigt, als ob diese Änderungen erkannt wird nur dann, wenn sie die Daten abruft. Dies schließt die Groß-/Kleinschreibung bei **SQLFetchScroll** mit FetchOrientation SQL_FETCH_RELATIVE und FetchOffset auf 0 festgelegt, um das gleiche Rowset untergeordnete festgelegt aufgerufen wird, aber enthält keine den Fall, wenn SQLSetPos mit fOption auf SQL_ aufgerufen wird AKTUALISIEREN. In letzterem Fall werden die Daten in den Puffern Rowset aktualisiert, aber nicht erneut abgerufen, und gelöschte Zeilen werden nicht aus dem Resultset entfernt. Daher, wenn eine Zeile gelöscht oder in das aktuelle Rowset eingefügt wird, werden der Cursor nicht die Rowset-Puffer geändert. Stattdessen wird die Änderung, wenn es beliebiges Rowset, die abruft zuvor die gelöschte Zeile enthalten oder enthält jetzt die eingefügte Zeile erkannt.  
  
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
  
 Wenn **SQLFetchScroll** ein neues Rowsets, die eine Position relativ zum aktuellen Rowset - zurückgibt, also FetchOrientation ist SQL_FETCH_NEXT, SQL_FETCH_PRIOR oder SQL_FETCH_RELATIVE: er enthält keine Änderungen an das aktuelle Rowset Wenn die Anfangsposition des neuen Rowsets zu berechnen. Allerdings ist diese Änderungen außerhalb der aktuellen Rowset enthalten, wenn es entdeckt werden kann. Darüber hinaus, wenn **SQLFetchScroll** gibt ein neues Rowset, das eine Position, die unabhängig von der das aktuelle Rowset - verfügt über FetchOrientation wird SQL_FETCH_FIRST SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE oder SQL_FETCH_BOOKMARK - es enthält alle Änderungen, die erkannt werden, ist es auch, wenn sie in das aktuelle Rowset sind.  
  
 Bei der Bestimmung, ob die neu hinzugefügte Zeilen innerhalb oder außerhalb der aktuellen Rowsets sind, gilt eine partielle Rowset in den letzten gültigen Zeile enden; d. h. die letzte Zeile, die für die Zeile nicht SQL_ROW_NOROW ist. Nehmen wir beispielsweise an, der Cursor befindet sich der neu hinzugefügte Zeilen erkennen kann, das aktuelle Rowset ist eine partielle Rowset, die Anwendung fügt neue Zeilen hinzu, und der Cursor fügt diese Zeilen am Ende des Resultsets. Wenn die Anwendung ruft **SQLFetchScroll** mit FetchOrientation festgelegt SQL_FETCH_NEXT, **SQLFetchScroll** gibt das Rowset, beginnend mit der ersten neu hinzugefügte Zeile zurück.  
  
 Nehmen wir beispielsweise an das aktuelle Rowset besteht aus Zeilen 21 bis 30, die Rowsetgröße ist 10, der Cursor entfernt Zeilen, die aus dem Resultset gelöscht und der Cursor erkennt Zeilen zum Resultset hinzugefügt. Die folgende Tabelle zeigt die Zeilen **SQLFetchScroll** in verschiedenen Situationen gibt.  
  
|Ändern|FETCH-Typ|FetchOffset|Neue Rowset [1]|  
|------------|----------------|-----------------|---------------------|  
|Löschen Sie Zeile 21|NEXT|0|31 bis 40|  
|Zeile 31 löschen|NEXT|0|32 bis 41|  
|Einfügen einer Zeile zwischen Zeilen 21 und 22|NEXT|0|31 bis 40|  
|Einfügen einer Zeile zwischen den Zeilen 30 und 31|NEXT|0|Eingefügte Zeile 31 bis 39|  
|Löschen Sie Zeile 21|PRIOR|0|11 bis 20|  
|Zeile 20 löschen|PRIOR|0|10 bis 19|  
|Einfügen einer Zeile zwischen Zeilen 21 und 22|PRIOR|0|11 bis 20|  
|Einfügen einer Zeile zwischen Zeilen 20 und 21|PRIOR|0|eingefügte Zeile 12 bis 20|  
|Löschen Sie Zeile 21|RELATIVE|0|22 bis 31<sup>[2]</sup>|  
|Löschen Sie Zeile 21|RELATIVE|1|22 bis 31|  
|Einfügen einer Zeile zwischen Zeilen 21 und 22|RELATIVE|0|21, eingefügten Zeile 22 bis 29|  
|Einfügen einer Zeile zwischen Zeilen 21 und 22|RELATIVE|1|22 bis 31|  
|Löschen Sie Zeile 21|ABSOLUTE|21|22 bis 31<sup>[2]</sup>|  
|Zeile 22 löschen|ABSOLUTE|21|21, 23 bis 31|  
|Einfügen einer Zeile zwischen Zeilen 21 und 22|ABSOLUTE|22|Eingefügte Zeile 22 bis 29|  
  
 [1] für diese Spalte verwendet die Zeilennummern, bevor Zeilen eingefügt oder gelöscht wurden.  
  
 [2] In diesem Fall versucht, der Cursor ab Zeile 21 Zeilen zurückgeben. Da Zeile 21 gelöscht wurde, ist die erste Zeile zurückgegebene Zeile 22.  
  
 Fehlerzeilen (d. h. Zeilen mit dem Status der SQL_ROW_ERROR) wirken sich nicht auf Bewegung des Cursors aus. Z. B. wenn das aktuelle Rowset mit Zeile 11 und den Status der beginnt Zeile 11 ist SQL_ROW_ERROR, Aufrufen von **SQLFetchScroll** FetchOrientation SQL_FETCH_RELATIVE und FetchOffset festgelegt auf 5 festgelegt ab Zeile 16, Rowset zurückgibt genau wie bei der Status für die Zeile 11 SQL_SUCCESS zurück.  
  
## <a name="returning-data-in-bound-columns"></a>Zurückgeben von Daten in gebundenen Spalten  
 **SQLFetchScroll** Daten im gebundenen Spalten gibt, auf die gleiche Weise wie **SQLFetch**. Weitere Informationen finden Sie unter "Zurückgeben von Daten in gebundenen Spalten" in [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Wenn keine Spalten gebunden sind, **SQLFetchScroll** keine Daten zurückgibt, jedoch werden die Blockcursor an die angegebene Position verschoben. Gibt an, ob die Daten von ungebundenen Spalten, die von einem Blockcursor mit abgerufen werden können **SQLGetData** hängt von den Treiber. Diese Funktion wird unterstützt, wenn ein Aufruf von **SQLGetInfo** das bit für den Informationstyp SQL_GETDATA_EXTENSIONS SQL_GD_BLOCK zurückgibt.  
  
## <a name="buffer-addresses"></a>Pufferadressen  
 **SQLFetchScroll** verwendet die gleiche Formel zum Ermitteln der Adresse der Daten und Längenindikator/Puffer als **SQLFetch**. Weitere Informationen finden Sie unter "Pufferadressen" in [SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="row-status-array"></a>Zeilenstatusarray  
 **SQLFetchScroll** legt die Werte in der zeilenstatusarray in die gleiche Weise wie SQLFetch fest. Weitere Informationen finden Sie unter "Zeilenstatusarray" in [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="rows-fetched-buffer"></a>Die Zeilen abgerufen, Puffer  
 **SQLFetchScroll** gibt die Anzahl der Zeilen im Puffer abgerufenen Zeilen abgerufen werden, auf die gleiche Weise wie **SQLFetch**. Weitere Informationen finden Sie unter "Zeilen abgerufen Puffer" in [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 Wenn eine Anwendung ruft **SQLFetchScroll** in einem ODBC-3.x-Treiber, ruft der Treiber-Manager **SQLFetchScroll** im Treiber. Wenn eine Anwendung ruft **SQLFetchScroll** in eine ODBC 2.x-Treiber ruft der Treiber-Manager SQLExtendedFetch im Treiber. Da **SQLFetchScroll** und SQLExtendedFetch Behandeln von Fehlern in leicht unterschiedliche Weise, die Anwendung sieht etwas anderen Fehlerverhalten beim Aufruf **SQLFetchScroll** in ODBC 2.x und ODBC 3.x-Treiber.  
  
 **SQLFetchScroll** Fehler und Warnungen zurückgegeben, auf die gleiche Weise wie **SQLFetch**; Weitere Informationen finden Sie unter "Fehlerbehandlung" in **SQLFetch**. **SQLExtendedFetch** gibt Fehler zurück, auf die gleiche Weise wie **SQLFetch**, mit den folgenden Ausnahmen:  
  
 Beim Auftreten einer Warnung, die für eine bestimmte Zeile im Rowset gilt, legt SQLExtendedFetch den entsprechenden Eintrag im Array Status Zeile SQL_ROW_SUCCESS, nicht SQL_ROW_SUCCESS_WITH_INFO fest.  
  
 Treten Fehler in jeder Zeile im Rowset, SQL_SUCCESS_WITH_INFO zurückgegeben. SQLExtendedFetch, nicht als SQL_ERROR zurück.  
  
 In jeder Gruppe der Statusdatensätze, die auf eine einzelne Zeile angewendet wird, darf der erste Status Datensatz SQLExtendedFetch zurückgegebenes SQLSTATE 01 s 01 (Fehler in Zeile;) **SQLFetchScroll** SQLSTATE wird nicht zurückgegeben. Wenn SQLExtendedFetch zusätzliche SQLSTATEs zurückgeben kann, muss sie weiterhin diese SQLSTATE zurückgeben.  
  
## <a name="sqlfetchscroll-and-optimistic-concurrency"></a>SQLFetchScroll und vollständige Parallelität  
 Falls ein Cursor verwendet die optimistische nebenläufigkeit –, also das SQL_ATTR_CONCURRENCY-Anweisungsattribut den Wert SQL_CONCUR_VALUES oder SQL_CONCUR_ROWVER ist - **SQLFetchScroll** aktualisiert die optimistische nebenläufigkeit-Werte, die durch die Daten verwendet wird die Quelle zu erkennen, ob eine Zeile geändert wurde. Dies geschieht, wenn **SQLFetchScroll** ein neues Rowsets, die auch bei der es sich um das aktuelle Rowset refetches abruft. (Es heißt mit FetchOrientation auf SQL_FETCH_RELATIVE und FetchOffset legen Sie auf 0 festgelegt.)  
  
## <a name="sqlfetchscroll-and-odbc-2x-drivers"></a>SQLFetchScroll und ODBC 2.x-Treiber  
 Wenn eine Anwendung ruft **SQLFetchScroll** in eine ODBC 2.x-Treiber ordnet der Treiber-Manager diesen Aufruf an **SQLExtendedFetch**. Sie übergibt die folgenden Werte für die Argumente der **SQLExtendedFetch**.  
  
|SQLExtendedFetch-argument|Wert|  
|-------------------------------|-----------|  
|StatementHandle|StatementHandle in **SQLFetchScroll**.|  
|FetchOrientation|FetchOrientation in **SQLFetchScroll**.|  
|FetchOffset|Wenn FetchOrientation nicht sql_fetch_bookmark auf, den Wert der FetchOffset-Argument in ist **SQLFetchScroll** verwendet wird.<br /><br /> Wenn FetchOrientation SQL_FETCH_BOOKMARK ist, wird der Wert, der unter der Adresse, die durch das SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungsattribut angegebene gespeicherte verwendet.|  
|RowCountPtr|Die Adresse, die durch das SQL_ATTR_ROWS_FETCHED_PTR-Attribut-Anweisung angegeben wird.|  
|RowStatusArray|Die Adresse, die durch das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR angegeben wird.|  
  
 Weitere Informationen finden Sie unter [Blockcursor, scrollbare Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
  
## <a name="descriptors-and-sqlfetchscroll"></a>Deskriptoren und SQLFetchScroll  
 **SQLFetchScroll** Deskriptoren interagiert, auf die gleiche Weise wie **SQLFetch**. Weitere Informationen finden Sie im Abschnitt "Deskriptoren und SQLFetchScroll" in [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [spaltenbezogene Bindungen](../../../odbc/reference/develop-app/column-wise-binding.md), [zeilenbezogene Bindungen](../../../odbc/reference/develop-app/row-wise-binding.md), [positioniert, Update und Delete-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md), und [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Bulk Insert, Update oder Delete-Vorgänge|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen einer einzelnen Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Schließen des Cursors in der Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Die Anzahl der Resultsets zurückgeben von Resultsetspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset, oder aktualisieren oder Löschen von Daten im Resultset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Wenn eine Anweisungsattribut|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
