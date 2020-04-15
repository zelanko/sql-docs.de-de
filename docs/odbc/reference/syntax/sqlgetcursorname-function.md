---
title: SQLGetCursorName-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285548"
---
# <a name="sqlgetcursorname-function"></a>SQLGetCursorName-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetCursorName** gibt den Cursornamen zurück, der einer angegebenen Anweisung zugeordnet ist.  
  
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
 [Eingabe] Anweisungshandle.  
  
 *CursorName*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem der Cursorname zurückgegeben wird.  
  
 Wenn *CursorName* NULL ist, gibt *NameLengthPtr* weiterhin die Gesamtzahl der Zeichen zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer verwiesen wird, auf den *CursorName*zeigt.  
  
 *BufferLength*  
 [Eingabe] Länge \*von *CursorName*, in Zeichen. Wenn der Wert in * \*CursorName* eine Unicode-Zeichenfolge ist (beim Aufrufen von **SQLGetCursorNameW**), muss das *BufferLength-Argument* eine gerade Zahl sein.  
  
 *NameLengthPtr*  
 [Ausgabe] Zeiger auf den Speicher, in dem die Gesamtzahl der Zeichen (mit Ausnahme \*des Null-Beendigungszeichens) zurückgegeben werden soll, die in *CursorName*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer oder gleich *BufferLength*ist, wird der Cursorname in \* *CursorName* auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetCursorName** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLGetCursorName** zurückgegeben werden, und es werden die SQLSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der \*Puffer *CursorName* war nicht groß genug, um den gesamten Cursornamen zurückzugeben, sodass der Cursorname abgeschnitten wurde. Die Länge des nicht abgeschnittenen Cursornamens wird in **NameLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLGetCursorName-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY015|Kein Cursorname verfügbar|(DM) Der Treiber war ein ODBC 2 *.x-Treiber,* es gab keinen geöffneten Cursor für die Anweisung, und es wurde kein Cursorname mit **SQLSetCursorName**festgelegt.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der im Argument *BufferLength* angegebene Wert war kleiner als 0.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Cursornamen werden nur in positionierten Aktualisierungs- und Löschanweisungen verwendet (z. B. **UPDATE** _UPDATE-Tabellenname_ ... **WO STROM VON** _Cursor-Name_). Weitere Informationen finden Sie unter [Positionierte Aktualisierungs- und Löschanweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Wenn die Anwendung **SQLSetCursorName** nicht aufruft, um einen Cursornamen zu definieren, generiert der Treiber einen Namen. Dieser Name beginnt mit den Buchstaben SQL_CUR.  
  
> [!NOTE]
>  In ODBC 2 *.x*, wenn kein geöffneter Cursor vorhanden war und kein Name durch einen Aufruf von **SQLSetCursorName**festgelegt wurde, gab ein Aufruf von **SQLGetCursorName** SQLSTATE HY015 zurück (kein Cursorname verfügbar). In ODBC 3 *.x*ist dies nicht mehr wahr; unabhängig davon, wann **SQLGetCursorName** aufgerufen wird, gibt der Treiber den Cursornamen zurück.  
  
 **SQLGetCursorName** gibt den Namen eines Cursors zurück, unabhängig davon, ob der Name explizit oder implizit erstellt wurde. Ein Cursorname wird implizit generiert, wenn **SQLSetCursorName** nicht aufgerufen wird. **SQLSetCursorName** kann aufgerufen werden, um einen Cursor für eine Anweisung umzubenennen, solange sich der Cursor in einem zugewiesenen oder vorbereiteten Zustand befindet.  
  
 Ein Cursorname, der entweder explizit oder implizit festgelegt wird, bleibt so lange festgelegt, bis das *StatementHandle,* dem er zugeordnet ist, mithilfe von **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_STMT gelöscht wird.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Festlegen eines Cursornamens|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
