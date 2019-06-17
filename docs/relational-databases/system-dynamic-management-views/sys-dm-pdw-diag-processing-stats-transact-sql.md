---
title: Sys.dm_pdw_diag_processing_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f96dd7be6de1415abb8a71425b083c58e7012d9d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62691373"
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>sys.dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Zeigt Informationen im Zusammenhang mit der alle internen Diagnoseereignisse, die in vom Administrator definierten diagnosesitzungen aufgenommen werden können. Fragen Sie diese Ansicht, um der Statistik hinter die Diagnose- und Ereignisse Subsysteme dieses Laufwerk die Auffüllung für die anderen DMVs zu verstehen. Es gibt eine Gruppe von Warteschlangen für jeden Prozess auf jedem Knoten.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Appliance-Knoten, die dieses Protokoll stammt.|  
|**process_id**|**int**|Der Bezeichner des Prozesses ausgeführt wird, senden diese Statistik.|  
|**target_name**|**nvarchar(255)**|Der Name der Warteschlange.|  
|**queue_size**|**int**|Die Anzahl der Elemente in die Prozesswarteschlange geleitet. Die Größe der Warteschlange in der Regel ist 0. Eine positive Zahl gibt an, dass das System ausgelastet ist und Backlog von Ereignissen erstellt. Eine positive Anzahl in den anderen Spalten bedeutet, dass System für diese bestimmten Warteschlange beschädigt wurde und alle zugehörigen DMVs.|  
|**lost_events_count**|**bigint**|Die Anzahl verloren gegangener Ereignisse.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
