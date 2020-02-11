---
title: sys. dm_os_job_object (Azure SQL-Datenbank) | Microsoft-Dokumentation
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
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 43063bb56607d1b5a21ae04b40ee4c7a17825521
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900134"
---
# <a name="sysdm_os_job_object-azure-sql-database"></a>sys.dm_os_job_object (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Gibt eine einzelne Zeile zurück, die die Konfiguration des Auftrags Objekts beschreibt, das den SQL Server Prozess verwaltet, sowie bestimmte Statistiken zum Ressourcenverbrauch auf Auftrags Objektebene. Gibt eine leere Menge zurück, wenn SQL Server nicht in einem Job-Objekt ausgeführt wird. 

Ein Auftrags Objekt ist ein Windows-Konstrukt, das CPU-, Arbeitsspeicher-und e/A-Ressourcenkontrolle auf Betriebssystemebene implementiert. Weitere Informationen zu Auftrags Objekten finden Sie unter [Auftrags Objekte](/windows/desktop/ProcThread/job-objects). 
  
|Spalten|Datentyp|BESCHREIBUNG|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|Gibt den Anteil der Prozessor Zyklen an, den die SQL Server Threads während jedes Zeit Planungs Intervalls verwenden können. Der Wert wird als Prozentsatz der verfügbaren Zyklen innerhalb eines 10000-Zyklus-Planungs Intervalls gemeldet. Beispielsweise bedeutet der Wert 100, dass Threads CPU-Kerne verwenden können, deren volle Kapazität erreicht ist.|
|cpu_affinity_mask|**BIGINT**|Eine Bitmaske, die beschreibt, welche logischen Prozessoren der SQL Server Prozess innerhalb der Prozessor Gruppe verwenden kann. Beispielsweise bedeutet cpu_affinity_mask 255 (1111 1111 in Binary), dass die ersten acht logischen Prozessoren verwendet werden können.|
|cpu_affinity_group|**int**|Die Nummer der Prozessor Gruppe, die von SQL Server verwendet wird.|
|memory_limit_mb|**BIGINT**|Die maximale Menge an zugespeichertem Speicher (in MB), die alle Prozesse im Auftrags Objekt, einschließlich SQL Server, kumulativ verwenden können.| 
|process_memory_limit_mb |**BIGINT**|Die maximale Menge an zugespeichertem Speicher (in MB), die ein einzelner Prozess im Auftrags Objekt (z. b. SQL Server) verwenden kann.|
|workingset_limit_mb |**BIGINT**|Die maximale Arbeitsspeicher Menge in MB, die der SQL Server Workingset verwenden kann.|
|non_sos_mem_gap_mb|**BIGINT**|Die Größe des Arbeitsspeichers in MB, der für Thread Stapel, DLLs und andere nicht-SOS-Speicher Belegungen reserviert ist. SOS-Ziel Arbeitsspeicher ist der `process_memory_limit_mb` unter `non_sos_mem_gap_mb`schied zwischen und.| 
|low_mem_signal_threshold_mb|**BIGINT**|Ein Arbeitsspeicher Schwellenwert (in MB). Wenn die Menge an verfügbarem Arbeitsspeicher für das Auftrags Objekt unter diesem Schwellenwert liegt, wird ein Benachrichtigungs Signal mit geringem Arbeitsspeicher an den SQL Server Prozess gesendet. |
|total_user_time|**BIGINT**|Die Gesamtanzahl der 100 ns-Ticks, die Threads innerhalb des Auftrags Objekts im Benutzermodus aufgewendet haben, seit das Auftrags Objekt erstellt wurde. |
|total_kernel_time |**BIGINT**|Die Gesamtanzahl der 100 ns-Ticks, die Threads innerhalb des Auftrags Objekts im Kernel Modus aufgewendet haben, seit das Auftrags Objekt erstellt wurde. |
|write_operation_count |**BIGINT**|Die Gesamtanzahl der Schreibvorgänge auf lokalen Datenträgern, die von SQL Server seit der Erstellung des Auftrags Objekts ausgegeben wurden. |
|read_operation_count |**BIGINT**|Die Gesamtanzahl der Lese-e/a-Vorgänge auf lokalen Datenträgern, die von SQL Server seit der Erstellung des Auftrags Objekts ausgegeben wurden. |
|peak_process_memory_used_mb|**BIGINT**|Die maximale Arbeitsspeicher Menge in MB, die ein einzelner Prozess im Auftrags Objekt, wie z. b. SQL Server, seit der Erstellung des Auftrags Objekts verwendet hat.| 
|peak_job_memory_used_mb|**BIGINT**|Die Höchstmenge an Arbeitsspeicher in MB, die alle Prozesse im Auftrags Objekt kumulativ seit der Erstellung des Auftrags Objekts verwendet haben.|
  
## <a name="permissions"></a>Berechtigungen  
Auf verwaltete SQL-Datenbank-Instanz ist die `VIEW SERVER STATE` -Berechtigung erforderlich. In der SQL-Datenbank ist die `VIEW DATABASE STATE`-Berechtigung für die Datenbank erforderlich.  
 
## <a name="see-also"></a>Weitere Informationen  

Informationen zu verwalteten Instanzen finden Sie unter [verwaltete SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
