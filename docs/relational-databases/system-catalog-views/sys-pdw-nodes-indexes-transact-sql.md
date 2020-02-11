---
title: sys. pdw_nodes_indexes (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: bb20ecd4fe212f4004061a6c39ad33c3ffc8ac8e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68809935"
---
# <a name="syspdw_nodes_indexes-transact-sql"></a>sys. pdw_nodes_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Gibt Indizes für [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|ID des Objekts, zu dem dieser Index gehört.||  
|name|**sysname**|Der Name des Indexes. Der Name ist nur innerhalb des Objekts eindeutig. NULL = Heap||  
|index_id|**int**|ID des Indexes. index_id ist nur innerhalb des-Objekts eindeutig.<br /><br /> 0 = Heap<br /><br /> 1 = Gruppierter Index<br /><br /> > 1 = Nicht gruppierter Index||  
|type|**tinyint**|Typ des Index:<br /><br /> 0 = Heap<br /><br /> 1 = In einem Cluster gruppiert<br /><br /> 2 = Nicht gruppiert<br /><br /> 5 = gruppierter Speicher optimierter xvelocity-columnstore--Index|  
|type_desc|**nvarchar (60)**|Beschreibung des Typs des Index:<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> gruppierter columnstore||  
|is_unique|**bit**|0 = Der Index ist nicht eindeutig.|Immer 0.|  
|data_space_id|**int**|ID des Datenraums für diesen Index. Der Datenspeicherplatz ist entweder eine Dateigruppe oder ein Partitionsschema.<br /><br /> 0 = object_id ist eine Tabellenwertfunktion.||  
|ignore_dup_key|**bit**|0 = IGNORE_DUP_KEY ist OFF.|Immer 0.|  
|is_primary_key|**bit**|1 = Der Index ist Teil einer PRIMARY KEY-Einschränkung.|Immer 0.|  
|is_unique_constraint|**bit**|1 = Der Index ist Teil einer UNIQUE-Einschränkung.|Immer 0.|  
|fill_factor|**tinyint**|> 0 = FILLFACTOR-Prozentsatz, der beim Erstellen oder erneuten Erstellen des Indexes verwendet wurde.<br /><br /> 0 = Standardwert|Immer 0.|  
|is_padded|**bit**|0 = PADINDEX ist OFF.|Immer 0.|  
|is_disabled|**bit**|1 = Der Index ist deaktiviert.<br /><br /> 0 = Der Index ist nicht deaktiviert.||  
|is_hypothetical|**bit**|0 = Der Index ist nicht hypothetisch.|Immer 0.|  
|allow_row_locks|**bit**|1 = Der Index lässt Zeilensperren zu.|Immer 1.|  
|allow_page_locks|**bit**|1 = Der Index lässt Seitensperren zu.|Immer 1.|  
|has_filter|**bit**|0 = Index hat keinen Filter.|Immer 0.|  
|filter_definition|**nvarchar(max)**|Ausdruck für die Teilmenge von Zeilen, die im gefilterten Index enthalten sind.|Immer NULL.|  
|pdw_node_id|**int**|Eindeutiger Bezeichner [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] eines Knotens.|NOT NULL|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL SERVER-Berechtigung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
