---
title: Sys.dm_pdw_diag_processing_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f1e2180e6d22cee81c94d880eca1debaa20c8c5d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837188"
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>Sys.dm_pdw_diag_processing_stats (Transact-SQL)
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
  
  
