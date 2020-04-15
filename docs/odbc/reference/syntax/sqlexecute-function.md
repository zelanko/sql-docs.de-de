---
title: SQLExecute-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5306567aebc229a8bc9d1d3c91bcbd8e79391752
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286070"
---
# <a name="sqlexecute-function"></a>SQLExecute-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLExecute** führt eine vorbereitete Anweisung aus, indem die aktuellen Werte der Parametermarkervariablen verwendet werden, wenn Parametermarkierungen in der Anweisung vorhanden sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLExecute(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_NO_DATA, SQL_INVALID_HANDLE oder SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLExecute** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLExecute** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01001|Cursor-Operation-Konflikt|Die vorbereitete Anweisung, die dem StatementHandle zugeordnet *ist,* enthielt eine positionierte Aktualisierungs- oder Löschanweisung, und keine Zeilen oder mehr zeilen wurden aktualisiert oder gelöscht. (Weitere Informationen zu Aktualisierungen in mehr als einer Zeile finden Sie in der Beschreibung des SQL_ATTR_SIMULATE_CURSOR *Attributs* in **SQLSetStmtAttr**.)<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01003|NULL-Wert in Set-Funktion eliminiert|Die vorbereitete Anweisung, *die StatementHandle* zugeordnet ist, enthielt eine set-Funktion (z. **B. AVG**, **MAX**, **MIN**usw.), aber nicht die COUNT-Set-Funktion, und NULL-Argumentwerte wurden eliminiert, bevor die Funktion angewendet wurde. **COUNT** (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für einen Ausgabeparameter zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind. Wenn es sich um einen Zeichenfolgenwert handelte, wurde er rechts abgeschnitten. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01006|Berechtigung nicht widerrufen|Die vorbereitete Anweisung, die dem *StatementHandle* zugeordnet ist, war eine **REVOKE-Anweisung,** und der Benutzer verfügte nicht über die angegebene Berechtigung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01007|Privileg nicht gewährt|Die vorbereitete Anweisung, die dem *StatementHandle* zugeordnet ist, war eine **GRANT-Anweisung,** und dem Benutzer konnte die angegebene Berechtigung nicht gewährt werden.|  
|01S02|Optionswert geändert|Ein angegebenes Anweisungsattribut war aufgrund von Implementierungsarbeitsbedingungen ungültig, sodass ein ähnlicher Wert vorübergehend ersetzt wurde. (**SQLGetStmtAttr** kann aufgerufen werden, um zu bestimmen, was der vorübergehend ersetzte Wert ist.) Der Ersatzwert ist für das *StatementHandle gültig,* bis der Cursor geschlossen wird. Die Anweisungsattribute, die geändert werden können, sind: SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT und SQL_ATTR_SIMULATE_CURSOR. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S07|Bruchschnitt|Die für einen Eingabe-/Ausgabe- oder Ausgabeparameter zurückgegebenen Daten wurden abgeschnitten, sodass der Bruchteil eines numerischen Datentyps abgeschnitten oder der Bruchteil der Zeitkomponente eines Zeit-, Zeitstempel- oder Intervalldatentyps abgeschnitten wurde.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07002|COUNT-Feld falsch|Die Anzahl der in **SQLBindParameter** angegebenen Parameter war kleiner als \*die Anzahl der Parameter in der SQL-Anweisung, die in *StatementText*enthalten ist.<br /><br /> **SQLBindParameter** wurde aufgerufen, wobei *ParameterValuePtr* auf einen Nullzeiger festgelegt *wurde, StrLen_or_IndPtr* nicht auf SQL_NULL_DATA oder SQL_DATA_AT_EXEC festgelegt wurde, und *InputOutputType* nicht auf SQL_PARAM_OUTPUT festgelegt, sodass die Anzahl der in **SQLBindParameter** angegebenen Parameter größer als die Anzahl der Parameter in der SQL-Anweisung in **StatementText*war.|  
|07006|Verletzung des eingeschränkten Datentypattributs|Der datenwert, der durch das *ValueType-Argument* in **SQLBindParameter** für den bound-Parameter identifiziert wurde, konnte nicht in den Datentyp konvertiert werden, der durch das *ParameterType-Argument* in **SQLBindParameter**identifiziert wurde.<br /><br /> Der Datenwert, der für einen Parameter zurückgegeben wird, der als SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT gebunden ist, konnte nicht in den Datentyp konvertiert werden, der durch das *ValueType-Argument* in **SQLBindParameter**identifiziert wurde.<br /><br /> (Wenn die Datenwerte für eine oder mehrere Zeilen nicht konvertiert werden konnten, aber eine oder mehrere Zeilen erfolgreich zurückgegeben wurden, gibt diese Funktion SQL_SUCCESS_WITH_INFO zurück.)|  
|07007|Eingeschränkte Parameterwertverletzung|Der Parametertyp SQL_PARAM_INPUT_OUTPUT_STREAM wird nur für einen Parameter verwendet, der Daten in Teilen sendet und empfängt. Ein Eingabegebundener Puffer ist für diesen Parametertyp nicht zulässig.<br /><br /> Dieser Fehler tritt auf, wenn der Parametertyp SQL_PARAM_INPUT_OUTPUT ist und wenn die \*in **SQLBindParameter** angegebenen *StrLen_or_IndPtr* nicht gleich SQL_NULL_DATA, SQL_DEFAULT_PARAM, SQL_LEN_DATA_AT_EXEC(len) oder SQL_DATA_AT_EXEC sind.|  
|07S01|Ungültige Verwendung des Standardparameters|Ein Parameterwert, der mit **SQLBindParameter**festgelegt wurde, wurde SQL_DEFAULT_PARAM, und der entsprechende Parameter war kein Parameter für einen Aufruf einer canonischen ODBC-Prozedur.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|21S02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|Die vorbereitete Anweisung, die dem *StatementHandle* zugeordnet ist, enthielt eine **CREATE VIEW-Anweisung,** und die liste der nicht qualifizierten Spalten (die Anzahl der Spalten, die für die Ansicht in den *Spaltenbezeichnerargumenten der SQL-Anweisung* angegeben wurden) enthielt mehr Namen als die Anzahl der Spalten in der abgeleiteten Tabelle, die durch das Abfragespezifikationsargument der *SQL-Anweisung* definiert wurde.|  
|22001|Zeichenfolgendaten, rechtes Abschneiden|Die Zuweisung eines Zeichens oder Binärwerts zu einer Spalte führte zum Abschneiden von nicht leeren (Zeichen) oder Nicht-NULL-Zeichen oder Bytes (binär).|  
|22002|Indikatorvariable erforderlich, aber nicht mitgeliefert|NULL-Daten wurden an einen Ausgabeparameter gebunden, dessen *StrLen_or_IndPtr* von **SQLBindParameter** festgelegt wurde, ein Nullzeiger war.|  
|22003|Numerischer Wert aofc|Die vorbereitete Anweisung, die dem StatementHandle zugeordnet *ist,* enthielt einen gebundenen numerischen Parameter, und der Parameterwert bewirkte, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde, wenn er der zugeordneten Tabellenspalte zugewiesen wurde.<br /><br /> Das Zurückgeben eines numerischen Werts (als numerische oder Zeichenfolge) für einen oder mehrere Eingabe-/Ausgabe- oder Ausgabeparameter hätte dazu geführt, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde.|  
|22007|Ungültiges Datumszeitformat|Die vorbereitete Anweisung, die dem *StatementHandle* zugeordnet ist, enthielt eine SQL-Anweisung, die ein Datum, eine Uhrzeit oder eine Zeitstempelstruktur als gebundenen Parameter enthielt, und der Parameter war jeweils ein ungültiges Datum, eine uhrlange Uhrzeit oder ein Zeitstempel.<br /><br /> Ein Eingabe-/Ausgabe- oder Ausgabeparameter war an eine Datums-, Uhrzeit- oder Zeitstempel-C-Struktur gebunden, und ein Wert im zurückgegebenen Parameter war jeweils ein ungültiges Datum, eine ungültige Uhrzeit oder ein Zeitstempel. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22008|Datetime-Feldüberlauf|Die vorbereitete Anweisung, die dem *StatementHandle* zugeordnet ist, enthielt eine SQL-Anweisung, die einen datetime-Ausdruck enthielt, der bei der Berechnung zu einer ungültigen Datums-, Uhrzeit- oder Zeitstempelstruktur führte.<br /><br /> Ein Datumszeitausdruck, der für einen Eingabe-/Ausgabe- oder Ausgabeparameter berechnet wurde, führte zu einer ungültigen Datums-, Uhrzeit- oder Zeitstempel-C-Struktur.|  
|22012|Division durch Null|Die vorbereitete Anweisung, die dem StatementHandle zugeordnet *ist,* enthielt einen arithmetischen Ausdruck, der die Division durch Null verursachte.<br /><br /> Ein arithmetischer Ausdruck, der für einen Eingabe-/Ausgabe- oder Ausgabeparameter berechnet wurde, führte zur Division durch Null.|  
|22015|Intervallfeldüberlauf|StatementText enthielt einen genauen numerischen oder Intervallparameter, der bei der Konvertierung in einen INTERVALL-SQL-Datentyp einen Verlust signifikanter Ziffern verursachte. * \**<br /><br /> StatementText enthielt einen Intervallparameter mit mehr als einem Feld, das bei der Konvertierung in einen numerischen Datentyp in einer Spalte keine Darstellung im numerischen Datentyp hatte. * \**<br /><br /> StatementText enthielt Parameterdaten, die einem SQL-Intervalltyp zugewiesen wurden, und es gab keine Darstellung des Werts des Typs C im Intervall-SQL-Typ. * \**<br /><br /> Das Zuweisen eines Eingabe-/Ausgabe- oder Ausgabeparameters, der ein exakter SQL-Typ für numerische Serregnen oder Intervalle war, zu einem Intervall-C-Typ verursachte einen Verlust signifikanter Ziffern.<br /><br /> Wenn ein Eingabe-/Ausgabe- oder Ausgabeparameter einer Intervall-C-Struktur zugewiesen wurde, gab es keine Darstellung der Daten in der Intervalldatenstruktur.|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|StatementText enthielt einen C-Typ, der ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp war. * \** Der SQL-Typ der Spalte war ein Zeichendatentyp; und der Wert in der Spalte war kein gültiges Literal des gebundenen C-Typs.<br /><br /> Wenn ein Eingabe-/Ausgabe- oder Ausgabeparameter zurückgegeben wurde, war der SQL-Typ ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. der Typ C wurde SQL_C_CHAR; und der Wert in der Spalte war kein gültiges Literal des gebundenen SQL-Typs.|  
|22019|Ungültiges Escapezeichen|Die vorbereitete Anweisung, *die StatementHandle* zugeordnet ist, enthielt ein LIKE-Prädikat mit einem **ESCAPE-Zeichen** in der **WHERE-Klausel,** und die Länge des Escapezeichens nach **ESCAPE** war nicht gleich 1. **LIKE**|  
|22025|Ungültige Escapesequenz|Die vorbereitete Anweisung, die *StatementHandle* zugeordnet ist, enthielt "**LIKE** _pattern value_ **ESCAPE** _escape character_" in der **WHERE-Klausel,** und das Zeichen, das dem Escapezeichen im Musterwert folgt, war nicht "%" oder "_".|  
|23000|Verletzung der Integritätseinschränkung|Die vorbereitete Anweisung, die dem StatementHandle zugeordnet *ist,* enthielt einen Parameter. Der Parameterwert war NULL für eine Spalte, die in der zugeordneten Tabellenspalte als NICHT NULL definiert wurde, ein doppelter Wert wurde für eine Spalte angegeben, die nur eindeutige Werte enthalten darf, oder eine andere Integritätseinschränkung wurde verletzt.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor wurde auf dem *StatementHandle* von **SQLFetch** oder **SQLFetchScroll**positioniert. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Im *StatementHandle*wurde ein Cursor geöffnet.<br /><br /> Die vorbereitete Anweisung, die dem StatementHandle zugeordnet *ist,* enthielt eine positionierte Aktualisierung oder Lösch-Statemen,t und der Cursor wurde vor dem Anfang des Resultsets oder nach dem Ende des Resultsets positioniert.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcenstillstands mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntaxfehler oder Zugriffsverletzung|Der Benutzer war nicht berechtigt, die vorbereitete Anweisung auszuführen, die dem *StatementHandle*zugeordnet ist.|  
|44000|WITH CHECK OPTION-Verstoß|Die vorbereitete Anweisung, *die StatementHandle* zugeordnet ist, enthielt eine **INSERT-Anweisung,** die für eine angezeigte Tabelle ausgeführt wurde, oder eine Tabelle, die von der angezeigten Tabelle abgeleitet wurde, die durch Angabe von WITH CHECK **OPTION**erstellt wurde, sodass eine oder mehrere Zeilen, die von der **INSERT-Anweisung** betroffen sind, nicht mehr in der angezeigten Tabelle vorhanden sind.<br /><br /> Die vorbereitete Anweisung, die dem *StatementHandle* zugeordnet ist, enthielt eine UPDATE-Anweisung, die für eine angezeigte Tabelle ausgeführt wurde, oder eine Tabelle, die von der angezeigten Tabelle abgeleitet wurde, die durch Angabe von **WITH CHECK OPTION**erstellt wurde, sodass eine oder mehrere Zeilen, die von der **UPDATE-Anweisung** betroffen sind, nicht mehr in der angezeigten Tabelle vorhanden sind. **UPDATE**|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLExecute-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Der *StatementHandle* wurde nicht erstellt.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|Ein Parameterwert, der mit **SQLBindParameter**festgelegt wurde, war ein Nullzeiger, und der Parameterlängenwert war nicht 0, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Ein Parameterwert, der mit **SQLBindParameter**festgelegt wurde, war kein Nullzeiger; der C-Datentyp SQL_C_BINARY oder SQL_C_CHAR; und der Parameterlängenwert war kleiner als 0, war jedoch nicht SQL_NTS, SQL_NULL_DATA, SQL_DEFAULT_PARAM oder SQL_DATA_AT_EXEC oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Ein Parameterlängenwert, der durch **SQLBindParameter** gebunden ist, wurde auf SQL_DATA_AT_EXEC festgelegt. Der SQL-Typ war entweder SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer datenquellenspezifischer Datentyp. und der SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo** war "Y".|  
|HY105|Ungültiger Parametertyp|Der für das Argument *InputOutputType* in **SQLBindParameter** angegebene Wert wurde SQL_PARAM_OUTPUT, und der Parameter war ein Eingabeparameter.|  
|HY109|Ungültige Cursorposition|Die vorbereitete Anweisung war eine positionierte Aktualisierungs- oder Löschanweisung, und der Cursor wurde (von **SQLSetPos** oder **SQLFetchScroll**) in einer Zeile positioniert, die gelöscht wurde oder nicht abgerufen werden konnte.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
 **SQLExecute** kann jede SQLSTATE zurückgeben, die von **SQLPrepare**zurückgegeben werden kann, basierend darauf, wann die Datenquelle die SQL-Anweisung auswertet, die der Anweisung zugeordnet ist.  
  
## <a name="comments"></a>Kommentare  
 **SQLExecute** führt eine von **SQLPrepare**vorbereitete Anweisung aus. Nachdem die Anwendung die Ergebnisse eines Aufrufs von **SQLExecute**verarbeitet oder verworfen hat, kann die Anwendung **SQLExecute** mit neuen Parameterwerten erneut aufrufen. Weitere Informationen zur vorbereiteten Ausführung finden Sie unter [Vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
 Um eine **SELECT-Anweisung** mehr als einmal auszuführen, muss die Anwendung **SQLCloseCursor** aufrufen, bevor die **SELECT-Anweisung** erneut ausgeführt wird.  
  
 Wenn sich die Datenquelle im manuellen Commit-Modus befindet (die explizite Transaktionsinitiierung erfordert) und eine Transaktion noch nicht initiiert wurde, initiiert der Treiber eine Transaktion, bevor er die SQL-Anweisung sendet. Weitere Informationen finden Sie unter [Transaktionen](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Wenn eine Anwendung **SQLPrepare** zum Vorbereiten und **SQLExecute** zum Übermitteln einer **COMMIT-** oder **ROLLBACK-Anweisung** verwendet, ist sie zwischen DBMS-Produkten nicht interoperabel. Um eine Transaktion festzuschreiben oder zurückzusetzen, rufen Sie **SQLEndTran**auf.  
  
 Wenn **SQLExecute** auf einen Data-at-Execution-Parameter trifft, gibt es SQL_NEED_DATA zurück. Die Anwendung sendet die Daten mit **SQLParamData** und **SQLPutData**. Siehe [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)und [Senden von Long Data](../../../odbc/reference/develop-app/sending-long-data.md).  
  
 Wenn **SQLExecute** eine durchsuchte Aktualisierungs-, Einfüge- oder Löschanweisung ausführt, die sich nicht auf Zeilen in der Datenquelle auswirkt, gibt der Aufruf von **SQLExecute** SQL_NO_DATA zurück.  
  
 Wenn der Wert des SQL_ATTR_PARAMSET_SIZE-Anweisungsattributs größer als 1 ist und die SQL-Anweisung mindestens eine Parametermarkierung enthält, führt SQLExecute die **SQL-Anweisung** einmal für jeden Satz von Parameterwerten in den Arrays aus, auf die * \*das ParameterValuePtr-Argument* in den Aufrufen von **SQLBindParameter**zeigt. Weitere Informationen finden Sie unter [Arrays von Parameterwerten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Wenn Lesezeichen aktiviert sind und eine Abfrage ausgeführt wird, die keine Lesezeichen unterstützen kann, sollte der Treiber versuchen, die Umgebung zu einer Umgebung zu erführen, die Lesezeichen unterstützt, indem sie einen Attributwert ändert und SQLSTATE 01S02 zurückgibt (Optionswert geändert). Wenn das Attribut nicht geändert werden kann, sollte der Treiber SQLSTATE HY024 (Ungültiger Attributwert) zurückgeben.  
  
> [!NOTE]  
>  Bei der Verwendung des Verbindungspoolings darf eine Anwendung keine SQL-Anweisungen ausführen, **USE** die die Datenbank oder den Kontext der Datenbank ändern, z. B. die _USE-Datenbankanweisung_ in SQL Server, die den von einer Datenquelle verwendeten Katalog ändert.  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)und [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Schließen des Cursors|[SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Ausführen eines Commit- oder Rollbackvorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Abrufen mehrerer Datenzeilen|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Befreien eines Anweisungshandles|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
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
