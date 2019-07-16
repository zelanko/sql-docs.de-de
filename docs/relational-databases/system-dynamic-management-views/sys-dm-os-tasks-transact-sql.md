---
title: Sys. dm_os_tasks (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_tasks
- sys.dm_os_tasks_TSQL
- dm_os_tasks_TSQL
- dm_os_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_tasks dynamic management view
ms.assetid: 180a3c41-e71b-4670-819d-85ea7ef98bac
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ad4abcaf4bd22afef1d8438b2acc848606cc0733
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899727"
---
# <a name="sysdmostasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jeden aktiven Task in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz zurück.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_os_tasks**.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Speicheradresse des Objekts.|  
|**task_state**|**nvarchar(60)**|Der Status des Tasks. Die folgenden Werte sind möglich:<br /><br /> AUSSTEHEND: Warten auf einen Arbeitsthread.<br /><br /> RUNNABLE: Ausführbar, doch eines Quantums gewartet.<br /><br /> AUSGEFÜHRTE: Wird derzeit auf dem Zeitplanungsmodul ausgeführt.<br /><br /> ANGEHALTEN: Verfügt über einen Arbeitsthread, aber für ein Ereignis wartet.<br /><br /> FERTIG: Abgeschlossen.<br /><br /> SPINLOOP: Hängen in einem SpinLock festgehalten.|  
|**context_switches_count**|**int**|Anzahl der Kontextwechsel im Zeitplanungsmodul, die dieser Task abgeschlossen hat.|  
|**pending_io_count**|**int**|Anzahl der physischen E/A-Vorgänge, die dieser Task ausgeführt hat.|  
|**pending_io_byte_count**|**bigint**|Gesamtbytezahl der von diesem Task ausgeführten E/A-Vorgänge.|  
|**pending_io_byte_average**|**int**|Durchschnittliche Bytezahl der von diesem Task ausgeführten E/A-Vorgänge.|  
|**scheduler_id**|**int**|ID des übergeordneten Zeitplanungsmoduls. Dies ist ein Handle für die Zeitplanungsmodul-Informationen zu diesem Task. Weitere Informationen finden Sie unter [DM_OS_SCHEDULERS &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|**session_id**|**smallint**|ID der Sitzung, die dem Task zugeordnet ist.|  
|**exec_context_id**|**int**|Die dem Task zugeordnete Ausführungskontext-ID.|  
|**request_id**|**int**|Die ID der Anforderung des Tasks. Weitere Informationen finden Sie unter [Sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|**worker_address**|**varbinary(8)**|Speicheradresse des Arbeitsthreads, der den Task ausführt.<br /><br /> NULL = Task wartet entweder darauf, dass ein Arbeitsthread ausgeführt werden kann, oder die Ausführung des Threads wurde soeben beendet.<br /><br /> Weitere Informationen finden Sie unter [dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|**host_address**|**varbinary(8)**|Speicheradresse des Hosts.<br /><br /> 0 = Hosting wurde zum Erstellen des Tasks nicht verwendet. Dadurch kann der Host identifiziert werden, der zum Erstellen dieses Tasks verwendet wurde.<br /><br /> Weitere Informationen finden Sie unter [dm_os_hosts &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md).|  
|**parent_task_address**|**varbinary(8)**|Speicheradresse des Tasks, der dem Objekt übergeordnet ist.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] ist die Berechtigung `VIEW DATABASE STATE` in der Datenbank erforderlich.   

## <a name="examples"></a>Beispiele  
  
### <a name="a-monitoring-parallel-requests"></a>A. Überwachung paralleler Anforderungen  
 Für Anforderungen, die parallel ausgeführt werden, sehen Sie mehrere Zeilen für die gleiche Kombination (\<**Session_id**>, \< **Request_id**>). Verwenden Sie die folgende Abfrage zum Suchen der [konfigurieren Sie die Max. Grad an Parallelität-Konfigurationsoption](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) für alle aktiven Anforderungen.  
  
> [!NOTE]  
>  Ein **Request_id** innerhalb einer Sitzung eindeutig ist.  
  
```  
SELECT  
    task_address,  
    task_state,  
    context_switches_count,  
    pending_io_count,  
    pending_io_byte_count,  
    pending_io_byte_average,  
    scheduler_id,  
    session_id,  
    exec_context_id,  
    request_id,  
    worker_address,  
    host_address  
  FROM sys.dm_os_tasks  
  ORDER BY session_id, request_id;  
```  
  
### <a name="b-associating-session-ids-with-windows-threads"></a>B. Zuordnen von Sitzungs-IDs und Windows-Threads  
 Mithilfe der folgenden Abfrage lässt sich eine Sitzungs-ID einer Windows-Thread-ID zuordnen. Sie können die Leistung des Threads dann im Windows-Systemmonitor überwachen. Mit der folgenden Abfrage werden keine Informationen für ruhende Sitzungen (sleeping) zurückgegeben.  
  
```  
SELECT STasks.session_id, SThreads.os_thread_id  
  FROM sys.dm_os_tasks AS STasks  
  INNER JOIN sys.dm_os_threads AS SThreads  
    ON STasks.worker_address = SThreads.worker_address  
  WHERE STasks.session_id IS NOT NULL  
  ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
  [Dynamische Verwaltungssichten in Verbindung mit SQL Server-Betriebssystem &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


