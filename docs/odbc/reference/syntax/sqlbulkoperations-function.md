---
title: SQLBulkOperations-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 60bcb6851adeba08105dabd6fb0800d2e969a04e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68343180"
---
# <a name="sqlbulkoperations-function"></a>SQLBulkOperations-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLBulkOperations** führt Massen Einfügungen und Massen Lesezeichen Vorgänge aus, einschließlich aktualisieren, löschen und Abrufen von Lesezeichen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLBulkOperations(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Operation);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *Vorgang*  
 Der Auszuführenden Vorgang:  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 Weitere Informationen finden Sie unter "comments".  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLBulkOperations** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLBulkOperations** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
 Für alle Sqlstates-Werte, die SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgeben können (außer 01xxx Sqlstates), wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn ein Fehler in einer oder mehreren, aber nicht in allen Zeilen eines mehr Zeilen Vorgangs auftritt, und SQL_ERROR zurückgegeben, wenn ein Fehler in einem Einzel Zeilen Vorgang.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Abkürzen von Zeichen folgen Daten|Das *Vorgangs* Argument wurde SQL_FETCH_BY_BOOKMARK, und Zeichen folgen-oder Binärdaten, die für eine Spalte oder Spalten mit dem Datentyp SQL_C_CHAR oder SQL_C_BINARY zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind.|  
|01s01|Fehler in Zeile|Das *Vorgangs* Argument wurde SQL_ADD, und beim Ausführen des Vorgangs ist ein Fehler in einer oder mehreren Zeilen aufgetreten, aber mindestens eine Zeile wurde erfolgreich hinzugefügt. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> (Dieser Fehler wird nur ausgelöst, wenn eine Anwendung mit einem ODBC 2 arbeitet. *x* -Treiber.)|  
|01S07|Abschneiden von Sekundenbruchteilen|Das *Vorgangs* Argument wurde SQL_FETCH_BY_BOOKMARK, der Datentyp des Anwendungs Puffers wurde nicht SQL_C_CHAR oder SQL_C_BINARY, und die Daten, die an Anwendungs Puffer für eine oder mehrere Spalten zurückgegeben wurden, wurden abgeschnitten. (Bei numerischen C-Datentypen wurde der Bruchteile der Zahl abgeschnitten. Für Zeit-, timestamp-und Interval C-Datentypen, die eine Zeitkomponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.)<br /><br /> (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|Das *Vorgangs* Argument wurde SQL_FETCH_BY_BOOKMARK, und der Datenwert einer Spalte im Resultset konnte nicht in den Datentyp konvertiert werden, der durch das *TargetType* -Argument im Aufrufen von **SQLBindCol**angegeben wurde.<br /><br /> Das *Vorgangs* Argument war SQL_UPDATE_BY_BOOKMARK oder SQL_ADD, und der Datenwert in den Anwendungs Puffern konnte nicht in den Datentyp einer Spalte im Resultset konvertiert werden.|  
|07009|Ungültiger deskriptorindex.|Der Argument *Vorgang* wurde SQL_ADD, und eine Spalte wurde mit einer Spaltennummer gebunden, die größer als die Anzahl der Spalten im Resultset ist.|  
|21s02|Der Grad der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein.|Der Argument *Vorgang* war SQL_UPDATE_BY_BOOKMARK. und es sind keine Spalten aktualisierbar, da alle Spalten entweder ungebunden oder schreibgeschützt waren oder der Wert im gebundenen Längen-/Indikatorpuffer SQL_COLUMN_IGNORE war.|  
|22001|Abkürzen von Zeichen folgen Daten|Die Zuweisung eines Zeichens oder Binärwerts zu einer Spalte im Resultset führte zum Abschneiden von nicht leeren (für Zeichen) oder nicht-NULL-Zeichen (für Binär Zeichen) oder Bytes.|  
|22003|Numerischer Wert außerhalb des zulässigen Bereichs|Das *Vorgangs* Argument wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK, und die Zuweisung eines numerischen Werts zu einer Spalte im Resultset hat bewirkt, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wird.<br /><br /> Der Argument *Vorgang* wurde SQL_FETCH_BY_BOOKMARK, und das Zurückgeben des numerischen Werts für eine oder mehrere gebundene Spalten hätte zu einem Verlust signifikanter Ziffern geführt.|  
|22007|Ungültiges datetime-Format.|Das *Vorgangs* Argument wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK, und die Zuweisung eines Datums-oder Zeitstempel-Werts zu einer Spalte im Resultset hat bewirkt, dass das Feld "Year", "Month" oder "Day" außerhalb des gültigen Bereichs liegt.<br /><br /> Der Argument *Vorgang* wurde SQL_FETCH_BY_BOOKMARK, und das Zurückgeben des Datums-oder Zeitstempel-Werts für eine oder mehrere gebundene Spalten hätte dazu geführt, dass das Feld "Year", "Month" oder "Day" außerhalb des gültigen Bereichs liegt.|  
|22008|Überlauf bei Datum/Uhrzeit-Feld|Das *Vorgangs* Argument wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK. und die Leistung der DateTime-Arithmetik für Daten, die an eine Spalte im Resultset gesendet werden, führte zu einem DateTime-Feld (Jahr, Monat, Tag, Stunde, Minute oder zweites Feld) des Ergebnisses, das außerhalb des zulässigen Wertebereichs für das Feld liegt oder auf der Grundlage der natürlichen Regeln des gregorianischen Kalenders für datetimes ungültig ist.<br /><br /> Das *Vorgangs* Argument wurde SQL_FETCH_BY_BOOKMARK, und die Leistung der DateTime-Arithmetik für Daten, die aus dem Resultset abgerufen werden, führte zu einem DateTime-Feld (Jahr, Monat, Tag, Stunde, Minute oder zweites Feld) des Ergebnisses, das außerhalb des zulässigen Wertebereichs für das Feld liegt oder aufgrund der natürlichen Regeln des gregorianischen Kalenders für datetimes ungültig ist.|  
|22015|Überlauf des Intervall Felds|Das *Vorgangs* Argument wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK, und die Zuweisung eines exakten numerischen oder Interval C-Typs zu einem Interval-SQL-Datentyp verursachte einen Verlust signifikanter Ziffern.<br /><br /> Das *Vorgangs* Argument wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK. bei der Zuweisung zu einem Interval-SQL-Typ gab es keine Darstellung des Werts des C-Typs im Intervall-SQL-Typ.<br /><br /> Das *Vorgangs* Argument wurde SQL_FETCH_BY_BOOKMARK, und das Zuweisen von einem exakten numerischen oder Interval-SQL-Typ zu einem Interval-C-Typ verursachte einen Verlust signifikanter Ziffern im führenden Feld.<br /><br /> Das *Vorgangs* Argument wurde SQL_FETCH_BY_BOOKMARK. bei der Zuweisung zu einem Interval-c-Typ gab es keine Darstellung des Werts des SQL-Typs im Interval-c-Typ.|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|Das *Vorgangs* Argument wurde SQL_FETCH_BY_BOOKMARK. der C-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der SQL-Typ der Spalte war ein Zeichen Datentyp. und der Wert in der Spalte war kein gültiges Literale des gebundenen C-Typs.<br /><br /> Der Argument *Vorgang* war SQL_ADD oder SQL_UPDATE_BY_BOOKMARK. der SQL-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der C-Typ war SQL_C_CHAR. und der Wert in der Spalte war kein gültiges Literale des gebundenen SQL-Typs.|  
|23000|Verletzung der Integritäts Einschränkung|Das *Vorgangs* Argument war SQL_ADD, SQL_DELETE_BY_BOOKMARK oder SQL_UPDATE_BY_BOOKMARK, und eine Integritäts Einschränkung wurde verletzt.<br /><br /> Das *Vorgangs* Argument wurde SQL_ADD, und eine nicht gebundene Spalte ist als NOT NULL definiert und hat keinen Standardwert.<br /><br /> Das *Vorgangs* Argument wurde SQL_ADD, die im gebundenen *StrLen_or_IndPtr* Puffer angegebene Länge war SQL_COLUMN_IGNORE, und die Spalte enthielt keinen Standardwert.|  
|24.000|Ungültiger Cursorstatus|Das *StatementHandle* befand sich in einem ausgeführten Zustand, aber dem *StatementHandle*wurde kein Resultset zugeordnet.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde ein Rollback ausgeführt, weil ein Ressourcen Deadlock mit einer anderen Transaktion aufgetreten ist.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntax Fehler oder Zugriffsverletzung|Der Treiber konnte die Zeile nicht nach Bedarf sperren, um den im *Vorgangs* Argument angeforderten Vorgang auszuführen.|  
|44000|WITH CHECK OPTION-Verstoß|Das *Vorgangs* Argument war SQL_ADD oder SQL_UPDATE_BY_BOOKMARK, und der INSERT-oder Update-Vorgang wurde für eine angezeigte Tabelle (oder eine Tabelle, die von der angezeigten Tabelle abgeleitet wurde) ausgeführt, die durch Angabe von **with Check Option**erstellt wurde, so dass mindestens eine Zeile, auf die sich die INSERT-oder Update-Methode auswirkt, in der angezeigten Tabelle nicht mehr vorhanden ist.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLBulkOperations** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) das angegebene *StatementHandle* war nicht in einem ausgeführten Zustand. Die Funktion wurde aufgerufen, ohne zuerst **SQLExecDirect**, **SQLExecute**oder eine Katalog Funktion aufzurufen.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLSetPos** wurde für *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) der Treiber war ODBC 2. der *x* -Treiber und **SQLBulkOperations** wurden vor dem Aufruf von **SQLFetchScroll** oder **SQLFetch** für ein *StatementHandle* aufgerufen.<br /><br /> (DM) **SQLBulkOperations** wurde aufgerufen, nachdem **SQLExtendedFetch** für " *StatementHandle*" aufgerufen wurde.|  
|HY011|Das Attribut kann jetzt nicht festgelegt werden|(DM) der Treiber war ODBC 2. der *x* -Treiber und das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut wurde zwischen Aufrufen von **SQLFetch** oder **SQLFetchScroll** und **SQLBulkOperations**festgelegt.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|Das *Vorgangs* Argument wurde SQL_ADD oder SQL_UPDATE_BY_BOOKMARK. ein Datenwert war kein NULL-Zeiger. der C-Datentyp war SQL_C_BINARY oder SQL_C_CHAR. und der Spalten Längen Wert war kleiner als 0 (null), aber nicht gleich SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS oder SQL_NULL_DATA oder kleiner oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Der Wert in einem Längen-/Indikatorpuffer wurde SQL_DATA_AT_EXEC. der SQL-Typ war entweder SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer Datenquellen spezifischer Datentyp. und der SQL_NEED_LONG_DATA_LEN Informationstyp in **SQLGetInfo** lautete "Y".<br /><br /> Das *Vorgangs* Argument wurde SQL_ADD, das SQL_ATTR_USE_BOOKMARK Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und die Spalte 0 wurde an einen Puffer gebunden, dessen Länge nicht der maximalen Länge für das Lesezeichen für dieses Resultset entspricht. (Diese Länge ist im SQL_DESC_OCTET_LENGTH-Feld von IRD verfügbar und kann durch Aufrufen von **SQLDescribeCol**, **SQLColAttribute**oder **SQLGetDescField**abgerufen werden.)|  
|HY092|Ungültiger Attribut Bezeichner|(DM) der für das *Vorgangs* Argument angegebene Wert ist ungültig.<br /><br /> Das *Vorgangs* Argument war SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_DELETE_BY_BOOKMARK, und das SQL_ATTR_CONCURRENCY Statement-Attribut wurde auf SQL_CONCUR_READ_ONLY festgelegt.<br /><br /> Das *Vorgangs* Argument war SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK oder SQL_UPDATE_BY_BOOKMARK, und die Lesezeichen Spalte war nicht gebunden, oder das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_OFF festgelegt.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Der Treiber oder die Datenquelle unterstützt den im *Vorgangs* Argument angeforderten Vorgang nicht.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird über **SQLSetStmtAttr** mit dem *Attribut* Argument SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
  
> [!CAUTION]  
>  Informationen dazu, in welcher Anweisung **SQLBulkOperations** aufgerufen werden kann, und was Sie für die Kompatibilität mit ODBC 2 ausführen muss. *x* -Anwendungen finden Sie im Abschnitt [Blockcursorn,](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) Bild lauffähigen Cursor und Abwärtskompatibilität im Anhang G: Treiber Richtlinien für Abwärtskompatibilität.  
  
 In einer Anwendung werden **SQLBulkOperations** verwendet, um die folgenden Vorgänge für die Basistabelle oder-Sicht auszuführen, die der aktuellen Abfrage entspricht:  
  
-   Fügen Sie neue Zeilen hinzu.  
  
-   Aktualisieren Sie einen Satz von Zeilen, in dem jede Zeile durch ein Lesezeichen identifiziert wird.  
  
-   Löschen Sie eine Reihe von Zeilen, in denen jede Zeile durch ein Lesezeichen identifiziert wird.  
  
-   Abrufen eines Satzes von Zeilen, in dem jede Zeile durch ein Lesezeichen identifiziert wird.  
  
 Nach einem **SQLBulkOperations-Aufrufvorgang**ist die Block Cursorposition nicht definiert. Die Anwendung muss **SQLFetchScroll** aufzurufen, um die Cursorposition festzulegen. Eine Anwendung sollte **SQLFetchScroll** nur mit einem *FetchOrientation* -Argument von SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE oder SQL_FETCH_BOOKMARK aufzurufen. Die Cursorposition ist nicht definiert, wenn die Anwendung **SQLFetch** oder **SQLFetchScroll** mit einem *FetchOrientation* -Argument von SQL_FETCH_PRIOR, SQL_FETCH_NEXT oder SQL_FETCH_RELATIVE aufruft.  
  
 Eine Spalte kann bei Massen Vorgängen ignoriert werden, die durch einen **SQLBulkOperations** -Befehl durchgeführt werden, indem der im-Befehl **SQLBindCol**angegebene Spaltenlänge/Indikator Puffer auf SQL_COLUMN_IGNORE festgelegt wird.  
  
 Es ist nicht erforderlich, dass die Anwendung das SQL_ATTR_ROW_OPERATION_PTR Statement-Attribut beim Aufrufen von **SQLBulkOperations** festgelegt, da Zeilen beim Ausführen von Massen Vorgängen mit dieser Funktion nicht ignoriert werden können.  
  
 Der Puffer, auf den das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungs Attribut zeigt, enthält die Anzahl der Zeilen, auf die sich der **SQLBulkOperations**-Befehl auswirkt.  
  
 Wenn das *Vorgangs* Argument SQL_ADD oder SQL_UPDATE_BY_BOOKMARK ist und die SELECT-Liste der Abfrage Spezifikation, die dem Cursor zugeordnet ist, mehr als einen Verweis auf dieselbe Spalte enthält, wird der Treiber definiert, ob ein Fehler generiert wurde, oder der Treiber ignoriert die duplizierten Verweise und führt die angeforderten Vorgänge aus.  
  
 Weitere Informationen zur Verwendung von **SQLBulkOperations**finden Sie unter [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).  
  
## <a name="performing-bulk-inserts"></a>Ausführen von Massen Vorgängen  
 Zum Einfügen von Daten mit **SQLBulkOperations**führt eine Anwendung die folgenden Schritte aus:  
  
1.  Führt eine Abfrage aus, die ein Resultset zurückgibt.  
  
2.  Legt das Attribut der SQL_ATTR_ROW_ARRAY_SIZE Anweisung auf die Anzahl der Zeilen fest, die eingefügt werden soll.  
  
3.  Ruft **SQLBindCol** auf, um die einzufügenden Daten zu binden. Die Daten werden an ein Array gebunden, dessen Größe gleich dem Wert SQL_ATTR_ROW_ARRAY_SIZE ist.  
  
    > [!NOTE]  
    >  Die Größe des Arrays, auf das das SQL_ATTR_ROW_STATUS_PTR Statement-Attribut verweist, sollte entweder gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR ein NULL-Zeiger sein.  
  
4.  Ruft **SQLBulkOperations**(*StatementHandle,* SQL_ADD) auf, um die Einfügung auszuführen.  
  
5.  Wenn die Anwendung das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut festgelegt hat, kann Sie dieses Array überprüfen, um das Ergebnis des Vorgangs anzuzeigen.  
  
 Wenn eine Anwendung die Spalte 0 bindet, bevor **SQLBulkOperations** mit dem *Vorgangs* Argument SQL_ADD aufgerufen wird, aktualisiert der Treiber die gebundenen Spalten 0-Puffer mit den Lesezeichen Werten für die neu eingefügte Zeile. Hierzu muss die Anwendung das SQL_ATTR_USE_BOOKMARKS Statement-Attribut auf SQL_UB_VARIABLE festlegen, bevor die Anweisung ausgeführt wird. (Dies funktioniert nicht mit ODBC 2. *x* -Treiber.)  
  
 Lange Daten können durch SQLBulkOperations mithilfe von Aufrufen von SQLParamData und SQLPutData in Teilen eingefügt werden. Weitere Informationen finden Sie unter "Bereitstellen von langen Daten für Massen Einfügungen und Updates" weiter unten in dieser Funktionsreferenz.  
  
 Es ist nicht erforderlich, dass die Anwendung **SQLFetch** oder **SQLFetchScroll** aufruft, bevor **SQLBulkOperations** aufgerufen wird (es sei denn, es wird ein ODBC 2-Vorgang durchlaufen).* x* -Treiber; Siehe abwärts [Kompatibilität und Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)).  
  
 Das Verhalten ist Treiber definiert, wenn **SQLBulkOperations**mit dem *Vorgangs* Argument SQL_ADD für einen Cursor aufgerufen wird, der doppelte Spalten enthält. Der Treiber kann einen Treiber definierten SQLSTATE zurückgeben, die Daten der ersten Spalte hinzufügen, die im Resultset angezeigt wird, oder ein anderes Treiber definiertes Verhalten ausführen.  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>Ausführen von Massen Aktualisierungen mithilfe von Lesezeichen  
 Zum Ausführen von Massen Aktualisierungen mithilfe von Lesezeichen mit **SQLBulkOperations**führt eine Anwendung die folgenden Schritte nacheinander aus:  
  
1.  Legt das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung auf SQL_UB_VARIABLE fest.  
  
2.  Führt eine Abfrage aus, die ein Resultset zurückgibt.  
  
3.  Legt das Attribut der SQL_ATTR_ROW_ARRAY_SIZE Anweisung auf die Anzahl der Zeilen fest, die aktualisiert werden sollen.  
  
4.  Ruft **SQLBindCol** auf, um die zu aktualisierenden Daten zu binden. Die Daten werden an ein Array gebunden, dessen Größe gleich dem Wert SQL_ATTR_ROW_ARRAY_SIZE ist. Außerdem wird **SQLBindCol** aufgerufen, um Spalte 0 (die Lesezeichen Spalte) zu binden.  
  
5.  Kopiert die Lesezeichen für Zeilen, die aktualisiert werden sollen, in das Array, das an die Spalte 0 gebunden ist.  
  
6.  Aktualisiert die Daten in den gebundenen Puffern.  
  
    > [!NOTE]  
    >  Die Größe des Arrays, auf das das SQL_ATTR_ROW_STATUS_PTR Statement-Attribut verweist, sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR ein NULL-Zeiger sein.  
  
7.  Ruft **SQLBulkOperations**(*StatementHandle,* SQL_UPDATE_BY_BOOKMARK) auf.  
  
    > [!NOTE]  
    >  Wenn die Anwendung das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut festgelegt hat, kann Sie dieses Array überprüfen, um das Ergebnis des Vorgangs anzuzeigen.  
  
8.  Ruft optional **SQLBulkOperations**(*StatementHandle*, SQL_FETCH_BY_BOOKMARK) auf, um Daten in die gebundenen Anwendungs Puffer abzurufen und zu überprüfen, ob das Update aufgetreten ist.  
  
9. Wenn die Daten aktualisiert wurden, ändert der Treiber den Wert im Zeilen Status Array für die entsprechenden Zeilen in SQL_ROW_UPDATED.  
  
 Massen Updates, die von **SQLBulkOperations** ausgeführt werden, können lange Daten mithilfe von Aufrufen von **SQLParamData** und **SQLPutData**einschließen. Weitere Informationen finden Sie unter "Bereitstellen von langen Daten für Massen Einfügungen und Updates" weiter unten in dieser Funktionsreferenz.  
  
 Wenn Lesezeichen über Cursor hinweg beibehalten werden, muss die Anwendung **SQLFetch** oder **SQLFetchScroll** nicht vor der Aktualisierung durch Lesezeichen aufruft. Sie kann Lesezeichen verwenden, die von einem vorherigen Cursor gespeichert wurden. Wenn Lesezeichen nicht über Cursor hinweg beibehalten werden, muss die Anwendung **SQLFetch** oder **SQLFetchScroll** aufrufen, um die Lesezeichen abzurufen.  
  
 Das Verhalten ist Treiber definiert, wenn **SQLBulkOperations**mit dem *Vorgangs* Argument SQL_UPDATE_BY_BOOKMARK für einen Cursor aufgerufen wird, der doppelte Spalten enthält. Der Treiber kann einen Treiber definierten SQLSTATE zurückgeben, die erste Spalte aktualisieren, die im Resultset angezeigt wird, oder ein anderes Treiber definiertes Verhalten ausführen.  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>Ausführen von Massen Abruf Vorgängen mithilfe von Lesezeichen  
 Zum Ausführen von Massen Abruf Vorgängen mithilfe von Lesezeichen mit **SQLBulkOperations**führt eine Anwendung die folgenden Schritte nacheinander aus:  
  
1.  Legt das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung auf SQL_UB_VARIABLE fest.  
  
2.  Führt eine Abfrage aus, die ein Resultset zurückgibt.  
  
3.  Legt das Attribut der SQL_ATTR_ROW_ARRAY_SIZE Anweisung auf die Anzahl der Zeilen fest, die abgerufen werden sollen.  
  
4.  Ruft **SQLBindCol** auf, um die Daten zu binden, die abgerufen werden sollen. Die Daten werden an ein Array gebunden, dessen Größe gleich dem Wert SQL_ATTR_ROW_ARRAY_SIZE ist. Außerdem wird **SQLBindCol** aufgerufen, um Spalte 0 (die Lesezeichen Spalte) zu binden.  
  
5.  Kopiert die Lesezeichen für Zeilen, die an das an Spalte 0 gebundene Array abgerufen werden sollen. (Dies setzt voraus, dass die Lesezeichen von der Anwendung bereits separat abgerufen wurden.)  
  
    > [!NOTE]  
    >  Die Größe des Arrays, auf das das SQL_ATTR_ROW_STATUS_PTR Statement-Attribut verweist, sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR ein NULL-Zeiger sein.  
  
6.  Ruft **SQLBulkOperations**(*StatementHandle,* SQL_FETCH_BY_BOOKMARK) auf.  
  
7.  Wenn die Anwendung das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut festgelegt hat, kann Sie dieses Array überprüfen, um das Ergebnis des Vorgangs anzuzeigen.  
  
 Wenn Lesezeichen über Cursor hinweg beibehalten werden, muss die Anwendung **SQLFetch** oder **SQLFetchScroll** nicht vor dem Abrufen durch Lesezeichen aufruft. Sie kann Lesezeichen verwenden, die von einem vorherigen Cursor gespeichert wurden. Wenn Lesezeichen nicht über Cursor hinweg beibehalten werden, muss die Anwendung nur einmal **SQLFetch** oder **SQLFetchScroll** aufrufen, um die Lesezeichen abzurufen.  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>Ausführen von Massen Löschungen mit Lesezeichen  
 Zum Ausführen von Massen Löschungen mithilfe von Lesezeichen mit **SQLBulkOperations**führt eine Anwendung die folgenden Schritte nacheinander aus:  
  
1.  Legt das Attribut SQL_ATTR_USE_BOOKMARKS Anweisung auf SQL_UB_VARIABLE fest.  
  
2.  Führt eine Abfrage aus, die ein Resultset zurückgibt.  
  
3.  Legt das Attribut der SQL_ATTR_ROW_ARRAY_SIZE Anweisung auf die Anzahl der Zeilen fest, die gelöscht werden sollen.  
  
4.  Ruft **SQLBindCol** auf, um Spalte 0 (die Lesezeichen Spalte) zu binden.  
  
5.  Kopiert die Lesezeichen für Zeilen, die von diesem gelöscht werden sollen, in das Array, das an die Spalte 0 gebunden ist.  
  
    > [!NOTE]  
    >  Die Größe des Arrays, auf das das SQL_ATTR_ROW_STATUS_PTR Statement-Attribut verweist, sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR ein NULL-Zeiger sein.  
  
6.  Ruft **SQLBulkOperations**(*StatementHandle,* SQL_DELETE_BY_BOOKMARK) auf.  
  
7.  Wenn die Anwendung das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut festgelegt hat, kann Sie dieses Array überprüfen, um das Ergebnis des Vorgangs anzuzeigen.  
  
 Wenn Lesezeichen über Cursor hinweg beibehalten werden, muss die Anwendung **SQLFetch** oder **SQLFetchScroll** nicht vor dem Löschen durch Lesezeichen aufruft. Sie kann Lesezeichen verwenden, die von einem vorherigen Cursor gespeichert wurden. Wenn Lesezeichen nicht über Cursor hinweg beibehalten werden, muss die Anwendung nur einmal **SQLFetch** oder **SQLFetchScroll** aufrufen, um die Lesezeichen abzurufen.  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>Bereitstellen von langen Daten für Massen Einfügungen und Updates  
 Lange Daten können für Massen Einfügungen und Aktualisierungen bereitgestellt werden, die von Aufrufen von **SQLBulkOperations**ausgeführt werden. Um lange Daten einzufügen oder zu aktualisieren, führt eine Anwendung zusätzlich zu den im Abschnitt "Ausführen von Massen Einfügungen" und "Ausführen von Massen Updates mithilfe von Lesezeichen" weiter oben in diesem Thema beschriebenen Schritten die folgenden Schritte aus.  
  
1.  Wenn die Daten mithilfe von **SQLBindCol**gebunden werden, platziert die Anwendung einen Anwendungs definierten Wert, wie z. b. die Spaltennummer, für Data-at-Execution-Spalten in den * \*targetvalueptr* -Puffer. Der Wert kann später verwendet werden, um die Spalte zu identifizieren.  
  
     Die Anwendung platziert das Ergebnis des SQL_LEN_DATA_AT_EXEC (*length*)-Makros im * \*StrLen_or_IndPtr* Puffer. Wenn der SQL-Datentyp der Spalte SQL_LONGVARBINARY, SQL_LONGVARCHAR oder ein langer Datenquellen spezifischer Datentyp ist und der Treiber "Y" für den SQL_NEED_LONG_DATA_LEN Informationstyp in **SQLGetInfo**zurückgibt, ist *length* die Anzahl der Daten bytes, die für den Parameter gesendet werden sollen. Andernfalls muss es sich um einen nicht negativen Wert handeln und wird ignoriert.  
  
2.  Wenn **SQLBulkOperations** aufgerufen wird und Data-at-Execution-Spalten vorhanden sind, gibt die Funktion SQL_NEED_DATA zurück und geht mit Schritt 3 fort, das folgt. (Wenn keine Data-at-Execution-Spalten vorhanden sind, ist der Prozess vollständig.)  
  
3.  Die Anwendung ruft **SQLParamData** auf, um die Adresse des * \*targetvalueptr* -Puffers für die erste zu verarbeitende Data-at-Execution-Spalte abzurufen. **SQLParamData** gibt SQL_NEED_DATA zurück. Die Anwendung ruft den von der Anwendung definierten Wert aus dem * \*targetvalueptr* -Puffer ab.  
  
    > [!NOTE]  
    >  Obwohl Data-at-Execution-Parameter mit Data-at-Execution-Spalten vergleichbar sind, ist der von **SQLParamData** zurückgegebene Wert für jeden Wert anders.  
  
     Data-at-Execution-Spalten sind Spalten in einem Rowset, für die Daten mit **SQLPutData** gesendet werden, wenn eine Zeile aktualisiert oder mit **SQLBulkOperations**eingefügt wird. Sie sind mit **SQLBindCol**gebunden. Der von **SQLParamData** zurückgegebene Wert ist die Adresse der Zeile im **targetvalueptr* -Puffer, der verarbeitet wird.  
  
4.  Die Anwendung ruft **SQLPutData** mindestens einmal auf, um Daten für die Spalte zu senden. Mehrere Aufrufe sind erforderlich, wenn der gesamte Datenwert nicht im in **SQLPutData**angegebenen * \*targetvalueptr* -Puffer zurückgegeben werden kann. mehrere Aufrufe von **SQLPutData** für die gleiche Spalte sind nur zulässig, wenn Zeichen-c-Daten an eine Spalte mit einem Zeichen-, Binär-oder Datenquellen spezifischen Datentyp gesendet werden oder wenn binäre C-Daten an eine Spalte mit einem Zeichen-, Binär-oder Datenquellen spezifischen Datentyp gesendet werden.  
  
5.  Die Anwendung ruft **SQLParamData** erneut auf, um zu signalisieren, dass alle Daten für die Spalte gesendet wurden.  
  
    -   Wenn mehr Data-at-Execution-Spalten vorhanden sind, gibt **SQLParamData** SQL_NEED_DATA und die Adresse des *targetvalueptr* -Puffers für die nächste Data-at-Execution-Spalte zurück, die verarbeitet werden soll. Die Anwendung wiederholt die Schritte 4 und 5.  
  
    -   Wenn keine weiteren Data-at-Execution-Spalten vorhanden sind, ist der Prozess vollständig. Wenn die Anweisung erfolgreich ausgeführt wurde, gibt **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück. Wenn bei der Ausführung ein Fehler aufgetreten ist, wird SQL_ERROR zurückgegeben. An diesem Punkt können **SQLParamData** alle SQLSTATE-Zeichen zurückgeben, die von **SQLBulkOperations**zurückgegeben werden können.  
  
 Wenn der Vorgang abgebrochen wird oder ein Fehler in **SQLParamData** oder **SQLPutData** auftritt, nachdem **SQLBulkOperations** SQL_NEED_DATA zurückgibt und bevor Daten für alle Data-at-Execution-Spalten gesendet werden, die Anwendung kann nur **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**oder **SQLPutData** für die-Anweisung oder die Verbindung aufrufen, die der Anweisung zugeordnet ist. Wenn eine andere Funktion für die-Anweisung oder die mit der-Anweisung verknüpfte Verbindung aufgerufen wird, gibt die Funktion SQL_ERROR und SQLSTATE HY010 (Funktions Sequenz Fehler) zurück.  
  
 Wenn die Anwendung **SQLCancel** aufruft, während der Treiber weiterhin Daten für Data-at-Execution-Spalten benötigt, bricht der Treiber den Vorgang ab. Die Anwendung kann dann **SQLBulkOperations** erneut aufzurufen. Das Abbrechen wirkt sich nicht auf den Cursor Zustand oder die aktuelle Cursorposition aus.  
  
## <a name="row-status-array"></a>Zeilenstatusarray  
 Das Zeilen Status Array enthält nach einem **SQLBulkOperations-Aufrufvorgang**Statuswerte für jede Daten Zeile im Rowset. Der Treiber legt die Statuswerte in diesem Array nach einem Aufrufen von **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**oder **SQLBulkOperations**fest. Dieses Array wird anfänglich durch einen Aufruf von **SQLBulkOperations** aufgefüllt, wenn **SQLFetch** oder **SQLFetchScroll** nicht vor **SQLBulkOperations**aufgerufen wurde. Auf dieses Array wird durch das SQL_ATTR_ROW_STATUS_PTR-Anweisungs Attribut verwiesen. Die Anzahl der Elemente in den Zeilen Status Arrays muss der Anzahl der Zeilen im Rowset entsprechen (wie durch das SQL_ATTR_ROW_ARRAY_SIZE Statement-Attribut definiert). Weitere Informationen zu diesem Zeilen Status Array finden Sie unter [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel werden jeweils 10 Daten Zeilen aus der Customers-Tabelle abgerufen. Anschließend wird der Benutzer aufgefordert, eine Aktion auszuführen. Um den Netzwerk Datenverkehr zu reduzieren, werden im Beispiel die Daten in den gebundenen Arrays lokal aktualisiert, gelöscht und eingefügt, aber bei Offsets hinter den Rowsetdaten. Wenn der Benutzer das Senden von Aktualisierungen, Löschungen und Einfügungen in die Datenquelle auswählt, legt der Code den Bindungs Offset entsprechend fest und ruft **SQLBulkOperations**auf. Der Einfachheit halber kann der Benutzer nicht mehr als 10 Updates, Löschungen oder Einfügungen Puffern.  
  
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
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Ein einzelnes Feld eines Deskriptors wird abgerufen.|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Mehrere Felder eines Deskriptors werden abgerufen.|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen Felds eines Deskriptors|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen mehrerer Felder eines Deskriptors|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset oder aktualisieren oder Löschen von Daten im Rowset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Festlegen eines Anweisungs Attributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
