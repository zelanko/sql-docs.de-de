---
title: SQLProcedures-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLProcedures
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLProcedures
helpviewer_keywords:
- SQLProcedures function [ODBC]
ms.assetid: d0d9ef10-2fd4-44a5-9334-649f186f4ba0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a044f3122f3f553e068d474901e52cce3eef1c9
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120083"
---
# <a name="sqlprocedures-function"></a>SQLProcedures-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLProcedures** gibt die Liste der Prozedurnamen, die in einer bestimmten Datenquelle gespeichert. *Prozedur* ist ein generischer Begriff zum Beschreiben einer *ausführbares Objekt*, oder eine benannte Entität, die mit Eingabe-und Ausgabeparametern aufgerufen werden kann. Weitere Informationen zu Prozeduren finden Sie unter den [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLProcedures(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      ProcName,  
     SQLSMALLINT    NameLength3);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *Katalogname*  
 [Eingabe] Prozedur-Katalog. Wenn ein Treiber unterstützt die Kataloge für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, denen keine Kataloge. *CatalogName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *CatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *CatalogName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen des **CatalogName*.  
  
 *SchemaName*  
 [Eingabe] Eine Zeichenfolge Suchmuster für Prozedur Schemanamen. Wenn ein Treiber Schemas unterstützt, bei einigen Prozeduren, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für diese Verfahren, die keine Schemas aufweisen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *SchemaName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *SchemaName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen des **SchemaName*.  
  
 *"ProcName"*  
 [Eingabe] Suchmuster für den Prozedurnamen eine Zeichenfolge.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *ProcName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *ProcName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen des **ProcName*.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLProcedures** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLProcedures** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Das Anweisungsattribut SQL_ATTR_METADATA_ID wurde festgelegt auf SQL_TRUE, die *CatalogName* Argument wurde ein null-Zeiger ist, und die SQL_CATALOG_NAME *Informationsart* gibt zurück, die Namen Katalog werden unterstützt.<br /><br /> (DM) das Anweisungsattribut SQL_ATTR_METADATA_ID wurde Wert auf SQL_TRUE festgelegt, und die *SchemaName* oder *ProcName* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert eines der Argumente Länge Name war kleiner als 0, jedoch nicht SQL_NTS gleich.<br /><br /> Der Wert eines der Argumente Namen Länge überschritten Wert für maximale Länge für den entsprechenden Namen.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Eine Prozedur Catalog angegeben wurde, und der Treiber oder die Datenquelle Kataloge nicht unterstützt.<br /><br /> Eine prozedurschema angegeben wurde, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Ein Suchmuster für die Zeichenfolge für den prozedurschema oder der Name der Prozedur angegeben wurde, und die Datenquelle unterstützt nicht das Suchmuster für eine oder mehrere dieser Argumente.<br /><br /> Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Abfragetimeout abgelaufen, bevor Sie die Datenquelle, die das angeforderte Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* diese Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLProcedures** Listet alle Prozeduren in den angeforderten Bereich. Ein Benutzer kann oder möglicherweise nicht über die Berechtigung zum Ausführen eines dieser Verfahren. Um Zugriff zu überprüfen, kann eine Anwendung aufrufen **SQLGetInfo** und überprüfen Sie den Wert der SQL_ACCESSIBLE_PROCEDURES-Informationen. Die Anwendung muss, andernfalls können Sie mit der jeweiligen Situation, in denen der Benutzer eine Prozedur auswählt, die nicht ausgeführt werden kann. Informationen dazu, wie diese Informationen verwendet werden kann, finden Sie unter [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLProcedures** gibt die Ergebnisse als ein standard, geordnet nach PROCEDURE_CAT PROCEDURE_SCHEMA und PROCEDURE_NAME Resultset zurück.  
  
> [!NOTE]  
>  **SQLProcedures** möglicherweise nicht alle Prozeduren zurück. Anwendungen können eine beliebige gültige Prozedur unabhängig davon, ob sie von zurückgegeben wird **SQLProcedures**.  
  
 Die folgenden Spalten wurden umbenannt ODBC 3.*.x*. Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC 3.*.x* Spalte|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|PROZEDUR _OWNER|PROZEDUR _SCHEM|  
  
 Um die tatsächliche Länge der Spalten PROCEDURE_CAT PROCEDURE_SCHEM und PROCEDURE_NAME zu bestimmen, kann eine Anwendung aufrufen **SQLGetInfo** mit der SQL_MAX_CATALOG_NAME_LEN SQL_MAX_SCHEMA_NAME_LEN und SQL_MAX_PROCEDURE_ NAME_LEN-Optionen.  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 8 (PROCEDURE_TYPE) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf die treiberspezifischen Spalten erhalten, durch eine explizite Ordnungsposition angeben, statt nach unten am Ende des Resultsets gezählt. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|Prozedur-Katalog-Bezeichner. NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn ein Treiber Kataloge bei einigen Prozeduren unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Verfahren aus, denen keine Kataloge.|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|Prozedur-Schema-Bezeichner. NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn ein Treiber Schemas bei einigen Prozeduren unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Verfahren, die keine Schemas aufweisen.|  
|PROCEDURE_NAME (ODBC 2.0)|3|Varchar, die nicht NULL|Prozedur-Bezeichner.|  
|NUM_INPUT_PARAMS (ODBC 2.0)|4|–|Zur künftigen Verwendung reserviert. Anwendungen sollten nicht auf die in diesen Ergebnisspalten zurückgegebenen Daten verlassen.|  
|NUM_OUTPUT_PARAMS (ODBC 2.0)|5|–|Zur künftigen Verwendung reserviert. Anwendungen sollten nicht auf die in diesen Ergebnisspalten zurückgegebenen Daten verlassen.|  
|NUM_RESULT_SETS (ODBC 2.0)|6|–|Zur künftigen Verwendung reserviert. Anwendungen sollten nicht auf die in diesen Ergebnisspalten zurückgegebenen Daten verlassen.|  
|HINWEISE (ODBC 2.0)|7|Varchar|Eine Beschreibung der Prozedur.|  
|PROCEDURE_TYPE (ODBC 2.0)|8|Smallint|Definiert den Prozedurtyp an:<br /><br /> SQL_PT_UNKNOWN: Es kann nicht bestimmt werden, ob die Prozedur einen Wert zurückgibt.<br /><br /> SQL_PT_PROCEDURE: Das zurückgegebene Objekt ist eine Prozedur. Er hat, also keinen Wert zurückgegeben.<br /><br /> SQL_PT_FUNCTION: Das zurückgegebene Objekt ist eine Funktion. Das heißt, hat es einen Rückgabewert.|  
  
 Die *SchemaName* und *ProcName* Argumente akzeptieren Suchmuster. Weitere Informationen zu gültigen Suchmuster, finden Sie unter [Musterwerts](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [Prozeduraufrufe](../../../odbc/reference/develop-app/procedure-calls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben von Informationen zu einer Datenquelle oder Treiber|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Resultsetspalten zurückgeben, die Parameter und das Ergebnis einer Prozedur|[SQLProcedureColumns-Funktion](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|  
|Die Syntax zum Aufrufen von gespeicherter Prozeduren|[Ausführen von Anweisungen](../../../odbc/reference/develop-app/executing-statements-odbc.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
