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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f44ae90a82e778bf8e8564b719aa6b9f0157a05a
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204369"
---
# <a name="sqlspecialcolumns-function"></a>SQLSpecialColumns-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: Gruppe öffnen  
  
 **Zusammenfassung**  
 **SQLSpecialColumns** Ruft die folgenden Informationen zu den Spalten innerhalb einer angegebenen Tabelle ab:  
  
-   Die optimale Gruppe von Spalten, die eine Zeile in der Tabelle eindeutig identifiziert.  
  
-   Spalten, die automatisch aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion aktualisiert wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 [Eingabe] Typ der zurückzugebenden Spalte. Dabei muss es sich um einen der folgenden Werte sein:  
  
 SQL_BEST_ROWID: Gibt die optimale(n) Spalte(n) oder eine Gruppe von Spalten, denen durch Abrufen von Werten aus der Spalte bzw. Spalten, eine beliebige Zeile in der angegebenen Tabelle eindeutig identifiziert werden kann. Eine Spalte kann entweder eine Pseudospalte speziell für diesen Zweck (wie Oracle ROWID oder Ingres TID) oder die Spalte oder Spalten eines eindeutigen Indexes der Tabelle sein.  
  
 SQL_ROWVER: Gibt die Spalte oder Spalten in der angegebenen Tabelle zurück, sofern vorhanden, die von der Datenquelle automatisch aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion (wie SQLBase ROWID oder Sybase-TIMESTAMP) aktualisiert wird.  
  
 *Katalogname*  
 [Eingabe] Name des Katalogs für die Tabelle. Wenn ein Treiber unterstützt die Kataloge für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, denen keine Kataloge. *CatalogName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *CatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *CatalogName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen des **CatalogName*.  
  
 *SchemaName*  
 [Eingabe] Name des Schemas für die Tabelle. Wenn ein Treiber unterstützt die Schemas für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, die keine Schemas aufweisen. *SchemaName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *SchemaName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *SchemaName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen des **SchemaName*.  
  
 *TableName*  
 [Eingabe] Name der Tabelle. Dieses Argument darf nicht null-Zeiger sein. *TableName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *TableName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *TableName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen des **TableName*.  
  
 *Bereich*  
 [Eingabe] Mindestens erforderliche Bereich der Rowid. Die zurückgegebene Rowid möglicherweise von größerem Umfang. Dies muss eine der folgenden Ressourcen sein:  
  
 SQL_SCOPE_CURROW: Die Rowid ist garantiert, allerdings nur, wenn in dieser Zeile gültig ist. Eine spätere erneute Auswahl mit der Rowid möglicherweise nicht als eine Zeile zurück, wenn die Zeile aktualisiert wurde, oder durch eine andere Transaktion gelöscht.  
  
 SQL_SCOPE_TRANSACTION: Ist garantiert die Rowid für die Dauer der aktuellen Transaktion gültig sein.  
  
 SQL_SCOPE_SESSION: Ist garantiert die Rowid für die Dauer der Sitzung (über Transaktionsgrenzen hinweg) gültig sein.  
  
 *NULL zulassen*  
 [Eingabe] Bestimmt, ob besondere Spalten zurückgeben, die einen Nullwert aufweisen darf. Dies muss eine der folgenden Ressourcen sein:  
  
 SQL_NO_NULLS: Schließen Sie spezielle Spalten, die NULL-Werte enthalten können. Einige Treiber können nicht SQL_NO_NULLS unterstützen und diese Treiber werden SQL_NO_NULLS angegeben wurde ein leeres Resultset zurück. Anwendungen sollten für diesen Fall und die Anforderung SQL_NO_NULLS vorbereitet sein, nur dann, wenn es absolut erforderlich ist.  
  
 SQL_NULLABLE: Spezielle Spalten zurück, auch wenn sie NULL-Werte haben können.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSpecialColumns** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und eine *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLSpecialColumns** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Die *TableName* Argument wurde ein null-Zeiger.<br /><br /> Das Anweisungsattribut SQL_ATTR_METADATA_ID wurde festgelegt auf SQL_TRUE, die *CatalogName* Argument wurde ein null-Zeiger ist, und die SQL_CATALOG_NAME *Informationsart* gibt zurück, die Namen Katalog werden unterstützt.<br /><br /> (DM) das Anweisungsattribut SQL_ATTR_METADATA_ID wurde Wert auf SQL_TRUE festgelegt, und die *SchemaName* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Diese Funktion war immer noch ausgeführt, wenn **SQLSpecialColumns** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert der eines der Argumente für die Länge ist kleiner als 0, jedoch nicht SQL_NTS gleich.<br /><br /> Der Wert eines der Argumente Länge überschritten, den Wert für die maximale Länge für den entsprechenden Namen. Die maximale Länge des Namens abgerufen werden kann, durch den Aufruf **SQLGetInfo** mit der *Informationsart* Werte: SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN oder SQL_MAX_TABLE_NAME_LEN.|  
|HY097|Spaltentyp außerhalb des gültigen Bereichs|(DM) eine ungültige *IdentifierType* -Wert wurde angegeben.|  
|HY098|Bereichstyp außerhalb des gültigen Bereichs|(DM) eine ungültige *Bereich* -Wert wurde angegeben.|  
|HY099|Nullable-Typs außerhalb des gültigen Bereichs|(DM) eine ungültige *Nullable* -Wert wurde angegeben.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Ein Katalog angegeben wurde, und der Treiber oder die Datenquelle Kataloge nicht unterstützt.<br /><br /> Ein Schema angegeben wurde, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Abfragetimeout abgelaufen, bevor Sie die Datenquelle, die das angeforderte Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Wenn die *IdentifierType* Argument ist SQL_BEST_ROWID, **SQLSpecialColumns** gibt die Spalte oder Spalten, die jede Zeile in der Tabelle eindeutig identifizieren. Diese Spalten können immer verwendet werden, einem *Select-Liste* oder **, in denen** Klausel. **SQLColumns**, die verwendet wird, um eine Vielzahl von Informationen für die Spalten einer Tabelle zurückzugeben ist nicht unbedingt zurück, die Spalten, die jede Zeile eindeutig identifizieren oder Spalten, die automatisch aktualisiert werden, wenn ein in der Zeile Wert wird aktualisiert, indem ein die Transaktion. Z. B. **SQLColumns** möglicherweise nicht die Oracle-Pseudospalte ROWID zurück. Dies ist deshalb **SQLSpecialColumns** wird verwendet, um diese Spalten zurück. Weitere Informationen finden Sie unter [von Katalogdaten verwendet](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Wenn es wurden keine Spalten, die jede Zeile in der Tabelle eindeutig identifizieren **SQLSpecialColumns** gibt ein Rowset mit keine Zeilen zurück, die ein nachfolgender Aufruf von **SQLFetch** oder **SQLFetchScroll**für die Anweisung gibt SQL_NO_DATA zurück.  
  
 Wenn die *IdentifierType*, *Bereich*, oder *Nullable* Argumente geben die Eigenschaften, die von der Datenquelle nicht unterstützt werden **SQLSpecialColumns**  wird ein leeres Resultset zurückgegeben.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist die *CatalogName*, *SchemaName*, und *TableName* Argumente werden als Bezeichner behandelt, daher sie ein null-Zeiger in bestimmten Situationen kann festgelegt werden. (Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).)  
  
 **SQLSpecialColumns** gibt die Ergebnisse als standard Resultset, geordnet nach Bereich zurück.  
  
 Die folgenden Spalten wurden umbenannt ODBC 3.*.x*. Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC 3.*.x* Spalte|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
  
 Um die tatsächliche Länge der COLUMN_NAME-Spalte zu bestimmen, kann eine Anwendung aufrufen **SQLGetInfo** mit der Option SQL_MAX_COLUMN_NAME_LEN.  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 8 (PSEUDO_COLUMN) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf die treiberspezifischen Spalten erhalten, durch eine explizite Ordnungsposition angeben, statt nach unten am Ende des Resultsets gezählt. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|BEREICH (ODBC 1.0)|1|Smallint|Der Bereich der Rowid. Enthält einen der folgenden Werte:<br /><br /> SQL_SCOPE_CURROW SQL_SCOPE_TRANSACTION SQL_SCOPE_SESSION<br /><br /> NULL wird zurückgegeben, wenn *IdentifierType* SQL_ROWVER ist. Eine Beschreibung der einzelnen Werte finden Sie unter der Beschreibung der *Bereich* in "Syntax" weiter oben in diesem Abschnitt.|  
|COLUMN_NAME (ODBC 1.0)|2|Varchar, die nicht NULL|Name der Spalte. Der Treiber gibt eine leere Zeichenfolge für eine Spalte, die nicht über einen Namen verfügt.|  
|DATA_TYPE (ODBC 1.0)|3|Smallint nicht NULL|SQL-Datentyp. Dies kann einen ODBC-SQL-Datentyp oder die treiberspezifischen SQL-Datentyp sein. Eine Liste der gültigen ODBC-SQL-Datentypen, finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md). Informationen zu Treiber-spezifische SQL-Datentypen finden Sie in der vom Treiber-Dokumentation.|  
|TYPE_NAME (ODBC 1.0)|4|Varchar, die nicht NULL|Daten Datenquelle abhängiger Datentypname; z. B. "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY" oder "CHAR () für BIT-Daten".|  
|COLUMN_SIZE (ODBC 1.0)|5|Integer|Die Größe der Spalte in der Datenquelle. Weitere Informationen zu Spalten finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|DIE BUFFER_LENGTH (ODBC 1.0)|6|Integer|Die Länge in Bytes der Datenübertragung auf einen **SQLGetData** oder **SQLFetch** Vorgang, wenn SQL_C_DEFAULT angegeben wird. Für numerische Daten möglicherweise anders als die Größe der in der Datenquelle gespeicherten Daten diese Größe. Dieser Wert ist identisch mit der COLUMN_SIZE-Spalte für Zeichen- oder Binärdaten darstellen. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|DIE DECIMAL_DIGITS (ODBC 1.0)|7|Smallint|Die Dezimalstellen der Spalte in der Datenquelle. NULL wird für Datentypen zurückgegeben, in Dezimalstellen nicht anwendbar sind. Weitere Informationen zu Dezimalstellen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).|  
|PSEUDO_COLUMN (ODBC 2.0)|8|Smallint|Gibt an, ob die Spalte eine Pseudospalte, z. B. Oracle ROWID:<br /><br /> SQL_PC_UNKNOWN SQL_PC_NOT_PSEUDO SQL_PC_PSEUDO **beachten:**  Für eine optimale Interoperabilität Pseudospalten sollte nicht in Anführungszeichen eingeschlossen werden mit dem Bezeichner, die Anführungszeichen vom **SQLGetInfo**.|  
  
 Nachdem die Anwendung Werte für SQL_BEST_ROWID abgerufen hat, kann die Anwendung diese Werte verwenden, auf die Zeile innerhalb des definierten Bereichs erneut auswählen. Die **wählen** Anweisung ist garantiert keine Zeilen oder eine Zeile zurück.  
  
 Wenn eine Anwendung eine Zeile basierend auf der Rowid-Spalte bzw. Spalten reselects aus, und die Zeile wurde nicht gefunden, kann die Anwendung davon ausgehen, dass die Zeile gelöscht wurde oder die Rowid-Spalten geändert wurden. Das Gegenteil trifft nicht: selbst wenn die Rowid nicht geändert wurde, können die anderen Spalten in der Zeile geändert haben.  
  
 Spalten, die für den Spaltentyp SQL_BEST_ROWID sind nützlich für Anwendungen, die der Bildlauf vorwärts und zurück in ein Resultset, die zum Abrufen der neuesten Daten aus einem Satz von Zeilen zurückgegeben werden. Die Spalte oder Spalten der Rowid sind möglicherweise nicht geändert werden, wenn in dieser Zeile.  
  
 Die Spalte oder Spalten der Rowid können gültig bleiben, selbst wenn der Cursor sich nicht auf die Zeile befindet; die Anwendung kann dies durch Prüfen der SCOPE-Spalte im Resultset.  
  
 Spalten, die für den Spaltentyp SQL_ROWVER eignen sich für Anwendungen, die benötigen die Möglichkeit zu überprüfen, ob alle Spalten in einer bestimmten Zeile aktualisiert wurden, während die Zeile mit der Rowid anzeigte wurde, zurückgegeben. Nachdem ein erneuter Aufruf eine Zeile mit der Rowid, kann die Anwendung z. B. die vorherigen Werte in den SQL_ROWVER Spalten mit den gerade abgerufenen vergleichen. Wenn der Wert in einer Spalte SQL_ROWVER vom vorherigen Wert unterscheidet, kann die Anwendung den Benutzer warnen, den Daten in der Anzeige geändert wurde.  
  
## <a name="code-example"></a>Codebeispiel  
 Ein Codebeispiel der eine ähnliche Funktion finden Sie unter [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Spalten in einer Tabelle oder Tabellen|[SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Abrufen einer einzelnen Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben der Spalten eines Primärschlüssels|[SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
