---
description: SQLForeignKeys-Funktion
title: Sqlfremdnkeys-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: 802153837d53c6886b44511fbdffe6efa6b83281
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491303"
---
# <a name="sqlforeignkeys-function"></a>SQLForeignKeys-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **Sqlfremdnkeys** kann Folgendes zurückgeben:  
  
-   Eine Liste der Fremdschlüssel in der angegebenen Tabelle (Spalten in der angegebenen Tabelle, die auf Primärschlüssel in anderen Tabellen verweisen).  
  
-   Eine Liste von Fremdschlüsseln in anderen Tabellen, die auf den Primärschlüssel in der angegebenen Tabelle verweisen.  
  
 Der Treiber gibt jede Liste als Resultset für die angegebene Anweisung zurück.  
  
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
 Der Anweisungs Handle.  
  
 *PKCatalogName akzeptiert*  
 Der Katalog Name der Primärschlüssel Tabelle. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die nicht über Kataloge verfügen. *PKCatalogName* darf kein Zeichen folgen-Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *PKCatalogName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist " *PKCatalogName* " ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung. Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Der Länge von **PKCatalogName*in Zeichen.  
  
 *Pkschemaname*  
 Der Schema Name der Primärschlüssel Tabelle. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas aufweisen. " *Pkschemaname* " darf kein Zeichen folgen Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *pkschemaname* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist " *pkschemaname* " ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength2*  
 Der Länge von **pkschemaname*in Zeichen.  
  
 *PKTableName*  
 Der Name der Primärschlüssel Tabelle. " *PKTableName* " darf kein Muster für eine Zeichen folgen Suche enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *PKTableName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist " *PKTableName* " ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength3*  
 Der Länge von **PKTableName*in Zeichen.  
  
 *Parameter FKCatalogName*  
 Der Katalog Name der Fremdschlüssel Tabelle. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die nicht über Kataloge verfügen. " *Skcatalogname* " darf kein Zeichen folgen Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *FKCatalogName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist " *skcatalogname* " ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength4*  
 Der Länge*von * "**" in Zeichen.  
  
 *Name des Datei namens*  
 Der Schema Name der Fremdschlüssel Tabelle. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, gibt eine leere Zeichenfolge ("") die Tabellen an, die keine Schemas aufweisen. "File Schema *Name* " darf kein Zeichen folgen Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *fkschemaname* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist "f. Schema *Name* " ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength5*  
 Der Länge von * File Schema*Name*in Zeichen.  
  
 *"File Name"*  
 Der Name der Fremdschlüssel Tabelle. " *Sktablename* " darf kein Zeichen folgen Suchmuster enthalten.  
  
 Wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_TRUE festgelegt ist, wird *FKTableName* als Bezeichner behandelt, und die Groß-/Kleinschreibung ist nicht signifikant. Wenn Sie SQL_FALSE ist, ist " *f* " ein normales Argument. Sie wird buchstäblich behandelt, und die Groß-/Kleinschreibung ist von Bedeutung.  
  
 *NameLength6*  
 Der Länge*von * "**" in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlfremdnkeys** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **sqlfremdnkeys** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Ein Cursor war auf dem *StatementHandle*geöffnet, und **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen. Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.<br /><br /> Ein Cursor war auf dem *StatementHandle*geöffnet, aber **SQLFetch** oder **SQLFetchScroll** wurde nicht aufgerufen.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde ein Rollback ausgeführt, weil ein Ressourcen Deadlock mit einer anderen Transaktion aufgetreten ist.|  
|40003|Anweisungs Vervollständigung unbekannt|Bei der zugeordneten Verbindung ist während der Ausführung dieser Funktion ein Fehler aufgetreten, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen, und anschließend wurde die Funktion für " *StatementHandle*" erneut aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) die Argumente " *PKTableName* " und " *sktablename* " waren beide NULL-Zeiger.<br /><br /> Das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, das *FKCatalogName* -Argument oder das *PKCatalogName* -Argument war ein NULL-Zeiger, und der SQL_CATALOG_NAME *InfoType* gibt zurück, dass Katalognamen unterstützt werden.<br /><br /> (DM) das SQL_ATTR_METADATA_ID Statement-Attribut wurde auf SQL_TRUE festgelegt, und das Argument *fkschemaname*, *pkschemaname*, *FKTableName*oder *PKTableName* war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die sqlfremdnkeys-Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der Wert eines der namens Längen Argumente war kleiner als 0 (null), aber nicht gleich SQL_NTS.|  
|||Der Wert eines der namens Längen Argumente hat den maximalen Längen Wert für den entsprechenden Namen überschritten. (Siehe "Kommentare")|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert|Es wurde ein Katalog Name angegeben, und der Treiber oder die Datenquelle unterstützt keine Kataloge.<br /><br /> Es wurde ein Schema Name angegeben, und der Treiber oder die Datenquelle unterstützt keine Schemas.|  
|||Die Kombination der aktuellen Einstellungen der Attribute SQL_ATTR_CONCURRENCY und SQL_ATTR_CURSOR_TYPE Anweisung wurde vom Treiber oder der Datenquelle nicht unterstützt.<br /><br /> Das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_VARIABLE festgelegt, und das Attribut der SQL_ATTR_CURSOR_TYPE-Anweisung wurde auf einen Cursortyp festgelegt, für den der Treiber keine Lesezeichen unterstützt.|  
|HYT00|Timeout abgelaufen|Das Abfrage Timeout ist abgelaufen, bevor die Datenquelle das Resultset zurückgegeben hat. Der Timeout Zeitraum wird mithilfe von **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT festgelegt.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Informationen dazu, wie die von dieser Funktion zurückgegebenen Informationen verwendet werden können, finden Sie unter [Verwenden von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Wenn " \* *PKTableName* " einen Tabellennamen enthält, gibt **sqlforeign nkeys** ein Resultset zurück, das den Primärschlüssel der angegebenen Tabelle und alle Fremdschlüssel enthält, die darauf verweisen. Die Liste der Fremdschlüssel in anderen Tabellen enthält keine Fremdschlüssel, die auf eindeutige Einschränkungen in der angegebenen Tabelle verweisen.  
  
 Wenn \* *FKTableName* einen Tabellennamen enthält, gibt **sqlforeign nkeys** ein Resultset zurück, das alle Fremdschlüssel in der angegebenen Tabelle enthält, die auf Primärschlüssel in anderen Tabellen verweisen, und die Primärschlüssel in den anderen Tabellen, auf die Sie verweisen. Die Liste der Fremdschlüssel in der angegebenen Tabelle enthält keine Fremdschlüssel, die auf eindeutige Einschränkungen in anderen Tabellen verweisen.  
  
 Wenn sowohl \* *PKTableName* als auch \* *FKTableName* Tabellennamen enthalten, gibt **sqlforeign nkeys** die Fremdschlüssel in der in \* *FKTableName* angegebenen Tabelle zurück, die auf den Primärschlüssel der in **PKTableName*angegebenen Tabelle verweisen. Dabei sollte es sich höchstens um einen Schlüssel handeln.  
  
> [!NOTE]  
>  Weitere Informationen über die allgemeine Verwendung, Argumente und zurückgegebene Daten von ODBC-Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **Sqlfremdnkeys** gibt Ergebnisse als Standardresultset zurück. Wenn die einem Primärschlüssel zugeordneten Fremdschlüssel angefordert werden, wird das Resultset nach FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME und KEY_SEQ geordnet. Wenn die einem Fremdschlüssel zugeordneten Primärschlüssel angefordert werden, wird das Resultset nach PKTABLE_CAT, PKTABLE_SCHEM, PKTABLE_NAME und KEY_SEQ geordnet. In der folgenden Tabelle werden die Spalten im Resultset aufgelistet.  
  
 Die Längen von varchar-Spalten werden in der Tabelle nicht angezeigt. die tatsächlichen Längen hängen von der Datenquelle ab. Um die tatsächliche Länge der PKTABLE_CAT oder FKTABLE_CAT, der PKTABLE_SCHEM-oder FKTABLE_SCHEM-, PKTABLE_NAME-oder fktable_name-und PKCOLUMN_NAME-oder FKCOLUMN_NAME-Spalten zu ermitteln, kann eine Anwendung **SQLGetInfo** mit den Optionen SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN und SQL_MAX_COLUMN_NAME_LEN aufrufen.  
  
 Die folgenden Spalten wurden für ODBC 3 *. x umbenannt.* Die Spaltennamen Änderungen wirken sich nicht auf die Abwärtskompatibilität aus, da Anwendungen nach Spaltennummer gebunden werden.  
  
|ODBC 2,0-Spalte|ODBC 3 *. x* -Spalte|  
|---------------------|-----------------------|  
|PKTABLE_QUALIFIER|PKTABLE_CAT|  
|PKTABLE_OWNER|PKTABLE_SCHEM|  
|FKTABLE_QUALIFIER|FK_TABLE_CAT|  
|FKTABLE_OWNER|FKTABLE_SCHEM|  
  
 In der folgenden Tabelle werden die Spalten im Resultset aufgelistet. Zusätzliche Spalten jenseits der Spalte 14 (Hinweise) können vom Treiber definiert werden. Eine Anwendung sollte Zugriff auf Treiber spezifische Spalten erhalten, indem Sie vom Ende des Resultsets abzählt, anstatt eine explizite Ordinalposition anzugeben. Weitere Informationen finden Sie unter [von Katalog Funktionen zurückgegebene Daten](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Spaltenname|Spaltennummer|Datentyp|Kommentare|  
|-----------------|-------------------|---------------|--------------|  
|PKTABLE_CAT (ODBC 1,0)|1|Varchar|Katalog Name der Primärschlüssel Tabelle; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Tabellen zurückgegeben, die über keine Kataloge verfügen.|  
|PKTABLE_SCHEM (ODBC 1,0)|2|Varchar|Schema Name der Primärschlüssel Tabelle; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für Tabellen zurückgegeben, die keine Schemas aufweisen.|  
|PKTABLE_NAME (ODBC 1,0)|3|Varchar not NULL|Name der Primärschlüssel Tabelle.|  
|PKCOLUMN_NAME (ODBC 1,0)|4|Varchar not NULL|Name der Primärschlüssel Spalte. Der Treiber gibt eine leere Zeichenfolge für eine Spalte zurück, die über keinen Namen verfügt.|  
|FKTABLE_CAT (ODBC 1,0)|5|Varchar|Katalog Name der Fremdschlüssel Tabelle; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber Kataloge für einige Tabellen unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für die Tabellen zurückgegeben, die über keine Kataloge verfügen.|  
|FKTABLE_SCHEM (ODBC 1,0)|6|Varchar|Schema Name der Fremdschlüssel Tabelle; NULL, wenn nicht auf die Datenquelle anwendbar. Wenn ein Treiber für einige Tabellen Schemas unterstützt, aber nicht für andere, z. b. wenn der Treiber Daten von einem anderen DBMSs abruft, wird eine leere Zeichenfolge ("") für Tabellen zurückgegeben, die keine Schemas aufweisen.|  
|Fktable_name (ODBC 1,0)|7|Varchar not NULL|Name der Fremdschlüssel Tabelle.|  
|FKCOLUMN_NAME (ODBC 1,0)|8|Varchar not NULL|Name der Fremdschlüssel Spalte. Der Treiber gibt eine leere Zeichenfolge für eine Spalte zurück, die über keinen Namen verfügt.|  
|KEY_SEQ (ODBC 1,0)|9|Smallint nicht NULL|Spaltensequenznummer in Key (beginnend mit 1).|  
|UPDATE_RULE (ODBC 1,0)|10|Smallint|Aktion, die auf den Fremdschlüssel angewendet werden soll, wenn der SQL-Vorgang **aktualisiert**wird. Kann einen der folgenden Werte aufweisen. (Die Tabelle, auf die verwiesen wird, ist die Tabelle mit dem Primärschlüssel; die verweisende Tabelle ist die Tabelle mit dem Fremdschlüssel.)<br /><br /> SQL_CASCADE: Wenn der Primärschlüssel der Tabelle, auf die verwiesen wird, aktualisiert wird, wird auch der Fremdschlüssel der verweisenden Tabelle aktualisiert.<br /><br /> SQL_NO_ACTION: Wenn ein Update des Primärschlüssels der Tabelle, auf die verwiesen wird, einen "verbleibenden Verweis" in der verweisenden Tabelle auslöst (d. h., Zeilen in der verweisenden Tabelle enthalten keine Entsprechungen in der Tabelle, auf die verwiesen wird), wird das Update abgelehnt. Wenn ein Update des fremd Schlüssels der verweisenden Tabelle einen Wert enthält, der nicht als Wert des Primärschlüssels der Tabelle, auf die verwiesen wird, vorhanden ist, wird das Update abgelehnt. (Diese Aktion ist identisch mit der SQL_RESTRICT Aktion in ODBC 2 *. x*.)<br /><br /> SQL_SET_NULL: Wenn eine oder mehrere Zeilen in der Tabelle, auf die verwiesen wird, so aktualisiert werden, dass eine oder mehrere Komponenten des Primärschlüssels geändert werden, werden die Komponenten des fremd Schlüssels in der verweisenden Tabelle, die den geänderten Komponenten des Primärschlüssels entsprechen, in allen übereinstimmenden Zeilen der verweisenden Tabelle auf NULL festgelegt.<br /><br /> SQL_SET_DEFAULT: Wenn eine oder mehrere Zeilen in der Tabelle, auf die verwiesen wird, so aktualisiert werden, dass eine oder mehrere Komponenten des Primärschlüssels geändert werden, werden die Komponenten des fremd Schlüssels in der verweisenden Tabelle, die den geänderten Komponenten des Primärschlüssels entsprechen, auf die entsprechenden Standardwerte in allen übereinstimmenden Zeilen der verweisenden Tabelle festgelegt.<br /><br /> NULL, wenn nicht auf die Datenquelle anwendbar.|  
|DELETE_RULE (ODBC 1,0)|11|Smallint|Aktion, die auf den Fremdschlüssel angewendet werden soll, wenn der SQL-Vorgang **gelöscht**wird. Kann einen der folgenden Werte aufweisen. (Die Tabelle, auf die verwiesen wird, ist die Tabelle mit dem Primärschlüssel; die verweisende Tabelle ist die Tabelle mit dem Fremdschlüssel.)<br /><br /> SQL_CASCADE: Wenn eine Zeile in der Tabelle, auf die verwiesen wird, gelöscht wird, werden auch alle übereinstimmenden Zeilen in den verweisenden Tabellen gelöscht.<br /><br /> SQL_NO_ACTION: Wenn das Löschen einer Zeile in der Tabelle, auf die verwiesen wird, in der verweisenden Tabelle einen "verbleibenden Verweis" verursachen würde (d. h., Zeilen in der verweisenden Tabelle enthalten keine Entsprechungen in der Tabelle, auf die verwiesen wird), wird das Update abgelehnt. (Diese Aktion ist identisch mit der SQL_RESTRICT Aktion in ODBC 2 *. x*.)<br /><br /> SQL_SET_NULL: Wenn eine oder mehrere Zeilen in der Tabelle, auf die verwiesen wird, gelöscht werden, wird jede Komponente des fremd Schlüssels der verweisenden Tabelle in allen übereinstimmenden Zeilen der verweisenden Tabelle auf NULL festgelegt.<br /><br /> SQL_SET_DEFAULT: Wenn eine oder mehrere Zeilen in der Tabelle, auf die verwiesen wird, gelöscht werden, wird jede Komponente des fremd Schlüssels der verweisenden Tabelle auf den anwendbaren Standardwert in allen übereinstimmenden Zeilen der verweisenden Tabelle festgelegt.<br /><br /> NULL, wenn nicht auf die Datenquelle anwendbar.|  
|Fk_name (ODBC 2,0)|12|Varchar|Der Name des fremd Schlüssels. NULL, wenn nicht auf die Datenquelle anwendbar.|  
|PK_NAME (ODBC 2,0)|13|Varchar|Name des Primärschlüssels. NULL, wenn nicht auf die Datenquelle anwendbar.|  
|Verzögerung (ODBC 3,0)|14|Smallint|SQL_INITIALLY_DEFERRED, SQL_INITIALLY_IMMEDIATE SQL_NOT_DEFERRABLE.|  
  
## <a name="code-example"></a>Codebeispiel  
 Wie in der folgenden Tabelle dargestellt, werden in diesem Beispiel drei Tabellennamens Orders, Lines und Customers verwendet.  
  
|ORDERS|Betreff|Folgend|  
|------------|-----------|---------------|  
|ORDERID|ORDERID|CUSTID|  
|CUSTID|Betreff|NAME|  
|Opendate|PARTID|Adresse|  
|Vertriebsmitarbeiter|Mess|TELEFON|  
|STATUS|||  
  
 In der Tabelle Orders identifiziert CustID den Kunden, für den der Verkauf durchgeführt wurde. Es handelt sich um einen Fremdschlüssel, der auf CustID in der Customers-Tabelle verweist.  
  
 In der Tabelle Lines identifiziert OrderID die Bestellung, der das Zeilen Element zugeordnet ist. Es handelt sich um einen Fremdschlüssel, der auf OrderID in der Orders-Tabelle verweist.  
  
 In diesem Beispiel wird **SQLPrimaryKeys** aufgerufen, um den Primärschlüssel der Orders-Tabelle zu erhalten. Das Resultset weist eine Zeile auf. die signifikanten Spalten sind in der folgenden Tabelle aufgeführt.  
  
|table_name|COLUMN_NAME|KEY_SEQ|  
|-----------------|------------------|--------------|  
|ORDERS|ORDERID|1|  
  
 Im folgenden Beispiel wird **sqlforeign nkeys** aufgerufen, um die Fremdschlüssel in anderen Tabellen zu erhalten, die auf den Primärschlüssel der Orders-Tabelle verweisen. Das Resultset weist eine Zeile auf. die signifikanten Spalten sind in der folgenden Tabelle aufgeführt.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|ORDERS|CUSTID|Betreff|CUSTID|1|  
  
 Zum Schluss ruft das Beispiel **sqlforeign nkeys** auf, um die Fremdschlüssel in der Orders-Tabelle zu erhalten, die auf die Primärschlüssel anderer Tabellen verweisen. Das Resultset weist eine Zeile auf. die signifikanten Spalten sind in der folgenden Tabelle aufgeführt.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|Folgend|CUSTID|ORDERS|CUSTID|1|  
  
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
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Zurückgeben der Spalten eines Primärschlüssels|[SQLPrimaryKeys-Funktion](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
|Zurückgeben von Tabellenstatistiken und Indizes|[SQLStatistics-Funktion](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
