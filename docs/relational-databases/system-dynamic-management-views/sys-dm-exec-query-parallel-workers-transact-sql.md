---
title: Sys.dm_exec_query_parallel_workers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_parallel_workers_TSQL
- dm_exec_query_parallel_workers
- sys.dm_exec_query_parallel_workers_TSQL
- sys.dm_exec_query_parallel_workers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_parallel_workers dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9f
author: pelopes
ms.author: pelopes
manager: ajayj
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b1ff6dee668cd6bc93d9a3c74ae4b3e25cbe99be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47598129"
---
# <a name="sysdmexecqueryparallelworkers-transact-sql"></a>Sys.dm_exec_query_parallel_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Gibt zurück Worker Verfügbarkeitsinformationen pro Knoten.  
  
|Name|Datentyp|Description|  
|----------|---------------|-----------------|  
|**node_id**|**int**|NUMA-Knoten-ID.|  
|**scheduler_count**|**int**|Die Anzahl der Planer auf diesem Knoten.|  
|**max_worker_count**|**int**|Maximale Anzahl von Workern für parallele Abfragen.|  
|**reserved_worker_count**|**int**|Anzahl von Workern, die von parallelen Abfragen reserviert sowie die Anzahl der wichtigsten Worker von allen Anforderungen verwendet.| 
|**free_worker_count**|**int**|Anzahl von Arbeitsthreads, die für Aufgaben zur Verfügung.<br /><br />**Hinweis:** jede eingehende Anforderung verarbeitet, mindestens 1 Worker, die von der Anzahl der freien Arbeitsthreads subtrahiert wird.  Es ist möglich, dass die workeranzahl der freien auf einem stark ausgelasteten Server eine negative Zahl sein kann.| 
|**used_worker_count**|**int**|Anzahl von Arbeitsthreads, die von parallelen Abfragen verwendet.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   
 
## <a name="examples"></a>Beispiele  
  
### <a name="a-viewing-current-parallel-worker-availability"></a>A. Anzeigen des aktuellen parallelen Workerthread-Verfügbarkeit  

```sql 
SELECT * FROM sys.dm_exec_query_parallel_workers;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Ausführung bezogene dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)
