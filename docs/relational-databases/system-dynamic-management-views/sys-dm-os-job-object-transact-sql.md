---
title: sys. dm_os_job_object (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/11/2020
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
ms.openlocfilehash: b7674e3e7696d91170f9bf955808923d713479a1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "77147409"
---
# <a name="sysdm_os_job_object-azure-sql-database"></a>sys.dm_os_job_object (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Gibt eine einzelne Zeile zurück, die die Konfiguration des Auftrags Objekts beschreibt, das den SQL Server Prozess verwaltet, sowie bestimmte Statistiken zum Ressourcenverbrauch auf Auftrags Objektebene. Gibt eine leere Menge zurück, wenn SQL Server nicht in einem Job-Objekt ausgeführt wird.

Ein Auftrags Objekt ist ein Windows-Konstrukt, das CPU-, Arbeitsspeicher-und e/A-Ressourcenkontrolle auf Betriebssystemebene implementiert. Weitere Informationen zu Auftrags Objekten finden Sie unter [Auftrags Objekte](/windows/desktop/ProcThread/job-objects).
  
|Spalten|Datentyp|BESCHREIBUNG|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|Gibt den Anteil der Prozessor Zyklen an, den die SQL Server Threads während jedes Zeit Planungs Intervalls verwenden können. Der Wert wird als Prozentsatz der verfügbaren Zyklen innerhalb eines 10000-Zyklus-Planungs Intervalls gemeldet. Beispielsweise bedeutet der Wert 100, dass Threads CPU-Kerne verwenden können, deren volle Kapazität erreicht ist.|
|cpu_affinity_mask|**bigint**|Eine Bitmaske, die beschreibt, welche logischen Prozessoren der SQL Server Prozess innerhalb der Prozessor Gruppe verwenden kann. Beispielsweise bedeutet cpu_affinity_mask 255 (1111 1111 in Binary), dass die ersten acht logischen Prozessoren verwendet werden können. <br /><br />Diese Spalte wird aus Gründen der Abwärtskompatibilität bereitgestellt. Die Prozessor Gruppe wird nicht gemeldet, und der gemeldete Wert ist möglicherweise falsch, wenn eine Prozessor Gruppe mehr als 64 logische Prozessoren enthält. Verwenden Sie `process_physical_affinity` die-Spalte, um stattdessen die Prozessor Affinität zu bestimmen.|
|cpu_affinity_group|**int**|Die Nummer der Prozessor Gruppe, die von SQL Server verwendet wird.|
|memory_limit_mb|**bigint**|Die maximale Menge an zugespeichertem Speicher (in MB), die alle Prozesse im Auftrags Objekt, einschließlich SQL Server, kumulativ verwenden können.| 
|process_memory_limit_mb |**bigint**|Die maximale Menge an zugespeichertem Speicher (in MB), die ein einzelner Prozess im Auftrags Objekt (z. b. SQL Server) verwenden kann.|
|workingset_limit_mb |**bigint**|Die maximale Arbeitsspeicher Menge in MB, die der SQL Server Workingset verwenden kann.|
|non_sos_mem_gap_mb|**bigint**|Die Größe des Arbeitsspeichers in MB, der für Thread Stapel, DLLs und andere nicht-SOS-Speicher Belegungen reserviert ist. SOS-Ziel Arbeitsspeicher ist der `process_memory_limit_mb` unter `non_sos_mem_gap_mb`schied zwischen und.| 
|low_mem_signal_threshold_mb|**bigint**|Ein Arbeitsspeicher Schwellenwert (in MB). Wenn die Menge an verfügbarem Arbeitsspeicher für das Auftrags Objekt unter diesem Schwellenwert liegt, wird ein Benachrichtigungs Signal mit geringem Arbeitsspeicher an den SQL Server Prozess gesendet. |
|total_user_time|**bigint**|Die Gesamtanzahl der 100 ns-Ticks, die Threads innerhalb des Auftrags Objekts im Benutzermodus aufgewendet haben, seit das Auftrags Objekt erstellt wurde. |
|total_kernel_time |**bigint**|Die Gesamtanzahl der 100 ns-Ticks, die Threads innerhalb des Auftrags Objekts im Kernel Modus aufgewendet haben, seit das Auftrags Objekt erstellt wurde. |
|write_operation_count |**bigint**|Die Gesamtanzahl der Schreibvorgänge auf lokalen Datenträgern, die von SQL Server seit der Erstellung des Auftrags Objekts ausgegeben wurden. |
|read_operation_count |**bigint**|Die Gesamtanzahl der Lese-e/a-Vorgänge auf lokalen Datenträgern, die von SQL Server seit der Erstellung des Auftrags Objekts ausgegeben wurden. |
|peak_process_memory_used_mb|**bigint**|Die maximale Arbeitsspeicher Menge in MB, die ein einzelner Prozess im Auftrags Objekt, wie z. b. SQL Server, seit der Erstellung des Auftrags Objekts verwendet hat.| 
|peak_job_memory_used_mb|**bigint**|Die Höchstmenge an Arbeitsspeicher in MB, die alle Prozesse im Auftrags Objekt kumulativ seit der Erstellung des Auftrags Objekts verwendet haben.|
|process_physical_affinity|**nvarchar (3072)**|Bitmasken, die beschreiben, welche logischen Prozessoren der SQL Server Prozess in den einzelnen Prozessor Gruppen verwenden kann. Der Wert in dieser Spalte wird durch ein oder mehrere Wertpaare gebildet, die jeweils in geschweiften Klammern eingeschlossen sind. In jedem Paar ist der erste Wert die Prozessor Gruppennummer, und der zweite Wert ist die Affinitäts Bitmaske für diese Prozessor Gruppe. `{{0,a}{1,2}}` Der-Wert bedeutet beispielsweise, dass die Affinitäts Maske für `0` die `a` Prozessor`1010` Gruppe (in Binär Weise, die angibt, dass die Prozessoren 2 und 4 verwendet werden) und die `1` Affinitäts Maske für die Prozessor Gruppe ( `2` `10` in Binär Weise, die angibt, dass Prozessor 2 verwendet wird) ist.|
  
## <a name="permissions"></a>Berechtigungen  
Auf verwaltete SQL-Datenbank-Instanz ist die `VIEW SERVER STATE` -Berechtigung erforderlich. In der SQL-Datenbank ist die `VIEW DATABASE STATE`-Berechtigung für die Datenbank erforderlich.  
 
## <a name="see-also"></a>Weitere Informationen  

Informationen zu verwalteten Instanzen finden Sie unter [verwaltete SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
