---
title: SQLStatistics-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c2a5ef0b0e54e17a2dc091a98efc972fa608ef15
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302944"
---
# <a name="sqlstatistics-function"></a>SQLStatistics-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLStatistics** ruft eine Liste von Statistiken zu einer einzelnen Tabelle und den der Tabelle zugeordneten Indizes ab. Der Treiber gibt die Informationen als Ergebnissatz zurück.  
  
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
 [Eingabe] Anweisungshandle.  
  
 *Catalogname*  
 [Eingabe] Katalogname. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Kataloge haben. *CatalogName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *CatalogName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen von **CatalogName*.  
  
 *Schemaname*  
 [Eingabe] Schemaname. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas haben. *SchemaName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *SchemaName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *SchemaName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen von **SchemaName*.  
  
 *TableName*  
 [Eingabe] Tabellenname. Dieses Argument kann kein Nullzeiger sein. *SchemaName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *TableName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *TableName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen von **TableName*.  
  
 *Einzigartige*  
 [Eingabe] Indextyp: SQL_INDEX_UNIQUE oder SQL_INDEX_ALL.  
  
 *Reserved*  
 [Eingabe] Gibt die Bedeutung der Spalten CARDINALITY und PAGES im Resultset an. Die folgenden Optionen wirken sich nur auf die Rückgabe der Spalten CARDINALITY und PAGES aus. Indexinformationen werden zurückgegeben, auch wenn CARDINALITY und PAGES nicht zurückgegeben werden.  
  
 SQL_ENSURE fordert an, dass der Treiber die Statistiken bedingungslos abruft. (Treiber, die nur dem Open Group-Standard entsprechen und ODBC-Erweiterungen nicht unterstützen, können SQL_ENSURE nicht unterstützen.)  
  
 SQL_QUICK fordert an, dass der Treiber DIE CARDINALITY und PAGES nur dann abruft, wenn sie vom Server verfügbar sind. In diesem Fall wird vom Treiber nicht sichergestellt, dass die Werte aktuell sind. (Anwendungen, die in den Open Group-Standard geschrieben werden, erhalten immer SQL_QUICK Verhalten von ODBC *3.x*-kompatiblen Treibern.)  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLStatistics** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLStatistics** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|24.000|Ungültiger Cursorstatus|Im *StatementHandle*wurde ein Cursor geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat und vom Treiber zurückgegeben wird, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Im *StatementHandle*wurde ein Cursor geöffnet, **SQLFetch** oder **SQLFetchScroll** wurden jedoch nicht aufgerufen.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcendeadlocks mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für den *StatementHandle*aufgerufen, und dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das *TableName-Argument* war ein Nullzeiger.<br /><br /> Das attribut SQL_ATTR_METADATA_ID Anweisung wurde auf SQL_TRUE festgelegt, das *Argument CatalogName* war ein Nullzeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) Das SQL_ATTR_METADATA_ID-Anweisungsattribut wurde auf SQL_TRUE festgelegt, und das *SchemaName-Argument* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLStatistics-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der Wert eines der Argumente für die Namenslänge war kleiner als 0, aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der Namenslängenargumente hat den maximalen Längenwert für den entsprechenden Namen überschritten.|  
|HY100|Eindeutigkeitsoption atyp a-range|(DM) Es wurde ein ungültiger *Eindeutiger* Wert angegeben.|  
|HY101|Genauigkeitsoptionstyp a-range|(DM) Es wurde ein ungültiger *Reserved-Wert* angegeben.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Es wurde ein Katalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLStatistics** gibt Informationen zu einer einzelnen Tabelle als Standardergebnissatz zurück, sortiert nach NON_UNIQUE, TYPE, INDEX_QUALIFIER, INDEX_NAME und ORDINAL_POSITION. Das Resultset kombiniert Statistikinformationen (in den Spalten CARDINALITY und PAGES des Resultsets) für die Tabelle mit Informationen zu jedem Index. Informationen zur Verwendung dieser Informationen finden Sie unter [Verwendung von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Um die tatsächlichen Längen der TABLE_CAT-, TABLE_SCHEM-, TABLE_NAME- und COLUMN_NAME-Spalten zu bestimmen, kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN aufrufen.  
  
> [!NOTE]  
>  Weitere Informationen zur allgemeinen Verwendung, Argumente und zurückgegebenen Daten von ODBC-Katalogfunktionen finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Die folgenden Spalten wurden für ODBC *3.x*umbenannt. Die Änderungen des Spaltennamens wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer binden.  
  
|ODBC 2.0-Säule|ODBC *3.x-Spalte*|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|SEQ_IN_INDEX|ORDINAL_POSITION|  
|COLLATION|ASC_OR_DESC|  
  
 In der folgenden Tabelle sind die Spalten im Resultset aufgeführt. Zusätzliche Spalten über Spalte 13 (FILTER_CONDITION) hinaus können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifische Spalten erhalten, indem sie vom Ende des Resultsets herunterzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Katalogname der Tabelle, auf die die Statistik oder der Index angewendet wird; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für tabellen zurück, die keine Kataloge haben.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Schemaname der Tabelle, auf die die Statistik oder der Index angewendet wird; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für Tabellen zurück, die keine Schemas haben.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar nicht NULL|Tabellenname der Tabelle, auf die die Statistik oder der Index angewendet wird.|  
|NON_UNIQUE (ODBC 1.0)|4|Smallint|Gibt an, ob der Index keine doppelten Werte zulässt:<br /><br /> SQL_TRUE, wenn die Indexwerte nicht eindeutig sein können.<br /><br /> SQL_FALSE, wenn die Indexwerte eindeutig sein müssen.<br /><br /> NULL wird zurückgegeben, wenn TYPE SQL_TABLE_STAT ist.|  
|INDEX_QUALIFIER (ODBC 1.0)|5|Varchar|Der Bezeichner, der verwendet wird, um den Indexnamen für einen **DROP INDEX**zu qualifizieren; NULL wird zurückgegeben, wenn ein Indexqualifizierer von der Datenquelle nicht unterstützt wird oder wenn TYPE SQL_TABLE_STAT ist. Wenn in dieser Spalte ein Nicht-Null-Wert zurückgegeben wird, muss er verwendet werden, um den Indexnamen für eine **DROP INDEX-Anweisung** zu qualifizieren. Andernfalls sollte die TABLE_SCHEM verwendet werden, um den Indexnamen zu qualifizieren.|  
|INDEX_NAME (ODBC 1.0)|6|Varchar|Indexname; NULL wird zurückgegeben, wenn TYPE SQL_TABLE_STAT ist.|  
|TYP (ODBC 1.0)|7|Smallint nicht NULL|Art der zurückgegebenen Informationen:<br /><br /> SQL_TABLE_STAT gibt eine Statistik für die Tabelle an (in der Spalte CARDINALITY oder PAGES).<br /><br /> SQL_INDEX_BTREE gibt einen B-Baum-Index an.<br /><br /> SQL_INDEX_CLUSTERED gibt einen gruppierten Index an.<br /><br /> SQL_INDEX_CONTENT gibt einen Inhaltsindex an.<br /><br /> SQL_INDEX_HASHED gibt einen hashed Index an.<br /><br /> SQL_INDEX_OTHER gibt einen anderen Indextyp an.|  
|ORDINAL_POSITION (ODBC 1.0)|8|Smallint|Spaltensequenznummer im Index (beginnend mit 1); NULL wird zurückgegeben, wenn TYPE SQL_TABLE_STAT ist.|  
|COLUMN_NAME (ODBC 1.0)|9|Varchar|Spaltenname. Wenn die Spalte auf einem Ausdruck basiert, z. B. SALARY + BENEFITS, wird der Ausdruck zurückgegeben. Wenn der Ausdruck nicht bestimmt werden kann, wird eine leere Zeichenfolge zurückgegeben. NULL wird zurückgegeben, wenn TYPE SQL_TABLE_STAT ist.|  
|ASC_OR_DESC (ODBC 1.0)|10|Char(1)|Sortierreihenfolge für die Spalte: "A" für aufsteigend; "D" für absteigend; NULL wird zurückgegeben, wenn die Spaltensortfolge von der Datenquelle nicht unterstützt wird oder wenn TYPE SQL_TABLE_STAT ist.|  
|KARDINALITÄT (ODBC 1.0)|11|Integer|Kardinalität der Tabelle oder des Index; Anzahl der Zeilen in der Tabelle, wenn TYPE SQL_TABLE_STAT ist; Anzahl der eindeutigen Werte im Index, wenn TYPE nicht SQL_TABLE_STAT ist; NULL wird zurückgegeben, wenn der Wert nicht aus der Datenquelle verfügbar ist.|  
|SEITEN (ODBC 1.0)|12|Integer|Anzahl der Seiten, die zum Speichern des Indexes oder der Tabelle verwendet werden; Anzahl der Seiten für die Tabelle, wenn TYPE SQL_TABLE_STAT ist; Anzahl der Seiten für den Index, wenn TYPE nicht SQL_TABLE_STAT ist; NULL wird zurückgegeben, wenn der Wert nicht aus der Datenquelle verfügbar ist oder nicht für die Datenquelle geeignet ist.|  
|FILTER_CONDITION (ODBC 2.0)|13|Varchar|Wenn es sich bei dem Index um einen gefilterten Index handelt, ist dies die Filterbedingung, z. B. SALARY > 30000; Wenn die Filterbedingung nicht bestimmt werden kann, handelt es sich um eine leere Zeichenfolge.<br /><br /> NULL, wenn es sich bei dem Index nicht um einen gefilterten Index handelt, kann nicht bestimmt werden, ob es sich bei dem Index um einen gefilterten Index handelt oder type SQL_TABLE_STAT.|  
  
 Wenn die Zeile im Resultset einer Tabelle entspricht, legt der Treiber TYPE auf SQL_TABLE_STAT und NON_UNIQUE, INDEX_QUALIFIER, INDEX_NAME, ORDINAL_POSITION, COLUMN_NAME und ASC_OR_DESC auf NULL fest. Wenn CARDINALITY oder PAGES aus der Datenquelle nicht verfügbar sind, legt der Treiber sie auf NULL fest.  
  
## <a name="code-example"></a>Codebeispiel  
 Ein Codebeispiel für eine ähnliche Funktion finden Sie unter [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in einer vorwärts gerichteten Richtung.|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben der Spalten von Fremdschlüsseln|[SQLForeignKeys-Funktion](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|Zurückgeben der Spalten eines Primärschlüssels|[SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
