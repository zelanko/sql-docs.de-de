---
title: Sys. availability_read_only_routing_lists (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_read_only_routing_lists_TSQL
- availability_read_only_routing_lists
- sys.availability_read_only_routing_lists
- sys.availability_read_only_routing_lists_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- read-only routing
- Availability Groups [SQL Server], readable secondary replicas
- Availability Groups [SQL Server], read-only routing
- readable secondary replicas
- sys.availability_read_only_routing_lists dynamic management view
ms.assetid: 0686bc5a-c206-41ef-b40a-79a8259d51d2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 48e497c41cc542e54ec4fffa1f97dac5635e0039
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603148"
---
# <a name="sysavailabilityreadonlyroutinglists-transact-sql"></a>sys.availability_read_only_routing_lists (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für die schreibgeschützte Routingliste aller Verfügbarkeitsreplikate zurück, die zu einer Always On-Verfügbarkeitsgruppe im WSFC-Failovercluster gehören.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Eindeutige ID des Verfügbarkeitsreplikats, das die Routingliste besitzt.|  
|**routing_priority**|**int**|Prioritätsreihenfolge nach Routing (1 an erster Stelle, 2 an zweiter Stelle usw.).|  
|**read_only_replica_id**|**uniqueidentifier**|Eindeutige ID des Verfügbarkeitsreplikats, zu der eine schreibgeschützte Arbeitsauslastung weitergeleitet wird.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen für Always On-Verfügbarkeitsgruppen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Katalogsichten Always On-Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Überwachen von Verfügbarkeitsgruppen (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
