---
title: SQLRowCount-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2cbca03e7c3e381b803196a1bf7bb227ebeea03b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293370"
---
# <a name="sqlrowcount-function"></a>SQLRowCount-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLRowCount** gibt die Anzahl der Zeilen zurück, die von einer **UPDATE**-, **INSERT**- oder **DELETE-Anweisung** betroffen sind. ein SQL_ADD-, SQL_UPDATE_BY_BOOKMARK- oder SQL_DELETE_BY_BOOKMARK-Vorgang in **SQLBulkOperations**; oder ein SQL_UPDATE oder SQL_DELETE In **SQLSetPos**.  
  
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
 [Ausgabe] Zeigt auf einen Puffer, in dem eine Zeilenanzahl zurückgegeben werden soll. Für **UPDATE**-, **INSERT-** und **DELETE-Anweisungen** für die SQL_ADD-, SQL_UPDATE_BY_BOOKMARK- und SQL_DELETE_BY_BOOKMARK-Vorgänge in **SQLBulkOperations**und für die SQL_UPDATE- oder SQL_DELETE-Vorgänge in **SQLSetPos**ist der in **RowCountPtr* zurückgegebene Wert entweder die Anzahl der von der Anforderung betroffenen Zeilen oder -1, wenn die Anzahl der betroffenen Zeilen nicht verfügbar ist.  
  
 Wenn **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, **SQLSetPos oder SQLMoreResults** aufgerufen wird, wird das SQL_DIAG_ROW_COUNT Feld der Diagnosedatenstruktur auf die Zeilenanzahl festgelegt, und die Zeilenanzahl wird auf eine implementierungsabhängige Weise zwischengespeichert. **SQLRowCount** gibt den zwischengespeicherten Zeilenanzahlwert zurück. Der zwischengespeicherte Zeilenanzahlwert ist gültig, bis das Anweisungshandle auf den vorbereiteten oder zugewiesenen Zustand zurückgesetzt wird, die Anweisung erneut ausgeführt wird oder **SQLCloseCursor** aufgerufen wird. Wenn eine Funktion aufgerufen wurde, seit das feld SQL_DIAG_ROW_COUNT festgelegt wurde, kann sich der von **SQLRowCount** zurückgegebene Wert vom Wert im Feld SQL_DIAG_ROW_COUNT unterscheiden, da das SQL_DIAG_ROW_COUNT Feld durch einen beliebigen Funktionsaufruf auf 0 zurückgesetzt wird.  
  
 Für andere Anweisungen und Funktionen kann der \*Treiber den in *RowCountPtr*zurückgegebenen Wert definieren. Einige Datenquellen können z. B. die Anzahl der Zeilen zurückgeben, die von einer **SELECT-Anweisung** oder einer Katalogfunktion zurückgegeben werden, bevor die Zeilen abgerufen werden.  
  
> [!NOTE]  
>  Viele Datenquellen können die Anzahl der Zeilen in einem Resultset nicht zurückgeben, bevor sie abgerufen werden. Für maximale Interoperabilität sollten sich Anwendungen nicht auf dieses Verhalten verlassen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLRowCount** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLRowCount** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLRowCount-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Die Funktion wurde aufgerufen, bevor **SIE SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** für das *StatementHandle*aufruft.<br /><br /> (DM) Eine asynchron ausgeführte Funktion wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Wenn die letzte SQL-Anweisung, die für das Anweisungshandle ausgeführt wurde, keine **UPDATE-,** **INSERT-** oder **DELETE-Anweisung** war oder wenn das *Operation-Argument* beim vorherigen Aufruf von **SQLBulkOperations** nicht SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_DELETE_BY_BOOKMARK war oder wenn das *Operation-Argument* beim vorherigen Aufruf von **SQLSetPos** nicht SQL_UPDATE oder SQL_DELETE war, ist der Wert von **RowCountPtr* treiberdefiniert. Weitere Informationen finden Sie unter [Ermitteln der Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
