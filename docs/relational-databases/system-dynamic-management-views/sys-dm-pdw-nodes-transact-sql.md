---
title: Sys.dm_pdw_nodes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ff3f6c31389622dc424c42e06bfa78477c70cde2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769368"
---
# <a name="sysdmpdwnodes-transact-sql"></a>Sys.dm_pdw_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen Knoten im [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]. Sie enthält eine Zeile pro Knoten in der Appliance.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Eindeutige numerische Id, die dem Knoten zugeordnet.<br /><br /> Der Schlüssel für diese Sicht.|Auf der gesamten Appliance, unabhängig vom Typ eindeutig.|  
|Typ|**nvarchar(32)**|Der Typ des Knotens.|'BERECHNEN', 'CONTROL', 'VERWALTUNG'|  
|NAME|**nvarchar(32)**|Logischer Name des Knotens.|Jede Zeichenfolge der Länge der entsprechenden.|  
|address|**nvarchar(32)**|IP-Adresse dieses Knotens.|Das Format [0-255]. [0-255]. [0-255]. [0-255].|  
|is_passive|**int**|Gibt an, ob der virtuelle Computer mit dem Knoten, auf dem Server zugewiesen ausgeführt wird oder ein auf den freien Server Failover wurde.|0-Knoten-VM wird auf dem ursprünglichen Server ausgeführt werden.<br /><br /> 1-Knoten-VM wird auf den spare-Server ausgeführt.|  
|Bereich|**nvarchar(32)**|Die Region, in dem der Knoten ausgeführt wird.|"PDW", "HDINSIGHT"|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
