---
title: sys. DM _dm_compute_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, big-data-clusters
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_dm_compute_pools
- dm_dm_compute_pools_TSQL
- dm_dm_compute_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_dm_compute_pools dynamic management view
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 0b21f517b540c69822dd8b1da4aa6a4cf8b8616f
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532958"
---
# <a name="sysdm_dm_compute_pools-transact-sql"></a>sys. DM _dm_compute_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|name|`sysname`|Der Name des computepools. Lässt keine NULL-Werte zu. Gibt `default` für den standardcomputepool zurück. |
|compute_pool_id|`int`|Eindeutiger Bezeichner für den Pool. Der Schlüssel für diese Ansicht.|  
|location|`sysname`|Endpunkt zu Controller in einem SQL-Big Data-Cluster. Lässt keine NULL-Werte zu. |

## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist `VIEW SERVER STATE`-Berechtigung erforderlich.

## <a name="see-also"></a>Siehe auch

[Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)]](../../big-data-cluster/big-data-cluster-overview.md)?
