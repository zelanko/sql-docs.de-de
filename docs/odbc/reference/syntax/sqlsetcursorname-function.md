---
description: SQLSetCursorName-Funktion
title: Sqlsetcurrsorname-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetCursorName
helpviewer_keywords:
- SQLSetCursorName function [ODBC]
ms.assetid: 4e055946-12d4-4589-9891-41617a50f34e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1a7deee4ecb37225260f011d4944e992f16d94e1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499489"
---
# <a name="sqlsetcursorname-function"></a>SQLSetCursorName-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetCursorName** ordnet einen Cursor Namen einer aktiven Anweisung zu. Wenn eine Anwendung **SQLSetCursorName**nicht aufruft, generiert der Treiber nach Bedarf für die Verarbeitung von SQL-Anweisungen Cursor Namen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetCursorName(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CursorName,  
     SQLSMALLINT   NameLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *Cursor Name*  
 Der Der Cursor Name. Zur effizienten Verarbeitung sollte der Cursor Name keine führenden oder nachfolgenden Leerzeichen im Cursor Namen enthalten, und wenn der Cursor Name einen Begrenzungs Bezeichner enthält, sollte das Trennzeichen als erstes Zeichen im Cursor Namen positioniert werden.  
  
 *NameLength*  
 Der Länge in Zeichen von **Cursor Name*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlsetcurrsorname** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die häufig von **sqlsetcurrsorname** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Der Cursor Name hat den maximalen Grenzwert überschritten, sodass nur die maximal zulässige Anzahl von Zeichen verwendet wurde.|  
|24.000|Ungültiger Cursorstatus|Die der *StatementHandle* entsprechende Anweisung war bereits in einem ausgeführten oder Cursor positionierten Zustand.|  
|34000|Ungültiger Cursorname|Der in **Cursorname* angegebene Cursor Name war ungültig, weil er die vom Treiber definierte maximale Länge überschritten hat oder mit "sqlcur" oder "SQL_CUR" gestartet wurde.|  
|3c000|Doppelter Cursor Name|Der in **Cursorname* angegebene Cursor Name ist bereits vorhanden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) das Argument *Cursor Name* war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese aynchronous-Funktion wurde noch ausgeführt, als die **sqlsetcurrsorname** -Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das *StatementHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der *argumentnamelength* war kleiner als 0, aber nicht gleich SQL_NTS.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Cursor Namen werden nur in positionierten Update-und DELETE-Anweisungen verwendet (z. b. **Update** _Table-Name_ ... **WHERE CURRENT of** _Cursor-Name_). Weitere Informationen finden Sie unter [positionierte UPDATE-und DELETE-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Wenn die Anwendung **SQLSetCursorName** nicht zum Definieren eines Cursor namens aufruft, generiert der Treiber bei der Ausführung einer Abfrage Anweisung einen Namen, der mit den Buchstaben SQL_CUR beginnt und nicht länger als 18 Zeichen ist.  
  
 Alle Cursor Namen innerhalb der Verbindung müssen eindeutig sein. Die maximale Länge eines Cursor namens wird vom Treiber definiert. Für eine maximale Interoperabilität empfiehlt es sich, dass die Cursor Namen von Anwendungen auf höchstens 18 Zeichen beschränkt werden. Wenn in ODBC 3 *. x*ein Cursor Name ein Bezeichner in Anführungszeichen ist, wird er in der Groß-und Kleinschreibung behandelt und kann Zeichen enthalten, die von der SQL-Syntax nicht zugelassen oder besonders behandelt werden, z. b. Leerzeichen oder reservierte Schlüsselwörter. Wenn ein Cursor Name nach Groß-/Kleinschreibung behandelt werden muss, muss er als Bezeichner in Anführungszeichen angegeben werden.  
  
 Ein Cursor Name, der entweder explizit oder implizit festgelegt wird, bleibt so lange festgelegt, bis die Anweisung, mit der er verknüpft ist, mit **SQLFreeHandle**gelöscht wird. **SQLSetCursorName** kann aufgerufen werden, um einen Cursor in einer-Anweisung umzubenennen, solange sich der Cursor in einem zugeordneten oder vorbereiteten Zustand befindet.  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel verwendet eine Anwendung **SQLSetCursorName** , um einen Cursor Namen für eine Anweisung festzulegen. Anschließend wird diese Anweisung verwendet, um Ergebnisse aus der Customers-Tabelle abzurufen. Schließlich wird ein positioniertes Update durchführt, um die Telefonnummer von John Smith zu ändern. Beachten Sie, dass die Anwendung verschiedene Anweisungs Handles für die **Select** -und **Update** -Anweisungen verwendet.  
  
 Ein weiteres Codebeispiel finden Sie unter [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```cpp  
#define NAME_LEN 50  
#define PHONE_LEN 10  
  
SQLHSTMT     hstmtSelect,  
SQLHSTMT     hstmtUpdate;  
SQLRETURN    retcode;  
SQLHDBC      hdbc;  
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];  
SQLINTEGER   cbName, cbPhone;  
  
/* Allocate the statements and set the cursor name. */  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmtSelect);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmtUpdate);  
SQLSetCursorName(hstmtSelect, "C1", SQL_NTS);  
  
/* SELECT the result set and bind its columns to local buffers. */  
  
SQLExecDirect(hstmtSelect,  
      "SELECT NAME, PHONE FROM CUSTOMERS",  
      SQL_NTS);  
SQLBindCol(hstmtSelect, 1, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
SQLBindCol(hstmtSelect, 2, SQL_C_CHAR, szPhone, PHONE_LEN, &cbPhone);  
  
/* Read through the result set until the cursor is */  
/* positioned on the row for John Smith. */  
  
do  
 retcode = SQLFetch(hstmtSelect);  
while ((retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) &&  
   (strcmp(szName, "Smith, John") != 0));  
  
/* Perform a positioned update of John Smith's name. */  
  
if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
   SQLExecDirect(hstmtUpdate,  
   "UPDATE EMPLOYEE SET PHONE=\"2064890154\" WHERE CURRENT OF C1",  
   SQL_NTS);  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Zurückgeben eines Cursor namens|[SQLGetCursorName-Funktion](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Festlegen der Cursor Scrolloptionen|[SQLSetScrollOptions-Funktion](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
