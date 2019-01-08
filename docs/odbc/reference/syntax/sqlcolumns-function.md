---
title: SQLColumns-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumns
helpviewer_keywords:
- SQLColumns function [ODBC]
ms.assetid: 4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51b14014853e0ccb91293097fd3aa81c1edcb2ae
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53207739"
---
# <a name="sqlcolumns-function"></a>SQLColumns-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: Gruppe öffnen  
  
 **Zusammenfassung**  
 **SQLColumns** die Liste der Spaltennamen in angegebenen Tabellen zurückgegeben. Der Treiber gibt diese Informationen, die als Resultset für das angegebene *StatementHandle*.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLColumns(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      ColumnName,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *Katalogname*  
 [Eingabe] Name des Katalogs. Wenn ein Treiber unterstützt die Kataloge für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") gibt an, die Tabellen, denen keine Kataloge. *CatalogName* darf kein Suchmuster Zeichenfolge enthalten.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *CatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *CatalogName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen des **CatalogName*.  
  
 *SchemaName*  
 [Eingabe] Zeichenfolge Suchmuster für den Schemanamen an. Wenn ein Treiber unterstützt die Schemas für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") gibt an, die Tabellen, die keine Schemas aufweisen.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *SchemaName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *SchemaName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen des **SchemaName*.  
  
 *TableName*  
 [Eingabe] Eine Zeichenfolge Suchmuster für den Tabellennamen.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *TableName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *TableName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen des **TableName*.  
  
 *ColumnName*  
 [Eingabe] Eine Zeichenfolge Suchmuster für den Spaltennamen.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *ColumnName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *ColumnName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength4*  
 [Eingabe] Länge in Zeichen des **ColumnName*.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLColumns** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLColumns** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle* aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde wegen eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Das Anweisungsattribut SQL_ATTR_METADATA_ID wurde festgelegt auf SQL_TRUE, die *CatalogName* Argument wurde ein null-Zeiger ist, und die SQL_CATALOG_NAME *Informationsart* gibt zurück, die Namen Katalog werden unterstützt.<br /><br /> (DM) das Anweisungsattribut SQL_ATTR_METADATA_ID wurde Wert auf SQL_TRUE festgelegt, und die *SchemaName*, *TableName*, oder *ColumnName* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLColumns** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert eines der Argumente Länge Name war kleiner als 0, jedoch nicht SQL_NTS gleich.|  
|||Der Wert eines der Argumente Namen Länge überschritten Wert für maximale Länge für die entsprechenden Katalog oder den Namen an. Die maximale Länge der einzelnen Katalog oder der Name abgerufen werden kann, durch den Aufruf **SQLGetInfo** mit der *Informationsart* Werte. (Siehe "Kommentare".)|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Ein Katalogname wurde angegeben, und der Treiber oder die Datenquelle Kataloge nicht unterstützt.<br /><br /> Ein Schemaname angegeben wurde, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Ein Suchmuster für die Zeichenfolge, die für die Schemanamen, Tabellenname und Spaltenname angegeben wurde, und die Datenquelle unterstützt nicht das Suchmuster für eine oder mehrere dieser Argumente.<br /><br /> Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird in der Regel vor der anweisungsausführung zum Abrufen von Informationen zu den Spalten für eine Tabelle oder Tabellen aus der Datenquelle des Katalogs verwendet. **SQLColumns** können verwendet werden, um das Abrufen von Daten für alle Typen von Elementen, die vom **SQLTables**. Neben der Basistabellen der Sicht, dies kann (ist aber nicht beschränkt auf) Ansichten, Synonyme, Systemtabellen und So weiter. Im Gegensatz dazu die Funktionen **SQLColAttribute** und **SQLDescribeCol** beschreiben die Spalten in einem Resultset und die Funktion **SQLNumResultCols** gibt die Anzahl der die Spalten in einem Resultset. Weitere Informationen finden Sie unter [von Katalogdaten verwendet](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLColumns** gibt die Ergebnisse als ein standard, geordnet nach TABLE_CAT, nach "TABLE_SCHEM", Tabellenname und ORDINAL_POSITION Resultset zurück.  
  
> [!NOTE]  
>  Wenn eine Anwendung mit einer ODBC 2. funktioniert. *x* -Treiber verwenden, wird keine ORDINAL_POSITION-Spalte im Resultset zurückgegeben. Als Ergebnis, bei der Arbeit mit ODBC 2. *x* Treiber, die Reihenfolge der Spalten in der Spaltenliste zurückgegebenes **SQLColumns** ist nicht unbedingt identisch mit der Reihenfolge der Spalten zurückgegeben, wenn die Anwendung eine SELECT-Anweisung für alle ausführt die Spalten in dieser Tabelle.  
  
> [!NOTE]  
>  **SQLColumns** möglicherweise nicht alle Spalten zurück. Beispielsweise kann ein Treiber nicht die Informationen zu Pseudo-Spalten, z. B. Oracle ROWID zurück. Anwendungen können gültige Spalte, verwenden Sie, ob sie von zurückgegeben wird **SQLColumns**.  
>   
>  Einige Spalten, die zurückgegeben werden können **SQLStatistics** werden nicht zurückgegeben **SQLColumns**. Z. B. **SQLColumns** kehrt die Spalten in einem Index erstellt, die über einen Ausdruck oder einen Filter, z. B. Gehalt "+" Vorteile "oder" DEPT = 0012.  
  
 Die Länge der VARCHAR-Spalten werden nicht in der Tabelle angezeigt; die tatsächliche Länge hängt von der Datenquelle ab. Um zu bestimmen, die tatsächliche Länge der Spalten TABLE_CAT, nach "TABLE_SCHEM", Tabellenname und Spaltenname, eine Anwendung aufrufen kann **SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN, und SQL_MAX_COLUMN_NAME_LEN-Optionen.  
  
 Die folgenden Spalten wurden umbenannt, ODBC 3. *x*. Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC 3. *x* Spalte|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Die folgenden Spalten wurden zurückgegebenes Resultset hinzugefügt **SQLColumns** ODBC 3. *X*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 18 (IS_NULLABLE) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifischen Spalten erhalten, indem nach unten am Ende des Resultsets anstatt einer expliziten Ordinalposition zählen. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spalte<br /><br /> number|Datentyp|Kommentare|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Name des Katalogs; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Kataloge für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, denen keine Kataloge.|  
|NACH "TABLE_SCHEM" (ODBC 1.0)|2|Varchar|Schemanamen; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Schemas für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, die keine Schemas aufweisen.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar, die nicht NULL|Tabellenname.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar, die nicht NULL|Name der Spalte. Der Treiber gibt eine leere Zeichenfolge für eine Spalte, die nicht über einen Namen verfügt.|  
|DATA_TYPE (ODBC 1.0)|5|Smallint nicht NULL|SQL-Datentyp. Dies kann einen ODBC-SQL-Datentyp oder die treiberspezifischen SQL-Datentyp sein. Bei "DateTime" "und" Interval-Datentypen gibt diese Spalte den präzisen Datentyp (z. B. SQL_TYPE_DATE oder SQL_INTERVAL_YEAR_TO_MONTH, anstatt die nonconcise Datentyp z. B. SQL_DATETIME oder SQL_INTERVAL) zurück. Eine Liste der gültigen ODBC-SQL-Datentypen, finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu Treiber-spezifische SQL-Datentypen finden Sie in der vom Treiber-Dokumentation.<br /><br /> Die Datentypen für ODBC 3 zurückgegeben. *x* und ODBC-2. *X* Anwendungen können unterschiedlich sein. Weitere Informationen finden Sie unter [Abwärtskompatibilität und zur Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|TYPE_NAME (ODBC 1.0)|6|Varchar, die nicht NULL|Daten Datenquelle abhängiger Datentypname; "z. B. CHAR", "VARCHAR", "MONEY", "LONG VARBINAR" oder "CHAR () für BIT-Daten".|  
|COLUMN_SIZE (ODBC 1.0)|7|Integer|Wenn DATA_TYPE SQL_CHAR oder SQL_VARCHAR sein wird, enthält diese Spalte die maximale Länge in Zeichen der Spalte an. Für Datetime-Datentypen ist dies die Gesamtzahl der Zeichen, die erforderlich sind, um den Wert anzuzeigen, wenn es in Zeichen konvertiert wird. Für numerische Datentypen ist dies entweder die Gesamtanzahl von Ziffern oder die Gesamtanzahl von Bits, die in der Spalte zulässig gemäß der NUM_PREC_RADIX-Spalte. Für die Interval-Datentypen, ist dies die Anzahl der Zeichen in die Darstellung der das Intervall literal (gemäß der Genauigkeit für anführenden Intervallwert, finden Sie unter [Datentyplänge Intervall](../../../odbc/reference/appendixes/interval-data-type-length.md) in Anhang D: Die Datentypen). Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|DIE BUFFER_LENGTH (ODBC 1.0)|8|Integer|Die Länge in Bytes der Daten, die auf einen Vorgang SQLGetData, SQLFetch oder SQLFetchScroll übertragen werden, wenn SQL_C_DEFAULT angegeben wird. Für numerische Daten kann die Größe der in der Datenquelle gespeicherten Daten diese Größe unterscheiden. Dieser Wert kann von COLUMN_SIZE-Spalte für Daten im Zeichenformat abweichen. Weitere Informationen zu Länge, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|DIE DECIMAL_DIGITS (ODBC 1.0)|9|Smallint|Die Gesamtanzahl der Ziffern rechts vom Dezimaltrennzeichen an. SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP enthält diese Spalte die Anzahl der Ziffern in der Komponente für Sekundenbruchteile. Für die anderen Datentypen ist dies die Dezimalstellen der Spalte in der Datenquelle. Für die Interval-Datentypen, die eine Komponente enthalten, enthält diese Spalte die Anzahl der Ziffern rechts vom Dezimaltrennzeichen an (Sekundenbruchteile). Für die Interval-Datentypen, die keine Zeitangabe enthalten, ist diese Spalte 0. Weitere Informationen zu Dezimalstellen, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen. NULL wird für Datentypen zurückgegeben, in dem kein DECIMAL_DIGITS anwendbar.|  
|NUM_PREC_RADIX (ODBC 1.0)|10|Smallint|Für numerische Datentypen entweder "10" oder "2. Wenn es 10 ist, geben Sie die Werte in der COLUMN_SIZE- und DECIMAL_DIGITS die Anzahl der Dezimalstellen für die Spalte zulässig sind. Beispielsweise würde ein NUM_PREC_RADIX von 10 und eine COLUMN_SIZE 12, ein DECIMAL_DIGITS 5 eine DECIMAL(12,5)-Spalte zurückgegeben wird. eine Spalte "float" konnte eine NUM_PREC_RADIX von 10 und eine COLUMN_SIZE 15 DECIMAL_DIGITS von NULL zurückgeben.<br /><br /> Wenn sie auf "2" ist, geben Sie die Werte in der COLUMN_SIZE- und DECIMAL_DIGITS die Anzahl der Bits, die in der Spalte zulässig. Eine "float"-Spalte kann z. B. eine Basis von 2 ist, eine COLUMN_SIZE 53 und DECIMAL_DIGITS von NULL zurückgegeben.<br /><br /> NULL wird für Datentypen zurückgegeben, in dem kein NUM_PREC_RADIX anwendbar.|  
|NULL-WERTE ZULÄSST (ODBC 1.0)|11|Smallint nicht NULL|SQL_NO_NULLS, wenn die Spalte keine NULL-Werte einschließen kann.<br /><br /> SQL_NULLABLE, wenn die Spalte NULL-Werte akzeptiert.<br /><br /> SQL_NULLABLE_UNKNOWN, wenn nicht bekannt ist, ob die Spalte NULL-Werte annimmt.<br /><br /> Für diese Spalte zurückgegebene Wert unterscheidet sich von der für die Spalte IS_NULLABLE zurückgegebene Wert. Die NULLABLE-Spalte gibt an, mit Bestimmtheit, dass eine Spalte NULL-Werte akzeptiert, aber nicht unbedingt sicher, dass eine Spalte keine NULL-Werte akzeptiert angeben. Die Spalte IS_NULLABLE gibt an, mit Bestimmtheit, dass eine Spalte kann keine NULL-Werte akzeptieren, aber nicht unbedingt sicher, dass eine Spalte NULL-Werte akzeptiert angeben.|  
|HINWEISE (ODBC 1.0)|12|Varchar|Eine Beschreibung der Spalte.|  
|COLUMN_DEF (ODBC 3.0)|13|Varchar|Der Standardwert der Spalte. Der Wert in dieser Spalte muss als Zeichenfolge interpretiert werden, wenn er in Anführungszeichen eingeschlossen ist.<br /><br /> Wenn NULL als Standardwert angegeben wurde, ist diese Spalte das Wort NULL ist, nicht in Anführungszeichen eingeschlossen. Wenn der Standardwert ungekürzt dargestellt werden kann, enthält diese Spalte abgeschnitten, ohne die Anführungszeichen einschließen. Wenn kein Standardwert angegeben wurde, ist diese Spalte NULL.<br /><br /> Der Wert des COLUMN_DEF dienen zum Generieren einer neuen Spaltendefinition, außer, wenn der Wert abgeschnitten enthalten.|  
|SQL_DATA_TYPE (ODBC 3.0)|14|Smallint nicht NULL|SQL-Datentyp, wie er im Feld Datensatz SQL_DESC_TYPE in IRD angezeigt wird. Dies kann einen ODBC-SQL-Datentyp oder die treiberspezifischen SQL-Datentyp sein. Diese Spalte entspricht der DATA_TYPE-Spalte, mit Ausnahme von "DateTime" "und" Interval-Datentypen. Diese Spalte gibt den nonconcise Datentyp (z. B. SQL_DATETIME oder SQL_INTERVAL), anstelle des präzisen Datentyp (z. B. SQL_TYPE_DATE oder SQL_INTERVAL_YEAR_TO_MONTH) für "DateTime" und die Interval-Datentypen zurück. Wenn diese Spalte SQL_DATETIME oder SQL_INTERVAL zurückgibt, kann im speziellen Datentyp aus der Spalte noch SQL_DATETIME_SUB ermittelt werden. Eine Liste der gültigen ODBC-SQL-Datentypen, finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu Treiber-spezifische SQL-Datentypen finden Sie in der vom Treiber-Dokumentation.<br /><br /> Die Datentypen für ODBC 3 zurückgegeben. *x* und ODBC-2. *X* Anwendungen können unterschiedlich sein. Weitere Informationen finden Sie unter [Abwärtskompatibilität und zur Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|NOCH SQL_DATETIME_SUB (ODBC 3.0)|15|Smallint|Der Untertypcode für Datetime "und" Interval-Datentypen. Für andere Datentypen gibt diese Spalte einen NULL-Wert zurück. Weitere Informationen zu Datetime "und" Interval Untercodes, finden Sie unter "SQL_DESC_DATETIME_INTERVAL_CODE" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|16|Integer|Die maximale Länge in Byte von einem Zeichen- oder Binärdaten-Datentypspalte. Bei allen anderen Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|ORDINAL_POSITION (ODBC 3.0)|17|Integer nicht NULL|Die Ordnungsposition einer Spalte innerhalb der Tabelle. Die erste Spalte in der Tabelle ist die Zahl 1.|  
|IS_NULLABLE (ODBC 3.0)|18|Varchar|"Nein", wenn die Spalte keine NULL-Werte enthält.<br /><br /> "YES", wenn die Spalte NULL-Werte einschließen kann.<br /><br /> Die Spalte gibt eine leere Zeichenfolge zurück, wenn die NULL-Zulässigkeit unbekannt ist.<br /><br /> Die NULL-Zulässigkeit wird gemäß den ISO-Regeln bestimmt. Ein DBMS nach ISO SQL kann keine leere Zeichenfolge zurückgeben.<br /><br /> Für diese Spalte zurückgegebene Wert unterscheidet sich von der für die NULLABLE-Spalte zurückgegebene Wert. (Siehe die Beschreibung der Spalte NULL-Werte zulässt.)|  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel deklariert eine Anwendung Puffer für das Resultset zurückgegebenes **SQLColumns**. Ruft **SQLColumns** zur Beschreibung der jede Spalte in der EMPLOYEE-Tabelle ein Resultset zurückgegeben. Es ruft dann **SQLBindCol** zum Binden der Spalten im Resultset den Puffern. Schließlich die Anwendung ruft jede Zeile von Daten mit **SQLFetch** und verarbeitet es.  
  
```  
// SQLColumns_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#define STR_LEN 128 + 1  
#define REM_LEN 254 + 1  
  
// Declare buffers for result set data  
SQLCHAR szSchema[STR_LEN];  
SQLCHAR szCatalog[STR_LEN];  
SQLCHAR szColumnName[STR_LEN];  
SQLCHAR szTableName[STR_LEN];  
SQLCHAR szTypeName[STR_LEN];  
SQLCHAR szRemarks[REM_LEN];  
SQLCHAR szColumnDefault[STR_LEN];  
SQLCHAR szIsNullable[STR_LEN];  
  
SQLINTEGER ColumnSize;  
SQLINTEGER BufferLength;  
SQLINTEGER CharOctetLength;  
SQLINTEGER OrdinalPosition;  
  
SQLSMALLINT DataType;  
SQLSMALLINT DecimalDigits;  
SQLSMALLINT NumPrecRadix;  
SQLSMALLINT Nullable;  
SQLSMALLINT SQLDataType;  
SQLSMALLINT DatetimeSubtypeCode;  
  
SQLHSTMT hstmt = NULL;  
  
// Declare buffers for bytes available to return  
SQLINTEGER cbCatalog;  
SQLINTEGER cbSchema;  
SQLINTEGER cbTableName;  
SQLINTEGER cbColumnName;  
SQLINTEGER cbDataType;  
SQLINTEGER cbTypeName;  
SQLINTEGER cbColumnSize;  
SQLLEN cbBufferLength;  
SQLINTEGER cbDecimalDigits;  
SQLINTEGER cbNumPrecRadix;  
SQLINTEGER cbNullable;  
SQLINTEGER cbRemarks;  
SQLINTEGER cbColumnDefault;  
SQLINTEGER cbSQLDataType;  
SQLINTEGER cbDatetimeSubtypeCode;  
SQLINTEGER cbCharOctetLength;  
SQLINTEGER cbOrdinalPosition;  
SQLINTEGER cbIsNullable;  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retcode = SQLColumns(hstmt, NULL, 0, NULL, 0, (SQLCHAR*)"CUSTOMERS", SQL_NTS, NULL, 0);  
  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      // Bind columns in result set to buffers  
      SQLBindCol(hstmt, 1, SQL_C_CHAR, szCatalog, STR_LEN,&cbCatalog);  
      SQLBindCol(hstmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &cbSchema);  
      SQLBindCol(hstmt, 3, SQL_C_CHAR, szTableName, STR_LEN,&cbTableName);  
      SQLBindCol(hstmt, 4, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);  
      SQLBindCol(hstmt, 5, SQL_C_SSHORT, &DataType, 0, &cbDataType);  
      SQLBindCol(hstmt, 6, SQL_C_CHAR, szTypeName, STR_LEN, &cbTypeName);  
      SQLBindCol(hstmt, 7, SQL_C_SLONG, &ColumnSize, 0, &cbColumnSize);  
      SQLBindCol(hstmt, 8, SQL_C_SLONG, &BufferLength, 0, &cbBufferLength);  
      SQLBindCol(hstmt, 9, SQL_C_SSHORT, &DecimalDigits, 0, &cbDecimalDigits);  
      SQLBindCol(hstmt, 10, SQL_C_SSHORT, &NumPrecRadix, 0, &cbNumPrecRadix);  
      SQLBindCol(hstmt, 11, SQL_C_SSHORT, &Nullable, 0, &cbNullable);  
      SQLBindCol(hstmt, 12, SQL_C_CHAR, szRemarks, REM_LEN, &cbRemarks);  
      SQLBindCol(hstmt, 13, SQL_C_CHAR, szColumnDefault, STR_LEN, &cbColumnDefault);  
      SQLBindCol(hstmt, 14, SQL_C_SSHORT, &SQLDataType, 0, &cbSQLDataType);  
      SQLBindCol(hstmt, 15, SQL_C_SSHORT, &DatetimeSubtypeCode, 0, &cbDatetimeSubtypeCode);  
      SQLBindCol(hstmt, 16, SQL_C_SLONG, &CharOctetLength, 0, &cbCharOctetLength);  
      SQLBindCol(hstmt, 17, SQL_C_SLONG, &OrdinalPosition, 0, &cbOrdinalPosition);  
      SQLBindCol(hstmt, 18, SQL_C_CHAR, szIsNullable, STR_LEN, &cbIsNullable);  
  
      while (SQL_SUCCESS == retcode) {  
         retcode = SQLFetch(hstmt);  
         /*  
         if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // show_error();  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // Process fetched data  
         else  
            break;  
        */  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Berechtigungen für eine oder mehrere Spalten|[SQLColumnPrivileges-Funktion](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen mehrerer Zeilen von Daten|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Zurückgeben von Spalten, die eine Zeile eindeutig zu identifizieren oder Spalten, die durch eine Transaktion automatisch aktualisiert.|[SQLSpecialColumns-Funktion](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|Zurückgeben von Statistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Zurückgeben einer Liste von Tabellen in einer Datenquelle|[SQLTables-Funktion](../../../odbc/reference/syntax/sqltables-function.md)|  
|Zurückgeben von Berechtigungen für eine Tabelle oder Tabellen|[SQLTablePrivileges-Funktion](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
