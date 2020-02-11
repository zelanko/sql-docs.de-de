---
title: SQLDescribeParam-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9c1ba115766b820cdcc4f671eeacf9eeec90a894
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68345447"
---
# <a name="sqldescribeparam-function"></a>SQLDescribeParam-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLDescribeParam** gibt die Beschreibung eines Parameter Markers zurück, der einer vorbereiteten SQL-Anweisung zugeordnet ist. Diese Informationen sind auch in den Feldern der IPD verfügbar.  
  
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
 Der Anweisungs Handle.  
  
 *ParameterNumber*  
 Der Parametermarker-Nummer, die nacheinander in einer aufsteigenden Parameterreihenfolge sortiert ist, beginnend bei 1.  
  
 *DataTypePtr*  
 Ausgeben Zeiger auf einen Puffer, in den der SQL-Datentyp des Parameters zurückgegeben werden soll. Dieser Wert wird aus dem Feld SQL_DESC_CONCISE_TYPE Datensatz der IPD gelesen. Dies ist einer der Werte im Abschnitt SQL- [Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) von Anhang D: Datentypen oder ein Treiber spezifischer SQL-Datentyp.  
  
 In ODBC 3. " *x*", "SQL_TYPE_DATE", "SQL_TYPE_TIME" oder "SQL_TYPE_TIMESTAMP" werden in * \*"DataTypePtr* " für Datums-, Uhrzeit-oder Zeitstempel-Daten zurückgegeben. in ODBC 2. *x*, SQL_DATE, SQL_TIME oder SQL_TIMESTAMP werden zurückgegeben. Der Treiber-Manager führt die erforderlichen Zuordnungen bei ODBC 2 aus. die *x* -Anwendung arbeitet mit ODBC 3. *x* -Treiber oder bei ODBC 3. die *x* -Anwendung arbeitet mit ODBC 2. *x* -Treiber  
  
 Wenn *ColumnNumber* gleich 0 (für eine Lesezeichen Spalte) ist, wird SQL_BINARY in * \*DataTypePtr* für Lesezeichen mit variabler Länge zurückgegeben. (SQL_INTEGER wird zurückgegeben, wenn Lesezeichen von ODBC 3 verwendet werden. *x* -Anwendung, die mit ODBC 2 arbeitet. *x* -Treiber oder ODBC 2. *x* -Anwendung, die mit ODBC 3 arbeitet. *x* -Treiber.)  
  
 Weitere Informationen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.  
  
 *ParameterSizePtr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Größe (in Zeichen) der Spalte oder des Ausdrucks der entsprechenden Parameter Markierung gemäß der Definition durch die Datenquelle zurückgegeben werden soll. Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalstellen, Länge von Oktett übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *Decimaldigitsptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in den die Anzahl der Dezimalstellen der Spalte oder des Ausdrucks des entsprechenden Parameters zurückgegeben werden soll, wie von der Datenquelle definiert. Weitere Informationen zu Dezimalziffern finden Sie unter [Spaltengröße, Dezimalstellen, Länge von Oktett übertragen und Größe anzeigen](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *Nullableptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem ein Wert zurückgegeben werden soll, der angibt, ob der Parameter NULL-Werte zulässt. Dieser Wert wird aus dem SQL_DESC_NULLABLE-Feld der IPD gelesen. Einer der folgenden:  
  
-   SQL_NO_NULLS: der-Parameter lässt keine NULL-Werte zu (Dies ist der Standardwert).  
  
-   SQL_NULLABLE: der Parameter lässt NULL-Werte zu.  
  
-   SQL_NULLABLE_UNKNOWN: der Treiber kann nicht bestimmen, ob der Parameter NULL-Werte zulässt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDescribeParam** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLDescribeParam** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger deskriptorindex.|(DM) der für das Argument *ParameterNumber* angegebene Wert ist kleiner als 1.<br /><br /> Der für das Argument *ParameterNumber* angegebene Wert war größer als die Anzahl der Parameter in der zugeordneten SQL-Anweisung.<br /><br /> Die Parameter Markierung war Teil einer nicht-DML-Anweisung.<br /><br /> Die Parameter Markierung war Teil einer **Auswahl** Liste.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|21s01|Die einfügewertliste stimmt nicht mit der Spaltenliste|Die Anzahl der Parameter in der **Insert** -Anweisung entsprach nicht der Anzahl der Spalten in der Tabelle, die in der-Anweisung angegeben ist.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) die Funktion wurde aufgerufen, bevor **SQLPrepare** oder **SQLExecDirect** für das *StatementHandle*aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLDescribeParam** -Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Parameter Markierungen werden in der Reihenfolge, in der Sie in der SQL-Anweisung angezeigt werden, in einer aufsteigenden Reihenfolge von Parametern nummeriert.  
  
 **SQLDescribeParam** gibt nicht den Typ (Eingabe, Eingabe/Ausgabe oder Ausgabe) eines Parameters in einer SQL-Anweisung zurück. Außer in Aufrufen von-Prozeduren sind alle Parameter in SQL-Anweisungen Eingabeparameter. Um den Typ jedes Parameters in einem Aufruf einer Prozedur zu ermitteln, ruft eine Anwendung **sqlprocedurecolenns**auf.  
  
 Weitere Informationen finden Sie unter [beschreiben von Parametern](../../../odbc/reference/develop-app/describing-parameters.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel wird der Benutzer zur Eingabe einer SQL-Anweisung aufgefordert und dann diese Anweisung vorbereitet. Anschließend wird **sqlnumparser** aufgerufen, um zu bestimmen, ob die Anweisung Parameter enthält. Wenn die Anweisung Parameter enthält, ruft Sie **SQLDescribeParam** auf, um diese Parameter zu beschreiben, und **SQLBindParameter** , um Sie zu binden. Schließlich wird der Benutzer aufgefordert, die Werte von Parametern einzugeben, und anschließend wird die Anweisung ausgeführt.  
  
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
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
