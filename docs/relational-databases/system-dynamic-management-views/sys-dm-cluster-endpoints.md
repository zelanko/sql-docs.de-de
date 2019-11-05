---
title: sys. DM _cluster_endpoints (Transact-SQL) | Microsoft-Dokumentation
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
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 05076a6b694ff5861c5a7862b1f8f913ddb67fd6
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536170"
---
# <a name="sysdm_cluster_endpoints-transact-sql"></a>sys. DM _cluster_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|name|`sysname`|Name des Dienstanbieter, der extern in einem SQL Big Data-Cluster verfügbar gemacht wird. Eindeutiger Bezeichner für den Endpunkt. Der Schlüssel für diese Ansicht. Lässt keine NULL-Werte zu. |  
|Beschreibung|`nvarchar(4000)`|Die Beschreibung des Dienstanbieter. Lässt keine NULL-Werte zu. |
|Endpunkt|`sysname`|Endpunkt-URL oder Verbindungs Attribut. Lässt keine NULL-Werte zu. |
|protocol_desc|`sysname`|Beschreibung des Endpunkt Protokolls |

## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist `VIEW SERVER STATE`-Berechtigung erforderlich.

## <a name="see-also"></a>Siehe auch

Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)](... /.. /big-data-cluster/big-data-cluster-overview.md)?
