---
description: SQLCopyDesc-Funktion
title: Sqlcopydebug-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCopyDesc
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLCopyDesc
helpviewer_keywords:
- SQLCopyDesc function [ODBC]
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ede6d52614c1c35cdc28f6d85e8b3be61235b4ca
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461192"
---
# <a name="sqlcopydesc-function"></a>SQLCopyDesc-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLCopyDesc** kopiert Deskriptorinformationen von einem Deskriptorhandle in ein anderes.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *Sourcedebug*  
 Der Das Quell Deskriptorhandle.  
  
 *Targetbeschandle*  
 Der Ziel Deskriptorhandle. Das *targettoschandle* -Argument kann ein Handle für einen Anwendungs Deskriptor oder eine IPD sein. *Targetdeschandle* kann nicht auf ein Handle für einen IRD festgelegt werden, oder **SQLCopyDesc** gibt SQLSTATE HY016 (ein Implementierungs Zeilen Deskriptor kann nicht geändert werden) zurück.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCopyDesc** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_DESC und einem *handle* von *targetdeschandle*abgerufen werden. Wenn ein ungültiges *sourcedebug* -Attribut im-Befehl weitergegeben wurde, wird SQL_INVALID_HANDLE zurückgegeben, aber es wird kein SQLSTATE zurückgegeben. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLCopyDesc** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
 Wenn ein Fehler zurückgegeben wird, wird der **sqlcopyde** -Befehl sofort abgebrochen, und der Inhalt der Felder im *targetbeschandle* -Deskriptor ist nicht definiert.  
  
 Da **SQLCopyDesc** durch Aufrufen von **SQLGetDescField** und **SQLSetDescField**implementiert werden kann, gibt **SQLCopyDesc** möglicherweise Sqlstates zurück, die von **SQLGetDescField** oder **SQLSetDescField**zurückgegeben werden.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte den erforderlichen Arbeitsspeicher nicht zuordnen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY007|Die zugehörige Anweisung ist nicht vorbereitet.|*Sourcetoschandle* wurde einem IRD zugeordnet, und das zugehörige Anweisungs Handle befand sich nicht im vorbereiteten oder ausgeführten Zustand.|  
|HY010|Funktions Sequenz Fehler|(DM) das Deskriptorhandle in *sourcetoschandle* oder *targettoschandle* wurde mit einem *StatementHandle* verknüpft, für das eine asynchron ausgeführte Funktion (nicht diese) aufgerufen wurde und noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) das Deskriptorhandle in *sourcedeschandle* oder *targetdeschandle* wurde mit einem *StatementHandle* verknüpft, für das **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** aufgerufen und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit *sourcedeschandle* oder *targetdeschandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **sqlcopyde SC** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungs Handles aufgerufen, die mit *sourcedebug* oder *targetdebug* verknüpft sind, und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY016|Ein Implementierungs Zeilen Deskriptor kann nicht geändert werden.|*Targetbeschandle* wurde einem IRD zugeordnet.|  
|HY021|Inkonsistente Deskriptorinformationen|Die während einer Konsistenzprüfung überprüften Deskriptorinformationen waren nicht konsistent. Weitere Informationen finden Sie unter "Konsistenzprüfungen" in **SQLSetDescField**.|  
|HY092|Ungültiger Attribut/Options Bezeichner|Der **SQLCopyDesc** -Befehl hat einen Aufrufen von **SQLSetDescField**angefordert, " * \* ValuePtr* " war jedoch für das *fieldidentifier* -Argument in " *targetdeschandle*" nicht gültig.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der mit *sourcedeschandle* oder *targetdeschandle* verknüpfte Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Bei einem **SQLCopyDesc** -Befehl werden die Felder des Quell Deskriptorhandles in das Ziel Deskriptorhandle kopiert. Felder können nur in einen Anwendungs Deskriptor oder eine IPD, aber nicht in einen IRD kopiert werden. Felder können entweder aus einer Anwendung oder aus einem Implementierungs Deskriptor kopiert werden.  
  
 Felder können nur von einem IRD kopiert werden, wenn sich das Anweisungs Handle im vorbereiteten oder ausgeführten Zustand befindet. Andernfalls gibt die Funktion SQLSTATE HY007 zurück (die zugehörige Anweisung ist nicht vorbereitet).  
  
 Felder können aus einem IPD kopiert werden, unabhängig davon, ob eine-Anweisung vorbereitet wurde. Wenn eine SQL-Anweisung mit dynamischen Parametern vorbereitet wurde und die automatische Auffüllung der IPD unterstützt und aktiviert ist, wird die IPD vom Treiber aufgefüllt. Wenn **sqlcopydebug** mit der IPD-Datei als *sourcedebug*aufgerufen wird, werden die ausgefüllten Felder kopiert. Wenn die IPD nicht vom Treiber aufgefüllt wird, werden die Inhalte der in der IPD ursprünglichen Felder kopiert.  
  
 Alle Felder des Deskriptors, außer SQL_DESC_ALLOC_TYPE (gibt an, ob das Deskriptorhandle automatisch oder explizit zugewiesen wurde), werden kopiert, unabhängig davon, ob das Feld für den Ziel Deskriptor definiert ist. Kopierte Felder überschreiben die vorhandenen Felder.  
  
 Der Treiber kopiert alle Deskriptorfelder, wenn die Argumente *sourcedebug* und *targetbeschandle* dem gleichen Treiber zugeordnet sind, auch wenn sich die Treiber in zwei unterschiedlichen Verbindungen oder Umgebungen befinden. Wenn die Argumente *sourcedeschandle* und *targetdeschandle* verschiedenen Treibern zugeordnet sind, kopiert der Treiber-Manager ODBC-definierte Felder, kopiert jedoch keine Treiber definierten Felder oder Felder, die nicht von ODBC für den Deskriptortyp definiert sind.  
  
 Der **sqlcopydebug** -aufrufsvorgang wird sofort abgebrochen, wenn ein Fehler auftritt.  
  
 Wenn das SQL_DESC_DATA_PTR Feld kopiert wird, wird für den Ziel Deskriptor eine Konsistenzprüfung durchgeführt. Wenn bei der Konsistenzprüfung ein Fehler auftritt, wird SQLSTATE HY021 (inkonsistente Deskriptorinformationen) zurückgegeben, und der **SQLCopyDesc** -Befehl wird sofort abgebrochen. Weitere Informationen zu Konsistenzprüfungen finden Sie unter "Konsistenzprüfungen" in der [SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Deskriptorhandles können über Verbindungen kopiert werden, auch wenn sich die Verbindungen in unterschiedlichen Umgebungen befinden. Wenn der Treiber-Manager erkennt, dass die Quell-und Ziel Deskriptorhandles nicht zur gleichen Verbindung gehören und die beiden Verbindungen zu separaten Treibern gehören, wird **SQLCopyDesc** implementiert, indem eine Feld Weise Kopie mithilfe von **SQLGetDescField** und **SQLSetDescField**durchgeführt wird.  
  
 Wenn **SQLCopyDesc** mit einem *sourcedeschandle* auf einem Treiber und einem *targetdeschandle* auf einem anderen Treiber aufgerufen wird, wird die Fehler Warteschlange von *sourcedeschandle* gelöscht. Dies tritt auf, da **SQLCopyDesc** in diesem Fall durch Aufrufe von **SQLGetDescField** und **SQLSetDescField**implementiert wird.  
  
> [!NOTE]  
>  Eine Anwendung kann ein explizit zugeordneter Deskriptorhandle einem *StatementHandle*zuordnen, anstatt **SQLCopyDesc** zum Kopieren von Feldern von einem Deskriptor in einen anderen zu aufrufen. Ein explizit zugeordneter Deskriptor kann einem anderen *StatementHandle* desselben *connectionHandle* zugeordnet werden, indem das SQL_ATTR_APP_ROW_DESC-oder SQL_ATTR_APP_PARAM_DESC Statement-Attribut auf das Handle des explizit zugeordneten Deskriptors festgelegt wird. Wenn dies geschehen ist, muss **SQLCopyDesc** nicht aufgerufen werden, um Deskriptorfeldwerte von einem Deskriptor in einen anderen zu kopieren. Ein Deskriptorhandle kann jedoch nicht mit einem *StatementHandle* auf einem anderen *connectionHandle*verknüpft werden. um dieselben Deskriptorfeldwerte für *statementhandles* auf verschiedenen *connectionhandles*zu verwenden, muss **SQLCopyDesc** aufgerufen werden.  
  
 Eine Beschreibung der Felder in einem deskriptorheader oder Datensatz finden Sie unter [SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="copying-rows-between-tables"></a>Kopieren von Zeilen zwischen Tabellen  
 Eine Anwendung kann Daten aus einer Tabelle in eine andere kopieren, ohne die Daten auf Anwendungsebene zu kopieren. Zu diesem Zweck bindet die Anwendung dieselben Datenpuffer und Deskriptorinformationen an eine-Anweisung, die die Daten abruft, und die-Anweisung, die die Daten in eine Kopie einfügt. Dies kann erreicht werden, indem Sie einen Anwendungs Deskriptor freigeben (einen explizit zugeordneten Deskriptor als ARD an eine Anweisung und die APD in einem anderen binden) oder indem Sie **SQLCopyDesc** zum Kopieren der Bindungen zwischen dem ARD und der APD der beiden Anweisungen verwenden. Wenn sich die-Anweisungen in unterschiedlichen Verbindungen befinden, muss **sqlcopydebug** verwendet werden. Außerdem muss **sqlcopydebug** aufgerufen werden, um die Bindungen zwischen dem IRD und der IPD der beiden Anweisungen zu kopieren. Beim Kopieren von Anweisungen über die gleiche Verbindung muss der SQL_ACTIVE_STATEMENTS Informationstyp, der vom Treiber für einen **SQLGetInfo-Befehl** zurückgegeben wird, größer als 1 sein, damit dieser Vorgang erfolgreich ausgeführt werden kann. (Dies ist nicht der Fall, wenn Verbindungen über mehrere Verbindungen hinweg kopiert werden.)  
  
### <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel werden deskriptorvorgänge verwendet, um die Felder der partssource-Tabelle in die partscopy-Tabelle zu kopieren. Der Inhalt der partssource-Tabelle wird in rowsetpuffer in *hstmt0*abgerufen. Diese Werte werden als Parameter einer INSERT-Anweisung auf *hstmt1* verwendet, um die Spalten der partscopy-Tabelle aufzufüllen. Zu diesem Zweck werden die Felder des IRD von *hstmt0* in die Felder der IPD von *hstmt1*kopiert, und die Felder der *hstmt0 von* werden in die Felder der APD von *hstmt1*kopiert. Verwenden Sie **SQLSetDescField** , um das SQL_DESC_PARAMETER_TYPE Attribut von IPD auf SQL_PARAM_INPUT festzulegen, wenn Sie IRD-Felder aus einer Anweisung mit Ausgabeparametern in IPD-Felder kopieren, die Eingabeparameter sein müssen.  
  
```cpp  
#define ROWS 100  
#define DESC_LEN 50  
#define SQL_SUCCEEDED(rc) (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO)  
  
// Template for a row  
typedef struct {  
   SQLINTEGER   sPartID;  
   SQLINTEGER   cbPartID;  
   SQLUCHAR     szDescription[DESC_LENGTH];  
   SQLINTEGER   cbDescription;  
   REAL         sPrice;  
   SQLINTEGER   cbPrice;  
} PartsSource;  
  
PartsSource    rget[ROWS];          // rowset buffer  
SQLUSMALLINT   sts_ptr[ROWS];       // status pointer  
SQLHSTMT       hstmt0, hstmt1;  
SQLHDESC       hArd0, hIrd0, hApd1, hIpd1;  
  
// ARD and IRD of hstmt0  
SQLGetStmtAttr(hstmt0, SQL_ATTR_APP_ROW_DESC, &hArd0, 0, NULL);  
SQLGetStmtAttr(hstmt0, SQL_ATTR_IMP_ROW_DESC, &hIrd0, 0, NULL);  
  
// APD and IPD of hstmt1  
SQLGetStmtAttr(hstmt1, SQL_ATTR_APP_PARAM_DESC, &hApd1, 0, NULL);  
SQLGetStmtAttr(hstmt1, SQL_ATTR_IMP_PARAM_DESC, &hIpd1, 0, NULL);  
  
// Use row-wise binding on hstmt0 to fetch rows  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER) sizeof(PartsSource), 0);  
  
// Set rowset size for hstmt0  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
  
// Execute a select statement  
SQLExecDirect(hstmt0, "SELECT PARTID, DESCRIPTION, PRICE FROM PARTS ORDER BY 3, 1, 2"",  
               SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt0, 1, SQL_C_SLONG, rget[0].sPartID, 0,   
   &rget[0].cbPartID);  
SQLBindCol(hstmt0, 2, SQL_C_CHAR, &rget[0].szDescription, DESC_LEN,   
   &rget[0].cbDescription);  
SQLBindCol(hstmt0, 3, SQL_C_FLOAT, rget[0].sPrice,   
   0, &rget[0].cbPrice);  
  
// Perform parameter bindings on hstmt1.   
SQLCopyDesc(hArd0, hApd1);  
SQLCopyDesc(hIrd0, hIpd1);  
  
// Set the array status pointer of IRD  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_STATUS_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the ARRAY_STATUS_PTR field of APD to be the same  
// as that in IRD.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_PARAM_OPERATION_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the hIpd1 records as input parameters  
rc = SQLSetDescField(hIpd1, 1, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 2, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 3, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
  
// Prepare an insert statement on hstmt1. PartsCopy is a copy of  
// PartsSource  
SQLPrepare(hstmt1, "INSERT INTO PARTS_COPY VALUES (?, ?, ?)", SQL_NTS);  
  
// In a loop, fetch a rowset, and copy the fetched rowset to PARTS_COPY  
  
rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
while (SQL_SUCCEEDED(rc)) {  
  
   // After the call to SQLFetchScroll, the status array has row   
   // statuses. This array is used as input status in the APD  
   // and hence determines which elements of the rowset buffer  
   // are inserted.  
   SQLExecute(hstmt1);  
  
   rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
} // while  
```  
  
### <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Mehrere Deskriptorfelder werden abgerufen.|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen deskriptorfelds|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen mehrerer Deskriptorfelder|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
