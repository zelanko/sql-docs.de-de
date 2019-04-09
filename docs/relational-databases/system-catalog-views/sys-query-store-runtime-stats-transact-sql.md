---
title: Sys. query_store_runtime_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.QUERY_STORE_RUNTIME_STATS_TSQL
- QUERY_STORE_RUNTIME_STATS_TSQL
- SYS.QUERY_STORE_RUNTIME_STATS
- QUERY_STORE_RUNTIME_STATS
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_runtime_stats catalog view
- sys.query_store_runtime_stats catalog view
ms.assetid: ccf7a57c-314b-450c-bd34-70749a02784a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3392bcde00439981a401c908ca7a1898d9d026f5
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59242308"
---
# <a name="sysquerystoreruntimestats-transact-sql"></a>sys.query_store_runtime_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Enthält Informationen zu der Common Language Runtime die Informationen für die Abfrage.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**runtime_stats_id**|**BIGINT**|Bezeichner der Zeile für die Laufzeit-Ausführungsstatistik für den **Plan_id**, **Execution_type** und **Runtime_stats_interval_id**. Es ist nur für die letzten Runtime Statistics Intervalle eindeutig. Für die aktuell aktiven Intervalls möglicherweise mehrere Zeilen, die Laufzeitstatistiken für den Plan verweist darstellt **Plan_id**, mit dem dargestellt wird, indem Sie Ausführung **Execution_type**. In der Regel stellt eine Zeile Clientlaufzeit-Statistik, die geleert werden, auf dem Datenträger, während andere (s) im Speicher enthaltenen Status darstellen. Daher zum Abrufen der tatsächlichen Status für jedes Intervall, müssen Sie aggregierte Metriken Gruppieren nach **Plan_id**, **Execution_type** und **Runtime_stats_interval_id**.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**plan_id**|**BIGINT**|Fremdschlüssel. Verknüpft mit [Sys. query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**BIGINT**|Fremdschlüssel. Verknüpft mit [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**execution_type**|**TINYINT**|Bestimmt die Art der Ausführung einer Abfrage:<br /><br /> 0 – reguläre Ausführung (erfolgreich abgeschlossen)<br /><br /> 3 – Client initiierter Abbruch der Ausführung<br /><br /> 4 - Ausnahme hat die Ausführung abgebrochen.|  
|**execution_type_desc**|**nvarchar(128)**|Die textbeschreibung des Type-Feld Ausführung:<br /><br /> 0 – reguläre<br /><br /> 3: abgebrochen<br /><br /> 4 - Ausnahme|  
|**first_execution_time**|**datetimeoffset**|Zeitpunkt der ersten Ausführung für den Abfrageplan in aggregationsintervalls.|  
|**last_execution_time**|**datetimeoffset**|Zeitpunkt der letzten Ausführung der Abfrage innerhalb des aggregationsintervalls zu planen.|  
|**count_executions**|**BIGINT**|Die Gesamtzahl der Ausführungen für den Abfrageplan in aggregationsintervalls.|  
|**avg_duration**|**FLOAT**|Die durchschnittliche Dauer für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**last_duration**|**BIGINT**|Planen Sie die letzte Dauer für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).|  
|**min_duration**|**BIGINT**|Die Mindestdauer für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**max_duration**|**BIGINT**|Maximale Dauer für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**stdev_duration**|**FLOAT**|Dauer der Standardabweichung für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**avg_cpu_time**|**FLOAT**|Die durchschnittliche CPU-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_cpu_time**|**BIGINT**|Planen Sie die letzte CPU-Zeit für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_cpu_time**|**BIGINT**|Minimale CPU-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_cpu_time**|**BIGINT**|Maximale CPU-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_cpu_time**|**FLOAT**|CPU-Zeit die Standardabweichung für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_logical_io_reads**|**FLOAT**|Durchschnittliche Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_logical_io_reads**|**BIGINT**|Letzte Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_logical_io_reads**|**BIGINT**|Minimale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_logical_io_reads**|**BIGINT**|Maximale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_logical_io_reads**|**FLOAT**|Anzahl logischer EA-Vorgänge liest die Standardabweichung für den Abfrageplan in aggregationsintervalls. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_logical_io_writes**|**FLOAT**|Durchschnittliche Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_logical_io_writes**|**BIGINT**|Letzte Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_logical_io_writes**|**BIGINT**|Minimale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_logical_io_writes**|**BIGINT**|Maximale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_logical_io_writes**|**FLOAT**|Anzahl logischer EA-Vorgänge schreibt die Standardabweichung für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_physical_io_reads**|**FLOAT**|Durchschnittliche Anzahl physischer e/a-liest, für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_physical_io_reads**|**BIGINT**|Letzten Anzahl physischer e/a-Lesevorgänge für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_physical_io_reads**|**BIGINT**|Minimale Anzahl physischer e/a-liest, für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_physical_io_reads**|**BIGINT**|Maximale Anzahl physischer e/a-liest, für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_physical_io_reads**|**FLOAT**|Anzahl der physischen e/a liest die Standardabweichung für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_clr_time**|**FLOAT**|Die durchschnittliche CLR-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_clr_time**|**BIGINT**|Planen Sie die letzte CLR-Zeit für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_clr_time**|**BIGINT**|Minimale CLR-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_clr_time**|**BIGINT**|Maximale CLR-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_clr_time**|**FLOAT**|Planen Sie die Standardabweichung der CLR-Zeit für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_dop**|**FLOAT**|Durchschnittliche DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_dop**|**BIGINT**|Letzte DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_dop**|**BIGINT**|Minimale DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_dop**|**BIGINT**|Maximale DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_dop**|**FLOAT**|DOP (Grad an Parallelität) die Standardabweichung für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_query_max_used_memory**|**FLOAT**|Durchschnittliche arbeitsspeicherzuweisung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_query_max_used_memory**|**BIGINT**|Letzte arbeitsspeicherzuweisung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_query_max_used_memory**|**BIGINT**|Minimale arbeitsspeicherzuweisung nutzen (als Anzahl von 8 KB-Seiten gemeldet) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_query_max_used_memory**|**BIGINT**|Maximale arbeitsspeicherzuweisung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_query_max_used_memory**|**FLOAT**|Bei der arbeitsspeicherzuweisung Standardabweichung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_rowcount**|**FLOAT**|Durchschnittliche Anzahl von zurückgegebenen Zeilen für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_rowcount**|**BIGINT**|Die Anzahl der zurückgegebenen Zeilen der letzten Ausführung des Abfrageplans in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_rowcount**|**BIGINT**|Planen Sie die minimale Anzahl von zurückgegebenen Zeilen für die Abfrage innerhalb des aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_rowcount**|**BIGINT**|Planen Sie die maximale Anzahl von zurückgegebenen Zeilen für die Abfrage innerhalb des aggregationsintervalls.|  
|**stdev_rowcount**|**FLOAT**|Die Anzahl der zurückgegebenen Zeilen Standardabweichung für den Abfrageplan in aggregationsintervalls.|
|**avg_log_bytes_used**|**FLOAT**|Durchschnittliche Anzahl von Bytes in das Datenbankprotokoll, die von der Abfrageplan in aggregationsintervalls verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_log_bytes_used**|**BIGINT**|Anzahl der Bytes im Protokoll von der letzten Ausführung des Abfrageplans, in dem aggregationsintervall verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_log_bytes_used**|**BIGINT**|Minimale Anzahl von Bytes in das Datenbankprotokoll, die von der Abfrageplan in aggregationsintervalls verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_log_bytes_used**|**BIGINT**|Maximale Anzahl von Bytes in das Datenbankprotokoll, die von der Abfrageplan in aggregationsintervalls verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_log_bytes_used**|**FLOAT**|Standardabweichung der die Anzahl der Bytes im Datenbankprotokoll von innerhalb des aggregationsintervalls eines Abfrageplans verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW DATABASE STATE** Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Gespeicherte Prozeduren für den Abfragespeicher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
