---
title: SQLSetPos-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetPos
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetPos
helpviewer_keywords:
- SQLSetPos function [ODBC]
ms.assetid: 80190ee7-ae3b-45e5-92a9-693eb558f322
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86386460c3abc9ab7b6463b01ee4388e9186ad2b
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536319"
---
# <a name="sqlsetpos-function"></a>SQLSetPos-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLSetPos** legt die Cursorposition in einem Rowset fest und ermöglicht es einer Anwendung, um Daten im Rowset zu aktualisieren oder zu aktualisieren oder Löschen von Daten im Resultset.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetPos(  
      SQLHSTMT        StatementHandle,  
      SQLSETPOSIROW   RowNumber,  
      SQLUSMALLINT    Operation,  
      SQLUSMALLINT    LockType);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *RowNumber*  
 [Eingabe] Die Position der Zeile im Rowset für das Ausführen des Vorgangs angegeben, mit der *Vorgang* Argument. Wenn *RowNumber* gleich 0 ist, der Vorgang gilt für jede Zeile im Rowset.  
  
 Weitere Informationen finden Sie unter "Kommentare".  
  
 *Vorgang*  
 [Eingabe] Der Vorgang ausführen:  
  
 SQL_POSITION SQL_REFRESH SQL_UPDATE SQL_DELETE  
  
> [!NOTE]
>  Der SQL_ADD-Wert für die *Vorgang* Argument ist veraltet für ODBC 3.*.x*. ODBC 3. *x* Treiber müssen SQL_ADD für die Abwärtskompatibilität zu unterstützen. Diese Funktionalität wurde ersetzt durch einen Aufruf von **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD. Wenn eine ODBC-3. *x* Anwendung funktioniert mit einer ODBC 2. *X* Treiber, der Treiber-Manager ordnet einen Aufruf von **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD auf **SQLSetPos** mit einer  *Vorgang* von SQL_ADD.  
  
 Weitere Informationen finden Sie unter "Kommentare".  
  
 *LockType*  
 [Eingabe] Gibt an, wie die Zeile zu sperren, nach dem Ausführen des Vorgangs angegeben, der *Vorgang* Argument.  
  
 SQL_LOCK_NO_CHANGE SQL_LOCK_EXCLUSIVE SQL_LOCK_UNLOCK  
  
 Weitere Informationen finden Sie unter "Kommentare".  
  
 **Gibt zurück**  
  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetPos** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLSetPos** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
 Für alle diese SQLSTATEs, der SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück (mit Ausnahme der 01xxx SQLSTATEs) zurückgeben kann, wird SQL_SUCCESS_WITH_INFO zurückgegeben, wenn bei ein oder mehrere, aber nicht alle Zeilen eines mehrzeiligen-Vorgangs ein Fehler auftritt, und SQL_ERROR zurückgegeben wird, wenn es sich bei Auftreten eines Fehlers auf einem einzeiliges-Vorgang.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01001|Konflikt beim Cursorvorgang|Die *Vorgang* Argument war SQL_DELETE oder SQL_UPDATE auf, und keine Zeilen oder mehr als eine Zeile gelöscht oder aktualisiert wurden. (Weitere Informationen zu Updates für mehr als eine Zeile, finden Sie unter der Beschreibung der SQL_ATTR_SIMULATE_CURSOR *Attribut* in **SQLSetStmtAttr**.) (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)<br /><br /> Die *Vorgang* Argument war SQL_DELETE oder SQL_UPDATE und der Vorgang ist fehlgeschlagen, da vollständige Parallelität. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgedaten rechts abgeschnitten|Die *Vorgang* Argument war SQL_REFRESH und Zeichenfolgen- oder Binärdaten, die für eine Spalte oder Spalten mit dem Datentyp des Typs SQL_C_CHAR oder sql_c_binary angegeben zurückgegeben, die in das Abschneiden von nicht leeren Zeichen oder binäre Daten ungleich NULL geführt haben.|  
|01S01|Fehler in Zeile|Die *RowNumber* Argument wurde 0 und Fehler in einer oder mehreren Zeilen beim Ausführen des Vorgangs angegeben, mit der *Vorgang* Argument.<br /><br /> (SQL_SUCCESS_WITH_INFO wird zurückgegeben, wenn bei ein oder mehrere, aber nicht alle Zeilen eines mehrzeiligen-Vorgangs ein Fehler auftritt, und wenn für einen Vorgang für die einzelnen Zeile ein Fehler auftritt, wird SQL_ERROR zurückgegeben.)<br /><br /> (Diese SQLSTATE wird nur zurückgegeben, wenn **SQLSetPos** wird aufgerufen, nachdem **SQLExtendedFetch**, wenn der Treiber einer ODBC 2. *X* Treiber und die Cursorbibliothek wird nicht verwendet.)|  
|01S07|Teilbereiche wurden abgeschnitten|Die *Vorgang* Argument war SQL_REFRESH, der Datentyp des Puffers Anwendung war nicht SQL_C_CHAR oder sql_c_binary angegeben und die Daten an Application-Puffer für eine oder mehrere Spalten zurückgegeben wurden abgeschnitten. Für numerische Datentypen wurde die Nachkommastellen der Zahl abgeschnitten. Für die Zeit, Zeitstempel und Interval-Datentypen, die eine Komponente enthält wurde der Bruchteil der Zeit abgeschnitten.<br /><br /> (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|Der Datenwert einer Spalte im Resultset konnte nicht konvertiert werden, um den angegebenen Datentyp *TargetType* im Aufruf von **SQLBindCol**.|  
|07009|Ungültiger Deskriptorindex|Das Argument *Vorgang* SQL_REFRESH oder SQL_UPDATE war und eine Spaltennummer, die größer als die Anzahl der Spalten im Resultset eine Spalte gebunden war.|  
|21S02|Spaltenzahl der abgeleiteten Tabelle stimmt nicht mit der Spaltenliste überein|Das Argument *Vorgang* SQL_UPDATE war und keine Spalten aktualisiert wurden, da alle Spalten entweder nicht gebundenen, schreibgeschützt wurden oder der Wert in die gebundenen Längen-/Indikatorpuffer SQL_COLUMN_IGNORE war.|  
|22001|Zeichenfolgendaten, rechts abgeschnitten.|Die *Vorgang* Argument war SQL_UPDATE auf, und die Zuweisung von einem Zeichen- oder binären Wert einer Spalte führt das Abschneiden von NichtLeer (für Zeichen) oder ungleich Null (für binär)-Zeichen oder Bytes.|  
|22003|Numerischer Wert außerhalb des gültigen Bereichs|Das Argument *Vorgang* SQL_UPDATE wurde und die Zuweisung eines numerischen Werts einer Spalte im Resultset verursacht des gesamten (im Gegensatz zu Bruch) Teils der Zahl abgeschnitten wird.<br /><br /> Das Argument *Vorgang* SQL_REFRESH war und den numerischen Wert für eine oder mehrere gebundene Spalten hätte ein Verlust signifikanter Ziffern.|  
|22007|Ungültiges Datetime-format|Das Argument *Vorgang* SQL_UPDATE wurde und die Zuweisung von einen Date- oder Timestamp-Wert an eine Spalte im Resultset, das verursacht hat, der Jahr, Monat oder Tagesfeld für die sich außerhalb des gültigen Bereichs.<br /><br /> Das Argument *Vorgang* SQL_REFRESH war und den Date- oder Timestamp-Wert für eine oder mehrere gebundene Spalten zurückgegeben hätte das Jahr, Monat oder Tagesfeld für die sich außerhalb des gültigen Bereichs.|  
|22008|Überlauf im Datum/Uhrzeit-Feld|Die *Vorgang* Argument war SQL_UPDATE auf, und die Leistung von "DateTime"-Arithmetik auf Daten an eine Spalte im Resultset gesendet werden, die in einem Datetime-Feld (das Jahr, Monat, Tag, Stunde, Minute oder zweites Feld) des Ergebnisses geführt haben basieren außerhalb des zulässigen Bereichs von Werten für das Feld oder ungültiger natürliche Regeln für den gregorianischen Kalender für DateTime-Werte.<br /><br /> Die *Vorgang* Argument war SQL_REFRESH und die Leistung von "DateTime"-Arithmetik auf Daten aus dem Resultset abgerufen werden, die in einem Datetime-Feld (das Jahr, Monat, Tag, Stunde, Minute oder zweites Feld) des Ergebnisses geführt haben basieren außerhalb des zulässigen Bereichs von Werten für das Feld oder ungültiger natürliche Regeln für den gregorianischen Kalender für DateTime-Werte.|  
|22015|Überlauf bei Intervallfeld|Die *Vorgang* Argument war SQL_UPDATE auf und die Zuweisung von einem genauen numerischen oder C Intervalltyp auf ein Intervall von SQL-Datentyp verursacht einen Verlust signifikanter Ziffern.<br /><br /> Die *Vorgang* Argument war SQL_UPDATE auf, wenn ein Intervall von SQL-Typ zuweisen, gab es keine Darstellung des Werts von der C-Typ in der SQL-Typ-Intervall.<br /><br /> Die *Vorgang* Argument war SQL_REFRESH und in das Feld "führende" C Intervalltyp aus einer genauen numerischen oder Intervall SQL-Typ zuweisen ein Verlust signifikanter Ziffern verursacht hat.<br /><br /> Die *Vorgang* Argument SQL_ aktualisieren, wenn ein von C-Intervalltyp zuweisen, gab es keine Darstellung des Werts von der SQL-Typ in den Intervalltyp C.|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|Die *Vorgang* Argument war SQL_REFRESH; der C-Typ wurde eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp; der SQL-Typ der Spalte einen Zeichendatentyp; und der Wert in der Spalte nicht wurde ein gültiger Literal mit dem C-Typ gebunden.<br /><br /> Das Argument *Vorgang* SQL_UPDATE wurde; der SQL-Typ wurde eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp, der C-Typ SQL_C_CHAR; und der Wert in der Spalte nicht wurde ein gültiger Literal des gebundenen Typen aus SQL.|  
|23000|Verletzung der integritätseinschränkung|Das Argument *Vorgang* SQL_DELETE oder SQL_UPDATE war und eine integritätseinschränkung verletzt wurde.|  
|24000|Ungültiger Cursorstatus|Die *StatementHandle* wurde in einem ausgeführten Zustand befindet, aber kein Resultset zugeordnet wurde die *StatementHandle*.<br /><br /> (DM) ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde, aber der Cursor positioniert wurde, vor dem Start des Resultsets oder nach das Ende des Resultsets.<br /><br /> Das Argument *Vorgang* war SQL_DELETE, SQL_REFRESH oder SQL_UPDATE auf, und der Cursor vor dem Start des Resultsets oder nach dem Ende des Resultsets positioniert wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|42000|Syntaxfehler oder zugriffsverletzung|Der Treiber konnte die Zeile zu sperren, je nach Bedarf zum Ausführen des Vorgangs angefordert, die im Argument *Vorgang*.<br /><br /> Der Treiber konnte die Zeile zu sperren, wie im Argument angefordert *LockType*.|  
|44000|WITH CHECK OPTION-Verstoß|Die *Vorgang* Argument war SQL_UPDATE auf, und das Update auf eine Tabelle ausgeführt wurde oder eine Tabelle abgeleitet wird, aus der angezeigten Tabelle durch Angabe erstellt wurde **WITH CHECK OPTION**, sodass eine oder mehrere Zeilen betroffen das Update wird nicht mehr in der angezeigten Tabelle vorhanden sein.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*, und klicken Sie dann die Funktion aufgerufen wurde erneut auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Diese asynchronen Funktion wurde noch ausgeführt werden, wenn die SQLSetPos-Funktion aufgerufen wurde.<br /><br /> (DM) der angegebenen *StatementHandle* war nicht in einem ausgeführten Zustand befindet. Die Funktion wurde aufgerufen, ohne den ersten Aufruf **SQLExecDirect**, **SQLExecute**, oder eine Katalogfunktion auf.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) der Treiber wurde eine ODBC-2. *x* -Treiber und **SQLSetPos** wurde aufgerufen, eine *StatementHandle* nach **SQLFetch** aufgerufen wurde.|  
|HY011|Attribut kann jetzt nicht festgelegt werden|(DM) der Treiber wurde eine ODBC-2. *x* -Treiber; die SQL_ATTR_ROW_STATUS_PTR Anweisung-Attribut festgelegt wurde, klicken Sie dann **SQLSetPos** war aufgerufen, bevor **SQLFetch**, **SQLFetchScroll**, oder **SQLExtendedFetch** aufgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|Die *Vorgang* Argument SQL_UPDATE auf, ein Datenwert wurde ein null-Zeiger, und der Spaltenwert für die Länge nicht wurde SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NULL_DATA, 0 oder kleiner als oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Die *Vorgang* Argument SQL_UPDATE; ein Datenwert war es sich nicht um einen null-Zeiger; wurde von der C-Datentyp SQL_C_BINARY oder SQL_C_CHAR; und der Spaltenwert für die Länge war kleiner als 0, aber nicht gleich auf SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE , SQL_NTS lauten oder SQL_NULL_DATA oder kleiner als oder gleich SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Der Wert in ein Längen-/Indikatorpuffer war SQL_DATA_AT_EXEC. der SQL-Typ wurde einem SQL_LONGVARCHAR SQL_LONGVARBINARY oder einen long-Daten datenquellenspezifische Datentyp; und welche Informationen SQL_NEED_LONG_DATA_LEN in **SQLGetInfo** wurde von "Y".|  
|HY092|Ungültiges Attribut-ID|(DM) der angegebene Wert für die *Vorgang* Argument war ungültig.<br /><br /> (DM) der angegebene Wert für die *LockType* Argument war ungültig.<br /><br /> Die *Vorgang* Argument war SQL_UPDATE oder SQL_DELETE und das SQL_ATTR_CONCURRENCY-Anweisungsattribut SQL_ATTR_CONCUR_READ_ONLY.|  
|HY107|Zeilenwert außerhalb des gültigen Bereichs|Der angegebene Wert für das Argument *RowNumber* war größer als die Anzahl der Zeilen im Rowset.|  
|HY109|Ungültige Cursorposition|Die zugeordneten Cursor der *StatementHandle* wurde als Vorwärtscursor, definiert, damit der Cursor nicht im Rowset positioniert werden kann. Siehe die Beschreibung für das SQL_ATTR_CURSOR_TYPE-Attribut im **SQLSetStmtAttr**.<br /><br /> Die *Vorgang* Argument war SQL_UPDATE auf SQL_DELETE oder SQL_REFRESH und die Zeile durch identifiziert die *RowNumber* Argument wurde gelöscht haben oder hatten, wurden nicht abgerufen.<br /><br /> (DM) die *RowNumber* Argument wurde 0 (null) und die *Vorgang* Argument war SQL_POSITION.<br /><br /> **SQLSetPos** wurde aufgerufen, nachdem **SQLBulkOperations** aufgerufen wurde und bevor **SQLFetchScroll** oder **SQLFetch** aufgerufen wurde.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Treiber oder die Datenquelle unterstützt nicht den in der angeforderte Vorgang die *Vorgang* Argument oder die *LockType* Argument.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr** mit einer *Attribut* von SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
  
> [!CAUTION]
>  Für Informationen über die Anweisung gibt an, die **SQLSetPos** in aufgerufen werden kann und was sie muss für die Kompatibilität mit ODBC 2.*.x* -Anwendungen finden Sie unter [Blockcursor, scrollbare Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md).  
  
## <a name="rownumber-argument"></a>RowNumber-Argument  
 Die *RowNumber* Argument gibt die Anzahl der Zeile im Rowset für das Ausführen des Vorgangs gemäß den *Vorgang* Argument. Wenn *RowNumber* gleich 0 ist, der Vorgang gilt für jede Zeile im Rowset. *RowNumber* muss ein Wert zwischen 0 und die Anzahl der Zeilen im Rowset.  
  
> [!NOTE]  
>  In der Programmiersprache C-Arrays sind 0-basiert und die *RowNumber* Argument ist 1-basiert. Z. B. um die fünfte Zeile des Rowsets zu aktualisieren, eine Anwendung ändert die Rowset-Puffer Arrayindex 4 gibt jedoch eine *RowNumber* 5.  
  
 Alle Vorgänge positionieren Sie den Cursor in der Zeile, die anhand des *RowNumber*. Die folgenden Vorgänge erfordern die Cursorposition:  
  
-   Positioniert Update und delete-Anweisungen.  
  
-   Aufrufe von **SQLGetData**.  
  
-   Aufrufe von **SQLSetPos** mit den Optionen SQL_DELETE SQL_REFRESH und SQL_UPDATE auf.  
  
 Z. B. wenn *RowNumber* ist 2 für einen Aufruf von **SQLSetPos** mit einer *Vorgang* von SQL_DELETE, befindet sich des Cursors in der zweiten Zeile des Rowsets und die Zeile gelöscht wird. Der Eintrag in der Implementierung zeilenstatusarray (verweist das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR) für die zweite Zeile wird in SQL_ROW_DELETED geändert.  
  
 Einer Anwendung angegeben beim Aufrufen eine Cursorposition **SQLSetPos**. In der Regel ruft **SQLSetPos** mit dem Vorgang SQL_POSITION oder SQL_REFRESH zur Positionierung des Cursors vor dem Ausführen einer positionierten aktualisieren oder delete-Anweisung oder Aufrufen **SQLGetData**.  
  
## <a name="operation-argument"></a>Vorgangsargument  
 Die *Vorgang* Argument unterstützt die folgenden Vorgänge. Um zu bestimmen, welche Optionen, die von einer Datenquelle unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit der SQL_DYNAMIC_CURSOR_ATTRIBUTES1 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_ CURSOR_ATTRIBUTES1 Informationstyp (je nach Art des Cursors).  
  
|*Vorgang*<br /><br /> Argument|Vorgang|  
|------------------------------|---------------|  
|SQL_POSITION|Der Treiber setzt den Cursor in der Zeile, angegeben *RowNumber*.<br /><br /> Der Inhalt der zeilenstatusarray verweist das Anweisungsattribut SQL_ATTR_ROW_OPERATION_PTR für die SQL_POSITION ignoriert *Vorgang*.|  
|SQL_REFRESH|Der Treiber setzt den Cursor in der Zeile, angegeben *RowNumber* und aktualisiert Daten in die Rowset-Puffer für Zeile. Weitere Informationen dazu, wie der Treiber die Daten in den Puffern Rowset zurückgibt, finden Sie unter den Beschreibungen der, spaltenweise und zeilenweise Bindung in **SQLBindCol**.<br /><br /> **SQLSetPos** mit einer *Vorgang* von SQL_REFRESH aktualisiert den Status und die Inhalte der Zeilen innerhalb des aktuellen abgerufenen Rowsets. Dies schließt die Lesezeichen aktualisieren. Da die Daten in den Puffern werden aktualisiert, aber nicht erneut abgerufen, ist die Mitgliedschaft des Rowsets fest. Dies unterscheidet sich von der Aktualisierung durchgeführt, die durch einen Aufruf von **SQLFetchScroll** mit einer *FetchOrientation* von SQL_FETCH_RELATIVE und *' RowNumber '* gleich 0 (null) und refetches Das Rowset aus dem Resultset, damit sie zusätzliche Daten anzeigen und entfernen kann gelöschte Daten auf, wenn diese Vorgänge von der Treiber und der Cursor unterstützt werden.<br /><br /> Eine erfolgreiche Aktualisierung mit **SQLSetPos** ändert sich nicht auf die Zeilenstatus SQL_ROW_DELETED. Gelöschte Zeilen im Rowset werden fortgesetzt, bis zum nächsten Abrufvorgang gelöscht zu markieren. Die Zeilen werden an den nächsten Abrufvorgang ausgeblendet, wenn der Cursor Packen von Metriken unterstützt (in der eine nachfolgende **SQLFetch** oder **SQLFetchScroll** gelöschte Zeilen wird nicht zurückgegeben).<br /><br /> Hinzugefügt von Zeilen werden nicht angezeigt, wenn eine Aktualisierung mit **SQLSetPos** erfolgt. Dieses Verhalten unterscheidet sich von **SQLFetchScroll** mit einem *FetchType* von SQL_FETCH_RELATIVE und *' RowNumber '* gleich 0 (null) und das aktuelle Rowset jedoch auch aktualisiert Zeigen Sie hinzugefügte Datensätze an, oder Packen Sie gelöschte Datensätze aus, wenn diese Vorgänge vom Cursor unterstützt werden.<br /><br /> Eine erfolgreiche Aktualisierung mit **SQLSetPos** wird nun einen Zeilenstatus SQL_ROW_ADDED SQL_ROW_SUCCESS (sofern die zeilenstatusarray vorhanden ist).<br /><br /> Eine erfolgreiche Aktualisierung mit **SQLSetPos** wird nun Zeilenstatus SQL_ROW_UPDATED neuen Status der Zeile (sofern die zeilenstatusarray vorhanden ist).<br /><br /> Im Falle ein Fehlers eine **SQLSetPos** Vorgang für eine Zeile den Zeilenstatus nastaven NA hodnotu SQL_ROW_ERROR (sofern die zeilenstatusarray vorhanden ist).<br /><br /> Für einen Cursor geöffnet, mit einem SQL_ATTR_CONCURRENCY-Anweisungsattribut SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES, eine Aktualisierung mit **SQLSetPos** möglicherweise aktualisieren Sie die vollständige Parallelität-Werte, die von der Datenquelle verwendet wird, um zu ermitteln, die Zeile wurde geändert. In diesem Fall werden die Zeilenversionen oder Werte, die verwendet werden, um sicherzustellen, dass Cursorparallelität aktualisiert, sobald die Rowset-Puffer vom Server aktualisiert werden. Dies tritt auf, für jede Zeile, die aktualisiert werden.<br /><br /> Der Inhalt der zeilenstatusarray verweist das Anweisungsattribut SQL_ATTR_ROW_OPERATION_PTR für die SQL_REFRESH ignoriert *Vorgang*.|  
|SQL_UPDATE|Der Treiber setzt den Cursor in der Zeile, angegeben *' RowNumber '* und aktualisiert die zugrunde liegenden Zeile der Daten mit den Werten in den Rowset Puffern (die *TargetValuePtr* -Argument in  **SQLBindCol**). Ruft die Länge der Daten aus den Längenindikator/Puffern ab (der *StrLen_or_IndPtr* -Argument in **SQLBindCol**). Wenn die Länge einer beliebigen Spalte SQL_COLUMN_IGNORE ist, wird die Spalte nicht aktualisiert werden. Nach dem Aktualisieren der zeilenupdates, ändert der Treiber das entsprechende Element von der zeilenstatusarray SQL_ROW_UPDATED oder SQL_ROW_SUCCESS_WITH_INFO an (sofern die zeilenstatusarray vorhanden ist).<br /><br /> Es wird von der Treiber definiert das Verhalten Wenn **SQLSetPos** mit einer *Vorgang* SQL_UPDATE Argument für einen Cursor, enthält doppelte Spalten, aufgerufen wird. Der Treiber kann ein SQLSTATE treiberdefinierten zurückgeben, können aktualisieren Sie die erste Spalte, die im Resultset angezeigt wird oder andere Treiber definierten Verhalten führen.<br /><br /> Die Zeile Operation-Array verweist das Anweisungsattribut SQL_ATTR_ROW_OPERATION_PTR kann verwendet werden, um anzugeben, dass eine Zeile im aktuellen Rowset während eines Massenupdates ignoriert werden sollen. Weitere Informationen finden Sie unter "Status und Vorgang Arrays" weiter unten in dieser Funktionsverweis.|  
|SQL_DELETE|Der Treiber setzt den Cursor in der Zeile, angegeben *RowNumber* und löscht die zugrunde liegenden Zeile der Daten. Das entsprechende Element des Arrays Zeile Status SQL_ROW_DELETED geändert. Nachdem die Zeile gelöscht wurde, sind die folgenden nicht gültig für die Zeile: positioniert Update und delete-Anweisungen, Aufrufe von **SQLGetData**, und Aufrufe von **SQLSetPos** mit *Vorgang* außer SQL_POSITION festgelegt. Für die Treiber, die Komprimierung zu unterstützen, wird die Zeile aus dem Cursor gelöscht, wenn neue Daten aus der Datenquelle abgerufen werden.<br /><br /> Gibt an, ob die Zeile sichtbar bleibt, hängt von der Cursortyp. Beispielsweise sind die gelöschte Zeilen für statische und keysetgesteuerte Cursor sichtbar, sind jedoch für dynamische Cursor nicht sichtbar.<br /><br /> Die Zeile Operation-Array verweist das Anweisungsattribut SQL_ATTR_ROW_OPERATION_PTR kann verwendet werden, um anzugeben, dass eine Zeile im aktuellen Rowset bei einer massenlöschung ignoriert werden sollen. Weitere Informationen finden Sie unter "Status und Vorgang Arrays" weiter unten in dieser Funktionsverweis.|  
  
## <a name="locktype-argument"></a>LockType-Argument  
 Die *LockType* Argument bietet eine Möglichkeit für Anwendungen, um Parallelität zu steuern. In den meisten Fällen unterstützt Datenquellen, die Parallelitätsebenen und Transaktionen unterstützen nur den SQL_LOCK_NO_CHANGE-Wert, der die *LockType* Argument. Die *LockType* Argument wird in der Regel nur für die Unterstützung dateibasierter verwendet.  
  
 Die *LockType* Argument gibt an, der Zustand der Zeile nach der Sperre **SQLSetPos** ausgeführt wurde. Wenn der Treiber konnte nicht gesperrt werden die Zeile, die zum Ausführen des angeforderten Vorgangs oder zum Erfüllen der *LockType* Argument gibt SQL_ERROR zurück, und SQLSTATE 42000 (Syntaxfehler oder zugriffsverletzung).  
  
 Obwohl die *LockType* Argument für eine einzelne Anweisung angegeben ist, wird die Sperre berechtigt, die gleichen Berechtigungen für alle Anweisungen für die Verbindung. Insbesondere kann eine Sperre, die von einer Anweisung für eine Verbindung abgerufen wurde mit einer anderen Anweisung für dieselbe Verbindung aufgehoben werden.  
  
 Eine Zeile gesperrt durch **SQLSetPos** bleibt gesperrt, bis die Anwendung ruft **SQLSetPos** für die Zeile mit *LockType* SQL_LOCK_UNLOCK, oder bis die Anwendung festgelegt Aufrufe **SQLFreeHandle** für die Anweisung oder **SQLFreeStmt** mit der Option SQL_CLOSE. Für einen Treiber, die Transaktionen unterstützt, eine Zeile gesperrt, bis **SQLSetPos** entsperrt wird, wenn die Anwendung ruft **SQLEndTran** , einen commit oder Rollback einer Transaktions für die Verbindung (falls ein Cursor geschlossen wird Wenn eine Transaktion wird ein Commit oder Rollback, wie durch die Informationstypen SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR zurückgegebenes **SQLGetInfo**).  
  
 Die *LockType* Argument unterstützt die folgenden Typen von Sperren. Um zu bestimmen, welche Sperren, die von einer Datenquelle unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit der SQL_DYNAMIC_CURSOR_ATTRIBUTES1 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_ CURSOR_ATTRIBUTES1 Informationstyp (je nach Art des Cursors).  
  
|*LockType* Argument|Sperrentyp|  
|-------------------------|---------------|  
|SQL_LOCK_NO_CHANGE|Die Treiber oder die Datenquelle wird sichergestellt, dass die Zeile in der gleichen gesperrt oder entsperrt Zustand wie vor **SQLSetPos** aufgerufen wurde. Dieser Wert *LockType* können Datenquellen, die kein explizites Sperren auf Zeilenebene alle Sperren erforderlich ist, durch Verwendung der aktuellen parallelitätseinstellung Isolationsstufen unterstützen.|  
|SQL_LOCK_EXCLUSIVE|Die Treiber oder die Datenquelle wird ausschließlich die Zeile gesperrt. Eine Anweisung auf eine andere Verbindung oder in einer anderen Anwendung kann nicht zum Abrufen der Sperren in der Zeile verwendet werden.|  
|SQL_LOCK_UNLOCK|Die Treiber oder die Datenquelle wird die Zeile entsperrt.|  
  
 Wenn ein Treiber SQL_LOCK_EXCLUSIVE unterstützt allerdings keine SQL_LOCK_UNLOCK, bleibt eine Zeile, die gesperrt wird gesperrt, bis zum Auftreten eines der Funktionsaufrufe im vorherigen Absatz beschrieben.  
  
 Wenn ein Treiber SQL_LOCK_EXCLUSIVE unterstützt allerdings keine SQL_LOCK_UNLOCK, eine Zeile, die gesperrt wird bleibt gesperrt bis die Anwendung ruft **SQLFreeHandle** für die Anweisung oder **SQLFreeStmt** mit die SQL_CLOSE-Option. Wenn der Treiber Transaktionen unterstützt, und schließt den Cursor beim Commit oder Rollback der Transaktion, die Anwendung ruft **SQLEndTran**.  
  
 Für die Update- und Delete-Vorgänge im **SQLSetPos**, die Anwendung verwendet die *LockType* Argument wie folgt:  
  
-   Um zu gewährleisten, dass eine Zeile nicht ändert, nachdem sie abgerufen wurden, eine Anwendung ruft **SQLSetPos** mit *Vorgang* SQL_REFRESH festgelegt und *LockType* SQL_LOCK_ festgelegt EXKLUSIVE.  
  
-   Wenn die Anwendung setzt *LockType* zu SQL_LOCK_NO_CHANGE, der Treiber wird sichergestellt, dass ein Update oder Delete-Vorgang erfolgreich ist, nur, wenn die Anwendung SQL_CONCUR_LOCK für das SQL_ATTR_CONCURRENCY-Anweisungsattribut angegeben.  
  
-   Wenn die Anwendung für das SQL_ATTR_CONCURRENCY-Anweisungsattribut SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES angegeben ist, wird der Treiber vergleicht Zeilenversionen oder Werte und den Vorgang wird abgelehnt, wenn die Zeile geändert hat, da die Anwendung die Zeile abgerufen.  
  
-   Wenn die Anwendung für das SQL_ATTR_CONCURRENCY-Anweisungsattribut SQL_CONCUR_READ_ONLY angegeben ist, wird der Treiber ein Update abgelehnt oder Löschvorgang.  
  
 Weitere Informationen zu den SQL_ATTR_CONCURRENCY-Anweisungsattribut, finden Sie unter [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="status-and-operation-arrays"></a>Status und die Vorgang-Arrays  
 Die folgenden Arrays von Status und der Vorgang wird beim Aufrufen von **SQLSetPos**:  
  
-   Die zeilenstatusarray (wie mit dem SQL_DESC_ARRAY_STATUS_PTR-Feld in IRD und das Anweisungsattribut SQL_ATTR_ROW_STATUS_ARRAY gezeigt) enthält die Status-Werte für jede Zeile der Daten im Rowset. Der Treiber setzt die Status-Werte in diesem Array nach einem Aufruf von **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, oder **SQLSetPos** . Dieses Array wird durch das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR verwiesen.  
  
-   Die Zeile Operation-Array (wie mit dem SQL_DESC_ARRAY_STATUS_PTR-Feld in der ARD und das Anweisungsattribut SQL_ATTR_ROW_OPERATION_ARRAY gezeigt) enthält einen Wert für jede Zeile im Rowset, der angibt, ob ein Aufruf zum **SQLSetPos**für ein Massenvorgang ignoriert oder ausgeführt wird. Jedes Element im Array ist auf SQL_ROW_PROCEED (Standard) oder SQL_ROW_IGNORE festgelegt. Dieses Array wird durch das Anweisungsattribut SQL_ATTR_ROW_OPERATION_PTR verwiesen.  
  
 Die Anzahl der Elemente in den Status und den Betrieb Arrays muss es sich um die Anzahl der Zeilen im Rowset (gemäß dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut-Anweisung) gleich.  
  
 Weitere Informationen zu den zeilenstatusarray, finden Sie unter [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md). Informationen zu der Zeile Operation-Array finden Sie unter "Wird ignoriert, eine Zeile in einer Massenvorgänge" weiter unten in diesem Abschnitt.  
  
## <a name="using-sqlsetpos"></a>Verwenden von SQLSetPos  
 Bevor eine Anwendung ruft **SQLSetPos**, müssen sie die folgende Schrittfolge ausführen:  
  
1.  Wenn die Anwendung aufruft **SQLSetPos** mit *Vorgang* SQL_UPDATE, Aufruf festgelegt **SQLBindCol** (oder **SQLSetDescRec**) für die einzelnen die Spalte geben seinen Datentyp und die Puffer für die Daten und die Länge der Spaltenwerts zu binden.  
  
2.  Wenn die Anwendung aufruft **SQLSetPos** mit *Vorgang* auf SQL_DELETE oder SQL_UPDATE, Aufruf festgelegt **SQLColAttribute** sicherstellen, dass die Spalten aus, die gelöscht oder aktualisiert werden können aktualisiert werden.  
  
3.  Rufen Sie **SQLExecDirect**, **SQLExecute**, oder einer Katalogfunktion, um ein Resultset zu erstellen.  
  
4.  Rufen Sie **SQLFetch** oder **SQLFetchScroll** zum Abrufen der Daten.  
  
 Weitere Informationen zur Verwendung von **SQLSetPos**, finden Sie unter [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
## <a name="deleting-data-using-sqlsetpos"></a>Löschen von Daten mit SQLSetPos  
 Zum Löschen von Daten mit **SQLSetPos**, eine Anwendung ruft **SQLSetPos** mit *RowNumber* auf die Anzahl der Zeilen festgelegt, um das Löschen und *Vorgang*auf SQL_DELETE festgelegt.  
  
 Nachdem die Daten gelöscht wurden, ändert der Treiber den Wert in der Implementierung zeilenstatusarray für die entsprechende Zeile in SQL_ROW_DELETED (oder SQL_ROW_ERROR) an.  
  
## <a name="updating-data-using-sqlsetpos"></a>Aktualisieren von Daten mit SQLSetPos  
 Eine Anwendung kann übergeben Sie den Wert für eine Spalte im Puffer an Sie gebundenen Daten oder durch eine oder mehrere Aufrufe **SQLPutData**. Spalten, deren Daten mit übergeben werden **SQLPutData** genannt werden *Data-at-Execution-* *Spalten*. Diese werden häufig zum Senden von Daten für Spalten SQL_LONGVARBINARY und SQL_LONGVARCHAR verwendet und können mit anderen Spalten kombiniert werden.  
  
#### <a name="to-update-data-with-sqlsetpos-an-application"></a>Um Daten mit SQLSetPos, eine Anwendung zu aktualisieren:  
  
1.  Stellen Werte in den Daten und Längenindikator/Puffern mit gebundenen **SQLBindCol**:  
  
    -   Für das normale Verhalten von Spalten, die Anwendung platziert den Wert der neuen Spalte in der  *\*TargetValuePtr* Puffer und die Länge des Werts in der  *\*StrLen_or_IndPtr* Puffer. Wenn die Zeile nicht aktualisiert werden soll, wird die Anwendung SQL_ROW_IGNORE in dieser Zeile-Element des Arrays Vorgang Zeile.  
  
    -   Für Data-at-Execution-Spalten wird die Anwendung einen anwendungsdefinierten Wert, z. B. die Nummer der Spalte, in der  *\*TargetValuePtr* Puffer. Der Wert kann später verwendet werden, um die Spalte identifizieren.  
  
         Die Anwendung platziert, das Ergebnis der SQL_LEN_DATA_AT_EXEC (*Länge*)-Makro in der **StrLen_or_IndPtr* Puffer. Wenn der SQL-Datentyp der Spalte SQL_LONGVARBINARY, SQL_LONGVARCHAR oder einem long-Datentyp datenquellenspezifische Daten und "Y" für den Typ der SQL_NEED_LONG_DATA_LEN Informationen in der Treiber gibt **SQLGetInfo**, *Länge*  ist die Anzahl der Datenbytes, die für den Parameter; gesendet werden andernfalls muss ein Wert nicht negativ sein und wird ignoriert.  
  
2.  Aufrufe **SQLSetPos** mit der *Vorgang* Argument, die auf SQL_UPDATE auf festgelegt ist, um die Zeile der Daten zu aktualisieren.  
  
    -   Wenn keine Data-at-Execution-Spalten vorhanden sind, ist der Prozess abgeschlossen.  
  
    -   Wenn alle Data-at-Execution-Spalten vorhanden sind, wird die Funktion wird SQL_NEED_DATA zurückgegeben, und fährt Sie fort mit Schritt 3 fort.  
  
3.  Aufrufe **SQLParamData** zum Abrufen der Adresse der  *\*TargetValuePtr* Puffer für die erste Data-at-Execution-Spalte, die verarbeitet werden. **SQLParamData** wird SQL_NEED_DATA zurückgegeben. Die Anwendung ruft den Anwendung definierte Wert aus der  *\*TargetValuePtr* Puffer.  
  
    > [!NOTE]  
    >  Obwohl Data-at-Execution-Parametern mit Data-at-Execution-Spalten vergleichbar sind, wird der Wert von zurückgegeben **SQLParamData** ist unterschiedlich.  
  
    > [!NOTE]  
    >  Data-at-Execution-Parameter sind die Parameter in einer SQL-Anweisung, die für die Daten gesendet werden mit **SQLPutData** Wenn die Anweisung ausgeführt wird, mit **SQLExecDirect** oder **SQLExecute**. Sie sind mit gebunden **SQLBindParameter** oder durch Festlegen von sicherheitsbeschreibungen mit **SQLSetDescRec**. Der Rückgabewert von **SQLParamData** ist eine 32-Bit-Wert, der an übergebene **SQLBindParameter** in die *ParameterValuePtr* Argument.  
  
    > [!NOTE]  
    >  Data-at-Execution-Spalten in einem Rowset, für die Daten mit gesendet werden, sind **SQLPutData** beim Aktualisieren einer Zeile mit **SQLSetPos**. Sie sind mit gebunden **SQLBindCol**. Der Rückgabewert von **SQLParamData** ist die Adresse der Zeile in der **TargetValuePtr* Puffer, der verarbeitet wird.  
  
4.  Aufrufe **SQLPutData** einmal oder mehrmals, um Daten für die Spalte zu senden. Mehrere ist erforderlich, wenn alle Datenwerte in zurückgegeben werden, können die  *\*TargetValuePtr* im angegebenen Puffer **SQLPutData**; mehrere Aufrufe **SQLPutData** für dieselbe Spalte dürfen nur beim Senden von Zeichendaten C an eine Spalte mit einem Zeichen oder den binären datenquellenspezifische Datentyp oder beim Senden von Binärdaten C an eine Spalte mit einem Zeichen, binär, oder geben Sie die spezifischen Daten.  
  
5.  Aufrufe **SQLParamData** erneut aus, um zu signalisieren, dass alle Daten für die Spalte gesendet wurde.  
  
    -   Wenn es weitere Data-at-Execution-Spalten, **SQLParamData** gibt SQL_NEED_DATA sowie die Adresse des der *TargetValuePtr* Puffer für die nächste Data-at-Execution-Spalte, die verarbeitet werden. Die Anwendung wiederholt die Schritte 4 und 5.  
  
    -   Wenn keine weiteren Data-at-Execution-Spalten vorhanden sind, ist der Prozess abgeschlossen. Wenn die Anweisung erfolgreich ausgeführt wurde **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO; Fehler bei der Ausführung gibt, wird SQL_ERROR zurückgegeben. An diesem Punkt **SQLParamData** können alle SQLSTATE, der zurückgegeben werden kann zurückgeben **SQLSetPos**.  
  
 Wenn Daten aktualisiert wurde, ändert der Treiber den Wert in der Implementierung zeilenstatusarray für die entsprechende Zeile in SQL_ROW_UPDATED an.  
  
 Wenn der Vorgang abgebrochen wird oder ein Fehler, in auftritt **SQLParamData** oder **SQLPutData**nach **SQLSetPos** wird SQL_NEED_DATA zurückgegeben und vor dem Senden von Daten für alle Data-at-Execution-Spalten, die Anwendung kann aufrufen nur **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions** , **SQLParamData**, oder **SQLPutData** für die Anweisung oder die Verbindung mit der Anweisung verknüpft ist. Wenn sie für die Anweisung oder die Verbindung mit der Anweisung verknüpfte jede andere Funktion aufruft, gibt die Funktion SQL_ERROR zurück, und SQLSTATE HY010 (Sequenzfehler funktionieren).  
  
 Wenn die Anwendung ruft **SQLCancel** während der Treiber noch Daten für die Data-at-Execution-Spalten benötigt, bricht der Treiber den Vorgang ab. Die Anwendung kann dann aufrufen **SQLSetPos** erneut Abbrechen wirkt sich nicht den Cursorstatus oder der aktuellen Cursorposition.  
  
 Wenn die SELECT-Liste der Query-Spezifikation, die dem Cursor zugeordnet mehr als einen Verweis auf die gleiche Spalte enthält, ob ein Fehler generiert wird, oder der Treiber ignoriert die doppelt vorhandenen Verweise und führt die angeforderten Vorgänge wird-Treiber definiert werden.  
  
## <a name="performing-bulk-operations"></a>Massenvorgänge  
 Wenn die *RowNumber* -Argument 0 ist, die der Treiber führt den Vorgang angegeben wird, der *Vorgang* Argument für jede Zeile im Rowset, das in dem Feld in der Zeile Vorgang einen Wert von SQL_ROW_PROCEED enthält Array auf SQL_ATTR_ROW_OPERATION_PTR-Anweisungsattribut zeigt. Dies ist ein gültiger Wert von der *RowNumber* Argument für eine *Vorgang* Argument SQL_DELETE, SQL_REFRESH, oder SQL_UPDATE, jedoch nicht SQL_POSITION. **SQLSetPos** mit einer *Vorgang* von SQL_POSITION und *RowNumber* SQLSTATE HY109 gleich 0 zurück (ungültige Cursorposition).  
  
 Wenn ein Fehler auftritt, bezieht sich auf das gesamte Rowset, z. B. SQLSTATE HYT00 (Timeout ist abgelaufen), gibt der Treiber SQL_ERROR zurück, und dem entsprechenden SQLSTATE. Der Inhalt der Rowset-Puffer ist nicht definiert, und die Cursorposition bleibt unverändert.  
  
 Wenn ein Fehler auftritt, bezieht sich auf eine einzelne Zeile den Treiber ein:  
  
-   Legt das Element für die Zeile in der zeilenstatusarray verweist das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut, SQL_ROW_ERROR fest.  
  
-   Stellt eine oder mehrere zusätzliche SQLSTATEs für den Fehler in der Fehlerwarteschlange und legt das SQL_DIAG_ROW_NUMBER-Feld in der Struktur der Diagnosedaten.  
  
 Nachdem sie den Fehler oder die Warnung verarbeitet, wenn der Treiber den Vorgang für die verbleibenden Zeilen im Rowset abgeschlossen wird, wird SQL_SUCCESS_WITH_INFO zurückgegeben. Daher wird für jede Zeile, die einen Fehler zurückgegeben, die Fehlerwarteschlange NULL oder mehr zusätzliche SQLSTATEs enthält. Wenn der Treiber den Vorgang beendet, nachdem sie den Fehler oder Warnung verarbeitet wurde, wird SQL_ERROR zurückgegeben.  
  
 Wenn der Treiber alle Warnungen, z. B. SQLSTATE 01004 (Daten wurden abgeschnitten) zurückgibt, wird der Warnungen, die auf das gesamte Rowset oder unbekannte Zeilen im Rowset anwenden, bevor sie die Fehlerinformationen zurückgibt, die für bestimmte Zeilen gilt. Es gibt Warnungen für bestimmte Zeilen sowie andere Fehlerinformationen über die Zeilen zurück.  
  
 Wenn *RowNumber* ist gleich 0 und *Vorgang* ist SQL_UPDATE, SQL_REFRESH oder SQL_DELETE, die Anzahl von Zeilen, die **SQLSetPos** arbeitet auf verweist das SQL_ATTR_ROWS _FETCHED_PTR-Anweisungsattribut.  
  
 Wenn *RowNumber* ist gleich 0 und *Vorgang* ist SQL_DELETE, SQL_REFRESH oder SQL_UPDATE auf, die aktuelle Zeile aus, nachdem der Vorgang der aktuellen Zeile vor dem Vorgang identisch ist.  
  
## <a name="ignoring-a-row-in-a-bulk-operation"></a>Eine Zeile in einem Massenvorgang wird ignoriert.  
 Die Zeile Operation-Array kann verwendet werden, um anzugeben, dass eine Zeile im aktuellen Rowset sollen, während ein Vorgang mithilfe ignoriert werden **SQLSetPos**. Damit den Treiber, um eine oder mehrere Zeilen zu ignorieren, während eines Massenvorgangs durchführt, sollte eine Anwendung die folgenden Schritte ausführen:  
  
1.  Rufen Sie **SQLSetStmtAttr** beim Festlegen des Attributs SQL_ATTR_ROW_OPERATION_PTR-Anweisung, um auf ein Array von SQLUSMALLINTs zu verweisen. Dieses Feld kann auch festgelegt werden, durch den Aufruf **SQLSetDescField** das Headerfeld SQL_DESC_ARRAY_STATUS_PTR der ARD festlegen, die erfordert, dass eine Anwendung die Deskriptorhandles erhält.  
  
2.  Legen Sie jedes Element des Arrays Vorgang Zeile auf einen von zwei Werten:  
  
    -   SQL_ROW_IGNORE, um anzugeben, dass die Zeile für Massenvorgänge ausgeschlossen ist.  
  
    -   SQL_ROW_PROCEED, um anzugeben, dass die Zeile in den Massenvorgang enthalten ist. (Dies ist der Standardwert.)  
  
3.  Rufen Sie **SQLSetPos** Massenvorgangs ausführen.  
  
 Die folgenden Regeln gelten für die Zeile Operation-Array:  
  
-   SQL_ROW_IGNORE und SQL_ROW_PROCEED beeinflussen nur mithilfe von Massenvorgängen **SQLSetPos** mit einer *Vorgang* SQL_DELETE oder SQL_UPDATE auf. Sie haben keine Auswirkungen, Aufrufe von **SQLSetPos** mit einer *Vorgang* SQL_REFRESH oder SQL_POSITION.  
  
-   Der Zeiger wird festgelegt. standardmäßig auf null.  
  
-   Wenn der Zeiger null ist, werden alle Zeilen aktualisiert, als ob alle Elemente auf SQL_ROW_PROCEED festgelegt wurden.  
  
-   Festlegen eines Elements auf SQL_ROW_PROCEED garantiert nicht, dass der Vorgang in einer bestimmten Zeile stattfindet. Z. B. wenn eine bestimmte Zeile im Rowset den Status SQL_ROW_ERROR verfügt, der Treiber möglicherweise nicht zum Aktualisieren dieser Zeile unabhängig davon, ob die Anwendung SQL_ROW_PROCEED angegeben. Eine Anwendung muss überprüfen Sie immer die zeilenstatusarray, um festzustellen, ob der Vorgang erfolgreich war.  
  
-   SQL_ROW_PROCEED ist als 0 in der Headerdatei definiert. Eine Anwendung kann die Zeile Operation-Array auf 0 initialisieren, um alle Zeilen zu verarbeiten.  
  
-   Wenn Element Anzahl "n" in der Zeile Operation-Array SQL_ROW_IGNORE festgelegt ist und **SQLSetPos** wird aufgerufen, um das Ausführen eines Massenupdates oder Löschvorgang, der n-te Zeile in das Rowset bleibt unverändert, nach dem Aufruf von **SQLSetPos**.  
  
-   Eine Anwendung sollte automatisch eine schreibgeschützte Spalte auf SQL_ROW_IGNORE festgelegt.  
  
## <a name="ignoring-a-column-in-a-bulk-operation"></a>Eine Spalte in einem Massenvorgang wird ignoriert.  
 Um unnötige Verarbeitungsvorgänge Diagnose von versuchten Updates für eine oder mehrere schreibgeschützte Spalten generiert zu vermeiden, kann eine Anwendung den Wert in die gebundenen Längen-/Indikatorpuffers auf SQL_COLUMN_IGNORE festlegen. Weitere Informationen finden Sie unter [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel kann eine Anwendung einen Benutzer, die ORDERS-Tabelle durchsuchen und Aktualisieren des Auftragsstatus. Der Cursor wird mit einer Rowsetgröße von 20 keysetgesteuerte und Steuerung für optimistische Parallelität Vergleichen von Zeilenversionen verwendet. Nachdem jedes Rowset abgerufen wird, wird die Anwendung gibt es, und ermöglicht dem Benutzer, wählen Sie aus, und aktualisieren Sie den Status einer Bestellung. Die Anwendung verwendet **SQLSetPos** zur Positionierung des Cursors auf die ausgewählte Zeile und führt ein positioniertes Update der Zeile. (Die Fehlerbehandlung wird aus Gründen der Übersichtlichkeit weggelassen.)  
  
```cpp  
#define ROWS 20  
#define STATUS_LEN 6  
  
SQLCHAR        szStatus[ROWS][STATUS_LEN], szReply[3];  
SQLINTEGER     cbStatus[ROWS], cbOrderID;  
SQLUSMALLINT   rgfRowStatus[ROWS];  
SQLUINTEGER    sOrderID, crow = ROWS, irow;  
SQLHSTMT       hstmtS, hstmtU;  
  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CONCURRENCY, (SQLPOINTER) SQL_CONCUR_ROWVER, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER) SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_STATUS_PTR, (SQLPOINTER) rgfRowStatus, 0);  
SQLSetCursorName(hstmtS, "C1", SQL_NTS);  
SQLExecDirect(hstmtS, "SELECT ORDERID, STATUS FROM ORDERS ", SQL_NTS);  
  
SQLBindCol(hstmtS, 1, SQL_C_ULONG, &sOrderID, 0, &cbOrderID);  
SQLBindCol(hstmtS, 2, SQL_C_CHAR, szStatus, STATUS_LEN, &cbStatus);  
  
while ((retcode == SQLFetchScroll(hstmtS, SQL_FETCH_NEXT, 0)) != SQL_ERROR) {  
   if (retcode == SQL_NO_DATA_FOUND)  
      break;  
   for (irow = 0; irow < crow; irow++) {  
      if (rgfRowStatus[irow] != SQL_ROW_DELETED)  
         printf("%2d %5d %*s\n", irow+1, sOrderID, NAME_LEN-1, szStatus[irow]);  
   }  
   while (TRUE) {  
      printf("\nRow number to update?");  
      gets_s(szReply, 3);  
      irow = atoi(szReply);  
      if (irow > 0 && irow <= crow) {  
         printf("\nNew status?");  
         gets_s(szStatus[irow-1], (ROWS * STATUS_LEN));  
         SQLSetPos(hstmtS, irow, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
         SQLPrepare(hstmtU,  
          "UPDATE ORDERS SET STATUS=? WHERE CURRENT OF C1", SQL_NTS);  
         SQLBindParameter(hstmtU, 1, SQL_PARAM_INPUT,  
            SQL_C_CHAR, SQL_CHAR,  
            STATUS_LEN, 0, szStatus[irow], 0, NULL);  
         SQLExecute(hstmtU);  
      } else if (irow == 0) {  
         break;  
      }  
   }  
}  
```  
  
 Weitere Beispiele finden Sie unter [positioniert Update- und Delete-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) und [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ausführen von Massenvorgängen, die nicht auf die Position des Blocks beziehen|[SQLBulkOperations-Funktion](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen eines einzelnen Felds einen Deskriptor|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Abrufen von mehreren Feldern einen Deskriptor|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen Felds einen Deskriptor|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen von mehreren Feldern einen Deskriptor|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Wenn eine Anweisungsattribut|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
