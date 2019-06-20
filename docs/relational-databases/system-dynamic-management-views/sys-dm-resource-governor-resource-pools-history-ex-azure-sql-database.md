---
title: Sys.dm_resource_governor_resource_pools_history_ex (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/27/2019
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
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
manager: craigg
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: d585f1f1245457aa9051f25bca696cf4495d93ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66743927"
---
# <a name="sysdmresourcegovernorresourcepoolshistoryex-transact-sql"></a>sys.dm_resource_governor_resource_pools_history_ex (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Gibt die Momentaufnahme in Intervallen von 15 Sekunden für die letzten 30 Minuten der Resource pools Statistiken für eine Azure SQL-Datenbank.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**pool_id**|ssNoversion|Die ID des Ressourcenpools. Lässt keine NULL-Werte zu.
|**name**|sysname|Der Name des Ressourcenpools. Lässt keine NULL-Werte zu.|
|**snapshot_time**|datetime2|Datum/Uhrzeit der Resource Pool Stats Momentaufnahme|
|**duration_ms**|ssNoversion|Dauer zwischen aktuellen und vorherigen Momentaufnahme|
|**statistics_start_time**|datetime2|Der Zeitpunkt, zu dem Statistiken für diesen Pool zurückgesetzt wurden. Lässt keine NULL-Werte zu.|
|**active_session_count**|ssNoversion|Gesamtanzahl der aktiven Sitzungen in der aktuellen Momentaufnahme|
|**active_worker_count**|ssNoversion|Gesamtanzahl an Workern in der aktuellen Momentaufnahme|
|**delta_cpu_usage_ms**|ssNoversion|CPU-Auslastung in Millisekunden seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_cpu_usage_preemptive_ms**|ssNoversion|PreEmptive-win32-Aufrufe steuern nicht von SQL-CPU-RG, seit der letzten Momentaufnahme|
|**used_data_space_kb**|BIGINT|In den Benutzerdatenbanken Benutzerpool zugeordneten belegter Gesamtspeicherplatz|
|**allocated_disk_space_kb**|BIGINT|Gesamtdaten Dateigröße von Benutzerdatenbanken in der zugeordneten mit Benutzerpool|
|**target_memory_kb**|BIGINT|Die Zielmenge an Arbeitsspeicher in Kilobyte, die der Ressourcenpool zu erlangen versucht. Dies basiert auf den aktuellen Einstellungen und dem Serverstatus. Lässt keine NULL-Werte zu.|
|**used_memory_kb**|BIGINT|Der Arbeitsspeicher in Kilobyte, der für den Ressourcenpool verwendet wird. Lässt keine NULL-Werte zu.|
|**cache_memory_kb**|BIGINT|Die gesamte aktuelle Cachespeicherverwendung in Kilobyte. Lässt keine NULL-Werte zu.|
|**compile_memory_kb**|BIGINT|Die aktuell verwendete (gestohlene) Arbeitsspeicher in Kilobyte (KB). Der Arbeitsspeicher wird hierbei hauptsächlich für die Kompilierung und Optimierung verwendet, kann jedoch auch zu anderen Zwecken verwendet werden. Lässt keine NULL-Werte zu.|
|**active_memgrant_count**|BIGINT|Die aktuelle Anzahl von Arbeitsspeicherzuweisungen. Lässt keine NULL-Werte zu.|
|**active_memgrant_kb**|BIGINT|Die Summe der aktuellen Arbeitsspeicherzuweisungen in Kilobyte (KB). Lässt keine NULL-Werte zu.|
|**used_memgrant_kb**|BIGINT|Der gesamte aktuell verwendete (gestohlene) Arbeitsspeicher aus der Arbeitsspeicherzuweisung. Lässt keine NULL-Werte zu.|
|**delta_memgrant_timeout_count**|ssNoversion|arbeitsspeicherzuweisungs-Timeouts in diesem Ressourcenpool in diesem Zeitraum. Lässt keine NULL-Werte zu.|
|**delta_memgrant_waiter_count**|ssNoversion|Die Anzahl von zurzeit ausstehenden Abfragen für Arbeitsspeicherzuweisungen. Lässt keine NULL-Werte zu.|
|**delta_out_of_memory_count**|ssNoversion|Die Anzahl der speicherbelegungsfehler im Pool seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_io_queued**|ssNoversion|Die Gesamtanzahl Lesevorgänge in die Warteschlange eingereiht, seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_read_io_issued**|ssNoversion|Die Gesamtanzahl Lesevorgänge seit der letzten Momentaufnahme ausgegeben. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_read_io_completed**|ssNoversion|Die Gesamtanzahl Lesevorgänge abgeschlossen, die seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_io_throttled**|ssNoversion|Die Gesamtanzahl Lesevorgänge gedrosselt, die seit der Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_read_bytes**|BIGINT|Die Gesamtanzahl von Bytes lesen seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_io_stall_ms**|ssNoversion|Die Gesamtzeit (in Millisekunden) zwischen dem Lesen e/a-Eingang und Abschluss seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_read_io_stall_queued_ms**|ssNoversion|Die Gesamtzeit (in Millisekunden) zwischen dem Lesen e/a-Eingang und Problem seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden. Ungleich 0 Delta_read_io_stall_queued_ms bedeutet, dass es sich bei e/a von RG bedingt ist.|
|**delta_write_io_queued**|ssNoversion|Die Gesamtanzahl Schreibvorgänge in die Warteschlange eingereiht, seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_write_io_issued**|ssNoversion|Die Gesamtanzahl Schreibvorgänge seit der letzten Momentaufnahme ausgegeben. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_write_io_completed**|ssNoversion|Die Gesamtanzahl Schreibvorgänge abgeschlossen, die seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_write_io_throttled**|ssNoversion|Der gesamte Schreibvorgang gedrosselt IOs seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_write_bytes**|BIGINT|Die Gesamtanzahl der seit der letzten Momentaufnahme geschriebenen Bytes. Lässt keine NULL-Werte zu.|
|**delta_write_io_stall_ms**|ssNoversion|Die Gesamtzeit (in Millisekunden) zwischen dem Write-e/a-Eingang und Abschluss seit der letzten Momentaufnahme. Lässt keine NULL-Werte zu.|
|**delta_write_io_stall_queued_ms**|ssNoversion|Die Gesamtzeit (in Millisekunden) zwischen dem Eingang der Write-e/a-"und" Problem seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**delta_io_issue_delay_ms**|ssNoversion|Die Gesamtzeit (in Millisekunden) zwischen der geplanten Ausgabe und tatsächlichen Ausgabe von e/a seit der letzten Momentaufnahme. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**max_iops_per_volume**|ssNoversion|Die maximale e/a pro Sekunde (IOPS) pro volumeeinstellung für diesen Pool. Lässt NULL-Werte zu. NULL, wenn E/A-Vorgänge für den Ressourcenpool nicht kontrolliert werden.|
|**max_memory_kb**|BIGINT|Die maximale Arbeitsspeichermenge in Kilobyte, über die der Ressourcenpool verfügen kann. Dies basiert auf den aktuellen Einstellungen und dem Serverstatus. Lässt keine NULL-Werte zu.
|**max_log_rate_kb**|BIGINT|Maximale protokollrate (Kilobyte pro Sekunde) auf ressourcengruppenebene-Pool.|
|**max_data_space_kb**|BIGINT|Höchstwerte für Pools für elastische Datenbanken Speichergrenzwert für diesen Pool für elastische Datenbanken in Kilobyte.|
|**max_session**|ssNoversion|Maximale Sitzungen für den pool|
|**max_worker**|ssNoversion|Begrenzung für Worker für den pool|
|**min_cpu_percent**|ssNoversion|Die aktuelle Konfiguration für die garantierte durchschnittliche CPU-Bandbreite für alle Anforderungen im Ressourcenpool, wenn CPU-Konflikte bestehen. Lässt keine NULL-Werte zu.|
|**max_cpu_percent**|ssNoversion|Die aktuelle Konfiguration für die maximale durchschnittliche CPU-Bandbreite, die für alle Anforderungen im Ressourcenpool zulässig ist, wenn CPU-Konflikte bestehen. Lässt keine NULL-Werte zu.|
|**cap_cpu_percent**|ssNoversion|Feste Obergrenze der CPU-Bandbreite, die allen Anforderungen im Ressourcenpool zugewiesen wird. Beschränkt die maximale CPU-Bandbreitenstufe auf die angegebene Stufe. Der zulässige Bereich für den Wert ist 1 bis 100. Lässt keine NULL-Werte zu.|
|**min_vcores**|decimal(5,2) wird|Die aktuelle Konfiguration für die garantierte durchschnittliche CPU-Bandbreite für alle Anforderungen im Ressourcenpool, wenn CPU-Konflikte bestehen.  In Einheiten von virtuellen Kernen|
|**max_vcores**|decimal(5,2) wird|Die aktuelle Konfiguration für die maximale durchschnittliche CPU-Bandbreite, die für alle Anforderungen im Ressourcenpool zulässig ist, wenn CPU-Konflikte bestehen.  In der Einheit von virtuellen Kernen|
|**cap_vcores**|decimal(5,2) wird|Feste Obergrenze der CPU-Bandbreite, die allen Anforderungen im Ressourcenpool zugewiesen wird.  In virtuellen Kernen-Komponente|
|**instance_cpu_count**|ssNoversion|Anzahl von CPUS, die für die Instanz konfiguriert|
|**instance_cpu_percent|decimal(5,2) wird|CPU-Prozentsatz für die Instanz konfiguriert|
|**instance_vcores**|decimal(5,2) wird|Anzahl von virtuellen Kernen, die für die Instanz konfiguriert|
|**delta_log_bytes_used**|decimal(5,2) wird|Gesamtprotokoll Generierung (in Byte) auf der Poolebene seit der letzten Momentaufnahme|
|**avg_login_rate_percent**|decimal(5,2) wird|Anzahl der Anmeldeversuche seit der letzten Momentaufnahme, mit der Grenzwert für Anmeldungen verglichen|
|**delta_vcores_used**|decimal(5,2) wird|Die servernutzung als Anzahl von virtuellen Kernen seit der letzten Momentaufnahme.|
|**cap_vcores_used_percent**|decimal(5,2) wird|Durchschnittliche computeauslastung als Prozentwert der maximalen Kapazität des Pools an.|
|**instance_vcores_used_percent**|decimal(5,2) wird|Durchschnittliche computeauslastung als Prozentwert der maximalen Kapazität der SQL-Instanz an.|
|**avg_data_io_percent**|decimal(5,2) wird|Durchschnittliche e/a-Auslastung als Prozentwert der maximalen Kapazität des Pools.|
|**avg_log_write_percent**|decimal(5,2) wird|Durchschnittliche Schreibressourcen als Prozentwert der maximalen Kapazität des Pools.|
|**avg_storage_percent**|decimal(5,2) wird|Durchschnittliche speicherauslastung als Prozentwert der speicherbeschränkung des Pools.|
|**avg_allocated_storage_percent**|decimal(5,2) wird|Der Prozentsatz an Datenspeicherplatz, von allen Datenbanken im Pool für elastische Datenbanken. Dies ist das Verhältnis des Datenspeicherplatzes, die Daten die maximale Größe für den elastischen Pool zugeordnet. Weitere Informationen finden Sie unter: Verwaltung von Übersetzungsdateien Speicherplatz in SQL-Datenbank|
|**max_worker_percent**|decimal(5,2) wird|Maximale gleichzeitige Worker (Anforderungen) als Prozentwert der maximalen Kapazität des Pools.|
|**max_session_percent**|decimal(5,2) wird|Maximaler gleichzeitiger Sitzungen als Prozentwert der maximalen Kapazität des Pools.|
|||

## <a name="permissions"></a>Berechtigungen

Diese Sicht erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="remarks"></a>Hinweise

Benutzer können diese dynamische verwaltungssicht, near Real-Time-Ressourcenverbrauch für arbeitsauslastungspool Benutzer als auch für interne Systempools der Azure SQL-Datenbank-Instanz überwachen zugreifen.

> [!IMPORTANT]
> Die meisten Daten, die von dieser DMV verfügbar gemacht, die für den internen Gebrauch vorgesehen ist und unterliegt Änderungen.

## <a name="examples"></a>Beispiele

Das folgende Beispiel gibt die maximale Rate-Protokolldaten und Verbrauch auf jede Momentaufnahme von Benutzerpool  

```sql
select snapshot_time, name, max_log_rate_kb, delta_log_bytes_used from sys.dm_resource_governor_resource_pools_history_ex where name like 'UserPool%' order by snapshot_time desc
```

Im folgende Beispiel gibt ähnliche Informationen als Sys. elastic_pool_resource_stats zurück, wenn keine Verbindung zum logischen Master

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

## <a name="see-also"></a>Siehe auch

- [Übersetzung Log Rate governance](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Ressourceneinschränkungen für Pools für elastische Datenbanken DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [VCore-ressourceneinschränkungen für Pools für elastische Datenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
