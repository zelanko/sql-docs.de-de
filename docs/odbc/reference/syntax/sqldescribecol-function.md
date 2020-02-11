---
title: SQLDescribeCol-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeCol
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeCol
helpviewer_keywords:
- SQLDescribeCol function [ODBC]
ms.assetid: eddef353-83f3-4a3c-8f24-f9ed888890a4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 63982d87f0dbbe0c8ab1a540185e298d9943f630
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68104793"
---
# <a name="sqldescribecol-function"></a>SQLDescribeCol-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLDescribeCol** gibt den Namen der Ergebnis Beschreibung, den Typ, die Spaltengröße, Dezimalstellen und die NULL-Zulässigkeit für eine Spalte im Resultset zurück. Diese Informationen sind auch in den Feldern des IRD verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLDescribeCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLCHAR *      ColumnName,  
      SQLSMALLINT    BufferLength,  
      SQLSMALLINT *  NameLengthPtr,  
      SQLSMALLINT *  DataTypePtr,  
      SQLULEN *      ColumnSizePtr,  
      SQLSMALLINT *  DecimalDigitsPtr,  
      SQLSMALLINT *  NullablePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *ColumnNumber*  
 Der Die Spaltennummer der Ergebnisdaten, die sequenziell in der Reihenfolge der Spalten sortiert werden, beginnend bei 1. Das *ColumnNumber* -Argument kann auch auf 0 festgelegt werden, um die Lesezeichen Spalte zu beschreiben.  
  
 *ColumnName*  
 Ausgeben Ein Zeiger auf einen null-terminierten Puffer, in den der Spaltenname zurückgegeben werden soll. Dieser Wert wird aus dem SQL_DESC_NAME-Feld des IRD gelesen. Wenn die Spalte unbenannt ist oder der Spaltenname nicht bestimmt werden kann, gibt der Treiber eine leere Zeichenfolge zurück.  
  
 Wenn *ColumnName* NULL ist, gibt *namelengthptr* weiterhin die Gesamtzahl der Zeichen zurück (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den von *ColumnName*verwiesen wird.  
  
 *Pufferlänge*  
 Der Länge des **ColumnName* -Puffers in Zeichen.  
  
 *Namelengthptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (ausgenommen der NULL-Beendigung) zurückgegeben werden \*soll, die in *ColumnName*zurückgegeben werden können. Wenn die Anzahl der zurück zugebende Zeichen größer als oder gleich *BufferLength*ist, wird der Spaltenname in \* *ColumnName* auf *BufferLength* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
 *DataTypePtr*  
 Ausgeben Zeiger auf einen Puffer, in den der SQL-Datentyp der Spalte zurückgegeben werden soll. Dieser Wert wird aus dem SQL_DESC_CONCISE_TYPE-Feld des IRD gelesen. Dies ist einer der Werte in SQL- [Datentypen](../../../odbc/reference/appendixes/sql-data-types.md)oder ein Treiber spezifischer SQL-Datentyp. Wenn der Datentyp nicht bestimmt werden kann, gibt der Treiber SQL_UNKNOWN_TYPE zurück.  
  
 In ODBC 3. " *x*", "SQL_TYPE_DATE", "SQL_TYPE_TIME" oder "SQL_TYPE_TIMESTAMP" wird in * \*"DataTypePtr* " für Datums-, Uhrzeit-oder Zeitstempel Daten zurückgegeben. in ODBC 2. *x*, SQL_DATE, SQL_TIME oder SQL_TIMESTAMP wird zurückgegeben. Der Treiber-Manager führt die erforderlichen Zuordnungen bei ODBC 2 aus. die *x* -Anwendung arbeitet mit ODBC 3. *x* -Treiber oder bei ODBC 3. die *x* -Anwendung arbeitet mit ODBC 2. *x* -Treiber  
  
 Wenn *ColumnNumber* gleich 0 (für eine Lesezeichen Spalte) ist, wird SQL_BINARY in * \*DataTypePtr* für Lesezeichen mit variabler Länge zurückgegeben. (SQL_INTEGER wird zurückgegeben, wenn Lesezeichen von ODBC 3 verwendet werden. *x* -Anwendung, die mit ODBC 2 arbeitet. *x* -Treiber oder ODBC 2. *x* -Anwendung, die mit ODBC 3 arbeitet. *x* -Treiber.)  
  
 Weitere Informationen zu diesen Datentypen finden Sie unter [SQL-Daten](../../../odbc/reference/appendixes/sql-data-types.md) Typen in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.  
  
 *ColumnSizePtr*  
 Ausgeben Ein Zeiger auf einen Puffer, in den die Größe (in Zeichen) der Spalte in der Datenquelle zurückgegeben werden soll. Wenn die Spaltengröße nicht bestimmt werden kann, gibt der Treiber 0 zurück. Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalstellen, Länge von Oktett übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.  
  
 *Decimaldigitsptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in den die Anzahl der Dezimalstellen der Spalte in der Datenquelle zurückgegeben werden soll. Wenn die Anzahl von Dezimalziffern nicht bestimmt werden kann oder nicht anwendbar ist, gibt der Treiber 0 zurück. Weitere Informationen zu Dezimalziffern finden Sie unter [Spaltengröße, Dezimalstellen, Länge des Oktetts übertragen und Anzeige Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.  
  
 *Nullableptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem ein Wert zurückgegeben werden soll, der angibt, ob die Spalte NULL-Werte zulässt. Dieser Wert wird aus dem SQL_DESC_NULLABLE-Feld des IRD gelesen. Der Wert ist einer der folgenden Werte:  
  
 SQL_NO_NULLS: die Spalte lässt keine NULL-Werte zu.  
  
 SQL_NULLABLE: die Spalte lässt NULL-Werte zu.  
  
 SQL_NULLABLE_UNKNOWN: der Treiber kann nicht bestimmen, ob die Spalte NULL-Werte zulässt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDescribeCol** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLDescribeCol** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Der \* *puffercolumnname* war nicht groß genug, um den gesamten Spaltennamen zurückzugeben, sodass der Spaltenname abgeschnitten wurde. Die Länge des nicht abgeschnittene Spaltennamens wird in **namelengthptr*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07005|Die vorbereitete Anweisung ist keine *Cursor Spezifikation* .|Die mit dem *StatementHandle* verknüpfte Anweisung hat kein Resultset zurückgegeben. Es waren keine zu beschreiften Spalten vorhanden.|  
|07009|Ungültiger deskriptorindex.|(DM) der für das Argument *ColumnNumber* angegebene Wert war gleich 0, und die Option SQL_ATTR_USE_BOOKMARKS Anweisung war SQL_UB_OFF.<br /><br /> Der für das Argument *ColumnNumber* angegebene Wert war größer als die Anzahl der Spalten im Resultset.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als **SQLDescribeCol** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) die Funktion wurde vor dem Aufrufen von **SQLPrepare**, **SQLExecute**oder einer Katalog Funktion für das Anweisungs Handle aufgerufen.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der für das Argument *BufferLength* angegebene Wert war kleiner als 0 (null).|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
 **SQLDescribeCol** kann jeden SQLSTATE zurückgeben, der von **SQLPrepare** oder **SQLExecute** zurückgegeben werden kann, wenn er nach **SQLPrepare** und vor **SQLExecute**aufgerufen wird, je nachdem, wann die Datenquelle die SQL-Anweisung auswertet, die dem Anweisungs Handle zugeordnet ist.  
  
 Aus Leistungsgründen sollte eine Anwendung **SQLDescribeCol** nicht vor dem Ausführen einer-Anweisung abrufen.  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung ruft **SQLDescribeCol** in der Regel nach einem Aufruf von **SQLPrepare** und vor oder nach dem zugehörigen Aufruf von **SQLExecute**auf. Eine Anwendung kann auch **SQLDescribeCol** nach einem **SQLExecDirect**-Befehl aufzurufen. Weitere Informationen finden Sie unter [Resultsetmetadaten](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLDescribeCol** Ruft den Spaltennamen, den Typ und die Länge ab, die von einer **Select** -Anweisung generiert werden. Wenn es sich bei der Spalte um einen Ausdruck handelt, ist **ColumnName* entweder eine leere Zeichenfolge oder ein Treiber definierter Name.  
  
> [!NOTE]  
>  ODBC unterstützt SQL_NULLABLE_UNKNOWN als Erweiterung, auch wenn in der "Open Group"-und der SQL-Zugriffs Gruppen-Schnittstellen Spezifikation die-Option für **SQLDescribeCol**nicht angegeben ist.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einem Resultset|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Abrufen mehrerer Daten Zeilen|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Zurückgeben der Anzahl von Resultsetspalten|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
