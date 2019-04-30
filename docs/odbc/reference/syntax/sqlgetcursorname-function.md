---
title: SQLGetCursorName-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: faa88d18a5b682b98a56b6426ba6a94ee4687cab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63258824"
---
# <a name="sqlgetcursorname-function"></a>SQLGetCursorName-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetCursorName** gibt zurück, der Name des Cursors eine angegebene Anweisung zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 [Ausgabe] Zeiger auf einen Puffer, in dem der Name des Cursors zurückgegeben.  
  
 Wenn *CursorName* NULL ist, *NameLengthPtr* gibt die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *CursorName*.  
  
 *BufferLength*  
 [Eingabe] Länge der \* *CursorName*, in Zeichen. Wenn der Wert in  *\*CursorName* ist eine Unicodezeichenfolge (beim Aufrufen von **SQLGetCursorNameW**), wird die *Pufferlänge* Argument muss eine gerade Zahl sein.  
  
 *NameLengthPtr*  
 [Ausgabe] Zeiger auf den Speicher für die Rückgabe der Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen) zur Verfügung, die in zurückgegeben \* *CursorName*. Wenn die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als oder gleich ist *Pufferlänge*, der Name des Cursors in \* *CursorName* auf abgeschnitten *Pufferlänge*abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetCursorName** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit eine *HandleType*von SQL_HANDLE_STMT auf, und ein *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLGetCursorName** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Puffer \* *CursorName* war nicht groß genug, um den gesamten Cursornamen, zurückgeben, damit der Name des Cursors abgeschnitten wurde. Die Länge des Cursornamens den ungekürzten wird zurückgegeben, **NameLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLGetCursorName** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY015|Es ist kein Cursorname verfügbar|(DM) der Treiber wurde von einer ODBC 2.*.x* Treiber, gab es keinen geöffneten Cursor in der Anweisung, und es ist kein Cursorname hatte festgelegt wurde, mit **SQLSetCursorName**.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Wert im Argument angegebene *Pufferlänge* war kleiner als 0.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Cursor werden verwendet, nur in positioniertes Update und delete-Anweisungen (z. B. **aktualisieren** _Tabellenname_ ... **WHERE CURRENT OF** _Cursorname_). Weitere Informationen finden Sie unter [positioniert Update- und Delete-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Wenn die Anwendung nicht aufruft **SQLSetCursorName** um einen Cursornamen zu definieren, generiert der Treiber einen Namen. Dieser Name beginnt mit den Buchstaben SQL_CUR.  
  
> [!NOTE]
>  In ODBC 2.*.x*beim gab es keinen geöffneten Cursor und kein Name wurde, durch einen Aufruf von festgelegt hatte **SQLSetCursorName**, einen Aufruf von **SQLGetCursorName** SQLSTATE HY015 zurückgegeben (es ist kein Cursorname verfügbar). In ODBC 3.*.x*, dies ist nicht mehr "true", unabhängig davon, wann **SQLGetCursorName** wird aufgerufen, gibt der Treiber den Cursornamen.  
  
 **SQLGetCursorName** gibt den Namen eines Cursors, und zwar unabhängig davon, ob der Name explizit oder implizit erstellt wurde. Ein Name des Cursors wird implizit generiert, wenn **SQLSetCursorName** wird nicht aufgerufen. **SQLSetCursorName** aufgerufen werden, um ein Cursor für eine Anweisung umbenennen, solange der Cursor in einem Zustand zugeordnet oder vorbereitet ist.  
  
 Ein Cursorname, die entweder explizit oder implizit festgelegt ist bleibt festgelegt, bis die *StatementHandle* mit dem es zugeordnet ist wird gelöscht, mit **SQLFreeHandle** mit einer *HandleType* von SQL_HANDLE_STMT auf.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Vorbereiten einer Anweisung für die Ausführung|[SQLPrepare-Funktion](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Ein Cursorname festlegen|[SQLSetCursorName-Funktion](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
