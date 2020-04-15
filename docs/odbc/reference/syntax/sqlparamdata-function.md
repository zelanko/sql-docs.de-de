---
title: SQLParamData-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLParamData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLParamData
helpviewer_keywords:
- SQLParamData function [ODBC]
ms.assetid: 68fe010d-9539-4e5b-a260-c8d32423b1db
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ed149e125e3231d670c6ddbd4569ff5ccee5c15
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306921"
---
# <a name="sqlparamdata-function"></a>SQLParamData-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLParamData** wird zusammen mit **SQLPutData** verwendet, um Parameterdaten zur Ausführungszeit von Auszugsangaben und mit **SQLGetData** zum Abrufen gestreamter Ausgabeparameterdaten zu liefern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLParamData(  
     SQLHSTMT       StatementHandle,  
     SQLPOINTER *   ValuePtrPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *WertPtrPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Adresse des *ParameterValuePtr-Puffers* zurückgegeben wird, der in **SQLBindParameter** (für Parameterdaten) angegeben ist, oder der Adresse des *TargetValuePtr-Puffers,* der in **SQLBindCol** (für Spaltendaten) angegeben ist, wie im SQL_DESC_DATA_PTR Deskriptordatensatzfeld enthalten.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLParamData** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLParamData** zurückgegeben werden, und es werden die sqlSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|Der datenwert, der durch das *ValueType-Argument* in **SQLBindParameter** für den bound-Parameter identifiziert wurde, konnte nicht in den Datentyp konvertiert werden, der durch das *ParameterType-Argument* in **SQLBindParameter**identifiziert wurde.<br /><br /> Der Datenwert, der für einen Parameter zurückgegeben wird, der als SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT gebunden ist, konnte nicht in den Datentyp konvertiert werden, der durch das *ValueType-Argument* in **SQLBindParameter**identifiziert wurde.<br /><br /> (Wenn die Datenwerte für eine oder mehrere Zeilen nicht konvertiert werden konnten, aber eine oder mehrere Zeilen erfolgreich zurückgegeben wurden, gibt diese Funktion SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|22026|Zeichenfolgendaten, nicht übereinstimmende Länge|Der SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo** war "Y", und für einen langen Parameter wurden weniger Daten gesendet (der Datentyp war SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer datenquellenspezifischer Datentyp), als mit dem *Argument StrLen_or_IndPtr* in **SQLBindParameter**angegeben wurde.<br /><br /> Der SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo** war "Y", und für eine lange Spalte wurden weniger Daten gesendet (der Datentyp war SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer datenquellenspezifischer Datentyp), als im Längenpuffer angegeben wurde, der einer Spalte in einer Datenzeile entspricht, die mit **SQLBulkOperations** hinzugefügt oder aktualisiert oder mit **SQLSetPos**aktualisiert wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcendeadlocks mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** auf dem *StatementHandle*aufgerufen; die Funktion wurde dann erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Der vorherige Funktionsaufruf war kein Aufruf von **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**oder **SQLSetPos,** bei dem der Rückgabecode SQL_NEED_DATA wurde oder der vorherige Funktionsaufruf ein Aufruf von **SQLPutData**war.<br /><br /> Der vorherige Funktionsaufruf war ein Aufruf von **SQLParamData**.<br /><br /> (DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLParamData-Funktion** aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. **SQLCancel** wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der Treiber, der dem *StatementHandle* entspricht, unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
 Wenn **SQLParamData** beim Senden von Daten für einen Parameter in einer SQL-Anweisung aufgerufen wird, kann es jede SQLSTATE zurückgeben, die von der Funktion zurückgegeben werden kann, die aufgerufen wird, die Anweisung auszuführen (**SQLExecute** oder **SQLExecDirect**). Wenn sie aufgerufen wird, während Daten für eine Spalte gesendet werden, die mit **SQLBulkOperations** aktualisiert oder hinzugefügt wird oder mit **SQLSetPos**aktualisiert wird, kann sie jede SQLSTATE zurückgeben, die von **SQLBulkOperations** oder **SQLSetPos**zurückgegeben werden kann.  
  
## <a name="comments"></a>Kommentare  
 **SQLParamData** kann aufgerufen werden, um Daten bei der Ausführung für zwei Verwendungen zu liefern: Parameterdaten, die in einem Aufruf von **SQLExecute** oder **SQLExecDirect**verwendet werden, oder Spaltendaten, die verwendet werden, wenn eine Zeile aktualisiert oder durch einen Aufruf von **SQLBulkOperations** hinzugefügt oder durch einen Aufruf von **SQLSetPos**aktualisiert wird. Zur Ausführungszeit gibt **SQLParamData** der Anwendung einen Indikator zurück, welche Daten der Treiber benötigt.  
  
 Wenn eine Anwendung **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos**aufruft, gibt der Treiber SQL_NEED_DATA zurück, wenn Daten bei der Ausführung benötigt werden. Eine Anwendung ruft dann **SQLParamData** auf, um zu bestimmen, welche Daten gesendet werden sollen. Wenn der Treiber Parameterdaten benötigt, gibt der Treiber im * \*ValuePtrPtr-Ausgabepuffer* den Wert zurück, den die Anwendung in den Rowset-Puffer gesetzt hat. Die Anwendung kann diesen Wert verwenden, um zu bestimmen, welche Parameterdaten der Treiber anfordert. Wenn der Treiber Spaltendaten benötigt, gibt der Treiber im * \*ValuePtrPtr-Puffer* die Adresse zurück, an die die Spalte ursprünglich gebunden war, wie folgt:  
  
 *Gebundene Adressbindung* + *Offset* + ((*Zeilennummer* - 1) x *Elementgröße*)  
  
 wobei die Variablen wie in der folgenden Tabelle angegeben definiert sind.  
  
|Variable|BESCHREIBUNG|  
|--------------|-----------------|  
|*Gebundene Adresse*|Die mit dem *TargetValuePtr-Argument* in **SQLBindCol**angegebene Adresse.|  
|*Bindungsversatz*|Der Wert, der an der Adresse gespeichert ist, die mit dem Attribut SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisung angegeben ist.|  
|*Row Number*|Die 1-basierte Nummer der Zeile im Rowset. Bei einzeiligen Abrufen, bei denen die Standardeinstellung angezeigt wird, ist dies 1.|  
|*Elementgröße*|Der Wert des SQL_ATTR_ROW_BIND_TYPE-Anweisungsattributs für Daten- und Längen-/Indikatorpuffer.|  
  
 Es gibt auch SQL_NEED_DATA zurück, was ein Indikator für die Anwendung ist, dass sie **SQLPutData** aufrufen sollte, um die Daten zu senden.  
  
 Die Anwendung ruft **SQLPutData** so oft wie nötig auf, um die Daten bei der Ausführung für die Spalte oder den Parameter zu senden. Nachdem alle Daten für die Spalte oder den Parameter gesendet wurden, ruft die Anwendung **SQLParamData** erneut auf. Wenn **SQLParamData** erneut SQL_NEED_DATA zurückgibt, müssen Daten für einen anderen Parameter oder eine andere Spalte gesendet werden. Daher ruft die Anwendung **SQLPutData**erneut auf. Wenn alle Daten bei der Ausführung für alle Parameter oder Spalten gesendet wurden, gibt **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück, der Wert in * \*ValuePtrPtr* ist nicht definiert, und die SQL-Anweisung kann ausgeführt werden, oder der **SQLBulkOperations-** oder **SQLSetPos-Aufruf** kann verarbeitet werden.  
  
 Wenn **SQLParamData** Parameterdaten für eine gesuchte Aktualisierungs- oder Löschanweisung bereitstellt, die keine Zeilen in der Datenquelle betrifft, gibt der Aufruf von **SQLParamData** SQL_NO_DATA zurück.  
  
 Weitere Informationen dazu, wie Data-at-Execution-Parameterdaten zur Ausführungszeit der Anweisung übergeben werden, finden Sie unter "Übergeben von Parameterwerten" in [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) und [Senden von Long Data](../../../odbc/reference/develop-app/sending-long-data.md). Weitere Informationen dazu, wie Daten-at-Execution-Spaltendaten aktualisiert oder hinzugefügt werden, finden Sie im Abschnitt "Verwenden von SQLSetPos" in [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Durchführen von Massenaktualisierungen mithilfe von Lesezeichen" in [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)und [Long Data und SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
 **SQLParamData** kann aufgerufen werden, um gestreamte Ausgabeparameter abzurufen. Wenn **SQLMoreResults**, **SQLExecute**, **SQLGetData**oder **SQLExecDirect** SQL_PARAM_DATA_AVAILABLE zurückgibt, rufen Sie **SQLParamData** auf, um zu bestimmen, welcher Parameter einen Verfügbaren Wert hat. Weitere Informationen zu SQL_PARAM_DATA_AVAILABLE und gestreamten Ausgabeparametern finden Sie unter [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an einen Parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einem Parameter in einer Anweisung|[SQLDescribeParam-Funktion](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Senden von Parameterdaten zur Ausführungszeit|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
