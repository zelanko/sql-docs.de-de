---
description: SQLExecDirect-Funktion
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0e6f2c3ed2334915d941aa9bffa898627b4dfc2e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476132"
---
# <a name="sqlexecdirect-function"></a>SQLExecDirect-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLExecDirect** führt eine vorbereit Bare Anweisung aus, wobei die aktuellen Werte der Parameter markervariablen verwendet werden, wenn in der Anweisung Parameter vorhanden sind. **SQLExecDirect** ist die schnellste Möglichkeit, eine SQL-Anweisung für die einmalige Ausführung zu übermitteln.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLExecDirect(  
     SQLHSTMT     StatementHandle,  
     SQLCHAR *    StatementText,  
     SQLINTEGER   TextLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *Status Text*  
 Der Auszuführende SQL-Anweisung.  
  
 *TextLength*  
 Der Länge von **Status Text* in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_NO_DATA, SQL_INVALID_HANDLE oder SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLExecDirect** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die häufig von **SQLExecDirect** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01001|Konflikt beim Cursor Vorgang|\*" *Status Text* " enthielt eine positionierte UPDATE-oder DELETE-Anweisung, und es wurden keine Zeilen oder mehr als eine Zeile aktualisiert oder gelöscht. (Weitere Informationen zu Updates für mehr als eine Zeile finden Sie in der Beschreibung des SQL_ATTR_SIMULATE_CURSOR- *Attributs* in **SQLSetStmtAttr**.)<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01003|NULL-Wert in Set-Funktion entfernt|Das Argument " *Status Text* " enthielt eine Set-Funktion (z **. b. AVG**, **Max**, **Min**usw.), aber nicht die **count** Set-Funktion, und NULL-Argument Werte wurden vor dem Anwenden der Funktion gelöscht. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Zeichen folgen-oder Binärdaten, die für einen Eingabe-/Ausgabe-oder Ausgabeparameter zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind Wenn es sich um einen Zeichen folgen Wert handelt, wurde er rechts abgeschnitten. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01006|Berechtigung nicht widerrufen|\*" *Status Text* " enthielt eine Anweisung zum **widerrufen** , und der Benutzer hat nicht die angegebene Berechtigung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01007|Berechtigung nicht erteilt|" * \* Status Text* " war eine **Grant** -Anweisung, und dem Benutzer konnte die angegebene Berechtigung nicht erteilt werden.|  
|01s02 entsprechen|Optionswert geändert|Ein angegebenes Anweisungs Attribut war aufgrund von Implementierungs Arbeitsbedingungen ungültig, sodass ein ähnlicher Wert vorübergehend ersetzt wurde. (**SQLGetStmtAttr** kann aufgerufen werden, um zu bestimmen, was der temporär ersetzte Wert ist.) Der Ersatzwert ist für " *StatementHandle* " gültig, bis der Cursor geschlossen wird. an diesem Punkt wird das Anweisungs Attribut auf seinen vorherigen Wert zurückgesetzt. Die Anweisungs Attribute, die geändert werden können, sind:<br /><br /> SQL_ ATTR_CONCURRENCY SQL_ ATTR_CURSOR_TYPE SQL_ ATTR_KEYSET_SIZE SQL_ ATTR_MAX_LENGTH SQL_ ATTR_MAX_ROWS SQL_ ATTR_QUERY_TIMEOUT SQL_ ATTR_SIMULATE_CURSOR<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Abschneiden von Sekundenbruchteilen|Die Daten, die für einen Eingabe-/Ausgabe-oder Ausgabeparameter zurückgegeben wurden, wurden abgeschnitten, sodass der Bruch Teil eines numerischen Datentyps abgeschnitten wurde oder der Bruchteil der Zeitkomponente eines Zeit-, Zeitstempel-oder Intervall Datentyps abgeschnitten wurde.<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07002|Anzahl Feld falsch|Die in **SQLBindParameter** angegebene Anzahl von Parametern war kleiner als die Anzahl von Parametern in der SQL-Anweisung, die in " \* *Status Text*" enthalten ist.<br /><br /> **SQLBindParameter** wurde mit *ParameterValuePtr* aufgerufen, auf einen NULL-Zeiger festgelegt, *StrLen_or_IndPtr* nicht auf SQL_NULL_DATA oder SQL_DATA_AT_EXEC festgelegt, und *inputoutputtype* ist nicht auf SQL_PARAM_OUTPUT festgelegt, sodass die Anzahl der in **SQLBindParameter** angegebenen Parameter größer als die Anzahl der Parameter in der SQL-Anweisung in **Status Text*war.|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|Der Datenwert, der vom *ValueType* -Argument in **SQLBindParameter** für den gebundenen Parameter identifiziert wurde, konnte nicht in den Datentyp konvertiert werden, der durch das *Parameter Type* -Argument in **SQLBindParameter**identifiziert wird.<br /><br /> Der Datenwert, der für einen Parameter zurückgegeben wird, der als SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT gebunden ist, konnte nicht in den Datentyp konvertiert werden, der vom *ValueType* -Argument in **SQLBindParameter angegeben**wird.<br /><br /> (Wenn die Datenwerte für eine oder mehrere Zeilen nicht konvertiert werden konnten, aber eine oder mehrere Zeilen erfolgreich zurückgegeben wurden, gibt diese Funktion SQL_SUCCESS_WITH_INFO zurück.)|  
|07007|Verstoß gegen eingeschränkten Parameterwert|Der Parametertyp SQL_PARAM_INPUT_OUTPUT_STREAM wird nur für einen Parameter verwendet, der Daten in Teilen sendet und empfängt. Ein Eingabe gebundener Puffer ist für diesen Parametertyp nicht zulässig.<br /><br /> Dieser Fehler tritt auf, wenn der Parametertyp SQL_PARAM_INPUT_OUTPUT ist, und wenn die \* in **SQLBindParameter** angegebene *StrLen_or_IndPtr* nicht gleich SQL_NULL_DATA, SQL_DEFAULT_PARAM, SQL_LEN_DATA_AT_EXEC (len) oder SQL_DATA_AT_EXEC ist.|  
|07S01|Ungültige Verwendung des Standard Parameters.|Ein Parameterwert, der mit **SQLBindParameter**festgelegt wurde, wurde SQL_DEFAULT_PARAM, und der entsprechende Parameter hat keinen Standardwert.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|21s01|Die einfügewertliste stimmt nicht mit der Spaltenliste|\*" *Status Text* " enthielt eine **Insert** -Anweisung, und die Anzahl der einzufügenden Werte entsprach nicht dem Grad der abgeleiteten Tabelle.|  
|21s02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein.|\*" *Status Text* " enthielt eine **CREATE VIEW** -Anweisung, und die nicht qualifizierte Spaltenliste (die Anzahl der Spalten, die für die Sicht in den *Spalten-ID-* Argumenten der SQL-Anweisung angegeben wurde) enthielt mehr Namen als die Anzahl der Spalten in der abgeleiteten Tabelle, die durch das *Query-Specification-* Argument der SQL-Anweisung definiert wird.|  
|22001|Zeichen folgen Daten, rechter Abschneiden|Die Zuweisung eines Zeichens oder Binärwerts zu einer Spalte führte zum Abschneiden von nicht leeren Zeichendaten oder Binärdaten, die nicht NULL sind.|  
|22002|Die Indikator Variable ist erforderlich, aber nicht angegeben.|NULL-Daten wurden an einen Output-Parameter gebunden, dessen *StrLen_or_IndPtr* von **SQLBindParameter** festgelegt war, ein NULL-Zeiger war.|  
|22003|Numerischer Wert außerhalb des zulässigen Bereichs|*" *Status Text* " enthielt eine SQL-Anweisung, die einen gebundenen numerischen Parameter oder ein literales enthält, und der Wert hat bewirkt, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wird, wenn er der zugeordneten Tabellenspalte zugewiesen wird.<br /><br /> Das Zurückgeben eines numerischen Werts (als numerisch oder Zeichenfolge) für einen oder mehrere Eingabe-/Ausgabe-oder Ausgabeparameter hätte dazu geführt, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wird.|  
|22007|Ungültiges datetime-Format.|*" *Status Text* " enthielt eine SQL-Anweisung, die eine Datums-, Uhrzeit-oder Zeitstempel Struktur als gebundenen Parameter enthielt, und der-Parameter war, bzw. ein ungültiges Datum, eine Uhrzeit oder ein ungültiger Zeitstempel.<br /><br /> Ein Eingabe-/Ausgabe-oder Ausgabeparameter wurde an eine Datums-, Uhrzeit-oder Zeitstempel-C-Struktur gebunden, und ein Wert im zurückgegebenen Parameter war, bzw. ein ungültiges Datum, eine Uhrzeit oder ein ungültiger Zeitstempel. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22008|Überlauf bei DateTime-Feld|*" *Status Text* " enthielt eine SQL-Anweisung, die einen DateTime-Ausdruck enthielt, der bei der Berechnung zu einer ungültigen Datums-, Uhrzeit-oder Zeitstempel Struktur geführt hat.<br /><br /> Ein für einen Eingabe-/Ausgabe-oder Ausgabeparameter berechneter DateTime-Ausdruck führte zu einer ungültigen Datums-, Uhrzeit-oder Zeitstempel-C-Struktur.|  
|22012|Division durch Null|*" *Status Text* " enthielt eine SQL-Anweisung, die einen arithmetischen Ausdruck enthielt, der die Division durch Null verursacht hat.<br /><br /> Ein arithmetischer Ausdruck, der für einen Eingabe-/Ausgabe-oder Ausgabeparameter berechnet wurde, führte zu einer Division|  
|22015|Überlauf des Intervall Felds|" * \* Status Text* " enthielt einen exakten numerischen oder Intervall Parameter, der bei der Konvertierung in einen SQL-Datentyp "Interval" zu einem Verlust signifikanter Ziffern geführt hat.<br /><br /> " * \* Status Text* " enthielt einen Interval-Parameter mit mehr als einem Feld, das beim Konvertieren in einen numerischen Datentyp in einer Spalte keine Darstellung im numerischen Datentyp enthielt.<br /><br /> " * \* Status Text* " enthielt Parameterdaten, die einem SQL-Intervalltyp zugewiesen wurden, und es gab keine Darstellung des Werts des C-Typs im Intervall-SQL-Typ.<br /><br /> Das Zuweisen eines Eingabe-/Ausgabe-oder Ausgabe Parameters, der ein genauer numerischer oder Interval-SQL-Typ für einen Interval-C-Typ war, verursachte einen Verlust signifikanter<br /><br /> Wenn ein Eingabe-/Ausgabe-oder Ausgabeparameter einer Intervall-C-Struktur zugewiesen wurde, gab es keine Darstellung der Daten in der Intervall Datenstruktur.|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|" * \* Status Text* " enthielt einen C-Typ, bei dem es sich um einen exakten oder ungefähren numerischen Datentyp, einen DateTime-Datentyp oder einen Interval-Datentyp handelte. der SQL-Typ der Spalte war ein Zeichen Datentyp, und der Wert in der Spalte war kein gültiges Literale des gebundenen C-Typs.<br /><br /> Wenn ein Eingabe-/Ausgabe-oder Ausgabeparameter zurückgegeben wurde, war der SQL-Typ ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der C-Typ war SQL_C_CHAR. und der Wert in der Spalte war kein gültiges Literale des gebundenen SQL-Typs.|  
|22019|Ungültiges Escapezeichen|\*" *Status Text* " enthielt eine SQL-Anweisung, die ein **like** -Prädikat mit einem Escapezeichen **in der** **Where** -Klausel enthielt, und die Länge des Escape-Zeichens nach Escapezeichen **war nicht** gleich 1.|  
|22025|Ungültige Escape-Sequenz|\**"Status Text* " enthielt eine SQL-Anweisung, die in der **Where** -Klausel "**like** _Pattern Wert_ **Escape** _Escapezeichen_" enthielt, und das Zeichen nach dem Escapezeichen im Muster Wert war nicht "%" oder "_".|  
|23000|Verletzung der Integritäts Einschränkung|*" *Status Text* " enthielt eine SQL-Anweisung, die einen Parameter oder einen Literalwert enthielt. Der Parameterwert war für eine Spalte, die in der zugeordneten Tabellenspalte als NOT NULL definiert war, NULL. für eine Spalte, die nur eindeutige Werte enthält, wurde ein doppelter Wert angegeben, oder eine andere Integritäts Einschränkung wurde verletzt.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor wurde auf dem *StatementHandle* von **SQLFetch** oder **SQLFetchScroll**positioniert. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor war geöffnet, aber nicht auf dem *StatementHandle*positioniert.<br /><br /> *" *Status Text* " enthielt eine positionierte UPDATE-oder DELETE-Anweisung, und der Cursor befand sich vor dem Anfang des Resultsets oder nach dem Ende des Resultsets.|  
|34000|Ungültiger Cursorname|*" *Status Text* " enthielt eine positionierte UPDATE-oder DELETE-Anweisung, und der Cursor, auf den von der ausgeführten Anweisung verwiesen wird, war nicht geöffnet.|  
|3D000|Ungültiger Katalog Name.|Der in " *Status Text* " angegebene Katalog Name war ungültig.|  
|3F-|Ungültiger Schema Name.|Der in ' *Status Text* ' angegebene Schema Name war ungültig.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde aufgrund eines Ressourcen Deadlocks mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntax Fehler oder Zugriffsverletzung|\*" *Status Text* " enthielt eine SQL-Anweisung, die nicht vorbereit ist oder einen Syntax Fehler enthielt.<br /><br /> Der Benutzer verfügte nicht über die Berechtigung zum Ausführen der in **Status Text*enthaltenen SQL-Anweisung.|  
|42s01|Die Basistabelle oder-Sicht ist bereits vorhanden.|\*" *Status Text* " enthielt eine **CREATE TABLE** -oder **CREATE VIEW** -Anweisung, und der angegebene Tabellen-oder Sichtname ist bereits vorhanden.|  
|42s02|Die Basistabelle oder-Sicht wurde nicht gefunden.|\*" *Status Text* " enthielt eine **DROP TABLE** -oder **Drop View** -Anweisung, und der angegebene Tabellen-oder Sichtname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **ALTER TABLE** -Anweisung, und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **CREATE VIEW** -Anweisung, und ein von der Abfrage Spezifikation definierter Tabellen-oder Sichtname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Create Index** -Anweisung, und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Grant** -oder **Widerruf** -Anweisung, und der angegebene Tabellen-oder Sichtname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Select** -Anweisung, und ein angegebener Tabellenname oder Sichtname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Delete**-, **Insert**-oder **Update** -Anweisung, und der angegebene Tabellenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **CREATE TABLE** -Anweisung, und eine Tabelle, die in einer Einschränkung angegeben ist (die auf eine andere Tabelle als die erstellte Tabelle verweist), ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Create Schema** -Anweisung, und ein angegebener Tabellenname oder Sichtname ist nicht vorhanden.|  
|42s11|Index ist bereits vorhanden.|\*" *Status Text* " enthielt eine **Create Index** -Anweisung, und der angegebene Indexname war bereits vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Create Schema** -Anweisung, und der angegebene Indexname war bereits vorhanden.|  
|42s12|Index nicht gefunden.|\*" *Status Text* " enthielt eine **Drop Index** -Anweisung, und der angegebene Indexname ist nicht vorhanden.|  
|42s21|Spalte ist bereits vorhanden.|\*" *Status Text* " enthielt eine **ALTER TABLE** -Anweisung, und die in der **Add** -Klausel angegebene Spalte ist nicht eindeutig oder identifiziert eine vorhandene Spalte in der Basistabelle.|  
|42s22|Spalte nicht gefunden|\*" *Status Text* " enthielt eine **Create Index** -Anweisung, und mindestens einer der in der Spaltenliste angegebenen Spaltennamen ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Grant** -oder **Widerruf** -Anweisung, und ein angegebener Spaltenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Select**-, **Delete**-, **Insert**-oder **Update** -Anweisung, und ein angegebener Spaltenname ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **CREATE TABLE** -Anweisung, und eine Spalte, die in einer Einschränkung angegeben ist (verweist auf eine andere Tabelle als die erstellte Tabelle), ist nicht vorhanden.<br /><br /> \*" *Status Text* " enthielt eine **Create Schema** -Anweisung, und ein angegebener Spaltenname ist nicht vorhanden.|  
|44000|WITH CHECK OPTION-Verstoß|Das Argument " *Status Text* " enthielt eine **Insert** -Anweisung für eine angezeigte Tabelle oder eine Tabelle, die von der angezeigten Tabelle abgeleitet wurde, die durch die Angabe von **with Check Option**erstellt wurde, sodass eine oder mehrere von der **Insert** -Anweisung betroffene Zeilen in der angezeigten Tabelle nicht mehr vorhanden sind.<br /><br /> Das Argument " *Status Text* " enthielt eine **Update** -Anweisung für eine angezeigte Tabelle oder eine Tabelle, die von der angezeigten Tabelle abgeleitet wurde, die durch die Angabe von **with Check Option**erstellt wurde, sodass eine oder mehrere von der **Update** -Anweisung betroffene Zeilen nicht mehr in der angezeigten Tabelle enthalten sind.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) **Status Text* war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLExecDirect** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) das Argument *TextLength* war kleiner als oder gleich 0, aber nicht gleich SQL_NTS.<br /><br /> Ein mit **SQLBindParameter**festgelegter Parameterwert war ein NULL-Zeiger, und der Parameter Längen Wert war nicht 0, SQL_NULL_DATA SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Ein mit **SQLBindParameter**festgelegter Parameterwert war kein NULL-Zeiger. der C-Datentyp war SQL_C_BINARY oder SQL_C_CHAR. und der Parameter Längen Wert war kleiner als 0 (null), aber nicht SQL_NTS, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Ein Parameter Längen Wert, der durch **SQLBindParameter** gebunden ist, wurde auf SQL_DATA_AT_EXEC festgelegt. der SQL-Typ war entweder SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer Datenquellen spezifischer Datentyp. und der SQL_NEED_LONG_DATA_LEN Informationstyp in **SQLGetInfo** lautete "Y".|  
|HY105|Ungültiger Parametertyp|Der für das Argument *inputoutputtype* in **SQLBindParameter** angegebene Wert wurde SQL_PARAM_OUTPUT, und der Parameter war ein Eingabeparameter.|  
|HY109|Ungültige Cursorposition|\*" *Status Text* " enthielt eine positionierte UPDATE-oder DELETE-Anweisung, und der Cursor wurde (von **SQLSetPos** oder **SQLFetchScroll**) für eine Zeile positioniert, die gelöscht wurde oder nicht abgerufen werden konnte.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Die Anwendung ruft **SQLExecDirect** auf, um eine SQL-Anweisung an die Datenquelle zu senden. Weitere Informationen zur direkten Ausführung finden Sie unter [direkte Ausführung](../../../odbc/reference/develop-app/direct-execution-odbc.md). Der Treiber ändert die-Anweisung, um die von der Datenquelle verwendete SQL-Form zu verwenden, und sendet Sie dann an die Datenquelle. Insbesondere ändert der Treiber die Escapesequenzen, die zum Definieren bestimmter SQL-Funktionen verwendet werden. Die Syntax der Escapesequenzen finden Sie unter Escapesequenzen [in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md).  
  
 Die Anwendung kann einen oder mehrere Parametermarker in der SQL-Anweisung enthalten. Wenn Sie einen Parametermarker einschließen möchten, bettet die Anwendung ein Fragezeichen (?) an der entsprechenden Position in die SQL-Anweisung ein. Weitere Informationen zu Parametern finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Wenn die SQL-Anweisung eine **Select** -Anweisung ist und die Anwendung **SQLSetCursorName** aufruft, um einen Cursor einer Anweisung zuzuordnen, verwendet der Treiber den angegebenen Cursor. Andernfalls generiert der Treiber einen Cursor Namen.  
  
 Wenn sich die Datenquelle im manuellen Commitmodus befindet (was eine explizite Transaktions Initiierung erfordert) und eine Transaktion noch nicht initiiert wurde, initiiert der Treiber eine Transaktion, bevor Sie die SQL-Anweisung sendet. Weitere Informationen finden Sie unter [manueller Commit-Modus](../../../odbc/reference/develop-app/manual-commit-mode.md).  
  
 Wenn eine Anwendung **SQLExecDirect** zum Übermitteln einer **Commit** -oder **Rollback** -Anweisung verwendet, ist Sie zwischen DBMS-Produkten nicht interoperabel. Zum Ausführen eines Commits oder Rollbacks für eine Transaktion wird von einer Anwendung **SQLEndTran**aufgerufen.  
  
 Wenn **SQLExecDirect** auf einen Data-at-Execution-Parameter stößt, wird SQL_NEED_DATA zurückgegeben. Die Anwendung sendet die Daten mithilfe von **SQLParamData** und **SQLPutData**. Weitere Informationen finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)und [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md).  
  
 Wenn **SQLExecDirect** eine gesuchte Update-, INSERT-oder DELETE-Anweisung ausführt, die keine Zeilen in der Datenquelle beeinflusst, gibt der **SQLExecDirect** -Befehl SQL_NO_DATA zurück.  
  
 Wenn der Wert des SQL_ATTR_PARAMSET_SIZE-Anweisungs Attributs größer als 1 ist und die SQL-Anweisung mindestens einen Parametermarker enthält, führt **SQLExecDirect** die SQL-Anweisung einmal für jeden Satz von Parameterwerten aus den Arrays aus, auf die durch das *parametervaluepointer* -Argument im **SQLBindParameter**-Befehl verwiesen wird. Weitere Informationen finden Sie unter [Arrays von Parameter Werten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Wenn Lesezeichen aktiviert sind und eine Abfrage ausgeführt wird, die keine Lesezeichen unterstützt, sollte der Treiber versuchen, die Umgebung in eine zu konvertieren, die Lesezeichen unterstützt, indem ein Attribut Wert geändert und SQLSTATE 01s02 (Optionswert geändert) zurückgegeben wird. Wenn das Attribut nicht geändert werden kann, sollte der Treiber SQLSTATE HY024 (Ungültiger Attribut Wert) zurückgeben.  
  
> [!NOTE]  
>  Wenn Sie das Verbindungspooling verwenden, darf eine Anwendung keine SQL-Anweisungen ausführen, die die Datenbank oder den Kontext der Datenbank ändern, wie z. b. die **use** _Database_ -Anweisung in SQL Server, die den von einer Datenquelle verwendeten Katalog ändert.  
  
## <a name="code-example"></a>Codebeispiel  
 Weitere Informationen finden Sie unter [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)und [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen eines Commit-oder Rollback-Vorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen mehrerer Daten Zeilen|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben eines Cursor namens|[SQLGetCursorName-Funktion](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Abrufen eines Teils oder aller Datenspalten|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Zurückgeben des nächsten Parameters zum Senden von Daten|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Senden von Parameterdaten zur Ausführungszeit|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Festlegen eines Cursor namens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
|Festlegen eines Anweisungs Attributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
