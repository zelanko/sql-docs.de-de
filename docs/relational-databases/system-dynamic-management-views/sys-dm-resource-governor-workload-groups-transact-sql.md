---
title: Sys. dm_resource_governor_workload_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups
- sys.dm_resource_governor_workload_groups_TSQL
- dm_resource_governor_workload_groups
- dm_resource_governor_workload_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_workload_groups dynamic management view
ms.assetid: f63c4914-1272-43ef-b135-fe1aabd953e0
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1f70e500e47534bd89162828715db1887491d0b3
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43067740"
---
# <a name="sysdmresourcegovernorworkloadgroups-transact-sql"></a>sys.dm_resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Statistiken zu Arbeitsauslastungsgruppen sowie die aktuelle Konfiguration der Arbeitsauslastungsgruppen im Arbeitsspeicher zurück. Diese Sicht kann mit sys.dm_resource_governor_resource_pools verknüpft werden, um den Ressourcenpoolnamen abzurufen.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_resource_governor_workload_groups**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|group_id|**int**|ID der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|  
|NAME|**sysname**|Name der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|  
|pool_id|**int**|Die ID des Ressourcenpools an. Lässt keine NULL-Werte zu.|  
|external_pool_id|**int**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Die ID des externen Ressourcenpools. Lässt keine NULL-Werte zu.|  
|statistics_start_time|**datetime**|Uhrzeit, zu der die Statistikauflistung für die Arbeitsauslastungsgruppe zurückgesetzt wurde. Lässt keine NULL-Werte zu.|  
|total_request_count|**bigint**|Kumulierte Anzahl vervollständigter Anforderungen in der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|  
|total_queued_request_count|**bigint**|Kumulierte Anzahl von Anforderungen, die in die Warteschlange gestellt wurden, nachdem die GROUP_MAX_REQUESTS-Grenze erreicht wurde. Lässt keine NULL-Werte zu.|  
|active_request_count|**int**|Die aktuelle Anforderungsanzahl. Lässt keine NULL-Werte zu.|  
|queued_request_count|**int**|Die Anzahl der zurzeit in der Warteschlange befindlichen Anforderungen. Lässt keine NULL-Werte zu.|  
|total_cpu_limit_violation_count|**bigint**|Kumulierte Anzahl von Anforderungen, die die CPU-Grenze übersteigen. Lässt keine NULL-Werte zu.|  
|total_cpu_usage_ms|**bigint**|Kumulierte CPU-Verwendung dieser Arbeitsauslastungsgruppe in Millisekunden. Lässt keine NULL-Werte zu.|  
|max_request_cpu_time_ms|**bigint**|Maximale CPU-Nutzung für eine einzelne Anforderung in Millisekunden. Lässt keine NULL-Werte zu.<br /><br /> **Hinweis:** sieht einen gemessenen Wert, im Gegensatz zu Request_max_cpu_time_sec, dies ist eine konfigurierbare Einstellung. Weitere Informationen finden Sie unter [CPU Threshold Exceeded (Ereignisklasse)](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).|  
|blocked_task_count|**int**|Aktuelle Anzahl blockierter Tasks. Lässt keine NULL-Werte zu.|  
|total_lock_wait_count|**bigint**|Kumulierte Anzahl von Sperrwartezeiten, die aufgetreten sind. Lässt keine NULL-Werte zu.|  
|total_lock_wait_time_ms|**bigint**|Kumulierte Summe der verstrichenen Zeit einer Sperre in Millisekunden. Lässt keine NULL-Werte zu.|  
|total_query_optimization_count|**bigint**|Kumulierte Anzahl von Abfrageoptimierungen in dieser Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|  
|total_suboptimal_plan_generation_count|**bigint**|Kumulierte Anzahl von nicht optimalen Planerstellungen, die aufgrund des nicht ausreichenden Arbeitsspeichers in dieser Arbeitsauslastungsgruppe aufgetreten sind. Lässt keine NULL-Werte zu.|  
|total_reduced_memgrant_count|**bigint**|Kumulierte Anzahl von Arbeitsspeicherzuweisungen, die die maximale Abfragegrößenbeschränkung erreicht haben. Lässt keine NULL-Werte zu.|  
|max_request_grant_memory_kb|**bigint**|Maximale Arbeitsspeicherzuweisungsgröße einer einzelnen Anforderung, seit die Statistik zurückgesetzt wurde, in Kilobyte. Lässt keine NULL-Werte zu.|  
|active_parallel_thread_count|**bigint**|Aktuelle Anzahl der parallelen Thread-Auslastung. Lässt keine NULL-Werte zu.|  
|importance|**sysname**|Aktueller Konfigurationswert für die relative Wichtigkeit einer Anforderung in dieser Arbeitsauslastungsgruppe. Ist eine der folgenden, wobei Medium wird der Standardwert: niedrig, Mittel oder hoch.<br /><br /> Lässt keine NULL-Werte zu.|  
|request_max_memory_grant_percent|**int**|Aktuelle Einstellung der maximalen Arbeitsspeicherzuweisung in Prozent für eine einzelne Anforderung. Lässt keine NULL-Werte zu.|  
|request_max_cpu_time_sec|**int**|Aktuelle Einstellung für den maximalen CPU-Nutzungsgrenzwert für eine einzelne Anforderung in Sekunden. Lässt keine NULL-Werte zu.|  
|request_memory_grant_timeout_sec|**int**|Aktuelle Einstellung für das Timeout der Arbeitsspeicherzuweisung für eine einzelne Anforderung in Sekunden. Lässt keine NULL-Werte zu.|  
|group_max_requests|**int**|Aktuelle Einstellung für die maximale Anzahl gleichzeitiger Anforderungen. Lässt keine NULL-Werte zu.|  
|max_dop|**int**|Maximaler Grad der Parallelität für die Arbeitsauslastungsgruppe. Der Standardwert 0 verwendet globale Einstellungen. Lässt keine NULL-Werte zu.|  
|pdw_node_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="remarks"></a>Hinweise  
 Diese dynamische Verwaltungssicht zeigt die Konfiguration im Arbeitsspeicher an. Verwenden Sie die Katalogsicht sys.resource_governor_workload_groups, um die gespeicherten Konfigurationsmetadaten anzuzeigen.  
  
 Wenn ALTER RESOURCE GOVERNOR RESET STATISTICS erfolgreich ausgeführt wird, werden die folgenden Zähler zurückgesetzt: Statistics_start_time, Total_request_count, Total_queued_request_count, Total_cpu_limit_violation_count, Total_cpu_usage_ms, Max_request_ Cpu_time_ms, Total_lock_wait_count, Total_lock_wait_time_ms, Total_query_optimization_count, Total_suboptimal_plan_generation_count, Total_reduced_memgrant_count und Max_request_grant_memory_kb. Statistics_start_time wird auf das aktuelle Systemdatum und die Uhrzeit festgelegt, die anderen Zähler werden auf 0 (null) festgelegt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Sys. dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  



