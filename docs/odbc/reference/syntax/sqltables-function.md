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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039529"
---
# <a name="sqltables-function"></a>SQLTables-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: Gruppe öffnen  
  
 **Zusammenfassung**  
 **SQLTables** gibt die Liste der Namen von Tabellen, -Katalogs oder Schemas und Tabellentypen, die in einer bestimmten Datenquelle gespeichert. Der Treiber gibt zurück, die Informationen als Resultset.  
  
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
 [Eingabe] Anweisungshandle für die abgerufenen Ergebnisse.  
  
 *Katalogname*  
 [Eingabe] Name des Katalogs. Die *CatalogName* Argument akzeptiert Suchmuster ist umgebungsattributs SQL_ODBC_VERSION SQL_OV_ODBC3 fest; Suchmuster werden nicht akzeptiert, wenn SQL_OV_ODBC2 festgelegt ist. Wenn Sie ein Treiber unterstützt die Kataloge für einige Tabellen jedoch nicht für andere, z. B. wenn ein Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge abruft ("") gibt an, die Tabellen, denen keine Kataloge.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *CatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *CatalogName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen des **CatalogName*.  
  
 *SchemaName*  
 [Eingabe] Zeichenfolge Suchmuster für den Schemanamen an. Wenn ein Treiber unterstützt die Schemas für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") gibt an, die Tabellen, die keine Schemas aufweisen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *SchemaName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *SchemaName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen des **SchemaName*.  
  
 *TableName*  
 [Eingabe] Eine Zeichenfolge Suchmuster für den Tabellennamen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *TableName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *TableName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen des **TableName*.  
  
 *TableType*  
 [Eingabe] Liste der Tabelle übereinstimmen.  
  
 Beachten Sie, dass das Anweisungsattribut SQL_ATTR_METADATA_ID keine Auswirkungen auf die *TableType* Argument. *TableType* ist ein Argument des Wert-Liste, unabhängig von der Einstellung der SQL_ATTR_METADATA_ID.  
  
 *NameLength4*  
 [Eingabe] Länge in Zeichen des **TableType*.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLTables** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLTables** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde wegen eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Das Anweisungsattribut SQL_ATTR_METADATA_ID wurde festgelegt auf SQL_TRUE, die *CatalogName* Argument wurde ein null-Zeiger ist, und die SQL_CATALOG_NAME *Informationsart* gibt zurück, die Namen Katalog werden unterstützt.<br /><br /> (DM) das Anweisungsattribut SQL_ATTR_METADATA_ID wurde Wert auf SQL_TRUE festgelegt, und die *SchemaName* oder *TableName* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn SQLTables aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert der eines der Argumente für die Länge ist kleiner als 0, jedoch nicht SQL_NTS gleich.<br /><br /> Der Wert eines der Argumente Namen Länge überschritten Wert für maximale Länge für den entsprechenden Namen.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Ein Katalog angegeben wurde, und der Treiber oder die Datenquelle Kataloge nicht unterstützt.<br /><br /> Ein Schema angegeben wurde, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Ein Suchmuster Zeichenfolge wurde der Name des Katalogs Tabellenschema oder Tabellenname angegeben, und die Datenquelle unterstützt nicht das Suchmuster für eine oder mehrere dieser Argumente.<br /><br /> Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Abfragetimeout abgelaufen, bevor Sie die Datenquelle, die das angeforderte Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLTables** Listet alle Tabellen im angeforderten Bereich. Ein Benutzer kann, oder es kann keine SELECT-Privilegien auf eine der beiden Tabellen. Um Zugriff zu überprüfen, können eine Anwendung:  
  
-   Rufen Sie **SQLGetInfo** und überprüfen Sie den Typ der SQL_ACCESSIBLE_TABLES-Informationen.  
  
-   Rufen Sie **SQLTablePrivileges** , überprüfen Sie die Berechtigungen für jede Tabelle.  
  
 Andernfalls muss die Anwendung kann mit der jeweiligen Situation, in denen der Benutzer eine Tabelle, für die wählt **wählen** Berechtigungen nicht erteilt wurden.  
  
 Die *SchemaName* und *TableName* Argumente akzeptieren Suchmuster. Die *CatalogName* Argument akzeptiert Suchmuster ist umgebungsattributs SQL_ODBC_VERSION SQL_OV_ODBC3 fest; Suchmuster werden nicht akzeptiert, wenn SQL_OV_ODBC2 festgelegt ist. Wenn SQL_OV_ODBC3 festgelegt ist, wird eine ODBC 3. *.x* Treiber benötigen, Platzhalterzeichen den *CatalogName* -Argument werden mit Escapezeichen versehen, um als Literalzeichen behandelt werden. Weitere Informationen zu gültigen Suchmuster, finden Sie unter [Musterwerts](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Um die Enumeration der Kataloge, Schemas und Tabellentypen zu unterstützen, werden die folgende spezielle Semantik für definiert die *CatalogName*, *SchemaName*, *TableName*, und  *TableType* Argumente **SQLTables**:  
  
-   Wenn *CatalogName* sql_all_catalogs lautet und *SchemaName* und *TableName* sind leere Zeichenfolgen, das Resultset enthält eine Liste der gültigen Kataloge für die Datenquelle. (Alle Spalten außer der TABLE_CAT-Spalte NULL-Werte enthalten.)  
  
-   Wenn *SchemaName* ist SQL_ALL_SCHEMAS und *CatalogName* und *TableName* sind leere Zeichenfolgen, das Resultset enthält eine Liste der gültigen Schemas für die Datenquelle. (Alle Spalten außer der Spalte nach "TABLE_SCHEM" enthält ein NULL-Werte.)  
  
-   Wenn *TableType* ist SQL_ALL_TABLE_TYPES und *CatalogName*, *SchemaName*, und *TableName* sind leere Zeichenfolgen, das Resultset enthält eine Liste der gültigen Tabellentypen für die Datenquelle an. (Alle Spalten außer der TABLE_TYPE-Spalte NULL-Werte enthalten.)  
  
 Wenn *TableType* ist keine leere Zeichenfolge ist, müssen sie eine Liste von durch Trennzeichen getrennten Werten für die Typen von Interesse sind enthalten, und jeder Wert in einfache Anführungszeichen (') eingeschlossen werden können oder ohne Anführungszeichen, z. B. 'TABLE', "VIEW" oder Tabelle anzeigen. Eine Anwendung sollten immer angeben, den "Table" in Großbuchstaben; der Treiber sollten den Tabellentyp konvertieren, um den Fall, die von der Datenquelle erforderlich ist. Wenn die Datenquelle nicht über einen angegebenen Tabellentyp unterstützt **SQLTables** gibt keine Ergebnisse für diesen Typ zurück.  
  
 **SQLTables** gibt die Ergebnisse als standard Resultset, nach TABLE_TYPE, TABLE_CAT, TABLE_NAME und nach "TABLE_SCHEM" sortiert zurück. Informationen dazu, wie diese Informationen verwendet werden kann, finden Sie unter [von Katalogdaten verwendet](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Um die tatsächliche Länge der Spalten TABLE_CAT, nach "TABLE_SCHEM" und TABLE_NAME zu bestimmen, kann eine Anwendung aufrufen **SQLGetInfo** mit den Informationen SQL_MAX_CATALOG_NAME_LEN SQL_MAX_SCHEMA_NAME_LEN und SQL_MAX_TABLE_NAME_LEN Typen.  
  
 Die folgenden Spalten wurden umbenannt ODBC 3. *.x*. Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC 3. *.x* Spalte|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 5 ("Hinweise") können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifischen Spalten erhalten, indem nach unten am Ende des Resultsets anstatt einer expliziten Ordinalposition zählen. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Name des Katalogs; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Kataloge für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, denen keine Kataloge.|  
|NACH "TABLE_SCHEM" (ODBC 1.0)|2|Varchar|Schemanamen; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Schemas für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, die keine Schemas aufweisen.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar|Tabellenname.|  
|TABLE_TYPE (ODBC 1.0)|4|Varchar|Tabellentypnamen; eine der folgenden: "TABLE", "VIEW", "SYSTEM-TABLE", "Globale temporäre", "Lokale temporäre", "ALIAS", "Synonyms" oder einen Datentypnamen datenquellenspezifische.<br /><br /> Die Bedeutung der "ALIAS" und "SYNONYM" sind treiberspezifisch.|  
|HINWEISE (ODBC 1.0)|5|Varchar|Eine Beschreibung der Tabelle.|  
  
## <a name="example"></a>Beispiel  
 Der folgende Code gibt keine Handles und Verbindungen frei. Finden Sie unter [SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md) und [SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md) Codebeispiele, Handles und Anweisungen freizugeben.  
  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Berechtigungen für eine oder mehrere Spalten|[SQLColumnPrivileges-Funktion](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Zurückgeben von Spalten in einer Tabelle oder Tabellen|[SQLColumns-Funktion](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Abrufen einer einzelnen Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben von Statistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Zurückgeben von Berechtigungen für eine Tabelle oder Tabellen|[SQLTablePrivileges-Funktion](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
