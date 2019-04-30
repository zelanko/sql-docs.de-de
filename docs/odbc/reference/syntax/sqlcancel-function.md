---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b9d0c756db7f84e6bcec46a61ef805f885f39d28
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63258873"
---
# <a name="sqlcancel-function"></a>SQLCancel-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLCancel** bricht die Verarbeitung in einer Anweisung.  
  
 Verwenden Sie zum Abbrechen der Verarbeitung einer Verbindung oder einer Anweisung [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLCancel(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCancel** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLCancel** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) im Argument  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLCancel** Funktion aufgerufen wurde.<br /><br /> (DM) Abbruchvorgang ist fehlgeschlagen, da ein asynchroner Vorgang für ein Verbindungshandle ausgeführt wird, die zugeordnet wird *StatementHandle*.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY018|Cancel-Anforderung wurde vom Server abgelehnt|Der Server hat die Anforderung zum Abbrechen abgelehnt.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 **SQLCancel** können die folgenden Typen von Verarbeitung in einer Anweisung Abbrechen:  
  
-   Eine Funktion, die asynchron auf die Anweisung ausgeführt werden.  
  
-   Eine Funktion in einer Anweisung, die Daten benötigt.  
  
-   Eine Funktion, die bei der Anweisung in einem anderen Thread ausgeführt wird.  
  
 In ODBC 2. *x*, wenn eine Anwendung ruft **SQLCancel** Wenn in der Anweisung keine Verarbeitung erfolgt **SQLCancel** hat dieselbe Wirkung wie das **SQLFreeStmt** mit der Option SQL_CLOSE; Dieses Verhalten ist nur der Vollständigkeit halber definiert, und Anwendungen sollten Aufrufen **SQLFreeStmt** oder **SQLCloseCursor** um Cursor zu schließen.  
  
 Wenn **SQLCancel** aufgerufen, um eine Funktion, die asynchrone Ausführung in einer Anweisung oder eine Funktion in einer Anweisung, dass Anforderungen Daten DiagnoseDatensätze bereitgestellt, die von der Funktion, die abgebrochen wird deaktiviert sind, abzubrechen und **SQLCancel**  stellt eine eigene DiagnoseDatensätze; Wenn **SQLCancel** wird aufgerufen, um eine Funktion in einer Anweisung in einem anderen Thread zu kündigen, allerdings es die Diagnose löscht nicht die Datensätze des abgebrochen-Funktion und wird nicht Stellen Sie eine eigene DiagnoseDatensätze.  
  
## <a name="canceling-asynchronous-processing"></a>Abbruch asynchroner Verarbeitung  
 Nachdem eine Anwendung eine Funktion asynchron aufruft, ruft es die Funktion, um zu bestimmen, ob die Verarbeitung abgeschlossen wurde. Wenn die Funktion immer noch verarbeitet wird, gibt es SQL_STILL_EXECUTING zurück. Wenn die Funktion die Verarbeitung abgeschlossen ist, gibt es einen anderen Code zurück.  
  
 Nach einem der Funktion, die SQL_STILL_EXECUTING zurückgibt Aufruf, kann eine Anwendung aufrufen **SQLCancel** zum Abbrechen der Funktion. Der Treiber gibt SQL_SUCCESS zurück, wenn die Cancel-Anforderung erfolgreich ist, befindet. Diese Meldung, nicht dass die Funktion tatsächlich abgebrochen wurde; Er gibt an, dass die Cancel-Anforderung verarbeitet wurde. Ist treiberabhängig und datenquellenabhängig, wann und ob die Funktion tatsächlich abgebrochen wird. Die Anwendung muss weiterhin die ursprüngliche Funktion aufrufen, bis der Rückgabecode nicht SQL_STILL_EXECUTING ist. Wenn die Funktion wurde erfolgreich abgebrochen wurde, ist der Rückgabecode SQL_ERROR zurück, und SQLSTATE HY008 (der Vorgang wurde abgebrochen). Wenn die Funktion die normale Verarbeitung abgeschlossen hat, ist der Rückgabecode SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, wenn die Funktion erfolgreich ausgeführt wurde oder SQL_ERROR und ein SQLSTATE als HY008 (der Vorgang wurde abgebrochen.) Wenn die Funktion fehlgeschlagen ist.  
  
> [!NOTE]  
>  In einem Aufruf von ODBC 3.5 **SQLCancel** Wenn keine Verarbeitung auf die Anweisung ausgeführt werden wird nicht als behandelt **SQLFreeStmt** mit der Option SQL_CLOSE enthält, jedoch ist Sie gar keine Auswirkungen. Um einen Cursor zu schließen, eine Anwendung aufrufen sollten **SQLCloseCursor**, nicht **SQLCancel**.  
  
 Weitere Informationen zur asynchronen Verarbeitung finden Sie unter [asynchrone Ausführung](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).  
  
## <a name="canceling-functions-that-need-data"></a>Abbrechen von Funktionen, die Daten benötigen.  
 Nach dem **SQLExecute** oder **SQLExecDirect** wird SQL_NEED_DATA zurückgegeben. und bevor die Daten für alle Data-at-Execution-Parameter gesendet wurde, kann eine Anwendung aufrufen **SQLCancel** um die Ausführung der Anweisung zu stornieren. Nachdem die Anweisung abgebrochen wurde, kann die Anwendung aufrufen **SQLExecute** oder **SQLExecDirect** erneut aus. Weitere Informationen finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Nach dem **SQLBulkOperations** oder **SQLSetPos** wird SQL_NEED_DATA zurückgegeben. und bevor die Daten für alle Data-at-Execution-Spalten gesendet wurde, kann eine Anwendung aufrufen **SQLCancel** um den Vorgang abzubrechen. Nachdem der Vorgang abgebrochen wurde, kann die Anwendung aufrufen **SQLBulkOperations** oder **SQLSetPos** erneut Abbrechen wirkt sich nicht den Cursorstatus oder der aktuellen Cursorposition. Weitere Informationen finden Sie unter [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md) oder [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
## <a name="canceling-functions-executing-on-another-thread"></a>Funktionen, die Ausführung auf einem anderen Thread abgebrochen  
 In einer multithread-Anwendung kann die Anwendung eine Funktion Abbrechen, die auf einem anderen Thread ausgeführt wird. Die Funktion ruft die Anwendung Abbrechen **SQLCancel** mit dasselbe Anweisungshandle, die von der Zielfunktion, sondern in einem anderen Thread verwendet. Wie die Funktion abgebrochen wird, hängt von der Treiber und das Betriebssystem. Wie Sie eine Funktion asynchron den Rückgabecode der Abbruch der **SQLCancel** gibt nur an, ob der Treiber die Anforderung erfolgreich verarbeitet. Nur SQL_SUCCESS oder SQL_ERROR kann zurückgegeben werden soll. Es wird keine Diagnoseinformationen zurückgegeben. Wenn die ursprüngliche Funktion abgebrochen wird, gibt SQL_ERROR zurück, und SQLSTATE HY008 (der Vorgang wurde abgebrochen).  
  
 Wenn eine SQL-Anweisung wird ausgeführt, wenn **SQLCancel** aufgerufen wird, in einem anderen Thread zum Abbrechen der anweisungsausführung, es ist möglich, für die Ausführung erfolgreich ist und return SQL_SUCCESS zurück, während die "Abbrechen" ist auch erfolgreich ist. In diesem Fall wird der Treiber-Manager davon ausgegangen, dass der Cursor geöffnet wird, indem Sie Ausführung der Anweisung durch die "Abbrechen", geschlossen wird, sodass die Anwendung nicht den Cursor zu verwenden.  
  
 Weitere Informationen zu threading, finden Sie unter [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer, an einen parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Ausführen von Massenladen Einfüge- und Updatevorgänge|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Bricht eine Funktion, die asynchrone Ausführung für ein Verbindungshandle außerdem auf die Funktionen des **SQLCancel**.|[SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Freigeben eines Anweisungshandles|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Erhalten ein Feld ein Diagnosedatensatz oder ein Feld des Diagnose-Headers|[SQLGetDiagField-Funktion](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
|Abrufen von mehreren Feldern einer Datenstruktur für die Diagnose|[SQLGetDiagRec-Funktion](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|  
|Den nächsten Parameter zum Senden von Daten für die Rückgabe|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Senden von Daten von Parametern zum Zeitpunkt der Ausführung|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Positionieren den Cursor in einem Rowset, das Aktualisieren von Daten im Rowset aktualisieren oder Löschen von Daten im Resultset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
