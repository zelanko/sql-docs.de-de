---
title: Sys.dm_pdw_dms_cores (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4d0ef7c4424f4a8d1a18d3b6c7a5776e9df0f5f0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62691396"
---
# <a name="sysdmpdwdmscores-transact-sql"></a>sys.dm_pdw_dms_cores (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen über alle DMS-Dienste, die auf den Computeknoten der Appliance ausgeführt wird. Sie enthält eine Zeile für jede Dienstinstanz, die sich derzeit um eine Zeile pro Knoten befindet.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|Eindeutige numerische Id diese DMS-Core zugeordnet.<br /><br /> Der Schlüssel für diese Sicht.|Legen Sie auf die Pdw_node_id des Knotens, der diesem DMS-Kern ausgeführt wird.|  
|pdw_node_id|**int**|Die ID des Knotens, auf dem diese DMS-Dienst ausgeführt wird.|Finden Sie unter Node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(32)**|Aktuelle Status der DMS-Dienst.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 Informationen, die maximale Anzahl Zeilen, die von dieser Sicht beibehalten können, finden Sie im Abschnitt "Metadaten" in der [Kapazitätsgrenzen](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) Thema.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
