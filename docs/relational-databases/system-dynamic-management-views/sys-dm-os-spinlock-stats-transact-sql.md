---
description: sys. dm_os_spinlock_stats (Transact-SQL)
title: sys. dm_os_spinlock_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/03/2019
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_spinlock_stats_TSQL
- dm_os_spinlock_stats_TSQL
- dm_os_spinlock_stats
- sys.dm_os_spinlock_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_spinlock_stats dynamic management view
author: bluefooted
ms.author: pamela
ms.reviewer: maghan
manager: amitban
ms.openlocfilehash: 053dc2ccc68a7e0479ad1e37a181a25b0cefcc53
ms.sourcegitcommit: f7c9e562d6048f89d203d71685ba86f127d8d241
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042751"
---
# <a name="sysdm_os_spinlock_stats-transact-sql"></a>sys. dm_os_spinlock_stats (Transact-SQL)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt Informationen zu allen Spinlock-warte Vorgängen nach Typ organisiert zurück.  
  

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(256)**|Der Name des Spinlock-Typs.|  
|Stöße|**bigint**|Gibt an, wie oft ein Thread versucht, die Spinlock abzurufen, und wird blockiert, da ein anderer Thread derzeit die Spinlock-Sperre besitzt.|  
|HS|**bigint**|Gibt an, wie oft ein Thread eine Schleife ausführt, während versucht wird, das Spinlock abzurufen.|  
|spins_per_collision|**real**|Das Verhältnis von Drehungen pro Kollision.|  
|sleep_time|**bigint**|Die Zeitspanne in Millisekunden, die Threads im Fall eines Backoff im Standbymodus verbracht haben.|  
|Backoffs auch|**int**|Gibt an, wie oft ein Thread, der "spinnt" ist, den Spinlock nicht abrufen kann und den Scheduler ergibt.|  


## <a name="permissions"></a>Berechtigungen  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist die- `VIEW SERVER STATE` Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die- `VIEW DATABASE STATE` Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der  **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.    
  
## <a name="remarks"></a>Bemerkungen  
 
 sys. dm_os_spinlock_stats kann zum Identifizieren der Quelle von Spinlock-Konflikten verwendet werden. In einigen Situationen können Sie möglicherweise Spinlock-Konflikte auflösen oder verringern. Es kann jedoch Situationen geben, in denen Sie sich mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support Services in Verbindung setzen müssen.  
  
 Sie können den Inhalt von sys. dm_os_spinlock_stats zurücksetzen, indem Sie `DBCC SQLPERF` wie folgt verwenden:  
  
```  
DBCC SQLPERF ('sys.dm_os_spinlock_stats', CLEAR);  
GO  
```  
  
 Dadurch werden alle Leistungsindikatoren auf 0 zurückgesetzt.  
  
> [!NOTE]  
>  Diese Statistiken werden nicht persistent gespeichert, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu gestartet wird. Alle Daten stellen einen Gesamtwert seit dem letzten Zurücksetzen der Statistiken oder dem Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dar.  
  
## <a name="spinlocks"></a>Spinlocks  
 Ein Spinlock ist ein schlankes Synchronisierungs Objekt, das verwendet wird, um den Zugriff auf Datenstrukturen zu serialisieren, die in der Regel für kurze Zeit aufbewahrt werden. Wenn ein Thread versucht, auf eine Ressource zuzugreifen, die durch einen Spinlock geschützt ist, der von einem anderen Thread aufbewahrt wird, führt der Thread eine Schleife aus, und versucht erneut, auf die Ressource zuzugreifen, anstatt sofort den Scheduler wie bei einem Latch oder einer anderen Ressourcen Wartezeit bereitzustellen. Der Thread wird fortgesetzt, bis die Ressource verfügbar ist, oder die Schleife wird beendet. zu diesem Zeitpunkt führt der Thread den Scheduler aus und wechselt zurück in die ausführbare Warteschlange. Durch diese Vorgehensweise wird die übermäßige Thread Kontext Umschaltung verringert. Wenn jedoch ein Konflikt zwischen Spinlock vorliegt, wird möglicherweise eine beträchtliche CPU-Auslastung festgestellt.
   
 Die folgende Tabelle enthält kurze Beschreibungen einiger der gängigsten Spinlock-Typen.  
  
|SpinLock-Typ|BESCHREIBUNG|  
|-----------------|-----------------|  
|ABR|Nur interne Verwendung.|
|ADB_CACHE|Nur interne Verwendung.|
|ALLOC_CACHES_HASH|Nur interne Verwendung.|
|APPENDONLY_STORAGE|Nur interne Verwendung.|
|APRC_BACK_OFF_STATS|Nur interne Verwendung.|
|APRC_EVENT_LIST|Nur interne Verwendung.|
|APRC_QUEUE_LIST|Nur interne Verwendung.|
|APRC_VALIDATION_QUEUE_LIST|Nur interne Verwendung.|
|ASYNC_OP_ADMIN_CLIENT_REGISTRATION_LIST|Nur interne Verwendung.|
|ASYNC_OP_ADMIN_WORK_REGISTRATION_HASH_TABLE|Nur interne Verwendung.|
|Asyncstatuslist|Nur interne Verwendung.|
|BACKUP|Nur interne Verwendung.|
|BACKUP_COPY_CONTEXT|Nur interne Verwendung.|
|BACKUP_CTX|Nur interne Verwendung.|
|BASE_XACT_HASH|Nur interne Verwendung.|
|BLOCKER_ENUM|Nur interne Verwendung.|
|Bprepartition|Nur interne Verwendung.|
|Bpworkfile|Nur interne Verwendung.|
|BUF_HASH|Nur interne Verwendung.|
|BUF_LINK|Nur interne Verwendung.|
|BUF_WRITE_LOG|Nur interne Verwendung.|
|CACHEOBJ_DBG|Nur interne Verwendung.|
|Channelforceclosemanager|Nur interne Verwendung.|
|CHECK_AGGREGATE_STATE|Nur interne Verwendung.|
|CLR_HOSTTASK|Nur interne Verwendung.|
|CLR_SPIN_LOCK|Nur interne Verwendung.|
|CMED_DATABASE|Nur interne Verwendung.|
|CMED_HASH_SET|Nur interne Verwendung.|
|Columndatasetsessionlist|Nur interne Verwendung.|
|COLUMNSTORE_HASHTABLE|Nur interne Verwendung.|
|COLUMNSTOREBUILDSTATE_LIST|Nur interne Verwendung.|
|COM_INIT|Nur interne Verwendung.|
|Commit ausgeführt|Nur interne Verwendung.|
|COMPPLAN_SKELETON|Nur interne Verwendung.|
|CONNECTION_MANAGER|Nur interne Verwendung.|
|Stan|Nur interne Verwendung.|
|Csibuildmem|Nur interne Verwendung.|
|CURSOR|Nur interne Verwendung.|
|Cursor|Nur interne Verwendung.|
|Dataportconsumer|Nur interne Verwendung.|
|Dataportsourceinfocredit|Nur interne Verwendung.|
|Dataportsourceinfoqueue|Nur interne Verwendung.|
|DATASET_FREELIST|Nur interne Verwendung.|
|DBCC_CHECK|Nur interne Verwendung.|
|DBSEEDING_OPERATION|Nur interne Verwendung.|
|DBT_HASH|Nur interne Verwendung.|
|DBT_IO_LIST|Nur interne Verwendung.|
|DBTABLE|Steuert den Zugriff auf eine Datenstruktur im Arbeitsspeicher für jede Datenbank in einer SQL Server, die die Eigenschaften dieser Datenbank enthält. Weitere Informationen finden Sie in [diesem Artikel](https://techcommunity.microsoft.com/t5/SQL-Server/Improving-Concurrency-Scalability-of-SQL-Server-workload-by/ba-p/384789). |
|DEFERRED_WF_EXT_DROP|Nur interne Verwendung.|
|DEK_INSTANCE|Nur interne Verwendung.|
|DELAYED_PARTITIONED_STACK|Nur interne Verwendung.|
|Deletebitmap|Nur interne Verwendung.|
|DIAG_MANAGER|Nur interne Verwendung.|
|DIAG_OBJECT|Nur interne Verwendung.|
|DIGEST_CACHE|Nur interne Verwendung.|
|Dinpbuf|Nur interne Verwendung.|
|Directlogconsumer|Nur interne Verwendung.|
|DP_LIST|Steuert den Zugriff auf die Liste der geänderten Seiten für eine Datenbank, für die ein indirekter Prüfpunkt aktiviert ist. Weitere Informationen finden Sie in [diesem Artikel](https://techcommunity.microsoft.com/t5/SQL-Server/Indirect-Checkpoint-and-tempdb-8211-the-good-the-bad-and-the-non/ba-p/385510).|
|DROP|Nur interne Verwendung.|
|DROP_TEMPO|Nur interne Verwendung.|
|DROPPED_ALLOC_UNIT|Nur interne Verwendung.|
|DTC_HASHTABLE|Nur interne Verwendung.|
|DTT_LIST|Nur interne Verwendung.|
|ENDD_LIST|Nur interne Verwendung.|
|EXT_CACHE|Nur interne Verwendung.|
|EXTENT_ACTIVATION|Nur interne Verwendung.|
|FABRIC_DB_MGR_PTR|Nur interne Verwendung.|
|FABRIC_LOG_MANAGEMENT_INPUT_VALUE|Nur interne Verwendung.|
|FABRIC_REPLICA_TRANSPORT|Nur interne Verwendung.|
|FABRIC_TVF_DATA_CONSUMER_LIST|Nur interne Verwendung.|
|FABRIC_TVF_LOAD_LIB|Nur interne Verwendung.|
|FCB_REPLICA_SYNC|Nur interne Verwendung.|
|FGCB_PRP_FILL|Nur interne Verwendung.|
|FILE_HANDLE_CACHE|Nur interne Verwendung.|
|FILE_TABLE|Nur interne Verwendung.|
|FILESTREAM_CHUNKER|Nur interne Verwendung.|
|FREE_SPACE_CACHE_ENTRY|Nur interne Verwendung.|
|FS_CONTAINER_LIST_WITH_DELETE|Nur interne Verwendung.|
|FS_DELETED_FOLDER_CLEANUP|Nur interne Verwendung.|
|FSAGENT|Nur interne Verwendung.|
|FSGHOST_STATUS|Nur interne Verwendung.|
|FT_INIT|Nur interne Verwendung.|
|GHOST_FREE|Nur interne Verwendung.|
|GHOST_HASH|Nur interne Verwendung.|
|GLOBAL_SCHEDULER_LIST|Nur interne Verwendung.|
|GLOBAL_TRACE_FLAGS|Nur interne Verwendung.|
|Globaltrans|Nur interne Verwendung.|
|GROUP_COMMIT_FEEDBACK_LOOP|Nur interne Verwendung.|
|GUARDIAN|Nur interne Verwendung.|
|HADR_AGH_X_ACCESS|Nur interne Verwendung.|
|HADR_AR_CONTROLLER_COLLECTION|Nur interne Verwendung.|
|HADR_AR_DB_MGR|Nur interne Verwendung.|
|HADR_AR_TRANSPORT|Nur interne Verwendung.|
|HADR_COMPRESSION_MGR_POOL|Nur interne Verwendung.|
|HADR_FABRIC_FACTORY|Nur interne Verwendung.|
|HADR_PRIORITY_QUEUE|Nur interne Verwendung.|
|HADR_TRANSPORT_CONTROL|Nur interne Verwendung.|
|HADR_TRANSPORT_LIST|Nur interne Verwendung.|
|Hadrseedinglist|Nur interne Verwendung.|
|HOBT_DROPPED|Nur interne Verwendung.|
|HOBT_HASH|Nur interne Verwendung.|
|HTTP|Nur interne Verwendung.|
|HTTP_CONNCACHE|Nur interne Verwendung.|
|HTTP_ENDPOINT|Nur interne Verwendung.|
|IDENTITY|Nur interne Verwendung.|
|INDEX_CREATE|Nur interne Verwendung.|
|IO_DISPENSER_PAUSE|Nur interne Verwendung.|
|IO_RG_VOLUME_HASHTABLE|Nur interne Verwendung.|
|Ioreq|Nur interne Verwendung.|
|Issresource|Nur interne Verwendung.|
|KTM_ENLISTMENT|Nur interne Verwendung.|
|LANG_RES_LOAD|Nur interne Verwendung.|
|LIVE_TARGET_TVF|Nur interne Verwendung.|
|LOCK_FREE_LIST|Nur interne Verwendung.|
|LOCK_HASH|Schützt den Zugriff auf die Hash Tabelle des Sperren-Managers, in der Informationen zu den Sperren gespeichert werden, die in einer Datenbank gespeichert sind. Weitere Informationen finden Sie in [diesem Artikel](https://support.microsoft.com/kb/2926217).|
|LOCK_NOTIFICATION|Nur interne Verwendung.|
|LOCK_RESOURCE_ID|Nur interne Verwendung.|
|LOCK_RW_ABTX_HASH_SET|Nur interne Verwendung.|
|LOCK_RW_AGDB_HEALTH_DIAG|Nur interne Verwendung.|
|LOCK_RW_CMED_HASH_SET|Nur interne Verwendung.|
|LOCK_RW_DPT_TABLE|Nur interne Verwendung.|
|LOCK_RW_IN_ROW_TRACKER|Nur interne Verwendung.|
|LOCK_RW_LOGIN_RATE_STATS|Nur interne Verwendung.|
|LOCK_RW_PVS_PAGE_TRACKER|Nur interne Verwendung.|
|LOCK_RW_RBIO_REQ|Nur interne Verwendung.|
|LOCK_RW_SECURITY_CACHE|Nur interne Verwendung.|
|LOCK_RW_TEST|Nur interne Verwendung.|
|LOCK_RW_WPR_BUCKET|Nur interne Verwendung.|
|LOCK_SORT_STREAM|Nur interne Verwendung.|
|LOCK_SQLSATELLITE_MESSAGE|Nur interne Verwendung.|
|LOG_CONSOLIDATION|Nur interne Verwendung.|
|LOG_RG_GOVERNOR|Nur interne Verwendung.|
|LOGCACHE_ACCESS|Nur interne Verwendung.|
|Logflushq|Nur interne Verwendung.|
|Logioabq|Nur interne Verwendung.|
|Logioseqmappdingmessagequeue|Nur interne Verwendung.|
|Loglc|Nur interne Verwendung.|
|Loglfm|Nur interne Verwendung.|
|LOGON_TRIGGER_CACHE|Nur interne Verwendung.|
|LOGPOOL_HASHBUCKET|Nur interne Verwendung.|
|LOGPOOL_REFCOUNTEDOBJECT|Nur interne Verwendung.|
|LOGPOOL_SHAREDCACHEBUFFER|Nur interne Verwendung.|
|LOGPOOL_SIZEPERRESOURCEPOOL|Nur interne Verwendung.|
|LPE_BATCH|Nur interne Verwendung.|
|LPE_SESSION|Nur interne Verwendung.|
|LPE_SXTP|Nur interne Verwendung.|
|Lsid|Nur interne Verwendung.|
|Lslist|Nur interne Verwendung.|
|Lsnreflist|Nur interne Verwendung.|
|LSS_SYNC_DTC|Nur interne Verwendung.|
|MD_CHANGE_NOTIFICATION|Nur interne Verwendung.|
|MDB_REMOTE_BATCH_STATS_HASH_TABLE|Nur interne Verwendung.|
|MDB_REMOTE_SESSION_HASH_TABLE|Nur interne Verwendung.|
|MEM_MGR|Nur interne Verwendung.|
|MGR_CACHE|Nur interne Verwendung.|
|MIGRATION_BUF_LIST|Nur interne Verwendung.|
|NETCONN_ADDRESS|Nur interne Verwendung.|
|ONDEMAND_TASK|Nur interne Verwendung.|
|ONE_PROC_SIM_NODE_CONTEXT|Nur interne Verwendung.|
|ONE_PROC_SIM_NODE_CONTEXT_LIST|Nur interne Verwendung.|
|ONE_PROC_SIM_REPLICA_CONTEXT|Nur interne Verwendung.|
|ONE_PROC_SIM_SERVICE_PARTITION|Nur interne Verwendung.|
|OPT_IDX_MISS_ID|Nur interne Verwendung.|
|OPT_IDX_MISS_KEY|Nur interne Verwendung.|
|OPT_IDX_STATS|Nur interne Verwendung.|
|OPT_INFO_MGR|Nur interne Verwendung.|
|PAGE_WORKITEMLIST|Nur interne Verwendung.|
|Pagecopier|Nur interne Verwendung.|
|Parallelredocache|Nur interne Verwendung.|
|PARTITIONED_HEAP_FREE_LIST|Nur interne Verwendung.|
|PROGRESS_REPORT|Nur interne Verwendung.|
|QE_SHUTDOWN|Nur interne Verwendung.|
|QSCAN_CACHE|Nur interne Verwendung.|
|QUERY_EXEC_STATS|Nur interne Verwendung.|
|QUERY_STORE_ASYNC_PERSIST|Nur interne Verwendung.|
|QUERY_STORE_ASYNC_QUEUE_TLIST|Nur interne Verwendung.|
|QUERY_STORE_CAPTURE_POLICY_INTERVAL|Nur interne Verwendung.|
|QUERY_STORE_CAPTURE_POLICY_STATS|Nur interne Verwendung.|
|QUERY_STORE_CAPTURE_POLICY_THRESHOLD|Nur interne Verwendung.|
|QUERY_STORE_CURRENT_INTERVAL|Nur interne Verwendung.|
|QUERY_STORE_HT_CACHE|Nur interne Verwendung.|
|QUERY_STORE_LIST|Nur interne Verwendung.|
|QUERY_STORE_PLAN_COMP_AGG|Nur interne Verwendung.|
|QUERY_STORE_PLAN_LIST|Nur interne Verwendung.|
|QUERY_STORE_READ_ONLY_FLAGS|Nur interne Verwendung.|
|QUERY_STORE_SELF_AGG|Nur interne Verwendung.|
|QUERY_STORE_STMT_COMP_AGG|Nur interne Verwendung.|
|QueryExec|Nur interne Verwendung.|
|Queryscan|Nur interne Verwendung.|
|RANGE_GENERATION|Nur interne Verwendung.|
|READ_AHEAD|Nur interne Verwendung.|
|Redomgrstate|Nur interne Verwendung.|
|REMOTE_SESSION_CACHE|Nur interne Verwendung.|
|Remoteblockio|Nur interne Verwendung.|
|Remoteop|Nur interne Verwendung.|
|REPL_LOGREADER_HISTORY_CACHE|Nur interne Verwendung.|
|REPL_LOGREADER_PERDB_HISTORY_CACHE|Nur interne Verwendung.|
|Resmanager|Nur interne Verwendung.|
|RESSOURCE|Nur interne Verwendung.|
|ResQueue|Nur interne Verwendung.|
|RFS_THREAD_QUEUE|Nur interne Verwendung.|
|RG_TIMER|Nur interne Verwendung.|
|ROWGROUP_VERSIONS|Nur interne Verwendung.|
|Rpcchannelpool|Nur interne Verwendung.|
|Rpcpackage|Nur interne Verwendung.|
|Rpkrequestorcontext|Nur interne Verwendung.|
|RWLOCK_LAST|Nur interne Verwendung.|
|SATELLITE_CONNECTION|Nur interne Verwendung.|
|SBS_CLIENT_ENDPOINTS|Nur interne Verwendung.|
|SBS_CLIENT_REQUESTS|Nur interne Verwendung.|
|SBS_DISPATCH|Nur interne Verwendung.|
|SBS_PENDING|Nur interne Verwendung.|
|SBS_SERVER_XACT_TASK_PROXY|Nur interne Verwendung.|
|SBS_TRANSPORT|Nur interne Verwendung.|
|SBS_UCS_DISPATCH|Nur interne Verwendung.|
|SICHERHEIT|Nur interne Verwendung.|
|SECURITY_CACHE|Nur interne Verwendung.|
|SECURITY_FEDAUTH_AAD_BECWSCONNS|Nur interne Verwendung.|
|SEMANTIC_TICACHE|Nur interne Verwendung.|
|SEQUENCED_OBJECT|Nur interne Verwendung.|
|SEQUEUE_SIZED_THREADSAFE|Nur interne Verwendung.|
|SESSION_KILLER|Nur interne Verwendung.|
|SESSION_MANAGER|Nur interne Verwendung.|
|SESSION_SEC_CONTEXT|Nur interne Verwendung.|
|SETRANGE_SYNC|Nur interne Verwendung.|
|SHARABLE_SESSION_OBJECTS|Nur interne Verwendung.|
|SLO_INFO_LIST|Nur interne Verwendung.|
|SNI|Nur interne Verwendung.|
|SNI_NODE_PENDING_IO_QUEUE|Nur interne Verwendung.|
|Soapsessions|Nur interne Verwendung.|
|SOS_ABORT_TASK|Nur interne Verwendung.|
|SOS_ACTIVEDESCRIPTOR|Nur interne Verwendung.|
|SOS_BLOCKALLOCPARTIALLIST|Nur interne Verwendung.|
|SOS_BLOCKDESCRIPTORBUCKET|Nur interne Verwendung.|
|SOS_CACHESTORE|Synchronisiert den Zugriff auf verschiedene in-Memory-Caches in SQL Server z. b. im Plancache oder temporären Tabellencache. Ein starker Konflikt bei diesem Spinlock-Typ kann viele verschiedene Dinge bedeuten, abhängig vom spezifischen Cache, der Konflikte verursacht. Wenden Sie sich an Microsoft [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support Services, um Hilfe bei der Behebung dieses Spinlock-Typs |
|SOS_CACHESTORE_CLOCK|Nur interne Verwendung.|
|SOS_CLOCKALG_INTERNODE_SYNC|Nur interne Verwendung.|
|SOS_DEBUG_HOOK|Nur interne Verwendung.|
|SOS_DESCDATABUFFERLIST|Nur interne Verwendung.|
|SOS_LARGEPAGE_ALLOCATOR|Nur interne Verwendung.|
|SOS_MINITHREAD|Nur interne Verwendung.|
|SOS_NODE|Nur interne Verwendung.|
|SOS_OBJECT_POOL|Nur interne Verwendung.|
|SOS_OBJECT_STORE|Nur interne Verwendung.|
|SOS_OOM_CHECK|Nur interne Verwendung.|
|SOS_PHYS_PAGE_CACHE|Nur interne Verwendung.|
|SOS_RESOURCE_CLERK_LIST|Nur interne Verwendung.|
|SOS_RINGBUFFER_RECORD|Nur interne Verwendung.|
|SOS_RW|Nur interne Verwendung.|
|SOS_SATELLITE_USER_POOL|Nur interne Verwendung.|
|SOS_SCHEDULER|Nur interne Verwendung.|
|SOS_SELIST_SIZED_SLOCK|Nur interne Verwendung.|
|SOS_SUSPEND_QUEUE|Nur interne Verwendung.|
|SOS_SYSTHREAD|Nur interne Verwendung.|
|SOS_SYSTHREAD_DISPATCHER|Nur interne Verwendung.|
|SOS_TASK|Nur interne Verwendung.|
|SOS_TLIST|Nur interne Verwendung.|
|SOS_VM_LOW|Nur interne Verwendung.|
|SOS_WAIT_STATS|Nur interne Verwendung.|
|SOS_WAITABLE_ADDRESS_HASHBUCKET|Nur interne Verwendung.|
|SPIN_EVENT_MUTEX|Nur interne Verwendung.|
|SPL_DISPATCHER_LIST|Nur interne Verwendung.|
|SPL_DISPATCHER_QUEUE|Nur interne Verwendung.|
|SPL_NONYIELD_ANALYSIS|Nur interne Verwendung.|
|SPL_QUERY_STORE_CTX_INITIALIZED|Nur interne Verwendung.|
|SPL_QUERY_STORE_EXEC_STATS_AGG|Nur interne Verwendung.|
|SPL_QUERY_STORE_EXEC_STATS_READ|Nur interne Verwendung.|
|SPL_QUERY_STORE_STATS_COOKIE_CACHE|Nur interne Verwendung.|
|SPL_SOS_DISPATCHER|Nur interne Verwendung.|
|SPL_TDS_PKT_QUEUE|Nur interne Verwendung.|
|SPL_XE_BUFFER_MGR|Nur interne Verwendung.|
|SPL_XE_DISPATCHER_QUEUE|Nur interne Verwendung.|
|SPL_XE_NOTIFICATION_CALLBACK_LIST|Nur interne Verwendung.|
|SPL_XE_SESSION_EVENT_MGR|Nur interne Verwendung.|
|SPL_XE_SESSION_MGR|Nur interne Verwendung.|
|SPL_XE_SESSION_TARGET_MGR|Nur interne Verwendung.|
|SPT_PROFILE|Nur interne Verwendung.|
|SQL_MGR|Nur interne Verwendung.|
|SQL_NORM|Nur interne Verwendung.|
|SQLTRACE_FILE_BUFFER|Nur interne Verwendung.|
|SRVPROC|Nur interne Verwendung.|
|STACK_HASHER|Nur interne Verwendung.|
|Sublatch|Nur interne Verwendung.|
|Subpabsc|Nur interne Verwendung.|
|SUBPDESC_LIST|Nur interne Verwendung.|
|SVC_BROKER_CTRL|Nur interne Verwendung.|
|SVC_BROKER_DEBUG_LIST|Nur interne Verwendung.|
|SVC_BROKER_LIST|Nur interne Verwendung.|
|SVC_BROKER_OBJECT|Nur interne Verwendung.|
|SYNCPOINT_RESOURCE|Nur interne Verwendung.|
|Taskelapandexecutionmonitor|Nur interne Verwendung.|
|TDS_TVP|Nur interne Verwendung.|
|Testteam|Nur interne Verwendung.|
|Testteamexponentielle|Nur interne Verwendung.|
|Testteamexponentialtastas|Nur interne Verwendung.|
|Testteamtastas|Nur interne Verwendung.|
|TMP_SESS_KEY|Nur interne Verwendung.|
|TSQL_DEBUG|Nur interne Verwendung.|
|TXFRM_REPL|Nur interne Verwendung.|
|VDI_OPERATION|Nur interne Verwendung.|
|WINFAB_REPORT_FAULT|Nur interne Verwendung.|
|WRITE_PAGE_RECORDER|Nur interne Verwendung.|
|X_PACKET_LIST|Nur interne Verwendung.|
|X_PIPE|Nur interne Verwendung.|
|X_PIPE_DEMAND|Nur interne Verwendung.|
|X_PORT|Nur interne Verwendung.|
|XACT_LOCK_INFO|Nur interne Verwendung.|
|XACT_LOCKINFO_TASK|Nur interne Verwendung.|
|XACT_WORKSPACE|Nur interne Verwendung.|
|Xcb|Nur interne Verwendung.|
|XCB_FREE_LIST|Nur interne Verwendung.|
|XCB_HASH|Nur interne Verwendung.|
|XCHNG_TRACE|Nur interne Verwendung.|
|XDES|Nur interne Verwendung.|
|XDES_HASH|Nur interne Verwendung.|
|XDE smgr|Nur interne Verwendung.|
|Xdestablelist|Nur interne Verwendung.|
|XE_RATE_LIMITER_STRETCHDB|Nur interne Verwendung.|
|XE_SESSION_STORAGE|Nur interne Verwendung.|
|XID_ARRAY|Nur interne Verwendung.|
|XIO_BLOCKLIST|Nur interne Verwendung.|
|XIO_REQSTR|Nur interne Verwendung.|
|XIO_SEQNUMBUMP|Nur interne Verwendung.|
|Xiostats|Nur interne Verwendung.|
|XTP_RT_DATA_LIST|Nur interne Verwendung.|
|XTS_MGR|Nur interne Verwendung.|
|XVB_CSN|Nur interne Verwendung.|
|XVB_LIST|Nur interne Verwendung.|
 

  
## <a name="see-also"></a>Weitere Informationen  
 
 [DBCC SQLPERF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)   
 
 [SQL Server dynamischen Verwaltungs Sichten im Zusammenhang mit dem Betriebs System &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  

 [Wann ist Spinlock ein bedeutender Treiber der CPU-Auslastung in SQL Server?](https://techcommunity.microsoft.com/t5/SQL-Server-Support/When-is-Spinlock-a-Significant-Driver-of-CPU-utilization-in-SQL/ba-p/530142)

  
  


