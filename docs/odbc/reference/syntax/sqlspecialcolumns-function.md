---
title: SQLSpecialColumns-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287170"
---
# <a name="sqlspecialcolumns-function"></a>SQLSpecialColumns-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0 Standards Compliance: Open Group  
  
 **Zusammenfassung**  
 **SQLSpecialColumns** ruft die folgenden Informationen zu Spalten in einer angegebenen Tabelle ab:  
  
-   Der optimale Satz von Spalten, der eine Zeile in der Tabelle eindeutig identifiziert.  
  
-   Spalten, die automatisch aktualisiert werden, wenn ein beliebiger Wert in der Zeile durch eine Transaktion aktualisiert wird.  
  
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
 [Eingabe] Anweisungshandle.  
  
 *IdentifierType*  
 [Eingabe] Typ der zurückzugebenden Spalte. Dies muss einer der folgenden Werte sein:  
  
 SQL_BEST_ROWID: Gibt die optimale Spalte oder den Satz von Spalten zurück, die durch Abrufen von Werten aus der Spalte oder den Spalten eine eindeutige Identifizierung einer beliebigen Zeile in der angegebenen Tabelle ermöglichen. Eine Spalte kann entweder eine Pseudospalte sein, die speziell für diesen Zweck entwickelt wurde (wie in Oracle ROWID oder Ingres TID) oder die Spalte oder Spalten eines eindeutigen Indexes für die Tabelle.  
  
 SQL_ROWVER: Gibt die Spalte oder Spalten in der angegebenen Tabelle zurück, die automatisch von der Datenquelle aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion aktualisiert wird (wie in SQLBase ROWID oder Sybase TIMESTAMP).  
  
 *Catalogname*  
 [Eingabe] Katalogname für die Tabelle. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Tabellen, die keine Kataloge haben. *CatalogName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *CatalogName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen von **CatalogName*.  
  
 *Schemaname*  
 [Eingabe] Schemaname für die Tabelle. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Tabellen, die keine Schemas haben. *SchemaName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *SchemaName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *SchemaName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen von **SchemaName*.  
  
 *TableName*  
 [Eingabe] Tabellenname. Dieses Argument kann kein Nullzeiger sein. *TableName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *TableName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *TableName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen von **TableName*.  
  
 *Umfang*  
 [Eingabe] Minimaler erforderlicher Bereich der Rowid. Die zurückgegebene Rowid kann einen größeren Umfang haben. Dies muss eine der folgenden Ressourcen sein:  
  
 SQL_SCOPE_CURROW: Die Rowid ist garantiert nur gültig, wenn sie in dieser Zeile positioniert ist. Eine spätere erneute Auswahl mit rowid gibt möglicherweise keine Zeile zurück, wenn die Zeile von einer anderen Transaktion aktualisiert oder gelöscht wurde.  
  
 SQL_SCOPE_TRANSACTION: Die Rowid ist garantiert für die Dauer der aktuellen Transaktion gültig.  
  
 SQL_SCOPE_SESSION: Die Rowid ist garantiert für die Dauer der Sitzung (über Transaktionsgrenzen hinweg) gültig.  
  
 *NULL zulassen*  
 [Eingabe] Legt fest, ob spezielle Spalten zurückgegeben werden sollen, die einen NULL-Wert haben können. Dies muss eine der folgenden Ressourcen sein:  
  
 SQL_NO_NULLS: Schließen Sie spezielle Spalten aus, die NULL-Werte aufweisen können. Einige Treiber können SQL_NO_NULLS nicht unterstützen, und diese Treiber geben ein leeres Resultset zurück, wenn SQL_NO_NULLS angegeben wurde. Anträge sollten für diesen Fall vorbereitet werden und SQL_NO_NULLS nur dann anfordern, wenn dies unbedingt erforderlich ist.  
  
 SQL_NULLABLE: Geben Sie spezielle Spalten zurück, auch wenn sie NULL-Werte haben können.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSpecialColumns** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von SQLSpecialColumns zurückgegeben werden, und es werden die **SQLSTATE-Werte** im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|24.000|Ungültiger Cursorstatus|Im *StatementHandle*wurde ein Cursor geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat und vom Treiber zurückgegeben wird, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Im *StatementHandle*wurde ein Cursor geöffnet, **SQLFetch** oder **SQLFetchScroll** wurden jedoch nicht aufgerufen.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcenstillstands mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das *TableName-Argument* war ein Nullzeiger.<br /><br /> Das attribut SQL_ATTR_METADATA_ID Anweisung wurde auf SQL_TRUE festgelegt, das *Argument CatalogName* war ein Nullzeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) Das SQL_ATTR_METADATA_ID-Anweisungsattribut wurde auf SQL_TRUE festgelegt, und das *SchemaName-Argument* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese Funktion wurde noch ausgeführt, als **SQLSpecialColumns** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der Wert eines der Längenargumente war kleiner als 0, aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der Längenargumente hat den maximalen Längenwert für den entsprechenden Namen überschritten. Die maximale Länge jedes Namens kann abgerufen werden, indem **SQLGetInfo** mit den *InfoType-Werten* aufgerufen wird: SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN oder SQL_MAX_TABLE_NAME_LEN.|  
|HY097|Spaltentyp a-range|(DM) Ein ungültiger *IdentifierType-Wert* wurde angegeben.|  
|HY098|Scope-Typ a-range|(DM) Es wurde ein ungültiger *Scope-Wert* angegeben.|  
|HY099|Nullabler Typ a-range|(DM) Es wurde ein *ungültiger Nullwert* angegeben.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Es wurde ein Katalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Wenn das *Argument IdentifierType* SQL_BEST_ROWID ist, gibt **SQLSpecialColumns** die Spalte oder Spalten zurück, die jede Zeile in der Tabelle eindeutig identifizieren. Diese Spalten können immer in einer Auswahlliste oder *WHERE-Klausel* verwendet werden. **WHERE** **SQLColumns**, das zum Zurückgeben einer Vielzahl von Informationen in den Spalten einer Tabelle verwendet wird, gibt nicht notwendigerweise die Spalten zurück, die jede Zeile eindeutig identifizieren, oder Spalten, die automatisch aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion aktualisiert wird. **SQLColumns** gibt z. B. die Oracle-Pseudospalte ROWID möglicherweise nicht zurück. Aus diesem Grund wird **SQLSpecialColumns** verwendet, um diese Spalten zurückzugeben. Weitere Informationen finden Sie unter [Verwendung von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Weitere Informationen zur allgemeinen Verwendung, Argumente und zurückgegebenen Daten von ODBC-Katalogfunktionen finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Wenn keine Spalten vorhanden sind, die jede Zeile in der Tabelle eindeutig identifizieren, gibt **SQLSpecialColumns** ein Rowset ohne Zeilen zurück. Ein nachfolgender Aufruf von **SQLFetch** oder **SQLFetchScroll** für die Anweisung gibt SQL_NO_DATA zurück.  
  
 Wenn die Argumente *IdentifierType*, *Scope*oder *Nullable* Merkmale angeben, die von der Datenquelle nicht unterstützt werden, gibt **SQLSpecialColumns** ein leeres Resultset zurück.  
  
 Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, werden die Argumente *CatalogName*, *SchemaName*und *TableName* als Bezeichner behandelt, sodass sie in bestimmten Situationen nicht auf einen Nullzeiger festgelegt werden können. (Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).)  
  
 **SQLSpecialColumns** gibt die Ergebnisse als Standardergebnissatz zurück, sortiert nach SCOPE.  
  
 Die folgenden Spalten wurden für ODBC *3.x*umbenannt. Die Änderungen des Spaltennamens wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer binden.  
  
|ODBC 2.0-Säule|ODBC *3.x-Spalte*|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
  
 Um die tatsächliche Länge der COLUMN_NAME Spalte zu bestimmen, kann eine Anwendung **SQLGetInfo** mit der Option SQL_MAX_COLUMN_NAME_LEN aufrufen.  
  
 In der folgenden Tabelle sind die Spalten im Resultset aufgeführt. Zusätzliche Spalten über Spalte 8 (PSEUDO_COLUMN) hinaus können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifische Spalten erhalten, indem sie vom Ende des Resultsets herunterzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|BEREICH (ODBC 1.0)|1|Smallint|Aktueller Bereich der rowid. Enthält einen der folgenden Werte:<br /><br /> SQL_SCOPE_CURROW SQL_SCOPE_TRANSACTION SQL_SCOPE_SESSION<br /><br /> NULL wird zurückgegeben, wenn *IdentifierType* SQL_ROWVER ist. Eine Beschreibung der einzelnen Werte finden Sie in der Beschreibung des *Bereichs* in "Syntax" weiter oben in diesem Abschnitt.|  
|COLUMN_NAME (ODBC 1.0)|2|Varchar nicht NULL|Spaltenname. Der Treiber gibt eine leere Zeichenfolge für eine Spalte zurück, die keinen Namen hat.|  
|DATA_TYPE (ODBC 1.0)|3|Smallint nicht NULL|SQL-Datentyp. Dies kann ein ODBC SQL-Datentyp oder ein treiberspezifischer SQL-Datentyp sein. Eine Liste gültiger ODBC SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md). Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.|  
|TYPE_NAME (ODBC 1.0)|4|Varchar nicht NULL|Datenquellenabhängiger Datentypname; z. B. "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY" oder "CHAR ( ) FOR BIT DATA".|  
|COLUMN_SIZE (ODBC 1.0)|5|Integer|Die Größe der Spalte in der Datenquelle. Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|BUFFER_LENGTH (ODBC 1.0)|6|Integer|Die Länge in Bytes von Daten, die für einen **SQLGetData-** oder **SQLFetch-Vorgang** übertragen werden, wenn SQL_C_DEFAULT angegeben ist. Bei numerischen Daten kann diese Größe von der Größe der in der Datenquelle gespeicherten Daten abweichen. Dieser Wert entspricht der COLUMN_SIZE Spalte für Zeichen- oder Binärdaten. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|DECIMAL_DIGITS (ODBC 1.0)|7|Smallint|Die Dezimalstellen der Spalte in der Datenquelle. NULL wird für Datentypen zurückgegeben, für die Dezimalstellen nicht anwendbar sind. Weitere Informationen zu Dezimalstellen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|PSEUDO_COLUMN (ODBC 2.0)|8|Smallint|Gibt an, ob es sich bei der Spalte um eine Pseudospalte handelt, z. B. Oracle ROWID:<br /><br /> SQL_PC_UNKNOWN SQL_PC_NOT_PSEUDO SQL_PC_PSEUDO **Hinweis:** Für maximale Interoperabilität sollten Pseudospalten nicht mit dem von **SQLGetInfo**zurückgegebenen Bezeichneranführungszeichen zitiert werden.|  
  
 Nachdem die Anwendung Werte für SQL_BEST_ROWID abgerufen hat, kann die Anwendung diese Werte verwenden, um diese Zeile innerhalb des definierten Bereichs erneut auszuwählen. Die **SELECT-Anweisung** gibt garantiert entweder keine Zeilen oder eine Zeile zurück.  
  
 Wenn eine Anwendung eine Zeile basierend auf der Rowidspalte oder den Zeilen wieder auswählt und die Zeile nicht gefunden wird, kann die Anwendung davon ausgehen, dass die Zeile gelöscht oder die Rowidspalten geändert wurden. Das Gegenteil ist nicht der Fall: Auch wenn sich die Rowid nicht geändert hat, können sich die anderen Spalten in der Zeile geändert haben.  
  
 Spalten, die für spaltentyp SQL_BEST_ROWID zurückgegeben werden, sind nützlich für Anwendungen, die innerhalb eines Resultsets vorwärts und zurück scrollen müssen, um die neuesten Daten aus einer Reihe von Zeilen abzurufen. Die Spalte oder Spalten der Rowid werden garantiert nicht geändert, während sie in dieser Zeile positioniert werden.  
  
 Die Spalte oder die Spalten der Rowid bleiben auch dann gültig, wenn der Cursor nicht in der Zeile positioniert ist. Die Anwendung kann dies bestimmen, indem sie die SCOPE-Spalte im Resultset überprüft.  
  
 Spalten, die für den Spaltentyp SQL_ROWVER zurückgegeben werden, sind nützlich für Anwendungen, die überprüfen können, ob Spalten in einer bestimmten Zeile aktualisiert wurden, während die Zeile mit der Rowid erneut ausgewählt wurde. Nach dem erneuten Auswählen einer Zeile mit rowid kann die Anwendung beispielsweise die vorherigen Werte in den SQL_ROWVER Spalten mit den gerade abgerufenen Vergleichen vergleichen. Wenn der Wert in einer SQL_ROWVER Spalte vom vorherigen Wert abweicht, kann die Anwendung den Benutzer warnen, dass sich die Daten auf der Anzeige geändert haben.  
  
## <a name="code-example"></a>Codebeispiel  
 Ein Codebeispiel für eine ähnliche Funktion finden Sie unter [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben der Spalten in einer Tabelle oder Tabellen|[SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in einer vorwärtsgerichteten Richtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben der Spalten eines Primärschlüssels|[SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
