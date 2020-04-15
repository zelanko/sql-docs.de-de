---
title: SQLTables-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae52e6431679ed0f260e6885090ac38363b4ef3d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287130"
---
# <a name="sqltables-function"></a>SQLTables-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0 Standards Compliance: Open Group  
  
 **Zusammenfassung**  
 **SQLTables** gibt die Liste der Tabellen-, Katalog- oder Schemanamen und Tabellentypen zurück, die in einer bestimmten Datenquelle gespeichert sind. Der Treiber gibt die Informationen als Ergebnissatz zurück.  
  
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
 [Eingabe] Anweisungshandle für abgerufene Ergebnisse.  
  
 *Catalogname*  
 [Eingabe] Katalogname. Das *Argument CatalogName* akzeptiert Suchmuster, wenn das SQL_ODBC_VERSION Umgebungsattribut SQL_OV_ODBC3 ist. Es akzeptiert keine Suchmuster, wenn SQL_OV_ODBC2 festgelegt ist. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn ein Treiber Daten aus verschiedenen DBMS abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Kataloge haben.  
  
 Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE, ist *CatalogName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen von **CatalogName*.  
  
 *Schemaname*  
 [Eingabe] Zeichenfolgensuchmuster für Schemanamen. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas haben.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *SchemaName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *SchemaName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen von **SchemaName*.  
  
 *TableName*  
 [Eingabe] Zeichenfolgensuchmuster für Tabellennamen.  
  
 Wenn das SQL_ATTR_METADATA_ID Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *TableName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE, ist *TableName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen von **TableName*.  
  
 *TableType*  
 [Eingabe] Liste der übereinstimmenden Tabellentypen.  
  
 Beachten Sie, dass das SQL_ATTR_METADATA_ID-Anweisungsattribut keine Auswirkungen auf das *TableType-Argument* hat. *TableType* ist ein Argument für die Wertliste, unabhängig von der Einstellung SQL_ATTR_METADATA_ID.  
  
 *NameLength4*  
 [Eingabe] Länge in Zeichen von **TableType*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLTables** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von SQLTables zurückgegeben werden, und es werden die **SQLSTATE-Werte** im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|24.000|Ungültiger Cursorstatus|Im *StatementHandle*wurde ein Cursor geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat und vom Treiber zurückgegeben wird, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Im *StatementHandle*wurde ein Cursor geöffnet, **SQLFetch** oder **SQLFetchScroll** wurden jedoch nicht aufgerufen.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcendeadlocks mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das attribut SQL_ATTR_METADATA_ID Anweisung wurde auf SQL_TRUE festgelegt, das *Argument CatalogName* war ein Nullzeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) Das SQL_ATTR_METADATA_ID-Anweisungsattribut wurde auf SQL_TRUE festgelegt, und das *Argument SchemaName* oder *TableName* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als SQLTables aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der Wert eines der Längenargumente war kleiner als 0, aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der Namenslängenargumente hat den maximalen Längenwert für den entsprechenden Namen überschritten.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Es wurde ein Katalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Für den Katalognamen, das Tabellenschema oder den Tabellennamen wurde ein Zeichenfolgensuchmuster angegeben, und die Datenquelle unterstützt keine Suchmuster für eines oder mehrere dieser Argumente.<br /><br /> Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLTables** listet alle Tabellen im angeforderten Bereich auf. Ein Benutzer kann über SELECT-Berechtigungen für eine dieser Tabellen verfügen oder auch nicht. Um die Barrierefreiheit zu überprüfen, kann eine Anwendung:  
  
-   Rufen Sie **SQLGetInfo** auf, und überprüfen Sie den SQL_ACCESSIBLE_TABLES-Informationstyp.  
  
-   Rufen Sie **SQLTablePrivileges** auf, um die Berechtigungen für jede Tabelle zu überprüfen.  
  
 Andernfalls muss die Anwendung in der Lage sein, eine Situation zu behandeln, in der der Benutzer eine Tabelle auswählt, für die **keine SELECT-Berechtigungen** gewährt werden.  
  
 Die Argumente *SchemaName* und *TableName* akzeptieren Suchmuster. Das *Argument CatalogName* akzeptiert Suchmuster, wenn das SQL_ODBC_VERSION Umgebungsattribut SQL_OV_ODBC3 ist. Es akzeptiert keine Suchmuster, wenn SQL_OV_ODBC2 festgelegt ist. Wenn SQL_OV_ODBC3 festgelegt ist, erfordert ein ODBC 3 *.x-Treiber,* dass Platzhalterzeichen im *CatalogName-Argument* mit escapeigungszeichen versehen werden, um buchstäblich behandelt zu werden. Weitere Informationen zu gültigen Suchmustern finden Sie unter [Pattern Value Arguments](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Weitere Informationen zur allgemeinen Verwendung, Argumente und zurückgegebenen Daten von ODBC-Katalogfunktionen finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Um die Enumeration von Katalogen, Schemas und Tabellentypen zu unterstützen, werden die folgenden speziellen Semantik-Codes für die Argumente *CatalogName*, *SchemaName*, *TableName*und *TableType* von **SQLTables**definiert:  
  
-   Wenn *CatalogName* SQL_ALL_CATALOGS und *SchemaName* und *TableName* leere Zeichenfolgen sind, enthält das Resultset eine Liste gültiger Kataloge für die Datenquelle. (Alle Spalten außer der TABLE_CAT Spalte enthalten NULLs.)  
  
-   Wenn *SchemaName* SQL_ALL_SCHEMAS und *CatalogName* und *TableName* leere Zeichenfolgen sind, enthält das Resultset eine Liste gültiger Schemas für die Datenquelle. (Alle Spalten außer der TABLE_SCHEM Spalte enthalten NULLs.)  
  
-   Wenn *TableType* SQL_ALL_TABLE_TYPES und *CatalogName*, *SchemaName*und *TableName* leere Zeichenfolgen sind, enthält das Resultset eine Liste gültiger Tabellentypen für die Datenquelle. (Alle Spalten mit Ausnahme der TABLE_TYPE Spalte enthalten NULLs.)  
  
 Wenn *TableType* keine leere Zeichenfolge ist, muss sie eine Liste von durch Kommas getrennten Werten für die Interessentypen enthalten. jeder Wert kann in einfache Anführungszeichen (') oder nicht zitiert werden, z. B. 'TABLE', 'VIEW' oder TABLE, VIEW. Eine Anwendung sollte immer den Tabellentyp in Großbuchstaben angeben. Der Treiber sollte den Tabellentyp in den gewünschten Fall konvertieren, der von der Datenquelle benötigt wird. Wenn die Datenquelle keinen angegebenen Tabellentyp unterstützt, gibt **SQLTables** keine Ergebnisse für diesen Typ zurück.  
  
 **SQLTables** gibt die Ergebnisse als Standardergebnissatz zurück, sortiert nach TABLE_TYPE, TABLE_CAT, TABLE_SCHEM und TABLE_NAME. Informationen zur Verwendung dieser Informationen finden Sie unter [Verwendung von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Um die tatsächlichen Längen der Spalten TABLE_CAT, TABLE_SCHEM und TABLE_NAME zu bestimmen, kann eine Anwendung **SQLGetInfo** mit den SQL_MAX_CATALOG_NAME_LEN-, SQL_MAX_SCHEMA_NAME_LEN- und SQL_MAX_TABLE_NAME_LEN-Informationstypen aufrufen.  
  
 Die folgenden Spalten wurden für ODBC 3 *.x*umbenannt. Die Änderungen des Spaltennamens wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer binden.  
  
|ODBC 2.0-Säule|ODBC 3 *.x-Säule*|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 In der folgenden Tabelle sind die Spalten im Resultset aufgeführt. Zusätzliche Spalten jenseits von Spalte 5 (REMARKS) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifische Spalten erhalten, indem sie vom Ende des Resultsets herunterzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Katalogname; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für tabellen zurück, die keine Kataloge haben.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Schemaname; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für Tabellen zurück, die keine Schemas haben.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar|Tabellenname.|  
|TABLE_TYPE (ODBC 1.0)|4|Varchar|Tabellentypname; einer der folgenden Optionen: "TABLE", "VIEW", "SYSTEM TABLE", "GLOBAL TEMPORARY", "LOCAL TEMPORARY", "ALIAS", "SYNONYM" oder ein datenquellenspezifischer Typname.<br /><br /> Die Bedeutungen von "ALIAS" und "SYNONYM" sind treiberspezifisch.|  
|BEMERKUNGEN (ODBC 1.0)|5|Varchar|Eine Beschreibung der Tabelle.|  
  
## <a name="example"></a>Beispiel  
 Der folgende Beispielcode gibt keine Handles und Verbindungen frei. Siehe [SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md) und [SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md) für Codebeispiele zum Freiwerden von Handles und Anweisungen.  
  
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
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Berechtigungen für eine Spalte oder Spalten|[SQLColumnPrivileges-Funktion](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Zurückgeben der Spalten in einer Tabelle oder Tabellen|[SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in einer vorwärtsgerichteten Richtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben von Tabellenstatistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Zurückgeben von Berechtigungen für eine Tabelle oder Tabellen|[SQLTablePrivileges-Funktion](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
