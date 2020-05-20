---
title: sys. dm_hadr_instance_node_map (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sys.dm_hadr_instance_node_map_TSQL
- sys.sys.dm_hadr_instance_node_map
- sys.dm_hadr_instance_node_map_TSQL
- sys.dm_hadr_instance_node_map
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC
- sys.sys.dm_hadr_instance_node_map dynamic management view
ms.assetid: ccfaf62c-9f87-43cf-a5e7-8942e91dd041
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2ae75aa570b20a21c31d75b66ddf5c01635eee51
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830564"
---
# <a name="sysdm_hadr_instance_node_map-transact-sql"></a>sys.dm_hadr_instance_node_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Für jede Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die ein Verfügbarkeits Replikat hostet, das mit der Always on Verfügbarkeits Gruppe verknüpft ist, gibt den Namen des wsfc-Knotens (Windows Server Failover Cluster) zurück, der die Server Instanz hostet. Die dynamische Verwaltungssicht dient für Folgendes:  
  
-   Diese dynamische Verwaltungssicht ist nützlich für das Erkennen einer Verfügbarkeitsgruppe mit mehreren Verfügbarkeitsreplikaten, die im selben WSFC-Knoten gehostet werden, der eine nicht unterstützte Konfiguration ist. Letztere könnte nach einem FCI-Failover auftreten, wenn die Verfügbarkeitsgruppe falsch konfiguriert wird. Weitere Informationen finden Sie unter [Failoverclustering und Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).  
  
-   Wenn mehrere SQL Server-Instanzen auf demselben WSFC-Knoten gehostet werden, verwendet die Ressourcen-DLL diese dynamische Verwaltungssicht, um die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu bestimmen, mit der eine Verbindung hergestellt werden soll.  
   
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**ag_resource_id**|**nvarchar(256)**|Eindeutige ID der Verfügbarkeits Gruppe als Ressource im wsfc.|  
|**instance_name**|**nvarchar(256)**|Name-*Server* / *Instanz*-einer Serverinstanz, die ein Replikat für die Verfügbarkeits Gruppe hostet.|  
|**node_name**|**nvarchar(256)**|Der Name des wsfc-Knotens.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Always on Verfügbarkeits gruppendynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Katalog Sichten für Always on-Verfügbarkeits Gruppen &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Überwachen von Verfügbarkeits Gruppen &#40;Transact-SQL-&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
