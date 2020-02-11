---
title: SQLFreeHandle-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeHandle
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFreeHandle
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e312bcbc6efcb96ff02657b98034f0340ae377dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68345182"
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLFreeHandle** gibt Ressourcen frei, die einer bestimmten Umgebung, einer Verbindung, einer Anweisung oder einem Deskriptorhandle zugeordnet sind.  
  
> [!NOTE]
>  Diese Funktion ist eine generische Funktion zum Freigeben von Handles. Sie ersetzt die ODBC 2,0-Funktionen **sqlfreeconnetct** (für die Freigabe eines Verbindungs Handles) und **sqlfreedenv** (zum Freigeben eines Umgebungs Handles). **Sqlfreeconnetct** und **sqlfreeev** sind in ODBC 3 *. x*als veraltet markiert. **SQLFreeHandle** ersetzt auch die ODBC 2,0-Funktion **SQLFreeStmt** (durch die SQL_DROP- *Option*) zum Freigeben eines Anweisungs Handles. Weitere Informationen finden Sie unter "comments". Weitere Informationen dazu, wie der Treiber-Manager diese Funktion zuordnet, wenn eine ODBC 3 *. x* -Anwendung mit einem ODBC 2 *. x* -Treiber arbeitet, finden Sie unterzuordnen [von Ersetzungs Funktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 Der Der Typ des Handles, das von **SQLFreeHandle**freigegeben werden soll. Dies muss einer der folgenden Werte sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur vom Treiber-Manager und vom Treiber verwendet. Anwendungen sollten diesen Handlertyp nicht verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [entwickeln von Verbindungs Pool Informationen in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 Wenn " *shandtype* " keiner dieser Werte ist, gibt **SQLFreeHandle** SQL_INVALID_HANDLE zurück.  
  
 *Bewältigen*  
 Der Das Handle, das freigegeben werden soll.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
 Wenn **SQLFreeHandle** SQL_ERROR zurückgibt, ist das Handle noch gültig.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFreeHandle** SQL_ERROR zurückgibt, kann ein zugeordneter SQLSTATE-Wert aus der Diagnosedaten Struktur für das Handle abgerufen werden, das von **SQLFreeHandle** freigegeben wurde. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLFreeHandle** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) das *handlentypargument* wurde SQL_HANDLE_ENV, und mindestens eine Verbindung befand sich im zugeordneten oder verbundenen Zustand. **SQLDisconnect** und **SQLFreeHandle** mit dem *Typ* "SQL_HANDLE_DBC" müssen für jede Verbindung aufgerufen werden, bevor **SQLFreeHandle** mit dem *Typ* "SQL_HANDLE_ENV" aufgerufen wird.<br /><br /> (DM) das *HandlerType* -Argument wurde SQL_HANDLE_DBC, und die Funktion wurde aufgerufen, bevor **SQLDisconnect** für die Verbindung aufgerufen wurde.<br /><br /> (DM) das *handlentypargument* wurde SQL_HANDLE_DBC. Eine asynchron ausgeführte Funktion wurde mit *handle* aufgerufen, und die Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) das *handlentypargument* wurde SQL_HANDLE_STMT. **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde mit dem Anweisungs Handle aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) das *handlentypargument* wurde SQL_HANDLE_STMT. Eine asynchron ausgeführte Funktion wurde für das Anweisungs Handle oder für das zugeordnete Verbindungs Handle aufgerufen, und die Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) das *handlentypargument* wurde SQL_HANDLE_DESC. Für das zugeordnete Verbindungs Handle wurde eine asynchron ausgeführte Funktion aufgerufen. die Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) alle neben geordneten Handles und anderen Ressourcen wurden nicht freigegeben, bevor **SQLFreeHandle** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungs Handles aufgerufen, die mit dem *handle* verknüpft sind, und der *Tortyp* wurde auf SQL_HANDLE_STMT festgelegt, oder SQL_HANDLE_DESC zurückgegebene SQL_PARAM_DATA_AVAILABLE. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.|  
|HY013|Speicher Verwaltungsfehler|Das ' *Lenker Type* '-Argument war SQL_HANDLE_STMT oder SQL_HANDLE_DESC, und der Funktions aufgerufene konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY017|Ungültige Verwendung eines automatisch zugeordneten Deskriptorhandles.|(DM) das *handle* -Argument wurde auf das Handle für einen automatisch zugeordneten Deskriptor festgelegt.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) das *handlentypargument* wurde SQL_HANDLE_DESC, und der Treiber war ein ODBC 2 *. x* -Treiber.<br /><br /> (DM) das *handlentypargument* wurde SQL_HANDLE_STMT, und der Treiber war kein gültiger ODBC-Treiber.|  
  
## <a name="comments"></a>Kommentare  
 **SQLFreeHandle** wird zum Freigeben von Handles für Umgebungen, Verbindungen, Anweisungen und Deskriptoren verwendet, wie in den folgenden Abschnitten beschrieben. Allgemeine Informationen zu Handles finden Sie unter [Handles](../../../odbc/reference/develop-app/handles.md).  
  
 Eine Anwendung sollte kein Handle verwenden, nachdem Sie freigegeben wurde. der Treiber-Manager überprüft nicht die Gültigkeit eines Handles in einem Funktions Aufruf.  
  
## <a name="freeing-an-environment-handle"></a>Freigeben eines Umgebungs Handles  
 Bevor **SQLFreeHandle** mit einem *Handlertyp* von SQL_HANDLE_ENV aufgerufen wird, muss eine Anwendung **SQLFreeHandle** mit einem *Handlertyp* von SQL_HANDLE_DBC für alle Verbindungen aufrufen, die unter der Umgebung zugeordnet sind. Andernfalls gibt der **SQLFreeHandle** -Befehl SQL_ERROR zurück, und die Umgebung und eine beliebige aktive Verbindung bleiben gültig. Weitere Informationen finden Sie unter [Umgebungs Handles](../../../odbc/reference/develop-app/environment-handles.md) und [Zuordnen des Umgebungs](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)Handles.  
  
 Wenn die Umgebung eine freigegebene Umgebung ist, hat die Anwendung, die **SQLFreeHandle** mit einem *Handlertyp* von aufruft, SQL_HANDLE_ENV keinen Zugriff mehr auf die Umgebung nach dem Aufruf, aber die Ressourcen der Umgebung werden nicht zwangsläufig freigegeben. Der **SQLFreeHandle** -Befehl Dekremente den Verweis Zähler der Umgebung. Der Verweis Zähler wird vom Treiber-Manager verwaltet. Wenn keine Null erreicht wird, wird die freigegebene Umgebung nicht freigegeben, da Sie noch von einer anderen Komponente verwendet wird. Wenn der Verweis Zähler Null erreicht, werden die Ressourcen der freigegebenen Umgebung freigegeben.  
  
## <a name="freeing-a-connection-handle"></a>Freigeben eines Verbindungs Handles  
 Bevor **SQLFreeHandle** mit dem *Handlertyp* SQL_HANDLE_DBC aufgerufen wird, muss eine Anwendung **SQLDisconnect** für die Verbindung aufrufen, wenn eine Verbindung mit diesem Handle besteht *.* Andernfalls gibt der **SQLFreeHandle** -Befehl SQL_ERROR zurück, und die Verbindung bleibt gültig.  
  
 Weitere Informationen finden Sie unter [Verbindungs Handles](../../../odbc/reference/develop-app/connection-handles.md) und [Trennen der Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Freigeben eines Anweisungshandles  
 Ein **SQLFreeHandle** -Befehl mit einem *handsortyp* von SQL_HANDLE_STMT gibt alle Ressourcen frei, die durch einen-Befehl von **sqlzugewieschandle** mit dem *Typ* "SQL_HANDLE_STMT" zugeordnet wurden. Wenn eine Anwendung **SQLFreeHandle** zum Freigeben einer Anweisung mit ausstehenden Ergebnissen aufruft, werden die ausstehenden Ergebnisse gelöscht. Wenn eine Anwendung ein Anweisungs Handle freigibt, gibt der Treiber die vier automatisch zugeordneten Deskriptoren frei, die diesem Handle zugeordnet sind. Weitere Informationen finden Sie unter [Anweisungs Handles](../../../odbc/reference/develop-app/statement-handles.md) und [Freigeben eines Anweisungs Handles](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 Beachten Sie, dass **SQLDisconnect** alle in der Verbindung geöffneten Anweisungen und Deskriptoren automatisch löscht.  
  
## <a name="freeing-a-descriptor-handle"></a>Freigeben eines Deskriptorhandles  
 Ein **SQLFreeHandle** -Befehl mit einem *Handlertyp* von SQL_HANDLE_DESC gibt das Deskriptorhandle in *handle*frei. Der **SQLFreeHandle** -Befehl gibt keinen Speicher frei, der von der Anwendung belegt wird, auf die von einem Zeiger Feld (einschließlich SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR) eines beliebigen deskriptordaten Satzes des *Handles*verwiesen werden kann. Der vom Treiber für Felder, die keine Zeiger Felder sind, zugeordnete Arbeitsspeicher wird freigegeben, wenn das Handle freigegeben wird. Wenn ein vom Benutzer zugeordnetes Deskriptorhandle freigegeben wird, werden alle Anweisungen, denen das freigegebene Handle zugeordnet wurde, auf die jeweiligen automatisch zugeordneten Deskriptorhandles zurückgesetzt.  
  
> [!NOTE]
>  ODBC 2 *. x* -Treiber unterstützen das Freigeben von Deskriptorhandles nicht, so wie Sie die Zuordnung von Deskriptorhandles nicht unterstützen.  
  
 Beachten Sie, dass **SQLDisconnect** alle in der Verbindung geöffneten Anweisungen und Deskriptoren automatisch löscht. Wenn eine Anwendung ein Anweisungs Handle freigibt, gibt der Treiber alle automatisch generierten Deskriptoren aus, die diesem Handle zugeordnet sind.  
  
 Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Weitere Codebeispiele finden Sie unter [sqlbrowseconnetct](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) und [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
### <a name="code"></a>Code  
  
```cpp  
// SQLFreeHandle.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <stdio.h>  
  
int main() {  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   // Initialize the environment, connection, statement handles.  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   // Allocate the environment.  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set environment attributes.  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
  
   // Allocate the connection.  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
   // Set the login timeout.  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
  
   // Let the user select the data source and connect to the database.  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Free handles, and disconnect.     
   if (hstmt) {   
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
      hstmt = NULL;   
   }  
   if (hdbc) {   
      SQLDisconnect(hdbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
      hdbc = NULL;   
   }  
   if (henv) {   
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
      henv = NULL;   
   }  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuordnen eines Handles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[Sqlcance functionl](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Festlegen eines Cursor namens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Header Dateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md)
