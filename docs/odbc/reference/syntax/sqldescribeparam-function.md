---
title: SQLDescribeParam-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeParam
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeParam
helpviewer_keywords:
- SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e810d2e7ff3f69faea5fdcbccbb7f7ba276df48
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537617"
---
# <a name="sqldescribeparam-function"></a>SQLDescribeParam-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLDescribeParam** gibt die Beschreibung einer parametermarkierung zugeordneten vorbereitete SQL-Anweisung zurück. Diese Informationen sind auch in den Feldern IPD zur Verfügung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLDescribeParam(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT *   DataTypePtr,  
      SQLULEN *       ParameterSizePtr,  
      SQLSMALLINT *   DecimalDigitsPtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="argument"></a>Argument  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *ParameterNumber*  
 [Eingabe] Marker Parameternummer sortiert sequenziell in aufsteigender Parameterreihenfolge, beginnend mit 1.  
  
 *DataTypePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem den SQL-Datentyp des Parameters zurückgegeben. Dieser Wert wird vom des IPD-Datensatzfeld SQL_DESC_CONCISE_TYPE gelesen. Dies können die Werte in der [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) Abschnitt Anhang D: Datentypen, oder einen Treiber-spezifische SQL-Datentyp.  
  
 In ODBC 3. *x*, SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP werden im zurückgegeben  *\*DataTypePtr* für Datum, Uhrzeit oder Zeitstempeldaten; in ODBC 2. *X*, SQL_DATE, SQL_TIME oder SQL_TIMESTAMP zurückgegeben. Der Treiber-Manager führt die erforderlichen Mappings, wenn eine ODBC-2. *x* Anwendung arbeitet mit einer ODBC 3. *X* Treiber oder wenn eine ODBC 3. *X* Anwendung arbeitet mit einer ODBC 2. *X* Treiber.  
  
 Beim *ColumnNumber* ist gleich 0 (für eine Lesezeichenspalte) ist, wird im SQL_BINARY zurückgegeben  *\*DataTypePtr* variabler Länge, die Lesezeichen. (SQL_INTEGER wird zurückgegeben, wenn Lesezeichen von einer ODBC-3 verwendet werden. *x* Anwendung mit einer ODBC 2. *X* Treiber oder von einer ODBC 2. *X* Anwendung mit einer ODBC 3. *X* Treiber.)  
  
 Weitere Informationen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu Treiber-spezifische SQL-Datentypen finden Sie in der vom Treiber-Dokumentation.  
  
 *ParameterSizePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Größe der Spalte oder des Ausdrucks der entsprechenden parametermarkierung in Zeichen zurückgeben, wenn die Datenquelle definiert. Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *DecimalDigitsPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Anzahl der Dezimalstellen der Spalte oder einen Ausdruck des entsprechenden Parameters zurückgeben, wenn die Datenquelle definiert. Weitere Informationen zu Dezimalstellen, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *NullablePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem einen Wert zurückgegeben, der angibt, ob der Parameter NULL-Werte zulässt. Dieser Wert wird aus dem Feld SQL_DESC_NULLABLE des IPD gelesen. Einer der folgenden Typen:  
  
-   SQL_NO_NULLS: Der Parameter lässt keine NULL-Werte (Dies ist der Standardwert).  
  
-   SQL_NULLABLE: Der Parameter zulässt NULL-Werte.  
  
-   SQL_NULLABLE_UNKNOWN: Der Treiber kann nicht bestimmen, ob der Parameter NULL-Werte zulässt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDescribeParam** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und eine *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLDescribeParam** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|(DM) der Wert für das Argument angegebene *ParameterNumber* ist kleiner als 1.<br /><br /> Der angegebene Wert für das Argument *ParameterNumber* war größer als die Anzahl von Parametern in der zugeordneten SQL-Anweisung.<br /><br /> Die parametermarkierung war Teil einer nicht-DML-Anweisung.<br /><br /> Die parametermarkierung war Teil einer **wählen** Liste.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|21S01|Die Liste einzufügender Werte entspricht nicht der Spaltenliste.|Die Anzahl von Parametern in der **einfügen** Anweisung entsprach nicht der Anzahl der Spalten in der Tabelle in der Anweisung.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) die Funktion wurde vor dem Aufruf aufgerufen **SQLPrepare** oder **SQLExecDirect** für die *StatementHandle*.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLDescribeParam** Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Parametermarkierungen sind nummeriert, in der Reihenfolge der zunehmenden Parameter, beginnend mit 1, in der Reihenfolge, die sie in der SQL-Anweisung angezeigt werden.  
  
 **SQLDescribeParam** gibt nicht den Typ (Eingabe, Eingabe/Ausgabe- oder Ausgabe) eines Parameters in einer SQL­Anweisung zurück. Mit Ausnahme sind alle Parameter im SQL-Anweisungen in Aufrufen von Prozeduren Eingabeparameter. Um zu bestimmen, den Typ jedes Parameters in einem Aufruf an eine Prozedur, eine Anwendung ruft **SQLProcedureColumns**.  
  
 Weitere Informationen finden Sie unter [Parameter beschreiben](../../../odbc/reference/develop-app/describing-parameters.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel fordert den Benutzer zu einer SQL-Anweisung, und dann wird diese Anweisung vorbereitet. Anschließend ruft er **SQLNumParams** zu bestimmen, ob die Anweisung Parameter enthält. Wenn die Anweisung Parameter enthält, ruft es **SQLDescribeParam** um diesen Parameter zu beschreiben und **SQLBindParameter** sie binden. Abschließend fordert den Benutzer für die Werte aller Parameter, und klicken Sie dann die Anweisung ausführt wird.  
  
```cpp  
SQLCHAR       Statement[100];  
SQLSMALLINT   NumParams, i, DataType, DecimalDigits, Nullable;  
SQLUINTEGER   ParamSize;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement and prepare it.  
GetSQLStatement(Statement);  
SQLPrepare(hstmt, Statement, SQL_NTS);  
  
// Check to see if there are any parameters. If so, process them.  
SQLNumParams(hstmt, &NumParams);  
if (NumParams) {  
   // Allocate memory for three arrays. The first holds pointers to buffers in which  
   // each parameter value will be stored in character form. The second contains the  
   // length of each buffer. The third contains the length/indicator value for each  
   // parameter.  
   SQLPOINTER * PtrArray = (SQLPOINTER *) malloc(NumParams * sizeof(SQLPOINTER));  
   SQLINTEGER * BufferLenArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
   SQLINTEGER * LenOrIndArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
  
   for (i = 0; i < NumParams; i++) {  
   // Describe the parameter.  
   SQLDescribeParam(hstmt, i + 1, &DataType, &ParamSize, &DecimalDigits, &Nullable);  
  
   // Call a helper function to allocate a buffer in which to store the parameter  
   // value in character form. The function determines the size of the buffer from  
   // the SQL data type and parameter size returned by SQLDescribeParam and returns  
   // a pointer to the buffer and the length of the buffer.  
   AllocParamBuffer(DataType, ParamSize, &PtrArray[i], &BufferLenArray[i]);  
  
   // Bind the memory to the parameter. Assume that we only have input parameters.  
   SQLBindParameter(hstmt, i + 1, SQL_PARAM_INPUT, SQL_C_CHAR, DataType, ParamSize,  
         DecimalDigits, PtrArray[i], BufferLenArray[i],  
         &LenOrIndArray[i]);  
  
   // Prompt the user for the value of the parameter and store it in the memory  
   // allocated earlier. For simplicity, this function does not check the value  
   // against the information returned by SQLDescribeParam. Instead, the driver does  
   // this when the statement is executed.  
   GetParamValue(PtrArray[i], BufferLenArray[i], &LenOrIndArray[i]);  
   }  
}  
  
// Execute the statement.  
SQLExecute(hstmt);  
  
// Process the statement further, such as retrieving results (if any) and closing the  
// cursor (if any). Code not shown.  
  
// Free the memory allocated for each parameter and the memory allocated for the arrays  
// of pointers, buffer lengths, and length/indicator values.  
for (i = 0; i < NumParams; i++) free(PtrArray[i]);  
free(PtrArray);  
free(BufferLenArray);  
free(LenOrIndArray);  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer, an einen parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
