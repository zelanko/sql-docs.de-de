---
description: SQLDisconnect-Funktion
title: SQLDisconnect-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: 604f5af6f425506996e7e15b7db73878f3d8b2c6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428942"
---
# <a name="sqldisconnect-function"></a>SQLDisconnect-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLDisconnect** schließt die Verbindung, die einem bestimmten Verbindungs Handle zugeordnet ist.  
  
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
 Wenn **SQLDisconnect** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_DBC und einem *handle* von *connectionHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLDisconnect** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01002|Fehler beim Trennen|Fehler beim trennen. Die Verbindung wurde jedoch erfolgreich getrennt. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) die im Argument *connectionHandle* angegebene Verbindung war nicht geöffnet.|  
|25000|Ungültiger Transaktionsstatus|Die vom Argument " *connectionHandle*" angegebene Verbindung enthält eine Transaktion. Die Transaktion bleibt aktiv.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *connectionHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung der [sqlcancelhandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) abgeschlossen wurde, wurde Sie für *connectionHandle*aufgerufen. Anschließend wurde die Funktion für *connectionHandle*erneut aufgerufen.<br /><br /> Die-Funktion wurde aufgerufen, und vor der Ausführung von **sqlcancelhandle** wurde für *connectionHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für ein *StatementHandle* aufgerufen, das dem *connectionHandle* zugeordnet ist, und wird noch ausgeführt, als " **SQLDisconnect** " aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für *connectionHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für ein *StatementHandle* aufgerufen, das dem *connectionHandle* zugeordnet ist, und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Das Verbindungs Timeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat und die Verbindung noch aktiv ist. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *connectionHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Wenn eine Anwendung **SQLDisconnect** aufruft, nachdem **sqlbrowseconnetct** SQL_NEED_DATA zurückgegeben hat und bevor ein anderer Rückgabecode zurückgegeben wird, bricht der Treiber den Vorgang zum Durchsuchen der Verbindung ab und gibt die Verbindung wieder in den Status "nicht verbunden" zurück.  
  
 Wenn eine Anwendung **SQLDisconnect** aufruft, während eine unvollständige Transaktion mit dem Verbindungs Handle verknüpft ist, gibt der Treiber SQLSTATE 25000 (Ungültiger Transaktionsstatus) zurück. Dies deutet darauf hin, dass die Transaktion unverändert ist und die Verbindung geöffnet ist. Bei einer unvollständigen Transaktion handelt es sich um eine Transaktion, für die kein Commit oder Rollback mit **SQLEndTran**ausgeführt wurde.  
  
 Wenn eine Anwendung **SQLDisconnect** aufruft, bevor Sie alle der Verbindung zugeordneten Anweisungen freigegeben hat, gibt der Treiber nach der erfolgreichen Trennung der Verbindung mit der Datenquelle die-Anweisungen und alle Deskriptoren frei, die explizit für die Verbindung zugeordnet wurden. Wenn jedoch mindestens eine der mit der Verbindung verknüpften Anweisungen weiterhin asynchron ausgeführt wird, gibt **SQLDisconnect** SQL_ERROR mit dem SQLSTATE-Wert HY010 (Funktions Sequenz Fehler) zurück. Außerdem gibt **SQLDisconnect** alle zugehörigen-Anweisungen und alle Deskriptoren frei, die explizit für die Verbindung zugeordnet wurden, wenn sich die Verbindung im angehaltenen Zustand befindet oder **SQLDisconnect** erfolgreich von **sqlcancelhandle**abgebrochen wurde.  
  
 Informationen dazu, wie eine Anwendung **SQLDisconnect**verwendet, finden Sie unter [Trennen der Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="disconnecting-from-a-pooled-connection"></a>Trennen einer Verbindung mit einer gepoolten Verbindung  
 Wenn das Verbindungspooling für eine freigegebene Umgebung aktiviert ist und eine Anwendung **SQLDisconnect** für eine Verbindung in dieser Umgebung aufruft, wird die Verbindung an den Verbindungspool zurückgegeben und ist weiterhin für andere Komponenten verfügbar, die dieselbe freigegebene Umgebung verwenden.  
  
## <a name="code-example"></a>Codebeispiel  
 Weitere Informationen finden Sie unter [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md), [sqlbrowseconnetct-Funktion](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)und [SQLCONNECT-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuordnen eines Handles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Herstellen einer Verbindung mit einer Datenquelle über eine Verbindungs Zeichenfolge oder ein Dialogfeld|[SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Ausführen eines Commit-oder Rollback-Vorgangs|[SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Freigeben eines Verbindungs Handles|[SQLFreeConnect-Funktion](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
