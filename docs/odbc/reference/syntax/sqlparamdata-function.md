---
title: SQLParamData-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306921"
---
# <a name="sqlparamdata-function"></a>SQLParamData-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLParamData** wird in Verbindung mit **SQLPutData** verwendet, um Parameterdaten zur Anweisungs Ausführungszeit bereitzustellen, und mit **SQLGetData** , um gestreute Ausgabeparameter Daten abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLParamData(  
     SQLHSTMT       StatementHandle,  
     SQLPOINTER *   ValuePtrPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *ValuePtrPtr*  
 Ausgeben Ein Zeiger auf einen Puffer, in den die Adresse des in **SQLBindParameter** (für Parameterdaten) angegebenen *ParameterValuePtr* -Puffers zurückgegeben wird, oder die Adresse des in **SQLBindCol** (für Spaltendaten) angegebenen *targetvalueptr* -Puffers, wie er im Feld SQL_DESC_DATA_PTR Deskriptor-Datensatz enthalten ist.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLParamData** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle werden die SQLSTATE-Werte aufgelistet, die in der Regel von **SQLParamData** zurückgegeben werden, und jede im Kontext dieser Funktion wird erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|Der Datenwert, der vom *ValueType* -Argument in **SQLBindParameter** für den gebundenen Parameter identifiziert wurde, konnte nicht in den Datentyp konvertiert werden, der durch das *Parameter Type* -Argument in **SQLBindParameter**identifiziert wird.<br /><br /> Der Datenwert, der für einen Parameter zurückgegeben wird, der als SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT gebunden ist, konnte nicht in den Datentyp konvertiert werden, der vom *ValueType* -Argument in **SQLBindParameter angegeben**wird.<br /><br /> (Wenn die Datenwerte für eine oder mehrere Zeilen nicht konvertiert werden konnten, aber eine oder mehrere Zeilen erfolgreich zurückgegeben wurden, gibt diese Funktion SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|22026|Zeichenfolgendaten, nicht übereinstimmende Länge|Der SQL_NEED_LONG_DATA_LEN Informationstyp in **SQLGetInfo** lautete "Y", und für einen Long-Parameter wurden weniger Daten gesendet (der Datentyp war SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer Datenquellen spezifischer Datentyp), als mit dem *StrLen_or_IndPtr* -Argument in **SQLBindParameter**angegeben wurde.<br /><br /> Der SQL_NEED_LONG_DATA_LEN Informationstyp in **SQLGetInfo** lautete "Y", und es wurden weniger Daten für eine lange Spalte (der Datentyp SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer Datenquellen spezifischer Datentyp) als in dem Längenpuffer angegeben, der einer Spalte in einer Daten Zeile entspricht, die mit **SQLBulkOperations** hinzugefügt oder aktualisiert wurde oder mit **SQLSetPos**aktualisiert wurde.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde ein Rollback ausgeführt, weil ein Ressourcen Deadlock mit einer anderen Transaktion aufgetreten ist.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. die Funktion wurde dann erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) der vorherige Funktions aufrufame war kein Aufrufen von **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**oder **SQLSetPos** , bei dem der Rückgabecode SQL_NEED_DATA war, oder der vorherige Funktions aufrufwar ein Aufrufen von **SQLPutData**.<br /><br /> Der vorherige Funktions aufzurufen war ein **SQLParamData**-aufrufender.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLParamData** -Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. **SQLCancel** wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der Treiber, der dem *StatementHandle* entspricht, unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
 Wenn **SQLParamData** beim Senden von Daten für einen Parameter in einer SQL-Anweisung aufgerufen wird, kann es jeden SQLSTATE-Wert zurückgeben, der von der aufgerufenen Funktion zurückgegeben werden kann, um die Anweisung auszuführen (**SQLExecute** oder **SQLExecDirect**). Wenn Sie beim Senden von Daten für eine Spalte aufgerufen wird, die mit **SQLBulkOperations** aktualisiert oder hinzugefügt oder mit **SQLSetPos**aktualisiert wird, können alle SQLSTATE-Objekte zurückgegeben werden, die von **SQLBulkOperations** oder **SQLSetPos**zurückgegeben werden können.  
  
## <a name="comments"></a>Kommentare  
 **SQLParamData** kann aufgerufen werden, um Data-at-Execution-Daten für zwei Verwendungen bereitzustellen: Parameterdaten, die in einem Aufruf von **SQLExecute** oder **SQLExecDirect**verwendet werden, oder Spaltendaten, die verwendet werden, wenn eine Zeile durch einen Aufruf von **SQLBulkOperations** aktualisiert oder hinzugefügt oder durch einen Aufruf von **SQLSetPos**aktualisiert wird. Zur Ausführungszeit gibt **SQLParamData** einen Indikator für die vom Treiber benötigten Daten an die Anwendung zurück.  
  
 Wenn eine Anwendung **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos**aufruft, gibt der Treiber SQL_NEED_DATA zurück, wenn er Data-at-Execution-Daten benötigt. Eine Anwendung ruft dann **SQLParamData** auf, um zu bestimmen, welche Daten gesendet werden sollen. Wenn der Treiber Parameterdaten erfordert, gibt der Treiber im * \*ValuePtrPtr* -Ausgabepuffer den Wert zurück, den die Anwendung in den rowsetpuffer eingefügt hat. Die Anwendung kann diesen Wert verwenden, um zu bestimmen, welche Parameterdaten der Treiber anfordert. Wenn der Treiber Spaltendaten erfordert, gibt der Treiber die Adresse, an die die Spalte ursprünglich gebunden wurde, im * \*ValuePtrPtr* -Puffer wie folgt zurück:  
  
 *Bound Address* + *Bindungs Offset* für gebundene Adresse + ((*Zeilennummer* -1) x- *Element Größe*)  
  
 Dabei werden die Variablen wie in der folgenden Tabelle angegeben definiert.  
  
|Variable|BESCHREIBUNG|  
|--------------|-----------------|  
|*Gebundene Adresse*|Die mit dem *targetvalueptr* -Argument in **SQLBindCol**angegebene Adresse.|  
|*Bindungs Offset*|Der Wert, der an der mit dem SQL_ATTR_ROW_BIND_OFFSET_PTR Statement-Attribut angegebenen Adresse gespeichert wird.|  
|*Row Number*|Die 1-basierte Nummer der Zeile im Rowset. Bei einzeiligen Abruf Vorgängen, bei denen es sich um die Standardeinstellung handelt, ist dies 1.|  
|*Element Größe*|Der Wert des Attributs der SQL_ATTR_ROW_BIND_TYPE Anweisung für Daten-und Längen-/Indikatorpuffer.|  
  
 Außerdem wird SQL_NEED_DATA zurückgegeben, bei dem es sich um einen Indikator für die Anwendung handelt, der zum Senden der Daten **SQLPutData** aufruft.  
  
 Die Anwendung ruft **SQLPutData** so oft wie nötig auf, um die Data-at-Execution-Daten für die Spalte oder den Parameter zu senden. Nachdem alle Daten für die Spalte oder den Parameter gesendet wurden, ruft die Anwendung **SQLParamData** erneut auf. Wenn **SQLParamData** erneut SQL_NEED_DATA zurückgibt, müssen Daten für einen anderen Parameter oder eine Spalte gesendet werden. Daher ruft die Anwendung erneut **SQLPutData**auf. Wenn alle Data-at-Execution-Daten für alle Parameter oder Spalten gesendet wurden, gibt **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück, der Wert in * \*ValuePtrPtr* ist nicht definiert, und die SQL-Anweisung kann ausgeführt werden, oder der **SQLBulkOperations** -oder **SQLSetPos** -Befehl kann verarbeitet werden.  
  
 Wenn **SQLParamData** Parameterdaten für eine gesuchte Update-oder DELETE-Anweisung bereitstellt, die keine Zeilen in der Datenquelle beeinflusst, gibt der **SQLParamData** -Befehl SQL_NO_DATA zurück.  
  
 Weitere Informationen zur Übergabe von Data-at-Execution-Parameterdaten zur Anweisungs Ausführungszeit finden Sie unter "übergeben von Parameterwerten" in [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) und [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md). Weitere Informationen zur Aktualisierung oder zum Hinzufügen von Data-at-Execution-Spaltendaten finden Sie im Abschnitt "Verwenden von SQLSetPos" in [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Ausführen von Massen Aktualisierungen mithilfe von Lesezeichen" in [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)und [Long Data und SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
 **SQLParamData** kann aufgerufen werden, um gestreute Ausgabeparameter abzurufen. Wenn **SQLMoreResults**, **SQLExecute**, **SQLGetData**oder **SQLExecDirect** SQL_PARAM_DATA_AVAILABLE zurückgibt, müssen Sie **SQLParamData** aufrufen, um zu bestimmen, für welchen Parameter ein Wert verfügbar ist. Weitere Informationen zu SQL_PARAM_DATA_AVAILABLE und gestreamt-Ausgabeparametern finden [Sie unter Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Binden eines Puffers an einen Parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einem Parameter in einer-Anweisung|[SQLDescribeParam-Funktion](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Senden von Parameterdaten zur Ausführungszeit|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Header Dateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
