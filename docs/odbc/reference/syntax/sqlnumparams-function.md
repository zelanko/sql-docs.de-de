---
title: SQLNumParams-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLNumParams
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLNumParams
helpviewer_keywords:
- SQLNumParams function [ODBC]
ms.assetid: dbf2da44-253b-4094-bd6b-29bafc23c7a3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05e65eac94cffa0e31e3ec71179f18704a7e8b71
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536590"
---
# <a name="sqlnumparams-function"></a>SQLNumParams-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLNumParams** gibt die Anzahl von Parametern in einer SQL­Anweisung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLNumParams(  
     SQLHSTMT        StatementHandle,  
     SQLSMALLINT *   ParameterCountPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *ParameterCountPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in die die Anzahl von Parametern in der Anweisung zurückgegeben werden sollen.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLNumParams** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLNumParams** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die **SQLNumParams** Funktion aufgerufen wurde und, bevor es ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* ; die **SQLNumParams** Funktion wurde dann erneut aufgerufen, auf die *StatementHandle*.<br /><br /> Or **SQLNumParams** Funktion aufgerufen wurde und, bevor es ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*  von einem anderen Thread in einer multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) die Funktion wurde vor dem Aufruf aufgerufen **SQLPrepare** oder **SQLExecDirect** für die *StatementHandle*.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLNumParams** Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLNumParams** kann aufgerufen werden, erst nach dem **SQLPrepare** aufgerufen wurde.  
  
 Wenn die Anweisung zugeordnet *StatementHandle* enthält keine Parameter **SQLNumParams** legt **ParameterCountPtr* auf 0.  
  
 Die Anzahl von Parametern, die vom **SQLNumParams** ist der gleiche Wert wie das Feld SQL_DESC_COUNT des IPD.  
  
 Weitere Informationen finden Sie unter [Parameter beschreiben](../../../odbc/reference/develop-app/describing-parameters.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer, an einen parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Zurückgeben von Informationen über einen Parameter in einer Anweisung|[SQLDescribeParam-Funktion](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
