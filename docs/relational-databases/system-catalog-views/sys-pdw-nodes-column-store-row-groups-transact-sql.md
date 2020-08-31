---
description: sys. pdw_nodes_column_store_row_groups (Transact-SQL)
title: sys. pdw_nodes_column_store_row_groups (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 08/05/2020
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 17a4c925-d4b5-46ee-9cd6-044f714e6f0e
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4e712d2b5adafbb3f47ef132c701a82d3c9026c9
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "89062349"
---
# <a name="syspdw_nodes_column_store_row_groups-transact-sql"></a>sys. pdw_nodes_column_store_row_groups (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Stellt Informationen zu gruppierten columnstore--Indizes auf Segment Basis bereit, damit Administratoren Entscheidungen zur Systemverwaltung in treffen können [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] . **sys. pdw_nodes_column_store_row_groups** verfügt über eine Spalte für die Gesamtzahl der physisch gespeicherten Zeilen (einschließlich der als gelöscht markierten Zeilen) und eine Spalte für die Anzahl der Zeilen, die als gelöscht markiert sind. Verwenden Sie **sys. pdw_nodes_column_store_row_groups** , um zu bestimmen, welche Zeilen Gruppen einen hohen Prozentsatz gelöschter Zeilen aufweisen und neu erstellt werden sollten.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID der zugrunde liegenden Tabelle. Dabei handelt es sich um die physische Tabelle auf dem Computeknoten, nicht um die object_id für die logische Tabelle auf dem Steuerelement Knoten. Beispielsweise stimmt object_id nicht mit dem object_id in sys. Tables.<br /><br /> Verwenden Sie zum Verknüpfen mit sys. Tables sys. pdw_index_mappings.|  
|**index_id**|**int**|ID des gruppierten columnstore--Indexes in *object_id* Tabelle.|  
|**partition_number**|**int**|ID der Tabellen Partition, die Zeilen Gruppen *row_group_id*enthält. Sie können *partition_number* verwenden, um diese DMV mit sys. Partitions zu verknüpfen.|  
|**row_group_id**|**int**|ID dieser Zeilen Gruppe. Diese ist innerhalb der Partition eindeutig.|  
|**dellta_store_hobt_id**|**bigint**|Die hobt_id für Deltazeilengruppen oder NULL, wenn der Zeilengruppentyp nicht Delta ist. Eine Deltazeilengruppe ist eine Zeilengruppe mit Lese-/Schreibzugriff, die neue Datensätze akzeptiert. Eine Delta Zeilen Gruppe hat den **offenen** Status. Eine Deltazeilengruppe befindet sich weiterhin im rowstore-Format und wurde nicht in das columnstore-Format komprimiert.|  
|**state**|**tinyint**|Die der state_description zugeordnete ID.<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED|  
|**state_desccription**|**nvarchar(60)**|Beschreibung des persistenten Status der Zeilengruppe:<br /><br /> Öffnen: eine Zeilen Gruppe mit Lese-/Schreibzugriff, die neue Datensätze akzeptiert. Eine offene Zeilengruppe befindet sich weiterhin im rowstore-Format und wurde nicht in das columnstore-Format komprimiert.<br /><br /> Closed: eine Zeilen Gruppe, die ausgefüllt, aber noch nicht durch den tupelverschiebungsprozess komprimiert wurde.<br /><br /> Komprimiert: eine Zeilen Gruppe, die ausgefüllt und komprimiert wurde.|  
|**total_rows**|**bigint**|Gesamtzahl der Zeilen, die in der Zeilengruppe physisch gespeichert sind. Einige wurden u. U. gelöscht, sind aber weiterhin gespeichert. Die maximale Anzahl der Zeilen in einer Zeilengruppe beträgt 1.048.576 (hexadezimal FFFFF).|  
|**deleted_rows**|**bigint**|Anzahl der in der Zeilen Gruppe physisch gespeicherten Zeilen, die zum Löschen markiert sind.<br /><br /> Immer 0 für Delta-Zeilen Gruppen.|  
|**size_in_bytes**|**int**|Kombinierte Größe (in Bytes) aller Seiten in dieser Zeilen Gruppe. Diese Größe enthält nicht die Größe, die zum Speichern von Metadaten oder freigegebenen Wörterbüchern erforderlich ist.|  
|**pdw_node_id**|**int**|Eindeutige ID eines [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knotens.|  
|**distribution_id**|**int**|Eindeutige ID der Verteilung.|
  
## <a name="remarks"></a>Hinweise  
 Gibt eine Zeile für jede columnstore-Zeilengruppe für jede Tabelle zurück, die über einen gruppierten oder nicht gruppierten columnstore-Index verfügt.  
  
 Verwenden Sie **sys. pdw_nodes_column_store_row_groups** , um die Anzahl der Zeilen, die in der Zeilen Gruppe enthalten sind, und die Größe der Zeilen Gruppe zu bestimmen.  
  
 Wenn die Anzahl der gelöschten Zeilen in einer Zeilengruppe auf einen hohen Prozentsatz der Gesamtzeilen ansteigt, wird die Tabelle weniger effizient. Erstellen Sie den columnstore-Index neu, um die Tabellengröße zu verringern und die Datenträger-E/A zu reduzieren, die zum Lesen der Tabelle erforderlich ist. Verwenden Sie die **Rebuild** -Option der **Alter Index** -Anweisung, um den columnstore--Index neu zu erstellen.  
  
 Der aktualisierbare columnstore-fügt zunächst neue Daten in eine **geöffnete** Zeilen Gruppe ein, die im rowstore-Format vorliegt, und wird manchmal auch als Delta Tabelle bezeichnet.  Wenn eine offene Zeilen Gruppe voll ist, ändert sich der Status in " **geschlossen**". Eine geschlossene Zeilen Gruppe wird vom tupelverschiebungsvorgang im columnstore--Format komprimiert, und der Status ändert sich in **komprimiert**.  Die Tupelverschiebungsfunktion ist ein Hintergrundprozess, der regelmäßig aktiv wird und überprüft, ob geschlossene Zeilengruppen vorhanden sind, die in eine columnstore-Zeilengruppe komprimiert werden können.  Die Tupelverschiebungsfunktion gibt außerdem alle Zeilengruppen frei, in denen alle Zeilen gelöscht wurden. Die zugeordneten Zeilen Gruppen **werden als veraltet**markiert. Verwenden Sie die Option **reorganisieren** der **Alter Index** -Anweisung, um den tupelverschiebungsvorgang sofort auszuführen.  
  
 Wenn eine columnstore-Zeilengruppe aufgefüllt wurde, wird sie komprimiert und akzeptiert keine neuen Zeilen mehr. Wenn aus einer komprimierten Gruppe Zeilen gelöscht werden, verbleiben sie zwar, werden aber als gelöscht gekennzeichnet. Updates einer komprimierten Gruppe werden als Löschvorgang für die komprimierte Gruppe und als Einfügevorgang für eine offene Gruppe implementiert.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW SERVER STATE**-Berechtigung.  
  
## <a name="examples-sssdw-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird die **sys. pdw_nodes_column_store_row_groups** -Tabelle mit anderen Systemtabellen verbunden, um Informationen zu bestimmten Tabellen zurückzugeben. Die berechnete `PercentFull`-Spalte ist eine Schätzung der Effizienz der Zeilengruppe. Wenn Sie Informationen zu einer einzelnen Tabelle suchen möchten, entfernen Sie die Kommentar-Bindestriche vor der WHERE-Klausel, und geben Sie einen Tabellennamen an.  
  
```sql
SELECT IndexMap.object_id,   
  object_name(IndexMap.object_id) AS LogicalTableName,   
  i.name AS LogicalIndexName, IndexMap.index_id, NI.type_desc,   
  IndexMap.physical_name AS PhyIndexNameFromIMap,   
  CSRowGroups.*,  
  100*(ISNULL(deleted_rows,0))/total_rows AS PercentDeletedRows   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.pdw_index_mappings AS IndexMap  
    ON i.object_id = IndexMap.object_id  
    AND i.index_id = IndexMap.index_id  
JOIN sys.pdw_nodes_indexes AS NI  
    ON IndexMap.physical_name = NI.name  
    AND IndexMap.index_id = NI.index_id  
JOIN sys.pdw_nodes_column_store_row_groups AS CSRowGroups  
    ON CSRowGroups.object_id = NI.object_id   
    AND CSRowGroups.pdw_node_id = NI.pdw_node_id  
    AND CSRowGroups.index_id = NI.index_id      
WHERE total_rows > 0
--WHERE t.name = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, IndexMap.physical_name, pdw_node_id;  
```  

Im folgenden [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] Beispiel werden die Zeilen pro Partition für geclusterte Spalten Speicher und die Anzahl der Zeilen in geöffneten, geschlossenen oder komprimierten Zeilen Gruppen gezählt:  

```sql
SELECT
    s.name AS [Schema Name]
    ,t.name AS [Table Name]
    ,rg.partition_number AS [Partition Number]
    ,SUM(rg.total_rows) AS [Total Rows]
    ,SUM(CASE WHEN rg.State = 1 THEN rg.Total_rows Else 0 END) AS [Rows in OPEN Row Groups]
    ,SUM(CASE WHEN rg.State = 2 THEN rg.Total_Rows ELSE 0 END) AS [Rows in Closed Row Groups]
    ,SUM(CASE WHEN rg.State = 3 THEN rg.Total_Rows ELSE 0 END) AS [Rows in COMPRESSED Row Groups]
FROM sys.pdw_nodes_column_store_row_groups rg
  JOIN sys.pdw_nodes_tables pt
    ON rg.object_id = pt.object_id
    AND rg.pdw_node_id = pt.pdw_node_id
    AND pt.distribution_id = rg.distribution_id
  JOIN sys.pdw_table_mappings tm
    ON pt.name = tm.physical_name
  INNER JOIN sys.tables t
    ON tm.object_id = t.object_id
  INNER JOIN sys.schemas s
    ON t.schema_id = s.schema_id
GROUP BY s.name, t.name, rg.partition_number
ORDER BY 1, 2
```
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Erstellen eines columnstore-Indexes &#40;Transact-SQL-&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys. pdw_nodes_column_store_segments &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys. pdw_nodes_column_store_dictionaries &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  
