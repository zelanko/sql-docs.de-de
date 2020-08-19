---
description: SQLBindCol-Funktion
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
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBindCol
helpviewer_keywords:
- SQLBindCol function [ODBC]
ms.assetid: 41a37655-84cd-423f-9daa-e0b47b88dc54
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 84793bdd1261c4a2f65b1bdb60eec4a516a1a1d6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476168"
---
# <a name="sqlbindcol-function"></a>SQLBindCol-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
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
 Der Anweisungs Handle.  
  
 *ColumnNumber*  
 Der Die Nummer der zu bindenden Resultsetspalte. Spalten werden in aufsteigender Spaltenreihenfolge beginnend bei 0 nummeriert, wobei Spalte 0 die Lesezeichen Spalte ist. Wenn keine Lesezeichen verwendet werden, d. h., das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wird auf SQL_UB_OFF festgelegt, und die Spalten Nummern beginnen bei 1.  
  
 *TargetType*  
 Der Der Bezeichner des C-Datentyps des \* *targetvalueptr* -Puffers. Beim Abrufen von Daten aus der Datenquelle mit **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**oder **SQLSetPos**konvertiert der Treiber die Daten in diesen Typ. beim Senden von Daten an die Datenquelle mit **SQLBulkOperations** oder **SQLSetPos**konvertiert der Treiber die Daten von diesem Typ. Eine Liste gültiger c-Datentypen und-Typbezeichner finden Sie im Abschnitt [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen.  
  
 Wenn das *TargetType* -Argument ein Interval-Datentyp ist, werden die standardmäßige Intervall Genauigkeit (2) und die Standardgenauigkeit für Sekundenbruchteilen (6), wie in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION und SQL_DESC_PRECISION der ARD festgelegt, für die Daten verwendet. Wenn das *TargetType* -Argument SQL_C_NUMERIC ist, werden die Standardgenauigkeit (Treiber definiert) und die Standardskala (0), die in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE der ARD festgelegt sind, für die Daten verwendet. Wenn eine Standardgenauigkeit oder Dezimalstellen Angabe nicht angemessen ist, muss die Anwendung das entsprechende Deskriptorfeld explizit durch einen **SQLSetDescField** -oder **SQLSetDescRec**-Befehl festlegen.  
  
 Sie können auch einen erweiterten C-Datentyp angeben. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *Targetvalueptr*  
 [Verzögerte Eingabe/Ausgabe] Zeiger auf den Datenpuffer, der an die Spalte gebunden werden soll. **SQLFetch** und **SQLFetchScroll** geben Daten in diesem Puffer zurück. **SQLBulkOperations** gibt Daten in diesem Puffer zurück, wenn der *Vorgang* SQL_FETCH_BY_BOOKMARK ist. Es werden Daten aus diesem Puffer abgerufen, wenn der *Vorgang* SQL_ADD oder SQL_UPDATE_BY_BOOKMARK ist. **SQLSetPos** gibt Daten in diesem Puffer zurück, wenn der *Vorgang* SQL_REFRESH wird. Es werden Daten aus diesem Puffer abgerufen, wenn der *Vorgang* SQL_UPDATE wird.  
  
 Wenn *targetvalueptr* ein NULL-Zeiger ist, hebt der Treiber die Bindung des Daten Puffers für die Spalte auf. Eine Anwendung kann die Bindung aller Spalten aufheben, indem **SQLFreeStmt** mit der Option SQL_UNBIND aufgerufen wird. Eine Anwendung kann die Bindung des Daten Puffers für eine Spalte aufheben, aber trotzdem einen Längen-/indikatorenpuffer für die Spalte angeben, wenn das *targetvalueptr* -Argument im **SQLBindCol** -Befehl ein NULL-Zeiger ist, das *StrLen_or_IndPtr* -Argument jedoch ein gültiger Wert ist.  
  
 *BufferLength*  
 Der Länge des \* *targetvalueptr* -Puffers in Bytes.  
  
 Der Treiber verwendet *BufferLength* , um das Schreiben über das Ende des \* *targetvalueptr* -Puffers zu vermeiden, wenn er Daten variabler Länge zurückgibt, wie z. b. Zeichen-oder Binärdaten. Beachten Sie, dass der Treiber beim zurückkehren von Zeichendaten an \* *targetvalueptr*das NULL-Terminierungs Zeichen zählt. \**Targetvalueptr* muss daher Leerzeichen für das NULL-Terminierungs Zeichen enthalten, oder der Treiber schneidet die Daten ab.  
  
 Wenn der Treiber Daten fester Länge zurückgibt, wie z. b. eine ganze Zahl oder eine Datums Struktur, ignoriert der Treiber *BufferLength* und geht davon aus, dass der Puffer groß genug ist, um die Daten zu speichern. Daher ist es wichtig, dass die Anwendung einen ausreichend großen Puffer für Daten fester Länge zuweist oder dass der Treiber über das Ende des Puffers hinaus schreibt.  
  
 **SQLBindCol** gibt SQLSTATE HY090 (ungültige Zeichen folgen-oder Pufferlänge) zurück, wenn *BufferLength* kleiner als 0 (null) ist, aber nicht, wenn *BufferLength* gleich 0 ist Wenn *TargetType* jedoch einen Zeichentyp angibt, sollte für eine Anwendung *BufferLength* nicht auf 0 festgelegt werden, da die von der ISO-CLI kompatiblen Treiber SQLSTATE HY090 (ungültige Zeichen folgen-oder Pufferlänge) in diesem Fall zurückgeben.  
  
 *StrLen_or_IndPtr*  
 [Verzögerte Eingabe/Ausgabe] Zeiger auf den Längen-/Indikatorpuffer, der an die Spalte gebunden werden soll. **SQLFetch** und **SQLFetchScroll** geben einen Wert in diesem Puffer zurück. **SQLBulkOperations** Ruft einen Wert aus diesem Puffer ab, wenn der *Vorgang* SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_DELETE_BY_BOOKMARK ist. **SQLBulkOperations** gibt einen Wert in diesem Puffer zurück, wenn der *Vorgang* SQL_FETCH_BY_BOOKMARK wird. **SQLSetPos** gibt einen Wert in diesem Puffer zurück, wenn der *Vorgang* SQL_REFRESH wird. Wenn der *Vorgang* SQL_UPDATE wird, ruft er einen Wert aus diesem Puffer ab.  
  
 **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**und **SQLSetPos** können die folgenden Werte im length/Indicator-Puffer zurückgeben:  
  
-   Die Länge der Daten, die zurückgegeben werden können.  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Die Anwendung kann die folgenden Werte für die Verwendung mit **SQLBulkOperations** oder **SQLSetPos**in den Längen-/Indikatorpuffer einfügen:  
  
-   Die Länge der Daten, die gesendet werden.  
  
-   SQL_NTS  
  
-   SQL_NULL_DATA  
  
-   SQL_DATA_AT_EXEC  
  
-   Das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros.  
  
-   SQL_COLUMN_IGNORE  
  
 Wenn der Indikator Puffer und der Längenpuffer separate Puffer sind, kann der Indikator Puffer nur SQL_NULL_DATA zurückgeben, während der Längenpuffer alle anderen Werte zurückgeben kann.  
  
 Weitere Informationen finden Sie unter [SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)-Funktion, [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)und Verwenden von [Längen-/indikatorenwerten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Wenn *StrLen_or_IndPtr* ein NULL-Zeiger ist, wird keine Längen-oder Indikatorwerte verwendet. Dies ist ein Fehler beim Abrufen von Daten, und die Daten sind NULL.  
  
 Weitere Informationen finden Sie unter [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung unter einem 64-Bit-Betriebssystem ausgeführt wird.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLBindCol** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLBindCol** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|(DM) das *ColumnNumber* -Argument war 0, und das *TargetType* -Argument war nicht SQL_C_BOOKMARK oder SQL_C_VARBOOKMARK.|  
|07009|Ungültiger deskriptorindex.|Der für das Argument *ColumnNumber* angegebene Wert hat die maximale Anzahl von Spalten im Resultset überschritten.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY003|Ungültiger Anwendungs Puffertyp.|Das Argument *TargetType* war weder ein gültiger Datentyp noch SQL_C_DEFAULT.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als **SQLBindCol** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das *StatementHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der für das Argument *BufferLength* angegebene Wert war kleiner als 0 (null).<br /><br /> (DM) der Treiber war ODBC 2. *x* -Treiber, das *ColumnNumber* -Argument wurde auf 0 festgelegt, und der für das Argument *BufferLength* angegebene Wert war nicht gleich 4.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Der Treiber oder die Datenquelle unterstützt nicht die Konvertierung, die durch die Kombination aus dem *TargetType* -Argument und dem treiberspezifischen SQL-Datentyp der entsprechenden Spalte angegeben wird.<br /><br /> Das Argument *ColumnNumber* war 0, und der Treiber unterstützt keine Lesezeichen.<br /><br /> Der Treiber unterstützt nur ODBC 2. *x* und das *TargetType* -Argument sind eine der folgenden:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> und eines der in [c-Daten](../../../odbc/reference/appendixes/c-data-types.md) Typen aufgelisteten Interval c-Datentypen in Anhang D: Datentypen.<br /><br /> Der Treiber unterstützt nur ODBC-Versionen vor 3,50, und das *TargetType* -Argument wurde SQL_C_GUID.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 **SQLBindCol** wird verwendet, um Spalten im Resultset zu Daten Puffern und Längen-/indikatorpuffern in der Anwendung zuzuordnen oder zu *binden* . Wenn die Anwendung **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos** zum Abrufen von Daten aufruft, gibt der Treiber die Daten für die gebundenen Spalten in den angegebenen Puffern zurück. Weitere Informationen finden Sie unter [SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md). Wenn die Anwendung **SQLBulkOperations** aufruft, um eine Zeile oder **SQLSetPos** zum Aktualisieren einer Zeile zu aktualisieren oder einzufügen, ruft der Treiber die Daten für die gebundenen Spalten aus den angegebenen Puffern ab. Weitere Informationen finden Sie unter [SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md) oder [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md). Weitere Informationen zur Bindung finden Sie unter [Abrufen von Ergebnissen (Standard)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 Beachten Sie, dass Spalten nicht zum Abrufen von Daten gebunden werden müssen. Eine Anwendung kann auch **SQLGetData** aufrufen, um Daten aus Spalten abzurufen. Obwohl es möglich ist, einige Spalten in einer Zeile zu binden und **SQLGetData** für andere aufzurufen, unterliegt dies einigen Einschränkungen. Weitere Informationen finden Sie unter [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
## <a name="binding-unbinding-and-rebinding-columns"></a>Binden, Aufheben der Bindung und neubinden von Spalten  
 Eine Spalte kann zu einem beliebigen Zeitpunkt gebunden, ungebunden oder erneut gebunden werden, auch nachdem die Daten aus dem Resultset abgerufen wurden. Die neue Bindung wird wirksam, wenn eine Funktion, die Bindungen verwendet, das nächste Mal aufgerufen wird. Nehmen wir beispielsweise an, dass eine Anwendung die Spalten in einem Resultset bindet und **SQLFetch**aufruft. Der Treiber gibt die Daten in den gebundenen Puffern zurück. Nehmen Sie nun an, dass die Anwendung die Spalten an einen anderen Satz von Puffern bindet. Der Treiber legt die Daten für die gerade abgerufene Zeile in den neu gebundenen Puffern nicht ab. Stattdessen wird gewartet, bis **SQLFetch** erneut aufgerufen wird, und dann werden die Daten für die nächste Zeile in den neu gebundenen Puffern platziert.  
  
> [!NOTE]  
>  Das Anweisungs Attribut SQL_ATTR_USE_BOOKMARKS sollte immer festgelegt werden, bevor eine Spalte an Spalte 0 gebunden wird. Dies ist nicht erforderlich, wird jedoch dringend empfohlen.  
  
## <a name="binding-columns"></a>Binden von Spalten  
 Um eine Spalte zu binden, ruft eine Anwendung **SQLBindCol** auf und übergibt die Spaltennummer, den Typ, die Adresse und die Länge eines Daten Puffers sowie die Adresse eines Längen-/indikatorenpuffers. Informationen dazu, wie diese Adressen verwendet werden, finden Sie unter "Puffer Adressen" weiter unten in diesem Abschnitt. Weitere Informationen zum Binden von Spalten finden [Sie unter Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Die Verwendung dieser Puffer wird verzögert. Das heißt, die Anwendung bindet Sie in **SQLBindCol** , aber der Treiber greift von anderen Funktionen aus, also **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos**. Es liegt in der Verantwortung der Anwendung, sicherzustellen, dass die in **SQLBindCol** angegebenen Zeiger gültig bleiben, solange die Bindung weiterhin gültig ist. Wenn die Anwendung zulässt, dass diese Zeiger ungültig werden, z. b. Wenn Sie einen Puffer freigibt und dann eine Funktion aufruft, die erwartet, dass Sie gültig sind, sind die Folgen nicht definiert. Weitere Informationen finden Sie unter [verzögerte Puffer](../../../odbc/reference/develop-app/deferred-buffers.md).  
  
 Die Bindung bleibt wirksam, bis Sie durch eine neue Bindung ersetzt wird, dass die Spalte ungebunden ist oder die Anweisung freigegeben wird.  
  
## <a name="unbinding-columns"></a>Aufheben der Bindung von Spalten  
 Zum Aufheben der Bindung einer einzelnen Spalte Ruft eine Anwendung **SQLBindCol** auf, wobei *ColumnNumber* auf die Nummer dieser Spalte und *targetvalueptr* auf einen NULL-Zeiger festgelegt ist. Wenn *ColumnNumber* auf eine ungebundene Spalte verweist, gibt **SQLBindCol** weiterhin SQL_SUCCESS zurück.  
  
 Um die Bindung aller Spalten aufzuheben, ruft eine Anwendung **SQLFreeStmt** auf, wobei *fOption* auf SQL_UNBIND festgelegt ist. Dies kann auch erreicht werden, indem das SQL_DESC_COUNT-Feld der ARD auf NULL festgelegt wird.  
  
## <a name="rebinding-columns"></a>Neubinden von Spalten  
 Eine Anwendung kann eine der beiden Vorgänge ausführen, um eine Bindung zu ändern:  
  
-   Aufrufen von **SQLBindCol** , um eine neue Bindung für eine Spalte anzugeben, die bereits gebunden ist. Der Treiber überschreibt die alte Bindung mit der neuen.  
  
-   Geben Sie einen Offset an, der der Puffer Adresse hinzugefügt werden soll, die durch den Bindungs Befehl **SQLBindCol**angegeben wurde. Weitere Informationen finden Sie im nächsten Abschnitt "Bindungs Offsets".  
  
## <a name="binding-offsets"></a>Bindungs Offsets  
 Ein Bindungs Offset ist ein Wert, der den Adressen der Daten-und Längen-/Indikatorpuffer (wie in der *targetvalueptr* -und *StrLen_or_IndPtr* -Argument angegeben) hinzugefügt wird, bevor Sie dereferenziert werden. Wenn Offsets verwendet werden, sind die Bindungen eine "Vorlage" dafür, wie die Puffer der Anwendung angelegt werden, und die Anwendung kann diese "Vorlage" durch Ändern des Offsets in verschiedene Speicherbereiche verschieben. Da der gleiche Offset jeder Adresse in jeder Bindung hinzugefügt wird, müssen die relativen Offsets zwischen Puffern für verschiedene Spalten innerhalb der einzelnen Puffer Sätze identisch sein. Dies gilt immer, wenn die zeilenweise Bindung verwendet wird. die Anwendung muss die Puffer sorgfältig anordnen, damit dies wahr ist, wenn die spaltenweise Bindung verwendet wird.  
  
 Die Verwendung eines Bindungs Offsets hat im Grunde denselben Effekt wie das erneute Binden einer Spalte durch Aufrufen von **SQLBindCol**. Der Unterschied besteht darin, dass ein neuer **SQLBindCol** -Befehl neue Adressen für den Datenpuffer und den Längen-/Indikatorpuffer angibt, während die Verwendung eines Bindungs Offsets die Adressen nicht ändert, sondern lediglich einen Offset hinzufügt. Die Anwendung kann einen neuen Offset angeben, wenn Sie möchten, und dieser Offset wird immer den ursprünglich gebundenen Adressen hinzugefügt. Insbesondere, wenn der Offset auf 0 festgelegt ist oder das Anweisungs Attribut auf einen NULL-Zeiger festgelegt ist, verwendet der Treiber die ursprünglich gebundenen Adressen.  
  
 Um einen Bindungs Offset anzugeben, legt die Anwendung das SQL_ATTR_ROW_BIND_OFFSET_PTR Statement-Attribut auf die Adresse eines SQLINTEGER-Puffers fest. Bevor die Anwendung eine Funktion aufruft, die Bindungen verwendet, versetzt Sie einen Offset in Bytes in diesen Puffer. Um die Adresse des zu verwendenden Puffers zu bestimmen, fügt der Treiber den Offset der Adresse in der Bindung hinzu. Die Summe der Adresse und des Offsets muss eine gültige Adresse sein, aber die Adresse, zu der der Offset hinzugefügt wird, muss ungültig sein. Weitere Informationen zur Verwendung von Bindungs Offsets finden Sie unter "Puffer Adressen" weiter unten in diesem Abschnitt.  
  
## <a name="binding-arrays"></a>Binden von Arrays  
 Wenn die Rowsetgröße (der Wert des SQL_ATTR_ROW_ARRAY_SIZE-Anweisungs Attributs) größer als 1 ist, bindet die Anwendung die Puffer Arrays anstelle einzelner Puffer. Weitere Informationen finden Sie unter [Blockcursorn](../../../odbc/reference/develop-app/block-cursors.md).  
  
 Die Anwendung kann Arrays auf zwei Arten binden:  
  
-   Binden Sie ein Array an jede Spalte. Dies wird als *spaltenweise Bindung* bezeichnet, da jede Datenstruktur (Array) Daten für eine einzelne Spalte enthält.  
  
-   Definieren Sie eine Struktur, in der die Daten für eine ganze Zeile enthalten sind, und binden Sie ein Array dieser Strukturen. Dies wird als *Zeilen weises binden* bezeichnet, da jede Datenstruktur die Daten für eine einzelne Zeile enthält.  
  
 Jedes Puffer Array muss mindestens so viele Elemente aufweisen wie die Größe des Rowsets.  
  
> [!NOTE]  
>  Eine Anwendung muss überprüfen, ob die Ausrichtung gültig ist. Weitere Informationen zu Ausrichtungs Überlegungen finden Sie unter [Alignment](../../../odbc/reference/develop-app/alignment.md).  
  
## <a name="column-wise-binding"></a>Spaltenbezogenes Binden  
 In Spalten weiser Bindung bindet die Anwendung separate Daten-und Längen-/indikatorenarrays an jede Spalte.  
  
 Um die spaltenweise Bindung zu verwenden, legt die Anwendung zuerst das SQL_ATTR_ROW_BIND_TYPE Statement-Attribut auf SQL_BIND_BY_COLUMN fest. (Dies ist die Standardeinstellung.) Für jede Spalte, die gebunden werden soll, führt die Anwendung die folgenden Schritte aus:  
  
1.  Ordnet ein Datenpuffer Array zu.  
  
2.  Ordnet ein Array von Längen-/indikatorenpuffern zu.  
  
    > [!NOTE]  
    >  Wenn die Anwendung bei Verwendung der Spalten bezogenen Bindung direkt in Deskriptoren schreibt, können separate Arrays für Längen-und Indikator Daten verwendet werden.  
  
3.  Ruft **SQLBindCol** mit den folgenden Argumenten auf:  
  
    -   *TargetType* ist der Typ eines einzelnen Elements im Datenpuffer Array.  
  
    -   *Targetvalueptr* ist die Adresse des Datenpuffer Arrays.  
  
    -   *BufferLength* ist die Größe eines einzelnen Elements im Datenpuffer Array. Das *BufferLength* -Argument wird ignoriert, wenn die Daten Daten fester Länge haben.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des Längen-/indikatorenarrays.  
  
 Weitere Informationen zur Verwendung dieser Informationen finden Sie unter "Puffer Adressen" weiter unten in diesem Abschnitt. Weitere Informationen zur Spalten bezogenen Bindung finden Sie unter [spaltenweise Bindung](../../../odbc/reference/develop-app/column-wise-binding.md).  
  
## <a name="row-wise-binding"></a>Zeilenbezogenes Binden  
 In Zeilen weiser Bindung definiert die Anwendung eine-Struktur, die Daten und Längen-/Indikatorpuffer für jede zu gebundene Spalte enthält.  
  
 Die Anwendung führt die folgenden Schritte aus, um die zeilenweise Bindung zu verwenden:  
  
1.  Definiert eine-Struktur, die eine einzelne Daten Zeile (einschließlich der Daten-und Längen-/Indikatorpuffer) enthält und ein Array dieser Strukturen zuordnet.  
  
    > [!NOTE]  
    >  Wenn die Anwendung bei Verwendung der Zeilen bezogenen Bindung direkt in Deskriptoren schreibt, können separate Felder für Längen-und Indikator Daten verwendet werden.  
  
2.  Legt das SQL_ATTR_ROW_BIND_TYPE Anweisungs Attribut auf die Größe der Struktur fest, die eine einzelne Daten Zeile enthält, oder auf die Größe einer Instanz eines Puffers, in den die Ergebnis Spalten gebunden werden. Die Länge muss Leerzeichen für alle gebundenen Spalten und alle Auffüll Zeichen der Struktur oder des Puffers enthalten, um sicherzustellen, dass das Ergebnis, wenn die Adresse einer gebundenen Spalte mit der angegebenen Länge inkrementiert wird, auf den Anfang derselben Spalte in der nächsten Zeile zeigt. Wenn der *sizeof* -Operator in ANSI C verwendet wird, ist dieses Verhalten garantiert.  
  
3.  Ruft **SQLBindCol** mit den folgenden Argumenten für jede Spalte auf, die gebunden werden soll:  
  
    -   *TargetType* ist der Typ des Datenpuffer Members, der an die Spalte gebunden werden soll.  
  
    -   *Targetvalueptr* ist die Adresse des Datenpuffer Members im ersten Array Element.  
  
    -   *BufferLength* ist die Größe des Datenpuffer Members.  
  
    -   *StrLen_or_IndPtr* ist die Adresse des Längen-/indikatorenmembers, der gebunden werden soll.  
  
 Weitere Informationen zur Verwendung dieser Informationen finden Sie unter "Puffer Adressen" weiter unten in diesem Abschnitt. Weitere Informationen zur Spalten bezogenen Bindung finden Sie unter [Zeilen weises binden](../../../odbc/reference/develop-app/row-wise-binding.md).  
  
## <a name="buffer-addresses"></a>Puffer Adressen  
 Die *Puffer Adresse* ist die tatsächliche Adresse des Daten-oder Längen-/Indikatorpuffers. Der Treiber berechnet die Puffer Adresse unmittelbar vor dem Schreiben in die Puffer (z. b. während der Abruf Zeit). Der Wert wird anhand der folgenden Formel berechnet, in der die in den *targetvalueptr* -und *StrLen_or_IndPtr* -Argumenten angegebenen Adressen, der Bindungs Offset und die Zeilennummer verwendet werden:  
  
 *Gebundene Adresse*  +  *Bindungs Offset* + ((*Zeilennummer* -1) x- *Element Größe*)  
  
 Dabei werden die Variablen der Formel wie in der folgenden Tabelle beschrieben definiert.  
  
|Variable|Beschreibung|  
|--------------|-----------------|  
|*Gebundene Adresse*|Für Datenpuffer die mit dem *targetvalueptr* -Argument in **SQLBindCol**angegebene Adresse.<br /><br /> Für Längen-/Indikatorpuffer die mit dem *StrLen_or_IndPtr* -Argument in **SQLBindCol**angegebene Adresse. Weitere Informationen finden Sie unter "Weitere Kommentare" im Abschnitt "Deskriptors und SQLBindCol".<br /><br /> Wenn die gebundene Adresse 0 ist, wird kein Datenwert zurückgegeben, auch wenn die Adresse, wie von der vorherigen Formel berechnet, ungleich 0 (null) ist.|  
|*Bindungs Offset*|Wenn die zeilenweise Bindung verwendet wird, wird der Wert an der Adresse gespeichert, die mit dem SQL_ATTR_ROW_BIND_OFFSET_PTR Statement-Attribut angegeben wird.<br /><br /> Wenn die spaltenweise Bindung verwendet wird oder wenn der Wert des SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungs Attributs ein NULL-Zeiger ist, ist der *Bindungs Offset* 0.|  
|*Zeilennummer*|Die 1-basierte Nummer der Zeile im Rowset. Bei einzeiligen Abruf Vorgängen, bei denen es sich um die Standardeinstellung handelt, ist dies 1.|  
|*Element Größe*|Die Größe eines Elements im gebundenen Array.<br /><br /> Wenn die spaltenweise Bindung verwendet wird, ist dies **sizeof (SQLINTEGER)** für Längen-/Indikatorpuffer. Für Datenpuffer ist dies der Wert des *BufferLength* -Arguments in **SQLBindCol** , wenn der Datentyp eine Variable Länge ist, und die Größe des Datentyps, wenn der Datentyp eine festgelegte Länge hat.<br /><br /> Wenn die zeilenweise Bindung verwendet wird, ist dies der Wert des SQL_ATTR_ROW_BIND_TYPE-Anweisungs Attributs für Daten-und Längen-/Indikatorpuffer.|  
  
## <a name="descriptors-and-sqlbindcol"></a>Deskriptoren und SQLBindCol  
 In den folgenden Abschnitten wird beschrieben, wie **SQLBindCol** mit Deskriptoren interagiert.  
  
> [!CAUTION]  
>  Das Aufrufen von **SQLBindCol** für eine Anweisung kann sich auf andere-Anweisungen auswirken. Dies tritt auf, wenn der mit der-Anweisung verknüpfte ARD explizit zugeordnet und auch anderen-Anweisungen zugeordnet wird. Da **SQLBindCol** den Deskriptor ändert, gelten die Änderungen für alle-Anweisungen, die diesem Deskriptor zugeordnet sind. Wenn dies nicht das erforderliche Verhalten ist, muss die Anwendung diesen Deskriptor von den anderen Anweisungen trennen, bevor **SQLBindCol**aufgerufen wird.  
  
## <a name="argument-mappings"></a>Argument Zuordnungen  
 Konzeptionell führt **SQLBindCol** die folgenden Schritte nacheinander aus:  
  
1.  Ruft **SQLGetStmtAttr** auf, um das ARD-Handle abzurufen.  
  
2.  Ruft **SQLGetDescField** auf, um das SQL_DESC_COUNT Feld dieses Deskriptors zu erhalten, und wenn der Wert im *ColumnNumber* -Argument den Wert von SQL_DESC_COUNT überschreitet, ruft **SQLSetDescField** auf, um den Wert von SQL_DESC_COUNT auf *ColumnNumber*zu erhöhen.  
  
3.  Ruft **SQLSetDescField** mehrmals auf, um den folgenden Feldern der ARD Werte zuzuweisen:  
  
    -   Legt SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE auf den Wert von *TargetType*fest, mit dem Unterschied, dass, wenn *TargetType* einer der präziseren Bezeichner eines DateTime-oder Interval-unter Typs ist, SQL_DESC_TYPE auf SQL_DATETIME bzw. SQL_INTERVAL festgelegt wird. legt SQL_DESC_CONCISE_TYPE auf den präzisen Bezeichner fest. und legt SQL_DESC_DATETIME_INTERVAL_CODE auf den entsprechenden DateTime-oder Interval-Subcode fest.  
  
    -   Legt eine oder mehrere SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_DATETIME_INTERVAL_PRECISION entsprechend für *TargetType*fest.  
  
    -   Legt das SQL_DESC_OCTET_LENGTH-Feld auf den Wert von *BufferLength*fest.  
  
    -   Legt das SQL_DESC_DATA_PTR-Feld auf den Wert von *TargetValue*fest.  
  
    -   Legt das SQL_DESC_INDICATOR_PTR-Feld auf den Wert *StrLen_Or_Ind*fest. (Weitere Informationen finden Sie im folgenden Abschnitt.)  
  
    -   Legt das SQL_DESC_OCTET_LENGTH_PTR-Feld auf den Wert *StrLen_Or_Ind*fest. (Weitere Informationen finden Sie im folgenden Abschnitt.)  
  
 Die Variable, auf die das *StrLen_Or_Ind* -Argument verweist, wird sowohl für Indikator-als auch für Längen Informationen verwendet. Wenn ein Abruf Vorgang einen NULL-Wert für die Spalte ermittelt, speichert er SQL_NULL_DATA in dieser Variablen. Andernfalls wird die Daten Länge in dieser Variablen gespeichert. Wenn ein NULL-Zeiger als *StrLen_Or_Ind* übergeben wird, wird der Abruf Vorgang von der Rückgabe der Daten Länge beendet, der Abruf schlägt jedoch fehl, wenn ein NULL-Wert gefunden wird und keine Möglichkeit besteht, SQL_NULL_DATA zurückzugeben.  
  
 Wenn der **SQLBindCol** -Befehl fehlschlägt, sind die Inhalte der Deskriptorfelder, die in der ARD festgelegt wurden, nicht definiert, und der Wert des SQL_DESC_COUNT-Felds der ARD bleibt unverändert.  
  
## <a name="implicit-resetting-of-count-field"></a>Implizites Zurücksetzen des zählungs Felds  
 **SQLBindCol** legt SQL_DESC_COUNT nur auf den Wert des *ColumnNumber* -Arguments fest, wenn dadurch der Wert SQL_DESC_COUNT erhöht würde. Wenn der Wert im *targetvalueptr* -Argument ein NULL-Zeiger ist und der Wert im *ColumnNumber* -Argument gleich SQL_DESC_COUNT ist (d. h. beim Aufheben der Bindung der höchsten gebundenen Spalte), wird SQL_DESC_COUNT auf die Nummer der höchsten verbleibenden gebundenen Spalte festgelegt.  
  
## <a name="cautions-regarding-sql_default"></a>Vorsichts Hinweise bezüglich SQL_DEFAULT  
 Zum erfolgreichen Abrufen von Spaltendaten muss die Anwendung die Länge und den Anfangspunkt der Daten im Anwendungs Puffer ordnungsgemäß bestimmen. Wenn die Anwendung einen expliziten *TargetType*angibt, werden falsche Anwendungs Missverständnisse erkannt. Wenn die Anwendung jedoch einen *TargetType* von SQL_DEFAULT angibt, kann **SQLBindCol** auf eine Spalte mit einem anderen Datentyp als der von der Anwendung vorgesehenen Datentyp angewendet werden, entweder von Änderungen an den Metadaten oder durch Anwenden des Codes auf eine andere Spalte. In diesem Fall kann die Anwendung nicht immer den Anfang oder die Länge der abgerufenen Spaltendaten ermitteln. Dies kann zu nicht gemeldeten Datenfehlern oder Speicher Verletzungen führen.  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel führt eine Anwendung eine **Select** -Anweisung für die Customers-Tabelle aus, um ein Resultset der Kunden-IDs,-Namen und Telefonnummern nach Namen sortiert zurückzugeben. Anschließend wird **SQLBindCol** aufgerufen, um die Spalten der Daten an lokale Puffer zu binden. Schließlich ruft die Anwendung jede Daten Zeile mit **SQLFetch** ab und gibt den Namen, die ID und die Telefonnummer jedes Kunden aus.  
  
 Weitere Codebeispiele finden Sie in der [SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md), der [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)-Funktion, der [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)-Funktion und der [SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
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
  
 Siehe auch [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen mehrerer Daten Zeilen|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Freigeben von Spalten Puffern in der Anweisung|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Abrufen eines Teils oder aller Datenspalten|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Zurückgeben der Anzahl von Resultsetspalten|[SQLNumResultCols-Funktion](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
