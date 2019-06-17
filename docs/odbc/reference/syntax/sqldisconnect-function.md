---
title: SQLDisconnect-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDisconnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDisconnect
helpviewer_keywords:
- SQLDisconnect function [ODBC]
ms.assetid: 9e84a58e-db48-4821-a0cd-5c711fcbe36b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 444e41699c1a61acb82acc419a2f23db6142f7bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537562"
---
# <a name="sqldisconnect-function"></a>SQLDisconnect-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLDisconnect** schließt die Verbindung eines bestimmten Verbindungshandles zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLDisconnect(  
     SQLHDBC     ConnectionHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDisconnect** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_DBC und *behandeln* von *ConnectionHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLDisconnect** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01002|Fehler beim Trennen|Fehler bei der die Trennung der Verbindung. Allerdings wurde erfolgreich die Trennung der Verbindung ein. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) die Verbindung im Argument angegebene *ConnectionHandle* konnte nicht geöffnet werden.|  
|25000|Ungültiger Transaktionsstatus|Es wurde eine Transaktion im Prozess für die Verbindung, die durch das Argument angegebenen *ConnectionHandle*. Die Transaktion bleibt aktiv.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *ConnectionHandle*. Die Funktion wurde aufgerufen, und vor dem Ausführen von hat [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) aufgerufen wurde, auf die *ConnectionHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *ConnectionHandle*.<br /><br /> Die Funktion aufgerufen wurde und bevor sie die Ausführung beendet **SQLCancelHandle** aufgerufen wurde, auf die *ConnectionHandle* von einem anderen Thread in einer multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, eine *StatementHandle* zugeordneten der *ConnectionHandle* und wurde noch ausgeführt, wenn **SQLDisconnect** wurde wird aufgerufen.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *ConnectionHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, eine *StatementHandle*  zugeordneten der *ConnectionHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat, und die Verbindung noch aktiv ist. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *ConnectionHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Wenn eine Anwendung ruft **SQLDisconnect** nach **SQLBrowseConnect** wird SQL_NEED_DATA zurückgegeben. und bevor sie einen anderen Rückgabecode zurückgibt, wird der Treiber bricht die Verbindung mit dem Durchsuchen der Prozess ab und gibt zurück die Verbindung mit einem nicht verbundenen Zustand.  
  
 Wenn eine Anwendung ruft **SQLDisconnect** zwar gibt es eine unvollständige Transaktion, die mit dem Verbindungshandle verknüpft ist, gibt der Treiber SQLSTATE 25000 (Ungültiger Transaktionsstatus), gibt an, dass die Transaktion nicht geändert wird. und die Verbindung geöffnet ist. Eine unvollständige Transaktion ist eine, die kein Commit oder Rollback mit **SQLEndTran**.  
  
 Wenn eine Anwendung ruft **SQLDisconnect** bevor er alle Anweisungen der Verbindung zugeordnete freigegeben hat, der Treiber, nachdem sie erfolgreich aus der Datenquelle, trennt die Verbindung freigegeben dieser Anweisungen und alle Deskriptoren, die wurden für die Verbindung explizit zugewiesen. Allerdings, wenn eine oder mehrere der die Anweisungen der Verbindung zugeordnet sind immer noch asynchron ausgeführt, **SQLDisconnect** gibt SQL_ERROR zurück, mit dem Wert SQLSTATE HY010 (Sequenzfehler funktionieren). Darüber hinaus **SQLDisconnect** gibt alle zugeordneten Anweisungen und alle Deskriptoren, die explizit für die Verbindung zugewiesen wurden, wenn die Verbindung in einem angehaltenen Zustand befindet oder wenn frei **SQLDisconnect** wurde wurde erfolgreich abgebrochen von **SQLCancelHandle**.  
  
 Informationen darüber, wie eine Anwendung verwendet **SQLDisconnect**, finden Sie unter [Trennen von einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="disconnecting-from-a-pooled-connection"></a>Eine zusammengeführte Verbindung trennen  
 Wenn Verbindungspooling, für die einer freigegebenen Umgebung aktiviert ist aus, und eine Anwendung ruft **SQLDisconnect** für eine Verbindung in der Umgebung, die Verbindung an den Verbindungspool zurückgegeben werden soll, und ist weiterhin verfügbar, mit anderen Komponenten, die mithilfe von die gleichen freigegebenen Umgebung.  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md), [SQLBrowseConnect-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), und [SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ein Handle zuordnen|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle mit einer Zeichenfolge oder eines Dialogfelds Verbindungsdialogfeld|[SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Ausführen eines Commit- oder Rollback-Vorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Freigeben eines Verbindungshandles|[SQLFreeConnect-Funktion](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
