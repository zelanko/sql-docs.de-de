---
title: SQLDescribeCol-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c727f6b36930b0d2ad0d5a61592b83bcd4995426
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301170"
---
# <a name="sqldescribecol-function"></a>SQLDescribeCol-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLDescribeCol** gibt den Ergebnisdeskriptor - Spaltenname, Typ, Spaltengröße, Dezimalstellen und NULL-Wert - für eine Spalte im Resultset zurück. Diese Informationen sind auch in den Bereichen der IRD verfügbar.  
  
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
 [Eingabe] Anweisungshandle.  
  
 *ColumnNumber*  
 [Eingabe] Spaltenanzahl der Ergebnisdaten, sequenziell in steigender Spaltenreihenfolge sortiert, beginnend bei 1. Das *ColumnNumber-Argument* kann auch auf 0 gesetzt werden, um die Lesezeichenspalte zu beschreiben.  
  
 *ColumnName*  
 [Ausgabe] Zeiger auf einen null-beendeten Puffer, in dem der Spaltenname zurückgegeben werden soll. Dieser Wert wird aus dem SQL_DESC_NAME Feld des IRD gelesen. Wenn die Spalte unbenannt ist oder der Spaltenname nicht bestimmt werden kann, gibt der Treiber eine leere Zeichenfolge zurück.  
  
 Wenn *ColumnName* NULL ist, gibt *NameLengthPtr* weiterhin die Gesamtzahl der Zeichen zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den *ColumnName*zeigt.  
  
 *BufferLength*  
 [Eingabe] Länge des **ColumnName-Puffers* in Zeichen.  
  
 *NameLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (mit \*Ausnahme der Nullbeendigung) zurückgegeben werden soll, die in *ColumnName*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer oder gleich *BufferLength*ist, wird der Spaltenname in \* *ColumnName* auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
 *DataTypePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem der SQL-Datentyp der Spalte zurückgegeben werden soll. Dieser Wert wird aus dem SQL_DESC_CONCISE_TYPE Feld der IRD gelesen. Dies ist einer der Werte in [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md)oder ein treiberspezifischer SQL-Datentyp. Wenn der Datentyp nicht ermittelt werden kann, gibt der Treiber SQL_UNKNOWN_TYPE zurück.  
  
 In ODBC 3. *x*, SQL_TYPE_DATE, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP wird in * \*DataTypePtr* für Datums-, Uhrzeit- oder Zeitstempeldaten zurückgegeben. in ODBC 2. *x*, SQL_DATE, SQL_TIME oder SQL_TIMESTAMP zurückgegeben. Der Treiber-Manager führt die erforderlichen Zuordnungen aus, wenn ein ODBC 2. *x-Anwendung* arbeitet mit einem ODBC 3. *x-Treiber* oder wenn ein ODBC 3. *x-Anwendung* arbeitet mit einem ODBC 2. *x-Treiber.*  
  
 Wenn *ColumnNumber* gleich 0 ist (für eine Lesezeichenspalte), wird SQL_BINARY in * \*DataTypePtr* für Lesezeichen variabler Länge zurückgegeben. (SQL_INTEGER wird zurückgegeben, wenn Lesezeichen von einem ODBC 3 verwendet werden. *x* Anwendung, die mit einem ODBC 2 arbeitet. *x-Treiber* oder durch einen ODBC 2. *x* Anwendung, die mit einem ODBC 3 arbeitet. *x* x-Treiber.)  
  
 Weitere Informationen zu diesen Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.  
  
 *ColumnSizePtr*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die Größe (in Zeichen) der Spalte in der Datenquelle zurückgegeben werden soll. Wenn die Spaltengröße nicht bestimmt werden kann, gibt der Treiber 0 zurück. Weitere Informationen zur Spaltengröße finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.  
  
 *DecimalDigitsPtr*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die Anzahl der Dezimalstellen der Spalte in der Datenquelle zurückgegeben wird. Wenn die Anzahl der Dezimalstellen nicht bestimmt werden kann oder nicht anwendbar ist, gibt der Treiber 0 zurück. Weitere Informationen zu Dezimalstellen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.  
  
 *NullablePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem ein Wert zurückgegeben wird, der angibt, ob die Spalte NULL-Werte zulässt. Dieser Wert wird aus dem SQL_DESC_NULLABLE Feld der IRD gelesen. Der Wert ist einer der folgenden:  
  
 SQL_NO_NULLS: Die Spalte lässt keine NULL-Werte zu.  
  
 SQL_NULLABLE: Die Spalte lässt NULL-Werte zu.  
  
 SQL_NULLABLE_UNKNOWN: Der Treiber kann nicht ermitteln, ob die Spalte NULL-Werte zulässt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLDescribeCol** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLDescribeCol** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der \*Puffer *ColumnName* war nicht groß genug, um den gesamten Spaltennamen zurückzugeben, sodass der Spaltenname abgeschnitten wurde. Die Länge des nicht abgeschnittenen Spaltennamens wird in **NameLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07005|Vorbereitete Anweisung keine *Cursorspezifikation*|Die dem *StatementHandle* zugeordnete Anweisung hat kein Resultset zurückgegeben. Es gab keine Spalten zu beschreiben.|  
|07009|Ungültiger Deskriptorindex|(DM) Der für das Argument *ColumnNumber* angegebene Wert war gleich 0, und die SQL_ATTR_USE_BOOKMARKS Anweisungsoption wurde SQL_UB_OFF.<br /><br /> Der für das Argument *ColumnNumber* angegebene Wert war größer als die Anzahl der Spalten im Resultset.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als **SQLDescribeCol** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) Die Funktion wurde aufgerufen, bevor **SQLPrepare**, **SQLExecute**oder eine Katalogfunktion für das Anweisungshandle aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der für das Argument *BufferLength* angegebene Wert war kleiner als 0.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
 **SQLDescribeCol** kann jede SQLSTATE zurückgeben, die von **SQLPrepare** oder **SQLExecute** zurückgegeben werden kann, wenn sie nach **SQLPrepare** und vor **SQLExecute**aufgerufen wird, je nachdem, wann die Datenquelle die SQL-Anweisung auswertet, die dem Anweisungshandle zugeordnet ist.  
  
 Aus Leistungsgründen sollte eine Anwendung **SQLDescribeCol** nicht aufrufen, bevor eine Anweisung ausgeführt wird.  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung ruft **SQLDescribeCol** in der Regel nach einem Aufruf von **SQLPrepare** und vor oder nach dem zugeordneten Aufruf von **SQLExecute**auf. Eine Anwendung kann **SQLDescribeCol** auch nach einem Aufruf von **SQLExecDirect**aufrufen. Weitere Informationen finden Sie unter [Ergebnissatzmetadaten](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLDescribeCol** ruft den Spaltennamen, -typ und -länge ab, die von einer **SELECT-Anweisung** generiert werden. Wenn es sich bei der Spalte um einen Ausdruck handelt, ist **ColumnName* entweder eine leere Zeichenfolge oder ein treiberdefinierter Name.  
  
> [!NOTE]  
>  ODBC unterstützt SQL_NULLABLE_UNKNOWN als Erweiterung, obwohl die Spezifikation Open Group and SQL Access Group Call Level Interface die Option für **SQLDescribeCol**nicht angibt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einer Ergebnismenge|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Abrufen mehrerer Datenzeilen|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Zurückgeben der Anzahl der Ergebnissatzspalten|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
