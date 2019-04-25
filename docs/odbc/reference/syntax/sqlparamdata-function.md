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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec0038e0ec6c87dba403bbe62441815dfa6d0251
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62465966"
---
# <a name="sqlparamdata-function"></a>SQLParamData-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLParamData** zusammen mit **SQLPutData** Parameterdaten während der Ausführung der Anweisung, und klicken Sie mit bereitstellen **SQLGetData** gestreamte ausgabeparameterdaten abrufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLParamData(  
     SQLHSTMT       StatementHandle,  
     SQLPOINTER *   ValuePtrPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *ValuePtrPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Adresse des zurückzugebenden der *ParameterValuePtr* im angegebenen Puffer **SQLBindParameter** (für Parameterdaten) oder die Adresse des der *TargetValuePtr* im angegebenen Puffer **SQLBindCol** (für Spaltendaten) an, wie in das SQL_DESC_DATA_PTR-Deskriptorfeld Datensatz enthalten.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLParamData** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLParamData** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|Der Wert von identifiziert die *ValueType* -Argument in **SQLBindParameter** für der gebundene Parameter nicht in der identifizierte Datentyp konvertiert werden kann die *ParameterType*-Argument in **SQLBindParameter**.<br /><br /> Der Wert zurückgegeben, für einen Parameter gebunden wird, wie SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT nicht in der identifizierte Datentyp konvertiert werden konnte die *ValueType* -Argument in **SQLBindParameter**.<br /><br /> (Wenn die Datenwerte für eine oder mehrere Zeilen nicht konvertiert werden konnte, aber eine oder mehrere Zeilen wurden erfolgreich zurückgegeben, diese Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|22026|Zeichenfolgendaten, nicht übereinstimmende Länge|Der Typ des SQL_NEED_LONG_DATA_LEN-Informationen in **SQLGetInfo** wurde von "Y", und weniger Daten für einen Parameter "long" (der Datentyp wurde SQL_LONGVARCHAR, SQL_LONGVARBINARY oder einen long-Daten datenquellenspezifische-Datentyp) gesendet wurde, als angegeben wurde mit der *StrLen_or_IndPtr* -Argument in **SQLBindParameter**.<br /><br /> Der Typ des SQL_NEED_LONG_DATA_LEN-Informationen in **SQLGetInfo** wurde von "Y", und weniger Daten für eine lange Spalte (der Datentyp wurde SQL_LONGVARCHAR, SQL_LONGVARBINARY oder einen long-Daten datenquellenspezifische-Datentyp) gesendet wurde, als im angegebenen die Puffer der Länge für eine Spalte in eine Zeile mit Daten, die hinzugefügt oder aktualisiert wurde **SQLBulkOperations** oder mit aktualisierten **SQLSetPos**.|  
|40001|Serialisierungsfehler|Die Transaktion wurde wegen eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*; die Funktion wurde dann erneut auf aufgerufen die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) der vorherigen Funktionsaufruf war keinem Aufruf von **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, oder **SQLSetPos** , in dem die Zurückgeben der Code war SQL_NEED_DATA oder der vorherigen Funktionsaufruf einen Aufruf von **SQLPutData**.<br /><br /> Der vorherige Funktionsaufruf wurde **SQLParamData**.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLParamData** Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und zurückgegebene SQL_NEED_DATA zurück. **SQLCancel** wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber, der die entspricht der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
 Wenn **SQLParamData** wird aufgerufen, beim Senden von Daten für einen Parameter in einer SQL­Anweisung, jeder SQLSTATE, die von der Funktion wird aufgerufen, um die Ausführung der Anweisung zurückgegeben werden kann zurückgegeben werden kann (**SQLExecute** oder **SQLExecDirect**). Wenn sie, beim Senden von Daten für eine Spalte aufgerufen wird, die aktualisiert oder hinzugefügt, die mit **SQLBulkOperations** oder aktualisiert wird **SQLSetPos**, alle SQLSTATE zurückgegeben werden kann, die zurückgegeben werden kann  **SQLBulkOperations** oder **SQLSetPos**.  
  
## <a name="comments"></a>Kommentare  
 **SQLParamData** aufgerufen werden, um das Bereitstellen von Data-at-Execution-Daten für zwei Zwecke: Parameterdaten, die in einem Aufruf verwendet werden, **SQLExecute** oder **SQLExecDirect**, oder die Daten der Spalte, die verwendet wird, wenn eine Zeile aktualisiert oder hinzugefügt, die durch einen Aufruf von **SQLBulkOperations** oder durch einen Aufruf aktualisiert **SQLSetPos**. Zum Zeitpunkt der Ausführung **SQLParamData** zurückgegeben wird, um die Anwendung, die ein Indikator, der die Daten der Treiber erfordert.  
  
 Wenn eine Anwendung ruft **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos**, gibt der Treiber SQL_NEED_ Daten, wenn sie Data-at-Execution-Daten. Klicken Sie dann eine Anwendung ruft **SQLParamData** um zu bestimmen, welche die zu sendenden Daten. Wenn der Treiber die Parameterdaten erforderlich ist, gibt der Treiber der  *\*ValuePtrPtr* Ausgabe puffert den Wert, der die Anwendung im Rowset Puffer abgelegt. Die Anwendung kann diesen Wert verwenden, um zu bestimmen, welche Parameterdaten des Treibers anfordert. Wenn der Treiber die Daten der Spalte erforderlich ist, gibt der Treiber der  *\*ValuePtrPtr* Puffern Sie die Adresse, die die Spalte ursprünglich wie folgt, gebunden wurde:  
  
 *Adresse gebunden* + *Bindung Offset* + ((*Zeilennummer* - 1) X *Elementgröße*)  
  
 auf die Variablen definiert werden, wie in der folgenden Tabelle angegeben.  
  
|Variable|Description|  
|--------------|-----------------|  
|*Adresse gebunden*|Die Adresse angegeben wird, mit der *TargetValuePtr* -Argument in **SQLBindCol**.|  
|*Binden von Offset*|Der Wert, der mit dem SQL_ATTR_ROW_BIND_OFFSET_PTR Anweisung-Attribut angegebenen Adresse gespeichert.|  
|*Zeilennummer*|Die 1-basierten Nummer der Zeile im Rowset. Einzeiliges Abrufe, die standardmäßig, die werden zu können, ist dies 1.|  
|*Elementgröße*|Der Wert des Attributs SQL_ATTR_ROW_BIND_TYPE-Anweisung für die Daten- und Längenindikator/Puffer.|  
  
 Sie gibt überdies SQL_NEED_DATA zurückgegeben, die ein Indikator dafür, dass die Anwendung ist, die sie aufrufen, sollten **SQLPutData** zum Senden der Daten.  
  
 Ruft die Anwendung **SQLPutData** so oft wie nötig, um die Data-at-Execution-Daten für die Spalte oder Parameter zu senden. Nachdem alle Daten für die Spalte oder Parameter gesendet wurde, wird die Anwendung ruft **SQLParamData** erneut aus. Wenn **SQLParamData** erneut wird SQL_NEED_DATA zurückgegeben, für eine andere Spalte oder die Daten gesendet werden müssen. Die Anwendung erneut daher ruft **SQLPutData**. Wenn alle Data-at-Execution-Daten wurde gesendet für alle Parameter oder Spalten, klicken Sie dann **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, den Wert in  *\*ValuePtrPtr* nicht definiert ist, und die SQL-Anweisung ausgeführt werden kann oder die **SQLBulkOperations** oder **SQLSetPos** Aufruf verarbeitet werden kann.  
  
 Wenn **SQLParamData** stellt Parameterdaten für einen komplexen aktualisieren oder delete-Anweisung, die keine Zeilen in der Datenquelle, die den Aufruf von auswirkt, **SQLParamData** SQL_NO_DATA zurückgibt.  
  
 Weitere Informationen zu wie Data-at-Execution-Parameterdaten zur Ausführungszeit für die Anweisung übergeben wird, finden Sie unter "Übergeben von Parameterwerten" in [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) und [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md). Weitere Informationen zu wie Data-at-Execution-Spaltendaten aktualisiert oder hinzugefügt wird, finden Sie im Abschnitt "Verwenden von SQLSetPos" in [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Ausführen von Massenladen Updates mithilfe von Lesezeichen" in [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), und [Long-Daten, SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
 **SQLParamData** aufgerufen werden, um die gestreamte Ausgabeparameter abgerufen werden. Wenn **SQLMoreResults**, **SQLExecute**, **SQLGetData**, oder **SQLExecDirect** gibt SQL_PARAM_DATA_AVAILABLE, rufen Sie **SQLParamData** um zu bestimmen, welche Parameter einen Wert zur Verfügung hat. Weitere Informationen über SQL_PARAM_DATA_AVAILABLE und gestreamte Output-Parameter, finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer, an einen parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen über einen Parameter in einer Anweisung|[SQLDescribeParam-Funktion](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Senden von Daten von Parametern zum Zeitpunkt der Ausführung|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
