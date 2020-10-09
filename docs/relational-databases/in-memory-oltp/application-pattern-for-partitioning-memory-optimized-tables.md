---
title: Anwendungsmuster zur Partitionierung von speicheroptimierten Tabellen
description: Hier erfahren Sie mehr über das Entwurfsmuster der In-Memory OLTP-Anwendung, die die aktuellen aktiven Daten in einer speicheroptimierten Tabelle und ältere Daten in einer partitionierten Tabelle speichert.
ms.custom: seo-dt-2019,issue-PR=4700-14820
ms.date: 05/03/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 3f867763-a8e6-413a-b015-20e9672cc4d1
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 08fb58f77382dae2d6455cc181c983798c89050a
ms.sourcegitcommit: d56a834269132a83e5fe0a05b033936776cda8bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91529411"
---
# <a name="application-pattern-for-partitioning-memory-optimized-tables"></a>Anwendungsmuster zur Partitionierung von speicheroptimierten Tabellen

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

[!INCLUDE[hek_2](../../includes/hek-2-md.md)] unterstützt ein Anwendungsentwurfsmuster, das Leistungsressourcen für relativ aktuelle Daten bereitstellt. Dieses Muster kann angewendet werden, wenn aktuelle Daten wesentlich häufiger gelesen oder aktualisiert werden als ältere Daten. In diesem Fall werden die aktuellen Daten als *aktiv* oder *heiß* und die älteren Daten als *kalt* bezeichnet.

Der Hauptgedanke besteht darin, *heiße* Daten in einer speicheroptimierten Tabelle zu speichern. Ältere und somit *kalte* Daten werden wöchentlich oder monatlich in eine partitionierte Tabelle verschoben. In der partitionierten Tabelle werden die Daten auf einem Datenträger oder auf einer anderen Festplatte und nicht im Arbeitsspeicher gespeichert.

In der Regel wird bei diesem Entwurf ein **datetime**-Schlüssel verwendet, damit der Verschiebungsvorgang effizient zwischen heißen und kalten Daten unterscheiden kann.

## <a name="advanced-partitioning"></a>Erweiterte Partitionierung

Der Entwurf soll eine partitionierte Tabelle mit einer speicheroptimierten Partition imitieren. Damit dieser Entwurf funktioniert, müssen Sie sicherstellen, dass alle Tabellen ein gemeinsames Schema verwenden. Das Codebeispiel weiter unten in diesem Artikel veranschaulicht dieses Verfahren.

Es wird davon ausgegangen, dass neue Daten der Definition nach heiß sind. Heiße Daten werden in die speicheroptimierte Tabelle eingefügt und aktualisiert. Kalte Daten werden in der herkömmlichen partitionierten Tabelle beibehalten. Eine gespeicherte Prozedur fügt in regelmäßigen Abständen eine neue Partition hinzu. Die Partition enthält die neuesten kalten Daten, die aus der speicheroptimierten Tabelle verschoben wurden.

Wenn für einen Vorgang nur heiße Daten benötigt werden, können nativ kompilierte gespeicherte Prozeduren für den Zugriff auf die Daten verwendet werden. Vorgänge, bei denen auf heiße oder kalte Daten zugegriffen wird, müssen interpretiertes [!INCLUDE[tsql](../../includes/tsql-md.md)] verwenden, um die speicheroptimierte Tabelle mit der partitionierten Tabelle zu verknüpfen.

### <a name="add-a-partition"></a>Hinzufügen einer Partition

Daten, die vor kurzem kalt geworden sind, müssen in die partitionierte Tabelle verschoben werden. Die Schritte für diesen regelmäßigen Partitionsaustausch lauten wie folgt:

1. Legen Sie für die Daten in der speicheroptimierten Tabelle den datetime-Wert fest, der die Grenze bzw. den Umstellungszeitpunkt für die heißen bzw. neuen kalten Daten darstellt.
2. Fügen Sie die neuen kalten Daten aus der In-Memory-OLTP-Tabelle in eine *cold\_staging*-Tabelle ein.
3. Löschen Sie diese kalten Daten aus der speicheroptimierten Tabelle.
4. Ändern Sie die „cold\_staging“-Tabelle in eine Partition.
5. Fügen Sie die Partition hinzu.

#### <a name="maintenance-window"></a>Wartungsfenster

Einer der vorangegangenen Schritte besteht darin, die neuen kalten Daten aus der speicheroptimierten Tabelle zu löschen. Es gibt einen Zeitintervall zwischen diesem Löschvorgang und dem letzten Schritt, mit dem die neue Partition hinzufügt wird. Während dieses Intervalls tritt bei jeder Anwendung, die versucht, die neuen kalten Daten zu lesen, ein Fehler auf.

Ein Beispiel dazu finden Sie unter [Partitionierung auf Anwendungsebene](../../relational-databases/in-memory-oltp/application-level-partitioning.md).

## <a name="code-sample"></a>Codebeispiel

Das folgende Transact-SQL-Beispiel wird nur für die vereinfachte Darstellung in mehreren kleineren Codeblöcken angezeigt. Für Ihre Tests könnten Sie alle an einen großen Codeblock anfügen.

Insgesamt zeigt das T-SQL-Beispiel, wie eine speicheroptimierte Tabelle mit einer partitionierten, datenträgerbasierten Tabelle verwendet wird.

In den ersten Phasen des T-SQL-Beispiels werden zunächst die Datenbank und anschließend Objekte wie Tabellen in der Datenbank erstellt. In den weiteren Phasen wird gezeigt, wie Daten aus einer speicheroptimierten Tabelle in eine partitionierte Tabelle verschoben werden.

### <a name="create-a-database"></a>Erstellen einer Datenbank

In diesem Abschnitt des T-SQL-Beispiels wird eine Testdatenbank erstellt. Die Datenbank ist so konfiguriert, dass sowohl speicheroptimierte Tabellen als auch partitionierte Tabellen unterstützt werden.

```sql
CREATE DATABASE PartitionSample;
GO

-- Add a FileGroup, enabled for In-Memory OLTP.
-- Change file path as needed.

ALTER DATABASE PartitionSample
    ADD FILEGROUP PartitionSample_mod
    CONTAINS MEMORY_OPTIMIZED_DATA;

ALTER DATABASE PartitionSample
    ADD FILE(
        NAME = 'PartitionSample_mod',
        FILENAME = 'c:\data\PartitionSample_mod')
    TO FILEGROUP PartitionSample_mod;
GO
```

### <a name="create-a-memory-optimized-table-for-hot-data"></a>Erstellen einer speicheroptimierten Tabelle für heiße Daten

In diesem Abschnitt wird die speicheroptimierte Tabelle erstellt, in der die neuesten Daten enthalten sind. Bei diesen Daten handelt es sich noch immer größtenteils um heiße Daten.

```sql
USE PartitionSample;
GO

-- Create a memory-optimized table for the HOT Sales Order data.
-- Notice the index that uses datetime2.

CREATE TABLE dbo.SalesOrders_hot (
   so_id INT IDENTITY PRIMARY KEY NONCLUSTERED,
   cust_id INT NOT NULL,
   so_date DATETIME2 NOT NULL INDEX ix_date NONCLUSTERED,
   so_total MONEY NOT NULL,
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)
) WITH (MEMORY_OPTIMIZED=ON);
GO
```

### <a name="create-a-partitioned-table-for-cold-data"></a>Erstellen einer partitionierten Tabelle für kalte Daten

In diesem Abschnitt wird die partitionierte Tabelle erstellt, in der die kalten Daten enthalten sind.

```sql
-- Create a partition and table for the COLD Sales Order data.
-- Notice the index that uses datetime2.

CREATE PARTITION FUNCTION [ByDatePF](datetime2) AS RANGE RIGHT
   FOR VALUES();
GO

CREATE PARTITION SCHEME [ByDateRange]
   AS PARTITION [ByDatePF]
   ALL TO ([PRIMARY]);
GO

CREATE TABLE dbo.SalesOrders_cold (
   so_id INT NOT NULL,
   cust_id INT NOT NULL,
   so_date DATETIME2 NOT NULL,
   so_total MONEY NOT NULL,
   CONSTRAINT PK_SalesOrders_cold PRIMARY KEY (so_id, so_date),
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)
) ON [ByDateRange](so_date);
GO
```

### <a name="create-a-table-to-store-cold-data-during-move"></a>Erstellen einer Tabelle zum Speichern kalter Daten während der Verschiebung

In diesem Abschnitt wird die „cold\_staging“-Tabelle erstellt. Es wird auch eine Ansicht erstellt, in der die aktiven und kalten Daten aus den beiden Tabellen zusammengeführt werden.

```sql
-- A table used to briefly stage the newly cold data, during moves to a partition.

CREATE TABLE dbo.SalesOrders_cold_staging (
   so_id INT NOT NULL,
   cust_id INT NOT NULL,
   so_date datetime2 NOT NULL,
   so_total MONEY NOT NULL,
   CONSTRAINT PK_SalesOrders_cold_staging PRIMARY KEY (so_id, so_date),
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc),
   CONSTRAINT CHK_SalesOrders_cold_staging CHECK (so_date >= '1900-01-01')
);
GO

-- A view, for retrieving the aggregation of hot plus cold data.

CREATE VIEW dbo.SalesOrders
AS SELECT so_id,
          cust_id,
          so_date,
          so_total,
          1 AS 'is_hot'
       FROM dbo.SalesOrders_hot
   UNION ALL
   SELECT so_id,
          cust_id,
          so_date,
          so_total,
          0 AS 'is_cold'
       FROM dbo.SalesOrders_cold;
GO
```

### <a name="create-the-stored-procedure"></a>Erstellen der gespeicherten Prozedur

In diesem Abschnitt wird die gespeicherte Prozedur erstellt, die Sie regelmäßig ausführen. Die Prozedur verschiebt neue kalte Daten aus der speicheroptimierten Tabelle in die partitionierte Tabelle.

```sql
-- A stored procedure to move all newly cold sales orders data
-- to its staging location.

CREATE PROCEDURE dbo.usp_SalesOrdersOffloadToCold @splitdate datetime2
   AS
   BEGIN
      BEGIN TRANSACTION;

      -- Insert the cold data as a temporary heap.
      INSERT INTO dbo.SalesOrders_cold_staging WITH (TABLOCKX)
      SELECT so_id , cust_id , so_date , so_total
         FROM dbo.SalesOrders_hot WITH (serializable)
         WHERE so_date <= @splitdate;

      -- Delete the moved data from the hot table.
      DELETE FROM dbo.SalesOrders_hot WITH (SERIALIZABLE)
         WHERE so_date <= @splitdate;

      -- Update the partition function, and switch in the new partition.
      ALTER PARTITION SCHEME [ByDateRange] NEXT USED [PRIMARY];

      DECLARE @p INT = (
        SELECT MAX(partition_number)
            FROM sys.partitions
            WHERE object_id = OBJECT_ID('dbo.SalesOrders_cold'));

      EXEC sp_executesql
        N'ALTER TABLE dbo.SalesOrders_cold_staging
            SWITCH TO dbo.SalesOrders_cold partition @i',
        N'@i int',
        @i = @p;

      ALTER PARTITION FUNCTION [ByDatePF]()
      SPLIT RANGE( @splitdate);

      -- Modify a constraint on the cold_staging table, to align with new partition.
      ALTER TABLE dbo.SalesOrders_cold_staging
         DROP CONSTRAINT CHK_SalesOrders_cold_staging;

      DECLARE @s nvarchar( 100) = CONVERT( nvarchar( 100) , @splitdate , 121);
      DECLARE @sql nvarchar( 1000) = N'alter table dbo.SalesOrders_cold_staging 
         add constraint CHK_SalesOrders_cold_staging check (so_date > ''' + @s + ''')';
      PRINT @sql;
      EXEC sp_executesql @sql;

      COMMIT;
END;
GO
```

### <a name="prepare-sample-data-and-demo-the-stored-procedure"></a>Vorbereiten von Beispieldaten und Veranschaulichung der gespeicherten Prozedur

In diesem Abschnitt werden Beispieldaten generiert und eingefügt. Anschließend wird die gespeicherte Prozedur zur Veranschaulichung ausgeführt.

```sql
-- Insert sample values into the hot table.
INSERT INTO dbo.SalesOrders_hot VALUES(1,SYSDATETIME(), 1);
GO
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);
GO
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);
GO

-- Verify that the hot data is in the table, by selecting from the view.
SELECT * FROM dbo.SalesOrders;
GO

-- Treat all data in the hot table as cold data:
-- Run the stored procedure, to move (offload) all sales orders to date to cold storage.
DECLARE @t datetime2 = SYSDATETIME();
EXEC dbo.usp_SalesOrdersOffloadToCold @t;

-- Again, read hot plus cold data from the view.
SELECT * FROM dbo.SalesOrders;
GO

-- Retrieve the name of every partition.
SELECT OBJECT_NAME( object_id) , * FROM sys.dm_db_partition_stats ps
   WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold');

-- Insert more data into the hot table.
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);
GO
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);
GO
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);
GO

-- Read hot plus cold data from the view.
SELECT * FROM dbo.SalesOrders;
GO

-- Again, run the stored procedure, to move all sales orders to date to cold storage.
DECLARE @t datetime2 = SYSDATETIME();
EXEC dbo.usp_SalesOrdersOffloadToCold @t;

-- Read hot plus cold data from the view.
SELECT * FROM dbo.SalesOrders;
GO

-- Again, retrieve the name of every partition.
-- The stored procedure can modify the partitions.
SELECT OBJECT_NAME( object_id) , partition_number , row_count
  FROM sys.dm_db_partition_stats ps
  WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold')
    AND index_id = 1;
```

### <a name="drop-all-the-demo-objects"></a>Löschen aller für die Veranschaulichung verwendeten Objekte

Denken Sie daran, die für die Veranschaulichung verwendete Testdatenbank vom Testsystem zu entfernen.

```sql
-- You must first leave the context of the PartitionSample database.

-- USE <A-Database-Name-Here>;
GO

DROP DATABASE PartitionSample;
GO
```

## <a name="see-also"></a>Weitere Informationen

[Speicheroptimierte Tabellen](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)
