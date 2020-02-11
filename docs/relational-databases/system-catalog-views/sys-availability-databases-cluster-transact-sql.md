---
title: sys. availability_databases_cluster (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.availability_databases_cluster_TSQL
- sys.availability_databases_cluster
- availability_databases_cluster_TSQL
- availability_databases_cluster
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.availability_databases_cluster catalog view
- Availability Groups [SQL Server], databases
ms.assetid: 8d9c57e5-7f39-4315-b466-92748231140a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 206c9b1c250cb95a6ad49ccf20f8badf11f870ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046533"
---
# <a name="sysavailability_databases_cluster-transact-sql"></a>sys.availability_databases_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Verfügbarkeits Datenbank in der Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von, die ein Verfügbarkeits Replikat für jede Always on Verfügbarkeits Gruppe im wsfc-Cluster (Windows Server Failover Clustering) hostet, unabhängig davon, ob die lokale Kopie der Datenbank noch mit der Verfügbarkeits Gruppe verknüpft wurde.  
  
> [!NOTE]  
>  Wenn eine Datenbank einer Verfügbarkeitsgruppe hinzugefügt wird, wird die primäre Datenbank automatisch mit der Gruppe verknüpft. Sekundäre Datenbanken müssen auf jedem sekundären Replikat vorbereitet werden, bevor sie mit der Verfügbarkeitsgruppe verknüpft werden können.   
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Eindeutiger Bezeichner der Verfügbarkeitsgruppe, in der die Datenbank enthalten ist, falls vorhanden.<br /><br /> NULL = Datenbank ist kein Teil eines Verfügbarkeitsreplikats einer Verfügbarkeitsgruppe|  
|**group_database_id**|**uniqueidentifier**|Eindeutiger Bezeichner der Datenbank innerhalb der Verfügbarkeitsgruppe, in der die Datenbank enthalten ist, falls vorhanden. **group_database_id** ist für diese Datenbank für das primäre Replikat und für jedes sekundäre Replikat, auf dem die Datenbank der Verfügbarkeits Gruppe hinzugefügt wurde, identisch.<br /><br /> NULL = Datenbank ist kein Teil eines Verfügbarkeitsreplikats einer beliebigen Verfügbarkeitsgruppe|  
|**database_name**|**sysname**|Name der Datenbank, die der Verfügbarkeitsgruppe hinzugefügt wurde.|  
  
## <a name="permissions"></a>Berechtigungen  
 Wenn der Aufrufer von **sys.availability_databases_cluster** nicht der Besitzer der Datenbank ist, sind zum Anzeigen der entsprechenden Zeile mindestens die Berechtigungen ALTER ANY DATABASE oder VIEW ANY DATABASE auf Serverebene oder die CREATE DATABASE-Berechtigung für die **master** -Datenbank oder aktuelle Datenbank erforderlich.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.availability_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys. dm_hadr_database_replica_states &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)   
 [sys. dm_hadr_database_replica_cluster_states &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql.md)   
 [Übersicht zu AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
