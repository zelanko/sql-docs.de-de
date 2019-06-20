---
title: SQLFreeHandle-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeHandle
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFreeHandle
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0ddaae66e60f77156b2d7c7e975875bb78d56cb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537328"
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLFreeHandle** gibt ein bestimmtes Umgebung, Verbindung, Anweisung oder Deskriptor Handle zugeordneten Ressourcen frei.  
  
> [!NOTE]
>  Diese Funktion ist eine generische Funktion für das Freigeben des Handles. Er ersetzt die Funktionen der ODBC 2.0 **SQLFreeConnect** (für die Freigabe ein Verbindungshandle) und **SQLFreeEnv** (für die Freigabe ein Umgebungshandle). **SQLFreeConnect** und **SQLFreeEnv** sind sowohl in ODBC 3. veraltet *.x*. **SQLFreeHandle** auch die ODBC 2.0-Funktion ersetzt **SQLFreeStmt** (mit der SQL_DROP *Option*) für das Freigeben eines Anweisungshandles. Weitere Informationen finden Sie unter "Kommentare". Weitere Informationen dazu, was der Treiber-Manager diese Funktion auf, wenn eine ODBC 3. zuordnet *.x* Anwendung arbeitet mit einer ODBC 2. *.x* -Treiber verwenden, finden Sie unter [Zuordnen von Ersatzfunktionen für rückwärts Kompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Der Typ des Handles freigegeben werden, indem **SQLFreeHandle**. Dabei muss es sich um einen der folgenden Werte sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur von der Treiber-Manager und Treiber verwendet. Anwendungen sollten nicht mit dieser Handletyp verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN, finden Sie unter [Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 Wenn *HandleType* ist keiner dieser Werte, **SQLFreeHandle** SQL_INVALID_HANDLE gibt.  
  
 *Handle*  
 [Eingabe] Das Handle freigegeben werden.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
 Wenn **SQLFreeHandle** gibt SQL_ERROR zurück, das Handle ist weiterhin gültig.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFreeHandle** gibt SQL_ERROR zurück, die einen zugeordneten SQLSTATE-Wert aus der Struktur diagnostische Daten für das Handle abgerufen werden können, die **SQLFreeHandle** hat versucht, eine kostenlose konnte aber nicht. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLFreeHandle** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) die *HandleType* Argument war SQL_HANDLE_ENV auf, und über mindestens eine Verbindung in einem Zustand zugeordnet und verbunden wurde. **SQLDisconnect** und **SQLFreeHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, muss für jede Verbindung vor dem Aufruf aufgerufen werden **SQLFreeHandle** mit einer *HandleType* SQL_HANDLE_ENV auf.<br /><br /> (DM) die *HandleType* Argument war SQL_HANDLE_DBC auf, und die Funktion aufgerufen wurde, vor dem Aufruf **SQLDisconnect** für die Verbindung.<br /><br /> (DM) die *HandleType* Argument war SQL_HANDLE_DBC auf. Eine asynchrone Funktion aufgerufen wurde, wobei *behandeln* und die Funktion wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) die *HandleType* Argument war SQL_HANDLE_STMT auf. **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** war aufgerufen, wobei das Anweisungshandle und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) die *HandleType* Argument war SQL_HANDLE_STMT auf. Eine asynchrone Funktion aufgerufen wurde, auf das Anweisungshandle oder auf das zugeordnete Verbindungshandle aus, und die Funktion wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) die *HandleType* Argument war SQL_HANDLE_DESC. Eine asynchrone Funktion wurde für das zugeordnete Verbindungshandle aufgerufen; und die Funktion wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) alle untergeordneten Handles und andere Ressourcen wurden keine vor freigegeben **SQLFreeHandle** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** für eines der zugeordneten Anweisungshandles aufgerufen wurde die *behandeln* und *HandleType* auf SQL_HANDLE_STMT festgelegt wurde, oder SQL_HANDLE_DESC zurückgegeben SQL_PARAM_DATA_AVAILABLE. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Die *HandleType* Argument war SQL_HANDLE_STMT auf oder SQL_HANDLE_DESC und Aufruf der Funktion konnte nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY017|Ungültige Verwendung einer automatisch zugeordneten Deskriptorhandles.|(DM) die *behandeln* -Argument wurde auf das Handle für einen automatisch zugewiesenen Deskriptor festgelegt.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) die *HandleType* Argument war SQL_HANDLE_DESC und des Treibers einer ODBC 2. *.x* Treiber.<br /><br /> (DM) die *HandleType* Argument SQL_HANDLE_STMT auf, und der Treiber nicht wurde ein gültiger ODBC-Treiber.|  
  
## <a name="comments"></a>Kommentare  
 **SQLFreeHandle** wird zum Freigeben des Handles für Umgebungen, die Verbindungen, Anweisungen und Deskriptoren, wie in den folgenden Abschnitten beschrieben. Allgemeine Informationen zu Handles finden Sie unter [Handles](../../../odbc/reference/develop-app/handles.md).  
  
 Ein Handle sollte von einer Anwendung nicht verwendet werden, nachdem dieser freigegeben wurde. der Treiber-Manager überprüft nicht die Gültigkeit eines Handles in einem Funktionsaufruf.  
  
## <a name="freeing-an-environment-handle"></a>Freigeben eines Umgebungshandles  
 Vor dem Aufrufen **SQLFreeHandle** mit einem *HandleType* SQL_HANDLE_ENV auf, eine Anwendung aufrufen muss **SQLFreeHandle** mit einem *HandleType*SQL_HANDLE_DBC auf, für alle Verbindungen, die unter der Umgebung zugeordnet. Andernfalls, den Aufruf von **SQLFreeHandle** gibt SQL_ERROR zurück, und die Umgebung und alle aktiven Verbindungen gültig bleibt. Weitere Informationen finden Sie unter [Umgebung verarbeitet](../../../odbc/reference/develop-app/environment-handles.md) und [zuordnen, die Umgebung behandeln](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Wenn die Umgebung auf einer freigegebenen Umgebung ist, ruft die Anwendung, die **SQLFreeHandle** mit einem *HandleType* SQL_HANDLE_ENV auf, hat keinen Zugriff mehr auf die Umgebung nach dem Aufruf, aber der Umgebung Ressourcen werden nicht unbedingt freigegeben werden. Der Aufruf von **SQLFreeHandle** dekrementiert den Verweiszähler der Umgebung. Der Verweiszähler wird vom Treiber-Manager verwaltet werden. Wenn es nicht 0 (null) erreicht, wird die freigegebene Umgebung nicht freigegeben, da sie immer noch von einer anderen Komponente verwendet wird. Wenn der Verweiszähler null erreicht, werden die Ressourcen von der freigegebenen Umgebung freigegeben.  
  
## <a name="freeing-a-connection-handle"></a>Freigeben eines Verbindungshandles  
 Vor dem Aufrufen **SQLFreeHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, eine Anwendung aufrufen muss **SQLDisconnect** für die Verbindung, wenn eine dazu Verbindung behandeln *.* Andernfalls, den Aufruf von **SQLFreeHandle** gibt SQL_ERROR zurück, und die Verbindung gültig bleibt.  
  
 Weitere Informationen finden Sie unter [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md) und [Trennen von einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Freigeben eines Anweisungshandles  
 Ein Aufruf von **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_STMT auf, alle Ressourcen, die durch einen Aufruf von zugeordnet wurden freigegeben werden **SQLAllocHandle** mit einer  *HandleType* von SQL_HANDLE_STMT auf. Wenn eine Anwendung ruft **SQLFreeHandle** um eine Anweisung freizugeben, die über ausstehende Ergebnisse verfügt, werden die ausstehenden Ergebnisse gelöscht. Wenn eine Anwendung ein Anweisungshandle frei, gibt der Treiber die vier automatisch zugewiesenen Deskriptoren dieser Handle zugeordneten frei. Weitere Informationen finden Sie unter [-Anweisung behandelt](../../../odbc/reference/develop-app/statement-handles.md) und [Freigeben einer Anweisungshandle](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 Beachten Sie, dass **SQLDisconnect** löscht automatisch alle Anweisungen und Deskriptoren öffnen, für die Verbindung.  
  
## <a name="freeing-a-descriptor-handle"></a>Ein Deskriptorhandle freigeben  
 Ein Aufruf von **SQLFreeHandle** mit einer *HandleType* von SQL_HANDLE_DESC frei Deskriptorhandles in *behandeln*. Der Aufruf von **SQLFreeHandle** aufgehoben, Arbeitsspeicher, der von der Anwendung, die von einem Zeigerfeld (einschließlich SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR) referenziert werden kann, belegt der anwendungsparameterdeskriptor-Datensatz der *behandeln*. Die Speichermenge, die vom Treiber für Felder, die keine Zeiger Felder sind wird freigegeben, wenn das Handle freigegeben wird. Wenn ein vom Benutzer zugewiesener Deskriptorhandle freigegeben wird, können Sie alle Anweisungen, denen das freigegebene Handle zugeordnet wurde mussten auf ihre jeweiligen automatisch zugeordneten Deskriptorhandles zurückgesetzt.  
  
> [!NOTE]
>  ODBC 2. *.x* Treiber unterstützen keine freigebenden Deskriptorhandles, wie sie beim Zuordnen von Deskriptorhandles nicht unterstützen.  
  
 Beachten Sie, dass **SQLDisconnect** löscht automatisch alle Anweisungen und Deskriptoren öffnen, für die Verbindung. Wenn eine Anwendung ein Anweisungshandle frei, gibt der Treiber alle automatisch generierten Deskriptoren dieser Handle zugeordneten frei.  
  
 Weitere Informationen zu den sicherheitsbeschreibungen, finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Weitere Codebeispiele finden Sie unter [SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) und [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ein Handle zuordnen|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCance Functionl](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ein Cursorname festlegen|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md)
