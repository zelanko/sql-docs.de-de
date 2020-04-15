---
title: SQLForeignKeys-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5f2769fb378a5ee989fb6a0351537edb3de03469
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285860"
---
# <a name="sqlforeignkeys-function"></a>SQLForeignKeys-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLForeignKeys** kann zurückgeben:  
  
-   Eine Liste von Fremdschlüsseln in der angegebenen Tabelle (Spalten in der angegebenen Tabelle, die auf Primärschlüssel in anderen Tabellen verweisen).  
  
-   Eine Liste von Fremdschlüsseln in anderen Tabellen, die auf den Primärschlüssel in der angegebenen Tabelle verweisen.  
  
 Der Treiber gibt jede Liste als Ergebnissatz für die angegebene Anweisung zurück.  
  
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
 [Eingabe] Katalogname der Primärschlüsseltabelle. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Tabellen, die keine Kataloge haben. *PKCatalogName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *PKCatalogName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *PKCatalogName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Eingabe] Länge von **PKCatalogName*in Zeichen.  
  
 *PKSchemaName*  
 [Eingabe] Schemaname der Primärschlüsseltabelle. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Tabellen, die keine Schemas haben. *PKSchemaName* darf kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das attribut SQL_ATTR_METADATA_ID-Anweisung auf SQL_TRUE festgelegt ist, wird *PKSchemaName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es SQL_FALSE ist, ist *PKSchemaName* ein gewöhnliches Argument; es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength2*  
 [Eingabe] Länge von **PKSchemaName*, in Zeichen.  
  
 *PKTableName*  
 [Eingabe] Primärschlüsseltabellenname. *PKTableName* kann kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *PKTableName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *PKTableName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength3*  
 [Eingabe] Länge von **PKTableName*, in Zeichen.  
  
 *FKCatalogName*  
 [Eingabe] Fremdschlüsseltabellenkatalogname. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Tabellen, die keine Kataloge haben. *FKCatalogName* kann kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *FKCatalogName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE, ist *FKCatalogName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength4*  
 [Eingabe] Länge von **FKCatalogName*, in Zeichen.  
  
 *FKSchemaName*  
 [Eingabe] Fremdschlüsseltabellenschemaname. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, bezeichnet eine leere Zeichenfolge ("") die Tabellen, die keine Schemas haben. *FKSchemaName* kann kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das Attribut SQL_ATTR_METADATA_ID Anweisung auf SQL_TRUE festgelegt ist, wird *FKSchemaName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE, ist *FKSchemaName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength5*  
 [Eingabe] Länge von **FKSchemaName*, in Zeichen.  
  
 *FKTableName*  
 [Eingabe] Fremdschlüsseltabellenname. *FKTableName* kann kein Zeichenfolgensuchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID Anweisungsattribut auf SQL_TRUE festgelegt ist, wird *FKTableName* als Bezeichner behandelt, und seine Anfrage ist nicht signifikant. Wenn es sich um SQL_FALSE handelt, ist *FKTableName* ein gewöhnliches Argument. es wird buchstäblich behandelt, und sein Fall ist bedeutsam.  
  
 *NameLength6*  
 [Eingabe] Länge von **FKTableName*, in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLForeignKeys** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von SQLForeignKeys zurückgegeben werden, und es werden die **SQLSTATE-Werte** im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|24.000|Ungültiger Cursorstatus|Im *StatementHandle*wurde ein Cursor geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.<br /><br /> Im *StatementHandle*wurde ein Cursor geöffnet, **SQLFetch** oder **SQLFetchScroll** wurden jedoch nicht aufgerufen.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcendeadlocks mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für den *StatementHandle*aufgerufen, und dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) Die Argumente *PKTableName* und *FKTableName* waren beide NULL-Zeiger.<br /><br /> Das SQL_ATTR_METADATA_ID Anweisungsattribut wurde auf SQL_TRUE festgelegt, das Argument *FKCatalogName* oder *PKCatalogName* war ein Nullzeiger, und die SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) Das SQL_ATTR_METADATA_ID-Anweisungsattribut wurde auf SQL_TRUE festgelegt, und das Argument *FKSchemaName*, *PKSchemaName*, *FKTableName*oder *PKTableName* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die SQLForeignKeys-Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der Wert eines der Argumente für die Namenslänge war kleiner als 0, aber nicht gleich SQL_NTS.|  
|||Der Wert eines der Namenslängenargumente hat den maximalen Längenwert für den entsprechenden Namen überschritten. (Siehe "Kommentare.")|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Es wurde ein Katalogname angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schemaname angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.|  
|||Die Kombination der aktuellen Einstellungen der SQL_ATTR_CONCURRENCY- und SQL_ATTR_CURSOR_TYPE-Anweisungsattribute wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde auf SQL_UB_VARIABLE festgelegt, und das SQL_ATTR_CURSOR_TYPE Anweisungsattribut wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Der Abfragetimeoutzeitraum ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeoutzeitraum wird über **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Informationen dazu, wie die von dieser Funktion zurückgegebenen Informationen verwendet werden können, finden Sie unter [Verwendung von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Wenn \* *PKTableName* einen Tabellennamen enthält, gibt **SQLForeignKeys** ein Resultset zurück, das den Primärschlüssel der angegebenen Tabelle und alle Fremdschlüssel enthält, auf die sie verweist. Die Liste der Fremdschlüssel in anderen Tabellen enthält keine Fremdschlüssel, die auf eindeutige Einschränkungen in der angegebenen Tabelle verweisen.  
  
 Wenn \* *FKTableName* einen Tabellennamen enthält, gibt **SQLForeignKeys** ein Resultset zurück, das alle Fremdschlüssel in der angegebenen Tabelle enthält, die auf Primärschlüssel in anderen Tabellen und die Primärschlüssel in den anderen Tabellen verweisen, auf die sie verweisen. Die Liste der Fremdschlüssel in der angegebenen Tabelle enthält keine Fremdschlüssel, die auf eindeutige Einschränkungen in anderen Tabellen verweisen.  
  
 Wenn \*sowohl *PKTableName* \*als auch *FKTableName* Tabellennamen enthalten, gibt **SQLForeignKeys** die Fremdschlüssel in der in \* *FKTableName* angegebenen Tabelle zurück, die auf den Primärschlüssel der tabelle verweisen, die in **PKTableName*angegeben ist. Dies sollte höchstens ein Schlüssel sein.  
  
> [!NOTE]  
>  Weitere Informationen zur allgemeinen Verwendung, Argumente und zurückgegebenen Daten von ODBC-Katalogfunktionen finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLForeignKeys** gibt Ergebnisse als Standardergebnissatz zurück. Wenn die Fremdschlüssel, die einem Primärschlüssel zugeordnet sind, angefordert werden, wird das Resultset nach FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME und KEY_SEQ sortiert. Wenn die Primärschlüssel, die einem Fremdschlüssel zugeordnet sind, angefordert werden, wird das Resultset nach PKTABLE_CAT, PKTABLE_SCHEM, PKTABLE_NAME und KEY_SEQ sortiert. In der folgenden Tabelle sind die Spalten im Resultset aufgeführt.  
  
 Die Längen der VARCHAR-Spalten werden in der Tabelle nicht angezeigt. die tatsächlichen Längen hängen von der Datenquelle ab. Um die tatsächlichen Längen der PKTABLE_CAT oder FKTABLE_CAT, PKTABLE_SCHEM oder FKTABLE_SCHEM, PKTABLE_NAME oder FKTABLE_NAME und PKCOLUMN_NAME oder FKCOLUMN_NAME Spalten zu bestimmen, kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN aufrufen.  
  
 Die folgenden Spalten wurden für ODBC 3 *.x umbenannt.* Die Änderungen des Spaltennamens wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer binden.  
  
|ODBC 2.0-Säule|ODBC 3 *.x-Säule*|  
|---------------------|-----------------------|  
|PKTABLE_QUALIFIER|PKTABLE_CAT|  
|PKTABLE_OWNER|PKTABLE_SCHEM|  
|FKTABLE_QUALIFIER|FK_TABLE_CAT|  
|FKTABLE_OWNER|FKTABLE_SCHEM|  
  
 In der folgenden Tabelle sind die Spalten im Resultset aufgeführt. Zusätzliche Spalten jenseits von Spalte 14 (REMARKS) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf treiberspezifische Spalten erhalten, indem sie vom Ende des Resultsets herunterzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [Von Katalogfunktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|PKTABLE_CAT (ODBC 1.0)|1|Varchar|Katalogname der Primärschlüsseltabelle; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für tabellen zurück, die keine Kataloge haben.|  
|PKTABLE_SCHEM (ODBC 1.0)|2|Varchar|Schemaname der Primärschlüsseltabelle; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für Tabellen zurück, die keine Schemas haben.|  
|PKTABLE_NAME (ODBC 1.0)|3|Varchar nicht NULL|Primärschlüsseltabellenname.|  
|PKCOLUMN_NAME (ODBC 1.0)|4|Varchar nicht NULL|Primärschlüsselspaltenname. Der Treiber gibt eine leere Zeichenfolge für eine Spalte zurück, die keinen Namen hat.|  
|FKTABLE_CAT (ODBC 1.0)|5|Varchar|Katalogname für Fremdschlüsseltabellen; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für tabellen zurück, die keine Kataloge haben.|  
|FKTABLE_SCHEM (ODBC 1.0)|6|Varchar|Verzeichnisschemaname für Fremdschlüsseltabellen; NULL, wenn sie nicht auf die Datenquelle anwendbar ist. Wenn ein Treiber Schemas für einige Tabellen unterstützt, jedoch nicht für andere, z. B. wenn der Treiber Daten aus verschiedenen DBMS abruft, gibt er eine leere Zeichenfolge ("") für Tabellen zurück, die keine Schemas haben.|  
|FKTABLE_NAME (ODBC 1.0)|7|Varchar nicht NULL|Fremdschlüsseltabellenname.|  
|FKCOLUMN_NAME (ODBC 1.0)|8|Varchar nicht NULL|Fremdschlüsselspaltenname. Der Treiber gibt eine leere Zeichenfolge für eine Spalte zurück, die keinen Namen hat.|  
|KEY_SEQ (ODBC 1.0)|9|Smallint nicht NULL|Spaltensequenznummer im Schlüssel (beginnend mit 1).|  
|UPDATE_RULE (ODBC 1.0)|10|Smallint|Aktion, die auf den Fremdschlüssel angewendet werden soll, wenn der SQL-Vorgang **UPDATE**ist. Kann einen der folgenden Werte aufweisen. (Die referenzierte Tabelle ist die Tabelle mit dem Primärschlüssel; die referenzierende Tabelle ist die Tabelle mit dem Fremdschlüssel.)<br /><br /> SQL_CASCADE: Wenn der Primärschlüssel der referenzierten Tabelle aktualisiert wird, wird auch der Fremdschlüssel der referenzierenden Tabelle aktualisiert.<br /><br /> SQL_NO_ACTION: Wenn eine Aktualisierung des Primärschlüssels der referenzierten Tabelle einen "baumelnden Verweis" in der referenzierenden Tabelle verursachen würde (d. h., Zeilen in der Referenztabelle hätten keine Gegenstücke in der referenzierten Tabelle), wird die Aktualisierung abgelehnt. Wenn eine Aktualisierung des Fremdschlüssels der referenzierenden Tabelle einen Wert einführt, der nicht als Wert des Primärschlüssels der referenzierten Tabelle vorhanden ist, wird die Aktualisierung abgelehnt. (Diese Aktion entspricht der SQL_RESTRICT Aktion in ODBC 2 *.x*.)<br /><br /> SQL_SET_NULL: Wenn eine oder mehrere Zeilen in der referenzierten Tabelle so aktualisiert werden, dass eine oder mehrere Komponenten des Primärschlüssels geändert werden, werden die Komponenten des Fremdschlüssels in der Referenztabelle, die den geänderten Komponenten des Primärschlüssels entsprechen, in allen übereinstimmenden Zeilen der referenzierenden Tabelle auf NULL gesetzt.<br /><br /> SQL_SET_DEFAULT: Wenn eine oder mehrere Zeilen in der referenzierten Tabelle so aktualisiert werden, dass eine oder mehrere Komponenten des Primärschlüssels geändert werden, werden die Komponenten des Fremdschlüssels in der Referenztabelle, die den geänderten Komponenten des Primärschlüssels entsprechen, in allen übereinstimmenden Zeilen der referenzierenden Tabelle auf die entsprechenden Standardwerte festgelegt.<br /><br /> NULL, wenn sie nicht auf die Datenquelle anwendbar ist.|  
|DELETE_RULE (ODBC 1.0)|11|Smallint|Aktion, die auf den Fremdschlüssel angewendet werden soll, wenn der SQL-Vorgang **DELETE**ist. Kann einen der folgenden Werte aufweisen. (Die referenzierte Tabelle ist die Tabelle mit dem Primärschlüssel; die referenzierende Tabelle ist die Tabelle mit dem Fremdschlüssel.)<br /><br /> SQL_CASCADE: Wenn eine Zeile in der referenzierten Tabelle gelöscht wird, werden auch alle übereinstimmenden Zeilen in den referenzierenden Tabellen gelöscht.<br /><br /> SQL_NO_ACTION: Wenn ein Löschen einer Zeile in der referenzierten Tabelle einen "baumelnden Verweis" in der referenzierenden Tabelle verursachen würde (d. h., Zeilen in der Referenztabelle hätten keine Gegenstücke in der referenzierten Tabelle), wird die Aktualisierung abgelehnt. (Diese Aktion entspricht der SQL_RESTRICT Aktion in ODBC 2 *.x*.)<br /><br /> SQL_SET_NULL: Wenn eine oder mehrere Zeilen in der referenzierten Tabelle gelöscht werden, wird jede Komponente des Fremdschlüssels der referenzierenden Tabelle in allen übereinstimmenden Zeilen der referenzierenden Tabelle auf NULL gesetzt.<br /><br /> SQL_SET_DEFAULT: Wenn eine oder mehrere Zeilen in der referenzierten Tabelle gelöscht werden, wird jede Komponente des Fremdschlüssels der referenzierenden Tabelle in allen übereinstimmenden Zeilen der referenzierenden Tabelle auf den entsprechenden Standardwert gesetzt.<br /><br /> NULL, wenn sie nicht auf die Datenquelle anwendbar ist.|  
|FK_NAME (ODBC 2.0)|12|Varchar|Fremdschlüsselname. NULL, wenn sie nicht auf die Datenquelle anwendbar ist.|  
|PK_NAME (ODBC 2.0)|13|Varchar|Primärschlüsselname. NULL, wenn sie nicht auf die Datenquelle anwendbar ist.|  
|VERSCHWENSBARKEIT (ODBC 3.0)|14|Smallint|SQL_INITIALLY_DEFERRED, SQL_INITIALLY_IMMEDIATE, SQL_NOT_DEFERRABLE.|  
  
## <a name="code-example"></a>Codebeispiel  
 Wie in der folgenden Tabelle dargestellt, werden in diesem Beispiel drei Tabellen mit dem Namen ORDERS, LINES und CUSTOMERS verwendet.  
  
|ORDERS|Linien|Kunden|  
|------------|-----------|---------------|  
|Orderid|Orderid|CUSTID|  
|CUSTID|Linien|NAME|  
|OPENDATE|PARTID|Adresse|  
|Verkäufer|Menge|TELEFON|  
|STATUS|||  
  
 In der Tabelle ORDERS identifiziert CUSTID den Debitor, an den der Verkauf erfolgt ist. Es ist ein Fremdschlüssel, der in der TABELLE CUSTOMERS auf CUSTID verweist.  
  
 In der Tabelle LINES identifiziert ORDERID den Auftrag, dem die Position zugeordnet ist. Es ist ein Fremdschlüssel, der in der Tabelle ORDERS auf ORDERID verweist.  
  
 In diesem Beispiel wird **SQLPrimaryKeys** aufruft, um den Primärschlüssel der ORDERS-Tabelle abzuruft. Das Resultset hat eine Zeile. Die wichtigen Spalten sind in der folgenden Tabelle dargestellt.  
  
|table_name|COLUMN_NAME|KEY_SEQ|  
|-----------------|------------------|--------------|  
|ORDERS|Orderid|1|  
  
 Als Nächstes ruft das Beispiel **SQLForeignKeys** auf, um die Fremdschlüssel in anderen Tabellen abzuruft, die auf den Primärschlüssel der ORDERS-Tabelle verweisen. Das Resultset hat eine Zeile. Die wichtigen Spalten sind in der folgenden Tabelle dargestellt.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|ORDERS|CUSTID|Linien|CUSTID|1|  
  
 Schließlich ruft das Beispiel **SQLForeignKeys** auf, um die Fremdschlüssel in der Tabelle ORDERS abzuruft, die auf die Primärschlüssel anderer Tabellen verweisen. Das Resultset hat eine Zeile. Die wichtigen Spalten sind in der folgenden Tabelle dargestellt.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|Kunden|CUSTID|ORDERS|CUSTID|1|  
  
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
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in einer vorwärtsgerichteten Richtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben der Spalten eines Primärschlüssels|[SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
|Zurückgeben von Tabellenstatistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
