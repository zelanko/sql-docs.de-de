---
title: SQLDescribeParam-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeParam
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeParam
helpviewer_keywords:
- SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be6d076ca121923a4b6769c7dad5269c3fd642ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301160"
---
# <a name="sqldescribeparam-function"></a>SQLDescribeParam-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLDescribeParam** gibt die Beschreibung einer Parametermarkierung zurück, die einer vorbereiteten SQL-Anweisung zugeordnet ist. Diese Informationen sind auch in den Feldern des IPD verfügbar.  
  
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
 [Eingabe] Parameter-Marker-Nummer sequenziell in steigender Parameterreihenfolge sortiert, beginnend bei 1.  
  
 *DataTypePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem der SQL-Datentyp des Parameters zurückgegeben werden soll. Dieser Wert wird aus dem SQL_DESC_CONCISE_TYPE Datensatzfeld der IPD gelesen. Dies ist einer der Werte im Abschnitt [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen oder ein treiberspezifischer SQL-Datentyp.  
  
 In ODBC 3. *x*, SQL_TYPE_DATE, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP werden in * \*DataTypePtr* für Datums-, Uhrzeit- oder Zeitstempeldaten zurückgegeben. in ODBC 2. *x*, SQL_DATE, SQL_TIME oder SQL_TIMESTAMP werden zurückgegeben. Der Treiber-Manager führt die erforderlichen Zuordnungen aus, wenn ein ODBC 2. *x-Anwendung* arbeitet mit einem ODBC 3. *x-Treiber* oder wenn ein ODBC 3. *x-Anwendung* arbeitet mit einem ODBC 2. *x-Treiber.*  
  
 Wenn *ColumnNumber* gleich 0 ist (für eine Lesezeichenspalte), wird SQL_BINARY in * \*DataTypePtr* für Lesezeichen variabler Länge zurückgegeben. (SQL_INTEGER wird zurückgegeben, wenn Lesezeichen von einem ODBC 3 verwendet werden. *x* Anwendung, die mit einem ODBC 2 arbeitet. *x-Treiber* oder durch einen ODBC 2. *x* Anwendung, die mit einem ODBC 3 arbeitet. *x* x-Treiber.)  
  
 Weitere Informationen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.  
  
 *ParameterSizePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Größe der Spalte oder des Ausdrucks der entsprechenden Parametermarkierung, wie sie von der Datenquelle definiert wird, in Zeichen zurückgegeben werden soll. Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *DecimalDigitsPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Anzahl der Dezimalstellen der Spalte oder des Ausdrucks des entsprechenden Parameters, wie in der Datenquelle definiert, zurückgegeben werden soll. Weitere Informationen zu Dezimalstellen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *NullablePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem ein Wert zurückgegeben wird, der angibt, ob der Parameter NULL-Werte zulässt. Dieser Wert wird aus dem SQL_DESC_NULLABLE Feld der IPD gelesen. Einer der folgenden:  
  
-   SQL_NO_NULLS: Der Parameter lässt keine NULL-Werte zu (dies ist der Standardwert).  
  
-   SQL_NULLABLE: Der Parameter lässt NULL-Werte zu.  
  
-   SQL_NULLABLE_UNKNOWN: Der Treiber kann nicht bestimmen, ob der Parameter NULL-Werte zulässt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDescribeParam** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLDescribeParam** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|(DM) Der für das Argument *ParameterNumber* angegebene Wert ist kleiner als 1.<br /><br /> Der für das Argument *ParameterNumber* angegebene Wert war größer als die Anzahl der Parameter in der zugeordneten SQL-Anweisung.<br /><br /> Die Parametermarkierung war Teil einer Nicht-DML-Anweisung.<br /><br /> Die Parametermarkierung war **SELECT** Teil einer SELECT-Liste.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|21S01|Wertliste einfügen stimmt nicht mit der Spaltenliste überein|Die Anzahl der Parameter in der **INSERT-Anweisung** stimmt nicht mit der Anzahl der Spalten in der Tabelle überein, die in der Anweisung benannt sind.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Die Funktion wurde aufgerufen, bevor **SQLPrepare** oder **SQLExecDirect** für *den StatementHandle*aufgerufen wurde.<br /><br /> (DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLDescribeParam-Funktion** aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Parametermarkierungen werden in zunehmender Parameterreihenfolge nummeriert, beginnend mit 1, in der Reihenfolge, in der sie in der SQL-Anweisung angezeigt werden.  
  
 **SQLDescribeParam** gibt den Typ (Eingabe, Eingabe/Ausgabe oder Ausgabe) eines Parameters in einer SQL-Anweisung nicht zurück. Außer bei Aufrufen von Prozeduren sind alle Parameter in SQL-Anweisungen Eingabeparameter. Um den Typ der einzelnen Parameter in einem Aufruf einer Prozedur zu bestimmen, ruft eine Anwendung **SQLProcedureColumns**auf.  
  
 Weitere Informationen finden Sie unter [Beschreiben von Parametern](../../../odbc/reference/develop-app/describing-parameters.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel wird der Benutzer zur Eingabe einer SQL-Anweisung aufgefordert und anschließend vorbereitet. Als Nächstes ruft es **SQLNumParams** auf, um zu bestimmen, ob die Anweisung Parameter enthält. Wenn die Anweisung Parameter enthält, ruft sie **SQLDescribeParam** auf, um diese Parameter zu beschreiben, und **SQLBindParameter,** um sie zu binden. Schließlich fordert er den Benutzer zur Eingabe der Werte aller Parameter auf und führt dann die Anweisung aus.  
  
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
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an einen Parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
