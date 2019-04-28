---
title: Sys.dm_exec_dms_workers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_dms_workers management view
- sys.dm_exec_dms_workers management view
ms.assetid: f468da29-78c3-4f10-8a3c-17905bbf46f2
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8a31b03208eba573fc6bd50f2348733ef0a07c2b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013325"
---
# <a name="sysdmexecdmsworkers-transact-sql"></a>sys.dm_exec_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen Workern, die DMS-Schritte.  
  
 In dieser Ansicht wird angezeigt, die Daten für die letzten 1000 Anforderungen und die aktiven Anforderungen. aktive Anforderungen haben immer die Daten in dieser Ansicht vorhanden.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Fragen Sie, dass der DMS-Worker Teil of.request_id, Step_index, und Dms_step_index bilden den Schlüssel für diese Sicht.||  
|step_index|**int**|Fragen Sie Schritt ab, den der DMS-Worker angehört.|Finden Sie unter schrittindex in [dm_exec_distributed_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Schritt in den DMS-Plan, den dieser Arbeitsthread ausgeführt wird.|See [sys.dm_exec_dms_workers (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)|  
|compute_node_id|**int**|Knoten, der die Worker ausgeführt wird.|Finden Sie unter [dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|**int**|||  
|Typ|**nvarcha(32)**|||  
|status|**nvarchar(32)**|Status dieses Schritts|'Pending', 'Running', 'Complete', 'Failed', 'UndoFailed', 'PendingCancel', 'Cancelled', 'Undone', 'Aborted'|  
|bytes_per_sec|**bigint**|||  
|bytes_processed|**bigint**|||  
|rows_processed|**bigint**|||  
|start_time|**datetime**|Zeitpunkt, an dem der Schritt die Ausführung gestartet|Kleiner oder gleich der aktuellen Zeit und größer oder gleich End_compile_time der Abfrage zu der dieser Schritt gehört.|  
|end_time|**datetime**|Zeitpunkt, an dem dieser Schritt ausgeführt wurden, wurde abgebrochen oder fehlerhaft.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich Start_time, für die Schritte, die derzeit in der Ausführung auf NULL festgelegt oder in die Warteschlange eingereiht.|  
|total_elapsed_time|**int**|Gesamtmenge der Mal, wenn der abfrageschritt, in Millisekunden ausgeführt wurde|Zwischen 0 und der Unterschied zwischen End_time und Start_time. 0 für die Schritte in Warteschlange.|  
|cpu_time|**bigint**|||  
|query_time|**int**|||  
|buffers_available|**int**|||  
|dms_cpid|**int**|||  
|sql_spid|**int**|||  
|error_id|**nvarchar(36)**|||  
|source_info|**nvarchar(4000)**|||  
|destination_info|**nvarchar(4000)**|||  
|Befehl|**nvarchar(4000)**|||  
  
## <a name="see-also"></a>Siehe auch  
 [PolyBase-Problembehandlung mit dynamischen Verwaltungssichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
