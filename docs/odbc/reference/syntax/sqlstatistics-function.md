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
manager: craigg
ms.openlocfilehash: bc0c1d981180c61452f97a01bc0aba6fdc2d81e3
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793735"
---
# <a name="sqlstatistics-function"></a>SQLStatistics-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLStatistics** Ruft eine Liste der Statistiken zu einer einzelnen Tabelle und die Indizes der Tabelle zugeordnet. Der Treiber gibt zurück, die Informationen als Resultset.  
  
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
  
 *CatalogName*  
 [Eingabe] Name des Katalogs. Wenn ein Treiber unterstützt die Kataloge für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") gibt an, die Tabellen, denen keine Kataloge. *CatalogName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *CatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *CatalogName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen des **CatalogName*.  
  
 *SchemaName*  
 [Eingabe] Name des Schemas. Wenn ein Treiber unterstützt die Schemas für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") gibt an, die Tabellen, die keine Schemas aufweisen. *SchemaName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *SchemaName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *SchemaName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen des **SchemaName*.  
  
 *TableName*  
 [Eingabe] Name der Tabelle. Dieses Argument darf nicht null-Zeiger sein. *SchemaName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *TableName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *TableName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen des **TableName*.  
  
 *Eindeutig*  
 [Eingabe] Der Typ des Indexes: SQL_INDEX_UNIQUE oder SQL_INDEX_ALL.  
  
 *Reserved*  
 [Eingabe] Gibt die Bedeutung der KARDINALITÄT und Seiten Spalten im Resultset an. Die folgenden Optionen Einfluss auf die Rückgabe von nur die KARDINALITÄT und Seiten Spalten. Informationen zu Indizes wird zurückgegeben, auch wenn die KARDINALITÄT und Seiten nicht zurückgegeben werden.  
  
 SQL_ENSURE angefordert wird, dass der Treiber unbedingten Abrufen der Statistiken. (Treiber, die nur für die Open Group-Standard entsprechen, und bieten keine Unterstützung für ODBC-Erweiterungen nicht SQL_ENSURE unterstützen werden.)  
  
 SQL_QUICK angefordert wird, dass der Treiber die KARDINALITÄT und Seiten abrufen, nur dann, wenn sie direkt auf dem Server verfügbar sind. In diesem Fall wird vom Treiber nicht sichergestellt, dass die Werte aktuell sind. (Anwendungen, die in den Standard Open Group geschrieben werden rufen immer das SQL_QUICK-Verhalten von ODBC *3.x*-kompatibel sind.)  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLStatistics** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLStatistics** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde wegen eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*, und klicken Sie dann die Funktion aufgerufen wurde erneut auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Die *TableName* Argument wurde ein null-Zeiger.<br /><br /> Das Anweisungsattribut SQL_ATTR_METADATA_ID wurde festgelegt auf SQL_TRUE, die *CatalogName* Argument wurde ein null-Zeiger ist, und die SQL_CATALOG_NAME *Informationsart* gibt zurück, die Namen Katalog werden unterstützt.<br /><br /> (DM) das Anweisungsattribut SQL_ATTR_METADATA_ID wurde Wert auf SQL_TRUE festgelegt, und die *SchemaName* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLStatistics** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert eines der Argumente Länge Name war kleiner als 0, jedoch nicht SQL_NTS gleich.<br /><br /> Der Wert eines der Argumente Namen Länge überschritten Wert für maximale Länge für den entsprechenden Namen.|  
|HY100|Der Eindeutigkeitsoptionstyp außerhalb des gültigen Bereichs|(DM) eine ungültige *Unique* -Wert wurde angegeben.|  
|HY101|Der Genauigkeitoptionstyp außerhalb des gültigen Bereichs|(DM) eine ungültige *reserviert* -Wert wurde angegeben.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Ein Katalog angegeben wurde, und der Treiber oder die Datenquelle Kataloge nicht unterstützt.<br /><br /> Ein Schema angegeben wurde, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Abfragetimeout abgelaufen, bevor Sie die Datenquelle, die das angeforderte Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLStatistics** gibt Informationen zu einer einzelnen Tabelle als standard Resultset, geordnet nach NON_UNIQUE, Typ, INDEX_QUALIFIER, INDEX_NAME und ORDINAL_POSITION zurück. Das Resultset werden statistische Informationen (in der KARDINALITÄT und Seiten-Spalten des Resultsets) für die Tabelle mit Informationen zu jedem Index kombiniert. Informationen dazu, wie diese Informationen verwendet werden kann, finden Sie unter [von Katalogdaten verwendet](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Um zu bestimmen, die tatsächliche Länge der Spalten TABLE_CAT, nach "TABLE_SCHEM", Tabellenname und Spaltenname, eine Anwendung aufrufen kann **SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN, und SQL_MAX_COLUMN_NAME_LEN-Optionen.  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Die folgenden Spalten wurden umbenannt für ODBC *3.x*. Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC *3.x* Spalte|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|SEQ_IN_INDEX|ORDINAL_POSITION|  
|COLLATION|ASC_OR_DESC|  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 13 (filterbedingung) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifischen Spalten erhalten, indem nach unten am Ende des Resultsets anstatt einer expliziten Ordinalposition zählen. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Der Katalogname der Tabelle, für die die Statistik bzw. der Index gilt; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Kataloge für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, denen keine Kataloge.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Der Schemaname der Tabelle, für die die Statistik bzw. der Index gilt; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Schemas für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, die keine Schemas aufweisen.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar, die nicht NULL|Der Tabellenname der Tabelle, für die die Statistik bzw. der Index gilt.|  
|NON_UNIQUE (ODBC 1.0)|4|Smallint|Gibt an, ob der Index keine doppelten Werte zulässig sind:<br /><br /> SQL_TRUE, wenn die Indexwerte nicht eindeutig sein können.<br /><br /> SQL_FALSE, wenn die Indexwerte eindeutig sein müssen.<br /><br /> Wenn Typ SQL_TABLE_STAT ist, wird NULL zurückgegeben.|  
|INDEX_QUALIFIER (ODBC 1.0)|5|Varchar|Der Bezeichner, der verwendet wird, um den Index zu qualifizieren nennen dies einen **DROP INDEX**; NULL wird zurückgegeben, wenn ein Index Qualifizierer nicht von der Datenquelle unterstützt wird, oder wenn Typ SQL_TABLE_STAT ist. Wenn ein Wert ungleich Null in dieser Spalte zurückgegeben wird, muss es zum Qualifizieren Sie den Namen des Indexes auf verwendet werden eine **DROP INDEX** -Anweisung; andernfalls sollte der nach "TABLE_SCHEM" verwendet werden, um den Namen des Indexes zu qualifizieren.|  
|INDEX_NAME (ODBC 1.0)|6|Varchar|Name des Indexes; Wenn Typ SQL_TABLE_STAT ist, wird NULL zurückgegeben.|  
|TYP (ODBC 1.0)|7|Smallint nicht NULL|Typ der Informationen zurückgegeben werden:<br /><br /> SQL_TABLE_STAT zeigt eine Statistik für die Tabelle (in der Spalte "KARDINALITÄT" oder "Seiten") an.<br /><br /> SQL_INDEX_BTREE gibt einen B-Strukturindex an.<br /><br /> SQL_INDEX_CLUSTERED gibt an, einen gruppierten Index.<br /><br /> SQL_INDEX_CONTENT gibt einen Inhaltsindex an.<br /><br /> SQL_INDEX_HASHED gibt einen Hashindex an.<br /><br /> SQL_INDEX_OTHER gibt einen anderen Typ des Indexes an.|  
|ORDINAL_POSITION (ODBC 1.0)|8|Smallint|Sequenz-Nummer der Spalte im Index (beginnend mit 1); Wenn Typ SQL_TABLE_STAT ist, wird NULL zurückgegeben.|  
|COLUMN_NAME (ODBC 1.0)|9|Varchar|Name der Spalte. Wenn die Spalte auf einem Ausdruck basiert, z. B. Gehalt + Vorteile, der Ausdruck zurückgegeben. Wenn der Ausdruck kann nicht bestimmt werden, wird eine leere Zeichenfolge zurückgegeben. Wenn Typ SQL_TABLE_STAT ist, wird NULL zurückgegeben.|  
|ASC_OR_DESC (ODBC 1.0)|10|char(1)|Die Sortierreihenfolge für die Spalte: "A" für eine aufsteigende; "D" für eine absteigende; NULL wird zurückgegeben, wenn die Sortierreihenfolge der Spalte von der Datenquelle nicht unterstützt wird oder SQL_TABLE_STAT ist.|  
|CARDINALITY (ODBC 1.0)|11|Integer|Die Kardinalität der Tabelle oder eines Indexes; die Anzahl der Zeilen in Tabelle, wenn der Typ SQL_TABLE_STAT ist; die Anzahl der eindeutigen Werte in der Index, wenn der Typ nicht SQL_TABLE_STAT ist; NULL wird zurückgegeben, wenn der Wert aus der Datenquelle nicht verfügbar ist.|  
|SEITEN (ODBC 1.0)|12|Integer|Die Anzahl der Seiten, die zum Speichern des Indexes oder der Tabelle; die Anzahl der Seiten für die Tabelle, sofern der Typ SQL_TABLE_STAT ist; die Anzahl der Seiten, die für den Index, wenn der Typ nicht SQL_TABLE_STAT ist; NULL wird zurückgegeben, wenn der Wert aus der Datenquelle nicht verfügbar ist, oder wenn mit der Datenquelle nicht anwendbar.|  
|FILTER_CONDITION (ODBC 2.0)|13|Varchar|Wenn der Index ein gefilterter Index ist, ist dies die filterbedingung, z. B. Gehalt > 30000 ist Wenn die filterbedingung nicht bestimmt werden kann, ist dies eine leere Zeichenfolge.<br /><br /> NULL, wenn der Index nicht über ein gefilterter Index ist, kann nicht bestimmt werden, ob der Index ein gefilterter Index ist oder Typ SQL_TABLE_STAT.|  
  
 Wenn die Zeile im Resultset in eine Tabelle entspricht, der Treiber legt Typ auf SQL_TABLE_STAT und NON_UNIQUE, INDEX_QUALIFIER, INDEX_NAME, ORDINAL_POSITION, COLUMN_NAME und ASC_OR_DESC auf NULL. KARDINALITÄT oder Seiten nicht verfügbar von der Datenquelle sind, werden sie von der Treiber auf NULL festgelegt.  
  
## <a name="code-example"></a>Codebeispiel  
 Ein Codebeispiel der eine ähnliche Funktion finden Sie unter [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Eine einzelne Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor werden abgerufen.|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben von Spalten von Fremdschlüsseln|[SQLForeignKeys-Funktion](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|Zurückgeben der Spalten eines Primärschlüssels|[SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
