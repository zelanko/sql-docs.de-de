---
title: SQLExecDirect-Funktion | Microsoft Docs
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
ms.openlocfilehash: 5739e397467deb684a4cd6c7b13a507f30b53fa7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286110"
---
# <a name="sqlexecdirect-function"></a>SQLExecDirect-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLExecDirect** führt eine präparierbare Anweisung aus, indem die aktuellen Werte der Parametermarkervariablen verwendet werden, wenn Parameter in der Anweisung vorhanden sind. **SQLExecDirect** ist die schnellste Möglichkeit, eine SQL-Anweisung zur einmaligen Ausführung zu übermitteln.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLExecDirect(  
     SQLHSTMT     StatementHandle,  
     SQLCHAR *    StatementText,  
     SQLINTEGER   TextLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *StatementText*  
 [Eingabe] SQL-Anweisung, die ausgeführt werden soll.  
  
 *TextLength*  
 [Eingabe] Länge von **StatementText* in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_NO_DATA, SQL_INVALID_HANDLE oder SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLExecDirect** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLExecDirect** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01001|Cursor-Operation-Konflikt|\**StatementText* enthielt eine positionierte Aktualisierungs- oder Löschanweisung, und keine Zeilen oder mehr zeilen wurden aktualisiert oder gelöscht. (Weitere Informationen zu Aktualisierungen in mehr als einer Zeile finden Sie in der Beschreibung des SQL_ATTR_SIMULATE_CURSOR *Attributs* in **SQLSetStmtAttr**.)<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01003|NULL-Wert in Set-Funktion eliminiert|Das Argument *StatementText* enthielt eine set-Funktion (z. **B. AVG**, **MAX**, **MIN**usw.), aber nicht die COUNT-Set-Funktion, und NULL-Argumentwerte wurden eliminiert, bevor die Funktion angewendet wurde. **COUNT** (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für einen Eingabe-/Ausgabe- oder Ausgabeparameter zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen- oder Nicht-NULL-Binärdaten. Wenn es sich um einen Zeichenfolgenwert handelte, wurde er rechts abgeschnitten. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01006|Berechtigung nicht widerrufen|\**StatementText* enthielt eine **REVOKE-Anweisung,** und der Benutzer verfügte nicht über die angegebene Berechtigung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01007|Privileg nicht gewährt|StatementText war eine **GRANT-Anweisung,** und dem Benutzer konnte die angegebene Berechtigung nicht gewährt werden. * \**|  
|01S02|Optionswert geändert|Ein angegebenes Anweisungsattribut war aufgrund von Implementierungsarbeitsbedingungen ungültig, sodass ein ähnlicher Wert vorübergehend ersetzt wurde. (**SQLGetStmtAttr** kann aufgerufen werden, um zu bestimmen, was der vorübergehend ersetzte Wert ist.) Der Ersatzwert ist für das *StatementHandle gültig,* bis der Cursor geschlossen wird. Die Anweisungsattribute, die geändert werden können, sind:<br /><br /> SQL_ ATTR_CONCURRENCY SQL_ ATTR_CURSOR_TYPE SQL_ ATTR_KEYSET_SIZE SQL_ ATTR_MAX_LENGTH SQL_ ATTR_MAX_ROWS SQL_ ATTR_QUERY_TIMEOUT SQL_ ATTR_SIMULATE_CURSOR<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Bruchschnitt|Die für einen Eingabe-/Ausgabe- oder Ausgabeparameter zurückgegebenen Daten wurden abgeschnitten, sodass der Bruchteil eines numerischen Datentyps abgeschnitten oder der Bruchteil der Zeitkomponente eines Zeit-, Zeitstempel- oder Intervalldatentyps abgeschnitten wurde.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07002|COUNT-Feld falsch|Die Anzahl der in **SQLBindParameter** angegebenen Parameter war kleiner als \*die Anzahl der Parameter in der SQL-Anweisung, die in *StatementText*enthalten ist.<br /><br /> **SQLBindParameter** wurde aufgerufen, wobei *ParameterValuePtr* auf einen Nullzeiger festgelegt *wurde, StrLen_or_IndPtr* nicht auf SQL_NULL_DATA oder SQL_DATA_AT_EXEC festgelegt wurde, und *InputOutputType* nicht auf SQL_PARAM_OUTPUT festgelegt, sodass die Anzahl der in **SQLBindParameter** angegebenen Parameter größer als die Anzahl der Parameter in der SQL-Anweisung in **StatementText*war.|  
|07006|Verletzung des eingeschränkten Datentypattributs|Der datenwert, der durch das *ValueType-Argument* in **SQLBindParameter** für den bound-Parameter identifiziert wurde, konnte nicht in den Datentyp konvertiert werden, der durch das *ParameterType-Argument* in **SQLBindParameter**identifiziert wurde.<br /><br /> Der Datenwert, der für einen Parameter zurückgegeben wird, der als SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT gebunden ist, konnte nicht in den Datentyp konvertiert werden, der durch das *ValueType-Argument* in **SQLBindParameter**identifiziert wurde.<br /><br /> (Wenn die Datenwerte für eine oder mehrere Zeilen nicht konvertiert werden konnten, aber eine oder mehrere Zeilen erfolgreich zurückgegeben wurden, gibt diese Funktion SQL_SUCCESS_WITH_INFO zurück.)|  
|07007|Eingeschränkte Parameterwertverletzung|Der Parametertyp SQL_PARAM_INPUT_OUTPUT_STREAM wird nur für einen Parameter verwendet, der Daten in Teilen sendet und empfängt. Ein Eingabegebundener Puffer ist für diesen Parametertyp nicht zulässig.<br /><br /> Dieser Fehler tritt auf, wenn der Parametertyp SQL_PARAM_INPUT_OUTPUT ist und wenn die \*in **SQLBindParameter** angegebenen *StrLen_or_IndPtr* nicht gleich SQL_NULL_DATA, SQL_DEFAULT_PARAM, SQL_LEN_DATA_AT_EXEC(len) oder SQL_DATA_AT_EXEC sind.|  
|07S01|Ungültige Verwendung des Standardparameters|Ein Parameterwert, der mit **SQLBindParameter**festgelegt wurde, wurde SQL_DEFAULT_PARAM, und der entsprechende Parameter hatte keinen Standardwert.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|21S01|Wertliste einfügen stimmt nicht mit der Spaltenliste überein|\**StatementText* enthielt eine **INSERT-Anweisung,** und die Anzahl der einzufügenden Werte stimmt nicht mit dem Grad der abgeleiteten Tabelle überein.|  
|21S02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|\**StatementText* enthielt eine **CREATE VIEW-Anweisung,** und die Liste der nicht qualifizierten Spalten (die Anzahl der Spalten, die für die Ansicht in den *Spaltenbezeichnerargumenten der SQL-Anweisung* angegeben wurden) enthielt mehr Namen als die Anzahl der Spalten in der abgeleiteten Tabelle, die durch das Abfragespezifikationsargument der *SQL-Anweisung* definiert wurde.|  
|22001|Zeichenfolgendaten, rechtes Abschneiden|Die Zuweisung eines Zeichens oder Binärwerts zu einer Spalte führte zum Abschneiden von nicht leeren Zeichendaten oder Binärdaten ohne Null.|  
|22002|Indikatorvariable erforderlich, aber nicht mitgeliefert|NULL-Daten wurden an einen Ausgabeparameter gebunden, dessen *StrLen_or_IndPtr* von **SQLBindParameter** festgelegt wurde, ein Nullzeiger war.|  
|22003|Numerischer Wert aofc|**StatementText* enthielt eine SQL-Anweisung, die einen gebundenen numerischen Parameter oder ein Literal enthielt, und der Wert verursachte, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde, wenn er der zugeordneten Tabellenspalte zugewiesen wurde.<br /><br /> Das Zurückgeben eines numerischen Werts (als numerische oder Zeichenfolge) für einen oder mehrere Eingabe-/Ausgabe- oder Ausgabeparameter hätte dazu geführt, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde.|  
|22007|Ungültiges Datumszeitformat|**StatementText* enthielt eine SQL-Anweisung, die eine Datums-, Uhrzeit- oder Zeitstempelstruktur als gebundenen Parameter enthielt, und der Parameter war jeweils ein ungültiges Datum, eine uhrlange Uhrzeit oder ein Zeitstempel.<br /><br /> Ein Eingabe-/Ausgabe- oder Ausgabeparameter war an eine Datums-, Uhrzeit- oder Zeitstempel-C-Struktur gebunden, und ein Wert im zurückgegebenen Parameter war jeweils ein ungültiges Datum, eine ungültige Uhrzeit oder ein Zeitstempel. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22008|Datetime-Feldüberlauf|**StatementText* enthielt eine SQL-Anweisung, die einen Datetime-Ausdruck enthielt, der bei der Berechnung zu einer ungültigen Datums-, Uhrzeit- oder Zeitstempelstruktur führte.<br /><br /> Ein Datumszeitausdruck, der für einen Eingabe-/Ausgabe- oder Ausgabeparameter berechnet wurde, führte zu einer ungültigen Datums-, Uhrzeit- oder Zeitstempel-C-Struktur.|  
|22012|Division durch Null|**StatementText* enthielt eine SQL-Anweisung, die einen arithmetischen Ausdruck enthielt, der die Division durch Null verursachte.<br /><br /> Ein arithmetischer Ausdruck, der für einen Eingabe-/Ausgabe- oder Ausgabeparameter berechnet wurde, führte zur Division durch Null.|  
|22015|Intervallfeldüberlauf|StatementText enthielt einen genauen numerischen oder Intervallparameter, der bei der Konvertierung in einen INTERVALL-SQL-Datentyp einen Verlust signifikanter Ziffern verursachte. * \**<br /><br /> StatementText enthielt einen Intervallparameter mit mehr als einem Feld, das bei der Konvertierung in einen numerischen Datentyp in einer Spalte keine Darstellung im numerischen Datentyp hatte. * \**<br /><br /> StatementText enthielt Parameterdaten, die einem SQL-Intervalltyp zugewiesen wurden, und es gab keine Darstellung des Werts des Typs C im Intervall-SQL-Typ. * \**<br /><br /> Das Zuweisen eines Eingabe-/Ausgabe- oder Ausgabeparameters, der ein exakter SQL-Typ für numerische Serregnen oder Intervalle war, zu einem Intervall-C-Typ verursachte einen Verlust signifikanter Ziffern.<br /><br /> Wenn ein Eingabe-/Ausgabe- oder Ausgabeparameter einer Intervall-C-Struktur zugewiesen wurde, gab es keine Darstellung der Daten in der Intervalldatenstruktur.|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|StatementText enthielt einen C-Typ, der ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp war. * \** Der SQL-Typ der Spalte war ein Zeichendatentyp; und der Wert in der Spalte war kein gültiges Literal des gebundenen C-Typs.<br /><br /> Wenn ein Eingabe-/Ausgabe- oder Ausgabeparameter zurückgegeben wurde, war der SQL-Typ ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. der Typ C wurde SQL_C_CHAR; und der Wert in der Spalte war kein gültiges Literal des gebundenen SQL-Typs.|  
|22019|Ungültiges Escapezeichen|\**StatementText* enthielt eine SQL-Anweisung, die ein LIKE-Prädikat mit einem **ESCAPE-Zeichen** in der **LIKE** **WHERE-Klausel** enthielt, und die Länge des Escapezeichens nach **ESCAPE** war nicht gleich 1.|  
|22025|Ungültige Escapesequenz|\**StatementText* enthielt eine SQL-Anweisung, die _"LIKE-Musterwert_ **LIKE** **ESCAPE** _ESCAPE-Escape-Zeichen_" in der **WHERE-Klausel** enthielt, und das Zeichen, das dem Escapezeichen im Musterwert folgte, war nicht "%" oder "_".|  
|23000|Verletzung der Integritätseinschränkung|**StatementText* enthielt eine SQL-Anweisung, die einen Parameter oder ein Literal enthielt. Der Parameterwert war NULL für eine Spalte, die in der zugeordneten Tabellenspalte als NICHT NULL definiert wurde, ein doppelter Wert wurde für eine Spalte angegeben, die nur eindeutige Werte enthalten darf, oder eine andere Integritätseinschränkung wurde verletzt.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor wurde auf dem *StatementHandle* von **SQLFetch** oder **SQLFetchScroll**positioniert. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Ein Cursor war geöffnet, aber nicht auf dem *StatementHandle*positioniert.<br /><br /> **StatementText* enthielt eine positionierte Aktualisierungs- oder Löschanweisung, und der Cursor wurde vor dem Anfang des Resultsets oder nach dem Ende des Resultsets positioniert.|  
|34000|Ungültiger Cursorname|**StatementText* enthielt eine positionierte Aktualisierungs- oder Löschanweisung, und der Cursor, auf den von der ausgeführten Anweisung verwiesen wurde, war nicht geöffnet.|  
|3D000|Ungültiger Katalogname|Der in *StatementText* angegebene Katalogname war ungültig.|  
|3F000|Ungültiger Schemaname|Der in *StatementText* angegebene Schemaname war ungültig.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcenstillstands mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntaxfehler oder Zugriffsverletzung|\**StatementText* enthielt eine SQL-Anweisung, die nicht präparierbar war oder einen Syntaxfehler enthielt.<br /><br /> Der Benutzer war nicht berechtigt, die sql-Anweisung in **StatementText*auszuführen.|  
|42S01|Basistabelle oder -ansicht ist bereits vorhanden|\**StatementText* enthielt eine **CREATE TABLE-** oder **CREATE VIEW-Anweisung,** und der angegebene Tabellenname oder Ansichtsname ist bereits vorhanden.|  
|42S02|Basistabelle oder Ansicht nicht gefunden|\**StatementText* enthielt eine **DROP TABLE** oder eine **DROP VIEW-Anweisung,** und der angegebene Tabellenname oder Ansichtsname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **ALTER TABLE-Anweisung,** und der angegebene Tabellenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE VIEW-Anweisung,** und ein tabellen- oder ansichtsname, der von der Abfragespezifikation definiert wurde, war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE INDEX-Anweisung,** und der angegebene Tabellenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **GRANT-** oder **REVOKE-Anweisung,** und der angegebene Tabellenname oder Ansichtsname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **SELECT-Anweisung,** und ein angegebener Tabellenname oder Ansichtsname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **DELETE-Anweisung**, **INSERT**oder **UPDATE-Anweisung,** und der angegebene Tabellenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE TABLE-Anweisung,** und eine in einer Einschränkung angegebene Tabelle (die auf eine andere Tabelle als die erstellte verweist) war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE SCHEMA-Anweisung,** und ein angegebener Tabellenname oder Ansichtsname war nicht vorhanden.|  
|42S11|Index ist bereits vorhanden|\**StatementText* enthielt eine **CREATE INDEX-Anweisung,** und der angegebene Indexname war bereits vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE SCHEMA-Anweisung,** und der angegebene Indexname war bereits vorhanden.|  
|42S12|Index nicht gefunden|\**StatementText* enthielt eine **DROP INDEX-Anweisung,** und der angegebene Indexname war nicht vorhanden.|  
|42S21|Spalte ist bereits vorhanden|\**StatementText* enthielt eine **ALTER TABLE-Anweisung,** und die in der **ADD-Klausel** angegebene Spalte ist nicht eindeutig oder identifiziert eine vorhandene Spalte in der Basistabelle.|  
|42S22|Spalte nicht gefunden|\**StatementText* enthielt eine **CREATE INDEX-Anweisung,** und einer oder mehrere der in der Spaltenliste angegebenen Spaltennamen waren nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **GRANT-** oder **REVOKE-Anweisung,** und ein angegebener Spaltenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **SELECT**-, **DELETE**- **INSERT**- oder **UPDATE-Anweisung,** und ein angegebener Spaltenname war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE TABLE-Anweisung,** und eine in einer Einschränkung angegebene Spalte (die auf eine andere Tabelle als die erstellte verweist) war nicht vorhanden.<br /><br /> \**StatementText* enthielt eine **CREATE SCHEMA-Anweisung,** und ein angegebener Spaltenname war nicht vorhanden.|  
|44000|WITH CHECK OPTION-Verstoß|Das Argument *StatementText* enthielt eine INSERT-Anweisung, die für eine angezeigte Tabelle ausgeführt wurde, oder eine Tabelle, die von der angezeigten Tabelle abgeleitet wurde, die durch Angabe von **WITH CHECK OPTION**erstellt wurde, sodass eine oder mehrere Zeilen, die von der **INSERT-Anweisung** betroffen sind, nicht mehr in der angezeigten Tabelle vorhanden sind. **INSERT**<br /><br /> Das Argument *StatementText* enthielt eine UPDATE-Anweisung, die für eine angezeigte Tabelle oder eine Tabelle ausgeführt wurde, die von der angezeigten Tabelle abgeleitet wurde, die durch Angabe von **WITH CHECK OPTION**erstellt wurde, sodass eine oder mehrere Zeilen, die von der **UPDATE-Anweisung** betroffen sind, nicht mehr in der angezeigten Tabelle vorhanden sind. **UPDATE**|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) **StatementText* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLExecDirect-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Das Argument *TextLength* war kleiner oder gleich 0, aber nicht gleich SQL_NTS.<br /><br /> Ein Parameterwert, der mit **SQLBindParameter**festgelegt wurde, war ein Nullzeiger, und der Parameterlängenwert war nicht 0, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Ein Parameterwert, der mit **SQLBindParameter**festgelegt wurde, war kein Nullzeiger; der C-Datentyp SQL_C_BINARY oder SQL_C_CHAR; und der Parameterlängenwert war kleiner als 0, war jedoch nicht SQL_NTS, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Ein Parameterlängenwert, der durch **SQLBindParameter** gebunden ist, wurde auf SQL_DATA_AT_EXEC festgelegt. Der SQL-Typ war entweder SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer datenquellenspezifischer Datentyp. und der SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo** war "Y".|  
|HY105|Ungültiger Parametertyp|Der für das Argument *InputOutputType* in **SQLBindParameter** angegebene Wert wurde SQL_PARAM_OUTPUT, und der Parameter war ein Eingabeparameter.|  
|HY109|Ungültige Cursorposition|\**StatementText* enthielt eine positionierte Aktualisierungs- oder Löschanweisung, und der Cursor wurde (durch **SQLSetPos** oder **SQLFetchScroll**) in einer Zeile positioniert, die gelöscht wurde oder nicht abgerufen werden konnte.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Die Anwendung ruft **SQLExecDirect** auf, um eine SQL-Anweisung an die Datenquelle zu senden. Weitere Informationen zur direkten Ausführung finden Sie unter [Direkte Ausführung](../../../odbc/reference/develop-app/direct-execution-odbc.md). Der Treiber ändert die Anweisung, um die von der Datenquelle verwendete SQL-Form zu verwenden, und sendet sie dann an die Datenquelle. Insbesondere ändert der Treiber die Escapesequenzen, die zum Definieren bestimmter Features in SQL verwendet werden. Die Syntax von Escape-Sequenzen finden Sie [unter Escape-Sequenzen in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md).  
  
 Die Anwendung kann eine oder mehrere Parametermarkierungen in der SQL-Anweisung enthalten. Um eine Parametermarkierung einzuschließen, bettet die Anwendung ein Fragezeichen (?) an der entsprechenden Position in die SQL-Anweisung ein. Informationen zu Parametern finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Wenn die SQL-Anweisung eine **SELECT-Anweisung** ist und die Anwendung mit dem Namen **SQLSetCursorName** einen Cursor einer Anweisung zuordnen soll, verwendet der Treiber den angegebenen Cursor. Andernfalls generiert der Treiber einen Cursornamen.  
  
 Wenn sich die Datenquelle im manuellen Commit-Modus befindet (die explizite Transaktionsinitiierung erfordert) und eine Transaktion noch nicht initiiert wurde, initiiert der Treiber eine Transaktion, bevor er die SQL-Anweisung sendet. Weitere Informationen finden Sie unter [Manueller Commit-Modus](../../../odbc/reference/develop-app/manual-commit-mode.md).  
  
 Wenn eine Anwendung **SQLExecDirect** zum Übermitteln einer **COMMIT-** oder **ROLLBACK-Anweisung** verwendet, ist sie zwischen DBMS-Produkten nicht interoperabel. Um eine Transaktion festzuschreiben oder zurückzusetzen, ruft eine Anwendung **SQLEndTran**auf.  
  
 Wenn **SQLExecDirect** auf einen Data-at-Execution-Parameter trifft, wird SQL_NEED_DATA zurückgegeben. Die Anwendung sendet die Daten mit **SQLParamData** und **SQLPutData**. Siehe [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)und [Senden von Long Data](../../../odbc/reference/develop-app/sending-long-data.md).  
  
 Wenn **SQLExecDirect** eine durchsuchte Aktualisierungs-, Einfüge- oder Löschanweisung ausführt, die sich nicht auf Zeilen in der Datenquelle auswirkt, gibt der Aufruf von **SQLExecDirect** SQL_NO_DATA zurück.  
  
 Wenn der Wert des SQL_ATTR_PARAMSET_SIZE-Anweisungsattributs größer als 1 ist und die SQL-Anweisung mindestens eine Parametermarkierung enthält, führt **SQLExecDirect** die SQL-Anweisung einmal für jeden Satz von Parameterwerten aus den Arrays aus, auf die das *ParameterValuePointer-Argument* beim Aufruf von **SQLBindParameter**zeigt. Weitere Informationen finden Sie unter [Arrays von Parameterwerten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Wenn Lesezeichen aktiviert sind und eine Abfrage ausgeführt wird, die keine Lesezeichen unterstützen kann, sollte der Treiber versuchen, die Umgebung zu einer Umgebung zu erführen, die Lesezeichen unterstützt, indem er einen Attributwert ändert und SQLSTATE 01S02 zurückgibt (Optionswert geändert). Wenn das Attribut nicht geändert werden kann, sollte der Treiber SQLSTATE HY024 (Ungültiger Attributwert) zurückgeben.  
  
> [!NOTE]  
>  Bei der Verwendung des Verbindungspoolings darf eine Anwendung keine SQL-Anweisungen ausführen, **USE** die die Datenbank oder den Kontext der Datenbank ändern, z. B. die _USE-Datenbankanweisung_ in SQL Server, die den von einer Datenquelle verwendeten Katalog ändert.  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)und [Beispiel ODBC Program](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen eines Commit- oder Rollbackvorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen mehrerer Datenzeilen|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben eines Cursornamens|[SQLGetCursorName-Funktion](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Abrufen eines Teils oder der gesamten Datenspalte|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Zurückgeben des nächsten Parameters zum Senden von Daten für|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Senden von Parameterdaten zur Ausführungszeit|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Festlegen eines Cursornamens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
|Festlegen eines Anweisungsattributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
