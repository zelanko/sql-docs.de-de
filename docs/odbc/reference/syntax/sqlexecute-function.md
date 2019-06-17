---
title: SQLExecute-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLExecute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExecute
helpviewer_keywords:
- SQLExecute function [ODBC]
ms.assetid: 9286a01d-cde2-4b90-af94-9fd7f8da48bf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08eb9db7645448157a76b3bcfdd302f6654f68f5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537256"
---
# <a name="sqlexecute-function"></a>SQLExecute-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLExecute** führt eine vorbereitete Anweisung, die die aktuellen Werte der Variablen Marker Parameter verwenden, wenn einem Parametermarker in der Anweisung vorhanden sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLExecute(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_NO_DATA, SQL_INVALID_HANDLE, or SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLExecute** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, zurück ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und eine *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLExecute** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01001|Konflikt beim Cursorvorgang|Die vorbereitete Anweisung zugeordneten der *StatementHandle* enthaltenen ein positioniertes update oder delete-Anweisung, und keine Zeilen oder mehr als eine Zeile aktualisiert oder gelöscht wurden. (Weitere Informationen zu Updates für mehr als eine Zeile, finden Sie unter der Beschreibung der SQL_ATTR_SIMULATE_CURSOR *Attribut* in **SQLSetStmtAttr**.)<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01003|NULL-Wert in der Set-Funktion entfernt|Der vorbereiteten Anweisung zugeordneten *StatementHandle* enthalten eine Set-Funktion (z. B. **AVG**, **MAX**, **MIN**und so weiter), aber nicht die **Anzahl** -Funktion, und NULL Argument Werte wurden entfernt, bevor die Funktion angewendet wurde. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für ein Output-Parameter zurückgegeben hat das Abschneiden von nicht leeren Zeichen oder binäre Daten ungleich NULL. Falls es sich um einen Zeichenfolgenwert handelt, war es, rechts abgeschnitten. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01006|Berechtigung nicht aufgehoben.|Die vorbereitete Anweisung zugeordneten der *StatementHandle* wurde eine **widerrufen** -Anweisung und der Benutzer keine die angegebene Berechtigung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01007|Berechtigung wurde nicht erteilt|Der vorbereiteten Anweisung zugeordneten der *StatementHandle* wurde eine **GRANT** -Anweisung und der Benutzer konnte nicht gewährt werden die angegebene Berechtigung.|  
|01S02|Optionswert geändert|Ein Attribut für die angegebene Anweisung ist ungültig aufgrund der Implementierung Arbeitsbedingungen, also ein ähnlichen Wert vorübergehend ersetzt wurde. (**SQLGetStmtAttr** aufgerufen werden, um zu bestimmen, welche vorübergehend ersetzten Werts ist.) Der Ersatzwert ist gültig für die *StatementHandle* bis der Cursor geschlossen wird, an diesem Punkt das Anweisungsattribut setzt auf seinen ursprünglichen Wert. Die Anweisungsattribute, die geändert werden können, sind: SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT und SQL_ATTR_SIMULATE_CURSOR. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Teilbereiche wurden abgeschnitten|Die Daten zurückgegeben, für die Eingabe/Ausgabe oder Output-Parameter wurde abgeschnitten, damit die Nachkommastellen eines numerischen Datentyps wurde abgeschnitten oder der Bruchteile den Teil der Zeitkomponente eines Datentyps Zeit, Timestamp- oder Intervall wurde abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07002|Falsches COUNT-Feld|Die Anzahl von Parametern, die im angegebenen **SQLBindParameter** war kleiner als die Anzahl von Parametern in der SQL-Anweisung, die in enthaltenen \* *StatementText*.<br /><br /> **SQLBindParameter** aufgerufen wurde, wobei *ParameterValuePtr* legen Sie auf ein null-Zeiger *StrLen_or_IndPtr* nicht auf SQL_NULL_DATA oder SQL_DATA_AT_EXEC, festgelegt und *InputOutputType*  nicht auf SQL_PARAM_OUTPUT, festgelegt werden, sodass die Anzahl von Parametern in angegeben **SQLBindParameter** war größer als die Anzahl von Parametern in der SQL-Anweisung, die in enthaltenen **StatementText* .|  
|07006|Attributverletzung eingeschränkter Daten|Der Wert von identifiziert die *ValueType* -Argument in **SQLBindParameter** für der gebundene Parameter nicht in der identifizierte Datentyp konvertiert werden kann die *ParameterType*-Argument in **SQLBindParameter**.<br /><br /> Der Wert zurückgegeben, für einen Parameter gebunden wird, wie SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT nicht in der identifizierte Datentyp konvertiert werden konnte die *ValueType* -Argument in **SQLBindParameter**.<br /><br /> (Wenn die Datenwerte für eine oder mehrere Zeilen nicht konvertiert werden konnte, aber eine oder mehrere Zeilen wurden erfolgreich zurückgegeben, diese Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07007|Verletzung aufgrund eines eingeschränkten Parameterwerts.|Der Parametertyp SQL_PARAM_INPUT_OUTPUT_STREAM wird nur für einen Parameter verwendet, die Daten sendet und empfängt in Teilen. Ein gebundener Eingabepuffer ist für diesen Parameter nicht zulässig.<br /><br /> Dieser Fehler tritt auf, wenn der Parametertyp SQL_PARAM_INPUT_OUTPUT ist und wenn die \* *StrLen_or_IndPtr* im angegebenen **SQLBindParameter** entspricht nicht auf SQL_NULL_DATA, SQL_DEFAULT_ PARAM, SQL_LEN_DATA_AT_EXEC(len) oder SQL_DATA_AT_EXEC.|  
|07S01|Ungültige Verwendung des Standardparameters|Legen Sie ein Parameterwert mit **SQLBindParameter**SQL_DEFAULT_PARAM wurde und der entsprechende Parameter war es sich nicht um einen Parameter für einen kanonischen ODBC-Prozeduraufruf.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|21S02|Spaltenzahl der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|Der vorbereiteten Anweisung zugeordneten der *StatementHandle* enthalten eine **CREATE VIEW** -Anweisung und der Liste der nicht qualifizierte Spalten (die angegebene Anzahl von Spalten für die Ansicht in der  *Spalten-ID* Argumente der SQL-Anweisung) enthalten weitere Namen als die Anzahl der Spalten in der abgeleiteten Tabelle definiert werden, indem die *-Abfragespezifikation* Argument der SQL-Anweisung.|  
|22001|Zeichenfolgendaten, rechts abgeschnitten.|Die Zuweisung von einem Zeichen- oder binären Wert einer Spalte führte das Abschneiden von NichtLeer (Zeichen), (binär) nicht-Null-Zeichen oder Bytes.|  
|22002|Anzeigevariable erforderlich, aber nicht angegeben|NULL-Daten an ein Output-Parameter gebunden wurde, deren *StrLen_or_IndPtr* festlegen, indem **SQLBindParameter** wurde ein null-Zeiger.|  
|22003|Numerischer Wert außerhalb des gültigen Bereichs|Die vorbereitete Anweisung zugeordneten der *StatementHandle* enthalten einen gebundenen numerischen Parameter und der Wert des Parameters, verursacht des gesamten (im Gegensatz zu Bruch) Teils der Zahl abgeschnitten wird, wenn die zugeordnete zugewiesen Tabellenspalte.<br /><br /> Einen numerischen Wert (als numerisch oder Zeichenfolge) für einen oder mehrere Eingabe-/Ausgabe- oder Ausgabe-Parameter zurückgegeben würde den gesamten (im Gegensatz zu Bruch) Teil der Zahl abgeschnitten wird verursacht.|  
|22007|Ungültiges Datetime-format|Die vorbereitete Anweisung zugeordneten der *StatementHandle* enthalten eine SQL-Anweisung, die ein Datum, Uhrzeit oder Timestamp-Struktur als gebundene Parameter enthalten, und der Parameter war, bzw. ein ungültiges Datum, Uhrzeit, oder der Zeitstempel.<br /><br /> Ein Eingabe-/Ausgabe- oder Ausgabe-Parameter gebunden wurde ein Datum, Uhrzeit oder Zeitstempel C-Struktur, und ein Wert in der zurückgegebenen Parameter war, jeweils ein ungültiges Datum, Uhrzeit oder Zeitstempel. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22008|Überlauf im DateTime-Feld|Die vorbereitete Anweisung zugeordneten der *StatementHandle* enthalten eine SQL-Anweisung, die einen Datetime-Ausdruck enthalten, wenn berechnet, führte zu einem Datum, Uhrzeit oder Zeitstempel, die Struktur war ungültig.<br /><br /> Ein Datetime-Ausdruck berechnet, für die Eingabe/Ausgabe oder Ausgabeparameter führte dazu, dass ein Datum, Uhrzeit oder Zeitstempel C-Struktur, die ungültig war.|  
|22012|Division durch 0 (null)|Die vorbereitete Anweisung zugeordneten der *StatementHandle* enthalten einen arithmetischen Ausdruck, der Division durch 0 (null) verursacht.<br /><br /> Ein arithmetischer Ausdruck berechnet, für die Eingabe/Ausgabe oder Ausgabeparameter führte Division durch 0 (null).|  
|22015|Überlauf bei Intervallfeld|*\*StatementText* einen genauen numerischen oder Intervall-Parameter enthalten, wenn auf ein Intervall von SQL-Datentyp konvertiert wird, verursacht einen Verlust signifikanter Ziffern.<br /><br /> *\*StatementText* einen intervallparameter mit mehr als ein Feld enthalten, bei der Konvertierung in einen numerischen Datentyp in einer Spalte keine Entsprechung in der numerische Datentyp haben.<br /><br /> *\*StatementText* enthaltenen Parameterdaten, die auf ein Intervall von SQL-Typ zugewiesen wurde, und es war keine Darstellung des Werts von der C-Typ in der SQL-Typ-Intervall.<br /><br /> Zuweisen von ein Eingabe-/Ausgabe- oder Ausgabe-Parameter, die einen genauen numerischen oder Intervall SQL-Typ in einen C Intervalltyp, der einen Verlust signifikanter Ziffern verursacht wurde.<br /><br /> Wenn ein Eingabe-/Ausgabe- oder Ausgabe-Parameter auf eine C-Intervall-Struktur zugewiesen wurde, gab es keine Entsprechung für die Daten in der Datenstruktur Intervall.|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|*\*StatementText* einen C-Typ enthalten, das war eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp; der SQL-Typ der Spalte einen Zeichendatentyp; und der Wert in der Spalte nicht wurde ein gültiger Literal des gebundenen Typen aus C.<br /><br /> Wenn ein Eingabe-/Ausgabe- oder Ausgabe-Parameter zurückgegeben wurde, war der SQL-Typ eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp. der C-Typ wurde SQL_C_CHAR; und kein Wert in der Spalte wurde ein gültiger Literal des gebundenen Typen aus SQL.|  
|22019|Ungültiges Escapezeichen|Der vorbereiteten Anweisung zugeordnet *StatementHandle* enthalten eine **wie** Prädikat mit einer **mit Escapezeichen versehen** in die **, in denen** -Klausel, und die Länge der Escape-Zeichen folgenden **ESCAPE** war nicht gleich 1.|  
|22025|Ungültige Escapesequenz|Die vorbereitete Anweisung zugeordneten *StatementHandle* enthaltenen "**wie** _Musterwert_ **ESCAPE** _Escapezeichen Zeichen_"in der **, in denen** -Klausel und das Zeichen, die das Escapezeichen im Musterwert war keiner der"%"oder"_".|  
|23000|Verletzung der integritätseinschränkung|Die vorbereitete Anweisung zugeordneten der *StatementHandle* enthalten einen Parameter. Der Wert des Parameters wurde NULL für eine Spalte als NOT NULL in der zugeordneten Spalte definiert, ein doppelter Wert wurde angegeben, für eine Spalte beschränkt auf die nur eindeutige Werte enthalten, oder einige andere integritätseinschränkung verletzt wurde.|  
|24000|Ungültiger Cursorstatus|Ein Cursor positioniert wurde, auf die *StatementHandle* von **SQLFetch** oder **SQLFetchScroll**. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*.<br /><br /> Die vorbereitete Anweisung zugeordneten der *StatementHandle* enthalten ein positioniertes Update oder Delete-Statemen "," t "und" den Cursor vor dem Start des Resultsets oder nach dem Ende des Resultsets positioniert wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntaxfehler oder zugriffsverletzung|Der Benutzer keine Berechtigung zum Ausführen des vorbereiteten Anweisung zugeordneten der *StatementHandle*.|  
|44000|WITH CHECK OPTION-Verstoß|Die vorbereitete Anweisung zugeordneten *StatementHandle* enthalten eine **einfügen** -Anweisung für eine Tabelle ausgeführt oder eine Tabelle aus der angezeigten Tabelle, die erstellt wurde, indem Sie abgeleitet**WITH CHECK OPTION**, sodass eine oder mehrere Zeilen auswirkt. der **einfügen** Anweisung wird nicht mehr in der angezeigten Tabelle vorhanden sein.<br /><br /> Die vorbereitete Anweisung zugeordneten der *StatementHandle* enthalten ein **UPDATE** -Anweisung für eine Tabelle ausgeführt oder eine Tabelle aus der angezeigten Tabelle, die erstellt wurde, indem Sie abgeleitet**WITH CHECK OPTION**, sodass eine oder mehrere Zeilen auswirkt. der **UPDATE** Anweisung wird nicht mehr in der angezeigten Tabelle vorhanden sein.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLExecute** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) die *StatementHandle* wurde nicht vorbereitet.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|Legen Sie ein Parameterwert mit **SQLBindParameter**wurde ein null-Zeiger und die Länge der Parameterwert lag nicht 0, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM oder kleiner als oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Legen Sie ein Parameterwert mit **SQLBindParameter**, war es sich nicht um ein null-Zeiger; wurde von der C-Datentyp SQL_C_BINARY oder SQL_C_CHAR; und der Wert des Parameters Länge war kleiner als 0, aber nicht SQL_NTS, SQL_NULL_DATA, SQL_DEFAULT_PARAM oder SQL_DATA_ AT_EXEC, oder kleiner als oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Ein Längenwert für den Parameter gebunden wird, indem **SQLBindParameter** auf SQL_DATA_AT_EXEC festgelegt wurde, wurde des SQL-Typs, SQL_LONGVARCHAR, SQL_LONGVARBINARY, oder ein long-Daten datenquellenspezifische Datentyp und die SQL_NEED_LONG_DATA_LEN-Informationen Geben Sie in **SQLGetInfo** wurde von "Y".|  
|HY105|Ungültiger Parametertyp|Der angegebene Wert für das Argument *InputOutputType* in **SQLBindParameter** war SQL_PARAM_OUTPUT und des Parameters ein Eingabeparameter.|  
|HY109|Ungültige Cursorposition|Die vorbereitete Anweisung wurde ein positioniertes Update oder Delete-Anweisung und der Cursor positioniert wurde (durch **SQLSetPos** oder **SQLFetchScroll**) in einer Zeile, die hatte, wurde gelöscht oder konnte nicht abgerufen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
 **SQLExecute** können alle SQLSTATE, der zurückgegeben werden kann zurückgeben **SQLPrepare**basierend auf, wenn die Datenquelle für die SQL-Anweisung der Anweisung zugeordneten auswertet.  
  
## <a name="comments"></a>Kommentare  
 **SQLExecute** führt eine Anweisung vorbereitet, indem **SQLPrepare**. Nachdem die Anwendung verarbeitet oder die Ergebnisse von einem Aufruf von verwirft **SQLExecute**, die Anwendung aufrufen kann **SQLExecute** erneut mit neuen Parameterwerte. Weitere Informationen über die vorbereitete Ausführung finden Sie unter [vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
 Zum Ausführen einer **wählen** -Anweisung mehr als einmal, es muss die Anwendung aufrufen. **SQLCloseCursor** vor reexecuting der **wählen** Anweisung.  
  
 Wenn die Datenquelle im Manualcommit-Modus (dafür müssen expliziten Transaktion Initiierung) und eine Transaktion nicht gestartet wurde wurde, initiiert der Treiber eine Transaktion vor dem Senden der SQL-Anweisung. Weitere Informationen finden Sie unter [Transaktionen](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Wenn eine Anwendung verwendet **SQLPrepare** vorbereiten und **SQLExecute** Übermitteln einer **COMMIT** oder **ROLLBACK** -Anweisung ist nicht möglich Interoperabilität zwischen DBMS-Produkte. Rufen Sie einen commit oder Rollback einer Transaktions, **SQLEndTran**.  
  
 Wenn **SQLExecute** erkennt einen Data-at-Execution-Parameter, es wird SQL_NEED_DATA zurückgegeben. Die Anwendung sendet die Daten mit **SQLParamData** und **SQLPutData**. Finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), und [Long-Daten senden](../../../odbc/reference/develop-app/sending-long-data.md).  
  
 Wenn **SQLExecute** führt ein gesuchtes Update, Insert oder Delete-Anweisung, die keine Zeilen in der Datenquelle, die den Aufruf von auswirkt, **SQLExecute** SQL_NO_DATA zurückgibt.  
  
 Wenn der Wert des Attributs-Anweisung verweist SQL_ATTR_PARAMSET_SIZE größer als 1 ist, und die SQL-Anweisung mindestens eine parametermarkierung enthält, **SQLExecute** führt die SQL-Anweisung einmal für jeden Satz von Parameterwerten in Arrays Zeigt die  *\*ParameterValuePtr* Argument in den Aufrufen **SQLBindParameter**. Weitere Informationen finden Sie unter [Arrays von Parameterwerten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Wenn Lesezeichen aktiviert sind, und eine Abfrage ausgeführt wird, kann nicht die Lesezeichen unterstützen, der Treiber sollten versuchen, von der Umgebung zu einem umgewandelt werden soll, die Lesezeichen unterstützt, indem Sie einen Attributwert und Rückgabe von SQLSTATE 01 s 02 (der Optionswert wurde geändert). Wenn das Attribut kann nicht geändert werden, sollte der Treiber SQLSTATE HY024 zurück (ungültige Attribut-Wert).  
  
> [!NOTE]  
>  Wenn Sie Verbindungspooling verwenden, muss eine Anwendung nicht SQL-Anweisungen, die die Datenbank oder im Kontext der Datenbank, wie z. B. ändern Ausführen der **verwenden** _Datenbank_ -Anweisung in SQL Server, der Änderungen der Katalog, die von einer Datenquelle verwendet wird.  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), und [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Schließen des Cursors|[SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Ausführen eines Commit- oder Rollback-Vorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Abrufen mehrerer Zeilen von Daten|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Freigeben eines Anweisungshandles|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Ein Cursorname zurückgeben|[SQLGetCursorName-Funktion](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Abrufen von teilweise oder vollständig eine Spalte mit Daten|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Den nächsten Parameter zum Senden von Daten für die Rückgabe|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Senden von Daten von Parametern zum Zeitpunkt der Ausführung|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Ein Cursorname festlegen|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
|Wenn eine Anweisungsattribut|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
