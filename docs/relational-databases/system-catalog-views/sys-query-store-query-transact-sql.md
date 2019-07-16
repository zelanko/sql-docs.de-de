---
title: query_store_query (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_QUERY
- SYS.QUERY_STORE_QUERY_TSQL
- SYS.QUERY_STORE_QUERY
- QUERY_STORE_QUERY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_query catalog view
- sys.query_store_query catalog view
ms.assetid: bdee149e-7556-4fc3-8242-925dd4b7b6ac
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d5b7eea64a807af96094767ef5aca00167d5946c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067965"
---
# <a name="sysquerystorequery-transact-sql"></a>query_store_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Enthält Informationen über die Abfrage und die zugeordneten gesamte aggregierte Laufzeit-Ausführungsstatistik.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**query_id**|**bigint**|Der Primärschlüssel.|  
|**query_text_id**|**bigint**|Fremdschlüssel. Verknüpft mit [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|  
|**context_settings_id**|**bigint**|Fremdschlüssel. Verknüpft mit [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**object_id**|**bigint**|ID des Datenbankobjekts, das die Abfrage angehört (gespeicherte Prozedur, Trigger, CLR-UDF/UDAgg, usw..). 0, wenn die Abfrage nicht als Teil eines Datenbankobjekts (Ad-hoc-Abfrage) ausgeführt wird.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**batch_sql_handle**|**varbinary(64)**|ID des Anweisungsbatches der Abfrage stammt. Nur aufgefüllt, wenn die Abfrage verweist, temporäre Tabellen oder Tabellenvariablen auf.<br/>**Hinweis**: Azure SQL Data Warehouse gibt stets *NULL*.|  
|**query_hash**|**binary(8)**|MD5-Hash, der die einzelne Abfrage, die basierend auf der logischen Abfragestruktur. Enthält Hinweise für den Abfrageoptimierer an.|  
|**is_internal_query**|**bit**|Die Abfrage wurde intern generiert.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**query_parameterization_type**|**tinyint**|Die Art der Parametrisierung:<br /><br /> 0 - keine<br /><br /> 1 – Benutzer<br /><br /> 2 – einfach<br /><br /> 3 – erzwungen<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**query_parameterization_type_desc**|**nvarchar(60)**|Die textbeschreibung für den Typ der Parametrisierung.<br/>**Hinweis**: Azure SQL Data Warehouse gibt stets *keine*.|  
|**initial_compile_start_time**|**datetimeoffset**|Kompilieren Sie die Startzeit.|  
|**last_compile_start_time**|**datetimeoffset**|Kompilieren Sie die Startzeit.|  
|**last_execution_time**|**datetimeoffset**|Zeitpunkt der letzten Ausführung bezeichnet die letzte Beendigungszeit der den Abfrageplan.|  
|**last_compile_batch_sql_handle**|**varbinary(64)**|Handle für den letzten SQL-Batch, die in dem Abfrage zuletzt verwendet wurde. Es kann bereitgestellt werden, als Eingabe für [Sys. dm_exec_sql_text &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) um den vollständigen Text des Batches zu erhalten.<br/>**Hinweis**: Azure SQL Data Warehouse gibt stets *NULL*.|  
|**last_compile_batch_offset_start**|**bigint**|Informationen, die mit Sys. dm_exec_sql_text zusammen mit Last_compile_batch_sql_handle bereitgestellt werden kann.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_compile_batch_offset_end**|**bigint**|Informationen, die mit Sys. dm_exec_sql_text zusammen mit Last_compile_batch_sql_handle bereitgestellt werden kann.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**count_compiles**|**bigint**|Statistiken, die Kompilierung.<br/>**Hinweis**: Azure SQL Data Warehouse wird immer eins (1) zurückgegeben.|  
|**avg_compile_duration**|**float**|Statistiken, die Kompilierung in Mikrosekunden.|  
|**last_compile_duration**|**bigint**|Statistiken, die Kompilierung in Mikrosekunden.|  
|**avg_bind_duration**|**float**|Binden Statistiken in Mikrosekunden.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**last_bind_duration**|**bigint**|Statistiken, die Bindung.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**avg_bind_cpu_time**|**float**|Statistiken, die Bindung.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**last_bind_cpu_time**|**bigint**|Statistiken, die Bindung.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**avg_optimize_duration**|**float**|Statistiken zur abfrageoptimierung in Mikrosekunden.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_optimize_duration**|**bigint**|Statistiken zur abfrageoptimierung.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_optimize_cpu_time**|**float**|Statistiken zur abfrageoptimierung in Mikrosekunden.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_optimize_cpu_time**|**bigint**|Statistiken zur abfrageoptimierung.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_compile_memory_kb**|**float**|Speicherstatistiken zu kompilieren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_compile_memory_kb**|**bigint**|Speicherstatistiken zu kompilieren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_compile_memory_kb**|**bigint**|Speicherstatistiken zu kompilieren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**is_clouddb_internal_query**|**bit**|Immer 0 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lokal.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW DATABASE STATE** Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Gespeicherte Prozeduren für den Abfragespeicher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
