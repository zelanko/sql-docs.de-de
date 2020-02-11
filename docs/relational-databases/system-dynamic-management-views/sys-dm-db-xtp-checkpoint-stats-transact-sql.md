---
title: sys. dm_db_xtp_checkpoint_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_checkpoint_stats
- dm_db_xtp_checkpoint_stats_TSQL
- sys.dm_db_xtp_checkpoint_stats
- sys.dm_db_xtp_checkpoint_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_checkpoint_stats dynamic management view
ms.assetid: 8d0b18ca-db4d-4376-9905-3e4457727c46
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 84cbfafdba3bca9b06f250ed9996f0a87e71a18c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68026864"
---
# <a name="sysdm_db_xtp_checkpoint_stats-transact-sql"></a>sys.dm_db_xtp_checkpoint_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Gibt Statistiken zu den In-Memory OLTP-Prüfpunktvorgängen in der aktuellen Datenbank zurück. Wenn für die Datenbank keine In-Memory OLTP-Objekte vorhanden sind, wird ein leeres Resultset zurückgegeben.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
```  
USE In_Memory_db_name
SELECT * FROM sys.dm_db_xtp_checkpoint_stats;  
```  
  
**[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]unterscheidet sich wesentlich von neueren Versionen und wird weiter unten im Thema unter [SQL Server 2014](#bkmk_2014)erläutert.**
  
## <a name="includesssql15includessssql15-mdmd-and-later"></a>[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]und höher  
 In der folgenden Tabelle werden die Spalten `sys.dm_db_xtp_checkpoint_stats`in beschrieben, **[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]** die mit beginnen.  
  
|Spaltenname|type|BESCHREIBUNG|  
|-----------------|----------|-----------------|  
|last_lsn_processed|**BIGINT**|Die letzte LSN, die vom Controller erkannt wird.|  
|end_of_log_lsn|**numerisch (38)**|Die LSN für das Ende des Protokolls.|  
|bytes_to_end_of_log|**BIGINT**|Protokoll bytes, die vom Controller nicht verarbeitet werden, entsprechen den Bytes `last_lsn_processed` zwischen `end_of_log_lsn`und.|  
|log_consumption_rate|**BIGINT**|Rate des Transaktionsprotokoll Verbrauchs durch den Controller (in KB/Sek.).|  
|active_scan_time_in_ms|**BIGINT**|Die Zeit, die der Controller beim aktiven Scannen des Transaktions Protokolls aufgewendet hat.|  
|total_wait_time_in_ms|**BIGINT**|Kumulierte Wartezeit für den Controller, ohne das Protokoll zu scannen.|  
|waits_for_io|**BIGINT**|Anzahl der Warte Vorgänge für Protokoll-e/a-Vorgänge, die durch den Controller Thread|  
|io_wait_time_in_ms|**BIGINT**|Kumulierte Zeit für das warten auf die Protokoll-e/a durch den Controller Thread.|  
|waits_for_new_log_count|**BIGINT**|Anzahl der Warte Vorgänge, die vom Controller Thread für das Generieren eines neuen Protokolls durchgeführt werden.|  
|new_log_wait_time_in_ms|**BIGINT**|Kumulierte Zeit, die für das warten auf ein neues Protokoll durch den Controller Thread aufgewendet wurde.|  
|idle_attempts_count|**BIGINT**|Gibt an, wie oft der Controller in den Leerlauf wechselt.|  
|tx_segments_dispatched|**BIGINT**|Anzahl der Segmente, die vom Controller erkannt und an die serialisierungsinitialisierer gesendet werden. Segment ist ein zusammenhängender Teil des Protokolls, der eine Einheit der Serialisierung bildet. Die Größe beträgt derzeit 1 MB, kann sich jedoch in Zukunft ändern.|  
|segment_bytes_dispatched|**BIGINT**|Die Gesamtanzahl der Bytes, die vom Controller an serialisierungssoren seit dem Neustart der Datenbank gesendet wurden.|  
|bytes_serialized|**BIGINT**|Gesamtanzahl von Bytes, die seit dem Neustart der Datenbank serialisiert wurden.|  
|serializer_user_time_in_ms|**BIGINT**|Die Zeit, die von Serialisierern im Benutzermodus aufgewendet wurde.|  
|serializer_kernel_time_in_ms|**BIGINT**|Die Zeit, die von Serialisierern im Kernel Modus aufgewendet wurde.|  
|xtp_log_bytes_consumed|**BIGINT**|Gesamtanzahl der Protokoll bytes, die seit dem Neustart der Datenbank verbraucht wurden.|  
|checkpoints_closed|**BIGINT**|Anzahl von Prüfpunkten, die seit dem Neustart der Datenbank geschlossen wurden.|  
|last_closed_checkpoint_ts|**BIGINT**|Zeitstempel des letzten geschlossenen Prüf Punkts.|  
|hardened_recovery_lsn|**numerisch (38)**|Die Wiederherstellung wird von dieser LSN gestartet.|  
|hardened_root_file_guid|**uniqueidentifier**|GUID der Stammdatei, die als Ergebnis des letzten abgeschlossenen Prüf Punkts festgeschrieben wurde.|  
|hardened_root_file_watermark|**BIGINT**|**Nur intern**. Gibt an, wie weit es gültig ist, die Stammdatei zu lesen (Hierbei handelt es sich um einen intern relevanten Typ, der nur als BSN bezeichnet wird).|  
|hardened_truncation_lsn|**numerisch (38)**|LSN des abkürzen Punkts.|  
|log_bytes_since_last_close|**BIGINT**|Bytes ab dem letzten Ende des Protokolls.|  
|time_since_last_close_in_ms|**BIGINT**|Die Zeit seit der letzten Schließung des Prüf Punkts.|  
|current_checkpoint_id|**BIGINT**|Diesem Prüfpunkt werden zurzeit neue Segmente zugewiesen. Das Prüf Punkt System ist eine Pipeline. Der aktuelle Prüfpunkt ist der, dem die Segmente aus dem Protokoll zugewiesen werden. Sobald die Grenze erreicht ist, wird der Prüfpunkt vom Controller freigegeben und ein neuer, der als aktueller erstellt wurde.|  
|current_checkpoint_segment_count|**BIGINT**|Anzahl der Segmente im aktuellen Prüfpunkt.|  
|recovery_lsn_candidate|**BIGINT**|**Nur intern**. Kandidat, der als Wiederherstellbarkeit ausgewählt werden soll, wenn current_checkpoint_id geschlossen wird.|  
|outstanding_checkpoint_count|**BIGINT**|Anzahl von Prüfpunkten in der Pipeline, die darauf warten, geschlossen zu werden.|  
|closing_checkpoint_id|**BIGINT**|ID des schließenden Prüf Punkts.<br /><br /> Serialisierungssoren arbeiten parallel. Wenn Sie fertig sind, ist der Prüfpunkt ein Kandidat, der von einem schließenden Thread geschlossen werden soll. Der schließende Thread kann jedoch nur nacheinander geschlossen werden, und er muss sich in der richtigen Reihenfolge befinden, sodass der schließende Prüfpunkt der Wert ist, an dem der schließende Thread arbeitet.|  
|recovery_checkpoint_id|**BIGINT**|ID des Prüf Punkts, der bei der Wiederherstellung verwendet werden soll.|  
|recovery_checkpoint_ts|**BIGINT**|Zeitstempel des Wiederherstellungs Prüf Punkts.|  
|bootstrap_recovery_lsn|**numerisch (38)**|Wiederherstellungs-LSN für den Bootstrap.|  
|bootstrap_root_file_guid|**uniqueidentifier**|GUID der Stammdatei für den Bootstrap.|  
|internal_error_code|**BIGINT**|Fehler, der von einem Controller, Serialisierungsprogramm, Close und Merge-Threads erkannt wird.|
|bytes_of_large_data_serialized|**BIGINT**|Die Menge der Daten, die serialisiert wurde. |  
  
##  <a name="bkmk_2014"></a> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 In der folgenden Tabelle werden die Spalten `sys.dm_db_xtp_checkpoint_stats`in beschrieben **[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]**.  
  
|Spaltenname|type|BESCHREIBUNG|  
|-----------------|----------|-----------------|  
|log_to_process_in_bytes|**BIGINT**|Die Anzahl von Protokollbytes zwischen der aktuellen Protokollfolgenummer (LSN) und dem Protokollende des Threads.|  
|total_log_blocks_processed|**BIGINT**|Gesamtzahl der Protokollblöcke, die seit dem Start des Servers verarbeitet wurden.|  
|total_log_records_processed|**BIGINT**|Gesamtzahl der Protokolldatensätze, die seit dem Start des Servers verarbeitet wurden.|  
|xtp_log_records_processed|**BIGINT**|Gesamtzahl der In-Memory OLTP-Protokolldatensätze, die seit dem Start des Servers verarbeitet wurden.|  
|total_wait_time_in_ms|**BIGINT**|Kumulierte Wartezeit (ms).|  
|waits_for_io|**BIGINT**|Anzahl von Wartevorgängen für Protokoll-EAs.|  
|io_wait_time_in_ms|**BIGINT**|Kumulierte Wartezeit für Protokoll-EA.|  
|waits_for_new_log|**BIGINT**|Anzahl der Wartevorgänge für neu zu erstellendes Protokoll.|  
|new_log_wait_time_in_ms|**BIGINT**|Kumulierte Wartezeit für neues Protokoll.|  
|log_generated_since_last_checkpoint_in_bytes|**BIGINT**|Umfang des seit dem letzten In-Memory OLTP-Prüfpunkt generierten Protokolls.|  
|ms_since_last_checkpoint|**BIGINT**|Zeit in Millisekunden seit dem letzten In-Memory OLTP-Prüfpunkt.|  
|checkpoint_lsn|**numerisch (38)**|Die Protokollfolgenummer (LSN) der Wiederherstellung, die dem zuletzt abgeschlossenen OLTP-Prüfpunkt im Arbeitsspeicher zugeordnet ist.|  
|current_lsn|**numerisch (38)**|Die LSN des Protokolldatensatzes, der gerade verarbeitet wird.|  
|end_of_log_lsn|**numerisch (38)**|Die LSN des Protokollendes.|  
|task_address|**varbinary(8)**|Die Adresse von SOS_Task. Stellen Sie einen Join mit sys.dm_os_tasks her, um weitere Informationen zu suchen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW DATABASE STATE`-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten für Speicher optimierte Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
