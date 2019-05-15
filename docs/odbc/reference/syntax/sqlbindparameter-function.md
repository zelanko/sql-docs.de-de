---
title: SQLBindParameter-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 13f4c879f94118a2e2302a2032991e85551be0f7
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538130"
---
# <a name="sqlbindparameter-function"></a>SQLBindParameter-Funktion

**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 2.0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLBindParameter** bindet einen Puffer an eine parametermarkierung in einer SQL­Anweisung. **SQLBindParameter** unterstützt die Bindung an eine Unicode-C-Datentyp, selbst wenn die zugrunde liegenden Treiber Unicode-Daten nicht unterstützt.  
  
> [!NOTE]  
>  Diese Funktion ersetzt die ODBC-1.0-Funktion **SQLSetParam**. Weitere Informationen finden Sie unter "Kommentare".  
  
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
 [Eingabe] Parameter, mit der Nummer sortiert sequenziell in aufsteigender Parameterreihenfolge, beginnend mit 1.  
  
 *InputOutputType*  
 [Eingabe] Der Typ des Parameters. Weitere Informationen finden Sie unter "*InputOutputType* Argument" in "Kommentare".  
  
 *ValueType*  
 [Eingabe] Der C-Datentyp des Parameters. Weitere Informationen finden Sie unter "*ValueType* Argument" in "Kommentare".  
  
 *ParameterType*  
 [Eingabe] Der SQL-Datentyp des Parameters. Weitere Informationen finden Sie unter "*ParameterType* Argument" in "Kommentare".  
  
 *ColumnSize*  
 [Eingabe] Die Größe der Spalte oder des Ausdrucks der entsprechenden parametermarkierung. Weitere Informationen finden Sie unter "*ColumnSize* Argument" in "Kommentare".  
  
 Wenn Ihre Anwendung auf einem 64-Bit-Windows-Betriebssystem ausgeführt wird, finden Sie unter [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md).  
  
 *DecimalDigits*  
 [Eingabe] Die Dezimalstellen der Spalte oder des Ausdrucks der entsprechenden parametermarkierung. Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *ParameterValuePtr*  
 [Verzögerte Eingabe] Ein Zeiger auf einen Puffer für die Parameterdaten. Weitere Informationen finden Sie unter "*ParameterValuePtr* Argument" in "Kommentare".  
  
 *BufferLength*  
 [Eingabe/Ausgabe] Länge der *ParameterValuePtr* Puffers in Byte. Weitere Informationen finden Sie unter "*Pufferlänge* Argument" in "Kommentare".  
  
 Finden Sie unter [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird.  
  
 *StrLen_or_IndPtr*  
 [Verzögerte Eingabe] Ein Zeiger auf einen Puffer für die Länge des-Parameters werden soll. Weitere Informationen finden Sie unter "*StrLen_or_IndPtr* Argument" in "Kommentare".  
  
## <a name="returns"></a>Rückgabewert

 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose

 Wenn **SQLBindParameter** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und eine *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLBindParameter** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  

|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|Der identifizierte Datentyp die *ValueType* Argument kann nicht konvertiert werden, in den Datentyp von identifiziert die *ParameterType* Argument. Beachten Sie, die von dieser Fehler zurückgegeben werden kann **SQLExecDirect**, **SQLExecute**, oder **SQLPutData** zum Zeitpunkt der Ausführung, anstatt nach **SQLBindParameter**.|  
|07009|Ungültiger Deskriptorindex|(DM) der Wert für das Argument angegebene *ParameterNumber* war kleiner als 1.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in der **MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY003|Ungültiger Anwendungspuffertyp|Der Wert, der durch das Argument angegebenen *ValueType* war keine gültige C-Datentyp oder SQL_C_DEFAULT.|  
|HY004|Ungültiger SQL-Datentyp|Der angegebene Wert für das Argument *ParameterType* war weder eine gültige ODBC-SQL-Datentypbezeichner noch eine treiberspezifische SQL Datentypbezeichner vom Treiber unterstützt werden.|  
|HY009|Ungültiger Argumentwert|(DM) das Argument *ParameterValuePtr* wurde ein null-Zeiger ist das Argument *StrLen_or_IndPtr* wurde ein null-Zeiger ist, und das Argument *InputOutputType* war nicht SQL_PARAM_ DIE AUSGABE.<br /><br /> SQL_PARAM_OUTPUT (DM), wobei das Argument *ParameterValuePtr* wurde ein null-Zeiger der C-Typ wurde Char "oder" Binary, und die Pufferlänge (*CbValueMax*) war größer als 0.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn **SQLBindParameter** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY021|Inkonsistente deskriptorinformation|Die Informationen der Sicherheitsbeschreibung während einer konsistenzprüfung eingecheckt war nicht konsistent. (Finden Sie im Abschnitt "Konsistenzprüfungen" in **SQLSetDescField**.)<br /><br /> Der angegebene Wert für das Argument *DecimalDigits* lag außerhalb des Bereichs von Werten, die von der Datenquelle für eine Spalte mit der angegebenen SQL-Datentyp unterstützt die *ParameterType* Argument.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) den Wert in *Pufferlänge* war kleiner als 0. (Siehe dazu die Beschreibung das SQL_DESC_DATA_PTR-Feld in **SQLSetDescField**.)|  
|HY104|Ungültiger Wert für Genauigkeit oder Dezimalstellenanzahl|Der angegebene Wert für das Argument *ColumnSize* oder *DecimalDigits* lag außerhalb des Bereichs von Werten, die von der Datenquelle für eine Spalte mit der angegebenen SQL-Datentyp unterstützt die  *ParameterType* Argument.|  
|HY105|Ungültiger Parametertyp|(DM) der Wert für das Argument angegebene *InputOutputType* war ungültig. (Siehe "Kommentare".)|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Treiber oder die Datenquelle unterstützt nicht die Konvertierung durch die Kombination der angegebene Wert für das Argument angegebenen *ValueType* und der Treiber-spezifische-Wert, der für das Argument angegebene *ParameterType*.<br /><br /> Der angegebene Wert für das Argument *ParameterType* wurde ein gültiger ODBC-SQL-Datentypbezeichner, für die ODBC-Version vom Treiber unterstützt, jedoch wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Der Treiber unterstützt nur ODBC 2. *x* und das Argument *ValueType* war eines der folgenden:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> und die C-Intervall-Datentypen in [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen.<br /><br /> Der Treiber unterstützt nur die ODBC-Versionen vor, und das Argument zum Preis von 3,50 *ValueType* SQL_C_GUID wurde.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare

 Ruft die Anwendung **SQLBindParameter** jede parametermarkierung in einer SQL-Anweisung zu binden. Bindungen bleiben wirksam, bis die Anwendung ruft **SQLBindParameter** in diesem Fall ruft **SQLFreeStmt** mit SQL_RESET_PARAMS-Option oder Aufrufe **SQLSetDescField** auf das Headerfeld SQL_DESC_COUNT APD auf 0 festgelegt.  
  
 Weitere Informationen zu Parametern finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md). Weitere Informationen zu Datentypen und parametermarkierungen, finden Sie unter [Parameterdatentypen](../../../odbc/reference/appendixes/parameter-data-types.md) und [Parametermarkierungen](../../../odbc/reference/appendixes/parameter-markers.md) in Anhang C: SQL-Grammatik.  
  
## <a name="parameternumber-argument"></a>ParameterNumber-Argument  
 Wenn *ParameterNumber* im Aufruf von **SQLBindParameter** ist größer als der Wert des SQL_DESC_COUNT, **SQLSetDescField** wird aufgerufen, um den Wert des SQL_DESC_ erhöhen Anzahl der zu *ParameterNumber*.  
  
## <a name="inputoutputtype-argument"></a>InputOutputType-Argument  
 Die *InputOutputType* Argument gibt den Typ des Parameters. Dieses Argument legt Feld SQL_DESC_PARAMETER_TYPE in IPD fest. Alle Parameter im SQL-Anweisungen, die nicht Verfahren, wie z. B. Aufrufen **einfügen** -Anweisungen sind *Eingabe ** Parameter*. In Prozeduraufrufen können eingegeben werden, Eingabe/Ausgabe- oder Ausgabeparameter enthalten. (Eine Anwendung ruft **SQLProcedureColumns** bestimmen den Typ eines Parameters in einem Prozeduraufruf, Parameter, dessen Typ kann nicht bestimmt werden, gelten als Eingabeparameter.)  
  
 Die *InputOutputType* Argument ist eine der folgenden Werte:  
  
-   SQL_PARAM_INPUT. Der Parameter kennzeichnet einen Parameter in einer SQL-Anweisung, die eine Prozedur, nicht, wie z. B. aufgerufen wird eine **einfügen** -Anweisung, oder markiert einen Eingabeparameter in einer Prozedur. Zum Beispiel die Parameter in **INSERT INTO Mitarbeiter VALUES (?,?,?)**  Eingabeparameter sind, während die Parameter in **{AddEmp aufrufen (?,?,?)}**  kann sein, aber nicht notwendigerweise, Eingabeparameter.  
  
     Wenn die Anweisung ausgeführt wird, sendet der Treiber Daten für den Parameter an die Datenquelle an. die \* *ParameterValuePtr* Puffer muss einen gültigen Eingabewert enthalten oder **StrLen_or_IndPtr* Puffer darf, SQL_NULL_DATA, SQL_DATA_AT_EXEC oder das Ergebnis der SQL_LEN_DATA_AT _EXEC-Makro.  
  
     Wenn eine Anwendung nicht den Typ eines Parameters in einem Prozeduraufruf bestimmen kann, wird *InputOutputType* zu SQL_PARAM_INPUT; Wenn die Datenquelle gibt einen Wert für den Parameter zurück, verwirft der Treiber es.  
  
-   SQL_PARAM_INPUT_OUTPUT. Der-Parameter kennzeichnet eine Eingabe-/Ausgabeparameter in einer Prozedur. Z. B. der Parameter in **{aufrufen GetEmpDept(?)}**  ist ein e/a-Parameter, die den Namen eines Mitarbeiters akzeptiert und gibt den Namen des Mitarbeiters Abteilung zurück.  
  
     Wenn die Anweisung ausgeführt wird, sendet der Treiber Daten für den Parameter an die Datenquelle an. die \* *ParameterValuePtr* Puffer muss einen gültigen Eingabewert enthält oder der \* *StrLen_or_IndPtr* Puffer darf, SQL_NULL_DATA, SQL_DATA_AT_EXEC oder das Ergebnis des das Makro SQL_LEN_DATA_AT_EXEC. Nachdem die Anweisung ausgeführt wird, gibt der Treiber die Daten für den Parameter zurück, an die Anwendung; Wenn die Datenquelle nicht für eine Eingabe/Ausgabe-Parameter einen Wert zurückgibt, wird der Treiber setzt die **StrLen_or_IndPtr* Puffer auf SQL_NULL_DATA.  
  
    > [!NOTE]  
    >  Wenn eine ODBC-1.0-Anwendung aufruft **SQLSetParam** in ODBC 2.0-Treiber, der Treiber-Manager konvertiert diese in einen Aufruf von **SQLBindParameter** in dem die *InputOutputType* Argument wird auf SQL_PARAM_INPUT_OUTPUT festgelegt.  
  
-   SQL_PARAM_OUTPUT. Der Parameter markiert den Rückgabewert einer Prozedur oder ein Output-Parameter in einer Prozedur; in beiden Fällen werden diese als bezeichnet *Ausgabeparameter*. Z. B. der Parameter in **{? = aufrufen GetNextEmpID}** ist ein Ausgabeparameter, der die nächste Mitarbeiter-ID zurückgibt.  
  
     Nachdem die Anweisung ausgeführt wird, gibt der Treiber Daten für den Parameter an die Anwendung, es sei denn, die *ParameterValuePtr* und *StrLen_or_IndPtr* Argumente sind null-Zeiger, in diesem Fall die Treiber verwirft den Ausgabewert. Wenn die Datenquelle keinen Wert für ein Output-Parameter zurückgibt, wird der Treiber setzt die **StrLen_or_IndPtr* Puffer auf SQL_NULL_DATA.  
  
-   SQL_PARAM_INPUT_OUTPUT_STREAM. Gibt an, dass ein Eingabe-/Ausgabeparameter gestreamt werden sollen. **SQLGetData** können Parameterwerte in Teilen zu lesen. *BufferLength* wird ignoriert, da die Länge des Puffers beim Aufruf der eingestuft wird **SQLGetData**. Der Wert des der *StrLen_or_IndPtr* Puffer muss SQL_NULL_DATA SQL_DEFAULT_PARAM, SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC Makros enthalten. Wenn es an der Ausgabe gestreamt wird, muss ein Parameter als Data-at-Execution (. DAE) Parameter an der Eingabe gebunden werden. *ParameterValuePtr* kann jeder nicht-Null-Zeiger-Wert, der von zurückgegeben werden, werden **SQLParamData** wie der benutzerdefinierte-, dessen Wert Token mit übergebene *ParameterValuePtr* für sowohl Eingabe- und die Ausgabe. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_PARAM_OUTPUT_STREAM. Identisch mit SQL_PARAM_INPUT_OUTPUT_STREAM, für die ein Output-Parameter. **StrLen_or_IndPtr* bei Eingabe ignoriert.  
  
 Die folgende Tabelle enthält verschiedene Kombinationen von *InputOutputType* und **StrLen_or_IndPtr*:  
  
|*InputOutputType*|**StrLen_or_IndPtr*|Ergebnis|Weisen darauf hin, auf ParameterValuePtr|  
|-----------------------|----------------------------|-------------|---------------------------------|  
|SQL_PARAM_INPUT|SQL_LEN_DATA_AT_EXEC (*Len*) oder SQL_DATA_AT_EXEC|Eingabe in Teilen|*ParameterValuePtr* können Zeigerwert, der von zurückgegeben werden, werden **SQLParamData** wie der benutzerdefinierte-, dessen Wert Token mit übergebene *ParameterValuePtr*.|  
|SQL_PARAM_INPUT|Nicht SQL_LEN_DATA_AT_EXEC (*Len*) oder SQL_DATA_AT_EXEC|Eingabe gebunden Puffer|*ParameterValuePtr* ist die Adresse des Eingabepuffers.|  
|SQL_PARAM_OUTPUT|Bei Eingabe ignoriert.|Gebundene Ausgabepuffer|*ParameterValuePtr* ist die Adresse des Ausgabepuffers.|  
|SQL_PARAM_OUTPUT_STREAM|Bei Eingabe ignoriert.|Gestreamte Ausgabe|*ParameterValuePtr* möglich, dass alle Zeigerwert, der zurückgegebenen **SQLParamData** wie der benutzerdefinierte-, dessen Wert Token mit übergebene *ParameterValuePtr*.|  
|SQL_PARAM_INPUT_OUTPUT|SQL_LEN_DATA_AT_EXEC (*Len*) oder SQL_DATA_AT_EXEC|Eingabe in Teile und gebundene Ausgabepuffer|*ParameterValuePtr* ist die Adresse des Ausgabepuffers, die auch von zurückgegeben werden **SQLParamData** wie der benutzerdefinierte-, dessen Wert Token mit übergebene *ParameterValuePtr*.|  
|SQL_PARAM_INPUT_OUTPUT|Nicht SQL_LEN_DATA_AT_EXEC (*Len*) oder SQL_DATA_AT_EXEC|Eingabe gebunden, Puffer und gebundene Ausgabepuffer|*ParameterValuePtr* ist die Adresse der freigegebenen e/a-Puffer.|
|SQL_PARAM_INPUT_OUTPUT_STREAM|SQL_LEN_DATA_AT_EXEC (*Len*) oder SQL_DATA_AT_EXEC|Eingabe in Teile und gestreamte Ausgabe|*ParameterValuePtr* möglich, dass alle nicht-Null-Zeiger-Wert, der zurückgegebenen **SQLParamData** wie der benutzerdefinierte-, dessen Wert Token mit übergeben wurde *ParameterValuePtr* für beide Eingabe und die Ausgabe.|  
  
> [!NOTE]  
>  Der Treiber muss entscheiden, welche SQL-Typen zulässig sind, wenn eine Anwendung eines Ausgabe- oder Eingabe / Ausgabe-Parameter gebunden, übertragen. Der Treiber-Manager generiert keine Fehler ein ungültiger SQL-Typ.  
  
## <a name="valuetype-argument"></a>ValueType-Argument

 Die *ValueType* Argument gibt an, die C-Datentyp des Parameters. Dieses Argument legt fest, die Felder SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE APD. Dies muss einer der Werte in der [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) Abschnitt Anhang D: Datentypen.  
  
 Wenn die *ValueType* Argument ist eine von der Interval-Datentypen, das SQL_DESC_TYPE-Feld, der die *ParameterNumber* Datensatz APD nastaven NA hodnotu SQL_INTERVAL ist festgelegt, Feld SQL_DESC_CONCISE_TYPE in APD die präzise Interval-Datentypen und das Feld SQL_DESC_DATETIME_INTERVAL_CODE, der die *ParameterNumber* Datensatz auf einem Subcode für den bestimmten Intervall-Datentyp festgelegt ist. (Finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).) Das Standardintervall für führende Genauigkeit (2) und Intervall Sekunden standardgenauigkeit (6), wie in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION und SQL_DESC_PRECISION der APD, festgelegt, werden für die Daten verwendet. Wenn entweder die standardgenauigkeit nicht geeignet ist, der Anwendung sollten explizit festlegen das Deskriptorfeld durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**.  
  
 Wenn die *ValueType* Argument ist einer der Datentypen "DateTime", das SQL_DESC_TYPE-Feld, der die *ParameterNumber* Datensatz APD nastaven NA hodnotu SQL_DATETIME, Feld SQL_DESC_CONCISE_TYPE der *ParameterNumber* Datensatz APD festgelegt ist, die präzise "DateTime"-C-Datentyp und das Feld SQL_DESC_DATETIME_INTERVAL_CODE der *ParameterNumber* Datensatz auf einen Subcode für jeweils Datum und Uhrzeit festgelegt ist -Datentyp. (Finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Wenn die *ValueType* Argument ist ein Datentyp SQL_C_NUMERIC für die standardmäßige Genauigkeit (die treiberdefinierten) und der Standardwert (0) festgelegt, in die Felder SQL_DESC_PRECISION und SQL_DESC_SCALE der APD, dienen für die Daten. Wenn die standardmäßige Genauigkeit oder Skala nicht geeignet ist, der Anwendung sollten explizit festlegen das Deskriptorfeld durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**.  
  
 SQL_C_DEFAULT gibt an, dass der Wert des Parameters aus dem Standard-C-Datentyp übertragen werden, für die SQL-Datentyp angegeben *ParameterType*.  
  
 Sie können auch einen erweiterte C-Datentyp angeben. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 Weitere Informationen finden Sie unter [C-Standarddatentypen](../../../odbc/reference/appendixes/default-c-data-types.md), [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md), und [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in Anhang D: Datentypen.  
  
## <a name="parametertype-argument"></a>ParameterType-Argument

 Dies muss einer der Werte aufgeführt, die der [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) Abschnitt Anhang D: Datentypen, oder es muss eine treiberspezifische-Wert sein. Dieses Argument legt die SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE Felder des IPD fest.  
  
 Wenn die *ParameterType* Argument ist einer der Bezeichner "DateTime", das SQL_DESC_TYPE-Feld des IPD nastaven NA hodnotu SQL_DATETIME, Feld SQL_DESC_CONCISE_TYPE in IPD präzise "DateTime" SQL-Datentyps und der SQL_DESC_ festgelegt ist DATETIME_INTERVAL_CODE-Feld ist auf den entsprechenden Datetime subcodewert festgelegt.  
  
 Wenn *ParameterType* ist die Intervall-Bezeichner, wird das SQL_DESC_TYPE-Feld des IPD auf SQL_INTERVAL festgelegt, den präzise Datentyp für die SQL-Zeitintervall und die SQL_DESC_DATETIME_ Feld SQL_DESC_CONCISE_TYPE in IPD festgelegt ist INTERVAL_CODE-Feld des IPD ist auf dem Subcode angemessenen Zeitraum festgelegt. Die SQL_DESC_DATETIME_INTERVAL_PRECISION-Feld des IPD ist die führende Genauigkeit Intervall festgelegt, und das Feld "SQL_DESC_PRECISION" auf eine Genauigkeit von Sekunden das Intervall festgelegt ist, falls zutreffend. Wenn der Standardwert der SQL_DESC_DATETIME_INTERVAL_PRECISION oder SQL_DESC_PRECISION nicht geeignet ist, die Anwendung sollte legen Sie es explizit durch Aufrufen von **SQLSetDescField**. Weitere Informationen zu diesen Feldern finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Wenn die *ValueType* Argument ist ein SQL_NUMERIC-Datentyp, der die Genauigkeit (die treiberdefinierten) und der Standardwert (0) festgelegt, in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE des IPD, dienen für die Daten. Wenn die standardmäßige Genauigkeit oder Skala nicht geeignet ist, der Anwendung sollten explizit festlegen das Deskriptorfeld durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**.  
  
 Weitere Informationen dazu, wie die Daten konvertiert werden, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) und [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in Anhang D: Datentypen.  
  
## <a name="columnsize-argument"></a>ColumnSize-Argument

 Die *ColumnSize* Argument gibt die Größe der Spalte oder des Ausdrucks, der an die parametermarkierung, die Länge der Daten oder beides entspricht. Dieses Argument setzt verschiedene Felder des IPD, abhängig von der SQL-Datentyp (der *ParameterType* Argument). Die folgenden Regeln gelten für diese Zuordnung auf:  
  
-   Wenn *ParameterType* ist SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_BINARY, SQL_VARBINARY und SQL_LONGVARBINARY oder eines die präzisen SQL "DateTime" oder das Intervall-Datentypen, die SQL_DESC_LENGTH-Feld des IPD festgelegt ist, auf den Wert der  *ColumnSize*. (Weitere Informationen finden Sie unter den [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) Abschnitt in Anhang D: Die Datentypen.)  
  
-   Wenn *ParameterType* ist SQL_DECIMAL SQL_NUMERIC, SQL_FLOAT, SQL_REAL oder SQL_DOUBLE, Feld SQL_DESC_PRECISION in IPD festgelegt ist, auf den Wert der *ColumnSize*.  
  
-   Für andere Datentypen die *ColumnSize* Argument wird ignoriert.  
  
 Weitere Informationen finden Sie unter "Übergeben von Parameterwerten" und SQL_DATA_AT_EXEC in "*StrLen_or_IndPtr* Argument."  
  
## <a name="decimaldigits-argument"></a>DecimalDigits-Argument

 Wenn *ParameterType* ist SQL_TYPE_TIME SQL_TYPE_TIMESTAMP, SQL_INTERVAL_SECOND, SQL_INTERVAL_DAY_TO_SECOND, SQL_INTERVAL_HOUR_TO_SECOND oder SQL_INTERVAL_MINUTE_TO_SECOND, Feld SQL_DESC_PRECISION in IPD festgelegt ist um *DecimalDigits*. Wenn *ParameterType* ist SQL_NUMERIC oder SQL_DECIMAL, Feld SQL_DESC_SCALE in IPD nastaven NA hodnotu *DecimalDigits*. Für alle anderen Datentypen die *DecimalDigits* Argument wird ignoriert.  
  
## <a name="parametervalueptr-argument"></a>ParameterValuePtr-Argument

 Die *ParameterValuePtr* -Argument zeigt auf einen Puffer, wenn **SQLExecute** oder **SQLExecDirect** aufgerufen wird, enthält die tatsächlichen Daten für den Parameter. Die Daten müssen in Form von angegeben sein, dass die *ValueType* Argument. Dieses Argument legt fest, das SQL_DESC_DATA_PTR-Feld der APD. Eine Anwendung festlegen, kann die *ParameterValuePtr* Argument für ein null-Zeiger, solange  *\*StrLen_or_IndPtr* ist SQL_NULL_DATA oder SQL_DATA_AT_EXEC. (Dies trifft nur zu Eingabe-oder Eingabe/Ausgabe).  
  
 Wenn \* *StrLen_or_IndPtr* ist das Ergebnis der SQL_LEN_DATA_AT_EXEC (*Länge*)-Makro oder SQL_DATA_AT_EXEC, klicken Sie dann *ParameterValuePtr* ist ein anwendungsdefinierte Zeigerwert, der dem Parameter zugeordnet ist. Er wird zurückgegeben, die der Anwendung über **SQLParamData**. Z. B. *ParameterValuePtr* kann ein Token ungleich NULL, z. B. ein Parameter mit der Nummer, ein Zeiger auf Daten oder ein Zeiger auf eine Struktur, die die Anwendung mit dem Eingabeparameter gebunden werden. Beachten Sie jedoch, dass bei der Parameter ist ein Eingabe-/Ausgabeparameter *ParameterValuePtr* muss ein Zeiger auf einen Puffer, in der Ausgabewert gespeichert werden kann wird. Wenn der Wert in das Anweisungsattribut verweist SQL_ATTR_PARAMSET_SIZE größer als 1 ist, können die Anwendung den Wert verweist das SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisungsattribut zusammen mit den *ParameterValuePtr* Argument. Z. B. *ParameterValuePtr* möglicherweise zeigen Sie auf ein Array von Werten und die Anwendung möglicherweise verwenden Sie den Wert SQL_ATTR_PARAMS_PROCESSED_PTR verweist auf den richtigen Wert aus dem Array abzurufen. Weitere Informationen finden Sie unter "Übergeben von Parameterwerten" weiter unten in diesem Abschnitt.  
  
 Wenn die *InputOutputType* Argument ist SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT, *ParameterValuePtr* verweist auf einen Puffer, in dem der Treiber den Ausgabewert zurückgibt. Wenn die Prozedur eine oder mehrere Resultsets zurückgibt, die \* *ParameterValuePtr* Puffer ist garantiert nicht festgelegt werden, bis alle Ergebnis legt/Zeilenanzahl verarbeitet wurden. Wenn der Puffer nicht festgelegt ist, bis die Verarbeitung abgeschlossen ist, sind die Output-Parameter und Rückgabewerte nicht verfügbar, bis **SQLMoreResults** SQL_NO_DATA zurückgibt. Aufrufen von **SQLCloseCursor** oder **SQLFreeStmt** mit einer Option von SQL_CLOSE führt dazu, dass diese Werte verworfen werden.  
  
 Wenn der Wert im Attribut-Anweisung verweist SQL_ATTR_PARAMSET_SIZE größer als 1 ist *ParameterValuePtr* zeigt auf ein Array. Eine SQL-Anweisung das gesamte Array mit der Eingabewerten für einen Eingabe- oder Eingabe/Ausgabe-Parameter verarbeitet, und gibt ein Array von Ausgabewerte für eine e/a oder einem Ausgabeparameter zurück.  
  
## <a name="bufferlength-argument"></a>BufferLength-Argument

 Für Zeichen- und Binärdaten C die *Pufferlänge* Argument gibt die Länge des der \* *ParameterValuePtr* Puffer (sofern es sich um ein einzelnes Element ist) oder die Länge eines Elements in der \* *ParameterValuePtr* array (wenn der Wert im Attribut-Anweisung verweist SQL_ATTR_PARAMSET_SIZE größer als 1 ist). Dieses Argument legt die SQL_DESC_OCTET_LENGTH-Datensatzfeld vom APD fest. Wenn die Anwendung mit mehreren Werten angibt *Pufferlänge* wird verwendet, um zu bestimmen, den Speicherort der Werte in der **ParameterValuePtr* array, bei der Eingabe und Ausgabe. Für e/a und Ausgabe-Parameter wird es zu bestimmen, ob zum Abschneiden von Zeichen- und Binärdaten für C bei der Ausgabe verwendet:  
  
-   Für Daten im Zeichenformat C, wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *Pufferlänge*, die Daten in \* *ParameterValuePtr* auf abgeschnitten  *BufferLength* weniger die Länge der einen Null-Terminierungszeichen und Null-terminiert ist vom Treiber.  
  
-   Für C Binärdaten, wenn die Anzahl der zurückzugebenden verfügbaren Bytes übersteigt *Pufferlänge*, die Daten in \* *ParameterValuePtr* auf abgeschnitten *Pufferlänge*Bytes.  
  
 Für alle anderen Typen von C-Daten die *Pufferlänge* Argument wird ignoriert. Die Länge der \* *ParameterValuePtr* Puffer (sofern es sich um ein einzelnes Element ist) oder die Länge eines Elements in der \* *ParameterValuePtr* array (wenn die Anwendung aufruft **SQLSetStmtAttr** mit einer *Attribut* Argument verweist SQL_ATTR_PARAMSET_SIZE zur Angabe mehrerer Werte für jeden Parameter) wird davon ausgegangen, dass die Länge der C-Datentyp sein.  
  
 Für die gestreamte Ausgabe oder gestreamte ein-/Ausgabeparameter der *Pufferlänge* Argument wird ignoriert, da die Länge des Puffers in angegeben ist **SQLGetData**.  
  
> [!NOTE]  
>  Wenn eine ODBC-1.0-Anwendung aufruft **SQLSetParam** in einer ODBC 3. *X* -Treiber verwenden, der Treiber-Manager konvertiert diese in einen Aufruf **SQLBindParameter** in dem die *Pufferlänge* Argument ist immer SQL_SETPARAM_VALUE_MAX. Da der Treiber-Manager einen Fehler Wenn eine ODBC 3. zurückgibt. *x* legt Anwendung *Pufferlänge* zu SQL_SETPARAM_VALUE_MAX, eine ODBC 3. *X* Treiber können dies auf Sie bestimmen, wenn sie von einer ODBC-1.0-Anwendung aufgerufen wird.  
  
> [!NOTE]  
>  In **SQLSetParam**, die Möglichkeit, die angibt, in dem eine Anwendung die Länge des der **ParameterValuePtr* gepuffert, damit der Treiber zurückkehren kann, Zeichen- oder Binärdaten und die Möglichkeit, in denen eine Anwendung sendet, eine Array von Zeichen oder binäre Parameterwerte an den Treiber, sind treiberdefinierten.  
  
## <a name="strlenorindptr-argument"></a>StrLen_or_IndPtr Argument

 Die *StrLen_or_IndPtr* -Argument zeigt auf einen Puffer, wenn **SQLExecute** oder **SQLExecDirect** aufgerufen wird, enthält mindestens eine der folgenden. (Dieses Argument stellt die SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_INDICATOR_PTR Datensatzfelder der Anwendung Parameter Zeiger.)  
  
-   Die Länge der Wert des Parameters, die in gespeicherten **ParameterValuePtr*. Dies wird mit Ausnahme von Zeichen- oder Binärdaten C ignoriert.  
  
-   SQL_NTS. Der Parameterwert ist eine Null-terminierte Zeichenfolge.  
  
-   SQL_NULL_DATA. Der Wert des Parameters ist NULL.  
  
-   SQL_DEFAULT_PARAM. Eine Prozedur ist die Verwendung den Standardwert eines Parameters, statt eines Werts aus der Anwendung abgerufen. Dieser Wert gilt nur in einer Prozedur namens in kanonischer ODBC-Syntax, und klicken Sie dann nur, wenn die *InputOutputType* Argument ist SQL_PARAM_INPUT, SQL_PARAM_INPUT_OUTPUT_STREAM oder SQL_PARAM_INPUT_OUTPUT an. Wenn \* *StrLen_or_IndPtr* SQL_DEFAULT_PARAM, ist die *ValueType*, *ParameterType*, *ColumnSize*,  *DecimalDigits*, *Pufferlänge*, und *ParameterValuePtr* Argumente für Eingabeparameter ignoriert werden und werden nur verwendet, um den Wert des Ausgabeparameters für die Eingabe definieren / Output-Parameter.  
  
-   Das Ergebnis der SQL_LEN_DATA_AT_EXEC (*Länge*) Makro. Die Daten für den Parameter mit gesendet werden, **SQLPutData**. Wenn die *ParameterType* Argument SQL_LONGVARBINARY, SQL_LONGVARCHAR oder einen Long-Wert, Data Source-spezifische Daten eingeben, und gibt "Y" für den Typ der SQL_NEED_LONG_DATA_LEN Informationen in der Treiber **SQLGetInfo**, *Länge* ist die Anzahl von Datenbytes an den-Parameter gesendet werden soll, andernfalls *Länge* muss ein nicht negativen Wert und wird ignoriert. Weitere Informationen finden Sie unter "Übergeben Parameterwerte" weiter unten in diesem Abschnitt.  
  
     Um beispielsweise anzugeben, dass mit 10.000 Bytes an Daten gesendet werden **SQLPutData** in einen oder mehrere Aufrufe für eine SQL_LONGVARCHAR-Parameter, eine Anwendung festlegt **StrLen_or_IndPtr* in SQL_LEN_DATA_AT_EXEC ( 10000).  
  
-   SQL_DATA_AT_EXEC. Die Daten für den Parameter mit gesendet werden, **SQLPutData**. Dieser Wert wird von ODBC-1.0-Anwendungen verwendet, wenn sie ODBC 3. aufrufen. *x* Treiber. Weitere Informationen finden Sie unter "Übergeben Parameterwerte" weiter unten in diesem Abschnitt.  
  
 Wenn *StrLen_or_IndPtr* ist ein null-Zeiger der Treiber wird davon ausgegangen, dass alle Werte der Eingabeparameter ungleich NULL sind und Zeichen und binäre Daten Null-terminiert ist. Wenn *InputOutputType* ist SQL_PARAM_OUTPUT oder SQL_PARAM_OUTPUT_STREAM und *ParameterValuePtr* und *StrLen_or_IndPtr* sind null-Zeiger, der Treiber verwirft der Ausgabewert.  
  
> [!NOTE]  
>  Anwendungsentwickler sind dringend davon abgeraten, einen null-Zeiger für die Angabe *StrLen_or_IndPtr* Wenn der Datentyp des Parameters SQL_C_BINARY ist. Um sicherzustellen, dass ein Treiber nicht unerwartet SQL_C_BINARY Daten abgeschnitten *StrLen_or_IndPtr* muss einen Zeiger auf eine gültige Länge-Wert enthalten.  
  
 Wenn die *InputOutputType* Argument ist SQL_PARAM_INPUT_OUTPUT SQL_PARAM_OUTPUT, SQL_PARAM_INPUT_OUTPUT_STREAM oder SQL_PARAM_OUTPUT_STREAM, *StrLen_or_IndPtr* verweist auf einen Puffer, in dem die Treiber zurückgibt, SQL_NULL_DATA, die verfügbare Anzahl von Bytes im zurückzugebenden \* *ParameterValuePtr* (außer das Null-Terminierung Byte Zeichendaten enthalten sind), oder SQL_NO_TOTAL (wenn die Anzahl der Bytes, die zur Verfügung Return kann nicht ermittelt werden). Wenn die Prozedur eine oder mehrere Resultsets zurückgibt, die **StrLen_or_IndPtr* Puffer ist garantiert nicht festgelegt werden, bis alle Ergebnisse abgerufen wurden.  
  
 Wenn der Wert im Attribut-Anweisung verweist SQL_ATTR_PARAMSET_SIZE größer als 1 ist *StrLen_or_IndPtr* verweist auf ein Array von Werten von SQLLEN. Diese können eines der weiter oben in diesem Abschnitt aufgeführten Werte und werden mit einer einzigen SQL­Anweisung verarbeitet.  
  
## <a name="passing-parameter-values"></a>Übergeben von Parameterwerten

 Eine Anwendung kann den Wert für einen Parameter übergeben, entweder in der \* *ParameterValuePtr* Puffer oder durch eine oder mehrere Aufrufe **SQLPutData**. Parameter, dessen Daten mit übergeben werden **SQLPutData** genannt werden *Data-at-Execution-* Parameter. Diese werden in der Regel zum Senden von Daten für SQL_LONGVARBINARY und SQL_LONGVARCHAR-Parameter verwendet und können mit anderen Parametern kombiniert werden.  
  
 Um Parameterwerte zu übergeben, führt eine Anwendung die folgende Sequenz von Schritten:  
  
1.  Aufrufe **SQLBindParameter** für jeden Parameter, um Puffer für den Wert des Parameters zu binden (*ParameterValuePtr* Argument) und den Längenindikator / (*StrLen_or_IndPtr* Argument). Bei Data-at-Execution-Parametern *ParameterValuePtr* ist ein anwendungsdefinierte Zeigerwert, z. B. ein Parameter mit der Nummer oder ein Zeiger auf Daten. Der Wert wird später zurückgegeben werden und kann verwendet werden, um den Parameter zu identifizieren.  
  
2.  Legt Werte für Eingabe- und Eingabe-/Ausgabeparameter Parameter in der \* *ParameterValuePtr* und **StrLen_or_IndPtr* Puffer:  
  
    -   Für normale-Parameter, die Anwendung platziert den Wert des Parameters in der \* *ParameterValuePtr* Puffer und die Länge des Werts in der **StrLen_or_IndPtr* Puffer. Weitere Informationen finden Sie unter [Einstellung Parameterwerte](../../../odbc/reference/develop-app/setting-parameter-values.md).  
  
    -   Für Data-at-Execution-Parameter, wird die Anwendung das Ergebnis der SQL_LEN_DATA_AT_EXEC (*Länge*) Makro (beim Aufrufen von ODBC 2.0-Treiber) in der **StrLen_or_IndPtr* Puffer.  
  
3.  Aufrufe **SQLExecute** oder **SQLExecDirect** zum Ausführen der SQL-Anweisung.  
  
    -   Wenn keine Data-at-Execution-Parameter vorhanden sind, ist der Prozess abgeschlossen.  
  
    -   Wenn Data-at-Execution-Parameter vorhanden sind, gibt die Funktion SQL_NEED_DATA zurück.  
  
4.  Aufrufe **SQLParamData** zum Abrufen des Anwendung definierte Wert im angegebenen die *ParameterValuePtr* Argument **SQLBindParameter** für die erste Data-at-Execution-Parameter verarbeitet werden. **SQLParamData** wird SQL_NEED_DATA zurückgegeben.  
  
    > [!NOTE]  
    >  Obwohl Data-at-Execution-Parameter Data-at-Execution-Spalten entsprechen, wird der Wert von zurückgegeben **SQLParamData** ist unterschiedlich. Data-at-Execution-Parameter sind die Parameter in einer SQL-Anweisung, die für die Daten gesendet werden mit **SQLPutData** Wenn die Anweisung ausgeführt wird, mit **SQLExecDirect** oder **SQLExecute**. Sie sind mit gebunden **SQLBindParameter**. Der Rückgabewert von **SQLParamData** ist ein Zeigerwert übergeben **SQLBindParameter** in die *ParameterValuePtr* Argument. Data-at-Execution-Spalten in einem Rowset, für die Daten mit gesendet werden, sind **SQLPutData** Wenn eine Zeile aktualisiert oder hinzugefügt, die mit **SQLBulkOperations** oder mit aktualisierten **SQLSetPos**. Sie sind mit gebunden **SQLBindCol**. Den Rückgabewert von **SQLParamData** ist die Adresse der Zeile in der **TargetValuePtr* Puffer (festgelegt durch einen Aufruf von **SQLBindCol**), die verarbeitet wird.  
  
5.  Aufrufe **SQLPutData** einmal oder mehrmals, um Daten für den Parameter zu senden. Mehrere ist erforderlich, wenn der Wert größer ist die \* *ParameterValuePtr* im angegebenen Puffer **SQLPutData**; mehrere Aufrufe **SQLPutData**für denselben Parameter dürfen nur beim Senden von Zeichendaten C an eine Spalte mit einem Zeichen oder den binären datenquellenspezifische Datentyp oder beim Senden von Binärdaten C an eine Spalte mit einem Zeichen, binär, oder geben Sie die spezifischen Daten.  
  
6.  Aufrufe **SQLParamData** erneut aus, um zu signalisieren, dass alle Daten für den Parameter gesendet wurde.  
  
    -   Wenn weitere Data-at-Execution-Parameter, **SQLParamData** gibt SQL_NEED_DATA zurück, und der Anwendung definierte Wert für den nächsten Data-at-Execution-Parameter verarbeitet werden. Die Anwendung wiederholt die Schritte 4 und 5.  
  
    -   Wenn keine weiteren Data-at-Execution-Parameter vorhanden sind, ist der Prozess abgeschlossen. Wenn die Anweisung erfolgreich ausgeführt wurde, **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO; Fehler bei der Ausführung gibt, wird SQL_ERROR zurückgegeben. An diesem Punkt **SQLParamData** können alle SQLSTATE, die von der Funktion zurückgegeben werden kann, die verwendet wird, zum Ausführen der Anweisung zurückgeben (**SQLExecDirect** oder **SQLExecute**).  
  
         Ausgabewerte für alle Eingabe-/Ausgabe- oder Ausgabe-Parameter sind verfügbar, in der \* *ParameterValuePtr* und **StrLen_or_IndPtr* puffert, nachdem die Anwendung alle Resultsets abgerufen hat von der Anweisung generiert.  
  
 Aufrufen von **SQLExecute** oder **SQLExecDirect** fügt die Anweisung in einem Zustand SQL_NEED_DATA zurück. Die Anwendung kann jetzt nur aufrufen **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**, oder **SQLPutData** mit der Anweisung oder der *Verbindungshandle* der Anweisung zugeordneten. Wenn sie jede andere Funktion mit der Anweisung oder die Verbindung mit der Anweisung verknüpfte aufgerufen wird, wird die Funktion gibt SQLSTATE HY010 (Sequenzfehler funktionieren). Die Anweisung / / Blätter der SQL_NEED_DATA Zustand über, wenn **SQLParamData** oder **SQLPutData** ein Fehler zurückgegeben, **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, oder die Anweisung abgebrochen.  
  
 Wenn die Anwendung ruft **SQLCancel** während der Treiber noch Daten für die Data-at-Execution-Parameter benötigt, bricht der Treiber anweisungsausführung ab; die Anwendung kann dann aufrufen **SQLExecute** oder  **SQLExecDirect** erneut aus.  
  
## <a name="retrieving-streamed-output-parameters"></a>Abrufen von Ausgabeparametern gestreamte

 Wenn eine Anwendung festlegt *InputOutputType* SQL_PARAM_INPUT_OUTPUT_STREAM oder SQL_PARAM_OUTPUT_STREAM, den Wert des Ausgabeparameters abgerufen werden muss, durch eine oder mehrere Aufrufe von **SQLGetData**. Wenn der Treiber einen Parameterwert gestreamte Ausgabe an die Anwendung zurückgegeben wurde, wird als Reaktion auf einen Aufruf an die folgenden Funktionen SQL_PARAM_DATA_AVAILABLE zurückgegeben: **SQLMoreResults**, **SQLExecute**, und **SQLExecDirect**. Ruft die Anwendung **SQLParamData** um zu bestimmen, welcher Parameterwert verfügbar ist.  
  
 Weitere Informationen über SQL_PARAM_DATA_AVAILABLE und gestreamte Output-Parameter, finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-arrays-of-parameters"></a>Verwenden von Parameterarrays

 Wenn eine Anwendung eine Anweisung mit parametermarkierungen auf und übergibt ein Array von Parametern vorbereitet, gibt es zwei Möglichkeiten, die diese ausgeführt werden kann. Eine Möglichkeit ist der Treiber die Array-Verarbeitungsfunktionen des Back-End abhängen, in dem Fall die gesamte Anweisung mit dem Array der Parameter als eine unteilbare Einheit behandelt wird. Oracle ist ein Beispiel für eine Datenquelle, die Array-Verarbeitungsfunktionen unterstützt. Eine weitere Möglichkeit zum Implementieren dieses Feature ist für den Treiber zum Generieren eines Batches von SQL-Anweisungen, eine SQL-Anweisung für einen Satz von Parametern im Parameterarray, und führen Sie den Batch. Arrays von Parametern können nicht verwendet werden, mit einem **UPDATE WHERE CURRENT OF** Anweisung.  
  
 Wenn ein Array von Parametern verarbeitet wird, wird individuellen Ergebnis legt/Zeilenanzahl (eine für jeden Parametersatz) können verfügbar sein, oder legt/Zeilen Ergebnisanzahl können in einem Rollup. Die SQL_PARAM_ARRAY_ROW_COUNTS option **SQLGetInfo** gibt an, ob die Zeilenanzahl für einen Satz von Parametern (SQL_PARC_BATCH) verfügbar sind oder nur eine Zeile die Anzahl ist verfügbar (SQL_PARC_NO_BATCH).  
  
 Die SQL_PARAM_ARRAY_SELECTS option **SQLGetInfo** angibt, ob ein Resultset für einen Satz von Parametern (SQL_PAS_BATCH) verfügbar ist oder nur ein Resultset ist verfügbar (SQL_PAS_NO_BATCH). Wenn eine Ergebnis generiert Set-Anweisung als ein Array von Parametern ausgeführt wird durch der Treiber nicht möglich ist, gibt SQL_PARAM_ARRAY_SELECTS SQL_PAS_NO_SELECT zurück.  
  
 Weitere Informationen finden Sie unter [SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 Zur Unterstützung von Parameterarrays das verweist SQL_ATTR_PARAMSET_SIZE-Anweisungsattribut festgelegt, um die Anzahl der Werte für jeden Parameter anzugeben. Wenn das Feld größer als 1 ist, müssen die Felder SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR APD auf Arrays verweisen. Die Kardinalität jedes Arrays ist gleich dem Wert des verweist SQL_ATTR_PARAMSET_SIZE.  
  
 Das Feld SQL_DESC_ROWS_PROCESSED_PTR APD verweist auf einen Puffer, der die Anzahl von Parametersätzen, die verarbeitet wurden Fehler einschließlich. Als ein Satz von Parametern verarbeitet wird, speichert der Treiber einen neuen Wert in den Puffer. Keine Anzahl wird zurückgegeben, wenn dies ein null-Zeiger ist. Wenn Arrays von Parametern verwendet werden, wird der Wert, der auf das Feld SQL_DESC_ROWS_PROCESSED_PTR APD zeigt aufgefüllt, selbst wenn von der Einstellung Funktion SQL_ERROR zurückgegeben wird. Wird SQL_NEED_DATA zurückgegeben, ist der Wert, der auf das Feld SQL_DESC_ROWS_PROCESSED_PTR APD zeigt auf den Satz der Parameter festgelegt, die verarbeitet wird.  
  
 Was geschieht, wenn ein Array der Parameter gebunden ist und ein **UPDATE WHERE CURRENT OF** -Anweisung ausgeführt wird, wird durch Treiber definiert.  
  
## <a name="column-wise-parameter-binding"></a>Spaltenweiser Parameterbindung

 In spaltenbezogene Bindungen bindet die Anwendung separaten Parameter und den Längenindikator/Arrays an jeden Parameter an.  
  
 Um spaltenbezogene Bindungen verwenden zu können, wird die Anwendung zuerst das SQL_ATTR_PARAM_BIND_TYPE-Anweisungsattribut auf SQL_PARAM_BIND_BY_COLUMN. (Dies ist die Standardeinstellung.) Für jede Spalte gebunden werden soll führt die Anwendung die folgenden Schritte aus:  
  
1.  Ordnet ein Array der Parameter-Puffer.  
  
2.  Ordnet ein Array von Längenindikator/Puffern.  
  
    > [!NOTE]  
    >  Wenn die Anwendung direkt auf Deskriptoren schreibt, wenn spaltenbezogene Bindungen verwendet wird, können die separate Arrays für Länge und Indikator verwendet werden.  
  
3.  Aufrufe **SQLBindParameter** mit den folgenden Argumenten:  
  
    -   *ValueType* ist der C-Typ, der ein einzelnes Element in der Parameterpufferarray.  
  
    -   *ParameterType* ist der SQL-Typ des Parameters.  
  
    -   *ParameterValuePtr* ist die Adresse des Puffers Parameterarrays.  
  
    -   *BufferLength* ist die Größe eines einzelnen Elements im Parameterarray Puffer. Die *Pufferlänge* Argument wird ignoriert, wenn die Daten fester Länge sind.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des Längenindikator/Arrays.  
  
 Weitere Informationen, wie diese Informationen verwendet werden finden Sie unter "ParameterValuePtr Argument" in "Kommentare" unten in diesem Abschnitt. Weitere Informationen zu spaltenbezogene Bindung von Parametern, finden Sie unter [Arrays Bindungsparameter](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md).  
  
## <a name="row-wise-parameter-binding"></a>Parameterbindung

 Die zeilenweise Bindung definiert die Anwendung eine Struktur, die enthält der Parameter und den Längenindikator/Puffer für jeden Parameter gebunden werden soll.  
  
 Um die zeilenweise Bindung zu verwenden, führt die Anwendung die folgenden Schritte aus:  
  
1.  Definiert eine Struktur zum Speichern von eines einzigen Satz von Parametern (z. B. sowohl Parameter als auch Längenindikator/Puffer) und ordnet ein Array dieser Strukturen.  
  
    > [!NOTE]  
    >  Wenn die Anwendung direkt auf Deskriptoren schreibt, wenn die zeilenweise Bindung verwendet wird, können separate Felder für Länge und Indikator verwendet werden.  
  
2.  Legt das Anweisungsattribut SQL_ATTR_PARAM_BIND_TYPE fest, auf die Größe der Struktur, die einen einzelnen Satz von Parametern enthält, oder auf die Größe einer Instanz eines Puffers, in dem der Parameter gebunden werden. Die Länge muss Speicherplatz für alle gebundenen Parameter, und möglicherweise vorhandene Auffüllzeichen der Struktur bzw. des Puffers, um sicherzustellen, dass bei der die Adresse des gebundenen Parameter mit der angegebenen Länge erhöht wird, wird das Ergebnis an den Anfang denselben Parameter im zeigen Sie enthalten die nächste Zeile. Bei Verwendung der *"sizeof"* -Operator in ANSI C, wird dieses Verhalten garantiert.  
  
3.  Aufrufe **SQLBindParameter** mit den folgenden Argumenten für jeden Parameter gebunden werden soll:  
  
    -   *ValueType* ist der Typ des Members Puffer Parameter an die Spalte gebunden werden.  
  
    -   *ParameterType* ist der SQL-Typ des Parameters.  
  
    -   *ParameterValuePtr* ist die Adresse des Elements Puffer Parameter in das erste Arrayelement.  
  
    -   *BufferLength* ist die Größe des Puffers Parameter-Elements.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des Elements Längenindikator/gebunden werden soll.  
  
 Weitere Informationen, wie diese Informationen verwendet werden, finden Sie unter "*ParameterValuePtr* Argument" weiter unten in diesem Abschnitt. Weitere Informationen über die zeilenweise Bindung von Parametern finden Sie unter den [Arrays Bindungsparameter](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md).  
  
## <a name="error-information"></a>Fehlerinformationen

 Wenn ein Treiber nicht Parameterarrays als Batches implementiert werden (die Option SQL_PARAM_ARRAY_ROW_COUNTS entspricht SQL_PARC_NO_BATCH), werden Fehler behandelt, als ob eine Anweisung ausgeführt wurden. Wenn der Treiber Parameterarrays als Batches implementiert, kann eine Anwendung das Headerfeld SQL_DESC_ARRAY_STATUS_PTR IPD verwenden, um zu bestimmen, welche Parameter, der eine SQL-Anweisung oder die Parameter in ein Array von Parametern verursacht  **SQLExecDirect** oder **SQLExecute** einen Fehler zurückgibt. Dieses Feld enthält Statusinformationen für jede Zeile von Parameterwerten. Wenn das Feld gibt an, dass ein Fehler aufgetreten ist, werden Felder in der Diagnosedaten-Struktur der Zeilen- und Parameter-Nummer des Parameters an, die nicht. Die Anzahl der Elemente im Array wird durch das Headerfeld für SQL_DESC_ARRAY_SIZE im APD, definiert werden, die durch das verweist SQL_ATTR_PARAMSET_SIZE-Anweisungsattribut festgelegt werden kann.  
  
> [!NOTE]  
>  Das SQL_DESC_ARRAY_STATUS_PTR-Headerfeld in APD wird verwendet, um Parameter zu ignorieren. Weitere Informationen zu Parameter werden ignoriert finden Sie im nächsten Abschnitt, "Einen Satz von Parametern wird ignoriert."  
  
 Wenn **SQLExecute** oder **SQLExecDirect** gibt SQL_ERROR zurück, die Elemente im Array verweist das SQL_DESC_ARRAY_STATUS_PTR-Feld in IPD SQL_PARAM_ERROR, SQL_PARAM_SUCCESS, SQL_ enthält PARAM_SUCCESS_WITH_INFO, SQL_PARAM_UNUSED oder SQL_PARAM_DIAG_UNAVAILABLE.  
  
 Für jedes Element im Array enthält die Diagnosedaten-Struktur eine oder mehrere Statusdatensätze. Die SQL_DIAG_ROW_NUMBER-Feld der Struktur gibt an, die Zeilennummer der Parameterwerte, die den Fehler verursacht hat. Wenn es möglich ist, des entsprechenden Parameters in einer Zeile von Parametern zu ermitteln, die den Fehler verursacht hat, wird die Anzahl der Parameter in das Feld "SQL_DIAG_COLUMN_NUMBER" eingegeben werden.  
  
 SQL_PARAM_UNUSED eingegeben, wenn ein Parameter nicht verwendet wurde, da in einem früheren-Parameter ist ein Fehler aufgetreten, die erzwungene **SQLExecute** oder **SQLExecDirect** zum abzubrechen. Z. B. wenn 50 Parameter vorhanden sind und ein Fehler beim Ausführen des Fortieth Satz von Parametern, die verursacht **SQLExecute** oder **SQLExecDirect** abbricht, und klicken Sie dann im SQL_PARAM_UNUSED eingegeben wird, die Statusarray für Parameter 41 bis 50.  
  
 SQL_PARAM_DIAG_UNAVAILABLE eingegeben, wenn der Treiber von Parameterarrays als monolithische Einheit behandelt, damit sie diese Ebene der einzelnen Parameter mit Fehlerinformationen nicht generiert.  
  
 Einige Fehler bei der Verarbeitung von einem einzigen Satz von Parametern dazu führen, dass die Verarbeitung der nachfolgenden Sätze von Parametern im Array zu beenden. Andere Fehler wirken sich nicht auf die Verarbeitung der nachfolgenden Parameter aus. Welche Fehler Verarbeitung angehalten werden, werden die Treiber definiert. Wenn die Verarbeitung wird nicht beendet, alle Parameter im Array werden verarbeitet, aufgrund des Fehlers SQL_SUCCESS_WITH_INFO zurückgegeben und der Puffer von SQL_ATTR_PARAMS_PROCESSED_PTR definiert und der maximalen Anzahl von Parametersätzen verarbeitet festgelegt ist (gemäß der SQL_ATTR_PARAMSET_SIZE Anweisungsattribut), die enthält Fehler.  
  
> [!CAUTION]  
>  ODBC-Verhalten tritt ein Fehler bei der Verarbeitung der ein Array von Parametern ist in ODBC 3. unterschiedlich. *x* als ODBC 2. vorlag. *X*. In ODBC 2. *x*, der Funktion zurückgegebene endete, SQL_ERROR zurück, und verarbeiten. Der Puffer auf die von der *Pirow* Argument **SQLParamOptions** enthalten die Anzahl der Fehlerzeile. In ODBC 3. *x*, SQL_SUCCESS_WITH_INFO zurückgegeben. die Funktion und Verarbeiten von Mai entweder beendet oder fortgesetzt werden. Wenn es weiterhin besteht, wird von SQL_ATTR_PARAMS_PROCESSED_PTR angegebene Puffer festgelegt werden, auf den Wert aller Parameter verarbeitet, einschließlich derjenigen, die zu einem Fehler geführt haben. Diese Änderung im Verhalten kann für vorhandene Anwendungen beeinträchtigen.  
  
 Wenn **SQLExecute** oder **SQLExecDirect** gibt vor dem Abschluss der Verarbeitung alle Parametersätze in einem Parameterarray, z. B. wenn SQL_ERROR oder SQL_NEED_DATA zurückgegeben wird, enthält die Statusarray der Status für diesen Parameter, die bereits verarbeitet wurden. Der Speicherort, verweist das SQL_DESC_ROWS_PROCESSED_PTR-Feld in IPD enthält die Nummer der Zeile im Parameterarray, das SQL_ERROR oder SQL_NEED_DATA zurückgegeben. Fehlercode: verursacht hat. Wenn ein Array von Parametern an eine SELECT-Anweisung gesendet wird, ist die Verfügbarkeit von Array-Statuswerte mit dem treiberdefinierten; Sie möglicherweise zur Verfügung, nachdem die Anweisung ausgeführt wurde oder als Ergebnis legt abgerufen werden.  
  
## <a name="ignoring-a-set-of-parameters"></a>Eine Reihe von Parametern wird ignoriert.

 Das Feld SQL_DESC_ARRAY_STATUS_PTR APD (wie durch das SQL_ATTR_PARAM_STATUS_PTR-Anweisungsattribut festgelegt) kann verwendet werden, um anzugeben, dass eine Reihe von gebundenen Parametern in einer SQL­Anweisung ignoriert werden sollen. Damit den Treiber, um eine oder mehrere Sätze von Parametern während der Ausführung ignorieren durchführt, sollte eine Anwendung die folgenden Schritte ausführen:  
  
1.  Rufen Sie **SQLSetDescField** festzulegende das Headerfeld SQL_DESC_ARRAY_STATUS_PTR APD um auf ein Array von Werten der SQLUSMALLINT enthält Statusinformationen zu verweisen. Dieses Feld kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit einer *Attribut* von SQL_ATTR_PARAM_OPERATION_PTR, der eine Anwendung das Feld festgelegt werden, ohne ein Deskriptorhandle abrufen kann.  
  
2.  Legen Sie jedes Element des Arrays durch das Feld SQL_DESC_ARRAY_STATUS_PTR APD auf einen von zwei Werten definiert:  
  
    -   SQL_PARAM_IGNORE, um anzugeben, dass die Zeile aus der Ausführung der Anweisung ausgeschlossen ist.  
  
    -   SQL_PARAM_PROCEED, um anzugeben, dass die Zeile in der Ausführung der Anweisung enthalten ist.  
  
3.  Rufen Sie **SQLExecDirect** oder **SQLExecute** zur Ausführung der vorbereiteten Anweisung.  
  
 Die folgenden Regeln gelten für das Array, das durch das Feld SQL_DESC_ARRAY_STATUS_PTR APD definiert:  
  
-   Der Zeiger wird festgelegt. standardmäßig auf null.  
  
-   Wenn der Zeiger null ist, werden alle Sätze von Parametern verwendet, als ob alle Elemente auf SQL_ROW_PROCEED festgelegt wurden.  
  
-   Festlegen eines Elements auf SQL_PARAM_PROCEED garantiert nicht, dass der Vorgang dieses bestimmten Satz von Parametern verwendet.  
  
-   SQL_PARAM_PROCEED ist als 0 in der Headerdatei definiert.  
  
 Eine Anwendung kann die SQL_DESC_ARRAY_STATUS_PTR Feld im APD auf dasselbe Array als verweisen, auf das durch das SQL_DESC_ARRAY_STATUS_PTR in IRD festgelegt. Dies ist nützlich beim Binden von Parametern an die Daten der Zeile. Parameter können dann nach dem Status der Daten aus der Zeile ignoriert werden. Zusätzlich zu SQL_PARAM_IGNORE dazu führen, dass die folgenden Codes für einen Parameter in einer SQL­Anweisung ignoriert werden soll: SQL_ROW_DELETED, SQL_ROW_UPDATED und SQL_ROW_ERROR. Zusätzlich zu SQL_PARAM_PROCEED dazu führen, dass die folgenden Codes für eine SQL-Anweisung, um den Vorgang fortzusetzen: SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO, and SQL_ROW_ADDED.  
  
## <a name="rebinding-parameters"></a>Erneutes Binden von Datenquellenverweisen Parameter

 Eine Anwendung kann eine der beiden Vorgänge so ändern Sie eine Bindung durchführen:  
  
-   Rufen Sie **SQLBindParameter** an eine neue Bindung für eine Spalte, die bereits gebunden ist. Der Treiber überschreibt die alte Bindung mit den neuen Wert.  
  
-   Geben Sie einen Offset, um die Pufferadresse hinzugefügt werden, die durch den Aufruf Bindung angegeben wurde **SQLBindParameter**. Weitere Informationen finden Sie im nächsten Abschnitt, "Neubindung mit Offsets".  
  
## <a name="rebinding-with-offsets"></a>Das erneute Binden mit Offsets

 Das erneute Binden der Parameter ist besonders nützlich, wenn eine Anwendung ein Puffer Bereich Setup verfügt, die viele Parameter, aber ein Aufruf enthalten, können **SQLExecDirect** oder **SQLExecute** nur einige der Parameter verwendet. Der verbleibende Raum im Pufferbereich kann für die nächste Gruppe von Parametern verwendet werden, durch Ändern der vorhandenen Bindung durch einen Offset.  
  
 Das SQL_DESC_BIND_OFFSET_PTR-Headerfeld in APD verweist auf den Offset für die Bindung. Wenn das Feld nicht Null ist, der Treiber dereferenziert den Zeiger und, wenn keiner der Werte in den Feldern SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR ein null-Zeiger ist, fügt den verweislosen Wert auf diese Felder im Deskriptor Datensätze zum Zeitpunkt der Ausführung. Die neuen Zeigerwerte werden verwendet, wenn die SQL-Anweisungen ausgeführt werden. Der Offset bleibt gültig, nachdem das erneute Binden. Da SQL_DESC_BIND_OFFSET_PTR ein Zeiger auf den Offset anstatt der Offset selbst ist, eine Anwendung kann den Offset direkt ändern, ohne Aufruf [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) oder [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md) auf Ändern Sie das Deskriptorfeld. Der Zeiger wird festgelegt. standardmäßig auf null. Das Feld SQL_DESC_BIND_OFFSET_PTR der ARD kann festgelegt werden, durch einen Aufruf von [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) oder durch einen Aufruf von [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)mit eine *fAttribute* von SQL_ATTR_PARAM_BIND_ OFFSET_PTR.  
  
 Der Offset für die Bindung wird immer direkt auf die Werte in den Feldern SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR hinzugefügt. Wenn der Offset in einen anderen Wert geändert wird, ist der neue Wert direkt auf den Wert in jedem Deskriptorfeld weiterhin hinzugefügt. Der neue Offset ist die Summe aus der Wert des Felds und alle früheren Offsets nicht hinzugefügt.  
  
## <a name="descriptors"></a>Deskriptoren

 Wie ein Parameter gebunden ist, wird durch die Felder mit den APDs und Identitätsanbieter bestimmt. Die Argumente in **SQLBindParameter** werden verwendet, um diese deskriptorfelder festgelegt. Die Felder können auch festgelegt werden, indem die **SQLSetDescField** funktioniert, obwohl **SQLBindParameter** ist effizienter, die verwendet werden, da die Anwendung nicht unbedingt ein Deskriptorhandle zum Aufrufen von erhalten**SQLBindParameter**.  
  
> [!CAUTION]  
>  Aufrufen von **SQLBindParameter** für eine Anweisung auf andere Anweisungen auswirken kann. Dies tritt auf, wenn es sich bei der der Anweisung zugeordneten ARD explizit zugeordnet ist, und auch andere Anweisungen zugeordnet ist. Da **SQLBindParameter** ändert die Felder APD, gelten die Änderungen für alle Anweisungen, die der dieser Deskriptor zugeordnet ist. Ist dies nicht das erforderliche Verhalten, die Anwendung sollte Trennen dieser Deskriptor aus den anderen Anweisungen vor **SQLBindParameter**.  
  
 Im Prinzip **SQLBindParameter** führt Sie nacheinander die folgenden Schritte aus:  
  
1.  Aufrufe [SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) um die APD-Handle zu erhalten.  
  
2.  Aufrufe [SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) zum Abrufen APDs SQL_DESC_COUNT-Feld, und wenn der Wert des der *ColumnNumber* Arguments überschreitet den Wert von SQL_DESC_COUNT, Aufrufe **SQLSetDescField**zur Erhöhung des Werts der SQL_DESC_COUNT zu *ColumnNumber*.  
  
3.  Aufrufe [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) mehrere Male auf, um die folgenden Felder der APD Werte zuzuweisen:  
  
    -   Legt die SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE auf den Wert der *ValueType*, mit dem Unterschied, dass wenn *ValueType* ist eine präzise Bezeichner eines Untertyps "DateTime" oder das Intervall, SQL_DESC_TYPE auf SQL_ festgelegt DATETIME oder SQL_INTERVAL, bzw. legt SQL_DESC_CONCISE_TYPE auf die präzise-ID und SQL_DESC_DATETIME_INTERVAL_CODE das entsprechende DateTime ' oder ' Intervall Fehlersubcode.  
  
    -   Legt das SQL_DESC_OCTET_LENGTH-Feld auf den Wert der *Pufferlänge*.  
  
    -   Legt das SQL_DESC_DATA_PTR-Feld auf den Wert der *ParameterValue*.  
  
    -   Legt das SQL_DESC_OCTET_LENGTH_PTR-Feld auf den Wert der *StrLen_or_Ind*.  
  
    -   Wird das Feld "SQL_DESC_INDICATOR_PTR" auch auf den Wert der *StrLen_or_Ind*.  
  
     Die *StrLen_or_Ind* Parameter gibt an, sowohl den Indikator als auch die Länge für den Parameterwert.  
  
4.  Aufrufe [SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) um die IPD-Handle zu erhalten.  
  
5.  Aufrufe [SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) IPD Feld "SQL_DESC_COUNT" abgerufen und, wenn der Wert des der *ColumnNumber* Arguments überschreitet den Wert von SQL_DESC_COUNT, Aufrufe **SQLSetDescField**zur Erhöhung des Werts der SQL_DESC_COUNT zu *ColumnNumber*.  
  
6.  Aufrufe [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) mehrere Male auf, um die folgenden Felder des IPD Werte zuzuweisen:  
  
    -   Legt die SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE auf den Wert der *ParameterType*, mit dem Unterschied, dass wenn *ParameterType* ist eine präzise Bezeichner eines Untertyps "DateTime" oder das Intervall, SQL_DESC_TYPE wird auf SQL_DATETIME oder SQL_INTERVAL setzt sich der SQL_DESC_CONCISE_TYPE, auf dem präzise Bezeichner und legt SQL_DESC_DATETIME_INTERVAL_CODE das entsprechende DateTime ' oder ' Intervall Fehlersubcode.  
  
    -   Legt eine oder mehrere der SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION und SQL_DESC_LENGTH entsprechend *ParameterType*.  
  
    -   Legt SQL_DESC_SCALE auf den Wert der *DecimalDigits*.  
  
 Wenn der Aufruf von **SQLBindParameter** ein Fehler auftritt, der Inhalt der deskriptorfelder, die sie im APD festgelegt haben, würden sind nicht definiert, und das Feld SQL_DESC_COUNT APD bleibt unverändert. Darüber hinaus wird die SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_TYPE-Felder des entsprechenden Datensatzes in IPD sind nicht definiert, und das SQL_DESC_COUNT-Feld des IPD bleibt unverändert.  
  
## <a name="conversion-of-calls-to-and-from-sqlsetparam"></a>Konvertierung von Aufrufe in und aus SQLSetParam

 Wenn eine ODBC-1.0-Anwendung aufruft **SQLSetParam** in einer ODBC 3. *X* -Treiber verwenden, die ODBC 3. *X* -Treiber-Manager wird den Aufruf zugeordnet, wie in der folgenden Tabelle gezeigt.  
  
|Aufrufen von ODBC-1.0-Anwendung|Rufen Sie mit ODBC 3. *x* Treiber|  
|----------------------------------|-------------------------------|  
|SQLSetParam(      StatementHandle,      ParameterNumber,      ValueType,      ParameterType,      LengthPrecision,      ParameterScale,      ParameterValuePtr,      StrLen_or_IndPtr);|SQLBindParameter (StatementHandle "," ParameterNumber "," SQL_PARAM_INPUT_OUTPUT an "," ValueType "," ParameterType, *ColumnSize*, *DecimalDigits*, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX,      StrLen_or_IndPtr);|  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel wird eine Anwendung eine SQL-Anweisung zum Einfügen von Daten in die Tabelle ORDERS vorbereitet. Für jeden Parameter in der Anweisung, die Anwendung ruft **SQLBindParameter** zum Angeben der ODBC-C-Datentyp und der SQL-Datentyp des Parameters und einen Puffer auf jeden Parameter zu binden. Für jede Zeile der Daten, die Anwendung Datenwerte auf jeden Parameter an und ruft weist **SQLExecute** zum Ausführen der Anweisung.  
  
 Im folgende Beispiel wird davon ausgegangen, dass Sie eine ODBC-Datenquelle verfügen, auf dem Computer namens Northwind herzustellen, der die Northwind-Datenbank zugeordnet ist.  
  
 Weitere Codebeispiele, finden Sie unter [SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLProcedures-Funktion](../../../odbc/reference/syntax/sqlprocedures-function.md), [SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md), und [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
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

 Im folgenden Beispiel führt eine Anwendung eine gespeicherte SQL Server-Prozedur, die mit einem benannten Parameter.  
  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben von Informationen über einen Parameter in einer Anweisung|[SQLDescribeParam-Funktion](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Freigeben von Parameterpuffern für die Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Zurückgeben der Anzahl der Parameter|[SQLNumParams-Funktion](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|Den nächsten Parameter zum Senden von Daten für die Rückgabe|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Angeben mehrerer Parameterwerte|[SQLParamOptions-Funktion](../../../odbc/reference/syntax/sqlparamoptions-function.md)|  
|Senden von Daten von Parametern zum Zeitpunkt der Ausführung|[SQLPutData-Funktion](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Siehe auch

 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
