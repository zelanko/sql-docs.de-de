---
title: SQLFreeStmt-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeStmt
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFreeStmt
helpviewer_keywords:
- SQLFreeStmt function [ODBC]
ms.assetid: 03408162-8b63-4470-90c4-e6c7d8d33892
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6141f3efe357bfb3f14c04aa2f6760e9470649a6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68345150"
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLFreeStmt** beendet die Verarbeitung, die einer bestimmten Anweisung zugeordnet ist, schließt alle geöffneten Cursor, die der Anweisung zugeordnet sind, verwirft ausstehende Ergebnisse oder gibt optional alle dem Anweisungs Handle zugeordneten Ressourcen frei.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle  
  
 *Option*  
 Der Eine der folgenden Optionen:  
  
 SQL_ Close: schließt den mit *StatementHandle* verknüpften Cursor (sofern definiert) und verwirft alle ausstehenden Ergebnisse. Die Anwendung kann diesen Cursor später erneut öffnen, indem eine **Select** -Anweisung mit denselben oder anderen Parameterwerten erneut ausgeführt wird. Wenn kein Cursor geöffnet ist, hat diese Option keine Auswirkung auf die Anwendung. **SQLCloseCursor** kann auch aufgerufen werden, um einen Cursor zu schließen. Weitere Informationen finden Sie unter [Schließen des Cursors](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 SQL_DROP: diese Option ist veraltet. Ein **SQLFreeStmt** -Befehl mit der *Option* SQL_DROP wird im Treiber-Manager [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)zugeordnet.  
  
 SQL_UNBIND: legt das SQL_DESC_COUNT Feld der ARD auf 0 fest und gibt alle von **SQLBindCol** gebundenen Spalten Puffer für das angegebene *StatementHandle*frei. Dadurch wird die Bindung der Lesezeichen Spalte nicht aufgehoben. zu diesem Zweck wird das SQL_DESC_DATA_PTR-Feld der ARD für die Lesezeichen Spalte auf NULL festgelegt. Beachten Sie Folgendes: Wenn dieser Vorgang für einen explizit zugewiesenen Deskriptor ausgeführt wird, der von mehr als einer Anweisung gemeinsam genutzt wird, wirkt sich der Vorgang auf die Bindungen aller Anweisungen aus, die den Deskriptor gemeinsam verwenden. Weitere Informationen finden Sie unter [Übersicht über das Abrufen von Ergebnissen (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 SQL_RESET_PARAMS: legt das SQL_DESC_COUNT-Feld der APD auf 0 fest und gibt alle durch **SQLBindParameter** festgelegten Parameter Puffer für das angegebene *StatementHandle*frei. Wenn dieser Vorgang für einen explizit zugewiesenen Deskriptor ausgeführt wird, der von mehr als einer Anweisung gemeinsam genutzt wird, wirkt sich dieser Vorgang auf die Bindungen aller Anweisungen aus, die den Deskriptor gemeinsam verwenden. Weitere Informationen finden Sie unter [Bindungs Parameter](../../../odbc/reference/develop-app/binding-parameters-odbc.md).  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFreeStmt** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLFreeStmt** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als **SQLFreeStmt** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde mit der *Option* auf SQL_RESET_PARAMS festgelegt, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das *StatementHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY092|Optionstyp außerhalb des gültigen Bereichs|(DM) der für die Argument *Option* angegebene Wert ist nicht:<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Das Aufrufen von **SQLFreeStmt** mit der SQL_CLOSE-Option entspricht dem Aufrufen von **SQLCloseCursor**, mit dem Unterschied, dass **SQLFreeStmt** mit SQL_CLOSE keine Auswirkung auf die Anwendung hat, wenn kein Cursor in der Anweisung geöffnet ist. Wenn kein Cursor geöffnet ist, gibt ein **SQLCloseCursor** -Befehl SQLSTATE 24000 (Ungültiger Cursor Zustand) zurück.  
  
 Eine Anwendung sollte kein Anweisungs Handle verwenden, nachdem Sie freigegeben wurde. der Treiber-Manager überprüft nicht die Gültigkeit eines Handles in einem Funktions Aufruf.  
  
## <a name="example"></a>Beispiel  
 Es ist eine gute Programmier Übung, Handles freizugeben. Der Einfachheit halber enthält das folgende Beispiel jedoch keinen Code, der zugeordnete Handles freigibt. Ein Beispiel für das Freigeben von Handles finden Sie unter [SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
```cpp  
// SQLFreeStmt.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
   retCode = SQLFreeStmt(hstmt, SQL_UNBIND);  
   retCode = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuordnen eines Handles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Schließen eines Cursors|[SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Freigeben eines Handles|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Festlegen eines Cursor namens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
