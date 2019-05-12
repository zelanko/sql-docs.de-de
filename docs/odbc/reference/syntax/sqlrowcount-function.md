---
title: SQLRowCount-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRowCount
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRowCount
helpviewer_keywords:
- SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ccc858603fc5662f380c5d3ae48d777005ddac4
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537155"
---
# <a name="sqlrowcount-function"></a>SQLRowCount-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLRowCount** gibt die Anzahl der von betroffenen Zeilen eine **UPDATE**, **einfügen**, oder **löschen** Anweisung; eine SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_ Vorgang DELETE_BY_BOOKMARK **SQLBulkOperations**; oder einen Vorgang SQL_UPDATE oder SQL_DELETE in **SQLSetPos**.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *RowCountPtr*  
 [Ausgabe] Verweist auf einen Puffer, in die die Zeilenanzahl zurückgegeben werden sollen. Für **UPDATE**, **einfügen**, und **löschen** -Anweisungen für die Vorgänge SQL_ADD SQL_UPDATE_BY_BOOKMARK und SQL_DELETE_BY_BOOKMARK in  **SQLBulkOperations**, und für die SQL_UPDATE oder SQL_DELETE Vorgänge im **SQLSetPos**, zurückgegebene Wert in **RowCountPtr* ist entweder die Anzahl der von betroffenen Zeilen die Anforderung oder -1, wenn die Anzahl der betroffenen Zeilen nicht verfügbar ist.  
  
 Wenn **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, **SQLSetPos oder SQLMoreResults** aufgerufen wird, wird die SQL_DIAG_ROW_COUNT -Feld der Struktur diagnostische Daten auf die Anzahl der Zeilen festgelegt ist, und die Anzahl der Zeilen in eine Möglichkeit der Implementierung abhängige zwischengespeichert ist. **SQLRowCount** gibt der Wert für die zwischengespeicherten Zeile. Der Wert für die zwischengespeicherten Zeile ist gültig, bis das Anweisungshandle wieder in den vorbereiteten oder zugeordneten Zustand festgelegt wird, wird die Anweisung erneut ausgeführt, oder **SQLCloseCursor** aufgerufen wird. Beachten Sie, dass eine Funktion aufgerufen wurde, da das Feld SQL_DIAG_ROW_COUNT festgelegt wurde, der Wert von zurückgegeben **SQLRowCount** möglicherweise verschiedene, von dem Wert in das Feld "SQL_DIAG_ROW_COUNT" auf das Feld "SQL_DIAG_ROW_COUNT" zurückgesetzt wird 0 von einem beliebigen Funktionsaufruf.  
  
 Für andere Anweisungen und Funktionen, kann der Treiber den Rückgabewert definieren \* *RowCountPtr*. Z. B. einige Datenquellen möglicherweise die Anzahl von zurückgegebenen Zeilen zurückgeben einer **wählen** -Anweisung oder einer Katalogfunktion vor dem Abrufen der Zeilen.  
  
> [!NOTE]  
>  Viele Datenquellen können nicht in einem Resultset, die vor dem Abrufen der sie die Anzahl der Zeilen zurückgegeben wird. für eine optimale Interoperabilität sollten die Anwendungen nicht auf dieses Verhalten verlassen.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLRowCount** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLRowCount** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLRowCount** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) die Funktion wurde vor dem Aufruf aufgerufen **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** für die  *StatementHandle*.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Wenn die letzte SQL-Anweisung, die über das Anweisungshandle ausgeführt, nicht wurde eine **UPDATE**, **einfügen**, oder **löschen** Anweisung oder, wenn die *Vorgang* Argument in den vorherigen Aufruf von **SQLBulkOperations** war nicht SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_DELETE_BY_BOOKMARK, oder wenn die *Vorgang* Argument in den vorherigen Aufruf von  **SQLSetPos** wurde nicht SQL_UPDATE oder SQL_DELETE, den Wert der **RowCountPtr* wird durch die Treiber definiert. Weitere Informationen finden Sie unter [bestimmen die Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
