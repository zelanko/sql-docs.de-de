---
title: Sys. query_store_runtime_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/03/2019
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
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3ba19045d0184e498b559da0b97b3cd4d95d30c9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067933"
---
# <a name="sysquerystoreruntimestats-transact-sql"></a>Sys. query_store_runtime_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Enthält Informationen zu der Common Language Runtime die Informationen für die Abfrage.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**runtime_stats_id**|**bigint**|Bezeichner der Zeile für die Laufzeit-Ausführungsstatistik für den **Plan_id**, **Execution_type** und **Runtime_stats_interval_id**. Es ist nur für die letzten Runtime Statistics Intervalle eindeutig. Für die aktuell aktiven Intervalls möglicherweise mehrere Zeilen, die Laufzeitstatistiken für den Plan verweist darstellt **Plan_id**, mit dem dargestellt wird, indem Sie Ausführung **Execution_type**. In der Regel stellt eine Zeile Clientlaufzeit-Statistik, die geleert werden, auf dem Datenträger, während andere (s) im Speicher enthaltenen Status darstellen. Daher zum Abrufen der tatsächlichen Status für jedes Intervall, müssen Sie aggregierte Metriken Gruppieren nach **Plan_id**, **Execution_type** und **Runtime_stats_interval_id**.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**plan_id**|**bigint**|Fremdschlüssel. Verknüpft mit [Sys. query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**bigint**|Fremdschlüssel. Verknüpft mit [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**execution_type**|**tinyint**|Bestimmt die Art der Ausführung einer Abfrage:<br /><br /> 0 – reguläre Ausführung (erfolgreich abgeschlossen)<br /><br /> 3 – Client initiierter Abbruch der Ausführung<br /><br /> 4 - Ausnahme hat die Ausführung abgebrochen.|  
|**execution_type_desc**|**nvarchar(128)**|Die textbeschreibung des Type-Feld Ausführung:<br /><br /> 0 – reguläre<br /><br /> 3: abgebrochen<br /><br /> 4 - Ausnahme|  
|**first_execution_time**|**datetimeoffset**|Zeitpunkt der ersten Ausführung für den Abfrageplan in aggregationsintervalls. Dies bezieht sich auf die Endzeit der Ausführung der Abfrage.|  
|**last_execution_time**|**datetimeoffset**|Zeitpunkt der letzten Ausführung der Abfrage innerhalb des aggregationsintervalls zu planen. Dies bezieht sich auf die Endzeit der Ausführung der Abfrage.|  
|**count_executions**|**bigint**|Die Gesamtzahl der Ausführungen für den Abfrageplan in aggregationsintervalls.|  
|**avg_duration**|**float**|Die durchschnittliche Dauer für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**last_duration**|**bigint**|Planen Sie die letzte Dauer für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).|  
|**min_duration**|**bigint**|Die Mindestdauer für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**max_duration**|**bigint**|Maximale Dauer für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**stdev_duration**|**float**|Dauer der Standardabweichung für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).|  
|**avg_cpu_time**|**float**|Die durchschnittliche CPU-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_cpu_time**|**bigint**|Planen Sie die letzte CPU-Zeit für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_cpu_time**|**bigint**|Minimale CPU-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_cpu_time**|**bigint**|Maximale CPU-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_cpu_time**|**float**|CPU-Zeit die Standardabweichung für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_logical_io_reads**|**float**|Durchschnittliche Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_logical_io_reads**|**bigint**|Letzte Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_logical_io_reads**|**bigint**|Minimale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_logical_io_reads**|**bigint**|Maximale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls liest. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_logical_io_reads**|**float**|Anzahl logischer EA-Vorgänge liest die Standardabweichung für den Abfrageplan in aggregationsintervalls. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_logical_io_writes**|**float**|Durchschnittliche Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_logical_io_writes**|**bigint**|Letzte Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_logical_io_writes**|**bigint**|Minimale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_logical_io_writes**|**bigint**|Maximale Anzahl logischer EA-Vorgänge werden für den Abfrageplan in aggregationsintervalls schreibt.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_logical_io_writes**|**float**|Anzahl logischer EA-Vorgänge schreibt die Standardabweichung für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_physical_io_reads**|**float**|Durchschnittliche Anzahl physischer e/a-liest, für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_physical_io_reads**|**bigint**|Letzten Anzahl physischer e/a-Lesevorgänge für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_physical_io_reads**|**bigint**|Minimale Anzahl physischer e/a-liest, für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_physical_io_reads**|**bigint**|Maximale Anzahl physischer e/a-liest, für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_physical_io_reads**|**float**|Anzahl der physischen e/a liest die Standardabweichung für den Abfrageplan in aggregationsintervalls (ausgedrückt als eine Reihe von 8KB-Seiten lesen).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_clr_time**|**float**|Die durchschnittliche CLR-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_clr_time**|**bigint**|Planen Sie die letzte CLR-Zeit für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_clr_time**|**bigint**|Minimale CLR-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_clr_time**|**bigint**|Maximale CLR-Zeit für den Abfrageplan in die aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_clr_time**|**float**|Planen Sie die Standardabweichung der CLR-Zeit für die Abfrage innerhalb der aggregationsintervall (in Mikrosekunden gemeldet).<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_dop**|**float**|Durchschnittliche DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_dop**|**bigint**|Letzte DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_dop**|**bigint**|Minimale DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_dop**|**bigint**|Maximale DOP (Grad an Parallelität) für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_dop**|**float**|DOP (Grad an Parallelität) die Standardabweichung für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_query_max_used_memory**|**float**|Durchschnittliche arbeitsspeicherzuweisung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_query_max_used_memory**|**bigint**|Letzte arbeitsspeicherzuweisung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_query_max_used_memory**|**bigint**|Minimale arbeitsspeicherzuweisung nutzen (als Anzahl von 8 KB-Seiten gemeldet) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_query_max_used_memory**|**bigint**|Maximale arbeitsspeicherzuweisung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_query_max_used_memory**|**float**|Bei der arbeitsspeicherzuweisung Standardabweichung (angegeben als Anzahl von 8 KB-Seiten) für den Abfrageplan in aggregationsintervalls. 0 für Abfragen, die systemintern kompiliert immer Speicheroptimierte Verfahren.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**avg_rowcount**|**float**|Durchschnittliche Anzahl von zurückgegebenen Zeilen für den Abfrageplan in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_rowcount**|**bigint**|Die Anzahl der zurückgegebenen Zeilen der letzten Ausführung des Abfrageplans in aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_rowcount**|**bigint**|Planen Sie die minimale Anzahl von zurückgegebenen Zeilen für die Abfrage innerhalb des aggregationsintervalls.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_rowcount**|**bigint**|Planen Sie die maximale Anzahl von zurückgegebenen Zeilen für die Abfrage innerhalb des aggregationsintervalls.|  
|**stdev_rowcount**|**float**|Die Anzahl der zurückgegebenen Zeilen Standardabweichung für den Abfrageplan in aggregationsintervalls.|
|**avg_log_bytes_used**|**float**|Durchschnittliche Anzahl von Bytes in das Datenbankprotokoll, die von der Abfrageplan in aggregationsintervalls verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**last_log_bytes_used**|**bigint**|Anzahl der Bytes im Protokoll von der letzten Ausführung des Abfrageplans, in dem aggregationsintervall verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**min_log_bytes_used**|**bigint**|Minimale Anzahl von Bytes in das Datenbankprotokoll, die von der Abfrageplan in aggregationsintervalls verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**max_log_bytes_used**|**bigint**|Maximale Anzahl von Bytes in das Datenbankprotokoll, die von der Abfrageplan in aggregationsintervalls verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|
|**stdev_log_bytes_used**|**float**|Standardabweichung der die Anzahl der Bytes im Datenbankprotokoll von innerhalb des aggregationsintervalls eines Abfrageplans verwendet.<br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**avg_page_server_io_reads**|**float**|Durchschnittliche Anzahl der Seitenlesevorgänge Server-e/a für den Abfrageplan in aggregationsintervalls. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br><br/>**Hinweis**: Gilt für: Hochgradig skalierbaren Azure SQL-Datenbank</br> Azure SQL Data Warehouse, Azure SQL-Datenbank, MI (nicht-hochgradig skalierbaren) gibt immer 0 (null) zurück.|
|**last_page_server_io_reads**|**bigint**|Letzte Anzahl Seite Server e/a-Lesevorgänge für den Abfrageplan in aggregationsintervalls. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br><br/>**Hinweis**: Gilt für: Hochgradig skalierbaren Azure SQL-Datenbank </br> Azure SQL Data Warehouse, Azure SQL-Datenbank, MI (nicht-hochgradig skalierbaren) gibt immer 0 (null) zurück.|
|**min_page_server_io_reads**|**bigint**|Minimale Anzahl der Seitenlesevorgänge Server-e/a für den Abfrageplan in aggregationsintervalls. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br><br/>**Hinweis**: Gilt für: Hochgradig skalierbaren Azure SQL-Datenbank </br> Azure SQL Data Warehouse, Azure SQL-Datenbank, MI (nicht-hochgradig skalierbaren) gibt immer 0 (null) zurück.|
|**max_page_server_io_reads**|**bigint**|Maximale Anzahl der Seitenlesevorgänge Server-e/a für den Abfrageplan in aggregationsintervalls. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br><br/>**Hinweis**: Gilt für: Hochgradig skalierbaren Azure SQL-Datenbank </br> Azure SQL Data Warehouse, Azure SQL-Datenbank, MI (nicht-hochgradig skalierbaren) gibt immer 0 (null) zurück.|
|**stdev_page_server_io_reads**|**float**|Anzahl der Seitenserver e/a-Lesevorgänge auf Standardabweichung für den Abfrageplan in aggregationsintervalls. (ausgedrückt als eine Reihe von 8KB-Seiten zu lesen.)<br><br/>**Hinweis**: Gilt für: Hochgradig skalierbaren Azure SQL-Datenbank </br> Azure SQL Data Warehouse, Azure SQL-Datenbank, MI (nicht-hochgradig skalierbaren) gibt immer 0 (null) zurück.|
  
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
 [Query Store gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
