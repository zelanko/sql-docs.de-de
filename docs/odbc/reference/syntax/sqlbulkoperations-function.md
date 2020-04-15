---
title: SQLBulkOperations-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBulkOperations
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBulkOperations
helpviewer_keywords:
- SQLBulkOperations function [ODBC]
ms.assetid: 7029d0da-b0f2-44e6-9114-50bd96f47196
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f4f294a6d84856bc3065b599a370bb5658e3ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301330"
---
# <a name="sqlbulkoperations-function"></a>SQLBulkOperations-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLBulkOperations** führt Masseneinfügungen und Massentextmarkierungsvorgänge durch, einschließlich Aktualisieren, Löschen und Abrufen nach Lesezeichen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLBulkOperations(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Operation);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *Vorgang*  
 [Eingabe] Vorgang zum Ausführen von:  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 Weitere Informationen finden Sie unter "Kommentare".  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLBulkOperations** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLBulkOperations** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
 Für alle SQLSTATEs, die SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgeben können (außer 01xxx SQLSTATEs), wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn ein Fehler bei einer oder mehreren Zeilen eines mehrreihigen Vorgangs auftritt, und SQL_ERROR wird zurückgegeben, wenn ein Fehler bei einem einzeiligen Vorgang auftritt.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten-Rechts-Abschneiden|Das *Operation-Argument* wurde SQL_FETCH_BY_BOOKMARK, und Zeichenfolgen- oder Binärdaten, die für eine Spalte oder Spalten mit einem Datentyp von SQL_C_CHAR oder SQL_C_BINARY zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind.|  
|01S01|Fehler in Zeile|Das *Argument Operation* wurde SQL_ADD, und beim Ausführen des Vorgangs ist ein Fehler in einer oder mehreren Zeilen aufgetreten, aber mindestens eine Zeile wurde erfolgreich hinzugefügt. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> (Dieser Fehler wird nur ausgelöst, wenn eine Anwendung mit einem ODBC 2 arbeitet. *x* x-Treiber.)|  
|01S07|Bruchschnitt|Das *Argument Operation* wurde SQL_FETCH_BY_BOOKMARK, der Datentyp des Anwendungspuffers war nicht SQL_C_CHAR oder SQL_C_BINARY, und die Anstellungsdaten für eine oder mehrere Spalten wurden abgeschnitten. (Bei numerischen C-Datentypen wurde der Bruchteil der Zahl abgeschnitten. Für Zeit-, Zeitstempel- und Intervall-C-Datentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.)<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|Das *Argument Operation* wurde SQL_FETCH_BY_BOOKMARK, und der Datenwert einer Spalte im Resultset konnte nicht in den Datentyp konvertiert werden, der durch das *TargetType-Argument* beim Aufruf von **SQLBindCol**angegeben wurde.<br /><br /> Das *Argument Operation* wurde SQL_UPDATE_BY_BOOKMARK oder SQL_ADD, und der Datenwert in den Anwendungspuffern konnte nicht in den Datentyp einer Spalte im Resultset konvertiert werden.|  
|07009|Ungültiger Deskriptorindex|Das Argument *Operation* wurde SQL_ADD, und eine Spalte wurde mit einer Spaltennummer gebunden, die größer als die Anzahl der Spalten im Resultset ist.|  
|21S02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|Das Argument *Operation* war SQL_UPDATE_BY_BOOKMARK; und keine Spalten waren aufrüstbar, da alle Spalten entweder ungebunden oder schreibgeschützt waren oder der Wert im gebundenen Längen-/Indikatorpuffer SQL_COLUMN_IGNORE war.|  
|22001|String-Daten-Rechts-Abschneiden|Die Zuweisung eines Zeichens oder Binärwerts zu einer Spalte in der Resultset führte zum Abschneiden von nicht leeren (für Zeichen) oder nicht NULL (für Binärzeichen) Zeichen oder Bytes.|  
|22003|Numerischer Wert aofc|Das *Argument Operation* wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK, und die Zuweisung eines numerischen Werts zu einer Spalte in der Ergebnismenge führte dazu, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde.<br /><br /> Das Argument *Operation* wurde SQL_FETCH_BY_BOOKMARK, und das Zurückgeben des numerischen Werts für eine oder mehrere gebundene Spalten hätte zu einem Verlust signifikanter Ziffern geführt.|  
|22007|Ungültiges Datumszeitformat|Das *Argument "Vorgang"* wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK, und die Zuordnung eines Datums- oder Zeitstempelwerts zu einer Spalte in der Ergebnismenge führte dazu, dass das Feld "Jahr", "Monat" oder "Tag" anicht in Reichweite lag.<br /><br /> Das Argument *Operation* wurde SQL_FETCH_BY_BOOKMARK, und das Zurückgeben des Datums- oder Zeitstempelwerts für eine oder mehrere gebundene Spalten hätte dazu geführt, dass das Feld "Jahr", "Monat" oder "Tag" anicht in den Bereich gefallen wäre.|  
|22008|Datums-/Uhrzeitfeldüberlauf|Das *Operation-Argument* wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK, und die Leistung der Datetime-Arithmetik für Daten, die an eine Spalte im Resultset gesendet wurden, führte zu einem Datumsuhrfeld (Jahr, Monat, Tag, Stunde, Minute oder zweites Feld), das außerhalb des zulässigen Wertebereichs für das Feld liegt oder aufgrund der natürlichen Regeln des Gregorianischen Kalenders für Datumszeiten ungültig ist.<br /><br /> Das *Operation-Argument* wurde SQL_FETCH_BY_BOOKMARK, und die Leistung der Datetime-Arithmetik für Daten, die aus dem Resultset abgerufen wurden, führte zu einem Datumszeitfeld (Jahr, Monat, Tag, Stunde, Minute oder zweites Feld) des Ergebnisses, das außerhalb des zulässigen Wertebereichs für das Feld liegt oder aufgrund der natürlichen Regeln des Gregorianischen Kalenders für Datumszeiten ungültig ist.|  
|22015|Intervallfeldüberlauf|Das *Argument Operation* wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK, und die Zuweisung eines genauen numerischen oder Intervall-C-Typs zu einem Intervall-SQL-Datentyp verursachte einen Verlust signifikanter Ziffern.<br /><br /> Das *Argument Operation* wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK. Beim Zuweisen eines INTERVALL-SQL-Typs gab es keine Darstellung des Wertes des Typs C im Intervall-SQL-Typ.<br /><br /> Das *Argument Operation* wurde SQL_FETCH_BY_BOOKMARK, und das Zuweisen eines SQL-Typs aus einem exakten numerischen oder Intervall-SQL-Typ zu einem Intervall-C-Typ verursachte einen Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Das *Argument Operation* wurde SQL_FETCH_BY_BOOKMARK; Beim Zuweisen zu einem Intervall-C-Typ gab es keine Darstellung des Wertes des SQL-Typs im Intervall-C-Typ.|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|Das *Argument Operation* wurde SQL_FETCH_BY_BOOKMARK; Der C-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp; Der SQL-Typ der Spalte war ein Zeichendatentyp; und der Wert in der Spalte war kein gültiges Literal des gebundenen C-Typs.<br /><br /> Das Argument *Operation* wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK; Der SQL-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. der Typ C wurde SQL_C_CHAR; und der Wert in der Spalte war kein gültiges Literal des gebundenen SQL-Typs.|  
|23000|Verletzung der Integritätseinschränkung|Das *Argument "Vorgang"* wurde SQL_ADD, SQL_DELETE_BY_BOOKMARK oder SQL_UPDATE_BY_BOOKMARK, und eine Integritätseinschränkung wurde verletzt.<br /><br /> Das *Argument Operation* wurde SQL_ADD, und eine Spalte, die nicht gebunden war, ist als NOT NULL definiert und hat keinen Standardwert.<br /><br /> Das *Argument Operation* wurde SQL_ADD, die im StrLen_or_IndPtr Puffer angegebene Länge SQL_COLUMN_IGNORE wurde und die Spalte keinen Standardwert hatte. *StrLen_or_IndPtr*|  
|24.000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcendeadlocks mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntaxfehler oder Zugriffsverletzung|Der Treiber konnte die Zeile nicht nach Bedarf sperren, um den im *Argument Operation* angeforderten Vorgang auszuführen.|  
|44000|WITH CHECK OPTION-Verstoß|Das *Operation-Argument* wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK, und das Einfügen oder Aktualisieren wurde für eine angezeigte Tabelle (oder eine von der angezeigten Tabelle abgeleitete Tabelle) ausgeführt, die durch Angabe von **WITH CHECK OPTION**erstellt wurde, so dass eine oder mehrere Zeilen, die von der Einfügung oder Aktualisierung betroffen sind, nicht mehr in der angezeigten Tabelle vorhanden sind.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLBulkOperations-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Der angegebene *StatementHandle* befand sich nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute**oder eine Katalogfunktion aufzurufen.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLSetPos** wurde für den *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Der Treiber war ein ODBC 2. *x-Treiber* und **SQLBulkOperations** wurde für einen *StatementHandle* aufgerufen, bevor **SQLFetchScroll** oder **SQLFetch** aufgerufen wurden.<br /><br /> (DM) **SQLBulkOperations** wurde aufgerufen, nachdem **SQLExtendedFetch** für *den StatementHandle*aufgerufen wurde.|  
|HY011|Attribut kann jetzt nicht festgelegt werden|(DM) Der Treiber war ein ODBC 2. *x-Treiber* und das Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung wurde zwischen Aufrufen von **SQLFetch** oder **SQLFetchScroll** und **SQLBulkOperations**festgelegt.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|Das *Argument Operation* wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK. ein Datenwert war kein Nullzeiger; der C-Datentyp SQL_C_BINARY oder SQL_C_CHAR; und der Wert für die Spaltenlänge war kleiner als 0, aber nicht gleich SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS oder SQL_NULL_DATA oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Der Wert in einem Längen-Indikator-Puffer wurde SQL_DATA_AT_EXEC; Der SQL-Typ war entweder SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer datenquellenspezifischer Datentyp. und der SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo** war "Y".<br /><br /> Das *Argument Operation* wurde SQL_ADD, das SQL_ATTR_USE_BOOKMARK Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und Spalte 0 wurde an einen Puffer gebunden, dessen Länge nicht der maximalen Länge für die Textmarke für dieses Resultset entsprach. (Diese Länge ist im Feld SQL_DESC_OCTET_LENGTH der IRD verfügbar und kann durch Aufrufen von **SQLDescribeCol**, **SQLColAttribute**oder **SQLGetDescField**abgerufen werden.)|  
|HY092|Ungültiger Attributbezeichner|(DM) Der für das *Operation-Argument* angegebene Wert war ungültig.<br /><br /> Das *Argument Operation* wurde SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_DELETE_BY_BOOKMARK, und das Attribut SQL_ATTR_CONCURRENCY Anweisung wurde auf SQL_CONCUR_READ_ONLY festgelegt.<br /><br /> Das *Argument Operation* war SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK oder SQL_UPDATE_BY_BOOKMARK, und die Textzeichenspalte war nicht gebunden, oder das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung wurde auf SQL_UB_OFF festgelegt.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der Treiber oder die Datenquelle unterstützt den im *Argument Operation* angeforderten Vorgang nicht.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr** mit dem *Attributargument* SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
  
> [!CAUTION]  
>  Informationen darüber, in welchen Anweisungszuständen **SQLBulkOperations** aufgerufen werden kann und was sie für die Kompatibilität mit ODBC 2 tun müssen. *x-Anwendungen* finden Sie im Abschnitt [Blockcursors, Scrollable Cursors und Backward Compatibility](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.  
  
 Eine Anwendung verwendet **SQLBulkOperations,** um die folgenden Vorgänge für die Basistabelle oder -ansicht auszuführen, die der aktuellen Abfrage entspricht:  
  
-   Fügen Sie neue Zeilen hinzu.  
  
-   Aktualisieren Sie eine Reihe von Zeilen, in denen jede Zeile durch ein Lesezeichen identifiziert wird.  
  
-   Löschen Sie eine Reihe von Zeilen, in denen jede Zeile durch eine Textmarke identifiziert wird.  
  
-   Rufen Sie eine Reihe von Zeilen ab, in denen jede Zeile durch ein Lesezeichen identifiziert wird.  
  
 Nach einem Aufruf von **SQLBulkOperations**ist die Blockcursorposition nicht definiert. Die Anwendung muss **SQLFetchScroll** aufrufen, um die Cursorposition festzulegen. Eine Anwendung sollte **SQLFetchScroll** nur mit dem *FetchOrientation-Argument* SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE oder SQL_FETCH_BOOKMARK aufrufen. Die Cursorposition ist nicht definiert, wenn die Anwendung **SQLFetch** oder **SQLFetchScroll** mit dem *FetchOrientation-Argument* SQL_FETCH_PRIOR, SQL_FETCH_NEXT oder SQL_FETCH_RELATIVE aufruft.  
  
 Eine Spalte kann bei Massenvorgängen ignoriert werden, die von einem Aufruf von **SQLBulkOperations** ausgeführt werden, indem die spaltenlange/indikatorpuffer, die im Aufruf von **SQLBindCol**angegeben wurde, auf SQL_COLUMN_IGNORE festgelegt wird.  
  
 Es ist nicht erforderlich, dass die Anwendung das attribut SQL_ATTR_ROW_OPERATION_PTR-Anweisung beim Aufrufen von **SQLBulkOperations** legt, da Zeilen beim Ausführen von Massenvorgängen mit dieser Funktion nicht ignoriert werden können.  
  
 Der Puffer, auf den das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut zeigt, enthält die Anzahl der Zeilen, die von einem Aufruf von **SQLBulkOperations**betroffen sind.  
  
 Wenn das *Argument Operation* SQL_ADD oder SQL_UPDATE_BY_BOOKMARK ist und die Auswahlliste der abfragespezifikation, die dem Cursor zugeordnet ist, mehr als einen Verweis auf dieselbe Spalte enthält, wird definiert, ob ein Fehler generiert wird oder der Treiber die duplizierten Verweise ignoriert und die angeforderten Vorgänge ausführt.  
  
 Weitere Informationen zur Verwendung von **SQLBulkOperations**finden Sie unter [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).  
  
## <a name="performing-bulk-inserts"></a>Ausführen von Masseneinsätzen  
 Um Daten mit **SQLBulkOperations**einzufügen, führt eine Anwendung die folgende Folge von Schritten aus:  
  
1.  Führt eine Abfrage aus, die ein Resultset zurückgibt.  
  
2.  Legt das SQL_ATTR_ROW_ARRAY_SIZE Anweisungsattribut auf die Anzahl der Zeilen fest, die eingefügt werden sollen.  
  
3.  Ruft **SQLBindCol** auf, um die Daten zu binden, die es einfügen möchte. Die Daten sind an ein Array mit einer Größe gebunden, die dem Wert von SQL_ATTR_ROW_ARRAY_SIZE entspricht.  
  
    > [!NOTE]  
    >  Die Größe des Arrays, auf das das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut zeigt, sollte entweder gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR ein Nullzeiger sein sollte.  
  
4.  Ruft **SQLBulkOperations**(*StatementHandle,* SQL_ADD) auf, um das Einfügen durchzuführen.  
  
5.  Wenn die Anwendung das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut festgelegt hat, kann sie dieses Array überprüfen, um das Ergebnis des Vorgangs anzuzeigen.  
  
 Wenn eine Anwendung Spalte 0 bindet, bevor sie **SQLBulkOperations** mit dem *Operation-Argument* von SQL_ADD aufruft, aktualisiert der Treiber die gebundenen Spalten-0-Puffer mit den Lesezeichenwerten für die neu eingefügte Zeile. Damit dies geschieht, muss die Anwendung das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung auf SQL_UB_VARIABLE festgelegt haben, bevor die Anweisung ausgeführt wird. (Dies funktioniert nicht mit einem ODBC 2. *x* x-Treiber.)  
  
 Lange Daten können in Teilen von SQLBulkOperations hinzugefügt werden, indem Aufrufe von SQLParamData und SQLPutData verwendet werden. Weitere Informationen finden Sie weiter unten in dieser Funktionsreferenz unter "Bereitstellen langer Daten für Masseneinsätze und Updates".  
  
 Es ist nicht erforderlich, dass die Anwendung **SQLFetch** oder **SQLFetchScroll** aufruft, bevor sie **SQLBulkOperations** aufruft (außer wenn sie mit einem ODBC 2 ausgeht).* x-Treiber;* siehe [Abwärtskompatibilität und Konformität von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)).  
  
 Das Verhalten ist treiberdefiniert, wenn **SQLBulkOperations**mit dem *Operation-Argument* SQL_ADD auf einem Cursor aufgerufen wird, der doppelte Spalten enthält. Der Treiber kann einen treiberdefinierten SQLSTATE zurückgeben, die Daten zur ersten Spalte hinzufügen, die im Resultset angezeigt wird, oder andere treiberdefinierte Verhaltensweisen ausführen.  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>Ausführen von Massenaktualisierungen mithilfe von Lesezeichen  
 Um Massenaktualisierungen mithilfe von Lesezeichen mit **SQLBulkOperations**durchzuführen, führt eine Anwendung die folgenden Schritte nacheinander aus:  
  
1.  Legt das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE fest.  
  
2.  Führt eine Abfrage aus, die ein Resultset zurückgibt.  
  
3.  Legt das attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung auf die Anzahl der Zeilen fest, die aktualisiert werden sollen.  
  
4.  Ruft **SQLBindCol** auf, um die Zuschreibungsdaten zu binden. Die Daten sind an ein Array mit einer Größe gebunden, die dem Wert von SQL_ATTR_ROW_ARRAY_SIZE entspricht. Außerdem wird **SQLBindCol** zum Binden der Spalte 0 (die Lesezeichenspalte) aufgeschrieben.  
  
5.  Kopiert die Lesezeichen für Zeilen, die an der Aktualisierung in das Array für Spalte 0 gebunden sind.  
  
6.  Aktualisiert die Daten in den gebundenen Puffern.  
  
    > [!NOTE]  
    >  Die Größe des Arrays, auf das das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut zeigt, sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR ein Nullzeiger sein sollte.  
  
7.  Ruft **SQLBulkOperations**(*StatementHandle,* SQL_UPDATE_BY_BOOKMARK) auf.  
  
    > [!NOTE]  
    >  Wenn die Anwendung das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut festgelegt hat, kann sie dieses Array überprüfen, um das Ergebnis des Vorgangs anzuzeigen.  
  
8.  Ruft optional **SQLBulkOperations**(*StatementHandle*, SQL_FETCH_BY_BOOKMARK) auf, um Daten in die gebundenen Anwendungspuffer abzurufen, um zu überprüfen, ob die Aktualisierung aufgetreten ist.  
  
9. Wenn Daten aktualisiert wurden, ändert der Treiber den Wert im Zeilenstatusarray für die entsprechenden Zeilen, um SQL_ROW_UPDATED.  
  
 Massenaktualisierungen, die von **SQLBulkOperations** durchgeführt werden, können lange Daten mithilfe von Aufrufen von **SQLParamData** und **SQLPutData**enthalten. Weitere Informationen finden Sie weiter unten in dieser Funktionsreferenz unter "Bereitstellen langer Daten für Masseneinsätze und Updates".  
  
 Wenn Lesezeichen cursorübergreifend beibehalten werden, muss die Anwendung **SQLFetch** oder **SQLFetchScroll** nicht aufrufen, bevor sie nach Lesezeichen aktualisiert wird. Es kann Lesezeichen verwenden, die es von einem vorherigen Cursor gespeichert hat. Wenn Lesezeichen nicht cursorübergreifend beibehalten werden, muss die Anwendung **SQLFetch** oder **SQLFetchScroll** aufrufen, um die Lesezeichen abzurufen.  
  
 Das Verhalten ist treiberdefiniert, wenn **SQLBulkOperations**mit dem *Operation-Argument* SQL_UPDATE_BY_BOOKMARK auf einem Cursor aufgerufen wird, der doppelte Spalten enthält. Der Treiber kann eine treiberdefinierte SQLSTATE zurückgeben, die erste Spalte aktualisieren, die im Resultset angezeigt wird, oder ein anderes treiberdefiniertes Verhalten ausführen.  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>Ausführen von Massenabrufs mithilfe von Lesezeichen  
 Um Massenabrufe mit Lesezeichen mit **SQLBulkOperations**auszuführen, führt eine Anwendung die folgenden Schritte nacheinander aus:  
  
1.  Legt das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE fest.  
  
2.  Führt eine Abfrage aus, die ein Resultset zurückgibt.  
  
3.  Legt das Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung auf die Anzahl der Zeilen fest, die abgerufen werden sollen.  
  
4.  Ruft **SQLBindCol** auf, um die Daten zu binden, die es abrufen möchte. Die Daten sind an ein Array mit einer Größe gebunden, die dem Wert von SQL_ATTR_ROW_ARRAY_SIZE entspricht. Außerdem wird **SQLBindCol** zum Binden der Spalte 0 (die Lesezeichenspalte) aufgeschrieben.  
  
5.  Kopiert die Lesezeichen für Zeilen, die in das Array abgerufen werden möchten, das an Spalte 0 gebunden ist. (Dies setzt voraus, dass die Anwendung die Lesezeichen bereits separat erhalten hat.)  
  
    > [!NOTE]  
    >  Die Größe des Arrays, auf das das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut zeigt, sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR ein Nullzeiger sein sollte.  
  
6.  Ruft **SQLBulkOperations**(*StatementHandle,* SQL_FETCH_BY_BOOKMARK) auf.  
  
7.  Wenn die Anwendung das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut festgelegt hat, kann sie dieses Array überprüfen, um das Ergebnis des Vorgangs anzuzeigen.  
  
 Wenn Lesezeichen über Cursor hinweg beibehalten werden, muss die Anwendung **SQLFetch** oder **SQLFetchScroll** nicht aufrufen, bevor sie nach Lesezeichen abgerufen wird. Es kann Lesezeichen verwenden, die es von einem vorherigen Cursor gespeichert hat. Wenn Lesezeichen nicht cursorübergreifend beibehalten werden, muss die Anwendung EINMAL **SQLFetch** oder **SQLFetchScroll** aufrufen, um die Lesezeichen abzurufen.  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>Ausführen von Massenlöschungen mithilfe von Lesezeichen  
 Um Massenlöschungen mit Lesezeichen mit **SQLBulkOperations**auszuführen, führt eine Anwendung die folgenden Schritte nacheinander aus:  
  
1.  Legt das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE fest.  
  
2.  Führt eine Abfrage aus, die ein Resultset zurückgibt.  
  
3.  Legt das Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung auf die Anzahl der Zeilen fest, die gelöscht werden sollen.  
  
4.  Ruft **SQLBindCol** auf, um Spalte 0 (die Lesezeichenspalte) zu binden.  
  
5.  Kopiert die Lesezeichen für Zeilen, die an der Löschung interessiert sind, in das Array, das an Spalte 0 gebunden ist.  
  
    > [!NOTE]  
    >  Die Größe des Arrays, auf das das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut zeigt, sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR ein Nullzeiger sein sollte.  
  
6.  Ruft **SQLBulkOperations**(*StatementHandle,* SQL_DELETE_BY_BOOKMARK) auf.  
  
7.  Wenn die Anwendung das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut festgelegt hat, kann sie dieses Array überprüfen, um das Ergebnis des Vorgangs anzuzeigen.  
  
 Wenn Lesezeichen cursorübergreifend beibehalten werden, muss die Anwendung **sqlFetch** oder **SQLFetchScroll** nicht aufrufen, bevor sie nach Lesezeichen gelöscht wird. Es kann Lesezeichen verwenden, die es von einem vorherigen Cursor gespeichert hat. Wenn Lesezeichen nicht cursorübergreifend beibehalten werden, muss die Anwendung EINMAL **SQLFetch** oder **SQLFetchScroll** aufrufen, um die Lesezeichen abzurufen.  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>Bereitstellen langer Daten für Masseneinsätze und Updates  
 Lange Daten können für Masseneinfügungen und Aktualisierungen bereitgestellt werden, die von Aufrufen von **SQLBulkOperations**ausgeführt werden. Um lange Daten einzufügen oder zu aktualisieren, führt eine Anwendung zusätzlich zu den Schritten aus, die in den Abschnitten "Durchführen von Masseneinfügungen" und "Durchführen von Massenaktualisierungen mithilfe von Lesezeichen" weiter oben in diesem Thema beschrieben wurden.  
  
1.  Wenn die Daten mithilfe von **SQLBindCol**gebunden werden, platziert die Anwendung einen anwendungsdefinierten Wert, z. B. die Spaltennummer, im * \*TargetValuePtr-Puffer* für Data-at-Execution-Spalten. Der Wert kann später verwendet werden, um die Spalte zu identifizieren.  
  
     Die Anwendung platziert das Ergebnis des*SQL_LEN_DATA_AT_EXEC(Länge*) Makros im * \*StrLen_or_IndPtr* Puffer. Wenn der SQL-Datentyp der Spalte SQL_LONGVARBINARY, SQL_LONGVARCHAR oder ein langer datenquellenspezifischer Datentyp ist und der Treiber "Y" für den SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo**zurückgibt, ist *Länge* die Anzahl der Bytes an Daten, die für den Parameter gesendet werden sollen. Andernfalls muss es sich um einen nicht negativen Wert handelt und wird ignoriert.  
  
2.  Wenn **SQLBulkOperations** aufgerufen wird, wenn Daten-at-Execution-Spalten vorhanden sind, gibt die Funktion SQL_NEED_DATA zurück und fährt mit Schritt 3 fort, der folgt. (Wenn keine Data-at-Execution-Spalten vorhanden sind, ist der Vorgang abgeschlossen.)  
  
3.  Die Anwendung ruft **SQLParamData** auf, um die Adresse des * \*TargetValuePtr-Puffers* für die erste zu verarbeitende Data-at-Execution-Spalte abzurufen. **SQLParamData** gibt SQL_NEED_DATA zurück. Die Anwendung ruft den anwendungsdefinierten Wert aus dem * \*TargetValuePtr-Puffer* ab.  
  
    > [!NOTE]  
    >  Obwohl Daten-at-Execution-Parameter Daten-at-Execution-Spalten ähneln, ist der von **SQLParamData** zurückgegebene Wert für jeden wert unterschiedlich.  
  
     Data-at-Execution-Spalten sind Spalten in einem Rowset, für die Daten mit **SQLPutData** gesendet werden, wenn eine Zeile aktualisiert oder mit **SQLBulkOperations**eingefügt wird. Sie sind mit **SQLBindCol**gebunden. Der von **SQLParamData** zurückgegebene Wert ist die Adresse der Zeile im **TargetValuePtr-Puffer,* der verarbeitet wird.  
  
4.  Die Anwendung ruft **SQLPutData** ein oder mehrere Male auf, um Daten für die Spalte zu senden. Es ist mehr als ein Aufruf erforderlich, wenn der gesamte Datenwert **SQLPutData**nicht im * \*in* SQLPutData angegebenen TargetValuePtr-Puffer zurückgegeben werden kann. Mehrere Aufrufe von **SQLPutData** für dieselbe Spalte sind nur zulässig, wenn Zeichen-C-Daten an eine Spalte mit einem zeichen-, binären oder datenquellenspezifischen Datentyp gesendet werden oder wenn binäre C-Daten an eine Spalte mit einem Zeichen-, Binär- oder Datenquellentyp gesendet werden.  
  
5.  Die Anwendung ruft **SQLParamData** erneut auf, um zu signalisieren, dass alle Daten für die Spalte gesendet wurden.  
  
    -   Wenn mehr Data-at-Execution-Spalten vorhanden sind, gibt **SQLParamData** SQL_NEED_DATA und die Adresse des *TargetValuePtr-Puffers* für die nächste zu verarbeitende Data-at-Execution-Spalte zurück. Die Anwendung wiederholt die Schritte 4 und 5.  
  
    -   Wenn keine weiteren Data-at-Execution-Spalten vorhanden sind, ist der Vorgang abgeschlossen. Wenn die Anweisung erfolgreich ausgeführt wurde, gibt **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück. Wenn die Ausführung fehlgeschlagen ist, wird SQL_ERROR zurückgegeben. An diesem Punkt kann **SQLParamData** jede SQLSTATE zurückgeben, die von **SQLBulkOperations**zurückgegeben werden kann.  
  
 Wenn der Vorgang abgebrochen wird oder ein Fehler in **SQLParamData** oder **SQLPutData** auftritt, nachdem **SQLBulkOperations** SQL_NEED_DATA zurückgegeben hat und bevor Daten für alle Data-at-Execution-Spalten gesendet werden, kann die Anwendung nur **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**oder **SQLPutData** für die Anweisung oder die mit der Anweisung verknüpfte Verbindung aufrufen. Wenn eine andere Funktion für die Anweisung oder die verbindung, die der Anweisung zugeordnet ist, aufruft, gibt die Funktion SQL_ERROR und SQLSTATE HY010 (Funktionssequenzfehler) zurück.  
  
 Wenn die Anwendung **SQLCancel** aufruft, während der Treiber weiterhin Daten für Daten-bei-Ausführung-Spalten benötigt, bricht der Treiber den Vorgang ab. Die Anwendung kann dann **SQLBulkOperations** erneut aufrufen. der Abbruch wirkt sich nicht auf den Cursorzustand oder die aktuelle Cursorposition aus.  
  
## <a name="row-status-array"></a>Zeilenstatusarray  
 Das Zeilenstatusarray enthält Statuswerte für jede Datenzeile im Rowset nach einem Aufruf von **SQLBulkOperations**. Der Treiber legt die Statuswerte in diesem Array nach einem Aufruf von **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**oder **SQLBulkOperations**fest. Dieses Array wird zunächst durch einen Aufruf von **SQLBulkOperations** aufgefüllt, wenn **SQLFetch** oder **SQLFetchScroll** nicht vor **SQLBulkOperations**aufgerufen wurde. Auf dieses Array weist das attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung hin. Die Anzahl der Elemente in den Zeilenstatusarrays muss der Anzahl der Zeilen im Rowset entsprechen (wie durch das Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung definiert). Informationen zu diesem Zeilenstatusarray finden Sie unter [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel werden 10 Zeilen mit Daten gleichzeitig aus der Tabelle Customers abgerufen. Anschließend wird der Benutzer aufgefordert, eine Aktion zu ergreifen. Um den Netzwerkverkehr zu reduzieren, aktualisiert, löscht und fügt der Beispielpuffer lokal in die gebundenen Arrays, jedoch bei Offsets hinter den Rowsetdaten ein. Wenn der Benutzer Updates, Löschungen und Einfügungen an die Datenquelle sendet, legt der Code den Bindungsoffset entsprechend fest und ruft **SQLBulkOperations**auf. Der Einfachheit halber kann der Benutzer nicht mehr als 10 Aktualisierungen, Löschungen oder Einfügungen puffern.  
  
```cpp  
// SQLBulkOperations_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include "stdio.h"  
  
#define UPDATE_ROW 100  
#define DELETE_ROW 101  
#define ADD_ROW 102  
#define SEND_TO_DATA_SOURCE 103  
#define UPDATE_OFFSET 10  
#define INSERT_OFFSET 20  
#define DELETE_OFFSET 30  
  
// Define structure for customer data (assume 10 byte maximum bookmark size).  
typedef struct tagCustStruct {  
   SQLCHAR Bookmark[10];  
   SQLINTEGER BookmarkLen;  
   SQLUINTEGER CustomerID;  
   SQLINTEGER CustIDInd;  
   SQLCHAR CompanyName[51];  
   SQLINTEGER NameLenOrInd;  
   SQLCHAR Address[51];  
   SQLINTEGER AddressLenOrInd;  
   SQLCHAR Phone[11];  
   SQLINTEGER PhoneLenOrInd;  
} CustStruct;  
  
// Allocate 40 of these structures. Elements 0-9 are for the current rowset,  
// elements 10-19 are for the buffered updates, elements 20-29 are for  
// the buffered inserts, and elements 30-39 are for the buffered deletes.  
CustStruct CustArray[40];  
SQLUSMALLINT RowStatusArray[10], Action, RowNum, NumUpdates = 0, NumInserts = 0,  
NumDeletes = 0;  
SQLLEN BindOffset = 0;  
SQLRETURN retcode;  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLHSTMT hstmt = NULL;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Set the following statement attributes:  
   // SQL_ATTR_CURSOR_TYPE:           Keyset-driven  
   // SQL_ATTR_ROW_BIND_TYPE:         Row-wise  
   // SQL_ATTR_ROW_ARRAY_SIZE:        10  
   // SQL_ATTR_USE_BOOKMARKS:         Use variable-length bookmarks  
   // SQL_ATTR_ROW_STATUS_PTR:        Points to RowStatusArray  
   // SQL_ATTR_ROW_BIND_OFFSET_PTR:   Points to BindOffset  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_KEYSET_DRIVEN, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER)sizeof(CustStruct), 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_USE_BOOKMARKS, (SQLPOINTER)SQL_UB_VARIABLE, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_OFFSET_PTR, &BindOffset, 0);  
  
   // Bind arrays to the bookmark, CustomerID, CompanyName, Address, and Phone columns.  
   retcode = SQLBindCol(hstmt, 0, SQL_C_VARBOOKMARK, CustArray[0].Bookmark, sizeof(CustArray[0].Bookmark), &CustArray[0].BookmarkLen);  
   retcode = SQLBindCol(hstmt, 1, SQL_C_ULONG, &CustArray[0].CustomerID, 0, &CustArray[0].CustIDInd);  
   retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, CustArray[0].CompanyName, sizeof(CustArray[0].CompanyName), &CustArray[0].NameLenOrInd);  
   retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, CustArray[0].Address, sizeof(CustArray[0].Address), &CustArray[0].AddressLenOrInd);  
   retcode = SQLBindCol(hstmt, 4, SQL_C_CHAR, CustArray[0].Phone, sizeof(CustArray[0].Phone), &CustArray[0].PhoneLenOrInd);  
  
   // Execute a statement to retrieve rows from the Customers table.  
   retcode = SQLExecDirect(hstmt, (SQLCHAR*)"SELECT CustomerID, CompanyName, Address, Phone FROM Customers", SQL_NTS);  
  
   // Fetch and display the first 10 rows.  
   retcode = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
   // DisplayCustData(CustArray, 10);  
  
   // Call GetAction to get an action and a row number from the user.  
   // while (GetAction(&Action, &RowNum)) {  
   Action = SQL_FETCH_NEXT;  
   RowNum = 2;  
   switch (Action) {  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmt, Action, RowNum);  
         // DisplayCustData(CustArray, 10);  
         break;  
  
      case UPDATE_ROW:  
         // Check if we have reached the maximum number of buffered updates.  
         if (NumUpdates < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered updates section of CustArray, copy the bookmark of the row  
            // being updated to the same element, and increment the update counter.  
            // Checking to see we have not already buffered an update for this  
            // row not shown.  
            // GetNewCustData(CustArray, UPDATE_OFFSET + NumUpdates);  
            memcpy(CustArray[UPDATE_OFFSET + NumUpdates].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
            CustArray[UPDATE_OFFSET + NumUpdates].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
            NumUpdates++;  
         } else {  
            printf("Buffers full. Send buffered changes to the data source.");  
         }  
         break;  
      case DELETE_ROW:  
         // Check if we have reached the maximum number of buffered deletes.  
         if (NumDeletes < 10) {  
            // Copy the bookmark of the row being deleted to the next available element  
            // of the buffered deletes section of CustArray and increment the delete  
            // counter. Checking to see we have not already buffered an update for  
            // this row not shown.  
            memcpy(CustArray[DELETE_OFFSET + NumDeletes].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
  
            CustArray[DELETE_OFFSET + NumDeletes].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
  
            NumDeletes++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case ADD_ROW:  
         // reached maximum number of buffered inserts?  
         if (NumInserts < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered inserts section of CustArray and increment insert counter.  
            // GetNewCustData(CustArray, INSERT_OFFSET + NumInserts);  
            NumInserts++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case SEND_TO_DATA_SOURCE:  
         // If there are any buffered updates, inserts, or deletes, set the array size  
         // to that number, set the binding offset to use the data in the buffered  
         // update, insert, or delete part of CustArray, and call SQLBulkOperations to  
         // do the updates, inserts, or deletes. Because we will never have more than  
         // 10 updates, inserts, or deletes, we can use the same row status array.  
         if (NumUpdates) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumUpdates, 0);  
            BindOffset = UPDATE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_UPDATE_BY_BOOKMARK);  
            NumUpdates = 0;  
         }  
  
         if (NumInserts) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumInserts, 0);  
            BindOffset = INSERT_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_ADD);  
            NumInserts = 0;  
         }  
  
         if (NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumDeletes, 0);  
            BindOffset = DELETE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_DELETE_BY_BOOKMARK);  
            NumDeletes = 0;  
         }  
  
         // If there were any updates, inserts, or deletes, reset the binding offset  
         // and array size to their original values.  
         if (NumUpdates || NumInserts || NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
            BindOffset = 0;  
         }  
         break;  
   }  
   // }  
  
   // Close the cursor.  
   SQLFreeStmt(hstmt, SQL_CLOSE);  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen eines einzelnen Feldes eines Deskriptors|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Abrufen mehrerer Felder eines Deskriptors|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen Felds eines Deskriptors|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen mehrerer Felder eines Deskriptors|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset oder Aktualisieren oder Löschen von Daten im Rowset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Festlegen eines Anweisungsattributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
