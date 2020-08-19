---
description: SQLNativeSql-Funktion
title: SQLNativeSql-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: cbdf43d1120065f981d43e58490e328c6ef7691c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428902"
---
# <a name="sqlnativesql-function"></a>SQLNativeSql-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLNativeSql** gibt die SQL-Zeichenfolge zurück, die vom Treiber geändert wurde. **SQLNativeSql** führt die SQL-Anweisung nicht aus.  
  
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
  
 *Instatus-Text*  
 Der SQL-Text Zeichenfolge, die übersetzt werden soll.  
  
 *TextLength1*  
 Der Länge in Zeichen der **instatuementtext* -Text Zeichenfolge.  
  
 *Outstatus-Text*  
 Ausgeben Zeiger auf einen Puffer, in den die übersetzte SQL-Zeichenfolge zurückgegeben werden soll.  
  
 Wenn *outstatuementtext* NULL ist, gibt *TextLength2Ptr* weiterhin die Gesamtzahl der Zeichen zurück (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den von *Outstatus ementtext*verwiesen wird.  
  
 *BufferLength*  
 Der Anzahl der Zeichen im \* *Outstatus-Text* Puffer. Wenn der in * \* instatuementtext* zurückgegebene Wert eine Unicode-Zeichenfolge ist (beim Aufrufen von **sqlnativesqlw**), muss das *BufferLength* -Argument eine gerade Zahl sein.  
  
 *TextLength2Ptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (mit Ausnahme der NULL-Beendigung) zurückgegeben werden soll, die in \* *Outstatus-Text*zurückgegeben werden können. Wenn die Anzahl der zurück zugebende Zeichen größer als oder gleich *BufferLength*ist, wird die übersetzte SQL-Zeichenfolge in \* *Outstatus-Text* auf *BufferLength* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLNativeSql** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_DBC und einem *handle* von *connectionHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die häufig von **SQLNativeSql** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Der Puffer \* *Outstatus Text* war nicht groß genug, um die gesamte SQL-Zeichenfolge zurückzugeben, daher wurde die SQL-Zeichenfolge abgeschnitten. Die Länge der nicht abgeschnittene SQL-Zeichenfolge wird in **TextLength2Ptr*zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|Das *connectionHandle* befand sich nicht in einem verbundenen Zustand.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|22007|Ungültiges datetime-Format.|**Instatuementtext* enthielt eine Escape-Klausel mit einem ungültigen Date-, Time-oder Zeitstempel-Wert.|  
|24.000|Ungültiger Cursorstatus|Der Cursor, auf den in der Anweisung verwiesen wird, wurde vor dem Anfang des Resultsets oder nach dem Ende des Resultsets positioniert. Dieser Fehler wird möglicherweise nicht von einem Treiber zurückgegeben, der über eine native DBMS-Cursor Implementierung verfügt.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) **instatus-Text* war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für *connectionHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) das Argument *TextLength1* war kleiner als 0 (null), aber nicht gleich SQL_NTS.|  
|||(DM) das Argument *BufferLength* war kleiner als 0, und das Argument *outstatuementtext* war kein NULL-Zeiger.|  
|HY109|Ungültige Cursorposition|Die aktuelle Zeile des Cursors wurde gelöscht oder nicht abgerufen. Dieser Fehler wird möglicherweise nicht von einem Treiber zurückgegeben, der über eine native DBMS-Cursor Implementierung verfügt.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *connectionHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Im folgenden finden Sie Beispiele für das **SQLNativeSql** -Element für die folgende Eingabe-SQL-Zeichenfolge, die die Skalarfunktion Convert enthält Angenommen, die Spalte "EmpID" hat den Typ "Integer" in der Datenquelle:  
  
```sql  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Ein Treiber für Microsoft SQL Server gibt möglicherweise die folgende übersetzte SQL-Zeichenfolge zurück:  
  
```sql  
SELECT convert (smallint, empid) FROM employee  
```  
  
 Ein Treiber für Oracle Server gibt möglicherweise die folgende übersetzte SQL-Zeichenfolge zurück:  
  
```sql  
SELECT to_number (empid) FROM employee  
```  
  
 Ein Treiber für Ingres gibt möglicherweise die folgende übersetzte SQL-Zeichenfolge zurück:  
  
```sql  
SELECT int2 (empid) FROM employee  
```  
  
 Weitere Informationen finden Sie unter [direkte Ausführung](../../../odbc/reference/develop-app/direct-execution-odbc.md) und [vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
 Keine.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
