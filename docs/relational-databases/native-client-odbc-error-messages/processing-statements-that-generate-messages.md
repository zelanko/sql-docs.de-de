---
description: Verarbeiten von Anweisungen, die Meldungen generieren
title: Verarbeiten von Anweisungen, die Meldungen generieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- PRINT statement
- messages [ODBC], statements generating messages
- statements [ODBC], message generation
- errors [ODBC], statements generating messages
- SQL Server Native Client ODBC driver, errors
- STATISTICS IO option
- STATISTICS TIME option
- DBCC statements
- SQLExecute function
- RAISERROR statement
- SQLGetDiagRec function
- ODBC error handling, statements generating messages
- SQLExecDirect function
ms.assetid: 672ebdc5-7fa1-4ceb-8d52-fd25ef646654
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ca60a4bbe9652d20cb4db0f9f4522d2fa1ff1afc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420514"
---
# <a name="processing-statements-that-generate-messages"></a>Verarbeiten von Anweisungen, die Meldungen generieren
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Die [!INCLUDE[tsql](../../includes/tsql-md.md)]-SET-Anweisungsoptionen STATISTICS TIME und STATISTICS IO werden verwendet, um Informationen zur Unterstützung bei der Diagnose von Abfragen mit langer Ausführungszeit zu gewinnen. Frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützen auch die SHOWPLAN-Option zur Analyse von Abfrageplänen. Eine ODBC-Anwendung kann diese Optionen festlegen, indem sie die folgenden Anweisungen ausführt:  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 Wenn SET STATISTICS Time oder SET SHOWPLAN on ist, werden **SQLExecute** und **SQLExecDirect** SQL_SUCCESS_WITH_INFO zurückgegeben. an diesem Punkt kann die Anwendung die Ausgabe des Showplan oder der Statistik Zeit abrufen, indem Sie **SQLGetDiagRec** aufruft, bis SQL_NO_DATA zurückgegeben wird. Jede Zeile der SHOWPLAN-Daten wird im folgenden Format ausgegeben:  
  
```  
szSqlState="01000", *pfNativeError=6223,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]   
              Table Scan"  
```  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 wurde die SHOWPLAN-Option durch SHOWPLAN_ALL und SHOWPLAN_TEXT ersetzt. Beide Optionen geben die Ausgabe als Resultset, nicht wie zuvor als Meldungssätze, zurück.  
  
 Jede Zeile der STATISTICS TIME-Daten wird im folgenden Format ausgegeben:  
  
```  
szSqlState="01000", *pfNativeError= 3613,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
   SQL Server Parse and Compile Time: cpu time = 0 ms."  
```  
  
 Die Ausgabe von SET STATISTICS IO ist bis zum Ende eines Resultsets nicht verfügbar. Zum Abrufen der Statistik-e/a-Ausgabe Ruft die Anwendung **SQLGetDiagRec** auf, wenn **SQLFetch** oder [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) SQL_NO_DATA zurückgibt. Die Ausgabe der STATISTICS IO-Option erfolgt in folgendem Format:  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a>Verwenden von DBCC-Anweisungen  
 DBCC-Anweisungen geben Daten als Meldungen, nicht als Resultsets, zurück. **SQLExecDirect** oder **SQLExecute** geben SQL_SUCCESS_WITH_INFO zurück, und die Anwendung ruft die Ausgabe ab, indem Sie **SQLGetDiagRec** aufrufen, bis Sie SQL_NO_DATA zurückgibt.  
  
 Beispielsweise gibt die folgende Anweisung SQL_SUCCESS_WITH_INFO zurück:  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 Aufrufe von **SQLGetDiagRec** geben Folgendes zurück:  
  
```  
szSqlState = "01000", *pfNativeError = 2536,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Checking authors"  
szSqlState = "01000", *pfNativeError = 2579,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   The total number of data pages in this table is 1."  
szSqlState = "01000", *pfNativeError = 7929,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table has 23 data rows."  
szSqlState = "01000", *pfNativeError = 2528  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   DBCC execution completed. If DBCC printed error messages,  
   see your System Administrator."  
```  
  
## <a name="using-print-and-raiserror-statements"></a>Verwenden der Anweisungen PRINT und RAISERROR  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] Print-und RAISERROR-Anweisungen geben auch Daten durch Aufrufen von **SQLGetDiagRec**zurück. Print-Anweisungen bewirken, dass die Ausführung der SQL-Anweisung SQL_SUCCESS_WITH_INFO zurückgibt, und ein nachfolgende-Befehl von **SQLGetDiagRec** gibt den *SQLSTATE* -Wert 01000 zurück. Ein RAISERROR mit einem Schweregrad bis einschließlich 10 zeigt dasselbe Verhalten wie PRINT. Ein RAISERROR mit einem Schweregrad von 11 oder höher bewirkt, dass die Execute-SQL_ERROR zurückgibt, und ein nachfolgende-Befehl von **SQLGetDiagRec** gibt *SQLSTATE* 42000 zurück. Beispielsweise gibt die folgende Anweisung SQL_SUCCESS_WITH_INFO zurück:  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 Der Aufruf von **SQLGetDiagRec** gibt Folgendes zurück:  
  
```  
szSQLState = "01000", *pfNative Error = 0,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Some message"  
```  
  
 Die folgende Anweisung gibt SQL_SUCCESS_WITH_INFO zurück:  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 1.', 10, -1)",  
   SQL_NTS)  
```  
  
 Der Aufruf von **SQLGetDiagRec** gibt Folgendes zurück:  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 Die folgende Anweisung gibt SQL_ERROR zurück:  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 Der Aufruf von **SQLGetDiagRec** gibt Folgendes zurück:  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 Die zeitliche Steuerung von **SQLGetDiagRec** ist wichtig, wenn die Ausgabe von Print-oder RAISERROR-Anweisungen in einem Resultset enthalten ist. Der Aufrufen von **SQLGetDiagRec** zum Abrufen der Print-oder RAISERROR-Ausgabe muss direkt nach der Anweisung erfolgen, die SQL_ERROR oder SQL_SUCCESS_WITH_INFO empfängt. Dies ist einfach, wenn nur eine einzelne SQL-Anweisung ausgeführt wird, wie in den oben stehenden Beispielen. In diesen Fällen gibt der Aufruf von **SQLExecDirect** oder **SQLExecute** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, und **SQLGetDiagRec** kann dann aufgerufen werden. Komplizierter wird es, wenn Schleifen zum Behandeln der Ausgabe einer Reihe von SQL-Anweisungen codiert, oder wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-gespeicherte Prozeduren ausgeführt werden müssen.  
  
 In diesem Fall gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Resultset für jede SELECT-Anweisung zurück, die in einem Batch oder in einer gespeicherten Prozedur ausgeführt wurde. Wenn der Batch bzw. die Prozedur PRINT- oder RAISERROR-Anweisungen enthält, ist die Ausgabe dieser Anweisungen mit den Resultsets der SELECT-Anweisungen verschachtelt. Wenn die erste Anweisung im Batch oder in der Prozedur ein Druck-oder RAISERROR-Wert ist, gibt **SQLExecute** oder **SQLExecDirect** SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück, und die Anwendung muss **SQLGetDiagRec** aufrufen, bis SQL_NO_DATA zum Abrufen der Druck-oder RAISERROR-Informationen zurückgegeben wird.  
  
 Wenn die Print-oder RAISERROR-Anweisung auf eine SQL-Anweisung (z. b. eine SELECT-Anweisung) folgt, werden die Print-oder RAISERROR-Informationen zurückgegeben, wenn [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)in dem Resultset, das den Fehler enthält, positioniert werden. **SQLMoreResults** gibt SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurück, je nach Schweregrad der Nachricht. Nachrichten werden durch Aufrufen von **SQLGetDiagRec** abgerufen, bis SQL_NO_DATA zurückgegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
