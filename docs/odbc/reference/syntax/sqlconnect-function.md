---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 530a5acf9cc7c0de375906279aff2bc6a05ec8a0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259525"
---
# <a name="sqlconnect-function"></a>SQLConnect-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLConnect** stellt Verbindungen einen Treiber zu einer Datenquelle her. Das Verbindungs-Handle verweist auf Speicher, der alle Informationen über die Verbindung mit der Datenquelle, einschließlich Status, Transaktionsstatus und Fehlerinformationen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 [Eingabe] Datenquellenname. Daten können sich auf demselben Computer wie die Anwendung oder auf einem anderen Computer an einer beliebigen Stelle in einem Netzwerk sein. Weitere Informationen dazu, wie eine Anwendung eine Datenquelle wählt, finden Sie unter [Auswählen einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Eingabe] Länge der **ServerName* in Zeichen.  
  
 *UserName*  
 [Eingabe] Benutzer-ID.  
  
 *NameLength2*  
 [Eingabe] Länge der **Benutzername* in Zeichen.  
  
 *Authentifizierung*  
 [Eingabe] Zeichenfolge zur cloudauthentifizierung (in der Regel das Kennwort).  
  
 *NameLength3*  
 [Eingabe] Länge der **Authentifizierung* in Zeichen.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLConnect** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_DBC und *behandeln* von *ConnectionHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLConnect** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber nicht den angegebenen Wert, der die *ValuePtr* -Argument in **SQLSetConnectAttr** und einen ähnlichen Wert ersetzt. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08001|Client kann keine Verbindung herstellen.|Der Treiber konnte nicht zum Herstellen einer Verbindung mit der Datenquelle.|  
|08002|Name der Verbindung verwendet|(DM) der angegebenen *ConnectionHandle* hatte bereits zum Herstellen einer Verbindung mit einer Datenquelle und die Verbindung weiterhin geöffnet wurde oder der Benutzer besucht wurde, für eine Verbindung verwendet wurde.|  
|08004|Der Server wies die Verbindung|Die Datenquelle die Herstellung der Verbindung festzulegenden Gründen zurückgewiesen Implementierung definiert.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, zu der der Treiber versucht hat, die Verbindung, konnte nicht vor der Verarbeitung für die Funktion abgeschlossen.|  
|28000|Ungültige Autorisierungsangabe|Der angegebene Wert für das Argument *Benutzername* oder der Wert für das Argument angegebene *Authentifizierung* verletzt die Einschränkungen, die von der Datenquelle definiert.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber-Managers (DM) wurde, kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *ConnectionHandle*. Die **SQLConnect** Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) aufgerufen wurde, auf die *ConnectionHandle*, und klicken Sie dann die **SQLConnect** Funktion wurde erneut aufgerufen, auf die *ConnectionHandle*.<br /><br /> Or **SQLConnect** Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancelHandle** aufgerufen wurde, auf die *ConnectionHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *ConnectionHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) für Argument angegebene Wert *NameLength1*, *NameLength2*, oder *NameLength3* war kleiner als 0, aber nicht SQL_NTS gleich.<br /><br /> (DM) für Argument angegebene Wert *NameLength1* überschreitet die maximale Länge für einen Datenquellennamen ein.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Abfragetimeout abgelaufen, bevor Sie die Verbindung mit der Datenquelle abgeschlossen. Das Timeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT.|  
|HY114|Verbindung auf asynchrone Ausführung der unterstützt Treiber nicht.|(DM) aktiviert die Anwendung den asynchronen Vorgang auf dem Verbindungshandle vor dem Herstellen der Verbindung. Allerdings unterstützt der Treiber nicht asynchroner Vorgänge auf dem Verbindungshandle.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber, der Name der Datenquelle anhand der Funktion nicht unterstützt.|  
|IM002|Datenquelle wurde nicht gefunden und kein Standardtreiber angegeben|(DM) der Name der Datenquelle im Argument angegebene *ServerName* wurde nicht gefunden, in den Systeminformationen, noch gab es eine Standard-Treiber-Spezifikation.|  
|IM003|Angegebene Treiber konnte keine Verbindung hergestellt werden|(DM) der Treiber aufgeführt, in den Daten Quellspezifikation in den Systeminformationen wurde nicht gefunden oder konnte nicht mit einem anderen Grund verbunden werden.|  
|IM004|Fehler beim des Treibers SQLAllocHandle auf SQL_HANDLE_ENV auf.|(DM) während der **SQLConnect**, der Treiber-Manager Namens des Treibers **SQLAllocHandle** -Funktion mit einem *HandleType* SQL_HANDLE_ENV und der Treiber hat einen Fehler zurückgegeben.|  
|IM005|Fehler beim des Treibers SQLAllocHandle auf SQL_HANDLE_DBC auf.|(DM) während der **SQLConnect**, der Treiber-Manager Namens des Treibers **SQLAllocHandle** -Funktion mit einem *HandleType* SQL_HANDLE_DBC auf, und der Treiber hat einen Fehler zurückgegeben.|  
|IM006|Fehler des Treibers SQLSetConnectAttr|Während der **SQLConnect**, der Treiber-Manager Namens des Treibers **SQLSetConnectAttr** -Funktion und der Treiber hat einen Fehler zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|IM009|Keine Verbindung zum Konvertierungs-DLL|Der Treiber konnte keine Verbindung mit dem Konvertierungs-DLL, die für die Datenquelle angegeben wurde.|  
|IM010|Der Datenquellenname ist zu lang.|(DM)  *\*ServerName* wurde länger als SQL_MAX_DSN_LENGTH Zeichen.|  
|IM014|Der angegebene DSN enthält einen architekturkonflikt zwischen dem Treiber und der Anwendung|(DM)-32-Bit-Anwendung verwendet einen DSN Herstellen einer Verbindung mit einer 64-Bit-Treiber. oder umgekehrt.|  
|IM015|Fehler des Treibers SQLConnect auf SQL_HANDLE_DBC_INFO_HANDLE|Ein Treiber SQL_ERROR zurück, der Treiber-Manager für die Anwendung SQL_ERROR zurück, und die Verbindung schlägt fehl.<br /><br /> Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN, finden Sie unter [Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
|S1118|Asynchrone Benachrichtigung unterstützt Treiber nicht.|Wenn der Treiber die asynchrone Benachrichtigung nicht unterstützt, können nicht Sie SQL_ATTR_ASYNC_DBC_EVENT oder SQL_ATTR_ASYNC_DBC_RETCODE_PTR festlegen.|  
  
## <a name="comments"></a>Kommentare  
 Informationen dazu, warum eine Anwendung verwendet **SQLConnect**, finden Sie unter [Herstellen einer Verbindung mit SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md).  
  
 Der Treiber-Manager keine Verbindung zu einem Treiber, bis die Anwendung eine Funktion aufruft (**SQLConnect**, **SQLDriverConnect**, oder **SQLBrowseConnect**) zum Herstellen einer Verbindung mit dem Treiber. Bis zu diesem Zeitpunkt wird der Treiber-Manager arbeitet mit eigenen Handles und Verbindungsinformationen verwaltet. Wenn die Anwendung eine Verbindungsfunktion aufruft, überprüft der Treiber-Manager, ob ein Treiber derzeit mit, für den angegebenen verbunden ist *ConnectionHandle*:  
  
-   Wenn ein Treiber nicht mit verbunden ist, verbindet sich der Treiber-Manager auf die Treiber und der Aufrufe **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_ENV auf, **SQLAllocHandle** mit einer *HandleType* SQL_HANDLE_DBC auf, **SQLSetConnectAttr** (wenn die Anwendung Verbindungsattribute angegeben), und die Verbindungsfunktion im Treiber. Der Treiber-Manager gibt SQLSTATE IM006 (des Treibers **SQLSetConnectOption** Fehler) und SQL_SUCCESS_WITH_INFO für die Verbindungsfunktion, wenn der Treiber einen Fehler für zurückgegeben **SQLSetConnectAttr**. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md).  
  
-   Wenn der angegebene Treiber bereits verbunden ist, auf die *ConnectionHandle*, der Treiber-Manager ruft nur die Verbindungsfunktion im Treiber. In diesem Fall der Treiber muss sicherstellen, dass alle Verbindungen für die Attribute der *ConnectionHandle* verwalten Sie ihre aktuellen Einstellungen.  
  
-   Wenn Sie ein anderen Treiber mit verbunden ist, ruft der Treiber-Manager **SQLFreeHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, und klicken Sie dann, wenn keine anderen Treiber mit in dieser Umgebung verbunden ist, ruft es **SQLFreeHandle** mit einem *HandleType* SQL_HANDLE_ENV auf, in der verbundenen Treiber, und klicken Sie dann diesen Treiber die Verbindung trennt. Es führt dann die gleichen Vorgänge wie wenn ein Treiber nicht mit verbunden ist.  
  
 Der Treiber dann weist Handles und initialisiert sich selbst.  
  
 Wenn die Anwendung ruft **SQLDisconnect**, die Treiber-Manager ruft **SQLDisconnect** im Treiber. Den Treiber werden jedoch nicht getrennt. Dadurch wird den Treiber, im Arbeitsspeicher für Anwendungen, die wiederholt Herstellen einer Verbindung mit einer Datenquelle trennen. Wenn die Anwendung ruft **SQLFreeHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, ruft der Treiber-Manager **SQLFreeHandle** mit einer *HandleType*  SQL_HANDLE_DBC auf, und klicken Sie dann **SQLFreeHandle** mit einer *HandleType* SQL_HANDLE_ENV auf, im Treiber, und klicken Sie dann trennt den Treiber.  
  
 Eine ODBC-Anwendung kann mehr als eine Verbindung herzustellen.  
  
## <a name="driver-manager-guidelines"></a>Treiber-Manager-Richtlinien  
 Der Inhalt der **ServerName* beeinflussen, wie der Treiber-Manager und einen Treiber zusammenarbeiten, um eine Verbindung mit einer Datenquelle herzustellen.  
  
-   Wenn \* *ServerName* enthält einen gültigen Namen der Datenquelle der Treiber-Manager sucht nach der Angabe der entsprechenden Datenquelle in den Systeminformationen und eine Verbindung mit der zugehörigen Treiber. Der Treiber-Manager übergibt jedes **SQLConnect** Argument an den Treiber.  
  
-   Wenn der Name der Datenquelle nicht gefunden werden kann oder *ServerName* ist ein null-Zeiger der Treiber-Manager sucht nach der Angabe der standardmäßigen Datenquelle und eine Verbindung mit der zugehörigen Treiber. Der Treiber-Manager übergibt, an den Treiber die *Benutzername* und *Authentifizierung* Argumente, die unverändert, und "Standard" für die *ServerName* Argument.  
  
-   Wenn die *ServerName* Argument ist "DEFAULT" und der Treiber-Manager sucht nach der Angabe der standardmäßigen Datenquelle eine Verbindung mit der zugehörigen Treiber. Der Treiber-Manager übergibt jedes **SQLConnect** Argument an den Treiber.  
  
-   Wenn der Name der Datenquelle nicht gefunden werden kann oder *ServerName* ist ein null-Zeiger und dem Standard-datenquellenspezifikation ist nicht vorhanden, die der Treiber-Manager gibt SQL_ERROR mit SQLSTATE IM002 (Data source Name wurde nicht gefunden und kein Standardwert Treiber angegeben).  
  
 Nachdem er mit vom Treiber-Manager verbunden ist, kann ein Treiber suchen der entsprechenden Data Source-Spezifikation in den Systeminformationen und treiberspezifische Informationen aus der Spezifikation verwenden, um einen Satz von erforderlichen Verbindungsinformationen abzuschließen.  
  
 Wenn eine Standardbibliothek für die Übersetzung in die Systeminformationen für die Datenquelle angegeben wird, der Treiber eine Verbindung damit her. Einer anderen übersetzungsbibliothek mit verbunden werden kann, durch den Aufruf **SQLSetConnectAttr** mit dem SQL_ATTR_TRANSLATE_LIB-Attribut. Eine Übersetzungsoption kann angegeben werden, durch den Aufruf **SQLSetConnectAttr** mit dem SQL_ATTR_TRANSLATE_OPTION-Attribut.  
  
 Wenn ein Treiber unterstützt **SQLConnect**, muss der Treiber-Schlüsselwort Teil die Systeminformationen für den Treiber enthalten die **ConnectFunctions** Schlüsselwortgruppe mit dem ersten Zeichen in "Y".  
  
### <a name="connection-pooling"></a>Verbindungspooling  
 Verbindungspooling ermöglicht einer Anwendung, die eine Verbindung wiederzuverwenden, die bereits erstellt wurde. Wenn Verbindungspooling aktiviert ist und **SQLConnect** aufgerufen wurde, versucht der Treiber-Manager zum Herstellen der Verbindung über eine Verbindung, die Teil eines Pools von Verbindungen in einer Umgebung, die für das Verbindungspooling festgelegt wurde. Diese Umgebung kann es sich um eine freigegebene Umgebung, die von allen Anwendungen verwendet wird, die Verbindungen im Pool zu verwenden.  
  
 Verbindungs-pooling aktiviert ist, bevor die Umgebung, durch den Aufruf zugeordnet wird **SQLSetEnvAttr** SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER (der maximal einen Pool pro Treiber angegeben ist) oder SQL_CP_ONE_PER_HENV festlegen (maximal einen Pool pro Umgebung gibt). **SQLSetEnvAttr** wird in diesem Fall mit aufgerufen *EnvironmentHandle* auf Null gesetzt, wodurch dem Attribut ein Attribut auf Prozessebene. Wenn SQL_ATTR_CONNECTION_POOLING SQL_CP_OFF festgelegt ist, ist das Verbindungspooling deaktiviert.  
  
 Nachdem der Verbindungs-pooling aktiviert wurde, **SQLAllocHandle** mit einer *HandleType* SQL_HANDLE_ENV auf, wird aufgerufen, um eine Umgebung zuzuweisen. Die Umgebung, die durch diesen Aufruf zugeordnet ist einer freigegebenen Umgebung aus, da Verbindungspooling aktiviert ist. Die Umgebung, die verwendet werden, wird jedoch nicht bestimmt, bis **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, aufgerufen wird.  
  
 **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, wird aufgerufen, um eine Verbindung zu reservieren. Der Treiber-Manager versucht, eine vorhandene freigegebene Umgebung zu finden, die festlegen, indem die Anwendung Umgebungsattribute entspricht. Wenn keine Umgebung dieser Art vorhanden ist, wird eine erstellt, wie ein impliziter *freigegebenen Umgebung*. Wenn eine übereinstimmende freigegebene Umgebung gefunden wird, das Umgebungshandle an die Anwendung zurückgegeben, und dessen Verweiszähler erhöht wird.  
  
 Die Verbindung, die verwendet werden, wird jedoch nicht bestimmt, bis **SQLConnect** aufgerufen wird. An diesem Punkt versucht der Treiber-Manager auf eine vorhandene Verbindung im Verbindungspool zu suchen, die die Kriterien, die von der Anwendung angeforderten entspricht ein. Diese Kriterien umfassen, die im Aufruf angeforderten Verbindungsoptionen **SQLConnect** (die Werte der *ServerName*, *Benutzername*, und  *Authentifizierung* Schlüsselwörter) und Verbindungsattribute festgelegt werden, da **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, aufgerufen wurde. Der Treiber-Manager prüft diese Kriterien für die entsprechenden Verbindungsschlüsselwörter und Attribute in der Verbindungen im Pool. Wenn eine Übereinstimmung gefunden wird, wird die Verbindung im Pool verwendet. Wenn keine Übereinstimmung gefunden wird, wird eine neue Verbindung erstellt.  
  
 Wenn umgebungsattributs SQL_ATTR_CP_MATCH auf SQL_CP_STRICT_MATCH festgelegt ist, muss die Übereinstimmung für eine Verbindung im Pool zu verwendende genaue sein. Wenn umgebungsattributs SQL_ATTR_CP_MATCH auf SQL_CP_RELAXED_MATCH festgelegt ist, wird die Verbindung im Aufruf von Optionen **SQLConnect** überein, aber nicht alle Verbindungsattribute müssen übereinstimmen.  
  
 Die folgenden Regeln werden angewendet, wenn ein Verbindungsattribut als Satz von der Anwendung vor dem **SQLConnect** aufgerufen wird, das die Verbindung im Pool-Verbindungsattribut stimmt nicht überein:  
  
-   Wenn das Verbindungsattribut festgelegt werden muss, bevor die Verbindung hergestellt wird:  
  
     Wenn SQL_ATTR_CP_MATCH SQL_CP_STRICT_MATCH ist, müssen SQL_ATTR_PACKET_SIZE in die zusammengeführte Verbindung mit dem Attribut, das von der Anwendung festgelegte identisch sein. Wenn SQL_CP_RELAXED_MATCH, die Werte der SQL_ATTR_PACKET_SIZE unterschiedlich sein können.  
  
     Der Wert des SQL_ATTR_LOGIN_VALUE wirkt sich nicht auf die Übereinstimmung aus.  
  
-   Wenn das Verbindungsattribut festgelegt werden kann, bevor oder nachdem die Verbindung hergestellt wird:  
  
     Wenn das Verbindungsattribut nicht von der Anwendung festgelegt wurde, aber für die Verbindung im Pool festgelegt wurde und es ein Standardwert ist, wird das Verbindungsattribut in die zusammengeführte Verbindung wieder auf den Standardwert festgelegt ist, und es wird eine Übereinstimmung deklariert. Wenn kein Standardwert angegeben ist, wird die zusammengeführte Verbindung kein übereinstimmend angesehen.  
  
     Wenn das Verbindungsattribut von der Anwendung festgelegt wurde, jedoch nicht für die Verbindung im Pool festgelegt wurde wurde, wird das Verbindungsattribut für den Pool in diesem Satz von der Anwendung geändert, und es wird eine Übereinstimmung deklariert.  
  
     Wenn das Verbindungsattribut von der Anwendung festgelegt wurde, und wurde auch für die Verbindung im Pool festgelegt wurde, aber die Werte abweichen voneinander, wird der Wert des Verbindungsattributs der Anwendung wird verwendet, und eine Übereinstimmung wird deklariert.  
  
-   Wenn die Werte der treiberspezifische Verbindungsattribute nicht identisch sind und SQL_ATTR_CP_MATCH auf SQL_CP_STRICT_MATCH festgelegt ist, wird die Verbindung im Pool nicht verwendet werden.  
  
 Wenn die Anwendung ruft **SQLDisconnect** So trennen Sie die Verbindung an den Verbindungspool zurückgegeben werden soll, und für die Wiederverwendung verfügbar wird.  
  
### <a name="optimizing-connection-pooling-performance"></a>Optimieren der Leistung für Verbindungspooling  
 Bei verteilte Transaktionen beteiligt sind, ist es möglich, Optimieren der Leistung mithilfe von Verbindungspooling **SQL_DTC_TRANSITION_COST**, dies ist eine Bitmaske SQLUINTEGER. Die genannten Übergänge sind Übergänge des Verbindungsattributs SQL_ATTR_ENLIST_IN_DTC Weg vom Wert 0 zu ungleich NULL, und umgekehrt. Dies ist eine Verbindung von nicht in einer verteilten Transaktion eingetragen eingetragen in einer verteilten Transaktion (und umgekehrt). Abhängig davon, wie der Treiber Eintragung (Einstellung Verbindungsattribut SQL_ATTR_ENLIST_IN_DTC) implementiert ist wird diese Übergänge können sehr speicherintensiv sein und sollte daher vermieden werden, für eine optimale Leistung.  
  
 Der vom Treiber zurückgegebene Wert enthält eine beliebige Kombination der folgenden Bits:  
  
-   **SQL_DTC_ENLIST_EXPENSIVE**, wenn festgelegt, bedeutet das 0 (null) für den Übergang von ungleich NULL ist deutlich teurer als eine Umstellung von ungleich Null auf einen anderen Wert ungleich Null (eine zuvor eingetragene Verbindung in der nächsten Transaktion eintragen).  
  
-   **SQL_DTC_UNENLIST_EXPENSIVE**, wenn festgelegt, wird impliziert, die ungleich NULL, NULL Übergang ist deutlich teurer als die Verwendung einer Verbindungs, dessen Attribut SQL_ATTR_ENLIST_IN_DTC bereits auf 0 (null) festgelegt ist.  
  
 Es gibt eine Leistung und Nutzung Nachteil der Verbindung. Wenn der Treiber gibt an, dass eine oder mehrere dieser Übergänge teuer, antwortet Verbindungspoolfunktion des Treiber-Managers zu diesem bleiben mehr Verbindungen im Pool. Einige der Verbindungen im Pool werden bevorzugt, für die Verwendung des nicht transaktionalen, und einige sind der bevorzugte transaktional. Jedoch, wenn der Treiber gibt an, dass diese Übergänge nicht teuer sind, können weniger Verbindungen verwendet werden möglicherweise nicht transaktionalen und transaktionale Verwendung abwechselnd.  
  
 Treiber, die keine SQL_ATTR_ENLIST_IN_DTC unterstützen müssen nicht SQL_DTC_TRANSITION_COST zu unterstützen. Für die Treiber, die SQL_ATTR_ENLIST_IN_DTC lauten, aber nicht SQL_DTC_TRANSITION_COST unterstützen, wird davon ausgegangen, dass das geht nicht viel Leistung beanspruchen, als ob der Treiber auf 0 (keine festgelegten Bits) für diesen Wert zurückgegeben werden.  
  
 Obwohl SQL_DTC_TRANSITION_COST in einer ODBC 2. ODBC 3.5 eingeführt wurde. *x* Treiber kann ebenfalls unterstützt, da der Treiber-Manager diese Informationen unabhängig von der Version des Treibers abgefragt wird.  
  
### <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel ordnet die Anwendung umgebungs- und Handles. Klicken Sie dann eine Verbindung mit der Datenquelle "SalesOrders" mit dem Benutzer-ID an der JohnS und das Kennwort Sesame her, und verarbeitet Daten. Wenn sie mit dem Verarbeiten von Daten abgeschlossen hat, trennt die Verbindung aus der Datenquelle und die Handles frei.  
  
```  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ein Handle zuordnen|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Ermitteln und Aufzählen von Werten, die für die Verbindung mit einer Datenquelle|[SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Trennen von einer Datenquelle|[SQLDisconnect-Funktion](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle mit einer Zeichenfolge oder eines Dialogfelds Verbindungsdialogfeld|[SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Die Einstellung ein Verbindungsattribut zurückgeben|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Ein Verbindungsattribut festlegen|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
