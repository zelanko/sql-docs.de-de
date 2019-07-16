---
title: Sys. dm_hadr_cluster_members (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_cluster_members_TSQL
- sys.dm_hadr_cluster_members
- dm_hadr_cluster_members_TSQL
- dm_hadr_cluster_members
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_members catalog view
ms.assetid: feb20b3a-8835-41d3-9a1c-91d3117bc170
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8b28b708aabfdf3ec4e569aab6d8a95e2330b370
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900766"
---
# <a name="sysdmhadrclustermembers-transact-sql"></a>sys.dm_hadr_cluster_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Wenn der WSFC-Knoten, der eine lokale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -fähige Instanz von [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] hostet, über ein WSFC-Quorum verfügt, wird eine Zeile für jedes Element, aus denen das Quorum besteht, einschließlich Elementstatus zurückgegeben. Dazu gehören alle Knoten in dem Cluster (zurückgegeben von der Funktion **Clusterenum** mit dem Typ CLUSTER_ENUM_NODE) sowie die Datenträger- bzw. Dateifreigabenzeugen. Die für ein bestimmtes Element zurückgegebene Zeile enthält Informationen zum Status dieses Elements. Beispiel: Für einen Cluster mit fünf Knoten mit Mehrheitsknotenquorum, in dem ein Knoten heruntergefahren ist, stellt **sys.dm_hadr_cluster_members** den Status des heruntergefahrenen Knotens als "NODE_DOWN" dar, wenn [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] sys.dm_hadr_cluster_members **von einer Serverinstanz aus abgefragt wird, die** -fähig ist und sich in einem Knoten mit Quorum befindet.  
  
 Wenn der WSFC-Knoten nicht über ein Quorum verfügt, werden keine Zeilen zurückgegeben.  
  
 Mithilfe dieser dynamischen Verwaltungssicht können Sie beispielsweise folgende Fragen beantworten:  
  
-   Welche Knoten werden derzeit auf dem WSFC-Cluster ausgeführt?  
  
-   Wie viele weitere Fehler kann der WSFC-Cluster tolerieren, bevor er sein Quorum in einem Szenario mit einem Mehrheitsknoten verliert?  

 > [!TIP]
 > Ab [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], diese dynamische verwaltungssicht unterstützt immer auf Failoverclusterinstanzen zusätzlich zu AlwaysOn-Verfügbarkeitsgruppen.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar(128)**|Der Elementname, der ein Computername, ein Laufwerkbuchstabe oder ein Dateifreigabepfad sein kann.|  
|**member_type**|**tinyint**|Der Typ des Elements. Folgende Werte sind möglich:<br /><br /> 0 = WSFC-Knoten<br /><br /> 1 = Datenträgerzeuge<br /><br /> 2 = Dateifreigabenzeuge<br /><br /> 3 = Cloudzeugen|  
|**member_type_desc**|**nvarchar(50)**|Beschreibung von **member_type**. Folgende Werte sind möglich:<br /><br /> CLUSTER_NODE<br /><br /> DISK_WITNESS<br /><br /> FILE_SHARE_WITNESS<br /><br /> CLOUD_WITNESS|  
|**member_state**|**tinyint**|Der Status des Elements. Folgende Werte sind möglich:<br /><br /> 0 = Offline<br /><br /> 1 = Online|  
|**member_state_desc**|**nvarchar(60)**|Beschreibung von **member_state**. Folgende Werte sind möglich:<br /><br /> UP<br /><br /> NACH UNTEN|  
|**number_of_quorum_votes**|**tinyint**|Anzahl von Quorumabstimmungen, die im Besitz dieses Quorumelements sind. Wenn keine Mehrheit: Nur Datenträger-Quorumstypen ist dieser Wert 0. Für andere Quorumstypen wird dieser Wert standardmäßig auf "1" festgelegt.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen für Always On-Verfügbarkeitsgruppen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Katalogsichten Always On-Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Überwachen von Verfügbarkeitsgruppen (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
