---
description: SQLConnect-Funktion
title: SQLConnect-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConnect
helpviewer_keywords:
- SQLConnect function [ODBC]
ms.assetid: 59075e46-a0ca-47bf-972a-367b08bb518d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 714bc6f69a72609ee266effff71f1898d62ec7d6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461202"
---
# <a name="sqlconnect-function"></a>SQLConnect-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLCONNECT** stellt Verbindungen mit einem Treiber und einer Datenquelle her. Das Verbindungs Handle verweist auf die Speicherung aller Informationen über die Verbindung mit der Datenquelle, einschließlich Status, Transaktionsstatus und Fehlerinformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLConnect(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      ServerName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      UserName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      Authentication,  
     SQLSMALLINT    NameLength3);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *ServerName*  
 Der Der Name der Datenquelle. Die Daten befinden sich möglicherweise auf demselben Computer wie das Programm oder auf einem anderen Computer in einem Netzwerk. Informationen dazu, wie eine Anwendung eine Datenquelle auswählt, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 Der Länge von **Servername* in Zeichen.  
  
 *UserName*  
 Der Benutzer-ID.  
  
 *NameLength2*  
 Der Länge von **Benutzername* in Zeichen.  
  
 *Authentifizierung*  
 Der Authentifizierungs Zeichenfolge (in der Regel das Kennwort)  
  
 *NameLength3*  
 Der Länge der *-*Authentifizierung* in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCONNECT** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_DBC und einem *handle* von *connectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLCONNECT** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s02 entsprechen|Optionswert geändert|Der Treiber hat den angegebenen Wert des *ValuePtr* -Arguments in **SQLSetConnectAttr** nicht unterstützt und ersetzt einen ähnlichen Wert. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08001|Der Client kann keine Verbindung herstellen.|Der Treiber konnte keine Verbindung mit der Datenquelle herstellen.|  
|08002|Der Verbindungs Name wird verwendet.|(DM) das angegebene *connectionHandle* wurde bereits verwendet, um eine Verbindung mit einer Datenquelle herzustellen, und die Verbindung war weiterhin geöffnet, oder der Benutzer hat eine Verbindung durchsucht.|  
|08004|Der Server hat die Verbindung abgelehnt.|Die Datenquelle hat die Einrichtung der Verbindung aus Implementierungs Gründen abgelehnt.|  
|08S01|Kommunikations Verbindungsfehler|Der Kommunikationslink zwischen dem Treiber und der Datenquelle, mit dem der Treiber eine Verbindung herstellen wollte, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|28000|Ungültige Autorisierungs Spezifikation|Der für das Argument *username* angegebene Wert oder der für die Argument *Authentifizierung* angegebene Wert verletzt die von der Datenquelle definierten Einschränkungen.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|(DM) der Treiber-Manager konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *connectionHandle*aktiviert. Die **SQLCONNECT** -Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde die [sqlcancelhandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) für *connectionHandle*aufgerufen, und anschließend wurde die **SQLCONNECT** -Funktion für *connectionHandle*erneut aufgerufen.<br /><br /> Oder die **SQLCONNECT** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **sqlcancelhandle** für *connectionHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für *connectionHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der für das Argument *NameLength1*, *NameLength2*oder *NameLength3* angegebene Wert war kleiner als 0 (null), aber nicht gleich SQL_NTS.<br /><br /> (DM) der für das Argument *NameLength1* angegebene Wert hat die maximale Länge für einen Datenquellen Namen überschritten.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Verbindung mit der Datenquelle abgeschlossen wurde. Der Timeout Zeitraum wird mithilfe von **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT festgelegt.|  
|HY114|Der Treiber unterstützt keine asynchrone Funktions Ausführung auf Verbindungs Ebene.|(DM) die Anwendung hat den asynchronen Vorgang für das Verbindungs Handle aktiviert, bevor die Verbindung hergestellt wird. Der Treiber unterstützt jedoch keine asynchronen Vorgänge für das Verbindungs Handle.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der vom Datenquellen Namen angegebene Treiber unterstützt die-Funktion nicht.|  
|IM002|Die Datenquelle wurde nicht gefunden und es wurde kein Standardtreiber angegeben.|(DM) der im Argument *Server* Name angegebene Datenquellen Name wurde in den Systeminformationen nicht gefunden, und es war keine Standardtreiber Spezifikation vorhanden.|  
|IM003|Der angegebene Treiber konnte nicht verbunden werden.|(DM) der in der Datenquellen Spezifikation in den Systeminformationen aufgeführte Treiber wurde aus einem anderen Grund nicht gefunden oder konnte nicht verbunden werden.|  
|IM004|Fehler beim Treiber "sqlzugewiesene CHandle" auf SQL_HANDLE_ENV|(DM) bei der **SQLCONNECT**-Funktion hat der Treiber-Manager die **sqlzuweisung** -Funktion des Treibers mit dem *Typ* "SQL_HANDLE_ENV" aufgerufen, und der Treiber hat einen Fehler zurückgegeben.|  
|IM005|Fehler beim Treiber "sqlzugewiesene CHandle" auf SQL_HANDLE_DBC|(DM) bei der **SQLCONNECT**-Funktion hat der Treiber-Manager die **sqlzuweisung** -Funktion des Treibers mit dem *Typ* "SQL_HANDLE_DBC" aufgerufen, und der Treiber hat einen Fehler zurückgegeben.|  
|IM006|Fehler bei ' SQLSetConnectAttr ' des Treibers.|Während der **SQLCONNECT**-Funktion hat der Treiber-Manager die **SQLSetConnectAttr** -Funktion des Treibers aufgerufen, und der Treiber hat einen Fehler zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|IM009|Verbindung mit Übersetzungs-DLL kann nicht hergestellt werden.|Der Treiber konnte keine Verbindung mit der Übersetzungs-DLL herstellen, die für die Datenquelle angegeben wurde.|  
|IM010|Der Datenquellen Name ist zu lang.|(DM) * \* Servername* ist länger als SQL_MAX_DSN_LENGTH Zeichen.|  
|IM014|Der angegebene DSN enthält einen Architektur Konflikt zwischen dem Treiber und der Anwendung.|(DM) 32-Bit-Anwendung verwendet einen DSN, der eine Verbindung mit einem 64-Bit-Treiber herstellt. oder umgekehrt.|  
|IM015|Fehler beim Treiber von SQLConnect auf SQL_HANDLE_DBC_INFO_HANDLE|Wenn ein Treiber SQL_ERROR zurückgibt, wird der Treiber-Manager SQL_ERROR an die Anwendung zurückgegeben, und die Verbindung wird nicht hergestellt.<br /><br /> Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [entwickeln von Verbindungs Pool Informationen in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
|S1118|Der Treiber unterstützt keine asynchrone Benachrichtigung.|Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, können Sie SQL_ATTR_ASYNC_DBC_EVENT oder SQL_ATTR_ASYNC_DBC_RETCODE_PTR nicht festlegen.|  
  
## <a name="comments"></a>Kommentare  
 Informationen dazu, warum eine Anwendung **SQLCONNECT**verwendet, finden Sie unter [Herstellen einer Verbindung mit SQLCONNECT](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md).  
  
 Der Treiber-Manager stellt keine Verbindung mit einem Treiber her, bis die Anwendung eine Funktion (**SQLCONNECT**, **SQLDriverConnect**oder **sqlbrowseconnetct**) zum Herstellen einer Verbindung mit dem Treiber aufruft. Bis zu diesem Zeitpunkt arbeitet der Treiber-Manager mit seinen eigenen Handles und verwaltet die Verbindungsinformationen. Wenn die Anwendung eine Verbindungsfunktion aufruft, überprüft der Treiber-Manager, ob zurzeit ein Treiber für das angegebene *connectionHandle*verbunden ist:  
  
-   Wenn ein Treiber nicht mit verbunden ist, stellt der Treiber-Manager eine Verbindung mit dem Treiber her und ruft **sqlzubinchandle** mit dem *Handlertyp* SQL_HANDLE_ENV, **sqlzuordchandle** mit dem *Handlertyp* SQL_HANDLE_DBC, **SQLSetConnectAttr** (wenn die Anwendung Verbindungs Attribute angegeben hat) und der Verbindungsfunktion im Treiber auf. Der Treiber-Manager gibt SQLSTATE IM006 ( **SQLSetConnectOption** des Treibers) zurück und SQL_SUCCESS_WITH_INFO für die Verbindungsfunktion, wenn der Treiber einen Fehler für **SQLSetConnectAttr**zurückgegeben hat. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md).  
  
-   Wenn der angegebene Treiber bereits mit dem *connectionHandle*verbunden ist, ruft der Treiber-Manager nur die Verbindungsfunktion im Treiber auf. In diesem Fall muss der Treiber sicherstellen, dass alle Verbindungs Attribute für das *connectionHandle* die aktuellen Einstellungen beibehalten.  
  
-   Wenn ein anderer Treiber mit verbunden ist, ruft der Treiber-Manager **SQLFreeHandle mit dem Handlertyp** SQL_HANDLE_DBC auf, und wenn in dieser Umgebung kein anderer Treiber mit verbunden ist, ruft er **SQLFreeHandle** mit einem *Handlertyp* SQL_HANDLE_ENV im verbundenen Treiber auf und trennt dann die Verbindung mit dem Treiber. *HandleType* Anschließend werden die gleichen Vorgänge durchführt, als wenn ein Treiber nicht mit verbunden ist.  
  
 Der Treiber ordnet dann Handles zu und initialisiert sich selbst.  
  
 Wenn die Anwendung **SQLDisconnect**aufruft, ruft der Treiber-Manager **SQLDisconnect** im Treiber auf. Der Treiber wird jedoch nicht getrennt. Dadurch bleibt der Treiber im Speicher für Anwendungen, die wiederholt eine Verbindung mit einer Datenquelle herstellen und diese trennen. Wenn die Anwendung **SQLFreeHandle** mit einem Handlertyp von SQL_HANDLE_DBC aufruft, ruft der Treiber-Manager **SQLFreeHandle** mit dem *Typ* SQL_HANDLE_DBC und dann **SQLFreeHandle** *mit einem Handlertyp von* SQL_HANDLE_ENV im Treiber auf und trennt dann die Verbindung des Treibers. *HandleType*  
  
 Eine ODBC-Anwendung kann mehr als eine Verbindung herstellen.  
  
## <a name="driver-manager-guidelines"></a>Leitfaden für Treiber-Manager  
 Der Inhalt von **Servername* wirkt sich darauf aus, wie der Treiber-Manager und ein Treiber zusammenarbeiten, um eine Verbindung mit einer Datenquelle herzustellen.  
  
-   Wenn \* *Server* Name einen gültigen Datenquellen Namen enthält, wird vom Treiber-Manager die entsprechende Datenquellen Spezifikation in den Systeminformationen angezeigt, und es wird eine Verbindung mit dem zugeordneten Treiber hergestellt. Der Treiber-Manager übergibt jedes **SQLCONNECT** -Argument an den Treiber.  
  
-   Wenn der Name der Datenquelle nicht gefunden werden kann oder wenn *Server* Name ein NULL-Zeiger ist, sucht der Treiber-Manager die Spezifikation der Standarddaten Quelle und stellt eine Verbindung mit dem zugeordneten Treiber her. Der Treiber-Manager übergibt den *Benutzernamen* und die *Authentifizierungs* Argumente unverändert und "Standard" für das *Servername* -Argument.  
  
-   Wenn das *Servername* -Argument "Default" ist, sucht der Treiber-Manager nach der standardmäßigen Datenquellen Spezifikation und stellt eine Verbindung mit dem zugeordneten Treiber her. Der Treiber-Manager übergibt jedes **SQLCONNECT** -Argument an den Treiber.  
  
-   Wenn der Name der Datenquelle nicht gefunden werden kann oder wenn *Server* Name ein NULL-Zeiger ist und die standardmäßige Datenquellen Spezifikation nicht vorhanden ist, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE IM002 zurück (der Datenquellen Name wurde nicht gefunden, und es wurde kein Standardtreiber angegeben).  
  
 Nachdem eine Verbindung mit dem Treiber-Manager hergestellt wurde, kann ein Treiber seine entsprechende Datenquellen Spezifikation in den Systeminformationen finden und Treiber spezifische Informationen aus der Spezifikation verwenden, um die erforderlichen Verbindungsinformationen abzuschließen.  
  
 Wenn eine Standard Übersetzungs Bibliothek in den Systeminformationen für die Datenquelle angegeben ist, stellt der Treiber eine Verbindung damit her. Eine andere Übersetzungs Bibliothek kann durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_TRANSLATE_LIB-Attribut verbunden werden. Eine Übersetzungs Option kann durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_TRANSLATE_OPTION-Attribut angegeben werden.  
  
 Wenn ein Treiber **SQLCONNECT**unterstützt, muss der Treiber Schlüsselwortbereich der Systeminformationen für den Treiber das **connectfunctions** -Schlüsselwort enthalten, wobei das erste Zeichen auf "Y" festgelegt ist.  
  
### <a name="connection-pooling"></a>Verbindungspooling  
 Das Verbindungspooling ermöglicht einer Anwendung, eine bereits erstellte Verbindung wiederzuverwenden. Wenn das Verbindungspooling aktiviert ist und **SQLCONNECT** aufgerufen wird, versucht der Treiber-Manager, die Verbindung mithilfe einer Verbindung herzustellen, die zu einem Pool von Verbindungen in einer Umgebung gehört, die für das Verbindungspooling vorgesehen ist. Diese Umgebung ist eine freigegebene Umgebung, die von allen Anwendungen verwendet wird, die die Verbindungen im Pool verwenden.  
  
 Das Verbindungspooling wird aktiviert, bevor die Umgebung zugeordnet wird, indem **SQLSetEnvAttr** aufgerufen wird, um SQL_ATTR_CONNECTION_POOLING auf SQL_CP_ONE_PER_DRIVER festzulegen (das maximal einen Pool pro Treiber angibt) oder SQL_CP_ONE_PER_HENV (das maximal einen Pool pro Umgebung angibt). **SQLSetEnvAttr** wird in diesem Fall mit dem auf NULL festgelegten *environmenthandle* aufgerufen, wodurch das Attribut ein Attribut auf Prozessebene ist. Wenn SQL_ATTR_CONNECTION_POOLING auf SQL_CP_OFF festgelegt ist, wird das Verbindungs Pooling deaktiviert.  
  
 Nachdem das Verbindungspooling aktiviert wurde, wird **SQLAllocHandle** mit dem *Typ* "SQL_HANDLE_ENV" aufgerufen, um eine Umgebung zuzuordnen. Die durch diesen-Befehl zugeordnete Umgebung ist eine freigegebene Umgebung, da Verbindungspooling aktiviert wurde. Die Umgebung, die verwendet wird, wird jedoch erst bestimmt, wenn " **sqlzuzuordchandle** " mit dem *Typ* "SQL_HANDLE_DBC" aufgerufen wird.  
  
 **SQLAllocHandle** mit dem *Typ* "SQL_HANDLE_DBC" wird aufgerufen, um eine Verbindung zuzuordnen. Der Treiber-Manager versucht, eine vorhandene freigegebene Umgebung zu finden, die mit den von der Anwendung festgelegten Umgebungs Attributen übereinstimmt. Wenn keine solche Umgebung vorhanden ist, wird eine solche Umgebung als implizite frei *gegebene Umgebung*erstellt. Wenn eine übereinstimmende freigegebene Umgebung gefunden wird, wird das Umgebungs Handle an die Anwendung zurückgegeben, und der Verweis Zähler wird inkrementiert.  
  
 Die Verbindung, die verwendet wird, wird jedoch erst bestimmt, wenn **SQLCONNECT** aufgerufen wird. An diesem Punkt versucht der Treiber-Manager, eine vorhandene Verbindung im Verbindungspool zu suchen, die den von der Anwendung angeforderten Kriterien entspricht. Diese Kriterien umfassen die im Aufruf von **SQLCONNECT** angeforderten Verbindungsoptionen (die Werte der Schlüsselwörter " *Servername*", " *username*" und " *Authentication* ") und alle Verbindungs Attribute, die seit dem Aufruf von " **sqlzuordchandle** " mit dem *Typ* "SQL_HANDLE_DBC" aufgerufen wurden. Der Treiber-Manager überprüft diese Kriterien anhand der entsprechenden Verbindungs Schlüsselwörter und Attribute in Verbindungen im Pool. Wenn eine Entsprechung gefunden wird, wird die Verbindung im Pool verwendet. Wenn keine Entsprechung gefunden wird, wird eine neue Verbindung erstellt.  
  
 Wenn das SQL_ATTR_CP_MATCH-Umgebungs Attribut auf SQL_CP_STRICT_MATCH festgelegt ist, muss die Entsprechung für eine zu verwendende Verbindung im Pool genau sein. Wenn das SQL_ATTR_CP_MATCH-Umgebungs Attribut auf SQL_CP_RELAXED_MATCH festgelegt ist, müssen die Verbindungsoptionen im-Befehl von **SQLCONNECT** entsprechen, aber nicht alle Verbindungs Attribute müssen identisch sein.  
  
 Die folgenden Regeln werden angewendet, wenn ein Verbindungs Attribut, das von der Anwendung vor dem Aufruf von **SQLCONNECT** festgelegt wurde, nicht mit dem Verbindungs Attribut der Verbindung im Pool identisch ist:  
  
-   Wenn das Verbindungs Attribut festgelegt werden muss, bevor die Verbindung hergestellt wird:  
  
     Wenn SQL_ATTR_CP_MATCH SQL_CP_STRICT_MATCH ist, müssen SQL_ATTR_PACKET_SIZE in der zusammen gepoolten Verbindung mit dem von der Anwendung festgelegten Attribut identisch sein. Wenn SQL_CP_RELAXED_MATCH, können sich die Werte SQL_ATTR_PACKET_SIZE unterscheiden.  
  
     Der Wert SQL_ATTR_LOGIN_VALUE hat keine Auswirkung auf die Entsprechung.  
  
-   Wenn das Verbindungs Attribut entweder vor oder nach dem Herstellen der Verbindung festgelegt werden kann:  
  
     Wenn das Verbindungs Attribut nicht von der Anwendung festgelegt wurde, aber für die Verbindung im Pool festgelegt wurde und ein Standardwert vorhanden ist, wird das Verbindungs Attribut in der gepoolten Verbindung auf den Standardwert zurückgesetzt, und eine Entsprechung wird deklariert. Wenn kein Standardwert vorhanden ist, wird die im Pool zusammengefasste Verbindung nicht als Abgleich betrachtet.  
  
     Wenn das Verbindungs Attribut von der Anwendung festgelegt wurde, jedoch nicht für die Verbindung im Pool festgelegt wurde, wird das Verbindungs Attribut für den Pool in das von der Anwendung festgelegte geändert, und eine Entsprechung wird deklariert.  
  
     Wenn das Verbindungs Attribut von der Anwendung festgelegt wurde und auch für die Verbindung im Pool festgelegt wurde, die Werte jedoch unterschiedlich sind, wird der Wert des Verbindungs Attributs der Anwendung verwendet, und eine Entsprechung wird deklariert.  
  
-   Wenn die Werte von treiberspezifischen Verbindungs Attributen nicht identisch sind und SQL_ATTR_CP_MATCH auf SQL_CP_STRICT_MATCH festgelegt ist, wird die Verbindung im Pool nicht verwendet.  
  
 Wenn die Anwendung **SQLDisconnect** aufruft, um die Verbindung zu trennen, wird die Verbindung an den Verbindungspool zurückgegeben und steht zur erneuten Verwendung zur Verfügung.  
  
### <a name="optimizing-connection-pooling-performance"></a>Optimieren der Verbindungs Pooling-Leistung  
 Wenn verteilte Transaktionen beteiligt sind, ist es möglich, die Verbindung mit dem Verbindungspooling mithilfe von **SQL_DTC_TRANSITION_COST**zu optimieren. dabei handelt es sich um eine SQLUINTEGER-Bitmaske. Bei den Übergängen, auf die verwiesen wird, handelt es sich um die Übergänge des Connection-Attributs SQL_ATTR_ENLIST_IN_DTC von Wert 0 bis ungleich NULL und umgekehrt. Dabei handelt es sich um eine Verbindung, die von nicht in einer verteilten Transaktion in eine verteilte Transaktion eingetragen wird und umgekehrt. Abhängig davon, wie der Treiber die Eintragung implementiert hat (Festlegen der Verbindungs Attribute SQL_ATTR_ENLIST_IN_DTC), können diese Übergänge teuer sein und sollten daher für eine optimale Leistung vermieden werden.  
  
 Der vom Treiber zurückgegebene Wert enthält eine beliebige Kombination der folgenden Bits:  
  
-   Wenn festgelegt ist, bedeutet **SQL_DTC_ENLIST_EXPENSIVE**, dass der Übergang zwischen null und NULL erheblich teurer ist als ein Übergang von einem Wert ungleich 0 (null) zu einem anderen Wert ungleich 0 (eingetragen eine zuvor eingetragene Verbindung in der nächsten Transaktion).  
  
-   Wenn festgelegt ist, bedeutet das, dass der Übergang ungleich NULL und NULL erheblich teurer ist als die Verwendung einer Verbindung, deren SQL_ATTR_ENLIST_IN_DTC-Attribut bereits auf NULL festgelegt ist. **SQL_DTC_UNENLIST_EXPENSIVE**  
  
 Es gibt einen Kompromiss bei der Leistungs-und Verbindungs Verwendung. Wenn ein Treiber anzeigt, dass mindestens einer dieser Übergänge teuer ist, antwortet der Verbindungspool des Treiber-Managers darauf, indem er mehr Verbindungen im Pool beibehält. Einige der Verbindungen im Pool werden für die nicht transaktionale Verwendung bevorzugt, und einige sind für die Transaktions Verwendung bevorzugt. Wenn der Treiber jedoch angibt, dass diese Übergänge nicht teuer sind, können weniger Verbindungen verwendet werden, möglicherweise Wechsel zwischen nicht transaktionaler und transaktionaler Verwendung.  
  
 Treiber, die SQL_ATTR_ENLIST_IN_DTC nicht unterstützen, müssen SQL_DTC_TRANSITION_COST nicht unterstützen. Für Treiber, die SQL_ATTR_ENLIST_IN_DTC, aber nicht SQL_DTC_TRANSITION_COST unterstützen, wird davon ausgegangen, dass die Übergänge nicht aufwendig sind, als ob der Treiber 0 (keine Bits festgelegt) für diesen Wert zurückgegeben hat.  
  
 Obwohl SQL_DTC_TRANSITION_COST in ODBC 3,5 eingeführt wurde, ein ODBC 2. der *x* -Treiber kann ihn auch unterstützen, da der Treiber-Manager diese Informationen unabhängig von der Treiber Version abfragt.  
  
### <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel weist eine Anwendung Umgebungs-und Verbindungs Handles zu. Anschließend wird eine Verbindung mit der Datenquelle SalesOrders mit der Benutzer-ID Johns und dem Kennwort Sesam hergestellt, und die Daten werden verarbeitet. Wenn die Verarbeitung von Daten abgeschlossen ist, wird die Verbindung mit der Datenquelle getrennt, und die Handles werden freigegeben.  
  
```cpp  
// SQLConnect_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
  
   SQLCHAR * OutConnStr = (SQLCHAR * )malloc(255);  
   SQLSMALLINT * OutConnStrLen = (SQLSMALLINT *)malloc(255);  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLCHAR*) "NorthWind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
### <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuordnen eines Handles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Ermitteln und Auflisten von Werten, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Trennen der Verbindung mit einer Datenquelle|[SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungs Zeichenfolge oder ein Dialogfeld|[SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Zurückgeben der Einstellung eines Verbindungs Attributs|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Festlegen eines Verbindungs Attributs|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
