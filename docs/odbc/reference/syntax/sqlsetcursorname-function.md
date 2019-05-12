---
title: SQLSetCursorName-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a976d7caad790c80b15c17d65686ee1f6308f415
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536748"
---
# <a name="sqlsetcursorname-function"></a>SQLSetCursorName-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetCursorName** eine aktive Anweisung ein Cursorname zugeordnet. Wenn eine Anwendung nicht aufruft **SQLSetCursorName**, generiert der Treiber die Cursornamen nach Bedarf für die Verarbeitung von SQL-Anweisung.  
  
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
 [Eingabe] Name des Cursors. Für die effiziente Verarbeitung nicht sollte der Name des Cursors keine führenden oder nachgestellten Leerzeichen enthalten, in der Name des Cursors, und wenn der Name des Cursors einen Begrenzungsbezeichner enthält, das Trennzeichen positioniert werden muss als erstes Zeichen in der Name des Cursors.  
  
 *NameLength*  
 [Eingabe] Länge in Zeichen des **CursorName*.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetCursorName** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und eine *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLSetCursorName** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Name des Cursors überschreitet den maximalen Grenzwert, also nur die maximal zulässige Anzahl von Zeichen verwendet wurde.|  
|24000|Ungültiger Cursorstatus|Die Anweisung entspricht *StatementHandle* wurde bereits in einem Zustand ausgeführt oder Cursor positioniert.|  
|34000|Ungültiger Cursorname|Der Name des Cursors im angegebenen **CursorName* war ungültig, da er die maximale Länge, überschreitet wie vom Treiber definiert, oder muss mit "SQLCUR" oder "SQL_CUR."|  
|3C000|Doppelter Cursorname|Der Name des Cursors im angegebenen **CursorName* ist bereits vorhanden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY009|Ungültige Verwendung eines null-Zeiger|(DM) das Argument *CursorName* wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Diese Funktion Aynchronous war immer noch ausgeführt, wenn die **SQLSetCursorName** Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) das Argument *Namenslänge* war kleiner als 0, aber nicht SQL_NTS gleich.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Cursor werden verwendet, nur in positioniertes Update und delete-Anweisungen (z. B. **aktualisieren** _Tabellenname_ ... **WHERE CURRENT OF** _Cursorname_). Weitere Informationen finden Sie unter [positioniert Update- und Delete-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Wenn die Anwendung nicht aufruft **SQLSetCursorName** bei der Ausführung einer abfrageanweisung ein Cursorname definiert der Treiber generiert einen Namen, die mit den Buchstaben SQL_CUR beginnt und bis zu 18 Zeichen Länge nicht überschreitet.  
  
 Alle Cursornamen innerhalb der Verbindung müssen eindeutig sein. Maximal ein Cursorname wird vom Treiber definiert. Für eine optimale Interoperabilität empfiehlt es sich, dass Anwendungen Cursornamen nicht mehr als 18 Zeichen beschränkt. In ODBC 3.*.x*, wenn ein Cursorname ein Bezeichner in Anführungszeichen ist, es die Groß-und Kleinschreibung behandelt wird und darf die Zeichen, dass die Syntax von SQL würde nicht zulässig insbesondere, wie z. B. Leerzeichen behandelt oder Schlüsselwörter reservierte. Wenn ein Cursorname in Groß-und Kleinschreibung behandelt werden muss, muss es als ein Bezeichner in Anführungszeichen übergeben werden.  
  
 Ein Cursorname, die entweder explizit festgelegt oder implizit bleibt festgelegt, bis die Anweisung, mit denen sie zugeordnet ist, mit gelöscht wird, **SQLFreeHandle**. **SQLSetCursorName** aufgerufen werden, um ein Cursor für eine Anweisung umbenennen, solange der Cursor in einem Zustand zugeordnet oder vorbereitet ist.  
  
## <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel verwendet eine Anwendung **SQLSetCursorName** um einen Cursornamen für eine Anweisung festzulegen. Klicken Sie dann verwendet die Anweisung zum Abrufen der Ergebnisse aus der Tabelle CUSTOMERS. Abschließend führt er ein positioniertes Update zum Ändern der Telefonnummer des John Smith. Beachten Sie, dass die Anwendung für unterschiedliche Anweisungshandles verwendet die **wählen** und **UPDATE** Anweisungen.  
  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Ein Cursorname zurückgeben|[SQLGetCursorName-Funktion](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Festlegen von Optionen für die cursorbildlauf|[SQLSetScrollOptions-Funktion](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
