---
description: SQLCancelHandle-Funktion
title: Sqlcancelhandle-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: 3f466f63d6da9aa9a96b9e929ea2b59a3e43491d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448850"
---
# <a name="sqlcancelhandle-function"></a>SQLCancelHandle-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,8 Standards Compliance: None  
  
 Es wird erwartet, dass die meisten ODBC 3,8-Treiber (und höher) diese Funktion implementieren. Wenn ein Treiber nicht durch einen **sqlcancelhandle** -Befehl mit einem Verbindungs Handle im *handle* -Parameter wird SQL_ERROR mit dem SQLSTATE-Wert zurückgegeben, und der Message-Treiber unterstützt diese Funktion **nicht. ein** **sqlcancelhandle** -Befehl mit einem Anweisungs Handle, weil der *handle* -Parameter einem **SQLCancel-Befehl durch den** Treiber-Manager zugeordnet wird Eine Anwendung kann **SQLGetFunctions** verwenden, um zu bestimmen, ob ein Treiber **sqlcancelhandle**unterstützt.  
  
 **Zusammenfassung**  
 **Sqlcancelhandle** bricht die Verarbeitung für eine Verbindung oder eine Anweisung ab. Der Treiber-Manager ordnet einen **sqlcancelhandle** -Befehl einem **SQLCancel** -Befehl zu, wenn der- *Typ* SQL_HANDLE_STMT ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCancelHandle(  
      SQLSMALLINT  HandleType,  
      SQLHANDLE    Handle);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 Der Der Typ des Handles, für das die cacel-Verarbeitung durchgeführt werden soll. Gültige Werte sind SQL_HANDLE_DBC oder SQL_HANDLE_STMT.  
  
 *Handle*  
 Der Das Handle, für das die Verarbeitung abgebrochen werden soll.  
  
 Wenn *handle* kein gültiges Handle des Typs ist, der von " *Lenker*" angegeben wird, gibt **sqlcancelhandle** SQL_INVALID_HANDLE zurück.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlcancelhandle** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit dem Handlertyp SQL_HANDLE_STMT und einem Anweisungs *handle oder einem* Handlertyp von SQL_HANDLE_DBC und einem *handle*für den Verbindungs Handle aufgerufen wird. *HandleType* *HandleType*  
  
 In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **sqlcancelhandle** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md) im Argument * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|Eine asynchron ausgeführte, Anweisungs bezogene Funktion wurde für eines der Anweisungs Handles aufgerufen, die mit dem *handle*verknüpft sind, und der *Typ "tortype* " wurde auf SQL_HANDLE_DBC festgelegt. Die asynchrone Funktion wurde noch ausgeführt, als " **sqlcancelhandle** " aufgerufen wurde.<br /><br /> (DM) das *handlentypargument* wurde SQL_HANDLE_STMT. für das zugeordnete Verbindungs Handle wurde eine asynchron ausgeführte Funktion aufgerufen. die Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungs Handles aufgerufen, die mit dem *handle* verknüpft sind, und der *Tortyp* wurde auf SQL_HANDLE_DBC festgelegt und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> **Sqlbrowseconnetct** wurde für *connectionHandle*aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor der Suchvorgang abgeschlossen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY092|Ungültiger Attribut/Options Bezeichner|Der *Handtyp* wurde auf SQL_HANDLE_ENV oder SQL_HANDLE_DESC festgelegt.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der mit dem *handle* verknüpfte Treiber unterstützt die-Funktion nicht.|  
  
 Wenn **sqlcancelhandle** mit dem auf SQL_HANDLE_STMT festgelegten *andtertyp* aufgerufen wird, kann ein beliebiger SQLSTATE-Wert zurückgegeben werden, der von der **SQLCancel**-Funktion zurückgegeben werden kann.  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion ähnelt **SQLCancel** , kann jedoch entweder eine Verbindung oder ein Anweisungs Handle als Parameter anstelle eines Anweisungs Handles annehmen. Der Treiber-Manager ordnet einen **sqlcancelhandle** -Befehl einem **SQLCancel** -Befehl zu, wenn der- *Typ* SQL_HANDLE_STMT ist. Dadurch können Anwendungen mit **sqlcancelhandle** Anweisungs Vorgänge abbrechen, auch wenn der Treiber **sqlcancelhandle**nicht implementiert.  
  
 Weitere Informationen zum Abbrechen eines Anweisungs Vorgangs finden Sie unter [SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md).  
  
 Wenn keine Vorgänge in *Bearbeitung* sind, hat der **sqlcancelhandle** -Befehl keine Auswirkung.  
  
 **Sqlcancelhandle** für ein Verbindungs Handle kann die folgenden Verarbeitungs Typen Abbrechen:  
  
-   Eine Funktion, die asynchron für die Verbindung ausgeführt wird.  
  
-   Eine Funktion, die auf dem Verbindungs Handle in einem anderen Thread ausgeführt wird.  
  
 Wenn **sqlcancelhandle** aufgerufen wird, um eine Funktion abzubrechen, die asynchron in einer Verbindung ausgeführt wird, werden Diagnosedaten Sätze, die von **sqlcancelhandle** gesendet werden, an die durch den Vorgang zurückgegebenen Vorgänge angehängt. **Sqlcancelhandle** gibt jedoch keine Diagnosedaten Sätze zurück, wenn eine Funktion abgebrochen wird, die für eine Verbindung in einem anderen Thread ausgeführt wird.  
  
 Die Verwendung von **sqlcancelhandle** zum Abbrechen von **SQLEndTran** kann die Verbindung in den Status "angehalten" versetzen. Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Informationen zur Verwendung von **sqlcancelhandle** in einer Anwendung, die auf einem Windows-Betriebssystem bereitgestellt wird, das älter als Windows 7 ist, finden Sie unter [Kompatibilitäts Matrix](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
#### <a name="canceling-connection-related-asynchronous-processing"></a>Abbrechen der Verbindungs bezogenen asynchronen Verarbeitung  
 Wenn eine Funktion SQL_STILL_EXECUTING zurückgibt, kann eine Anwendung **sqlcancelhandle** aufzurufen, um den Vorgang abzubrechen. Wenn die Abbruch Anforderung erfolgreich ist, gibt **sqlcancelhandle** SQL_SUCCESS zurück. Dies bedeutet nicht, dass die ursprüngliche Funktion abgebrochen wurde. Gibt an, dass die Abbruch Anforderung verarbeitet wurde. Der Treiber und die Datenquelle bestimmen, wann oder ob der Vorgang abgebrochen wird. Die Anwendung muss die ursprüngliche Funktion weiterhin aufzurufen, bis der Rückgabecode nicht SQL_STILL_EXECUTING ist. Wenn die ursprüngliche Funktion abgebrochen wurde, wird der Rückgabecode SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen). Wenn die ursprüngliche Funktion Ihre normale Verarbeitung abgeschlossen hat (wurde nicht abgebrochen), wird der Rückgabecode SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, oder SQL_ERROR und ein anderer SQLSTATE als HY008 (Vorgang abgebrochen), wenn die ursprüngliche Funktion fehlgeschlagen ist.  
  
#### <a name="canceling-functions-executing-on-another-thread"></a>Abbrechen von Funktionen, die in einem anderen Thread ausgeführt werden  
 In einer Multithreadanwendung kann die Anwendung einen Vorgang abbrechen, der in einem anderen Thread ausgeführt wird. Um den Vorgang abzubrechen, ruft die Anwendung **sqlcancelhandle** mit dem von der Funktion verwendeten Handle auf, aber in einem anderen Thread. Der Treiber und das Betriebssystem bestimmen, wie der Vorgang abgebrochen wird. Der Rückgabecode **sqlcancelhandle** gibt an, ob der Treiber die Anforderung verarbeitet hat, und gibt entweder SQL_SUCCESS oder SQL_ERROR zurück (es werden keine Diagnoseinformationen zurückgegeben). Wenn die Verarbeitung der ursprünglichen Funktion abgebrochen wird, gibt die ursprüngliche Funktion SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen) zurück.  
  
 Wenn eine Funktion ausgeführt wird, wenn **sqlcancelhandle** in einem anderen Thread aufgerufen wird, um die Funktion abzubrechen, ist es möglich, dass die Funktion erfolgreich ist und SQL_SUCCESS zurückgibt, bevor der Abbruch wirksam werden kann. Ein Aufruf von **sqlcancelhandle** hat keine Auswirkung, wenn der Vorgang abgeschlossen wurde, bevor **sqlcancelhandle** den Vorgang abbrechen konnte.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abbrechen einer Funktion, die asynchron für ein Anweisungs Handle ausgeführt wird, Abbrechen einer Funktion für eine Anweisung, die Daten benötigt, oder Abbrechen einer Funktion, die in einer Anweisung in einem anderen Thread ausgeführt wird.|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Header Dateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Asynchrone Ausführung (Abruf Methode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
