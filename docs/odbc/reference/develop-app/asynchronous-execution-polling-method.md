---
title: Asynchrone Ausführung (Polling-Methode) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- asynchronous execution [ODBC]
ms.assetid: 8cd21734-ef8e-4066-afd5-1f340e213f9c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca7b3d5fa16be44bf4c2ef8f8df8953ae081235d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293400"
---
# <a name="asynchronous-execution-polling-method"></a>Asynchrone Ausführung (Abrufmethode)
Vor ODBC 3.8 und dem Windows 7 SDK waren asynchrone Vorgänge nur für Anweisungsfunktionen zulässig. Weitere Informationen finden Sie im Weiteren Umsteigen der **Ausführenvon Anweisungsoperationen Asynchron**.  
  
 ODBC 3.8 im Windows 7 SDK führte eine asynchrone Ausführung für verbindungsbezogene Vorgänge ein. Weitere Informationen finden Sie im Abschnitt **Asynchrones Ausführen von Verbindungsvorgängen** weiter unten in diesem Thema.  
  
 Im Windows 7 SDK hat eine Anwendung für asynchrone Anweisungs- oder Verbindungsvorgänge festgestellt, dass der asynchrone Vorgang mithilfe der Abrufmethode abgeschlossen wurde. Ab dem Windows 8 SDK können Sie mithilfe der Benachrichtigungsmethode feststellen, dass ein asynchroner Vorgang abgeschlossen ist. Weitere Informationen finden Sie unter [Asynchrone Ausführung (Benachrichtigungsmethode)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 Standardmäßig führen Treiber ODBC-Funktionen synchron aus. Das heißt, die Anwendung ruft eine Funktion auf, und der Treiber gibt die Steuerung erst an die Anwendung zurück, wenn er die Ausführung der Funktion abgeschlossen hat. Einige Funktionen können jedoch asynchron ausgeführt werden. Das heißt, die Anwendung ruft die Funktion auf, und der Treiber gibt nach minimaler Verarbeitung die Steuerung an die Anwendung zurück. Die Anwendung kann dann andere Funktionen aufrufen, während die erste Funktion noch ausgeführt wird.  
  
 Die asynchrone Ausführung wird für die meisten Funktionen unterstützt, die größtenteils in der Datenquelle ausgeführt werden, z. B. die Funktionen zum Herstellen von Verbindungen, vorbereiten und ausführen von SQL-Anweisungen, Abrufen von Metadaten, Abrufen von Daten und Committransaktionen. Dies ist besonders nützlich, wenn die Aufgabe, die auf der Datenquelle ausgeführt wird, lange dauert, z. B. ein Anmeldeprozess oder eine komplexe Abfrage für eine große Datenbank.  
  
 Wenn die Anwendung eine Funktion mit einer Anweisung oder Verbindung ausführt, die für die asynchrone Verarbeitung aktiviert ist, führt der Treiber eine minimale Verarbeitungsmenge (z. B. das Überprüfen von Argumenten auf Fehler), die Händeverarbeitung an die Datenquelle aus und gibt die Steuerung an die Anwendung mit dem SQL_STILL_EXECUTING Zurücksendecode zurück. Die Anwendung führt dann andere Aufgaben aus. Um zu bestimmen, wann die asynchrone Funktion beendet ist, fragt die Anwendung den Treiber in regelmäßigen Abständen ab, indem sie die Funktion mit den gleichen Argumenten aufruft, die sie ursprünglich verwendet hat. Wenn die Funktion noch ausgeführt wird, gibt sie SQL_STILL_EXECUTING zurück. Wenn die Ausführung abgeschlossen ist, gibt sie den zurückgegebenen Code zurück, wenn er synchron ausgeführt worden wäre, z. B. SQL_SUCCESS, SQL_ERROR oder SQL_NEED_DATA.  
  
 Ob eine Funktion synchron oder asynchron ausgeführt wird, ist treiberspezifisch. Angenommen, die Metadaten des Resultsets werden im Treiber zwischengespeichert. In diesem Fall dauert es sehr wenig Zeit, **SQLDescribeCol** auszuführen, und der Treiber sollte einfach die Funktion ausführen, anstatt die Ausführung künstlich zu verzögern. Wenn der Treiber hingegen die Metadaten aus der Datenquelle abrufen muss, sollte er die Steuerung an die Anwendung zurückgeben, während er dies tut. Daher muss die Anwendung in der Lage sein, einen anderen Rückgabecode als SQL_STILL_EXECUTING zu behandeln, wenn sie eine Funktion zum ersten Mal asynchron ausführt.  
  
## <a name="executing-statement-operations-asynchronously"></a>Asynchrones Ausführen von Anweisungsvorgängen  
 Die folgenden Anweisungsfunktionen funktionieren auf einer Datenquelle und können asynchron ausgeführt werden:  
  
||||  
|-|-|-|  
|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|['SQLProcedures'](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|['SQLSpecialColumns'](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|['SQLStatistics'](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 Die Ausführung asynchroner Anweisung wird je nach Datenquelle entweder pro Anweisung oder auf Der Verbindungsbasis gesteuert. Das heißt, die Anwendung gibt nicht an, dass eine bestimmte Funktion asynchron ausgeführt werden soll, sondern dass jede Funktion, die für eine bestimmte Anweisung ausgeführt wird, asynchron ausgeführt werden soll. Um herauszufinden, welche Anwendung unterstützt wird, ruft eine Anwendung [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) mit der Option SQL_ASYNC_MODE auf. SQL_AM_CONNECTION wird zurückgegeben, wenn die asynchrone Ausführung auf Verbindungsebene (für ein Anweisungshandle) unterstützt wird. SQL_AM_STATEMENT, wenn die asynchrone Ausführung auf Anweisungsebene unterstützt wird.  
  
 Um anzugeben, dass Funktionen, die mit einer bestimmten Anweisung ausgeführt werden, asynchron ausgeführt werden sollen, ruft die Anwendung **SQLSetStmtAttr** mit dem SQL_ATTR_ASYNC_ENABLE-Attribut auf und legt es auf SQL_ASYNC_ENABLE_ON. Wenn die asynchrone Verarbeitung auf Verbindungsebene unterstützt wird, ist das SQL_ATTR_ASYNC_ENABLE Anweisungsattribut schreibgeschützt, und sein Wert entspricht dem Verbindungsattribut der Verbindung, der die Anweisung zugewiesen wurde. Es ist treiberspezifisch, ob der Wert des Anweisungsattributs zur Verteilungszeit oder später festgelegt wird. Beim Festlegen wird SQL_ERROR und SQLSTATE HYC00 zurückgegeben (Optionale Funktion nicht implementiert).  
  
 Um anzugeben, dass Funktionen, die mit einer bestimmten Verbindung ausgeführt werden, asynchron ausgeführt werden sollen, ruft die Anwendung **SQLSetConnectAttr** mit dem SQL_ATTR_ASYNC_ENABLE-Attribut auf und legt es auf SQL_ASYNC_ENABLE_ON. Alle zukünftigen Anweisungshandles, die für die Verbindung zugewiesen sind, werden für die asynchrone Ausführung aktiviert. Es ist treiberdefiniert, ob vorhandene Anweisungshandles durch diese Aktion aktiviert werden. Wenn SQL_ATTR_ASYNC_ENABLE auf SQL_ASYNC_ENABLE_OFF festgelegt ist, befinden sich alle Anweisungen auf der Verbindung im synchronen Modus. Ein Fehler wird zurückgegeben, wenn die asynchrone Ausführung aktiviert ist, während eine aktive Anweisung für die Verbindung vorhanden ist.  
  
 Um die maximale Anzahl aktiver gleichzeitiger Anweisungen im asynchronen Modus zu bestimmen, die der Treiber für eine bestimmte Verbindung unterstützen kann, ruft die Anwendung **SQLGetInfo** mit der Option SQL_MAX_ASYNC_CONCURRENT_STATEMENTS auf.  
  
 Der folgende Code veranschaulicht, wie das Abrufmodell funktioniert:  
  
```  
SQLHSTMT  hstmt1;  
SQLRETURN rc;  
  
// Specify that the statement is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute a SELECT statement asynchronously.  
while ((rc=SQLExecDirect(hstmt1,"SELECT * FROM Orders",SQL_NTS))==SQL_STILL_EXECUTING) {  
   // While the statement is still executing, do something else.  
   // Do not use hstmt1, because it is being used asynchronously.  
}  
  
// When the statement has finished executing, retrieve the results.  
```  
  
 Während eine Funktion asynchron ausgeführt wird, kann die Anwendung Funktionen für andere Anweisungen aufrufen. Die Anwendung kann auch Funktionen für jede Verbindung aufrufen, mit Ausnahme der, die der asynchronen Anweisung zugeordnet ist. Die Anwendung kann jedoch nur die ursprüngliche Funktion und die folgenden Funktionen (mit dem Anweisungshandle oder der zugehörigen Verbindung, dem Umgebungshandle) aufrufen, nachdem ein Anweisungsvorgang SQL_STILL_EXECUTING zurückgegeben hat:  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (im Anweisungshandle)  
  
-   [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
 Wenn die Anwendung eine andere Funktion mit der asynchronen Anweisung oder mit der dieser Anweisung zugeordneten Verbindung aufruft, gibt die Funktion z. B. SQLSTATE HY010 (Funktionssequenzfehler) zurück.  
  
```  
SQLHDBC       hdbc1, hdbc2;  
SQLHSTMT      hstmt1, hstmt2, hstmt3;  
SQLCHAR *     SQLStatement = "SELECT * FROM Orders";  
SQLUINTEGER   InfoValue;  
SQLRETURN     rc;  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt2);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc2, &hstmt3);  
  
// Specify that hstmt1 is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute hstmt1 asynchronously.  
while ((rc = SQLExecDirect(hstmt1, SQLStatement, SQL_NTS)) == SQL_STILL_EXECUTING) {  
   // The following calls return HY010 because the previous call to  
   // SQLExecDirect is still executing asynchronously on hstmt1. The  
   // first call uses hstmt1 and the second call uses hdbc1, on which  
   // hstmt1 is allocated.  
   SQLExecDirect(hstmt1, SQLStatement, SQL_NTS);   // Error!  
   SQLGetInfo(hdbc1, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // Error!  
  
   // The following calls do not return errors. They use a statement  
   // handle other than hstmt1 or a connection handle other than hdbc1.  
   SQLExecDirect(hstmt2, SQLStatement, SQL_NTS);   // OK  
   SQLTables(hstmt3, NULL, 0, NULL, 0, NULL, 0, NULL, 0);   // OK  
   SQLGetInfo(hdbc2, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // OK  
}  
```  
  
 Wenn eine Anwendung eine Funktion aufruft, um zu bestimmen, ob sie noch asynchron ausgeführt wird, muss sie das ursprüngliche Anweisungshandle verwenden. Dies liegt daran, dass die asynchrone Ausführung pro Anweisung nachverfolgt wird. Die Anwendung muss auch gültige Werte für die anderen Argumente angeben - die ursprünglichen Argumente werden dies tun -, um die Fehlerüberprüfung im Treiber-Manager zu umgehen. Nachdem der Treiber jedoch das Anweisungshandle überprüft und feststellt, dass die Anweisung asynchron ausgeführt wird, werden alle anderen Argumente ignoriert.  
  
 Während eine Funktion asynchron ausgeführt wird, d. h. nachdem sie SQL_STILL_EXECUTING zurückgegeben hat und bevor sie einen anderen Code zurückgibt , kann die Anwendung sie abbrechen, indem sie **SQLCancel** oder **SQLCancelHandle** mit demselben Anweisungshandle aufruft. Dies ist nicht garantiert, um die Funktionsausführung abzubrechen. Die Funktion ist z. B. möglicherweise bereits beendet. Darüber hinaus gibt der von **SQLCancel** oder **SQLCancelHandle** zurückgegebene Code nur an, ob der Versuch, die Funktion abzubrechen, erfolgreich war, und nicht, ob die Funktion tatsächlich abgebrochen wurde. Um festzustellen, ob die Funktion abgebrochen wurde, ruft die Anwendung die Funktion erneut auf. Wenn die Funktion abgebrochen wurde, gibt sie SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen) zurück. Wenn die Funktion nicht abgebrochen wurde, gibt sie einen anderen Code zurück, z. B. SQL_SUCCESS, SQL_STILL_EXECUTING oder SQL_ERROR mit einem anderen SQLSTATE.  
  
 Um die asynchrone Ausführung einer bestimmten Anweisung zu deaktivieren, wenn der Treiber asynchrone Verarbeitung auf Anweisungsebene unterstützt, ruft die Anwendung **SQLSetStmtAttr** mit dem attribut SQL_ATTR_ASYNC_ENABLE auf und legt es auf SQL_ASYNC_ENABLE_OFF. Wenn der Treiber asynchrone Verarbeitung auf Verbindungsebene unterstützt, ruft die Anwendung **SQLSetConnectAttr** auf, um SQL_ATTR_ASYNC_ENABLE auf SQL_ASYNC_ENABLE_OFF festzulegen, wodurch die asynchrone Ausführung aller Anweisungen für die Verbindung deaktiviert wird.  
  
 Die Anwendung sollte Diagnosedatensätze in der wiederholten Schleife der ursprünglichen Funktion verarbeiten. Wenn **SQLGetDiagField** oder **SQLGetDiagRec** aufgerufen wird, wenn eine asynchrone Funktion ausgeführt wird, gibt sie die aktuelle Liste der Diagnosedatensätze zurück. Jedes Mal, wenn der ursprüngliche Funktionsaufruf wiederholt wird, werden frühere Diagnosedatensätze gelöschen.  
  
## <a name="executing-connection-operations-asynchronously"></a>Asynchrones Ausführen von Verbindungsvorgängen  
 Vor ODBC 3.8 war die asynchrone Ausführung für Anweisungsbezogene Vorgänge wie Vorbereiten, Ausführen und Abrufen sowie für Katalogmetadatenvorgänge zulässig. Ab ODBC 3.8 ist die asynchrone Ausführung auch für verbindungsbezogene Vorgänge wie Verbinden, Trennen, Commit und Rollback möglich.  
  
 Weitere Informationen zu ODBC 3.8 finden Sie [unter Neuerungen in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 Das asynchrone Ausführen von Verbindungsvorgängen ist in den folgenden Szenarien nützlich:  
  
-   Wenn eine kleine Anzahl von Threads eine große Anzahl von Geräten mit sehr hohen Datenraten verwaltet. Um die Reaktionsfähigkeit und Skalierbarkeit zu maximieren, ist es wünschenswert, dass alle Vorgänge asynchron sind.  
  
-   Wenn Sie Datenbankvorgänge über mehrere Verbindungen überlappen möchten, um verstrichene Übertragungszeiten zu reduzieren.  
  
-   Effiziente asynchrone ODBC-Aufrufe und die Möglichkeit, Verbindungsvorgänge abzubrechen, ermöglichen es einer Anwendung, einen langsamen Vorgang abzubrechen, ohne auf Timeouts warten zu müssen.  
  
 Folgende Funktionen, die an Verbindungsgriffen ausgeführt werden, können nun asynchron ausgeführt werden:  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Um zu bestimmen, ob ein Treiber asynchrone Vorgänge für diese Funktionen unterstützt, ruft eine Anwendung **SQLGetInfo** mit SQL_ASYNC_DBC_FUNCTIONS auf. SQL_ASYNC_DBC_CAPABLE wird zurückgegeben, wenn asynchrone Vorgänge unterstützt werden. SQL_ASYNC_DBC_NOT_CAPABLE wird zurückgegeben, wenn asynchrone Vorgänge nicht unterstützt werden.  
  
 Um anzugeben, dass Funktionen, die mit einer bestimmten Verbindung ausgeführt werden, asynchron ausgeführt werden sollen, ruft die Anwendung **SQLSetConnectAttr** auf und legt das SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE-Attribut auf SQL_ASYNC_DBC_ENABLE_ON. Das Festlegen eines Verbindungsattributs vor dem Herstellen einer Verbindung wird immer synchron ausgeführt. Außerdem wird das Verbindungsattribut SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE mit **SQLSetConnectAttr** immer synchron ausgeführt.  
  
 Eine Anwendung kann den asynchronen Betrieb aktivieren, bevor eine Verbindung hergestellt wird. Da der Treiber-Manager nicht bestimmen kann, welchen Treiber vor dem Herstellen einer Verbindung verwendet werden soll, gibt der Treiber-Manager immer den Erfolg in **SQLSetConnectAttr**zurück. Es kann jedoch sein, dass eine Verbindung nicht hergestellt werden kann, wenn der ODBC-Treiber keine asynchronen Vorgänge unterstützt.  
  
 Im Allgemeinen kann höchstens eine asynchron ausgeführte Funktion einem bestimmten Verbindungshandle oder Anweisungshandle zugeordnet sein. Ein Verbindungshandle kann jedoch über mehr als ein zugeordnetes Anweisungshandle verfügen. Wenn kein asynchroner Vorgang für das Verbindungshandle ausgeführt wird, kann ein zugeordnetes Anweisungshandle einen asynchronen Vorgang ausführen. Ebenso können Sie einen asynchronen Vorgang für ein Verbindungshandle durchführen, wenn keine asynchronen Vorgänge für ein zugeordnetes Anweisungshandle ausgeführt werden. Bei dem Versuch, einen asynchronen Vorgang mithilfe eines Handles auszuführen, das derzeit einen asynchronen Vorgang ausführt, wird HY010, "Funktionssequenzfehler" zurückgegeben.  
  
 Wenn ein Verbindungsvorgang SQL_STILL_EXECUTING zurückgibt, kann eine Anwendung nur die ursprüngliche Funktion und die folgenden Funktionen für dieses Verbindungshandle aufrufen:  
  
-   **SQLCancelHandle** (im Verbindungshandle)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **SQLAllocHandle** (Zuweisen von ENV/DBC)  
  
-   **SQLAllocHandleStd** (Zuweisen von ENV/DBC)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 Die Anwendung sollte Diagnosedatensätze in der wiederholten Schleife der ursprünglichen Funktion verarbeiten. Wenn SQLGetDiagField oder SQLGetDiagRec aufgerufen wird, wenn eine asynchrone Funktion ausgeführt wird, gibt sie die aktuelle Liste der Diagnosedatensätze zurück. Jedes Mal, wenn der ursprüngliche Funktionsaufruf wiederholt wird, werden frühere Diagnosedatensätze gelöschen.  
  
 Wenn eine Verbindung asynchron geöffnet oder geschlossen wird, wird der Vorgang abgeschlossen, wenn die Anwendung SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO im ursprünglichen Funktionsaufruf empfängt.  
  
 OdBC 3.8, **SQLCancelHandle**, wurde eine neue Funktion hinzugefügt. Diese Funktion bricht die sechs Verbindungsfunktionen ab (**SQLBrowseConnect**, **SQLConnect**, **SQLDisconnect**, **SQLDriverConnect**, **SQLEndTran**und **SQLSetConnectAttr**). Eine Anwendung sollte **SQLGetFunctions** aufrufen, um zu bestimmen, ob der Treiber **SQLCancelHandle**unterstützt. Wie bei **SQLCancel**bedeutet dies nicht, dass der Vorgang abgebrochen wurde, wenn **SQLCancelHandle Erfolg zurückgibt.** Eine Anwendung sollte die ursprüngliche Funktion erneut aufrufen, um festzustellen, ob der Vorgang abgebrochen wurde. **Mit SQLCancelHandle** können Sie asynchrone Vorgänge für Verbindungshandles oder Anweisungshandles abbrechen. Die Verwendung von **SQLCancelHandle** zum Abbrechen eines Vorgangs für ein Anweisungshandle entspricht dem Aufrufen von **SQLCancel**.  
  
 Es ist nicht erforderlich, sowohl **SQLCancelHandle** als auch asynchrone Verbindungsvorgänge gleichzeitig zu unterstützen. Ein Treiber kann asynchrone Verbindungsvorgänge unterstützen, jedoch nicht **SQLCancelHandle**oder umgekehrt.  
  
 Asynchrone Verbindungsvorgänge und **SQLCancelHandle** können auch von ODBC 3.x- und ODBC 2.x-Anwendungen mit odBC 3.8-Treiber und ODBC 3.8-Treiber-Manager verwendet werden. Informationen dazu, wie Sie einer älteren Anwendung die Verwendung neuer Features in einer späteren ODBC-Version ermöglichen, finden Sie unter [Kompatibilitätsmatrix](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Verbindungspooling  
 Wenn das Verbindungspooling aktiviert ist, werden asynchrone Vorgänge nur minimal unterstützt, um eine Verbindung herzustellen (mit **SQLConnect** und **SQLDriverConnect**) und eine Verbindung mit **SQLDisconnect**zu schließen. Eine Anwendung sollte jedoch weiterhin in der Lage sein, den SQL_STILL_EXECUTING Rückgabewert von **SQLConnect**, **SQLDriverConnect**und **SQLDisconnect**zu verarbeiten.  
  
 Wenn das Verbindungspooling aktiviert ist, werden **SQLEndTran** und **SQLSetConnectAttr** für asynchrone Vorgänge unterstützt.  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt, wie **Sie SQLSetConnectAttr** verwenden, um die asynchrone Ausführung für verbindungsbezogene Funktionen zu aktivieren.  
  
### <a name="code"></a>Code  
  
```  
BOOL AsyncConnect (SQLHANDLE hdbc)   
{  
   SQLRETURN r;  
   SQLHANDLE hdbc;  
  
   // Enable asynchronous execution of connection functions.  
   // This must be executed synchronously, that is r != SQL_STILL_EXECUTING  
   r = SQLSetConnectAttr(  
         hdbc,   
         SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE,  
         reinterpret_cast<SQLPOINTER> (SQL_ASYNC_DBC_ENABLE_ON),  
         0);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   TCHAR szConnStrIn[256] = _T("DSN=AsyncDemo");  
  
   r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
  
   if (r == SQL_ERROR)   
   {  
      // Use SQLGetDiagRec to process the error.  
      // If SQLState is HY114, the driver does not support asynchronous execution.  
      return FALSE;  
   }  
  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion, with the same set of arguments.  
      r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   return TRUE;  
}  
  
```  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Dieses Beispiel zeigt asynchrone Commitvorgänge. Rollbackvorgänge können auch auf diese Weise durchgeführt werden.  
  
### <a name="code"></a>Code  
  
```  
BOOL AsyncCommit ()   
{  
   SQLRETURN r;   
  
   // Assume that SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE is SQL_ASYNC_DBC_ENABLE_ON.  
  
   r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion with the same set of arguments.  
      r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Anweisungen ODBC](../../../odbc/reference/develop-app/executing-statements-odbc.md)
