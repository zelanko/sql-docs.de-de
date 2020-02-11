---
title: Sqlgettypeingefo-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030587"
---
# <a name="sqlgettypeinfo-function"></a>SQLGetTypeInfo-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetTypeInfo** gibt Informationen zu Datentypen zurück, die von der Datenquelle unterstützt werden. Der Treiber gibt die Informationen in Form eines SQL-Resultsets zurück. Die Datentypen sind für die Verwendung in DDL-Anweisungen (Data Definition Language) vorgesehen.  
  
> [!IMPORTANT]  
>  Anwendungen müssen die Typnamen verwenden, die in der Spalte TYPE_NAME des Resultsets **SQLGetTypeInfo** in den Anweisungen **ALTER TABLE** und **CREATE TABLE** zurückgegeben werden. **SQLGetTypeInfo** gibt möglicherweise mehr als eine Zeile mit demselben Wert in der DATA_TYPE Spalte zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetTypeInfo(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   DataType);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle für das Resultset.  
  
 *DataType*  
 Der Der SQL-Datentyp. Dies muss einer der Werte im Abschnitt SQL- [Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) von Anhang D: Datentypen oder ein Treiber spezifischer SQL-Datentyp sein. SQL_ALL_TYPES gibt an, dass Informationen zu allen Datentypen zurückgegeben werden sollen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetTypeInfo** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle werden die SQLSTATE-Werte aufgelistet, die häufig von **SQLGetTypeInfo** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s02 entsprechen|Optionswert geändert|Ein angegebenes Anweisungs Attribut war aufgrund von Implementierungs Arbeitsbedingungen ungültig, sodass ein ähnlicher Wert vorübergehend ersetzt wurde. (Aufrufen von **SQLGetStmtAttr** , um den vorübergehend ersetzten Wert zu bestimmen.) Der Ersatzwert ist für " *StatementHandle* " gültig, bis der Cursor geschlossen wird. Die Anweisungs Attribute, die geändert werden können, sind: SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT und SQL_ATTR_SIMULATE_CURSOR. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor war auf dem *StatementHandle geöffnet,* und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Resultset war für *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde aufgrund eines Ressourcen Deadlocks mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Anweisungs Vervollständigung unbekannt|Die zugeordnete Verbindung konnte während der Ausführung dieser Funktion nicht hergestellt werden, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY004|Ungültiger SQL-Datentyp.|Der für den Argument *Datentyp* angegebene Wert war weder ein gültiger ODBC-SQL-Datentyp Bezeichner noch ein Treiber spezifischer Datentyp Bezeichner, der vom Treiber unterstützt wird.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert, dann wurde die Funktion aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die-Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **sqlgettypeingefo** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der der *StatementHandle* entsprechende Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLGetTypeInfo** gibt die Ergebnisse als Standardresultset zurück, geordnet nach DATA_TYPE und dann nach der Übereinstimmung des Datentyps mit dem entsprechenden ODBC SQL-Datentyp. Datentypen, die von der Datenquelle definiert werden, haben Vorrang vor benutzerdefinierten Datentypen. Folglich ist die Sortierreihenfolge nicht notwendigerweise konsistent, kann jedoch als data_type zuerst generalisiert werden, gefolgt von TYPE_NAME, beide aufsteigend. Nehmen wir beispielsweise an, dass eine Datenquelle die Datentypen integer und Counter definiert, wobei Counter automatisch inkrementiert wird und dass auch ein benutzerdefinierter Datentyp "wholenum" definiert wurde. Diese werden in den Reihenfolge Integer, wholenum und Counter zurückgegeben, da die-Ganzzahl dem ODBC-SQL-Datentyp SQL_INTEGER nah zugeordnet wird, während der automatisch inkrementierende Datentyp, auch wenn er von der Datenquelle unterstützt wird, einem ODBC-SQL-Datentyp nicht genau zugeordnet ist. Informationen dazu, wie diese Informationen verwendet werden können, finden Sie unter [DDL-Anweisungen](../../../odbc/reference/develop-app/ddl-statements.md).  
  
 Wenn das *DataType* -Argument einen Datentyp angibt, der für die Version von ODBC gültig ist, die vom Treiber unterstützt wird, jedoch nicht vom Treiber unterstützt wird, wird ein leeres Resultset zurückgegeben.  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumente und zurückgegebene Daten von ODBC-Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Die folgenden Spalten wurden für ODBC 3 umbenannt. *x*. Die Spaltennamen Änderungen wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer gebunden werden.  
  
|ODBC 2,0-Spalte|ODBC 3. *x* -Spalte|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|MONEY|FIXED_PREC_SCALE|  
|AUTO_INCREMENT|AUTO_UNIQUE_VALUE|  
  
 Die folgenden Spalten wurden dem von **SQLGetTypeInfo** für ODBC 3 zurückgegebenen Resultset hinzugefügt. *x*:  
  
-   SQL_DATA_TYPE  
  
-   INTERVAL_PRECISION  
  
-   SQL_DATETIME_SUB  
  
-   NUM_PREC_RADIX  
  
 In der folgenden Tabelle werden die Spalten im Resultset aufgelistet. Zusätzliche Spalten, die über die Spalte 19 (INTERVAL_PRECISION) hinausgehen, können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf Treiber spezifische Spalten erhalten, indem Sie vom Ende des Resultsets abzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt möglicherweise nicht alle Datentypen zurück. Beispielsweise gibt ein Treiber möglicherweise keine benutzerdefinierten Datentypen zurück. Anwendungen können jeden gültigen Datentyp verwenden, unabhängig davon, ob Sie von **SQLGetTypeInfo**zurückgegeben werden. Die von **SQLGetTypeInfo** zurückgegebenen Datentypen sind die von der Datenquelle unterstützten Datentypen. Sie sind für die Verwendung in DDL-Anweisungen (Data Definition Language) vorgesehen. Treiber können Resultsetdaten mit anderen Datentypen als den von **SQLGetTypeInfo**zurückgegebenen Typen zurückgeben. Beim Erstellen des Resultsets für eine Katalog Funktion kann der Treiber einen Datentyp verwenden, der nicht von der Datenquelle unterstützt wird.  
  
|Spaltenname|Column<br /><br /> number|Datentyp|Kommentare|  
|-----------------|-----------------------|---------------|--------------|  
|Type_name (ODBC 2,0)|1|Varchar not NULL|Datenquellen abhängiger Datentyp Name; beispielsweise "char ()", "varchar ()", "Money", "Long varbinary" oder "char () for Bit Data". Anwendungen müssen diesen Namen in **CREATE TABLE** -und **ALTER TABLE** -Anweisungen verwenden.|  
|Data_type (ODBC 2,0)|2|Smallint nicht NULL|SQL-Datentyp. Hierbei kann es sich um einen ODBC-SQL-Datentyp oder um einen treiberspezifischen SQL-Datentyp handeln. Für DateTime-oder interval-Datentypen gibt diese Spalte den präzisen Datentyp zurück (z. b. SQL_TYPE_TIME oder SQL_INTERVAL_YEAR_TO_MONTH). Eine Liste der gültigen ODBC-SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.|  
|COLUMN_SIZE (ODBC 2,0)|3|Integer|Die maximale Spaltengröße, die der Server für diesen Datentyp unterstützt. Bei numerischen Daten ist dies die maximale Genauigkeit. Bei Zeichen folgen Daten ist dies die Länge in Zeichen. Bei datetime-Datentypen ist dies die Länge in Zeichen der Zeichen folgen Darstellung (vorausgesetzt, die maximal zulässige Genauigkeit der Komponente für Sekundenbruchteile). NULL wird für Datentypen zurückgegeben, bei denen die Spaltengröße nicht anwendbar ist. Bei interval-Datentypen ist dies die Anzahl der Zeichen in der Zeichen Darstellung des intervallliterals (wie durch die vorangehende Genauigkeit definiert). Weitere Informationen finden Sie unter [Intervall Datentyp Länge](../../../odbc/reference/appendixes/interval-data-type-length.md) in Anhang D: Datentypen.<br /><br /> Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalstellen, Länge von Oktett übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|LITERAL_PREFIX (ODBC 2,0)|4|Varchar|Zeichen oder Zeichen, die verwendet werden, um einem literalpräfix zum Beispiel ein einzelnes Anführungszeichen (') für Zeichen Datentypen oder 0x für binäre Datentypen; NULL wird für Datentypen zurückgegeben, bei denen kein literalpräfix anwendbar ist.|  
|LITERAL_SUFFIX (ODBC 2,0)|5|Varchar|Zum Beenden eines Literals verwendetes Zeichen oder Zeichen zum Beispiel ein einzelnes Anführungszeichen (') für Zeichen Datentypen; NULL wird für Datentypen zurückgegeben, bei denen ein literales Suffix nicht anwendbar ist.|  
|CREATE_PARAMS (ODBC 2,0)|6|Varchar|Eine durch Kommas getrennte Liste von Schlüsselwörtern entsprechend den einzelnen Parametern, die von der Anwendung in Klammern angegeben werden können, wenn der Name verwendet wird, der im TYPE_NAME Feld zurückgegeben wird. Die Schlüsselwörter in der Liste können eine der folgenden sein: Länge, Genauigkeit oder Skalierung. Sie werden in der Reihenfolge angezeigt, in der Sie von der Syntax verwendet werden müssen. Beispielsweise ist CREATE_PARAMS für Decimal "Precision, Scale". CREATE_PARAMS für varchar wäre gleich "length". NULL wird zurückgegeben, wenn keine Parameter für die Datentyp Definition vorhanden sind. beispielsweise Integer.<br /><br /> Der Treiber liefert den CREATE_PARAMS Text in der Sprache des Landes bzw. der Region, in dem er verwendet wird.|  
|Nullable (ODBC 2,0)|7|Smallint nicht NULL|Gibt an, ob der Datentyp einen NULL-Wert akzeptiert:<br /><br /> SQL_NO_NULLS, wenn der Datentyp keine NULL-Werte akzeptiert.<br /><br /> SQL_NULLABLE, wenn der Datentyp NULL-Werte akzeptiert.<br /><br /> SQL_NULLABLE_UNKNOWN, wenn nicht bekannt ist, ob die Spalte NULL-Werte akzeptiert.|  
|CASE_SENSITIVE (ODBC 2,0)|8|Smallint nicht NULL|Ob bei einem Zeichen Datentyp in Sortierungen und vergleichen die Groß-/Kleinschreibung beachtet wird:<br /><br /> SQL_TRUE, wenn der Datentyp ein Zeichen Datentyp ist und die Groß-/Kleinschreibung beachtet.<br /><br /> SQL_FALSE, wenn der Datentyp kein Zeichen Datentyp ist oder die Groß-/Kleinschreibung nicht beachtet.|  
|Durchsuchbar (ODBC 2,0)|9|Smallint nicht NULL|Verwendung des Datentyps in einer **Where** -Klausel:<br /><br /> SQL_PRED_NONE, wenn die Spalte nicht in einer **Where** -Klausel verwendet werden kann. (Dies entspricht dem SQL_UNSEARCHABLE Wert in ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR, wenn die Spalte in einer **Where** -Klausel verwendet werden kann, jedoch nur mit dem **like** -Prädikat. (Dies entspricht dem SQL_LIKE_ONLY Wert in ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC, wenn die Spalte in einer **Where** -Klausel mit allen Vergleichs Operatoren mit Ausnahme von **like** verwendet werden kann (Vergleich, quantifizierter Vergleich, **between**, **verschieden**, **in**, **Match**und **Unique**). (Dies entspricht dem SQL_ALL_EXCEPT_LIKE Wert in ODBC 2. *x*.)<br /><br /> SQL_SEARCHABLE, wenn die Spalte in einer **Where** -Klausel mit einem beliebigen Vergleichs Operator verwendet werden kann.|  
|UNSIGNED_ATTRIBUTE (ODBC 2,0)|10|Smallint|Gibt an, ob der Datentyp nicht signiert ist:<br /><br /> SQL_TRUE, wenn der Datentyp nicht signiert ist.<br /><br /> SQL_FALSE, wenn der Datentyp signiert ist.<br /><br /> NULL wird zurückgegeben, wenn das Attribut nicht auf den Datentyp anwendbar ist oder der Datentyp nicht numerisch ist.|  
|FIXED_PREC_SCALE (ODBC 2,0)|11|Smallint nicht NULL|Gibt an, ob der Datentyp eine vordefinierte festgelegte Genauigkeit und Dezimalstellen (Datenquellen spezifisch) aufweist, wie z. b. ein Money-Datentyp:<br /><br /> SQL_TRUE, wenn Sie eine vordefinierte Genauigkeit und dezimal sind.<br /><br /> SQL_FALSE, wenn Sie nicht über eine vordefinierte Genauigkeit und Skalierung mit fester Genauigkeit verfügt.|  
|AUTO_UNIQUE_VALUE (ODBC 2,0)|12|Smallint|Gibt an, ob der Datentyp automatisch inkrementiert wird:<br /><br /> SQL_TRUE, wenn der Datentyp automatisch inkrementiert wird.<br /><br /> SQL_FALSE, wenn der Datentyp nicht automatisch inkrementiert wird.<br /><br /> NULL wird zurückgegeben, wenn das Attribut nicht auf den Datentyp anwendbar ist oder der Datentyp nicht numerisch ist.<br /><br /> Eine Anwendung kann Werte in eine Spalte einfügen, die über dieses Attribut verfügt, aber die Werte in der Spalte in der Regel nicht aktualisieren können.<br /><br /> Wenn eine Einfügung in eine automatische Inkrement-Spalte eingefügt wird, wird während der Einfügezeit ein eindeutiger Wert in die Spalte eingefügt. Das Inkrement ist nicht definiert, sondern ist Datenquellen spezifisch. Eine Anwendung sollte nicht davon ausgehen, dass eine automatische Inkrement-Spalte an einem bestimmten Punkt beginnt oder um einen bestimmten Wert erhöht.|  
|LOCAL_TYPE_NAME (ODBC 2,0)|13|Varchar|Lokalisierte Version des von der Datenquelle abhängigen Datentypamens. NULL wird zurückgegeben, wenn ein lokalisierter Name nicht von der Datenquelle unterstützt wird. Dieser Name ist nur für die Anzeige vorgesehen, z. b. in Dialogfeldern.|  
|MINIMUM_SCALE (ODBC 2,0)|14|Smallint|Die minimale Skala des Datentyps in der Datenquelle. Wenn für einen Datentyp feste Dezimalstellen definiert wurden, enthalten die Spalten MINIMUM_SCALE und MAXIMUM_SCALE denselben Wert. Beispielsweise kann eine SQL_TYPE_TIMESTAMP Spalte eine feste Skala für Sekundenbruchteile aufweisen. NULL wird zurückgegeben, wenn Dezimalstellen auf den Datentyp nicht anwendbar sind. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|MAXIMUM_SCALE (ODBC 2,0)|15|Smallint|Die maximale Skalierung des Datentyps in der Datenquelle. NULL wird zurückgegeben, wenn Dezimalstellen auf den Datentyp nicht anwendbar sind. Wenn die maximale Skala nicht separat in der Datenquelle definiert ist, sondern stattdessen so definiert ist, dass Sie mit der maximalen Genauigkeit identisch ist, enthält diese Spalte denselben Wert wie die COLUMN_SIZE Spalte. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|SQL_DATA_TYPE (ODBC 3,0)|16|Smallint not NULL|Der Wert des SQL-Datentyps, wie er im SQL_DESC_TYPE-Feld des Deskriptors angezeigt wird. Diese Spalte ist mit Ausnahme von Interval-und datetime-Datentypen identisch mit der Spalte data_type.<br /><br /> Bei Interval-und datetime-Datentypen gibt das SQL_DATA_TYPE-Feld im Resultset SQL_INTERVAL oder SQL_DATETIME zurück, und das SQL_DATETIME_SUB Feld gibt den Subcode für den spezifischen Interval-oder DateTime-Datentyp zurück. (Siehe [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3,0)|17|Smallint|Wenn der Wert von SQL_DATA_TYPE SQL_DATETIME oder SQL_INTERVAL ist, enthält diese Spalte den DateTime/Interval-Subcode. Bei anderen Datentypen als DateTime und Interval ist dieses Feld NULL.<br /><br /> Bei Interval-oder datetime-Datentypen gibt das SQL_DATA_TYPE-Feld im Resultset SQL_INTERVAL oder SQL_DATETIME zurück, und das SQL_DATETIME_SUB Feld gibt den Subcode für den spezifischen Interval-oder DateTime-Datentyp zurück. (Siehe [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|NUM_PREC_RADIX (ODBC 3,0)|18|Integer|Wenn es sich bei dem Datentyp um einen ungefähren numerischen Typ handelt, enthält diese Spalte den Wert 2, um anzugeben, dass COLUMN_SIZE eine Anzahl von Bits angibt. Bei exakten numerischen Typen enthält diese Spalte den Wert 10, um anzugeben, dass COLUMN_SIZE eine Anzahl von Dezimalziffern angibt. Andernfalls ist diese Spalte NULL.|  
|INTERVAL_PRECISION (ODBC 3,0)|19|Smallint|Wenn der Datentyp ein Interval-Datentyp ist, enthält diese Spalte den Wert der führenden Genauigkeit des Intervalls. (Weitere Informationen finden Sie unter [Interval Datentyp Precision](../../../odbc/reference/appendixes/interval-data-type-precision.md) in Anhang D: Datentypen.) Andernfalls ist diese Spalte NULL.|  
  
 Attributinformationen können auf Datentypen oder bestimmte Spalten in einem Resultset angewendet werden. **SQLGetTypeInfo** gibt Informationen zu Attributen zurück, die Datentypen zugeordnet sind. **SQLColAttribute** gibt Informationen zu Attributen zurück, die Spalten in einem Resultset zugeordnet sind.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLColAttribute-Funktion](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Zurückgeben von Informationen zu einem Treiber oder einer Datenquelle|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
