---
title: SQLFreeStmt-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeStmt
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFreeStmt
helpviewer_keywords:
- SQLFreeStmt function [ODBC]
ms.assetid: 03408162-8b63-4470-90c4-e6c7d8d33892
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 83e62430e55a82c904e6cae996538225ac8282b8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006221"
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLFreeStmt** beendet die Verarbeitung einer bestimmten Anweisung zugeordneten, schließt alle geöffneten Cursor verknüpft ist, mit der Anweisung, verwirft ausstehende Ergebnisse zu erzielen, oder gibt optional das Anweisungshandle zugeordnete Ressourcen frei.  
  
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
  
 SQL_ SCHLIESSEN: Schließt den Cursor zugeordnet *StatementHandle* (falls definiert), und alle ausstehende Ergebnisse verworfen. Die Anwendung kann erneut öffnen dieses Cursors später durch Ausführen einer **wählen** Anweisung erneut mit demselben oder einem anderen Parameterwerte. Wenn keine Cursor geöffnet ist, hat diese Option keine Auswirkungen auf die Anwendung an. **SQLCloseCursor** auch aufgerufen werden, um einen Cursor zu schließen. Weitere Informationen finden Sie unter [Schließen des Cursors](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 SQL_DROP: Diese Option ist veraltet. Einen Aufruf von **SQLFreeStmt** mit einer *Option* von SQL_DROP zugeordnet wird, im Treiber-Manager auf [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
 SQL_UNBIND: Legt das SQL_DESC_COUNT-Feld, der die ARD 0 ist, Freigeben von Puffern für alle Spalten gebunden **SQLBindCol** für den angegebenen *StatementHandle*. Dies ist kein Aufheben der Bindung der Lesezeichenspalte; zu diesem Zweck wird von der ARD für die Lesezeichenspalte das SQL_DESC_DATA_PTR-Feld auf NULL festgelegt. Beachten Sie, dass wenn Sie diesen Vorgang für einen explizit zugewiesenen Deskriptor ausgeführt wird, die von mehr als eine Anweisung verwendet wird, der Vorgang die Bindungen aller Anweisungen auswirkt, die den Deskriptor gemeinsam nutzen. Weitere Informationen finden Sie unter [Übersicht von Ergebnissen ' abrufen ' (Standard)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 SQL_RESET_PARAMS: Legt das SQL_DESC_COUNT-Feld der APD auf 0 (null) festlegen, indem alle Parameter-Puffer freigeben **SQLBindParameter** für den angegebenen *StatementHandle*. Wenn dieser Vorgang für einen explizit zugewiesenen Deskriptor ausgeführt wird, die von mehr als eine Anweisung verwendet wird, wirkt sich dieser Vorgang die Bindungen der alle Anweisungen, die den Deskriptor gemeinsam nutzen. Weitere Informationen finden Sie unter [Bindungsparameter](../../../odbc/reference/develop-app/binding-parameters-odbc.md).  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLFreeStmt** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLFreeStmt** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn **SQLFreeStmt** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion wurde mit dem Namen *Option* auf SQL_RESET_PARAMS festgelegt werden, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY092|Optionstyp außerhalb des gültigen Bereichs|(DM) der Wert für das Argument angegebene *Option* war nicht:<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Aufrufen von **SQLFreeStmt** Option entspricht dem Aufruf mit der SQL_CLOSE **SQLCloseCursor**, außer dass **SQLFreeStmt** mit SQL_CLOSE hat keine Auswirkungen auf die Anwendung Wenn keine Cursor geöffnet, in der Anweisung ist. Wenn keine Cursor zu öffnen, einen Aufruf von **SQLCloseCursor** SQLSTATE 24000 (Ungültiger Cursorstatus) zurückgibt.  
  
 Ein Anweisungshandle sollten von einer Anwendung nicht verwendet werden, nachdem dieser freigegeben wurde. der Treiber-Manager überprüft nicht die Gültigkeit eines Handles in einem Funktionsaufruf.  
  
## <a name="example"></a>Beispiel  
 Es ist ein gutes Programmierverfahren, Handles freizugeben. Jedoch aus Gründen der Einfachheit umfasst im folgende Beispiel keinen Code, der freigibt Handles zugeordnet. Ein Beispiel für das Freigeben des Handles, finden Sie unter [SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ein Handle zuordnen|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Schließen eines Cursors|[SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Ein Handle freigeben|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Ein Cursorname festlegen|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
