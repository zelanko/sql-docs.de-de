---
title: Asynchrone Ausführung (Benachrichtigungsmethode) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 66b806b698164b306eee4dc7d4c48fbe7835adae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077062"
---
# <a name="asynchronous-execution-notification-method"></a>Asynchrone Ausführung (Benachrichtigungsmethode)
ODBC ermöglicht die asynchrone Ausführung der Verbindungs- und Vorgänge der Anweisung. Ein Thread der Anwendung kann eine ODBC-Funktion aufrufen, im asynchronen Modus aus, und die Funktion zurückgeben kann, bevor der Vorgang abgeschlossen ist, ermöglicht dem Thread der Anwendung für andere Aufgaben ist. In der Windows 7-SDK für asynchrone-Anweisung oder Verbindungsvorgängen sendet bestimmt eine Anwendung an, dass der asynchrone Vorgang abgeschlossen ist, verwenden der Abrufmethode war. Weitere Informationen finden Sie unter [asynchrone Ausführung (Methode abrufen)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Ab Windows 8 SDK, können Sie feststellen, dass ein asynchroner Vorgang abgeschlossen ist, verwenden die Benachrichtigungsmethode ist.  
  
 In der Abrufmethode müssen Anwendungen die asynchrone Funktion jedes Mal aufrufen, den Status des Vorgangs werden sollen. Die Benachrichtigungsmethode ist ähnlich wie Rückruf und Wartezeit in ADO.NET. ODBC, verwendet jedoch die Win32-Ereignissen als das Benachrichtigungsobjekt.  
  
 Die ODBC Cursor Library und ODBC asynchrone Benachrichtigung können nicht gleichzeitig verwendet werden. Beide Attribute festlegen, wird ein Fehler mit SQLSTATE S1119 zurückgegeben (Cursor Library und die asynchrone Benachrichtigung kann nicht gleichzeitig aktiviert werden).  
  
 Finden Sie unter [Benachrichtigung der asynchronen Funktion Abschluss](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md) Informationen für Treiberentwickler.  
  
> [!NOTE]  
>  Die Benachrichtigungsmethode wird mit der Cursorbibliothek nicht unterstützt. Eine Anwendung wird die Fehlermeldung angezeigt, wenn es versucht, Cursorbibliothek über SQLSetConnectAttr, aktivieren, wenn die Benachrichtigungsmethode aktiviert ist.  
  
## <a name="overview"></a>Übersicht  
 Wenn eine ODBC-Funktion im asynchronen Modus aufgerufen wird, wird das Steuerelement an die aufrufende Anwendung sofort mit dem Rückgabecode SQL_STILL_EXECUTING zurückgegeben. Die Anwendung muss die Funktion wiederholt abrufen, bis sie einen anderen Wert als SQL_STILL_EXECUTING zurückgibt. Die Abrufschleife steigt die CPU-Auslastung, schlechten Leistung in vielen asynchronen Szenarien verursacht.  
  
 Wenn das Benachrichtigungsmodell verwendet wird, ist das Modell abrufen deaktiviert. Anwendungen sollten die ursprüngliche Funktion nicht erneut aufrufen. Rufen Sie [SQLCompleteAsync-Funktion](../../../odbc/reference/syntax/sqlcompleteasync-function.md) zum Abschließen des asynchronen Vorgangs. Wenn eine Anwendung die ursprüngliche Funktion erneut aufruft, bevor der asynchrone Vorgang abgeschlossen ist, gibt der Aufruf SQL_ERROR mit SQLSTATE IM017 zurück (Abruf im Modus für asynchrone Benachrichtigung deaktiviert ist).  
  
 Wenn Sie das Benachrichtigungsmodell verwenden möchten, kann die Anwendung aufrufen **SQLCancel** oder **SQLCancelHandle** , einen Anweisung oder Verbindung Vorgang abzubrechen. Wenn die Cancel-Anforderung erfolgreich ist, wird ODBC SQL_SUCCESS zurückgegeben. Diese Meldung, nicht dass die Funktion tatsächlich abgebrochen wurde; Er gibt an, dass die Cancel-Anforderung verarbeitet wurde. Gibt an, ob die Funktion tatsächlich abgebrochen wird, ist treiberabhängig und datenquellenabhängig. Wenn ein Vorgang abgebrochen wird, wird der Treiber-Manager immer noch das Ereignis zu signalisieren. Der Treiber-Manager gibt SQL_ERROR zurück, in der Rückgabecode Puffer und der Status ist SQLSTATE HY008 (der Vorgang wurde abgebrochen), um anzugeben, der Abbruchvorgang ist erfolgreich. Wenn die Funktion die normale Verarbeitung abgeschlossen hat, gibt der Treiber-Manager SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück.  
  
### <a name="downlevel-behavior"></a>Verhalten von Vorgängerversionen  
 Die ODBC-Treiber-Manager-Version, die diese Benachrichtigung auf vollständige Unterstützung ist ODBC 3.81.  
  
|ODBC-Version der Anwendung|Treiber-Manager-Version|Treiberversion|Verhalten|  
|------------------------------|----------------------------|--------------------|--------------|  
|Neue Anwendung einer ODBC-version|ODBC 3.81|ODBC 3,80 Treiber|Anwendung kann diese Funktion verwenden, wenn der Treiber dieses Feature unterstützt, andernfalls der Treiber-Manager tritt ein Fehler auf.|  
|Neue Anwendung einer ODBC-version|ODBC 3.81|3,80 Pre-ODBC-Treiber|Der Treiber-Manager tritt ein Fehler auf, wenn der Treiber diese Funktion nicht unterstützt.|  
|Neue Anwendung einer ODBC-version|Pre-ODBC-3.81|Any|Wenn die Anwendung diese Funktion verwendet, einen alten Treiber-Manager werden die neuen Attribute als treiberspezifischen Attribute betrachten, und der Treiber sollte der Fehler ausgegeben. Ein neuer Treiber-Manager werden diese Attribute nicht an den Treiber übergeben werden.|  
  
 Eine Anwendung sollte die Treiber-Manager-Version überprüfen Sie vor Verwendung dieses Features. Andernfalls ist, wenn ein fehlerhaft geschriebener Treiber keine Fehler führt und der Treiber-Manager-Version vor ODBC 3.81, Verhalten undefiniert.  
  
## <a name="use-cases"></a>Anwendungsfälle  
 Dieser Abschnitt zeigt die Anwendungsfälle für die asynchrone Ausführung und der Abrufmechanismus.  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>Integrieren von Daten aus mehreren ODBC-Datenquellen  
 Eine Anwendung für die Datenintegration werden die Daten asynchron aus mehreren Datenquellen abgerufen. Einige der Daten werden von Remotedatenquellen und werden einige Daten aus lokalen Dateien. Die Anwendung kann nicht fortgesetzt, bis die asynchronen Vorgänge abgeschlossen sind.  
  
 Anstatt die Fertigstellung wiederholt eines Vorgangs, um zu bestimmen, ob der Vorgang abgeschlossen ist, kann die Anwendung ein Ereignisobjekt erstellen und mit einer ODBC-Verbindungshandle oder ein ODBC-Anweisungshandle zuordnen. Klicken Sie dann die Anwendung ruft die Betriebssystem-Synchronisierungs-APIs, um auf ein Ereignis oder viele Event-Objekte (ODBC-Ereignisse und andere Windows-Ereignisse) zu warten. ODBC ist das Ereignisobjekt signalisieren, wenn der entsprechende asynchrone ODBC-Vorgang abgeschlossen ist.  
  
 Klicken Sie auf Windows Win32-Objekte verwendet werden, und, wird dem Benutzer ein einheitliches Programmiermodell bereitstellen. Treibermanager auf anderen Plattformen können die Implementierung der Ereignis-Objekt für diese Plattformen verwenden.  
  
 Das folgende Codebeispiel veranschaulicht die Verwendung der Verbindung und asynchrone Benachrichtigung Anweisung:  
  
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
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>Bestimmen, ob ein Treiber unterstützt die asynchrone Benachrichtigung  
 Eine ODBC-Anwendung kann bestimmen, ob es sich bei ein ODBC-Treiber unterstützt die asynchrone Benachrichtigung durch den Aufruf [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md). Der ODBC-Treiber-Manager ruft folglich die **SQLGetInfo** des Treibers mit SQL_ASYNC_NOTIFICATION.  
  
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
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Verknüpfen ein Win32-Ereignishandle mit einer ODBC-Anweisungshandle  
 Anwendungen sind verantwortlich für das Erstellen von Win32-Event-Objekte, die mit den entsprechenden Win32-Funktionen. Eine Anwendung kann eine Win32-Ereignishandle eine ODBC-Verbindungshandle oder eine ODBC-Anweisungshandle zuordnen.  
  
 Verbindungsattribute SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE und SQL_ATTR_ASYNC_DBC_EVENT bestimmen, ob ODBC im asynchronen Modus ausgeführt wird, und gibt an, ob ODBC Benachrichtigungsmodus für ein Verbindungshandle ermöglicht. Anweisungsattribute SQL_ATTR_ASYNC_ENABLE und SQL_ATTR_ASYNC_STMT_EVENT bestimmen, ob ODBC im asynchronen Modus ausgeführt wird, und gibt an, ob ODBC Benachrichtigungsmodus für ein Anweisungshandle ermöglicht.  
  
|SQL_ATTR_ASYNC_ENABLE oder SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT oder SQL_ATTR_ASYNC_DBC_EVENT|Modus|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|Aktivieren|ungleich null|Asynchrone Benachrichtigung|  
|Aktivieren|NULL|Asynchrone Abruf|  
|Deaktivieren|any|Synchron|  
  
 Eine Anwendung kann asynchronen Betriebsmodus vorübergehend deaktivieren. ODBC ignoriert Werte SQL_ATTR_ASYNC_DBC_EVENT auf, wenn die Verbindung asynchrone Vorgang auf Taskebene deaktiviert ist. ODBC ignoriert Werte SQL_ATTR_ASYNC_STMT_EVENT auf, wenn die Anweisung asynchronen Vorgang auf Taskebene deaktiviert ist.  
  
 Synchroner Aufruf von **SQLSetStmtAttr** und **SQLSetConnectAttr**  
 -   **SQLSetConnectAttr** unterstützt asynchrone Vorgänge jedoch den Aufruf der **SQLSetConnectAttr** festzulegende SQL_ATTR_ASYNC_DBC_EVENT ist immer synchron.  
  
-   **SQLSetStmtAttr** asynchrone Ausführung nicht unterstützt.  
  
 Fehler-Out-Szenario  
 Wenn **SQLSetConnectAttr** wird aufgerufen, bevor Sie vornehmen, eine Verbindung kann nicht der Treiber-Manager den zu verwendenden Treiber zu ermitteln. Daher gibt der Treiber-Manager zurück, Erfolg **SQLSetConnectAttr** jedoch das Attribut möglicherweise nicht im Treiber festlegen. Der Treiber-Manager werden diese Attribute festgelegt, wenn die Anwendung eine Verbindungsfunktion aufruft. Der Treiber-Manager kann Fehler – nicht, weil Treiber asynchrone Vorgänge nicht unterstützt.  
  
 Vererbung von Verbindungsattribute  
 Die Anweisungen der Verbindung werden in der Regel die Verbindungsattribute erben. Allerdings wird das Attribut SQL_ATTR_ASYNC_DBC_EVENT kann nicht geerbt werden und wirkt sich nur auf die Verbindungsvorgänge.  
  
 Um einem Handle für eine ODBC-Verbindungshandle zuzuordnen, eine ODBC-Anwendung die ODBC API-Aufrufe **SQLSetConnectAttr** und SQL_ATTR_ASYNC_DBC_EVENT gibt an, wie das Attribut und das Ereignis als Attributwert verarbeiten. Das neue ODBC-Attribut ist SQL_ATTR_ASYNC_DBC_EVENT vom Typ SQL_IS_POINTER.  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 Erstellen Sie Anwendungen in der Regel automatisches Zurücksetzungsereignis-Objekte. ODBC werden das Ereignisobjekt nicht zurückgesetzt werden. Anwendungen müssen sicherstellen, dass das Objekt nicht signalisierten Zustand ist, bevor Sie eine asynchrone ODBC-Funktion aufrufen.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT ist ein nur-Treiber-Manager-Attribut, die nicht im Treiber festgelegt werden.  
  
 Der Standardwert von SQL_ATTR_ASYNC_DBC_EVENT ist NULL. Wenn der Treiber die asynchrone Benachrichtigung nicht unterstützt, Abrufen oder Festlegen des SQL_ATTR_ASYNC_DBC_EVENT gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner).  
  
 Wenn des letzten SQL_ATTR_ASYNC_DBC_EVENT-Werts für festlegen eine ODBC-Verbindungshandle ist nicht NULL und die Anwendung asynchronen Modus aktiviert, indem Attribut SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE mit SQL_ASYNC_DBC_ENABLE_ON, eine ODBC-Verbindung aufrufen Funktion, die asynchronen Modus unterstützt, wird eine abschlussbenachrichtigung abrufen. Wenn der letzte SQL_ATTR_ASYNC_DBC_EVENT-Wert, legen Sie für eine ODBC-Verbindungshandle NULL ist, sendet ODBC nicht der Anwendung eine Benachrichtigung, unabhängig davon, ob der asynchrone Modus aktiviert ist.  
  
 Eine Anwendung kann SQL_ATTR_ASYNC_DBC_EVENT vor oder nach dem Festlegen des Attributs SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE festlegen.  
  
 Anwendungen können das SQL_ATTR_ASYNC_DBC_EVENT-Attribut auf eine ODBC-Verbindungshandle vor dem Aufrufen einer Verbindungsfunktion festlegen (**SQLConnect**, **SQLBrowseConnect**, oder  **SQLDriverConnect**). Da der ODBC-Treiber-Manager nicht die ODBC-Treiber erkennt der Anwendung verwendet werden, wird SQL_SUCCESS zurückgegeben. Wenn die Anwendung eine Verbindungsfunktion aufruft, wird der ODBC-Treiber-Manager überprüfen Sie, ob der Treiber die asynchrone Benachrichtigung unterstützt. Wenn der Treiber die asynchrone Benachrichtigung nicht unterstützt, gibt der ODBC-Treiber-Manager SQL_ERROR mit SQLSTATE S1_118 (Treiber nicht unterstützt asynchrone Benachrichtigung). Wenn der Treiber die asynchrone Benachrichtigung unterstützt, die ODBC-Treiber-Manager ruft den Treiber und legen Sie die entsprechenden Attribute SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK und SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT.  
  
 Auf ähnliche Weise eine Anwendung ruft **SQLSetStmtAttr** für eine ODBC-Anweisung zu verarbeiten, und gibt das Attribut SQL_ATTR_ASYNC_STMT_EVENT zum Aktivieren oder deaktivieren die Anweisung auf die asynchrone Benachrichtigung. Da eine Anweisung Funktion immer aufgerufen wird, nachdem die Verbindung hergestellt wurde, **SQLSetStmtAttr** SQL_ERROR mit SQLSTATE S1_118 zurück (Treiber nicht unterstützt asynchrone Benachrichtigung) sofort, wenn die entsprechende Treiber unterstützt keine asynchronen Vorgänge oder der Treiber unterstützt asynchrone Vorgänge unterstützt jedoch keine asynchrone Benachrichtigung.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT, der auf NULL festgelegt werden kann, ist ein nur-Treiber-Manager-Attribut, die nicht im Treiber festgelegt werden.  
  
 Der Standardwert von SQL_ATTR_ASYNC_STMT_EVENT ist NULL. Wenn der Treiber die asynchrone Benachrichtigung nicht unterstützt, Abrufen oder Festlegen des Attributs SQL_ATTR_ASYNC_ STMT_EVENT gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner).  
  
 Eine Anwendung sollte das gleiche Ereignishandle nicht mehr als eine ODBC-Anweisungshandle zuordnen. Andernfalls, eine Benachrichtigung verloren, wenn zwei asynchrone Aufrufe für die ODBC-Funktion auf zwei Handles abgeschlossen wird, die dasselbe Ereignishandle freigeben. Um ein Anweisungshandle, der dem Verbindungshandle erben das gleiche Ereignishandle zu vermeiden, gibt ODBC SQL_ERROR mit SQLSTATE IM016 (kann nicht-Anweisungsattribut in Verbindungshandle festgelegt) zurück, wenn eine Anwendung SQL_ATTR_ASYNC_STMT_EVENT für ein Verbindungshandle festlegt.  
  
### <a name="calling-asynchronous-odbc-functions"></a>Aufrufen von asynchronen ODBC-Funktionen  
 Nach dem Aktivieren von asynchronen Benachrichtigungen, und starten einen asynchronen Vorgang, kann die Anwendung eine ODBC-Funktion aufrufen. Wenn die Funktion auf den Satz von Funktionen, die asynchronen Vorgang zu unterstützen gehört, erhalten die Anwendung eine abschlussbenachrichtigung, wenn der Vorgang abgeschlossen ist, unabhängig davon, ob die Funktion ist fehlgeschlagen oder erfolgreich.  Die einzige Ausnahme ist, dass die Anwendung eine ODBC-Funktion mit einem ungültigen Handle der Verbindung oder Anweisung aufruft. In diesem Fall ODBC nicht das Ereignishandle zu erhalten und legen Sie ihn auf den signalisierten Zustand.  
  
 Die Anwendung muss sicherstellen, dass das zugeordnete Ereignis-Objekt in einen nicht signalisierten Zustand ist, vor dem Starten eines asynchronen Vorgangs für die entsprechenden ODBC-Anweisungshandle. ODBC werden das Ereignisobjekt nicht zurückgesetzt werden.  
  
### <a name="getting-notification-from-odbc"></a>Abrufen von Benachrichtigungen aus ODBC  
 Ein Anwendungsthread kann Aufrufen **WaitForSingleObject** , auf das Handle für ein Ereignis oder den Aufruf warten **WaitForMultipleObjects** zum Warten auf ein Array von Ereignishandles, und werden angehalten, bis eine oder alle der Ereignisobjekte signalisiert oder das Timeoutintervall verstrichen ist.  
  
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
