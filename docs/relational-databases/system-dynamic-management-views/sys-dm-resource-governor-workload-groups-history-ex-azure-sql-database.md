---
title: Sys.dm_resource_governor_workload_groups_history_ex (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups_history_ex_TSQL
- sys.dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_resource_governor_workload_groups_history_ex dynamic management view
author: joesackmsft
ms.author: josack
manager: craigg
ms.openlocfilehash: 1a2123c3da5945fb42184631e43fe27d83972375
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66744025"
---
# <a name="sysdmresourcegovernorworkloadgroupshistoryex-azure-sql-database"></a>sys.dm_resource_governor_workload_groups_history_ex (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Gibt die Momentaufnahme in Intervallen von 15 Sekunden für die letzten 30 Minuten der Resource pools Statistiken für eine Azure SQL-Datenbank.
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**pool_id**| ssNoversion |Die ID des Ressourcenpools an. Lässt keine NULL-Werte zu.|
|**group_id**| ssNoversion |ID der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|
|**name**| nvarchar(256) |Name der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|
|**snapshot_time**| DATETIME |Datum und Uhrzeit der Resource Group Statistiken Momentaufnahme.|
|**duration_ms**| ssNoversion |Die Dauer zwischen aktuellen und vorherigen Momentaufnahme.|
|**active_worker_count**| ssNoversion |Gesamtanzahl an Workern in der aktuellen Momentaufnahme.|
|**active_request_count**| ssNoversion |Die aktuelle Anforderungsanzahl. Lässt keine NULL-Werte zu.|
|**active_session_count**| ssNoversion |Aktive Sitzungen in der aktuellen Momentaufnahme insgesamt.|
|**total_request_count**| BIGINT |Kumulierte Anzahl vervollständigter Anforderungen in der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|
|**delta_request_count**| ssNoversion |Anzahl von abgeschlossenen Anforderungen in der Arbeitsauslastungsgruppe seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**total_cpu_usage_ms**| BIGINT |Kumulierte CPU-Verwendung dieser Arbeitsauslastungsgruppe in Millisekunden. Lässt keine NULL-Werte zu.|
|**delta_cpu_usage_ms**| ssNoversion |CPU-Auslastung in Millisekunden seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_cpu_usage_preemptive_ms**| ssNoversion |PreEmptive-win32-Aufrufe, die Sie nicht von SQL-CPU-RG Regeln seit der letzten Momentaufnahme.|
|**delta_reads_reduced_memgrant_count**| ssNoversion |Die Anzahl von arbeitsspeicherzuweisungen, die die maximale Größe seit der letzten Momentaufnahme erreicht. Lässt keine NULL-Werte zu.|
|**reads_throttled**| ssNoversion |Gesamte Anzahl der Lesevorgänge, die gedrosselt.|
|**delta_reads_queued**| ssNoversion |Die Gesamtanzahl Lesevorgänge in die Warteschlange eingereiht, seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a verwaltet wird.|
|**delta_reads_issued**| ssNoversion |Die Gesamtanzahl Lesevorgänge seit der letzten Momentaufnahme ausgegeben. Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a verwaltet wird.|
|**delta_reads_completed**| ssNoversion |Die Gesamtanzahl Lesevorgänge abgeschlossen, die seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_bytes**| BIGINT |Die Gesamtanzahl von Bytes lesen seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_stall_ms**| ssNoversion |Die Gesamtzeit (in Millisekunden) zwischen dem Lesen e/a-Eingang und Abschluss seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_stall_queued_ms**| ssNoversion |Die Gesamtzeit (in Millisekunden) zwischen dem Lesen e/a-Eingang und Problem seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a verwaltet wird. Ungleich 0 Delta_read_stall_queued_ms bedeutet, dass es sich bei e/a von RG bedingt ist.|
|**delta_writes_queued**| ssNoversion |Die Gesamtanzahl Schreibvorgänge in die Warteschlange eingereiht, seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a verwaltet wird.|
|**delta_writes_issued**| ssNoversion |Die Gesamtanzahl Schreibvorgänge seit der letzten Momentaufnahme ausgegeben. Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a verwaltet wird.|
|**delta_writes_completed**| ssNoversion |Die Gesamtanzahl Schreibvorgänge abgeschlossen, die seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_writes_bytes**| BIGINT |Die Gesamtanzahl der seit der letzten Momentaufnahme geschriebenen Bytes. Lässt keine NULL-Werte zu.|
|**delta_write_stall_ms**| ssNoversion |Die Gesamtzeit (in Millisekunden) zwischen dem Write-e/a-Eingang und Abschluss seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_background_writes**| ssNoversion |Die Gesamtanzahl der Schreibzugriffe von Aufgaben im Hintergrund ausgeführt wird, seit der letzten Momentaufnahme.|
|**delta_background_write_bytes**| BIGINT |Die Gesamtanzahl Schreibvorgänge Größe, die von Aufgaben im Hintergrund ausgeführt wird, seit der letzten Momentaufnahme in Byte.|
|**delta_log_bytes_used**| BIGINT |Protokoll verwendet, die seit der letzten Momentaufnahme in Byte.|
|**delta_log_temp_db_bytes_used**| BIGINT |Tempdb-Protokolldatei, die seit der letzten Momentaufnahme in Byte verwendet.|
|**delta_query_optimizations**| BIGINT |Die Anzahl von abfrageoptimierungen in dieser Arbeitsauslastungsgruppe seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_suboptimal_plan_generations**| BIGINT |Die Anzahl von nicht optimalen planerstellungen, die seit der letzten Momentaufnahme in dieser Arbeitsauslastungsgruppe aufgrund von ungenügendem Arbeitsspeicher aufgetreten. Lässt keine NULL-Werte zu.
|**max_memory_grant_kb**| BIGINT |Maximale arbeitsspeicherzuweisung für die Gruppe in KB.|
|**max_request_cpu_msec**| BIGINT |Maximale CPU-Nutzung für eine einzelne Anforderung in Millisekunden. Lässt keine NULL-Werte zu.|
|**max_concurrent_request**| ssNoversion |Aktuelle Einstellung für die maximale Anzahl gleichzeitiger Anforderungen. Lässt keine NULL-Werte zu.|
|**max_io**| ssNoversion |Maximale e/a-Grenzwert für die Gruppe.|
|**max_global_io**| ssNoversion |Nur für Informationszwecke identifiziert. Wird nicht unterstützt. Zukünftige Kompatibilität wird nicht sichergestellt.
|**max_queued_io**| ssNoversion |Nur für Informationszwecke identifiziert. Wird nicht unterstützt. Zukünftige Kompatibilität wird nicht sichergestellt.|
|**max_log_rate_kb**| BIGINT |Maximale protokollrate (Kilobyte pro Sekunde) auf ressourcengruppenebene sein.|
|**max_session**| ssNoversion |Maximale Sitzungen für die Gruppe.|
|**max_worker**| ssNoversion |Begrenzung für Worker für die Gruppe.|
|||

## <a name="permissions"></a>Berechtigungen

Diese Sicht erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="remarks"></a>Hinweise

Benutzer können diese dynamische verwaltungssicht, near Real-Time-Ressourcenverbrauch für arbeitsauslastungspool Benutzer als auch für interne Systempools der Azure SQL-Datenbank-Instanz überwachen zugreifen.

> [!IMPORTANT]
> Die meisten Daten, die von dieser DMV verfügbar gemacht, die für den internen Gebrauch vorgesehen ist und unterliegt Änderungen.

## <a name="examples"></a>Beispiele

Das folgende Beispiel gibt die maximale Rate-Protokolldaten und Verbrauch auf jede Momentaufnahme zurück, indem Benutzerpool:

```sql
SELECT snapshot_time,
       name,
       max_log_rate_kb,
       delta_log_bytes_used
FROM sys.dm_resource_governor_workload_groups_history_ex
WHERE name LIKE 'User%'
ORDER BY snapshot_time DESC;
```

## <a name="see-also"></a>Siehe auch

- [Übersetzung Log Rate governance](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Ressourceneinschränkungen für Pools für elastische Datenbanken DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [VCore-ressourceneinschränkungen für Pools für elastische Datenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
