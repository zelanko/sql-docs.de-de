---
title: SQLDisconnect-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDisconnect
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLDisconnect
helpviewer_keywords:
- SQLDisconnect function [ODBC]
ms.assetid: 9e84a58e-db48-4821-a0cd-5c711fcbe36b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5ea73919fbe90719d881fb43108ab1934933708
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301150"
---
# <a name="sqldisconnect-function"></a>SQLDisconnect-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLDisconnect** schließt die Verbindung, die einem bestimmten Verbindungshandle zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLDisconnect(  
     SQLHDBC     ConnectionHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDisconnect** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DBC und einem *Handle* von *ConnectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLDisconnect** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01002|Trennfehler|Während der Trennung ist ein Fehler aufgetreten. Die Trennung war jedoch erfolgreich. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) Die im Argument *ConnectionHandle* angegebene Verbindung war nicht geöffnet.|  
|25000|Ungültiger Transaktionsstatus|Für die verbindung, die durch das Argument ConnectionHandle angegeben *wurde,* wurde eine Transaktion ausgeführt. Die Transaktion bleibt aktiv.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *den ConnectionHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor sie die Ausführung der [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) abbrach, wurde sie auf dem *ConnectionHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *ConnectionHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung von SQLCancelHandle abgeschlossen wurde, wurde **sqlCancelHandle** von einem anderen Thread in einer Multithreadanwendung auf den *ConnectionHandle* aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Eine asynchron ausführende Funktion wurde für einen *StatementHandle* aufgerufen, der dem *ConnectionHandle* zugeordnet war, und wurde noch ausgeführt, als **SQLDisconnect** aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausführende Funktion (nicht diese) wurde für den *ConnectionHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für ein *StatementHandle* aufgerufen, das dem *ConnectionHandle* zugeordnet ist, und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat und die Verbindung noch aktiv ist. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *ConnectionHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Wenn eine Anwendung **SQLDisconnect** aufruft, nachdem **SQLBrowseConnect** SQL_NEED_DATA und bevor sie einen anderen Rückgabecode zurückgibt, bricht der Treiber den Verbindungsbrowsingvorgang ab und gibt die Verbindung in einen nicht verbundenen Zustand zurück.  
  
 Wenn eine Anwendung **SQLDisconnect** aufruft, während dem Verbindungshandle eine unvollständige Transaktion zugeordnet ist, gibt der Treiber SQLSTATE 25000 (Ungültiger Transaktionsstatus) zurück, was angibt, dass die Transaktion unverändert ist und die Verbindung geöffnet ist. Eine unvollständige Transaktion ist eine Transaktion, die nicht mit **SQLEndTran**festgeschrieben oder zurückgesetzt wurde.  
  
 Wenn eine Anwendung **SQLDisconnect** aufruft, bevor sie alle der Verbindung zugeordneten Anweisungen freigegeben hat, gibt der Treiber diese Anweisungen und alle Deskriptoren frei, die explizit für die Verbindung zugewiesen wurden, nachdem er erfolgreich die Verbindung von der Datenquelle getrennt hat. Wenn jedoch eine oder mehrere der Verbindung zugeordnete Anweisungen weiterhin asynchron ausgeführt werden, gibt **SQLDisconnect** SQL_ERROR mit dem SQLSTATE-Wert HY010 (Funktionssequenzfehler) zurück. Außerdem gibt **SQLDisconnect** alle zugeordneten Anweisungen und alle Deskriptoren frei, die explizit für die Verbindung zugewiesen wurden, wenn sich die Verbindung in einem angehaltenen Zustand befindet oder wenn **SQLDisconnect** von **SQLCancelHandle**erfolgreich abgebrochen wurde.  
  
 Informationen dazu, wie eine Anwendung **SQLDisconnect**verwendet, finden Sie unter [Trennen von einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="disconnecting-from-a-pooled-connection"></a>Trennen der Verbindung von einer gepoolten Verbindung  
 Wenn das Verbindungspooling für eine freigegebene Umgebung aktiviert ist und eine Anwendung **SQLDisconnect** für eine Verbindung in dieser Umgebung aufruft, wird die Verbindung an den Verbindungspool zurückgegeben und ist weiterhin für andere Komponenten verfügbar, die dieselbe freigegebene Umgebung verwenden.  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [Beispiel ODBC-Programm](../../../odbc/reference/sample-odbc-program.md), [SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)und [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuweisen eines Griffs|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungszeichenfolge oder ein Dialogfeld|[SQLDriveConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Ausführen eines Commit- oder Rollbackvorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Befreien eines Verbindungsgriffs|[SQLFreeConnect-Funktion](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
