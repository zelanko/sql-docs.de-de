---
title: SQLColumnPrivileges-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColumnPrivileges
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumnPrivileges
helpviewer_keywords:
- SQLColumnPrivileges function [ODBC]
ms.assetid: ef233d9a-6ed5-4986-9d42-5e0b1a79fb6e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7f0cb3edba5fc9bbee9b614c7008d00454778be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800368"
---
# <a name="sqlcolumnprivileges-function"></a>SQLColumnPrivileges-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLColumnPrivileges** gibt eine Liste von Spalten und den zugeordneten Berechtigungen für die angegebene Tabelle zurück. Der Treiber gibt zurück, die Informationen, die als Resultset für das angegebene *StatementHandle*.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLColumnPrivileges(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *Katalogname*  
 [Eingabe] Name des Katalogs. Wenn ein Treiber Namen unterstützt, für einige Kataloge für andere jedoch nicht, wie z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") bezeichnet die Kataloge, die keine Namen aufweisen. *CatalogName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *CatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *CatalogName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen des **CatalogName*.  
  
 *SchemaName*  
 [Eingabe] Name des Schemas. Wenn ein Treiber unterstützt die Schemas für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, die keine Schemas aufweisen. *SchemaName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *SchemaName* wird als Bezeichner behandelt. Ist dies SQL_FALSE, *SchemaName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen des **SchemaName*.  
  
 *TableName*  
 [Eingabe] Name der Tabelle. Dieses Argument darf nicht null-Zeiger sein. *TableName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *TableName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *TableName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen des **TableName*.  
  
 *Spaltenname*  
 [Eingabe] Eine Zeichenfolge Suchmuster für den Spaltennamen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *ColumnName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *ColumnName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength4*  
 [Eingabe] Länge in Zeichen des **ColumnName*.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLColumnPrivileges** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und ein *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLColumnPrivileges** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der vom Treiber zurückgegebene SQLSTATEs -Manager. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle,* und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Die *TableName* Argument wurde ein null-Zeiger.<br /><br /> Das Anweisungsattribut SQL_ATTR_METADATA_ID wurde festgelegt auf SQL_TRUE, die *CatalogName* Argument wurde ein null-Zeiger ist, und die SQL_CATALOG_NAME *Informationsart* gibt zurück, die Namen Katalog werden unterstützt.<br /><br /> (DM) das Anweisungsattribut SQL_ATTR_METADATA_ID wurde Wert auf SQL_TRUE festgelegt, und die *SchemaName* oder *ColumnName* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Diese asynchronen Funktion war immer noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert eines der Argumente Länge Name war kleiner als 0, jedoch nicht SQL_NTS gleich.|  
|||Der Wert eines der Argumente Namen Länge überschritten Wert für maximale Länge für den entsprechenden Namen. (Siehe "Kommentare".)|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Ein Katalogname wurde angegeben, und der Treiber oder die Datenquelle Kataloge nicht unterstützt.<br /><br /> Ein Schemaname angegeben wurde, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Ein Suchmuster für die Zeichenfolge, die für den Namen der Spalte angegeben wurde, und die Datenquelle unterstützt nicht das Suchmuster für dieses Argument.<br /><br /> Die Kombination aus der aktuellen Einstellungen der Anweisungsattribute SQL_CONCURRENCY und SQL_CURSOR_TYPE wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLColumnPrivileges** gibt die Ergebnisse als standard Resultset, nach TABLE_CAT, nach "TABLE_SCHEM", TABLE_NAME, COLUMN_NAME und PRIVILEGE sortiert zurück.  
  
> [!NOTE]  
>  **SQLColumnPrivileges** möglicherweise keine Berechtigungen für alle Spalten zurück. Beispielsweise kann ein Treiber nicht auf Informationen zu Berechtigungen für Pseudo-Spalten, z. B. Oracle ROWID zurück. Anwendungen können eine beliebige gültige Spalte, unabhängig davon, ob sie von zurückgegeben wird **SQLColumnPrivileges**.  
  
 Die Länge der VARCHAR-Spalten werden nicht in der Tabelle angezeigt; die tatsächliche Länge hängt von der Datenquelle ab. Um zu bestimmen, die tatsächliche Länge der Spalten CATALOG_NAME, SCHEMA_NAME, Tabellenname und Spaltenname, eine Anwendung aufrufen kann **SQLGetInfo** mit der SQL_MAX_TABLE_NAME_ SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, LEN und SQL_MAX_COLUMN_NAME_LEN-Optionen.  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Die folgenden Spalten wurden umbenannt, ODBC 3. *x*. Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC 3. *x* Spalte|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 8 (IS_GRANTABLE) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf die treiberspezifischen Spalten erhalten, durch eine explizite Ordnungsposition angeben, statt nach unten am Ende des Resultsets gezählt. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Katalog-Bezeichner. NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Kataloge für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, denen keine Kataloge.|  
|NACH "TABLE_SCHEM" (ODBC 1.0)|2|Varchar|Schemabezeichner. NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Schemas für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, die keine Schemas aufweisen.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar, die nicht NULL|Bezeichner der Tabelle.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar, die nicht NULL|Name der Spalte. Der Treiber gibt eine leere Zeichenfolge für eine Spalte, die nicht über einen Namen verfügt.|  
|DER BERECHTIGENDE (ODBC 1.0)|5|Varchar|Name des Benutzers, der die Berechtigung gewährt werden soll; NULL, wenn Sie mit der Datenquelle nicht anwendbar.<br /><br /> Für alle Zeilen in denen der Wert in der Spalte für die Empfänger der Besitzer des Objekts ist, werden die GRANTOR-Spalte "_SYSTEM".|  
|EMPFÄNGER (ODBC 1.0)|6|Varchar, die nicht NULL|Der Name des Benutzers, dem die Berechtigung erteilt wurde.|  
|BERECHTIGUNGEN (ODBC 1.0)|7|Varchar, die nicht NULL|Gibt die Berechtigung für die Spalte an. Kann einen der folgenden sein (oder andere durch die Daten unterstützt Datenquelle implementierungsdefinierte):<br /><br /> Wählen Sie aus: Der Empfänger ist zum Abrufen von Daten für die Spalte zulässig.<br /><br /> INSERT: Der Empfänger ist zulässig, Daten für die Spalte in neue Zeilen bereitstellen, die in der zugeordneten Tabelle eingefügt werden.<br /><br /> UPDATE: Der Empfänger ist zum Aktualisieren von Daten in der Spalte zulässig.<br /><br /> Verweise: Der Empfänger ist zum Verweisen auf die Spalte in einer Einschränkung zulässig (z. B. einen eindeutigen, referenzielle, oder eine Tabelle, die check-Einschränkung).|  
|IS_GRANTABLE (ODBC 1.0)|8|Varchar|Gibt an, ob der Empfänger berechtigt ist, auf die Berechtigung, anderen Benutzern zu gewähren. "YES", "Nein" oder "NULL", wenn unbekannt oder nicht anwendbar ist, mit der Datenquelle.<br /><br /> Eine Berechtigung ist entweder Berechtigung gewährt werden kann oder nicht die Berechtigung gewährt werden kann, aber nicht beides. Das Resultset zurückgegebenes **SQLColumnPrivileges** enthält niemals zwei Zeilen, die für die alle Spalten außer der IS_GRANTABLE-Spalte den gleichen Wert enthalten.|  
  
## <a name="code-example"></a>Codebeispiel  
 Ein Codebeispiel der eine ähnliche Funktion finden Sie unter [SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Spalten in einer Tabelle oder Tabellen|[SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen mehrerer Zeilen von Daten|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Zurückgeben von Berechtigungen für eine Tabelle oder Tabellen|[SQLTablePrivileges-Funktion](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
|Zurückgeben einer Liste von Tabellen in einer Datenquelle|[SQLTables-Funktion](../../../odbc/reference/syntax/sqltables-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
