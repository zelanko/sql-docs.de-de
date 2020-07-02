---
title: sys. dm_cluster_endpoints (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, big-data-clusters
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_cluster_endpoints
- dm_cluster_endpoints_TSQL
- dm_cluster_endpoints
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cluster_endpoints dynamic management view
ms.assetid: ''
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 95f251db2efe471455d18f4735be99ecee962a7d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717501"
---
# <a name="sysdm_cluster_endpoints-transact-sql"></a>sys. dm_cluster_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/applies-to-version/sqlserver2019.md)]

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|name|`sysname`|Name des Dienstanbieter, der extern in einem SQL Big Data-Cluster verfügbar gemacht wird. Eindeutiger Bezeichner für den Endpunkt. Der Schlüssel für diese Ansicht. Lässt keine NULL-Werte zu. |  
|description|`nvarchar(4000)`|Beschreibung des Diensts Lässt keine NULL-Werte zu. |
|endpoint|`sysname`|Endpunkt-URL oder Verbindungs Attribut. Lässt keine NULL-Werte zu. |
|protocol_desc|`sysname`|Beschreibung des Endpunkt Protokolls |

## <a name="permissions"></a>Berechtigungen

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist die- `VIEW SERVER STATE` Berechtigung erforderlich.

## <a name="see-also"></a>Weitere Informationen

[Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] ](../../big-data-cluster/big-data-cluster-overview.md)?
