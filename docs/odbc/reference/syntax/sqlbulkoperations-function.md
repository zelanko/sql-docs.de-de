---
title: SQLBulkOperations-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBulkOperations
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBulkOperations
helpviewer_keywords:
- SQLBulkOperations function [ODBC]
ms.assetid: 7029d0da-b0f2-44e6-9114-50bd96f47196
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14e51f1d04012e22c198b7ed5f70d9b508933c5d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65538037"
---
# <a name="sqlbulkoperations-function"></a>SQLBulkOperations-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLBulkOperations** führt Bulk einfügungen und Bulk-Lesezeichen Vorgänge, einschließlich aktualisieren, löschen und durch Lesezeichen abrufen.  
  
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
 [Eingabe] Der Vorgang ausführen:  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 Weitere Informationen finden Sie unter "Kommentare".  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLBulkOperations** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und eine *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLBulkOperations** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben . Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
 Für alle diese SQLSTATEs, der SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück (mit Ausnahme der 01xxx SQLSTATEs) zurückgeben kann, wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn bei ein oder mehrere, aber nicht alle Zeilen eines mehrzeiligen-Vorgangs ein Fehler auftritt, und SQL_ERROR zurückgegeben wird, wenn es sich bei Auftreten eines Fehlers auf einem einzeiliges-Vorgang.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgedaten rechts abgeschnitten|Die *Vorgang* Argument war SQL_FETCH_BY_BOOKMARK und Zeichenfolgen- oder Binärdaten, die für eine Spalte oder Spalten mit dem Datentyp des Typs SQL_C_CHAR oder sql_c_binary angegeben zurückgegeben, die in das Abschneiden von nicht leeren Zeichen oder binäre Daten ungleich NULL geführt haben.|  
|01S01|Fehler in Zeile|Die *Vorgang* Argument war SQL_ADD, und beim Ausführen des Vorgangs ist in einer oder mehreren Zeilen ein Fehler aufgetreten, aber mindestens eine Zeile wurde erfolgreich hinzugefügt. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> (Dieser Fehler wird nur ausgelöst, wenn eine Anwendung mit einer ODBC 2. arbeitet. *x* Treiber.)|  
|01S07|Teilbereiche wurden abgeschnitten|Die *Vorgang* Argument war SQL_FETCH_BY_BOOKMARK, der Datentyp des Puffers Anwendung war nicht SQL_C_CHAR oder sql_c_binary angegeben und die Daten an Application-Puffer für eine oder mehrere Spalten zurückgegeben wurden abgeschnitten. (Für numerische C-Datentypen, wurde die Nachkommastellen der Zahl abgeschnitten. Für die Zeit, Zeitstempel und Intervall C-Datentypen, die eine Komponente enthalten, wurde der Bruchteil der Zeit abgeschnitten.)<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|Die *Vorgang* Argument war SQL_FETCH_BY_BOOKMARK und der Datenwert einer Spalte im Resultset konnte nicht auf den angegebenen Datentyp konvertiert werden die *TargetType* Argument im Aufruf von **SQLBindCol**.<br /><br /> Die *Vorgang* Argument war SQL_UPDATE_BY_BOOKMARK oder SQL_ADD und der Datenwert in den Puffern für die Anwendung konnte nicht in den Datentyp einer Spalte im Resultset konvertiert werden.|  
|07009|Ungültiger Deskriptorindex|Das Argument *Vorgang* SQL_ADD war und eine Spaltennummer, die größer als die Anzahl der Spalten im Resultset eine Spalte gebunden war.|  
|21S02|Spaltenzahl der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|Das Argument *Vorgang* SQL_UPDATE_BY_BOOKMARK; wurde und keine Spalten aktualisiert wurden, da alle Spalten aufgehoben oder nur-Lese wurden- oder der Wert in die gebundenen Längen-/Indikatorpuffer SQL_COLUMN_IGNORE war.|  
|22001|Zeichenfolgedaten rechts abgeschnitten|Die Zuweisung von einem Zeichen- oder binären Wert einer Spalte im Resultset führte das Abschneiden von NichtLeer (für Zeichen) oder ungleich Null (für binär)-Zeichen oder Bytes.|  
|22003|Numerischer Wert außerhalb des gültigen Bereichs|Die *Vorgang* Argument war SQL_ADD oder SQL_UPDATE_BY_BOOKMARK und die Zuweisung eines numerischen Werts einer Spalte im Resultset, verursacht des gesamten (im Gegensatz zu Bruch) Teils der Zahl abgeschnitten wird.<br /><br /> Das Argument *Vorgang* SQL_FETCH_BY_BOOKMARK war und den numerischen Wert für eine oder mehrere gebundene Spalten hätte ein Verlust signifikanter Ziffern.|  
|22007|Ungültiges Datetime-format|Die *Vorgang* Argument war SQL_ADD oder SQL_UPDATE_BY_BOOKMARK und die Zuweisung von einen Date- oder Timestamp-Wert an eine Spalte im Resultset, das verursacht hat, der Jahr, Monat oder Tagesfeld für die sich außerhalb des gültigen Bereichs.<br /><br /> Das Argument *Vorgang* SQL_FETCH_BY_BOOKMARK war und den Date- oder Timestamp-Wert für eine oder mehrere gebundene Spalten zurückgegeben hätte das Jahr, Monat oder Tagesfeld für die sich außerhalb des gültigen Bereichs.|  
|22008|Überlauf im Datum/Uhrzeit-Feld|Die *Vorgang* Argument war SQL_ADD oder SQL_UPDATE_BY_BOOKMARK und die Leistung von "DateTime"-Arithmetik auf Daten an eine Spalte im Resultset gesendet werden, die in einem Datetime-Feld (das Jahr, Monat, Tag, Stunde, Minute oder Sekunde geführt haben Feld) das Ergebnis außerhalb des zulässigen Bereichs von Werten zurück, für das Feld oder ungültige wird anhand des gregorianischen Kalenders natürlichen-Regeln für DateTime-Werte.<br /><br /> Die *Vorgang* Argument war SQL_FETCH_BY_BOOKMARK und die Leistung von "DateTime"-Arithmetik auf Daten aus dem Resultset abgerufen werden, die in einem Datetime-Feld (das Jahr, Monat, Tag, Stunde, Minute oder zweites Feld) der geführt haben die Ergebnis außerhalb des zulässigen Bereichs von Werten zurück, für das Feld oder ungültiger basierend auf dem gregorianischen Kalender natürlichen Regeln für DateTime-Werte.|  
|22015|Überlauf bei Intervallfeld|Die *Vorgang* Argument war SQL_ADD oder SQL_UPDATE_BY_BOOKMARK und die Zuweisung von einem genauen numerischen oder C Intervalltyp auf ein Intervall von SQL-Datentyp verursacht einen Verlust signifikanter Ziffern.<br /><br /> Die *Vorgang* Argument war SQL_ADD oder SQL_UPDATE_BY_BOOKMARK; Wenn Sie ein Intervall von SQL-Typ zuweisen, gab es keine Darstellung des Werts von der C-Typ in der SQL-Typ-Intervall.<br /><br /> Die *Vorgang* Argument war SQL_FETCH_BY_BOOKMARK und in das Feld "führende" C Intervalltyp aus einer genauen numerischen oder Intervall SQL-Typ zuweisen ein Verlust signifikanter Ziffern verursacht hat.<br /><br /> Die *Vorgang* Argument war SQL_FETCH_BY_BOOKMARK; Wenn ein von C-Intervalltyp zuweisen, gab es keine Darstellung des Werts von der SQL-Typ in den Intervalltyp C.|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|Die *Vorgang* Argument war SQL_FETCH_BY_BOOKMARK; der C-Typ wurde eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp; der SQL-Typ der Spalte einen Zeichendatentyp; und der Wert in der Spalte nicht wurde ein gültiger Literale des gebundenen Typen aus C#.<br /><br /> Das Argument *Vorgang* SQL_ADD oder SQL_UPDATE_BY_BOOKMARK war, wurde des SQL-Typs, eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp; der C-Typ SQL_C_CHAR; und der Wert in der Spalte nicht wurde ein gültiger Literal vom den SQL-Typ gebunden.|  
|23000|Verletzung der integritätseinschränkung|Die *Vorgang* Argument war SQL_ADD, SQL_DELETE_BY_BOOKMARK oder SQL_UPDATE_BY_BOOKMARK und eine integritätseinschränkung verletzt wurde.<br /><br /> Die *Vorgang* Argument war SQL_ADD und eine Spalte, die nicht gebunden wurde als NOT NULL und keinen Standard besitzt definiert ist.<br /><br /> Die *Vorgang* Argument war SQL_ADD, die in die Grenze angegebene Länge *StrLen_or_IndPtr* Puffer war SQL_COLUMN_IGNORE aus, und die Spalte keinen Standardwert.|  
|24000|Ungültiger Cursorstatus|Die *StatementHandle* wurde in einem ausgeführten Zustand befindet, aber kein Resultset zugeordnet wurde die *StatementHandle*.|  
|40001|Serialisierungsfehler|Die Transaktion wurde wegen eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntaxfehler oder zugriffsverletzung|Der Treiber konnte die Zeile zu sperren, je nach Bedarf zum Ausführen des Vorgangs angefordert wird, der *Vorgang* Argument.|  
|44000|WITH CHECK OPTION-Verstoß|Die *Vorgang* Argument war SQL_ADD oder SQL_UPDATE_BY_BOOKMARK und die Einfügung oder Updatevorgang für eine Tabelle ausgeführt wurde (oder eine Tabelle aus der angezeigten Tabelle abgeleitet), die erstellt wurde, indem **WITH CHECK OPTION**, so, dass eine oder mehrere Zeilen von den Insert-betroffen oder Update wird nicht mehr in der angezeigten Tabelle vorhanden sein.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLBulkOperations** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) der angegebenen *StatementHandle* war nicht in einem ausgeführten Zustand befindet. Die Funktion wurde aufgerufen, ohne den ersten Aufruf **SQLExecDirect**, **SQLExecute**, oder eine Katalogfunktion auf.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) der Treiber wurde eine ODBC-2. *x* -Treiber und **SQLBulkOperations** wurde aufgerufen, eine *StatementHandle* vor **SQLFetchScroll** oder **SQLFetch**  aufgerufen wurde.<br /><br /> (DM) **SQLBulkOperations** wurde aufgerufen, nachdem **SQLExtendedFetch** aufgerufen wurde, auf die *StatementHandle*.|  
|HY011|Attribut kann jetzt nicht festgelegt werden|(DM) der Treiber wurde eine ODBC-2. *x* Treiber und das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut festgelegt wurde, zwischen den Aufrufen **SQLFetch** oder **SQLFetchScroll** und **SQLBulkOperations** .|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|Die *Vorgang* Argument SQL_ADD oder SQL_UPDATE_BY_BOOKMARK; ein Datenwert war es sich nicht um einen null-Zeiger; wurde von der C-Datentyp SQL_C_BINARY oder SQL_C_CHAR; und der Spaltenwert für die Länge war kleiner als 0, aber nicht gleich auf SQL_DATA_AT_EXEC , SQL_COLUMN_IGNORE SQL_NTS oder SQL_NULL_DATA oder kleiner als oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Der Wert in ein Längen-/Indikatorpuffer war SQL_DATA_AT_EXEC. der SQL-Typ wurde einem SQL_LONGVARCHAR SQL_LONGVARBINARY oder einen long-Daten datenquellenspezifische Datentyp; und welche Informationen SQL_NEED_LONG_DATA_LEN in **SQLGetInfo** wurde von "Y".<br /><br /> Die *Vorgang* Argument war SQL_ADD, das SQL_ATTR_USE_BOOKMARK-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde und Spalte 0 in einen Puffer, dessen Länge nicht mit die maximale Länge für das Lesezeichen für dieses Resultset stimmte, gebunden wurde. (Diese Länge finden Sie im Feld SQL_DESC_OCTET_LENGTH IRD und erhalten Sie durch Aufrufen von **SQLDescribeCol**, **SQLColAttribute**, oder **SQLGetDescField**.)|  
|HY092|Ungültiges Attribut-ID|(DM) der angegebene Wert für die *Vorgang* Argument war ungültig.<br /><br /> Die *Vorgang* Argument war SQL_ADD, SQL_UPDATE_BY_BOOKMARK oder SQL_DELETE_BY_BOOKMARK und das SQL_ATTR_CONCURRENCY-Anweisungsattribut auf SQL_CONCUR_READ_ONLY festgelegt wurde.<br /><br /> Die *Vorgang* Argument war SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK oder SQL_UPDATE_BY_BOOKMARK, und die Lesezeichenspalte wurde nicht gebunden oder das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF festgelegt wurde.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Treiber oder die Datenquelle unterstützt nicht den in der angeforderte Vorgang die *Vorgang* Argument.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr** mit einer *Attribut* SQL_ATTR_QUERY_TIMEOUT Argument.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
  
> [!CAUTION]  
>  Informationen zu fehlerhaften Anweisung besagt **SQLBulkOperations** in aufgerufen werden kann und was sie tun muss, für die Kompatibilität mit ODBC 2. *X* -Anwendungen finden Sie unter den [Blockcursor, scrollbare Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) Abschnitt in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
  
 Eine Anwendung verwendet **SQLBulkOperations** , führen Sie die folgenden Vorgänge für die Basistabelle oder Sicht, die der aktuellen Abfrage entsprechen:  
  
-   Fügen Sie neue Zeilen hinzu.  
  
-   Aktualisieren Sie eine Gruppe von Zeilen, die in der jede Zeile von einem Lesezeichen identifiziert wird.  
  
-   Löschen Sie eine Gruppe von Zeilen, die in der jede Zeile von einem Lesezeichen identifiziert wird.  
  
-   Rufen Sie eine Gruppe von Zeilen, die in der jede Zeile von einem Lesezeichen identifiziert wird.  
  
 Nach einem Aufruf von **SQLBulkOperations**, der die Position des Blocks ist nicht definiert. Rufen Sie die Anwendung muss **SQLFetchScroll** um die Cursorposition festzulegen. Es sollte eine Anwendung aufrufen **SQLFetchScroll** nur mit einer *FetchOrientation* Argument SQL_FETCH_FIRST SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE oder sql_fetch_bookmark auf. Die Position des Cursors ist nicht definiert, wenn die Anwendung ruft **SQLFetch** oder **SQLFetchScroll** mit einer *FetchOrientation* Argument SQL_FETCH_PRIOR, SQL_FETCH_NEXT, oder SQL_FETCH_RELATIVE.  
  
 Eine Spalte kann ignoriert werden, in Massenvorgängen, die ausgeführt werden, durch einen Aufruf von **SQLBulkOperations** durch Festlegen der im Aufruf der angegebenen Spalte Längen-/Indikatorpuffer **SQLBindCol**, um SQL_COLUMN_IGNORE.  
  
 Es ist nicht erforderlich, für die Anwendung das Anweisungsattribut SQL_ATTR_ROW_OPERATION_PTR beim Aufruf **SQLBulkOperations** da Zeilen beim Ausführen von Massenvorgängen mit dieser Funktion nicht ignoriert werden können.  
  
 Der Puffer, der auf das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut enthält die Anzahl der durch einen Aufruf von betroffenen Zeilen **SQLBulkOperations**.  
  
 Wenn die *Vorgang* -Argument SQL_ADD oder SQL_UPDATE_BY_BOOKMARK und die Select-Liste der mit dem Cursor verknüpfte Abfragespezifikation enthält mehr als einen Verweis auf die gleiche Spalte ist, es ist treiberdefinierten, ob ein Fehler wird generiert, oder der Treiber ignoriert die doppelt vorhandenen Verweise und führt die angeforderten Vorgänge.  
  
 Weitere Informationen zur Verwendung von **SQLBulkOperations**, finden Sie unter [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).  
  
## <a name="performing-bulk-inserts"></a>Fügt ein auszuführen  
 Zum Einfügen von Daten mit **SQLBulkOperations**, eine Anwendung führt die folgende Sequenz von Schritten:  
  
1.  Führt eine Abfrage, die ein Resultset zurückgibt.  
  
2.  Legt das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf die Anzahl der Zeilen, die sie einfügen möchte.  
  
3.  Aufrufe **SQLBindCol** um die Daten zu binden, die sie einfügen möchte. Die Daten werden in ein Array mit einer Größe, die gleich dem Wert des SQL_ATTR_ROW_ARRAY_SIZE gebunden.  
  
    > [!NOTE]  
    >  Die Größe des Arrays zeigt das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR sollte ein null-Zeiger sein.  
  
4.  Aufrufe **SQLBulkOperations**(*StatementHandle,* SQL_ADD), die den Einfügevorgang auszuführen.  
  
5.  Wenn die Anwendung das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR festgelegt wurde, können sie dieses Array aus, um das Ergebnis des Vorgangs finden Sie unter überprüfen.  
  
 Wenn eine Anwendung Spalte 0 gebunden vor dem Aufrufen **SQLBulkOperations** mit einer *Vorgang* Argument SQL_ADD, der Treiber aktualisiert die Puffern mit gebundenen Spalten 0 mit den Werten der Lesezeichen für die neu eingefügte Zeile. Damit dies eintritt muss die Anwendung das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt haben vor dem Ausführen der Anweisung. (Dies funktioniert nicht mit einer ODBC 2. *x* Treiber.)  
  
 Long-Daten können mithilfe der Aufrufe von der SQLParamData und SQLPutData in Teilen von SQLBulkOperations, hinzugefügt werden. Weitere Informationen finden Sie unter "Bereitstellen von lange Daten für Bulk Insert und Update" weiter unten in dieser Funktionsverweis.  
  
 Es ist nicht erforderlich, für die Anwendung aufrufen, **SQLFetch** oder **SQLFetchScroll** vor **SQLBulkOperations** (außer wenn für eine ODBC 2. *X* -Treiber; Siehe [Abwärtskompatibilität und zur Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)).  
  
 Das Verhalten ist treiberdefinierten Wenn **SQLBulkOperations**, mit einem *Vorgang* SQL_ADD, Argument für einen Cursor, enthält doppelte Spalten, aufgerufen wird. Der Treiber kann ein SQLSTATE treiberdefinierten zurück, die Daten in die erste Spalte, die im Resultset angezeigt wird festgelegt, oder führen Sie andere Treiber definierten Verhalten hinzufügen.  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>Durchführen von Massenaktualisierungen mithilfe von Lesezeichen  
 Um massenaktualisierungen auszuführen, mithilfe von Lesezeichen mit **SQLBulkOperations**, eine Anwendung die folgenden Schritte nacheinander ausführt:  
  
1.  Legt das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE fest.  
  
2.  Führt eine Abfrage, die ein Resultset zurückgibt.  
  
3.  Legt das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf die Anzahl der Zeilen, die sie aktualisieren möchte.  
  
4.  Aufrufe **SQLBindCol** um die Daten zu binden, die sie aktualisieren möchte. Die Daten werden in ein Array mit einer Größe, die gleich dem Wert des SQL_ATTR_ROW_ARRAY_SIZE gebunden. Außerdem ruft **SQLBindCol** Spalte 0 (die Lesezeichenspalte) zu binden.  
  
5.  Kopien gebunden Lesezeichen für die Zeilen an, die sie interessiert ist, aktualisieren Sie in das Array an die Spalte 0.  
  
6.  Aktualisiert die Daten in den Puffern mit gebundenen.  
  
    > [!NOTE]  
    >  Die Größe des Arrays zeigt das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR sollte ein null-Zeiger sein.  
  
7.  Aufrufe **SQLBulkOperations**(*StatementHandle,* SQL_UPDATE_BY_BOOKMARK).  
  
    > [!NOTE]  
    >  Wenn die Anwendung das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR festgelegt wurde, können sie dieses Array aus, um das Ergebnis des Vorgangs finden Sie unter überprüfen.  
  
8.  Ruft optional **SQLBulkOperations**(*StatementHandle*, SQL_FETCH_BY_BOOKMARK) zum Abrufen von Daten in die gebundene Anwendungspuffer auf, um sicherzustellen, dass das Update aufgetreten ist.  
  
9. Wenn Daten aktualisiert wurde, ändert der Treiber den Wert in der zeilenstatusarray für die entsprechenden Zeilen in SQL_ROW_UPDATED an.  
  
 Massenaktualisierungen von ausgeführten **SQLBulkOperations** zählen long-Daten über Aufrufe **SQLParamData** und **SQLPutData**. Weitere Informationen finden Sie unter "Bereitstellen von lange Daten für Bulk Insert und Update" weiter unten in dieser Funktionsverweis.  
  
 Wenn Lesezeichen für Cursor persistent speichern, die Anwendung muss nicht aufrufen, **SQLFetch** oder **SQLFetchScroll** vor dem Aktualisieren von Lesezeichen. Sie können Lesezeichen verwenden, die sie von einem vorherigen Cursor gespeichert wurde. Wenn Lesezeichen für Cursor nicht beibehalten werden, muss die Anwendung aufrufen **SQLFetch** oder **SQLFetchScroll** Lesezeichen abrufen.  
  
 Das Verhalten ist treiberdefinierten Wenn **SQLBulkOperations**, mit einem *Vorgang* SQL_UPDATE_BY_BOOKMARK, Argument für einen Cursor, enthält doppelte Spalten, aufgerufen wird. Der Treiber kann ein SQLSTATE treiberdefinierten zurückgeben, aktualisieren Sie die erste Spalte, die im Resultset angezeigt wird oder andere Treiber definierten Verhalten führen.  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>Ausführen von Massenladen abruft, mithilfe von Lesezeichen  
 Zum Ausführen der Bulk-Abrufvorgänge mithilfe von Lesezeichen mit **SQLBulkOperations**, eine Anwendung die folgenden Schritte nacheinander ausführt:  
  
1.  Legt das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE fest.  
  
2.  Führt eine Abfrage, die ein Resultset zurückgibt.  
  
3.  Legt das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf die Anzahl der Zeilen, die abgerufen werden sollen.  
  
4.  Aufrufe **SQLBindCol** um die Daten zu binden, die abgerufen werden sollen. Die Daten werden in ein Array mit einer Größe, die gleich dem Wert des SQL_ATTR_ROW_ARRAY_SIZE gebunden. Außerdem ruft **SQLBindCol** Spalte 0 (die Lesezeichenspalte) zu binden.  
  
5.  Kopien gebunden Lesezeichen für die Zeilen an, die sie interessiert ist, beim Abrufen in das Array von Spalte 0. (Dies setzt voraus, dass Lesezeichen auf die Anwendung bereits separat erworben hat.)  
  
    > [!NOTE]  
    >  Die Größe des Arrays zeigt das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR sollte ein null-Zeiger sein.  
  
6.  Aufrufe **SQLBulkOperations**(*StatementHandle,* SQL_FETCH_BY_BOOKMARK).  
  
7.  Wenn die Anwendung das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR festgelegt wurde, können sie dieses Array aus, um das Ergebnis des Vorgangs finden Sie unter überprüfen.  
  
 Wenn Lesezeichen für Cursor persistent speichern, die Anwendung muss nicht aufrufen, **SQLFetch** oder **SQLFetchScroll** vor dem Abrufen von Lesezeichen. Sie können Lesezeichen verwenden, die sie von einem vorherigen Cursor gespeichert wurde. Wenn Lesezeichen für Cursor nicht beibehalten werden, muss die Anwendung aufrufen **SQLFetch** oder **SQLFetchScroll** einmal zum Abrufen von Lesezeichen.  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>Ausführen von Massenladen werden mithilfe von Lesezeichen gelöscht.  
 Mithilfe von Lesezeichen mit massenlöschungen auszuführenden **SQLBulkOperations**, eine Anwendung die folgenden Schritte nacheinander ausführt:  
  
1.  Legt das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE fest.  
  
2.  Führt eine Abfrage, die ein Resultset zurückgibt.  
  
3.  Legt das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf die Anzahl der Zeilen, die sie löschen möchte.  
  
4.  Aufrufe **SQLBindCol** Spalte 0 (die Lesezeichenspalte) zu binden.  
  
5.  Kopien gebunden Lesezeichen für die Zeilen an, die sie interessiert ist, löschen Sie in das Array, an die Spalte 0.  
  
    > [!NOTE]  
    >  Die Größe des Arrays zeigt das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR sollte gleich SQL_ATTR_ROW_ARRAY_SIZE oder SQL_ATTR_ROW_STATUS_PTR sollte ein null-Zeiger sein.  
  
6.  Calls **SQLBulkOperations**(*StatementHandle,* SQL_DELETE_BY_BOOKMARK).  
  
7.  Wenn die Anwendung das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR festgelegt wurde, können sie dieses Array aus, um das Ergebnis des Vorgangs finden Sie unter überprüfen.  
  
 Wenn Lesezeichen über Cursor beibehalten werden, die Anwendung muss nicht aufrufen, **SQLFetch** oder **SQLFetchScroll** vor dem Löschen von Lesezeichen. Sie können Lesezeichen verwenden, die sie von einem vorherigen Cursor gespeichert wurde. Wenn Lesezeichen für Cursor nicht beibehalten werden, muss die Anwendung aufrufen **SQLFetch** oder **SQLFetchScroll** einmal zum Abrufen von Lesezeichen.  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>Bereitstellen von Long-Daten für Masseneinfügungen und-Updates  
 Long-Daten können bereitgestellt werden, für masseneinfügungen und-Updates ausgeführt, die durch Aufrufe von **SQLBulkOperations**. Zum Einfügen oder Aktualisieren von long-Daten, führt eine Anwendung die folgenden Schritte aus, zusätzlich zu den in den Abschnitten "Ausführen von Masseneinfügungen" und "Ausführen von Massenladen Updates mithilfe von Lesezeichen" weiter oben in diesem Thema beschriebenen Schritten.  
  
1.  Wenn bindet die Daten mithilfe von **SQLBindCol**, die Anwendung wird einen anwendungsdefinierten Wert wie die Nummer der Spalte, in der  *\*TargetValuePtr* Puffer für die Data-at-Execution Spalten. Der Wert kann später verwendet werden, um die Spalte identifizieren.  
  
     Die Anwendung platziert, das Ergebnis der SQL_LEN_DATA_AT_EXEC (*Länge*)-Makro in der  *\*StrLen_or_IndPtr* Puffer. Wenn der SQL-Datentyp der Spalte SQL_LONGVARBINARY, SQL_LONGVARCHAR oder einem long-Datentyp datenquellenspezifische Daten und "Y" für den Typ der SQL_NEED_LONG_DATA_LEN Informationen in der Treiber gibt **SQLGetInfo**, *Länge*  ist die Anzahl der Datenbytes, die für den Parameter; gesendet werden andernfalls muss einen nicht negativen Wert und wird ignoriert.  
  
2.  Wenn **SQLBulkOperations** aufgerufen wird, wenn Data-at-Execution-Spalten, die Funktion gibt SQL_NEED_DATA zurück und setzt den Vorgang fort mit Schritt 3 fort, die folgenden vorhanden sind. (Wenn keine Data-at-Execution-Spalten vorhanden sind, ist der Prozess abgeschlossen.)  
  
3.  Ruft die Anwendung **SQLParamData** zum Abrufen der Adresse der  *\*TargetValuePtr* Puffer für die erste Data-at-Execution-Spalte, die verarbeitet werden. **SQLParamData** wird SQL_NEED_DATA zurückgegeben. Die Anwendung ruft den Anwendung definierte Wert aus der  *\*TargetValuePtr* Puffer.  
  
    > [!NOTE]  
    >  Obwohl Data-at-Execution-Parameter Data-at-Execution-Spalten entsprechen, wird der Wert von zurückgegeben **SQLParamData** ist unterschiedlich.  
  
     Data-at-Execution-Spalten in einem Rowset, für die Daten mit gesendet werden, sind **SQLPutData** Wenn eine Zeile aktualisiert oder eingefügt werden, mit **SQLBulkOperations**. Sie sind mit gebunden **SQLBindCol**. Der Rückgabewert von **SQLParamData** ist die Adresse der Zeile in der **TargetValuePtr* Puffer, der verarbeitet wird.  
  
4.  Ruft die Anwendung **SQLPutData** einmal oder mehrmals, um Daten für die Spalte zu senden. Mehrere ist erforderlich, wenn der Datenwert in zurückgegeben werden, kann die  *\*TargetValuePtr* im angegebenen Puffer **SQLPutData**; mehrere Aufrufe **SQLPutData** für dieselbe Spalte dürfen nur beim Senden von Zeichendaten C an eine Spalte mit einem Zeichen oder den binären datenquellenspezifische Datentyp oder beim Senden von Binärdaten C an eine Spalte mit einem Zeichen, binär, oder geben Sie die spezifischen Daten.  
  
5.  Ruft die Anwendung **SQLParamData** erneut aus, um zu signalisieren, dass alle Daten für die Spalte gesendet wurde.  
  
    -   Wenn es weitere Data-at-Execution-Spalten, **SQLParamData** gibt SQL_NEED_DATA sowie die Adresse des der *TargetValuePtr* Puffer für die nächste Data-at-Execution-Spalte, die verarbeitet werden. Die Anwendung wiederholt die Schritte 4 und 5.  
  
    -   Wenn keine weiteren Data-at-Execution-Spalten vorhanden sind, ist der Prozess abgeschlossen. Wenn die Anweisung erfolgreich ausgeführt wurde **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO; Fehler bei der Ausführung gibt, wird SQL_ERROR zurückgegeben. An diesem Punkt **SQLParamData** können alle SQLSTATE, der zurückgegeben werden kann zurückgeben **SQLBulkOperations**.  
  
 Wenn der Vorgang abgebrochen wird oder ein Fehler, in auftritt **SQLParamData** oder **SQLPutData** nach **SQLBulkOperations** wird SQL_NEED_DATA zurückgegeben und vor dem Senden von Daten für alle Data-at-Execution-Spalten, die Anwendung kann aufrufen nur **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions** , **SQLParamData**, oder **SQLPutData** für die Anweisung oder die Verbindung mit der Anweisung verknüpft ist. Wenn sie für die Anweisung oder die Verbindung mit der Anweisung verknüpfte jede andere Funktion aufruft, gibt die Funktion SQL_ERROR zurück, und SQLSTATE HY010 (Sequenzfehler funktionieren).  
  
 Wenn die Anwendung ruft **SQLCancel** während der Treiber noch Daten für die Data-at-Execution-Spalten benötigt, bricht der Treiber den Vorgang ab. Die Anwendung kann dann aufrufen **SQLBulkOperations** erneut Abbrechen wirkt sich nicht den Cursorstatus oder der aktuellen Cursorposition.  
  
## <a name="row-status-array"></a>Zeilenstatusarray  
 Die zeilenstatusarray Statuswerte für jede Zeile der Daten im Rowset enthält, nach einem Aufruf von **SQLBulkOperations**. Der Treiber setzt die Status-Werte in diesem Array nach einem Aufruf von **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, oder **SQLBulkOperations** . Dieses Array wird zunächst durch einen Aufruf von aufgefüllt **SQLBulkOperations** Wenn **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen wurde, bevor **SQLBulkOperations** . Dieses Array wird durch das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR verwiesen. Die Anzahl der Elemente in der Zeile Status Arrays muss es sich um die Anzahl der Zeilen im Rowset (gemäß dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut-Anweisung) gleich. Weitere Informationen zu diesem zeilenstatusarray, finden Sie unter [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgende Beispiel ruft 10 Zeilen gleichzeitig aus der Customers-Tabelle ab. Sie werden dann aufgefordert, den Benutzer für eine Aktion. Zur Reduzierung des Netzwerkverkehrs, der Beispiel-Puffer updates, Löschvorgängen und und fügt lokal in den gebundenen Arrays, sondern auf Offsets hinter die Rowsetdaten. Wenn der Benutzer auswählt, die zum Senden von Updates, löschungen und fügt in der Datenquelle ein, der Code legt die Bindung, die Abweichung entsprechend fest und ruft **SQLBulkOperations**. Der Benutzer kann nicht mehr als 10-Updates, löschungen oder einfügungen Puffer ist aus Gründen der Einfachheit.  
  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen eines einzelnen Felds einen Deskriptor|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Abrufen von mehreren Feldern einen Deskriptor|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen Felds einen Deskriptor|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen von mehreren Feldern einen Deskriptor|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Positionieren des Cursors, Aktualisieren von Daten im Rowset, oder aktualisieren oder Löschen von Daten im rowset|[SQLSetPos-Funktion](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Wenn eine Anweisungsattribut|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
