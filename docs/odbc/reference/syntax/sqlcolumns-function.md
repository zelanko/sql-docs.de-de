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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36293c1f2393e9a57351fc8cd19dcc6e3338f5cc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301256"
---
# <a name="sqlcolumns-function"></a>SQLColumns-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: Open Group  
  
 **Zusammenfassung**  
 **SQLColumns** gibt die Liste der Spaltennamen in angegebenen Tabellen zurück. Der Treiber gibt diese Informationen als Resultset für das angegebene *StatementHandle*zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
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
 Der Anweisungs Handle.  
  
 *CatalogName*  
 Der Katalog Name. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die nicht über Kataloge verfügen. *CatalogName* darf kein Zeichen folgen-Suchmuster enthalten.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *CatalogName* ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Der Länge in Zeichen von **CatalogName*.  
  
 *Schema Name*  
 Der Zeichen folgen Suchmuster für Schema Namen. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas aufweisen.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird Schema *Name* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist Schema *Name* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength2*  
 Der Länge in Zeichen von * Schema*Name*.  
  
 *TableName*  
 Der Zeichen folgen Suchmuster für Tabellennamen.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *TableName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *TableName* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength3*  
 Der Länge in Zeichen von **TableName*.  
  
 *ColumnName*  
 Der Zeichen folgen Suchmuster für Spaltennamen.  
  
> [!NOTE]  
>  Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *ColumnName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *ColumnName* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength4*  
 Der Länge in Zeichen von **ColumnName*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLColumns** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLColumns** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor war auf dem *StatementHandle* geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde ein Rollback ausgeführt, weil ein Ressourcen Deadlock mit einer anderen Transaktion aufgetreten ist.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, das *CatalogName* -Argument war ein NULL-Zeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, *und das Schema*Name-, *TableName*-oder *ColumnName* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLColumns** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der Wert eines der namens Längen Argumente war kleiner als 0 (null), aber nicht gleich SQL_NTS.|  
|||Der Wert eines der namens Längen Argumente hat den maximalen Längen Wert für den entsprechenden Katalog oder Namen überschritten. Die maximale Länge jedes Katalogs oder Namens kann durch Aufrufen von **SQLGetInfo** mit den *InfoType* -Werten erreicht werden. (Siehe "Kommentare")|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Es wurde ein Katalog Name angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schema Name angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Für den Schema Namen, den Tabellennamen oder den Spaltennamen wurde ein Zeichen folgen Suchmuster angegeben, und die Datenquelle unterstützt keine Suchmuster für mindestens ein Argument.<br /><br /> Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird in der Regel vor der Anweisungs Ausführung verwendet, um Informationen über Spalten für eine Tabelle oder Tabellen aus dem Katalog der Datenquelle abzurufen. **SQLColumns** kann zum Abrufen von Daten für alle Typen von Elementen verwendet werden, die von **SQLTables**zurückgegeben werden. Zusätzlich zu den Basistabellen kann dies (aber nicht beschränkt auf) Sichten, Synonyme, Systemtabellen usw. enthalten. Im Gegensatz dazu beschreiben die Funktionen **SQLColAttribute** und **SQLDescribeCol** die Spalten in einem **Resultset, und die SQLNumResultCols** -Funktion gibt die Anzahl der Spalten in einem Resultset zurück. Weitere Informationen finden Sie unter [Verwenden von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumente und zurückgegebene Daten von ODBC-Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLColumns** gibt die Ergebnisse als Standardresultset zurück, geordnet nach TABLE_CAT, TABLE_SCHEM, TABLE_NAME und ORDINAL_POSITION.  
  
> [!NOTE]  
>  Wenn eine Anwendung mit einem ODBC 2 funktioniert. *x* -Treiber, es wird keine ORDINAL_POSITION Spalte im Resultset zurückgegeben. Dies hat zur Folge, dass Sie mit ODBC 2 arbeiten. *x* -Treiber: die Reihenfolge der Spalten in der von **SQLColumns** zurückgegebenen Spaltenliste ist nicht notwendigerweise identisch mit der Reihenfolge der Spalten, die zurückgegeben werden, wenn die Anwendung eine SELECT-Anweisung für alle Spalten in dieser Tabelle ausführt.  
  
> [!NOTE]  
>  **SQLColumns** gibt möglicherweise nicht alle Spalten zurück. Beispielsweise gibt ein Treiber möglicherweise keine Informationen zu Pseudo Spalten zurück, wie z. b. Oracle ROWID. Anwendungen können beliebige gültige Spalten verwenden, unabhängig davon, ob Sie von **SQLColumns**zurückgegeben werden.  
>   
>  Einige Spalten, die von **SQLStatistics** zurückgegeben werden können, werden von **SQLColumns**nicht zurückgegeben. **SQLColumns** gibt z. b. nicht die Spalten in einem Index zurück, der für einen Ausdruck oder Filter erstellt wurde, wie z. b. "Gehalt + Benefits" oder "TPT = 0012".  
  
 Die Längen von varchar-Spalten werden in der Tabelle nicht angezeigt. die tatsächlichen Längen hängen von der Datenquelle ab. Zum Bestimmen der tatsächlichen Längen der Spalten TABLE_CAT, TABLE_SCHEM, TABLE_NAME und column_name kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN aufrufen.  
  
 Die folgenden Spalten wurden für ODBC 3 umbenannt. *x*. Die Spaltennamen Änderungen wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer gebunden werden.  
  
|ODBC 2,0-Spalte|ODBC 3. *x* -Spalte|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Die folgenden Spalten wurden dem Resultset hinzugefügt, das von **SQLColumns** für ODBC 3 zurückgegeben wurde. *x*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 In der folgenden Tabelle werden die Spalten im Resultset aufgelistet. Zusätzliche Spalten, die über die Spalte 18 (IS_NULLABLE) hinausgehen, können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf Treiber spezifische Spalten erhalten, indem Sie vom Ende des Resultsets abzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Column<br /><br /> number|Datentyp|Kommentare|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1,0)|1|Varchar|Katalog Name; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Tabellen zurückgegeben, die über keine Kataloge verfügen.|  
|TABLE_SCHEM (ODBC 1,0)|2|Varchar|Schema Name; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für Tabellen zurückgegeben, die keine Schemas aufweisen.|  
|Table_name (ODBC 1,0)|3|Varchar not NULL|Tabellenname.|  
|Column_name (ODBC 1,0)|4|Varchar not NULL|Spaltenname. Der Treiber gibt eine leere Zeichenfolge für eine Spalte zurück, die über keinen Namen verfügt.|  
|Data_type (ODBC 1,0)|5|Smallint nicht NULL|SQL-Datentyp. Hierbei kann es sich um einen ODBC-SQL-Datentyp oder um einen treiberspezifischen SQL-Datentyp handeln. Für DateTime-und interval-Datentypen gibt diese Spalte den präzisen Datentyp (z. b. SQL_TYPE_DATE oder SQL_INTERVAL_YEAR_TO_MONTH anstelle des nicht präzisen Datentyps, z. b. SQL_DATETIME oder SQL_INTERVAL), zurück. Eine Liste der gültigen ODBC-SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.<br /><br /> Die Datentypen, die für ODBC 3 zurückgegeben werden. *x* und ODBC 2. *x* -Anwendungen können unterschiedlich sein. Weitere Informationen finden Sie unter abwärts [Kompatibilität und Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|Type_name (ODBC 1,0)|6|Varchar not NULL|Datenquellen abhängiger Datentyp Name; Beispiel: "char", "varchar", "Money", "Long varbinar" oder "char () for Bit Data".|  
|COLUMN_SIZE (ODBC 1,0)|7|Integer|Wenn data_type SQL_CHAR oder SQL_VARCHAR ist, enthält diese Spalte die maximale Länge der Spalte in Zeichen. Bei datetime-Datentypen ist dies die Gesamtzahl der Zeichen, die erforderlich sind, um den Wert beim Konvertieren in Zeichen anzuzeigen. Bei numerischen Datentypen entspricht dies entweder der Gesamtanzahl der Ziffern oder der Gesamtzahl der in der Spalte zulässigen Bits gemäß der NUM_PREC_RADIX Spalte. Bei interval-Datentypen ist dies die Anzahl der Zeichen in der Zeichen Darstellung des intervallliterals (wie durch die vorangehende Genauigkeit von Intervallen definiert). Weitere Informationen finden Sie unter [Intervall Datentyp Länge](../../../odbc/reference/appendixes/interval-data-type-length.md) in Anhang D: Datentypen. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|BUFFER_LENGTH (ODBC 1,0)|8|Integer|Die Länge der Daten in Bytes, die auf einen SQLGetData-, SQLFetch-oder SQLFetchScroll-Vorgang übertragen werden, wenn SQL_C_DEFAULT angegeben wird. Bei numerischen Daten unterscheidet sich diese Größe möglicherweise von der Größe der Daten, die in der Datenquelle gespeichert sind. Dieser Wert kann sich von COLUMN_SIZE Spalte für Zeichendaten unterscheiden. Weitere Informationen über die Länge finden Sie unter [Spaltengröße, Dezimalstellen, Länge von Oktett übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|DECIMAL_DIGITS (ODBC 1,0)|9|Smallint|Die Gesamtanzahl der signifikanten Ziffern rechts vom Dezimaltrennzeichen. Bei SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP enthält diese Spalte die Anzahl der Ziffern in der Komponente für Sekundenbruchteile. Bei den anderen Datentypen handelt es sich hierbei um die Dezimalstellen der Spalte in der Datenquelle. Für Intervall Datentypen, die eine Zeitkomponente enthalten, enthält diese Spalte die Anzahl der Ziffern rechts vom Dezimaltrennzeichen (Sekundenbruchteile). Für Intervall Datentypen, die keine Zeitkomponente enthalten, ist diese Spalte 0. Weitere Informationen zu Dezimalziffern finden Sie unter [Spaltengröße, Dezimalstellen, Länge des Oktetts übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen. NULL wird für Datentypen zurückgegeben, bei denen DECIMAL_DIGITS nicht anwendbar ist.|  
|NUM_PREC_RADIX (ODBC 1,0)|10|Smallint|Für numerische Datentypen, entweder 10 oder 2. Wenn der Wert 10 ist, gibt die Werte in COLUMN_SIZE und DECIMAL_DIGITS die Anzahl der für die Spalte zulässigen Dezimalstellen an. Beispielsweise würde eine dezimale Spalte (12, 5) eine NUM_PREC_RADIX von 10, eine COLUMN_SIZE von 12 und eine DECIMAL_DIGITS von 5 zurückgeben. eine float-Spalte kann eine NUM_PREC_RADIX von 10, eine COLUMN_SIZE 15 und eine DECIMAL_DIGITS NULL zurückgeben.<br /><br /> Wenn der Wert 2 ist, haben die Werte in COLUMN_SIZE und DECIMAL_DIGITS die Anzahl der in der Spalte zulässigen Bits. Eine float-Spalte könnte z. b. ein Radix von 2, eine COLUMN_SIZE von 53 und eine DECIMAL_DIGITS NULL zurückgeben.<br /><br /> NULL wird für Datentypen zurückgegeben, bei denen NUM_PREC_RADIX nicht anwendbar ist.|  
|Nullable (ODBC 1,0)|11|Smallint nicht NULL|SQL_NO_NULLS, wenn die Spalte keine NULL-Werte enthalten darf.<br /><br /> SQL_NULLABLE, wenn die Spalte NULL-Werte akzeptiert.<br /><br /> SQL_NULLABLE_UNKNOWN, wenn nicht bekannt ist, ob die Spalte NULL-Werte akzeptiert.<br /><br /> Der für diese Spalte zurückgegebene Wert unterscheidet sich von dem Wert, der für die IS_NULLABLE Spalte zurückgegeben wurde. Die Nullable-Spalte gibt mit Sicherheit an, dass eine Spalte NULL-Werte akzeptieren kann, aber nicht mit Sicherheit angeben kann, dass eine Spalte keine NULL-Werte akzeptiert. Die Spalte IS_NULLABLE gibt mit Sicherheit an, dass eine Spalte keine NULL-Werten annehmen kann, aber nicht mit der Gewissheit angeben kann, dass eine Spalte NULL-Werten akzeptiert.|  
|Hinweise (ODBC 1,0)|12|Varchar|Eine Beschreibung der Spalte.|  
|COLUMN_DEF (ODBC 3,0)|13|Varchar|Der Standardwert der Spalte. Der Wert in dieser Spalte sollte als Zeichenfolge interpretiert werden, wenn er in Anführungszeichen eingeschlossen ist.<br /><br /> Wenn NULL als Standardwert angegeben wurde, ist diese Spalte das Wort NULL und nicht in Anführungszeichen eingeschlossen. Wenn der Standardwert nicht ohne Abschneiden dargestellt werden kann, enthält diese Spalte abgeschnitten, ohne einfache Anführungszeichen einzuschließen. Wenn kein Standardwert angegeben wurde, ist diese Spalte NULL.<br /><br /> Der Wert COLUMN_DEF kann verwendet werden, um eine neue Spaltendefinition zu erstellen, außer wenn Sie den abgeschnittene Wert enthält.|  
|SQL_DATA_TYPE (ODBC 3,0)|14|Smallint nicht NULL|SQL-Datentyp, wie er im Feld SQL_DESC_TYPE Datensatz im IRD angezeigt wird. Hierbei kann es sich um einen ODBC-SQL-Datentyp oder um einen treiberspezifischen SQL-Datentyp handeln. Diese Spalte ist mit Ausnahme der Datentypen datetime und Interval identisch mit der Spalte data_type. Diese Spalte gibt den nicht präzisen Datentyp (z. b. SQL_DATETIME oder SQL_INTERVAL) anstelle des präzisen Datentyps (z. b. SQL_TYPE_DATE oder SQL_INTERVAL_YEAR_TO_MONTH) für DateTime-und interval-Datentypen zurück. Wenn diese Spalte SQL_DATETIME oder SQL_INTERVAL zurückgibt, kann der spezifische Datentyp aus der SQL_DATETIME_SUB Spalte ermittelt werden. Eine Liste der gültigen ODBC-SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.<br /><br /> Die Datentypen, die für ODBC 3 zurückgegeben werden. *x* und ODBC 2. *x* -Anwendungen können unterschiedlich sein. Weitere Informationen finden Sie unter abwärts [Kompatibilität und Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|SQL_DATETIME_SUB (ODBC 3,0)|15|Smallint|Der Untertyp Code für DateTime-und interval-Datentypen. Für andere Datentypen gibt diese Spalte einen NULL-Wert zurück. Weitere Informationen zu DateTime-und Interval-Subcodes finden Sie unter "SQL_DESC_DATETIME_INTERVAL_CODE" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).|  
|CHAR_OCTET_LENGTH (ODBC 3,0)|16|Integer|Die maximale Länge in Bytes für eine Zeichen-oder Binär Datentyp Spalte. Bei allen anderen Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|ORDINAL_POSITION (ODBC 3,0)|17|Integer nicht NULL|Die Ordnungsposition einer Spalte innerhalb der Tabelle. Die erste Spalte in der Tabelle ist Nummer 1.|  
|IS_NULLABLE (ODBC 3,0)|18|Varchar|"No", wenn die Spalte keine Nullen enthält.<br /><br /> "Yes", wenn die Spalte NULL-Werten enthalten könnte.<br /><br /> Die Spalte gibt eine leere Zeichenfolge zurück, wenn die NULL-Zulässigkeit unbekannt ist.<br /><br /> Die NULL-Zulässigkeit wird gemäß den ISO-Regeln bestimmt. Ein DBMS nach ISO SQL kann keine leere Zeichenfolge zurückgeben.<br /><br /> Der für diese Spalte zurückgegebene Wert unterscheidet sich von dem für die Nullable-Spalte zurückgegebenen Wert. (Siehe die Beschreibung der Spalte, die NULL-Werte zulässt.)|  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel deklariert eine Anwendung Puffer für das von **SQLColumns**zurückgegebene Resultset. Es wird **SQLColumns** aufgerufen, um ein Resultset zurückzugeben, das jede Spalte in der Employee-Tabelle beschreibt. Anschließend wird **SQLBindCol** aufgerufen, um die Spalten im Resultset an die Puffer zu binden. Schließlich ruft die Anwendung jede Daten Zeile mit **SQLFetch** ab und verarbeitet sie.  
  
```cpp  
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
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Berechtigungen für eine Spalte oder Spalten|[SQLColumnPrivileges-Funktion](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen mehrerer Daten Zeilen|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Zurückgeben von Spalten, die eine Zeile eindeutig identifizieren, oder Spalten, die automatisch durch eine Transaktion aktualisiert werden|[SQLSpecialColumns-Funktion](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|Zurückgeben von Tabellenstatistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Zurückgeben einer Liste von Tabellen in einer Datenquelle|[SQLTables-Funktion](../../../odbc/reference/syntax/sqltables-function.md)|  
|Zurückgeben von Berechtigungen für eine Tabelle oder Tabellen|[SQLTablePrivileges-Funktion](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
