---
title: SQLCancelHandle-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
f1_keywords:
- SQLCancelHandle
helpviewer_keywords:
- SQLCancelHandle function [ODBC]
ms.assetid: 16049b5b-22a7-4640-9897-c25dd0f19d21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 655c3c76794b170b113442b14ae75cf977ac024c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63253175"
---
# <a name="sqlcancelhandle-function"></a>SQLCancelHandle-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.8  
  
 Einhaltung von Standards: None  
  
 Es wird erwartet, dass die meisten ODBC 3.8 (und höher)-Treiber werden diese Funktion zu implementieren. Wenn ein Treiber nicht, einen Aufruf von **SQLCancelHandle** mit einer Verbindung zu behandeln, der *behandeln* Parameter SQL_ERROR mit SQLSTATE von IM001 und eine Nachricht zurück "Treiber diese Funktion nicht unterstützt" einen Aufruf um **SQLCancelHandle** mit einer Anweisung zu verarbeiten, als die *behandeln* Parameter für einen Aufruf von zugeordnet **SQLCancel** vom Treiber-Manager und verarbeitet werden können, wenn der Treiber implementiert **SQLCancel**. Eine Anwendung kann mithilfe **SQLGetFunctions** zu bestimmen, ob ein Treiber unterstützt **SQLCancelHandle**.  
  
 **Zusammenfassung**  
 **SQLCancelHandle** bricht die Verarbeitung auf eine Verbindung oder eine Anweisung. Der Treiber-Manager zugeordnet wird, einen Aufruf von **SQLCancelHandle** für einen Aufruf von **SQLCancel** beim *HandleType* SQL_HANDLE_STMT auf ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLCancelHandle(  
      SQLSMALLINT  HandleType,  
      SQLHANDLE    Handle);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Der Typ des Handles auf dem Cacel-Verarbeitung. Gültige Werte sind SQL_HANDLE_DBC auf oder SQL_HANDLE_STMT auf.  
  
 *Handle*  
 [Eingabe] Das Handle für die Verarbeitung abzubrechen.  
  
 Wenn *behandeln* ist kein gültiges Handle des Typs vom angegebenen *HandleType*, **SQLCancelHandle** SQL_INVALID_HANDLE gibt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCancelHandle** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von Behandeln von SQL_HANDLE_STMT auf, und eine Anweisung *behandeln* oder *HandleType* SQL_HANDLE_DBC auf, und ein Verbindungshandle *behandeln*.  
  
 Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLCancelHandle** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) im Argument  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY010|Fehler in der Funktionsreihenfolge|Eine Funktion asynchron ausgeführte, Anweisung bezogene wurde aufgerufen, für eine von der zugeordneten Anweisungshandles der *behandeln*, und *HandleType* auf SQL_HANDLE_DBC festgelegt wurde. Die asynchrone Funktion war immer noch ausgeführt, wenn **SQLCancelHandle** aufgerufen wurde.<br /><br /> (DM) die *HandleType* Argument war SQL_HANDLE_STMT auf, für das zugeordnete Verbindungshandle; wurde eine asynchrone Funktion aufgerufen und die Funktion wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** für eines der zugeordneten Anweisungshandles aufgerufen wurde die *behandeln* und *HandleType* auf SQL_HANDLE_DBC festgelegt wird, und die SQL_PARAM_DATA_AVAILABLE zurückgegeben wurde. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> **SQLBrowseConnect** wurde aufgerufen, *ConnectionHandle*, SQL_NEED_DATA zurückgegeben. Diese Funktion wurde vor der durchsuchen-Prozess abgeschlossen wurde aufgerufen.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|*HandleType* auf SQL_HANDLE_ENV oder SQL_HANDLE_DESC festgelegt wurde.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *behandeln* die Funktion nicht unterstützt.|  
  
 Wenn **SQLCancelHandle** aufgerufen wird und *HandleType* auf SQL_HANDLE_STMT festgelegt wird, können sie alle SQLSTATE, die von der Funktion zurückgegeben werden kann zurückgeben **SQLCancel**.  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion ist vergleichbar mit **SQLCancel** aber kann entweder eine Verbindung oder eine Anweisung Handle als Parameter statt nur für ein Anweisungshandle dauern. Der Treiber-Manager zugeordnet wird, einen Aufruf von **SQLCancelHandle** für einen Aufruf von **SQLCancel** beim *HandleType* SQL_HANDLE_STMT auf ist. Dadurch können Anwendungen mit **SQLCancelHandle** Anweisung Vorgänge abgebrochen werden, selbst wenn der Treiber nicht implementiert **SQLCancelHandle**.  
  
 Weitere Informationen zum Abbrechen eines Vorgangs für die Anweisung, finden Sie unter [SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md).  
  
 Wenn es keine Vorgänge in Bearbeitung auf *behandeln* den Aufruf von **SQLCancelHandle** hat keine Auswirkungen.  
  
 **SQLCancelHandle** Handle kann für eine Verbindung die folgenden Typen von Verarbeitung Abbrechen:  
  
-   Eine Funktion, die über die Verbindung asynchron ausgeführt wird.  
  
-   Eine Funktion, die auf dem Verbindungshandle in einem anderen Thread ausgeführt wird.  
  
 Wenn **SQLCancelHandle** aufgerufen, um eine Funktion, die asynchrone Ausführung in einer Verbindung, bereitgestellt von Diagnosedatensätzen abzubrechen **SQLCancelHandle** werden, die zurückgegeben werden, indem der Vorgang wird angefügt abgebrochen; **SQLCancelHandle** keinen zurückgibt DiagnoseDatensätze, jedoch beim Abbrechen von einer Funktion, die auf eine Verbindung in einem anderen Thread ausgeführt wird.  
  
 Mithilfe von **SQLCancelHandle** Abbrechen **SQLEndTran** angehaltenen Zustand die Verbindung festlegen können. Weitere Informationen zum angehaltenen Zustand, finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Informationen zur Verwendung von **SQLCancelHandle** in einer Anwendung, die auf einem Windows-Betriebssystem, die älter als Windows 7 bereitgestellt werden, finden Sie unter [Matrix der Sperrenkompatibilität](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
#### <a name="canceling-connection-related-asynchronous-processing"></a>Abbruch asynchroner Verarbeitung Verbindungsrelevante  
 Wenn eine Funktion SQL_STILL_EXECUTING zurückgibt, kann eine Anwendung aufrufen **SQLCancelHandle** , den Vorgang abzubrechen. Wenn die Cancel-Anforderung erfolgreich ist, ist **SQLCancelHandle** gibt SQL_SUCCESS zurück. Dies bedeutet nicht, dass die ursprüngliche Funktion abgebrochen wurde. Er gibt an, dass die Cancel-Anforderung verarbeitet wurde. Der Treiber und die Datenquelle ermitteln, wann oder ob der Vorgang abgebrochen wird. Die Anwendung muss weiterhin die ursprüngliche Funktion aufrufen, bis der Rückgabecode nicht SQL_STILL_EXECUTING ist. Wenn die ursprüngliche Funktion abgebrochen wurde, ist der Rückgabecode SQL_ERROR zurück, und SQLSTATE HY008 (der Vorgang wurde abgebrochen). Wenn die ursprüngliche Funktion die normalen Verarbeitung abgeschlossen wurde (nicht abgebrochen wurde), der Rückgabecode wird SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, oder SQL_ERROR und ein SQLSTATE als HY008 (der Vorgang wurde abgebrochen), wenn die ursprüngliche Funktion fehlgeschlagen ist.  
  
#### <a name="canceling-functions-executing-on-another-thread"></a>Funktionen, die Ausführung auf einem anderen Thread abgebrochen  
 In einer multithread-Anwendung kann die Anwendung einen Vorgang abbrechen, der auf einem anderen Thread ausgeführt wird. Zum Abbrechen des Vorgangs, der die Anwendung ruft **SQLCancelHandle** mit dem Handle, das von der Funktion, sondern in einem anderen Thread verwendet. Der Treiber und Betriebssystem bestimmen, wie der Vorgang abgebrochen wird. Die **SQLCancelHandle** Rückgabewert Code gibt an, ob der Treiber die Anforderung, die zurückgegeben werden verarbeitet, entweder SQL_SUCCESS oder SQL_ERROR zurückgegeben (es wird keine Diagnoseinformationen zurückgegeben). Wenn die Verarbeitung auf die ursprüngliche Funktion abgebrochen wird, gibt die ursprüngliche Funktion SQL_ERROR zurück, und SQLSTATE HY008 (Vorgang wurde abgebrochen).  
  
 Wenn eine Funktion wird ausgeführt, wenn **SQLCancelHandle** wird aufgerufen, in einem anderen Thread, um die Funktion abzubrechen, es ist möglich, für die Funktion erfolgreich ist und SQL_SUCCESS zurück, bevor der Abbruchvorgang wirksam werden kann. Ein Aufruf von **SQLCancelHandle** hat keine Auswirkungen, wenn der Vorgang, bevor Sie abgeschlossen **SQLCancelHandle** konnte den Vorgang abzubrechen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Abbrechen von einer Funktion, die asynchrone Ausführung für ein Anweisungshandle, eine Funktion für eine Anweisung, die Daten abbrechen oder Abbrechen von einer Funktion, die auf eine Anweisung in einem anderen Thread ausgeführt wird.|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
