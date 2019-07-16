---
title: dm_db_xtp_checkpoint_stats (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026864"
---
# <a name="sysdmdbxtpcheckpointstats-transact-sql"></a>sys.dm_db_xtp_checkpoint_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Gibt Statistiken zu den In-Memory OLTP-Prüfpunktvorgängen in der aktuellen Datenbank zurück. Wenn für die Datenbank keine In-Memory OLTP-Objekte vorhanden sind, wird ein leeres Resultset zurückgegeben.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
```  
USE In_Memory_db_name
SELECT * FROM sys.dm_db_xtp_checkpoint_stats;  
```  
  
**[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterscheidet sich deutlich von neueren Versionen und wird im Thema zur niedriger erläutert [SQL Server 2014](#bkmk_2014).**
  
## <a name="includesssql15includessssql15-mdmd-and-later"></a>[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher  
 Die folgende Tabelle beschreibt die Spalten in `sys.dm_db_xtp_checkpoint_stats`ab **[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]** .  
  
|Spaltenname|Typ|Beschreibung|  
|-----------------|----------|-----------------|  
|last_lsn_processed|**bigint**|Letzte LSN, die vom Controller angezeigt werden.|  
|end_of_log_lsn|**numeric(38)**|Die LSN der das Ende des Protokolls.|  
|bytes_to_end_of_log|**bigint**|Protokollbytes, die nicht verarbeitet, durch den Controller, die für die Bytes zwischen `last_lsn_processed` und `end_of_log_lsn`.|  
|log_consumption_rate|**bigint**|Rate der Transaction Log-Auslastung durch den Controller (in KB/s).|  
|active_scan_time_in_ms|**bigint**|Zeit vom Controller aktiv Scannen des Transaktionsprotokolls.|  
|total_wait_time_in_ms|**bigint**|Kumulierte Wartezeit für den Controller während des Protokolls nicht gescannt.|  
|waits_for_io|**bigint**|Anzahl von Wartevorgängen für Protokoll-e/a durch die controllerthread anfallen.|  
|io_wait_time_in_ms|**bigint**|Kumulierte Wartezeit für Protokoll-e/a vom controllerthread.|  
|waits_for_new_log_count|**bigint**|Anzahl der Wartevorgänge, die durch den controllerthread für ein neues Protokoll zu generierenden anfallen.|  
|new_log_wait_time_in_ms|**bigint**|Kumulierte Wartezeit für ein neues Protokoll vom controllerthread.|  
|idle_attempts_count|**bigint**|Anzahl von Wiederholungen, die der Controller in einen Leerlaufzustand gewechselt.|  
|tx_segments_dispatched|**bigint**|Anzahl von Segmenten, die vom Controller gefunden und wird an die Serialisierungsprogramme verteilt. Segment ist ein zusammenhängender Bereich des Protokolls, die der Serialisierung bildet. Es ist derzeit auf 1MB groß, aber Sie können in Zukunft ändern.|  
|segment_bytes_dispatched|**bigint**|Gesamtzahl der Byte-Anzahl der Bytes, die durch den Controller für Serialisierungsprogramme, weitergeleitet werden, da die Datenbank neu starten.|  
|bytes_serialized|**bigint**|Gesamtanzahl der Bytes, die serialisiert werden, da die Datenbank neu starten.|  
|serializer_user_time_in_ms|**bigint**|Zeit von Serialisierungsprogrammen, im Benutzermodus.|  
|serializer_kernel_time_in_ms|**bigint**|Zeit von Serialisierungsprogrammen im Kernelmodus ausgeführt.|  
|xtp_log_bytes_consumed|**bigint**|Gesamte Anzahl von Protokollbytes, die seit der die Datenbank neu starten.|  
|checkpoints_closed|**bigint**|Anzahl von Prüfpunkten wird geschlossen, weil die Datenbank neu starten.|  
|last_closed_checkpoint_ts|**bigint**|Zeitstempel des letzten Prüfpunkts geschlossen.|  
|hardened_recovery_lsn|**numeric(38)**|Wiederherstellung wird von dieser LSN gestartet.|  
|hardened_root_file_guid|**uniqueidentifier**|GUID der Datei des Stammzertifikats, die als Ergebnis der letzten abgeschlossenen Prüfpunkt festgeschrieben.|  
|hardened_root_file_watermark|**bigint**|**Interne nur**. Wie weit-Datei des Stammzertifikats bis zu gelesen werden kann (Dies ist nur - eine intern relevante Typ Startsequenznummer bezeichnet).|  
|hardened_truncation_lsn|**numeric(38)**|LSN des den Protokollkürzungspunkt dar.|  
|log_bytes_since_last_close|**bigint**|Bytes vom letzten Schließen Sie auf das aktuelle Protokollende.|  
|time_since_last_close_in_ms|**bigint**|Zeit seit der letzten Schließen des Prüfpunkts.|  
|current_checkpoint_id|**bigint**|Derzeit neue Segmenten werden diesen Prüfpunkt zugewiesen wird. Checkpoint Systems handelt es sich um eine Pipeline. Die aktuelle Prüfpunkt wird die Segmente aus dem Protokoll zugeordnet sind. Einen Grenzwert erreicht wurde, wird der Prüfpunkt durch den Controller und eine neue erstellt als aktuell freigegeben.|  
|current_checkpoint_segment_count|**bigint**|Die Anzahl der Segmente in der aktuellen Prüfpunkt.|  
|recovery_lsn_candidate|**bigint**|**Intern nur**. Der Kandidat als Recoverylsn entnommen werden, wenn Current_checkpoint_id geschlossen wird.|  
|outstanding_checkpoint_count|**bigint**|Die Anzahl von Prüfpunkten in der Pipeline, die darauf warten, geschlossen werden.|  
|closing_checkpoint_id|**bigint**|Die ID des Prüfpunkts schließen.<br /><br /> Serialisierungsprogramme arbeiten parallel, also sobald sie fertig sind. Klicken Sie dann der Prüfpunkt ein Kandidat durch Schließen Thread geschlossen werden. Aber der schließende-Thread kann nur jeweils einzeln schließen, und es muss in der Reihenfolge, damit der schließen-Prüfpunkt handelt, in der der Thread schließende arbeitet.|  
|recovery_checkpoint_id|**bigint**|Die ID des Prüfpunkts in der Wiederherstellung verwendet werden.|  
|recovery_checkpoint_ts|**bigint**|Zeitstempel des Wiederherstellungs-Prüfpunkt.|  
|bootstrap_recovery_lsn|**numeric(38)**|Wiederherstellungs-LSN für den Bootstrap-Stil.|  
|bootstrap_root_file_guid|**uniqueidentifier**|GUID der-Datei des Stammzertifikats für den Bootstrap-Stil.|  
|internal_error_code|**bigint**|Fehler, die von einem der Controller, der Serialisierer, geschlossen wurden, und der Merge-Threads angezeigt werden.|
|bytes_of_large_data_serialized|**bigint**|Die Menge der Daten, die serialisiert wurde. |  
  
##  <a name="bkmk_2014"></a> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 Die folgende Tabelle beschreibt die Spalten in `sys.dm_db_xtp_checkpoint_stats`, für die **[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** .  
  
|Spaltenname|Typ|Beschreibung|  
|-----------------|----------|-----------------|  
|log_to_process_in_bytes|**bigint**|Die Anzahl von Protokollbytes zwischen der aktuellen Protokollfolgenummer (LSN) und dem Protokollende des Threads.|  
|total_log_blocks_processed|**bigint**|Gesamtzahl der Protokollblöcke, die seit dem Start des Servers verarbeitet wurden.|  
|total_log_records_processed|**bigint**|Gesamtzahl der Protokolldatensätze, die seit dem Start des Servers verarbeitet wurden.|  
|xtp_log_records_processed|**bigint**|Gesamtzahl der In-Memory OLTP-Protokolldatensätze, die seit dem Start des Servers verarbeitet wurden.|  
|total_wait_time_in_ms|**bigint**|Kumulierte Wartezeit (ms).|  
|waits_for_io|**bigint**|Anzahl von Wartevorgängen für Protokoll-EAs.|  
|io_wait_time_in_ms|**bigint**|Kumulierte Wartezeit für Protokoll-EA.|  
|waits_for_new_log|**bigint**|Anzahl der Wartevorgänge für neu zu erstellendes Protokoll.|  
|new_log_wait_time_in_ms|**bigint**|Kumulierte Wartezeit für neues Protokoll.|  
|log_generated_since_last_checkpoint_in_bytes|**bigint**|Umfang des seit dem letzten In-Memory OLTP-Prüfpunkt generierten Protokolls.|  
|ms_since_last_checkpoint|**bigint**|Zeit in Millisekunden seit dem letzten In-Memory OLTP-Prüfpunkt.|  
|checkpoint_lsn|**numeric (38)**|Die Protokollfolgenummer (LSN) der Wiederherstellung, die dem zuletzt abgeschlossenen OLTP-Prüfpunkt im Arbeitsspeicher zugeordnet ist.|  
|current_lsn|**numeric (38)**|Die LSN des Protokolldatensatzes, der gerade verarbeitet wird.|  
|end_of_log_lsn|**numeric (38)**|Die LSN des Protokollendes.|  
|task_address|**varbinary(8)**|Die Adresse von SOS_Task. Stellen Sie einen Join mit sys.dm_os_tasks her, um weitere Informationen zu suchen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW DATABASE STATE`-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Eine Speicheroptimierte Tabelle dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
