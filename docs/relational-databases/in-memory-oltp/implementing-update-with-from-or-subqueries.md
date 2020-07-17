---
title: Implementieren von UPDATE mit FROM oder Unterabfragen | Microsoft-Dokumentation
description: Erfahren Sie, welche Syntaxelemente in einem nativ kompilierten T-SQL-Modul von der Transact-SQL-Anweisung UPDATE unterstützt werden.
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 138f5b0e-f8a4-400f-b581-8062aebc62b6
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 95e55e1519ab61eee3bed031d0d80565e56b0a69
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723155"
---
# <a name="implementing-update-with-from-or-subqueries"></a>Implementieren von UPDATE mit FROM oder Unterabfragen

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]



In einem nativ kompilierten T-SQL-Modul werden folgende Syntaxelemente *nicht* von der UPDATE-Anweisung in Transact-SQL unterstützt:

- FROM-Klausel
- Unterabfragen

Im Gegensatz dazu werden die vorherigen Elemente in nativ kompilierten Modulen von der SELECT-Anweisung *unterstützt*.

UPDATE-Anweisungen mit einer FROM-Klausel werden oft verwendet, um Informationen in einer Tabelle, die auf einem Tabellenwertparameter (table-valued parameter; TVP) basiert, oder Spalten in einer Tabelle in einem AFTER-Trigger zu aktualisieren.

Ein Updateszenario, das auf einem Tabellenwertparameter basiert, finden Sie unter [Implementieren von MERGE-Funktionalität in einer nativ kompilierten gespeicherten Prozedur](../../relational-databases/in-memory-oltp/implementing-merge-functionality-in-a-natively-compiled-stored-procedure.md). 

Im folgende Beispiel wird ein in einem Trigger ausgeführtes Update veranschaulicht. In der Tabelle wird die Spalte „LastUpdated“ mithilfe der AFTER-Anweisung auf das aktuelle Datums-/Uhrzeitformat nach dem Update festgelegt. Die Problemumgehung führt mithilfe der folgenden Elemente einzelne Updates aus:

- Eine Tabellenvariable, die eine IDENTITY-Spalte aufweist.
- Eine WHILE-Schleife zum Durchlaufen der Zeilen in der Tabellenvariablen.

Dies ist die ursprüngliche T-SQL UPDATE-Anweisung:

   ```sql
    UPDATE dbo.Table1  
        SET LastUpdated = SysDateTime()  
        FROM  
            dbo.Table1 t  
            JOIN Inserted i ON t.Id = i.Id;  
   ```

Der T-SQL-Beispielcode im folgenden Block veranschaulicht eine leistungsstarke Problemumgehung. Die Problemumgehung wird in einem nativ kompilierten Trigger implementiert. Beachten Sie unbedingt:  
  
- Den Typen namens dbo.Type1, der einen speicheroptimierten Tabellentyp darstellt.  
- Die WHILE-Schleife im Trigger.  
  - Dass die Schleife die Zeilen eine nach der anderen aus „Inserted“ abruft.  
  
  
  
 ```sql
    DROP TABLE IF EXISTS dbo.Table1;  
    go  
    DROP TYPE IF EXISTS dbo.Type1;  
    go  
    -----------------------------
    -- Table and table type.
    -----------------------------
  
    CREATE TABLE dbo.Table1  
    (  
        Id           INT        NOT NULL  PRIMARY KEY NONCLUSTERED,  
        Column2      INT        NOT NULL,  
        LastUpdated  DATETIME2  NOT NULL  DEFAULT (SYSDATETIME())  
    )  
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
  
  
    CREATE TYPE dbo.Type1 AS TABLE  
    (  
        Id       INT NOT  NULL,  
        
        RowID    INT NOT  NULL  IDENTITY,  
        INDEX ix_RowID HASH (RowID) WITH (BUCKET_COUNT=1024)
    )   
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
    ----------------------------------------
    -- Trigger that contains the workaround
    -- for UPDATE with FROM.
    ----------------------------------------
  
    CREATE TRIGGER dbo.tr_a_u_Table1  
        ON dbo.Table1  
        WITH NATIVE_COMPILATION, SCHEMABINDING  
        AFTER UPDATE  
    AS 
    BEGIN ATOMIC WITH  
        (  
        TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
        LANGUAGE = N'us_english'  
        )  
        
      DECLARE @tabvar1 dbo.Type1;  
    
      INSERT @tabvar1 (Id)   
          SELECT Id FROM Inserted;  
    
      DECLARE  
          @i INT = 1,  @Id INT,  
          @max INT = SCOPE_IDENTITY();  
    
      ---- Loop as a workaround to simulate a cursor.
      ---- Iterate over the rows in the memory-optimized table  
      ----   variable and perform an update for each row.  
    
      WHILE @i <= @max  
      BEGIN  
          SELECT @Id = Id  
              FROM @tabvar1  
              WHERE RowID = @i;  
    
          UPDATE dbo.Table1  
              SET LastUpdated = SysDateTime()  
              WHERE Id = @Id;  
    
          SET @i += 1;  
      END  
    END  
    go  
    ---------------------------------
    -- Test to verify functionality.
    ---------------------------------
  
    SET NOCOUNT ON;  
  
    INSERT dbo.Table1 (Id, Column2)  
        VALUES (1,9), (2,9), (3,600);  
    
    SELECT N'BEFORE-Update' AS [BEFORE-Update], *  
        FROM dbo.Table1  
        ORDER BY Id;  
  
    WAITFOR DELAY '00:00:01';  

    UPDATE dbo.Table1  
        SET   Column2 += 1  
        WHERE Column2 <= 99;  
  
    SELECT N'AFTER--Update' AS [AFTER--Update], *  
        FROM dbo.Table1  
        ORDER BY Id;  
    go  
    -----------------------------  
  
    /**** Actual output:  
  
    BEFORE-Update   Id   Column2   LastUpdated  
    BEFORE-Update   1       9      2016-04-20 21:18:42.8394659  
    BEFORE-Update   2       9      2016-04-20 21:18:42.8394659  
    BEFORE-Update   3     600      2016-04-20 21:18:42.8394659  
  
    AFTER--Update   Id   Column2   LastUpdated  
    AFTER--Update   1      10      2016-04-20 21:18:43.8529692  
    AFTER--Update   2      10      2016-04-20 21:18:43.8529692  
    AFTER--Update   3     600      2016-04-20 21:18:42.8394659  
    ****/  
 ```
