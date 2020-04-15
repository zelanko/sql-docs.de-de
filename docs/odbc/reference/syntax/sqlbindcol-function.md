---
title: SQLBindCol-Funktion | Microsoft Docs
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
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBindCol
helpviewer_keywords:
- SQLBindCol function [ODBC]
ms.assetid: 41a37655-84cd-423f-9daa-e0b47b88dc54
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90bb1c1aa4dbfa2614f689faa47eb0c41a6cecd6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298740"
---
# <a name="sqlbindcol-function"></a>SQLBindCol-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLBindCol** bindet Anwendungsdatenpuffer an Spalten im Resultset.  
  
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
 [Eingabe] Nummer der zu bindenden Ergebnissatzspalte. Spalten werden in zunehmender Spaltenreihenfolge ab 0 nummeriert, wobei Spalte 0 die Lesezeichenspalte ist. Wenn Keine Lesezeichen verwendet werden , d. h., das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung auf SQL_UB_OFF festgelegt ist - beginnen die Spaltennummern bei 1.  
  
 *Targettype*  
 [Eingabe] Der Bezeichner des C-Datentyps des \* *TargetValuePtr-Puffers.* Wenn Daten aus der Datenquelle mit **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**oder **SQLSetPos**abgerufen werden, konvertiert der Treiber die Daten in diesen Typ. Wenn Daten mit **SQLBulkOperations** oder **SQLSetPos**an die Datenquelle gesendet werden, konvertiert der Treiber die Daten von diesem Typ. Eine Liste gültiger C-Datentypen und Typbezeichner finden Sie im Abschnitt [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen.  
  
 Wenn das *TargetType-Argument* ein Intervalldatentyp ist, werden für die Daten die Standardmäßige Intervallführungsgenauigkeit (2) und die Standardintervallsekundengenauigkeit (6), wie sie in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION bzw. SQL_DESC_PRECISION der ARD festgelegt sind, verwendet. Wenn das *TargetType-Argument* SQL_C_NUMERIC ist, werden für die Daten die Standardgenauigkeit (treiberdefiniert) und die Standardskala (0), wie sie in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE der ARD festgelegt sind, verwendet. Wenn eine Standardgenauigkeit oder ein Standardmaßstab nicht geeignet ist, sollte die Anwendung das entsprechende Deskriptorfeld explizit durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**festlegen.  
  
 Sie können auch einen erweiterten C-Datentyp angeben. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *TargetValuePtr*  
 [Verzögerter Eingang/Ausgang] Zeiger auf den Datenpuffer, der an die Spalte gebunden werden soll. **SQLFetch** und **SQLFetchScroll** geben Daten in diesem Puffer zurück. **SQLBulkOperations** gibt Daten in diesem Puffer zurück, wenn *der Vorgang* SQL_FETCH_BY_BOOKMARK wird. Es ruft Daten aus diesem Puffer ab, wenn *Der Vorgang* SQL_ADD oder SQL_UPDATE_BY_BOOKMARK ist. **SQLSetPos** gibt Daten in diesem Puffer zurück, wenn *der Vorgang* SQL_REFRESH wird. Es ruft Daten aus diesem Puffer ab, wenn *Der Vorgang* SQL_UPDATE wird.  
  
 Wenn *TargetValuePtr* ein Nullzeiger ist, hebt der Treiber die Bindung des Datenpuffers für die Spalte auf. Eine Anwendung kann die Bindung aller Spalten aufkleben, indem **sie SQLFreeStmt** mit der Option SQL_UNBIND aufruft. Eine Anwendung kann die Bindung des Datenpuffers für eine Spalte aufheben, aber dennoch einen Längen-/Indikatorpuffer für die Spalte gebunden haben, wenn das *TargetValuePtr-Argument* im Aufruf von **SQLBindCol** ein Nullzeiger ist, das *argument StrLen_or_IndPtr* jedoch ein gültiger Wert ist.  
  
 *BufferLength*  
 [Eingabe] Länge des \* *TargetValuePtr-Puffers* in Bytes.  
  
 Der Treiber verwendet *BufferLength,* um zu \*vermeiden, dass das Ende des *TargetValuePtr-Puffers* überschrieben wird, wenn Daten mit variabler Länge zurückgegeben werden, z. B. Zeichen- oder Binärdaten. Beachten Sie, dass der Treiber das Null-Beendigungszeichen zählt, wenn er Zeichendaten an \* *TargetValuePtr*zurückgibt. \**TargetValuePtr* muss daher Platz für das Null-Beendigungszeichen enthalten, da der Treiber die Daten abnimmt.  
  
 Wenn der Treiber Daten fester Länge zurückgibt, z. B. eine ganze Zahl oder eine Datumsstruktur, ignoriert der Treiber *BufferLength* und geht davon aus, dass der Puffer groß genug ist, um die Daten zu halten. Daher ist es wichtig, dass die Anwendung einen ausreichend großen Puffer für Daten fester Länge reserviert, oder der Treiber schreibt über das Ende des Puffers hinaus.  
  
 **SQLBindCol** gibt SQLSTATE HY090 (Ungültige Zeichenfolge oder Pufferlänge) zurück, wenn *BufferLength* kleiner als 0 ist, aber nicht, wenn *BufferLength* 0 ist. Wenn *TargetType* jedoch einen Zeichentyp angibt, sollte eine Anwendung *BufferLength* nicht auf 0 setzen, da ISO CLI-kompatible Treiber in diesem Fall SQLSTATE HY090 (Ungültige Zeichenfolge oder Pufferlänge) zurückgeben.  
  
 *StrLen_or_IndPtr*  
 [Verzögerter Eingang/Ausgang] Zeiger auf den Längen-/Indikatorpuffer, der an die Spalte gebunden werden soll. **SQLFetch** und **SQLFetchScroll** geben einen Wert in diesem Puffer zurück. **SQLBulkOperations** ruft einen Wert aus diesem Puffer ab, wenn *Der Vorgang* SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_DELETE_BY_BOOKMARK ist. **SQLBulkOperations** gibt einen Wert in diesem Puffer zurück, wenn *Der Vorgang* SQL_FETCH_BY_BOOKMARK wird. **SQLSetPos** gibt einen Wert in diesem Puffer zurück, wenn *Der Vorgang* SQL_REFRESH wird. Es ruft einen Wert aus diesem Puffer ab, wenn *Operation* SQL_UPDATE wird.  
  
 **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**und **SQLSetPos** können die folgenden Werte im Längen-/Indikatorpuffer zurückgeben:  
  
-   Die Länge der zur Rückgabe verfügbaren Daten  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Die Anwendung kann die folgenden Werte in den Längen-/Indikatorpuffer für die Verwendung mit **SQLBulkOperations** oder **SQLSetPos**setzen:  
  
-   Die Länge der gesendeten Daten  
  
-   SQL_NTS  
  
-   SQL_NULL_DATA  
  
-   SQL_DATA_AT_EXEC  
  
-   Das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros  
  
-   SQL_COLUMN_IGNORE  
  
 Wenn der Indikatorpuffer und der Längenpuffer separate Puffer sind, kann der Indikatorpuffer nur SQL_NULL_DATA zurückgeben, während der Längenpuffer alle anderen Werte zurückgeben kann.  
  
 Weitere Informationen finden Sie unter [SQLBulkOperations Function](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md), [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md)und Using [Length/Indicator Values](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Wenn *StrLen_or_IndPtr* ein Nullzeiger ist, wird kein Längen- oder Indikatorwert verwendet. Dies ist ein Fehler beim Abrufen von Daten, und die Daten sind NULL.  
  
 Siehe [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLBindCol** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLBindCol** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|(DM) Das *ColumnNumber-Argument* war 0, und das *TargetType-Argument* wurde nicht SQL_C_BOOKMARK oder SQL_C_VARBOOKMARK.|  
|07009|Ungültiger Deskriptorindex|Der für das Argument *ColumnNumber* angegebene Wert hat die maximale Anzahl von Spalten im Resultset überschritten.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY003|Ungültiger Anwendungspuffertyp|Das Argument *TargetType* war weder ein gültiger Datentyp noch SQL_C_DEFAULT.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als **SQLBindCol** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der für das Argument *BufferLength* angegebene Wert war kleiner als 0.<br /><br /> (DM) Der Treiber war ein ODBC 2. *x-Treiber* wurde das *ColumnNumber-Argument* auf 0 gesetzt, und der für das Argument *BufferLength* angegebene Wert war nicht gleich 4.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der Treiber oder die Datenquelle unterstützt die Konvertierung, die durch die Kombination des *TargetType-Arguments* und des treiberspezifischen SQL-Datentyps der entsprechenden Spalte angegeben wird, nicht.<br /><br /> Das Argument *ColumnNumber* war 0, und der Treiber unterstützt keine Lesezeichen.<br /><br /> Der Treiber unterstützt nur ODBC 2. *x* und das Argument *TargetType* war eines der folgenden:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> und alle In-Intervall-C-Datentypen, die in [Anhang](../../../odbc/reference/appendixes/c-data-types.md) D: Datentypen aufgeführt sind.<br /><br /> Der Treiber unterstützt nur ODBC-Versionen vor 3.50, und das Argument *TargetType* wurde SQL_C_GUID.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 **SQLBindCol** wird verwendet, um Spalten im Resultset Datenpuffern und Längen-/Indikatorpuffern in der Anwendung zuzuordnen oder zu *binden.* Wenn die Anwendung **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos** aufruft, um Daten abzurufen, gibt der Treiber die Daten für die gebundenen Spalten in den angegebenen Puffern zurück. Weitere Informationen finden Sie unter [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md). Wenn die Anwendung **SQLBulkOperations** aufruft, um eine Zeile oder **SQLSetPos** zu aktualisieren, um eine Zeile zu aktualisieren, ruft der Treiber die Daten für die gebundenen Spalten aus den angegebenen Puffern ab. Weitere Informationen finden Sie unter [SQLBulkOperations Function](../../../odbc/reference/syntax/sqlbulkoperations-function.md) oder [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md). Weitere Informationen zur Bindung finden Sie unter [Abrufen von Ergebnissen (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 Beachten Sie, dass Spalten nicht gebunden sein müssen, um Daten aus ihnen abzurufen. Eine Anwendung kann auch **SQLGetData** aufrufen, um Daten aus Spalten abzurufen. Obwohl es möglich ist, einige Spalten in einer Zeile zu binden und **SQLGetData** für andere aufzurufen, unterliegt dies einigen Einschränkungen. Weitere Informationen finden Sie unter [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
## <a name="binding-unbinding-and-rebinding-columns"></a>Bindungs-, Unbindungs- und Neubindungsspalten  
 Eine Spalte kann jederzeit gebunden, ungebunden oder zurückgesetzt werden, auch nachdem Daten aus dem Resultset abgerufen wurden. Die neue Bindung wird wirksam, wenn das nächste Mal eine Funktion aufgerufen wird, die Bindungen verwendet. Angenommen, eine Anwendung bindet die Spalten in einem Resultset und ruft **SQLFetch**auf. Der Treiber gibt die Daten in den gebundenen Puffern zurück. Angenommen, die Anwendung bindet die Spalten an einen anderen Satz von Puffern. Der Treiber legt die Daten für die gerade abgerufene Zeile nicht in den neu gebundenen Puffern ab. Stattdessen wartet es, bis **SQLFetch** erneut aufgerufen wird, und platziert dann die Daten für die nächste Zeile in den neu gebundenen Puffern.  
  
> [!NOTE]  
>  Das Anweisungsattribut SQL_ATTR_USE_BOOKMARKS sollte immer festgelegt werden, bevor eine Spalte an Spalte 0 gebunden wird. Dies ist nicht erforderlich, wird aber dringend empfohlen.  
  
## <a name="binding-columns"></a>Binden von Spalten  
 Um eine Spalte zu binden, ruft eine Anwendung **SQLBindCol** auf und übergibt die Spaltennummer, den Typ, die Adresse und die Länge eines Datenpuffers sowie die Adresse eines Längen-/Indikatorpuffers. Informationen zur Verwendung dieser Adressen finden Sie weiter unten in diesem Abschnitt unter "Pufferadressen". Weitere Informationen zu Bindungsspalten finden Sie unter [Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Die Verwendung dieser Puffer wird zurückgestellt; Das heißt, die Anwendung bindet sie in **SQLBindCol,** aber der Treiber greift von anderen Funktionen auf sie zu - nämlich **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos**. Es liegt in der Verantwortung der Anwendung sicherzustellen, dass die in **SQLBindCol** angegebenen Zeiger gültig bleiben, solange die Bindung wirksam bleibt. Wenn die Anwendung zulässt, dass diese Zeiger ungültig werden - z. B. gibt sie einen Puffer frei - und dann eine Funktion aufruft, die erwartet, dass sie gültig sind, sind die Folgen nicht definiert. Weitere Informationen finden Sie unter [Verzögerte Puffer](../../../odbc/reference/develop-app/deferred-buffers.md).  
  
 Die Bindung bleibt so lange wirksam, bis sie durch eine neue Bindung ersetzt wird, die Spalte ungebunden ist oder die Anweisung freigegeben wird.  
  
## <a name="unbinding-columns"></a>Unbinding Columns  
 Um die Bindung einer einzelnen Spalte aufzuheben, ruft eine Anwendung **SQLBindCol** auf, wobei *ColumnNumber* auf die Nummer dieser Spalte und *TargetValuePtr* auf einen Nullzeiger festgelegt ist. Wenn *ColumnNumber* auf eine ungebundene Spalte verweist, gibt **SQLBindCol** immer noch SQL_SUCCESS zurück.  
  
 Um die Bindung aller Spalten aufzukleben, ruft eine Anwendung **SQLFreeStmt** auf, wobei *fOption* auf SQL_UNBIND festgelegt ist. Dies kann auch erreicht werden, indem man das SQL_DESC_COUNT der ARD auf Null setzt.  
  
## <a name="rebinding-columns"></a>Wiederbinden von Spalten  
 Eine Anwendung kann einen der beiden Vorgänge ausführen, um eine Bindung zu ändern:  
  
-   Rufen Sie **SQLBindCol** auf, um eine neue Bindung für eine Spalte anzugeben, die bereits gebunden ist. Der Treiber überschreibt die alte Bindung mit der neuen.  
  
-   Geben Sie einen Offset an, der der Pufferadresse hinzugefügt werden soll, die durch den Bindungsaufruf an **SQLBindCol**angegeben wurde. Weitere Informationen finden Sie im nächsten Abschnitt "Bindungvon Offsets".  
  
## <a name="binding-offsets"></a>Bindungsversätze  
 Ein Bindungsoffset ist ein Wert, der den Adressen der Daten- und Längen-/Indikatorpuffer hinzugefügt wird (wie in *TargetValuePtr* und *StrLen_or_IndPtr* Argument angegeben), bevor sie dereferenziert werden. Wenn Offsets verwendet werden, sind die Bindungen eine "Vorlage" dafür, wie die Puffer der Anwendung angeordnet sind, und die Anwendung kann diese "Vorlage" in verschiedene Speicherbereiche verschieben, indem sie den Offset ändert. Da jeder Adresse in jeder Bindung derselbe Offset hinzugefügt wird, müssen die relativen Offsets zwischen Puffern für verschiedene Spalten innerhalb jedes Puffersatzes identisch sein. Dies gilt immer dann, wenn zeilenweise bindung verwendet wird; Die Anwendung muss ihre Puffer sorgfältig festlegen, damit dies bei verwendung einer spaltenweisen Bindung zutrifft.  
  
 Die Verwendung eines Bindungsoffsets hat im Grunde den gleichen Effekt wie das erneutbinden einer Spalte durch Aufrufen von **SQLBindCol**. Der Unterschied besteht darin, dass ein neuer Aufruf von **SQLBindCol** neue Adressen für den Datenpuffer und den Längen-/Indikatorpuffer angibt, während die Verwendung eines Bindungsoffsets die Adressen nicht ändert, sondern nur einen Offset hinzufügt. Die Anwendung kann jederzeit einen neuen Offset angeben, und dieser Offset wird immer zu den ursprünglich gebundenen Adressen hinzugefügt. Insbesondere, wenn der Offset auf 0 oder wenn das Anweisungsattribut auf einen Nullzeiger gesetzt ist, verwendet der Treiber die ursprünglich gebundenen Adressen.  
  
 Um einen Bindungsoffset anzugeben, legt die Anwendung das SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattribut auf die Adresse eines SQLINTEGER-Puffers fest. Bevor die Anwendung eine Funktion aufruft, die Bindungen verwendet, wird in diesem Puffer ein Offset in Bytes eingefügt. Um die Adresse des zu verwendenden Puffers zu bestimmen, fügt der Treiber den Offset zur Adresse in der Bindung hinzu. Die Summe der Adresse und des Offsets muss eine gültige Adresse sein, aber die Adresse, der der Offset hinzugefügt wird, muss nicht gültig sein. Weitere Informationen zur Verwendung von Bindungsoffsets finden Sie weiter unten in diesem Abschnitt unter "Pufferadressen".  
  
## <a name="binding-arrays"></a>Bindungs-Arrays  
 Wenn die Rowsetgröße (der Wert des attributs SQL_ATTR_ROW_ARRAY_SIZE Anweisung) größer als 1 ist, bindet die Anwendung Arrays von Puffern anstelle einzelner Puffer. Weitere Informationen finden Sie unter [Blockieren von Cursors](../../../odbc/reference/develop-app/block-cursors.md).  
  
 Die Anwendung kann Arrays auf zwei Arten binden:  
  
-   Binden Sie ein Array an jede Spalte. Dies wird als *spaltenweise Bindung* bezeichnet, da jede Datenstruktur (Array) Daten für eine einzelne Spalte enthält.  
  
-   Definieren Sie eine Struktur, um die Daten für eine ganze Zeile zu halten und ein Array dieser Strukturen zu binden. Dies wird als *zeilenweise Bindung* bezeichnet, da jede Datenstruktur die Daten für eine einzelne Zeile enthält.  
  
 Jedes Array von Puffern muss mindestens so viele Elemente wie die Größe des Rowsets aufweisen.  
  
> [!NOTE]  
>  Eine Anwendung muss überprüfen, ob die Ausrichtung gültig ist. Weitere Informationen zu [Ausrichtungsüberlegungen](../../../odbc/reference/develop-app/alignment.md)finden Sie unter Ausrichtung .  
  
## <a name="column-wise-binding"></a>Spaltenbezogenes Binden  
 In der spaltenweisen Bindung bindet die Anwendung separate Daten- und Längen-/Indikatorarrays an jede Spalte.  
  
 Um die spaltenweise Bindung zu verwenden, legt die Anwendung zuerst das attribut SQL_ATTR_ROW_BIND_TYPE-Anweisung auf SQL_BIND_BY_COLUMN. (Dies ist die Standardeinstellung.) Für jede zu bindende Spalte führt die Anwendung die folgenden Schritte aus:  
  
1.  Ordnet ein Datenpufferarray zu.  
  
2.  Ordnet ein Array von Längen-/Indikatorpuffern zu.  
  
    > [!NOTE]  
    >  Wenn die Anwendung direkt in Deskriptoren schreibt, wenn spaltenweise Bindungen verwendet werden, können separate Arrays für Längen- und Indikatordaten verwendet werden.  
  
3.  Ruft **SQLBindCol** mit den folgenden Argumenten auf:  
  
    -   *TargetType* ist der Typ eines einzelnen Elements im Datenpufferarray.  
  
    -   *TargetValuePtr* ist die Adresse des Datenpufferarrays.  
  
    -   *BufferLength* ist die Größe eines einzelnen Elements im Datenpufferarray. Das *Argument BufferLength* wird ignoriert, wenn es sich bei den Daten um Daten fester Länge handelt.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des Längen-/Indikator-Arrays.  
  
 Weitere Informationen zur Verwendung dieser Informationen finden Sie weiter unten in diesem Abschnitt unter "Pufferadressen". Weitere Informationen zur spaltenweisen Bindung finden Sie unter [Column-Wise Binding](../../../odbc/reference/develop-app/column-wise-binding.md).  
  
## <a name="row-wise-binding"></a>Zeilenbezogenes Binden  
 In der zeilenweisen Bindung definiert die Anwendung eine Struktur, die Daten und Längen-/Indikatorpuffer für jede zu bindende Spalte enthält.  
  
 Um die zeilenweise Bindung zu verwenden, führt die Anwendung die folgenden Schritte aus:  
  
1.  Definiert eine Struktur für eine einzelne Datenzeile (einschließlich Daten- und Längen-/Indikatorpuffer) und weist ein Array dieser Strukturen zu.  
  
    > [!NOTE]  
    >  Wenn die Anwendung direkt in Deskriptoren schreibt, wenn zeilenweise Bindung verwendet wird, können separate Felder für Längen- und Indikatordaten verwendet werden.  
  
2.  Legt das SQL_ATTR_ROW_BIND_TYPE Anweisungsattribut auf die Größe der Struktur fest, die eine einzelne Datenzeile enthält, oder auf die Größe einer Instanz eines Puffers, an die die Ergebnisspalten gebunden werden. Die Länge muss Platz für alle gebundenen Spalten und alle Auffüllungen der Struktur oder des Puffers enthalten, um sicherzustellen, dass das Ergebnis auf den Anfang derselben Spalte in der nächsten Zeile zeigen, wenn die Adresse einer gebundenen Spalte mit der angegebenen Länge erhöht wird. Bei Verwendung *des Operators "Sizeof"* in ANSI C ist dieses Verhalten garantiert.  
  
3.  Ruft **SQLBindCol** mit den folgenden Argumenten für jede zu bindende Spalte auf:  
  
    -   *TargetType* ist der Typ des Datenpuffermembers, der an die Spalte gebunden werden soll.  
  
    -   *TargetValuePtr* ist die Adresse des Datenpufferelements im ersten Arrayelement.  
  
    -   *BufferLength* ist die Größe des Datenpufferelements.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des zu bindenden Längen-/Indikatorelements.  
  
 Weitere Informationen zur Verwendung dieser Informationen finden Sie weiter unten in diesem Abschnitt unter "Pufferadressen". Weitere Informationen zur spaltenweisen Bindung finden Sie unter [Row-Wise Binding](../../../odbc/reference/develop-app/row-wise-binding.md).  
  
## <a name="buffer-addresses"></a>Pufferadressen  
 Die *Pufferadresse* ist die tatsächliche Adresse der Daten oder Länge/Indikatorpuffer. Der Treiber berechnet die Pufferadresse kurz vor dem Schreiben in die Puffer (z. B. während der Abrufzeit). Er wird aus der folgenden Formel berechnet, die die in den *Argumenten TargetValuePtr* und *StrLen_or_IndPtr* angegebenen Adressen, den Bindungsoffset und die Zeilennummer verwendet:  
  
 *Gebundene Adressbindung* + *Offset* + ((*Zeilennummer* - 1) x *Elementgröße*)  
  
 wobei die Variablen der Formel wie in der folgenden Tabelle beschrieben definiert sind.  
  
|Variable|BESCHREIBUNG|  
|--------------|-----------------|  
|*Gebundene Adresse*|Bei Datenpuffern die Adresse, die mit dem *TargetValuePtr-Argument* in **SQLBindCol**angegeben wurde.<br /><br /> Für Längen-/Indikatorpuffer die Adresse, die mit dem *Argument StrLen_or_IndPtr* in **SQLBindCol**angegeben ist. Weitere Informationen finden Sie unter "Zusätzliche Kommentare" im Abschnitt "Deskriptoren und SQLBindCol".<br /><br /> Wenn die gebundene Adresse 0 ist, wird kein Datenwert zurückgegeben, auch wenn die adresse, wie durch die vorherige Formel berechnet, ungleich Null ist.|  
|*Bindungsversatz*|Wenn zeilenweise Bindung verwendet wird, wird der Wert verwendet, der an der Adresse gespeichert ist, die mit dem attribut SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisung angegeben ist.<br /><br /> Wenn die spaltenweise Bindung verwendet wird oder wenn der Wert des SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattributs ein Nullzeiger ist, ist *Binding Offset* 0.|  
|*Row Number*|Die 1-basierte Nummer der Zeile im Rowset. Bei einzeiligen Abrufen, bei denen die Standardeinstellung angezeigt wird, ist dies 1.|  
|*Elementgröße*|Die Größe eines Elements im gebundenen Array.<br /><br /> Wenn spaltenweise Bindung verwendet wird, ist dies **sizeof(SQLINTEGER)** für Längen-/Indikatorpuffer. Bei Datenpuffern ist es der Wert des *BufferLength-Arguments* in **SQLBindCol,** wenn der Datentyp eine variable Länge ist, und die Größe des Datentyps, wenn der Datentyp eine feste Länge ist.<br /><br /> Wenn zeilenweise Bindung verwendet wird, ist dies der Wert des SQL_ATTR_ROW_BIND_TYPE-Anweisungsattributs für Daten- und Längen-/Indikatorpuffer.|  
  
## <a name="descriptors-and-sqlbindcol"></a>Deskriptoren und SQLBindCol  
 In den folgenden Abschnitten wird beschrieben, wie **SQLBindCol** mit Deskriptoren interagiert.  
  
> [!CAUTION]  
>  Das Aufrufen von **SQLBindCol** für eine Anweisung kann sich auf andere Anweisungen auswirken. Dies geschieht, wenn die ARD, die mit der Erklärung verbunden ist, explizit zugeordnet und auch mit anderen Aussagen in Verbindung gebracht wird. Da **SQLBindCol** den Deskriptor ändert, gelten die Änderungen für alle Anweisungen, denen dieser Deskriptor zugeordnet ist. Wenn dies nicht das erforderliche Verhalten ist, sollte die Anwendung diesen Deskriptor von den anderen Anweisungen trennen, bevor sie **SQLBindCol**aufruft.  
  
## <a name="argument-mappings"></a>Argumentzuordnungen  
 **SqlBindCol** führt konzeptionell die folgenden Schritte nacheinander aus:  
  
1.  Ruft **SQLGetStmtAttr** auf, um das ARD-Handle zu erhalten.  
  
2.  Ruft **SQLGetDescField** auf, um das SQL_DESC_COUNT Feld dieses Deskriptors abzubekommen, und wenn der Wert im *ColumnNumber-Argument* den Wert von SQL_DESC_COUNT überschreitet, ruft **SQLSetDescField** auf, um den Wert von SQL_DESC_COUNT in *ColumnNumber*zu erhöhen.  
  
3.  Ruft **SQLSetDescField** mehrmals auf, um den folgenden Feldern der ARD Werte zuzuweisen:  
  
    -   Legt SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE auf den Wert von *TargetType*fest, mit der Ausnahme, dass *TargetType,* wenn targetType einer der prägnanten Bezeichner eines Datumszeit- oder Intervallsubtyps ist, SQL_DESC_TYPE auf SQL_DATETIME bzw. SQL_INTERVAL festgelegt wird. legt SQL_DESC_CONCISE_TYPE auf den prägnanten Bezeichner fest; und legt SQL_DESC_DATETIME_INTERVAL_CODE auf den entsprechenden Datetime- oder Intervall-Untercode fest.  
  
    -   Legt je nach *TargetType*einen oder mehrere SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_DATETIME_INTERVAL_PRECISION fest.  
  
    -   Legt das SQL_DESC_OCTET_LENGTH Feld auf den Wert *BufferLength*fest.  
  
    -   Legt das SQL_DESC_DATA_PTR Feld auf den Wert *targetValue*fest.  
  
    -   Legt das Feld SQL_DESC_INDICATOR_PTR auf den Wert *von StrLen_or_Ind*fest. (Siehe den folgenden Absatz.)  
  
    -   Legt das Feld SQL_DESC_OCTET_LENGTH_PTR auf den Wert *von StrLen_or_Ind*fest. (Siehe den folgenden Absatz.)  
  
 Die Variable, auf die sich das *StrLen_or_Ind-Argument* bezieht, wird sowohl für Indikator- als auch für Längeninformationen verwendet. Wenn ein Abruf auf einen NULL-Wert für die Spalte trifft, werden SQL_NULL_DATA in dieser Variablen gespeichert. Andernfalls wird die Datenlänge in dieser Variablen gespeichert. Das Übergeben eines Nullzeigers als *StrLen_or_Ind* verhindert, dass der Abrufvorgang die Datenlänge zurückgibt, aber der Abruf schlägt fehl, wenn er auf einen Nullwert trifft und keine Möglichkeit hat, SQL_NULL_DATA zurückzugeben.  
  
 Schlägt der Aufruf von **SQLBindCol** fehl, ist der Inhalt der Deskriptorfelder, die er in der ARD festgelegt hätte, nicht definiert und der Wert des SQL_DESC_COUNT Feldes der ARD bleibt unverändert.  
  
## <a name="implicit-resetting-of-count-field"></a>Implizites Zurücksetzen des COUNT-Feldes  
 **SQLBindCol** legt SQL_DESC_COUNT auf den Wert des *ColumnNumber-Arguments* nur dann fest, wenn dadurch der Wert von SQL_DESC_COUNT erhöht wird. Wenn der Wert im *TargetValuePtr-Argument* ein Nullzeiger ist und der Wert im *ColumnNumber-Argument* gleich SQL_DESC_COUNT ist (d. h., wenn die Bindung der Spalte am höchsten gebundenen Wert aufgehoben wird), wird SQL_DESC_COUNT auf die Anzahl der höchsten verbleibenden gebundenen Spalte festgelegt.  
  
## <a name="cautions-regarding-sql_default"></a>Vorsichtsmaßnahmen in Bezug auf SQL_DEFAULT  
 Um Spaltendaten erfolgreich abzurufen, muss die Anwendung die Länge und den Startpunkt der Daten im Anwendungspuffer korrekt bestimmen. Wenn die Anwendung einen expliziten *TargetType*angibt, werden Anwendungsfehler leicht erkannt. Wenn die Anwendung jedoch einen *TargetType* der SQL_DEFAULT angibt, kann **SQLBindCol** auf eine Spalte mit einem anderen Datentyp als der von der Anwendung beabsichtigten angewendet werden, entweder von Änderungen an den Metadaten oder durch Anwenden des Codes auf eine andere Spalte. In diesem Fall bestimmt die Anwendung möglicherweise nicht immer den Start oder die Länge der abgerufenen Spaltendaten. Dies kann zu nicht gemeldeten Datenfehlern oder Speicherverletzungen führen.  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel führt eine Anwendung eine **SELECT-Anweisung** in der Tabelle Customers aus, um eine Resultmenge der Kunden-IDs, -Namen und -Telefonnummern, sortiert nach Namen, zurückzugeben. Anschließend wird **SQLBindCol** aufruft, um die Datenspalten an lokale Puffer zu binden. Schließlich ruft die Anwendung jede Datenzeile mit **SQLFetch** ab und druckt den Namen, die ID und die Telefonnummer jedes Kunden.  
  
 Weitere Codebeispiele finden Sie unter [SQLBulkOperations Function](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLColumns Function](../../../odbc/reference/syntax/sqlcolumns-function.md), [SQLFetchScroll Function](../../../odbc/reference/syntax/sqlfetchscroll-function.md)und [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```cpp  
// SQLBindCol_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <stdio.h>  
  
#define UNICODE  
#include <sqlext.h>  
  
#define NAME_LEN 50  
#define PHONE_LEN 60
  
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
                  retcode = SQLBindCol(hstmt, 1, SQL_C_WCHAR, &sCustID, 100, &cbCustID);  
                  retcode = SQLBindCol(hstmt, 2, SQL_C_WCHAR, szName, NAME_LEN, &cbName);  
                  retcode = SQLBindCol(hstmt, 3, SQL_C_WCHAR, szPhone, PHONE_LEN, &cbPhone);   
  
                  // Fetch and print each row of data. On an error, display a message and exit.  
                  for (int i=0 ; ; i++) {  
                     retcode = SQLFetch(hstmt);  
                     if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
                        show_error();  
                     if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                     {
                        //replace wprintf with printf
                        //%S with %ls
                        //warning C4477: 'wprintf' : format string '%S' requires an argument of type 'char *'
                        //but variadic argument 2 has type 'SQLWCHAR *'
                        //wprintf(L"%d: %S %S %S\n", i + 1, sCustID, szName, szPhone);  
                        printf("%d: %ls %ls %ls\n", i + 1, sCustID, szName, szPhone);  
                    }    
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
  
 Siehe auch [Beispiel ODBC-Programm](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben von Informationen zu einer Spalte in einer Ergebnismenge|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen mehrerer Datenzeilen|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Freigeben von Spaltenpuffern für die Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Abrufen eines Teils oder der gesamten Datenspalte|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Zurückgeben der Anzahl der Ergebnissatzspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
