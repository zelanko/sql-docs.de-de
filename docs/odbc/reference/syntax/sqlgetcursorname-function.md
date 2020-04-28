---
title: Sqlgetcurrsorname-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetCursorName
helpviewer_keywords:
- SQLGetCursorName function [ODBC]
ms.assetid: e6e92199-7bb6-447c-8987-049a4c6ce05d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3ac65dc07897ddc789ee03b06b1bc1f71d37c3c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285548"
---
# <a name="sqlgetcursorname-function"></a>SQLGetCursorName-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetCursorName** gibt den mit einer angegebenen Anweisung verknüpften Cursor Namen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetCursorName(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CursorName,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   NameLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *Cursor Name*  
 Ausgeben Zeiger auf einen Puffer, in den der Cursor Name zurückgegeben werden soll.  
  
 Wenn *Cursor Name* NULL ist, gibt *namelengthptr* weiterhin die Gesamtzahl der Zeichen zurück (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den von *Cursor Name*verwiesen wird.  
  
 *Pufferlänge*  
 Der Länge von \* *Cursor Name*in Zeichen. Wenn der Wert in * \*Cursor Name* eine Unicode-Zeichenfolge ist (beim Aufrufen von **sqlgetcurrsornamew**), muss das *BufferLength* -Argument eine gerade Zahl sein.  
  
 *Namelengthptr*  
 Ausgeben Ein Zeiger auf den Arbeitsspeicher, in den die Gesamtzahl der Zeichen (ausgenommen des NULL-Beendigungs Zeichens) zurück \*gegeben werden soll, die in *Cursor Name*zurückgegeben werden können. Wenn die Anzahl der zurück zugebende Zeichen größer als oder gleich *BufferLength*ist, wird der Cursor Name in \* *Cursorname* auf *BufferLength* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlgetcurrsorname** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die häufig von **sqlgetcursor Name** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Der buffer \* *Cursorname* war nicht groß genug, um den gesamten Cursor Namen zurückzugeben, sodass der Cursor Name abgeschnitten wurde. Die Länge des nicht abgeschnittene Cursor namens wird in **namelengthptr*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **sqlgetcurrsorname** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das *StatementHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY015|Kein Cursor Name verfügbar.|(DM) der Treiber war ein ODBC 2 *. x* -Treiber, es gab keinen geöffneten Cursor in der Anweisung, und es wurde kein Cursor Name mit **SQLSetCursorName**festgelegt.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der im Argument *BufferLength* angegebene Wert war kleiner als 0 (null).|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Cursor Namen werden nur in positionierten Update-und DELETE-Anweisungen verwendet (z. b. **Update** _Table-Name_ ... **WHERE CURRENT of** _Cursor-Name_). Weitere Informationen finden Sie unter [positionierte UPDATE-und DELETE-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Wenn die Anwendung **SQLSetCursorName** nicht zum Definieren eines Cursor namens aufruft, generiert der Treiber einen Namen. Dieser Name beginnt mit den Buchstaben SQL_CUR.  
  
> [!NOTE]
>  In ODBC 2 *. x*hat ein **SQLGetCursorName** -Befehl SQLSTATE HY015 (kein Cursor Name verfügbar) zurückgegeben, wenn es keinen geöffneten Cursor gab und kein Name durch einen Befehl von **SQLSetCursorName**festgelegt wurde. In ODBC 3 *. x*ist dies nicht mehr der Fall. unabhängig davon, wann **SQLGetCursorName** aufgerufen wird, gibt der Treiber den Cursor Namen zurück.  
  
 **SQLGetCursorName** gibt den Namen eines Cursors zurück, unabhängig davon, ob der Name explizit oder implizit erstellt wurde. Ein Cursor Name wird implizit generiert, wenn **SQLSetCursorName** nicht aufgerufen wird. **SQLSetCursorName** kann aufgerufen werden, um einen Cursor in einer-Anweisung umzubenennen, solange sich der Cursor in einem zugeordneten oder vorbereiteten Zustand befindet.  
  
 Ein Cursor Name, der entweder explizit oder implizit festgelegt wird, bleibt so lange festgelegt, bis das *StatementHandle* , mit dem es verknüpft ist, gelöscht wird. dabei wird **SQLFreeHandle** mit dem *Handtyp* SQL_HANDLE_STMT verwendet.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Festlegen eines Cursor namens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
