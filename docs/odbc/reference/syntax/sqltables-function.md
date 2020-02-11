---
title: SQLTables-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTables
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTables
helpviewer_keywords:
- SQLTables function [ODBC]
ms.assetid: 60d5068a-7d7c-447c-acc6-f3f2cf73440c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e99dd2f5cf3186120297d7679f87e973d5164a57
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039529"
---
# <a name="sqltables-function"></a>SQLTables-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: Open Group  
  
 **Zusammenfassung**  
 **SQLTables** gibt die Liste der Tabellen-, Katalog-oder Schema Namen sowie Tabellentypen zurück, die in einer bestimmten Datenquelle gespeichert sind. Der Treiber gibt die Informationen als Resultset zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLTables(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      TableType,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle für abgerufene Ergebnisse.  
  
 *CatalogName*  
 Der Katalog Name. Das *CatalogName* -Argument akzeptiert Suchmuster, wenn das SQL_ODBC_VERSION-Umgebungs Attribut SQL_OV_ODBC3 ist. Wenn SQL_OV_ODBC2 festgelegt ist, werden Suchmuster nicht akzeptiert. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. Wenn ein Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die nicht über Kataloge verfügen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *CatalogName* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Der Länge in Zeichen von **CatalogName*.  
  
 *Schema Name*  
 Der Zeichen folgen Suchmuster für Schema Namen. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas aufweisen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird Schema *Name* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist Schema *Name* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength2*  
 Der Länge in Zeichen von * Schema*Name*.  
  
 *TableName*  
 Der Zeichen folgen Suchmuster für Tabellennamen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *TableName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist *TableName* ein Muster Wert Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength3*  
 Der Länge in Zeichen von **TableName*.  
  
 *TableType*  
 Der Liste der zu Übereinstimmungs enden Tabellentypen.  
  
 Beachten Sie, dass das SQL_ATTR_METADATA_ID Statement-Attribut keine Auswirkung auf das *TABLETYPE* -Argument hat. *TABLETYPE* ist ein Wert Listen Argument, unabhängig von der Einstellung SQL_ATTR_METADATA_ID.  
  
 *NameLength4*  
 Der Länge in Zeichen von **TABLETYPE*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLTables** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle werden die SQLSTATE-Werte aufgelistet, die in der Regel von **SQLTables** zurückgegeben werden, und jede im Kontext dieser Funktion wird erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben wurde und vom Treiber zurückgegeben wird, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor war auf dem *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde ein Rollback ausgeführt, weil ein Ressourcen Deadlock mit einer anderen Transaktion aufgetreten ist.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, das *CatalogName* -Argument war ein NULL-Zeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, und das Schema *Name* -oder *TableName* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als "SQLTables" aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der Wert eines Längen Arguments ist kleiner als 0 (null), aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der namens Längen Argumente hat den maximalen Längen Wert für den entsprechenden Namen überschritten.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Es wurde ein Katalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Für den Katalognamen, das Tabellen Schema oder den Tabellennamen wurde ein Zeichen folgen Suchmuster angegeben, und die Datenquelle unterstützt keine Suchmuster für mindestens ein Argument.<br /><br /> Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLTables** listet alle Tabellen im angeforderten Bereich auf. Ein Benutzer verfügt möglicherweise über SELECT-Berechtigungen für diese Tabellen. Zum Überprüfen der Barrierefreiheit kann eine Anwendung folgende Aktionen ausführen:  
  
-   Aufrufen von **SQLGetInfo** und Überprüfen des SQL_ACCESSIBLE_TABLES-Informations Typs.  
  
-   Wenden Sie **SQLTablePrivileges** an, um die Berechtigungen für jede Tabelle zu überprüfen.  
  
 Andernfalls muss die Anwendung in der Lage sein, eine Situation zu behandeln, in der der Benutzer eine Tabelle auswählt, für die keine **Select** -Berechtigungen erteilt wurden.  
  
 Die *SchemaName* -und *TableName* -Argumente akzeptieren Suchmuster. Das *CatalogName* -Argument akzeptiert Suchmuster, wenn das SQL_ODBC_VERSION-Umgebungs Attribut SQL_OV_ODBC3 ist. Wenn SQL_OV_ODBC2 festgelegt ist, werden Suchmuster nicht akzeptiert. Wenn SQL_OV_ODBC3 festgelegt ist, erfordert ein ODBC 3 *. x* -Treiber, dass Platzhalter Zeichen im *CatalogName* -Argument mit Escapezeichen versehen werden, damit Sie buchstäblich behandelt werden. Weitere Informationen zu gültigen Suchmustern finden Sie unter [Muster Wert Argumente](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumente und zurückgegebene Daten von ODBC-Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Zur Unterstützung der Enumeration von Katalogen, Schemas und Tabellentypen wird die folgende besondere Semantik für die Argumente *CatalogName*, *Schema*Name, *TableName*und *TABLETYPE* von **SQLTables**definiert:  
  
-   Wenn *CatalogName* SQL_ALL_CATALOGS und *SchemaName* und *TableName* leere Zeichen folgen sind, enthält das Resultset eine Liste gültiger Kataloge für die Datenquelle. (Alle Spalten außer der Spalte TABLE_CAT enthalten NULL-Zeichen.)  
  
-   Wenn *Schema* Name SQL_ALL_SCHEMAS und *CatalogName* und *TableName* leere Zeichen folgen sind, enthält das Resultset eine Liste gültiger Schemas für die Datenquelle. (Alle Spalten außer der Spalte TABLE_SCHEM enthalten NULL-Zeichen.)  
  
-   Wenn *TABLETYPE* SQL_ALL_TABLE_TYPES und *CatalogName* *, Schema*Name und *TableName* leere Zeichen folgen sind, enthält das Resultset eine Liste gültiger Tabellentypen für die Datenquelle. (Alle Spalten außer der Spalte TABLE_TYPE enthalten NULL-Zeichen.)  
  
 Wenn *TABLETYPE* keine leere Zeichenfolge ist, muss Sie eine Liste von durch Trennzeichen getrennten Werten für die interessanten Typen enthalten. Jeder Wert kann in einfache Anführungszeichen (') oder nicht in Anführungszeichen eingeschlossen werden, z. b. "Table", "View" oder "Table", "View". Eine Anwendung sollte immer den Tabellentyp in Großbuchstaben angeben. der Treiber sollte den Tabellentyp in den von der Datenquelle benötigten Fall konvertieren. Wenn die Datenquelle einen angegebenen Tabellentyp nicht unterstützt, gibt **SQLTables** keine Ergebnisse für diesen Typ zurück.  
  
 **SQLTables** gibt die Ergebnisse als Standardresultset zurück, geordnet nach TABLE_TYPE, TABLE_CAT, TABLE_SCHEM und TABLE_NAME. Informationen dazu, wie diese Informationen verwendet werden können, finden Sie unter [Verwenden von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Zum Bestimmen der tatsächlichen Längen der Spalten TABLE_CAT, TABLE_SCHEM und table_name kann eine Anwendung **SQLGetInfo** mit den Informationstypen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN und SQL_MAX_TABLE_NAME_LEN aufrufen.  
  
 Die folgenden Spalten wurden für ODBC 3 *. x*umbenannt. Die Spaltennamen Änderungen wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer gebunden werden.  
  
|ODBC 2,0-Spalte|ODBC 3 *. x* -Spalte|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 In der folgenden Tabelle werden die Spalten im Resultset aufgelistet. Zusätzliche Spalten, die über die Spalte 5 hinausgehen (Hinweise), können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf Treiber spezifische Spalten erhalten, indem Sie vom Ende des Resultsets abzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1,0)|1|Varchar|Katalog Name; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Tabellen zurückgegeben, die über keine Kataloge verfügen.|  
|TABLE_SCHEM (ODBC 1,0)|2|Varchar|Schema Name; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für Tabellen zurückgegeben, die keine Schemas aufweisen.|  
|Table_name (ODBC 1,0)|3|Varchar|Tabellenname.|  
|TABLE_TYPE (ODBC 1,0)|4|Varchar|Tabellentyp Name; eines der folgenden: "Table", "View", "System Table", "Global Temporary", "LOCAL TEMPORARY", "Alias", "Synonym" oder ein Datenquellen spezifischer Typname.<br /><br /> Die Bedeutung von "Alias" und "Synonym" sind Treiber spezifisch.|  
|Hinweise (ODBC 1,0)|5|Varchar|Eine Beschreibung der Tabelle.|  
  
## <a name="example"></a>Beispiel  
 Der folgende Beispielcode gibt keine Handles und Verbindungen frei. Codebeispiele zum Freigeben von Handles und Anweisungen finden Sie unter [SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md) und [SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md) .  
  
```cpp  
// SQLTables.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
// simple helper functions  
int MySQLSuccess(SQLRETURN rc) {  
   return (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO);  
}  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printCatalog(const struct DataBinding* catalogResult) {  
   if (catalogResult[0].StrLen_or_Ind != SQL_NULL_DATA)   
      printf("Catalog Name = %s\n", (char *)catalogResult[0].TargetValuePtr);  
}  
  
// remember to disconnect and free memory, and free statements and handles  
int main() {  
   int bufferSize = 1024, i, numCols = 5;  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   wchar_t* dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   wchar_t* userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR*)"Driver={SQL Server}", SQL_NTS, (SQLCHAR*)connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
  
   bufferSize = 1024;  
  
   // allocate memory for the binding  
   // free this memory when done  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // setup the binding (can be used even if the statement is closed by closeStatementHandle)  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   // all catalogs query  
   printf( "A list of names of all catalogs\n" );  
   retCode = SQLTables( hstmt, (SQLCHAR*)SQL_ALL_CATALOGS, SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS );  
   for ( retCode = SQLFetch(hstmt) ;  MySQLSuccess(retCode) ; retCode = SQLFetch(hstmt) )  
      printCatalog( catalogResult );  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Berechtigungen für eine Spalte oder Spalten|[SQLColumnPrivileges-Funktion](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Zurückgeben der Spalten in einer Tabelle oder in Tabellen|[SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben von Tabellenstatistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Zurückgeben von Berechtigungen für eine Tabelle oder Tabellen|[SQLTablePrivileges-Funktion](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
