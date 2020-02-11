---
title: SQLStatistics-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLStatistics
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLStatistics
helpviewer_keywords:
- SQLStatistics function [ODBC]
ms.assetid: 45210682-cfea-4e5d-9951-bcf1cbe10f41
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef0f25660a0faa0747752a8ca15c207c1e939669
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039549"
---
# <a name="sqlstatistics-function"></a>SQLStatistics-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLStatistics** Ruft eine Liste von Statistiken zu einer einzelnen Tabelle und den Indizes ab, die der Tabelle zugeordnet sind. Der Treiber gibt die Informationen als Resultset zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLStatistics(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CatalogName,  
     SQLSMALLINT     NameLength1,  
     SQLCHAR *       SchemaName,  
     SQLSMALLINT     NameLength2,  
     SQLCHAR *       TableName,  
     SQLSMALLINT     NameLength3,  
     SQLUSMALLINT    Unique,  
     SQLUSMALLINT    Reserved);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *CatalogName*  
 Der Katalog Name. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die nicht über Kataloge verfügen. *CatalogName* darf kein Zeichen folgen-Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *CatalogName* ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Der Länge in Zeichen von **CatalogName*.  
  
 *Schema Name*  
 Der Schema Name. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas aufweisen. Schema *Name* darf kein Zeichen folgen-Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird Schema *Name* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist Schema *Name* ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength2*  
 Der Länge in Zeichen von * Schema*Name*.  
  
 *TableName*  
 Der Tabellenname. Dieses Argument darf kein NULL-Zeiger sein. Schema *Name* darf kein Zeichen folgen-Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *TableName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *TableName* ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength3*  
 Der Länge in Zeichen von **TableName*.  
  
 *Gem*  
 Der Indextyp: SQL_INDEX_UNIQUE oder SQL_INDEX_ALL.  
  
 *Bleiben*  
 Der Gibt die Wichtigkeit der Spalten "Cardinality" und "Pages" im Resultset an. Die folgenden Optionen wirken sich nur auf die Rückgabe der Spalten "Cardinality" und "Pages" aus. Indexinformationen werden auch dann zurückgegeben, wenn Kardinalität und Seiten nicht zurückgegeben werden.  
  
 SQL_ENSURE Anforderungen an, dass der Treiber die Statistiken bedingungslos abruft. (Treiber, die nur dem Open Group-Standard entsprechen und keine ODBC-Erweiterungen unterstützen, können SQL_ENSURE nicht unterstützen.)  
  
 SQL_QUICK Anforderungen, dass der Treiber die Kardinalität und Seiten nur dann abruft, wenn Sie auf dem Server verfügbar sind. In diesem Fall wird vom Treiber nicht sichergestellt, dass die Werte aktuell sind. (Anwendungen, die in den offenen Gruppen Standard geschrieben werden, erhalten immer SQL_QUICK Verhalten von ODBC *3. x*-kompatiblen Treibern.)  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLStatistics** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle werden die SQLSTATE-Werte aufgelistet, die in der Regel von **SQLStatistics** zurückgegeben werden, und jede im Kontext dieser Funktion wird erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben wurde und vom Treiber zurückgegeben wird, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor war auf dem *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde ein Rollback ausgeführt, weil ein Ressourcen Deadlock mit einer anderen Transaktion aufgetreten ist.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen, und anschließend wurde die Funktion für " *StatementHandle*" erneut aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das *TableName* -Argument war ein NULL-Zeiger.<br /><br /> Das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, das *CatalogName* -Argument war ein NULL-Zeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, und das Schema *Name* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLStatistics** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der Wert eines der namens Längen Argumente war kleiner als 0 (null), aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der namens Längen Argumente hat den maximalen Längen Wert für den entsprechenden Namen überschritten.|  
|HY100|Eindeutigkeits Optionstyp außerhalb des gültigen Bereichs|(DM) Es wurde *ein ungültiger* eindeutiger Wert angegeben.|  
|HY101|Genauigkeits Optionstyp außerhalb des gültigen Bereichs|(DM) Es wurde ein ungültiger *reservierter* Wert angegeben.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Es wurde ein Katalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLStatistics** gibt Informationen zu einer einzelnen Tabelle als Standardresultset zurück, geordnet nach NON_UNIQUE, Typ, INDEX_QUALIFIER, index_name und ORDINAL_POSITION. Das Resultset kombiniert Statistik Informationen (in den Spalten "Cardinality" und "Pages" des Resultsets) für die Tabelle mit Informationen zu jedem Index. Informationen dazu, wie diese Informationen verwendet werden können, finden Sie unter [Verwenden von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Zum Bestimmen der tatsächlichen Längen der Spalten TABLE_CAT, TABLE_SCHEM, TABLE_NAME und column_name kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN aufrufen.  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumente und zurückgegebene Daten von ODBC-Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Die folgenden Spalten wurden für ODBC *3. x*umbenannt. Die Spaltennamen Änderungen wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer gebunden werden.  
  
|ODBC 2,0-Spalte|ODBC *3. x* -Spalte|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|SEQ_IN_INDEX|ORDINAL_POSITION|  
|COLLATION|ASC_OR_DESC|  
  
 In der folgenden Tabelle werden die Spalten im Resultset aufgelistet. Zusätzliche Spalten, die über die Spalte 13 (FILTER_CONDITION) hinausgehen, können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf Treiber spezifische Spalten erhalten, indem Sie vom Ende des Resultsets abzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1,0)|1|Varchar|Katalog Name der Tabelle, auf die die Statistik oder der Index angewendet wird. NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Tabellen zurückgegeben, die über keine Kataloge verfügen.|  
|TABLE_SCHEM (ODBC 1,0)|2|Varchar|Der Schema Name der Tabelle, auf die die Statistik oder der Index angewendet wird. NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für Tabellen zurückgegeben, die keine Schemas aufweisen.|  
|Table_name (ODBC 1,0)|3|Varchar not NULL|Der Tabellenname der Tabelle, für die die Statistik oder der Index gilt.|  
|NON_UNIQUE (ODBC 1,0)|4|Smallint|Gibt an, ob der Index doppelte Werte zulässt:<br /><br /> SQL_TRUE, wenn die Indexwerte nicht eindeutig sein dürfen.<br /><br /> SQL_FALSE, wenn die Indexwerte eindeutig sein müssen.<br /><br /> NULL wird zurückgegeben, wenn der Typ SQL_TABLE_STAT ist.|  
|INDEX_QUALIFIER (ODBC 1,0)|5|Varchar|Der Bezeichner, der zum Qualifizieren des Index namens verwendet wird, der einen **Drop Index**. NULL wird zurückgegeben, wenn ein Index Qualifizierer von der Datenquelle nicht unterstützt wird oder wenn der Typ SQL_TABLE_STAT ist. Wenn ein Wert ungleich NULL in dieser Spalte zurückgegeben wird, muss er zum Qualifizieren des Index namens in einer **Drop Index** Anweisung verwendet werden. Andernfalls sollte die TABLE_SCHEM verwendet werden, um den Indexnamen zu qualifizieren.|  
|Index_name (ODBC 1,0)|6|Varchar|Indexname; NULL wird zurückgegeben, wenn der Typ SQL_TABLE_STAT ist.|  
|Type (ODBC 1,0)|7|Smallint nicht NULL|Typ der Informationen, die zurückgegeben werden:<br /><br /> SQL_TABLE_STAT gibt eine Statistik für die Tabelle an (in der Spalte Kardinalität oder Seiten).<br /><br /> SQL_INDEX_BTREE gibt einen B-Struktur Index an.<br /><br /> SQL_INDEX_CLUSTERED gibt einen gruppierten Index an.<br /><br /> SQL_INDEX_CONTENT gibt einen Inhalts Index an.<br /><br /> SQL_INDEX_HASHED gibt einen Hash Index an.<br /><br /> SQL_INDEX_OTHER gibt einen anderen Indextyp an.|  
|ORDINAL_POSITION (ODBC 1,0)|8|Smallint|Spaltensequenznummer in Index (beginnend mit 1); NULL wird zurückgegeben, wenn der Typ SQL_TABLE_STAT ist.|  
|Column_name (ODBC 1,0)|9|Varchar|Spaltenname. Wenn die Spalte auf einem Ausdruck basiert, z. b. "Gehalt + Vorteile", wird der Ausdruck zurückgegeben. Wenn der Ausdruck nicht bestimmt werden kann, wird eine leere Zeichenfolge zurückgegeben. NULL wird zurückgegeben, wenn der Typ SQL_TABLE_STAT ist.|  
|ASC_OR_DESC (ODBC 1,0)|10|Char(1)|Sortierreihenfolge für die Spalte: "A" für aufsteigend; "D" für absteigend; NULL wird zurückgegeben, wenn die Spalten Sortierreihenfolge von der Datenquelle nicht unterstützt wird oder wenn der Typ SQL_TABLE_STAT ist.|  
|Kardinalität (ODBC 1,0)|11|Integer|Kardinalität der Tabelle oder des Indexes; Anzahl der Zeilen in der Tabelle, wenn der Typ SQL_TABLE_STAT ist. die Anzahl eindeutiger Werte im Index, wenn der Typ nicht SQL_TABLE_STAT ist. NULL wird zurückgegeben, wenn der Wert aus der Datenquelle nicht verfügbar ist.|  
|Seiten (ODBC 1,0)|12|Integer|Anzahl der Seiten, die zum Speichern des Indexes oder der Tabelle verwendet werden. Anzahl von Seiten für die Tabelle, wenn der Typ SQL_TABLE_STAT ist. Anzahl der Seiten für den Index, wenn der Typ nicht SQL_TABLE_STAT ist. NULL wird zurückgegeben, wenn der Wert nicht in der Datenquelle verfügbar ist oder nicht auf die Datenquelle anwendbar ist.|  
|FILTER_CONDITION (ODBC 2,0)|13|Varchar|Wenn der Index ein gefilterter Index ist, ist dies die Filterbedingung, z. b. Gehalt > 30000; Wenn die Filterbedingung nicht bestimmt werden kann, handelt es sich um eine leere Zeichenfolge.<br /><br /> NULL, wenn der Index kein gefilterter Index ist, kann nicht ermittelt werden, ob der Index ein gefilterter Index ist oder ob der Typ SQL_TABLE_STAT ist.|  
  
 Wenn die Zeile im Resultset einer Tabelle entspricht, legt der Treiber Type auf SQL_TABLE_STAT fest und legt NON_UNIQUE, INDEX_QUALIFIER, index_name, ORDINAL_POSITION, column_name und ASC_OR_DESC auf NULL fest. Wenn die Kardinalität oder die Seiten nicht in der Datenquelle verfügbar sind, legt der Treiber Sie auf NULL fest.  
  
## <a name="code-example"></a>Codebeispiel  
 Ein Codebeispiel für eine ähnliche Funktion finden Sie unter [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung.|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben der Spalten von Fremdschlüsseln|[SQLForeignKeys-Funktion](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|Zurückgeben der Spalten eines Primärschlüssels|[SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
