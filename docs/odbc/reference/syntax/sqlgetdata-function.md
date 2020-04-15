---
title: SQLGetData-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetData
helpviewer_keywords:
- SQLGetData function [ODBC]
ms.assetid: e3c1356a-5db7-4186-85fd-8b74633317e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac11505b8e47dae8df53af27c64a7ee6372b3f28
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285506"
---
# <a name="sqlgetdata-function"></a>SQLGetData-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetData** ruft Daten für eine einzelne Spalte im Resultset oder für einen einzelnen Parameter ab, nachdem **SQLParamData** SQL_PARAM_DATA_AVAILABLE zurückgegeben hat. Es kann mehrmals aufgerufen werden, um Daten variabler Länge in Teilen abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetData(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   Col_or_Param_Num,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_IndPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *Col_or_Param_Num*  
 [Eingabe] Zum Abrufen von Spaltendaten ist dies die Nummer der Spalte, für die Daten zurückgegeben werden sollen. Ergebnissatzspalten werden in zunehmender Spaltenreihenfolge ab 1 nummeriert. Die Textzeichenspalte ist Spaltennummer 0; Dies kann nur angegeben werden, wenn Lesezeichen aktiviert sind.  
  
 Zum Abrufen von Parameterdaten ist es die Ordnung des Parameters, die bei 1 beginnt.  
  
 *Targettype*  
 [Eingabe] Der Typbezeichner des C-Datentyps des **TargetValuePtr-Puffers.* Eine Liste gültiger C-Datentypen und Typbezeichner finden Sie im Abschnitt [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen.  
  
 Wenn *TargetType* SQL_ARD_TYPE ist, verwendet der Treiber den Typbezeichner, der im Feld SQL_DESC_CONCISE_TYPE der ARD angegeben ist. Wenn *TargetType* SQL_APD_TYPE ist, verwendet **SQLGetData** denselben C-Datentyp, der in **SQLBindParameter**angegeben wurde. Andernfalls überschreibt der in **SQLGetData** angegebene C-Datentyp den in **SQLBindParameter**angegebenen C-Datentyp . Wenn es sich um SQL_C_DEFAULT, wählt der Treiber den Standardmäßigen C-Datentyp basierend auf dem SQL-Datentyp der Quelle aus.  
  
 Sie können auch einen erweiterten C-Datentyp angeben. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *TargetValuePtr*  
 [Ausgabe] Zeigen Sie auf den Puffer, in dem die Daten zurückgegeben werden sollen.  
  
 *TargetValuePtr* kann nicht NULL sein.  
  
 *BufferLength*  
 [Eingabe] Länge des **TargetValuePtr-Puffers* in Bytes.  
  
 Der Treiber verwendet *BufferLength,* um zu \*vermeiden, dass das Ende des TargetValuePtr-Puffers beim Zurückgeben von Variablenlängendaten, z. B. Zeichen- oder Binärdaten, über das Ende des *TargetValuePtr-Puffers* hinausgeschrieben wird. Beachten Sie, dass der Treiber das Null-Beendigungszeichen zählt, wenn Zeichendaten an \* *TargetValuePtr*zurückgegeben werden. **TargetValuePtr* muss daher Platz für das Null-Beendigungszeichen enthalten, da der Treiber die Daten abnimmt.  
  
 Wenn der Treiber Daten fester Länge zurückgibt, z. B. eine ganze Zahl oder eine Datumsstruktur, ignoriert der Treiber *BufferLength* und geht davon aus, dass der Puffer groß genug ist, um die Daten zu halten. Daher ist es wichtig, dass die Anwendung einen ausreichend großen Puffer für Daten fester Länge zuweist, oder der Treiber schreibt über das Ende des Puffers hinaus.  
  
 **SQLGetData** gibt SQLSTATE HY090 (Ungültige Zeichenfolge oder Pufferlänge) zurück, wenn *BufferLength* kleiner als 0 ist, aber nicht, wenn *BufferLength* 0 ist.  
  
 *StrLen_or_IndPtr*  
 [Ausgabe] Zeiger auf den Puffer, in dem die Länge oder der Indikatorwert zurückgegeben werden soll. Wenn es sich um einen Nullzeiger handelt, wird kein Längen- oder Indikatorwert zurückgegeben. Dies gibt einen Fehler zurück, wenn die abgerufenen Daten NULL sind.  
  
 **SQLGetData** kann die folgenden Werte im Längen-/Indikatorpuffer zurückgeben:  
  
-   Die Länge der zur Rückgabe verfügbaren Daten  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Weitere Informationen finden Sie unter [Verwenden von Längen-/Indikatorwerten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md) und "Kommentare" in diesem Thema.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetData** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLGetData** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Nicht alle Daten für die angegebene *Spalte, Col_or_Param_Num*, konnten in einem einzigen Aufruf der Funktion abgerufen werden. SQL_NO_TOTAL oder die Länge der Daten, die vor dem aktuellen Aufruf von \* **SQLGetData** in der angegebenen Spalte verbleiben, wird in *StrLen_or_IndPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> Weitere Informationen zur Verwendung mehrerer Aufrufe von **SQLGetData** für eine einzelne Spalte finden Sie unter "Kommentare".|  
|01S07|Bruchschnitt|Die für eine oder mehrere Spalten zurückgegebenen Daten wurden abgeschnitten. Bei numerischen Datentypen wurde der Bruchteil der Zahl abgeschnitten. Für Zeit-, Zeitstempel- und Intervalldatentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|Der Datenwert einer Spalte im Resultset kann nicht in den Vom Argument *TargetType*angegebenen Datentyp C konvertiert werden.|  
|07009|Ungültiger Deskriptorindex|Der für das Argument *Col_or_Param_Num* angegebene Wert war 0, und das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung wurde auf SQL_UB_OFF festgelegt.<br /><br /> Der für das Argument *Col_or_Param_Num* angegebene Wert war größer als die Anzahl der Spalten im Resultset.<br /><br /> Der *Col_or_Param_Num* Wert war nicht gleich der Ordnung des verfügbaren Parameters.<br /><br /> (DM) Die angegebene Spalte war gebunden. Diese Beschreibung gilt nicht für Treiber, die die SQL_GD_BOUND Bitmaske für die Option SQL_GETDATA_EXTENSIONS in **SQLGetInfo**zurückgeben.<br /><br /> (DM) Die Anzahl der angegebenen Spalte war kleiner oder gleich der Anzahl der am höchsten gebundenen Spalte. Diese Beschreibung gilt nicht für Treiber, die die SQL_GD_ANY_COLUMN Bitmaske für die Option SQL_GETDATA_EXTENSIONS in **SQLGetInfo**zurückgeben.<br /><br /> (DM) Die Anwendung hat **sqlGetData** für die aktuelle Zeile bereits aufgerufen. Die Nummer der im aktuellen Aufruf angegebenen Spalte war kleiner als die Nummer der Spalte, die im vorherigen Aufruf angegeben wurde. und der Treiber gibt die SQL_GD_ANY_ORDER Bitmaske für die Option SQL_GETDATA_EXTENSIONS in **SQLGetInfo**nicht zurück.<br /><br /> (DM) Das *TargetType-Argument* wurde SQL_ARD_TYPE, und der *Col_or_Param_Num* Deskriptordatensatz in der ARD hat die Konsistenzprüfung nicht bestanden.<br /><br /> (DM) Das *TargetType-Argument* war SQL_ARD_TYPE, und der Wert im SQL_DESC_COUNT Feld der ARD war geringer als das *argument Col_or_Param_Num.*|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|22002|Indikatorvariable erforderlich, aber nicht mitgeliefert|*StrLen_or_IndPtr* war ein Nullzeiger, und NULL-Daten wurden abgerufen.|  
|22003|Numerischer Wert aofc|Das Zurückgeben des numerischen Werts (als numerische oder Zeichenfolge) für die Spalte hätte dazu geführt, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde.<br /><br /> Weitere Informationen finden Sie in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22007|Ungültiges Datumszeitformat|Die Zeichenspalte im Resultset war an ein C-Datum, eine Uhrzeit oder eine Zeitstempelstruktur gebunden, und der Wert in der Spalte war ein ungültiges Datum, eine ungültige Uhrzeit bzw. ein Zeitstempel. Weitere Informationen finden Sie in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).|  
|22012|Division durch Null|Ein Wert aus einem arithmetischen Ausdruck, der zur Division durch Null führte, wurde zurückgegeben.|  
|22015|Intervallfeldüberlauf|Das Zuweisen eines SQL-Typs aus einem exakten numerischen oder Intervall-SQL-Typ zu einem Intervall-C-Typ verursachte einen Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Beim Zurückgeben von Daten in einen Intervall-C-Typ gab es keine Darstellung des Wertes des SQL-Typs im Intervall-C-Typ.|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|Eine Zeichenspalte im Resultset wurde an einen Zeichen-C-Puffer zurückgegeben, und die Spalte enthielt ein Zeichen, für das der Zeichensatz des Puffers nicht dargestellt wurde.<br /><br /> Der C-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. Der SQL-Typ der Spalte war ein Zeichendatentyp; und der Wert in der Spalte war kein gültiges Literal des gebundenen C-Typs.|  
|24.000|Ungültiger Cursorstatus|(DM) Die Funktion wurde aufgerufen, ohne zuerst **SQLFetch** oder **SQLFetchScroll** aufzurufen, um den Cursor in der erforderlichen Datenzeile zu positionieren.<br /><br /> (DM) Der *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.<br /><br /> Ein Cursor wurde für *das StatementHandle* geöffnet und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen, aber der Cursor wurde vor dem Anfang des Resultsets oder nach dem Ende des Resultsets positioniert.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im *MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY003|Programmtyp a-range|(DM) Das Argument *TargetType* war kein gültiger Datentyp, SQL_C_DEFAULT, SQL_ARD_TYPE (im Falle des Abrufens von Spaltendaten) oder SQL_APD_TYPE (im Falle des Abrufens von Parameterdaten).<br /><br /> (DM) Das Argument *Col_or_Param_Num* war 0, und das Argument *TargetType* war nicht für eine Textmarke mit fester Länge SQL_C_BOOKMARK oder SQL_C_VARBOOKMARK für eine Lesezeichen variabler Länge.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für den *StatementHandle*aufgerufen, und dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen, und dann wurde die Funktion erneut im *StatementHandle*aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) Das Argument *TargetValuePtr* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Der angegebene *StatementHandle* befand sich nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute** oder eine Katalogfunktion aufzurufen.<br /><br /> (DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLGetData-Funktion** aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Der *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.<br /><br /> Ein Aufruf von **SQLExeceute**, **SQLExecDirect**oder **SQLMoreResults** wurde SQL_PARAM_DATA_AVAILABLE zurückgegeben, aber **SQLGetData** wurde anstelle von **SQLParamData**aufgerufen.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der für das Argument *BufferLength* angegebene Wert war kleiner als 0.<br /><br /> Der für das Argument *BufferLength* angegebene Wert war kleiner als 4, das *argument Col_or_Param_Num* wurde auf 0 festgelegt, und der Treiber war ein ODBC 2 *.x-Treiber.*|  
|HY109|Ungültige Cursorposition|Der Cursor wurde (von **SQLSetPos**, **SQLFetch**, **SQLFetchScroll**oder **SQLBulkOperations**) in einer Zeile positioniert, die gelöscht wurde oder nicht abgerufen werden konnte.<br /><br /> Der Cursor war ein Vorwärtscursor, und die Rowsetgröße war größer als eincursor.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der Treiber oder die Datenquelle unterstützt nicht die Verwendung von **SQLGetData** mit mehreren Zeilen in **SQLFetchScroll**. Diese Beschreibung gilt nicht für Treiber, die die SQL_GD_BLOCK Bitmaske für die Option SQL_GETDATA_EXTENSIONS in **SQLGetInfo**zurückgeben.<br /><br /> Der Treiber oder die Datenquelle unterstützt die Konvertierung, die durch die Kombination des *TargetType-Arguments* und des SQL-Datentyps der entsprechenden Spalte angegeben wird, nicht. Dieser Fehler tritt nur zu, wenn der SQL-Datentyp der Spalte einem treiberspezifischen SQL-Datentyp zugeordnet wurde.<br /><br /> Der Treiber unterstützt nur ODBC 2 *.x*, und das Argument *TargetType* war eines der folgenden:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> und alle In-Intervall-C-Datentypen, die in [Anhang](../../../odbc/reference/appendixes/c-data-types.md) D: Datentypen aufgeführt sind.<br /><br /> Der Treiber unterstützt nur ODBC-Versionen vor 3.50, und das Argument *TargetType* wurde SQL_C_GUID.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* entsprechende Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLGetData** gibt die Daten in einer angegebenen Spalte zurück. **SQLGetData** kann nur aufgerufen werden, nachdem eine oder mehrere Zeilen aus dem Resultset von **SQLFetch**, **SQLFetchScroll**oder **SQLExtendedFetch**abgerufen wurden. Wenn Daten variabler Länge zu groß sind, um in einem einzelnen Aufruf von **SQLGetData** zurückgegeben zu werden (aufgrund einer Einschränkung in der Anwendung), kann **SQLGetData** sie in Teilen abrufen. Es ist möglich, einige Spalten in einer Zeile zu binden und **SQLGetData** für andere aufzurufen, obwohl dies einigen Einschränkungen unterliegt. Weitere Informationen finden Sie unter [Abrufen langer Daten](../../../odbc/reference/develop-app/getting-long-data.md).  
  
 Informationen zur Verwendung von **SQLGetData** mit gestreamten Ausgabeparametern finden Sie unter [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-sqlgetdata"></a>Verwenden von SQLGetData  
 Wenn der Treiber keine Erweiterungen von **SQLGetData**unterstützt, kann die Funktion Daten nur für ungebundene Spalten zurückgeben, deren Zahl größer ist als die der letzten gebundenen Spalte. Darüber hinaus muss innerhalb einer Datenzeile der Wert des *Col_or_Param_Num-Arguments* in jedem Aufruf von **SQLGetData** größer oder gleich dem Wert von *Col_or_Param_Num* im vorherigen Aufruf sein. Das heißt, Daten müssen in zunehmender Spaltennummernreihenfolge abgerufen werden. Wenn keine Erweiterungen unterstützt werden, kann **SQLGetData** nicht aufgerufen werden, wenn die Rowsetgröße größer als 1 ist.  
  
 Autofahrer können jede dieser Einschränkungen lockern. Um zu bestimmen, welche Einschränkungen ein Treiber ausgelockert wird, ruft eine Anwendung **SQLGetInfo** mit einer der folgenden SQL_GETDATA_EXTENSIONS Optionen auf:  
  
-   SQL_GD_OUTPUT_PARAMS = **SQLGetData** kann aufgerufen werden, um Ausgabeparameterwerte zurückzugeben. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_GD_ANY_COLUMN. Wenn diese Option zurückgegeben wird, kann **SQLGetData** für jede ungebundene Spalte aufgerufen werden, einschließlich der Spalten vor der letzten gebundenen Spalte.  
  
-   SQL_GD_ANY_ORDER. Wenn diese Option zurückgegeben wird, kann **SQLGetData** für ungebundene Spalten in beliebiger Reihenfolge aufgerufen werden.  
  
-   SQL_GD_BLOCK. Wenn diese Option von **SQLGetInfo** für die SQL_GETDATA_EXTENSIONS InfoType zurückgegeben wird, unterstützt der Treiber Aufrufe von **SQLGetData,** wenn die Rowsetgröße größer als 1 ist und die Anwendung **SQLSetPos** mit der Option SQL_POSITION aufrufen kann, um den Cursor in der richtigen Zeile zu positionieren, bevor **SIE SQLGetData aufruft.**  
  
-   SQL_GD_BOUND. Wenn diese Option zurückgegeben wird, kann **SQLGetData** für gebundene Spalten sowie ungebundene Spalten aufgerufen werden.  
  
 Es gibt zwei Ausnahmen von diesen Einschränkungen und die Fähigkeit eines Fahrers, sie zu entspannen. Erstens sollte **SQLGetData** niemals für einen Vorwärtscursor aufgerufen werden, wenn die Rowsetgröße größer als 1 ist. Zweitens, wenn ein Treiber Lesezeichen unterstützt, muss er immer die Möglichkeit unterstützen, **SQLGetData** für Spalte 0 aufzurufen, auch wenn es Anwendungen nicht erlaubt, **SQLGetData** für andere Spalten vor der letzten gebundenen Spalte aufzurufen. (Wenn eine Anwendung mit einem ODBC 2 *.x-Treiber* arbeitet, gibt **SQLGetData** erfolgreich ein Lesezeichen zurück, wenn es nach einem Aufruf von **SQLFetch**mit *Col_or_Param_Num* gleich 0 aufgerufen wird, da **SQLFetch** vom ODBC 3 *.x* Driver Manager **SQLExtendedFetch** mit einem *FetchOrientation* von SQL_FETCH_NEXT zugeordnet wird und **SQLGetData** mit einem *Col_or_Param_Num* von 0 vom ODBC 3 *.x* Driver Manager **mit** einer *FOption* von SQL_GET_BOOKMARK zugeordnet wird.  
  
 **SQLGetData** kann nicht verwendet werden, um die Textmarke für eine Gerade eingefügte Zeile abzurufen, indem **SQLBulkOperations** mit der Option SQL_ADD aufgerufen wird, da der Cursor nicht in der Zeile positioniert ist. Eine Anwendung kann die Textmarke für eine solche Zeile durch Bindung der Spalte 0 abrufen, bevor **SIE SQLBulkOperations** mit SQL_ADD aufruft. In diesem Fall gibt **SQLBulkOperations** die Textmarke im gebundenen Puffer zurück. **SQLFetchScroll** kann dann mit SQL_FETCH_BOOKMARK aufgerufen werden, um den Cursor in dieser Zeile neu zu positionieren.  
  
 Wenn das *TargetType-Argument* ein Intervalldatentyp ist, werden für die Daten die Standardmäßige Intervallführungsgenauigkeit (2) und die Standardintervallsekundengenauigkeit (6), wie sie in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION bzw. SQL_DESC_PRECISION der ARD festgelegt sind, verwendet. Wenn es sich bei dem *TargetType-Argument* um einen SQL_C_NUMERIC Datentyps handelt, werden für die Daten die Standardgenauigkeit (treiberdefiniert) und die Standardskala (0), wie sie in den Feldern SQL_DESC_PRECISION und SQL_DESC_SCALE der ARD festgelegt sind, verwendet. Wenn eine Standardgenauigkeit oder ein Standardmaßstab nicht geeignet ist, sollte die Anwendung das entsprechende Deskriptorfeld explizit durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**festlegen. Es kann das feld SQL_DESC_CONCISE_TYPE auf SQL_C_NUMERIC festlegen und **SQLGetData** mit dem *TargetType-Argument* von SQL_ARD_TYPE aufrufen, wodurch die Genauigkeits- und Skalierungswerte in den Deskriptorfeldern verwendet werden.  
  
> [!NOTE]
>  In ODBC 2 *.x*legen Anwendungen *TargetType* auf SQL_C_DATE, \*SQL_C_TIME oder SQL_C_TIMESTAMP fest, um anzugeben, dass *TargetValuePtr* eine Datums-, Uhrzeit- oder Zeitstempelstruktur ist. In ODBC 3 *.x*legen Anwendungen *TargetType* auf SQL_C_TYPE_DATE, SQL_C_TYPE_TIME oder SQL_C_TYPE_TIMESTAMP fest. Der Treiber-Manager erstellt bei Bedarf entsprechende Zuordnungen basierend auf der Anwendungs- und Treiberversion.  
  
## <a name="retrieving-variable-length-data-in-parts"></a>Abrufen von Daten variabler Länge in Teilen  
 **SQLGetData** kann verwendet werden, um Daten aus einer Spalte abzurufen, die Daten variabler Länge in Teilen enthält, d. h., wenn der Bezeichner des SQL-Datentyps der Spalte SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_WCHAR, SQL_WVARCHAR, SQL_WLONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY oder ein treiberspezifischer Bezeichner für einen Variablentyp ist.  
  
 Um Daten aus einer Spalte in Teilen abzurufen, ruft die Anwendung **SQLGetData** mehrmals hintereinander für dieselbe Spalte auf. Bei jedem Aufruf gibt **SQLGetData** den nächsten Teil der Daten zurück. Es liegt an der Anwendung, die Teile wieder zusammenzusetzen, wobei darauf geachtet wird, das Null-Beendigungszeichen aus Zwischenteilen von Zeichendaten zu entfernen. Wenn mehr Daten zurückgegeben werden sollen oder nicht genügend Puffer für das beendende Zeichen zugewiesen wurde, gibt **SQLGetData** SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 (Daten abgeschnitten) zurück. Wenn der letzte Teil der Daten zurückgegeben wird, gibt **SQLGetData** SQL_SUCCESS zurück. Weder SQL_NO_TOTAL noch Null können beim letzten gültigen Aufruf zurückgegeben werden, um Daten aus einer Spalte abzurufen, da die Anwendung dann keine Möglichkeit hätte zu wissen, wie viel der Daten im Anwendungspuffer gültig ist. Wenn **SQLGetData** danach aufgerufen wird, gibt es SQL_NO_DATA zurück. Weitere Informationen finden Sie im nächsten Abschnitt "Abrufen von Daten mit SQLGetData".  
  
 Lesezeichen variabler Länge können in Teilen von **SQLGetData**zurückgegeben werden. Wie bei anderen Daten gibt ein Aufruf von **SQLGetData,** um Lesezeichen variabler Länge in Teilen zurückzugeben, SQLSTATE 01004 (String-Daten, rechts abgeschnitten) und SQL_SUCCESS_WITH_INFO, wenn mehr Daten zurückgegeben werden sollen. Dies unterscheidet sich von dem Fall, wenn eine Textmarke mit variabler Länge durch einen Aufruf von **SQLFetch** oder **SQLFetchScroll**abgeschnitten wird, der SQL_ERROR und SQLSTATE 22001 (Zeichenfolgendaten, rechts abgeschnitten) zurückgibt.  
  
 **SQLGetData** kann nicht verwendet werden, um Daten fester Länge in Teilen zurückzugeben. Wenn **SQLGetData** mehr als einmal hintereinander für eine Spalte aufgerufen wird, die Daten fester Länge enthält, wird SQL_NO_DATA für alle Aufrufe nach dem ersten zurückgegeben.  
  
## <a name="retrieving-streamed-output-parameters"></a>Abrufen von streamierten Ausgabeparametern  
 Wenn ein Treiber gestreamte Ausgabeparameter unterstützt, kann eine Anwendung **SQLGetData** mit einem kleinen Puffer mehrmals aufrufen, um einen großen Parameterwert abzurufen. Weitere Informationen zu gestreamten Ausgabeparametern finden Sie unter [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="retrieving-data-with-sqlgetdata"></a>Abrufen von Daten mit SQLGetData  
 Um Daten für die angegebene Spalte zurückzugeben, führt **SQLGetData** die folgende Folge von Schritten aus:  
  
1.  Gibt SQL_NO_DATA zurück, wenn bereits alle Daten für die Spalte zurückgegeben wurden.  
  
2.  Legt \* *StrLen_or_IndPtr* auf SQL_NULL_DATA fest, wenn die Daten NULL sind. Wenn die Daten NULL sind und *StrLen_or_IndPtr* ein NULL-Zeiger war, gibt **SQLGetData** SQLSTATE 22002 zurück (Indikatorvariable erforderlich, aber nicht angegeben).  
  
     Wenn die Daten für die Spalte nicht NULL sind, fährt **SQLGetData** mit Schritt 3 fort.  
  
3.  Wenn das Attribut SQL_ATTR_MAX_LENGTH Anweisung auf einen Wert ungleich Null festgelegt ist, wenn die Spalte Zeichen- oder Binärdaten enthält und **SQLGetData** zuvor nicht für die Spalte aufgerufen wurde, werden die Daten auf SQL_ATTR_MAX_LENGTH Bytes abgeschnitten.  
  
    > [!NOTE]  
    >  Das Attribut SQL_ATTR_MAX_LENGTH-Anweisung soll den Netzwerkverkehr reduzieren. Sie wird in der Regel von der Datenquelle implementiert, die die Daten abkürt, bevor sie über das Netzwerk zurückgegeben werden. Treiber und Datenquellen sind nicht erforderlich, um sie zu unterstützen. Um zu gewährleisten, dass Daten auf eine bestimmte Größe abgeschnitten werden, sollte eine Anwendung daher einen Puffer dieser Größe zuweisen und die Größe im *BufferLength-Argument* angeben.  
  
4.  Konvertiert die Daten in den in *TargetType*angegebenen Typ . Die Daten erhalten die Standardgenauigkeit und Skalierung für diesen Datentyp. Wenn *TargetType* SQL_ARD_TYPE ist, wird der Datentyp im SQL_DESC_CONCISE_TYPE Feld der ARD verwendet. Wenn *TargetType* SQL_ARD_TYPE ist, erhalten die Daten die Genauigkeit und Skalierung in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION und SQL_DESC_SCALE der ARD, abhängig vom Datentyp im SQL_DESC_CONCISE_TYPE Feld. Wenn eine Standardgenauigkeit oder ein Standardmaßstab nicht geeignet ist, sollte die Anwendung das entsprechende Deskriptorfeld explizit durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**festlegen.  
  
5.  Wenn die Daten in einen Datentyp variabler Länge konvertiert wurden, z. B. Zeichen oder Binärdaten, prüft **SQLGetData,** ob die Länge der Daten *BufferLength*überschreitet. Wenn die Länge der Zeichendaten (einschließlich des Null-Beendigungszeichens) *BufferLength*überschreitet, kürt **SQLGetData** die Daten auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens. Anschließend werden die Daten auf null beendet. Wenn die Länge der Binärdaten die Länge des Datenpuffers überschreitet, wird er **von SQLGetData** auf *BufferLength-Bytes* abgeschnitten.  
  
     Wenn der angegebene Datenpuffer zu klein ist, um das Null-Beendigungszeichen zu enthalten, gibt **SQLGetData** SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 zurück.  
  
     **SQLGetData** führt niemals Daten herunter, die in Datentypen fester Länge konvertiert wurden. Es wird immer davon ausgegangen, dass die Länge von **TargetValuePtr* die Größe des Datentyps ist.  
  
6.  Platziert die konvertierten (und möglicherweise abgeschnittenen) Daten in \* *TargetValuePtr*. Beachten Sie, dass SQLGetData keine Daten a-zeiler **zurückgibt.**  
  
7.  Platziert die Länge der \*Daten in *StrLen_or_IndPtr*. Wenn *StrLen_or_IndPtr* ein Nullzeiger war, gibt **SQLGetData** die Länge nicht zurück.  
  
    -   Bei Zeichen- oder Binärdaten ist dies die Länge der Daten nach der Konvertierung und vor dem Abschneiden aufgrund *von BufferLength*. Wenn der Treiber die Länge der Daten nach der Konvertierung nicht bestimmen kann, wie dies manchmal bei langen Daten der Fall ist, gibt er SQL_SUCCESS_WITH_INFO zurück und legt die Länge auf SQL_NO_TOTAL fest. (Der letzte Aufruf von **SQLGetData** muss immer die Länge der Daten zurückgeben, nicht Null oder SQL_NO_TOTAL.) Wenn Daten aufgrund des Attributs SQL_ATTR_MAX_LENGTH Anweisung abgeschnitten wurden, wird der Wert dieses Attributs \*- im Gegensatz zur tatsächlichen Länge - in *StrLen_or_IndPtr*. Dies liegt daran, dass dieses Attribut entwickelt wurde, um Daten auf dem Server vor der Konvertierung zu abschneiden, sodass der Treiber keine Möglichkeit hat, herauszufinden, wie hoch die tatsächliche Länge ist. Wenn **SQLGetData** mehrmals hintereinander für dieselbe Spalte aufgerufen wird, ist dies die Länge der Daten, die zu Beginn des aktuellen Aufrufs verfügbar sind. d. h., die Länge nimmt mit jedem nachfolgenden Aufruf ab.  
  
    -   Bei allen anderen Datentypen ist dies die Länge der Daten nach der Konvertierung; Das heißt, es ist die Größe des Typs, in den die Daten konvertiert wurden.  
  
8.  Wenn die Daten während der Konvertierung ohne Signifikanzverlust abgeschnitten werden (z. B. wird die reelle Zahl 1.234 abgeschnitten, wenn sie in die ganze Zahl 1 konvertiert wird) oder weil *BufferLength* zu klein ist (z. B. wird die Zeichenfolge "abcdef" in einem 4-Byte-Puffer platziert), gibt **SQLGetData** SQLSTATE 01004 (Data truncated) zurück und SQL_SUCCESS_WITH_INFO. Wenn Daten aufgrund des SQL_ATTR_MAX_LENGTH-Anweisungsattributs ohne Signifikanzverlust abgeschnitten werden, gibt **SQLGetData** SQL_SUCCESS zurück und gibt SQLSTATE 01004 (Daten abgeschnitten) nicht zurück.  
  
 Der Inhalt des gebundenen Datenpuffers (wenn **SQLGetData** für eine gebundene Spalte aufgerufen wird) und der Längen-/Indikatorpuffer sind nicht definiert, wenn **SQLGetData** nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt.  
  
 Aufeinanderfolgende Aufrufe von **SQLGetData** rufen Daten aus der letzten angeforderten Spalte ab. vorherige Offsets werden ungültig. Wenn z. B. die folgende Sequenz ausgeführt wird:  
  
```cpp  
SQLGetData(icol=n), SQLGetData(icol=m), SQLGetData(icol=n)  
```  
  
 Der zweite Aufruf von SQLGetData(icol=n) ruft Daten vom Anfang der n-Spalte ab. Jeder Offset in den Daten aufgrund früherer Aufrufe von **SQLGetData** für die Spalte ist nicht mehr gültig.  
  
## <a name="descriptors-and-sqlgetdata"></a>Deskriptoren und SQLGetData  
 **SQLGetData** interagiert nicht direkt mit Deskriptorfeldern.  
  
 Wenn *TargetType* SQL_ARD_TYPE ist, wird der Datentyp im SQL_DESC_CONCISE_TYPE Feld der ARD verwendet. Wenn *TargetType* entweder SQL_ARD_TYPE oder SQL_C_DEFAULT ist, erhalten die Daten die Genauigkeit und Skalierung in den Feldern SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION und SQL_DESC_SCALE der ARD, abhängig vom Datentyp im Feld SQL_DESC_CONCISE_TYPE.  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel führt eine Anwendung eine **SELECT-Anweisung** aus, um eine Resultmenge der Kunden-IDs, -Namen und -Telefonnummern zurückzugeben, sortiert nach Name, ID und Telefonnummer. Für jede Datenzeile wird **SQLFetch** auf, um den Cursor in der nächsten Zeile zu positionieren. Es ruft **SQLGetData** auf, um die abgerufenen Daten abzurufen. Die Puffer für die Daten und die zurückgegebene Anzahl von Bytes werden im Aufruf von **SQLGetData**angegeben. Schließlich werden der Name, die ID und die Telefonnummer jedes Mitarbeiters gedruckt.  
  
```cpp  
#define NAME_LEN 50  
#define PHONE_LEN 50  
  
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];  
SQLINTEGER   sCustID, cbName, cbAge, cbBirthday;  
SQLRETURN    retcode;  
SQLHSTMT     hstmt;  
  
retcode = SQLExecDirect(hstmt,  
   "SELECT CUSTID, NAME, PHONE FROM CUSTOMERS ORDER BY 2, 1, 3",  
   SQL_NTS);  
  
if (retcode == SQL_SUCCESS) {  
   while (TRUE) {  
      retcode = SQLFetch(hstmt);  
      if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO) {  
         show_error();  
      }  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){  
  
         /* Get data for columns 1, 2, and 3 */  
  
         SQLGetData(hstmt, 1, SQL_C_ULONG, &sCustID, 0, &cbCustID);  
         SQLGetData(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
         SQLGetData(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN,  
            &cbPhone);  
  
         /* Print the row of data */  
  
         fprintf(out, "%-5d %-*s %*s", sCustID, NAME_LEN-1, szName,   
            PHONE_LEN-1, szPhone);  
      } else {  
         break;  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuweisen von Speicher für eine Spalte in einem Resultset|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Massenvorgängen, die sich nicht auf die Blockcursorposition beziehen|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen einer einzelnen Datenzeile oder eines Datenblocks in einer vorwärtsgerichteten Richtung|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Senden von Parameterdaten zur Ausführungszeit|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset oder Aktualisieren oder Löschen von Daten im Rowset|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
