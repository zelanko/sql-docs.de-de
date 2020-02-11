---
title: Asynchrone Ausführung (Abruf Methode) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97fe8af6f02e9797bc14578edda09c420f8f94e2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077051"
---
# <a name="asynchronous-execution-polling-method"></a>Asynchrone Ausführung (Abrufmethode)
Vor ODBC 3,8 und dem Windows 7 SDK waren asynchrone Vorgänge nur für Anweisungs Funktionen zulässig. Weitere Informationen finden Sie unter **asynchrone Vorgänge der Ausführung**von Anweisungen weiter unten in diesem Thema.  
  
 ODBC 3,8 im Windows 7 SDK führte die asynchrone Ausführung für verbindungsbezogene Vorgänge ein. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt **asynchrones Ausführen von Verbindungs Vorgängen** .  
  
 Im Windows 7 SDK hat eine Anwendung für asynchrone Anweisungs-oder Verbindungs Vorgänge festgestellt, dass der asynchrone Vorgang mit der Abruf Methode durchgeführt wurde. Ab dem Windows 8 SDK können Sie mithilfe der Benachrichtigungs Methode ermitteln, ob ein asynchroner Vorgang fertiggestellt ist. Weitere Informationen finden Sie unter [asynchrone Ausführung (Benachrichtigungs Methode)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 Standardmäßig werden ODBC-Funktionen von Treibern synchron ausgeführt. Dies bedeutet, dass die Anwendung eine Funktion aufruft und der Treiber die Steuerung erst dann an die Anwendung zurückgibt, wenn die Ausführung der Funktion abgeschlossen ist. Einige Funktionen können jedoch asynchron ausgeführt werden. Das heißt, die Anwendung ruft die-Funktion auf, und der Treiber gibt nach minimaler Verarbeitung die Steuerung an die Anwendung zurück. Die Anwendung kann dann andere Funktionen aufzurufen, während die erste Funktion noch ausgeführt wird.  
  
 Die asynchrone Ausführung wird für die meisten Funktionen unterstützt, die größtenteils in der Datenquelle ausgeführt werden, wie z. b. die Funktionen zum Herstellen von Verbindungen, vorbereiten und Ausführen von SQL-Anweisungen, Abrufen von Metadaten, Abrufen von Daten und committransaktionen. Dies ist besonders hilfreich, wenn der Task, der für die Datenquelle ausgeführt wird, lange Zeit benötigt, z. b. ein Anmeldevorgang oder eine komplexe Abfrage für eine große Datenbank.  
  
 Wenn die Anwendung eine Funktion mit einer-Anweisung oder-Verbindung ausführt, die für die asynchrone Verarbeitung aktiviert ist, führt der Treiber einen minimalen Verarbeitungsaufwand aus (z. b. das Überprüfen von Argumenten auf Fehler), die Verarbeitung der Datenquelle und die Rückgabe von Steuern Sie die Anwendung mit dem SQL_STILL_EXECUTING Rückgabecode. Die Anwendung führt dann andere Aufgaben aus. Um zu ermitteln, wann die asynchrone Funktion abgeschlossen wurde, ruft die Anwendung den Treiber in regelmäßigen Abständen ab, indem die Funktion mit denselben Argumenten aufgerufen wird, die ursprünglich verwendet wurde. Wenn die Funktion noch ausgeführt wird, wird SQL_STILL_EXECUTING zurückgegeben. Wenn die Ausführung abgeschlossen ist, wird der Code zurückgegeben, der zurückgegeben wurde, wenn er synchron ausgeführt wurde, z. b. SQL_SUCCESS, SQL_ERROR oder SQL_NEED_DATA.  
  
 Ob eine Funktion synchron oder asynchron ausgeführt wird, ist Treiber spezifisch. Nehmen wir beispielsweise an, dass die Resultsetmetadaten im Treiber zwischengespeichert werden. In diesem Fall dauert die Ausführung von **SQLDescribeCol** sehr wenig Zeit, und der Treiber sollte die Funktion einfach ausführen, anstatt die Ausführung künstlich zu verzögern. Wenn der Treiber dagegen die Metadaten aus der Datenquelle abrufen muss, sollte er die Steuerung an die Anwendung zurückgeben. Daher muss die Anwendung einen anderen Rückgabecode als SQL_STILL_EXECUTING verarbeiten können, wenn Sie eine Funktion zum ersten Mal asynchron ausführt.  
  
## <a name="executing-statement-operations-asynchronously"></a>Asynchrones Ausführen von Anweisungs Operationen  
 Die folgenden-Anweisungs Funktionen arbeiten auf einer Datenquelle und können asynchron ausgeführt werden:  
  
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
  
 Die asynchrone Anweisungs Ausführung wird abhängig von der Datenquelle entweder für eine pro-Anweisung oder eine Verbindungs Basis gesteuert. Das heißt, die Anwendung gibt an, dass eine bestimmte Funktion nicht asynchron ausgeführt werden soll, aber dass jede Funktion, die für eine bestimmte Anweisung ausgeführt wird, asynchron ausgeführt werden soll. Um herauszufinden, welche unterstützt wird, ruft eine Anwendung [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) mit der Option SQL_ASYNC_MODE auf. SQL_AM_CONNECTION wird zurückgegeben, wenn die asynchrone Ausführung auf Verbindungs Ebene (für ein Anweisungs Handle) unterstützt wird. SQL_AM_STATEMENT, wenn die asynchrone Ausführung auf Anweisungs Ebene unterstützt wird.  
  
 Um anzugeben, dass Funktionen, die mit einer bestimmten Anweisung ausgeführt werden, asynchron ausgeführt werden sollen, ruft die Anwendung **SQLSetStmtAttr** mit dem SQL_ATTR_ASYNC_ENABLE-Attribut auf, und legt Sie auf SQL_ASYNC_ENABLE_ON fest. Wenn die asynchrone Verarbeitung auf Verbindungs Ebene unterstützt wird, ist das SQL_ATTR_ASYNC_ENABLE-Anweisungs Attribut schreibgeschützt, und sein Wert ist identisch mit dem Verbindungs Attribut der Verbindung, für die die-Anweisung zugewiesen wurde. Es ist Treiber spezifisch, ob der Wert des Anweisungs Attributs zur Anweisungs Zuordnungs Zeit oder später festgelegt wird. Wenn Sie versuchen, diese festzulegen, wird SQL_ERROR und SQLSTATE HYC00 (optionales Feature nicht implementiert) zurückgegeben.  
  
 Um anzugeben, dass Funktionen, die mit einer bestimmten Verbindung ausgeführt werden, asynchron ausgeführt werden sollen, ruft die Anwendung **SQLSetConnectAttr** mit dem SQL_ATTR_ASYNC_ENABLE-Attribut auf, und legt Sie auf SQL_ASYNC_ENABLE_ON fest. Alle zukünftigen Anweisungs Handles, die der Verbindung zugeordnet sind, werden für die asynchrone Ausführung aktiviert. Es ist Treiber definiert, ob vorhandene Anweisungs Handles durch diese Aktion aktiviert werden. Wenn SQL_ATTR_ASYNC_ENABLE auf SQL_ASYNC_ENABLE_OFF festgelegt ist, befinden sich alle Anweisungen für die Verbindung im synchronen Modus. Ein Fehler wird zurückgegeben, wenn die asynchrone Ausführung aktiviert ist, während eine aktive-Anweisung für die Verbindung vorhanden ist.  
  
 Um die maximale Anzahl aktiver gleichzeitiger Anweisungen im asynchronen Modus zu ermitteln, die der Treiber für eine bestimmte Verbindung unterstützen kann, ruft die Anwendung **SQLGetInfo** mit der SQL_MAX_ASYNC_CONCURRENT_STATEMENTS-Option auf.  
  
 Der folgende Code veranschaulicht die Funktionsweise des Abruf Modells:  
  
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
  
 Während eine Funktion asynchron ausgeführt wird, kann die Anwendung Funktionen für beliebige andere Anweisungen aufzurufen. Die Anwendung kann auch Funktionen für jede Verbindung aufzurufen, mit Ausnahme derjenigen, die der asynchronen-Anweisung zugeordnet ist. Die Anwendung kann jedoch nur die ursprüngliche Funktion und die folgenden Funktionen (mit dem Anweisungs Handle oder der zugehörigen Verbindung, Umgebungs Handle) aufzurufen, nachdem ein Anweisungs Vorgang SQL_STILL_EXECUTING zurückgegeben hat:  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [Sqlcancelhandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (auf dem Anweisungs Handle)  
  
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
  
 Wenn die Anwendung eine andere Funktion mit der asynchronen Anweisung oder mit der Verbindung aufruft, die mit dieser Anweisung verknüpft ist, gibt die Funktion SQLSTATE HY010 (Funktions Sequenz Fehler) zurück, z. b..  
  
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
  
 Wenn eine Anwendung eine Funktion aufruft, um zu bestimmen, ob Sie noch asynchron ausgeführt wird, muss Sie das ursprüngliche Anweisungs Handle verwenden. Der Grund hierfür ist, dass die asynchrone Ausführung pro Anweisung nachverfolgt wird. Die Anwendung muss auch gültige Werte für die anderen Argumente angeben, die die ursprünglichen Argumente verwenden, um die Fehlerüberprüfung im Treiber-Manager zu erhalten. Nachdem der Treiber jedoch das Anweisungs Handle überprüft und ermittelt hat, dass die Anweisung asynchron ausgeführt wird, werden alle anderen Argumente ignoriert.  
  
 Während eine Funktion asynchron ausgeführt wird, d. h. Nachdem Sie SQL_STILL_EXECUTING und vor der Rückgabe eines anderen Codes zurückgegeben hat, kann Sie durch Aufrufen von **SQLCancel** oder **sqlcancelhandle** mit demselben Anweisungs Handle abgebrochen werden. Dadurch wird nicht garantiert, dass die Funktions Ausführung abgebrochen wird. Beispielsweise ist die-Funktion möglicherweise bereits fertig. Außerdem gibt der von **SQLCancel** oder **sqlcancelhandle** zurückgegebene Code nur an, ob der Versuch, die Funktion abzubrechen, erfolgreich war und nicht, ob die Funktion tatsächlich abgebrochen wurde. Um zu ermitteln, ob die Funktion abgebrochen wurde, ruft die Anwendung die Funktion erneut auf. Wenn die Funktion abgebrochen wurde, gibt Sie SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen) zurück. Wenn die Funktion nicht abgebrochen wurde, gibt Sie einen anderen Code zurück, z. b. SQL_SUCCESS, SQL_STILL_EXECUTING oder SQL_ERROR mit einem anderen SQLSTATE.  
  
 Um die asynchrone Ausführung einer bestimmten Anweisung zu deaktivieren, wenn der Treiber die asynchrone Verarbeitung auf Anweisungs Ebene unterstützt, ruft die Anwendung **SQLSetStmtAttr** mit dem SQL_ATTR_ASYNC_ENABLE-Attribut auf und legt Sie auf SQL_ASYNC_ENABLE_OFF fest. Wenn der Treiber die asynchrone Verarbeitung auf Verbindungs Ebene unterstützt, ruft die Anwendung **SQLSetConnectAttr** auf, um SQL_ATTR_ASYNC_ENABLE auf SQL_ASYNC_ENABLE_OFF festzulegen. Dadurch wird die asynchrone Ausführung aller Anweisungen für die Verbindung deaktiviert.  
  
 Die Anwendung sollte Diagnosedaten Sätze in der sich wiederholenden Schleife der ursprünglichen Funktion verarbeiten. Wenn **SQLGetDiagField** oder **SQLGetDiagRec** beim Ausführen einer asynchronen Funktion aufgerufen wird, wird die aktuelle Liste der Diagnosedaten Sätze zurückgegeben. Jedes Mal, wenn der ursprüngliche Funktionsaufruf wiederholt wird, werden vorherige Diagnosedaten Sätze gelöscht.  
  
## <a name="executing-connection-operations-asynchronously"></a>Asynchrones Ausführen von Verbindungs Vorgängen  
 Vor ODBC 3,8 war die asynchrone Ausführung für Anweisungs bezogene Vorgänge (z. b. vorbereiten, ausführen und Abrufen) sowie für Catalog-Metadatenvorgänge zulässig. Ab ODBC 3,8 ist die asynchrone Ausführung auch für verbindungsbezogene Vorgänge möglich, wie z. b. Connect, Disconnect, Commit und Rollback.  
  
 Weitere Informationen zu ODBC 3,8 finden Sie unter [What es New in ODBC 3,8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 Die asynchrone Ausführung von Verbindungs Vorgängen ist in den folgenden Szenarien nützlich:  
  
-   Wenn eine kleine Anzahl von Threads eine große Anzahl von Geräten mit sehr hohen Datenraten verwaltet. Um die Reaktionsfähigkeit und Skalierbarkeit zu maximieren, ist es wünschenswert, dass alle Vorgänge asynchron sind.  
  
-   Wenn Sie Daten Bank Vorgänge über mehrere Verbindungen überlappen möchten, um verstrichene Übertragungszeiten zu verringern.  
  
-   Effiziente asynchrone ODBC-Aufrufe und die Möglichkeit zum Abbrechen von Verbindungs Vorgängen ermöglichen es einer Anwendung, den Benutzern das Abbrechen eines beliebigen langsamen Vorgangs zu gestatten, ohne auf Timeouts warten zu müssen.  
  
 Die folgenden Funktionen, die auf Verbindungs Handles angewendet werden, können jetzt asynchron ausgeführt werden:  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Um zu ermitteln, ob ein Treiber für diese Funktionen asynchrone Vorgänge unterstützt, ruft eine Anwendung **SQLGetInfo** mit SQL_ASYNC_DBC_FUNCTIONS auf. SQL_ASYNC_DBC_CAPABLE wird zurückgegeben, wenn asynchrone Vorgänge unterstützt werden. SQL_ASYNC_DBC_NOT_CAPABLE wird zurückgegeben, wenn asynchrone Vorgänge nicht unterstützt werden.  
  
 Um anzugeben, dass Funktionen, die mit einer bestimmten Verbindung ausgeführt werden, asynchron ausgeführt werden sollen, ruft die Anwendung **SQLSetConnectAttr** auf und legt das SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE-Attribut auf SQL_ASYNC_DBC_ENABLE_ON fest. Das Festlegen eines Verbindungs Attributs vor dem Herstellen einer Verbindung wird immer synchron ausgeführt. Außerdem wird der Vorgang, der das mit **SQLSetConnectAttr** SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE Connection-Attribut festlegt, immer synchron ausgeführt.  
  
 Eine Anwendung kann vor dem Herstellen einer Verbindung einen asynchronen Vorgang aktivieren. Da der Treiber-Manager nicht ermitteln kann, welcher Treiber verwendet werden muss, bevor er eine Verbindung herstellt, gibt der Treiber-Manager in **SQLSetConnectAttr**immer Erfolg zurück. Möglicherweise kann jedoch keine Verbindung hergestellt werden, wenn der ODBC-Treiber keine asynchronen Vorgänge unterstützt.  
  
 Im Allgemeinen kann es höchstens eine asynchron ausgeführte Funktion geben, die einem bestimmten Verbindungs Handle oder Anweisungs Handle zugeordnet ist. Ein Verbindungs Handle kann jedoch mehrere zugeordnete Anweisungs Handles aufweisen. Wenn auf dem Verbindungs Handle kein asynchroner Vorgang ausgeführt wird, kann ein zugeordnetes Anweisungs Handle einen asynchronen Vorgang ausführen. Auf ähnliche Weise können Sie einen asynchronen Vorgang für ein Verbindungs Handle ausführen, wenn für ein zugeordnetes Anweisungs Handle keine asynchronen Vorgänge ausgeführt werden. Wenn Sie versuchen, einen asynchronen Vorgang mit einem Handle auszuführen, das gerade einen asynchronen Vorgang ausführt, wird HY010, "Funktions Sequenz Fehler", zurückgegeben.  
  
 Wenn ein Verbindungsvorgang SQL_STILL_EXECUTING zurückgibt, kann eine Anwendung nur die ursprüngliche Funktion und die folgenden Funktionen für dieses Verbindungs Handle aufzurufen:  
  
-   **Sqlcancelhandle** (auf dem Verbindungs Handle)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **Sqlzuordchandle** (Zuordnung von "en v/DBC")  
  
-   **Sqlzuordchandlestd** (Zuordnung von "en v/DBC")  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 Die Anwendung sollte Diagnosedaten Sätze in der sich wiederholenden Schleife der ursprünglichen Funktion verarbeiten. Wenn SQLGetDiagField oder SQLGetDiagRec beim Ausführen einer asynchronen Funktion aufgerufen wird, wird die aktuelle Liste der Diagnosedaten Sätze zurückgegeben. Jedes Mal, wenn der ursprüngliche Funktionsaufruf wiederholt wird, werden vorherige Diagnosedaten Sätze gelöscht.  
  
 Wenn eine Verbindung asynchron geöffnet oder geschlossen wird, ist der Vorgang abgeschlossen, wenn die Anwendung SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO im ursprünglichen Funktions aufzurufen empfängt.  
  
 ODBC 3,8, **sqlcancelhandle**, wurde eine neue Funktion hinzugefügt. Diese Funktion bricht die sechs Verbindungsfunktionen ab (**sqlbrowseconnetct**, **SQLCONNECT**, **SQLDisconnect**, **SQLDriverConnect**, **SQLEndTran**und **SQLSetConnectAttr**). Eine Anwendung sollte **SQLGetFunctions** aufrufen, um zu bestimmen, ob der Treiber **sqlcancelhandle**unterstützt. Wie bei **SQLCancel**bedeutet dies nicht, dass der Vorgang abgebrochen wurde, wenn **sqlcancelhandle** Erfolg zurückgibt. Eine Anwendung sollte die ursprüngliche Funktion erneut aufzurufen, um zu bestimmen, ob der Vorgang abgebrochen wurde. **Sqlcancelhandle** ermöglicht das Abbrechen von asynchronen Vorgängen für Verbindungs Handles oder Anweisungs Handles. Die Verwendung von **sqlcancelhandle** , um einen Vorgang für ein Anweisungs Handle abzubrechen, entspricht dem Aufrufen von **SQLCancel**.  
  
 Es ist nicht erforderlich, gleichzeitig sowohl **sqlcancelhandle** -als auch asynchronen-Verbindungs Vorgänge zu unterstützen. Ein Treiber kann asynchrone Verbindungs Vorgänge unterstützen, jedoch nicht **sqlcancelhandle**(oder umgekehrt).  
  
 Asynchrone Verbindungs Vorgänge und **sqlcancelhandle** können auch von ODBC 3. x-und ODBC 2. x-Anwendungen mit einem ODBC 3,8-Treiber und ODBC 3,8-Treiber-Manager verwendet werden. Informationen dazu, wie Sie eine ältere Anwendung für die Verwendung neuer Features in einer späteren ODBC-Version aktivieren, finden Sie unter [Kompatibilitäts Matrix](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Verbindungspooling  
 Wenn das Verbindungspooling aktiviert ist, werden asynchrone Vorgänge nur minimal für das Herstellen einer Verbindung (mit **SQLCONNECT** und **SQLDriverConnect**) und das Schließen einer Verbindung mit **SQLDisconnect**unterstützt. Eine Anwendung sollte jedoch weiterhin in der Lage sein, den SQL_STILL_EXECUTING Rückgabewert von **SQLCONNECT**, **SQLDriverConnect**und **SQLDisconnect**zu verarbeiten.  
  
 Wenn das Verbindungspooling aktiviert ist, werden **SQLEndTran** und **SQLSetConnectAttr** für asynchrone Vorgänge unterstützt.  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>BESCHREIBUNG  
 Im folgenden Beispiel wird gezeigt, wie Sie **SQLSetConnectAttr** verwenden, um die asynchrone Ausführung für verbindungsbezogene Funktionen zu aktivieren.  
  
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
  
### <a name="description"></a>BESCHREIBUNG  
 Dieses Beispiel zeigt asynchrone Commit-Vorgänge. Rollback-Vorgänge können auch auf diese Weise ausgeführt werden.  
  
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
 [Ausführen von ODBC-Anweisungen](../../../odbc/reference/develop-app/executing-statements-odbc.md)
