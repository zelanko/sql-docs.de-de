---
title: Sys.dm_os_job_object (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/17/2018
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 074981f19f0eb74a7e7c7d4e82466957f0ff98b8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047044"
---
# <a name="sysdmosjobobject-azure-sql-database"></a>Sys.dm_os_job_object (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Gibt eine einzelne Zeile, beschreibt die Konfiguration des Auftragsobjekts, die SQL Server-Prozess als auch bestimmte Ressourcenstatistiken für die Nutzung auf Objektebene Auftrag verwaltet. Gibt ein leeres Resultset zurück, wenn SQL Server nicht in ein Job-Objekt ausgeführt wird. 

Ein Job-Objekt ist ein Windows-Konstrukt, die CPU, Arbeitsspeicher und e/a-Ressourcenkontrolle auf Betriebssystemebene implementiert. Weitere Informationen zu Auftragsobjekte, finden Sie unter [Auftragsobjekte](/windows/desktop/ProcThread/job-objects). 
  
|Spalte|Datentyp|Beschreibung|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|Gibt an, der Teil der Prozessorzyklen an, denen die SQL Server-Threads während jedes Intervall für die Planung verwenden können. Der Wert wird als Prozentsatz der verfügbaren Zyklen in ein Intervall für die Planung der 10000-Zyklus gemeldet. Beispielsweise gibt der Wert 100 bedeutet, dass Threads CPU-Kerne nutzt der vollen Kapazität.|
|cpu_affinity_mask|**bigint**|Eine Bitmaske, die Beschreibung der logischen Prozessoren kann SQL Server-Prozess in der Gruppe "Prozessor" verwenden. Z. B. Cpu_affinity_mask 255 (1111 1111 binär) bedeutet, dass die ersten acht logische Prozessoren verwendet werden können.|
|cpu_affinity_group|**int**|Die Anzahl der Prozessoren an, die von SQL Server verwendet wird.|
|memory_limit_mb|**bigint**|Die maximale Menge des zugesicherten Arbeitsspeichers in MB, die alle Prozesse des Auftragsobjekts, einschließlich SQL Server, kumulativ verwenden können.| 
|process_memory_limit_mb |**bigint**|Die maximale Menge des zugesicherten Arbeitsspeichers in MB, die einen einzelner Prozess des Auftragsobjekts, z.B. SQL Server, verwenden können.|
|workingset_limit_mb |**bigint**|Die Höchstmenge des Speichers in MB, der das SQL Server-Workingset verwenden kann.|
|non_sos_mem_gap_mb|**bigint**|Die Menge des Arbeitsspeichers in MB, reservieren Sie für Threadstapel, DLLs und andere nicht-SOS-speicherbelegungen. SOS-Zielspeicher ist der Unterschied zwischen `process_memory_limit_mb` und `non_sos_mem_gap_mb`.| 
|low_mem_signal_threshold_mb|**bigint**|Ein Speichergrenzwert in MB. Wenn die Menge des verfügbaren Arbeitsspeichers für das Auftragsobjekt unter diesem Schwellenwert liegt, wird ein wenig Arbeitsspeicher-Notification-Signal an den SQL Server-Prozess gesendet. |
|total_user_time|**bigint**|Die Gesamtanzahl von 100 ns-Ticks, die Threads in das Auftragsobjekt im Benutzermodus, verbracht haben, da das Auftragsobjekt erstellt wurde. |
|total_kernel_time |**bigint**|Die Gesamtanzahl von 100 ns-Ticks, die Threads in das Auftragsobjekt im Kernelmodus, verbracht haben, da das Auftragsobjekt erstellt wurde. |
|write_operation_count |**bigint**|Die Gesamtanzahl der schreiben e/a-Vorgänge auf lokalen Datenträgern, die von SQL Server ausgegeben werden, da das Auftragsobjekt erstellt wurde. |
|read_operation_count |**bigint**|Die Gesamtanzahl der e/a-Lesevorgänge auf lokalen Datenträgern, die von SQL Server ausgegeben werden, da das Auftragsobjekt erstellt wurde. |
|peak_process_memory_used_mb|**bigint**|Die maximale Arbeitsspeichermenge in MB, die Verarbeitung einer einzelnen des Auftragsobjekts, z.B. SQL Server, wurde verwendet, da das Auftragsobjekt erstellt wurde.| 
|peak_job_memory_used_mb|**bigint**|Die maximale Arbeitsspeichermenge in MB, die alle Prozesse des Auftragsobjekts kumulativ, da das Auftragsobjekt verwendet haben wurde erstellt.|
  
## <a name="permissions"></a>Berechtigungen  
Für verwaltete SQL-Datenbankinstanz, erfordert `VIEW SERVER STATE` Berechtigung. Für SQL-Datenbank erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.  
 
## <a name="see-also"></a>Siehe auch  

Weitere Informationen zu verwalteten Instanzen finden Sie unter [verwaltete SQL-Datenbankinstanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
