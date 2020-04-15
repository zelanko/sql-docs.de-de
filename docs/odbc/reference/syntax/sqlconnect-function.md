---
title: SQLConnect-Funktion | Microsoft Docs
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
ms.openlocfilehash: ab0a31845efeb484c554a9c9cf1afeaeab1a8bea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301216"
---
# <a name="sqlconnect-function"></a>SQLConnect-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLConnect** stellt Verbindungen zu einem Treiber und einer Datenquelle her. Das Verbindungshandle verweist auf die Speicherung aller Informationen über die Verbindung zur Datenquelle, einschließlich Status, Transaktionsstatus und Fehlerinformationen.  
  
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
 [Eingabe] Datenquellenname. Die Daten befinden sich möglicherweise auf demselben Computer wie das Programm oder auf einem anderen Computer irgendwo in einem Netzwerk. Informationen dazu, wie eine Anwendung eine Datenquelle auswählt, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Eingabe] Länge von **ServerName* in Zeichen.  
  
 *Nutzername*  
 [Eingabe] Benutzerkennung.  
  
 *NameLength2*  
 [Eingabe] Länge von **UserName* in Zeichen.  
  
 *Authentifizierung*  
 [Eingabe] Authentifizierungszeichenfolge (in der Regel das Kennwort).  
  
 *NameLength3*  
 [Eingabe] Länge der **Authentifizierung* in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLConnect** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DBC und einem *Handle* von *ConnectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLConnect** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber unterstützte den angegebenen Wert des *ValuePtr-Arguments* in **SQLSetConnectAttr** nicht und ersetzte einen ähnlichen Wert. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08001|Client kann keine Verbindung herstellen|Der Treiber konnte keine Verbindung mit der Datenquelle herstellen.|  
|08002|Verbindungsname wird verwendet|(DM) Das angegebene *ConnectionHandle* wurde bereits verwendet, um eine Verbindung mit einer Datenquelle herzustellen, und die Verbindung war noch geöffnet oder der Benutzer suchte nach einer Verbindung.|  
|08004|Server hat die Verbindung abgelehnt|Die Datenquelle lehnte den Aufbau der Verbindung aus implementierungsdefinierten Gründen ab.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber eine Verbindung herstellen wollte, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|28000|Ungültige Autorisierungsspezifikation|Der für das Argument *UserName* oder den für das Argument *Authentifizierung* angegebene Wert hat Einschränkungen verletzt, die von der Datenquelle definiert wurden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|(DM) Der Treiber-Manager konnte keinen Speicher zuweisen, der zur Unterstützung der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *den ConnectionHandle*aktiviert. Die **SQLConnect-Funktion** wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde [DIE SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) für den *ConnectionHandle*aufgerufen, und dann wurde die **SQLConnect-Funktion** erneut für *ConnectionHandle*aufgerufen.<br /><br /> Oder die **SQLConnect-Funktion** wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancelHandle** für das *ConnectionHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Eine asynchron ausführende Funktion (nicht diese) wurde für den *ConnectionHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der für das Argument *NameLength1*, *NameLength2*oder *NameLength3* angegebene Wert war kleiner als 0, aber nicht gleich SQL_NTS.<br /><br /> (DM) Der für das Argument *NameLength1* angegebene Wert hat die maximale Länge für einen Datenquellennamen überschritten.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Verbindung mit der Datenquelle abgeschlossen wurde. Der Timeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT festgelegt.|  
|HY114|Treiber unterstützt keine asynchrone Funktionsausführung auf Verbindungsebene|(DM) Die Anwendung aktivierte den asynchronen Vorgang am Verbindungshandle, bevor die Verbindung hergestellt wurde. Der Treiber unterstützt jedoch keine asynchronen Vorgänge für das Verbindungshandle.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der durch den Datenquellennamen angegebene Treiber unterstützt die Funktion nicht.|  
|IM002|Datenquelle nicht gefunden und kein Standardtreiber angegeben|(DM) Der im Argument *ServerName* angegebene Datenquellenname wurde in den Systeminformationen nicht gefunden, und es gab auch keine Standardtreiberspezifikation.|  
|IM003|Der angegebene Treiber konnte nicht mit|(DM) Der treiber, der in der Datenquellenspezifikation in den Systeminformationen aufgeführt ist, wurde aus einem anderen Grund nicht gefunden oder konnte nicht verbunden werden.|  
|IM004|SQLAllocHandle des Treibers auf SQL_HANDLE_ENV fehlgeschlagen|(DM) Während **SQLConnect**rief der Treiber-Manager die **SQLAllocHandle-Funktion** des Treibers mit einem *HandleType* von SQL_HANDLE_ENV und der Treiber gab einen Fehler zurück.|  
|IM005|SQLAllocHandle des Treibers auf SQL_HANDLE_DBC fehlgeschlagen|(DM) Während **SQLConnect**rief der Treiber-Manager die **SQLAllocHandle-Funktion** des Treibers mit einem *HandleType* von SQL_HANDLE_DBC und der Treiber gab einen Fehler zurück.|  
|IM006|SQLSetConnectAttr des Treibers fehlgeschlagen|Während **SQLConnect**rief der Treiber-Manager die **SQLSetConnectAttr-Funktion** des Treibers auf, und der Treiber gab einen Fehler zurück. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|IM009|Übersetzungs-DLL kann nicht hergestellt werden.|Der Treiber konnte keine Verbindung mit der Übersetzungs-DLL herstellen, die für die Datenquelle angegeben wurde.|  
|IM010|Datenquellenname zu lang|(DM) * \*ServerName* war länger als SQL_MAX_DSN_LENGTH Zeichen.|  
|IM014|Der angegebene DSN enthält eine Architekturkonfliktübereinstimmung zwischen Treiber und Anwendung|(DM) 32-Bit-Anwendung verwendet eine DSN-Verbindung mit einem 64-Bit-Treiber; oder umgekehrt.|  
|IM015|SQLConnect des Treibers auf SQL_HANDLE_DBC_INFO_HANDLE fehlgeschlagen|Wenn ein Treiber SQL_ERROR zurückkehrt, kehrt der Treiber-Manager SQL_ERROR an die Anwendung zurück, und die Verbindung schlägt fehl.<br /><br /> Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [Entwickeln von Verbindungspool-Awareness in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
|S1118|Treiber unterstützt keine asynchrone Benachrichtigung|Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, können Sie keine SQL_ATTR_ASYNC_DBC_EVENT oder SQL_ATTR_ASYNC_DBC_RETCODE_PTR festlegen.|  
  
## <a name="comments"></a>Kommentare  
 Informationen dazu, warum eine Anwendung **SQLConnect**verwendet, finden Sie unter [Verbinden mit SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md).  
  
 Der Treiber-Manager stellt erst dann eine Verbindung mit einem Treiber her, wenn die Anwendung eine Funktion (**SQLConnect**, **SQLDriverConnect**oder **SQLBrowseConnect**) aufruft, um eine Verbindung mit dem Treiber herzustellen. Bis zu diesem Zeitpunkt arbeitet der Treiber-Manager mit eigenen Handles und verwaltet Verbindungsinformationen. Wenn die Anwendung eine Verbindungsfunktion aufruft, prüft der Treiber-Manager, ob ein Treiber derzeit für den angegebenen *ConnectionHandle*verbunden ist:  
  
-   Wenn ein Treiber nicht mit einem Treiber verbunden ist, stellt der Treiber-Manager eine Verbindung mit dem Treiber her und ruft **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV, **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DBC, **SQLSetConnectAttr** (wenn die Anwendung Verbindungsattribute angegeben hat) und die Verbindungsfunktion im Treiber auf. Der Treiber-Manager gibt SQLSTATE IM006 **(Treiber SQLSetConnectOption** fehlgeschlagen) und SQL_SUCCESS_WITH_INFO für die Verbindungsfunktion zurück, wenn der Treiber einen Fehler für **SQLSetConnectAttr**zurückgegeben hat. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md).  
  
-   Wenn der angegebene Treiber bereits mit dem *ConnectionHandle*verbunden ist, ruft der Treiber-Manager nur die Verbindungsfunktion im Treiber auf. In diesem Fall muss der Treiber sicherstellen, dass alle Verbindungsattribute für das *ConnectionHandle* ihre aktuellen Einstellungen beibehalten.  
  
-   Wenn ein anderer Treiber mit einem anderen Treiber verbunden ist, ruft der Treiber-Manager **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DBC auf, und wenn kein anderer Treiber in dieser Umgebung verbunden ist, ruft er **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_ENV im verbundenen Treiber auf und trennt dann diesen Treiber. Anschließend werden dieselben Vorgänge ausgeführt, mit denen ein Treiber nicht verbunden ist.  
  
 Der Treiber ordnet dann Handles zu und initialisiert sich selbst.  
  
 Wenn die Anwendung **SQLDisconnect**aufruft, ruft der Treiber-Manager **SQLDisconnect** im Treiber auf. Der Treiber wird jedoch nicht getrennt. Dadurch bleibt der Treiber im Arbeitsspeicher für Anwendungen, die wiederholt eine Verbindung zu einer Datenquelle herstellen und diese trennen. Wenn die Anwendung **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DBC aufruft, ruft der Treiber-Manager **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DBC und dann **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_ENV im Treiber auf und trennt dann den Treiber.  
  
 Eine ODBC-Anwendung kann mehr als eine Verbindung herstellen.  
  
## <a name="driver-manager-guidelines"></a>Driver Manager-Richtlinien  
 Der Inhalt von **ServerName* wirkt sich auf die Zusammenarbeit zwischen dem Treiber-Manager und einem Treiber aus, um eine Verbindung zu einer Datenquelle herzustellen.  
  
-   Wenn \* *ServerName* einen gültigen Datenquellennamen enthält, sucht der Treiber-Manager die entsprechende Datenquellenspezifikation in den Systeminformationen und stellt eine Verbindung mit dem zugehörigen Treiber her. Der Treiber-Manager übergibt jedes **SQLConnect-Argument** an den Treiber.  
  
-   Wenn der Datenquellenname nicht gefunden werden kann oder *ServerName* ein Nullzeiger ist, sucht der Treiber-Manager die Standarddatenquellenspezifikation und stellt eine Verbindung mit dem zugehörigen Treiber her. Der Treiber-Manager übergibt dem Treiber die *Unmodifizierten UserName-* und *Authentifizierungsargumente* und "DEFAULT" für das *Argument ServerName* an den Treiber.  
  
-   Wenn das *Argument ServerName "DEFAULT"* lautet, sucht der Treiber-Manager die Standarddatenquellenspezifikation und stellt eine Verbindung mit dem zugehörigen Treiber her. Der Treiber-Manager übergibt jedes **SQLConnect-Argument** an den Treiber.  
  
-   Wenn der Datenquellenname nicht gefunden werden kann oder *ServerName* ein Nullzeiger ist und die Standarddatenquellenspezifikation nicht vorhanden ist, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE IM002 zurück (Datenquellenname nicht gefunden und kein Standardtreiber angegeben).  
  
 Nachdem er über den Treiber-Manager verbunden wurde, kann ein Treiber die entsprechende Datenquellenspezifikation in den Systeminformationen finden und treiberspezifische Informationen aus der Spezifikation verwenden, um die erforderlichen Verbindungsinformationen auszufüllen.  
  
 Wenn in den Systeminformationen für die Datenquelle eine Standardübersetzungsbibliothek angegeben ist, stellt der Treiber eine Verbindung mit ihr her. Eine andere Übersetzungsbibliothek kann verbunden werden, indem **SQLSetConnectAttr** mit dem Attribut SQL_ATTR_TRANSLATE_LIB aufgerufen wird. Eine Übersetzungsoption kann angegeben werden, indem **SQLSetConnectAttr** mit dem Attribut SQL_ATTR_TRANSLATE_OPTION aufgerufen wird.  
  
 Wenn ein Treiber **SQLConnect**unterstützt, muss der Schlüsselwortabschnitt des Treiberschlüsselworts der Systeminformationen für den Treiber das **Schlüsselwort ConnectFunctions** mit dem ersten Zeichensatz auf "Y" enthalten.  
  
### <a name="connection-pooling"></a>Verbindungspooling  
 Durch das Verbindungspooling kann eine Anwendung eine bereits erstellte Verbindung wiederverwenden. Wenn das Verbindungspooling aktiviert ist und **SQLConnect** aufgerufen wird, versucht der Treiber-Manager, die Verbindung mithilfe einer Verbindung herzustellen, die Teil eines Verbindungspools in einer Umgebung ist, die für das Verbindungspooling vorgesehen ist. Diese Umgebung ist eine freigegebene Umgebung, die von allen Anwendungen verwendet wird, die die Verbindungen im Pool verwenden.  
  
 Das Verbindungspooling wird aktiviert, bevor die Umgebung zugewiesen wird, indem **SQLSetEnvAttr** aufgerufen wird, um SQL_ATTR_CONNECTION_POOLING auf SQL_CP_ONE_PER_DRIVER (die maximal einen Pool pro Treiber angibt) oder SQL_CP_ONE_PER_HENV (die ein Maximum von einem Pool pro Umgebung angibt) festzulegen. **SQLSetEnvAttr** wird in diesem Fall aufgerufen, wobei *EnvironmentHandle* auf null gesetzt ist, wodurch das Attribut zu einem Attribut auf Prozessebene wird. Wenn SQL_ATTR_CONNECTION_POOLING auf SQL_CP_OFF festgelegt ist, ist das Verbindungspooling deaktiviert.  
  
 Nachdem das Verbindungspooling aktiviert wurde, wird **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV aufgerufen, um eine Umgebung zuzuweisen. Die von diesem Aufruf zugewiesene Umgebung ist eine freigegebene Umgebung, da das Verbindungspooling aktiviert wurde. Die Umgebung, die verwendet wird, wird jedoch erst bestimmt, **wenn SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DBC aufgerufen wird.  
  
 **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DBC wird aufgerufen, um eine Verbindung zuzuweisen. Der Treiber-Manager versucht, eine vorhandene freigegebene Umgebung zu finden, die den von der Anwendung festgelegten Umgebungsattributen entspricht. Wenn keine solche Umgebung vorhanden ist, wird eine als implizite *gemeinsame Umgebung*erstellt. Wenn eine übereinstimmende freigegebene Umgebung gefunden wird, wird das Umgebungshandle an die Anwendung zurückgegeben, und die Referenzanzahl wird erhöht.  
  
 Die Verbindung, die verwendet wird, wird jedoch erst bestimmt, wenn **SQLConnect** aufgerufen wird. Zu diesem Zeitpunkt versucht der Treiber-Manager, eine vorhandene Verbindung im Verbindungspool zu finden, die den von der Anwendung angeforderten Kriterien entspricht. Zu diesen Kriterien gehören die verbindungsoptionen, die beim Aufruf von **SQLConnect** angefordert werden (die Werte der Schlüsselwörter *ServerName*, *UserName*und *Authentication)* und alle Verbindungsattribute, die seit **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DBC aufgerufen wurden. Der Treiber-Manager überprüft diese Kriterien anhand der entsprechenden Verbindungsschlüsselwörter und Attribute in Verbindungen im Pool. Wenn eine Übereinstimmung gefunden wird, wird die Verbindung im Pool verwendet. Wenn keine Übereinstimmung gefunden wird, wird eine neue Verbindung erstellt.  
  
 Wenn das SQL_ATTR_CP_MATCH Umgebungsattribut auf SQL_CP_STRICT_MATCH festgelegt ist, muss die Übereinstimmung genau sein, damit eine Verbindung im Pool verwendet werden kann. Wenn das SQL_ATTR_CP_MATCH Umgebungsattribut auf SQL_CP_RELAXED_MATCH festgelegt ist, müssen die Verbindungsoptionen im Aufruf von **SQLConnect** übereinstimmen, aber nicht alle Verbindungsattribute müssen übereinstimmen.  
  
 Die folgenden Regeln werden angewendet, wenn ein Verbindungsattribut, wie von der Anwendung festgelegt, bevor **SQLConnect** aufgerufen wird, nicht mit dem Verbindungsattribut der Verbindung im Pool übereinstimmt:  
  
-   Wenn das Verbindungsattribut festgelegt werden muss, bevor die Verbindung hergestellt wird:  
  
     Wenn SQL_ATTR_CP_MATCH SQL_CP_STRICT_MATCH ist, muss SQL_ATTR_PACKET_SIZE in der gepoolten Verbindung mit dem von der Anwendung festgelegten Attribut identisch sein. Wenn SQL_CP_RELAXED_MATCH, können die Werte von SQL_ATTR_PACKET_SIZE unterschiedlich sein.  
  
     Der Wert von SQL_ATTR_LOGIN_VALUE wirkt sich nicht auf die Übereinstimmung aus.  
  
-   Wenn das Verbindungsattribut entweder vor oder nach dem Herstellen der Verbindung festgelegt werden kann:  
  
     Wenn das Verbindungsattribut nicht von der Anwendung festgelegt wurde, aber für die Verbindung im Pool festgelegt wurde und ein Standardwert vorhanden ist, wird das Verbindungsattribut in der gepoolten Verbindung auf den Standardwert zurückgesetzt, und es wird eine Übereinstimmung deklariert. Wenn kein Standardwert vorhanden ist, wird die gepoolte Verbindung nicht als Übereinstimmung betrachtet.  
  
     Wenn das Verbindungsattribut von der Anwendung festgelegt, aber nicht für die Verbindung im Pool festgelegt wurde, wird das Verbindungsattribut im Pool in das von der Anwendung festgelegte geändert, und es wird eine Übereinstimmung deklariert.  
  
     Wenn das Verbindungsattribut von der Anwendung festgelegt wurde und auch für die Verbindung im Pool festgelegt wurde, die Werte jedoch unterschiedlich sind, wird der Wert des Verbindungsattributs der Anwendung verwendet und eine Übereinstimmung deklariert.  
  
-   Wenn die Werte der treiberspezifischen Verbindungsattribute nicht identisch sind und SQL_ATTR_CP_MATCH auf SQL_CP_STRICT_MATCH festgelegt ist, wird die Verbindung im Pool nicht verwendet.  
  
 Wenn die Anwendung **sqlDisconnect** aufruft, um die Verbindung zu trennen, wird die Verbindung an den Verbindungspool zurückgegeben und kann wiederverwendet werden.  
  
### <a name="optimizing-connection-pooling-performance"></a>Optimieren der Verbindungspooling-Leistung  
 Wenn verteilte Transaktionen beteiligt sind, ist es möglich, die Verbindungspooling-Performance mithilfe **von SQL_DTC_TRANSITION_COST zu**optimieren, bei dem es sich um eine SQLUINTEGER-Bitmaske handelt. Die Übergänge, auf die verwiesen wird, sind die Übergänge des Verbindungsattributs SQL_ATTR_ENLIST_IN_DTC, die von Wert 0 nach ungleich Null gehen, und umgekehrt. Dies ist eine Verbindung, die nicht in einer verteilten Transaktion eingetragen ist, um in eine verteilte Transaktion eingeschrieben zu sein, und umgekehrt. Je nachdem, wie der Treiber die Einschreibung implementiert hat (Einstellung des Verbindungsattributs SQL_ATTR_ENLIST_IN_DTC), können diese Übergänge teuer sein und sollten daher für eine optimale Leistung vermieden werden.  
  
 Der vom Treiber zurückgegebene Wert enthält eine beliebige Kombination der folgenden Bits:  
  
-   **SQL_DTC_ENLIST_EXPENSIVE**impliziert, dass der Übergang von Null in Unwert null erheblich teurer ist als ein Übergang von einem Wert ungleich Null zu einem anderen Wert ungleich Null (das Auflisten einer zuvor eingetragenen Verbindung in der nächsten Transaktion).  
  
-   **SQL_DTC_UNENLIST_EXPENSIVE**, wenn festgelegt, impliziert, dass der Übergang ungleich Null auf Null erheblich teurer ist als die Verwendung einer Verbindung, deren SQL_ATTR_ENLIST_IN_DTC Attribut bereits auf Null festgelegt ist.  
  
 Es gibt einen Leistungs-im-Vergleich mit der Verbindungsnutzung. Wenn ein Treiber angibt, dass einer oder mehrere dieser Übergänge teuer sind, reagiert der Verbindungspooler des Treiber-Managers darauf, indem er mehr Verbindungen im Pool behält. Einige der Verbindungen im Pool werden für die nicht transaktionale Verwendung bevorzugt, und einige werden für die Transaktion bevorzugt. Wenn der Treiber jedoch angibt, dass diese Übergänge nicht teuer sind, können weniger Verbindungen verwendet werden, was möglicherweise zwischen nicht transaktionaler und transaktionaler Verwendung erfolgt.  
  
 Treiber, die SQL_ATTR_ENLIST_IN_DTC nicht unterstützen, müssen SQL_DTC_TRANSITION_COST nicht unterstützen. Für Treiber, die SQL_ATTR_ENLIST_IN_DTC, aber nicht SQL_DTC_TRANSITION_COST unterstützen, wird davon ausgegangen, dass die Übergänge nicht teuer sind, als ob der Treiber 0 (keine Bits gesetzt) für diesen Wert zurückgegeben hätte.  
  
 Obwohl SQL_DTC_TRANSITION_COST in ODBC 3.5 eingeführt wurde, wurde ein ODBC 2 eingeführt. *x-Treiber* können es auch unterstützen, da der Treiber-Manager diese Informationen unabhängig von der Treiberversion abfragt.  
  
### <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel weist eine Anwendung Umgebungs- und Verbindungshandles zu. Anschließend stellt es eine Verbindung mit der SalesOrders-Datenquelle mit der Benutzer-ID JohnS und dem Kennwort Sesame her und verarbeitet Daten. Wenn die Verarbeitung von Daten abgeschlossen ist, trennt sie die Verbindung zur Datenquelle und gibt die Handles frei.  
  
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
|Zuweisen eines Griffs|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Ermitteln und Aufzählen von Werten, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Trennen der Verbindung zu einer Datenquelle|[SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungszeichenfolge oder ein Dialogfeld|[SQLDriveConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Zurückgeben der Einstellung eines Verbindungsattributs|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Festlegen eines Verbindungsattributs|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
