---
title: SQLFreeStmt-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e252769c26a5491100094b1243b9c2c6bb67d94d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285700"
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLFreeStmt** stoppt die Verarbeitung, die einer bestimmten Anweisung zugeordnet ist, schließt alle geöffneten Cursor, die der Anweisung zugeordnet sind, verwirft ausstehende Ergebnisse oder gibt optional alle Ressourcen frei, die dem Anweisungshandle zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle  
  
 *Option*  
 [Eingabe] Eine der folgenden Optionen:  
  
 SQL_ CLOSE: Schließt den Cursor, der *StatementHandle* zugeordnet ist (falls einer definiert wurde) und verwirft alle ausstehenden Ergebnisse. Die Anwendung kann diesen Cursor später erneut öffnen, indem sie eine **SELECT-Anweisung** mit den gleichen oder anderen Parameterwerten erneut ausführt. Wenn kein Cursor geöffnet ist, hat diese Option keine Auswirkungen auf die Anwendung. **SQLCloseCursor** kann auch aufgerufen werden, um einen Cursor zu schließen. Weitere Informationen finden Sie unter [Schließen des Cursors](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 SQL_DROP: Diese Option ist veraltet. Ein Aufruf von **SQLFreeStmt** mit der *Option* SQL_DROP wird im Treiber-Manager [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)zugeordnet.  
  
 SQL_UNBIND: Legt das SQL_DESC_COUNT Feld der ARD auf 0 fest und gibt alle Spaltenpuffer frei, die an **SQLBindCol** für den gegebenen *StatementHandle*gebunden sind. Dadurch wird die Bindung der Lesezeichenspalte nicht aufekleben. Dazu wird das SQL_DESC_DATA_PTR der ARD für die Lesezeichenspalte auf NULL gesetzt. Beachten Sie, dass der Vorgang die Bindungen aller Anweisungen beeinflusst, die den Deskriptor gemeinsam verwenden, wenn dieser Vorgang für einen explizit zugewiesenen Deskriptor ausgeführt wird, der von mehr als einer Anweisung gemeinsam genutzt wird. Weitere Informationen finden Sie unter [Übersicht über das Abrufen von Ergebnissen (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 SQL_RESET_PARAMS: Legt das SQL_DESC_COUNT Feld der APD auf 0 fest und gibt alle Parameterpuffer frei, die von **SQLBindParameter** für das gegebene *StatementHandle*festgelegt wurden. Wenn dieser Vorgang für einen explizit zugewiesenen Deskriptor ausgeführt wird, der von mehr als einer Anweisung gemeinsam genutzt wird, wirkt sich dieser Vorgang auf die Bindungen aller Anweisungen aus, die den Deskriptor gemeinsam verwenden. Weitere Informationen finden Sie unter [Bindungsparameter](../../../odbc/reference/develop-app/binding-parameters-odbc.md).  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFreeStmt** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLFreeStmt** zurückgegeben werden, und es werden die sqlSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als **SQLFreeStmt** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, wobei *Option* auf SQL_RESET_PARAMS festgelegt wurde, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY092|Optionstyp a-range|(DM) Der für das Argument *Option* angegebene Wert war nicht:<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Das Aufrufen von **SQLFreeStmt** mit der Option SQL_CLOSE entspricht dem Aufrufen von **SQLCloseCursor**, mit der Ausnahme, dass **SQLFreeStmt** mit SQL_CLOSE die Anwendung nicht beeinflusst, wenn kein Cursor für die Anweisung geöffnet ist. Wenn kein Cursor geöffnet ist, gibt ein Aufruf von **SQLCloseCursor** SQLSTATE 24000 (Ungültiger Cursorstatus) zurück.  
  
 Eine Anwendung sollte kein Anweisungshandle verwenden, nachdem es freigegeben wurde. Der Treiber-Manager überprüft nicht die Gültigkeit eines Handles in einem Funktionsaufruf.  
  
## <a name="example"></a>Beispiel  
 Es ist eine gute Programmierpraxis, Griffe freizugeben. Der Einfachheit halber enthält das folgende Beispiel jedoch keinen Code, der zugewiesene Handles freigibt. Ein Beispiel für das Freiwerden von Handles finden Sie unter [SQLFreeHandle Function](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
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
|Zuweisen eines Griffs|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Schließen eines Cursors|[SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Befreien eines Griffs|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Festlegen eines Cursornamens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
