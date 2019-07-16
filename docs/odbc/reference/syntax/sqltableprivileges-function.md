---
title: SQLTablePrivileges-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTablePrivileges
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTablePrivileges
helpviewer_keywords:
- SQLTablePrivileges function [ODBC]
ms.assetid: 8cfdb64f-64c5-47e6-ad57-0533ac630afa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e63677180cc86f022550477bd598eaa61013d694
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039519"
---
# <a name="sqltableprivileges-function"></a>SQLTablePrivileges-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLTablePrivileges** gibt eine Liste von Tabellen und die Berechtigungen, die jeder Tabelle zugeordneten zurück. Der Treiber gibt zurück, die Informationen, die als Resultset auf der angegebenen Anweisung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLTablePrivileges(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *Katalogname*  
 [Eingabe] Der Tabellenkatalog Wenn ein Treiber unterstützt die Kataloge für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, denen keine Kataloge. *CatalogName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *CatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *CatalogName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen des **CatalogName*.  
  
 *SchemaName*  
 [Eingabe] Zeichenfolge Suchmuster für den Schemanamen an. Wenn ein Treiber unterstützt die Schemas für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, die keine Schemas aufweisen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *SchemaName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *SchemaName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen des **SchemaName*.  
  
 *TableName*  
 [Eingabe] Eine Zeichenfolge Suchmuster für den Tabellennamen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *TableName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *TableName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen des **TableName*.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLTablePrivileges** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und ein *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLTablePrivileges** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben . Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die **SQLTablePrivileges** Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die  *StatementHandle*. Die **SQLTablePrivileges** Funktion wurde erneut aufgerufen, auf die *StatementHandle*.<br /><br /> Die **SQLTablePrivileges** Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die  *StatementHandle* von einem anderen Thread in einer multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Das Anweisungsattribut SQL_ATTR_METADATA_ID wurde festgelegt auf SQL_TRUE, die *CatalogName* Argument wurde ein null-Zeiger ist, und die SQL_CATALOG_NAME *Informationsart* gibt zurück, die Namen Katalog werden unterstützt.<br /><br /> (DM) das Anweisungsattribut SQL_ATTR_METADATA_ID wurde Wert auf SQL_TRUE festgelegt, und die *SchemaName* oder *TableName* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLTablePrivileges** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert eines der Argumente Länge Name war kleiner als 0, jedoch nicht SQL_NTS gleich.<br /><br /> Der Wert eines der Argumente Namen Länge überschritten Wert für maximale Länge für die entsprechenden Qualifizierer oder den Namen.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum Zustand "angehalten" [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Ein Katalog angegeben wurde, und der Treiber oder die Datenquelle Kataloge nicht unterstützt.<br /><br /> Ein Schema angegeben wurde, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Ein Suchmuster für die Zeichenfolge, die für die Tabellenschema, Tabellenname und Spaltenname angegeben wurde, und die Datenquelle unterstützt nicht das Suchmuster für eine oder mehrere dieser Argumente.<br /><br /> Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Die *SchemaName* und *TableName* Argumente akzeptieren Suchmuster. Weitere Informationen zu gültigen Suchmuster, finden Sie unter [Musterwerts](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
 **SQLTablePrivileges** gibt die Ergebnisse als ein standard, geordnet nach TABLE_CAT, nach "TABLE_SCHEM", Tabellenname, Berechtigungen und Empfänger Resultset zurück.  
  
 Um die tatsächliche Länge der Spalten TABLE_CAT, nach "TABLE_SCHEM" und TABLE_NAME zu bestimmen, kann eine Anwendung aufrufen **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN SQL_MAX_SCHEMA_NAME_LEN und SQL_MAX_TABLE_NAME_LEN.  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Die folgenden Spalten wurden umbenannt für ODBC *3.x*. Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC *3.x* Spalte|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 7 (IS_GRANTABLE) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf die treiberspezifischen Spalten erhalten, durch eine explizite Ordnungsposition angeben, statt nach unten am Ende des Resultsets gezählt. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Name des Katalogs; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Kataloge für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, denen keine Kataloge.|  
|NACH "TABLE_SCHEM" (ODBC 1.0)|2|Varchar|Schemanamen; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Schemas für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, die keine Schemas aufweisen.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar, die nicht NULL|Tabellenname.|  
|DER BERECHTIGENDE (ODBC 1.0)|4|Varchar|Name des Benutzers, der die Berechtigung gewährt werden soll; NULL, wenn Sie mit der Datenquelle nicht anwendbar.<br /><br /> Für alle Zeilen in denen der Wert in der Spalte für die Empfänger der Besitzer des Objekts ist, werden die GRANTOR-Spalte "_SYSTEM".|  
|EMPFÄNGER (ODBC 1.0)|5|Varchar, die nicht NULL|Der Name des Benutzers, dem die Berechtigung erteilt wurde.|  
|BERECHTIGUNGEN (ODBC 1.0)|6|Varchar, die nicht NULL|Die Table-Berechtigung. Dabei kann es sich um eine der folgenden Werte oder die Berechtigungen einer Daten-datenquellenspezifische sein.<br /><br /> WÄHLEN SIE AUS: Der Empfänger ist zum Abrufen von Daten für eine oder mehrere Spalten der Tabelle zulässig.<br /><br /> FÜGEN SIE EIN: Der Empfänger ist zulässig, um neue Zeilen, die mit den Daten für eine oder mehrere Spalten in die Tabelle einzufügen.<br /><br /> UPDATE: Der Empfänger ist zulässig, um die Daten in einer oder mehreren Spalten der Tabelle zu aktualisieren.<br /><br /> LÖSCHEN: Der Empfänger ist zulässig, um Zeilen mit Daten aus der Tabelle zu löschen.<br /><br /> VERWEISE: Der Empfänger ist zum Verweisen auf eine oder mehrere Spalten der Tabelle eine Einschränkung zulässig (z. B. einen eindeutigen, referenzielle, oder eine Tabelle, die check-Einschränkung).<br /><br /> Der Bereich der Aktion, die den Empfänger durch ein bestimmtes Tabellenprivileg zugelassen ist datenquellenabhängig. Beispielsweise kann die UPDATE-Privileg der GRANTEE aktualisieren alle Spalten in einer Tabelle für eine Datenquelle und nur die Spalten, die für die der berechtigende (Grantor) für eine andere Datenquelle die UPDATE-Privileg besitzt.|  
|IS_GRANTABLE (ODBC 1.0)|7|Varchar|Gibt an, ob der Empfänger berechtigt ist, auf die Berechtigung, anderen Benutzern zu gewähren. "YES", "Nein", oder NULL, wenn unbekannt oder nicht anwendbar ist, mit der Datenquelle.<br /><br /> Eine Berechtigung ist die Berechtigung gewährt werden kann oder keine erteilbaren, aber nicht beides. Das Resultset zurückgegebenes **SQLColumnPrivileges** enthält niemals zwei Zeilen, die für die alle Spalten außer der IS_GRANTABLE-Spalte den gleichen Wert enthalten.|  
  
## <a name="code-example"></a>Codebeispiel  
 Ein Codebeispiel der eine ähnliche Funktion finden Sie unter [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Berechtigungen für eine oder mehrere Spalten|[SQLColumnPrivileges-Funktion](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Zurückgeben von Spalten in einer Tabelle oder Tabellen|[SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Abrufen einer einzelnen Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben von Statistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Zurückgeben einer Liste von Tabellen in einer Datenquelle|[SQLTables-Funktion](../../../odbc/reference/syntax/sqltables-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
