---
title: SQLProcedures-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4c8b8a9f22f6005d1af811e56485299bad3a425
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306841"
---
# <a name="sqlprocedures-function"></a>SQLProcedures-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLProcedures** gibt die Liste der Prozedurnamen zurück, die in einer bestimmten Datenquelle gespeichert sind. *Prozedur* ist ein generischer Begriff, der verwendet wird, um ein *ausführbares Objekt*oder eine benannte Entität zu beschreiben, die mithilfe von Eingabe- und Ausgabeparametern aufgerufen werden kann. Weitere Informationen zu Verfahren finden Sie in den [Verfahren](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
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
  
 *Catalogname*  
 [Eingabe] Prozedurkatalog. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Tabellen, die keine Kataloge haben. *CatalogName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *CatalogName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *CatalogName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen von **CatalogName*.  
  
 *Schemaname*  
 [Eingabe] Zeichenfolgensuche-Muster für Prozedurschemanamen. Wenn ein Treiber Schemas für einige Prozeduren unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Prozeduren, die keine Schemas haben.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *SchemaName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *SchemaName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen von **SchemaName*.  
  
 *ProcName*  
 [Eingabe] Zeichenfolgensuche-Muster für Prozedurnamen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *ProcName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *ProcName* ein Musterwertargument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen von **ProcName*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLProcedures** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von SQLProcedures zurückgegeben werden, und es werden die **sqlSTATE-Werte** im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|24.000|Ungültiger Cursorstatus|Im *StatementHandle*wurde ein Cursor geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Im *StatementHandle*wurde ein Cursor geöffnet, **SQLFetch** oder **SQLFetchScroll** wurden jedoch nicht aufgerufen.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcenstillstands mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das attribut SQL_ATTR_METADATA_ID Anweisung wurde auf SQL_TRUE festgelegt, das *Argument CatalogName* war ein Nullzeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) Das SQL_ATTR_METADATA_ID-Anweisungsattribut wurde auf SQL_TRUE festgelegt, und das *Argument SchemaName* oder *ProcName* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der Wert eines der Argumente für die Namenslänge war kleiner als 0, aber nicht gleich SQL_NTS.<br /><br /> Der Wert eines der Namenslängenargumente hat den maximalen Längenwert für den entsprechenden Namen überschritten.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Es wurde ein Prozedurkatalog angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Prozedurschema angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Für das Prozedurschema oder den Prozedurnamen wurde ein Zeichenfolgensuchmuster angegeben, und die Datenquelle unterstützt keine Suchmuster für eines oder mehrere dieser Argumente.<br /><br /> Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das angeforderte Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt diese Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLProcedures** listet alle Prozeduren im angeforderten Bereich auf. Ein Benutzer kann über die Berechtigung zum Ausführen eines dieser Verfahren verfügen oder nicht. Um die Barrierefreiheit zu überprüfen, kann eine Anwendung **SQLGetInfo** aufrufen und den SQL_ACCESSIBLE_PROCEDURES Informationswert überprüfen. Andernfalls muss die Anwendung in der Lage sein, eine Situation zu behandeln, in der der Benutzer eine Prozedur auswählt, die er nicht ausführen kann. Informationen zur Verwendung dieser Informationen finden Sie unter [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
> [!NOTE]  
>  Weitere Informationen zur allgemeinen Verwendung, Argumente und zurückgegebenen Daten von ODBC-Katalogfunktionen finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLProcedures** gibt die Ergebnisse als Standardergebnissatz zurück, sortiert nach PROCEDURE_CAT, PROCEDURE_SCHEMA und PROCEDURE_NAME.  
  
> [!NOTE]  
>  **SQLProcedures** gibt möglicherweise nicht alle Prozeduren zurück. Anwendungen können eine beliebige gültige Prozedur verwenden, unabhängig davon, ob sie von **SQLProcedures**zurückgegeben wird.  
  
 Die folgenden Spalten wurden für ODBC 3 *.x*umbenannt. Die Änderungen des Spaltennamens wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer binden.  
  
|ODBC 2.0-Säule|ODBC 3 *.x-Säule*|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|PROCEDURE _OWNER|PROCEDURE _SCHEM|  
  
 Um die tatsächlichen Längen der PROCEDURE_CAT-, PROCEDURE_SCHEM- und PROCEDURE_NAME-Spalten zu bestimmen, kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN und SQL_MAX_PROCEDURE_NAME_LEN aufrufen.  
  
 In der folgenden Tabelle sind die Spalten im Resultset aufgeführt. Zusätzliche Spalten jenseits von Spalte 8 (PROCEDURE_TYPE) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifische Spalten erhalten, indem sie vom Ende des Resultsets herunterzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|Prozedurkatalog-Idon; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Kataloge für einige Prozeduren unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für die Prozeduren zurück, die keine Kataloge haben.|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|Prozedurschemabezeichner; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Schemas für einige Prozeduren unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für prozedursfreie Prozeduren zurück, die keine Schemas haben.|  
|PROCEDURE_NAME (ODBC 2.0)|3|Varchar nicht NULL|Prozedurbezeichner.|  
|NUM_INPUT_PARAMS (ODBC 2.0)|4|Nicht zutreffend|Für die zukünftige Verwendung reserviert. Anwendungen sollten sich nicht auf die in diesen Ergebnisspalten zurückgegebenen Daten verlassen.|  
|NUM_OUTPUT_PARAMS (ODBC 2.0)|5|Nicht zutreffend|Für die zukünftige Verwendung reserviert. Anwendungen sollten sich nicht auf die in diesen Ergebnisspalten zurückgegebenen Daten verlassen.|  
|NUM_RESULT_SETS (ODBC 2.0)|6|Nicht zutreffend|Für die zukünftige Verwendung reserviert. Anwendungen sollten sich nicht auf die in diesen Ergebnisspalten zurückgegebenen Daten verlassen.|  
|BEMERKUNGEN (ODBC 2.0)|7|Varchar|Eine Beschreibung des Verfahrens.|  
|PROCEDURE_TYPE (ODBC 2.0)|8|Smallint|Definiert den Prozedurtyp:<br /><br /> SQL_PT_UNKNOWN: Es kann nicht festgestellt werden, ob die Prozedur einen Wert zurückgibt.<br /><br /> SQL_PT_PROCEDURE: Das zurückgegebene Objekt ist eine Prozedur; d. h., es hat keinen Rückgabewert.<br /><br /> SQL_PT_FUNCTION: Das zurückgegebene Objekt ist eine Funktion; d. h., es hat einen Rückgabewert.|  
  
 Die Argumente *SchemaName* und *ProcName* akzeptieren Suchmuster. Weitere Informationen zu gültigen Suchmustern finden Sie unter [Pattern Value Arguments](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [Prozeduraufrufe](../../../odbc/reference/develop-app/procedure-calls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in einer vorwärtsgerichteten Richtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben von Informationen zu einem Treiber oder einer Datenquelle|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Zurückgeben der Parameter und Ergebnissatzspalten einer Prozedur|[SQLProcedureColumns-Funktion](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|  
|Syntax zum Aufrufen gespeicherter Prozeduren|[Ausführen von Anweisungen](../../../odbc/reference/develop-app/executing-statements-odbc.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
