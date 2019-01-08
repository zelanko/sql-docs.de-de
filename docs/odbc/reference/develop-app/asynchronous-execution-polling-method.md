---
title: Asynchrone Ausführung (Abrufmethode) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 8ca0a5094e40f13aef4b4f87d5642e51e7a9b765
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52523444"
---
# <a name="asynchronous-execution-polling-method"></a>Asynchrone Ausführung (Abrufmethode)
Vor der ODBC 3.8 und der Windows 7-SDK waren asynchrone Vorgänge nur auf Anweisung Funktionen zulässig. Weitere Informationen finden Sie unter den **Anweisung-Vorgänge asynchron ausführen**weiter unten in diesem Thema.  
  
 ODBC 3.8 im Windows 7 SDK wurde die asynchrone Ausführung von Vorgängen mit Verbindungen eingeführt. Weitere Informationen finden Sie unter den **Verbindung-Vorgänge asynchron ausführen** weiter unten in diesem Thema.  
  
 In der Windows 7-SDK für asynchrone-Anweisung oder Verbindungsvorgängen sendet bestimmt eine Anwendung an, dass der asynchrone Vorgang abgeschlossen ist, verwenden der Abrufmethode war. Ab Windows 8 SDK, können Sie feststellen, dass ein asynchroner Vorgang abgeschlossen ist, verwenden die Benachrichtigungsmethode ist. Weitere Informationen finden Sie unter [asynchrone Ausführung (Benachrichtigungsmethode)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 Standardmäßig werden Treiber ODBC-Funktionen synchron; also die Anwendung ruft eine Funktion, und der Treiber ist keine Steuerung erst zurück, an die Anwendung Ausführung der Funktion abgeschlossen wurde. Einige Funktionen können jedoch asynchron ausgeführt werden; d. h. die Anwendung ruft die Funktion, und die Treiber nach der minimale Verarbeitung übergibt die Steuerung an die Anwendung. Die Anwendung kann dann andere Funktionen aufrufen, während die erste Funktion noch ausgeführt wird.  
  
 Asynchrone Ausführung wird unterstützt, für die meisten Funktionen, die zum größten Teil der Datenquelle ausgeführt werden, wie z. B. die Funktionen zum Herstellen von Verbindungen, Vorbereiten und Ausführen von SQL-Anweisungen, Abrufen von Metadaten, Daten abzurufen und commit der Transaktionen. Es ist besonders hilfreich, wenn die Aufgabe ausgeführt wird, für die Datenquelle sehr lange, wie z. B. einen Anmeldeprozess oder eine komplexe Abfrage in einer großen Datenbank dauert.  
  
 Wenn die Anwendung ausgeführt, eine Funktion mit einer Anweisung oder die Verbindung, die für die asynchrone Verarbeitung aktiviert ist wird, der Treiber führt eine minimale Menge an Verarbeitungstyp (z. B. überprüfen die Argumente für Fehler), übergibt die Verarbeitung an die Datenquelle und gibt zurück die Steuerung an die Anwendung mit dem Rückgabecode SQL_STILL_EXECUTING. Die Anwendung führt anschließend andere Aufgaben. Um zu bestimmen, wenn die asynchrone Funktion abgeschlossen ist, fragt die Anwendung den Treiber in regelmäßigen Abständen durch Aufrufen der Funktion mit den gleichen Argumenten wie ursprünglich verwendet ab. Wenn die Funktion weiterhin ausgeführt wird, gibt sie SQL_STILL_EXECUTING zurück. Wenn sie die Ausführung beendet hat, wird der Code, den er es synchron ausgeführt worden, wie SQL_SUCCESS oder SQL_ERROR SQL_NEED_DATA zurückgegeben. zurückgegeben hätte zurückgegeben.  
  
 Gibt an, ob eine Funktion synchron oder asynchron ausgeführt wird, ist treiberspezifisch. Nehmen wir beispielsweise an die resultsetmetadaten im Treiber zwischengespeichert wird. In diesem Fall nur sehr wenig Zeit für die Ausführung dauert **SQLDescribeCol** und der Treiber sollte einfach die Funktion ausführen, statt künstlich Ausführung verzögern. Andererseits, wenn der Treiber zum Abrufen der Metadaten aus der Datenquelle muss, sollte zurückgegeben werden Steuerelement an die Anwendung während sie dies erreicht. Die Anwendung muss daher einen anderen Rückgabecode als SQL_STILL_EXECUTING verarbeiten, wenn sie zunächst eine Funktion asynchron ausgeführt wird.  
  
## <a name="executing-statement-operations-asynchronously"></a>Anweisung Vorgänge asynchron ausführen  
 Die folgenden Funktionen für die Anweisung für eine Datenquelle verwendet werden und können asynchron ausgeführt werden:  
  
||||  
|-|-|-|  
|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 Asynchrone Ausführung wird auf einer pro-Anweisung oder einer Basis pro Verbindung abhängig von der Datenquelle gesteuert. Das heißt, gibt die Anwendung nicht, dass eine bestimmte Funktion wird asynchron ausgeführt werden, aber jede Funktion, die für eine bestimmte Anweisung ausgeführt wird, die asynchron ausgeführt werden. Um finden ausgecheckt wird die wird unterstützt, eine Anwendung ruft [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) mit einer Option zur SQL_ASYNC_MODE. SQL_AM_CONNECTION wird zurückgegeben, wenn Verbindungsebene asynchrone Ausführung (für ein Anweisungshandle) unterstützt wird. SQL_AM_STATEMENT, wenn auf Anweisungsebene asynchrone Ausführung unterstützt wird.  
  
 Um anzugeben, dass Funktionen, die mit einer bestimmten Anweisung ausgeführt werden, werden asynchron, ruft die Anwendung ausgeführt **SQLSetStmtAttr** mit der SQL_ATTR_ASYNC_ENABLE Attribut, und legt es auf SQL_ASYNC_ENABLE_ON. Wenn die asynchrone Verarbeitung Verbindungsebene unterstützt wird, das SQL_ATTR_ASYNC_ENABLE-Anweisungsattribut ist schreibgeschützt und sein Wert ist identisch mit der Verbindungszeichenfolge-Attribut der Verbindung auf der die Anweisung zugewiesen wurde. Es ist treiberspezifisch gibt an, ob der Wert des Attributs Anweisung zum Zeitpunkt Zuordnung oder höher festgelegt ist. Beim Festlegen wird zurückgegeben, wird SQL_ERROR und SQLSTATE HYC00 (optionales Feature nicht implementiert).  
  
 Um anzugeben, dass Funktionen, die mit einer bestimmten Verbindung ausgeführt werden, werden asynchron, ruft die Anwendung ausgeführt **SQLSetConnectAttr** mit der SQL_ATTR_ASYNC_ENABLE Attribut, und legt es auf SQL_ASYNC_ENABLE_ON. Alle zukünftigen Anweisungshandles zugeordnet, die für die Verbindung werden für die asynchrone Ausführung aktiviert sein. Es ist treiberdefinierten, ob vorhandene Anweisungshandles durch diese Aktion aktiviert werden. Wenn SQL_ATTR_ASYNC_ENABLE auf SQL_ASYNC_ENABLE_OFF festgelegt ist, wird für alle Anweisungen für die Verbindung im synchronen Modus. Wenn die asynchrone Ausführung aktiviert ist, es gibt zwar eine aktive Anweisung für die Verbindung ein Fehler zurückgegeben.  
  
 Um die maximale Anzahl der aktiven gleichzeitigen Anweisungen im asynchronen Modus zu bestimmen, die der Treiber auf eine bestimmte Verbindung unterstützt, die Anwendung ruft **SQLGetInfo** mit der Option SQL_MAX_ASYNC_CONCURRENT_STATEMENTS.  
  
 Der folgende Code veranschaulicht die Funktionsweise des Modells abrufen:  
  
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
  
 Während eine Funktion asynchron ausgeführt wird, kann Funktionen von die Anwendung auf allen anderen Anweisungen aufrufen. Die Anwendung kann auch Funktionen über eine Verbindung mit Ausnahme des verknüpft ist, mit der asynchronen-Anweisung aufrufen. Aber die Anwendung kann nur aufrufen, die ursprüngliche Funktion und die folgenden Funktionen (mit das Anweisungshandle oder die zugehörige Verbindung, Umgebungshandle), nach einer Anweisung gibt SQL_STILL_EXECUTING:  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (über das Anweisungshandle)  
  
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
  
 Wenn die Anwendung auf eine beliebige Funktion mit der asynchronen-Anweisung oder die Verbindung mit dieser Anweisung verknüpfte aufruft, wird die Funktion gibt SQLSTATE HY010 (Funktion Sequenzfehler), z. B.  
  
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
  
 Wenn eine Anwendung, eine Funktion aufruft, um festzustellen, ob er immer noch asynchron ausgeführt wird, müssen sie das ursprüngliche Anweisungshandle verwenden. Dies ist, da die asynchrone Ausführung auf einer Basis pro Anweisung nachverfolgt wird. Die Anwendung muss auch gültige Werte für die anderen Argumente angeben: die ursprünglichen Argumente erfolgt – rufen Sie nach fehlerüberprüfung im Treiber-Manager. Nachdem der Treiber das Anweisungshandle überprüft und feststellt, dass die Anweisung asynchron ausgeführt wird, ignoriert sie jedoch alle anderen Argumente an.  
  
 Während eine Funktion asynchron - ausgeführt wird, also nachdem es SQL_STILL_EXECUTING zurückgegeben hat, und vor der Rückgabe eines anderen Codes - Anwendung kann Abbrechen durch Aufrufen von **SQLCancel** oder **SQLCancelHandle** mit dem gleichen Anweisungshandle. Dies ist nicht garantiert, zum Abbrechen der Ausführung. Z. B. die Funktion möglicherweise bereits abgeschlossen haben. Darüber hinaus der Code zurückgegebenes **SQLCancel** oder **SQLCancelHandle** gibt nur an, ob der Versuch, kündigen die Funktion erfolgreich war, nicht nur, ob es sich tatsächlich um die Funktion abgebrochen. Um zu bestimmen, ob die Funktion abgebrochen wurde, ruft die Anwendung die Funktion erneut aus. Wenn die Funktion abgebrochen wurde, gibt SQL_ERROR zurück, und SQLSTATE HY008 (der Vorgang wurde abgebrochen). Wenn die Funktion nicht abgebrochen wurde, wird eine andere Code, z. B. SQL_STILL_EXECUTING, SQL_SUCCESS oder SQL_ERROR mit einem anderen SQLSTATE zurückgegeben.  
  
 Deaktivieren Sie asynchrone Ausführung einer bestimmten Anweisung aus, wenn der Treiber auf Anweisungsebene asynchronen Verarbeitung können die Anwendung ruft unterstützt **SQLSetStmtAttr** mit der SQL_ATTR_ASYNC_ENABLE Attribut, und legt es auf SQL_ ASYNC_ENABLE_OFF. Wenn der Treiber auf Verbindungsebene, die asynchrone Verarbeitung unterstützt, die Anwendung ruft **SQLSetConnectAttr** um SQL_ATTR_ASYNC_ENABLE auf SQL_ASYNC_ENABLE_OFF, festzulegen, die deaktiviert die asynchrone Ausführung aller Anweisungen auf der die Verbindung.  
  
 Die Anwendung sollte in der sich wiederholenden Schleife der ursprünglichen Funktion DiagnoseDatensätze verarbeiten. Wenn **SQLGetDiagField** oder **SQLGetDiagRec** wird aufgerufen, wenn es sich bei eine asynchrone Funktion ausgeführt wird, wird die aktuelle Liste der DiagnoseDatensätze zurückgegeben. Jedes Mal, wenn der ursprünglichen Funktionsaufruf wiederholt wird, löscht er die vorherigen DiagnoseDatensätze.  
  
## <a name="executing-connection-operations-asynchronously"></a>Verbindungsvorgänge der asynchron ausgeführt wird  
 Zugelassen Sie vor der ODBC 3.8 asynchrone Ausführung wurde, für Vorgänge im Zusammenhang mit-Anweisung wie z. B. vorbereiten, führen Sie aus und abzurufen Sie, sowie für Vorgänge mit Metadaten Katalog. In ODBC 3.8 ab ist asynchrone Ausführung auch möglich, dass die Verbindung datenbezogene Vorgänge, die etwa wie eine Verbindung herstellen, trennen, Commit und Rollback.  
  
 Weitere Informationen zu ODBC 3.8, finden Sie unter [Neuigkeiten in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 Verbindungsvorgänge der asynchron ausgeführt wird, ist in den folgenden Szenarien nützlich:  
  
-   Wenn eine kleine Anzahl von Threads für eine große Anzahl von Geräten mit sehr hohen Datenraten verwaltet. Um die Reaktionsfähigkeit und Skalierbarkeit zu maximieren, ist es wünschenswert, dass alle Vorgänge asynchron sein müssen.  
  
-   Wenn Sie überlappen von Datenbankvorgängen über mehrere Verbindungen verstrichene Übertragungszeiten reduzieren möchten.  
  
-   Aktivieren eine Anwendung, die dem Benutzer ermöglichen, alle langsamen Vorgang abbrechen, ohne zu warten, Timeouts, effiziente asynchrone ODBC-Aufrufe sowie die Möglichkeit, Verbindungsvorgänge abzubrechen.  
  
 Die folgenden Funktionen, die auf Verbindungshandles angewendet werden, können nun asynchron ausgeführt werden:  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Um zu bestimmen, ob ein Treiber asynchroner Vorgänge auf diese Funktionen unterstützt, eine Anwendung ruft **SQLGetInfo** mit SQL_ASYNC_DBC_FUNCTIONS. SQL_ASYNC_DBC_CAPABLE wird zurückgegeben, wenn asynchrone Vorgänge unterstützt werden. SQL_ASYNC_DBC_NOT_CAPABLE wird zurückgegeben, wenn asynchrone Vorgänge nicht unterstützt werden.  
  
 Um anzugeben, dass Funktionen, die mit einer bestimmten Verbindung ausgeführt werden, werden asynchron, ruft die Anwendung ausgeführt **SQLSetConnectAttr** und legt das SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE-Attribut auf SQL_ASYNC_DBC_ENABLE _EIN. Festlegen von ein Verbindungsattribut vor dem Herstellen einer Verbindung immer synchron ausgeführt. Darüber hinaus der Vorgang, der die Verbindung festlegen SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE mit Attribut **SQLSetConnectAttr** immer synchron ausgeführt.  
  
 Eine Anwendung kann asynchrone Operation vor dem Herstellen einer Verbindung ermöglichen. Da der Treiber-Manager die Treiber zu verwenden, bevor Sie eine Verbindung herstellen nicht bestimmen kann, gibt der Treiber-Manager immer erfolgreich in zurück **SQLSetConnectAttr**. Allerdings wird eventuell eine Verbindung herstellen, wenn der ODBC-Treiber keine asynchrone Vorgänge unterstützt.  
  
 Im Allgemeinen kann gibt es höchstens eine, die asynchrone Ausführung der Funktion eine bestimmte Verbindungshandle oder Anweisungshandle zugeordnet sind. Allerdings kann ein Verbindungshandle mehr als eine zugeordnete Anweisung ausführen zu lassen. Ist kein asynchroner Vorgang, der auf dem Verbindungshandle ausführen, kann ein Handle für die zugeordnete Anweisung einen asynchronen Vorgang ausführen. Auf ähnliche Weise haben Sie einen asynchronen Vorgang für ein Verbindungshandle, wenn es keine asynchronen Vorgänge in Bearbeitung auf alle zugeordneten Anweisungshandle sind. Ein Versuch zum Ausführen eines asynchronen Vorgangs mit der ein Handle, das gerade einen asynchronen Vorgang ausgeführt wird, gibt HY010, "Fehler bei Funktionssequenz" zurück.  
  
 Wenn ein Verbindungsvorgang SQL_STILL_EXECUTING zurückgibt, kann eine Anwendung nur die ursprüngliche Funktion und die folgenden Funktionen für diese Verbindungshandle aufrufen:  
  
-   **SQLCancelHandle** (auf dem Verbindungshandle)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **SQLAllocHandle** (Zuordnen von ENV/DBC)  
  
-   **SQLAllocHandleStd** (Zuordnen von ENV/DBC)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 Die Anwendung sollte in der sich wiederholenden Schleife der ursprünglichen Funktion DiagnoseDatensätze verarbeiten. Wenn beim Ausführen einer asynchronen Funktion SQLGetDiagField oder SQLGetDiagRec aufgerufen wird, wird die aktuelle Liste der DiagnoseDatensätze zurückgegeben. Jedes Mal, wenn der ursprünglichen Funktionsaufruf wiederholt wird, löscht er die vorherigen DiagnoseDatensätze.  
  
 Wenn eine Verbindung wird geöffnet, oder asynchron geschlossen, der Vorgang ist abgeschlossen, wenn die Anwendung im ursprünglichen Funktionsaufruf SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO empfängt.  
  
 ODBC 3.8, wurde eine neue Funktion hinzugefügt **SQLCancelHandle**. Diese Funktion bricht ab, die sechs Verbindungsfunktionen (**SQLBrowseConnect**, **SQLConnect**, **SQLDisconnect**, **SQLDriverConnect**, **SQLEndTran**, und **SQLSetConnectAttr**). Es sollte eine Anwendung aufrufen **SQLGetFunctions** zu bestimmen, ob der Treiber unterstützt **SQLCancelHandle**. Wie bei **SQLCancel**, wenn **SQLCancelHandle** Erfolg zurückgegeben wird, bedeutet dies nicht der Vorgang wurde abgebrochen. Eine Anwendung sollte die ursprüngliche Funktion erneut aus, um zu bestimmen, ob der Vorgang abgebrochen wurde, aufrufen. **SQLCancelHandle** können Sie die asynchrone Vorgänge für Verbindungshandles oder Anweisungshandles Abbrechen. Mithilfe von **SQLCancelHandle** Handle zum Abbrechen eines Vorgangs in einer Anweisung ist der gleiche wie das Aufrufen **SQLCancel**.  
  
 Es ist nicht erforderlich, um beide unterstützen **SQLCancelHandle** und asynchrone Verbindungsvorgänge zur gleichen Zeit. Ein-Treiber unterstützt asynchrone Verbindungsvorgängen sendet, nicht jedoch **SQLCancelHandle**, oder umgekehrt.  
  
 Asynchrone Verbindungsvorgänge und **SQLCancelHandle** kann auch verwendet werden, die von ODBC 3.x und ODBC 2.x-Anwendungen mit einer ODBC 3.8-Treiber und der ODBC 3.8-Treiber-Manager. Informationen zum Aktivieren der einer älteren Anwendung auf die neuen Funktionen in höheren ODBC-Version zu verwenden, finden Sie unter [Matrix der Sperrenkompatibilität](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Verbindungspooling  
 Wenn Verbindungspooling aktiviert ist, werden asynchrone Vorgänge nur minimal zum Herstellen einer Verbindung unterstützt (mit **SQLConnect** und **SQLDriverConnect**) und schließen eine Verbindung mit **SQLDisconnect**. Eine Anwendung sollte können jedoch weiterhin den Rückgabewert SQL_STILL_EXECUTING behandelt **SQLConnect**, **SQLDriverConnect**, und **SQLDisconnect**.  
  
 Wenn Verbindungspooling aktiviert ist, **SQLEndTran** und **SQLSetConnectAttr** für asynchrone Vorgänge unterstützt werden.  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Description  
 Das folgende Beispiel zeigt, wie Sie mit **SQLSetConnectAttr** zum Aktivieren asynchroner Ausführung für die Verbindung in Zusammenhang stehende Funktionen.  
  
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
  
### <a name="description"></a>Description  
 Dieses Beispiel zeigt die asynchroner Commit-Vorgängen. Rollback-Operationen können auch auf diese Weise erfolgen.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von ODBC-Anweisungen](../../../odbc/reference/develop-app/executing-statements-odbc.md)
