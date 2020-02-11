---
title: sys. dm_db_partition_stats (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cb9ab9e3cbf5948e5e832171c179d6daa2c0bc28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096283"
---
# <a name="sysdm_db_partition_stats-transact-sql"></a>sys.dm_db_partition_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Informationen zu Seiten- und Zeilenzahlen für jede Partition in der aktuellen Datenbank zurück.  
  
> [!NOTE]  
>  Um dies von oder [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]aus aufzurufen, verwenden Sie den Namen **sys. dm_pdw_nodes_db_partition_stats**. Der partition_id in sys. dm_pdw_nodes_db_partition_stats unterscheidet sich vom partition_id in der sys. Partitions-Katalog Sicht für Azure SQL Data Warehouse.
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**partition_id**|**BIGINT**|Die ID der Partition. Sie ist innerhalb einer Datenbank eindeutig. Dies ist der gleiche Wert wie der **partition_id** in der **sys. Partitions** -Katalog Sicht, mit Ausnahme von Azure SQL Data Warehouse.|  
|**object_id**|**int**|Objekt-ID der Tabelle oder der indizierten Sicht, in der die Partition enthalten ist.|  
|**index_id**|**int**|ID des Heaps oder Indexes, in dem die Partition enthalten ist.<br /><br /> 0 = Heap<br /><br /> 1 = Gruppierter Index.<br /><br /> > 1 = Nicht gruppierter Index|  
|**partition_number**|**int**|Auf 1 basierende Partitionsnummer im Index oder Heap.|  
|**in_row_data_page_count**|**BIGINT**|Anzahl der Seiten, die zum Speichern von Daten innerhalb einer Zeile dieser Partition verwendet werden. Falls die Partition Teil eines Heaps ist, gibt der Wert die Anzahl von Datenseiten im Heap an. Falls die Partition Teil eines Indexes ist, gibt der Wert die Anzahl der Seiten auf Blattebene an. (Nicht Blattseiten in der B-Struktur sind in der Zählung nicht enthalten.) IAM-Seiten (IAM) sind in beiden Fällen nicht enthalten. Immer 0 für einen speicheroptimierten xVelocity-columnstore-Index.|  
|**in_row_used_page_count**|**BIGINT**|Gesamtanzahl der Seiten, die zum Speichern und Verwalten der Daten in Zeilen in dieser Partition verwendet werden. Die Zahl schließt Seiten des inneren Blatts in der B-Struktur, IAM-Seiten und alle Seiten ein, die in der **in_row_data_page_count**-Spalte enthalten sind. Immer 0 für einen columnstore-Index.|  
|**in_row_reserved_page_count**|**BIGINT**|Gesamtanzahl der Seiten, die zum Speichern und Verwalten der Daten in Zeilen in dieser Partition reserviert sind, unabhängig davon, ob die Seiten verwendet werden. Immer 0 für einen columnstore-Index.|  
|**lob_used_page_count**|**BIGINT**|Anzahl der Seiten, die zum Speichern und Verwalten von Spalten vom Typ **text**, **ntext**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)** und **xml** außerhalb von Zeilen in der Partition verwendet werden. IAM-Seiten sind eingeschlossen.<br /><br /> Gesamtzahl von LOBs, die zum Speichern und Verwalten des columnstore-Index in der Partition verwendet werden.|  
|**lob_reserved_page_count**|**BIGINT**|Gesamtanzahl der Seiten, die zum Speichern und Verwalten von Spalten vom Typ **text**, **ntext**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)** und **xml** außerhalb von Zeilen in der Partition reserviert sind, unabhängig davon, ob die Seiten verwendet werden. IAM-Seiten sind eingeschlossen.<br /><br /> Gesamtzahl von LOBs, die zum Speichern und Verwalten eines columnstore-Index in der Partition reserviert wurden.|  
|**row_overflow_used_page_count**|**BIGINT**|Anzahl der Seiten, die zum Speichern und Verwalten von Zeilenüberlaufspalten vom Typ **varchar**, **nvarchar**, **varbinary** und **sql_variant** in der Partition verwendet werden. IAM-Seiten sind eingeschlossen.<br /><br /> Immer 0 für einen columnstore-Index.|  
|**row_overflow_reserved_page_count**|**BIGINT**|Gesamtanzahl der Seiten, die zum Speichern und Verwalten von Zeilenüberlaufspalten vom Typ **varchar**, **nvarchar**, **varbinary** und **sql_variant** in der Partition reserviert sind, unabhängig davon, ob die Seiten verwendet werden. IAM-Seiten sind eingeschlossen.<br /><br /> Immer 0 für einen columnstore-Index.|  
|**used_page_count**|**BIGINT**|Gesamtanzahl der für die Partition verwendeten Seiten. Wird als **in_row_used_page_count** + **lob_used_page_count** + **row_overflow_used_page_count**berechnet.|  
|**reserved_page_count**|**BIGINT**|Gesamtanzahl der für die Partition reservierten Seiten. Wird als **in_row_reserved_page_count** + **lob_reserved_page_count** + **row_overflow_reserved_page_count**berechnet.|  
|**row_count**|**BIGINT**|Die ungefähre Anzahl von Zeilen in dieser Partition.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
|**distribution_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Die eindeutige, der Verteilung zugeordnete numerische ID.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sys. dm_db_partition_stats** zeigt Informationen zum Speicherplatz an, der zum Speichern und Verwalten von LOB-Daten in Zeilen und Zeilen Überlauf Daten für alle Partitionen in einer Datenbank verwendet wird. Es wird eine Zeile pro Partition angezeigt.  
  
 Die Zahlen, auf denen die Ausgabe basiert, werden im Arbeitsspeicher zwischengespeichert oder auf einem Datenträger in unterschiedlichen Systemtabellen gespeichert.  
  
 In Zeilen gespeicherte Daten, LOB-Daten und Zeilenüberlaufdaten stellen die drei Zuordnungseinheiten dar, aus denen eine Partition besteht. Die [sys.allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)-Katalogsicht kann für Metadaten zu jeder Zuordnungseinheit in der Datenbank abgefragt werden.  
  
 Falls ein Heap oder Index nicht partitioniert ist, besteht er aus einer Partition (mit der Partitionsnummer = 1). Daher wird nur eine Zeile für diesen Heap oder Index zurückgegeben. Die [sys.partitions](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)-Katalogsicht kann für Metadaten zu jeder Partition aller Tabellen und Indizes in einer Datenbank abgefragt werden.  
  
 Die Gesamtanzahl für eine einzelne Tabelle oder einen Index kann durch das Addieren der Zahlen für alle relevanten Partitionen bestimmt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung zum Abfragen der dynamischen Verwaltungssicht **sys.dm_db_partition_stats**. Weitere Informationen zu Berechtigungen für dynamische Verwaltungs Sichten finden Sie unter [dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  


