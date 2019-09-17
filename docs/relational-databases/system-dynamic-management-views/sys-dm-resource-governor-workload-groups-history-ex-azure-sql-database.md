---
title: sys. DM _resource_governor_workload_groups_history_ex (Azure SQL-Datenbank) | Microsoft-Dokumentation
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
ms.openlocfilehash: 5fea5badf14ce9863f07dff189f1665788ec5fb6
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70873769"
---
# <a name="sysdm_resource_governor_workload_groups_history_ex-azure-sql-database"></a>sys.dm_resource_governor_workload_groups_history_ex (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Gibt die Momentaufnahme für die letzten 32 Minuten (insgesamt 128 RECS) der Ressourcenpool Statistik für eine Azure SQL-Datenbank zurück.
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**pool_id**| ssNoversion |ID des Ressourcenpools. Lässt keine NULL-Werte zu.|
|**group_id**| ssNoversion |ID der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|
|**name**| nvarchar(256) |Name der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|
|**snapshot_time**| DATETIME |DateTime der erstellten Ressourcengruppen-Statistik Momentaufnahme.|
|**duration_ms**| ssNoversion |Dauer zwischen aktueller und vorheriger Momentaufnahme.|
|**active_worker_count**| ssNoversion |Gesamtanzahl der Worker in der aktuellen Momentaufnahme.|
|**active_request_count**| ssNoversion |Die aktuelle Anforderungsanzahl. Lässt keine NULL-Werte zu.|
|**active_session_count**| ssNoversion |Gesamtanzahl aktiver Sitzungen in der aktuellen Momentaufnahme.|
|**total_request_count**| BIGINT |Kumulierte Anzahl vervollständigter Anforderungen in der Arbeitsauslastungsgruppe. Lässt keine NULL-Werte zu.|
|**delta_request_count**| ssNoversion |Anzahl der abgeschlossenen Anforderungen in der Arbeits Auslastungs Gruppe seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**total_cpu_usage_ms**| BIGINT |Kumulierte CPU-Verwendung dieser Arbeitsauslastungsgruppe in Millisekunden. Lässt keine NULL-Werte zu.|
|**delta_cpu_usage_ms**| ssNoversion |CPU-Auslastung in Millisekunden seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_cpu_usage_preemptive_ms**| ssNoversion |Präemptiv Win32-Aufrufe, die seit der letzten Momentaufnahme nicht von der SQL-CPU-RG-|
|**delta_reads_reduced_memgrant_count**| ssNoversion |Die Anzahl der Arbeitsspeicher Zuweisungen, die den maximalen Grenzwert für die Abfrage Größe seit der letzten Momentaufnahme erreicht haben. Lässt keine NULL-Werte zu.|
|**reads_throttled**| ssNoversion |Die Gesamtanzahl der gelesenen Lesevorgänge.|
|**delta_reads_queued**| ssNoversion |Die Gesamtanzahl der gelesenen e/As seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a-Vorgänge bestimmt ist.|
|**delta_reads_issued**| ssNoversion |Der seit der letzten Momentaufnahme ausgegebene Lesevorgang insgesamt. Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a-Vorgänge bestimmt ist.|
|**delta_reads_completed**| ssNoversion |Die Gesamtanzahl der gelesenen IOS-Lesevorgänge seit der letzten Lässt keine NULL-Werte zu.|
|**delta_read_bytes**| BIGINT |Die Gesamtanzahl der seit der letzten Momentaufnahme gelesenen Bytes. Lässt keine NULL-Werte zu.|
|**delta_read_stall_ms**| ssNoversion |Gesamtzeit (in Millisekunden) zwischen Lese-e/a-Empfang und-Abschluss seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_stall_queued_ms**| ssNoversion |Gesamtzeit (in Millisekunden) zwischen Lese-e/a-Empfang und Problem seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a-Vorgänge bestimmt ist. Delta_read_stall_queued_ms bedeutet, dass e/a-Vorgänge von der RG betroffen sind.|
|**delta_writes_queued**| ssNoversion |Die Gesamtanzahl der in die Warteschlange eingereihten e/a-Vorgänge seit Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a-Vorgänge bestimmt ist.|
|**delta_writes_issued**| ssNoversion |Die seit der letzten Momentaufnahme ausgegebene IOS-Summe. Lässt NULL-Werte zu. NULL, wenn die Ressourcengruppe nicht für e/a-Vorgänge bestimmt ist.|
|**delta_writes_completed**| ssNoversion |Die Summe der seit der letzten Momentaufnahme abgeschlossenen IOS-Schreibvorgänge. Lässt keine NULL-Werte zu.|
|**delta_writes_bytes**| BIGINT |Die Gesamtanzahl von Bytes, die seit der letzten Momentaufnahme geschrieben wurden. Lässt keine NULL-Werte zu.|
|**delta_write_stall_ms**| ssNoversion |Gesamtzeit (in Millisekunden) zwischen Schreib-e/a-Eingang und-Abschluss seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_background_writes**| ssNoversion |Die Gesamtanzahl der Schreibvorgänge, die seit der letzten Momentaufnahme von Hintergrundaufgaben|
|**delta_background_write_bytes**| BIGINT |Die Gesamt Schreibgröße, die seit der letzten Momentaufnahme von Hintergrundaufgaben ausgeführt wurde (in Bytes).|
|**delta_log_bytes_used**| BIGINT |Das Protokoll wurde seit der letzten Momentaufnahme in Bytes verwendet.|
|**delta_log_temp_db_bytes_used**| BIGINT |Das tempdb-Protokoll wurde seit der letzten Momentaufnahme in Bytes verwendet.|
|**delta_query_optimizations**| BIGINT |Gibt die Anzahl von Abfrage Optimierungen in dieser Arbeits Auslastungs Gruppe seit der letzten Momentaufnahme an. Lässt keine NULL-Werte zu.|
|**delta_suboptimal_plan_generations**| BIGINT |Die Anzahl der suboptimalen Plan Generierungen, die in dieser Arbeits Auslastungs Gruppe aufgrund von Speicherauslastung seit der letzten Momentaufnahme aufgetreten sind. Lässt keine NULL-Werte zu.
|**max_memory_grant_kb**| BIGINT |Maximale Arbeitsspeicher Zuweisung für die Gruppe in KB.|
|**max_request_cpu_msec**| BIGINT |Maximale CPU-Nutzung für eine einzelne Anforderung in Millisekunden. Lässt keine NULL-Werte zu.|
|**max_concurrent_request**| ssNoversion |Aktuelle Einstellung für die maximale Anzahl gleichzeitiger Anforderungen. Lässt keine NULL-Werte zu.|
|**max_io**| ssNoversion |Maximale e/a-Beschränkung für die Gruppe.|
|**max_global_io**| ssNoversion |Nur für Informationszwecke identifiziert. Wird nicht unterstützt. Zukünftige Kompatibilität wird nicht sichergestellt.
|**max_queued_io**| ssNoversion |Nur für Informationszwecke identifiziert. Wird nicht unterstützt. Zukünftige Kompatibilität wird nicht sichergestellt.|
|**max_log_rate_kb**| BIGINT |Maximale Protokoll Rate (Kilobytes pro Sekunde) auf Ressourcengruppen Ebene.|
|**max_session**| ssNoversion |Sitzungs Limit für die Gruppe.|
|**max_worker**| ssNoversion |Workerlimit für die Gruppe.|
|||

## <a name="permissions"></a>Berechtigungen

Diese Sicht erfordert die View Server State-Berechtigung.

## <a name="remarks"></a>Hinweise

Benutzer können auf diese dynamische Verwaltungs Sicht zugreifen, um den Ressourcenverbrauch nahezu in Echtzeit für den benutzerworkloadpool sowie systeminterne Pools der Azure SQL-Daten Bank Instanz zu überwachen.

> [!IMPORTANT]
> Die meisten Daten, die von dieser DMV festgestellt werden, sind für den internen Gebrauch vorgesehen und können geändert werden.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel werden die maximalen Protokoll Raten Daten und der Verbrauch bei den einzelnen Momentaufnahmen nach Benutzer Pool zurückgegeben:

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

- [Governanceprotokoll Raten-Governance](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [DTU-Ressourcen Limits für elastische Datenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [Ressourcen Limits für den Ressourcenpool für elastische Datenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
