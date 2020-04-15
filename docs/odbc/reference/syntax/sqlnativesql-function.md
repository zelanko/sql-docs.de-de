---
title: SQLNativeSql-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLNativeSql
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLNativeSql
helpviewer_keywords:
- SQLNativeSql function [ODBC]
ms.assetid: b8efc247-27ab-4a00-92b6-1400785783fe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9666bc767affb3b6bb624c416614079193d4b921
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304721"
---
# <a name="sqlnativesql-function"></a>SQLNativeSql-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLNativeSql** gibt die SQL-Zeichenfolge als vom Treiber geändert zurück. **SQLNativeSql** führt die SQL-Anweisung nicht aus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLNativeSql(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      InStatementText,  
     SQLINTEGER     TextLength1,  
     SQLCHAR *      OutStatementText,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   TextLength2Ptr);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *InStatementText*  
 [Eingabe] SQL-Textzeichenfolge, die übersetzt werden soll.  
  
 *TextLength1*  
 [Eingabe] Länge in Zeichen der **InStatementText-Textzeichenfolge.*  
  
 *OutStatementText*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die übersetzte SQL-Zeichenfolge zurückgegeben wird.  
  
 Wenn *OutStatementText* NULL ist, gibt *TextLength2Ptr* weiterhin die Gesamtzahl der Zeichen zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer von *OutStatementText*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Anzahl der Zeichen \*im *OutStatementText-Puffer.* Wenn der in * \*InStatementText* zurückgegebene Wert eine Unicode-Zeichenfolge ist (beim Aufrufen von **SQLNativeSqlW**), muss das *BufferLength-Argument* eine gerade Zahl sein.  
  
 *TextLength2Ptr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (ohne \*Null-Beendigung) zurückgegeben werden soll, die in *OutStatementText*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer oder gleich *BufferLength* \*ist, wird die übersetzte SQL-Zeichenfolge in *OutStatementText* auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLNativeSql** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DBC und einem *Handle* von *ConnectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLNativeSql** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der \*Puffer *OutStatementText* war nicht groß genug, um die gesamte SQL-Zeichenfolge zurückzugeben, sodass die SQL-Zeichenfolge abgeschnitten wurde. Die Länge der nicht abgeschnittenen SQL-Zeichenfolge wird in **TextLength2Ptr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|Der *ConnectionHandle* war nicht in einem verbundenen Zustand.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|22007|Ungültiges Datumszeitformat|**InStatementText* enthielt eine Escapeklausel mit einem ungültigen Datums-, Uhrzeit- oder Zeitstempelwert.|  
|24.000|Ungültiger Cursorstatus|Der Cursor, auf den in der Anweisung verwiesen wird, wurde vor dem Beginn des Resultsets oder nach dem Ende des Resultsets positioniert. Dieser Fehler wird möglicherweise nicht von einem Treiber mit einer systemeigenen DBMS-Cursorimplementierung zurückgegeben.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) **InStatementText* war ein Nullzeiger.|  
|HY010|Funktionssequenzfehler|(DM) Eine asynchron ausführende Funktion wurde für den *ConnectionHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Das Argument *TextLength1* war kleiner als 0, aber nicht gleich SQL_NTS.|  
|||(DM) Das Argument *BufferLength* war kleiner als 0 und das Argument *OutStatementText* war kein Nullzeiger.|  
|HY109|Ungültige Cursorposition|Die aktuelle Zeile des Cursors wurde gelöscht oder nicht abgerufen. Dieser Fehler wird möglicherweise nicht von einem Treiber mit einer systemeigenen DBMS-Cursorimplementierung zurückgegeben.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *ConnectionHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Im Folgenden finden Sie Beispiele dafür, was **SQLNativeSql** für die folgende SQL-Eingabezeichenfolge zurückgeben kann, die die Skalarfunktion CONVERT enthält. Angenommen, die Spalte empid ist vom Typ INTEGER in der Datenquelle:  
  
```sql  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Ein Treiber für Microsoft SQL Server gibt möglicherweise die folgende übersetzte SQL-Zeichenfolge zurück:  
  
```sql  
SELECT convert (smallint, empid) FROM employee  
```  
  
 Ein Treiber für ORACLE Server gibt möglicherweise die folgende übersetzte SQL-Zeichenfolge zurück:  
  
```sql  
SELECT to_number (empid) FROM employee  
```  
  
 Ein Treiber für Ingres gibt möglicherweise die folgende übersetzte SQL-Zeichenfolge zurück:  
  
```sql  
SELECT int2 (empid) FROM employee  
```  
  
 Weitere Informationen finden Sie unter [Direkte Ausführung](../../../odbc/reference/develop-app/direct-execution-odbc.md) und [vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
 Keine  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
