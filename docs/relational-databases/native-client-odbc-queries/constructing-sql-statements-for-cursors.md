---
title: Erstellen von SQL-Anweisungen für Cursor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 706559859c48fd61b7223793fc9421fdefc4798b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73779968"
---
# <a name="constructing-sql-statements-for-cursors"></a>Erstellen von SQL-Anweisungen für Cursor
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber verwendet Server Cursor, um die in der ODBC-Spezifikation definierte Cursor Funktion zu implementieren. Eine ODBC-Anwendung steuert das Cursor Verhalten, indem [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) verwendet wird, um unterschiedliche Anweisungs Attribute festzulegen. Nachfolgend sind die Attribute und ihre Standardwerte aufgeführt.  
  
|attribute|Standard|  
|---------------|-------------|  
|SQL_ATTR_CONCURRENCY|SQL_CONCUR_READ_ONLY|  
|SQL_ATTR_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE|SQL_NONSCROLLABLE|  
|SQL_ATTR_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_ATTR_ROW_ARRAY_SIZE|1|  
  
 Wenn diese Optionen zum Zeitpunkt der Ausführung einer SQL-Anweisung auf ihre Standardwerte festgelegt sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , verwendet der Native Client-ODBC-Treiber keinen Server Cursor zur Implementierung des Resultsets. Stattdessen wird ein Standardresultset verwendet. Wenn eine dieser Optionen zum Zeitpunkt der Ausführung einer SQL-Anweisung aus ihren Standardeinstellungen geändert wird, versucht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Native Client ODBC-Treiber, das Resultset mithilfe eines Server Cursors zu implementieren.  
  
 Standardresultsets unterstützen alle [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen. Es gibt keine Einschränkungen hinsichtlich der Arten von SQL-Anweisungen, die bei Verwendung eines Standardresultsets ausgeführt werden können.  
  
 Nicht alle [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen werden von Servercursorn unterstützt. Servercursor unterstützen keine SQL-Anweisungen, die mehrere Resultsets generieren.  
  
 Die folgenden Typen von Anweisungen werden von Serversursorn nicht unterstützt:  
  
-   Batches  
  
     Aus zwei oder mehr einzelnen SQL SELECT-Anweisungen erstellte SQL-Anweisungen, Beispiel.:  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   Gespeicherte Prozeduren mit mehreren SELECT-Anweisungen  
  
     SQL-Anweisungen, die eine gespeicherte Prozedur ausführen, die mehr als eine SELECT-Anweisung enthält Hierzu gehören auch SELECT-Anweisungen, mit denen Parameter- oder Variablenwerte abgerufen werden.  
  
-   Keywords  
  
     SQL-Anweisungen, die die Schlüsselwörter FOR BROWSE oder INTO enthalten.  
  
 Wenn in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine SQL-Anweisung ausgeführt wird, die eine dieser Bedingungen erfüllt, dann wird der Servercursor implizit in ein Standardresultset konvertiert. Nachdem **SQLExecDirect** oder **SQLExecute** SQL_SUCCESS_WITH_INFO zurückgegeben hat, werden die Cursor Attribute auf ihre Standardeinstellungen zurückgesetzt.  
  
 SQL-Anweisungen, die nicht in die oben genannten Kategorien passen, können mit beliebigen Anweisungsattributeinstelllungen ausgeführt werden. Sie funktionieren sowohl mit einem Standardresultset als auch einem Servercursor gleich gut.  
  
## <a name="errors"></a>Errors  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 und höher führt der Versuch, eine Anweisung auszuführen, die mehrere Resultsets erzeugt, zur Ausgabe von SQL_SUCCESS_WITH INFO und der folgenden Meldung:  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 ODBC-Anwendungen, die diese Nachricht empfangen, können [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) aufrufen, um die aktuellen Cursor Einstellungen zu bestimmen.  
  
 Der Versuch, bei Verwendung von Servercursorn eine Prozedur mit mehreren SELECT-Anweisungen auszuführen, erzeugt folgenden Fehler:  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 Der Versuch, bei Verwendung von Servercursorn einen Batch mit mehreren SELECT-Anweisungen auszuführen, erzeugt folgenden Fehler:  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 ODBC-Anwendungen, die diese Fehler erhalten, müssen alle Cursoranweisungsattribute auf die jeweilige Standardeinstellung zurücksetzen, bevor sie die Anweisung auszuführen versuchen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Abfragen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
