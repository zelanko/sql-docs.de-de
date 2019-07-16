---
title: Sys.pdw_nodes_indexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 261bcb7f-a906-4979-b274-bc5f1aa66426
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 2eb13830f666d6fbec67566d26abc7614d317f4d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059313"
---
# <a name="syspdwnodesindexes-transact-sql"></a>sys.pdw_nodes_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Gibt Indizes für [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|die ID des Objekts, zu dem dieser Index gehört.||  
|NAME|**sysname**|Der Name des Indexes. Name ist nur innerhalb des Objekts eindeutig. NULL = Heap||  
|index_id|**int**|die ID des Indexes. Index_id ist nur innerhalb des Objekts eindeutig.<br /><br /> 0 = Heap<br /><br /> 1 = Gruppierter Index<br /><br /> > 1 = nicht gruppierter Index||  
|Typ|**tinyint**|Typ des Index:<br /><br /> 0 = Heap<br /><br /> 1 = In einem Cluster gruppiert<br /><br /> 2 = nicht gruppierter<br /><br /> 5 = gruppierter speicheroptimierter xVelocity optimierter columnstore-Index|  
|type_desc|**nvarchar(60)**|Beschreibung des Typs des Index:<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> GRUPPIERTER COLUMNSTORE||  
|is_unique|**bit**|0 = Der Index ist nicht eindeutig.|Immer 0.|  
|data_space_id|**int**|die ID des Datenspeicherplatzes für diesen Index. Der Datenspeicherplatz ist entweder eine Dateigruppe oder ein Partitionsschema.<br /><br /> 0 = Object_id ist eine Funktion mit Tabellenrückgabe.||  
|ignore_dup_key|**bit**|0 = IGNORE_DUP_KEY ist OFF.|Immer 0.|  
|is_primary_key|**bit**|1 = Der Index ist Teil einer PRIMARY KEY-Einschränkung.|Immer 0.|  
|is_unique_constraint|**bit**|1 = Der Index ist Teil einer UNIQUE-Einschränkung.|Immer 0.|  
|fill_factor|**tinyint**|> 0 = FILLFACTOR-Prozentsatz verwendet, wenn der Index erstellt oder neu erstellt wurde.<br /><br /> 0 = Standardwert|Immer 0.|  
|is_padded|**bit**|0 = PADINDEX ist OFF.|Immer 0.|  
|is_disabled|**bit**|1 = Der Index ist deaktiviert.<br /><br /> 0 = Der Index ist nicht deaktiviert.||  
|is_hypothetical|**bit**|0 = Der Index ist nicht hypothetisch.|Immer 0.|  
|allow_row_locks|**bit**|1 = Der Index lässt Zeilensperren zu.|Immer 1.|  
|allow_page_locks|**bit**|1 = Der Index lässt Seitensperren zu.|Immer 1.|  
|has_filter|**bit**|0 = Index hat keinen Filter.|Immer 0.|  
|filter_definition|**nvarchar(max)**|Ausdruck für die Teilmenge von Zeilen, die im gefilterten Index enthalten sind.|Immer NULL.|  
|pdw_node_id|**int**|Der eindeutige Bezeichner des eine [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knoten.|NOT NULL|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL SERVER-Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
