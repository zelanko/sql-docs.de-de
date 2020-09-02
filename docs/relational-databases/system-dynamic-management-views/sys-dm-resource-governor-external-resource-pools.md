---
description: sys. dm_resource_governor_external_resource_pools (Transact-SQL)
title: sys. dm_resource_governor_external_resource_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2020
ms.prod: sql
ms.technology: machine-learning-services
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
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 99a85cb9c329752e35f720ec97dabbb417498d3d
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283631"
---
# <a name="sysdm_resource_governor_external_resource_pools-transact-sql"></a>sys. dm_resource_governor_external_resource_pools (Transact-SQL)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Gibt Informationen zum aktuellen Status des externen Ressourcenpools, zur aktuellen Konfiguration von Ressourcenpools und Ressourcenpool Statistiken zurück. 
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Spaltenname      |Datentyp      |BESCHREIBUNG|  
|----------------|---------------|-----------------| 
| external_pool_id|**int**|Die ID des Ressourcenpools. Lässt keine NULL-Werte zu. |
| name|**sysname**|Der Name des Ressourcenpools. Lässt keine NULL-Werte zu. 
| pool_version|**int**|Interne Versionsnummer.|
| max_cpu_percent|**int**|Die aktuelle Konfiguration für die maximale durchschnittliche CPU-Bandbreite, die für alle Anforderungen im Ressourcenpool zulässig ist, wenn CPU-Konflikte bestehen. Lässt keine NULL-Werte zu. |
| max_processes|**int**|Maximale Anzahl gleichzeitiger externer Prozesse. Der Standardwert 0 bedeutet, dass kein Grenzwert festgelegt ist. Lässt keine NULL-Werte zu.|
| max_memory_percent|**int**|Die aktuelle Konfiguration des Prozentsatzes des gesamten Serverspeichers, der für Anforderungen in diesem Ressourcenpool verwendet werden kann. Lässt keine NULL-Werte zu. |
| statistics_start_time|**datetime**|Der Zeitpunkt, zu dem Statistiken für diesen Pool zurückgesetzt wurden. Lässt keine NULL-Werte zu. 
| peak_memory_kb|**bigint**|Die maximale Menge an Arbeitsspeicher in Kilobyte für den Ressourcenpool. Lässt keine NULL-Werte zu. |
| write_io_count|**int**|Die Gesamtanzahl der E/A-Schreibvorgänge, die seit dem Zurücksetzen der Resource Governor-Statistiken ausgegeben wurden. Lässt keine NULL-Werte zu. |
| read_io_count|**int**|Die Gesamtanzahl der E/A-Lesevorgänge, die seit dem Zurücksetzen der Resource Governor-Statistiken ausgegeben wurden. Lässt keine NULL-Werte zu. |
| total_cpu_kernel_ms|**bigint**|Die kumulierte CPU-Benutzerkernelzeit in Millisekunden, seitdem die Resource Governor-Statistiken zurückgesetzt wurden. Lässt keine NULL-Werte zu. |
| total_cpu_user_ms|**bigint**|Die kumulierte CPU-Benutzerzeit in Millisekunden, seitdem die Resource Governor-Statistiken zurückgesetzt wurden. Lässt keine NULL-Werte zu. |
| active_processes_count|**int**|Die Anzahl externer Prozesse, die zum Zeitpunkt der Anforderung ausgeführt werden. Lässt keine NULL-Werte zu. |

 
## <a name="permissions"></a>Berechtigungen

Erfordert die `VIEW SERVER STATE`-Berechtigung.

## <a name="see-also"></a>Weitere Informationen  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
