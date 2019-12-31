---
title: sys. dm_resource_governor_resource_pools_history_ex (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_governor
- sys.resource_governor_TSQL
- resource_governor
- resource_governor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor catalog view
ms.assetid: ''
author: joesackmsft
ms.author: josack
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: ae34c89fd570921bec26d8a11537c58b6bba2302
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75247310"
---
# <a name="sysdm_resource_governor_resource_pools_history_ex-transact-sql"></a>sys. dm_resource_governor_resource_pools_history_ex (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Gibt die Momentaufnahme für die letzten 32 Minuten (insgesamt 128 RECS) der Ressourcenpool Statistik für eine Azure SQL-Datenbank zurück.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**pool_id**|int|Die ID des Ressourcenpools. Lässt keine NULL-Werte zu.
|**Benennen**|sysname|Der Name des Ressourcenpools. Lässt keine NULL-Werte zu.|
|**snapshot_time**|datetime2|DateTime der erstellten Statistik Momentaufnahme für den Ressourcenpool|
|**duration_ms**|int|Dauer zwischen aktueller und vorheriger Momentaufnahme|
|**statistics_start_time**|datetime2|Der Zeitpunkt, zu dem Statistiken für diesen Pool zurückgesetzt wurden. Lässt keine NULL-Werte zu.|
|**active_session_count**|int|Gesamtanzahl aktiver Sitzungen in der aktuellen Momentaufnahme|
|**active_worker_count**|int|Worker insgesamt in aktueller Momentaufnahme|
|**delta_cpu_usage_ms**|int|CPU-Auslastung in Millisekunden seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_cpu_usage_preemptive_ms**|int|Präemptiv Win32-Aufrufe, die seit der letzten Momentaufnahme nicht von SQL CPU RG|
|**used_data_space_kb**|bigint|Gesamter Speicherplatz in Benutzer Datenbanken, die dem Benutzer Pool zugeordnet sind|
|**allocated_disk_space_kb**|bigint|Gesamtgröße der Datendateien der Benutzer Datenbanken im zugeordneten Benutzer Pool|
|**target_memory_kb**|bigint|Die Zielmenge an Arbeitsspeicher in Kilobyte, die der Ressourcenpool zu erlangen versucht. Dies basiert auf den aktuellen Einstellungen und dem Serverstatus. Lässt keine NULL-Werte zu.|
|**used_memory_kb**|bigint|Der Arbeitsspeicher in Kilobyte, der für den Ressourcenpool verwendet wird. Lässt keine NULL-Werte zu.|
|**cache_memory_kb**|bigint|Die gesamte aktuelle Cachespeicherverwendung in Kilobyte. Lässt keine NULL-Werte zu.|
|**compile_memory_kb**|bigint|Die aktuell verwendete (gestohlene) Arbeitsspeicher in Kilobyte (KB). Der Arbeitsspeicher wird hierbei hauptsächlich für die Kompilierung und Optimierung verwendet, kann jedoch auch zu anderen Zwecken verwendet werden. Lässt keine NULL-Werte zu.|
|**active_memgrant_count**|bigint|Die aktuelle Anzahl von Arbeitsspeicherzuweisungen. Lässt keine NULL-Werte zu.|
|**active_memgrant_kb**|bigint|Die Summe der aktuellen Arbeitsspeicherzuweisungen in Kilobyte (KB). Lässt keine NULL-Werte zu.|
|**used_memgrant_kb**|bigint|Der gesamte aktuell verwendete (gestohlene) Arbeitsspeicher aus der Arbeitsspeicherzuweisung. Lässt keine NULL-Werte zu.|
|**delta_memgrant_timeout_count**|int|Anzahl der Timeouts für Arbeitsspeicher Zuweisungen in diesem Ressourcenpool in diesem Zeitraum. Lässt keine NULL-Werte zu.|
|**delta_memgrant_waiter_count**|int|Die Anzahl von zurzeit ausstehenden Abfragen für Arbeitsspeicherzuweisungen. Lässt keine NULL-Werte zu.|
|**delta_out_of_memory_count**|int|Die Anzahl der fehlerhaften Speicher Belegungen im Pool seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_io_queued**|int|Die Gesamtanzahl der gelesenen e/As seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_read_io_issued**|int|Der seit der letzten Momentaufnahme ausgegebene Lesevorgang insgesamt. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_read_io_completed**|int|Die Gesamtanzahl der gelesenen IOS-Lesevorgänge seit der letzten Lässt keine NULL-Werte zu.|
|**delta_read_io_throttled**|int|Die Gesamtanzahl der gelesenen IOS-Vorgänge seit der Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_read_bytes**|bigint|Die Gesamtanzahl der seit der letzten Momentaufnahme gelesenen Bytes. Lässt keine NULL-Werte zu.|
|**delta_read_io_stall_ms**|int|Gesamtzeit (in Millisekunden) zwischen Lese-e/a-Empfang und-Abschluss seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_io_stall_queued_ms**|int|Gesamtzeit (in Millisekunden) zwischen Lese-e/a-Empfang und Problem seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden. Delta_read_io_stall_queued_ms bedeutet, dass die e/a von der RG betroffen ist.|
|**delta_write_io_queued**|int|Die Gesamtanzahl der in die Warteschlange eingereihten e/a-Vorgänge seit Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_write_io_issued**|int|Die seit der letzten Momentaufnahme ausgegebene IOS-Summe. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_write_io_completed**|int|Die Summe der seit der letzten Momentaufnahme abgeschlossenen IOS-Schreibvorgänge. Lässt keine NULL-Werte zu.|
|**delta_write_io_throttled**|int|Die Gesamtzahl der Schreibvorgänge in ios seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_write_bytes**|bigint|Die Gesamtanzahl von Bytes, die seit der letzten Momentaufnahme geschrieben wurden. Lässt keine NULL-Werte zu.|
|**delta_write_io_stall_ms**|int|Gesamtzeit (in Millisekunden) zwischen Schreib-e/a-Eingang und-Abschluss seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_write_io_stall_queued_ms**|int|Gesamtzeit (in Millisekunden) zwischen dem e/a-Empfangsvorgang und dem Problem seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_io_issue_delay_ms**|int|Gesamtzeit (in Millisekunden) zwischen dem geplanten Problem und dem tatsächlichen Problem der e/a-Vorgänge seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**max_iops_per_volume**|int|Die Einstellung für die maximale e/a pro Sekunde (IOPS) pro Datenträger Volume für diesen Pool. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**max_memory_kb**|bigint|Die maximale Arbeitsspeichermenge in Kilobyte, über die der Ressourcenpool verfügen kann. Dies basiert auf den aktuellen Einstellungen und dem Serverstatus. Lässt keine NULL-Werte zu.
|**max_log_rate_kb**|bigint|Maximale Protokoll Rate (Kilobytes pro Sekunde) auf Ressourcenpool Ebene.|
|**max_data_space_kb**|bigint|Maximale Speicherlimit-Einstellung für elastische Pools für diesen Pool für elastische Datenbanken in Kilobyte.|
|**max_session**|int|Sitzungs Limit für den Pool|
|**max_worker**|int|Workerlimit für den Pool|
|**min_cpu_percent**|int|Die aktuelle Konfiguration für die garantierte durchschnittliche CPU-Bandbreite für alle Anforderungen im Ressourcenpool, wenn CPU-Konflikte bestehen. Lässt keine NULL-Werte zu.|
|**max_cpu_percent**|int|Die aktuelle Konfiguration für die maximale durchschnittliche CPU-Bandbreite, die für alle Anforderungen im Ressourcenpool zulässig ist, wenn CPU-Konflikte bestehen. Lässt keine NULL-Werte zu.|
|**cap_cpu_percent**|int|Feste Obergrenze der CPU-Bandbreite, die allen Anforderungen im Ressourcenpool zugewiesen wird. Beschränkt die maximale CPU-Bandbreitenstufe auf die angegebene Stufe. Der zulässige Bereich für den Wert ist 1 bis 100. Lässt keine NULL-Werte zu.|
|**min_vcores**|Dezimalzahl (5, 2)|Die aktuelle Konfiguration für die garantierte durchschnittliche CPU-Bandbreite für alle Anforderungen im Ressourcenpool, wenn CPU-Konflikte bestehen.  In Einheiten von virtuellen Kernen|
|**max_vcores**|Dezimalzahl (5, 2)|Die aktuelle Konfiguration für die maximale durchschnittliche CPU-Bandbreite, die für alle Anforderungen im Ressourcenpool zulässig ist, wenn CPU-Konflikte bestehen.  In Einheiten von virtuellen Kernen|
|**cap_vcores**|Dezimalzahl (5, 2)|Feste Obergrenze der CPU-Bandbreite, die allen Anforderungen im Ressourcenpool zugewiesen wird.  In Einheiten für virtuelle Kerne|
|**instance_cpu_count**|int|Anzahl der für die Instanz konfigurierten CPU|
|**instance_cpu_percent**|Dezimalzahl (5, 2)|CPU-Prozentsatz für die Instanz|
|**instance_vcores**|Dezimalzahl (5, 2)|Anzahl der für die Instanz konfigurierten vcores|
|**delta_log_bytes_used**|Dezimalzahl (5, 2)|Gesamte Protokoll Generierung (in Bytes) auf Poolebene seit der letzten Momentaufnahme|
|**avg_login_rate_percent**|Dezimalzahl (5, 2)|Anzahl von Anmeldungen seit der letzten Momentaufnahme, verglichen mit dem Anmelde Limit|
|**delta_vcores_used**|Dezimalzahl (5, 2)|Computeauslastung in Anzahl der vcores seit der letzten Momentaufnahme.|
|**cap_vcores_used_percent**|Dezimalzahl (5, 2)|Durchschnittliche Computeauslastung als Prozentwert der maximalen Kapazität des Pools.|
|**instance_vcores_used_percent**|Dezimalzahl (5, 2)|Durchschnittliche Compute-Auslastung als Prozentsatz des Limits der SQL-Instanz.|
|**avg_data_io_percent**|Dezimalzahl (5, 2)|Durchschnittliche E/A-Auslastung als Prozentwert der maximalen Kapazität des Pools.|
|**avg_log_write_percent**|Dezimalzahl (5, 2)|Durchschnittliche Auslastung der Schreibressourcen als Prozentwert der maximalen Kapazität des Pools.|
|**avg_storage_percent**|Dezimalzahl (5, 2)|Durchschnittliche Speicherauslastung als Prozentwert der Speicherbeschränkung des Pools.|
|**avg_allocated_storage_percent**|Dezimalzahl (5, 2)|Der Prozentsatz des Daten Speicherplatzes, der von allen Datenbanken im elastischen Pool zugewiesen wird. Dies ist das Verhältnis des Daten Speicherplatzes, der der maximalen Datengröße für den Pool für elastische Datenbanken zugeordnet ist. Weitere Informationen finden Sie unter: Dateispeicher Platz Verwaltung in SQL-DB.|
|**max_worker_percent**|Dezimalzahl (5, 2)|Maximale Anzahl der gleichzeitigen Worker (Anforderungen) als Prozentwert basierend auf der maximalen Kapazität des Pools.|
|**max_session_percent**|Dezimalzahl (5, 2)|Maximale Anzahl der gleichzeitigen Sitzungen als Prozentwert basierend auf der maximalen Kapazität des Pools.|
|||

## <a name="permissions"></a>Berechtigungen

Diese Sicht erfordert die View Server State-Berechtigung.

## <a name="remarks"></a>Hinweise

Benutzer können auf diese dynamische Verwaltungs Sicht zugreifen, um den Ressourcenverbrauch nahezu in Echtzeit für den benutzerworkloadpool sowie systeminterne Pools der Azure SQL-Daten Bank Instanz zu überwachen.

> [!IMPORTANT]
> Die meisten Daten, die von dieser DMV festgestellt werden, sind für den internen Gebrauch vorgesehen und können geändert werden.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel werden die maximalen Protokoll Raten Daten und der Verbrauch bei jeder Momentaufnahme durch den Benutzer Pool zurückgegeben.  

```sql
select snapshot_time, name, max_log_rate_kb, delta_log_bytes_used from sys.dm_resource_governor_resource_pools_history_ex where name like 'UserPool%' order by snapshot_time desc
```

Im folgenden Beispiel werden ähnliche Informationen wie sys. elastic_pool_resource_stats zurückgegeben, ohne eine Verbindung mit dem logischen Master herstellen zu müssen.

```sql
select snapshot_time, name, cap_vcores_used_percent,
  avg_data_io_percent,  
  avg_log_write_percent,
  avg_storage_percent,
  avg_allocated_storage_percent,
  max_data_space_kb,
  max_worker_percent,
  max_session_percent
    from sys.dm_resource_governor_resource_pools_history_ex where name like 'UserPool%' order by snapshot_time desc
```

## <a name="see-also"></a>Weitere Informationen

- [Governanceprotokoll Raten-Governance](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [DTU-Ressourcen Limits für elastische Datenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [Ressourcen Limits für den Ressourcenpool für elastische Datenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
