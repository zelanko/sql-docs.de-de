---
description: sys.dm_pdw_nodes (Transact-SQL)
title: sys.dm_pdw_nodes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b758dafadc743ffc6c51c6d1c94ab3a5ea597e2d
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037683"
---
# <a name="sysdm_pdw_nodes-transact-sql"></a>sys.dm_pdw_nodes (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält Informationen zu allen Knoten in [!INCLUDE[ssAPS](../../includes/ssaps-md.md)] . Es wird eine Zeile pro Knoten in der Appliance aufgelistet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.<br /><br /> Der Schlüssel für diese Ansicht.|In der gesamten Appliance eindeutig, unabhängig vom Typ.|  
|type|**nvarchar(32)**|Der Typ des Knotens.|"Compute", "Control", "Management"|  
|name|**nvarchar(32)**|Logischer Name des Knotens.|Eine beliebige Zeichenfolge mit entsprechender Länge.|  
|address|**nvarchar(32)**|Die IP-Adresse dieses Knotens.|Im Format [0-255]. [0-255]. [0-255]. [0-255].|  
|is_passive|**int**|Gibt an, ob der virtuelle Computer, auf dem der Knoten ausgeführt wird, auf dem zugewiesenen Server oder ein Failover auf den Ersatz Server ausgeführt wird.|0-Knoten-VM wird auf dem ursprünglichen Server ausgeführt.<br /><br /> 1-Knoten-VM wird auf dem Ersatz Server ausgeführt.|  
|region|**nvarchar(32)**|Die Region, in der der Knoten ausgeführt wird.|"PDW", "hdinsight"|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Azure Synapse Analytics und parallele Data Warehouse dynamische Verwaltungs Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
