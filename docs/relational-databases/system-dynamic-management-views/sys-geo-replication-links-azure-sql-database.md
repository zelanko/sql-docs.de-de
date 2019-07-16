---
title: Sys. geo_replication_links (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_links_TSQL
- dm_geo_replication_links
- sys.dm_geo_replication_links
- sys.dm_geo_replication_links_TSQL
helpviewer_keywords:
- sys.dm_geo_replication_links dynamic management view
- dm_geo_replication_links dynamic management view
ms.assetid: 58911798-1d60-4f28-87ab-2def2bfc3de7
author: mashamsft
ms.author: mathoma
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 6e768f447cd53321861eae91bbe40e2e34ad12f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043160"
---
# <a name="sysgeoreplicationlinks-azure-sql-database"></a>sys.geo_replication_links (Azure SQL-Datenbank)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden Replikationslink zwischen primären und sekundären Datenbanken in einer georeplikationspartnerschaft. Diese Ansicht befindet sich in der logischen Masterdatenbank.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID der aktuellen Datenbank in der Ansicht "sys.databases".|  
|start_date|**datetimeoffset**|UTC-Zeit in einem regionalen SQL-Datenbank-Datencenter, wenn die Datenbankreplikation initiiert wurde|  
|modify_date|**datetimeoffset**|UTC-Zeit in regionalen Rechenzentrum, zu SQL-Datenbank bei der georeplikation für die Datenbank abgeschlossen wurde. Die neue Datenbank wird mit der primären Datenbank ab diesem Zeitpunkt synchronisiert. .|  
|link_guid|**uniqueidentifier**|Eindeutige ID des Links Geo-Replikation.|  
|partner_server|**sysname**|Name der SQL-Datenbankserver, die die geografisch replizierte Datenbank enthält.|  
|partner_database|**sysname**|Der Name der geografisch replizierte Datenbank auf dem Verbindungsserver von SQL-Datenbank.|  
|replication_state|**tinyint**|Der Status der geografischen Replikation für diese Datenbank, eines:.<br /><br /> 0 = ausstehend. Die Erstellung der aktiven sekundären Datenbank ist geplant, aber die notwendigen Vorbereitungsschritte sind noch nicht abgeschlossen.<br /><br /> 1 = Seeding. Das Ziel für die geografische Replikation ist das Seeding durchgeführt wird, aber die beiden Datenbanken sind noch nicht synchronisiert. Bis zum Abschluss des Seedings können nicht Sie in der sekundären Datenbank verbinden. Entfernen der sekundären Datenbank vom primären Replikat wird den Seedingvorgang abzubrechen.<br /><br /> 2 = aufholen. Die sekundäre Datenbank befindet sich in einem transaktionskonsistenten Zustand und wird ständig mit der primären Datenbank synchronisiert.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|Rolle (role)|**tinyint**|Rolle "georeplikation", eine der:<br /><br /> 0 = Primary. Die Database_id bezieht sich auf der primären Datenbank in der georeplikationspartnerschaft.<br /><br /> 1 = der sekundären Datenbank.  Die Database_id bezieht sich auf der primären Datenbank in der georeplikationspartnerschaft.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Sekundären Typs, eines der:<br /><br /> 0 = Nein. Die sekundäre Datenbank kann nicht zugegriffen werden, bis ein Failover erfolgt.<br /><br /> 1 = ReadOnly. Die sekundäre Datenbank kann zugegriffen werden, nur für Clientverbindungen mit ApplicationIntent = ReadOnly.<br /><br /> 2 = Alle. Die sekundäre Datenbank wird auf jede Clientverbindung zugreifen kann.|  
|Secondary_allow_connections _desc|**nvarchar(256)**|Nein<br /><br /> All<br /><br /> Schreibgeschützt|  
  
## <a name="permissions"></a>Berechtigungen

Diese Ansicht ist nur verfügbar, in der **master** Datenbank, um die prinzipalanmeldung auf Serverebene.  
  
## <a name="example"></a>Beispiel

Zeigen Sie alle Datenbanken mit georeplikationsverknüpfungen.  

```sql
SELECT
     database_id  
   , start_date  
   , partner_server  
   , partner_database  
   , replication_state  
   , role_desc  
   , secondary_allow_connections_desc
FROM sys.geo_replication_links;  
```

## <a name="see-also"></a>Siehe auch

 [ALTER DATABASE (Azure SQL-Datenbank)](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [dm_geo_replication_link_status &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [Sys. dm_operation_status &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
