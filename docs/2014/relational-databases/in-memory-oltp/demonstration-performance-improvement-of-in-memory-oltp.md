---
title: 'Demo: Leistungsverbesserungen von In-Memory OLTP | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c6def45d-d2d4-4d24-8068-fab4cd94d8cc
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 8c9477a318d2cb4f9886d67da8a4f8b5967cc180
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63071785"
---
# <a name="demonstration-performance-improvement-of-in-memory-oltp"></a>Demo: Leistungsverbesserungen von In-Memory OLTP
  Dieses Beispiel zeigt Leistungsverbesserungen bei Verwendung von In-Memory OLTP, indem die Unterschiede bei der Antwortzeit bei Ausführung einer identischen Transact-SQL-Abfrage für speicheroptimierte und herkömmliche datenträgerbasierte Tabellen verglichen werden. Darüber hinaus wird eine systemintern kompilierte gespeicherte Prozedur erstellt (basierend auf der gleichen Abfrage) und dann ausgeführt, um zu veranschaulichen, dass die besten Antwortzeiten in der Regel beim Abfragen einer speicheroptimierten Tabelle mit einer systemintern kompilierten gespeicherten Prozedur erzielt werden. Dieses Beispiel zeigt nur einen Aspekt der Leistungsverbesserungen beim Zugriff auf Daten in speicheroptimierten Tabellen; Effizienz beim Datenzugriff bei der Durchführung von Einfügungen. Dieses Beispiel verwendet nur einen einzelnen Thread und nutzt nicht die Parallelitätsvorteile von In-Memory OLTP. Eine Arbeitsauslastung, die Parallelität verwendet, bietet noch größere Leistungsvorteile.  
  
> [!NOTE]  
>  Ein weiteres Beispiel zur Veranschaulichung Speicher optimierter Tabellen finden Sie unter [SQL Server 2014 in-Memory-OLTP-Beispiel](https://msftdbprodsamples.codeplex.com/releases/view/114491).  
  
 Für dieses Beispiel führen Sie die folgenden Schritte aus:  
  
1.  Erstellen Sie eine Datenbank namens **imoltp** , und ändern Sie die Dateidetails, um Sie für die Verwendung von in-Memory OLTP einzurichten.  
  
2.  Erstellen Sie die Datenbankobjekte für das Beispiel: drei Tabellen und eine systemintern kompilierte gespeicherte Prozedur.  
  
3.  Führen Sie die verschiedenen Abfragen aus, und zeigen Sie die Antwortzeiten für jede Abfrage an.  
  
 Um die **imoltp** -Datenbank für unser Beispiel einzurichten, erstellen Sie zunächst einen leeren Ordner: **c:\ imoltp_data**, und führen Sie dann den folgenden Code aus:  
  
```sql  
USE master  
GO  
  
-- Create a new database.  
CREATE DATABASE imoltp  
GO  
  
-- Prepare the database for In-Memory OLTP by  
-- adding a memory-optimized filegroup to the database.  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_file_group  
    CONTAINS MEMORY_OPTIMIZED_DATA;  
  
-- Add a file (to hold the memory-optimized data) to the new filegroup.  
ALTER DATABASE imoltp ADD FILE (name='imoltp_file', filename='c:\imoltp_data\imoltp_file')  
    TO FILEGROUP imoltp_file_group;  
GO  
  
```  
  
 Führen Sie als Nächstes den folgenden Code aus, um die datenträgerbasierte Tabelle, zwei (2) speicheroptimierte Tabellen und die systemintern kompilierte gespeicherte Prozedur zu erstellen, die zur Veranschaulichung der verschiedenen Datenzugriffsmethoden verwendet werden:  
  
```sql  
USE imoltp  
GO  
  
-- If the tables or stored procedure already exist, drop them to start clean.  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'DiskBasedTable')  
   DROP TABLE [dbo].[DiskBasedTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'InMemTable')  
   DROP TABLE [dbo].[InMemTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'InMemTable2')  
   DROP TABLE [dbo].[InMemTable2]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'usp_InsertData')  
   DROP PROCEDURE [dbo].[usp_InsertData]  
GO  
  
-- Create a traditional disk-based table.  
CREATE TABLE [dbo].[DiskBasedTable] (  
  c1 INT NOT NULL PRIMARY KEY,  
  c2 NCHAR(48) NOT NULL  
)  
GO  
  
-- Create a memory-optimized table.  
CREATE TABLE [dbo].[InMemTable] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a 2nd memory-optimized table.  
CREATE TABLE [dbo].[InMemTable2] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a natively-compiled stored procedure.  
CREATE PROCEDURE [dbo].[usp_InsertData]   
  @rowcount INT,  
  @c NCHAR(48)  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS   
  BEGIN ATOMIC   
  WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @i INT = 1;  
  WHILE @i <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[inMemTable2](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
END  
GO  
  
```  
  
 Das Setup ist abgeschlossen, und Sie können nun die Abfragen ausführen, die die Antwortzeiten anzeigen, anhand derer die Leistung der verschiedenen Datenzugriffsmethoden verglichen werden kann.  
  
 Führen Sie zum Abschließen des Beispiels den folgenden Code mehrmals aus. Ignorieren Sie die Ergebnisse der ersten Ausführung, da diese durch die anfängliche Speicherbelegung beeinträchtigt wird.  
  
```sql  
SET STATISTICS TIME OFF;  
SET NOCOUNT ON;  
  
-- Delete data from all tables to reset the example.  
DELETE FROM [dbo].[DiskBasedTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[inMemTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[InMemTable2]   
    WHERE [c1]>0  
GO  
  
-- Declare parameters for the test queries.  
DECLARE @i INT = 1;  
DECLARE @rowcount INT = 100000;  
DECLARE @c NCHAR(48) = N'12345678901234567890123456789012345678';  
DECLARE @timems INT;  
DECLARE @starttime datetime2 = sysdatetime();  
  
-- Disk-based table queried with interpreted Transact-SQL.  
BEGIN TRAN  
  WHILE @I <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[DiskBasedTable](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (disk-based table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with interpreted Transact-SQL.  
SET @i = 1;  
SET @starttime = sysdatetime();  
  
BEGIN TRAN  
  WHILE @i <= @rowcount  
    BEGIN  
      INSERT INTO [dbo].[InMemTable](c1,c2) VALUES (@i, @c);  
      SET @i += 1;  
    END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with a natively-compiled stored procedure.  
SET @starttime = sysdatetime();  
  
EXEC usp_InsertData @rowcount, @c;  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with natively-compiled stored procedure).';  
  
```  
  
 Die erwarteten Ergebnisse geben tatsächliche Antwortzeiten an, die zeigen, dass die Verwendung speicheroptimierter Tabellen und systemintern kompilierter gespeicherter Prozeduren in der Regel konsistent schnellere Antwortzeiten bietet als die Ausführung der gleichen Arbeitsauslastungen für herkömmliche datenträgerbasierte Tabellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen von AdventureWorks zur Veranschaulichung von in-Memory OLTP](../../database-engine/extensions-to-adventureworks-to-demonstrate-in-memory-oltp.md)   
 [In-Memory-OLTP &#40;in-Memory-Optimierung&#41;](in-memory-oltp-in-memory-optimization.md)   
 [Speicher optimierte Tabellen](memory-optimized-tables.md)   
 [System intern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)   
 [Anforderungen für die Verwendung Speicher optimierter Tabellen](requirements-for-using-memory-optimized-tables.md)   
 [Create Database &#40;SQL Server Transact-SQL-&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE-Optionen Datei und Dateigruppe &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)   
 [Erstellen von Prozeduren und Speicher optimierten Tabellen](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
