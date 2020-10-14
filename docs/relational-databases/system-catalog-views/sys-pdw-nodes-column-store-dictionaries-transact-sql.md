---
description: sys.pdw_nodes_column_store_dictionaries (Transact-SQL)
title: sys.pdw_nodes_column_store_dictionaries (Transact-SQL)
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.custom: seo-dt-2019
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 7ae1c2e4-45c0-4880-a692-1f299fbcfd19
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3171dabfa8ebb3d1a71c88633457446ef2016593
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036920"
---
# <a name="syspdw_nodes_column_store_dictionaries-transact-sql"></a>sys.pdw_nodes_column_store_dictionaries (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält eine Zeile für jedes in columnstore--Indizes verwendete Wörterbuch. Wörterbücher werden zum Codieren bestimmter, aber nicht aller Datentypen verwendet. Daher verfügen nicht alle Spalten in einem columnstore-Index über Wörterbücher. Ein Wörterbuch kann als primäres Wörterbuch (für alle Segmente) und möglicherweise für weitere sekundäre Wörterbücher vorhanden sein, die für eine Teilmenge der Spaltensegmente verwendet werden.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Gibt die Partitions-ID an. Ist innerhalb einer Datenbank eindeutig.|  
|**hobt_id**|**bigint**|ID des Heap-oder B-Struktur Index ("hubt") für die Tabelle, die diesen columnstore--Index aufweist.|  
|**column_id**|**int**|ID der columnstore-Spalte.|  
|**dictionary_id**|**int**|ID des Wörterbuchs.|  
|**version**|**int**|Version des Wörterbuchformats.|  
|**type**|**int**|Wörterbuchtyp:<br /><br /> 1-Hash Wörterbuch mit **int** -Werten<br /><br /> 2-nicht verwendet<br /><br /> 3-Hash-Wörterbuch mit Zeichen folgen Werten<br /><br /> 4-Hash Wörterbuch mit **float** -Werten|  
|**last_id**|**int**|Die letzte Daten-ID im Wörterbuch.|  
|**entry_count**|**bigint**|Die Anzahl von Einträgen im Wörterbuch.|  
|**on_disc_size**|**bigint**|Größe des Wörterbuchs in Byte.|  
|**pdw_node_id**|**int**|Eindeutiger Bezeichner eines [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knotens.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten von Azure Synapse Analytics und Parallel Data Warehouse Catalog](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Erstellen eines columnstore-Indexes &#40;Transact-SQL-&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
  
