---
title: Sys. dm_db_partition_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_partition_stats
- dm_db_partition_stats_TSQL
- sys.dm_db_partition_stats_TSQL
- sys.dm_db_partition_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_partition_stats dynamic management view
ms.assetid: 9db9d184-b3a2-421e-a804-b18ebcb099b7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74e3de1c32cb1ca1833121b4de1cef4db66f9e49
ms.sourcegitcommit: fa2afe8e6aec51e295f55f8cc6ad3e7c6b52e042
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462657"
---
# <a name="sysdmdbpartitionstats-transact-sql"></a>sys.dm_db_partition_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Informationen zu Seiten- und Zeilenzahlen für jede Partition in der aktuellen Datenbank zurück.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **Sys. dm_pdw_nodes_db_partition_stats**. Die Partition_id in Sys. dm_pdw_nodes_db_partition_stats unterscheidet sich von der Partition_id in der sys.partitions-Katalogsicht für Azure SQL Data Warehouse.
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Die ID der Partition. Sie ist innerhalb einer Datenbank eindeutig. Dies ist der gleiche Wert wie die **Partition_id** in die **sys.partitions** Katalogsicht mit Ausnahme von Azure SQL Data Warehouse.|  
|**object_id**|**int**|Objekt-ID der Tabelle oder der indizierten Sicht, in der die Partition enthalten ist.|  
|**index_id**|**int**|ID des Heaps oder Indexes, in dem die Partition enthalten ist.<br /><br /> 0 = Heap<br /><br /> 1 = Gruppierter Index.<br /><br /> > 1 = nicht gruppierter Index|  
|**partition_number**|**int**|Auf 1 basierende Partitionsnummer im Index oder Heap.|  
|**in_row_data_page_count**|**bigint**|Anzahl der Seiten, die zum Speichern von Daten innerhalb einer Zeile dieser Partition verwendet werden. Falls die Partition Teil eines Heaps ist, gibt der Wert die Anzahl von Datenseiten im Heap an. Falls die Partition Teil eines Indexes ist, gibt der Wert die Anzahl der Seiten auf Blattebene an. (Die Seiten des inneren Blatts in der B-Struktur sind in der Zählung nicht enthalten.) IAM (Index Allocation Map)-Seiten sind in beiden Fällen nicht enthalten. Immer 0 für einen speicheroptimierten xVelocity-columnstore-Index.|  
|**in_row_used_page_count**|**bigint**|Gesamtanzahl der Seiten, die zum Speichern und Verwalten der Daten in Zeilen in dieser Partition verwendet werden. Dazu gehören die Seiten der B-Struktur, IAM-Seiten und alle Seiten in enthalten die **In_row_data_page_count** Spalte. Immer 0 für einen columnstore-Index.|  
|**in_row_reserved_page_count**|**bigint**|Gesamtanzahl der Seiten, die zum Speichern und Verwalten der Daten in Zeilen in dieser Partition reserviert sind, unabhängig davon, ob die Seiten verwendet werden. Immer 0 für einen columnstore-Index.|  
|**lob_used_page_count**|**bigint**|Anzahl der Seiten zum Speichern und Verwalten von Out-of-Row- **Text**, **Ntext**, **Image**, **varchar(max)** , **Nvarchar (max)** , **'varbinary(max)'** , und **Xml** Spalten innerhalb der Partition. IAM-Seiten sind eingeschlossen.<br /><br /> Gesamtzahl von LOBs, die zum Speichern und Verwalten des columnstore-Index in der Partition verwendet werden.|  
|**lob_reserved_page_count**|**bigint**|Gesamtzahl der Seiten, die zum Speichern und Verwalten von Out-of-Row reserviert **Text**, **Ntext**, **Image**, **varchar(max)** ,  **nvarchar(max)** , **'varbinary(max)'** , und **Xml** Spalten innerhalb der Partition, unabhängig davon, ob die Seiten verwendet werden. IAM-Seiten sind eingeschlossen.<br /><br /> Gesamtzahl von LOBs, die zum Speichern und Verwalten eines columnstore-Index in der Partition reserviert wurden.|  
|**row_overflow_used_page_count**|**bigint**|Anzahl der Seiten zum Speichern und Verwalten von Zeilenüberlauf **Varchar**, **Nvarchar**, **Varbinary**, und **Sql_variant** Spalten in der Partition. IAM-Seiten sind eingeschlossen.<br /><br /> Immer 0 für einen columnstore-Index.|  
|**row_overflow_reserved_page_count**|**bigint**|Gesamtzahl der Seiten, die zum Speichern und Verwalten von Zeilenüberlauf reserviert **Varchar**, **Nvarchar**, **Varbinary**, und **Sql_variant** die Spalten innerhalb der Partition, unabhängig davon, ob die Seiten verwendet werden. IAM-Seiten sind eingeschlossen.<br /><br /> Immer 0 für einen columnstore-Index.|  
|**used_page_count**|**bigint**|Gesamtanzahl der für die Partition verwendeten Seiten. Berechnet als **In_row_used_page_count** + **Lob_used_page_count** + **Row_overflow_used_page_count**.|  
|**reserved_page_count**|**bigint**|Gesamtanzahl der für die Partition reservierten Seiten. Berechnet als **In_row_reserved_page_count** + **Lob_reserved_page_count** + **Row_overflow_reserved_page_count**.|  
|**row_count**|**bigint**|Die ungefähre Anzahl von Zeilen in dieser Partition.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
|**distribution_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Die eindeutige numerische Id, die die Verteilung.|  
  
## <a name="remarks"></a>Hinweise  
 **Sys. dm_db_partition_stats** zeigt Informationen zu den Speicherplatz zum Speichern und Verwalten von Daten in Zeilen LOB-Daten und zeilenüberlaufdaten für alle Partitionen in einer Datenbank verwendet. Es wird eine Zeile pro Partition angezeigt.  
  
 Die Zahlen, auf denen die Ausgabe basiert, werden im Arbeitsspeicher zwischengespeichert oder auf einem Datenträger in unterschiedlichen Systemtabellen gespeichert.  
  
 In Zeilen gespeicherte Daten, LOB-Daten und Zeilenüberlaufdaten stellen die drei Zuordnungseinheiten dar, aus denen eine Partition besteht. Die [Sys. allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md) -Katalogsicht für Metadaten zu jeder Zuordnungseinheit in der Datenbank abgefragt werden kann.  
  
 Falls ein Heap oder Index nicht partitioniert ist, besteht er aus einer Partition (mit der Partitionsnummer = 1). Daher wird nur eine Zeile für diesen Heap oder Index zurückgegeben. Die [sys.partitions](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md) -Katalogsicht für Metadaten zu jeder Partition aller Tabellen und Indizes in einer Datenbank abgefragt werden kann.  
  
 Die Gesamtanzahl für eine einzelne Tabelle oder einen Index kann durch das Addieren der Zahlen für alle relevanten Partitionen bestimmt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung zum Abfragen der **Sys. dm_db_partition_stats** dynamische verwaltungssicht. Weitere Informationen zu Berechtigungen auf dynamische Verwaltungssichten, finden Sie unter [dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-all-counts-for-all-partitions-of-all-indexes-and-heaps-in-a-database"></a>A. Zurückgeben aller Zahlen für alle Partitionen aller Indizes und Heaps in einer Datenbank  
 Im folgenden Beispiel werden alle Zahlen für alle Partitionen von allen Indizes und Heaps in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank angezeigt.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats;  
GO  
```  
  
### <a name="b-returning-all-counts-for-all-partitions-of-a-table-and-its-indexes"></a>B. Zurückgeben aller Zahlen für alle Partitionen einer Tabelle und ihrer Indizes  
 Im folgenden Beispiel werden alle Zahlen aller Partitionen der `HumanResources.Employee`-Tabelle und ihrer Indizes angezeigt.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats   
WHERE object_id = OBJECT_ID('HumanResources.Employee');  
GO  
```  
  
### <a name="c-returning-total-used-pages-and-total-number-of-rows-for-a-heap-or-clustered-index"></a>C. Zurückgeben aller verwendeter Seiten und der Gesamtzahl der Zeilen für einen Heap oder einen gruppierten Index  
 Im folgenden Beispiel werden Angaben zu den insgesamt verwendeten Seiten und zur Gesamtanzahl der Zeilen für den Heap oder gruppierten Index der `HumanResources.Employee`-Tabelle zurückgegeben. Da die `Employee`-Tabelle standardmäßig nicht partitioniert ist, umfasst die Summe nur eine Partition.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT SUM(used_page_count) AS total_number_of_used_pages,   
    SUM (row_count) AS total_number_of_rows   
FROM sys.dm_db_partition_stats  
WHERE object_id=OBJECT_ID('HumanResources.Employee')    AND (index_id=0 or index_id=1);  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  


