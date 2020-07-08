---
title: sys. dm_resource_governor_external_resource_pool_affinity (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6d583ec570c7532fbafc354d4d5c70016a8cebd1
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053140"
---
# <a name="sysdm_resource_governor_external_resource_pool_affinity-transact-sql"></a>sys. dm_resource_governor_external_resource_pool_affinity (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]
**Gilt für:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]und [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Gibt CPU-Affinitäts Informationen über die aktuelle Konfiguration des externen Ressourcenpools zurück.
  
|Spaltenname|Datentyp|BESCHREIBUNG|
|----------------|---------------|-----------------|
|pool_id|**int**|Die ID des externen Ressourcenpools. Lässt keine NULL-Werte zu.|
|processor_group|**smallint**|Die ID der logischen Windows-Prozessorgruppe. Lässt keine NULL-Werte zu.|
|cpu_mask|**bigint**|Die binäre Maske, die die diesem Pool zugeordneten CPUs darstellt. Lässt keine NULL-Werte zu.|
  
## <a name="remarks"></a>Hinweise

Pools, die mit einer Affinität von erstellt werden, werden `AUTO` in dieser Sicht nicht angezeigt, weil Sie keine Affinität haben. Weitere Informationen finden Sie unter [Erstellen eines externen Ressourcenpools &#40;Transact-SQL-&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md) und [Alter externer Ressourcenpool &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md) Anweisungen.

## <a name="permissions"></a>Berechtigungen

Erfordert die `VIEW SERVER STATE`-Berechtigung.

## <a name="see-also"></a>Weitere Informationen

[Resource governance for machine learning in SQL Server (Ressourcenkontrolle für Machine Learning in SQL Server)](../../machine-learning/administration/resource-governor.md)

[sys. dm_resource_governor_resource_pool_affinity &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[Externe Skripts aktiviert (Serverkonfigurationsoption)](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
