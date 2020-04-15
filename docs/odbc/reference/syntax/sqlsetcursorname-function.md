---
title: SQLSetCursorName-Funktion | Microsoft Docs
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
ms.openlocfilehash: 6a3bcd07a39401d49be04d141e50c671179efb16
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287340"
---
# <a name="sqlsetcursorname-function"></a>SQLSetCursorName-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetCursorName** ordnet einen Cursornamen einer aktiven Anweisung zu. Wenn eine Anwendung **SQLSetCursorName**nicht aufruft, generiert der Treiber Cursornamen, wie sie für die SQL-Anweisungsverarbeitung erforderlich sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetCursorName(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CursorName,  
     SQLSMALLINT   NameLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *CursorName*  
 [Eingabe] Cursorname. Für eine effiziente Verarbeitung sollte der Cursorname keine führenden oder nachgestellten Leerzeichen im Cursornamen enthalten, und wenn der Cursorname einen durch Trennzeichen getrennten Bezeichner enthält, sollte das Trennzeichen als erstes Zeichen im Cursornamen positioniert werden.  
  
 *NameLength*  
 [Eingabe] Länge in Zeichen von **CursorName*.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetCursorName** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLSetCursorName** zurückgegeben werden, und es werden die SQLSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der Cursorname hat die maximale Grenze überschritten, sodass nur die maximal zulässige Anzahl von Zeichen verwendet wurde.|  
|24.000|Ungültiger Cursorstatus|Die Anweisung, die *StatementHandle* entspricht, befand sich bereits in einem ausgeführten oder Cursor-positionierten Zustand.|  
|34000|Ungültiger Cursorname|Der in **CursorName* angegebene Cursorname war ungültig, da er die vom Treiber definierte maximale Länge überschritten oder mit "SQLCUR" oder "SQL_CUR" gestartet wurde.|  
|3C000|Duplikat-Cursorname|Der in **CursorName* angegebene Cursorname ist bereits vorhanden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) Das Argument *CursorName* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLSetCursorName-Funktion** aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausgeführte Funktion wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Das Argument *NameLength* war kleiner als 0, aber nicht gleich SQL_NTS.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Cursornamen werden nur in positionierten Aktualisierungs- und Löschanweisungen verwendet (z. B. **UPDATE** _UPDATE-Tabellenname_ ... **WO STROM VON** _Cursor-Name_). Weitere Informationen finden Sie unter [Positionierte Aktualisierungs- und Löschanweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Wenn die Anwendung **SQLSetCursorName** nicht aufruft, um einen Cursornamen zu definieren, generiert der Treiber bei der Ausführung einer Abfrageanweisung einen Namen, der mit den Buchstaben SQL_CUR beginnt und 18 Zeichen nicht überschreitet.  
  
 Alle Cursornamen innerhalb der Verbindung müssen eindeutig sein. Die maximale Länge eines Cursornamens wird vom Treiber definiert. Für maximale Interoperabilität wird empfohlen, dass Anwendungen Cursornamen auf maximal 18 Zeichen beschränken. In ODBC 3 *.x*, wenn ein Cursorname ein in Anführungszeichen gesetzter Bezeichner ist, wird er in einer Groß-/Kleinschreibung behandelt, und er kann Zeichen enthalten, die die Syntax von SQL nicht zulassen oder besonders behandeln würde, z. B. Leerzeichen oder reservierte Schlüsselwörter. Wenn ein Cursorname in einer unter Groß-/Kleinschreibung berücksichtigten Weise behandelt werden muss, muss er als Bezeichner in angesetzt übergeben werden.  
  
 Ein Cursorname, der entweder explizit oder implizit festgelegt wird, bleibt so lange festgelegt, bis die Anweisung, der er zugeordnet ist, mithilfe von **SQLFreeHandle**gelöscht wird. **SQLSetCursorName** kann aufgerufen werden, um einen Cursor für eine Anweisung umzubenennen, solange sich der Cursor in einem zugewiesenen oder vorbereiteten Zustand befindet.  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel verwendet eine Anwendung **SQLSetCursorName,** um einen Cursornamen für eine Anweisung festzulegen. Anschließend wird diese Anweisung verwendet, um Ergebnisse aus der CUSTOMERS-Tabelle abzurufen. Schließlich führt es eine positionierte Aktualisierung durch, um die Telefonnummer von John Smith zu ändern. Beachten Sie, dass die Anwendung unterschiedliche Anweisungshandles für die **SELECT-** und **UPDATE-Anweisungen** verwendet.  
  
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
|Zurückgeben eines Cursornamens|[SQLGetCursorName-Funktion](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Festlegen von Cursor-Scrolling-Optionen|[SQLSetScrollOptions-Funktion](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
