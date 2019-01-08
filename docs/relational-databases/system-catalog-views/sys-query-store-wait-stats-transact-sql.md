---
title: Sys. query_store_wait_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.query_store_wait_stats
- query_store_wait_stats
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_wait_stats catalog view
- sys.query_store_wait_stats catalog view
ms.assetid: ccf7a57c-314b-450c-bd34-70749a02784a
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 620413448f7bd6c10af2d0e7333cd9eb793ef41a
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52521254"
---
# <a name="sysquerystorewaitstats-transact-sql"></a>Sys. query_store_wait_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Enthält Informationen zu den Wartevorgang für die Abfrage an.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**wait_stats_id**|**bigint**|Der Bezeichner der Zeile, die Statistiken zu abfragewartevorgängen für ' plan_id ', Runtime_stats_interval_id, Execution_type und Wait_category darstellt. Es ist nur für die letzten Runtime Statistics Intervalle eindeutig. Für die aktuell aktiven Intervalls möglicherweise mehrere Zeilen, die Wartestatistiken für den Plan verweist ' plan_id ', mit den Ausführungstyp durch Execution_type und die Kategorie des Wartevorgangs Wait_category verhältnisschwellenwert dargestellt darstellt. In der Regel eine Zeile darstellt, der geleert werden Statistiken zu abfragewartevorgängen auf den Datenträger, während andere (s) im Speicher enthaltenen Status darstellen. Daher müssen zum Abrufen der tatsächlichen Status für jedes Intervall, Metriken zu aggregieren, Gruppieren nach ' plan_id ', Runtime_stats_interval_id, Execution_type und Wait_category. |  
|**plan_id**|**bigint**|Fremdschlüssel. Verknüpft mit [Sys. query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**bigint**|Fremdschlüssel. Verknüpft mit [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**wait_category**|**tinyint**|Wartetypen kategorisiert werden, mithilfe der folgenden Tabelle aus, und klicken Sie dann die Wartezeit aggregiert wird, für diese Kategorien warten. Verschiedene wartekategorien erfordern eine andere weitere Analyse das Problem zu beheben, aber Wartetypen aus der gleichen Kategorie Lead, ähnlich wie bei der Problembehandlung Erlebnis und Wartevorgänge Bereitstellen der betroffenen Abfrage darüber hinaus ist genau das Ausführen der Großteil der problembehebungsvorgängen erfolgreich.|
|**wait_category_desc**|**nvarchar(128)**|Die textbeschreibung des das Kategoriefeld warten finden Sie in der folgenden Tabelle.|
|**execution_type**|**tinyint**|Bestimmt die Art der Ausführung einer Abfrage:<br /><br /> 0 – reguläre Ausführung (erfolgreich abgeschlossen)<br /><br /> 3 – Client initiierter Abbruch der Ausführung<br /><br /> 4 - Ausnahme hat die Ausführung abgebrochen.|  
|**execution_type_desc**|**nvarchar(128)**|Die textbeschreibung des Type-Feld Ausführung:<br /><br /> 0 – reguläre<br /><br /> 3: abgebrochen<br /><br /> 4 - Ausnahme|  
|**total_query_wait_time_ms**|**bigint**|Insgesamt `CPU wait` Zeit für den Abfrageplan in aggregationsintervalls und warte-Kategorie (in Millisekunden gemeldet).|
|**avg_query_wait_time_ms**|**float**|Durchschnittliche Wartezeit für den Abfrageplan pro Ausführung innerhalb der Aggregation Intervall und warten Sie, Kategorie (in Millisekunden gemeldet).|
|**last_query_wait_time_ms**|**bigint**|Letzte Wartezeit für den Abfrageplan in aggregationsintervalls und warte-Kategorie (in Millisekunden gemeldet).|
|**min_query_wait_time_ms**|**bigint**|Minimale `CPU wait` Zeit für den Abfrageplan in aggregationsintervalls und warte-Kategorie (in Millisekunden gemeldet).|
|**max_query_wait_time_ms**|**bigint**|Maximale "CPU-Wartezeit" Zeit für den Abfrageplan in aggregationsintervalls und warte-Kategorie (in Millisekunden gemeldet).|
|**stdev_query_wait_time_ms**|**float**|`Query wait` Standardabweichung der Dauer für die Abfrage innerhalb eines aggregationsintervalls planen und warte-Kategorie (in Millisekunden gemeldet).|

## <a name="wait-categories-mapping-table"></a>Wartekategorien Tabelle zuordnen

"%" wird als Platzhalter verwendet.
  
|Integer-Wert|Wartekategorie|Wartetypen enthalten, in der Kategorie|  
|-----------------|---------------|-----------------|  
|**0**|**Unbekannt**|Unknown |  
|**1**|**CPU**|SOS_SCHEDULER_YIELD|
|**2**|**Arbeitsthread**|THREADPOOL|
|**3**|**Sperre**|LCK_M_ %|
|**4**|**Latch**|LATCH_ %|
|**5**|**Pufferlatch**|PAGELATCH_ %|
|**6**|**E/a-Puffer**|PAGEIOLATCH_ %|
|**7**|**Kompilierung***|RESOURCE_SEMAPHORE_QUERY_COMPILE|
|**8**|**SQL-CLR**|CLR %, SQLCLR|
|**9**|**Datenbankspiegelung**|DBMIRROR %|
|**10**|**Transaction**|XACT % "," DTC % "," TRAN_MARKLATCH_ % "," MSQL_XACT_ %, TRANSACTION_MUTEX|
|**11**|**Im Leerlauf**|SLEEP_ %, LAZYWRITER_SLEEP, SQLTRACE_BUFFER_FLUSH, SQLTRACE_INCREMENTAL_FLUSH_SLEEP, SQLTRACE_WAIT_ENTRIES, FT_IFTS_SCHEDULER_IDLE_WAIT, XE_DISPATCHER_WAIT, REQUEST_FOR_DEADLOCK_SEARCH, LOGMGR_QUEUE, ONDEMAND_TASK_QUEUE, CHECKPOINT_ WARTESCHLANGE XE_TIMER_EVENT|
|**12**|**PreEmptive**|PREEMPTIVE_ %|
|**13**|**Service Broker**|BROKER_ % **(aber nicht BROKER_RECEIVE_WAITFOR)**|
|**14**|**TRAN Protokollvorgänge**|LOGMGR, LOGBUFFER, LOGMGR_RESERVE_APPEND, LOGMGR_FLUSH, LOGMGR_PMM_LOG, CHKPT, WRITELOGF|
|**15**|**Netzwerk-e/a**|ASYNC_NETWORK_IO, NET_WAITFOR_PACKET, PROXY_NETWORK_IO, EXTERNAL_SCRIPT_NETWORK_IOF|
|**16**|**Parallelism**|CXPACKET, EXCHANGE|
|**17**|**Speicher**|RESOURCE_SEMAPHORE, CMEMTHREAD, CMEMPARTITIONED, EE_PMOLOCK, MEMORY_ALLOCATION_EXT, RESERVED_MEMORY_ALLOCATION_EXT, MEMORY_GRANT_UPDATE|
|**18**|**Wartezeit für Benutzer**|WAITFOR WAIT_FOR_RESULTS, BROKER_RECEIVE_WAITFOR|
|**19**|**Ablaufverfolgung**|TRACEWRITE, SQLTRACE_LOCK, SQLTRACE_FILE_BUFFER, SQLTRACE_FILE_WRITE_IO_COMPLETION, SQLTRACE_FILE_READ_IO_COMPLETION, SQLTRACE_PENDING_BUFFER_WRITERS, SQLTRACE_SHUTDOWN, QUERY_TRACEOUT, TRACE_EVTNOTIFF|
|**20**|**Volltextsuche**|FT_RESTART_CRAWL, VOLLTEXT-GATHERER, MSSEARCH, FT_METADATA_MUTEX, FT_IFTSHC_MUTEX, FT_IFTSISM_MUTEX, FT_IFTS_RWLOCK, FT_COMPROWSET_RWLOCK, FT_MASTER_MERGE, FT_PROPERTYLIST_CACHE, FT_MASTER_MERGE_COORDINATOR, PWAIT_RESOURCE_SEMAPHORE_FT_ PARALLEL_QUERY_SYNC|
|**21**|**Andere Datenträger-e/a**|ASYNC_IO_COMPLETION, IO_COMPLETION, BACKUPIO, WRITE_COMPLETION, IO_QUEUE_LIMIT, IO_RETRY|
|**22**|**Replikation**|SE_REPL_ % "," REPL_ % "," HADR_ % **(aber nicht HADR_THROTTLE_LOG_RATE_GOVERNOR)**, PWAIT_HADR_ %, REPLICA_WRITES, FCB_REPLICA_WRITE, FCB_REPLICA_READ, PWAIT_HADRSIM|
|**23**|**Rate der Protokollkontrolle**|LOG_RATE_GOVERNOR, POOL_LOG_RATE_GOVERNOR, HADR_THROTTLE_LOG_RATE_GOVERNOR, INSTANCE_LOG_RATE_GOVERNOR|

**Kompilierung** Warte-Kategorie wird derzeit nicht unterstützt.

## <a name="permissions"></a>Berechtigungen

 Erfordert die **VIEW DATABASE STATE** Berechtigung.  
  
## <a name="see-also"></a>Siehe auch

- [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)
- [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)
- [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)
- [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)
- [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)
- [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)
- [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)
- [Query Store gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
