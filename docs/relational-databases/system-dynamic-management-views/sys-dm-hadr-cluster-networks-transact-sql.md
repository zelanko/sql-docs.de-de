---
title: sys. dm_hadr_cluster_networks (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_hadr_cluster_networks
- sys.dm_hadr_cluster_networks_TSQL
- sys.dm_hadr_cluster_networks
- dm_hadr_cluster_networks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_networks dynamic management view
ms.assetid: ece32b15-d63f-4f93-92b7-e2930333e97a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0b2475a3881cb73d9dd82ee7fc311e7288aa4738
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900647"
---
# <a name="sysdm_hadr_cluster_networks-transact-sql"></a>sys.dm_hadr_cluster_networks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jedes WSFC-Clusterelement zurück, das an der Subnetzkonfiguration einer Verfügbarkeitsgruppe beteiligt ist. Sie können diese dynamische Verwaltungssicht verwenden, um die virtuelle IP-Adresse des Netzwerks zu überprüfen, die für jedes Verfügbarkeitsreplikat konfiguriert ist.  
  
 Primärschlüssel: **MEMBER_NAME** + **network_subnet_IP** + **network_subnet_prefix_length**  
  
 > [!TIP]
 > [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]Ab unterstützt diese dynamische Verwaltungs Sicht Always on-Failoverclusterinstanzen zusätzlich zu Always on Verfügbarkeits Gruppen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar(128)**|Der Computername eines Knotens im WSFC-Cluster.|  
|**network_subnet_ip**|**nvarchar (48)**|Die Netzwerk-IP-Adresse des Subnetzes, zu der der Computer gehört. Dies kann eine IPv4- oder eine IPv6-Adresse sein.|  
|**network_subnet_ipv4_mask**|**nvarchar (45)**|Die Netzwerksubnetz-Maske, die das Subnetz angibt, zu dem die IP-Adresse gehört. **network_subnet_ipv4_mask** , um die DHCP-<network_subnet_option> Optionen in einer With DHCP-Klausel der [Create Availability Group](../../t-sql/statements/create-availability-group-transact-sql.md) -oder [Alter Availability Group](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung anzugeben.<br /><br /> NULL = IPv6-Subnetz.|  
||||  
|**network_subnet_prefix_length**|**int**|Die Präfixlänge der Netzwerk-IP-Adresse, die das Subnetz angibt, zu dem der Computer gehört.|  
|**is_public**|**bit**|Gibt an, ob das Netzwerk im WSFC-Cluster privat oder öffentlich ist. Folgende Werte sind möglich:<br /><br /> 0 = Privat<br /><br /> 1 = Öffentlich|  
|**is_ipv4**|**bit**|Der Typ des Subnetzes. Folgende Werte sind möglich:<br /><br /> 1 = IPv4<br /><br /> 0 = IPv6|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Failoverclustering und Always On-Verfügbarkeitsgruppen (SQL Server)](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Überwachen von Verfügbarkeitsgruppen (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys. dm_os_cluster_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [Abfragen der SQL Server System Katalog-FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
