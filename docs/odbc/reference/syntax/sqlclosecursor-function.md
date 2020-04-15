---
title: SQLCloseCursor-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCloseCursor
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLCloseCursor
helpviewer_keywords:
- SQLCloseCursor function [ODBC]
ms.assetid: 05b0a054-e28d-4e16-b5b0-07418486b372
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f2703af46e6043fbadb7d3ceb5c00c565c1f6777
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301300"
---
# <a name="sqlclosecursor-function"></a>SQLCloseCursor-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLCloseCursor** schließt einen Cursor, der für eine Anweisung geöffnet wurde, und verwirft ausstehende Ergebnisse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCloseCursor(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCloseCursor** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLCloseCursor** zurückgegeben werden, und es werden die SQLSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|24.000|Ungültiger Cursorstatus|Im *StatementHandle*war kein Cursor geöffnet. (Dies wird nur von einem ODBC 3 zurückgegeben. *x* x-Treiber.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) Eine asynchron ausführende Funktion wurde für das dem *StatementHandle* zugeordnete Verbindungshandle aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausgeführte Funktion wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 **SQLCloseCursor** gibt SQLSTATE 24000 (Ungültiger Cursorstatus) zurück, wenn kein Cursor geöffnet ist. Das Aufrufen von **SQLCloseCursor** entspricht dem Aufrufen von **SQLFreeStmt** mit der Option SQL_CLOSE, mit der Ausnahme, dass **SQLFreeStmt** mit SQL_CLOSE keine Auswirkungen auf die Anwendung hat, wenn kein Cursor für die Anweisung geöffnet ist, während **SQLCloseCursor** SQLSTATE 24000 (Ungültiger Cursorstatus) zurückgibt.  
  
> [!NOTE]  
>  Wenn ein ODBC 3. *x* Anwendung, die mit einem ODBC 2 arbeitet. *x-Treiber* ruft **SQLCloseCursor** auf, wenn kein Cursor geöffnet ist, SQLSTATE 24000 (Ungültiger Cursorstatus) wird nicht zurückgegeben, da der Treiber-Manager **SQLCloseCursor** **SQLFreeStmt** mit SQL_CLOSE zuordnet.  
  
 Weitere Informationen finden Sie unter [Schließen des Cursors](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) und [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Befreien eines Griffs|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Verarbeiten mehrerer Resultsets|[SQLMoreResults-Funktion](../../../odbc/reference/syntax/sqlmoreresults-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
