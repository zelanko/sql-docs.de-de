---
title: SQLGetTypeInfo-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47273c75a005f11b33e9929977b57607b36898de
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303261"
---
# <a name="sqlgettypeinfo-function"></a>SQLGetTypeInfo-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetTypeInfo** gibt Informationen zu Datentypen zurück, die von der Datenquelle unterstützt werden. Der Treiber gibt die Informationen in Form eines SQL-Ergebnissatzes zurück. Die Datentypen sind für die Verwendung in DDL-Anweisungen (Data Definition Language) vorgesehen.  
  
> [!IMPORTANT]  
>  Anwendungen müssen die Typnamen verwenden, die in der TYPE_NAME Spalte des **SQLGetTypeInfo-Ergebnissatzes** in **ALTER TABLE-** und **CREATE TABLE-Anweisungen** zurückgegeben werden. **SQLGetTypeInfo** gibt möglicherweise mehr als eine Zeile mit demselben Wert in der Spalte DATA_TYPE zurück.  
  
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
 [Eingabe] Der SQL-Datentyp. Dies muss einer der Werte im Abschnitt [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen oder ein treiberspezifischer SQL-Datentyp sein. SQL_ALL_TYPES gibt an, dass Informationen zu allen Datentypen zurückgegeben werden sollen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetTypeInfo** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLGetTypeInfo** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Ein angegebenes Anweisungsattribut war aufgrund von Implementierungsarbeitsbedingungen ungültig, sodass ein ähnlicher Wert vorübergehend ersetzt wurde. (Rufen Sie **SQLGetStmtAttr** auf, um den vorübergehend ersetzten Wert zu ermitteln.) Der Ersatzwert ist für das *StatementHandle gültig,* bis der Cursor geschlossen wird. Die Anweisungsattribute, die geändert werden können, sind: SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT und SQL_ATTR_SIMULATE_CURSOR. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|24.000|Ungültiger Cursorstatus|Im StatementHandle wurde ein Cursor *geöffnet,* und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Ein Resultset wurde für *das StatementHandle*geöffnet, **aber SQLFetch** oder **SQLFetchScroll** wurden nicht aufgerufen.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcenstillstands mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY004|Ungültiger SQL-Datentyp|Der für das Argument *DataType* angegebene Wert war weder ein gültiger ODBC SQL-Datentypbezeichner noch ein treiberspezifischer Datentypbezeichner, der vom Treiber unterstützt wird.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert, dann wurde die Funktion aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für *das StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLGetTypeInfo-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* entsprechende Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLGetTypeInfo** gibt die Ergebnisse als Standardergebnissatz zurück, sortiert nach DATA_TYPE und dann nach der Nähe des Datentyps, der dem entsprechenden ODBC SQL-Datentyp zugeordnet ist. Datentypen, die von der Datenquelle definiert werden, haben Vorrang vor benutzerdefinierten Datentypen. Folglich ist die Sortierreihenfolge nicht unbedingt konsistent, sondern kann als zuerst DATA_TYPE verallgemeinert werden, gefolgt von TYPE_NAME, beide aufsteigend. Angenommen, eine Datenquelle definierte INTEGER- und COUNTER-Datentypen, wobei COUNTER automatisch inkrementiert wird, und dass auch ein benutzerdefinierter Datentyp WHOLENUM definiert wurde. Diese würden in der Reihenfolge INTEGER, WHOLENUM und COUNTER zurückgegeben, da WHOLENUM dem ODBC SQL-Datentyp SQL_INTEGER nahe zugeordnet ist, während der Datentyp für die automatische Inkrementelle Datenart, obwohl er von der Datenquelle unterstützt wird, nicht eng einem ODBC SQL-Datentyp zugeordnet ist. Informationen zur Verwendung dieser Informationen finden Sie unter [DDL-Anweisungen](../../../odbc/reference/develop-app/ddl-statements.md).  
  
 Wenn das *DataType-Argument* einen Datentyp angibt, der für die vom Treiber unterstützte ODBC-Version gültig ist, aber vom Treiber nicht unterstützt wird, gibt es ein leeres Resultset zurück.  
  
> [!NOTE]  
>  Weitere Informationen zur allgemeinen Verwendung, Argumente und zurückgegebenen Daten von ODBC-Katalogfunktionen finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Die folgenden Spalten wurden für ODBC 3 umbenannt. *x*. Die Änderungen des Spaltennamens wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer binden.  
  
|ODBC 2.0-Säule|ODBC 3. *x-Spalte*|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|MONEY|FIXED_PREC_SCALE|  
|AUTO_INCREMENT|AUTO_UNIQUE_VALUE|  
  
 Die folgenden Spalten wurden dem von **SQLGetTypeInfo** für ODBC 3 zurückgegebenen Ergebnissatz hinzugefügt. *x*:  
  
-   SQL_DATA_TYPE  
  
-   INTERVAL_PRECISION  
  
-   SQL_DATETIME_SUB  
  
-   NUM_PREC_RADIX  
  
 In der folgenden Tabelle sind die Spalten im Resultset aufgeführt. Zusätzliche Spalten über Spalte 19 (INTERVAL_PRECISION) hinaus können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifische Spalten erhalten, indem sie vom Ende des Resultsets herunterzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt möglicherweise nicht alle Datentypen zurück. Ein Treiber gibt z. B. möglicherweise keine benutzerdefinierten Datentypen zurück. Anwendungen können einen beliebigen gültigen Datentyp verwenden, unabhängig davon, ob er von **SQLGetTypeInfo**zurückgegeben wird. Die von **SQLGetTypeInfo** zurückgegebenen Datentypen sind die von der Datenquelle unterstützten. Sie sind für die Verwendung in DDL-Anweisungen (Data Definition Language) vorgesehen. Treiber können Resultset-Daten mithilfe anderer Datentypen als der von **SQLGetTypeInfo**zurückgegebenen Typen zurückgeben. Beim Erstellen des Resultsets für eine Katalogfunktion verwendet der Treiber möglicherweise einen Datentyp, der von der Datenquelle nicht unterstützt wird.  
  
|Spaltenname|Column<br /><br /> number|Datentyp|Kommentare|  
|-----------------|-----------------------|---------------|--------------|  
|TYPE_NAME (ODBC 2.0)|1|Varchar nicht NULL|Name des datenquellenabhängigen Datentyps; z. B. "CHAR()", "VARCHAR()", "MONEY", "LONG VARBINARY" oder "CHAR ( ) FOR BIT DATA". Anwendungen müssen diesen Namen in **CREATE TABLE-** und **ALTER TABLE-Anweisungen** verwenden.|  
|DATA_TYPE (ODBC 2.0)|2|Smallint nicht NULL|SQL-Datentyp. Dies kann ein ODBC SQL-Datentyp oder ein treiberspezifischer SQL-Datentyp sein. Bei Datums- oder Intervalldatentypen gibt diese Spalte den knappen Datentyp zurück (z. B. SQL_TYPE_TIME oder SQL_INTERVAL_YEAR_TO_MONTH). Eine Liste gültiger ODBC SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.|  
|COLUMN_SIZE (ODBC 2.0)|3|Integer|Die maximale Spaltengröße, die der Server für diesen Datentyp unterstützt. Bei numerischen Daten ist dies die maximale Genauigkeit. Bei Zeichenfolgendaten ist dies die Länge in Zeichen. Bei Datetime-Datentypen ist dies die Länge in Zeichen der Zeichenfolgendarstellung (unter der Voraussetzung, dass die maximale Genauigkeit der Komponente Bruchsekunden maximal zulässig ist). NULL wird für Datentypen zurückgegeben, für die die Spaltengröße nicht anwendbar ist. Bei Intervalldatentypen ist dies die Anzahl der Zeichen in der Zeichendarstellung des Intervallliterals (wie durch die Intervallführungsgenauigkeit definiert; siehe [Intervalldatentyplänge](../../../odbc/reference/appendixes/interval-data-type-length.md) in Anhang D: Datentypen).<br /><br /> Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|LITERAL_PREFIX (ODBC 2.0)|4|Varchar|Zeichen oder Zeichen, die verwendet werden, um einem Literal voranzupräfixieren; z. B. ein einfaches Anführungszeichen (') für Zeichendatentypen oder 0x für binäre Datentypen; NULL wird für Datentypen zurückgegeben, für die ein Literalpräfix nicht anwendbar ist.|  
|LITERAL_SUFFIX (ODBC 2.0)|5|Varchar|Zeichen oder Zeichen, die zum Beenden eines Literals verwendet werden; z. B. ein einfaches Anführungszeichen (') für Zeichendatentypen; NULL wird für Datentypen zurückgegeben, für die ein Literalsuffix nicht anwendbar ist.|  
|CREATE_PARAMS (ODBC 2.0)|6|Varchar|Eine Liste von Schlüsselwörtern, getrennt durch Kommas, die jedem Parameter entspricht, den die Anwendung in Klammern angeben kann, wenn der Name verwendet wird, der im Feld TYPE_NAME zurückgegeben wird. Die Schlüsselwörter in der Liste können eines der folgenden Schlüsselwörter sein: Länge, Genauigkeit oder Maßstab. Sie werden in der Reihenfolge angezeigt, in der sie für die Syntax verwendet werden müssen. Beispielsweise wäre CREATE_PARAMS für DECIMAL "Präzision, Maßstab"; CREATE_PARAMS für VARCHAR würde "Länge" entsprechen. NULL wird zurückgegeben, wenn keine Parameter für die Datentypdefinition vorhanden sind. z. B. INTEGER.<br /><br /> Der Treiber liefert den CREATE_PARAMS Text in der Sprache des Landes/der Region, in dem er verwendet wird.|  
|NULLABLE (ODBC 2.0)|7|Smallint nicht NULL|Gibt an, ob der Datentyp einen NULL-Wert akzeptiert:<br /><br /> SQL_NO_NULLS, wenn der Datentyp keine NULL-Werte akzeptiert.<br /><br /> SQL_NULLABLE, wenn der Datentyp NULL-Werte akzeptiert.<br /><br /> SQL_NULLABLE_UNKNOWN, ob nicht bekannt ist, ob die Spalte NULL-Werte akzeptiert.|  
|CASE_SENSITIVE (ODBC 2.0)|8|Smallint nicht NULL|Gibt an, ob bei Sortierungen und Vergleichen bei einem Zeichendatentyp die Groß-/Kleinschreibung beachtet wird:<br /><br /> SQL_TRUE, wenn es sich bei dem Datentyp um einen Zeichendatentyp handelt und die Groß-/Kleinschreibung beachtet wird.<br /><br /> SQL_FALSE, wenn der Datentyp kein Zeichendatentyp ist oder nicht die Groß-/Kleinschreibung beachtet wird.|  
|DURCHSUCHBAR (ODBC 2.0)|9|Smallint nicht NULL|Wie der Datentyp in einer **WHERE-Klausel** verwendet wird:<br /><br /> SQL_PRED_NONE, wenn die Spalte nicht in einer **WHERE-Klausel** verwendet werden kann. (Dies entspricht dem SQL_UNSEARCHABLE Wert in ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR, ob die Spalte in einer **WHERE-Klausel** verwendet werden kann, jedoch nur mit dem **PRÄdikat LIKE.** (Dies entspricht dem SQL_LIKE_ONLY Wert in ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC, ob die Spalte in einer **WHERE-Klausel** mit allen Vergleichsoperatoren außer **LIKE** verwendet werden kann (Vergleich, quantifizierter Vergleich, **BETWEEN**, **DISTINCT**, **IN**, **MATCH**und **UNIQUE**). (Dies entspricht dem SQL_ALL_EXCEPT_LIKE Wert in ODBC 2. *x*.)<br /><br /> SQL_SEARCHABLE, ob die Spalte in einer **WHERE-Klausel** mit einem beliebigen Vergleichsoperator verwendet werden kann.|  
|UNSIGNED_ATTRIBUTE (ODBC 2.0)|10|Smallint|Gibt an, ob der Datentyp nicht signiert ist:<br /><br /> SQL_TRUE, wenn der Datentyp nicht signiert ist.<br /><br /> SQL_FALSE, wenn der Datentyp signiert ist.<br /><br /> NULL wird zurückgegeben, wenn das Attribut nicht auf den Datentyp anwendbar ist oder der Datentyp nicht numerisch ist.|  
|FIXED_PREC_SCALE (ODBC 2.0)|11|Smallint nicht NULL|Gibt an, ob der Datentyp über eine vordefinierte feste Genauigkeit und Skalierung (die datenquellenspezifisch sind) verfügt, z. B. ein Gelddatentyp:<br /><br /> SQL_TRUE, wenn es eine vordefinierte feste Genauigkeit und Skalierung hat.<br /><br /> SQL_FALSE, wenn es keine vordefinierte feste Genauigkeit und Skalierung hat.|  
|AUTO_UNIQUE_VALUE (ODBC 2.0)|12|Smallint|Gibt an, ob der Datentyp automatisch inkrementiert wird:<br /><br /> SQL_TRUE, ob der Datentyp automatisch inkrementiert wird.<br /><br /> SQL_FALSE, wenn der Datentyp nicht automatisch inkrementiert wird.<br /><br /> NULL wird zurückgegeben, wenn das Attribut nicht auf den Datentyp anwendbar ist oder der Datentyp nicht numerisch ist.<br /><br /> Eine Anwendung kann Werte in eine Spalte mit diesem Attribut einfügen, aber in der Regel die Werte in der Spalte nicht aktualisieren.<br /><br /> Wenn eine Einfügung in eine Auto-Inkrement-Spalte vorgenommen wird, wird ein eindeutiger Wert zum Zeitpunkt des Einfügens in die Spalte eingefügt. Das Inkrement ist nicht definiert, sondern datenquellenspezifisch. Eine Anwendung sollte nicht davon ausgehen, dass eine Spalte mit automatischer Inkrementierung an einem bestimmten Punkt oder in Schritten um einen bestimmten Wert beginnt.|  
|LOCAL_TYPE_NAME (ODBC 2.0)|13|Varchar|Lokalisierte Version des von der Datenquelle abhängigen Datentypamens. NULL wird zurückgegeben, wenn ein lokalisierter Name nicht von der Datenquelle unterstützt wird. Dieser Name ist nur für die Anzeige vorgesehen, z. B. in Dialogfeldern.|  
|MINIMUM_SCALE (ODBC 2.0)|14|Smallint|Die Mindestskalierung des Datentyps in der Datenquelle. Wenn für einen Datentyp feste Dezimalstellen definiert wurden, enthalten die Spalten MINIMUM_SCALE und MAXIMUM_SCALE denselben Wert. Eine SQL_TYPE_TIMESTAMP Spalte kann z. B. eine feste Skalierung für Sekundenbruchteile haben. NULL wird zurückgegeben, wenn Dezimalstellen auf den Datentyp nicht anwendbar sind. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|MAXIMUM_SCALE (ODBC 2.0)|15|Smallint|Die maximale Skalierung des Datentyps in der Datenquelle. NULL wird zurückgegeben, wenn Dezimalstellen auf den Datentyp nicht anwendbar sind. Wenn der maximale Maßstab nicht separat in der Datenquelle definiert wird, sondern so definiert ist, dass er mit der maximalen Genauigkeit identisch ist, enthält diese Spalte denselben Wert wie die COLUMN_SIZE Spalte. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|SQL_DATA_TYPE (ODBC 3.0)|16|Smallint NICHT NULL|Der Wert des SQL-Datentyps, wie er im SQL_DESC_TYPE Feld des Deskriptors angezeigt wird. Diese Spalte entspricht der DATA_TYPE Spalte, mit Ausnahme von Intervall- und Datumszeitdatentypen.<br /><br /> Bei Intervall- und Datumszeitdatentypen gibt das Feld SQL_DATA_TYPE im Resultset SQL_INTERVAL oder SQL_DATETIME zurück, und das Feld SQL_DATETIME_SUB gibt den Untercode für den spezifischen Intervall- oder Datumszeitdatentyp zurück. (Siehe [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3.0)|17|Smallint|Wenn der Wert von SQL_DATA_TYPE SQL_DATETIME oder SQL_INTERVAL ist, enthält diese Spalte den Untercode datumsweise/Intervall. Für andere Datentypen als Datumszeit und Intervall ist dieses Feld NULL.<br /><br /> Bei Intervall- oder Datumszeitdatentypen gibt das Feld SQL_DATA_TYPE im Resultset SQL_INTERVAL oder SQL_DATETIME zurück, und das Feld SQL_DATETIME_SUB gibt den Untercode für den spezifischen Intervall- oder Datumszeitdatentyp zurück. (Siehe [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|NUM_PREC_RADIX (ODBC 3.0)|18|Integer|Wenn es sich bei dem Datentyp um einen ungefähren numerischen Typ handelt, enthält diese Spalte den Wert 2, um anzugeben, dass COLUMN_SIZE eine Anzahl von Bits angibt. Für exakte numerische Typen enthält diese Spalte den Wert 10, um anzugeben, dass COLUMN_SIZE eine Anzahl von Dezimalstellen angibt. Andernfalls ist diese Spalte NULL.|  
|INTERVAL_PRECISION (ODBC 3.0)|19|Smallint|Wenn es sich bei dem Datentyp um einen Intervalldatentyp handelt, enthält diese Spalte den Wert der Intervallführungsgenauigkeit. (Siehe [Intervalldatentypgenauigkeit](../../../odbc/reference/appendixes/interval-data-type-precision.md) in Anhang D: Datentypen.) Andernfalls ist diese Spalte NULL.|  
  
 Attributinformationen können auf Datentypen oder auf bestimmte Spalten in einer Ergebnismenge angewendet werden. **SQLGetTypeInfo** gibt Informationen zu Attributen zurück, die Datentypen zugeordnet sind. **SQLColAttribute** gibt Informationen zu Attributen zurück, die Spalten in einem Resultset zugeordnet sind.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einer Ergebnismenge|[SQLColAttribute-Funktion](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in einer vorwärtsgerichteten Richtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Zurückgeben von Informationen zu einem Treiber oder einer Datenquelle|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
