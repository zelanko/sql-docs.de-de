---
title: SQLCancel-Funktion | Microsoft Docs
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
ms.openlocfilehash: fcc2afce495a1481692ba1f20162a2df5d9a9458
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301310"
---
# <a name="sqlcancel-function"></a>SQLCancel-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLCancel** bricht die Verarbeitung für eine Anweisung ab.  
  
 Um die Verarbeitung für eine Verbindung oder Anweisung abzubrechen, verwenden Sie [die SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCancel(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCancel** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLCancel** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) im Argument * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLCancel-Funktion** aufgerufen wurde.<br /><br /> (DM) Fehler beim Abbrechen, da ein asynchroner Vorgang für ein Verbindungshandle ausgeführt wird, das *StatementHandle*zugeordnet ist.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY018|Server hat Abbruchanforderung abgelehnt|Der Server hat die Abbruchanforderung abgelehnt.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 **SQLCancel** kann die folgenden Verarbeitungstypen für eine Anweisung abbrechen:  
  
-   Eine Funktion, die asynchron für die Anweisung ausgeführt wird.  
  
-   Eine Funktion für eine Anweisung, die Daten benötigt.  
  
-   Eine Funktion, die für die Anweisung in einem anderen Thread ausgeführt wird.  
  
 In ODBC 2. *x*, wenn eine Anwendung **SQLCancel** aufruft, wenn keine Verarbeitung für die Anweisung durchgeführt wird, hat **SQLCancel** denselben Effekt wie **SQLFreeStmt** mit der Option SQL_CLOSE. Dieses Verhalten ist nur aus Gründen der Vollständigkeit definiert, und Anwendungen sollten **SQLFreeStmt** oder **SQLCloseCursor** aufrufen, um Cursor zu schließen.  
  
 Wenn **SQLCancel** aufgerufen wird, eine Funktion, die asynchron in einer Anweisung oder einer Funktion für eine Anweisung ausgeführt wird, die Daten benötigt, abzubrechen, werden Diagnosedatensätze, die von der abgebrochenen Funktion gesendet werden, gelöscht, und **SQLCancel** veröffentlicht seine eigenen Diagnosedatensätze. Wenn **SQLCancel** aufgerufen wird, eine Funktion abzubrechen, die für eine Anweisung in einem anderen Thread ausgeführt wird, werden die Diagnosedatensätze der abgebrochenen Funktion nicht gelöscht und keine eigenen Diagnosedatensätze gesendet.  
  
## <a name="canceling-asynchronous-processing"></a>Abbrechen der asynchronen Verarbeitung  
 Nachdem eine Anwendung eine Funktion asynchron aufruft, ruft sie die Funktion wiederholt auf, um zu bestimmen, ob die Verarbeitung abgeschlossen ist. Wenn die Funktion noch verarbeitet wird, gibt sie SQL_STILL_EXECUTING zurück. Wenn die Verarbeitung abgeschlossen ist, gibt sie einen anderen Code zurück.  
  
 Nach jedem Aufruf der Funktion, die SQL_STILL_EXECUTING zurückgibt, kann eine Anwendung **SQLCancel** aufrufen, um die Funktion abzubrechen. Wenn die Abbruchanforderung erfolgreich ist, gibt der Treiber SQL_SUCCESS zurück. Diese Meldung gibt nicht an, dass die Funktion tatsächlich abgebrochen wurde. Es gibt an, dass die Abbruchanforderung verarbeitet wurde. Wann oder ob die Funktion tatsächlich abgebrochen wird, ist treiberabhängig und datenquellenabhängig. Die Anwendung muss weiterhin die ursprüngliche Funktion aufrufen, bis der Rückgabecode nicht SQL_STILL_EXECUTING wird. Wenn die Funktion erfolgreich abgebrochen wurde, wird der Rückgabecode SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen). Wenn die Funktion die normale Verarbeitung abgeschlossen hat, wird der Rückgabecode SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO wenn die Funktion erfolgreich war oder SQL_ERROR und ein anderes SQLSTATE als HY008 (Vorgang abgebrochen), wenn die Funktion fehlgeschlagen ist.  
  
> [!NOTE]  
>  In ODBC 3.5 wird ein Aufruf von **SQLCancel,** wenn keine Verarbeitung für die Anweisung ausgeführt wird, nicht als **SQLFreeStmt** mit der option SQL_CLOSE behandelt, hat jedoch überhaupt keine Auswirkungen. Um einen Cursor zu schließen, sollte eine Anwendung **SQLCloseCursor**aufrufen, nicht **SQLCancel**.  
  
 Weitere Informationen zur asynchronen Verarbeitung finden Sie unter [Asynchrone Ausführung](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).  
  
## <a name="canceling-functions-that-need-data"></a>Abbrechen von Funktionen, die Daten benötigen  
 Nachdem **SQLExecute** oder **SQLExecDirect** SQL_NEED_DATA zurückgegeben haben und bevor Daten für alle Daten-at-Execution-Parameter gesendet wurden, kann eine Anwendung **SQLCancel** aufrufen, um die Anweisungsausführung abzubrechen. Nachdem die Anweisung abgebrochen wurde, kann die Anwendung **SQLExecute** oder **SQLExecDirect** erneut aufrufen. Weitere Informationen finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Nachdem **SQLBulkOperations** oder **SQLSetPos** SQL_NEED_DATA zurückgegeben haben und bevor Daten für alle Data-at-Execution-Spalten gesendet wurden, kann eine Anwendung **SQLCancel** aufrufen, um den Vorgang abzubrechen. Nachdem der Vorgang abgebrochen wurde, kann die Anwendung **SQLBulkOperations** oder **SQLSetPos** erneut aufrufen. der Abbruch wirkt sich nicht auf den Cursorzustand oder die aktuelle Cursorposition aus. Weitere Informationen finden Sie unter [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md) oder [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="canceling-functions-executing-on-another-thread"></a>Abbrechen von Funktionen, die in einem anderen Thread ausgeführt werden  
 In einer Multithreadanwendung kann die Anwendung eine Funktion abbrechen, die auf einem anderen Thread ausgeführt wird. Um die Funktion abzubrechen, ruft die Anwendung **SQLCancel** mit demselben Anweisungshandle auf, das von der Zielfunktion verwendet wird, jedoch in einem anderen Thread. Wie die Funktion abgebrochen wird, hängt vom Treiber und vom Betriebssystem ab. Wie beim Abbrechen einer funktional ausgeführten Funktion gibt der Rückgabecode von **SQLCancel** nur an, ob der Treiber die Anforderung erfolgreich verarbeitet hat. Nur SQL_SUCCESS oder SQL_ERROR können zurückgegeben werden; Es werden keine Diagnoseinformationen zurückgegeben. Wenn die ursprüngliche Funktion abgebrochen wird, wird SQL_ERROR und SQLSTATE HY008 zurückgegeben (Vorgang abgebrochen).  
  
 Wenn eine SQL-Anweisung ausgeführt wird, wenn **SQLCancel** in einem anderen Thread aufgerufen wird, um die Anweisungsausführung abzubrechen, kann die Ausführung erfolgreich ausgeführt und SQL_SUCCESS zurückgegeben werden, während der Abbruch ebenfalls erfolgreich ist. In diesem Fall geht der Treiber-Manager davon aus, dass der cursor, der von der Anweisungsausführung geöffnet wird, durch den Abbruch geschlossen wird, sodass die Anwendung den Cursor nicht verwenden kann.  
  
 Weitere Informationen zum Gewinden finden Sie unter [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an einen Parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Ausführen von Masseneinfüge- oder Aktualisierungsvorgängen|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Bricht eine Funktion ab, die asynchron auf einem Verbindungshandle ausgeführt wird, zusätzlich zur Funktionalität von **SQLCancel**.|[SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Befreien eines Anweisungshandles|['SQLFreeStmt'](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Abrufen eines Felds eines Diagnosedatensatzes oder eines Felds des Diagnoseheaders|[SQLGetDiagField-Funktion](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
|Abrufen mehrerer Felder einer Diagnosedatenstruktur|[SQLGetDiagRec-Funktion](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|  
|Zurückgeben des nächsten Parameters zum Senden von Daten für|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Senden von Parameterdaten zur Ausführungszeit|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Positionieren des Cursors in einem Rowset, Aktualisieren von Daten im Rowset oder Aktualisieren oder Löschen von Daten im Resultset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
