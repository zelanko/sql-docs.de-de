---
title: SQLFreeHandle-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0b136dec98a19676aa67c78615d8fe931f62aafa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285771"
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLFreeHandle** gibt Ressourcen frei, die einer bestimmten Umgebung, Verbindung, Anweisung oder Deskriptor-Handle zugeordnet sind.  
  
> [!NOTE]
>  Diese Funktion ist eine generische Funktion zum Freiwerden von Handles. Es ersetzt die ODBC 2.0-Funktionen **SQLFreeConnect** (zum Freiwerden eines Verbindungshandles) und **SQLFreeEnv** (zum Freiwerden eines Umgebungshandles). **SQLFreeConnect** und **SQLFreeEnv** sind beide in ODBC 3 *.x*veraltet. **SQLFreeHandle** ersetzt auch die ODBC 2.0-Funktion **SQLFreeStmt** (mit der SQL_DROP *Option*) zum Freiwerden eines Anweisungshandles. Weitere Informationen finden Sie unter "Kommentare". Weitere Informationen darüber, was der Treiber-Manager dieser Funktion zuordnet, wenn eine ODBC 3 *.x-Anwendung* mit einem ODBC 2 *.x-Treiber* arbeitet, finden Sie unter [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Der Typ des Handles, der von **SQLFreeHandle**freigegeben werden soll. Dies muss einer der folgenden Werte sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur vom Treiber-Manager und -Treiber verwendet. Anwendungen sollten diesen Handletyp nicht verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [Entwickeln von Verbindungspool-Awareness in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 Wenn *HandleType* nicht einer dieser Werte ist, gibt **SQLFreeHandle** SQL_INVALID_HANDLE zurück.  
  
 *Handle*  
 [Eingabe] Der zu befreiende Griff.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
 Wenn **SQLFreeHandle** SQL_ERROR zurückgibt, ist das Handle weiterhin gültig.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFreeHandle** SQL_ERROR zurückgibt, kann ein zugeordneter SQLSTATE-Wert aus der Diagnosedatenstruktur für das Handle abgerufen werden, das **SQLFreeHandle** zu befreien versucht hat, aber nicht konnte. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLFreeHandle** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY010|Funktionssequenzfehler|(DM) Das *HandleType-Argument* wurde SQL_HANDLE_ENV, und mindestens eine Verbindung befand sich in einem zugewiesenen oder verbundenen Zustand. **SQLDisconnect** und **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DBC müssen für jede Verbindung aufgerufen werden, bevor **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_ENV aufgerufen wird.<br /><br /> (DM) Das *HandleType-Argument* wurde SQL_HANDLE_DBC, und die Funktion wurde aufgerufen, bevor **SQLDisconnect** für die Verbindung aufgerufen wurde.<br /><br /> (DM) Das *HandleType-Argument* wurde SQL_HANDLE_DBC. Eine asynchron ausführende Funktion wurde mit *Handle* aufgerufen, und die Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) Das *HandleType-Argument* wurde SQL_HANDLE_STMT. **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurden mit dem Anweisungshandle aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Das *HandleType-Argument* wurde SQL_HANDLE_STMT. Eine asynchron ausgeführte Funktion wurde für das Anweisungshandle oder für das zugehörige Verbindungshandle aufgerufen, und die Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) Das *HandleType-Argument* wurde SQL_HANDLE_DESC. Eine asynchron ausgeführte Funktion wurde für das zugehörige Verbindungshandle aufgerufen. und die Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) Alle untergeordneten Handles und anderen Ressourcen wurden nicht freigegeben, bevor **SQLFreeHandle** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde aufgerufen, da eines der Anweisungshandles, die dem *Handle* zugeordnet sind, aufgerufen wurde und *HandleType* auf SQL_HANDLE_STMT festgelegt wurde oder SQL_HANDLE_DESC zurückgegebenen SQL_PARAM_DATA_AVAILABLE. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY013|Speicherverwaltungsfehler|Das *HandleType-Argument* wurde SQL_HANDLE_STMT oder SQL_HANDLE_DESC, und der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte möglicherweise aufgrund niedriger Speicherbedingungen nicht zugegriffen werden konnte.|  
|HY017|Ungültige Verwendung eines automatisch zugewiesenen Deskriptor-Handles.|(DM) Das *Handle-Argument* wurde auf das Handle für einen automatisch zugewiesenen Deskriptor festgelegt.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Das *HandleType-Argument* wurde SQL_HANDLE_DESC, und der Treiber war ein ODBC 2 *.x-Treiber.*<br /><br /> (DM) Das *HandleType-Argument* wurde SQL_HANDLE_STMT, und der Treiber war kein gültiger ODBC-Treiber.|  
  
## <a name="comments"></a>Kommentare  
 **SQLFreeHandle** wird verwendet, um Handles für Umgebungen, Verbindungen, Anweisungen und Deskriptoren freizugeben, wie in den folgenden Abschnitten beschrieben. Allgemeine Informationen zu Handles finden Sie unter [Handles](../../../odbc/reference/develop-app/handles.md).  
  
 Eine Anwendung sollte kein Handle verwenden, nachdem es freigegeben wurde. Der Treiber-Manager überprüft nicht die Gültigkeit eines Handles in einem Funktionsaufruf.  
  
## <a name="freeing-an-environment-handle"></a>Befreien eines Umgebungsgriffs  
 Bevor **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_ENV aufruft, muss eine Anwendung **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DBC für alle Verbindungen aufrufen, die unter der Umgebung zugewiesen sind. Andernfalls gibt der Aufruf von **SQLFreeHandle** SQL_ERROR und die Umgebung zurück, und jede aktive Verbindung bleibt gültig. Weitere Informationen finden Sie unter [Umgebungshandles](../../../odbc/reference/develop-app/environment-handles.md) und [Zuweisen des Umgebungshandles](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Wenn es sich bei der Umgebung um eine freigegebene Umgebung handelt, hat die Anwendung, die **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_ENV aufruft, nach dem Aufruf keinen Zugriff mehr auf die Umgebung, aber die Ressourcen der Umgebung werden nicht notwendigerweise freigegeben. Der Aufruf von **SQLFreeHandle** dekrementiert die Referenzanzahl der Umgebung. Die Referenzanzahl wird vom Treiber-Manager verwaltet. Wenn sie nicht Null erreicht, wird die freigegebene Umgebung nicht freigegeben, da sie immer noch von einer anderen Komponente verwendet wird. Wenn die Referenzanzahl Null erreicht, werden die Ressourcen der freigegebenen Umgebung freigegeben.  
  
## <a name="freeing-a-connection-handle"></a>Befreien eines Verbindungsgriffs  
 Bevor **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DBC aufruft, muss eine Anwendung **SQLDisconnect** für die Verbindung aufrufen, wenn eine Verbindung für dieses Handle*besteht.* Andernfalls gibt der Aufruf von **SQLFreeHandle** SQL_ERROR zurück, und die Verbindung bleibt gültig.  
  
 Weitere Informationen finden Sie unter [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md) und [Trennen von einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Freigeben eines Anweisungshandles  
 Ein Aufruf von **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_STMT gibt alle Ressourcen frei, die durch einen Aufruf von **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_STMT zugewiesen wurden. Wenn eine Anwendung **SQLFreeHandle** aufruft, um eine Anweisung mit ausstehenden Ergebnissen freizugeben, werden die ausstehenden Ergebnisse gelöscht. Wenn eine Anwendung ein Anweisungshandle freigibt, gibt der Treiber die vier automatisch zugewiesenen Deskriptoren frei, die diesem Handle zugeordnet sind. Weitere Informationen finden Sie unter [Anweisungshandles](../../../odbc/reference/develop-app/statement-handles.md) und [Befreien eines Anweisungshandles](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 Beachten Sie, dass **SQLDisconnect** automatisch alle Anweisungen und Deskriptoren löscht, die für die Verbindung geöffnet sind.  
  
## <a name="freeing-a-descriptor-handle"></a>Befreien eines Deskriptor-Handles  
 Ein Aufruf von **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DESC gibt das Deskriptorhandle in *Handle*frei. Der Aufruf von **SQLFreeHandle** gibt keinen von der Anwendung zugewiesenen Speicher frei, auf den möglicherweise ein Zeigerfeld (einschließlich SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR) eines Deskriptordatensatzes von *Handle*verweist. Der vom Treiber zugewiesene Speicher für Felder, die keine Zeigerfelder sind, wird freigegeben, wenn das Handle freigegeben wird. Wenn ein vom Benutzer zugewiesenes Deskriptor-Handle freigegeben wird, werden alle Anweisungen, denen das freigegebene Handle zugeordnet wurde, zu ihren jeweiligen automatisch zugewiesenen Deskriptorhandles zurückgesetzt.  
  
> [!NOTE]
>  ODBC 2 *.x-Treiber* unterstützen das Freiwerden von Deskriptor-Handles nicht, genauso wie sie das Zuweisen von Deskriptorhandles nicht unterstützen.  
  
 Beachten Sie, dass **SQLDisconnect** automatisch alle Anweisungen und Deskriptoren löscht, die für die Verbindung geöffnet sind. Wenn eine Anwendung ein Anweisungshandle freigibt, gibt der Treiber alle automatisch generierten Deskriptoren frei, die diesem Handle zugeordnet sind.  
  
 Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
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
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuweisen eines Griffs|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCance-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Festlegen eines Cursornamens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md)
