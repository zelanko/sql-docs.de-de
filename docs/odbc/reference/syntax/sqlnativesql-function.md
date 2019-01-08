---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab39d1fca288196dcf42da70083dad323c406ba0
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53208636"
---
# <a name="sqlnativesql-function"></a>SQLNativeSql-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLNativeSql** gibt die SQL-Zeichenfolge zurück, als vom Treiber geändert. **SQLNativeSql** die SQL-Anweisung wird nicht ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 [Eingabe] SQL-Text-Zeichenfolge übersetzt werden.  
  
 *TextLength1*  
 [Eingabe] Länge in Zeichen des **InStatementText* Textzeichenfolge.  
  
 *OutStatementText*  
 [Ausgabe] Zeiger auf einen Puffer, in die die übersetzte SQL-Zeichenfolge zurückgegeben werden sollen.  
  
 Wenn *OutStatementText* NULL ist, *TextLength2Ptr* gibt die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer zurückgegeben verweist *OutStatementText*.  
  
 *BufferLength*  
 [Eingabe] Anzahl der Zeichen in der \* *OutStatementText* Puffer. Wenn der Rückgabewert in  *\*InStatementText* ist eine Unicodezeichenfolge (beim Aufrufen von **SQLNativeSqlW**), wird die *Pufferlänge* Argument muss eine gerade Zahl sein.  
  
 *TextLength2Ptr*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe der Gesamtzahl der Zeichen (Null-Terminierung) zur Verfügung, die in zurückgegeben \* *OutStatementText*. Wenn die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als oder gleich ist *Pufferlänge*, übersetzt der SQL-Zeichenfolge in \* *OutStatementText* auf abgeschnitten  *BufferLength* abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLNativeSql** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit eine *HandleType* SQL_HANDLE_DBC auf, und ein *behandeln* von *ConnectionHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLNativeSql** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Puffer \* *OutStatementText* war nicht groß genug, um die gesamte SQL-Zeichenfolge zurück, damit die SQL-Zeichenfolge abgeschnitten wurde. Die Länge der ungekürzte SQL-Zeichenfolge wird zurückgegeben, **TextLength2Ptr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|Die *ConnectionHandle* war nicht verbunden.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|22007|Ungültiges Datetime-format|**InStatementText* eine Escape-Klausel mit einem ungültigen Wert für Datum, Uhrzeit oder Zeitstempel enthalten.|  
|24000|Ungültiger Cursorstatus|Der Cursor, die in der Anweisung bezeichnet wurde vor dem Start des Resultsets oder nach dem Ende des Resultsets positioniert. Dieser Fehler kann durch einen Treiber, müssen eine systemeigene Implementierung des DBMS-Cursor nicht zurückgegeben werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY009|Ungültige Verwendung eines null-Zeiger|(DM) **InStatementText* wurde ein null-Zeiger.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, die *ConnectionHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) das Argument *TextLength1* war kleiner als 0 ist, aber ungleich SQL_NTS.|  
|||(DM) das Argument *Pufferlänge* war kleiner als 0 und das Argument *OutStatementText* war es sich nicht um ein null-Zeiger.|  
|HY109|Ungültige Cursorposition|Die aktuelle Zeile des Cursors hatte, wurde gelöscht oder hatte nicht abgerufen wurde. Dieser Fehler kann durch einen Treiber, müssen eine systemeigene Implementierung des DBMS-Cursor nicht zurückgegeben werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *ConnectionHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Im folgenden sind Beispiele für **SQLNativeSql** möglicherweise für die folgende Eingabe SQL-Zeichenfolge, die mit der skalaren CONVERT-Funktion zurück. Nehmen Sie an, dass die Spalte Empid vom Typ ganze Zahl in der Datenquelle:  
  
```  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Ein Treiber für Microsoft SQL Server möglicherweise die folgende übersetzte SQL-Zeichenfolge zurück:  
  
```  
SELECT convert (smallint, empid) FROM employee  
```  
  
 Ein Treiber für ORACLE-Server möglicherweise die folgende übersetzte SQL-Zeichenfolge zurück:  
  
```  
SELECT to_number (empid) FROM employee  
```  
  
 Ein Treiber für Ingres gibt möglicherweise die folgende übersetzte SQL-Zeichenfolge zurück:  
  
```  
SELECT int2 (empid) FROM employee  
```  
  
 Weitere Informationen finden Sie unter [direkte Ausführung](../../../odbc/reference/develop-app/direct-execution-odbc.md) und [vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
 Keine.  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
