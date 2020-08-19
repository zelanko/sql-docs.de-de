---
description: SQLCancel-Funktion
title: SQLCancel-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCancel
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCancel
helpviewer_keywords:
- SQLCancel function [ODBC]
ms.assetid: ac0b5972-627f-4440-8c5a-0e8da728726d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 040cd9034a8f754a26f577b7efd6e1307e4c90c5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448872"
---
# <a name="sqlcancel-function"></a>SQLCancel-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLCancel** bricht die Verarbeitung für eine-Anweisung ab.  
  
 Verwenden Sie die [sqlcancelhandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md), um die Verarbeitung für eine Verbindung oder Anweisung abzubrechen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCancel(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCancel** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLCancel** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) im Argument * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLCancel** -Funktion aufgerufen wurde.<br /><br /> (DM)-Abbruch Vorgang fehlgeschlagen, da ein asynchroner Vorgang für ein Verbindungs Handle, das *StatementHandle*zugeordnet ist, ausgeführt wird.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY018|Der Server hat die Abbruch Anforderung abgelehnt|Der Server hat die Abbruch Anforderung abgelehnt.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 **SQLCancel** kann die folgenden Verarbeitungs Typen für eine-Anweisung abbrechen:  
  
-   Eine Funktion, die asynchron für die Anweisung ausgeführt wird.  
  
-   Eine Funktion für eine Anweisung, die Daten benötigt.  
  
-   Eine Funktion, die in der-Anweisung auf einem anderen Thread ausgeführt wird.  
  
 In ODBC 2. *x*: Wenn eine Anwendung **SQLCancel** aufruft, wenn keine Verarbeitung in der Anweisung erfolgt, hat **SQLCancel** dieselbe Auswirkung wie **SQLFreeStmt** mit der Option SQL_CLOSE. Dieses Verhalten wird nur aus Gründen der Vollständigkeit definiert, und Anwendungen sollten **SQLFreeStmt** oder **SQLCloseCursor zum Schließen von Cursorn** aufruft.  
  
 Wenn **SQLCancel** aufgerufen wird, um eine Funktion abzubrechen, die asynchron in einer-Anweisung ausgeführt wird, oder eine Funktion für eine Anweisung, die Daten benötigt, werden Diagnosedaten Sätze, die von der abzubrechenden Funktion gepostet wurden, gelöscht, und **SQLCancel** sendet eigene Diagnosedaten Sätze. Wenn **SQLCancel** aufgerufen wird, um eine Funktion abzubrechen, die für eine Anweisung in einem anderen Thread ausgeführt wird, werden die Diagnosedaten Sätze der abgebrochenen Funktion nicht gelöscht, und es werden keine eigenen Diagnosedaten Sätze bereitgestellt.  
  
## <a name="canceling-asynchronous-processing"></a>Abbrechen der asynchronen Verarbeitung  
 Nachdem eine Anwendung eine Funktion asynchron aufgerufen hat, ruft Sie die Funktion wiederholt auf, um zu bestimmen, ob Sie die Verarbeitung abgeschlossen hat. Wenn die Funktion noch verarbeitet wird, wird SQL_STILL_EXECUTING zurückgegeben. Wenn die Funktion die Verarbeitung abgeschlossen hat, wird ein anderer Code zurückgegeben.  
  
 Nach jedem Aufrufe der Funktion, die SQL_STILL_EXECUTING zurückgibt, kann eine Anwendung **SQLCancel** zum Abbrechen der Funktion aufruft. Wenn die Abbruch Anforderung erfolgreich ist, gibt der Treiber SQL_SUCCESS zurück. Diese Meldung weist nicht darauf hin, dass die Funktion tatsächlich abgebrochen wurde. Gibt an, dass die Abbruch Anforderung verarbeitet wurde. Wenn oder wenn die Funktion tatsächlich abgebrochen wird, ist Treiber abhängig und Datenquellen abhängig. Die Anwendung muss die ursprüngliche Funktion weiterhin aufzurufen, bis der Rückgabecode nicht SQL_STILL_EXECUTING ist. Wenn die Funktion erfolgreich abgebrochen wurde, wird der Rückgabecode SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen). Wenn die Funktion die normale Verarbeitung abgeschlossen hat, wird der Rückgabecode SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, wenn die Funktion erfolgreich war, oder SQL_ERROR und ein anderer SQLSTATE als HY008 (Vorgang abgebrochen), wenn die Funktion fehlgeschlagen ist.  
  
> [!NOTE]  
>  In ODBC 3,5 wird ein **SQLCancel** -Befehl, wenn keine Verarbeitung in der Anweisung ausgeführt wird, nicht als **SQLFreeStmt** mit der SQL_CLOSE-Option behandelt, aber hat überhaupt keine Auswirkung. Um einen Cursor zu schließen, sollte eine Anwendung **SQLCloseCursor**, nicht **SQLCancel**, abrufen.  
  
 Weitere Informationen zur asynchronen Verarbeitung finden Sie unter [asynchrone Ausführung](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).  
  
## <a name="canceling-functions-that-need-data"></a>Abbrechen von Funktionen, die Daten benötigen  
 Nachdem **SQLExecute** oder **SQLExecDirect** SQL_NEED_DATA zurückgegeben und bevor Daten für alle Data-at-Execution-Parameter gesendet wurden, kann eine Anwendung **SQLCancel** zum Abbrechen der Anweisungs Ausführung aufzurufen. Nachdem die Anweisung abgebrochen wurde, kann die Anwendung **SQLExecute** oder **SQLExecDirect** erneut abrufen. Weitere Informationen finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Nachdem **SQLBulkOperations** oder **SQLSetPos** SQL_NEED_DATA zurückgegeben und bevor Daten für alle Data-at-Execution-Spalten gesendet wurden, kann eine Anwendung **SQLCancel** aufrufen, um den Vorgang abzubrechen. Nachdem der Vorgang abgebrochen wurde, kann die Anwendung **SQLBulkOperations** oder **SQLSetPos** erneut aufrufen. Das Abbrechen wirkt sich nicht auf den Cursor Zustand oder die aktuelle Cursorposition aus. Weitere Informationen finden Sie unter [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md) oder [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="canceling-functions-executing-on-another-thread"></a>Abbrechen von Funktionen, die in einem anderen Thread ausgeführt werden  
 In einer Multithreadanwendung kann die Anwendung eine Funktion abbrechen, die in einem anderen Thread ausgeführt wird. Um die Funktion abzubrechen, ruft die Anwendung **SQLCancel** mit dem gleichen Anweisungs Handle auf, das von der Zielfunktion verwendet wird, jedoch in einem anderen Thread. Wie die Funktion abgebrochen wird, hängt vom Treiber und dem Betriebssystem ab. Wenn eine Funktion, die asynchron ausgeführt wird, abgebrochen wird, gibt der Rückgabecode von **SQLCancel** nur an, ob der Treiber die Anforderung erfolgreich verarbeitet hat. Es können nur SQL_SUCCESS oder SQL_ERROR zurückgegeben werden. Es werden keine Diagnoseinformationen zurückgegeben. Wenn die ursprüngliche Funktion abgebrochen wird, gibt Sie SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen) zurück.  
  
 Wenn eine SQL-Anweisung ausgeführt wird, wenn **SQLCancel** in einem anderen Thread aufgerufen wird, um die Ausführung der Anweisung abzubrechen, ist es möglich, dass die Ausführung erfolgreich ist und SQL_SUCCESS zurückgibt, während der Abbruch ebenfalls erfolgreich ist. In diesem Fall geht der Treiber-Manager davon aus, dass der von der Anweisungs Ausführung geöffnete Cursor durch Abbrechen geschlossen wird, sodass die Anwendung den Cursor nicht verwenden kann.  
  
 Weitere Informationen zum Threading finden Sie unter [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an einen Parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Ausführen von BULK INSERT-oder Update-Vorgängen|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Bricht eine Funktion ab, die asynchron auf einem Verbindungs Handle ausgeführt wird, sowie die Funktionalität von **SQLCancel**.|[SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Freigeben eines Anweisungs Handles|['SQLFreeStmt'](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Abrufen eines Felds eines Diagnosedaten Satzes oder eines Felds des Diagnose Headers|[SQLGetDiagField-Funktion](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
|Abrufen mehrerer Felder einer Diagnosedaten Struktur|[SQLGetDiagRec-Funktion](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|  
|Zurückgeben des nächsten Parameters zum Senden von Daten|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Senden von Parameterdaten zur Ausführungszeit|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Positionieren des Cursors in einem Rowset, Aktualisieren von Daten im Rowset oder aktualisieren oder Löschen von Daten im Resultset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
