---
title: SQLSetConnectAttr-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectAttr
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC]
ms.assetid: 97fc7445-5a66-4eb9-8e77-10990b5fd685
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8424462ddde4f99196e26d633fddfa5bb2ed6ee9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301936"
---
# <a name="sqlsetconnectattr-function"></a>SQLSetConnectAttr-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetConnectAttr** legt Attribute fest, die Aspekte von Verbindungen steuern.  
  
> [!NOTE]
>  Weitere Informationen darüber, was der Treiber-Manager dieser Funktion zuordnet, wenn eine ODBC 3 *.x-Anwendung* mit einem ODBC 2 *.x-Treiber* arbeitet, finden Sie unter [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetConnectAttr(  
     SQLHDBC       ConnectionHandle,  
     SQLINTEGER    Attribute,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    StringLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *Attribut*  
 [Eingabe] Zu setzendes Attribut, aufgeführt in "Kommentare".  
  
 *ValuePtr*  
 [Eingabe] Zeiger auf den Wert, der *Attribute*zugeordnet werden soll. Abhängig vom Wert von *Attribut*ist *ValuePtr* ein ganzzahliger Wert ohne Vorzeichen oder auf eine null-terminierte Zeichenfolge. Beachten Sie, dass der integrale Typ des *Attributarguments* möglicherweise keine feste Länge hat, siehe Abschnitt Kommentare für Details.  
  
 *StringLength*  
 [Eingabe] Wenn *Attribute* ein ODBC-definiertes Attribut ist und *ValuePtr* auf eine Zeichenfolge oder einen Binärpuffer verweist, sollte dieses Argument die Länge von **ValuePtr*sein. Bei Zeichenfolgendaten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *Attribute* ein ODBC-definiertes Attribut und *ValuePtr* eine ganze Zahl ist, wird *StringLength* ignoriert.  
  
 Wenn *Attribute* ein treiberdefiniertes Attribut ist, gibt die Anwendung die Art des Attributs für den Treiber-Manager an, indem das *StringLength-Argument* festgelegt wird. *StringLength* kann die folgenden Werte haben:  
  
-   Wenn *ValuePtr* ein Zeiger auf eine Zeichenfolge ist, ist *StringLength* die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen Binärpuffer ist, platziert die Anwendung das Ergebnis des*SQL_LEN_BINARY_ATTR(Länge*) Makros in *StringLength*. Dadurch wird ein negativer Wert in *StringLength*platziert.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine Binärzeichenfolge ist, sollte *StringLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn *ValuePtr* einen Wert mit fester Länge enthält, ist *StringLength* entweder SQL_IS_INTEGER oder SQL_IS_UINTEGER.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetConnectAttr** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DBC und einem *Handle* von *ConnectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLSetConnectAttr** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
 Der Treiber kann SQL_SUCCESS_WITH_INFO zurückgeben, um Informationen über das Ergebnis einer Option bereitzustellen.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber unterstützte den in *ValuePtr* angegebenen Wert nicht und ersetzte einen ähnlichen Wert. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08002|Verbindungsname wird verwendet|Das *Attributargument* wurde SQL_ATTR_ODBC_CURSORS, und der Treiber war bereits mit der Datenquelle verbunden.|  
|08003|Verbindung nicht geöffnet|(DM) Es wurde ein *Attributwert* angegeben, der eine offene Verbindung erforderte, aber das *ConnectionHandle* war nicht in einem verbundenen Zustand.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|24.000|Ungültiger Cursorstatus|Das *Attributargument* wurde SQL_ATTR_CURRENT_CATALOG, und ein Resultset war ausstehend.|  
|25000|Unzulässiger Vorgang in einer lokalen Transaktion|Eine Verbindung befand sich in einer lokalen Transaktion, während versucht wurde, sich in eine verteilte Transaktionsverbindung (DTC) einzutragen, indem das Verbindungsattribut SQL_ATTR_ENLIST_IN_DTC.<br /><br /> Eine Verbindung ist bereits in einem DTC eingetragen.<br /><br /> Eine Verbindung wurde in einer verteilten Transaktionsverbindung eingetragen, und eine lokale Transaktion wurde gestartet, indem SQL_ATTR_AUTOCOMMIT auf SQL_AUTOCOMMIT_OFF eingestellt wurde.|  
|3D000|Ungültiger Katalogname|Das *Attributargument* wurde SQL_CURRENT_CATALOG, und der angegebene Katalogname war ungültig.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *den ConnectionHandle*aktiviert. Die **SQLSetConnectAttr-Funktion** wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde die [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) für *den ConnectionHandle*aufgerufen, und dann wurde die **SQLSetConnectAttr-Funktion** erneut auf dem *ConnectionHandle*aufgerufen.<br /><br /> Oder die **SQLSetConnectAttr-Funktion** wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancelHandle** für das *ConnectionHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das *Attributargument* identifizierte ein Verbindungsattribut, das einen Zeichenfolgenwert erforderte, und das *ValuePtr-Argument* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Eine asynchron ausführende Funktion wurde für einen *StatementHandle* aufgerufen, der dem *ConnectionHandle* zugeordnet war, und wurde immer noch ausgeführt, als **SQLSetConnectAttr** aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausführende Funktion (nicht diese) wurde für den *ConnectionHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungshandles aufgerufen, die dem *ConnectionHandle* zugeordnet sind, und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für ein *StatementHandle* aufgerufen, das dem *ConnectionHandle* zugeordnet ist, und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) **SQLBrowseConnect** wurde für den *ConnectionHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor **SQLBrowseConnect** SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgegeben wurde.|  
|HY011|Attribut kann jetzt nicht festgelegt werden|Das *Attributargument* wurde SQL_ATTR_TXN_ISOLATION, und eine Transaktion war geöffnet.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY024|Ungültiger Attributwert|Angesichts des angegebenen *Attributwerts* wurde in *ValuePtr*ein ungültiger Wert angegeben. (Der Treiber-Manager gibt diese SQLSTATE nur für Verbindungs- und Anweisungsattribute zurück, die einen diskreten Satz von Werten akzeptieren, z. B. SQL_ATTR_ACCESS_MODE oder SQL_ATTR_ASYNC_ENABLE. Für alle anderen Verbindungs- und Anweisungsattribute muss der Treiber den in *ValuePtr*angegebenen Wert überprüfen.)<br /><br /> Das *Attributargument* wurde SQL_ATTR_TRACEFILE oder SQL_ATTR_TRANSLATE_LIB, und *ValuePtr* war eine leere Zeichenfolge.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|*(DM) \*ValuePtr* ist eine Zeichenfolge, und das *StringLength-Argument* war kleiner als 0, wurde aber nicht SQL_NTS.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) Der für das Argument *Attribut* angegebene Wert war für die vom Treiber unterstützte ODBC-Version ungültig.<br /><br /> (DM) Der für das Argument *Attribut* angegebene Wert war ein schreibgeschütztes Attribut.|  
|HY114|Treiber unterstützt keine asynchrone Funktionsausführung auf Verbindungsebene|(DM) Eine Anwendung hat versucht, die asynchrone Funktionsausführung mit SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE für einen Treiber zu aktivieren, der keine asynchronen Verbindungsvorgänge unterstützt.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HY121|Cursorbibliothek und Treiber-Aware-Pooling können nicht gleichzeitig aktiviert werden|Weitere Informationen finden Sie unter [Treiber-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der für das Argument *Attribut* angegebene Wert war eine gültige ODBC-Verbindung oder ein gültiges Anweisungsattribut für die vom Treiber unterstützte ODBC-Version, wurde jedoch vom Treiber nicht unterstützt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *ConnectionHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM009|Übersetzungs-DLL kann nicht geladen werden|Der Treiber konnte die für die Verbindung angegebene Übersetzungs-DLL nicht laden. Dieser Fehler kann nur zurückgegeben werden, wenn *Attribut* SQL_ATTR_TRANSLATE_LIB ist.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
|S1118|Treiber unterstützt keine asynchrone Benachrichtigung|SQL_ATTR_ASYNC_DBC_EVENT wurde festgelegt (nachdem die Verbindung hergestellt wurde), aber die asynchrone Benachrichtigung wird vom Treiber nicht unterstützt.|  
  
 Wenn *Attribute* ein Anweisungsattribut ist, kann **SQLSetConnectAttr** alle SQLSTATEs zurückgeben, die von **SQLSetStmtAttr**zurückgegeben werden.  
  
## <a name="comments"></a>Kommentare  
 Allgemeine Informationen zu Verbindungsattributen finden Sie unter [Verbindungsattribute](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Die aktuell definierten Attribute und die Version von ODBC, in der sie eingeführt wurden, werden in der Tabelle weiter unten in diesem Abschnitt angezeigt. Es wird erwartet, dass mehr Attribute definiert werden, um verschiedene Datenquellen zu nutzen. Ein Bereich von Attributen wird von ODBC reserviert. Treiberentwickler müssen Werte für ihre eigene treiberspezifische Verwendung von Open Group reservieren.  
  
> [!NOTE]
>  Die Möglichkeit, Anweisungsattribute auf Verbindungsebene durch Aufrufen von **SQLSetConnectAttr** festzulegen, ist in ODBC 3 *.x*veraltet. ODBC 3 *.x-Anwendungen* sollten niemals Anweisungsattribute auf Verbindungsebene festlegen. ODBC *.x* 3 .x-Anweisungsattribute können nicht auf Verbindungsebene festgelegt werden, mit Ausnahme der attribute SQL_ATTR_METADATA_ID und SQL_ATTR_ASYNC_ENABLE, die sowohl Verbindungsattribute als auch Anweisungsattribute sind und entweder auf Verbindungsebene oder auf Anweisungsebene festgelegt werden können.  
> 
>  ODBC 3 *.x-Treiber* müssen diese Funktionalität nur unterstützen, wenn sie mit ODBC 2 *.x-Anwendungen* arbeiten sollten, die ODBC 2 *.x-Anweisungsoptionen* auf Verbindungsebene festlegen. Weitere Informationen finden Sie unter [SQLSetConnectOption Mapping](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.  
  
 Eine Anwendung kann **SQLSetConnectAttr** jederzeit aufrufen, wenn die Verbindung zugewiesen und freigegeben wird. Alle Verbindungs- und Anweisungsattribute, die von der Anwendung erfolgreich für die Verbindung festgelegt wurden, bleiben bestehen, bis **SQLFreeHandle** für die Verbindung aufgerufen wird. Wenn eine Anwendung beispielsweise **SQLSetConnectAttr** aufruft, bevor eine Verbindung mit einer Datenquelle hergestellt wird, bleibt das Attribut auch dann erhalten, wenn **SQLSetConnectAttr** im Treiber fehlschlägt, wenn die Anwendung eine Verbindung mit der Datenquelle herstellt. Wenn eine Anwendung ein treiberspezifisches Attribut festlegt, bleibt das Attribut auch dann erhalten, wenn die Anwendung eine Verbindung mit einem anderen Treiber in der Verbindung herstellt.  
  
 Einige Verbindungsattribute können nur festgelegt werden, bevor eine Verbindung hergestellt wurde. andere können erst eingestellt werden, nachdem eine Verbindung hergestellt wurde. Die folgende Tabelle gibt die Verbindungsattribute an, die vor oder nach dem Herstellen einer Verbindung festgelegt werden müssen. *Entweder* gibt an, dass das Attribut entweder vor oder nach der Verbindung festgelegt werden kann.  
  
|Attribut|Vor oder nach der Verbindung einstellen?|  
|---------------|-------------------------------------|  
|SQL_ATTR_ACCESS_MODE|Entweder[1]|  
|SQL_ATTR_ASYNC_DBC_EVENT|Sowohl als auch|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE|Entweder[4]|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK|Sowohl als auch|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT|Sowohl als auch|  
|SQL_ATTR_ASYNC_ENABLE|Entweder[2]|  
|SQL_ATTR_AUTO_IPD|Sowohl als auch|  
|SQL_ATTR_AUTOCOMMIT|Entweder[5]|  
|SQL_ATTR_CONNECTION_DEAD|Nach|  
|SQL_ATTR_CONNECTION_TIMEOUT|Sowohl als auch|  
|SQL_ATTR_CURRENT_CATALOG|Entweder[1]|  
|SQL_ATTR_DBC_INFO_TOKEN|Nach|  
|SQL_ATTR_ENLIST_IN_DTC|Nach|  
|SQL_ATTR_LOGIN_TIMEOUT|vor|  
|SQL_ATTR_METADATA_ID|Sowohl als auch|  
|SQL_ATTR_ODBC_CURSORS|vor|  
|SQL_ATTR_PACKET_SIZE|vor|  
|SQL_ATTR_QUIET_MODE|Sowohl als auch|  
|SQL_ATTR_TRACE|Sowohl als auch|  
|SQL_ATTR_TRACEFILE|Sowohl als auch|  
|SQL_ATTR_TRANSLATE_LIB|Nach|  
|SQL_ATTR_TRANSLATE_OPTION|Nach|  
|SQL_ATTR_TXN_ISOLATION|Entweder[3]|  
  
 [1] SQL_ATTR_ACCESS_MODE und SQL_ATTR_CURRENT_CATALOG können vor oder nach dem Anschluss eingestellt werden, je nach Treiber. Interoperable Anwendungen legen sie jedoch vor dem Herstellen einer Verbindung fest, da einige Treiber das Ändern dieser Anwendungen nach dem Herstellen einer Verbindung nicht unterstützen.  
  
 [2] SQL_ATTR_ASYNC_ENABLE muss festgelegt werden, bevor eine aktive Anweisung vorhanden ist.  
  
 [3] SQL_ATTR_TXN_ISOLATION kann nur eingestellt werden, wenn keine offenen Transaktionen in der Verbindung vorhanden sind. Einige Verbindungsattribute unterstützen die Ersetzung eines ähnlichen Werts, wenn \*die Datenquelle den in *ValuePtr*angegebenen Wert nicht unterstützt. In solchen Fällen gibt der Treiber SQL_SUCCESS_WITH_INFO und SQLSTATE 01S02 zurück (Optionswert geändert). Wenn *Attribut* beispielsweise SQL_ATTR_PACKET_SIZE \*ist und *ValuePtr* die maximale Paketgröße überschreitet, ersetzt der Treiber die maximale Größe. Um den ersetzten Wert zu bestimmen, ruft eine Anwendung **SQLGetConnectAttr**auf.  
  
 [4] Wenn SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE festgelegt ist, bevor eine Verbindung geöffnet ist, legt der Treiber-Manager das Attribut des Treibers fest, wenn der Treiber während eines Aufrufs von **SQLBrowseConnect**, **SQLConnect**oder **SQLDriverConnect**geladen wird. Vor einem Aufruf von **SQLBrowseConnect**, **SQLConnect**oder **SQLDriverConnect**weiß der Treiber-Manager nicht, mit welchem Treiber eine Verbindung hergestellt werden soll, und weiß nicht, ob der Treiber asynchrone Verbindungsvorgänge unterstützt. Daher gibt der Treiber-Manager immer SQL_SUCCESS zurück. Falls der Treiber jedoch keine asynchronen Verbindungsvorgänge unterstützt, schlägt der Aufruf von **SQLBrowseConnect**, **SQLConnect**oder **SQLDriverConnect** fehl.  
  
 [5] Wenn SQL_ATTR_AUTOCOMMIT auf FALSE festgelegt ist, sollten Anwendungen SQLEndTran(SQL_ROLLBACK) aufrufen, wenn eine API SQL_ERROR zurückgibt, um die Transaktionskonsistenz sicherzustellen.  
  
 Das Format der im \* *ValuePtr-Puffer* festgelegten Informationen hängt vom angegebenen *Attribut*ab. **SQLSetConnectAttr** akzeptiert Attributinformationen in einem von zwei verschiedenen Formaten: einer null-terminierten Zeichenfolge oder einem Ganzzahlwert. Das Format der einzelnen Attribute wird in der Beschreibung des Attributs angegeben. Zeichenzeichenfolgen, auf die das *ValuePtr-Argument* von **SQLSetConnectAttr** zeigt, haben eine Länge von *StringLength-Bytes.*  
  
 Das *StringLength-Argument* wird ignoriert, wenn die Länge durch das Attribut definiert wird, wie dies bei allen Attributen der Fall ist, die in ODBC 2 *.x* oder früher eingeführt wurden.  
  
|*Attribut*|*ValuePtr-Inhalt*|  
|-----------------|-------------------------|  
|SQL_ATTR_ACCESS_MODE (ODBC 1.0)|Ein SQLUINTEGER-Wert. SQL_MODE_READ_ONLY wird vom Treiber oder der Datenquelle als Indikator dafür verwendet, dass die Verbindung nicht erforderlich ist, um SQL-Anweisungen zu unterstützen, die Aktualisierungen verursachen. Dieser Modus kann verwendet werden, um Sperrstrategien, Transaktionsverwaltung oder andere Bereiche entsprechend dem Treiber oder der Datenquelle zu optimieren. Der Treiber ist nicht erforderlich, um zu verhindern, dass solche Anweisungen an die Datenquelle übermittelt werden. Das Verhalten des Treibers und der Datenquelle, wenn sie aufgefordert werden, SQL-Anweisungen zu verarbeiten, die während einer schreibgeschützten Verbindung nicht schreibgeschützt sind, ist implementierungsdefiniert. SQL_MODE_READ_WRITE ist die Standardeinstellung.|  
|SQL_ATTR_ASYNC_DBC_EVENT (ODBC 3.8)|Ein SQLPOINTER-Wert, der ein Ereignishandle ist.<br /><br /> Die Benachrichtigung über den Abschluss asynchroner Funktionen wird durch Aufrufen von **SQLSetConnectAttr** mit dem Attribut SQL_ATTR_ASYNC_STMT_EVENT und Angeben des Ereignishandles aktiviert. **Hinweis:**  Die Benachrichtigungsmethode wird mit der Cursorbibliothek nicht unterstützt. Eine Anwendung erhält eine Fehlermeldung, wenn sie versucht, die Cursorbibliothek über SQLSetConnectAttr zu aktivieren, wenn die Benachrichtigungsmethode aktiviert ist.|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE (ODBC 3.8)|Ein SQLUINTEGER-Wert, der die asynchrone Ausführung ausgewählter Funktionen im Verbindungshandle aktiviert oder deaktiviert. Weitere Informationen finden Sie unter [Asynchrone Ausführung (Polling-Methode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).<br /><br /> SQL_ASYNC_DBC_ENABLE_ON = Asynchronen Betrieb für angegebene verbindungsbezogene Funktionen aktivieren.<br /><br /> SQL_ASYNC_DBC_ENABLE_OFF = (Standard) Asynchronen Betrieb für angegebene verbindungsbezogene Funktionen deaktivieren.<br /><br /> Das Festlegen SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE ist immer synchron (d. h., es wird nie SQL_STILL_EXECUTING zurückgegeben).<br /><br /> Die asynchrone Ausführung von Anweisungsvorgängen wird mit SQL_ATTR_ASYNC_ENABLE aktiviert.|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK (ODBC 3.8)|Ein SQLPOINTER-Wert, der auf die Kontextstruktur verweist.<br /><br /> Nur der Treiber-Manager kann die **SQLSetStmtAttr-Funktion** eines Treibers mit diesem Attribut aufrufen.|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT (ODBC 3.8)|Ein SQLPOINTER-Wert, der auf die Kontextstruktur verweist.<br /><br /> Nur der Treiber-Manager kann die **SQLSetStmtAttr-Funktion** eines Treibers mit diesem Attribut aufrufen.|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 3.0)|Ein SQLULEN-Wert, der angibt, ob eine Funktion, die mit einer Anweisung für die angegebene Verbindung aufgerufen wird, asynchron ausgeführt wird:<br /><br /> SQL_ASYNC_ENABLE_OFF = Asynchrone Ausführungsunterstützung für Anweisungsvorgänge auf Verbindungsebene deaktivieren (Standard).<br /><br /> SQL_ASYNC_ENABLE_ON = Aktivieren der asynchronen Ausführungsunterstützung für Anweisungsvorgänge auf Verbindungsebene.<br /><br /> Dieses Attribut kann festgelegt werden, ob **SQLGetInfo** mit dem SQL_ASYNC_MODE-Informationstyp SQL_AM_CONNECTION oder SQL_AM_STATEMENT zurückgibt.|  
|SQL_ATTR_AUTO_IPD (ODBC 3.0)|Ein schreibgeschützter SQLUINTEGER-Wert, der angibt, ob die automatische Auffüllung der IPD nach einem Aufruf von **SQLPrepare** unterstützt wird:<br /><br /> SQL_TRUE = Automatische Auffüllung der IPD nach einem Aufruf von **SQLPrepare** wird vom Treiber unterstützt.<br /><br /> SQL_FALSE = Die automatische Auffüllung der IPD nach einem Aufruf von **SQLPrepare** wird vom Treiber nicht unterstützt. Server, die keine vorbereiteten Anweisungen unterstützen, können die IPD nicht automatisch auffüllen.<br /><br /> Wenn SQL_TRUE für das SQL_ATTR_AUTO_IPD-Verbindungsattribut zurückgegeben wird, kann das Anweisungsattribut SQL_ATTR_ENABLE_AUTO_IPD so eingestellt werden, dass die automatische Auffüllung der IPD aktiviert oder deaktiviert wird. Wenn SQL_ATTR_AUTO_IPD SQL_FALSE ist, kann SQL_ATTR_ENABLE_AUTO_IPD nicht auf SQL_TRUE festgelegt werden. Der Standardwert von SQL_ATTR_ENABLE_AUTO_IPD entspricht dem Wert von SQL_ATTR_AUTO_IPD.<br /><br /> Dieses Verbindungsattribut kann von **SQLGetConnectAttr** zurückgegeben werden, kann aber nicht von **SQLSetConnectAttr**festgelegt werden.|  
|SQL_ATTR_AUTOCOMMIT (ODBC 1.0)|Ein SQLUINTEGER-Wert, der angibt, ob der Autocommit- oder der manuelle Commit-Modus verwendet werden soll:<br /><br /> SQL_AUTOCOMMIT_OFF = Der Treiber verwendet den manuellen Commit-Modus, und die Anwendung muss explizit Transaktionen mit **SQLEndTran**festschreiben oder zurücksetzen.<br /><br /> SQL_AUTOCOMMIT_ON = Der Treiber verwendet den Autocommit-Modus. Jede Anweisung wird sofort nach der Ausführung festgeschrieben. Dies ist die Standardoption. Alle offenen Transaktionen in der Verbindung werden festgeschrieben, wenn SQL_ATTR_AUTOCOMMIT auf SQL_AUTOCOMMIT_ON festgelegt ist, um vom manuellen Commit-Modus in den Autocommit-Modus zu wechseln.<br /><br /> Weitere Informationen finden Sie unter [Commit-Modus](../../../odbc/reference/develop-app/commit-mode.md). **Wichtig:**  Einige Datenquellen löschen die Zugriffspläne und schließen die Cursor für alle Anweisungen für eine Verbindung, wenn eine Anweisung festgeschrieben wird. Der Autocommit-Modus kann dazu führen, dass dies geschieht, nachdem jede Nichtabfrageanweisung ausgeführt wird oder wenn der Cursor für eine Abfrage geschlossen wird. Weitere Informationen finden Sie unter SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Informationstypen in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md). <br /><br /> Wenn ein Batch im Autocommit-Modus ausgeführt wird, sind zwei Dinge möglich. Die gesamte Charge kann als autocommitable Einheit behandelt werden, oder jede Anweisung in einer Charge wird als autocommitable Unit behandelt. Bestimmte Datenquellen können beide Verhaltensweisen unterstützen und eine Möglichkeit bieten, das eine oder andere zu wählen. Es wird definiert, ob ein Batch als autocommitable Unit behandelt wird oder ob jede einzelne Anweisung innerhalb des Stapels autocommitable ist.|  
|SQL_ATTR_CONNECTION_DEAD<br /><br /> (ODBC 3.5)|Ein schreibgeschützter SQLUINTEGER-Wert, der den Status der Verbindung angibt. Wenn SQL_CD_TRUE, ist die Verbindung verloren gegangen. Wenn SQL_CD_FALSE, ist die Verbindung weiterhin aktiv.|  
|SQL_ATTR_CONNECTION_TIMEOUT (ODBC 3.0)|Ein SQLUINTEGER-Wert, der der Anzahl der Sekunden entspricht, die gewartet werden müssen, bis eine Anforderung für die Verbindung abgeschlossen ist, bevor sie zur Anwendung zurückkehrt. Der Treiber sollte SQLSTATE HYT00 (Timeout abgelaufen) jederzeit zurückgeben, wenn es möglich ist, in einer Situation, die nicht mit abfrageausführung oder -anmeldung verbunden ist, eine Zeitnachweise zu verursachen.<br /><br /> Wenn *ValuePtr* gleich 0 ist (Standardeinstellung), gibt es kein Timeout.|  
|SQL_ATTR_CURRENT_CATALOG (ODBC 2.0)|Eine Zeichenfolge, die den Namen des Katalogs enthält, der von der Datenquelle verwendet werden soll. In SQL Server ist der Katalog beispielsweise eine Datenbank, sodass der Treiber eine *database* \* **USE** _USE-Datenbankanweisung_ an die Datenquelle sendet, wobei die Datenbank die in *ValuePtr*angegebene Datenbank ist. Bei einem Ein-Ebenen-Treiber kann es sich bei dem Katalog um ein Verzeichnis ergehen lassen, sodass der Treiber sein aktuelles Verzeichnis in das in **ValuePtr*angegebene Verzeichnis ändert.|  
|SQL_ATTR_DBC_INFO_TOKEN (ODBC 3.8|Ein SQLPOINTER-Wert, der verwendet wird, um das Verbindungsinfotoken in das DBC-Handle zurücksetzen, wenn der [SQLRateConnection-Parameter](../../../odbc/reference/syntax/sqlrateconnection-function.md)\**(pRating*) nicht gleich 100 ist.<br /><br /> SQL_ATTR_DBC_INFO_TOKEN ist nur festgelegt. Es ist nicht möglich, **SQLGetConnectAttr** oder **SQLGetConnectOption** zum Abrufen dieses Werts zu verwenden. **SQLSetConnectAttr** des Treiber-Managers akzeptiert SQL_ATTR_DBC_INFO_TOKEN nicht, da eine Anwendung dieses Attribut nicht festlegen sollte.<br /><br /> Wenn ein Treiber nach dem Festlegen SQL_ATTR_DBC_INFO_TOKEN SQL_ERROR zurückgibt, wird die gerade aus dem Pool erhaltene Verbindung freigegeben. Der Treiber-Manager versucht dann, eine weitere Verbindung aus dem Pool zu erhalten. Weitere Informationen finden Sie unter [Entwickeln der Verbindungspool-Bewusstseinskenntnis in einem ODBC-Treiber.](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)|  
|SQL_ATTR_ENLIST_IN_DTC (ODBC 3.0)|Ein SQLPOINTER-Wert, der angibt, ob der ODBC-Treiber in verteilten Transaktionen verwendet werden soll, die von Microsoft Component Services koordiniert werden.<br /><br /> Übergeben Sie ein DTC-OLE-Transaktionsobjekt, das die Transaktion angibt, die in SQL Server exportiert werden soll, oder SQL_DTC_DONE, um die DTC-Zuordnung der Verbindung zu beenden.<br /><br /> Der Client ruft die Microsoft Distributed Transaction Coordinator (MS DTC) OLE ITransactionDispenser::BeginTransaction-Methode auf, um eine MS DTC-Transaktion zu starten und ein MS DTC-Transaktionsobjekt zu erstellen, das die Transaktion darstellt. Die Anwendung ruft dann SQLSetConnectAttr mit der Option SQL_ATTR_ENLIST_IN_DTC auf, um das Transaktionsobjekt der ODBC-Verbindung zuzuordnen. Alle entsprechenden Datenbankaktivitäten werden unter dem Schutz der MS DTC-Transaktion durchgeführt. Die Anwendung ruft SQLSetConnectAttr mit SQL_DTC_DONE auf, um die DTC-Zuordnung der Verbindung zu beenden. Weitere Informationen finden Sie in der MS DTC-Dokumentation.|  
|SQL_ATTR_LOGIN_TIMEOUT (ODBC 1.0)|Ein SQLUINTEGER-Wert, der der Anzahl der Sekunden entspricht, die auf den Abschluss einer Anmeldeanforderung gewartet werden sollen, bevor zur Anwendung zurückgegeben wird. Der Standardwert ist treiberabhängig. Wenn *ValuePtr* 0 ist, ist das Timeout deaktiviert, und ein Verbindungsversuch wartet auf unbestimmte Zeit.<br /><br /> Wenn das angegebene Timeout das maximale Anmeldetimeout in der Datenquelle überschreitet, ersetzt der Treiber diesen Wert und gibt SQLSTATE 01S02 zurück (Optionswert geändert).|  
|SQL_ATTR_METADATA_ID (ODBC 3.0)|Ein SQLUINTEGER-Wert, der bestimmt, wie die Zeichenfolgenargumente von Katalogfunktionen behandelt werden.<br /><br /> Wenn SQL_TRUE, wird das Zeichenfolgenargument von Katalogfunktionen als Bezeichner behandelt. Der Fall ist nicht von Bedeutung. Bei nicht getrennten Zeichenfolgen entfernt der Treiber alle nachgestellten Leerzeichen, und die Zeichenfolge wird in Großbuchstaben gefaltet. Bei abgegrenzten Zeichenfolgen entfernt der Treiber alle führenden oder nachfolgenden Leerzeichen und nimmt buchstäblich alles, was zwischen den Trennzeichen ist. Wenn eines dieser Argumente auf einen Nullzeiger festgelegt ist, gibt die Funktion SQL_ERROR und SQLSTATE HY009 (Ungültige Verwendung von NULL-Zeiger) zurück.<br /><br /> Wenn SQL_FALSE, werden die Zeichenfolgenargumente von Katalogfunktionen nicht als Bezeichner behandelt. Der Fall ist von Bedeutung. Sie können je nach Argument entweder ein Zeichenfolgensuchmuster enthalten oder nicht.<br /><br /> Der Standardwert ist SQL_FALSE.<br /><br /> Das *TableType-Argument* von **SQLTables**, das eine Liste von Werten enthält, ist von diesem Attribut nicht betroffen.<br /><br /> SQL_ATTR_METADATA_ID kann auch auf Anweisungsebene festgelegt werden. (Es ist das einzige Verbindungsattribut, das auch ein Anweisungsattribut ist.)<br /><br /> Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).|  
|SQL_ATTR_ODBC_CURSORS (ODBC 2.0)|Ein SQLULEN-Wert, der angibt, wie der Treiber-Manager die ODBC-Cursorbibliothek verwendet:<br /><br /> SQL_CUR_USE_IF_NEEDED = Der Treiber-Manager verwendet die ODBC-Cursorbibliothek nur, wenn sie benötigt wird. Wenn der Treiber die SQL_FETCH_PRIOR Option in **SQLFetchScroll**unterstützt, verwendet der Treiber-Manager die Bildlauffunktionen des Treibers. Andernfalls wird die ODBC-Cursorbibliothek verwendet.<br /><br /> SQL_CUR_USE_ODBC = Der Treiber-Manager verwendet die ODBC-Cursorbibliothek.<br /><br /> SQL_CUR_USE_DRIVER = Der Treiber-Manager verwendet die Bildlauffunktionen des Treibers. Dies ist die Standardeinstellung.<br /><br /> Weitere Informationen zur ODBC-Cursorbibliothek finden Sie in [Anhang F: ODBC Cursor Library](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md). **Warnung:**  Die Cursorbibliothek wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.|  
|SQL_ATTR_PACKET_SIZE (ODBC 2.0)|Ein SQLUINTEGER-Wert, der die Netzwerkpaketgröße in Bytes angibt. **Hinweis:**  Viele Datenquellen unterstützen diese Option entweder nicht oder können nur die Netzwerkpaketgröße zurückgeben, aber nicht festlegen. <br /><br /> Wenn die angegebene Größe die maximale Paketgröße überschreitet oder kleiner als die minimale Paketgröße ist, ersetzt der Treiber diesen Wert und gibt SQLSTATE 01S02 zurück (Optionswert geändert).<br /><br /> Wenn die Anwendung die Paketgröße festlegt, nachdem eine Verbindung bereits hergestellt wurde, gibt der Treiber SQLSTATE HY011 zurück (Attribut kann jetzt nicht festgelegt werden).|  
|SQL_ATTR_QUIET_MODE (ODBC 2.0)|Ein Fenstergriff (HWND).<br /><br /> Wenn das Fensterhandle ein Nullzeiger ist, zeigt der Treiber keine Dialogfelder an.<br /><br /> Wenn das Fensterhandle kein Nullzeiger ist, sollte es das übergeordnete Fensterhandle der Anwendung sein. Dies ist die Standardoption. Der Treiber verwendet dieses Handle, um Dialogfelder anzuzeigen. **Hinweis:**  Das SQL_ATTR_QUIET_MODE Verbindungsattribut gilt nicht für Dialogfelder, die von **SQLDriverConnect**angezeigt werden.|  
|SQL_ATTR_TRACE (ODBC 1.0)|Ein SQLUINTEGER-Wert, der dem Treiber-Manager mitteilt, ob die Ablaufverfolgung ausgeführt werden soll:<br /><br /> SQL_OPT_TRACE_OFF = Ablaufverfolgung deaktiviert (Standard)<br /><br /> SQL_OPT_TRACE_ON = Ablaufverfolgung auf<br /><br /> Wenn die Ablaufverfolgung eingeschaltet ist, schreibt der Treiber-Manager jeden ODBC-Funktionsaufruf in die Ablaufverfolgungsdatei. **Hinweis:**  Wenn die Ablaufverfolgung aktiv ist, kann der Treiber-Manager SQLSTATE IM013 (Trace-Dateifehler) von jeder Funktion zurückgeben. <br /><br /> Eine Anwendung gibt eine Ablaufverfolgungsdatei mit der Option SQL_ATTR_TRACEFILE an. Wenn die Datei bereits vorhanden ist, fügt der Treiber-Manager an die Datei an. Andernfalls wird die Datei erstellt. Wenn die Ablaufverfolgung aktiv ist und keine Ablaufverfolgungsdatei angegeben wurde, schreibt der Treiber-Manager in die Datei SQL. LOG im Stammverzeichnis.<br /><br /> Eine Anwendung kann die Variable **ODBCSharedTraceFlag** so einstellen, dass die Ablaufverfolgung dynamisch aktiviert wird. Die Ablaufverfolgung ist dann für alle derzeit ausgeführten ODBC-Anwendungen aktiviert. Wenn eine Anwendung die Ablaufverfolgung deaktiviert, wird sie nur für diese Anwendung deaktiviert.<br /><br /> Wenn **Trace** das Trace-Schlüsselwort in den Systeminformationen auf 1 festgelegt ist, wenn eine Anwendung **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV aufruft, ist die Ablaufverfolgung für alle Handles aktiviert. Sie ist nur für die Anwendung aktiviert, die **SQLAllocHandle**aufgerufen hat.<br /><br /> Das Aufrufen von **SQLSetConnectAttr** mit einem *Attribut* von SQL_ATTR_TRACE erfordert nicht, dass das *ConnectionHandle-Argument* gültig ist, und gibt SQL_ERROR nicht zurück, wenn *ConnectionHandle* NULL ist. Dieses Attribut gilt für alle Verbindungen.|  
|SQL_ATTR_TRACEFILE (ODBC 1.0)|Eine null-terminierte Zeichenfolge, die den Namen der Ablaufverfolgungsdatei enthält.<br /><br /> Der Standardwert des SQL_ATTR_TRACEFILE-Attributs wird mit dem **TraceFile-Schlüsselwort** in den Systeminformationen angegeben. Weitere Informationen finden Sie unter [ODBC Subkey](../../../odbc/reference/install/odbc-subkey.md).<br /><br /> Das Aufrufen von **SQLSetConnectAttr** mit einem *Attribut* von SQL_ATTR_ TRACEFILE erfordert nicht, dass das *ConnectionHandle-Argument* gültig ist, und gibt SQL_ERROR nicht zurück, wenn *ConnectionHandle* ungültig ist. Dieses Attribut gilt für alle Verbindungen.|  
|SQL_ATTR_TRANSLATE_LIB (ODBC 1.0)|Eine null-terminierte Zeichenfolge, die den Namen einer Bibliothek enthält, die die Funktionen **SQLDriverToDataSource** und **SQLDataSourceToDriver** enthält, auf die der Treiber zugreift, um Aufgaben wie die Zeichensatzübersetzung auszuführen. Diese Option kann nur angegeben werden, wenn der Treiber eine Verbindung mit der Datenquelle hergestellt hat. Die Einstellung dieses Attributs bleibt über Verbindungen hinweg erhalten. Weitere Informationen zum Übersetzen von Daten finden Sie unter [Übersetzungs-DLLs](../../../odbc/reference/develop-app/translation-dlls.md) und [Übersetzungs-DLL-Funktionsreferenz](../../../odbc/reference/syntax/translation-dll-api-reference.md).|  
|SQL_ATTR_TRANSLATE_OPTION (ODBC 1.0)|Ein 32-Bit-Flagwert, der an die Übersetzungs-DLL übergeben wird. Dieses Attribut kann nur angegeben werden, wenn der Treiber eine Verbindung mit der Datenquelle hergestellt hat. Informationen zum Übersetzen von Daten finden Sie unter [Übersetzungs-DLLs](../../../odbc/reference/develop-app/translation-dlls.md).|  
|SQL_ATTR_TXN_ISOLATION (ODBC 1.0)|Eine 32-Bit-Bitmaske, die die Transaktionsisolationsstufe für die aktuelle Verbindung festlegt. Eine Anwendung muss **SQLEndTran** aufrufen, um alle geöffneten Transaktionen für eine Verbindung festzuschreiben oder zurückzusetzen, bevor **SQLSetConnectAttr** mit dieser Option aufgerufen wird.<br /><br /> Die gültigen Werte für *ValuePtr* können durch Aufrufen von **SQLGetInfo** mit *InfoType* gleich SQL_TXN_ISOLATION_OPTIONS bestimmt werden.<br /><br /> Eine Beschreibung der Transaktionsisolationsstufen finden Sie in der Beschreibung des SQL_DEFAULT_TXN_ISOLATION Informationstyps in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [Transaction Isolation Levels](../../../odbc/reference/develop-app/transaction-isolation-levels.md).|  
  
 [1] Diese Funktionen können nur dann asynchron aufgerufen werden, wenn der Deskriptor ein Implementierungsdeskriptor und kein Anwendungsdeskriptor ist.  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuweisen eines Griffs|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Zurückgeben der Einstellung eines Verbindungsattributs|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
