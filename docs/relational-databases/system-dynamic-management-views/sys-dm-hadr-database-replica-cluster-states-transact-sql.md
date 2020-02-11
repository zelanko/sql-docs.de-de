---
title: sys. dm_hadr_database_replica_cluster_states (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_database_replica_cluster_states
- dm_hadr_database_replica_cluster_states_TSQL
- sys.dm_hadr_database_replica_cluster_states_TSQL
- dm_hadr_database_replica_cluster_states
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_database_replica_cluster_states dynamic management view
ms.assetid: 6f719071-ebce-470d-aebd-1f55ee8cd70a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2fbd066113f5ad4394b83e0151643ab9ea3b7b82
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900668"
---
# <a name="sysdm_hadr_database_replica_cluster_states-transact-sql"></a>sys.dm_hadr_database_replica_cluster_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile mit Informationen zurück, die Aufschluss über die Integrität der Verfügbarkeitsdatenbanken in den Always On-Verfügbarkeitsgruppen in jeder Always On-Verfügbarkeitsgruppe im WSFC-Cluster (Windows Server Failover Clustering) geben sollen. Fragen Sie **sys. dm_hadr_database_replica_states** ab, um die folgenden Fragen zu beantworten:  
  
-   Sind alle Datenbanken in einer Verfügbarkeitsgruppe für ein Failover bereit?  
  
-   Wurde eine sekundäre Datenbank nach einem erzwungenen Failover lokal angehalten, und wurde das neue primäre Replikat über diesen Status informiert?  
  
-   Bei welchem sekundären Replikat wäre der Datenverlust am geringsten, wenn es zum primären Replikat würde, weil das primäre Replikat derzeit nicht verfügbar wäre?  
  
-   Wenn der Wert der Spalte [sys. Database](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)   **log_reuse_wait_desc** "AVAILABILITY_REPLICA" ist, wird das sekundäre Replikat in einer Verfügbarkeits Gruppe die Protokoll Verkürzung für eine bestimmte primäre Datenbank beibehalten?  
   
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Der Bezeichner des Verfügbarkeitsreplikats in der Verfügbarkeitsgruppe.|  
|**group_database_id**|**uniqueidentifier**|Der Bezeichner der Datenbank in der Verfügbarkeitsgruppe. Dieser Bezeichner ist auf jedem Replikat, mit dem diese Datenbank verknüpft ist, identisch.|  
|**database_name**|**sysname**|Der Name der Datenbank, die zur Verfügbarkeitsgruppe gehört.|  
|**is_failover_ready**|**bit**|Gibt an, ob die sekundäre Datenbank mit der entsprechenden primären Datenbank synchronisiert ist. eine der folgenden:<br /><br /> 0 = Die Datenbank ist im Cluster nicht als synchronisiert gekennzeichnet. Die Datenbank ist nicht zu einem Failover bereit.<br /><br /> 1 = Die Datenbank ist im Cluster als synchronisiert gekennzeichnet. Die Datenbank ist zu einem Failover bereit.|  
|**is_pending_secondary_suspend**|**bit**|Gibt an, ob das Anhalten der Datenbank nach einem erzwungenen Failover ansteht. Die möglichen Werte sind:<br /><br /> 0 = Beliebiger Status außer HADR_SYNCHRONIZED_ SUSPENDED.<br /><br /> 1 = HADR_SYNCHRONIZED_ SUSPENDED. Wenn ein erzwungenes Failover abgeschlossen wird, wird jede der sekundären Datenbanken auf HADR_SYNCHONIZED_SUSPENDED festgelegt und bleibt in diesem Status, bis das neue primäre Replikat von dieser sekundären Datenbank eine Bestätigung für die SUSPEND-Meldung empfängt.<br /><br /> NULL = Unbekannt (kein Quorum)|  
|**is_database_joined**|**bit**|Gibt an, ob die Datenbank auf diesem Verfügbarkeitsreplikat mit der Verfügbarkeitsgruppe verknüpft wurde. Die möglichen Werte sind:<br /><br /> 0 = Die Datenbank ist nicht mit der Verfügbarkeitsgruppe auf diesem Verfügbarkeitsreplikat verknüpft.<br /><br /> 1 = Die Datenbank ist mit der Verfügbarkeitsgruppe auf diesem Verfügbarkeitsreplikat verknüpft.<br /><br /> NULL = unbekannt (Das Verfügbarkeitsreplikat hat kein Quorum.)|  
|**recovery_lsn**|**numerisch (25, 0)**|Bei einem primären Replikat das Ende des Transaktionsprotokolls, bevor das Replikat nach einer Wiederherstellung oder einem Failover neue Protokolldatensätze schreibt. Auf dem primären Replikat verfügt die Zeile für eine bestimmte sekundäre Datenbank über den Wert, in den das primäre Replikat das sekundäre Replikat synchronisieren soll (also der Wert für die Wiederherstellung und erneute Initialisierung).<br /><br /> Auf sekundären Replikaten ist dieser Wert NULL. Beachten Sie, dass jedes sekundäre Replikat entweder den MAX-Wert oder einen niedrigeren Wert aufweist, auf den das sekundäre Replikat auf Aufweisung des primären Replikats zurückgesetzt werden soll.|  
|**truncation_lsn**|**numerisch (25, 0)**|Der [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]-Protokollkürzungswert, der höher als die lokale Kürzungs-LSN sein kann, wenn die lokale Protokollkürzung blockiert wird (z. B. durch einen Sicherungsvorgang).|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Always on Verfügbarkeits gruppendynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Katalogsichten Always On-Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Überwachen von Verfügbarkeitsgruppen (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [sys. dm_hadr_database_replica_states &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)  
  
  
