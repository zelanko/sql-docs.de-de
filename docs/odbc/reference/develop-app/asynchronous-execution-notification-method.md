---
description: Asynchrone Ausführung (Benachrichtigungsmethode)
title: Asynchrone Ausführung (Benachrichtigungs Methode) | Microsoft-Dokumentation
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
ms.openlocfilehash: 19c201d71d42c40277ad67cef25922e55e97de12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483123"
---
# <a name="asynchronous-execution-notification-method"></a>Asynchrone Ausführung (Benachrichtigungsmethode)
ODBC ermöglicht die asynchrone Ausführung von Verbindungs-und Anweisungs Vorgängen. Ein Anwendungs Thread kann eine ODBC-Funktion im asynchronen Modus aufzurufen, und die Funktion kann zurückgeben, bevor der Vorgang beendet ist, sodass der Anwendungs Thread andere Aufgaben ausführen kann. Im Windows 7 SDK hat eine Anwendung für asynchrone Anweisungs-oder Verbindungs Vorgänge festgestellt, dass der asynchrone Vorgang mit der Abruf Methode durchgeführt wurde. Weitere Informationen finden Sie unter [asynchrone Ausführung (Abruf Methode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Ab dem Windows 8 SDK können Sie mithilfe der Benachrichtigungs Methode ermitteln, ob ein asynchroner Vorgang fertiggestellt ist.  
  
 In der Abruf Methode müssen Anwendungen die asynchrone Funktion jedes Mal aufgerufen werden, wenn Sie den Status des Vorgangs wünscht. Die Benachrichtigungs Methode ähnelt Callback und Wait in ADO.net. ODBC verwendet jedoch Win32-Ereignisse als Benachrichtigungs Objekt.  
  
 Die ODBC-Cursor Bibliothek und die asynchrone ODBC-Benachrichtigung können nicht gleichzeitig verwendet werden. Wenn Sie beide Attribute festlegen, wird ein Fehler mit SQLSTATE S1119 zurückgegeben (die Cursor Bibliothek und die asynchrone Benachrichtigung können nicht gleichzeitig aktiviert werden).  
  
 Informationen für Treiber Entwickler finden Sie [unter Benachrichtigung über die Beendigung der asynchronen Funktion](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md) .  
  
> [!NOTE]  
>  Die Benachrichtigungs Methode wird mit der Cursor Bibliothek nicht unterstützt. Eine Anwendung empfängt eine Fehlermeldung, wenn Sie versucht, die Cursor Bibliothek über SQLSetConnectAttr zu aktivieren, wenn die Benachrichtigungs Methode aktiviert ist.  
  
## <a name="overview"></a>Übersicht  
 Wenn eine ODBC-Funktion im asynchronen Modus aufgerufen wird, wird das Steuerelement sofort mit dem Rückgabecode SQL_STILL_EXECUTING an die aufrufende Anwendung zurückgegeben. Die Anwendung muss die Funktion wiederholt Abfragen, bis Sie etwas anderes als SQL_STILL_EXECUTING zurückgibt. Die Abruf Schleife erhöht die CPU-Auslastung und führt in vielen asynchronen Szenarien zu einer schlechten Leistung.  
  
 Wenn das Benachrichtigungs Modell verwendet wird, ist das Abruf Modell deaktiviert. Anwendungen sollten die ursprüngliche Funktion nicht erneut aufzurufen. Aufrufen der [sqlcompleteasync-Funktion](../../../odbc/reference/syntax/sqlcompleteasync-function.md) , um den asynchronen Vorgang abzuschließen. Wenn eine Anwendung die ursprüngliche Funktion erneut aufruft, bevor der asynchrone Vorgang beendet ist, wird der Aufruf SQL_ERROR mit SQLSTATE IM017 zurückgegeben (der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert).  
  
 Wenn Sie das Benachrichtigungs Modell verwenden, kann die Anwendung **SQLCancel** oder **sqlcancelhandle** aufzurufen, um eine Anweisung oder einen Verbindungsvorgang abzubrechen. Wenn die Abbruch Anforderung erfolgreich ist, wird von ODBC SQL_SUCCESS zurückgegeben. Diese Meldung weist nicht darauf hin, dass die Funktion tatsächlich abgebrochen wurde. Gibt an, dass die Abbruch Anforderung verarbeitet wurde. Ob die Funktion tatsächlich abgebrochen wird, ist Treiber abhängig und Datenquellen abhängig. Wenn ein Vorgang abgebrochen wird, signalisiert der Treiber-Manager weiterhin das Ereignis. Der Treiber-Manager gibt SQL_ERROR im Rückgabecode Puffer zurück, und der Status lautet SQLSTATE HY008 (Vorgang abgebrochen), um anzugeben, dass der Abbruch erfolgreich war. Wenn die Funktion die normale Verarbeitung abgeschlossen hat, gibt der Treiber-Manager SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück.  
  
### <a name="downlevel-behavior"></a>Downlevelverhalten  
 Die Version des ODBC-Treiber-Managers, die diese Benachrichtigung unterstützt, ist ODBC 3,81.  
  
|ODBC-Version der Anwendung|Treiber-Manager-Version|Treiberversion|Verhalten|  
|------------------------------|----------------------------|--------------------|--------------|  
|Neue Anwendung einer beliebigen ODBC-Version|ODBC 3,81|ODBC 3,80-Treiber|Die Anwendung kann diese Funktion verwenden, wenn der Treiber diese Funktion unterstützt, andernfalls führt der Treiber-Manager zu einem Fehler.|  
|Neue Anwendung einer beliebigen ODBC-Version|ODBC 3,81|Pre-ODBC 3,80-Treiber|Der Treiber-Manager führt einen Fehler aus, wenn der Treiber dieses Feature nicht unterstützt.|  
|Neue Anwendung einer beliebigen ODBC-Version|Pre-ODBC 3,81|Any|Wenn diese Funktion von der Anwendung verwendet wird, werden die neuen Attribute von einem alten Treiber-Manager als Treiber spezifische Attribute betrachtet, und für den Treiber sollte ein Fehler ausgegeben werden. Diese Attribute werden von einem neuen Treiber-Manager nicht an den Treiber übergeben.|  
  
 Eine Anwendung sollte die Treiber-Manager-Version überprüfen, bevor Sie diese Funktion verwenden. Andernfalls ist das Verhalten nicht definiert, wenn ein schlecht geschriebener Treiber nicht fehlerhaft ist und die Treiber-Manager-Version vor ODBC 3,81 ist.  
  
## <a name="use-cases"></a>Anwendungsfälle  
 Dieser Abschnitt zeigt Anwendungsfälle für die asynchrone Ausführung und den Abruf Mechanismus.  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>Integrieren von Daten aus mehreren ODBC-Quellen  
 Eine Daten Integrations Anwendung Ruft asynchron Daten aus mehreren Datenquellen ab. Einige Daten stammen aus Remote Datenquellen, und einige Daten stammen aus lokalen Dateien. Die Anwendung kann erst fortgesetzt werden, wenn die asynchronen Vorgänge abgeschlossen sind.  
  
 Anstatt wiederholt einen Vorgang abzufragen, um zu ermitteln, ob er fertig ist, kann die Anwendung ein Ereignis Objekt erstellen und einem ODBC-Verbindungs Handle oder einem ODBC-Anweisungs Handle zuordnen. Die Anwendung ruft dann APIs für die Synchronisierung von Betriebssystemen auf, um auf ein Ereignis Objekt oder viele Ereignis Objekte (sowohl ODBC-Ereignisse als auch andere Windows-Ereignisse) zu warten. ODBC signalisiert das Ereignis Objekt, wenn der entsprechende asynchrone ODBC-Vorgang abgeschlossen ist.  
  
 Unter Windows werden Win32-Ereignis Objekte verwendet, die dem Benutzer ein einheitliches Programmiermodell bereitstellen. Treiber-Manager auf anderen Plattformen können die für diese Plattformen spezifische ereignisobjektimplementierung verwenden.  
  
 Im folgenden Codebeispiel wird die Verwendung von asynchronen Verbindungs-und Anweisungs Benachrichtigungen veranschaulicht:  
  
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
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>Ermitteln, ob ein Treiber eine asynchrone Benachrichtigung unterstützt  
 Eine ODBC-Anwendung kann ermitteln, ob ein ODBC-Treiber die asynchrone Benachrichtigung durch Aufrufen von [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)unterstützt. Der ODBC-Treiber-Manager ruft folglich **SQLGetInfo** des Treibers mit SQL_ASYNC_NOTIFICATION auf.  
  
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
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Zuordnen eines Win32-Ereignis Handles zu einem ODBC-Handle  
 Anwendungen sind für das Erstellen von Win32-Ereignis Objekten mithilfe der entsprechenden Win32-Funktionen verantwortlich. Eine Anwendung kann ein Win32-Ereignis Handle einem ODBC-Verbindungs Handle oder einem ODBC-Anweisungs Handle zuordnen.  
  
 Verbindungs Attribute SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE und SQL_ATTR_ASYNC_DBC_EVENT bestimmen, ob ODBC im asynchronen Modus ausgeführt wird und ob ODBC den Benachrichtigungs Modus für ein Verbindungs Handle aktiviert. Anweisungs Attribute SQL_ATTR_ASYNC_ENABLE und SQL_ATTR_ASYNC_STMT_EVENT bestimmen, ob ODBC im asynchronen Modus ausgeführt wird und ob ODBC den Benachrichtigungs Modus für ein Anweisungs Handle aktiviert.  
  
|SQL_ATTR_ASYNC_ENABLE oder SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT oder SQL_ATTR_ASYNC_DBC_EVENT|Mode|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|Aktivieren|ungleich NULL|Asynchrone Benachrichtigung|  
|Aktivieren|NULL|Asynchroner Abruf|  
|Deaktivieren|any|Synchron|  
  
 Eine Anwendung kann den asynchronen Betriebsmodus tempordisch deaktivieren. ODBC ignoriert Werte von SQL_ATTR_ASYNC_DBC_EVENT, wenn der asynchrone Vorgang auf Verbindungs Ebene deaktiviert ist. ODBC ignoriert Werte von SQL_ATTR_ASYNC_STMT_EVENT, wenn der asynchrone Vorgang auf Anweisungs Ebene deaktiviert ist.  
  
 Synchroner Aufrufen von **SQLSetStmtAttr** und **SQLSetConnectAttr**  
 -   **SQLSetConnectAttr** unterstützt asynchrone Vorgänge, aber der Aufruf von **SQLSetConnectAttr** , um SQL_ATTR_ASYNC_DBC_EVENT festzulegen, ist immer synchron.  
  
-   **SQLSetStmtAttr** unterstützt keine asynchrone Ausführung.  
  
 Fehlerausgabe Szenario  
 Wenn **SQLSetConnectAttr** vor dem Herstellen einer Verbindung aufgerufen wird, kann der Treiber-Manager nicht bestimmen, welcher Treiber verwendet werden soll. Daher gibt der Treiber-Manager Erfolg für **SQLSetConnectAttr** zurück, aber das Attribut kann nicht im Treiber festgelegt werden. Diese Attribute werden vom Treiber-Manager festgelegt, wenn die Anwendung eine Verbindungsfunktion aufruft. Der Treiber-Manager führt möglicherweise zu einem Fehler, da der Treiber keine asynchronen Vorgänge unterstützt.  
  
 Vererbung von Verbindungs Attributen  
 In der Regel erben die Anweisungen einer Verbindung die Verbindungs Attribute. Allerdings ist das Attribut SQL_ATTR_ASYNC_DBC_EVENT nicht vererbbar und wirkt sich nur auf die Verbindungs Vorgänge aus.  
  
 Um ein Ereignis Handle einem ODBC-Verbindungs Handle zuzuordnen, ruft eine ODBC-Anwendung die ODBC-API **SQLSetConnectAttr** auf und gibt SQL_ATTR_ASYNC_DBC_EVENT als das-Attribut und das-Ereignis Handle als Attribut Wert an. Das neue ODBC-Attribut SQL_ATTR_ASYNC_DBC_EVENT ist vom Typ SQL_IS_POINTER.  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 Normalerweise erstellen Anwendungen automatisch zurückgesetzte Ereignis Objekte. Das Ereignis Objekt wird von ODBC nicht zurückgesetzt. Anwendungen müssen sicherstellen, dass sich das Objekt nicht im signalisierten Zustand befindet, bevor Sie eine asynchrone ODBC-Funktion aufrufen.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT ist ein nur Treiber-Manager-Attribut, das nicht im Treiber festgelegt wird.  
  
 Der Standardwert SQL_ATTR_ASYNC_DBC_EVENT ist NULL. Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, wird beim Aktivieren oder festlegen SQL_ATTR_ASYNC_DBC_EVENT SQL_ERROR mit SQLState HY092 (Ungültiger Attribut-/Optionsbezeichner) zurückgegeben.  
  
 Wenn der letzte SQL_ATTR_ASYNC_DBC_EVENT auf einem ODBC-Verbindungs Handle festgelegte Wert nicht NULL ist und die Anwendung den asynchronen Modus durch Festlegen des Attributs SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE mit SQL_ASYNC_DBC_ENABLE_ON aktiviert hat, wird beim Aufrufen einer beliebigen ODBC-Verbindungsfunktion, die den asynchronen Modus unterstützt, eine Abschluss Benachrichtigung angezeigt. Wenn der letzte SQL_ATTR_ASYNC_DBC_EVENT Wert, der in einem ODBC-Verbindungs Handle festgelegt ist, NULL ist, sendet ODBC keine Benachrichtigung an die Anwendung, unabhängig davon, ob der asynchrone Modus aktiviert ist.  
  
 Eine Anwendung kann SQL_ATTR_ASYNC_DBC_EVENT vor oder nach dem Festlegen des-Attributs festlegen SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE.  
  
 Anwendungen können das SQL_ATTR_ASYNC_DBC_EVENT-Attribut für ein ODBC-Verbindungs Handle festlegen, bevor Sie eine Verbindungsfunktion aufrufen (**SQLCONNECT**, **sqlbrowseconnetct**oder **SQLDriverConnect**). Da der ODBC-Treiber-Manager nicht weiß, welcher ODBC-Treiber von der Anwendung verwendet wird, wird SQL_SUCCESS zurückgegeben. Wenn die Anwendung eine Verbindungsfunktion aufruft, prüft der ODBC-Treiber-Manager, ob der Treiber die asynchrone Benachrichtigung unterstützt. Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, wird der ODBC-Treiber-Manager mit SQLSTATE S1_118 SQL_ERROR zurückgegeben (der Treiber unterstützt keine asynchrone Benachrichtigung). Wenn der Treiber die asynchrone Benachrichtigung unterstützt, ruft der ODBC-Treiber-Manager den Treiber auf und legt die entsprechenden Attribute SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK und SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT fest.  
  
 Ebenso Ruft eine Anwendung **SQLSetStmtAttr** für ein ODBC-Anweisungs Handle auf und gibt das SQL_ATTR_ASYNC_STMT_EVENT Attribut an, um die asynchrone Benachrichtigung auf Anweisungs Ebene zu aktivieren oder zu deaktivieren. Da eine Anweisungs Funktion immer aufgerufen wird, nachdem die Verbindung hergestellt wurde, gibt **SQLSetStmtAttr** SQL_ERROR mit SQLSTATE S1_118 zurück (der Treiber unterstützt keine asynchrone Benachrichtigung), wenn der entsprechende Treiber keine asynchronen Vorgänge unterstützt oder der Treiber einen asynchronen Vorgang unterstützt, jedoch keine asynchrone Benachrichtigung unterstützt.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT, die auf NULL festgelegt werden kann, ist ein nur Treiber-Manager-Attribut, das nicht im Treiber festgelegt wird.  
  
 Der Standardwert SQL_ATTR_ASYNC_STMT_EVENT ist NULL. Wenn der Treiber keine asynchrone Benachrichtigung unterstützt, wird das SQL_ATTR_ASYNC_ STMT_EVENT Attribut SQL_ERROR mit SQLState HY092 (Ungültiger Attribut-/Optionsbezeichner) zurückgegeben.  
  
 Eine Anwendung sollte dem gleichen Ereignis Handle nicht mehr als einem ODBC-Handle zuordnen. Andernfalls geht eine Benachrichtigung verloren, wenn zwei asynchrone ODBC-Funktionsaufrufe für zwei Handles, die dasselbe Ereignis Handle verwenden, ausgeführt werden. Um zu vermeiden, dass ein Anweisungs Handle das gleiche Ereignis Handle vom Verbindungs Handle erbt, gibt ODBC SQL_ERROR mit SQLSTATE IM016 zurück (das Anweisungs Attribut kann nicht in das Verbindungs Handle gesetzt werden), wenn eine Anwendung SQL_ATTR_ASYNC_STMT_EVENT auf einem Verbindungs Handle festlegt.  
  
### <a name="calling-asynchronous-odbc-functions"></a>Aufrufen von asynchronen ODBC-Funktionen  
 Nachdem Sie die asynchrone Benachrichtigung aktiviert und einen asynchronen Vorgang gestartet haben, kann die Anwendung jede ODBC-Funktion abrufen. Wenn die Funktion zu dem Satz von Funktionen gehört, die den asynchronen Vorgang unterstützen, erhält die Anwendung eine Abschluss Benachrichtigung, sobald der Vorgang abgeschlossen ist, unabhängig davon, ob die Funktion fehlgeschlagen ist oder erfolgreich war.  Die einzige Ausnahme besteht darin, dass die Anwendung eine ODBC-Funktion mit einer ungültigen Verbindung oder einem ungültigen Anweisungs Handle aufruft. In diesem Fall erhält ODBC das Ereignis Handle nicht und legt es auf den signalisierten Zustand fest.  
  
 Die Anwendung muss sicherstellen, dass das zugeordnete Ereignis Objekt in einem nicht signalisierten Zustand ist, bevor ein asynchroner Vorgang für das entsprechende ODBC-Handle gestartet wird. Das Ereignis Objekt wird von ODBC nicht zurückgesetzt.  
  
### <a name="getting-notification-from-odbc"></a>Benachrichtigung von ODBC erhalten  
 Ein Anwendungs Thread kann **WaitForSingleObject** zum warten auf ein Ereignis handle oder **WaitForMultipleObjects** zum warten auf ein Array von Ereignis Handles und angehalten, bis ein oder alle der Ereignis Objekte signalisiert werden oder das Timeout Intervall abläuft.  
  
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
