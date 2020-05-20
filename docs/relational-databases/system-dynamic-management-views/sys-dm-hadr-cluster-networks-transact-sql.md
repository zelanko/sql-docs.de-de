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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dd37e1f39291e12bd313b03b556506eb51eb131d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829364"
---
# <a name="sysdm_hadr_cluster_networks-transact-sql"></a>sys.dm_hadr_cluster_networks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jedes WSFC-Clusterelement zurück, das an der Subnetzkonfiguration einer Verfügbarkeitsgruppe beteiligt ist. Sie können diese dynamische Verwaltungssicht verwenden, um die virtuelle IP-Adresse des Netzwerks zu überprüfen, die für jedes Verfügbarkeitsreplikat konfiguriert ist.  
  
 Primärschlüssel: **MEMBER_NAME**  +  **network_subnet_IP**  +  **network_subnet_prefix_length**  
  
 > [!TIP]
 > Ab [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterstützt diese dynamische Verwaltungs Sicht Always on-Failoverclusterinstanzen zusätzlich zu Always on Verfügbarkeits Gruppen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar(128)**|Der Computername eines Knotens im WSFC-Cluster.|  
|**network_subnet_ip**|**nvarchar (48)**|Die Netzwerk-IP-Adresse des Subnetzes, zu der der Computer gehört. Dies kann eine IPv4- oder eine IPv6-Adresse sein.|  
|**network_subnet_ipv4_mask**|**nvarchar (45)**|Die Netzwerksubnetz-Maske, die das Subnetz angibt, zu dem die IP-Adresse gehört. **network_subnet_ipv4_mask** , um die DHCP-<network_subnet_option> Optionen in einer With DHCP-Klausel der [Create Availability Group](../../t-sql/statements/create-availability-group-transact-sql.md) -oder [Alter Availability Group](../../t-sql/statements/alter-availability-group-transact-sql.md) - [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung anzugeben.<br /><br /> NULL = IPv6-Subnetz.|  
||||  
|**network_subnet_prefix_length**|**int**|Die Präfixlänge der Netzwerk-IP-Adresse, die das Subnetz angibt, zu dem der Computer gehört.|  
|**is_public**|**bit**|Gibt an, ob das Netzwerk im WSFC-Cluster privat oder öffentlich ist. Folgende Werte sind möglich:<br /><br /> 0 = Privat<br /><br /> 1 = Öffentlich|  
|**is_ipv4**|**bit**|Der Typ des Subnetzes. Folgende Werte sind möglich:<br /><br /> 1 = IPv4<br /><br /> 0 = IPv6|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Failoverclustering und Always on-Verfügbarkeits Gruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Überwachen von Verfügbarkeits Gruppen &#40;Transact-SQL-&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys. dm_os_cluster_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [Abfragen der SQL Server System Katalog-FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
