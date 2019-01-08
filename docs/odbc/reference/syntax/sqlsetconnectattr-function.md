---
title: SQLSetConnectAttr-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aad8baf55dc8960c533e1694309083952dece3d3
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591244"
---
# <a name="sqlsetconnectattr-function"></a>SQLSetConnectAttr-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standardkompatibilität: ISO-92  
  
 **Zusammenfassung**  
 **SQLSetConnectAttr** legt diese fest, die Aspekte der Verbindungen steuern.  
  
> [!NOTE]
>  Weitere Informationen dazu, was der Treiber-Manager diese Funktion auf, wenn eine ODBC 3. zuordnet *.x* Anwendung arbeitet mit einer ODBC 2.*.x* -Treiber verwenden, finden Sie unter [Zuordnen von Ersatzfunktionen für rückwärts Kompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 [Eingabe] Attribut, das festgelegt wird, aufgeführt in "Kommentare".  
  
 *ValuePtr*  
 [Eingabe] Zeiger auf den Wert zugeordnet werden *Attribut*. Abhängig vom Wert *Attribut*, *ValuePtr* werden ein Ganzzahlwert ohne Vorzeichen oder verweist auf eine Null-terminierte Zeichenfolge. Beachten Sie, die der ganzzahligen Typ, der die *Attribut* Argument kann nicht werden fester Länge, finden Sie im Abschnitt "Kommentare" Details.  
  
 *StringLength*  
 [Eingabe] Wenn *Attribut* ist ein ODBC-definierten Attribut und *ValuePtr* zeigt auf eine Zeichenfolge oder ein binärer Puffer, in dieses Argument muss die Länge des **ValuePtr*. Für Zeichenfolgendaten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *Attribut* ist ein ODBC-definierten Attribut und *ValuePtr* ist eine ganze Zahl, *StringLength* wird ignoriert.  
  
 Wenn *Attribut* ein treiberdefinierten-Attribut, wird die Anwendung zeigt die Art des Attributs auf den Treiber-Manager an, indem die *StringLength* Argument. *StringLength* können die folgenden Werte aufweisen:  
  
-   Wenn *ValuePtr* ist ein Zeiger auf eine Zeichenfolge, *StringLength* ist die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *ValuePtr* ist ein Zeiger auf ein binärer Puffer, aus, und klicken Sie dann die Anwendung das Ergebnis der SQL_LEN_BINARY_ATTR platziert (*Länge*)-Makro in *StringLength*. Dadurch wird einen negativen Wert im platziert *StringLength*.  
  
-   Wenn *ValuePtr* ist ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine binäre Zeichenfolge *StringLength* Wert SQL_IS_POINTER haben sollte.  
  
-   Wenn *ValuePtr* enthält einen Wert fester Länge *StringLength* ist SQL_IS_INTEGER oder SQL_IS_UINTEGER, nach Bedarf.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetConnectAttr** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DBC auf, und eine *behandeln* von *ConnectionHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLSetConnectAttr** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
 Der Treiber kann SQL_SUCCESS_WITH_INFO zum Bereitstellen von Informationen zum Festlegen einer Option Ergebnis zurück.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber nicht den Wert im angegebenen *ValuePtr* und einen ähnlichen Wert ersetzt. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08002|Name der Verbindung verwendet|Die *Attribut* Argument war SQL_ATTR_ODBC_CURSORS und der Treiber wurde bereits mit der Datenquelle verbunden.|  
|08003|Verbindung nicht geöffnet|(DM) eine *Attribut* -Wert wurde angegeben, die eine offene Verbindung erforderlich, aber die *ConnectionHandle* war nicht verbunden.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Die *Attribut* Argument war SQL_ATTR_CURRENT_CATALOG und ein Resultset steht aus.|  
|25000|Unzulässiger Vorgang bei einer lokalen Transaktion|Eine Verbindung wurde in einer lokalen Transaktion, bei dem Versuch, die in einer verteilten transaktionsverbindung (DTC) eintragen, indem das Verbindungsattribut SQL_ATTR_ENLIST_IN_DTC lauten.<br /><br /> Eine Verbindung ist bereits in einem DTC eingetragen.<br /><br /> Eine Verbindung wurde in einer verteilten transaktionsverbindung eingetragen, und eine lokale Transaktion gestartet wurde, indem Sie SQL_ATTR_AUTOCOMMIT auf SQL_AUTOCOMMIT_OFF festlegen.|  
|3D000|Ungültiger Katalogname|Die *Attribut* Argument SQL_CURRENT_CATALOG, und der Name des angegebenen Katalogs war ungültig.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *ConnectionHandle*. Die **SQLSetConnectAttr** Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, die [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) aufgerufen wurde, auf die *ConnectionHandle*, und klicken Sie dann die **SQLSetConnectAttr** Funktion wurde erneut aufgerufen, auf die *ConnectionHandle*.<br /><br /> Or **SQLSetConnectAttr** Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancelHandle** aufgerufen wurde, auf die *ConnectionHandle* von einem anderen Thread in eine multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Die *Attribut* Argument identifiziert ein Verbindungsattribut, die einen Zeichenfolgenwert erforderlich und die *ValuePtr* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, eine *StatementHandle* zugeordneten der *ConnectionHandle* und wurde noch ausgeführt, wenn **SQLSetConnectAttr**aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *ConnectionHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** für eines der zugeordneten Anweisungshandles aufgerufen wurde die *ConnectionHandle* und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, eine *StatementHandle*  zugeordneten der *ConnectionHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) **SQLBrowseConnect** wurde aufgerufen, die *ConnectionHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion aufgerufen wurde, bevor **SQLBrowseConnect** SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgegeben.|  
|HY011|Attribut kann jetzt nicht festgelegt werden|Die *Attribut* Argument war SQL_ATTR_TXN_ISOLATION und eine Transaktion geöffnet wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY024|Ungültiger Attributwert|Berücksichtigung des angegebenen *Attribut* Wert in wurde ein ungültiger Wert angegeben *ValuePtr*. (Der Treiber-Manager gibt SQLSTATE nur für die Verbindung und Anweisungsattribute, die einen diskreten Satz von Werten, z. B. SQL_ATTR_ACCESS_MODE oder SQL_ATTR_ASYNC_ENABLE zu akzeptieren. Für alle anderen Verbindung und Anweisungsattribute, die Treiber muss überprüfen Sie den Wert im angegebenen *ValuePtr*.)<br /><br /> Die *Attribut* Argument war SQL_ATTR_TRACEFILE oder SQL_ATTR_TRANSLATE_LIB, und *ValuePtr* wurde eine leere Zeichenfolge.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|*(DM) \*ValuePtr* ist eine Zeichenfolge, und die *StringLength* Argument war kleiner als 0, aber nicht SQL_NTS.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) der Wert für das Argument angegebene *Attribut* war nicht gültig für die Version von ODBC, die vom Treiber unterstützt werden.<br /><br /> (DM) der Wert für das Argument angegebene *Attribut* wurde eine nur-Lese Attribut.|  
|HY114|Auf Serverebene asynchrone Ausführung der unterstützt Treiber nicht.|(DM) versucht eine Anwendung, die asynchrone Ausführung mit SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE für einen Treiber zu aktivieren, die asynchrone Verbindungsvorgänge nicht unterstützt.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum Zustand "angehalten" [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HY121|Cursor-Bibliothek und Treiberfähiges Verbindungspooling können nicht gleichzeitig aktiviert werden|Weitere Informationen finden Sie unter [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|HYC00|Optionales Feature nicht implementiert.|Der angegebene Wert für das Argument *Attribut* wurde eine ODBC-Verbindung oder für die Version des ODBC-Anweisungsattribut vom Treiber unterstützt werden, jedoch wurde vom Treiber nicht unterstützt.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *ConnectionHandle* die Funktion nicht unterstützt.|  
|IM009|Kann nicht geladen werden Konvertierungs-DLL|Der Treiber konnte den Konvertierungs-DLL zu laden, die für die Verbindung angegeben wurde. Dieser Fehler kann zurückgegeben, wenn Sie nur, wenn *Attribut* SQL_ATTR_TRANSLATE_LIB wird.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
|S1118|Asynchrone Benachrichtigung unterstützt Treiber nicht.|SQL_ATTR_ASYNC_DBC_EVENT (nachdem die Verbindung hergestellt wurde) festgelegt wurde, aber die asynchrone Benachrichtigung wird vom Treiber nicht unterstützt.|  
  
 Wenn *Attribut* ist ein Anweisungsattribut **SQLSetConnectAttr** können alle SQLSTATEs zurückgegebenes zurückgeben **SQLSetStmtAttr**.  
  
## <a name="comments"></a>Kommentare  
 Allgemeine Informationen zu Verbindungsattributen finden Sie unter [Verbindungsattribute](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Die aktuell definierten Attribute und die Version von ODBC in der sie eingeführt wurden, werden in der Tabelle weiter unten in diesem Abschnitt angezeigt. Es wird erwartet, dass weitere Attribute definiert werden, um verschiedene Datenquellen nutzen. ODBC ist eine Reihe von Attributen reserviert. Treiberentwickler müssen Werte für die eigene Verwendung treiberspezifische aus Open Group reservieren.  
  
> [!NOTE]
>  Die Fähigkeit zum Festlegen von Anweisungsattribute auf der Verbindungsebene durch Aufrufen von **SQLSetConnectAttr** veraltet in ODBC 3.*.x*. ODBC 3.*.x* Anwendungen sollten auf der Verbindungsebene Anweisungsattribute festlegen. ODBC 3.*.x* Anweisungsattribute können nicht auf Verbindungsebene, mit Ausnahme von den SQL_ATTR_METADATA_ID und SQL_ATTR_ASYNC_ENABLE-Attributen, die sowohl-Verbindungsattributen und Anweisungsattribute und kann nicht festgelegt werden Legen Sie auf der Verbindungsebene oder Anweisungsebene.  
> 
>  ODBC 3.*.x* Treiber müssen nur diese Funktion unterstützen, wenn sie mit ODBC 2. funktionieren sollte *.x* Anwendungen, die ODBC 2. festgelegt *.x* Anweisungsoptionen auf Verbindungsebene. Weitere Informationen finden Sie unter [SQLSetConnectOption-Zuordnung](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
  
 Kann eine Anwendung aufrufen **SQLSetConnectAttr** zu einem beliebigen Zeitpunkt zwischen dem Zeitpunkt die Verbindung zugeordnet und freigegeben wird. Alle Verbindungs- und Attribute, die von der Anwendung für die Verbindung wurde erfolgreich festgelegt bleiben, bis **SQLFreeHandle** für die Verbindung aufgerufen wird. Wenn eine Anwendung ruft z. B. **SQLSetConnectAttr** vor dem Herstellen einer Verbindung mit einer Datenquelle, die das Attribut beibehalten selbst wenn **SQLSetConnectAttr** im Treiber ein Fehler auftritt, wenn die Anwendung eine Verbindung herstellt der Datenquelle Wenn eine Anwendung eine treiberspezifische Attribut festlegt, beibehalten das Attribut, auch wenn die Anwendung eine Verbindung zu einem anderen Treiber für die Verbindung herstellt.  
  
 Einige Verbindungsattribute können festgelegt werden, nur verwendet werden, bevor eine Verbindung hergestellt wurde. andere können festgelegt werden, nur, nachdem eine Verbindung hergestellt wurde. Die folgende Tabelle zeigt die Verbindungsattribute, die festgelegt werden müssen, bevor oder nachdem eine Verbindung hergestellt wurde. *Entweder* gibt an, dass das Attribut entweder vor oder nach der Verbindung festgelegt werden kann.  
  
|Attribut|Legen Sie vor oder nach Verbindung?|  
|---------------|-------------------------------------|  
|SQL_ATTR_ACCESS_MODE|[1]|  
|SQL_ATTR_ASYNC_DBC_EVENT|Sowohl als auch|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE|Entweder [4]|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK|Sowohl als auch|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT|Sowohl als auch|  
|SQL_ATTR_ASYNC_ENABLE|Entweder [2]|  
|SQL_ATTR_AUTO_IPD|Sowohl als auch|  
|SQL_ATTR_AUTOCOMMIT|Entweder [5]|  
|SQL_ATTR_CONNECTION_DEAD|Nach|  
|SQL_ATTR_CONNECTION_TIMEOUT|Sowohl als auch|  
|SQL_ATTR_CURRENT_CATALOG|[1]|  
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
|SQL_ATTR_TXN_ISOLATION|Entweder [3]|  
  
 [1] SQL_ATTR_ACCESS_MODE und SQL_ATTR_CURRENT_CATALOG kann vor oder nach der eine Verbindung herstellen, abhängig von der Treiber festgelegt werden. Jedoch festlegen, interoperable Anwendungen ausführen können sie vor dem Herstellen einer Verbindung, da einige Treiber ist es nicht möglich, diese nach dem Herstellen einer Verbindung zu ändern.  
  
 [2] SQL_ATTR_ASYNC_ENABLE muss festgelegt werden, bevor es eine aktive Anweisung ist.  
  
 [3] SQL_ATTR_TXN_ISOLATION kann festgelegt werden, nur dann, wenn keine offenen Transaktionen für die Verbindung vorhanden sind. Einige Verbindungsattribute unterstützen Ersetzung von einen ähnlichen Wert aus, wenn die Datenquelle in angegebenen Wert nicht unterstützt \* *ValuePtr*. In solchen Fällen gibt der Treiber SQL_SUCCESS_WITH_INFO und SQLSTATE 01 s 02 (der Optionswert wurde geändert). Z. B. wenn *Attribut* ist SQL_ATTR_PACKET_SIZE und \* *ValuePtr* überschreitet die maximale Paketgröße, die der Treiber ersetzt die maximale Größe. Um den Ersatzwert zu bestimmen, die eine Anwendung ruft **SQLGetConnectAttr**.  
  
 [4] Wenn es sich um eine SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE festgelegt ist, bevor eine Verbindung geöffnet ist, legen den Treiber-Manager des Treibers-Attribut, wenn während eines Aufrufs der Treiber geladen wurde **SQLBrowseConnect**, **SQLConnect**, oder **SQLDriverConnect**. Vor einem Aufruf von **SQLBrowseConnect**, **SQLConnect**, oder **SQLDriverConnect**, der Treiber-Manager ist nicht bekannt, welcher Treiber für das Herstellen einer Verbindung mit und weiß nicht, ob die -Treiber unterstützt die asynchrone Verbindungsvorgänge. Der Treiber-Manager wird daher immer SQL_SUCCESS zurückgegeben. Aber, für den Fall, dass der Treiber die asynchrone Verbindungsvorgängen sendet den Aufruf von nicht unterstützt **SQLBrowseConnect**, **SQLConnect**, oder **SQLDriverConnect** schlägt fehl.  
  
 [5] Wenn SQL_ATTR_AUTOCOMMIT auf "false" festgelegt ist, sollten Anwendungen SQLEndTran(SQL_ROLLBACK) aufrufen, wenn eine beliebige API SQL_ERROR zurück, um die Transaktionskonsistenz sicherzustellen zurückgibt.  
  
 Das Format der Daten, legen Sie in der \* *ValuePtr* Puffer hängt von der angegebenen *Attribut*. **SQLSetConnectAttr** Attributinformationen in einem von zwei verschiedenen Formaten akzeptiert: eine Null-terminierte Zeichenfolge oder einen ganzzahligen Wert. Das Format der einzelnen wird in seine Beschreibung aufgeführt. Zeichenfolgen, verweist der *ValuePtr* Argument **SQLSetConnectAttr** haben eine Länge von *StringLength* Bytes.  
  
 Die *StringLength* Argument wird ignoriert, wenn die Länge, durch das Attribut definiert ist, wie der Fall für alle Attribute in ODBC 2. eingeführt ist *.x* oder früher.  
  
|*Attribut*|*ValuePtr* Inhalt|  
|-----------------|-------------------------|  
|SQL_ATTR_ACCESS_MODE (ODBC 1.0)|Eine SQLUINTEGER-Wert. SQL_MODE_READ_ONLY wird vom Treiber oder der Datenquelle als Indikator verwendet, die die Verbindung nicht erforderlich ist, um SQL-Anweisungen unterstützen, die dazu führen, dass Updates aus. In diesem Modus kann verwendet werden, um Sperrstrategien, Verwalten von Transaktionen oder andere Bereiche entsprechend der Treiber oder eine Datenquelle zu optimieren. Der Treiber ist nicht erforderlich, um zu verhindern, dass diese Anweisungen, die an die Datenquelle gesendet wird. Das Verhalten des Treibers und der Datenquelle, wenn Sie aufgefordert, die SQL-Anweisungen verarbeiten, die nicht schreibgeschützt während einer nur-Lese Verbindung wird die Implementierung definiert. SQL_MODE_READ_WRITE ist die Standardeinstellung.|  
|SQL_ATTR_ASYNC_DBC_EVENT (ODBC 3.8)|Ein SQLPOINTER-Wert, der ein Ereignishandle ist.<br /><br /> Benachrichtigung über den Abschluss des asynchronen Funktionen ist aktiviert, durch den Aufruf **SQLSetConnectAttr** mit dem SQL_ATTR_ASYNC_STMT_EVENT-Attribut und das Ereignishandle angeben. **Hinweis**:  Die Benachrichtigungsmethode wird mit der Cursorbibliothek nicht unterstützt. Eine Anwendung wird die Fehlermeldung angezeigt, wenn es versucht, Cursorbibliothek über SQLSetConnectAttr, aktivieren, wenn die Benachrichtigungsmethode aktiviert ist.|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE (ODBC 3.8)|Eine SQLUINTEGER-Wert, der aktiviert oder deaktiviert die asynchrone Ausführung der ausgewählten Funktionen auf dem Verbindungshandle. Weitere Informationen finden Sie unter [asynchrone Ausführung (Methode abrufen)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).<br /><br /> SQL_ASYNC_DBC_ENABLE_ON = asynchronen Vorgang zum Aktivieren für die angegebene Verbindung in Zusammenhang stehende Funktionen.<br /><br /> SQL_ASYNC_DBC_ENABLE_OFF = (Standard) deaktivieren asynchronen Vorgangs für die angegebene Verbindung in Zusammenhang stehende Funktionen.<br /><br /> Festlegen von SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE ist immer synchron (d. h. Es gibt keine zurück SQL_STILL_EXECUTING).<br /><br /> Asynchrone Ausführung der Anweisung Vorgänge mit SQL_ATTR_ASYNC_ENABLE aktiviert sind.|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK (ODBC 3.8)|Ein SQLPOINTER-Wert, der auf Context-Struktur zeigt.<br /><br /> Nur der Treiber-Manager des Treibers aufrufen können **SQLSetStmtAttr** -Funktion mit diesem Attribut.|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT (ODBC 3.8)|Ein SQLPOINTER-Wert, der auf die Context-Struktur zeigt.<br /><br /> Nur der Treiber-Manager des Treibers aufrufen können **SQLSetStmtAttr** -Funktion mit diesem Attribut.|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 3.0)|Ein SQLULEN-Wert, der angibt, ob eine Funktion mit einer Anweisung für die angegebene Verbindung aufgerufen wird asynchron ausgeführt wird:<br /><br /> SQL_ASYNC_ENABLE_OFF = Disable-Verbindung auf asynchrone Ausführung Unterstützung für Anweisung (Standard).<br /><br /> SQL_ASYNC_ENABLE_ON = aktivieren Sie die Verbindung auf asynchrone Ausführung Unterstützung für Vorgänge der Anweisung.<br /><br /> Dieses Attribut kann sind festgelegt, ob **SQLGetInfo** mit den Informationen SQL_ASYNC_MODE Typ SQL_AM_CONNECTION oder SQL_AM_STATEMENT zurückgibt.|  
|SQL_ATTR_AUTO_IPD (ODBC 3.0)|Eine schreibgeschützte SQLUINTEGER-Wert, der angibt, ob automatische Auffüllung des IPD nach einem Aufruf von **SQLPrepare** wird unterstützt:<br /><br /> SQL_TRUE = automatischen Auffüllung des IPD nach einem Aufruf von **SQLPrepare** wird vom Treiber unterstützt.<br /><br /> SQL_FALSE = automatischen Auffüllung des IPD nach einem Aufruf von **SQLPrepare** wird vom Treiber nicht unterstützt. Server, die nicht unterstützen, vorbereitete Anweisungen werden nicht IPD automatisch aufgefüllt werden.<br /><br /> Wenn für das Verbindungsattribut SQL_ATTR_AUTO_IPD SQL_TRUE zurückgegeben wird, kann das Anweisungsattribut SQL_ATTR_ENABLE_AUTO_IPD zu aktivieren oder deaktivieren Sie die automatischen Auffüllung des IPD festgelegt werden. Wenn SQL_ATTR_AUTO_IPD SQL_FALSE ist, kann nicht SQL_ATTR_ENABLE_AUTO_IPD auf SQL_TRUE festgelegt werden. Der Standardwert von SQL_ATTR_ENABLE_AUTO_IPD ist gleich dem Wert des SQL_ATTR_AUTO_IPD.<br /><br /> Dieses Verbindungsattribut zurückgegeben werden kann, indem **SQLGetConnectAttr** aber nicht festgelegt werden, indem **SQLSetConnectAttr**.|  
|SQL_ATTR_AUTOCOMMIT (ODBC 1.0)|Eine SQLUINTEGER-Wert, der angibt, ob Autocommit oder im Manualcommit-Modus verwenden:<br /><br /> SQL_AUTOCOMMIT_OFF = verwendet der Treiber Manualcommit-Modus, und die Anwendung muss explizit einen commit oder Rollback für Transaktionen mit **SQLEndTran**.<br /><br /> SQL_AUTOCOMMIT_ON = den Treiber verwendet Autocommit-Modus. Jede Anweisung ist bestrebt, unmittelbar nachdem er ausgeführt wird. Dies ist die Standardeinstellung. Alle geöffneten Transaktionen für die Verbindung sind ein Commit ausgeführt, wenn SQL_ATTR_AUTOCOMMIT auf SQL_AUTOCOMMIT_ON festgelegt ist, um von Manualcommit-Modus in den Autocommitmodus zu ändern.<br /><br /> Weitere Informationen finden Sie unter [Commit-Modus](../../../odbc/reference/develop-app/commit-mode.md). **Wichtig:**  Einige Datenquellen löschen die Zugriffspläne, und schließen den Cursor für alle Anweisungen für eine Verbindung jedes Mal, wenn eine Anweisung ein Commit ausgeführt wird; der Autocommit-Modus kann dazu führen, dass dies nach der Ausführung jeder Anweisung Nonquery oder wenn der Cursor für eine Abfrage geschlossen wird. Weitere Informationen finden Sie unter den SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Informationstypen in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [Auswirkung von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md). <br /><br /> Wenn ein Batch im Autocommit-Modus ausgeführt wird, sind zwei Dinge möglich. Der gesamte Batch als eine Einheit Autocommitable behandelt werden kann, oder jede Anweisung in einem Batch wird als eine Einheit Autocommitable behandelt. Bestimmte Datenquellen unterstützen beide diese Verhaltensweisen und möglicherweise eine Möglichkeit zum Auswählen eines dieser Zuordnungsverfahren. Es ist treiberdefinierten gibt an, ob ein Batch als eine Einheit Autocommitable behandelt wird oder ob jede einzelne Anweisung im Batch Autocommitable ist.|  
|SQL_ATTR_CONNECTION_DEAD<br /><br /> (ODBC 3.5)|Ein nur-Lese SQLUINTEGER-Wert, der den Zustand der Verbindung angibt. Wenn SQL_CD_TRUE, die Verbindung unterbrochen wurde. Wenn SQL_CD_FALSE, die Verbindung noch aktiv ist.|  
|SQL_ATTR_CONNECTION_TIMEOUT (ODBC 3.0)|Eine SQLUINTEGER-Wert entspricht der Anzahl der Sekunden für jede Anforderung für die Verbindung ab, bevor Sie an die Anwendung zurückgegeben. Der Treiber SQLSTATE HYT00 sollte zurückgegeben werden (das Timeout ist abgelaufen), dass die It ist jederzeit möglich, zu einem Timeout in einer Situation, die nicht mit der Ausführung von Abfragen oder Anmeldenamen verknüpft sind.<br /><br /> Wenn *ValuePtr* ist gleich 0 (Standard), wird keine zeitliche Beschränkung.|  
|SQL_ATTR_CURRENT_CATALOG (ODBC 2.0)|Eine Zeichenfolge, die mit dem Namen des Katalogs ein, die von der Datenquelle verwendet werden. Z. B. in SQL Server, der Katalog ist eine Datenbank, damit der Treiber sendet eine **verwenden** _Datenbank_ Anweisung, um die Datenquelle, in denen *Datenbank* wird in die Datenbank angegeben \* *ValuePtr*. Für einen ein-Ebenen-Treiber, der Katalog ist möglicherweise ein Verzeichnis, daher ändert sich der Treiber das aktuelle Verzeichnis in das Verzeichnis im angegebenen **ValuePtr*.|  
|SQL_ATTR_DBC_INFO_TOKEN (ODBC 3.8|Ein SQLPOINTER-Wert, der zum Festlegen der wieder das Verbindungstoken für die Informationen in den DBC behandeln Wenn [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)des (\**pRating*)-Parameter ist nicht gleich 100.<br /><br /> SQL_ATTR_DBC_INFO_TOKEN ist nur auf. Es ist nicht möglich, verwenden Sie **SQLGetConnectAttr** oder **SQLGetConnectOption** zum Abrufen dieses Werts. Der Treiber-Manager **SQLSetConnectAttr** SQL_ATTR_DBC_INFO_TOKEN, wird nicht akzeptiert werden, da eine Anwendung sollte dieses Attribut nicht festgelegt.<br /><br /> Ein Treiber SQL_ERROR zurück, nachdem SQL_ATTR_DBC_INFO_TOKEN festgelegt haben, wird die Verbindung, die nur aus dem Pool abgerufen, freigegeben werden. Der Treiber-Manager versucht dann, eine andere Verbindung aus dem Pool zu erhalten. Finden Sie unter [Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md) für Weitere Informationen.|  
|SQL_ATTR_ENLIST_IN_DTC (ODBC 3.0)|Ein SQLPOINTER-Wert, der angibt, ob die ODBC-Treiber an verteilten Transaktionen, die von Microsoft Component Services koordiniert verwenden soll.<br /><br /> Übergeben Sie ein DTC OLE Transaction-Objekt, der angibt, die Transaktion zum Exportieren in SQL Server oder SQL_DTC_DONE auf, um die Verbindung DTC-Zuordnung zu beenden.<br /><br /> Der Client Ruft die Microsoft Distributed Transaction Coordinator (MS DTC) OLE ITransactionDispenser:: BeginTransaction-Methode, um eine MS DTC-Transaktion zu beginnen, und erstellen Sie ein MS DTC-Transaktionsobjekt, das die Transaktion darstellt. Klicken Sie dann die Anwendung ruft SQLSetConnectAttr, mit der Option SQL_ATTR_ENLIST_IN_DTC lauten, die ODBC-Verbindung das Transaktionsobjekt zugeordnet werden soll. Alle entsprechenden Datenbankaktivitäten werden unter dem Schutz der MS DTC-Transaktion durchgeführt. Die Anwendung ruft SQLSetConnectAttr mit SQL_DTC_DONE auf, um die Verbindung DTC-Zuordnung zu beenden. Weitere Informationen finden Sie in der MS DTC-Dokumentation.|  
|SQL_ATTR_LOGIN_TIMEOUT (ODBC 1.0)|Eine SQLUINTEGER-Wert entspricht der Anzahl der Sekunden warten, bis eine anmeldeanforderung ab, bevor Sie an die Anwendung zurückgegeben. Der Standardwert ist treiberabhängig. Wenn *ValuePtr* ist 0, das Timeout ist deaktiviert und ein Verbindungsversuch unbegrenzte Wartezeit festgelegt.<br /><br /> Überschreitet das angegebene Timeout das maximale Anmeldungstimeout in der Datenquelle, wird der Treiber ersetzt diesen Wert und gibt SQLSTATE 01 s 02 (der Optionswert wurde geändert).|  
|SQL_ATTR_METADATA_ID (ODBC 3.0)|Eine SQLUINTEGER-Wert, der bestimmt, wie die Zeichenfolgenargumente von Katalogfunktionen behandelt werden.<br /><br /> Wenn SQL_TRUE, das Zeichenfolgenargument von Katalogfunktionen als Bezeichner behandelt werden. Die Groß-/Kleinschreibung ist nicht signifikant. Der Treiber entfernt nachgestellten Leerzeichen als begrenzungsbezeichnern Zeichenfolgen und die Zeichenfolge in Großbuchstaben gefaltet wird. Für durch Trennzeichen getrennten Zeichenfolgen wird der Treiber entfernt keine führenden oder nachgestellten Leerzeichen und praktisch alles, was zwischen den Trennzeichen wird akzeptiert. Wenn eins dieser Argumente auf einen null-Zeiger festgelegt ist, gibt die Funktion SQL_ERROR zurück, und SQLSTATE HY009 (Ungültige Verwendung von null-Zeiger).<br /><br /> Wenn SQL_FALSE, die Zeichenfolgenargumente von Katalogfunktionen nicht als Bezeichner behandelt werden. Die Groß-/Kleinschreibung spielt. Sie können entweder ein Suchmuster Zeichenfolge oder nicht, je nach dem Argument enthalten.<br /><br /> Der Standardwert ist SQL_FALSE.<br /><br /> Die *TableType* Argument **SQLTables**, der eine Liste von Werten akzeptiert wird durch dieses Attribut nicht beeinflusst.<br /><br /> SQL_ATTR_METADATA_ID kann auch auf Anweisungsebene festgelegt werden. (Es ist das einzige Verbindung-Attribut, das auch ein Anweisungsattribut ist.)<br /><br /> Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).|  
|SQL_ATTR_ODBC_CURSORS (ODBC 2.0)|Ein SQLULEN-Wert, der angibt, wie der Treiber-Manager die ODBC-Cursorbibliothek verwendet wird:<br /><br /> SQL_CUR_USE_IF_NEEDED = der Treiber-Manager verwendet die ODBC-Cursorbibliothek nur, wenn er benötigt wird. Wenn der Treiber die SQL_FETCH_PRIOR-Option in unterstützt **SQLFetchScroll**, der Treiber-Manager verwendet die Bildlauf-Funktionen des Treibers. Andernfalls verwendet es die ODBC-Cursorbibliothek.<br /><br /> SQL_CUR_USE_ODBC = der Treiber-Manager verwendet die ODBC-Cursorbibliothek.<br /><br /> SQL_CUR_USE_DRIVER = der Treiber-Manager verwendet die Bildlauf-Funktionen des Treibers. Dies ist die Standardeinstellung.<br /><br /> Weitere Informationen zu den ODBC-Cursorbibliothek, finden Sie unter [Anhang F: ODBC-Cursorbibliothek](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md). **Warnung:**  Die Cursorbibliothek wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.|  
|SQL_ATTR_PACKET_SIZE (ODBC 2.0)|Eine SQLUINTEGER-Wert, die die Netzwerkpaketgröße in Bytes angibt. **Hinweis**:  Entweder unterstützen viele Datenquellen diese Option nicht oder nur kann Rückgabe jedoch nicht festgelegt der Netzwerkpaketgröße. <br /><br /> Wenn die angegebene Größe die maximale Paketgröße überschreitet oder kleiner als die minimale Paketgröße, wird der Treiber ersetzt diesen Wert und gibt SQLSTATE 01 s 02 (der Optionswert wurde geändert).<br /><br /> Wenn die Anwendung die Paketgröße festlegt, nachdem bereits eine Verbindung hergestellt wurde, wird der Treiber SQLSTATE HY011 zurück (Attribut kann nicht jetzt festgelegt werden).|  
|SQL_ATTR_QUIET_MODE (ODBC 2.0)|Ein Fensterhandle (HWND).<br /><br /> Wenn das Handle des Fensters ein null-Zeiger ist, wird der Treiber nicht; Dialogfelder angezeigt.<br /><br /> Das Fensterhandle kein null-Zeiger ist, sollte das Handle des übergeordneten Fensters der Anwendung sein. Dies ist die Standardeinstellung. Der Treiber verwendet dieses Handle Dialogfelder anzeigen. **Hinweis**:  Das Verbindungsattribut SQL_ATTR_QUIET_MODE gelten nicht für Dialogfelder, **SQLDriverConnect**.|  
|SQL_ATTR_TRACE (ODBC 1.0)|Eine SQLUINTEGER-Wert, der Treiber-Manager mitgeteilt wird, ob die Ablaufverfolgung ausgeführt:<br /><br /> SQL_OPT_TRACE_OFF = Ablaufverfolgung deaktiviert (Standard)<br /><br /> SQL_OPT_TRACE_ON = Ablaufverfolgung on<br /><br /> Wenn Ablaufverfolgung aktiviert ist, schreibt der Treiber-Manager jede ODBC-Funktionsaufruf in der Ablaufverfolgungsdatei. **Hinweis**:  Wenn Ablaufverfolgung aktiviert ist, kann der Treiber-Manager SQLSTATE IM013 zurückgeben (Fehler in der Ablaufverfolgungsdatei) aus jeder Funktion. <br /><br /> Eine Anwendung gibt eine Ablaufverfolgungsdatei mit der Option SQL_ATTR_TRACEFILE an. Wenn die Datei bereits vorhanden ist, wird der Datei der Treiber-Manager hinzufügt. Andernfalls wird die Datei erstellt. Wenn Ablaufverfolgung aktiviert ist und keine der Ablaufverfolgungsdatei angegeben wurde, schreibt in der SQL-Datei der Treiber-Manager. Melden Sie sich im Stammverzeichnis befindet.<br /><br /> Eine Anwendung kann die Variable festlegen **ODBCSharedTraceFlag** zum Aktivieren der Ablaufverfolgung dynamisch. Ablaufverfolgung wird für alle ODBC-Anwendungen, die derzeit ausgeführt. Klicken Sie dann aktiviert. Wenn eine Anwendung die Ablaufverfolgung deaktiviert wird, ist es nur für diese Anwendung deaktiviert.<br /><br /> Wenn die **Ablaufverfolgung** Schlüsselwort in den Systeminformationen auf 1 festgelegt ist, wenn eine Anwendung ruft **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_ENV auf, die Ablaufverfolgung ist für alle aktiviert behandelt. Es ist nur für die Anwendung, die Namen aktiviert **SQLAllocHandle**.<br /><br /> Aufrufen von **SQLSetConnectAttr** mit einer *Attribut* von SQL_ATTR_TRACE ist nicht erforderlich, die *ConnectionHandle* Argument gültig sein und keine SQL_ERROR zurück, wenn *ConnectionHandle* ist NULL. Dieses Attribut gilt für alle Verbindungen.|  
|SQL_ATTR_TRACEFILE (ODBC 1.0)|Eine Null endende Zeichenfolge, mit dem Namen der Ablaufverfolgungsdatei.<br /><br /> Der Standardwert des Attributs SQL_ATTR_TRACEFILE wird angegeben, mit der **TraceFile** Schlüsselwort in den Systeminformationen. Weitere Informationen finden Sie unter [Unterschlüssel für ODBC](../../../odbc/reference/install/odbc-subkey.md).<br /><br /> Aufrufen von **SQLSetConnectAttr** mit eine *Attribut* von SQL_ATTR_ TRACEFILE erfordert keine der *ConnectionHandle* Argument gültig ist und keine SQL_ERROR zurück, wenn *ConnectionHandle* ist ungültig. Dieses Attribut gilt für alle Verbindungen.|  
|SQL_ATTR_TRANSLATE_LIB (ODBC 1.0)|Eine Null-terminierte Zeichenfolge, die mit dem Namen einer Bibliothek enthält die Funktionen **SQLDriverToDataSource** und **SQLDataSourceToDriver** , dass der Treiber zum Durchführen von Aufgaben wie z. B. zugreift zeichensatzübersetzung. Diese Option ist möglicherweise nur angegeben werden, wenn der Treiber eine Verbindung mit der Datenquelle hergestellt hat. Die Einstellung des Attributs wird über Verbindungen beibehalten. Weitere Informationen zum Übersetzen von Daten, finden Sie unter [Konvertierungs-DLLs](../../../odbc/reference/develop-app/translation-dlls.md) und [Übersetzung DLL-Funktionsreferenz](../../../odbc/reference/syntax/translation-dll-api-reference.md).|  
|SQL_ATTR_TRANSLATE_OPTION (ODBC 1.0)|Eine 32-Bit-Flag-Wert, der an den Konvertierungs-DLL übergeben wird. Dieses Attribut kann nur angegeben werden, wenn der Treiber eine Verbindung mit der Datenquelle hergestellt hat. Informationen zum Übersetzen von Daten finden Sie unter [Konvertierungs-DLLs](../../../odbc/reference/develop-app/translation-dlls.md).|  
|SQL_ATTR_TXN_ISOLATION (ODBC 1.0)|Eine 32-Bit-Bitmaske, die die Transaktionsisolationsstufe für die aktuelle Verbindung legt diese fest. Eine Anwendung aufrufen muss **SQLEndTran** , einen commit oder Rollback für alle offenen Transaktionen aus, bei einer Verbindung vor dem Aufruf **SQLSetConnectAttr** mit dieser Option.<br /><br /> Die gültigen Werte für *ValuePtr* kann bestimmt werden, indem **SQLGetInfo** mit *Informationsart* SQL_TXN_ISOLATION_OPTIONS gleich.<br /><br /> Eine Beschreibung der Isolationsstufen von Transaktionen, finden Sie in der Beschreibung des Typs SQL_DEFAULT_TXN_ISOLATION Informationen in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [Isolationsstufen von Transaktionen](../../../odbc/reference/develop-app/transaction-isolation-levels.md).|  
  
 [1] für diese Funktionen können asynchron aufgerufen werden, nur dann, wenn der Deskriptor einer Implementierung, nicht für einen Anwendungsdienst-Deskriptor ist.  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ein Handle zuordnen|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Die Einstellung ein Verbindungsattribut zurückgeben|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
