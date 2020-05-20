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
ms.openlocfilehash: 41d360ef2d0e9808f1ef4af49b14354cff637a14
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824723"
---
# <a name="sysdm_cluster_endpoints-transact-sql"></a>sys. dm_cluster_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|name|`sysname`|Name des Dienstanbieter, der extern in einem SQL Big Data-Cluster verfügbar gemacht wird. Eindeutiger Bezeichner für den Endpunkt. Der Schlüssel für diese Ansicht. Lässt keine NULL-Werte zu. |  
|Beschreibung|`nvarchar(4000)`|Beschreibung des Diensts Lässt keine NULL-Werte zu. |
|endpoint|`sysname`|Endpunkt-URL oder Verbindungs Attribut. Lässt keine NULL-Werte zu. |
|protocol_desc|`sysname`|Beschreibung des Endpunkt Protokolls |

## <a name="permissions"></a>Berechtigungen

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist die- `VIEW SERVER STATE` Berechtigung erforderlich.

## <a name="see-also"></a>Weitere Informationen

[Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] ](../../big-data-cluster/big-data-cluster-overview.md)?
