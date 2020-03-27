---
title: sys. resource_governor_external_resource_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_external_resource_pools
- sys.resource_governor_external_resource_pools_TSQL
- resource_governor_external_resource_pools
- resource_governor_external_resource_pools_TSQL
helpviewer_keywords:
- sys.resource_governor_external_resource_pools
- resource_governor_external_resource_pools
ms.assetid: 75063e36-a91b-496f-9936-88f3d57bd447
author: stevestein
ms.author: sstein
ms.openlocfilehash: 79c81cafe588fd827ece6184cab5470df8ec4c42
ms.sourcegitcommit: eef5ab1966062e190dc1cd49409bc0429ba6d1e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "80290847"
---
# <a name="sysresource_governor_external_resource_pools-transact-sql"></a>sys. resource_governor_external_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Gilt für:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] und [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Gibt die gespeicherte Konfiguration des externen Ressourcenpools [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in zurück. Jede Zeile der Sicht bestimmt die Konfiguration eines Pools.
  
|Spaltenname|Datentyp|BESCHREIBUNG|
|-----------------|---------------|-----------------|
|external_pool_id|**int**|Eindeutige ID des Ressourcenpools. Lässt keine NULL-Werte zu.|
|name|**sysname**|Name des Ressourcenpools. Lässt keine NULL-Werte zu.|
|max_cpu_percent|**int**|Maximal zulässige durchschnittliche CPU-Bandbreite für alle Anforderungen im Ressourcenpool an, wenn CPU-Konflikte bestehen. Lässt keine NULL-Werte zu.|
|max_memory_percent|**int**|Prozentsatz des gesamten Serverspeichers, der für Anforderungen in diesem Ressourcenpool verwendet werden kann. Lässt keine NULL-Werte zu. Der geltende Höchstwert hängt von den Pool-Mindestwerten ab. So kann für max_memory_percent beispielsweise 100 festgelegt sein, aber der geltende Höchstwert ist niedriger.|
|max_processes|**int**|Maximale Anzahl gleichzeitiger externer Prozesse. Der Standardwert 0 bedeutet, dass kein Grenzwert festgelegt ist. Lässt keine NULL-Werte zu.|
|version|**bigint**|Interne Versionsnummer.|
  
## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="see-also"></a>Weitere Informationen

[Ressourcenkontrolle für Machine Learning in SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[Resource Governor Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)

[sys. dm_resource_governor_resource_pools &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)

[Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md)

[sys. dm_resource_governor_resource_pool_affinity &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[Externe Skripts aktiviert – Serverkonfigurationsoption](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[Alter externer Ressourcen Pool &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
