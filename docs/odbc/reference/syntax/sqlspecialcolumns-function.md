---
title: SQLSpecialColumns-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSpecialColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSpecialColumns
helpviewer_keywords:
- SQLSpecialColumns function [ODBC]
ms.assetid: bb2d9f21-bda0-4e50-a8be-f710db660034
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 826630e1d344322268a2f2638310b3a1e182de6d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287170"
---
# <a name="sqlspecialcolumns-function"></a>SQLSpecialColumns-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: Open Group  
  
 **Zusammenfassung**  
 **SQLSpecialColumns** Ruft die folgenden Informationen zu Spalten in einer angegebenen Tabelle ab:  
  
-   Die optimale Gruppe von Spalten, die eine Zeile in der Tabelle eindeutig identifiziert.  
  
-   Spalten, die automatisch aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion aktualisiert wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSpecialColumns(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   IdentifierType,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3,  
     SQLSMALLINT   Scope,  
     SQLSMALLINT   Nullable);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *IdentifierType*  
 Der Der Typ der zurück zugebende Spalte. Dies muss einer der folgenden Werte sein:  
  
 SQL_BEST_ROWID: gibt die optimale Spalte oder Gruppe von Spalten zurück, die durch das Abrufen von Werten aus der Spalte oder den Spalten das eindeutige identifizieren jeder Zeile in der angegebenen Tabelle ermöglicht. Eine Spalte kann entweder eine Pseudo Spalte sein, die speziell für diesen Zweck entworfen wurde (wie in Oracle ROWID oder Ingres TID), oder die Spalte bzw. Spalten eines eindeutigen Indexes für die Tabelle.  
  
 SQL_ROWVER: gibt ggf. die Spalte oder die Spalten in der angegebenen Tabelle zurück, die automatisch von der Datenquelle aktualisiert werden, wenn ein Wert in der Zeile durch eine beliebige Transaktion (wie in SQLBase ROWID oder Sybase-Zeitstempel) aktualisiert wird.  
  
 *CatalogName*  
 Der Der Katalog Name für die Tabelle. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die nicht über Kataloge verfügen. *CatalogName* darf kein Zeichen folgen-Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *CatalogName* ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Der Länge in Zeichen von **CatalogName*.  
  
 *Schema Name*  
 Der Der Name des Schemas für die Tabelle. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas aufweisen. Schema *Name* darf kein Zeichen folgen-Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird Schema *Name* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist Schema *Name* ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength2*  
 Der Länge in Zeichen von * Schema*Name*.  
  
 *TableName*  
 Der Tabellenname. Dieses Argument darf kein NULL-Zeiger sein. " *TableName* " darf kein Zeichen folgen Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *TableName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *TableName* ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength3*  
 Der Länge in Zeichen von **TableName*.  
  
 *Umfang*  
 Der Mindestens erforderlicher Bereich der ROWID. Die zurückgegebene ROWID kann einen größeren Bereich aufweisen. Dies muss eine der folgenden Ressourcen sein:  
  
 SQL_SCOPE_CURROW: die ROWID ist garantiert nur gültig, wenn Sie in dieser Zeile positioniert ist. Eine spätere erneute Auswahl mithilfe von ROWID gibt möglicherweise keine Zeile zurück, wenn die Zeile von einer anderen Transaktion aktualisiert oder gelöscht wurde.  
  
 SQL_SCOPE_TRANSACTION: für die Dauer der aktuellen Transaktion ist sichergestellt, dass die ROWID gültig ist.  
  
 SQL_SCOPE_SESSION: die ROWID ist gewährleistet, dass die Sitzung für die Dauer der Sitzung (über Transaktionsgrenzen hinweg) gültig ist.  
  
 *NULL zulassen*  
 Der Bestimmt, ob spezielle Spalten zurückgegeben werden, die einen NULL-Wert aufweisen können. Dies muss eine der folgenden Ressourcen sein:  
  
 SQL_NO_NULLS: schließt spezielle Spalten aus, die NULL-Werte aufweisen können. Einige Treiber können SQL_NO_NULLS nicht unterstützen, und diese Treiber geben ein leeres Resultset zurück, wenn SQL_NO_NULLS angegeben wurde. Anwendungen sollten für diesen Fall vorbereitet werden, und SQL_NO_NULLS nur dann anfordern, wenn dies unbedingt erforderlich ist.  
  
 SQL_NULLABLE: gibt spezielle Spalten zurück, auch wenn Sie NULL-Werte aufweisen können.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSpecialColumns** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLSpecialColumns** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben wurde und vom Treiber zurückgegeben wird, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor war auf dem *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde aufgrund eines Ressourcen Deadlocks mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das *TableName* -Argument war ein NULL-Zeiger.<br /><br /> Das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, das *CatalogName* -Argument war ein NULL-Zeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, und das Schema *Name* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese Funktion wurde noch ausgeführt, als **SQLSpecialColumns** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der Wert eines Längen Arguments ist kleiner als 0 (null), aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der Längen Argumente hat den maximalen Längen Wert für den entsprechenden Namen überschritten. Die maximale Länge jedes namens kann durch Aufrufen von **SQLGetInfo** mit den *InfoType* -Werten erreicht werden: SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN oder SQL_MAX_TABLE_NAME_LEN.|  
|HY097|Spaltentyp außerhalb des gültigen Bereichs|(DM) Es wurde ein ungültiger *IdentifierType* -Wert angegeben.|  
|HY098|Bereichstyp außerhalb des gültigen Bereichs|(DM) Es wurde ein ungültiger *Bereichs* Wert angegeben.|  
|HY099|Nullable-Typ außerhalb des gültigen Bereichs|(DM) ein ungültiger *Nullable* -Wert wurde angegeben.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Es wurde ein Katalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Wenn das *IdentifierType* -Argument SQL_BEST_ROWID ist, gibt **SQLSpecialColumns** die Spalten zurück, die jede Zeile in der Tabelle eindeutig identifizieren. Diese Spalten können immer in einer *Select-List-* Klausel oder **Where** -Klausel verwendet werden. **SQLColumns**, das verwendet wird, um eine Vielzahl von Informationen über die Spalten einer Tabelle zurückzugeben, gibt nicht notwendigerweise die Spalten zurück, die jede Zeile eindeutig identifizieren, oder Spalten, die automatisch aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion aktualisiert wird. Beispielsweise gibt **SQLColumns** möglicherweise nicht die Oracle-Pseudo Spalten-ROWID zurück. Aus diesem Grund werden **SQLSpecialColumns** verwendet, um diese Spalten zurückzugeben. Weitere Informationen finden Sie unter [Verwenden von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumente und zurückgegebene Daten von ODBC-Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Wenn keine Spalten vorhanden sind, die jede Zeile in der Tabelle eindeutig identifizieren, gibt **SQLSpecialColumns** ein Rowset ohne Zeilen zurück. bei einem nachfolgenden Aufrufs von **SQLFetch** oder **SQLFetchScroll** in der-Anweisung wird SQL_NO_DATA zurückgegeben.  
  
 Wenn die Argumente *IdentifierType*, *Scope*oder *Nullable* Merkmale angeben, die von der Datenquelle nicht unterstützt werden, gibt **SQLSpecialColumns** ein leeres Resultset zurück.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, werden die Argumente *CatalogName* *, Schema*Name und *TableName* als Bezeichner behandelt, sodass Sie in bestimmten Situationen nicht auf einen NULL-Zeiger festgelegt werden können. (Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).)  
  
 **SQLSpecialColumns** gibt die Ergebnisse als Standardresultset zurück, geordnet nach Bereich.  
  
 Die folgenden Spalten wurden für ODBC *3. x*umbenannt. Die Spaltennamen Änderungen wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer gebunden werden.  
  
|ODBC 2,0-Spalte|ODBC *3. x* -Spalte|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
  
 Um die tatsächliche Länge der COLUMN_NAME Spalte zu bestimmen, kann eine Anwendung **SQLGetInfo** mit der SQL_MAX_COLUMN_NAME_LEN-Option aufrufen.  
  
 In der folgenden Tabelle werden die Spalten im Resultset aufgelistet. Zusätzliche Spalten, die über die Spalte 8 (PSEUDO_COLUMN) hinausgehen, können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf Treiber spezifische Spalten erhalten, indem Sie vom Ende des Resultsets abzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|Bereich (ODBC 1,0)|1|Smallint|Tatsächlicher Bereich der ROWID. Enthält einen der folgenden Werte:<br /><br /> SQL_SCOPE_CURROW SQL_SCOPE_TRANSACTION SQL_SCOPE_SESSION<br /><br /> NULL wird zurückgegeben, wenn *IdentifierType* SQL_ROWVER ist. Eine Beschreibung der einzelnen Werte finden Sie in der Beschreibung des *Bereichs* unter "Syntax" weiter oben in diesem Abschnitt.|  
|Column_name (ODBC 1,0)|2|Varchar not NULL|Spaltenname. Der Treiber gibt eine leere Zeichenfolge für eine Spalte zurück, die über keinen Namen verfügt.|  
|Data_type (ODBC 1,0)|3|Smallint nicht NULL|SQL-Datentyp. Hierbei kann es sich um einen ODBC-SQL-Datentyp oder um einen treiberspezifischen SQL-Datentyp handeln. Eine Liste der gültigen ODBC-SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md). Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.|  
|Type_name (ODBC 1,0)|4|Varchar not NULL|Datenquellen abhängiger Datentyp Name; Beispiel: "char", "varchar", "Money", "Long varbinary" oder "char () for Bit Data".|  
|COLUMN_SIZE (ODBC 1,0)|5|Integer|Die Größe der Spalte in der Datenquelle. Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalstellen, Länge von Oktett übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|BUFFER_LENGTH (ODBC 1,0)|6|Integer|Die Länge der Daten in Bytes, die für einen **SQLGetData** -oder **SQLFetch** -Vorgang übertragen werden, wenn SQL_C_DEFAULT angegeben wird. Bei numerischen Daten unterscheidet sich diese Größe möglicherweise von der Größe der Daten, die in der Datenquelle gespeichert sind. Dieser Wert ist identisch mit dem COLUMN_SIZE Spalte für Zeichen-oder Binärdaten. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|DECIMAL_DIGITS (ODBC 1,0)|7|Smallint|Die Dezimalstellen der Spalte in der Datenquelle. NULL wird für Datentypen zurückgegeben, bei denen keine Dezimalstellen anwendbar sind. Weitere Informationen zu Dezimalziffern finden Sie unter [Spaltengröße, Dezimalstellen, Länge von Oktett übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|PSEUDO_COLUMN (ODBC 2,0)|8|Smallint|Gibt an, ob die Spalte eine Pseudo Spalte ist, z. b. "Oracle ROWID":<br /><br /> SQL_PC_UNKNOWN SQL_PC_NOT_PSEUDO SQL_PC_PSEUDO **Hinweis:** zur maximalen Interoperabilität sollten Pseudo Spalten nicht mit dem von **SQLGetInfo**zurückgegebenen bezeichneranführungs Zeichen in Anführungszeichen eingeschlossen werden.|  
  
 Nachdem die Anwendung Werte für SQL_BEST_ROWID abgerufen hat, kann die Anwendung diese Werte verwenden, um diese Zeile im definierten Bereich erneut auszuwählen. Die **Select** -Anweisung gibt entweder keine Zeilen oder eine Zeile zurück.  
  
 Wenn eine Anwendung eine Zeile auf der Grundlage der ROWID-Spalte oder-Spalten erneut auswählt und die Zeile nicht gefunden wird, kann die Anwendung davon ausgehen, dass die Zeile gelöscht wurde oder die ROWID-Spalten geändert wurden. Das Gegenteil ist nicht zutrifft: auch wenn die ROWID nicht geändert wurde, haben sich die anderen Spalten in der Zeile möglicherweise geändert.  
  
 Spalten, die für den Spaltentyp SQL_BEST_ROWID zurückgegeben werden, sind nützlich für Anwendungen, die in einem Resultset vorwärts und Rückwärtsscrollen müssen, um die aktuellsten Daten aus einer Reihe von Zeilen abzurufen. Es ist garantiert, dass die Spalten der ROWID nicht geändert werden, wenn Sie in dieser Zeile positioniert werden.  
  
 Die Spalten der ROWID können auch dann gültig bleiben, wenn der Cursor nicht in der Zeile positioniert ist. die Anwendung kann dies durch Überprüfen der Bereichs Spalte im Resultset bestimmen.  
  
 Spalten, die für den Spaltentyp SQL_ROWVER zurückgegeben werden, sind nützlich für Anwendungen, die überprüfen müssen, ob Spalten in einer bestimmten Zeile aktualisiert wurden, während die Zeile mit der ROWID erneut ausgewählt wurde. Wenn Sie z. b. eine Zeile mithilfe von ROWID erneut auswählen, kann die Anwendung die vorherigen Werte in den SQL_ROWVER Spalten mit den soeben abgerufenen vergleichen. Wenn sich der Wert in einer SQL_ROWVER Spalte vom vorherigen Wert unterscheidet, kann die Anwendung den Benutzer benachrichtigen, dass sich die Daten auf der Anzeige geändert haben.  
  
## <a name="code-example"></a>Codebeispiel  
 Ein Codebeispiel für eine ähnliche Funktion finden Sie unter [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben der Spalten in einer Tabelle oder in Tabellen|[SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben der Spalten eines Primärschlüssels|[SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
