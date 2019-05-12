---
title: SQLForeignKeys-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLForeignKeys
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLForeignKeys
helpviewer_keywords:
- SQLForeignKeys function [ODBC]
ms.assetid: 07f3f645-f643-4d39-9a10-70a72f24e608
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1aeaef9b120a0bd4be008adafe8e9a24724279a0
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537244"
---
# <a name="sqlforeignkeys-function"></a>SQLForeignKeys-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLForeignKeys** can return:  
  
-   Eine Liste der Fremdschlüssel in der angegebenen Tabelle (Spalten in der angegebenen Tabelle, die auf Primärschlüssel in anderen Tabellen verweisen).  
  
-   Eine Liste von Fremdschlüsseln in anderen Tabellen, die auf den Primärschlüssel in der angegebenen Tabelle verweisen.  
  
 Der Treiber gibt jede Liste, die als Resultset auf der angegebenen Anweisung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLForeignKeys(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      PKCatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      PKSchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      PKTableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      FKCatalogName,  
     SQLSMALLINT    NameLength4,  
     SQLCHAR *      FKSchemaName,  
     SQLSMALLINT    NameLength5,  
     SQLCHAR *      FKTableName,  
     SQLSMALLINT    NameLength6);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *PKCatalogName*  
 [Eingabe] Katalogname der Primärschlüsseltabelle. Wenn ein Treiber unterstützt die Kataloge für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, denen keine Kataloge. *PKCatalogName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *PKCatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *PKCatalogName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge der **PKCatalogName*, in Zeichen.  
  
 *PKSchemaName*  
 [Eingabe] Name der Primärschlüsseltabelle-Schemas. Wenn ein Treiber unterstützt die Schemas für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, die keine Schemas aufweisen. *PKSchemaName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *PKSchemaName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *PKSchemaName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength2*  
 [Eingabe] Länge der **PKSchemaName*, in Zeichen.  
  
 *PKTableName*  
 [Eingabe] Name der Primärschlüsseltabelle. *PKTableName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *PKTableName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *PKTableName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength3*  
 [Eingabe] Länge der **PKTableName*, in Zeichen.  
  
 *FKCatalogName*  
 [Eingabe] Katalogname der Fremdschlüsseltabelle. Wenn ein Treiber unterstützt die Kataloge für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, denen keine Kataloge. *FKCatalogName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *FKCatalogName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *FKCatalogName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength4*  
 [Eingabe] Länge der **FKCatalogName*, in Zeichen.  
  
 *FKSchemaName*  
 [Eingabe] Name der Fremdschlüsseltabelle-Schemas. Wenn ein Treiber unterstützt die Schemas für einige Tabellen jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS, eine leere Zeichenfolge ruft ("") steht für die Tabellen, die keine Schemas aufweisen. *FKSchemaName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *FKSchemaName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *FKSchemaName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength5*  
 [Eingabe] Länge der **FKSchemaName*, in Zeichen.  
  
 *FKTableName*  
 [Eingabe] Name der Fremdschlüsseltabelle. *FKTableName* darf kein Suchmuster Zeichenfolge enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_TRUE, festgelegt ist *FKTableName* wird als Bezeichner behandelt und der Fall ist nicht von Bedeutung. Ist dies SQL_FALSE, *FKTableName* ein normales Argument ist, wird es buchstäblich behandelt und der Fall ist von Bedeutung.  
  
 *NameLength6*  
 [Eingabe] Länge der **FKTableName*, in Zeichen.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLForeignKeys** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* SQL _HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLForeignKeys** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|24000|Ungültiger Cursorstatus|Ein Cursor geöffnet, auf war die *StatementHandle*, und **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor geöffnet, auf war die *StatementHandle*, aber **SQLFetch** oder **SQLFetchScroll** nicht aufgerufen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde wegen eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Es wurde der Treiber kann kein Arbeitsspeicher belegt werden, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*, und klicken Sie dann die Funktion aufgerufen wurde erneut auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|(DM) die Argumente *PKTableName* und *FKTableName* wurden null-Zeiger.<br /><br /> Das Anweisungsattribut SQL_ATTR_METADATA_ID wurde festgelegt auf SQL_TRUE, die *FKCatalogName* oder *PKCatalogName* Argument wurde ein null-Zeiger ist, und die SQL_CATALOG_NAME *Informationsart*gibt zurück, die Namen Katalog werden unterstützt.<br /><br /> (DM) das Anweisungsattribut SQL_ATTR_METADATA_ID wurde Wert auf SQL_TRUE festgelegt, und die *FKSchemaName*, *PKSchemaName*, *FKTableName*, oder *PKTableName*  Argument wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Diese asynchronen Funktion wurde noch ausgeführt werden, wenn die SQLForeignKeys-Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert eines der Argumente Länge Name war kleiner als 0, jedoch nicht SQL_NTS gleich.|  
|||Der Wert eines der Argumente Namen Länge überschritten Wert für maximale Länge für den entsprechenden Namen. (Siehe "Kommentare".)|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Ein Katalogname wurde angegeben, und der Treiber oder die Datenquelle Kataloge nicht unterstützt.<br /><br /> Ein Schemaname angegeben wurde, und der Treiber oder die Datenquelle unterstützt keine Schemas.|  
|||Die Kombination aus der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde durch das Treiber oder die Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_VARIABLE festgelegt wurde, und das SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung wurde festgelegt, um einen Cursortyp, die der Treiber für den Lesezeichen nicht unterstützt.|  
|HYT00|Timeout abgelaufen|Zeitraum für das Timeout ist abgelaufen, bevor die Datenquelle über das Resultset zurückgegeben. Das Timeout festgelegt ist, über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Informationen dazu, wie die von dieser Funktion zurückgegebenen Informationen verwendet werden kann, finden Sie unter [von Katalogdaten verwendet](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Wenn \* *PKTableName* enthält einen Tabellennamen **SQLForeignKeys** gibt ein Resultset, das den primären Schlüssel der angegebenen Tabelle und alle Fremdschlüssel, die darauf verweisen, enthält. Die Liste der Fremdschlüssel in anderen Tabellen umfasst keine Fremdschlüssel, die auf unique-Einschränkungen in der angegebenen Tabelle verweisen.  
  
 Wenn \* *FKTableName* enthält einen Tabellennamen **SQLForeignKeys** gibt ein Resultset, das alle Fremdschlüssel in der angegebenen Tabelle enthält, die auf Primärschlüssel in anderen Tabellen verweisen und die der Primärschlüssel in den anderen Tabellen, die auf die sie verweisen. Die Liste der Fremdschlüssel in der angegebenen Tabelle enthält keine Fremdschlüssel, die auf unique-Einschränkungen in anderen Tabellen verweisen.  
  
 Wenn beide \* *PKTableName* und \* *FKTableName* Tabellennamen enthalten **SQLForeignKeys** gibt Fremdschlüssel in der angegebenen Tabelle zurück in \* *FKTableName* , verweisen auf den Primärschlüssel der Tabelle, angegeben **PKTableName*. Dies sollte höchstens ein Schlüssel sein.  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumenten und zurückgegebenen Daten des ODBC-Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLForeignKeys** Ergebnisse als standard Resultset zurückgegeben. Wenn die Fremdschlüssel, die mit einem Primärschlüssel verknüpft angefordert werden, wird das Resultset nach FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME und KEY_SEQ sortiert. Wenn der Primärschlüssel, Fremdschlüssel zugeordnet angefordert werden, wird das Resultset nach PKTABLE_CAT, PKTABLE_SCHEM, PKTABLE_NAME und KEY_SEQ sortiert. Die folgende Tabelle enthält die Spalten im Resultset.  
  
 Die Länge der VARCHAR-Spalten werden nicht in der Tabelle angezeigt; die tatsächliche Länge hängt von der Datenquelle ab. Um die tatsächliche Länge des PKTABLE_CAT FKTABLE_CAT, PKTABLE_SCHEM oder FKTABLE_SCHEM zu bestimmen, PKTABLE_NAME oder FKTABLE_NAME, und PKCOLUMN_NAME oder FKCOLUMN_NAME Spalten kann eine Anwendung aufrufen **SQLGetInfo** mit der SQL_MAX_ CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN-Optionen.  
  
 Die folgenden Spalten wurden umbenannt für ODBC 3 *. X.* Die Änderungen an wirken Abwärtskompatibilität sich nicht, da Anwendungen durch die Nummer der Spalte binden.  
  
|ODBC 2.0-Spalte|ODBC 3.*.x* Spalte|  
|---------------------|-----------------------|  
|PKTABLE_QUALIFIER|PKTABLE_CAT|  
|PKTABLE_OWNER|PKTABLE_SCHEM|  
|FKTABLE_QUALIFIER|FK_TABLE_CAT|  
|FKTABLE_OWNER|FKTABLE_SCHEM|  
  
 Die folgende Tabelle enthält die Spalten im Resultset. Zusätzliche Spalten nach Spalte 14 ("Hinweise") können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifischen Spalten erhalten, indem nach unten am Ende des Resultsets anstatt einer expliziten Ordinalposition zählen. Weitere Informationen finden Sie unter [Daten von Katalogfunktionen zurückgegeben](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|PKTABLE_CAT (ODBC 1.0)|1|Varchar|Katalogname der Primärschlüsseltabelle; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Kataloge für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, denen keine Kataloge.|  
|PKTABLE_SCHEM (ODBC 1.0)|2|Varchar|Primärschlüsseltabelle Schemanamen; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Schemas für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, die keine Schemas aufweisen.|  
|PKTABLE_NAME (ODBC 1.0)|3|Varchar, die nicht NULL|Name der Primärschlüsseltabelle.|  
|PKCOLUMN_NAME (ODBC 1.0)|4|Varchar, die nicht NULL|Name der Primärschlüsselspalte. Der Treiber gibt eine leere Zeichenfolge für eine Spalte, die nicht über einen Namen verfügt.|  
|FKTABLE_CAT (ODBC 1.0)|5|Varchar|Katalogname der Fremdschlüsseltabelle; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Kataloge für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, denen keine Kataloge.|  
|FKTABLE_SCHEM (ODBC 1.0)|6|Varchar|Fremdschlüsseltabelle Schemanamen; NULL, wenn Sie mit der Datenquelle nicht anwendbar. Wenn Sie ein Treiber Schemas für einige Tabellen unterstützt jedoch nicht für andere, z. B. wenn der Treiber die Daten aus verschiedenen DBMS abruft, eine leere Zeichenfolge zurückgegeben ("") für diese Tabellen, die keine Schemas aufweisen.|  
|FKTABLE_NAME (ODBC 1.0)|7|Varchar, die nicht NULL|Name der Fremdschlüsseltabelle.|  
|FKCOLUMN_NAME (ODBC 1.0)|8|Varchar, die nicht NULL|Name der Fremdschlüsselspalte. Der Treiber gibt eine leere Zeichenfolge für eine Spalte, die nicht über einen Namen verfügt.|  
|KEY_SEQ (ODBC 1.0)|9|Smallint nicht NULL|Spalte Sequenznummer im Schlüssel (beginnend mit 1).|  
|UPDATE_RULE (ODBC 1.0)|10|Smallint|Aktion, die für den Fremdschlüssel angewendet werden, wenn der SQL-Vorgang ist **UPDATE**. Dabei kann es sich um einen der folgenden Werte aufweisen. (Die referenzierte Tabelle ist die Tabelle, die mit dem primären Schlüssel enthält; die verweisende Tabelle ist die Tabelle, die den Fremdschlüssel aufweist.)<br /><br /> SQL_CASCADE: Wenn der Primärschlüssel der referenzierten Tabelle aktualisiert wird, wird ebenfalls der Fremdschlüssel der verweisenden Tabelle aktualisiert.<br /><br /> SQL_NO_ACTION: Wenn ein Update des Primärschlüssels der Tabelle, auf die verwiesen wird "Verbleibende Referenz" in der verweisenden Tabelle würde (d. h. Zeilen in der verweisenden Tabelle müssten keine Entsprechung in der referenzierten Tabelle), wird das Update abgelehnt. Wenn ein Update des Fremdschlüssels der verweisenden Tabelle einen Wert führen würde, der als Wert des Primärschlüssels der referenzierten Tabelle nicht vorhanden ist, wird das Update abgelehnt. (Diese Aktion ist identisch mit der Aktion SQL_RESTRICT in ODBC 2.*.x*.)<br /><br /> SQL_SET_NULL: Wenn eine oder mehrere Zeilen in der referenzierten Tabelle so aktualisiert werden, dass eine oder mehrere Komponenten des primären Schlüssels geändert werden, werden die Komponenten des Fremdschlüssels in der verweisenden Tabelle, die die geänderten Komponenten des primären Schlüssels entsprechen, auf NULL in allen festgelegt übereinstimmende Zeilen der verweisenden Tabelle.<br /><br /> SQL_SET_DEFAULT: Wenn eine oder mehrere Zeilen in der referenzierten Tabelle so aktualisiert werden, dass eine oder mehrere Komponenten des primären Schlüssels geändert werden, werden die Komponenten des Fremdschlüssels in der verweisenden Tabelle, die die geänderten Komponenten des primären Schlüssels entsprechen, die Applicab festgelegt. LE-Standardwerte in der verweisenden Tabelle alle übereinstimmenden Zeilen.<br /><br /> NULL, wenn Sie mit der Datenquelle nicht anwendbar.|  
|DELETE_RULE (ODBC 1.0)|11|Smallint|Aktion, die für den Fremdschlüssel angewendet werden, wenn der SQL-Vorgang ist **löschen**. Dabei kann es sich um einen der folgenden Werte aufweisen. (Die referenzierte Tabelle ist die Tabelle, die mit dem primären Schlüssel enthält; die verweisende Tabelle ist die Tabelle, die den Fremdschlüssel aufweist.)<br /><br /> SQL_CASCADE: Wenn eine Zeile in der referenzierten Tabelle gelöscht wird, werden auch alle übereinstimmenden Zeilen in der verweisenden Tabelle gelöscht.<br /><br /> SQL_NO_ACTION: Wenn ein Löschvorgang einer Zeile in der referenzierten Tabelle "Verbleibende Referenz" in der verweisenden Tabelle würde (d. h. Zeilen in der verweisenden Tabelle müssten keine Entsprechung in der referenzierten Tabelle), wird das Update abgelehnt. (Diese Aktion ist identisch mit der Aktion SQL_RESTRICT in ODBC 2.*.x*.)<br /><br /> SQL_SET_NULL: Wenn eine oder mehrere Zeilen in der referenzierten Tabelle gelöscht werden, wird jede Komponente des Fremdschlüssels der verweisenden Tabelle auf NULL-Wert in der verweisenden Tabelle alle übereinstimmenden Zeilen festgelegt.<br /><br /> SQL_SET_DEFAULT: Wenn eine oder mehrere Zeilen in der referenzierten Tabelle gelöscht werden, wird jede Komponente des Fremdschlüssels der verweisenden Tabelle auf die entsprechenden Standardwerte in der verweisenden Tabelle alle übereinstimmenden Zeilen festgelegt.<br /><br /> NULL, wenn Sie mit der Datenquelle nicht anwendbar.|  
|FK_NAME (ODBC 2.0)|12|Varchar|Foreign Key-Name. NULL, wenn Sie mit der Datenquelle nicht anwendbar.|  
|PK_NAME (ODBC 2.0)|13|Varchar|Name des primären Schlüssels. NULL, wenn Sie mit der Datenquelle nicht anwendbar.|  
|DEFERRABILITY-WERT (ODBC 3.0)|14|Smallint|SQL_INITIALLY_DEFERRED, SQL_INITIALLY_IMMEDIATE, SQL_NOT_DEFERRABLE.|  
  
## <a name="code-example"></a>Codebeispiel  
 Wie in der folgenden Tabelle dargestellt wird, wird in diesem Beispiel drei Tabellen, die mit dem Namen ORDERS, Linien und Kunden verwendet.  
  
|ORDERS|ZEILEN|KUNDEN|  
|------------|-----------|---------------|  
|"ORDERID"|"ORDERID"|CUSTID|  
|CUSTID|ZEILEN|NAME|  
|OPENDATE|PARTID|ADRESSE|  
|VERTRIEBSMITARBEITER|MENGE|TELEFON|  
|STATUS|||  
  
 In der ORDERS-Tabelle identifiziert CUSTID des Kunden, den der Verkauf vorgenommen wurde. Es ist ein Fremdschlüssel, der auf CUSTID in der CUSTOMERS-Tabelle verweist.  
  
 In der Tabelle Zeilen identifiziert "OrderID" für den Auftrag, den die Position zugeordnet ist. Es ist ein Fremdschlüssel, der auf "OrderID" in der ORDERS-Tabelle verweist.  
  
 Dieses Beispiel ruft **SQLPrimaryKeys** um den Primärschlüssel der Tabelle ORDERS zu erhalten. Das Resultset müssen eine Zeile; die wichtigen Spalten werden in der folgenden Tabelle angezeigt.  
  
|table_name|COLUMN_NAME|KEY_SEQ|  
|-----------------|------------------|--------------|  
|ORDERS|"ORDERID"|1|  
  
 Als Nächstes das Beispiel ruft **SQLForeignKeys** um die Fremdschlüssel in anderen Tabellen zu erhalten, die den Primärschlüssel der Tabelle ORDERS verweisen. Das Resultset müssen eine Zeile; die wichtigen Spalten werden in der folgenden Tabelle angezeigt.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|ORDERS|CUSTID|ZEILEN|CUSTID|1|  
  
 Im Beispiel zum Schluss ruft **SQLForeignKeys** Fremdschlüssel in der ORDERS-Tabelle abgerufen, die auf den primären Schlüssel der anderen Tabellen verweisen. Das Resultset müssen eine Zeile; die wichtigen Spalten werden in der folgenden Tabelle angezeigt.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|KUNDEN|CUSTID|ORDERS|CUSTID|1|  
  
```cpp  
#define TAB_LEN SQL_MAX_TABLE_NAME_LEN + 1  
#define COL_LEN SQL_MAX_COLUMN_NAME_LEN + 1  
  
LPSTR   szTable;              /* Table to display */  
  
UCHAR szPkTable[TAB_LEN];   /* Primary key table name */  
UCHAR szFkTable[TAB_LEN];   /* Foreign key table name */  
UCHAR szPkCol[COL_LEN];     /* Primary key column */  
UCHAR szFkCol[COL_LEN];     /* Foreign key column */  
  
SQLHSTMT      hstmt;  
SQLINTEGER    cbPkTable, cbPkCol, cbFkTable, cbFkCol, cbKeySeq;  
SQLSMALLINT   iKeySeq;  
SQLRETURN     retcode;  
  
// Bind the columns that describe the primary and foreign keys.  
// Ignore the table schema, name, and catalog for this example.  
  
SQLBindCol(hstmt, 3, SQL_C_CHAR, szPkTable, TAB_LEN, &cbPkTable);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, szPkCol, COL_LEN, &cbPkCol);  
SQLBindCol(hstmt, 5, SQL_C_SSHORT, &iKeySeq, TAB_LEN, &cbKeySeq);  
SQLBindCol(hstmt, 7, SQL_C_CHAR, szFkTable, TAB_LEN, &cbFkTable);  
SQLBindCol(hstmt, 8, SQL_C_CHAR, szFkCol, COL_LEN, &cbFkCol);  
  
strcpy_s(szTable, sizeof(szTable), "ORDERS");  
  
/* Get the names of the columns in the primary key. */  
  
retcode = SQLPrimaryKeys(hstmt,  
         NULL, 0,             /* Catalog name */  
         NULL, 0,             /* Schema name */  
         szTable, SQL_NTS);   /* Table name */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL SUCCESS_WITH_INFO)) {  
  
   /* Fetch and display the result set. This will be a list of the */  
   /* columns in the primary key of the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "Table: %s Column: %s Key Seq: %hd \n", szPkTable, szPkCol,  
      iKeySeq);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys that refer to ORDERS primary key.*/   
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,            /* Primary catalog */  
         NULL, 0,            /* Primary schema */  
         szTable, SQL_NTS,   /* Primary table */  
         NULL, 0,            /* Foreign catalog */  
         NULL, 0,            /* Foreign schema */  
         NULL, 0);           /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* foreign keys in other tables that refer to the ORDERS */  
/* primary key. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s ) <-- %-s ( %-s )\n", szPkTable,  
               szPkCol, szFkTable, szFkCol);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys in the ORDERS table. */  
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,             /* Primary catalog */  
         NULL, 0,             /* Primary schema */  
         NULL, 0,             /* Primary table */  
         NULL, 0,             /* Foreign catalog */  
         NULL, 0,             /* Foreign schema */  
         szTable, SQL_NTS);   /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* primary keys in other tables that are referred to by foreign */  
/* keys in the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s )--> %-s ( %-s )\n", szFkTable, szFkCol, szPkTable, szPkCol);  
}  
  
/* Free the hstmt. */  
SQLFreeStmt(hstmt, SQL_DROP);  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben der Spalten eines Primärschlüssels|[SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
|Zurückgeben von Statistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
