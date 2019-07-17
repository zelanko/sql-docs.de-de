---
title: Sys. dm_os_spinlock_stats (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: eae0057441fe6bc356c7cea6c1e6ded829bbb9e6
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265687"
---
# <a name="sysdmosspinlockstats-transact-sql"></a>sys.dm_os_spinlock_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt Informationen zu allen Spinlock-Wartevorgängen, die nach Typ strukturiert.  
  

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|NAME|**nvarchar(256)**|Der Name des Spinlock-Typs.|  
|Konflikte|**bigint**|Wie oft ein Thread versucht, für den Spinlock und blockiert, weil ein anderer thread zurzeit enthält das Spinlock.|  
|Führt Spin-Vorgänge|**bigint**|Die Anzahl der Versuche, die ein Thread führt eine Schleife, bei dem Versuch, den Spinlock abzurufen.|  
|spins_per_collision|**real**|Das Verhältnis von Fäden pro Konflikt.|  
|sleep_time|**bigint**|Die Zeitspanne in Millisekunden, die Threads benötigt im Falle einer Wartezeit im Standbymodus.|  
|Backoffs auch|**int**|Die Anzahl wie oft ein Thread, der "rotierender" ein Fehler auftritt, das Spinlock abzurufen und im Zeitplanungsmodul.|  


## <a name="permissions"></a>Berechtigungen  
Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarife, erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank. Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard und Basic-Version, erfordert die **Serveradministrator** oder **Azure Active Directory-Administrator** Konto.    
  
## <a name="remarks"></a>Hinweise  
 
 Sys. dm_os_spinlock_stats kann verwendet werden, um die Quelle der Spinlock-Konflikte zu identifizieren. In einigen Fällen können Sie möglicherweise lösen oder Reduzieren von Spinlock-Konflikte. Es kann jedoch Situationen geben, in denen Sie sich mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support Services in Verbindung setzen müssen.  
  
 Sie können den Inhalt der Sys. dm_os_spinlock_stats zurücksetzen, indem Sie mithilfe von `DBCC SQLPERF` wie folgt:  
  
```  
DBCC SQLPERF ('sys.dm_os_spinlock_stats', CLEAR);  
GO  
```  
  
 Dadurch werden alle Leistungsindikatoren auf 0 zurückgesetzt.  
  
> [!NOTE]  
>  Diese Statistiken werden nicht persistent gespeichert, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu gestartet wird. Alle Daten stellen einen Gesamtwert seit dem letzten Zurücksetzen der Statistiken oder dem Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dar.  
  
## <a name="spinlocks"></a>Spinlocks  
 Ein Spinlock ist ein lightweight-Synchronisierungsobjekt verwendet, um den Zugriff auf die Datenstrukturen serialisiert, die anschließend in der Regel für einen kurzen Zeitraum aufrechterhalten werden. Wenn ein Thread versucht, die Zugriff auf eine Ressource, die von einem SpinLock festgehalten, die von einem anderen Thread gehalten wird geschützt, der Thread wird Ausführen einer Schleife, oder "starten" und versuchen Sie es noch Mal, Zugriff auf die Ressource sofort zurückgegeben wird, den Scheduler als ein Objekt oder eine andere Ressource Warte. Der Thread weiterhin sich drehende, bis die Ressource verfügbar ist, oder die Schleife abgeschlossen wird, an diesem Punkt der Thread den Scheduler ergeben, und wechseln Sie zurück, in der ausführbaren Warteschlange. Diese Vorgehensweise verringert übermäßig viele Threads wechseln des Kontexts, wenn bei einem SpinLock festgehalten Konflikte hoch ist, erhebliche CPU-Auslastung kann jedoch angezeigt werden.
   
 Die folgende Tabelle enthält kurze Beschreibungen der einige der am häufigsten verwendeten Spinlock-Typen.  
  
|Spinlocktyp|Beschreibung|  
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
|ASYNCSTATSLIST|Nur interne Verwendung.|
|BACKUP|Nur interne Verwendung.|
|BACKUP_COPY_CONTEXT|Nur interne Verwendung.|
|BACKUP_CTX|Nur interne Verwendung.|
|BASE_XACT_HASH|Nur interne Verwendung.|
|BLOCKER_ENUM|Nur interne Verwendung.|
|BPREPARTITION|Nur interne Verwendung.|
|BPWORKFILE|Nur interne Verwendung.|
|BUF_HASH|Nur interne Verwendung.|
|BUF_LINK|Nur interne Verwendung.|
|BUF_WRITE_LOG|Nur interne Verwendung.|
|CACHEOBJ_DBG|Nur interne Verwendung.|
|CHANNELFORCECLOSEMANAGER|Nur interne Verwendung.|
|CHECK_AGGREGATE_STATE|Nur interne Verwendung.|
|CLR_HOSTTASK|Nur interne Verwendung.|
|CLR_SPIN_LOCK|Nur interne Verwendung.|
|CMED_DATABASE|Nur interne Verwendung.|
|CMED_HASH_SET|Nur interne Verwendung.|
|COLUMNDATASETSESSIONLIST|Nur interne Verwendung.|
|COLUMNSTORE_HASHTABLE|Nur interne Verwendung.|
|COLUMNSTOREBUILDSTATE_LIST|Nur interne Verwendung.|
|COM_INIT|Nur interne Verwendung.|
|KEIN COMMIT AUSGEFÜHRT|Nur interne Verwendung.|
|COMPPLAN_SKELETON|Nur interne Verwendung.|
|CONNECTION_MANAGER|Nur interne Verwendung.|
|STELLT EINE VERBINDUNG HER|Nur interne Verwendung.|
|CSIBUILDMEM|Nur interne Verwendung.|
|CURSOR|Nur interne Verwendung.|
|CURSQL|Nur interne Verwendung.|
|DATAPORTCONSUMER|Nur interne Verwendung.|
|DATAPORTSOURCEINFOCREDIT|Nur interne Verwendung.|
|DATAPORTSOURCEINFOQUEUE|Nur interne Verwendung.|
|DATASET_FREELIST|Nur interne Verwendung.|
|DBCC_CHECK|Nur interne Verwendung.|
|DBSEEDING_OPERATION|Nur interne Verwendung.|
|DBT_HASH|Nur interne Verwendung.|
|DBT_IO_LIST|Nur interne Verwendung.|
|DBTABLE|Steuert den Zugriff auf eine Struktur in-Memory-Daten für jede Datenbank in einer SQL-Server, die die Eigenschaften für diese Datenbank enthält. Finden Sie unter [in diesem Artikel](https://techcommunity.microsoft.com/t5/SQL-Server/Improving-Concurrency-Scalability-of-SQL-Server-workload-by/ba-p/384789) für Weitere Informationen. |
|DEFERRED_WF_EXT_DROP|Nur interne Verwendung.|
|DEK_INSTANCE|Nur interne Verwendung.|
|DELAYED_PARTITIONED_STACK|Nur interne Verwendung.|
|DELETEBITMAP|Nur interne Verwendung.|
|DIAG_MANAGER|Nur interne Verwendung.|
|DIAG_OBJECT|Nur interne Verwendung.|
|DIGEST_CACHE|Nur interne Verwendung.|
|DINPBUF|Nur interne Verwendung.|
|DIRECTLOGCONSUMER|Nur interne Verwendung.|
|DP_LIST|Steuert den Zugriff auf die Liste der modifizierten Seiten für eine Datenbank, die indirekten Prüfpunkt aktiviert wurde. Finden Sie unter [in diesem Artikel](https://techcommunity.microsoft.com/t5/SQL-Server/Indirect-Checkpoint-and-tempdb-8211-the-good-the-bad-and-the-non/ba-p/385510) für Weitere Informationen.|
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
|GLOBALTRANS|Nur interne Verwendung.|
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
|HADRSEEDINGLIST|Nur interne Verwendung.|
|HOBT_DROPPED|Nur interne Verwendung.|
|HOBT_HASH|Nur interne Verwendung.|
|HTTP|Nur interne Verwendung.|
|HTTP_CONNCACHE|Nur interne Verwendung.|
|HTTP_ENDPOINT|Nur interne Verwendung.|
|IDENTITY|Nur interne Verwendung.|
|INDEX_CREATE|Nur interne Verwendung.|
|IO_DISPENSER_PAUSE|Nur interne Verwendung.|
|IO_RG_VOLUME_HASHTABLE|Nur interne Verwendung.|
|IOREQ|Nur interne Verwendung.|
|ISSRESOURCE|Nur interne Verwendung.|
|KTM_ENLISTMENT|Nur interne Verwendung.|
|LANG_RES_LOAD|Nur interne Verwendung.|
|LIVE_TARGET_TVF|Nur interne Verwendung.|
|LOCK_FREE_LIST|Nur interne Verwendung.|
|LOCK_HASH|Schützt den Zugriff auf die Sperren-Manager-Hash-Tabelle, die Informationen zu den Sperren in einer Datenbank gespeichert. Finden Sie unter [in diesem Artikel](https://support.microsoft.com/kb/2926217) für Weitere Informationen.|
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
|LOGFLUSHQ|Nur interne Verwendung.|
|LOGIOSEQ|Nur interne Verwendung.|
|LOGIOSEQMAPPENDINGMESSAGEQUEUE|Nur interne Verwendung.|
|LOGLC|Nur interne Verwendung.|
|LOGLFM|Nur interne Verwendung.|
|LOGON_TRIGGER_CACHE|Nur interne Verwendung.|
|LOGPOOL_HASHBUCKET|Nur interne Verwendung.|
|LOGPOOL_REFCOUNTEDOBJECT|Nur interne Verwendung.|
|LOGPOOL_SHAREDCACHEBUFFER|Nur interne Verwendung.|
|LOGPOOL_SIZEPERRESOURCEPOOL|Nur interne Verwendung.|
|LPE_BATCH|Nur interne Verwendung.|
|LPE_SESSION|Nur interne Verwendung.|
|LPE_SXTP|Nur interne Verwendung.|
|LSID|Nur interne Verwendung.|
|LSLIST|Nur interne Verwendung.|
|LSNREFLIST|Nur interne Verwendung.|
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
|PAGECOPIER|Nur interne Verwendung.|
|PARALLELREDOCACHE|Nur interne Verwendung.|
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
|QUERYEXEC|Nur interne Verwendung.|
|QUERYSCAN|Nur interne Verwendung.|
|RANGE_GENERATION|Nur interne Verwendung.|
|READ_AHEAD|Nur interne Verwendung.|
|REDOMGRSTATE|Nur interne Verwendung.|
|REMOTE_SESSION_CACHE|Nur interne Verwendung.|
|REMOTEBLOCKIO|Nur interne Verwendung.|
|REMOTEOP|Nur interne Verwendung.|
|REPL_LOGREADER_HISTORY_CACHE|Nur interne Verwendung.|
|REPL_LOGREADER_PERDB_HISTORY_CACHE|Nur interne Verwendung.|
|RESMANAGER|Nur interne Verwendung.|
|RESSOURCE|Nur interne Verwendung.|
|RESQUEUE|Nur interne Verwendung.|
|RFS_THREAD_QUEUE|Nur interne Verwendung.|
|RG_TIMER|Nur interne Verwendung.|
|ROWGROUP_VERSIONS|Nur interne Verwendung.|
|RPCCHANNELPOOL|Nur interne Verwendung.|
|RPCPACKAGE|Nur interne Verwendung.|
|RPCREQUESTORCONTEXT|Nur interne Verwendung.|
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
|SOAPSESSIONS|Nur interne Verwendung.|
|SOS_ABORT_TASK|Nur interne Verwendung.|
|SOS_ACTIVEDESCRIPTOR|Nur interne Verwendung.|
|SOS_BLOCKALLOCPARTIALLIST|Nur interne Verwendung.|
|SOS_BLOCKDESCRIPTORBUCKET|Nur interne Verwendung.|
|SOS_CACHESTORE|Synchronisiert den Zugriff auf verschiedene in-Memory-Caches in SQL Server wie z. B. den Plancache oder temporäre Tabellencache. Schwerwiegende Konflikte für diesen spinlocktyp kann viele verschiedene Dinge je nach den spezifischen Cache bedeuten, die in Konflikt. Wenden Sie sich an [!INCLUDE[msCoName](../../includes/msconame-md.md)] Microsoft Support Services, um Hilfe zur Problembehandlung dieses Spinlock-Typs. |
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
|SUBLATCH|Nur interne Verwendung.|
|SUBPDESC|Nur interne Verwendung.|
|SUBPDESC_LIST|Nur interne Verwendung.|
|SVC_BROKER_CTRL|Nur interne Verwendung.|
|SVC_BROKER_DEBUG_LIST|Nur interne Verwendung.|
|SVC_BROKER_LIST|Nur interne Verwendung.|
|SVC_BROKER_OBJECT|Nur interne Verwendung.|
|SYNCPOINT_RESOURCE|Nur interne Verwendung.|
|TaskElapsedExecutionMonitor|Nur interne Verwendung.|
|TDS_TVP|Nur interne Verwendung.|
|TESTTEAM|Nur interne Verwendung.|
|TESTTEAMEXPONENTIAL|Nur interne Verwendung.|
|TESTTEAMEXPONENTIALTASTAS|Nur interne Verwendung.|
|TESTTEAMTASTAS|Nur interne Verwendung.|
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
|XCB|Nur interne Verwendung.|
|XCB_FREE_LIST|Nur interne Verwendung.|
|XCB_HASH|Nur interne Verwendung.|
|XCHNG_TRACE|Nur interne Verwendung.|
|XDES|Nur interne Verwendung.|
|XDES_HASH|Nur interne Verwendung.|
|XDESMGR|Nur interne Verwendung.|
|XDESTABLELIST|Nur interne Verwendung.|
|XE_RATE_LIMITER_STRETCHDB|Nur interne Verwendung.|
|XE_SESSION_STORAGE|Nur interne Verwendung.|
|XID_ARRAY|Nur interne Verwendung.|
|XIO_BLOCKLIST|Nur interne Verwendung.|
|XIO_REQSTR|Nur interne Verwendung.|
|XIO_SEQNUMBUMP|Nur interne Verwendung.|
|XIOSTATS|Nur interne Verwendung.|
|XTP_RT_DATA_LIST|Nur interne Verwendung.|
|XTS_MGR|Nur interne Verwendung.|
|XVB_CSN|Nur interne Verwendung.|
|XVB_LIST|Nur interne Verwendung.|
 

  
## <a name="see-also"></a>Siehe auch  
 
 [DBCC SQLPERF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)   
 
 [Dynamische Verwaltungssichten in Verbindung mit SQL Server-Betriebssystem &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  

 [Wann ist Spinlock eine erhebliche Treiber der CPU-Auslastung in SQL Server?](https://techcommunity.microsoft.com/t5/SQL-Server-Support/When-is-Spinlock-a-Significant-Driver-of-CPU-utilization-in-SQL/ba-p/530142)

 [Diagnose und Behebung von Spinlock-Konflikte für SQLServer](https://www.microsoft.com/download/details.aspx?id=26666)
  
  


