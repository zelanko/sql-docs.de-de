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
manager: craigg
ms.openlocfilehash: 1b8453d76dc2af0499dc8d8af2ca1ec3024aee83
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52523811"
---
# <a name="sqldescribecol-function"></a>SQLDescribeCol-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO-92  
  
 **Zusammenfassung**  
 **SQLDescribeCol** den Ergebnis-Deskriptor - Spaltenname, Datentyp, Spaltengröße, Dezimalstellen und NULL-Zulässigkeit - für eine Spalte im Resultset zurückgegeben. Diese Informationen sind auch in den Feldern des IRD verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 [Eingabe] Anweisungshandle.  
  
 *ColumnNumber*  
 [Eingabe] Spaltennummer der Ergebnisdaten, sortiert sequenziell in der wachsenden Spaltenreihenfolge, beginnend mit 1. Die *ColumnNumber* Argument kann auch auf 0 festgelegt werden, um die Lesezeichenspalte zu beschreiben.  
  
 *ColumnName*  
 [Ausgabe] Zeiger auf einen Null-terminierte Puffer in den Namen der Spalte zurückgegeben. Dieser Wert wird vom IRD SQL_DESC_NAME-Felds gelesen werden. Wenn die Spalte keinen Namen hat oder den Namen der Spalte kann nicht bestimmt werden, gibt der Treiber eine leere Zeichenfolge zurück.  
  
 Wenn *ColumnName* NULL ist, *NameLengthPtr* gibt die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *ColumnName*.  
  
 *BufferLength*  
 [Eingabe] Länge der **ColumnName* Puffers in Zeichen.  
  
 *NameLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe der Gesamtzahl der Zeichen, die (mit Ausnahme der null-Terminierung) zur Verfügung, die in zurückgegeben \* *ColumnName*. Wenn die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als oder gleich ist *Pufferlänge*, den Spaltennamen in \* *ColumnName* auf abgeschnitten *Pufferlänge*abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
 *DataTypePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem den SQL-Datentyp der Spalte zurückgegeben. Dieser Wert wird aus dem Feld SQL_DESC_CONCISE_TYPE vom IRD gelesen. Dies können die Werte in [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md), oder treiberspezifischen SQL-Datentyp. Wenn der Datentyp kann nicht bestimmt werden, gibt der Treiber SQL_UNKNOWN_TYPE zurück.  
  
 In ODBC 3. *x*, SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP wird zurückgegeben,  *\*DataTypePtr* für Datum, Uhrzeit oder Zeitstempeldaten; in ODBC 2. *X*, SQL_DATE, SQL_TIME oder SQL_TIMESTAMP wird zurückgegeben. Der Treiber-Manager führt die erforderlichen Mappings, wenn eine ODBC-2. *x* Anwendung arbeitet mit einer ODBC 3. *X* Treiber oder wenn eine ODBC 3. *X* Anwendung arbeitet mit einer ODBC 2. *X* Treiber.  
  
 Beim *ColumnNumber* ist gleich 0 (für eine Lesezeichenspalte) ist, wird im SQL_BINARY zurückgegeben  *\*DataTypePtr* variabler Länge, die Lesezeichen. (SQL_INTEGER wird zurückgegeben, wenn Lesezeichen von einer ODBC-3 verwendet werden. *x* Anwendung mit einer ODBC 2. *X* Treiber oder von einer ODBC 2. *X* Anwendung mit einer ODBC 3. *X* Treiber.)  
  
 Weitere Informationen zu diesen Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu Treiber-spezifische SQL-Datentypen finden Sie in der vom Treiber-Dokumentation.  
  
 *ColumnSizePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in die die Größe (in Zeichen) der Spalte in der Datenquelle zurückgegeben werden sollen. Wenn die Spaltengröße nicht bestimmt werden kann, gibt der Treiber 0 zurück. Weitere Informationen zu Spaltengröße, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.  
  
 *DecimalDigitsPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in die die Anzahl der Dezimalstellen der Spalte in der Datenquelle zurückgegeben werden sollen. Der Treiber gibt 0 zurück, wenn die Anzahl der Dezimalstellen kann nicht bestimmt werden, oder es nicht anwendbar ist. Weitere Informationen zu Dezimalstellen, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.  
  
 *NullablePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem einen Wert zurückgegeben, der angibt, ob die Spalte NULL-Werte zulässt. Dieser Wert wird aus dem Feld SQL_DESC_NULLABLE vom IRD gelesen. Der Wert ist eine der folgenden:  
  
 SQL_NO_NULLS: Die Spalte lässt keine NULL-Werte zu.  
  
 SQL_NULLABLE: Die Spalte lässt NULL-Werte zu.  
  
 SQL_NULLABLE_UNKNOWN: Der Treiber kann nicht bestimmen, wenn die Spalte NULL-Werte zulässt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDescribeCol** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit eine *HandleType*von SQL_HANDLE_STMT auf, und ein *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLDescribeCol** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Puffer \* *ColumnName* nicht groß genug war, des gesamten Spaltennamens, zurückgegeben werden, damit Sie den Namen der Spalte abgeschnitten wurde. Die Länge des Spaltennamens den ungekürzten wird zurückgegeben, **NameLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07005|Keine vorbereitete Anweisung eine *Cursor-Spezifikation*|Die zugeordnete Anweisung die *StatementHandle* hat ein Resultset nicht zurückgegeben. Es wurden keine Spalten aus, um zu beschreiben.|  
|07009|Ungültiger Deskriptorindex|(DM) der Wert für das Argument angegebene *ColumnNumber* war gleich 0 und der Option-Anweisung SQL_ATTR_USE_BOOKMARKS SQL_UB_OFF.<br /><br /> Der angegebene Wert für das Argument *ColumnNumber* war größer als die Anzahl der Spalten im Resultset.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherbelegungsfehler|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn **SQLDescribeCol** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) die Funktion wurde vor dem Aufruf aufgerufen **SQLPrepare**, **SQLExecute**, oder eine Katalogfunktion über das Anweisungshandle.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) für Argument angegebene Wert *Pufferlänge* war kleiner als 0.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
 **SQLDescribeCol** können alle SQLSTATE, der zurückgegeben werden kann zurückgeben **SQLPrepare** oder **SQLExecute** beim Aufruf nach **SQLPrepare** und vor dem **SQLExecute**, abhängig davon ab, wenn die Datenquelle für die SQL-Anweisung, die das Anweisungshandle zugeordneten auswertet.  
  
 Zur Verbesserung der Leistung, eine Anwendung nicht aufrufen sollten **SQLDescribeCol** vor der Ausführung einer Anweisung.  
  
## <a name="comments"></a>Kommentare  
 Ruft eine Anwendung in der Regel **SQLDescribeCol** nach einem Aufruf von **SQLPrepare** und vor oder nach dem zugehörigen Aufruf von **SQLExecute**. Eine Anwendung kann auch aufrufen **SQLDescribeCol** nach einem Aufruf von **SQLExecDirect**. Weitere Informationen finden Sie unter [Ergebnismetadaten festgelegt](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLDescribeCol** Ruft ab, der Name der Spalte, Typ und Länge von generiert eine **wählen** Anweisung. Wenn die Spalte ein Ausdruck, **ColumnName* ist entweder eine leere Zeichenfolge oder einen Treiber-definierten Namen.  
  
> [!NOTE]  
>  ODBC unterstützt SQL_NULLABLE_UNKNOWN als eine Erweiterung, obwohl die Open Group und SQL Zugriff Gruppe aufrufen Level-Interface-Spezifikation nicht die Option zum angeben, wird **SQLDescribeCol**.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Abrufen mehrerer Zeilen von Daten|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Die Anzahl der Resultsets zurückgeben von Resultsetspalten|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
