---
title: Sys. query_store_runtime_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b1e6b88775a7df931919425955c51b6154fd9c4d
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39543700"
---
# <a name="sysquerystoreruntimestats-transact-sql"></a>Sys. query_store_runtime_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Enthält Informationen zu der Common Language Runtime die Informationen für die Abfrage.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**runtime_stats_id**|**bigint**|Bezeichner der Zeile für die Laufzeit-Ausführungsstatistik für den **Plan_id**, **Execution_type** und **Runtime_stats_interval_id**. Es ist nur für die letzten Runtime Statistics Intervalle eindeutig. Für die aktuell aktiven Intervalls möglicherweise mehrere Zeilen, die Laufzeitstatistiken für den Plan verweist darstellt **Plan_id**, mit dem dargestellt wird, indem Sie Ausführung **Execution_type**. In der Regel stellt eine Zeile Clientlaufzeit-Statistik, die geleert werden, auf dem Datenträger, während andere (s) im Speicher enthaltenen Status darstellen. Daher zum Abrufen der tatsächlichen Status für jedes Intervall, müssen Sie aggregierte Metriken Gruppieren nach **Plan_id**, **Execution_type** und **Runtime_stats_interval_id**. |  
|**plan_id**|**bigint**|Fremdschlüssel. Verknüpft mit [Sys. query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**bigint**|Fremdschlüssel. Verknüpft mit [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**execution_type**|**tinyint**|Bestimmt die Art der Ausführung einer Abfrage:<br /><br /> 0 – reguläre Ausführung (erfolgreich abgeschlossen)<br /><br /> 3 – Client initiierter Abbruch der Ausführung<br /><br /> 4 - Ausnahme hat die Ausführung abgebrochen.|  
|**execution_type_desc**|**nvarchar(128)**|Die textbeschreibung des Type-Feld Ausführung:<br /><br /> 0 – reguläre<br /><br /> 3 – abgebrochen<br /><br /> 4 - Ausnahme|  
|**first_execution_time**|**datetimeoffset**|Zeitpunkt der ersten Ausführung für den Abfrageplan in aggregationsintervalls.|  
|**last_execution_time**|**datetimeoffset**|Zeitpunkt der letzten Ausführung der Abfrage innerhalb des aggregationsintervalls zu planen.|  
|**count_executions**|**bigint**|Die Gesamtzahl der Ausführungen für den Abfrageplan in aggregationsintervalls.|  
|**avg_duration-Spalte**|**float**|Die durchschnittliche Dauer für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**last_duration**|**bigint**|Planen Sie die letzte Dauer für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).|  
|**min_duration**|**bigint**|Die Mindestdauer für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**max_duration**|**bigint**|Maximale Dauer für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**stdev_duration**|**float**|Dauer der Standardabweichung für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**avg_cpu_time**|**float**|Die durchschnittliche CPU-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**last_cpu_time**|**bigint**|Planen Sie die letzte CPU-Zeit für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).|  
|**min_cpu_time**|**bigint**|Minimale CPU-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**max_cpu_time**|**bigint**|Maximale CPU-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**stdev_cpu_time**|**float**|CPU-Zeit die Standardabweichung für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**avg_logical_io_reads**|**float**|Durchschnittliche Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)|  
|**last_logical_io_reads**|**bigint**|Letzte Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)|  
|**min_logical_io_reads**|**bigint**|Minimale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)|  
|**max_logical_io_reads**|**bigint**|Maximale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.) |  
|**stdev_logical_io_reads**|**float**|Anzahl logischer EA-Vorgänge liest die Standardabweichung für den Abfrageplan in aggregationsintervalls. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)|  
|**avg_logical_io_writes**|**float**|Durchschnittliche Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.|  
|**last_logical_io_writes**|**bigint**|Letzte Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.|  
|**min_logical_io_writes**|**bigint**|Minimale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.|  
|**max_logical_io_writes**|**bigint**|Maximale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.|  
|**stdev_logical_io_writes**|**float**|Anzahl logischer EA-Vorgänge schreibt die Standardabweichung für den Abfrageplan in aggregationsintervalls.|  
|**avg_physical_io_reads**|**float**|Durchschnittliche Anzahl physischer e/a-liest, für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).|  
|**last_physical_io_reads**|**bigint**|Letzten Anzahl physischer e/a-Lesevorgänge für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).|  
|**min_physical_io_reads**|**bigint**|Minimale Anzahl physischer e/a-liest, für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).|  
|**max_physical_io_reads**|**bigint**|Maximale Anzahl physischer e/a-liest, für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).|  
|**stdev_physical_io_reads**|**float**|Anzahl der physischen e/a liest die Standardabweichung für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).|  
|**avg_clr_time**|**float**|Die durchschnittliche CLR-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**last_clr_time**|**bigint**|Planen Sie die letzte CLR-Zeit für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).|  
|**min_clr_time**|**bigint**|Minimale CLR-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**max_clr_time**|**bigint**|Maximale CLR-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**stdev_clr_time**|**float**|Planen Sie die Standardabweichung der CLR-Zeit für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).|  
|**avg_dop**|**float**|Durchschnittliche DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.|  
|**last_dop**|**bigint**|Letzte DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.|  
|**min_dop**|**bigint**|Minimale DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.|  
|**max_dop**|**bigint**|Maximale DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.|  
|**stdev_dop**|**float**|DOP (Grad an Parallelität) die Standardabweichung für den Abfrageplan in aggregationsintervalls.|  
|**avg_query_max_used_memory**|**float**|Durchschnittliche arbeitsspeicherzuweisung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.|  
|**last_query_max_used_memory**|**bigint**|Letzte arbeitsspeicherzuweisung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.|  
|**min_query_max_used_memory**|**bigint**|Minimale arbeitsspeicherzuweisung nutzen (als Anzahl von 8 KB-Seiten gemeldet) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.|  
|**max_query_max_used_memory**|**bigint**|Maximale arbeitsspeicherzuweisung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.|  
|**stdev_query_max_used_memory**|**float**|Bei der arbeitsspeicherzuweisung Standardabweichung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.|  
|**avg_rowcount**|**float**|Durchschnittliche Anzahl von zurückgegebenen Zeilen für den Abfrageplan in aggregationsintervalls.|  
|**last_rowcount**|**bigint**|Die Anzahl der zurückgegebenen Zeilen der letzten Ausführung des Abfrageplans in aggregationsintervalls.|  
|**min_rowcount**|**bigint**|Planen Sie die minimale Anzahl von zurückgegebenen Zeilen für die Abfrage innerhalb des aggregationsintervalls.|  
|**max_rowcount**|**bigint**|Planen Sie die maximale Anzahl von zurückgegebenen Zeilen für die Abfrage innerhalb des aggregationsintervalls.|  
|**stdev_rowcount**|**float**|Die Anzahl der zurückgegebenen Zeilen Standardabweichung für den Abfrageplan in aggregationsintervalls.|
|**avg_log_bytes_used**|**float**|Durchschnittliche Anzahl von Bytes in das Datenbankprotokoll, die von der Abfrageplan in aggregationsintervalls verwendet. Wendet **nur für Azure SQL-Datenbank**.|    
|**last_log_bytes_used**|**bigint**|Anzahl der Bytes im Protokoll von der letzten Ausführung des Abfrageplans, in dem aggregationsintervall verwendet. Wendet **nur für Azure SQL-Datenbank**.|  
|**min_log_bytes_used**|**bigint**|Minimale Anzahl von Bytes in das Datenbankprotokoll, die von der Abfrageplan in aggregationsintervalls verwendet.  Wendet **nur für Azure SQL-Datenbank**.|  
|**max_log_bytes_used**|**bigint**|Maximale Anzahl von Bytes in das Datenbankprotokoll, die von der Abfrageplan in aggregationsintervalls verwendet.  Wendet **nur für Azure SQL-Datenbank**.| 
|**stdev_log_bytes_used**|**float**|Standardabweichung der die Anzahl der Bytes im Datenbankprotokoll von innerhalb des aggregationsintervalls eines Abfrageplans verwendet.  Wendet **nur für Azure SQL-Datenbank**.|
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW DATABASE STATE** Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [Sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Query Store gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
