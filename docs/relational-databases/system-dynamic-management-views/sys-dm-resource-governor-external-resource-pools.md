---
title: sys. DM _resource_governor_external_resource_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.technology: machine-learning
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pools_TSQL
- sys.dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_external_resource_pools
- sys.dm_resource_governor_external_resource_pools
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: cf77a073a1432df839bfd13046c66018496e79f1
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68468514"
---
# <a name="sysdmresourcegovernorexternalresourcepools-transact-sql"></a>sys. DM _resource_governor_external_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Gibt Informationen zum aktuellen Status des externen Ressourcenpools, zur aktuellen Konfiguration von Ressourcenpools und Ressourcenpool Statistiken zurück. 
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Name des colmn      |Datentyp      |Beschreibung|  
|----------------|---------------|-----------------| 
| external_pool_id|**int**|Die ID des Ressourcenpools. Lässt keine NULL-Werte zu. |
| NAME|**sysname**|Der Name des Ressourcenpools. Lässt keine NULL-Werte zu. 
| pool_version|**int**|Interne Versionsnummer.|
| max_cpu_percent|**int**|Die aktuelle Konfiguration für die maximale durchschnittliche CPU-Bandbreite, die für alle Anforderungen im Ressourcenpool zulässig ist, wenn CPU-Konflikte bestehen. Lässt keine NULL-Werte zu. |
| max_processes|**int**|Maximale Anzahl gleichzeitiger externer Prozesse. Der Standardwert 0 bedeutet, dass kein Grenzwert festgelegt ist. Lässt keine NULL-Werte zu.|
| max_memory_percent|**int**|Die aktuelle Konfiguration des Prozentsatzes des gesamten Serverspeichers, der für Anforderungen in diesem Ressourcenpool verwendet werden kann. Lässt keine NULL-Werte zu. |
| statistics_start_time|**datetime**|Der Zeitpunkt, zu dem Statistiken für diesen Pool zurückgesetzt wurden. Lässt keine NULL-Werte zu. 
| peak_memory_kb|**bigint**|Die maximale Menge an Arbeitsspeicher in Kilobyte für den Ressourcenpool. Lässt keine NULL-Werte zu. |
| write_io_count|**int**|Die Gesamtanzahl der E/A-Schreibvorgänge, die seit dem Zurücksetzen der Ressourcenkontrollstatistiken ausgegeben wurden. Lässt keine NULL-Werte zu. |
| read_io_count|**int**|Die Gesamtanzahl der E/A-Lesevorgänge, die seit dem Zurücksetzen der Ressourcenkontrollstatistiken ausgegeben wurden. Lässt keine NULL-Werte zu. |
| total_cpu_kernel_ms|**bigint**|Die CPU-Zeit des kumulativen CPU-Benutzers in Millisekunden seit dem Zurücksetzen der Ressourcen-govenstatistik. Lässt keine NULL-Werte zu. |
| total_cpu_user_ms|**bigint**|Die kumulierte CPU-Benutzer Zeit in Millisekunden seit dem Zurücksetzen der Ressourcen-govenstatistik. Lässt keine NULL-Werte zu. |
| active_processes_count|**int**|Die Anzahl externer Prozesse, die zum Zeitpunkt der Anforderung ausgeführt werden. Lässt keine NULL-Werte zu. |

 
## <a name="permissions"></a>Berechtigungen

Erfordert die `VIEW SERVER STATE`-Berechtigung.

## <a name="see-also"></a>Siehe auch  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
