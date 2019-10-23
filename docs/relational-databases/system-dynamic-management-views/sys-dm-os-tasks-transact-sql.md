---
title: sys. DM _os_tasks (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 69fb7b1e0d9f98ec7d00441613a8887a81c4567c
ms.sourcegitcommit: aece9f7db367098fcc0c508209ba243e05547fe1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72260425"
---
# <a name="sysdm_os_tasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jeden aktiven Task in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz zurück. Weitere Informationen zu Aufgaben finden Sie im [Handbuch zur Thread-und Task Architektur](../../relational-databases/thread-and-task-architecture-guide.md).
  
> [!NOTE]  
> Verwenden Sie den Namen **sys. DM _pdw_nodes_os_tasks**, um dies von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] aus aufzurufen.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Speicheradresse des Objekts.|  
|**task_state**|**nvarchar(60)**|Der Status des Tasks. Die folgenden Werte sind möglich:<br /><br /> AUSSTEHENDE Warten auf einen Arbeitsthread.<br /><br /> AUSFÜHRBAREN Runnable, aber wartet auf den Empfang eines Quantums.<br /><br /> DRÄNGT Wird derzeit auf dem Zeitplanungsmodul ausgeführt.<br /><br /> GESPERRT Verfügt über einen Worker, wartet jedoch auf ein Ereignis.<br /><br /> AUSGEFÜHRT Abgeschlossenen.<br /><br /> SPINLOOP An einem Spinlock hängen.|  
|**context_switches_count**|**int**|Anzahl der Kontextwechsel im Zeitplanungsmodul, die dieser Task abgeschlossen hat.|  
|**pending_io_count**|**int**|Anzahl der physischen E/A-Vorgänge, die dieser Task ausgeführt hat.|  
|**pending_io_byte_count**|**bigint**|Gesamtbytezahl der von diesem Task ausgeführten E/A-Vorgänge.|  
|**pending_io_byte_average**|**int**|Durchschnittliche Bytezahl der von diesem Task ausgeführten E/A-Vorgänge.|  
|**scheduler_id**|**int**|ID des übergeordneten Zeitplanungsmoduls. Dies ist ein Handle für die Zeitplanungsmodul-Informationen zu diesem Task. Weitere Informationen finden Sie unter [sys. DM _os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|**session_id**|**smallint**|ID der Sitzung, die dem Task zugeordnet ist.|  
|**exec_context_id**|**int**|Die dem Task zugeordnete Ausführungskontext-ID.|  
|**request_id**|**int**|Die ID der Anforderung des Tasks. Weitere Informationen finden Sie unter [sys. DM _exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|**worker_address**|**varbinary(8)**|Speicheradresse des Arbeitsthreads, der den Task ausführt.<br /><br /> NULL = Task wartet entweder darauf, dass ein Arbeitsthread ausgeführt werden kann, oder die Ausführung des Threads wurde soeben beendet.<br /><br /> Weitere Informationen finden Sie unter [sys. DM _os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|**host_address**|**varbinary(8)**|Speicheradresse des Hosts.<br /><br /> 0 = Hosting wurde zum Erstellen des Tasks nicht verwendet. Dadurch kann der Host identifiziert werden, der zum Erstellen dieses Tasks verwendet wurde.<br /><br /> Weitere Informationen finden Sie unter [sys. DM _os_hosts &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md).|  
|**parent_task_address**|**varbinary(8)**|Speicheradresse des Tasks, der dem Objekt übergeordnet ist.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="permissions"></a>Berechtigungen
Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist `VIEW SERVER STATE`-Berechtigung erforderlich.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Ebenen ist die `VIEW DATABASE STATE`-Berechtigung in der Datenbank erforderlich. Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]-Tarifen (Standard und Basic) ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   

## <a name="examples"></a>Beispiele  
  
### <a name="a-monitoring-parallel-requests"></a>A. Überwachung paralleler Anforderungen  
 Bei Anforderungen, die parallel ausgeführt werden, werden mehrere Zeilen für die gleiche Kombination von (\<**session_id**>, \<**request_id**>) angezeigt. Verwenden Sie die folgende Abfrage, um die [Server Konfigurations Option max. Grad an Parallelität konfigurieren](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) für alle aktiven Anforderungen zu finden.  
  
> [!NOTE]  
>  Ein **request_id** -Wert ist innerhalb einer Sitzung eindeutig.  
  
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
[SQL Server mit dem Betriebs System verbundene dynamische &#40;Verwaltungs Sichten Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
[Handbuch zur Thread- und Taskarchitektur](../../relational-databases/thread-and-task-architecture-guide.md)     
  


