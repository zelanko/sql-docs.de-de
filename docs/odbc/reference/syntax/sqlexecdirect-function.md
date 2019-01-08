---
title: SQLExecDirect-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLExecDirect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExecDirect
helpviewer_keywords:
- SQLExecDirect function [ODBC]
ms.assetid: 985fcee1-f204-425c-bdd1-deb0e7d7bbd9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 794dc83a27d3c4882b5df4edbb4f2a645cd5ca1c
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590704"
---
# <a name="sqlexecdirect-function"></a>SQLExecDirect-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO-92  
  
 **Zusammenfassung**  
 **SQLExecDirect** führt eine vorbereitbare-Anweisung, die aktuellen Werte der Variablen Marker Parameter verwenden, wenn alle Parameter in der Anweisung vorhanden sind. **SQLExecDirect** ist die schnellste Möglichkeit, um eine SQL-Anweisung für die einmalige Ausführung zu senden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLExecDirect(  
     SQLHSTMT     StatementHandle,  
     SQLCHAR *    StatementText,  
     SQLINTEGER   TextLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *StatementText*  
 [Eingabe] SQL-Anweisung ausgeführt werden.  
  
 *TextLength*  
 [Eingabe] Länge der **StatementText* in Zeichen.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_NO_DATA, SQL_INVALID_HANDLE oder SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLExecDirect** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit eine *HandleType* von SQL_HANDLE_STMT auf, und ein *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLExecDirect** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01001|Konflikt beim Cursorvorgang|\**StatementText* enthaltenen ein positioniertes update oder delete-Anweisung, und keine Zeilen oder mehr als eine Zeile aktualisiert oder gelöscht wurden. (Weitere Informationen zu Updates für mehr als eine Zeile, finden Sie unter der Beschreibung der SQL_ATTR_SIMULATE_CURSOR *Attribut* in **SQLSetStmtAttr**.)<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01003|NULL-Wert in der Set-Funktion entfernt|Das Argument *StatementText* enthalten eine Set-Funktion (z. B. **AVG**, **MAX**, **MIN**und so weiter), aber nicht die **Anzahl**  -Funktion, und NULL Argument Werte wurden entfernt, bevor die Funktion angewendet wurde. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Zeichenfolgen-oder Binärdaten, die für die Eingabe/Ausgabe zurückgegeben oder Output-Parameter, die in das Abschneiden von nicht leeren Zeichen oder binäre Daten ungleich NULL geführt haben. Falls es sich um einen Zeichenfolgenwert handelt, war es, rechts abgeschnitten. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01006|Berechtigung nicht aufgehoben.|\**StatementText* enthalten eine **widerrufen** -Anweisung und der Benutzer keine die angegebene Berechtigung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01007|Berechtigung wurde nicht erteilt|*\*StatementText* wurde eine **GRANT** -Anweisung und der Benutzer konnte nicht gewährt werden die angegebene Berechtigung.|  
|01S02|Optionswert geändert|Ein Attribut für die angegebene Anweisung ist ungültig aufgrund der Implementierung Arbeitsbedingungen, also ein ähnlichen Wert vorübergehend ersetzt wurde. (**SQLGetStmtAttr** aufgerufen werden, um zu bestimmen, welche vorübergehend ersetzten Werts ist.) Der Ersatzwert ist gültig für die *StatementHandle* bis der Cursor geschlossen wird, an diesem Punkt das Anweisungsattribut setzt auf seinen ursprünglichen Wert. Die Anweisungsattribute, die geändert werden können, sind:<br /><br /> SQL_ ATTR_CONCURRENCY SQL_ ATTR_CURSOR_TYPE SQL_ ATTR_KEYSET_SIZE SQL_ ATTR_MAX_LENGTH SQL_ ATTR_MAX_ROWS SQL_ ATTR_QUERY_TIMEOUT SQL_ ATTR_SIMULATE_CURSOR<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01 S 07|Teilbereiche wurden abgeschnitten|Die Daten zurückgegeben, für die Eingabe/Ausgabe oder Output-Parameter wurde abgeschnitten, damit die Nachkommastellen eines numerischen Datentyps wurde abgeschnitten oder der Bruchteile den Teil der Zeitkomponente eines Datentyps Zeit, Timestamp- oder Intervall wurde abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07002|Falsches COUNT-Feld|Die Anzahl von Parametern, die im angegebenen **SQLBindParameter** war kleiner als die Anzahl von Parametern in der SQL-Anweisung, die in enthaltenen \* *StatementText*.<br /><br /> **SQLBindParameter** aufgerufen wurde, wobei *ParameterValuePtr* legen Sie auf ein null-Zeiger *StrLen_or_IndPtr* nicht auf SQL_NULL_DATA oder SQL_DATA_AT_EXEC, festgelegt und *InputOutputType*  nicht auf SQL_PARAM_OUTPUT, festgelegt werden, sodass die Anzahl von Parametern in angegeben **SQLBindParameter** war größer als die Anzahl von Parametern in der SQL-Anweisung, die in enthaltenen **StatementText* .|  
|07006|Attributverletzung eingeschränkter Daten|Der Wert von identifiziert die *ValueType* -Argument in **SQLBindParameter** für der gebundene Parameter nicht in der identifizierte Datentyp konvertiert werden kann die *ParameterType*-Argument in **SQLBindParameter**.<br /><br /> Der Wert zurückgegeben, für einen Parameter gebunden wird, wie SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT nicht in der identifizierte Datentyp konvertiert werden konnte die *ValueType* -Argument in **SQLBindParameter**.<br /><br /> (Wenn die Datenwerte für eine oder mehrere Zeilen nicht konvertiert werden konnte, aber eine oder mehrere Zeilen wurden erfolgreich zurückgegeben, diese Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07007|Verletzung aufgrund eines eingeschränkten Parameterwerts.|Der Parametertyp SQL_PARAM_INPUT_OUTPUT_STREAM wird nur für einen Parameter verwendet, die Daten sendet und empfängt in Teilen. Ein gebundener Eingabepuffer ist für diesen Parameter nicht zulässig.<br /><br /> Dieser Fehler tritt auf, wenn der Parametertyp SQL_PARAM_INPUT_OUTPUT ist und wenn die \* *StrLen_or_IndPtr* im angegebenen **SQLBindParameter** entspricht nicht auf SQL_NULL_DATA, SQL_DEFAULT_ PARAM, SQL_LEN_DATA_AT_EXEC(len) oder SQL_DATA_AT_EXEC.|  
|07S01|Ungültige Verwendung des Standardparameters|Legen Sie ein Parameterwert mit **SQLBindParameter**SQL_DEFAULT_PARAM wurde und der entsprechende Parameter keinen Standardwert.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|21S01|Die Liste einzufügender Werte entspricht nicht der Spaltenliste.|\**StatementText* enthalten eine **einfügen** -Anweisung, und die Anzahl der einzufügenden Werte entsprach nicht den Grad der abgeleiteten Tabelle.|  
|21S02|Spaltenzahl der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|\**StatementText* enthalten eine **CREATE VIEW** -Anweisung und der Liste der nicht qualifizierte Spalten (die angegebene Anzahl von Spalten für die Ansicht in der *Spaltenbezeichner* Argumente für SQL -Anweisung) enthält mehrere Namen als die Anzahl der Spalten in der abgeleiteten Tabelle definiert werden, indem die *-Abfragespezifikation* Argument der SQL-Anweisung.|  
|22001|Zeichenfolgendaten, rechts abgeschnitten.|Die Zuweisung von einem Zeichen- oder binären Wert einer Spalte führte das Abschneiden von nicht leeren Zeichendaten oder binäre Daten ungleich Null.|  
|22002|Anzeigevariable erforderlich, aber nicht angegeben|NULL-Daten an ein Output-Parameter gebunden wurde, deren *StrLen_or_IndPtr* festlegen, indem **SQLBindParameter** wurde ein null-Zeiger.|  
|22003|Numerischer Wert außerhalb des gültigen Bereichs|**StatementText* enthalten eine SQL-Anweisung, die einen gebundenen numerischen Parameter oder ein Literal enthalten und der Wert verursacht des gesamten (im Gegensatz zu Bruch) Teils der Zahl abgeschnitten wird, wenn der zugeordnete Tabellenspalte zugewiesen.<br /><br /> Einen numerischen Wert (als numerisch oder Zeichenfolge) für einen oder mehrere Eingabe-/Ausgabe- oder Ausgabe-Parameter zurückgegeben würde den gesamten (im Gegensatz zu Bruch) Teil der Zahl abgeschnitten wird verursacht.|  
|22007|Ungültiges Datetime-format|**StatementText* enthalten Sie eine SQL-Anweisung, die ein Datum, Uhrzeit oder Timestamp-Struktur als gebundene Parameter enthalten, und der Parameter war, jeweils ein ungültiges Datum, Uhrzeit oder Zeitstempel.<br /><br /> Ein Eingabe-/Ausgabe- oder Ausgabe-Parameter gebunden wurde ein Datum, Uhrzeit oder Zeitstempel C-Struktur, und ein Wert in der zurückgegebenen Parameter war, jeweils ein ungültiges Datum, Uhrzeit oder Zeitstempel. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22008|Überlauf im DateTime-Feld|**StatementText* enthalten eine SQL-Anweisung, die einen Datetime-Ausdruck enthalten, wenn berechnet, führte zu einem Datum, Uhrzeit oder Zeitstempel, die Struktur war ungültig.<br /><br /> Ein Datetime-Ausdruck berechnet, für die Eingabe/Ausgabe oder Ausgabeparameter führte dazu, dass ein Datum, Uhrzeit oder Zeitstempel C-Struktur, die ungültig war.|  
|22012|Division durch 0 (null)|**StatementText* enthalten eine SQL-Anweisung, die einen arithmetischen Ausdruck enthalten, die Division durch 0 (null) verursacht.<br /><br /> Ein arithmetischer Ausdruck berechnet, für die Eingabe/Ausgabe oder Ausgabeparameter führte Division durch 0 (null).|  
|22015|Überlauf bei Intervallfeld|*\*StatementText* einen genauen numerischen oder Intervall-Parameter enthalten, wenn auf ein Intervall von SQL-Datentyp konvertiert wird, verursacht einen Verlust signifikanter Ziffern.<br /><br /> *\*StatementText* einen intervallparameter mit mehr als ein Feld enthalten, bei der Konvertierung in einen numerischen Datentyp in einer Spalte keine Entsprechung in der numerische Datentyp haben.<br /><br /> *\*StatementText* enthaltenen Parameterdaten, die auf ein Intervall von SQL-Typ zugewiesen wurde, und es war keine Darstellung des Werts von der C-Typ in der SQL-Typ-Intervall.<br /><br /> Zuweisen von ein Eingabe-/Ausgabe- oder Ausgabe-Parameter, die einen genauen numerischen oder Intervall SQL-Typ in einen C Intervalltyp, der einen Verlust signifikanter Ziffern verursacht wurde.<br /><br /> Wenn ein Eingabe-/Ausgabe- oder Ausgabe-Parameter auf eine C-Intervall-Struktur zugewiesen wurde, gab es keine Entsprechung für die Daten in der Datenstruktur Intervall.|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|*\*StatementText* einen C-Typ enthalten, das war eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp; der SQL-Typ der Spalte einen Zeichendatentyp; und der Wert in der Spalte nicht wurde ein gültiger Literal des gebundenen Typen aus C.<br /><br /> Wenn ein Eingabe-/Ausgabe- oder Ausgabe-Parameter zurückgegeben wurde, war der SQL-Typ eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp. der C-Typ wurde SQL_C_CHAR; und kein Wert in der Spalte wurde ein gültiger Literal des gebundenen Typen aus SQL.|  
|22019|Ungültiges Escapezeichen|\**StatementText* enthalten eine SQL-Anweisung, die enthalten eine **wie** Prädikat mit einer **ESCAPE** in die **, in denen** -Klausel und die Länge der-Escapesequenz folgende Zeichen **ESCAPEZEICHEN** war nicht gleich 1.|  
|22025|Ungültige Escapesequenz|\**StatementText* enthielt eine SQL­Anweisung, die enthaltenen "**wie** _Musterwert_ **ESCAPE** _Escapezeichen_ "in der **, in denen** -Klausel und das Zeichen, die das Escapezeichen im Musterwert war keiner der"%"oder"_".|  
|23000|Verletzung der integritätseinschränkung|**StatementText* enthalten eine SQL-Anweisung, die einen Parameter oder ein Literal enthalten. Der Wert des Parameters wurde NULL für eine Spalte als NOT NULL in der zugeordneten Spalte definiert, ein doppelter Wert wurde angegeben, für eine Spalte beschränkt auf die nur eindeutige Werte enthalten, oder einige andere integritätseinschränkung verletzt wurde.|  
|24000|Ungültiger Cursorstatus|Ein Cursor positioniert wurde, auf die *StatementHandle* von **SQLFetch** oder **SQLFetchScroll**. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, aber nicht positioniert war die *StatementHandle*.<br /><br /> **StatementText* enthaltenen ein positioniertes update oder delete-Anweisung und der Cursor vor dem Start des Resultsets oder nach dem Ende des Resultsets positioniert wurde.|  
|34000|Ungültiger Cursorname|**StatementText* enthaltenen ein positioniertes update oder delete-Anweisung und der Cursor die ausgeführte Anweisung verweist auf konnte nicht geöffnet werden.|  
|3D000|Ungültiger Katalogname|Der Name des Katalogs im angegebenen *StatementText* war ungültig.|  
|3F000|Ungültiger Schemaname|Der Schemaname, der im angegebenen *StatementText* war ungültig.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntaxfehler oder zugriffsverletzung|\**StatementText* enthielt eine SQL­Anweisung, die nicht vorbereitbaren war oder einen Syntaxfehler enthalten.<br /><br /> Der Benutzer keine Berechtigung zum Ausführen der SQL-Anweisung, die in enthaltenen **StatementText*.|  
|42S01|Basistabelle oder-Sicht ist bereits vorhanden.|\**StatementText* enthalten eine **CREATE TABLE** oder **CREATE VIEW** -Anweisung und der Tabellenname oder Ansicht, die Namen bereits vorhanden ist.|  
|42S02|Die Basistabelle oder-Sicht wurde nicht gefunden|\**StatementText* enthalten eine **DROP TABLE** oder **DROP VIEW** -Anweisung und der angegebenen Tabelle oder Sichtname Name ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **ALTER TABLE** Anweisung und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE VIEW** -Anweisung und einem Tabellennamen oder Ansicht, die von der Abfragespezifikation definierten Namen ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE INDEX** Anweisung und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **GRANT** oder **widerrufen** -Anweisung und der angegebenen Tabelle oder Sichtname Name ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **wählen** -Anweisung und eine angegebene Tabelle oder Sichtname Name ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **löschen**, **einfügen**, oder **UPDATE** Anweisung und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE TABLE** -Anweisung und eine Tabelle in einer Einschränkung (Verweis auf eine Tabelle außer der erstellt wird) angegeben war nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE SCHEMA** -Anweisung und eine angegebene Tabelle oder Sichtname Name ist nicht vorhanden.|  
|42S11|Index ist bereits vorhanden.|\**StatementText* enthalten eine **CREATE INDEX** -Anweisung und der angegebene Indexname bereits vorhanden war.<br /><br /> \**StatementText* enthalten eine **CREATE SCHEMA** -Anweisung und der angegebene Indexname bereits vorhanden war.|  
|42S12|Der Index wurde nicht gefunden.|\**StatementText* enthalten eine **DROP INDEX** -Anweisung und der angegebene Indexname ist nicht vorhanden.|  
|42S21|Spalte ist bereits vorhanden.|\**StatementText* enthalten eine **ALTER TABLE** -Anweisung und die Spalte angegeben wird, der **hinzufügen** -Klausel ist nicht eindeutig oder identifiziert eine vorhandene Spalte in der Basistabelle.|  
|42S22|Spalte wurde nicht gefunden|\**StatementText* enthalten eine **CREATE INDEX** -Anweisung, und mindestens eine der Spalte in der Spaltenliste angegebene Namen ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **GRANT** oder **widerrufen** -Anweisung und einen Namen für die angegebene Spalte ist nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **wählen**, **löschen**, **einfügen**, oder **UPDATE** -Anweisung und einen angegebenen Spaltennamen war nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE TABLE** -Anweisung und eine Spalte in einer Einschränkung (Verweis auf eine Tabelle außer der erstellt wird) angegeben war nicht vorhanden.<br /><br /> \**StatementText* enthalten eine **CREATE SCHEMA** -Anweisung und einen Namen für die angegebene Spalte ist nicht vorhanden.|  
|44000|WITH CHECK OPTION-Verstoß|Das Argument *StatementText* enthalten eine **einfügen** -Anweisung für eine Tabelle ausgeführt oder eine Tabelle, abgeleitet aus der angezeigten Tabelle, die durch Angabe erstellt wurde **WITH CHECK OPTION**, sodass eine oder mehrere Zeilen auswirkt. der **einfügen** Anweisung wird nicht mehr in der angezeigten Tabelle vorhanden sein.<br /><br /> Das Argument *StatementText* enthalten eine **UPDATE** -Anweisung für eine Tabelle ausgeführt oder eine Tabelle, abgeleitet aus der angezeigten Tabelle, die durch Angabe erstellt wurde **WITH CHECK OPTION**, sodass eine oder mehrere Zeilen auswirkt. der **UPDATE** Anweisung wird nicht mehr in der angezeigten Tabelle vorhanden sein.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|(DM) **StatementText* wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLExecDirect** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) das Argument *TextLength* war kleiner oder gleich 0, aber nicht SQL_NTS gleich.<br /><br /> Legen Sie ein Parameterwert mit **SQLBindParameter**wurde ein null-Zeiger und die Länge der Parameterwert lag nicht 0, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM oder kleiner als oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Legen Sie ein Parameterwert mit **SQLBindParameter**, war es sich nicht um ein null-Zeiger; wurde von der C-Datentyp SQL_C_BINARY oder SQL_C_CHAR; und der Wert des Parameters Länge war kleiner als 0, aber nicht SQL_NTS, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_ PARAM, oder kleiner als oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Ein Längenwert für den Parameter gebunden wird, indem **SQLBindParameter** auf SQL_DATA_AT_EXEC festgelegt wurde, wurde des SQL-Typs, SQL_LONGVARCHAR, SQL_LONGVARBINARY, oder ein long-Daten datenquellenspezifische Datentyp und die SQL_NEED_LONG_DATA_LEN-Informationen Geben Sie in **SQLGetInfo** wurde von "Y".|  
|HY105|Ungültiger Parametertyp|Der angegebene Wert für das Argument *InputOutputType* in **SQLBindParameter** war SQL_PARAM_OUTPUT und des Parameters ein Eingabeparameter.|  
|HY109|Ungültige Cursorposition|\**StatementText* enthaltenen ein positioniertes update oder delete-Anweisung und der Cursor positioniert wurde (durch **SQLSetPos** oder **SQLFetchScroll**) in einer Zeile, die hatte, wurde gelöscht oder konnte nicht abgerufen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Ruft die Anwendung **SQLExecDirect** um eine SQL-Anweisung mit der Datenquelle zu senden. Weitere Informationen über die direkte Ausführung finden Sie unter [direkte Ausführung](../../../odbc/reference/develop-app/direct-execution-odbc.md). Der Treiber die Verwendung der Form von der Datenquelle verwendete SQL-Anweisung geändert und dann an die Datenquelle übermittelt. Insbesondere wird der Treiber die Escapesequenzen, die zum Definieren von bestimmte Funktionen in SQL geändert. Die Syntax der Escape-Sequenzen, finden Sie unter [Escapesequenzen in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md).  
  
 Die Anwendung kann eine oder mehrere parametermarkierungen in der SQL-Anweisung enthalten. Um eine parametermarkierung einzuschließen, bettet die Anwendung ein Fragezeichen (?), in der SQL-Anweisung, die gewünschte Position. Weitere Informationen zu Parametern finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Wenn die SQL-Anweisung ist eine **wählen** -Anweisung und ob die Anwendung **SQLSetCursorName** um einen Cursor mit einer Anweisung zu verknüpfen, klicken Sie dann den Treiber verwendet den angegebenen Cursor. Andernfalls generiert der Treiber einen Cursornamen.  
  
 Wenn die Datenquelle im Manualcommit-Modus (dafür müssen expliziten Transaktion Initiierung) und eine Transaktion nicht gestartet wurde wurde, initiiert der Treiber eine Transaktion vor dem Senden der SQL-Anweisung. Weitere Informationen finden Sie unter [Manualcommit-Modus](../../../odbc/reference/develop-app/manual-commit-mode.md).  
  
 Wenn eine Anwendung verwendet **SQLExecDirect** Übermitteln einer **COMMIT** oder **ROLLBACK** -Anweisung ist nicht möglich Interoperabilität zwischen DBMS-Produkte. Um einen commit oder Rollback einer Transaktions, eine Anwendung ruft **SQLEndTran**.  
  
 Wenn **SQLExecDirect** erkennt einen Data-at-Execution-Parameter, es wird SQL_NEED_DATA zurückgegeben. Die Anwendung sendet die Daten mit **SQLParamData** und **SQLPutData**. Finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md), und [Long-Daten senden](../../../odbc/reference/develop-app/sending-long-data.md).  
  
 Wenn **SQLExecDirect** führt ein gesuchtes Update, Insert oder Delete-Anweisung, die keine Zeilen in der Datenquelle, die den Aufruf von auswirkt, **SQLExecDirect** SQL_NO_DATA zurückgibt.  
  
 Wenn der Wert des Attributs-Anweisung verweist SQL_ATTR_PARAMSET_SIZE größer als 1 ist, und die SQL-Anweisung mindestens eine parametermarkierung enthält, **SQLExecDirect** führt die SQL-Anweisung einmal für jeden Satz von Parameterwerten aus die Arrays verweist die *ParameterValuePointer* Argument im Aufruf von **SQLBindParameter**. Weitere Informationen finden Sie unter [Arrays von Parameterwerten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Wenn Lesezeichen eingeschaltet sind und eine Abfrage ausgeführt wird, kann nicht die Lesezeichen unterstützen, der Treiber sollten versuchen, von der Umgebung zu einem umgewandelt werden soll, die Lesezeichen unterstützt, indem Sie einen Attributwert und Rückgabe von SQLSTATE 01 s 02 (der Optionswert wurde geändert). Wenn das Attribut kann nicht geändert werden, sollte der Treiber SQLSTATE HY024 zurück (ungültige Attribut-Wert).  
  
> [!NOTE]  
>  Wenn Sie Verbindungspooling verwenden, muss eine Anwendung nicht SQL-Anweisungen, die die Datenbank oder im Kontext der Datenbank, wie z. B. ändern Ausführen der **verwenden** _Datenbank_ -Anweisung in SQL Server, der Änderungen der Katalog, die von einer Datenquelle verwendet wird.  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md), und [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen eines Commit- oder Rollback-Vorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen mehrerer Zeilen von Daten|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
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
