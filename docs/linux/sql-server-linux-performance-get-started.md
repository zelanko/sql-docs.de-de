---
title: Erste Schritte mit Leistungsfeatures von SQL Server unter Linux | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Einführung in SQL Server-Leistung-Funktionen für Linux-Benutzer, die mit SQL Server vertraut sind. Viele dieser Beispiele auf allen Plattformen funktioniert, aber im Rahmen dieses Artikels ist Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 60036d26-4797-4872-9a9e-3552841c61be
ms.custom: sql-linux
ms.openlocfilehash: 3288bb18a4bc8d87b9be1eb8f57bbc66555b9db5
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52401350"
---
# <a name="walkthrough-for-the-performance-features-of-sql-server-on-linux"></a>Exemplarische Vorgehensweise für die Leistungsmerkmale von SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Wenn Sie einen Linux-Benutzer, der in SQL Server neu ist sind, durchlaufen die folgenden Aufgaben Sie einige der Leistungsfeatures. Diese sind nicht eindeutig oder speziell für Linux, aber es hilft, erhalten Sie eine Vorstellung von Bereichen, um weiter zu untersuchen. In jedem Beispiel wird ein Link in der Tiefe Dokumentation für den entsprechenden Bereich bereitgestellt.

> [!NOTE]
> In den folgenden Beispielen wird die Beispieldatenbank Adventure Works verwendet. Anweisungen zum Abrufen und Installieren dieser Beispieldatenbank finden Sie [wiederherstellen eine SQL Server-Datenbank von Windows bis Linux](sql-server-linux-migrate-restore-database.md).

## <a name="create-a-columnstore-index"></a>Erstellen Sie einen columnstore-Index
Ein columnstore-Index ist eine Technologie zum Speichern und Abfragen von große Datenspeicher in einer spaltenbasierten Datenformats, das als Columnstore bezeichnet wird.  

1. Fügen Sie einen columnstore-Index der SalesOrderDetail-Tabelle hinzu, durch die folgenden Transact-SQL-Befehle ausführen:

   ```sql
   CREATE NONCLUSTERED COLUMNSTORE INDEX [IX_SalesOrderDetail_ColumnStore]
      ON Sales.SalesOrderDetail
      (UnitPrice, OrderQty, ProductID)
   GO
   ```

2. Führen Sie die folgende Abfrage, die den columnstore-Index verwendet, um die Tabelle zu scannen:

   ```sql
   SELECT ProductID, SUM(UnitPrice) SumUnitPrice, AVG(UnitPrice) AvgUnitPrice,
      SUM(OrderQty) SumOrderQty, AVG(OrderQty) AvgOrderQty
   FROM Sales.SalesOrderDetail
      GROUP BY ProductID
      ORDER BY ProductID
   ```

3. Stellen Sie sicher, dass der columnstore-Index verwendet wurde, indem Sie die Objekt-ID für den columnstore-Index suchen und zu bestätigen, dass er in die Verwendungsstatistiken für der SalesOrderDetail-Tabelle angezeigt wird:

   ```sql
   SELECT * FROM sys.indexes WHERE name = 'IX_SalesOrderDetail_ColumnStore'
   GO

   SELECT * 
   FROM sys.dm_db_index_usage_stats
      WHERE database_id = DB_ID('AdventureWorks')
      AND object_id = OBJECT_ID('AdventureWorks.Sales.SalesOrderDetail');
   ```
   
## <a name="use-in-memory-oltp"></a>Verwenden von In-Memory-OLTP
SQL Server bietet In-Memory-OLTP-Funktionen, die die Leistung von Anwendungssystemen erheblich verbessern können.  In diesem Abschnitt, der das Evaluierungshandbuch führt Sie durch die Schritte zum Erstellen einer speicheroptimierten Tabelle gespeichert, die im Arbeitsspeicher und einer systemintern kompilierten gespeicherten Prozedur, die in der Tabelle ohne kompiliert oder interpretiert werden zugreifen können.

### <a name="configure-database-for-in-memory-oltp"></a>Konfigurieren Sie für In-Memory-OLTP-Datenbank
1. Es wird empfohlen, für die Datenbank auf einen Kompatibilitätsgrad von mindestens 130 mit In-Memory OLTP zu aktivieren.  Verwenden Sie die folgende Abfrage, um den aktuellen Kompatibilitätsgrad von AdventureWorks zu überprüfen:  

   ```sql
   USE AdventureWorks
   GO
   SELECT d.compatibility_level
   FROM sys.databases as d
     WHERE d.name = Db_Name();
   GO
   ```
   
   Aktualisieren Sie die Ebene in 130, bei Bedarf:

   ```sql
   ALTER DATABASE CURRENT
   SET COMPATIBILITY_LEVEL = 130;
   GO
   ```

2. Wenn eine Transaktion eine datenträgerbasierte Tabelle und eine Speicheroptimierte Tabelle einschließt, namens es wesentlich, die der Speicheroptimierte Teil der Transaktion ausgeführt werden, auf die Transaktionsisolationsstufe SNAPSHOT.  Um dieser Stufe für Speicheroptimierte Tabellen in einer containerübergreifenden Transaktion zuverlässig zu erzwingen, führen Sie die folgenden Schritte aus:

   ```sql
   ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
   GO
   ```

3. Vor der Erstellung eine speicheroptimierten Tabelle müssen Sie zunächst erstellen Sie eine Speicheroptimierte DATEIGRUPPE und ein Container für Datendateien:

   ```sql
   ALTER DATABASE AdventureWorks ADD FILEGROUP AdventureWorks_mod CONTAINS memory_optimized_data
   GO  
   ALTER DATABASE AdventureWorks ADD FILE (NAME='AdventureWorks_mod', FILENAME='/var/opt/mssql/data/AdventureWorks_mod') TO FILEGROUP AdventureWorks_mod
   GO
   ```

### <a name="create-a-memory-optimized-table"></a>Erstellen Sie eine Speicheroptimierte Tabelle
Beim Primärspeicher für Speicheroptimierte Tabellen Hauptspeicher und im Gegensatz zu datenträgerbasierten Tabellen ist daher, muss Daten nicht in Speicherpuffer im vom Datenträger gelesen werden.  Verwenden Sie zum Erstellen einer speicheroptimierten Tabelle die MEMORY_OPTIMIZED = ON-Klausel.

1. Führen Sie die folgende Abfrage aus, um das "Dbo" eine Speicheroptimierte Tabelle zu erstellen. ShoppingCart.  Standardmäßig werden die Daten beibehalten werden auf dem Datenträger zu (Beachten Sie, die DAUERHAFTIGKEIT auch festgelegt werden kann, um das Schema nur beizubehalten). 

   ```sql
   CREATE TABLE dbo.ShoppingCart ( 
   ShoppingCartId INT IDENTITY(1,1) PRIMARY KEY NONCLUSTERED,
   UserId INT NOT NULL INDEX ix_UserId NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000), 
   CreatedDate DATETIME2 NOT NULL, 
   TotalPrice MONEY
   ) WITH (MEMORY_OPTIMIZED=ON) 
   GO
   ```

2. Einige Datensätze in die Tabelle einzufügen:

   ```sql
   INSERT dbo.ShoppingCart VALUES (8798, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (23, SYSDATETIME(), 45.4) 
   INSERT dbo.ShoppingCart VALUES (80, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (342, SYSDATETIME(), 65.4) 
   ```

### <a name="natively-compiled-stored-procedure"></a>Systemintern kompilierte gespeicherte Prozedur
SQL Server unterstützt systemintern kompilierte gespeicherte Prozeduren, die auf Speicheroptimierte Tabellen zugreifen. T-SQL-Anweisungen sind in Computercode kompiliert und als systemeigene DLLs, aktivieren schnelleren Datenzugriff und eine effizientere abfrageausführung als herkömmlichen T-SQL gespeichert.   Gespeicherte Prozeduren, die mit NATIVE_COMPILATION markiert sind, werden systemintern kompiliert. 

1. Führen Sie das folgende Skript aus, um eine systemintern kompilierte gespeicherte Prozedur zu erstellen, die eine große Anzahl von Datensätzen in die ShoppingCart-Tabelle eingefügt:


   ```sql
   CREATE PROCEDURE dbo.usp_InsertSampleCarts @InsertCount int 
    WITH NATIVE_COMPILATION, SCHEMABINDING AS 
   BEGIN ATOMIC 
   WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')

   DECLARE @i int = 0

   WHILE @i < @InsertCount 
    BEGIN 
     INSERT INTO dbo.ShoppingCart VALUES (1, SYSDATETIME() , NULL) 
     SET @i += 1 
    END
   END 
   ```
2. Fügen Sie 1.000.000 Zeilen ein:

   ```sql
   EXEC usp_InsertSampleCarts 1000000 
   ```

3. Stellen Sie sicher, dass die Zeilen eingefügt wurden:

   ```sql
   SELECT COUNT(*) FROM dbo.ShoppingCart 
   ```

### <a name="learn-more-about-in-memory-oltp"></a>Erfahren Sie mehr über In-Memory-OLTP
Weitere Informationen zu In-Memory OLTP finden Sie unter den folgenden Themen:

- [Schnellstart 1: In-Memory-OLTP-Technologien für höhere Transact-SQL-Leistung](../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)
- [Migrieren zu In-Memory OLTP](../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)
- [Schnellere temporäre Tabellen und Tabellenvariablen durch Speicheroptimierung](../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)
- [Überwachung und Fehlerbehebung für die Arbeitsspeicherauslastung](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)
- [In-Memory OLTP (Arbeitsspeicheroptimierung)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)

## <a name="use-query-store"></a>Die Query Store verwenden
Query Store werden ausführliche Informationen zu Abfragen, Ausführungspläne und Laufzeitstatistiken erfasst.

Query Store ist nicht standardmäßig aktiviert, und können mit ALTER DATABASE aktiviert werden:

   ```sql
   ALTER DATABASE AdventureWorks SET QUERY_STORE = ON;
   ```

Führen Sie die folgende Abfrage aus, um Informationen zu Abfragen und Pläne im Abfragespeicher zurückzugeben: 

   ```sql
   SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
   FROM sys.query_store_plan AS Pl
      JOIN sys.query_store_query AS Qry
         ON Pl.query_id = Qry.query_id
      JOIN sys.query_store_query_text AS Txt
         ON Qry.query_text_id = Txt.query_text_id ;
   ```

## <a name="query-dynamic-management-views"></a>Dynamische Verwaltungssichten für Abfrage
Dynamische Verwaltungssichten zurück Informationen zum Serverstatus, die verwendet werden kann, um den Zustand einer Serverinstanz zu überwachen, Diagnostizieren von Problemen und Optimieren der Leistung.

So fragen Sie die Dm_os_wait Statistiken des dynamische verwaltungssicht:

   ```sql
   SELECT wait_type, wait_time_ms
   FROM sys.dm_os_wait_stats;
   ```
