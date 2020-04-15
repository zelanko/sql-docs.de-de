---
title: SQLBindParameter-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBindParameter
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBindParameter
helpviewer_keywords:
- SQLBindParameter function [ODBC]
ms.assetid: 38349d4b-be03-46f9-9d6a-e50dd144e225
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02f50862bcfb0295c7f098afc6856c91e0249f66
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301360"
---
# <a name="sqlbindparameter-function"></a>SQLBindParameter-Funktion

**Konformität**  
 Eingeführte Version: ODBC 2.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLBindParameter** bindet einen Puffer an eine Parametermarkierung in einer SQL-Anweisung. **SQLBindParameter** unterstützt die Bindung an einen Unicode C-Datentyp, auch wenn der zugrunde liegende Treiber Keine Unicode-Daten unterstützt.  
  
> [!NOTE]  
>  Diese Funktion ersetzt die ODBC 1.0-Funktion **SQLSetParam**. Weitere Informationen finden Sie unter "Kommentare".  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN SQLBindParameter(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT     InputOutputType,  
      SQLSMALLINT     ValueType,  
      SQLSMALLINT     ParameterType,  
      SQLULEN         ColumnSize,  
      SQLSMALLINT     DecimalDigits,  
      SQLPOINTER      ParameterValuePtr,  
      SQLLEN          BufferLength,  
      SQLLEN *        StrLen_or_IndPtr);  
```
  
## <a name="arguments"></a>Argumente

 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *ParameterNumber*  
 [Eingabe] Parameternummer, sequenziell in steigender Parameterreihenfolge sortiert, beginnend bei 1.  
  
 *InputOutputType*  
 [Eingabe] Der Typ des Parameters. Weitere Informationen finden Sie unter *"InputOutputType* Argument" in "Kommentare".  
  
 *Valuetype*  
 [Eingabe] Der C-Datentyp des Parameters. Weitere Informationen finden Sie unter *"ValueType-Argument"* in "Kommentare".  
  
 *ParameterType*  
 [Eingabe] Der SQL-Datentyp des Parameters. Weitere Informationen finden Sie unter *"ParameterType* Argument" in "Kommentare".  
  
 *ColumnSize*  
 [Eingabe] Die Größe der Spalte oder des Ausdrucks der entsprechenden Parametermarkierung. Weitere Informationen finden Sie unter *"ColumnSize* Argument" in "Kommentare".  
  
 Wenn Ihre Anwendung auf einem 64-Bit-Windows-Betriebssystem ausgeführt wird, finden Sie weitere Informationen unter [ODBC 64-Bit Information](../../../odbc/reference/odbc-64-bit-information.md).  
  
 *DecimalDigits*  
 [Eingabe] Die Dezimalstellen der Spalte oder des Ausdrucks der entsprechenden Parametermarkierung. Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *ParameterValuePtr*  
 [Verzögerte Eingabe] Ein Zeiger auf einen Puffer für die Daten des Parameters. Weitere Informationen finden Sie unter *"ParameterValuePtr-Argument"* in "Kommentare".  
  
 *BufferLength*  
 [Eingang/Ausgang] Länge des *ParameterValuePtr-Puffers* in Bytes. Weitere Informationen finden Sie unter *"BufferLength-Argument"* in "Kommentare".  
  
 Siehe [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird.  
  
 *StrLen_or_IndPtr*  
 [Verzögerte Eingabe] Ein Zeiger auf einen Puffer für die Länge des Parameters. Weitere Informationen finden Sie unter *"StrLen_or_IndPtr* Argument" in "Kommentare".  
  
## <a name="returns"></a>Rückgabe

 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose

 Wenn **SQLBindParameter** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLBindParameter** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  

|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|Der durch das *ValueType-Argument* identifizierte Datentyp kann nicht in den Datentyp konvertiert werden, der durch das *ParameterType-Argument* identifiziert wird. Beachten Sie, dass dieser Fehler möglicherweise von **SQLExecDirect**, **SQLExecute**oder **SQLPutData** zur Ausführungszeit anstelle von **SQLBindParameter**zurückgegeben wird.|  
|07009|Ungültiger Deskriptorindex|(DM) Der für das Argument *ParameterNumber* angegebene Wert war kleiner als 1.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im **MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY003|Ungültiger Anwendungspuffertyp|Der vom Argument *ValueType* angegebene Wert war kein gültiger C-Datentyp oder SQL_C_DEFAULT.|  
|HY004|Ungültiger SQL-Datentyp|Der für das Argument *ParameterType* angegebene Wert war weder ein gültiger ODBC SQL-Datentypbezeichner noch ein treiberspezifischer SQL-Datentypbezeichner, der vom Treiber unterstützt wird.|  
|HY009|Ungültiger Argumentwert|(DM) Das Argument *ParameterValuePtr* war ein Nullzeiger, das Argument *StrLen_or_IndPtr* ein Nullzeiger und das Argument *InputOutputType* war nicht SQL_PARAM_OUTPUT.<br /><br /> (DM) SQL_PARAM_OUTPUT, wobei das Argument *ParameterValuePtr* ein Nullzeiger war, der C-Typ char oder binär war und die BufferLength (*cbValueMax*) größer als 0 war.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als **SQLBindParameter** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY021|Inkonsistente Deskriptorinformationen|Die bei einer Konsistenzprüfung überprüften Deskriptorinformationen waren nicht konsistent. (Siehe Abschnitt "Konsistenzprüfungen" in **SQLSetDescField**.)<br /><br /> Der für das Argument *DecimalDigits* angegebene Wert lag außerhalb des Wertebereichs, der von der Datenquelle für eine Spalte des SQL-Datentyps unterstützt wird, der durch das *ParameterType-Argument* angegeben wird.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der Wert in *BufferLength* war kleiner als 0. (Siehe beschreibung des SQL_DESC_DATA_PTR Feldes in **SQLSetDescField**.)|  
|HY104|Ungültiger Genauigkeits- oder Skalierungswert|Der für das Argument *ColumnSize* oder *DecimalDigits* angegebene Wert lag außerhalb des Wertebereichs, der von der Datenquelle für eine Spalte des SQL-Datentyps unterstützt wird, der durch das *ParameterType-Argument* angegeben wird.|  
|HY105|Ungültiger Parametertyp|(DM) Der für das Argument *InputOutputType* angegebene Wert war ungültig. (Siehe "Kommentare.")|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der Treiber oder die Datenquelle unterstützt die Konvertierung, die durch die Kombination des für das Argument *ValueType* angegebenen Werts und des treiberspezifischen Werts, der für das Argument *ParameterType*angegeben ist, nicht angegeben wird.<br /><br /> Der für das Argument *ParameterType* angegebene Wert war ein gültiger ODBC SQL-Datentypbezeichner für die vom Treiber unterstützte ODBC-Version, wurde jedoch vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Der Treiber unterstützt nur ODBC 2. *x* und das Argument *ValueType* war eines der folgenden:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> und alle Intervall-C-Datentypen, die in [Anhang](../../../odbc/reference/appendixes/c-data-types.md) D: Datentypen aufgeführt sind.<br /><br /> Der Treiber unterstützt nur ODBC-Versionen vor 3.50, und das Argument *ValueType* wurde SQL_C_GUID.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare

 Eine Anwendung ruft **SQLBindParameter** auf, um jede Parametermarkierung in einer SQL-Anweisung zu binden. Bindungen bleiben so lange wirksam, bis die Anwendung **SQLBindParameter** erneut aufruft, **SQLFreeStmt** mit der Option SQL_RESET_PARAMS aufruft oder **SQLSetDescField** aufruft, um das SQL_DESC_COUNT Headerfeld der APD auf 0 festzulegen.  
  
 Weitere Informationen zu Parametern finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md). Weitere Informationen zu Parameterdatentypen und Parametermarkierungen finden Sie unter [Parameterdatentypen](../../../odbc/reference/appendixes/parameter-data-types.md) und [Parametermarkierungen](../../../odbc/reference/appendixes/parameter-markers.md) in Anhang C: SQL-Grammatik.  
  
## <a name="parameternumber-argument"></a>ParameterNumber-Argument  
 Wenn *ParameterNumber* im Aufruf von **SQLBindParameter** größer als der Wert von SQL_DESC_COUNT ist, wird **SQLSetDescField** aufgerufen, um den Wert von SQL_DESC_COUNT zu *ParameterNumber*zu erhöhen.  
  
## <a name="inputoutputtype-argument"></a>InputOutputType-Argument  
 Das *Argument InputOutputType* gibt den Typ des Parameters an. Dieses Argument legt das SQL_DESC_PARAMETER_TYPE Feld der IPD fest. Alle Parameter in SQL-Anweisungen, die keine Prozeduren aufrufen, z. **B.** INSERT-Anweisungen, sind *eingabe**parameter*. Parameter in Prozeduraufrufen können Eingabe-, Ein-/Ausgabe- oder Ausgabeparameter sein. (Eine Anwendung ruft **SQLProcedureColumns** auf, um den Typ eines Parameters in einem Prozeduraufruf zu bestimmen; Parameter, deren Typ nicht bestimmt werden kann, werden als Eingabeparameter angenommen.)  
  
 Das *InputOutputType*-Argument ist einer der folgenden Werte:  
  
-   SQL_PARAM_INPUT. Der Parameter kennzeichnet einen Parameter in einer SQL-Anweisung, der keine Prozedur, z. B. eine **INSERT-Anweisung,** oder einen Eingabeparameter in einer Prozedur aufruft. Beispielsweise sind die Parameter in **INSERT INTO Employee VALUES (?, ?, ?)** Eingabeparameter, während die Parameter in **"call AddEmp(?, ?, ?)"** Eingabeparameter sein können, aber nicht unbedingt sind.  
  
     Wenn die Anweisung ausgeführt wird, sendet der Treiber Daten für den Parameter an die Datenquelle. Der \* *ParameterValuePtr-Puffer* muss einen gültigen Eingabewert enthalten, oder der **StrLen_or_IndPtr-Puffer* muss SQL_NULL_DATA, SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros enthalten.  
  
     Wenn eine Anwendung den Typ eines Parameters in einem Prozeduraufruf nicht bestimmen kann, legt sie *InputOutputType* auf SQL_PARAM_INPUT. Wenn die Datenquelle einen Wert für den Parameter zurückgibt, verwirft der Treiber ihn.  
  
-   SQL_PARAM_INPUT_OUTPUT. Der Parameter kennzeichnet einen Eingabe-/Ausgabeparameter in einer Prozedur. Der Parameter in **"call GetEmpDept(?)"** ist z. B. ein Eingabe-/Ausgabeparameter, der den Namen eines Mitarbeiters akzeptiert und den Namen der Abteilung des Mitarbeiters zurückgibt.  
  
     Wenn die Anweisung ausgeführt wird, sendet der Treiber Daten für den Parameter an die Datenquelle. Der \* *ParameterValuePtr-Puffer* muss einen gültigen \*Eingabewert enthalten, oder der *StrLen_or_IndPtr-Puffer* muss SQL_NULL_DATA, SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros enthalten. Nachdem die Anweisung ausgeführt wurde, gibt der Treiber Daten für den Parameter an die Anwendung zurück. Wenn die Datenquelle keinen Wert für einen Eingabe-/Ausgabeparameter zurückgibt, legt der Treiber den **StrLen_or_IndPtr* Puffer auf SQL_NULL_DATA.  
  
    > [!NOTE]  
    >  Wenn eine ODBC 1.0-Anwendung **SQLSetParam** in einem ODBC 2.0-Treiber aufruft, konvertiert der Treiber-Manager dies in einen Aufruf von **SQLBindParameter,** bei dem das *Argument InputOutputType* auf SQL_PARAM_INPUT_OUTPUT festgelegt ist.  
  
-   SQL_PARAM_OUTPUT. Der Parameter kennzeichnet den Rückgabewert einer Prozedur oder eines Ausgabeparameters in einer Prozedur. In beiden Fällen werden diese als *Ausgabeparameter*bezeichnet. Beispielsweise ist der Parameter in der Datei **GetNextEmpID** ein Ausgabeparameter, der die nächste Mitarbeiter-ID zurückgibt.  
  
     Nachdem die Anweisung ausgeführt wurde, gibt der Treiber Daten für den Parameter an die Anwendung zurück, es sei denn, die *Argumente ParameterValuePtr* und *StrLen_or_IndPtr* sind beide NULL-Zeiger, in diesem Fall verwirft der Treiber den Ausgabewert. Wenn die Datenquelle keinen Wert für einen Ausgabeparameter zurückgibt, legt der Treiber den **-StrLen_or_IndPtr-Puffer* auf SQL_NULL_DATA.  
  
-   SQL_PARAM_INPUT_OUTPUT_STREAM. Gibt an, dass ein Eingabe-/Ausgabeparameter gestreamt werden soll. **SQLGetData** kann Parameterwerte in Teilen lesen. *BufferLength* wird ignoriert, da die Pufferlänge beim Aufruf von **SQLGetData**bestimmt wird. Der Wert *StrLen_or_IndPtr* des StrLen_or_IndPtr-Puffers muss SQL_NULL_DATA, SQL_DEFAULT_PARAM, SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros enthalten. Ein Parameter muss als DAE-Parameter (Data-at-Execution) an der Eingabe gebunden werden, wenn er beim Ausgang gestreamt wird. *ParameterValuePtr* kann jeder Nicht-NULL-Zeigerwert sein, der von **SQLParamData** als benutzerdefiniertes Token zurückgegeben wird, dessen Wert mit *ParameterValuePtr* für Eingabe und Ausgabe übergeben wurde. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_PARAM_OUTPUT_STREAM. Wie SQL_PARAM_INPUT_OUTPUT_STREAM für einen Ausgabeparameter. **StrLen_or_IndPtr* wird bei der Eingabe ignoriert.  
  
 In der folgenden Tabelle sind verschiedene Kombinationen von *InputOutputType* und **StrLen_or_IndPtr*aufgeführt:  
  
|*InputOutputType*|**StrLen_or_IndPtr*|Ergebnis|Anmerkung zu ParameterValuePtr|  
|-----------------------|----------------------------|-------------|---------------------------------|  
|SQL_PARAM_INPUT|*SQL_LEN_DATA_AT_EXEC(len)* oder SQL_DATA_AT_EXEC|Eingabe in Teilen|*ParameterValuePtr* kann ein beliebiger Zeigerwert sein, der von **SQLParamData** als benutzerdefiniertes Token zurückgegeben wird, dessen Wert mit *ParameterValuePtr*übergeben wurde.|  
|SQL_PARAM_INPUT|Nicht SQL_LEN_DATA_AT_EXEC(*len*) oder SQL_DATA_AT_EXEC|Eingabegebundener Puffer|*ParameterValuePtr* ist die Adresse des Eingabepuffers.|  
|SQL_PARAM_OUTPUT|Ignoriert bei der Eingabe.|Ausgabegebundener Puffer|*ParameterValuePtr* ist die Adresse des Ausgabepuffers.|  
|SQL_PARAM_OUTPUT_STREAM|Ignoriert bei der Eingabe.|Gestreamte Ausgabe|*ParameterValuePtr* kann ein beliebiger Zeigerwert sein, der von **SQLParamData** als benutzerdefiniertes Token zurückgegeben wird, dessen Wert mit *ParameterValuePtr*übergeben wurde.|  
|SQL_PARAM_INPUT_OUTPUT|*SQL_LEN_DATA_AT_EXEC(len)* oder SQL_DATA_AT_EXEC|Eingabe in Teile und ausgabegebundener Puffer|*ParameterValuePtr* ist die Adresse des Ausgabepuffers, der auch von **SQLParamData** als benutzerdefiniertes Token zurückgegeben wird, dessen Wert mit *ParameterValuePtr*übergeben wurde.|  
|SQL_PARAM_INPUT_OUTPUT|Nicht SQL_LEN_DATA_AT_EXEC(*len*) oder SQL_DATA_AT_EXEC|Eingabegebundener Puffer und ausgabegebundener Puffer|*ParameterValuePtr* ist die Adresse des freigegebenen Eingabe-/Ausgabepuffers.|
|SQL_PARAM_INPUT_OUTPUT_STREAM|*SQL_LEN_DATA_AT_EXEC(len)* oder SQL_DATA_AT_EXEC|Eingabe in Teilen und gestreamter Ausgang|*ParameterValuePtr* kann ein beliebiger Null-Zeigerwert sein, der von **SQLParamData** als benutzerdefiniertes Token zurückgegeben wird, dessen Wert sowohl für die Eingabe als auch für die Ausgabe mit *ParameterValuePtr* übergeben wurde.|  
  
> [!NOTE]  
>  Der Treiber muss entscheiden, welche SQL-Typen zulässig sind, wenn eine Anwendung einen Ausgabe- oder Input-Output-Parameter als gestreamt bindet. Der Treiber-Manager generiert keinen Fehler für einen ungültigen SQL-Typ.  
  
## <a name="valuetype-argument"></a>ValueType-Argument

 Das *ValueType-Argument* gibt den C-Datentyp des Parameters an. Dieses Argument legt die Felder SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE der APD fest. Dies muss einer der Werte im Abschnitt [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen sein.  
  
 Wenn das *ValueType-Argument* einer der Intervalldatentypen ist, wird das SQL_DESC_TYPE Feld des *ParameterNumber-Datensatzes* der APD auf SQL_INTERVAL festgelegt, das SQL_DESC_CONCISE_TYPE Feld der APD auf den Datentyp des kurzen Intervalls und das SQL_DESC_DATETIME_INTERVAL_CODE Feld des *ParameterNumber-Datensatzes* auf einen Untercode für den spezifischen Intervalldatentyp festgelegt. (Siehe [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).) Für die Daten werden die Standardmäßigsgenauigkeit (2) und die Standardintervallsekundengenauigkeit (6) verwendet, die in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION bzw. SQL_DESC_PRECISION der APD festgelegt sind. Wenn eine der Standardgenauigkeiten nicht geeignet ist, sollte die Anwendung das Deskriptorfeld explizit durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**festlegen.  
  
 Wenn das *ValueType-Argument* einer der datetime-Datentypen ist, wird das SQL_DESC_TYPE Feld des *ParameterNumber-Datensatzes* der APD auf SQL_DATETIME festgelegt, das SQL_DESC_CONCISE_TYPE Feld des *ParameterNumber-Datensatzes* der APD auf den Datentyp "Datumszeit-C" und das SQL_DESC_DATETIME_INTERVAL_CODE-Feld des *ParameterNumber-Datensatzes* auf einen Untercode für den spezifischen Datetime-Datentyp festgelegt. (Siehe [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Wenn das *ValueType-Argument* ein SQL_C_NUMERIC Datentyp ist, werden die Standardgenauigkeit (die treiberdefiniert ist) und der Standardmaßstab (0), wie in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE der APD festgelegt, für die Daten verwendet. Wenn die Standardgenauigkeit oder der Standardmaßstab nicht geeignet ist, sollte die Anwendung das Deskriptorfeld explizit durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**festlegen.  
  
 SQL_C_DEFAULT gibt an, dass der Parameterwert vom Standarddatentyp C für den mit *ParameterType*angegebenen SQL-Datentyp übertragen wird.  
  
 Sie können auch einen erweiterten C-Datentyp angeben. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 Weitere Informationen finden Sie unter [Standard-C-Datentypen](../../../odbc/reference/appendixes/default-c-data-types.md), [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)und Konvertieren von Daten aus [SQL-In-C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in Anhang D: Datentypen.  
  
## <a name="parametertype-argument"></a>ParameterType-Argument

 Dies muss einer der Werte sein, die im Abschnitt [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen aufgeführt sind, oder es muss ein treiberspezifischer Wert sein. Dieses Argument legt die Felder SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE der IPD fest.  
  
 Wenn das *ParameterType-Argument* einer der Datumszeitbezeichner ist, wird das SQL_DESC_TYPE Feld der IPD auf SQL_DATETIME festgelegt, das SQL_DESC_CONCISE_TYPE Feld der IPD auf den sql-Datentyp "Kurze Datumszeit" und das Feld SQL_DESC_DATETIME_INTERVAL_CODE auf den entsprechenden Datumszeit-Untercodewert festgelegt.  
  
 Wenn *ParameterType* einer der Intervallbezeichner ist, wird das SQL_DESC_TYPE Feld der IPD auf SQL_INTERVAL, das SQL_DESC_CONCISE_TYPE Feld der IPD auf den präzisen SQL-Intervalldatentyp und das SQL_DESC_DATETIME_INTERVAL_CODE Feld der IPD auf den entsprechenden Intervalluntercode festgelegt. Das SQL_DESC_DATETIME_INTERVAL_PRECISION Feld der IPD wird auf die Intervallführungsgenauigkeit und das Feld SQL_DESC_PRECISION auf die Intervallsekundengenauigkeit festgelegt, falls zutreffend. Wenn der Standardwert von SQL_DESC_DATETIME_INTERVAL_PRECISION oder SQL_DESC_PRECISION nicht geeignet ist, sollte die Anwendung ihn explizit festlegen, indem sie **SQLSetDescField**aufruft. Weitere Informationen zu diesen Feldern finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Wenn das *ValueType-Argument* ein SQL_NUMERIC Datentyp ist, werden die Standardgenauigkeit (die treiberdefiniert ist) und der Standardmaßstab (0), wie in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE der IPD festgelegt, für die Daten verwendet. Wenn die Standardgenauigkeit oder der Standardmaßstab nicht geeignet ist, sollte die Anwendung das Deskriptorfeld explizit durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**festlegen.  
  
 Informationen zur Konvertierung von Daten finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) und Konvertieren von Daten aus [SQL-In-C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in Anhang D: Datentypen.  
  
## <a name="columnsize-argument"></a>ColumnSize-Argument

 Das *ColumnSize-Argument* gibt die Größe der Spalte oder des Ausdrucks an, die der Parametermarkierung, der Länge dieser Daten oder beidem entspricht. Dieses Argument legt je nach SQL-Datentyp (Argument *ParameterType)* unterschiedliche Felder der IPD fest. Für diese Zuordnung gelten die folgenden Regeln:  
  
-   Wenn *ParameterType* SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY oder einer der kurzen SQL-Datumszeit- oder Intervalldatentypen ist, wird das SQL_DESC_LENGTH Feld der IPD auf den Wert von *ColumnSize*festgelegt. (Weitere Informationen finden Sie im Abschnitt [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.)  
  
-   Wenn *ParameterType* SQL_DECIMAL, SQL_NUMERIC, SQL_FLOAT, SQL_REAL oder SQL_DOUBLE ist, wird das SQL_DESC_PRECISION Feld der IPD auf den Wert von *ColumnSize*festgelegt.  
  
-   Bei anderen Datentypen wird das *ColumnSize-Argument* ignoriert.  
  
 Weitere Informationen finden Sie unter "Übergeben von Parameterwerten" und SQL_DATA_AT_EXEC unter *"StrLen_or_IndPtr* Argument".  
  
## <a name="decimaldigits-argument"></a>DecimalDigits-Argument

 Wenn *ParameterType* SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP, SQL_INTERVAL_SECOND, SQL_INTERVAL_DAY_TO_SECOND, SQL_INTERVAL_HOUR_TO_SECOND oder SQL_INTERVAL_MINUTE_TO_SECOND ist, wird das SQL_DESC_PRECISION Feld der IPD auf *DecimalDigits*festgelegt. Wenn *ParameterType* SQL_NUMERIC oder SQL_DECIMAL ist, wird das SQL_DESC_SCALE Feld der IPD auf *DecimalDigits*festgelegt. Bei allen anderen Datentypen wird das *Argument DecimalDigits* ignoriert.  
  
## <a name="parametervalueptr-argument"></a>ParameterValuePtr-Argument

 Das *ParameterValuePtr-Argument* verweist auf einen Puffer, der beim Aufruf von **SQLExecute** oder **SQLExecDirect** die tatsächlichen Daten für den Parameter enthält. Die Daten müssen in der vom *ValueType-Argument* angegebenen Form angegeben sein. Dieses Argument legt das SQL_DESC_DATA_PTR Feld der APD fest. Eine Anwendung kann das *ParameterValuePtr-Argument* auf einen * \** Nullzeiger festlegen, solange StrLen_or_IndPtr SQL_NULL_DATA oder SQL_DATA_AT_EXEC ist. (Dies gilt nur für Eingabe- oder Eingabe-/Ausgabeparameter.)  
  
 Wenn \* *StrLen_or_IndPtr* das Ergebnis des Makros*SQL_LEN_DATA_AT_EXEC(Länge*) oder SQL_DATA_AT_EXEC ist, ist *ParameterValuePtr* ein anwendungsdefinierter Zeigerwert, der dem Parameter zugeordnet ist. Sie wird über **SQLParamData**an die Anwendung zurückgegeben. *ParameterValuePtr* kann z. B. ein Token ungleich Null sein, z. B. eine Parameternummer, ein Zeiger auf Daten oder ein Zeiger auf eine Struktur, die von der Anwendung zum Binden von Eingabeparametern verwendet wurde. Beachten Sie jedoch, dass *ParameterValuePtr* ein Zeiger auf einen Puffer sein muss, in dem der Ausgabewert gespeichert wird, wenn es sich um einen Input/Output-Parameter handelt. Wenn der Wert im SQL_ATTR_PARAMSET_SIZE-Anweisungsattribut größer als 1 ist, kann die Anwendung den Wert verwenden, auf den das SQL_ATTR_PARAMS_PROCESSED_PTR Anweisungsattribut zusammen mit dem *ParameterValuePtr-Argument* zeigt. *ParameterValuePtr* kann z. B. auf ein Array von Werten verweisen, und die Anwendung kann den Wert verwenden, auf den von SQL_ATTR_PARAMS_PROCESSED_PTR verwiesen wird, um den richtigen Wert aus dem Array abzurufen. Weitere Informationen finden Sie unter "Übergeben von Parameterwerten" weiter unten in diesem Abschnitt.  
  
 Wenn das *InputOutputType-Argument* SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT ist, zeigt *ParameterValuePtr* auf einen Puffer, in dem der Treiber den Ausgabewert zurückgibt. Wenn die Prozedur einen oder mehrere \*Resultsets zurückgibt, wird der *ParameterValuePtr-Puffer* erst dann festgelegt, wenn alle Resultsets/Zeilenanzahlen verarbeitet wurden. Wenn der Puffer erst nach Abschluss der Verarbeitung festgelegt ist, sind die Ausgabeparameter und Rückgabewerte nicht verfügbar, bis **SQLMoreResults** SQL_NO_DATA zurückgibt. Wenn Sie **SQLCloseCursor** oder **SQLFreeStmt** mit einer Option der SQL_CLOSE aufrufen, werden diese Werte verworfen.  
  
 Wenn der Wert im SQL_ATTR_PARAMSET_SIZE-Anweisungsattribut größer als 1 ist, zeigt *ParameterValuePtr* auf ein Array. Eine einzelne SQL-Anweisung verarbeitet das gesamte Array von Eingabewerten für einen Eingabe- oder Eingabe-/Ausgabeparameter und gibt ein Array von Ausgabewerten für einen Input-/Output- oder Ausgabeparameter zurück.  
  
## <a name="bufferlength-argument"></a>BufferLength-Argument

 Bei Zeichen- und Binär-C-Daten gibt das \* *Argument BufferLength* die Länge des *ParameterValuePtr-Puffers* (wenn \*es sich um ein einzelnes Element handelt) oder die Länge eines Elements im *ParameterValuePtr-Array* an (wenn der Wert im SQL_ATTR_PARAMSET_SIZE-Anweisungsattribut größer als 1 ist). Mit diesem Argument wird das SQL_DESC_OCTET_LENGTH Datensatzfeld der APD festgelegt. Wenn die Anwendung mehrere Werte angibt, wird *BufferLength* verwendet, um die Position der Werte im Array **ParameterValuePtr* sowohl bei der Eingabe als auch bei der Ausgabe zu bestimmen. Für Eingabe-/Ausgabe- und Ausgabeparameter wird ermittelt, ob Zeichen- und binäre C-Daten bei der Ausgabe abgeschnitten werden sollen:  
  
-   Wenn bei Zeichen C-Daten die Anzahl der zurückzugebenden Bytes größer oder \*gleich *BufferLength*ist, werden die Daten in *ParameterValuePtr* abzüglich der Länge eines Nullbeendigungszeichens auf *BufferLength* abgeschnitten und vom Treiber null beendet.  
  
-   Wenn bei binären C-Daten die Anzahl der zurückzugebenden Bytes \*größer als *BufferLength*ist, werden die Daten in *ParameterValuePtr* auf *BufferLength-Bytes* abgeschnitten.  
  
 Bei allen anderen Typen von C-Daten wird das *BufferLength-Argument* ignoriert. Die Länge \*des *ParameterValuePtr-Puffers* (wenn es sich um ein \*einzelnes Element handelt) oder die Länge eines Elements im *ParameterValuePtr-Array* (wenn die Anwendung **SQLSetStmtAttr** mit einem *Attributargument* von SQL_ATTR_PARAMSET_SIZE zur Angabe mehrerer Werte für jeden Parameter aufruft) wird als die Länge des C-Datentyps angenommen.  
  
 Bei gestreamten Ausgabe- oder gestreamten Eingabe-/Ausgabeparametern wird das *Argument BufferLength* ignoriert, da die Pufferlänge in **SQLGetData**angegeben ist.  
  
> [!NOTE]  
>  Wenn eine ODBC 1.0-Anwendung **SQLSetParam** in einem ODBC 3 aufruft. *x-Treiber* konvertiert der Treiber-Manager dies in einen Aufruf von **SQLBindParameter,** bei dem das *BufferLength-Argument* immer SQL_SETPARAM_VALUE_MAX ist. Da der Treiber-Manager einen Fehler zurückgibt, wenn ein ODBC 3. *x-Anwendung* legt *BufferLength* auf SQL_SETPARAM_VALUE_MAX, eine ODBC 3. *der x-Treiber* kann dies verwenden, um zu bestimmen, wann er von einer ODBC 1.0-Anwendung aufgerufen wird.  
  
> [!NOTE]  
>  In **SQLSetParam**ist die Art und Weise, in der eine Anwendung die Länge des **ParameterValuePtr-Puffers* angibt, sodass der Treiber Zeichen- oder Binärdaten zurückgeben kann, und die Art und Weise, wie eine Anwendung ein Array von Zeichen- oder Binärparameterwerten an den Treiber sendet, treiberdefiniert.  
  
## <a name="strlen_or_indptr-argument"></a>StrLen_or_IndPtr Argument

 Das *argument StrLen_or_IndPtr* verweist auf einen Puffer, der beim Aufruf von **SQLExecute** oder **SQLExecDirect** einen der folgenden Punkte enthält. (Dieses Argument legt die SQL_DESC_OCTET_LENGTH_PTR- und SQL_DESC_INDICATOR_PTR Datensatzfelder der Anwendungsparameterzeiger fest.)  
  
-   Die Länge des in **ParameterValuePtr*gespeicherten Parameterwerts. Dies wird mit Ausnahme von Zeichen- oder Binär-C-Daten ignoriert.  
  
-   SQL_NTS. Der Parameterwert ist eine null-terminierte Zeichenfolge.  
  
-   SQL_NULL_DATA. Der Parameterwert ist NULL.  
  
-   SQL_DEFAULT_PARAM. Eine Prozedur besteht darin, den Standardwert eines Parameters anstelle eines aus der Anwendung abgerufenen Werts zu verwenden. Dieser Wert ist nur in einer Prozedur gültig, die in der kanonischen ODBC-Syntax aufgerufen wird, und dann nur, wenn das *Argument InputOutputType* SQL_PARAM_INPUT, SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_INPUT_OUTPUT_STREAM ist. Wenn \* *StrLen_or_IndPtr* SQL_DEFAULT_PARAM ist, werden die Argumente *ValueType*, *ParameterType*, *ColumnSize*, *DecimalDigits*, *BufferLength*und *ParameterValuePtr* für Eingabeparameter ignoriert und nur verwendet, um den Ausgabeparameterwert für Eingabe-/Ausgabeparameter zu definieren.  
  
-   Das Ergebnis des*SQL_LEN_DATA_AT_EXEC(Länge*) Makros. Die Daten für den Parameter werden mit **SQLPutData**gesendet. Wenn das *ParameterType-Argument* SQL_LONGVARBINARY, SQL_LONGVARCHAR oder ein langer, datenquellenspezifischer Datentyp ist und der Treiber "Y" für den SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo**zurückgibt, ist *Länge* die Anzahl der Bytes an Daten, die für den Parameter gesendet werden sollen. Andernfalls muss *die Länge* ein nicht negativer Wert sein und wird ignoriert. Weitere Informationen finden Sie unter "Übergeben von Parameterwerten" weiter unten in diesem Abschnitt.  
  
     Um beispielsweise anzugeben, dass 10.000 Byte Daten mit **SQLPutData** in einem oder mehreren Aufrufen gesendet werden, legt eine Anwendung für einen SQL_LONGVARCHAR Parameter * StrLen_or_IndPtr auf SQL_LEN_DATA_AT_EXEC(10000)*fest.*  
  
-   SQL_DATA_AT_EXEC. Die Daten für den Parameter werden mit **SQLPutData**gesendet. Dieser Wert wird von ODBC 1.0-Anwendungen verwendet, wenn sie ODBC 3 aufrufen. *x-Treiber.* Weitere Informationen finden Sie unter "Übergeben von Parameterwerten" weiter unten in diesem Abschnitt.  
  
 Wenn *StrLen_or_IndPtr* ein Nullzeiger ist, geht der Treiber davon aus, dass alle Eingabeparameterwerte nicht NULL sind und dass Zeichen- und Binärdaten null beendet sind. Wenn *InputOutputType* SQL_PARAM_OUTPUT oder SQL_PARAM_OUTPUT_STREAM und *ParameterValuePtr* und *StrLen_or_IndPtr* beide NULL-Zeiger sind, verwirft der Treiber den Ausgabewert.  
  
> [!NOTE]  
>  Anwendungsentwicklern wird dringend davon abgeraten, einen Nullzeiger für *StrLen_or_IndPtr* anzugeben, wenn der Datentyp des Parameters SQL_C_BINARY ist. Um sicherzustellen, dass ein Treiber SQL_C_BINARY Daten nicht unerwartet abnimmt, sollten *StrLen_or_IndPtr* einen Zeiger auf einen gültigen Längenwert enthalten.  
  
 Wenn das *InputOutputType-Argument* SQL_PARAM_INPUT_OUTPUT, SQL_PARAM_OUTPUT, SQL_PARAM_INPUT_OUTPUT_STREAM oder SQL_PARAM_OUTPUT_STREAM ist, *StrLen_or_IndPtr* auf einen Puffer verweist, \*in dem der Treiber SQL_NULL_DATA zurückgibt, kann die Anzahl der Bytes, die in *ParameterValuePtr* zurückgegeben werden können (mit Ausnahme des Nullbeendigungsbytes von Zeichendaten), oder SQL_NO_TOTAL (wenn die Anzahl der zurückzugebenden Bytes nicht bestimmt werden kann). Wenn die Prozedur einen oder mehrere Resultsets zurückgibt, wird der **-StrLen_or_IndPtr-Puffer* erst dann festgelegt, wenn alle Ergebnisse abgerufen wurden.  
  
 Wenn der Wert im SQL_ATTR_PARAMSET_SIZE-Anweisungsattribut größer als 1 ist, *verweist StrLen_or_IndPtr* auf ein Array von SQLLEN-Werten. Dabei kann es sich um einen der oben in diesem Abschnitt aufgeführten Werte handelt, die mit einer einzelnen SQL-Anweisung verarbeitet werden.  
  
## <a name="passing-parameter-values"></a>Übergeben von Parameterwerten

 Eine Anwendung kann den Wert für \*einen Parameter entweder im *ParameterValuePtr-Puffer* oder mit einem oder mehreren Aufrufen von **SQLPutData**übergeben. Parameter, deren Daten mit **SQLPutData** übergeben werden, werden als *Data-at-Execution-Parameter* bezeichnet. Diese werden in der Regel zum Senden von Daten für SQL_LONGVARBINARY und SQL_LONGVARCHAR Parameter verwendet und können mit anderen Parametern gemischt werden.  
  
 Um Parameterwerte zu übergeben, führt eine Anwendung die folgende Folge von Schritten aus:  
  
1.  Ruft **SQLBindParameter** für jeden Parameter auf, um Puffer für den Parameterwert *(ParameterValuePtr-Argument)* und Length/Indicator *(StrLen_or_IndPtr* Argument) zu binden. *ParameterValuePtr* ist für Parameter-at-Execution-Parameter ein anwendungsdefinierter Zeigerwert, z. B. eine Parameternummer oder ein Zeiger auf Daten. Der Wert wird später zurückgegeben und kann verwendet werden, um den Parameter zu identifizieren.  
  
2.  Platziert Werte für Eingabe- und \*Eingabe-/Ausgabeparameter in den *ParameterValuePtr-* und * StrLen_or_IndPtr-Puffern:*StrLen_or_IndPtr*  
  
    -   Bei normalen Parametern platziert die Anwendung \*den Parameterwert im *ParameterValuePtr-Puffer* und die Länge dieses Werts im **StrLen_or_IndPtr-Puffer.* Weitere Informationen finden Sie unter [Festlegen von Parameterwerten](../../../odbc/reference/develop-app/setting-parameter-values.md).  
  
    -   Bei Parametern für data-at-execution legt die Anwendung das Ergebnis des*SQL_LEN_DATA_AT_EXEC(Länge*) -Makros (beim Aufrufen eines ODBC 2.0-Treibers) in den **-StrLen_or_IndPtr-Puffer.*  
  
3.  Ruft **SQLExecute** oder **SQLExecDirect** auf, um die SQL-Anweisung auszuführen.  
  
    -   Wenn keine Daten-bei-Ausführungsparameter vorhanden sind, ist der Vorgang abgeschlossen.  
  
    -   Wenn Daten-at-Execution-Parameter vorhanden sind, gibt die Funktion SQL_NEED_DATA zurück.  
  
4.  Ruft **SQLParamData** auf, um den anwendungsdefinierten Wert abzurufen, der im *ParameterValuePtr-Argument* von **SQLBindParameter** für den ersten zu verarbeitenden Data-at-Execution-Parameter angegeben ist. **SQLParamData** gibt SQL_NEED_DATA zurück.  
  
    > [!NOTE]  
    >  Obwohl Daten-at-Execution-Parameter Daten-at-Execution-Spalten ähneln, ist der von **SQLParamData** zurückgegebene Wert für jeden wert unterschiedlich. Data-at-Execution-Parameter sind Parameter in einer SQL-Anweisung, für die Daten mit **SQLPutData** gesendet werden, wenn die Anweisung mit **SQLExecDirect** oder **SQLExecute**ausgeführt wird. Sie sind mit **SQLBindParameter**gebunden. Der von **SQLParamData** zurückgegebene Wert ist ein Zeigerwert, der im *ParameterValuePtr-Argument* an **SQLBindParameter** übergeben wird. Data-at-Execution-Spalten sind Spalten in einem Rowset, für die Daten mit **SQLPutData** gesendet werden, wenn eine Zeile aktualisiert oder mit **SQLBulkOperations** oder mit **SQLSetPos**aktualisiert wird. Sie sind mit **SQLBindCol**gebunden. Der von **SQLParamData** zurückgegebene Wert ist die Adresse der Zeile im **TargetValuePtr-Puffer* (festgelegt durch einen Aufruf von **SQLBindCol**), die verarbeitet wird.  
  
5.  Ruft **SQLPutData** ein oder mehrere Male auf, um Daten für den Parameter zu senden. Mehr als ein Aufruf ist erforderlich, wenn \*der Datenwert größer als der in **SQLPutData**angegebene *ParameterValuePtr-Puffer* ist. Mehrere Aufrufe von **SQLPutData** für denselben Parameter sind nur zulässig, wenn Zeichen-C-Daten an eine Spalte mit einem zeichen-, binären oder datenquellenspezifischen Datentyp gesendet werden oder wenn binäre C-Daten an eine Spalte mit einem Zeichen-, Binär- oder Datenquellentyp gesendet werden.  
  
6.  Ruft **SQLParamData** erneut auf, um zu signalisieren, dass alle Daten für den Parameter gesendet wurden.  
  
    -   Wenn mehr Data-at-Execution-Parameter vorhanden sind, gibt **SQLParamData** SQL_NEED_DATA und den anwendungsdefinierten Wert für den nächsten zu verarbeitenden Data-at-Execution-Parameter zurück. Die Anwendung wiederholt die Schritte 4 und 5.  
  
    -   Wenn keine weiteren Daten-at-Execution-Parameter vorhanden sind, ist der Vorgang abgeschlossen. Wenn die Anweisung erfolgreich ausgeführt wurde, gibt **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück. Wenn die Ausführung fehlgeschlagen ist, wird SQL_ERROR zurückgegeben. An diesem Punkt kann **SQLParamData** jede SQLSTATE zurückgeben, die von der Funktion zurückgegeben werden kann, die zum Ausführen der Anweisung verwendet wird (**SQLExecDirect** oder **SQLExecute**).  
  
         Ausgabewerte für alle Eingabe-/Ausgabe- oder \*Ausgabeparameter sind im *ParameterValuePtr* und **StrLen_or_IndPtr* Puffer verfügbar, nachdem die Anwendung alle von der Anweisung generierten Resultsets abgerufen hat.  
  
 Wenn Sie **SQLExecute** oder **SQLExecDirect** aufrufen, wird die Anweisung in einen SQL_NEED_DATA Zustand versetzt. Zu diesem Zeitpunkt kann die Anwendung nur **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**oder **SQLPutData** mit der Anweisung oder dem der Anweisung zugeordneten *Verbindungshandle* aufrufen. Wenn eine andere Funktion mit der Anweisung oder der verbindung, die der Anweisung zugeordnet ist, aufruft, gibt die Funktion SQLSTATE HY010 (Funktionssequenzfehler) zurück. Die Anweisung verlässt den SQL_NEED_DATA-Status, wenn **SQLParamData** oder **SQLPutData** einen Fehler zurückgibt, **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt oder die Anweisung abgebrochen wird.  
  
 Wenn die Anwendung **SQLCancel** aufruft, während der Treiber weiterhin Daten für Daten-at-Execution-Parameter benötigt, bricht der Treiber die Anweisungsausführung ab. Die Anwendung kann dann **SQLExecute** oder **SQLExecDirect** erneut aufrufen.  
  
## <a name="retrieving-streamed-output-parameters"></a>Abrufen von streamierten Ausgabeparametern

 Wenn eine Anwendung *InputOutputType* auf SQL_PARAM_INPUT_OUTPUT_STREAM oder SQL_PARAM_OUTPUT_STREAM festlegt, muss der Ausgabeparameterwert von einem oder mehreren Aufrufen von **SQLGetData**abgerufen werden. Wenn der Treiber über einen gestreamten Ausgabeparameterwert verfügt, der an die Anwendung zurückgegeben werden soll, gibt er SQL_PARAM_DATA_AVAILABLE als Reaktion auf einen Aufruf der folgenden Funktionen zurück: **SQLMoreResults**, **SQLExecute**und **SQLExecDirect**. Eine Anwendung ruft **SQLParamData** auf, um zu bestimmen, welcher Parameterwert verfügbar ist.  
  
 Weitere Informationen zu SQL_PARAM_DATA_AVAILABLE und gestreamten Ausgabeparametern finden Sie unter [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-arrays-of-parameters"></a>Verwenden von Parameterarrays

 Wenn eine Anwendung eine Anweisung mit Parametermarkierungen vorbereitet und ein Array von Parametern übergibt, gibt es zwei verschiedene Möglichkeiten, dies auszuführen. Eine Möglichkeit besteht darin, dass sich der Treiber auf die Arrayverarbeitungsfunktionen des Back-End verlässt, wobei die gesamte Anweisung mit dem Array von Parametern als eine atomare Einheit behandelt wird. Oracle ist ein Beispiel für eine Datenquelle, die Arrayverarbeitungsfunktionen unterstützt. Eine weitere Möglichkeit, diese Funktion zu implementieren, besteht darin, dass der Treiber einen Batch von SQL-Anweisungen, eine SQL-Anweisung für jeden Parametersatz im Parameterarray generiert und den Batch ausführt. Arrays von Parametern können nicht mit einer **UPDATE WHERE CURRENT OF-Anweisung** verwendet werden.  
  
 Wenn ein Array von Parametern verarbeitet wird, können einzelne Resultsets/Zeilenanzahlen (eine für jeden Parametersatz) verfügbar sein oder Ergebnismengen/Zeilenanzahlen können in einem zusammengerollt werden. Die Option SQL_PARAM_ARRAY_ROW_COUNTS in **SQLGetInfo** gibt an, ob Zeilenanzahlen für jeden Parametersatz (SQL_PARC_BATCH) verfügbar sind oder nur eine Zeilenanzahl verfügbar ist (SQL_PARC_NO_BATCH).  
  
 Die Option SQL_PARAM_ARRAY_SELECTS in **SQLGetInfo** gibt an, ob für jeden Parametersatz (SQL_PAS_BATCH) ein Resultset verfügbar ist oder nur ein Resultset verfügbar ist (SQL_PAS_NO_BATCH). Wenn der Treiber nicht zulässt, dass eine Resultset-Generierende Anweisung mit einem Array von Parametern ausgeführt wird, gibt SQL_PARAM_ARRAY_SELECTS SQL_PAS_NO_SELECT zurück.  
  
 Weitere Informationen finden Sie unter [SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 Um Arrays von Parametern zu unterstützen, wird das Attribut SQL_ATTR_PARAMSET_SIZE Anweisung festgelegt, um die Anzahl der Werte für jeden Parameter anzugeben. Wenn das Feld größer als 1 ist, müssen die Felder SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR der APD auf Arrays verweisen. Die Kardinalität jedes Arrays entspricht dem Wert von SQL_ATTR_PARAMSET_SIZE.  
  
 Das SQL_DESC_ROWS_PROCESSED_PTR Feld der APD zeigt auf einen Puffer, der die Anzahl der verarbeiteten Parametersätze enthält, einschließlich Fehlersätzen. Wenn jeder Parametersatz verarbeitet wird, speichert der Treiber einen neuen Wert im Puffer. Keine Zahl wird zurückgegeben, wenn es sich um einen Nullzeiger handelt. Wenn Arrays von Parametern verwendet werden, wird der Wert, auf den das SQL_DESC_ROWS_PROCESSED_PTR Feld der APD zeigt, auch dann aufgefüllt, wenn SQL_ERROR von der Einstellungsfunktion zurückgegeben wird. Wenn SQL_NEED_DATA zurückgegeben wird, wird der Wert, auf den das Feld SQL_DESC_ROWS_PROCESSED_PTR der APD zeigt, auf den Satz von Parametern festgelegt, die verarbeitet werden.  
  
 Was passiert, wenn ein Array von Parametern gebunden ist und eine **UPDATE WHERE CURRENT OF-Anweisung** ausgeführt wird, ist treiberdefiniert.  
  
## <a name="column-wise-parameter-binding"></a>Spalten-Wise-Parameterbindung

 In der spaltenweisen Bindung bindet die Anwendung separate Parameter- und Längen-/Indikatorarrays an jeden Parameter.  
  
 Um die spaltenweise Bindung zu verwenden, legt die Anwendung zunächst das SQL_ATTR_PARAM_BIND_TYPE-Anweisungsattribut auf SQL_PARAM_BIND_BY_COLUMN. (Dies ist die Standardeinstellung.) Für jede zu bindende Spalte führt die Anwendung die folgenden Schritte aus:  
  
1.  Ordnet ein Parameterpufferarray zu.  
  
2.  Ordnet ein Array von Längen-/Indikatorpuffern zu.  
  
    > [!NOTE]  
    >  Wenn die Anwendung direkt in Deskriptoren schreibt, wenn spaltenweise Bindungen verwendet werden, können separate Arrays für Längen- und Indikatordaten verwendet werden.  
  
3.  Ruft **SQLBindParameter** mit den folgenden Argumenten auf:  
  
    -   *ValueType* ist der C-Typ eines einzelnen Elements im Parameterpufferarray.  
  
    -   *ParameterType* ist der SQL-Typ des Parameters.  
  
    -   *ParameterValuePtr* ist die Adresse des Parameterpufferarrays.  
  
    -   *BufferLength* ist die Größe eines einzelnen Elements im Parameterpufferarray. Das *Argument BufferLength* wird ignoriert, wenn es sich bei den Daten um Daten fester Länge handelt.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des Längen-/Indikator-Arrays.  
  
 Weitere Informationen zur Verwendung dieser Informationen finden Sie unter "ParameterValuePtr Argument" in "Kommentare" weiter unten in diesem Abschnitt. Weitere Informationen zur spaltenweisen Bindung von Parametern finden Sie unter [Binding Arrays of Parameters](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md).  
  
## <a name="row-wise-parameter-binding"></a>Row-Wise-Parameterbindung

 In der zeilenweisen Bindung definiert die Anwendung eine Struktur, die Parameter- und Längen-/Indikatorpuffer für jeden zu bindenden Parameter enthält.  
  
 Um die zeilenweise Bindung zu verwenden, führt die Anwendung die folgenden Schritte aus:  
  
1.  Definiert eine Struktur für einen einzelnen Satz von Parametern (einschließlich Parameter- und Längen-/Indikatorpuffer) und weist ein Array dieser Strukturen zu.  
  
    > [!NOTE]  
    >  Wenn die Anwendung direkt in Deskriptoren schreibt, wenn zeilenweise Bindung verwendet wird, können separate Felder für Längen- und Indikatordaten verwendet werden.  
  
2.  Legt das SQL_ATTR_PARAM_BIND_TYPE-Anweisungsattribut auf die Größe der Struktur fest, die einen einzelnen Satz von Parametern enthält, oder auf die Größe einer Instanz eines Puffers, an die die Parameter gebunden werden. Die Länge muss Platz für alle gebundenen Parameter und alle Auffüllungen der Struktur oder des Puffers enthalten, um sicherzustellen, dass das Ergebnis auf den Anfang desselben Parameters in der nächsten Zeile zeigen, wenn die Adresse eines gebundenen Parameters mit der angegebenen Länge erhöht wird. Wenn Sie den *Operator sizeof* in ANSI C verwenden, ist dieses Verhalten garantiert.  
  
3.  Ruft **SQLBindParameter** mit den folgenden Argumenten für jeden zu bindenden Parameter auf:  
  
    -   *ValueType* ist der Typ des Parameterpuffermembers, der an die Spalte gebunden werden soll.  
  
    -   *ParameterType* ist der SQL-Typ des Parameters.  
  
    -   *ParameterValuePtr* ist die Adresse des Parameterpufferelements im ersten Arrayelement.  
  
    -   *BufferLength* ist die Größe des Parameterpufferelements.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des zu bindenden Längen-/Indikatorelements.  
  
 Weitere Informationen zur Verwendung dieser Informationen finden Sie weiter unten in diesem Abschnitt unter *"ParameterValuePtr-Argument".* Weitere Informationen zur zeilenweisen Bindung von Parametern finden Sie in den [Bindungsarrays von Parametern](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md).  
  
## <a name="error-information"></a>Fehlerinformationen

 Wenn ein Treiber keine Parameterarrays als Batches implementiert (die Option SQL_PARAM_ARRAY_ROW_COUNTS entspricht SQL_PARC_NO_BATCH), werden Fehlersituationen so behandelt, als ob eine Anweisung ausgeführt würde. Wenn der Treiber Parameterarrays als Batches implementiert, kann eine Anwendung das SQL_DESC_ARRAY_STATUS_PTR Headerfeld der IPD verwenden, um zu bestimmen, welcher Parameter einer SQL-Anweisung oder welcher Parameter in einem Array von Parametern dazu geführt hat, dass **SQLExecDirect** oder **SQLExecute** einen Fehler zurückgeben. Dieses Feld enthält Statusinformationen für jede Zeile von Parameterwerten. Wenn das Feld angibt, dass ein Fehler aufgetreten ist, geben Felder in der Diagnosedatenstruktur die Zeile und Parameternummer des fehlgeschlagenen Parameters an. Die Anzahl der Elemente im Array wird durch das SQL_DESC_ARRAY_SIZE-Headerfeld in der APD definiert, das durch das Attribut SQL_ATTR_PARAMSET_SIZE-Anweisung festgelegt werden kann.  
  
> [!NOTE]  
>  Das SQL_DESC_ARRAY_STATUS_PTR Kopffeld in der APD wird verwendet, um Parameter zu ignorieren. Weitere Informationen zum Ignorieren von Parametern finden Sie im nächsten Abschnitt "Ignorieren eines Satzes von Parametern".  
  
 Wenn **SQLExecute** oder **SQLExecDirect** SQL_ERROR zurückgibt, enthalten die Elemente im Array, auf die das Feld SQL_DESC_ARRAY_STATUS_PTR in der IPD zeigt, SQL_PARAM_ERROR, SQL_PARAM_SUCCESS, SQL_PARAM_SUCCESS_WITH_INFO, SQL_PARAM_UNUSED oder SQL_PARAM_DIAG_UNAVAILABLE.  
  
 Für jedes Element in diesem Array enthält die Diagnosedatenstruktur einen oder mehrere Statusdatensätze. Das SQL_DIAG_ROW_NUMBER Feld der Struktur gibt die Zeilennummer der Parameterwerte an, die den Fehler verursacht haben. Wenn es möglich ist, den bestimmten Parameter in einer Reihe von Parametern zu bestimmen, die den Fehler verursacht haben, wird die Parameternummer in das Feld SQL_DIAG_COLUMN_NUMBER eingegeben.  
  
 SQL_PARAM_UNUSED wird eingegeben, wenn ein Parameter nicht verwendet wurde, da ein Fehler in einem früheren Parameter aufgetreten ist, der **SQLExecute** oder **SQLExecDirect** zum Abbrechen erzwungen hat. Wenn z. B. beim Ausführen des vierzigsten Satzes von Parametern, die den Abbruch von **SQLExecute** oder **SQLExecDirect** verursacht haben, ein Fehler aufgetreten ist und ein Fehler aufgetreten ist, wird SQL_PARAM_UNUSED im Statusarray für die Parameter 41 bis 50 eingegeben.  
  
 SQL_PARAM_DIAG_UNAVAILABLE wird eingegeben, wenn der Treiber Arrays von Parametern als monolithische Einheit behandelt, sodass diese individuelle Parameterebene der Fehlerinformationen nicht generiert wird.  
  
 Einige Fehler bei der Verarbeitung eines einzelnen Satzes von Parametern führen dazu, dass die Verarbeitung der nachfolgenden Parametersätze im Array beendet wird. Andere Fehler haben keinen Einfluss auf die Verarbeitung nachfolgender Parameter. Welche Fehler die Verarbeitung beenden, ist treiberdefiniert. Wenn die Verarbeitung nicht beendet wird, werden alle Parameter im Array verarbeitet, SQL_SUCCESS_WITH_INFO als Folge des Fehlers zurückgegeben wird, und der von SQL_ATTR_PARAMS_PROCESSED_PTR definierte Puffer wird auf die Gesamtzahl der verarbeiteten Parametersätze festgelegt (wie durch das Attribut SQL_ATTR_PARAMSET_SIZE-Anweisung definiert), einschließlich Fehlersätzen.  
  
> [!CAUTION]  
>  ODBC-Verhalten, wenn ein Fehler bei der Verarbeitung eines Arrays von Parametern auftritt, unterscheidet sich in ODBC 3. *x* als in ODBC 2. *x*. In ODBC 2. *x*, die Funktion zurückgegeben SQL_ERROR und Verarbeitung beendet. Der Puffer, auf den das *pirow-Argument* von **SQLParamOptions** zeigt, enthielt die Nummer der Fehlerzeile. In ODBC 3. *x*gibt die Funktion SQL_SUCCESS_WITH_INFO zurück, und die Verarbeitung kann entweder beendet oder fortgesetzt werden. Wenn dies weiterhin der Fall ist, wird der von SQL_ATTR_PARAMS_PROCESSED_PTR angegebene Puffer auf den Wert aller verarbeiteten Parameter festgelegt, einschließlich der Parameter, die zu einem Fehler geführt haben. Diese Verhaltensänderung kann zu Problemen bei vorhandenen Anwendungen führen.  
  
 Wenn **SQLExecute** oder **SQLExecDirect** zurückgibt, bevor die Verarbeitung aller Parametersätze in einem Parameterarray abgeschlossen wird, z. B. wenn SQL_ERROR oder SQL_NEED_DATA zurückgegeben wird, enthält das Statusarray Status für die Parameter, die bereits verarbeitet wurden. Die Position, auf die das Feld SQL_DESC_ROWS_PROCESSED_PTR in der IPD zeigt, enthält die Zeilennummer im Parameterarray, die den SQL_ERROR oder SQL_NEED_DATA Fehlercode verursacht hat. Wenn ein Array von Parametern an eine SELECT-Anweisung gesendet wird, ist die Verfügbarkeit von Status-Array-Werten treiberdefiniert. Sie können verfügbar sein, nachdem die Anweisung ausgeführt wurde oder als Ergebnismengen abgerufen werden.  
  
## <a name="ignoring-a-set-of-parameters"></a>Ignorieren eines Satzes von Parametern

 Das SQL_DESC_ARRAY_STATUS_PTR Feld der APD (wie durch das Attribut SQL_ATTR_PARAM_STATUS_PTR-Anweisung festgelegt), kann verwendet werden, um anzugeben, dass ein Satz gebundener Parameter in einer SQL-Anweisung ignoriert werden soll. Um den Treiber anzuweisen, einen oder mehrere Parametersätze während der Ausführung zu ignorieren, sollte eine Anwendung die folgenden Schritte ausführen:  
  
1.  Rufen Sie **SQLSetDescField** auf, um das SQL_DESC_ARRAY_STATUS_PTR Headerfeld der APD so festzulegen, dass es auf ein Array von SQLUSMALLINT-Werten zeigt, die Statusinformationen enthalten. Dieses Feld kann auch durch Aufrufen von **SQLSetStmtAttr** mit einem *Attribut* von SQL_ATTR_PARAM_OPERATION_PTR festgelegt werden, wodurch eine Anwendung das Feld festlegen kann, ohne ein Deskriptor-Handle zu erhalten.  
  
2.  Legen Sie jedes Element des Arrays, das durch das SQL_DESC_ARRAY_STATUS_PTR Feld der APD definiert wird, auf einen von zwei Werten fest:  
  
    -   SQL_PARAM_IGNORE, um anzugeben, dass die Zeile von der Anweisungsausführung ausgeschlossen ist.  
  
    -   SQL_PARAM_PROCEED, um anzugeben, dass die Zeile in die Anweisungsausführung einbezogen wird.  
  
3.  Rufen Sie **SQLExecDirect** oder **SQLExecute** auf, um die vorbereitete Anweisung auszuführen.  
  
 Die folgenden Regeln gelten für das Array, das durch das Feld SQL_DESC_ARRAY_STATUS_PTR der APD definiert ist:  
  
-   Der Zeiger ist standardmäßig auf null gesetzt.  
  
-   Wenn der Zeiger null ist, werden alle Parametersätze verwendet, als ob alle Elemente auf SQL_ROW_PROCEED festgelegt wären.  
  
-   Das Festlegen eines Elements auf SQL_PARAM_PROCEED garantiert nicht, dass der Vorgang diesen bestimmten Satz von Parametern verwendet.  
  
-   SQL_PARAM_PROCEED ist in der Headerdatei als 0 definiert.  
  
 Eine Anwendung kann das SQL_DESC_ARRAY_STATUS_PTR Feld in der APD so einstellen, dass es auf dasselbe Array zeigt, auf das das Feld SQL_DESC_ARRAY_STATUS_PTR im IRD hinweist. Dies ist nützlich, wenn Parameter an Zeilendaten bindung. Parameter können dann entsprechend dem Status der Zeilendaten ignoriert werden. Zusätzlich zu SQL_PARAM_IGNORE führen die folgenden Codes dazu, dass ein Parameter in einer SQL-Anweisung ignoriert wird: SQL_ROW_DELETED, SQL_ROW_UPDATED und SQL_ROW_ERROR. Zusätzlich zu SQL_PARAM_PROCEED führen die folgenden Codes dazu, dass eine SQL-Anweisung fortgesetzt wird: SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO und SQL_ROW_ADDED.  
  
## <a name="rebinding-parameters"></a>Neubindungsparameter

 Eine Anwendung kann einen der beiden Vorgänge ausführen, um eine Bindung zu ändern:  
  
-   Rufen Sie **SQLBindParameter** auf, um eine neue Bindung für eine Spalte anzugeben, die bereits gebunden ist. Der Treiber überschreibt die alte Bindung mit der neuen.  
  
-   Geben Sie einen Offset an, der der Pufferadresse hinzugefügt werden soll, die durch den Bindungsaufruf an **SQLBindParameter**angegeben wurde. Weitere Informationen finden Sie im nächsten Abschnitt "Wiederbinden mit Offsets".  
  
## <a name="rebinding-with-offsets"></a>Neubindung mit Offsets

 Das erneute Binden von Parametern ist besonders nützlich, wenn eine Anwendung über eine Pufferbereichseinrichtung verfügt, die viele Parameter enthalten kann, aber ein Aufruf von **SQLExecDirect** oder **SQLExecute** nur wenige der Parameter verwendet. Der verbleibende Platz im Pufferbereich kann für den nächsten Parametersatz verwendet werden, indem die vorhandene Bindung durch einen Offset geändert wird.  
  
 Das SQL_DESC_BIND_OFFSET_PTR Kopffeld im APD zeigt auf den Bindungsoffset. Wenn das Feld ungleich NULL ist, verweist der Treiber auf den Zeiger, und wenn keiner der Werte in den Feldern SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR ein Nullzeiger ist, fügt er den dereferenzierten Wert zu diesen Feldern in den Deskriptordatensätzen zur Ausführungszeit hinzu. Die neuen Zeigerwerte werden verwendet, wenn die SQL-Anweisungen ausgeführt werden. Der Offset bleibt nach der Neubindung gültig. Da SQL_DESC_BIND_OFFSET_PTR ein Zeiger auf den Offset und nicht auf den Offset selbst ist, kann eine Anwendung den Offset direkt ändern, ohne [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) oder [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md) aufrufen zu müssen, um das Deskriptorfeld zu ändern. Der Zeiger ist standardmäßig auf null gesetzt. Das SQL_DESC_BIND_OFFSET_PTR Feld der ARD kann durch einen Aufruf von [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) oder durch einen Aufruf von [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)mit einem *fAttribute* von SQL_ATTR_PARAM_BIND_OFFSET_PTR eingestellt werden.  
  
 Der Bindungsoffset wird immer direkt zu den Werten in den Feldern SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR hinzugefügt. Wenn der Offset in einen anderen Wert geändert wird, wird der neue Wert weiterhin direkt zum Wert in jedem Deskriptorfeld hinzugefügt. Der neue Offset wird nicht zur Summe des Feldwerts und aller früheren Offsets hinzugefügt.  
  
## <a name="descriptors"></a>Deskriptoren

 Wie ein Parameter gebunden wird, wird durch Felder der APDs und IPDs bestimmt. Die Argumente in **SQLBindParameter** werden verwendet, um diese Deskriptorfelder festzulegen. Die Felder können auch von den **SQLSetDescField-Funktionen** festgelegt werden, obwohl **SQLBindParameter** effizienter zu verwenden ist, da die Anwendung kein Deskriptorhandle zum Aufrufen von **SQLBindParameter**abrufen muss.  
  
> [!CAUTION]  
>  Das Aufrufen von **SQLBindParameter** für eine Anweisung kann sich auf andere Anweisungen auswirken. Dies geschieht, wenn die ARD, die mit der Erklärung verbunden ist, explizit zugeordnet und auch mit anderen Aussagen in Verbindung gebracht wird. Da **SQLBindParameter** die Felder der APD ändert, gelten die Änderungen für alle Anweisungen, denen dieser Deskriptor zugeordnet ist. Wenn dies nicht das erforderliche Verhalten ist, sollte die Anwendung diesen Deskriptor von den anderen Anweisungen trennen, bevor sie **SQLBindParameter aufruft.**  
  
 **SqlBindParameter** führt konzeptionell die folgenden Schritte nacheinander aus:  
  
1.  Ruft [SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) auf, um das APD-Handle abzuerhalten.  
  
2.  Ruft [SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) auf, um das SQL_DESC_COUNT Feld der APD abzubekommen, und wenn der Wert des *Arguments ColumnNumber* den Wert von SQL_DESC_COUNT überschreitet, ruft **SQLSetDescField** auf, um den Wert von SQL_DESC_COUNT zu *ColumnNumber*zu erhöhen.  
  
3.  Ruft [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) mehrmals auf, um den folgenden Feldern der APD Werte zuzuweisen:  
  
    -   Legt SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE auf den Wert von *ValueType*fest, mit der Ausnahme, dass, wenn *ValueType* einer der prägnanten Bezeichner eines Datumszeit- oder Intervallsubtyps ist, SQL_DESC_TYPE auf SQL_DATETIME bzw. SQL_INTERVAL festgelegt wird, SQL_DESC_CONCISE_TYPE auf den prägnanten Bezeichner festlegt und SQL_DESC_DATETIME_INTERVAL_CODE auf den entsprechenden Datumszeit- oder Intervalluntercode festlegt.  
  
    -   Legt das SQL_DESC_OCTET_LENGTH Feld auf den Wert *BufferLength*fest.  
  
    -   Legt das feld SQL_DESC_DATA_PTR auf den Wert von *ParameterValue*fest.  
  
    -   Legt das Feld SQL_DESC_OCTET_LENGTH_PTR auf den Wert *von StrLen_or_Ind*fest.  
  
    -   Legt das SQL_DESC_INDICATOR_PTR Feld auch auf den Wert *von StrLen_or_Ind*fest.  
  
     Der *Parameter StrLen_or_Ind* gibt sowohl die Indikatorinformationen als auch die Länge für den Parameterwert an.  
  
4.  Ruft [SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) auf, um das IPD-Handle abzuerhalten.  
  
5.  Ruft [SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) auf, um das SQL_DESC_COUNT Feld der IPD abzubekommen, und wenn der Wert des *Arguments ColumnNumber* den Wert von SQL_DESC_COUNT überschreitet, ruft **SQLSetDescField** auf, um den Wert von SQL_DESC_COUNT zu *ColumnNumber*zu erhöhen.  
  
6.  Ruft [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) mehrmals auf, um den folgenden Feldern der IPD Werte zuzuweisen:  
  
    -   Legt SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE auf den Wert von *ParameterType*fest, mit der Ausnahme, dass *ParameterType,* wenn parameterType einer der prägnanten Bezeichner eines Datumszeit- oder Intervallsubtyps ist, SQL_DESC_TYPE auf SQL_DATETIME bzw. SQL_INTERVAL festgelegt wird, SQL_DESC_CONCISE_TYPE auf den prägnanten Bezeichner festlegt und SQL_DESC_DATETIME_INTERVAL_CODE auf den entsprechenden Datumszeit- oder Intervalluntercode festlegt.  
  
    -   Legt je nach *ParameterType*einen oder mehrere SQL_DESC_LENGTH, SQL_DESC_PRECISION und SQL_DESC_DATETIME_INTERVAL_PRECISION fest.  
  
    -   Legt SQL_DESC_SCALE auf den Wert von *DecimalDigits*fest.  
  
 Wenn der Aufruf von **SQLBindParameter** fehlschlägt, ist der Inhalt der Deskriptorfelder, die er in der APD festgelegt hätte, nicht definiert, und das SQL_DESC_COUNT Feld der APD bleibt unverändert. Darüber hinaus sind die Felder SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_TYPE des entsprechenden Datensatzes in der IPD nicht definiert, und das SQL_DESC_COUNT Feld der IPD bleibt unverändert.  
  
## <a name="conversion-of-calls-to-and-from-sqlsetparam"></a>Konvertierung von Aufrufen zu und von SQLSetParam

 Wenn eine ODBC 1.0-Anwendung **SQLSetParam** in einem ODBC 3 aufruft. *x-Treiber,* der ODBC 3. *x* Driver Manager ordnet den Anruf wie in der folgenden Tabelle dargestellt zu.  
  
|Aufruf von ODBC 1.0-Anwendung|Rufen Sie ODBC 3 auf. *x-Treiber*|  
|----------------------------------|-------------------------------|  
|SQLSetParam( StatementHandle, ParameterNumber, ValueType, ParameterType, LengthPrecision, ParameterScale, ParameterValuePtr, StrLen_or_IndPtr);|SQLBindParameter( StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, *ColumnSize*, *DecimalDigits*, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr);|  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel bereitet eine Anwendung eine SQL-Anweisung vor, um Daten in die ORDERS-Tabelle einzufügen. Für jeden Parameter in der Anweisung ruft die Anwendung **SQLBindParameter** auf, um den ODBC C-Datentyp und den SQL-Datentyp des Parameters anzugeben und einen Puffer an jeden Parameter zu binden. Für jede Datenzeile weist die Anwendung jedem Parameter Datenwerte zu und ruft **SQLExecute** auf, um die Anweisung auszuführen.  
  
 Im folgenden Beispiel wird davon ausgegangen, dass Sie eine ODBC-Datenquelle auf Ihrem Computer namens Northwind haben, die der Northwind-Datenbank zugeordnet ist.  
  
 Weitere Codebeispiele finden Sie unter [SQLBulkOperations Function](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLProcedures Function](../../../odbc/reference/syntax/sqlprocedures-function.md), [SQLPutData Function](../../../odbc/reference/syntax/sqlputdata-function.md)und [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```cpp
// SQLBindParameter_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
#define EMPLOYEE_ID_LEN 10  
  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLRETURN retcode;  
SQLHSTMT hstmt = NULL;  
SQLSMALLINT sCustID;  
  
SQLCHAR szEmployeeID[EMPLOYEE_ID_LEN];  
SQL_DATE_STRUCT dsOrderDate;  
SQLINTEGER cbCustID = 0, cbOrderDate = 0, cbEmployeeID = SQL_NTS;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, EMPLOYEE_ID_LEN, 0, szEmployeeID, 0, &cbEmployeeID);  
   retcode = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sCustID, 0, &cbCustID);  
   retcode = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TIMESTAMP, sizeof(dsOrderDate), 0, &dsOrderDate, 0, &cbOrderDate);  
  
   retcode = SQLPrepare(hstmt, (SQLCHAR*)"INSERT INTO Orders(CustomerID, EmployeeID, OrderDate) VALUES (?, ?, ?)", SQL_NTS);  
  
   strcpy_s((char*)szEmployeeID, _countof(szEmployeeID), "BERGS");  
   sCustID = 5;  
   dsOrderDate.year = 2006;  
   dsOrderDate.month = 3;  
   dsOrderDate.day = 17;  
  
   retcode = SQLExecute(hstmt);  
}  
```  
  
## <a name="code-example"></a>Codebeispiel

 Im folgenden Beispiel führt eine Anwendung eine gespeicherte SQL Server-Prozedur mit einem benannten Parameter aus.  
  
```cpp
// SQLBindParameter_Function_2.cpp  
// compile with: ODBC32.lib  
// sample assumes the following stored procedure:  
// use northwind  
// DROP PROCEDURE SQLBindParameter  
// GO  
//   
// CREATE PROCEDURE SQLBindParameter @quote int  
// AS  
// delete from orders where OrderID >= @quote  
// GO  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
SQLHDESC hIpd = NULL;  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLRETURN retcode;  
SQLHSTMT hstmt = NULL;  
SQLCHAR szQuote[50] = "100084";  
SQLINTEGER cbValue = SQL_NTS;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retcode = SQLPrepare(hstmt, (SQLCHAR*)"{call SQLBindParameter(?)}", SQL_NTS);  
   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 50, 0, szQuote, 0, &cbValue);  
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &hIpd, 0, 0);  
   retcode = SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);  
  
   retcode = SQLExecute(hstmt);  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben von Informationen zu einem Parameter in einer Anweisung|[SQLDescribeParam-Funktion](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Freigeben von Parameterpuffern für die Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Zurückgeben der Anzahl der Anweisungsparameter|[SQLNumParams-Funktion](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|Zurückgeben des nächsten Parameters zum Senden von Daten für|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Angeben mehrerer Parameterwerte|[SQLParamOptions-Funktion](../../../odbc/reference/syntax/sqlparamoptions-function.md)|  
|Senden von Parameterdaten zur Ausführungszeit|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen

 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
