---
title: sys. PDW _nodes_partitions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b4216752-4813-4b2c-b259-7d8ffc6cc190
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d0fc42e1ce8d15498caf89582b66549f4e083130
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305230"
---
# <a name="syspdw_nodes_partitions-transact-sql"></a>sys.pdw_nodes_partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jede Partition aller Tabellen und die meisten Index Typen in einer [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]-Datenbank. Alle Tabellen und Indizes enthalten mindestens eine Partition, unabhängig davon, ob Sie explizit partitioniert sind.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|die ID der Partition. Ist innerhalb einer Datenbank eindeutig.|  
|object_id|**int**|ID des Objekts, zu dem diese Partition gehört. Jede Tabelle oder Sicht besteht aus mindestens einer Partition.|  
|index_id|**int**|ID des Indexes innerhalb des Objekts, zu dem diese Partition gehört.|  
|partition_number|**int**|Auf 1 basierende Partitionsnummer im besitzenden Index oder Heap. Bei [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ist der Wert dieser Spalte 1.|  
|hobt_id|**bigint**|Die ID des Data Heap-oder B-Struktur (hubt), das die Zeilen für diese Partition enthält.|  
|rows|**bigint**|Die ungefähre Anzahl der Zeilen in dieser Partition. |  
|data_compression|**int**|Gibt den Status der Komprimierung für jede Partition an:<br /><br /> 0 = NONE<br /><br /> 1 = ROW<br /><br /> 2 = PAGE<br /><br /> 3 = COLUMNSTORE|  
|data_compression_desc|**nvarchar(60)**|Gibt den Status der Komprimierung für jede Partition an. Mögliche Werte sind NONE, ROW und PAGE.|  
|pdw_node_id|**int**|Eindeutiger Bezeichner eines [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]-Knotens.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `CONTROL SERVER`-Berechtigung.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  

### <a name="example-a-display-rows-in-each-partition-within-each-distribution"></a>Beispiel A: Zeilen in jeder Partition in jeder Verteilung anzeigen 

**Gilt für:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
 
Verwenden Sie [DBCC PDW_SHOWPARTITIONSTATS (SQL Server PDW)](../../t-sql/database-console-commands/dbcc-pdw-showpartitionstats-transact-sql.md) , um die Anzahl der Zeilen in jeder Partition innerhalb der Verteilung anzuzeigen.

### <a name="example-b-uses-system-views-to-view-rows-in-each-partition-of-each-distribution-of-a-table"></a>Beispiel B: Verwendet System Sichten, um Zeilen in jeder Partition jeder Verteilung einer Tabelle anzuzeigen.

**Gilt für:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]
 
Diese Abfrage gibt die Anzahl der Zeilen in jeder Partition jeder Verteilung der Tabelle `myTable` zurück.  
 
```sql  
SELECT o.name, pnp.index_id, pnp.partition_id, pnp.rows,   
    pnp.data_compression_desc, pnp.pdw_node_id  
FROM sys.pdw_nodes_partitions AS pnp  
JOIN sys.pdw_nodes_tables AS NTables  
    ON pnp.object_id = NTables.object_id  
AND pnp.pdw_node_id = NTables.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON NTables.name = TMap.physical_name 
    AND substring(TMap.physical_name,40, 10) = pnp.distribution_id 
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
WHERE o.name = 'myTable'  
ORDER BY o.name, pnp.index_id, pnp.partition_id;  
```    
  
## <a name="see-also"></a>Siehe auch  
 [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  

