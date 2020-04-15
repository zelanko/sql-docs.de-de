---
title: SQLCancelHandle-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 059ed283032feb96ca5e6b12520682ccb034752a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299665"
---
# <a name="sqlcancelhandle-function"></a>SQLCancelHandle-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.8  
  
 Einhaltung der Standards: Keine  
  
 Es wird erwartet, dass die meisten ODBC 3.8 (und höher) Treiber diese Funktion implementieren werden. Wenn ein Treiber dies nicht tut, gibt ein Aufruf von **SQLCancelHandle** mit einem Verbindungshandle im *Handle-Parameter* SQL_ERROR mit einem SQLSTATE von IM001 und der Meldung 'Driver does not support this function'' ein Aufruf von **SQLCancelHandle** mit einem Anweisungshandle zurück, da der *Handle-Parameter* einem Aufruf von **SQLCancel** durch den Treiber-Manager zugeordnet wird und verarbeitet werden kann, wenn der Treiber **SQLCancel**implementiert. Eine Anwendung kann **SQLGetFunctions** verwenden, um zu bestimmen, ob ein Treiber **SQLCancelHandle**unterstützt.  
  
 **Zusammenfassung**  
 **SQLCancelHandle** bricht die Verarbeitung für eine Verbindung oder Anweisung ab. Der Treiber-Manager ordnet einen Aufruf von **SQLCancelHandle** einem Aufruf von **SQLCancel** zu, wenn *HandleType* SQL_HANDLE_STMT ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCancelHandle(  
      SQLSMALLINT  HandleType,  
      SQLHANDLE    Handle);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Der Typ des Handles, auf dem die Verarbeitung zu verarbeiten ist. Gültige Werte werden SQL_HANDLE_DBC oder SQL_HANDLE_STMT.  
  
 *Handle*  
 [Eingabe] Das Handle, für das die Verarbeitung abgebrochen werden soll.  
  
 Wenn *Handle* kein gültiges Handle des von *HandleType*angegebenen Typs ist, gibt **SQLCancelHandle** SQL_INVALID_HANDLE zurück.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCancelHandle** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem Anweisungshandle *Handle* oder einem *HandleType* von SQL_HANDLE_DBC und einem Verbindungshandlehandle aufgerufen wird. *Handle*  
  
 In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLCancelHandle** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) im Argument * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|Für eines der Anweisungshandles, die dem *Handle*zugeordnet sind, wurde eine asynchron ausgeführte, anweisungsbezogene Funktion aufgerufen, und *HandleType* wurde auf SQL_HANDLE_DBC festgelegt. Die asynchrone Funktion wurde noch ausgeführt, als **SQLCancelHandle** aufgerufen wurde.<br /><br /> (DM) Das *HandleType-Argument* wurde SQL_HANDLE_STMT; Eine asynchron ausgeführte Funktion wurde für das zugehörige Verbindungshandle aufgerufen. und die Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde aufgerufen, da eines der Anweisungshandles, die dem *Handle* zugeordnet sind, und *HandleType* auf SQL_HANDLE_DBC festgelegt wurde und SQL_PARAM_DATA_AVAILABLE zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> **SQLBrowseConnect** wurde für *ConnectionHandle*aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor der Browservorgang abgeschlossen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|*HandleType* wurde auf SQL_HANDLE_ENV oder SQL_HANDLE_DESC festgelegt.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *Handle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
 Wenn **SQLCancelHandle** aufgerufen wird, wenn *HandleType* auf SQL_HANDLE_STMT festgelegt ist, kann es jede SQLSTATE zurückgeben, die von der Funktion **SQLCancel**zurückgegeben werden kann.  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion ähnelt **SQLCancel,** kann jedoch entweder eine Verbindung oder ein Anweisungshandle als Parameter und nicht nur als Anweisungshandle verwenden. Der Treiber-Manager ordnet einen Aufruf von **SQLCancelHandle** einem Aufruf von **SQLCancel** zu, wenn *HandleType* SQL_HANDLE_STMT ist. Auf diese Weise können Anwendungen **SQLCancelHandle** verwenden, um Anweisungsvorgänge abzubrechen, auch wenn der Treiber **SQLCancelHandle**nicht implementiert.  
  
 Weitere Informationen zum Abbrechen eines Anweisungsvorgangs finden Sie unter [SQLCancel Function](../../../odbc/reference/syntax/sqlcancel-function.md).  
  
 Wenn keine Vorgänge für *Handle* ausgeführt werden, hat der Aufruf von **SQLCancelHandle** keine Auswirkungen.  
  
 **SQLCancelHandle** für ein Verbindungshandle kann die folgenden Verarbeitungstypen abbrechen:  
  
-   Eine Funktion, die asynchron auf der Verbindung ausgeführt wird.  
  
-   Eine Funktion, die auf dem Verbindungshandle für einen anderen Thread ausgeführt wird.  
  
 Wenn **SQLCancelHandle** aufgerufen wird, eine Funktion abzubrechen, die asynchron in einer Verbindung ausgeführt wird, werden von **SQLCancelHandle** veröffentlichte Diagnosedatensätze an die von dem abgebrochenen Vorgang zurückgegebenen Datensätze angehängt. **SQLCancelHandle** gibt jedoch keine Diagnosedatensätze zurück, wenn eine Funktion abgebrochen wird, die für eine Verbindung in einem anderen Thread ausgeführt wird.  
  
 Die Verwendung von **SQLCancelHandle** zum Abbrechen von **SQLEndTran** kann die Verbindung in einen angehaltenen Zustand versetzen. Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Informationen zur Verwendung von **SQLCancelHandle** in einer Anwendung, die auf einem Windows-Betriebssystem bereitgestellt wird, das älter als Windows 7 ist, finden Sie unter [Kompatibilitätsmatrix](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
#### <a name="canceling-connection-related-asynchronous-processing"></a>Abbrechen der verbindungsbezogenen asynchronen Verarbeitung  
 Wenn eine Funktion SQL_STILL_EXECUTING zurückgibt, kann eine Anwendung **SQLCancelHandle** aufrufen, um den Vorgang abzubrechen. Wenn die Abbruchanforderung erfolgreich ist, gibt **SQLCancelHandle** SQL_SUCCESS zurück. Dies bedeutet nicht, dass die ursprüngliche Funktion abgebrochen wurde. Es gibt an, dass die Abbruchanforderung verarbeitet wurde. Der Treiber und die Datenquelle bestimmen, wann oder ob der Vorgang abgebrochen wird. Die Anwendung muss weiterhin die ursprüngliche Funktion aufrufen, bis der Rückgabecode nicht SQL_STILL_EXECUTING wird. Wenn die ursprüngliche Funktion abgebrochen wurde, wird der Rückgabecode SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen). Wenn die ursprüngliche Funktion die normale Verarbeitung abgeschlossen hat (wurde nicht abgebrochen), wird der Rückgabecode SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO oder SQL_ERROR und einem anderen SQLSTATE als HY008 (Vorgang abgebrochen), wenn die ursprüngliche Funktion fehlgeschlagen ist.  
  
#### <a name="canceling-functions-executing-on-another-thread"></a>Abbrechen von Funktionen, die in einem anderen Thread ausgeführt werden  
 In einer Multithreadanwendung kann die Anwendung einen Vorgang abbrechen, der auf einem anderen Thread ausgeführt wird. Um den Vorgang abzubrechen, ruft die Anwendung **SQLCancelHandle** mit dem Handle auf, das von der Funktion verwendet wird, jedoch in einem anderen Thread. Der Treiber und das Betriebssystem bestimmen, wie der Vorgang abgebrochen wird. Der **SQLCancelHandle-Rückgabecode** gibt an, ob der Treiber die Anforderung verarbeitet hat, und gibt entweder SQL_SUCCESS oder SQL_ERROR zurück (es werden keine Diagnoseinformationen zurückgegeben). Wenn die Verarbeitung für die ursprüngliche Funktion abgebrochen wird, gibt die ursprüngliche Funktion SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen) zurück.  
  
 Wenn eine Funktion ausgeführt wird, wenn **SQLCancelHandle** in einem anderen Thread aufgerufen wird, um die Funktion abzubrechen, kann die Funktion erfolgreich sein und SQL_SUCCESS zurückgeben, bevor der Abbruch wirksam werden kann. Ein Aufruf von **SQLCancelHandle** hat keine Auswirkungen, wenn der Vorgang abgeschlossen wurde, bevor **SQLCancelHandle** den Vorgang abbrechen konnte.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abbrechen einer Funktion, die asynchron für ein Anweisungshandle ausgeführt wird, Abbrechen einer Funktion für eine Anweisung, die Daten benötigt, oder Abbrechen einer Funktion, die für eine Anweisung in einem anderen Thread ausgeführt wird.|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
