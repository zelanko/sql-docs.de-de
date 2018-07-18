---
title: Sys.pdw_nodes_column_store_dictionaries (Transact-SQL) | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 7ae1c2e4-45c0-4880-a692-1f299fbcfd19
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 78d8a2e2362adbebfdb5fa03aa48800d7726d000
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36875028"
---
# <a name="syspdwnodescolumnstoredictionaries-transact-sql"></a>Sys.pdw_nodes_column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jedes Wörterbuch, das in den columnstore-Indizes verwendet. Wörterbücher werden zum Codieren bestimmter, aber nicht aller Datentypen verwendet. Daher verfügen nicht alle Spalten in einem columnstore-Index über Wörterbücher. Ein Wörterbuch kann als primäres Wörterbuch (für alle Segmente) und möglicherweise für weitere sekundäre Wörterbücher vorhanden sein, die für eine Teilmenge der Spaltensegmente verwendet werden.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Gibt die Partitions-ID an. Ist innerhalb einer Datenbank eindeutig.|  
|**hobt_id**|**bigint**|ID des Heaps oder B-Struktur-Indexes (hobt) für die Tabelle, die diesen columnstore-Index aufweist.|  
|**column_id**|**int**|ID der columnstore-Spalte.|  
|**dictionary_id**|**int**|ID des Wörterbuchs.|  
|**version**|**int**|Version des Wörterbuchformats.|  
|**type**|**int**|Wörterbuchtyp:<br /><br /> 1-Hash Wörterbuch mit **Int** Werte<br /><br /> 2 - Nicht verwendet<br /><br /> 3 – Hashwörterbuch, das Zeichenfolgenwerte enthält<br /><br /> 4 – hashwörterbuch Wörterbuch mit **"float"** Werte|  
|**last_id**|**int**|Die letzte Daten-ID im Wörterbuch.|  
|**entry_count**|**bigint**|Die Anzahl von Einträgen im Wörterbuch.|  
|**on_disc_size**|**bigint**|Größe des Wörterbuchs in Byte.|  
|**pdw_node_id**|**int**|Der eindeutige Bezeichner des eine [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knoten.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Columnstore-INDEX erstellen &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
  
