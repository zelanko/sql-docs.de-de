---
title: Asynchrone Ausführung (Benachrichtigungsmethode) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 250e71dcb47d44a6e437d12c269ea23fa6fb3c2c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306411"
---
# <a name="asynchronous-execution-notification-method"></a>Asynchrone Ausführung (Benachrichtigungsmethode)
ODBC ermöglicht die asynchrone Ausführung von Verbindungs- und Anweisungsvorgängen. Ein Anwendungsthread kann eine ODBC-Funktion im asynchronen Modus aufrufen, und die Funktion kann zurückgegeben werden, bevor der Vorgang abgeschlossen ist, sodass der Anwendungsthread andere Aufgaben ausführen kann. Im Windows 7 SDK hat eine Anwendung für asynchrone Anweisungs- oder Verbindungsvorgänge festgestellt, dass der asynchrone Vorgang mithilfe der Abrufmethode abgeschlossen wurde. Weitere Informationen finden Sie unter [Asynchrone Ausführung (Polling-Methode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Ab dem Windows 8 SDK können Sie mithilfe der Benachrichtigungsmethode feststellen, dass ein asynchroner Vorgang abgeschlossen ist.  
  
 In der Abrufmethode müssen Anwendungen die asynchrone Funktion jedes Mal aufrufen, wenn sie den Status des Vorgangs aufrufen möchten. Die Benachrichtigungsmethode ähnelt dem Rückruf und wartet in ADO.NET. ODBC verwendet jedoch Win32-Ereignisse als Benachrichtigungsobjekt.  
  
 Die ODBC-Cursorbibliothek und die asynchrone ODBC-Benachrichtigung können nicht gleichzeitig verwendet werden. Wenn Sie beide Attribute festlegen, wird ein Fehler mit SQLSTATE S1119 zurückgegeben (Cursorlibrary und asynchrone Benachrichtigung können nicht gleichzeitig aktiviert werden).  
  
 Informationen für Treiberentwickler finden Sie unter [Benachrichtigung über den Abschluss asynchroner Funktionen.](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md)  
  
> [!NOTE]  
>  Die Benachrichtigungsmethode wird mit der Cursorbibliothek nicht unterstützt. Eine Anwendung erhält eine Fehlermeldung, wenn sie versucht, die Cursorbibliothek über SQLSetConnectAttr zu aktivieren, wenn die Benachrichtigungsmethode aktiviert ist.  
  
## <a name="overview"></a>Übersicht  
 Wenn eine ODBC-Funktion im asynchronen Modus aufgerufen wird, wird das Steuerelement sofort mit dem Rückgabecode SQL_STILL_EXECUTING an die aufrufende Anwendung zurückgegeben. Die Anwendung muss die Funktion wiederholt abrufen, bis sie etwas anderes als SQL_STILL_EXECUTING zurückgibt. Die Abrufschleife erhöht die CPU-Auslastung, was in vielen asynchronen Szenarien zu einer schlechten Leistung führt.  
  
 Bei jeder Verwendung des Benachrichtigungsmodells wird das Abrufmodell deaktiviert. Anwendungen sollten die ursprüngliche Funktion nicht erneut aufrufen. Rufen Sie [die SQLCompleteAsync-Funktion](../../../odbc/reference/syntax/sqlcompleteasync-function.md) auf, um den asynchronen Vorgang abzuschließen. Wenn eine Anwendung die ursprüngliche Funktion erneut aufruft, bevor der asynchrone Vorgang abgeschlossen ist, gibt der Aufruf SQL_ERROR mit SQLSTATE IM017 zurück (Polling ist im asynchronen Benachrichtigungsmodus deaktiviert).  
  
 Bei Verwendung des Benachrichtigungsmodells kann die Anwendung **SQLCancel** oder **SQLCancelHandle** aufrufen, um eine Anweisung oder einen Verbindungsvorgang abzubrechen. Wenn die Abbruchanforderung erfolgreich ist, gibt ODBC SQL_SUCCESS zurück. Diese Meldung gibt nicht an, dass die Funktion tatsächlich abgebrochen wurde. Es gibt an, dass die Abbruchanforderung verarbeitet wurde. Ob die Funktion tatsächlich abgebrochen wird, ist treiberabhängig und datenquellenabhängig. Wenn ein Vorgang abgebrochen wird, signalisiert der Treiber-Manager weiterhin das Ereignis. Der Treiber-Manager gibt SQL_ERROR im Rückgabecodepuffer zurück, und der Status ist SQLSTATE HY008 (Vorgang abgebrochen), um anzuzeigen, dass die Abbrechenierung erfolgreich ist. Wenn die Funktion die normale Verarbeitung abgeschlossen hat, gibt der Treiber-Manager SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück.  
  
### <a name="downlevel-behavior"></a>Downlevel-Verhalten  
 Die ODBC Driver Manager-Version, die diese Benachrichtigung vollständig unterstützt, ist ODBC 3.81.  
  
|Anwendung ODBC Version|Treiber-Manager-Version|Treiberversion|Verhalten|  
|------------------------------|----------------------------|--------------------|--------------|  
|Neue Anwendung einer beliebigen ODBC-Version|ODBC 3,81|ODBC 3.80 Treiber|Die Anwendung kann diese Funktion verwenden, wenn der Treiber diese Funktion unterstützt, andernfalls wird der Treiber-Manager fehlerfrei.|  
|Neue Anwendung einer beliebigen ODBC-Version|ODBC 3,81|Pre-ODBC 3.80 Treiber|Der Treiber-Manager wird fehlerfrei angezeigt, wenn der Treiber diese Funktion nicht unterstützt.|  
|Neue Anwendung einer beliebigen ODBC-Version|VorODBC 3.81|Any|Wenn die Anwendung diese Funktion verwendet, betrachtet ein alter Treiber-Manager die neuen Attribute als treiberspezifische Attribute, und der Treiber sollte fehlerfrei sein. Ein neuer Treiber-Manager gibt diese Attribute nicht an den Treiber weiter.|  
  
 Eine Anwendung sollte die Treiber-Manager-Version überprüfen, bevor sie diese Funktion verwendet. Andernfalls ist das Verhalten nicht definiert, wenn ein schlecht geschriebener Treiber keinen Fehler auslöst und die Treiber-Manager-Version vor ODBC 3.81 liegt.  
  
## <a name="use-cases"></a>Anwendungsfälle  
 In diesem Abschnitt werden Anwendungsfälle für die asynchrone Ausführung und den Abrufmechanismus angezeigt.  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>Integrieren von Daten aus mehreren ODBC-Quellen  
 Eine Datenintegrationsanwendung ruft daten asynchron aus mehreren Datenquellen ab. Einige der Daten stammen aus Entferntdatenquellen und einige Daten aus lokalen Dateien. Die Anwendung kann erst fortgesetzt werden, wenn die asynchronen Vorgänge abgeschlossen sind.  
  
 Anstatt einen Vorgang wiederholt abzuwählen, um festzustellen, ob er abgeschlossen ist, kann die Anwendung ein Ereignisobjekt erstellen und es einem ODBC-Verbindungshandle oder einem ODBC-Anweisungshandle zuordnen. Die Anwendung ruft dann Betriebssystemsynchronisierungs-APIs auf, um auf ein Ereignisobjekt oder viele Ereignisobjekte (sowohl ODBC-Ereignisse als auch andere Windows-Ereignisse) zu warten. ODBC signalisiert das Ereignisobjekt, wenn der entsprechende asynchrone ODBC-Vorgang abgeschlossen ist.  
  
 Unter Windows werden Win32-Ereignisobjekte verwendet, die dem Benutzer ein einheitliches Programmiermodell bieten. Treiber-Manager auf anderen Plattformen können die für diese Plattformen spezifische Ereignisobjektimplementierung verwenden.  
  
 Das folgende Codebeispiel veranschaulicht die Verwendung von verbindungs- und Anweisungsasynchronbenachrichtigungen:  
  
```  
// This function opens NUMBER_OPERATIONS connections and executes one query on statement of each connection.  
// Asynchronous Notification is used  
  
#define NUMBER_OPERATIONS 5  
int AsyncNotificationSample(void)  
{  
    RETCODE     rc;  
  
    SQLHENV     hEnv              = NULL;  
    SQLHDBC     arhDbc[NUMBER_OPERATIONS]         = {NULL};  
    SQLHSTMT    arhStmt[NUMBER_OPERATIONS]        = {NULL};  
  
    HANDLE      arhDBCEvent[NUMBER_OPERATIONS]    = {NULL};  
    RETCODE     arrcDBC[NUMBER_OPERATIONS]        = {0};  
    HANDLE      arhSTMTEvent[NUMBER_OPERATIONS]   = {NULL};  
    RETCODE     arrcSTMT[NUMBER_OPERATIONS]       = {0};  
  
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &hEnv);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    rc = SQLSetEnvAttr(hEnv,  
        SQL_ATTR_ODBC_VERSION,  
        (SQLPOINTER) SQL_OV_ODBC3_80,  
        SQL_IS_INTEGER);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    // Connection operations begin here  
  
    // Alloc NUMBER_OPERATIONS connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_DBC, hEnv, &arhDbc[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable DBC Async on all connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE, (SQLPOINTER)SQL_ASYNC_DBC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Application must create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhDBCEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhDBCEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all connection handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_EVENT, arhDBCEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate connect establishing  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLDriverConnect(arhDbc[i], NULL, (SQLTCHAR*)TEXT("Driver={ODBC Driver 11 for SQL Server};SERVER=dp-srv-sql2k;DATABASE=pubs;UID=sa;PWD=XYZ;"), SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE); // Wait All  
  
    // Complete connect API calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], & arrcDBC[i]);  
    }  
  
    BOOL fFail = FALSE; // Whether some connection openning fails.  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcDBC[i]) )   
            fFail = TRUE;  
    }  
  
    // If some SQLDriverConnect() fail, clean up.  
    if (fFail)  
    {  
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {  
                SQLDisconnect(arhDbc[i]); // This is also async  
            }  
            else  
            {  
                SetEvent(arhDBCEvent[i]); // Previous SQLDriverConnect() failed. No need to call SQLDisconnect().  
            }  
        }  
        WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE);   
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {     
                SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], &arrcDBC[i]);; // To Complete  
            }  
        }  
  
        goto Cleanup;  
    }  
  
    // Statement Operations begin here  
  
    // Alloc statement handle  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_STMT, arhDbc[i], &arhStmt[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable STMT Async on all statement handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_ENABLE, (SQLPOINTER)SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhSTMTEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhSTMTEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all statement handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_STMT_EVENT, arhSTMTEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate SQLExecDirect() calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLExecDirect(arhStmt[i], (SQLTCHAR*)TEXT("select au_lname, au_fname from authors"), SQL_NTS);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE); // Wait All  
  
    // Now, call SQLCompleteAsync to complete the operation and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return values  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        //Do some binding jobs here, set SQL_ATTR_ROW_ARRAY_SIZE   
    }  
  
    // Now, initiate fetching  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLFetch(arhStmt[i]);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE);   
  
    // Now, to complete the operations and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    // USE fetched data here!!  
  
Cleanup:  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhStmt[NUMBER_OPERATIONS])  
        {  
            SQLFreeHandle(SQL_HANDLE_STMT, arhStmt[i]);  
            arhStmt[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhSTMTEvent[i])  
        {  
            CloseHandle(arhSTMTEvent[i]);  
            arhSTMTEvent[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDbc[i])  
        {  
            SQLFreeHandle(SQL_HANDLE_DBC, arhDbc[i]);  
            arhDbc[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDBCEvent[i])  
        {  
            CloseHandle(arhDBCEvent[i]);  
            arhDBCEvent[i] = NULL;  
        }  
    }  
  
    if (hEnv)  
    {  
        SQLFreeHandle(SQL_HANDLE_ENV, hEnv);  
        hEnv = NULL;  
    }  
  
    return 0;  
}  
  
```  
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>Bestimmen, ob ein Treiber asynchrone Benachrichtigung unterstützt  
 Eine ODBC-Anwendung kann feststellen, ob ein ODBC-Treiber asynchrone Benachrichtigungen unterstützt, indem [sie SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)aufruft. Der ODBC-Treiber-Manager ruft daher die **SQLGetInfo** des Treibers mit SQL_ASYNC_NOTIFICATION auf.  
  
```  
SQLUINTEGER InfoValue;  
SQLLEN      cbInfoLength;  
  
SQLRETURN retcode;  
retcode = SQLGetInfo (hDbc,   
                      SQL_ASYNC_NOTIFICATION,   
                      &InfoValue,  
                      sizeof(InfoValue),  
                      NULL);  
if (SQL_SUCCEEDED(retcode))  
{  
if (SQL_ASYNC_NOTIFICATION_CAPABLE == InfoValue)  
      {  
          // The driver supports asynchronous notification  
      }  
      else if (SQL_ASYNC_NOTIFICATION_NOT_CAPABLE == InfoValue)  
      {  
          // The driver does not support asynchronous notification  
      }  
}  
```  
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Zuordnen eines Win32-Ereignishandles zu einem ODBC-Handle  
 Anwendungen sind für die Erstellung von Win32-Ereignisobjekten mit den entsprechenden Win32-Funktionen verantwortlich. Eine Anwendung kann ein Win32-Ereignishandle einem ODBC-Verbindungshandle oder einem ODBC-Anweisungshandle zuordnen.  
  
 Verbindungsattribute SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE und SQL_ATTR_ASYNC_DBC_EVENT bestimmen, ob ODBC im asynchronen Modus ausgeführt wird und ob ODBC den Benachrichtigungsmodus für ein Verbindungshandle aktiviert. Anweisungsattribute SQL_ATTR_ASYNC_ENABLE und SQL_ATTR_ASYNC_STMT_EVENT bestimmen, ob ODBC im asynchronen Modus ausgeführt wird und ob ODBC den Benachrichtigungsmodus für ein Anweisungshandle aktiviert.  
  
|SQL_ATTR_ASYNC_ENABLE oder SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT oder SQL_ATTR_ASYNC_DBC_EVENT|Mode|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|Aktivieren|nicht-NULL|Asynchrone Benachrichtigung|  
|Aktivieren|NULL|Asynchrones Polling|  
|Disable|any|Synchron|  
  
 Eine Anwendung kann den asynchronen Betriebsmodus vorübergehend deaktivieren. ODBC ignoriert Werte von SQL_ATTR_ASYNC_DBC_EVENT, wenn der asynchrone Vorgang auf Verbindungsebene deaktiviert ist. ODBC ignoriert Werte von SQL_ATTR_ASYNC_STMT_EVENT, wenn der asynchrone Vorgang auf Anweisungsebene deaktiviert ist.  
  
 Synchroner Aufruf von **SQLSetStmtAttr** und **SQLSetConnectAttr**  
 -   **SQLSetConnectAttr** unterstützt asynchrone Vorgänge, aber der Aufruf von **SQLSetConnectAttr** zum Festlegen SQL_ATTR_ASYNC_DBC_EVENT ist immer synchron.  
  
-   **SQLSetStmtAttr** unterstützt keine asynchrone Ausführung.  
  
 Fehlerszenario  
 Wenn **SQLSetConnectAttr** aufgerufen wird, bevor eine Verbindung hergestellt wird, kann der Treiber-Manager nicht bestimmen, welcher Treiber verwendet werden soll. Daher gibt der Treiber-Manager den Erfolg für **SQLSetConnectAttr** zurück, aber das Attribut ist möglicherweise nicht bereit, im Treiber festzulegen. Der Treiber-Manager legt diese Attribute fest, wenn die Anwendung eine Verbindungsfunktion aufruft. Der Treiber-Manager kann fehlerfrei sein, da der Treiber keine asynchronen Vorgänge unterstützt.  
  
 Vererbung von Verbindungsattributen  
 Normalerweise erben die Anweisungen einer Verbindung die Verbindungsattribute. Das Attribut SQL_ATTR_ASYNC_DBC_EVENT ist jedoch nicht vererbbar und wirkt sich nur auf die Verbindungsvorgänge aus.  
  
 Um ein Ereignishandle einem ODBC-Verbindungshandle zuzuordnen, ruft eine ODBC-Anwendung ODBC-API **SQLSetConnectAttr** auf und gibt SQL_ATTR_ASYNC_DBC_EVENT als Attribut und das Ereignishandle als Attributwert an. Das neue ODBC-Attribut SQL_ATTR_ASYNC_DBC_EVENT ist vom Typ SQL_IS_POINTER.  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 Normalerweise erstellen Anwendungen Ereignisobjekte für das automatische Zurücksetzen. ODBC setzt das Ereignisobjekt nicht zurück. Anwendungen müssen sicherstellen, dass sich das Objekt nicht im signalisierten Zustand befindet, bevor asynchrone ODBC-Funktionen aufgerufen werden.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT ist ein Nur-Treiber-Attribut, das nicht im Treiber festgelegt wird.  
  
 Der Standardwert von SQL_ATTR_ASYNC_DBC_EVENT ist NULL. Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, gibt das Abrufen oder Festlegen SQL_ATTR_ASYNC_DBC_EVENT SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück.  
  
 Wenn der letzte SQL_ATTR_ASYNC_DBC_EVENT Wert, der für ein ODBC-Verbindungshandle festgelegt wurde, nicht NULL ist und der asynchrone Modus der Anwendung durch Festlegen des Attributs SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE mit SQL_ASYNC_DBC_ENABLE_ON festgelegt wird, erhält das Aufrufen einer ODBC-Verbindungsfunktion, die den asynchronen Modus unterstützt, eine Abschlussbenachrichtigung. Wenn der letzte SQL_ATTR_ASYNC_DBC_EVENT Wert für ein ODBC-Verbindungshandle NULL ist, sendet ODBC der Anwendung keine Benachrichtigung, unabhängig davon, ob der asynchrone Modus aktiviert ist.  
  
 Eine Anwendung kann SQL_ATTR_ASYNC_DBC_EVENT vor oder nach dem Festlegen des Attributs festlegen, SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE.  
  
 Anwendungen können das SQL_ATTR_ASYNC_DBC_EVENT-Attribut für ein ODBC-Verbindungshandle festlegen, bevor sie eine Verbindungsfunktion aufrufen (**SQLConnect**, **SQLBrowseConnect**oder **SQLDriverConnect**). Da der ODBC-Treiber-Manager nicht weiß, welchen ODBC-Treiber die Anwendung verwenden wird, gibt er SQL_SUCCESS zurück. Wenn die Anwendung eine Verbindungsfunktion aufruft, überprüft der ODBC-Treiber-Manager, ob der Treiber asynchrone Benachrichtigungen unterstützt. Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, gibt der ODBC-Treiber-Manager SQL_ERROR mit SQLSTATE-S1_118 zurück (Driver unterstützt keine asynchrone Benachrichtigung). Wenn der Treiber asynchrone Benachrichtigungen unterstützt, ruft der ODBC-Treiber-Manager den Treiber auf und legt die entsprechenden Attribute SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK und SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT fest.  
  
 In ähnlicher Weise ruft eine Anwendung **SQLSetStmtAttr** für ein ODBC-Anweisungshandle auf und gibt das SQL_ATTR_ASYNC_STMT_EVENT-Attribut an, um asynchrone Benachrichtigungen auf Anweisungsebene zu aktivieren oder zu deaktivieren. Da eine Anweisungsfunktion immer aufgerufen wird, nachdem die Verbindung hergestellt wurde, gibt **SQLSetStmtAttr** sofort SQL_ERROR mit SQLSTATE S1_118 (Driver unterstützt keine asynchrone Benachrichtigung) sofort zurück, wenn der entsprechende Treiber keine asynchronen Vorgänge unterstützt oder der Treiber asynchronen Betrieb unterstützt, aber keine asynchrone Benachrichtigung unterstützt.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT, die auf NULL festgelegt werden kann, ist ein Nur-Treiber-Attribut, das nicht im Treiber festgelegt wird.  
  
 Der Standardwert von SQL_ATTR_ASYNC_STMT_EVENT ist NULL. Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, gibt das Abrufen oder Festlegen des SQL_ATTR_ASYNC_ STMT_EVENT-Attributs SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück.  
  
 Eine Anwendung sollte nicht dasselbe Ereignishandle mehr als einem ODBC-Handle zuordnen. Andernfalls geht eine Benachrichtigung verloren, wenn zwei asynchrone ODBC-Funktionsaufrufe für zwei Handles abgeschlossen werden, die dasselbe Ereignishandle verwenden. Um zu vermeiden, dass ein Anweisungshandle dasselbe Ereignishandle vom Verbindungshandle erbt, gibt ODBC SQL_ERROR mit SQLSTATE IM016 zurück (Anweisungsattribut kann nicht in Verbindungshandle festgelegt werden), wenn eine Anwendung SQL_ATTR_ASYNC_STMT_EVENT für ein Verbindungshandle festlegt.  
  
### <a name="calling-asynchronous-odbc-functions"></a>Aufrufen von asynchronen ODBC-Funktionen  
 Nach dem Aktivieren der asynchronen Benachrichtigung und dem Starten eines asynchronen Vorgangs kann die Anwendung jede ODBC-Funktion aufrufen. Wenn die Funktion zu den Funktionen gehört, die den asynchronen Vorgang unterstützen, erhält die Anwendung eine Abschlussbenachrichtigung, wenn der Vorgang abgeschlossen ist, unabhängig davon, ob die Funktion fehlgeschlagen oder erfolgreich war.  Die einzige Ausnahme ist, dass die Anwendung eine ODBC-Funktion mit einem ungültigen Verbindungs- oder Anweisungshandle aufruft. In diesem Fall erhält ODBC den Ereignishandle nicht und setzt es auf den signalisierten Zustand.  
  
 Die Anwendung muss sicherstellen, dass sich das zugeordnete Ereignisobjekt in einem nicht signalisierten Zustand befindet, bevor ein asynchroner Vorgang für das entsprechende ODBC-Handle gestartet wird. ODBC setzt das Ereignisobjekt nicht zurück.  
  
### <a name="getting-notification-from-odbc"></a>Abrufen von Benachrichtigungen von ODBC  
 Ein Anwendungsthread kann **WaitForSingleObject** aufrufen, um auf ein Ereignishandle zu warten, oder **WaitForMultipleObjects** aufrufen, um auf ein Array von Ereignishandles zu warten und angehalten zu werden, bis eines oder alle Ereignisobjekte signalisiert werden oder das Timeoutintervall verstreicht.  
  
```  
DWORD dwStatus = WaitForSingleObject(  
                        hEvent,  // The event associated with the ODBC handle  
                        5000     // timeout is 5000 millisecond   
);  
  
If (dwStatus == WAIT_TIMEOUT)  
{  
    // time-out interval elapsed before all the events are signaled.   
}  
Else  
{  
    // Call the corresponding Asynchronous ODBC API to complete all processing and retrieve the return code.  
}  
```
