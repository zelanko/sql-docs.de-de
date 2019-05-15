---
title: SQLProcedureColumns-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLProcedureColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLProcedureColumns
helpviewer_keywords:
- SQLProcedureColumns function [ODBC]
ms.assetid: 4ca37b28-a6df-465b-8988-d422d37fc025
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a2971ef09877a3a6e86334563913941282244f8
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537305"
---
# <a name="sqlprocedurecolumns-function"></a>SQLProcedureColumns-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLProcedureColumns** gibt die Liste der Eingabe-und Ausgabeparameter als auch die Spalten, die das Resultset für die angegebenen Prozeduren bilden. Der Treiber gibt zurück, die Informationen, die als Resultset auf der angegebenen Anweisung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLProcedureColumns(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     ProcName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *CatalogName*  
 [Eingabe] Der Name des Katalogs. Wenn ein Treiber Kataloge unterstützt, bei einigen Prozeduren, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") gibt die Prozeduren, die keine Kataloge. *CatalogName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *CatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *CatalogName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge in Zeichen des **CatalogName*.  
  
 *SchemaName*  
 [Eingabe] Eine Zeichenfolge Suchmuster für Prozedur Schemanamen. Wenn ein Treiber Schemas unterstützt, bei einigen Prozeduren, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für diese Verfahren, die keine Schemas aufweisen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *SchemaName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *SchemaName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength2*  
 [Eingabe] Länge in Zeichen des **SchemaName*.  
  
 *ProcName*  
 [Eingabe] Suchmuster für den Prozedurnamen eine Zeichenfolge.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *ProcName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *ProcName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength3*  
 [Eingabe] Länge in Zeichen des **ProcName*.  
  
 *ColumnName*  
 [Eingabe] Eine Zeichenfolge Suchmuster für den Spaltennamen.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *ColumnName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *ColumnName* Wertargument Muster ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength4*  
 [Eingabe] Länge in Zeichen des **ColumnName*.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLProcedureColumns** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und ein *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLProcedureColumns** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der vom Treiber zurückgegebene SQLSTATEs -Manager. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLError** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|Das Anweisungsattribut SQL_ATTR_METADATA_ID wurde festgelegt auf SQL_TRUE, die *CatalogName* Argument wurde ein null-Zeiger ist, und die SQL_CATALOG_NAME *Informationsart* gibt zurück, die Namen Katalog werden unterstützt.<br /><br /> (DM) das Anweisungsattribut SQL_ATTR_METADATA_ID wurde Wert auf SQL_TRUE festgelegt, und die *SchemaName*, *ProcName*, oder *ColumnName* Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Diese Funktion Aynschronous wurde noch ausgeführt werden, wenn die SQLProcedureColumns-Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert eines der Argumente Länge Name war kleiner als 0, jedoch nicht SQL_NTS gleich.<br /><br /> Der Wert eines der Argumente Namen Länge überschritten Wert für maximale Länge für den entsprechenden Katalog, Schema, Prozedur oder Name der Spalte.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Eine Prozedur Catalog angegeben wurde, und der Treiber oder die Datenquelle Kataloge nicht unterstützt.<br /><br /> Eine prozedurschema angegeben wurde, und der Treiber oder die Datenquelle unterstützt keine Schemas.<br /><br /> Ein Suchmuster für die Zeichenfolge, die für die prozedurschema, Name der Prozedur oder Name der Spalte angegeben wurde, und die Datenquelle unterstützt nicht das Suchmuster für eine oder mehrere dieser Argumente.<br /><br /> Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Diese Funktion wird in der Regel vor der anweisungsausführung verwendet, um Informationen zu den Prozedurparametern und den Spalten, aus denen das Resultset oder Gruppen, die von der Prozedur zurückgegebene ggf. abzurufen. Weitere Informationen finden Sie unter [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md).  
  
> [!NOTE]  
>  **SQLProcedureColumns** möglicherweise nicht alle Spalten, die von einer Prozedur verwendete zurück. Beispielsweise kann ein Treiber nur Informationen zu den Parametern, die von einer Prozedur und nicht die Spalten in einem Resultset generierten verwendet zurück.  
  
 Die *SchemaName*, *ProcName*, und *ColumnName* Argumente akzeptieren Suchmuster. Weitere Informationen zu gültigen Suchmuster, finden Sie unter [Musterwerts](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLProcedureColumns** gibt die Ergebnisse als ein standard, geordnet nach PROCEDURE_CAT, PROCEDURE_SCHEM, PROCEDURE_NAME und COLUMN_TYPE Resultset zurück. Spaltennamen für jede Prozedur in der folgenden Reihenfolge zurückgegeben werden: der Name des Rückgabewerts, die Namen der einzelnen Parameter in dem Prozeduraufruf (in Reihenfolge der Aufrufe gelistet) und klicken Sie dann den Namen der einzelnen Spalten im Resultset zurückgegeben, die von der Prozedur (in Reihenfolge).  
  
 Anwendungen sollten treiberspezifischen Spalten relativ zum Ende des Resultsets binden. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
 Um die tatsächliche Länge der Spalten PROCEDURE_CAT, PROCEDURE_SCHEM, PROCEDURE_NAME und COLUMN_NAME zu bestimmen, kann eine Anwendung aufrufen **SQLGetInfo** mit der SQL_MAX_ SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, PROCEDURE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN-Optionen.  
  
 Die folgenden Spalten wurden umbenannt, ODBC 3. *x*. Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC 3. *x* Spalte|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|PROZEDUR _OWNER|PROCEDURE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Das Resultset zurückgegebenes wurden die folgenden Spalten hinzugefügt **SQLProcedureColumns** ODBC 3. *X*:  
  
-   COLUMN_DEF  
  
-   DATETIME_CODE  
  
-   CHAR_OCTET_LENGTH  
  
-   ORDINAL_POSITION  
  
-   IS_NULLABLE  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 19 (IS_NULLABLE) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf die treiberspezifischen Spalten erhalten, durch eine explizite Ordnungsposition angeben, statt nach unten am Ende des Resultsets gezählt. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|Katalogname der Prozedur; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn ein Treiber Kataloge bei einigen Prozeduren unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Verfahren aus, denen keine Kataloge.|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|Prozedur Schemanamen; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn ein Treiber Schemas bei einigen Prozeduren unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Verfahren, die keine Schemas aufweisen.|  
|PROCEDURE_NAME (ODBC 2.0)|3|Varchar, die nicht NULL|Der Name der Prozedur. Für eine Prozedur, die nicht über einen Namen besitzt, wird eine leere Zeichenfolge zurückgegeben.|  
|COLUMN_NAME (ODBC 2.0)|4|Varchar, die nicht NULL|Der Name der Prozedur-Spalte. Der Treiber gibt eine leere Zeichenfolge für eine Prozedurspalte, die nicht über einen Namen verfügt.|  
|COLUMN_TYPE (ODBC 2.0)|5|Smallint nicht NULL|Definiert die Prozedurspalte als Parameter oder einer Resultsetspalte an:<br /><br /> SQL_PARAM_TYPE_UNKNOWN: Prozedurspalte ist ein Parameter, deren Typ unbekannt ist. (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT: Die Prozedurspalte ist ein Eingabeparameter. (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT_OUTPUT: Die Prozedurspalte ist ein Eingabe-/Ausgabeparameter. (ODBC 1.0)<br /><br /> SQL_PARAM_OUTPUT: Die Prozedurspalte ist ein Output-Parameter. (ODBC 2.0)<br /><br /> SQL_RETURN_VALUE: Die Prozedurspalte ist der Rückgabewert der Prozedur. (ODBC 2.0)<br /><br /> SQL_RESULT_COL: Die Prozedurspalte ist eine Resultsetspalte. (ODBC 1.0)|  
|DATA_TYPE (ODBC 2.0)|6|Smallint nicht NULL|SQL-Datentyp. Dies kann einen ODBC-SQL-Datentyp oder die treiberspezifischen SQL-Datentyp sein. Bei "DateTime" "und" Interval-Datentypen gibt diese Spalte die präzisen Datentypen (z. B. SQL_TYPE_TIME oder SQL_INTERVAL_YEAR_TO_MONTH) zurück. Eine Liste der gültigen ODBC-SQL-Datentypen, finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu Treiber-spezifische SQL-Datentypen finden Sie in der vom Treiber-Dokumentation.|  
|TYPE_NAME (ODBC 2.0)|7|Varchar, die nicht NULL|Daten Datenquelle abhängiger Datentypname; z. B. "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY" oder "CHAR () für BIT-Daten".|  
|COLUMN_SIZE (ODBC 2.0)|8|Integer|Die Spaltengröße der Prozedurspalte für die Datenquelle. NULL wird für Datentypen zurückgegeben, in denen ist Spaltengröße nicht anwendbar. Weitere Informationen zu Genauigkeit, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|BUFFER_LENGTH (ODBC 2.0)|9|Integer|Die Länge in Bytes der Datenübertragung auf einen **SQLGetData** oder **SQLFetch** Vorgang, wenn SQL_C_DEFAULT angegeben wird. Für numerische Daten möglicherweise anders als die Größe der in der Datenquelle gespeicherten Daten diese Größe. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md), klicken Sie im Anhang D: Datentypen.|  
|DECIMAL_DIGITS (ODBC 2.0)|10|Smallint|Die Dezimalstellen der Spalte Verfahren für die Datenquelle. NULL wird für Datentypen zurückgegeben, in denen ist Dezimalstellen nicht anwendbar. Weitere Informationen zu Dezimalstellen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md), klicken Sie im Anhang D: Datentypen.|  
|NUM_PREC_RADIX (ODBC 2.0)|11|Smallint|Für numerische Datentypen entweder "10" oder "2.<br /><br /> Wenn 10, geben Sie die Werte in der COLUMN_SIZE- und DECIMAL_DIGITS die Anzahl der Dezimalstellen für die Spalte zulässig sind. Beispielsweise würde ein NUM_PREC_RADIX von 10 und eine COLUMN_SIZE 12, ein DECIMAL_DIGITS 5 eine DECIMAL(12,5)-Spalte zurückgegeben wird. eine Spalte "float" konnte eine NUM_PREC_RADIX von 10 und eine COLUMN_SIZE 15 DECIMAL_DIGITS von NULL zurückgeben.<br /><br /> Wenn 2, geben Sie die Werte in der COLUMN_SIZE- und DECIMAL_DIGITS die Anzahl der Bits, die in der Spalte zulässig. Eine "float"-Spalte kann z. B. eine NUM_PREC_RADIX 2, eine COLUMN_SIZE 53 und DECIMAL_DIGITS von NULL zurückgegeben.<br /><br /> NULL wird für Datentypen zurückgegeben, in dem kein NUM_PREC_RADIX anwendbar.|  
|NULL-WERTE ZULÄSST (ODBC 2.0)|12|Smallint nicht NULL|Gibt an, ob die Prozedurspalte einen NULL-Wert akzeptiert:<br /><br /> SQL_NO_NULLS: Die Prozedurspalte akzeptiert keine NULL-Werte.<br /><br /> SQL_NULLABLE: Die Prozedurspalte akzeptiert NULL-Werte.<br /><br /> SQL_NULLABLE_UNKNOWN: Es ist nicht bekannt, wenn die Prozedurspalte NULL-Werte akzeptiert.|  
|HINWEISE (ODBC 2.0)|13|Varchar|Eine Beschreibung der Prozedurspalte.|  
|COLUMN_DEF (ODBC 3.0)|14|Varchar|Der Standardwert der Spalte.<br /><br /> Wenn NULL als Standardwert angegeben wurde, ist diese Spalte das Wort NULL ist, nicht in Anführungszeichen eingeschlossen. Der Standardwert ungekürzt dargestellt werden kann, enthält diese Spalte abgeschnitten, mit ohne einschließenden Anführungszeichen ein. Wenn kein Standardwert angegeben wurde, ist diese Spalte NULL.<br /><br /> Der Wert des COLUMN_DEF dienen zum Generieren einer neuen Spaltendefinition, außer, wenn der Wert abgeschnitten enthalten.|  
|SQL_DATA_TYPE (ODBC 3.0)|15|Smallint nicht NULL|Der Wert der SQL-Datentyp, wie er wird in das SQL_DESC_TYPE-Feld des Deskriptors angezeigt. Diese Spalte entspricht der DATA_TYPE-Spalte, mit Ausnahme von "DateTime" "und" Interval-Datentypen.<br /><br /> Für Datetime "und" Interval-Datentypen SQL_INTERVAL oder SQL_DATETIME die SQL_DATA_TYPE-Feld im Resultset zurück, und das Feld noch SQL_DATETIME_SUB dem Subcode für den bestimmten Intervall oder Datetime-Datentyp zurück. (Finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3.0)|16|Smallint|Der Untertypcode für Datetime "und" Interval-Datentypen. Für andere Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|17|Integer|Die maximale Länge in Byte von einem Zeichen- oder Binärdaten-Datentypspalte. Bei allen anderen Datentypen gibt diese Spalte einen NULL-Wert zurück.|  
|ORDINAL_POSITION (ODBC 3.0)|18|Integer nicht NULL|Für Eingabe- und Ausgabedateien, die Ordnungsposition des Parameters in der Prozedurdefinition (in der wachsenden Reihenfolge der Parameter, beginnend mit 1). Für einen Rückgabewert (sofern vorhanden) wird 0 zurückgegeben. Für Resultset Spalten, die Ordnungsposition der Spalte im Ergebnis festgelegt, durch die erste Spalte im Resultset wird Nummer 1. Wenn mehrere Resultsets vorhanden sind, werden die Ordnungsposition der Spalte auf eine treiberspezifische Weise zurückgegeben.|  
|IS_NULLABLE (ODBC 3.0)|19|Varchar|"Nein", wenn die Spalte keine NULL-Werte enthält.<br /><br /> "YES", wenn die Spalte NULL-Werte einschließen kann.<br /><br /> Die Spalte gibt eine leere Zeichenfolge zurück, wenn die NULL-Zulässigkeit unbekannt ist.<br /><br /> Die NULL-Zulässigkeit wird gemäß den ISO-Regeln bestimmt. Ein DBMS nach ISO SQL kann keine leere Zeichenfolge zurückgeben.<br /><br /> Der für diese Spalte zurückgegebene Wert ist ein anderer als der für die NULLABLE-Spalte zurückgegebene Wert. (Siehe die Beschreibung der Spalte NULL-Werte zulässt.)|  
  
## <a name="code-example"></a>Codebeispiel  
 Finden Sie unter [Prozeduraufrufe](../../../odbc/reference/develop-app/procedure-calls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben einer Liste von Prozeduren in einer Datenquelle|[SQLProcedures-Funktion](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
