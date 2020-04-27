---
title: sys. dm_hadr_availability_group_states (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_group_states
- sys.dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_group_states dynamic management view
ms.assetid: d18019dd-f8dc-4492-b035-b1a639369b65
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 91efefbdc28480cf2a3b3fb579dba0946dba8a2e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67900779"
---
# <a name="sysdm_hadr_availability_group_states-transact-sql"></a>sys.dm_hadr_availability_group_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Always on Verfügbarkeits Gruppe zurück, die ein Verfügbarkeits Replikat [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in der lokalen Instanz von besitzt. In jede Zeile werden die Statuswerte angezeigt, die den Zustand einer angegebenen Verfügbarkeitsgruppe definieren.  
  
> [!NOTE]  
>  Um die komplette Liste von zu erhalten, Fragen Sie die [sys. availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) -Katalog Sicht ab.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Eindeutiger Bezeichner der Verfügbarkeitsgruppe.|  
|**primary_replica**|**varchar(128)**|Name der Serverinstanz, die das aktuelle primäre Replikat hostet.<br /><br /> NULL = Nicht das primäre Replikat, oder mit dem WSFC-Failovercluster kann nicht kommuniziert werden.|  
|**primary_recovery_health**|**tinyint**|Gibt den Wiederherstellungszustand des primären Replikats an. Folgende Werte sind möglich:<br /><br /> 0 = in Bearbeitung<br /><br /> 1 = Online<br /><br /> NULL<br /><br /> Auf sekundären Replikaten ist die **primary_recovery_health** Spalte NULL.|  
|**primary_recovery_health_desc**|**nvarchar(60)**|Beschreibung der **primary_replica_health**, eine der folgenden:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**secondary_recovery_health**|**tinyint**|Gibt den Wiederherstellungs Zustand eines sekundären Replikat Replikats an. folgende:<br /><br /> 0 = in Bearbeitung<br /><br /> 1 = Online<br /><br /> NULL<br /><br /> Auf dem primären Replikat ist die **secondary_recovery_health** Spalte NULL.|  
|**secondary_recovery_health_desc**|**nvarchar(60)**|Beschreibung der **secondary_recovery_health**, eine der folgenden:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**synchronization_health**|**tinyint**|Gibt einen Rollup des **synchronization_health** aller Verfügbarkeits Replikate in der Verfügbarkeits Gruppe wieder. Unten sind die möglichen Werte und ihre Beschreibungen aufgeführt.<br /><br /> 0: nicht fehlerfrei. Keines der Verfügbarkeits Replikate hat einen fehlerfreien **synchronization_health** (2 = fehlerfrei).<br /><br /> 1: teilweise fehlerfrei. Der Synchronisierungsstatus einiger, aber nicht aller Verfügbarkeitsreplikate ist fehlerfrei.<br /><br /> 2: fehlerfrei. Der Synchronisierungsstatus jedes Verfügbarkeitsreplikats ist fehlerfrei.<br /><br /> Informationen zum Integritäts Status der Replikat Synchronisierung finden Sie in der **synchronization_health** Spalte in [sys. dm_hadr_availability_replica_states &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql.md).|  
|**synchronization_health_desc**|**nvarchar(60)**|Beschreibung der **synchronization_health**, eine der folgenden:<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen von Verfügbarkeits Gruppen &#40;Transact-SQL-&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Always on Verfügbarkeits Gruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Dynamische Verwaltungssichten und -funktionen für Always On-Verfügbarkeitsgruppen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)  
  
  
