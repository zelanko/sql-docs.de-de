---
title: SQLGetTypeInfo-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetTypeInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTypeInfo
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC]
ms.assetid: bdedb044-8924-4ca4-85f3-8b37578e0257
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1c597cd4ca51ca578ca90c4e95db584dec4bcd6d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030587"
---
# <a name="sqlgettypeinfo-function"></a>SQLGetTypeInfo-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetTypeInfo** gibt Informationen zu Datentypen, die von der Datenquelle unterstützt. Der Treiber zurückgegeben die Informationen in Form von einer SQL-Resultset. Die Datentypen sind für die Verwendung in-Anweisungen (Data Definition Language, Datendefinitionssprache) vorgesehen.  
  
> [!IMPORTANT]  
>  Anwendungen müssen die in der Spalte TYPE_NAME des zurückgegebenen Typnamen verwenden die **SQLGetTypeInfo** Resultset **ALTER TABLE** und **CREATE TABLE** Anweisungen. **SQLGetTypeInfo** möglicherweise mehr als eine Zeile mit dem gleichen Wert zurück, in der DATA_TYPE-Spalte.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetTypeInfo(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   DataType);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle für das Resultset.  
  
 *DataType*  
 [Eingabe] Der SQL-Datentyp. Dies muss einer der Werte in der [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) Abschnitt Anhang D: Datentypen, oder einen Treiber-spezifische SQL-Datentyp. SQL_ALL_TYPES gibt an, dass Informationen zu allen Datentypen zurückgegeben werden sollen.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetTypeInfo** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* SQL _HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLGetTypeInfo** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Ein Attribut für die angegebene Anweisung ist ungültig aufgrund der Implementierung Arbeitsbedingungen, also ein ähnlichen Wert vorübergehend ersetzt wurde. (Rufen **SQLGetStmtAttr** vorübergehend ersetzten Werts bestimmt.) Der Ersatzwert ist gültig für die *StatementHandle* bis der Cursor geschlossen wird. Die Anweisungsattribute, die geändert werden können, sind: SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT und SQL_ATTR_SIMULATE_CURSOR. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle,* und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Resultset war geöffnet, auf die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY004|Ungültiger SQL-Datentyp|Der angegebene Wert für das Argument *DataType* war weder eine gültige ODBC-SQL-Datentypbezeichner noch eine treiberspezifische Typ-ID, die vom Treiber unterstützt werden.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*, klicken Sie dann die Funktion aufgerufen wurde und bevor er abgeschlossen Ausführung **SQLCancel** oder **SQLCancelHandle** wurde wird aufgerufen, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde und, bevor es ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLGetTypeInfo** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber entspricht der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLGetTypeInfo** gibt die Ergebnisse als standard Resultset, sortiert nach DATA_TYPE und dann nach wie genau die Daten mit den entsprechenden ODBC SQL-Datentyp zurück. Von der Datenquelle definierte Datentypen haben Vorrang vor den benutzerdefinierten Datentypen. Daher kann die Sortierreihenfolge ist nicht unbedingt konsistent, aber werden zuerst als DATA_TYPE generalisiert, gefolgt von TYPE_NAME, beide Aufsteigend. Nehmen wir beispielsweise an, dass eine Datenquelle ganze Zahl und LEISTUNGSINDIKATOR-Datentypen definiert, in dem INDIKATOR wird automatisch erhöht, und auch ein benutzerdefinierten Datentyp WHOLENUM definiert wurde. Diese würden in der Reihenfolge WHOLENUM, ganze Zahl zurückgegeben werden und Zähler, da WHOLENUM entspricht fast der ODBC-SQL-Daten SQL_INTEGER, geben Sie zwar, geben Sie die Daten automatisch erhöht, obwohl von der Datenquelle unterstützt ordnet nicht eng in einen ODBC-SQL-Datentyp. Informationen dazu, wie diese Informationen verwendet werden kann, finden Sie unter [DDL-Anweisungen](../../../odbc/reference/develop-app/ddl-statements.md).  
  
 Wenn die *DataType* Argument gibt einen Datentyp, der für die vom Treiber unterstützt ODBC-Version gültig ist, jedoch wird vom Treiber nicht unterstützt, und dann wird ein leeres Resultset zurückgegeben.  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Die folgenden Spalten wurden umbenannt, ODBC 3. *x*. Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC 3. *x* Spalte|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|MONEY|FIXED_PREC_SCALE|  
|AUTO_INCREMENT|AUTO_UNIQUE_VALUE|  
  
 Das Resultset zurückgegebenes wurden die folgenden Spalten hinzugefügt **SQLGetTypeInfo** ODBC 3. *X*:  
  
-   SQL_DATA_TYPE  
  
-   INTERVAL_PRECISION  
  
-   SQL_DATETIME_SUB  
  
-   NUM_PREC_RADIX  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 19 (INTERVAL_PRECISION) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf die treiberspezifischen Spalten erhalten, durch eine explizite Ordnungsposition angeben, statt nach unten am Ende des Resultsets gezählt. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** möglicherweise nicht alle Datentypen zurück. Beispielsweise kann ein Treiber nicht benutzerdefinierte Datentypen zurückgeben. Anwendungen können eine beliebige gültige Datentyp verwenden, unabhängig davon, ob sie von zurückgegeben wird **SQLGetTypeInfo**. Die Datentypen, die vom **SQLGetTypeInfo** sind diejenigen, die von der Datenquelle unterstützt. Sie sind für die Verwendung in-Anweisungen (Data Definition Language, Datendefinitionssprache) vorgesehen. Treiber können die Resultset-Daten, die mithilfe der Datentypen von zurückgegebenen Typen zurückgeben **SQLGetTypeInfo**. Erstellen Sie das Resultset für eine Katalogfunktion auf, kann der Treiber einen Datentyp, der nicht unterstützt wird von der Datenquelle verwenden.  
  
|Spaltenname|Spalte<br /><br /> number|Datentyp|Kommentare|  
|-----------------|-----------------------|---------------|--------------|  
|TYPE_NAME (ODBC 2.0)|1|Varchar, die nicht NULL|Name des Data Source-abhängige Datentyp; z. B. "CHAR()", "VARCHAR()", "MONEY", "LONG VARBINARY" oder "CHAR () für BIT-Daten". Anwendungen müssen diesen Namen in verwenden **CREATE TABLE** und **ALTER TABLE** Anweisungen.|  
|DATA_TYPE (ODBC 2.0)|2|Smallint nicht NULL|SQL-Datentyp. Dies kann einen ODBC-SQL-Datentyp oder die treiberspezifischen SQL-Datentyp sein. Für die Datentypen "DateTime" oder das Intervall gibt diese Spalte den präzisen Datentyp (z. B. SQL_TYPE_TIME oder SQL_INTERVAL_YEAR_TO_MONTH) zurück. Eine Liste der gültigen ODBC-SQL-Datentypen, finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu Treiber-spezifische SQL-Datentypen finden Sie in der vom Treiber-Dokumentation.|  
|COLUMN_SIZE (ODBC 2.0)|3|Integer|Die maximale Spaltengröße, die der Server für diesen Datentyp unterstützt wird. Für numerische Daten ist dies die maximale Genauigkeit. Für Zeichenfolgendaten ist dies die Länge in Zeichen. Für Datetime-Datentypen ist dies die Länge in Zeichen der Zeichenfolgendarstellung (vorausgesetzt, die maximale zulässige Genauigkeit der Sekundenbruchteil-Komponente). NULL wird für Datentypen zurückgegeben, in denen ist Spaltengröße nicht anwendbar. Für die Interval-Datentypen, ist dies die Anzahl der Zeichen in die Darstellung der das Intervall literal (gemäß der mit Genauigkeit für anführenden Intervallwert, finden Sie unter [Datentyplänge Intervall](../../../odbc/reference/appendixes/interval-data-type-length.md) in Anhang D: Die Datentypen).<br /><br /> Weitere Informationen zu Spaltengröße, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|LITERAL_PREFIX-ZEICHEN (ODBC 2.0)|4|Varchar|Zeichen oder Zeichen verwendet, um ein Literal voranstellen; beispielsweise eine einfaches Anführungszeichen (') für Zeichendatentypen oder 0 X für binäre Datentypen; NULL wird für Datentypen zurückgegeben, in denen ist ein Zeichenfolgenliteral-Präfix nicht anwendbar.|  
|LITERAL_SUFFIX (ODBC 2.0)|5|Varchar|Zeichen oder Zeichen verwendet, um ein Literal beendet; Beispielsweise ist ein einfaches Anführungszeichen (') für Zeichendatentypen. NULL wird für Datentypen zurückgegeben, in denen ist eines literalen Suffixes nicht anwendbar.|  
|CREATE_PARAMS (ODBC 2.0)|6|Varchar|Eine Liste von Schlüsselwörtern, getrennt durch Kommas, die für jeden Parameter, die die Anwendung in Klammern angeben kann, wenn Sie den Namen zu verwenden, der in der TYPE_NAME-Feld zurückgegeben wird. Die Schlüsselwörter in der Liste können eine der folgenden sein: Länge, Genauigkeit oder Dezimalstellen. Sie werden in der Reihenfolge, in die Syntax verwendet werden muss. CREATE_PARAMS für DEZIMALSTELLEN wäre beispielsweise "Precision, Scale"; CREATE_PARAMS für VARCHAR würde "Length". gleich. NULL wird zurückgegeben, wenn keine Parameter für die Data-Type-Definition vorhanden sind; z. B. ganze Zahl.<br /><br /> Der Treiber stellt den CREATE_PARAMS Text in der Sprache Land/Region, in dem sie verwendet wird.|  
|NULL-WERTE ZULÄSST (ODBC 2.0)|7|Smallint nicht NULL|Gibt an, ob der Datentyp einen NULL-Wert zulässt:<br /><br /> SQL_NO_NULLS, wenn der Datentyp NULL-Werte nicht zulässig sind.<br /><br /> SQL_NULLABLE, wenn der Datentyp NULL-Werte zulässt.<br /><br /> SQL_NULLABLE_UNKNOWN, wenn nicht bekannt ist, ob die Spalte NULL-Werte annimmt.|  
|CASE_SENSITIVE (ODBC 2.0)|8|Smallint nicht NULL|Gibt an, ob ein Zeichendatentyp Groß-/Kleinschreibung beachtet, Sortierungen und Vergleiche ist:<br /><br /> SQL_TRUE, wenn der Datentyp einen Zeichendatentyp und Groß-/Kleinschreibung beachtet wird.<br /><br /> SQL_FALSE, wenn der Datentyp nicht vom Zeichendatentyp oder wird nicht beachtet.|  
|DURCHSUCHBARE (ODBC 2.0)|9|Smallint nicht NULL|Wie der Datentyp verwendet wird, in einem **, in denen** Klausel:<br /><br /> SQL_PRED_NONE, wenn die Spalte kann, in verwendet werden einem **, in denen** Klausel. (Dies ist der SQL_UNSEARCHABLE-Wert in ODBC 2. identisch. *x*.)<br /><br /> SQL_PRED_CHAR, wenn die Spalte kann, in verwendet werden eine **, in denen** -Klausel, aber nur mit der **wie** Prädikat. (Dies ist der SQL_LIKE_ONLY-Wert in ODBC 2. identisch. *x*.)<br /><br /> SQL_PRED_BASIC, wenn die Spalte kann, in verwendet werden eine **, in denen** -Klausel mit allen Vergleichsoperatoren mit Ausnahme **wie** (Vergleichsoperatoren, quantifizierte hingegen **BETWEEN**,  **UNTERSCHIEDLICHE**, **IN**, **Übereinstimmung**, und **UNIQUE**). (Dies ist der SQL_ALL_EXCEPT_LIKE-Wert in ODBC 2. identisch. *x*.)<br /><br /> SQL_SEARCHABLE, wenn die Spalte kann, in verwendet werden einem **, in denen** -Klausel mit jedem Vergleichsoperator.|  
|UNSIGNED_ATTRIBUTE (ODBC 2.0)|10|Smallint|Gibt an, ob der Datentyp kein Vorzeichen aufweist:<br /><br /> SQL_TRUE, wenn der Datentyp kein Vorzeichen aufweist.<br /><br /> SQL_FALSE, wenn der Datentyp ein Vorzeichen aufweist.<br /><br /> NULL wird zurückgegeben, wenn das Attribut nicht für den Datentyp gilt oder der Datentyp nicht numerisch ist.|  
|FIXED_PREC_SCALE (ODBC 2.0)|11|Smallint nicht NULL|Gibt an, ob der Datentyp vordefinierte fester Genauigkeit und Dezimalstellen (die Daten datenquellenspezifische sind), z. B. einen Money-Datentyp:<br /><br /> SQL_TRUE, wenn sie vordefinierte fester Genauigkeit und Dezimalstellenanzahl.<br /><br /> SQL_FALSE, wenn sie nicht über vordefinierte feste Genauigkeit und Dezimalstellen verfügt.|  
|AUTO_UNIQUE_VALUE ENTHÄLT (ODBC 2.0)|12|Smallint|Gibt an, ob der Datentyp automatisch inkrementiert wird:<br /><br /> SQL_TRUE, wenn der Datentyp automatisch inkrementiert wird.<br /><br /> SQL_FALSE, wenn der Datentyp nicht automatisch inkrementiert wird.<br /><br /> NULL wird zurückgegeben, wenn das Attribut nicht für den Datentyp gilt oder der Datentyp nicht numerisch ist.<br /><br /> Eine Anwendung können Sie die Werte in einer Spalte müssen dieses Attribut einfügen, aber die Werte in der Spalte in der Regel kann nicht aktualisiert werden.<br /><br /> Wenn eine Einfügung in einer automatisch inkrementierten Spalte erfolgt, wird ein eindeutiger Wert zum Zeitpunkt des Einfügens in die Spalte eingefügt. Die Schrittweite ist nicht definiert, aber Daten datenquellenspezifische ist. Eine Anwendung sollte nicht davon ausgehen, dass eine automatisch inkrementierten Spalte bei einem beliebigen Aspekt oder Schritten durch keinen bestimmten Wert beginnt.|  
|LOCAL_TYPE_NAME (ODBC 2.0)|13|Varchar|Lokalisierte Version des von der Datenquelle abhängigen Datentypamens. NULL wird zurückgegeben, wenn ein lokalisierter Name nicht von der Datenquelle unterstützt wird. Dieser Name ist für die Anzeige nur, z. B. Dialogfelder vorgesehen.|  
|MINIMUM_SCALE (ODBC 2.0)|14|Smallint|Die mindestdezimalstellen des Datentyps für die Datenquelle. Weist ein Datentyp Feste Dezimalstellen, enthalten die Spalten MINIMUM_SCALE und MAXIMUM_SCALE diesen Wert an. Z. B. möglicherweise eine SQL_TYPE_TIMESTAMP-Spalte eine feste Dezimalstellen für Sekundenbruchteile. NULL wird zurückgegeben, wenn Dezimalstellen auf den Datentyp nicht anwendbar sind. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|DIE MAXIMUM_SCALE (ODBC 2.0)|15|Smallint|Die maximalen Dezimalstellen des Datentyps für die Datenquelle. NULL wird zurückgegeben, wenn Dezimalstellen auf den Datentyp nicht anwendbar sind. Wenn die maximale Dezimalstellen für die Datenquelle nicht separat definiert, aber es wird stattdessen definiert der maximalen Genauigkeit entsprechen, enthält diese Spalte den gleichen Wert wie die COLUMN_SIZE-Spalte. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|SQL_DATA_TYPE (ODBC 3.0)|16|Smallint nicht NULL|Der Wert der SQL-Datentyp, wie er wird in das SQL_DESC_TYPE-Feld des Deskriptors angezeigt. Diese Spalte entspricht der DATA_TYPE-Spalte, mit Ausnahme von Intervall und Datetime-Datentypen.<br /><br /> Für Intervall und Datetime-Datentypen SQL_INTERVAL oder SQL_DATETIME die SQL_DATA_TYPE-Feld im Resultset zurück, und das Feld noch SQL_DATETIME_SUB dem Subcode für den bestimmten Intervall oder Datetime-Datentyp zurück. (Finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|NOCH SQL_DATETIME_SUB (ODBC 3.0)|17|Smallint|Wenn der Wert des SQL_DATA_TYPE SQL_DATETIME oder SQL_INTERVAL hat, enthält diese Spalte den Subcode für Datetime-Intervall. Für Datentypen als "DateTime" und das Intervall ist dieses Feld NULL.<br /><br /> Für das Intervall oder Datetime-Datentypen SQL_INTERVAL oder SQL_DATETIME die SQL_DATA_TYPE-Feld im Resultset zurück, und das Feld noch SQL_DATETIME_SUB dem Subcode für den bestimmten Intervall oder Datetime-Datentyp zurück. (Finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|NUM_PREC_RADIX (ODBC 3.0)|18|Integer|Wenn der Datentyp einen ungefähren numerischen Typ ist, enthält diese Spalte den Wert 2, um anzugeben, dass die COLUMN_SIZE eine Anzahl von Bits angibt. Bei exakten numerischen Datentypen enthält diese Spalte den Wert 10, um anzugeben, dass die COLUMN_SIZE eine Anzahl von Dezimalstellen angibt. Andernfalls ist diese Spalte NULL.|  
|INTERVAL_PRECISION (ODBC 3.0)|19|Smallint|Wenn der Datentyp ein Intervall-Datentyp ist, enthält diese Spalte den Wert für die die führende Genauigkeit Intervall. (Finden Sie unter [Genauigkeit für Datentyp Interval](../../../odbc/reference/appendixes/interval-data-type-precision.md) in Anhang D: Die Datentypen.) Andernfalls ist diese Spalte NULL.|  
  
 Informationen über Bildattribute kann für Datentypen oder für bestimmte Spalten in einem Resultset anwenden. **SQLGetTypeInfo** gibt Informationen zu Attributen, die zugeordneten Datentypen. **SQLColAttribute** gibt Informationen zu Attributen, die Spalten in einem Resultset zugeordnet sind.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLColAttribute-Funktion](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen einer einzelnen Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Zurückgeben von Informationen zu einer Datenquelle oder Treiber|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
