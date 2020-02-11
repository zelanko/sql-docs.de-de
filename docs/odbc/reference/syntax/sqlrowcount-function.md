---
title: SQLRowCount-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRowCount
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLRowCount
helpviewer_keywords:
- SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65683174ee5b48a8f7b861f3ba838334d70025ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68345435"
---
# <a name="sqlrowcount-function"></a>SQLRowCount-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLRowCount** gibt die Anzahl der Zeilen zurück, die von einer **Update**-, **Insert**-oder **Delete** -Anweisung betroffen sind. ein SQL_ADD-, SQL_UPDATE_BY_BOOKMARK-oder SQL_DELETE_BY_BOOKMARK Vorgang in **SQLBulkOperations**; oder ein SQL_UPDATE oder SQL_DELETE Vorgang in **SQLSetPos**.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *RowCountPtr*  
 Ausgeben Verweist auf einen Puffer, in den eine Zeilen Anzahl zurückgegeben werden soll. Bei **Update**-, **Insert**-und **Delete** -Anweisungen für die Vorgänge SQL_ADD, SQL_UPDATE_BY_BOOKMARK und SQL_DELETE_BY_BOOKMARK in **SQLBulkOperations**sowie für die SQL_UPDATE-oder SQL_DELETE Vorgänge in **SQLSetPos**ist der Wert, der in **rowcountrytptr* zurückgegeben wurde, entweder die Anzahl der von der Anforderung betroffenen Zeilen oder-1, wenn die Anzahl der betroffenen Zeilen nicht verfügbar ist.  
  
 Wenn **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, **SQLSetPos oder SQLMoreResults** aufgerufen wird, wird das SQL_DIAG_ROW_COUNT-Feld der Diagnosedaten Struktur auf die Zeilen Anzahl festgelegt, und die Zeilen Anzahl wird auf Implementierungs abhängige Weise zwischengespeichert. **SQLRowCount** gibt den zwischengespeicherten Zeilen Anzahl Wert zurück. Der Wert für die zwischengespeicherte Zeilen Anzahl ist gültig, bis das Anweisungs Handle auf den vorbereiteten oder zugewiesenen Zustand zurückgesetzt wird, die Anweisung erneut ausgeführt wird oder **SQLCloseCursor** aufgerufen wird. Beachten Sie Folgendes: Wenn eine Funktion aufgerufen wurde, seit das SQL_DIAG_ROW_COUNT Feld festgelegt wurde, kann sich der von **SQLRowCount** zurückgegebene Wert von dem Wert im SQL_DIAG_ROW_COUNT Feld unterscheiden, da das SQL_DIAG_ROW_COUNT Feld durch einen beliebigen Funktionsaufruf auf 0 zurückgesetzt wird.  
  
 Bei anderen Anweisungen und Funktionen kann der Treiber den Wert definieren, der in \* *rowcountrytptr*zurückgegeben wurde. Einige Datenquellen können z. b. die Anzahl der Zeilen zurückgeben, die von einer **Select** -Anweisung oder einer Katalog Funktion zurückgegeben werden, bevor die Zeilen abgerufen werden.  
  
> [!NOTE]  
>  Viele Datenquellen können vor dem Abrufen nicht die Anzahl der Zeilen in einem Resultset zurückgeben. für eine maximale Interoperabilität sollten sich Anwendungen nicht auf dieses Verhalten verlassen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLRowCount** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle werden die SQLSTATE-Werte aufgelistet, die häufig von **SQLRowCount** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLRowCount** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) die Funktion wurde vor dem Aufrufen von **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** für " *StatementHandle*" aufgerufen.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das *StatementHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Wenn die letzte SQL-Anweisung, die auf dem Anweisungs Handle ausgeführt wurde, keine **Update**-, **Insert**-oder **Delete** -Anweisung war oder wenn das *Vorgangs* Argument im vorherigen **SQLBulkOperations** -Befehl nicht SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_DELETE_BY_BOOKMARK war oder wenn das *Vorgangs* Argument im vorherigen **SQLSetPos** -Befehl nicht SQL_UPDATE oder SQL_DELETE war, ist der Wert von **rowcalltptr* Treiber definiert Weitere Informationen finden Sie unter [bestimmen der Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
