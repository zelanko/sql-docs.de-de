---
title: SQLBindCol-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBindCol
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBindCol
helpviewer_keywords:
- SQLBindCol function [ODBC]
ms.assetid: 41a37655-84cd-423f-9daa-e0b47b88dc54
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17b907be3e2641fe1dcbbb8fbd96586132e054ca
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65538065"
---
# <a name="sqlbindcol-function"></a>SQLBindCol-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLBindCol** Anwendung von Datenpuffern für Spalten im Resultset bindet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLBindCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *ColumnNumber*  
 [Eingabe] Anzahl des Ergebnisses legen Spalte binden. Spalten werden in der wachsenden Reihenfolge der Spalten, die beginnend ab 0 (null), in denen die Lesezeichenspalte ist die Spalte 0 nummeriert. Wenn das Lesezeichen nicht verwendet werden – d. h. das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF - festgelegt ist dann beginnen Spaltennummern bei 1.  
  
 *TargetType*  
 [Eingabe] Der Bezeichner für die C-Datentyp, der die \* *TargetValuePtr* Puffer. Wenn sie ist Abrufen von Daten aus der Datenquelle mit **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, oder **SQLSetPos**, Treiber konvertiert die Daten in diesen Typ; Wenn er Daten sendet, an die Datenquelle mit **SQLBulkOperations** oder **SQLSetPos**, konvertiert der Treiber die Daten von diesem Typ. Eine Liste der gültigen C-Datentypen und Typ-IDs, finden Sie unter den [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) Abschnitt in Anhang D: Datentypen.  
  
 Wenn die *TargetType* Argument ist ein Intervall Datentyp für die standardmäßige Intervall führende Genauigkeit (2) und die standardmäßige Intervall Sekunden Genauigkeit (6), wie in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION und SQL_DESC_PRECISION des festgelegt die ARD sind verwendet bzw. für die Daten. Wenn die *TargetType* Argument SQL_C_NUMERIC, die standardmäßige Genauigkeit von (treiberdefinierten) und Standard skalieren (0), wie in die Felder der ARD SQL_DESC_PRECISION und SQL_DESC_SCALE festgelegt, für die Daten verwendet werden. Wenn alle Standardwerte für die Genauigkeit oder Dezimalstellenanzahl nicht geeignet ist, die Anwendung sollte explizit festlegen der entsprechenden Deskriptorfeld durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**.  
  
 Sie können auch einen erweiterte C-Datentyp angeben. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *TargetValuePtr*  
 [Verzögerte Eingabe/Ausgabe] Zeiger auf den Datenpuffer, an die Spalte binden. **SQLFetch** und **SQLFetchScroll** Daten in diesen Puffer zurück. **SQLBulkOperations** gibt Daten zurück, in diesem Puffer beim *Vorgang* SQL_FETCH_BY_BOOKMARK; ist Daten aus dieser abgerufen beim Puffern *Vorgang* SQL_ADD oder SQL_UPDATE_BY_BOOKMARK ist. **SQLSetPos** gibt Daten zurück, in diesem Puffer beim *Vorgang* SQL_REFRESH; ist Daten aus dieser abgerufen beim Puffern *Vorgang* SQL_UPDATE ist.  
  
 Wenn *TargetValuePtr* ist ein null-Zeiger der Treiber hebt die Bindung des Datenpuffer für die Spalte. Eine Anwendung kann alle Spalten Bindung, durch den Aufruf **SQLFreeStmt** mit der Option SQL_UNBIND. Eine Anwendung kann den Datenpuffer für eine Spalte aufheben der Bindung jedoch noch ein Längen-/Indikatorpuffer, die für die Spalte gebunden wird, wenn die *TargetValuePtr* Argument im Aufruf von **SQLBindCol** ein null-Zeiger ist, aber die *StrLen_or_IndPtr* Argument ist ein gültiger Wert.  
  
 *BufferLength*  
 [Eingabe] Länge der **TargetValuePtr* Puffers in Byte.  
  
 Der Treiber verwendet *Pufferlänge* zu schreiben, die nach dem Ende zu vermeiden der \* *TargetValuePtr* gepuffert werden, wenn Daten mit variabler Länge, wie z. B. Zeichen- oder Binärdaten zurückgegeben. Beachten Sie, dass der Treiber die Null-Terminierungszeichen zählt, bei der Rückgabe Zeichendaten \* *TargetValuePtr*. **TargetValuePtr* Speicherplatz verfügen muss, der aus diesem Grund für die Null-Terminierungszeichen oder der Treiber die Daten abgeschnitten werden.  
  
 Beenden der Treiber Daten fester Länge, z. B. eine ganze Zahl oder einen Datumsstruktur, ignoriert der Treiber die *Pufferlänge* und nimmt an, dass der Puffer groß genug zum Speichern der Daten. Daher es ist wichtig für die Anwendung einen ausreichenden Puffer für Daten fester Länge zugewiesen werden, oder der Treiber wird nach dem Ende des Puffers geschrieben.  
  
 **SQLBindCol** SQLSTATE HY090 zurückgegeben (ungültige Zeichenfolgen- oder Pufferlänge.) Wenn *Pufferlänge* ist kleiner als 0, aber nicht, wenn *Pufferlänge* ist 0. Jedoch wenn *TargetType* gibt an, einen Zeichentyp handelt, eine Anwendung sollte nicht festgelegt. *Pufferlänge* 0 ist, da CLI von ISO-kompatible Treiber SQLSTATE HY090 zurückgeben (ungültige Zeichenfolgen- oder Pufferlänge), Fall.  
  
 *StrLen_or_IndPtr*  
 [Verzögerte Eingabe/Ausgabe] Zeiger auf den Längen-/Indikatorpuffers auf die Spalte gebunden. **SQLFetch** und **SQLFetchScroll** Geben Sie einen Wert zurück, in diesem Puffer. **SQLBulkOperations** Ruft einen Wert aus diesem Puffer beim *Vorgang* ist SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_DELETE_BY_BOOKMARK. **SQLBulkOperations** gibt einen Wert in diesem Puffer beim *Vorgang* SQL_FETCH_BY_BOOKMARK ist. **SQLSetPos** gibt einen Wert in diesem Puffer beim *Vorgang* ist SQL_REFRESH; er ruft einen Wert ab, aus dieser gepuffert, wenn *Vorgang* SQL_UPDATE ist.  
  
 **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, und **SQLSetPos** können die folgenden Werte in den Längen-/Indikatorpuffer zurück:  
  
-   Die Länge der zurückzugebenden verfügbaren Daten  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Die Anwendung kann die folgenden Werte in den Längen-/Indikatorpuffer für die Verwendung mit einfügen **SQLBulkOperations** oder **SQLSetPos**:  
  
-   Die Länge der gesendeten Daten  
  
-   SQL_NTS  
  
-   SQL_NULL_DATA  
  
-   SQL_DATA_AT_EXEC  
  
-   Das Ergebnis der SQL_LEN_DATA_AT_EXEC-Makro  
  
-   SQL_COLUMN_IGNORE  
  
 Wenn den Indikator und der Puffer der Länge verschiedenen Puffern sind, kann die Indikatorpuffers nur SQL_NULL_DATA zurück, während der Länge Puffer alle anderen Werte zurückgeben kann.  
  
 Weitere Informationen finden Sie unter [SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md), [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md), und [mit Längenindikator/Werten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Wenn *StrLen_or_IndPtr* ist ein null-Zeiger, keine Länge bzw. der Indikatorwert-Wert verwendet wird. Dies ist ein Fehler beim Abrufen von Daten und die Daten NULL ist.  
  
 Finden Sie unter [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLBindCol** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLBindCol** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|(DM) die *ColumnNumber* Argument wurde 0 (null) und die *TargetType* Argument war kein SQL_C_BOOKMARK oder SQL_C_VARBOOKMARK.|  
|07009|Ungültiger Deskriptorindex|Der angegebene Wert für das Argument *ColumnNumber* überschreitet die maximale Anzahl der Spalten im Resultset.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY003|Ungültiger Anwendungspuffertyp|Das Argument *TargetType* wurde weder SQL_C_DEFAULT als auch ein gültiger Datentyp.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn **SQLBindCol** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert für das Argument angegebene *Pufferlänge* war kleiner als 0.<br /><br /> (DM) der Treiber wurde eine ODBC-2. *x* -Treiber die *ColumnNumber* -Argument wurde auf 0 und dem Wert des Arguments festgelegt *Pufferlänge* war nicht gleich 4.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Treiber oder die Datenquelle unterstützt nicht die Konvertierung angegeben wird, durch die Kombination der *TargetType* Argument und der Treiber-spezifische SQL-Datentyp der entsprechenden Spalte.<br /><br /> Das Argument *ColumnNumber* wurde 0 und der Treiber die Lesezeichen nicht unterstützt.<br /><br /> Der Treiber unterstützt nur ODBC 2. *x* und das Argument *TargetType* war eines der folgenden:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> und keines der Intervalldatentypen C im [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen.<br /><br /> Der Treiber unterstützt nur die ODBC-Versionen vor, und das Argument zum Preis von 3,50 *TargetType* SQL_C_GUID wurde.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 **SQLBindCol** wird verwendet, um zu verknüpfen, oder *zu binden,* Spalten im Resultset von Datenpuffern und Längenindikator/Puffer in der Anwendung festgelegt. Wenn die Anwendung ruft **SQLFetch**, **SQLFetchScroll**, oder **SQLSetPos** zum Abrufen von Daten, gibt der Treiber die Daten für die gebundenen Spalten in den angegebenen Puffern; Weitere Informationen finden Sie unter [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md). Wenn die Anwendung ruft **SQLBulkOperations** zum Aktualisieren oder Einfügen einer Zeile oder **SQLSetPos** um eine Zeile zu aktualisieren, ruft der Treiber die Daten für die gebundenen Spalten aus den angegebenen Puffern; Weitere Informationen , finden Sie unter [SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md) oder [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md). Weitere Informationen zur Bindung finden Sie unter [Abrufen von Ergebnissen (Standard)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 Beachten Sie, dass Spalten nicht gebunden werden soll, um Daten daraus abzurufen. Eine Anwendung kann auch aufrufen **SQLGetData** zum Abrufen von Daten aus Spalten. Obwohl es möglich, einige Spalten in einer Zeile und den Aufruf zu binden ist **SQLGetData** für andere, ist dies der unterliegen einigen Einschränkungen. Weitere Informationen finden Sie unter [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
## <a name="binding-unbinding-and-rebinding-columns"></a>Bindung, die die Bindung und erneutes Binden von Datenquellenverweisen Spalten  
 Eine Spalte kann gebunden, aufgehoben oder jederzeit, auch nachdem die Daten aus dem Resultset abgerufen wurde erneut gebunden werden. Die neue Bindung wird wirksam, das nächste Mal, das eine Funktion, die diese Bindungen verwendet aufgerufen wird. Nehmen wir beispielsweise an, die eine Anwendung bindet die Spalten in einem Resultset und Aufrufe **SQLFetch**. Der Treiber zurückgegeben die Daten in den Puffern mit gebundenen. Nehmen wir nun an die Anwendung bindet die Spalten, die einen anderen Satz von Puffern. Der Treiber ist die Daten für den gerade abgerufenen Zeile nicht in die neu gebundenen Puffer abgelegt werden. Stattdessen erst **SQLFetch** erneut aufgerufen, und klicken Sie dann die Daten für die nächste Zeile platziert, in dem neu gebundenen Puffer.  
  
> [!NOTE]  
>  Das Anweisungsattribut SQL_ATTR_USE_BOOKMARKS sollte immer vor dem binden eine Spalte für Spalte auf 0 festgelegt werden. Dies ist nicht erforderlich, jedoch wird dringend empfohlen.  
  
## <a name="binding-columns"></a>Binden von Spalten  
 Um eine Spalte binden, eine Anwendung ruft **SQLBindCol** und übergibt die Spaltennummer, Typ, Adresse und Länge eines Datenpuffers mit und die Adresse des ein Längen-/Indikatorpuffer. Informationen, wie diese Adressen verwendet werden finden Sie unter "Pufferadressen," weiter unten in diesem Abschnitt. Weitere Informationen zum Binden von Spalten finden Sie unter [mithilfe von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Die Verwendung dieser Puffer wird verzögert, d. h. die Anwendung gebunden, die sie in **SQLBindCol** , aber der Treiber greift auf diese in Funktionen verwendet werden – d. h. **SQLBulkOperations**, **SQLFetch**,  **SQLFetchScroll**, oder **SQLSetPos**. Es ist Aufgabe der Anwendung, um sicherzustellen, dass der angegebene Zeiger im **SQLBindCol** bleiben gültig, solange die Bindung gültig ist. Wenn die Anwendung diese Zeiger ungültig werden kann: z. B. Es gibt einen Puffer - frei, und ruft dann eine Funktion, die erwartet, dass sie gültig ist, sind die folgen nicht definiert. Weitere Informationen finden Sie unter [verzögerte Puffer](../../../odbc/reference/develop-app/deferred-buffers.md).  
  
 Die Bindung bleibt wirksam, bis er durch eine neue Bindung ersetzt, die Spalte aufgehoben wird oder die Anweisung wird freigegeben.  
  
## <a name="unbinding-columns"></a>Die Bindung von Spalten  
 Zum Aufheben der Bindung einer einzelnen Spalteninhalts, eine Anwendung ruft **SQLBindCol** mit *ColumnNumber* legen die Anzahl der betroffenen Spalte und *TargetValuePtr* auf einen null-Zeiger festgelegt. Wenn *ColumnNumber* bezieht sich auf einer ungebundenen Spalte **SQLBindCol** weiterhin gibt SQL_SUCCESS zurück.  
  
 Zum Aufheben der Bindung aller Spalten, die eine Anwendung ruft **SQLFreeStmt** mit *fOption* auf SQL_UNBIND gesetzt ist. Dies kann auch durch Festlegen des Felds SQL_DESC_COUNT aus, der die ARD 0 (null) erfolgen.  
  
## <a name="rebinding-columns"></a>Erneutes Binden von Datenquellenverweisen Spalten  
 Eine Anwendung kann eine der beiden Vorgänge so ändern Sie eine Bindung durchführen:  
  
-   Rufen Sie **SQLBindCol** an eine neue Bindung für eine Spalte, die bereits gebunden ist. Der Treiber überschreibt die alte Bindung mit den neuen Wert.  
  
-   Geben Sie einen Offset, um die Pufferadresse hinzugefügt werden, die durch den Aufruf Bindung angegeben wurde **SQLBindCol**. Weitere Informationen finden Sie im nächsten Abschnitt, "Bindung Offsets".  
  
## <a name="binding-offsets"></a>Binden von Offsets  
 Ein Bindung-Offset ist ein Wert, der die Adressen der Daten und Längenindikator/Puffer hinzugefügt wird (gemäß den Angaben in der *TargetValuePtr* und *StrLen_or_IndPtr* Argument), bevor sie dereferenziert werden. Wenn Offsets verwendet werden, die Bindungen sind eine "Vorlage" wie die Anwendung Puffer angeordnet werden, und der Anwendung kann auf unterschiedliche Bereiche des Arbeitsspeichers dieser "Template" verschieben, durch Ändern des Offsets. Da es sich bei der gleiche Offset an jede Adresse in jeder Bindung hinzugefügt wird, müssen die relative Offsets zwischen Puffern für verschiedene Spalten innerhalb jeder Satz von Puffern identisch sein. Dies ist immer "true", wenn die zeilenweise Bindung verwendet wird; die Anwendung muss sorgfältig gestalten die Puffer für diesen auf "true" sein, wenn spaltenbezogene Bindungen verwendet wird.  
  
 Mit einem Offset für die Bindung weist im Grunde dieselbe Wirkung wie das erneute Binden einer Spalte durch den Aufruf **SQLBindCol**. Der Unterschied besteht darin, die einen neuen Aufruf von **SQLBindCol** neue Adressen für den Datenpuffer und Längen-/Indikatorpuffer, gibt an, während mit einem Offset für die Bindung sich nicht auf die Adressen ändert, sondern sie nur einen Offset hinzugefügt. Die Anwendung kann einen neuen Offset angeben, wenn dieser Offset ist immer an die ursprünglich gebundenen Adressen hinzugefügt werden sollen. Insbesondere verwendet der Treiber, wenn der Offset auf 0 festgelegt ist, oder wenn das-Anweisungsattribut auf einen null-Zeiger festgelegt ist, die ursprünglich gebundenen Adressen.  
  
 Um eine Bindung Offset anzugeben, legt die Anwendung das Anweisungsattribut SQL_ATTR_ROW_BIND_OFFSET_PTR an die Adresse eines Puffers SQLINTEGER fest. Bevor die Anwendung eine Funktion, die Bindungen verwendet aufruft, einen Offset in Bytes, die in diesem Puffer eingefügt. Um die Adresse des zu verwendenden Puffers zu bestimmen, fügt der Treiber den Offset in die Adresse in der Bindung. Die Summe der Adresse und den Offset muss eine gültige Adresse sein, aber die Adresse, zu der der Offset addiert wird, keine gültig ist. Weitere Informationen zur Verwendung von Offsets der Bindung finden Sie unter "Pufferadressen," weiter unten in diesem Abschnitt.  
  
## <a name="binding-arrays"></a>Binden von Arrays  
 Wenn die Größe des Rowsets (der Wert des Attributs SQL_ATTR_ROW_ARRAY_SIZE-Anweisung) größer als 1 ist, wird die Anwendung Arrays von Puffern, statt einzelnen Puffer gebunden. Weitere Informationen finden Sie unter [Blockcursor](../../../odbc/reference/develop-app/block-cursors.md).  
  
 Die Anwendung kann auf zwei Arten Arrays gebunden werden:  
  
-   Binden Sie ein Array für jede Spalte ein. Dies wird als bezeichnet *spaltenbezogene Bindungen* , da jede Data-Struktur (Array) Daten für eine einzelne Spalte enthält.  
  
-   Definieren Sie eine Struktur zum Speichern der Daten für eine gesamte Zeile und ein Array dieser Strukturen binden. Dies wird als bezeichnet *zeilenbezogene Bindungen* da jede Data-Struktur, die Daten für eine einzelne Zeile enthält.  
  
 Jedes Array von Puffer muss mindestens so viele Elemente als die Größe des Rowsets aufweisen.  
  
> [!NOTE]  
>  Eine Anwendung muss überprüfen Sie, ob Ausrichtung gültig ist. Weitere Informationen zu Ausrichtung Überlegungen finden Sie unter [Ausrichtung](../../../odbc/reference/develop-app/alignment.md).  
  
## <a name="column-wise-binding"></a>Spaltenbezogenes Binden  
 In spaltenbezogene Bindungen bindet die Anwendung unterschiedliche Daten- und Längenindikator/Arrays für die einzelnen Spalten an.  
  
 Um spaltenbezogene Bindungen verwenden zu können, legt die Anwendung zuerst das Anweisungsattribut SQL_ATTR_ROW_BIND_TYPE auf SQL_BIND_BY_COLUMN ein. (Dies ist die Standardeinstellung.) Für jede Spalte gebunden werden soll führt die Anwendung die folgenden Schritte aus:  
  
1.  Ordnet ein Array der Daten Puffer.  
  
2.  Ordnet ein Array von Längenindikator/Puffern.  
  
    > [!NOTE]  
    >  Wenn die Anwendung direkt auf Deskriptoren schreibt, wenn spaltenbezogene Bindungen verwendet wird, können die separate Arrays für Länge und Indikator verwendet werden.  
  
3.  Aufrufe **SQLBindCol** mit den folgenden Argumenten:  
  
    -   *TargetType* ist der Typ eines einzelnen Elements im Pufferarray Daten.  
  
    -   *TargetValuePtr* ist die Adresse des Pufferarrays Daten.  
  
    -   *BufferLength* ist die Größe eines einzelnen Elements im Pufferarray Daten. Die *Pufferlänge* Argument wird ignoriert, wenn die Daten fester Länge sind.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des Längenindikator/Arrays.  
  
 Weitere Informationen, wie diese Informationen verwendet werden finden Sie unter "Pufferadressen," weiter unten in diesem Abschnitt. Weitere Informationen zu spaltenbezogene Bindungen, finden Sie unter [die spaltenweise Bindung](../../../odbc/reference/develop-app/column-wise-binding.md).  
  
## <a name="row-wise-binding"></a>Zeilenbezogenes Binden  
 Die zeilenweise Bindung definiert die Anwendung eine Struktur, die Daten und Längenindikator/Puffer für jeden zu bindenden Spalte enthält.  
  
 Um die zeilenweise Bindung zu verwenden, führt die Anwendung die folgenden Schritte aus:  
  
1.  Definiert eine Struktur, um eine einzelne Zeile mit Daten (einschließlich der sowohl Daten als auch Längenindikator/Puffer) enthalten, und ordnet ein Array dieser Strukturen.  
  
    > [!NOTE]  
    >  Wenn die Anwendung direkt auf Deskriptoren schreibt, wenn die zeilenweise Bindung verwendet wird, können separate Felder für Länge und Indikator verwendet werden.  
  
2.  Legt das Anweisungsattribut SQL_ATTR_ROW_BIND_TYPE fest, auf die Größe der Struktur, die eine einzelne Zeile mit Daten enthält, oder auf die Größe einer Instanz eines Puffers, in dem die Ergebnisspalten gebunden werden. Die Länge muss Speicherplatz für alle gebundenen Spalten und möglicherweise vorhandene Auffüllzeichen der Struktur bzw. des Puffers, um sicherzustellen, dass bei der die Adresse einer gebundenen Spalte mit der angegebenen Länge erhöht wird, wird das Ergebnis an den Anfang derselben Spalte in der nächsten Zeile zeigen enthalten. Bei Verwendung der *"sizeof"* -Operator in ANSI C, wird dieses Verhalten garantiert.  
  
3.  Aufrufe **SQLBindCol** mit den folgenden Argumenten für jede Spalte gebunden werden soll:  
  
    -   *TargetType* ist der Typ des Datenelements Puffer der Spalte gebunden werden soll.  
  
    -   *TargetValuePtr* ist die Adresse des Datenmembers Puffer in das erste Arrayelement.  
  
    -   *BufferLength* ist die Größe des Puffers Datenmembers.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des Elements Längenindikator/gebunden werden soll.  
  
 Weitere Informationen, wie diese Informationen verwendet werden finden Sie unter "Pufferadressen," weiter unten in diesem Abschnitt. Weitere Informationen zu spaltenbezogene Bindungen, finden Sie unter [zeilenweise Bindung](../../../odbc/reference/develop-app/row-wise-binding.md).  
  
## <a name="buffer-addresses"></a>Pufferadressen  
 Die *Puffern Adresse* ist die tatsächliche Adresse des Puffers Daten oder Längenindikator /. Der Treiber berechnet die Pufferadresse nur vor dem Schreiben in den Puffern (z. B. während der Zeit abgerufen werden). Er wird berechnet aus der folgenden Formel, die die im angegebenen Adressen verwendet den *TargetValuePtr* und *StrLen_or_IndPtr* Argumente, den Offset für die Bindung und die Nummer der Zeile:  
  
 *Adresse gebunden* + *Bindung Offset* + ((*Zeilennummer* - 1) X *Elementgröße*)  
  
 auf der Formel die Variablen definiert werden, wie in der folgenden Tabelle beschrieben.  
  
|Variable|Description|  
|--------------|-----------------|  
|*Adresse gebunden*|Für Datenpuffer, die Adresse angegeben, mit der *TargetValuePtr* -Argument in **SQLBindCol**.<br /><br /> Für Längenindikator/Puffer, die Adresse angegeben, mit der *StrLen_or_IndPtr* -Argument in **SQLBindCol**. Weitere Informationen finden Sie unter "Zusätzliche Kommentare" im Abschnitt "Deskriptoren und SQLBindCol".<br /><br /> Wenn die gebundene Adresse 0 (null) ist kein Datenwert zurückgegeben, auch wenn die Adresse von der vorstehenden Formel berechnet ungleich NULL ist.|  
|*Binden von Offset*|Wenn zeilenbezogene Bindungen verwendet wird, der Wert an der Adresse gespeichert, die mit der SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattribut angegeben werden.<br /><br /> Wenn spaltenbezogene Bindungen verwendet wird, oder wenn der Wert des Attributs Anweisung SQL_ATTR_ROW_BIND_OFFSET_PTR ein null-Zeiger ist *Bindung Offset* ist 0.|  
|*Zeilennummer*|Die 1-basierten Nummer der Zeile im Rowset. Einzeiliges Abrufe, die standardmäßig, die werden zu können, ist dies 1.|  
|*Elementgröße*|Die Größe eines Elements in das gebundene Array.<br /><br /> Wenn Sie spaltenbezogene Bindungen verwendet wird, ist dies **sizeof(SQLINTEGER)** für Längenindikator/Puffer. Für Datenpuffer, es ist der Wert des der *Pufferlänge* -Argument in **SQLBindCol** , wenn der Datentyp variabler Länge und die Größe des Datentyps ist, wenn der Datentyp über eine feste Länge aufweist.<br /><br /> Wenn die zeilenweise Bindung verwendet wird, ist dies der Wert des Attributs SQL_ATTR_ROW_BIND_TYPE-Anweisung für die Daten- und Längenindikator/Puffer.|  
  
## <a name="descriptors-and-sqlbindcol"></a>Deskriptoren und SQLBindCol  
 In den folgenden Abschnitten wird beschrieben wie **SQLBindCol** interagiert mit Deskriptoren.  
  
> [!CAUTION]  
>  Aufrufen von **SQLBindCol** für eine Anweisung auf andere Anweisungen auswirken kann. Dies tritt auf, wenn es sich bei der der Anweisung zugeordneten ARD explizit zugeordnet ist, und auch andere Anweisungen zugeordnet ist. Da **SQLBindCol** ändert die Sicherheitsbeschreibung, die Änderungen gelten für alle Anweisungen, die der dieser Deskriptor zugeordnet ist. Ist dies nicht das erforderliche Verhalten, die Anwendung sollte Trennen dieser Deskriptor aus den anderen Anweisungen vor **SQLBindCol**.  
  
## <a name="argument-mappings"></a>Argument-Zuordnungen  
 Im Prinzip **SQLBindCol** führt Sie nacheinander die folgenden Schritte aus:  
  
1.  Aufrufe **SQLGetStmtAttr** um die ARD-Handle zu erhalten.  
  
2.  Aufrufe **SQLGetDescField** zum Abrufen dieses Deskriptors SQL_DESC_COUNT-Feld, und wenn der Wert in der *ColumnNumber* Arguments überschreitet den Wert von SQL_DESC_COUNT, Aufrufe **SQLSetDescField**  zur Erhöhung des Werts der SQL_DESC_COUNT zu *ColumnNumber*.  
  
3.  Aufrufe **SQLSetDescField** mehrere Male auf, um die folgenden Felder ein, der die ARD Werte zuzuweisen:  
  
    -   Legt die SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE auf den Wert der *TargetType*, mit dem Unterschied, dass wenn *TargetType* ist eine präzise Bezeichner eines Untertyps "DateTime" oder das Intervall, SQL_DESC_TYPE auf SQL_ festgelegt DATETIME oder SQL_INTERVAL, bzw.; Legt SQL_DESC_CONCISE_TYPE auf der präzisen Bezeichner fest. wobei SQL_DESC_DATETIME_INTERVAL_CODE das entsprechende DateTime ' oder ' Intervall Fehlersubcode.  
  
    -   Legt eine oder mehrere der SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_DATETIME_INTERVAL_PRECISION, je nach *TargetType*.  
  
    -   Legt das SQL_DESC_OCTET_LENGTH-Feld auf den Wert der *Pufferlänge*.  
  
    -   Legt das SQL_DESC_DATA_PTR-Feld auf den Wert der *Zielwert*.  
  
    -   Legt das SQL_DESC_INDICATOR_PTR-Feld auf den Wert der *StrLen_or_Ind*. (Siehe folgenden Abschnitt.)  
  
    -   Legt das SQL_DESC_OCTET_LENGTH_PTR-Feld auf den Wert der *StrLen_or_Ind*. (Siehe folgenden Abschnitt.)  
  
 Die Variable, die die *StrLen_or_Ind* -Argument bezieht sich auf Informationen sowohl Indikator und Länge verwendet wird. Wenn eine Abrufoperation für die Spalte einen null-Wert auftritt, SQL_NULL_DATA in dieser Variable gespeichert; Andernfalls werden die Datenlänge in dieser Variable gespeichert. Übergeben einen null-Zeiger als *StrLen_or_Ind* behält die Fetch-Vorgang die Datenlänge zurückgeben, aber den Abruf fehl, wenn es einen null-Wert erkennt und keine Möglichkeit hat, SQL_NULL_DATA zurückgegeben wird.  
  
 Wenn der Aufruf von **SQLBindCol** ein Fehler auftritt, der Inhalt der deskriptorfelder, die sie in der ARD festgelegt haben, würden sind nicht definiert, und der Wert des Felds SQL_DESC_COUNT aus, der die ARD bleibt unverändert.  
  
## <a name="implicit-resetting-of-count-field"></a>Implizite Zurücksetzen des COUNT-Feld  
 **SQLBindCol** SQL_DESC_COUNT auf den Wert der legt die *ColumnNumber* Argument nur, wenn dies den Wert des SQL_DESC_COUNT erhöhen würde. Wenn der Wert in der *TargetValuePtr* Argument ist ein null-Zeiger und den Wert in der *ColumnNumber* Argument SQL_DESC_COUNT gleich ist (d. h. wenn Aufheben der Bindung die höchste Spalte gebunden ist), dann SQL_DESC_ Die Anzahl wird auf die Anzahl der verbleibenden gebundene Spalte mit der höchsten festgelegt.  
  
## <a name="cautions-regarding-sqldefault"></a>Punkte in Bezug auf SQL_DEFAULT  
 Zum Abrufen von Daten der Spalte erfolgreich, muss die Anwendung ordnungsgemäß die Länge und den Ausgangspunkt der Daten in den Anwendungspuffer festgestellt werden. Wenn die Anwendung gibt eine explizite *TargetType*, Anwendung Missverständnisse sind leicht zu erkennen. Jedoch, wenn die Anwendung gibt an, eine *TargetType* von SQL_DEFAULT, **SQLBindCol** kann angewendet werden für eine Spalte mit einem anderen Datentyp aus das gewünschte von der Anwendung, entweder über Änderungen an der Metadaten oder durch den Code in eine andere Spalte anwenden. In diesem Fall kann die Anwendung nicht immer den Start oder die Länge der Spaltendaten an abgerufenen ermittelt werden. Dies kann zu Meldung Datenfehler oder Arbeitsspeicher-sicherheitsverletzungen führen.  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel führt eine Anwendung eine **wählen** Anweisung in der Customers-Tabelle, um ein Resultset des Kunden-IDs, Namen und Telefonnummern zurückzugeben, die nach Namen sortiert. Es ruft dann **SQLBindCol** um die Datenspalten an lokalen Puffer zu binden. Schließlich die Anwendung ruft jede Zeile von Daten mit **SQLFetch** und gibt Name, ID und Telefonnummer des Kunden.  
  
 Weitere Codebeispiele, finden Sie unter [SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md), [SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md), und [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```cpp  
// SQLBindCol_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <stdio.h>  
  
#define UNICODE  
#include <sqlext.h>  
  
#define NAME_LEN 50  
#define PHONE_LEN 20  
  
void show_error() {  
   printf("error\n");  
}  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
   SQLWCHAR szName[NAME_LEN], szPhone[PHONE_LEN], sCustID[NAME_LEN];  
   SQLLEN cbName = 0, cbCustID = 0, cbPhone = 0;  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLWCHAR*) L"NorthWind", SQL_NTS, (SQLWCHAR*) NULL, 0, NULL, 0);  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {   
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               retcode = SQLExecDirect(hstmt, (SQLWCHAR *) L"SELECT CustomerID, ContactName, Phone FROM CUSTOMERS ORDER BY 2, 1, 3", SQL_NTS);  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
                  // Bind columns 1, 2, and 3  
                  retcode = SQLBindCol(hstmt, 1, SQL_C_CHAR, &sCustID, 100, &cbCustID);  
                  retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
                  retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN, &cbPhone);   
  
                  // Fetch and print each row of data. On an error, display a message and exit.  
                  for (i ; ; i++) {  
                     retcode = SQLFetch(hstmt);  
                     if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
                        show_error();  
                     if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                        wprintf(L"%d: %S %S %S\n", i + 1, sCustID, szName, szPhone);  
                     else  
                        break;  
                  }  
               }  
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLCancel(hstmt);  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 Siehe auch [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen mehrerer Zeilen von Daten|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Freigeben von Puffern mit Spalten für die Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Abrufen von teilweise oder vollständig eine Spalte mit Daten|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Die Anzahl der Resultsets zurückgeben von Resultsetspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
