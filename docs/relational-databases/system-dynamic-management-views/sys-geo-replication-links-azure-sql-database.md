---
title: sys. geo_replication_links (Azure SQL-Datenbank) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68043160"
---
# <a name="sysgeo_replication_links-azure-sql-database"></a>sys.geo_replication_links (Azure SQL-Datenbank)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden Replikations Link zwischen primären und sekundären Datenbanken in einer Partnerschaft für die georeplikation. Diese Sicht befindet sich in der logischen Masterdatenbank  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID der aktuellen Datenbank in der sys. Database-Sicht.|  
|start_date|**datetimeoffset**|Die UTC-Zeit in einem regionalen SQL-Daten Bank Rechenzentrum, als die Daten Bank Replikation initiiert wurde.|  
|modify_date|**datetimeoffset**|Die UTC-Zeit in einem regionalen SQL-Daten Bank Rechenzentrum, wenn die georeplikation der Datenbank abgeschlossen ist. Die neue Datenbank wird ab diesem Zeitpunkt mit der primären Datenbank synchronisiert. .|  
|link_guid|**uniqueidentifier**|Eindeutige ID des Links für die georeplikation.|  
|partner_server|**sysname**|Der Name des SQL-Datenbankservers, der die georeplizierte Datenbank enthält.|  
|partner_database|**sysname**|Name der georeplizierten Datenbank auf dem verknüpften SQL-Datenbankserver.|  
|replication_state|**tinyint**|Der Status der georeplikation für diese Datenbank, einer von:.<br /><br /> 0 = ausstehend. Die Erstellung der aktiven sekundären Datenbank ist geplant, aber die notwendigen Vorbereitungsschritte sind noch nicht abgeschlossen.<br /><br /> 1 = Seeding. Für das Ziel der georeplikation wird ein Seeding durchgeführt, die beiden Datenbanken sind jedoch noch nicht synchronisiert. Bis das Seeding abgeschlossen ist, können Sie keine Verbindung mit der sekundären Datenbank herstellen. Durch das Entfernen der sekundären Datenbank aus der primären Datenbank wird der Seeding Vorgang abgebrochen.<br /><br /> 2 = Catch-up. Die sekundäre Datenbank befindet sich in einem Transaktions konsistenten Zustand und wird ständig mit der primären Datenbank synchronisiert.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|Rolle (role)|**tinyint**|Die georeplikationsrolle ist eine der folgenden:<br /><br /> 0 = primär. Der database_id bezieht sich auf die primäre Datenbank in der georeplikationspartnerschaft.<br /><br /> 1 = sekundär.  Der database_id bezieht sich auf die primäre Datenbank in der georeplikationspartnerschaft.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Der sekundäre Typ, einer der folgenden:<br /><br /> 0 = Nein. Der Zugriff auf die sekundäre Datenbank ist bis zum Failover nicht möglich.<br /><br /> 1 = schreibgeschützt. Auf die sekundäre Datenbank kann nur für Clientverbindungen mit applicationintent = schreibgeschützt zugegriffen werden.<br /><br /> 2 = Alle. Auf die sekundäre Datenbank kann jede Client Verbindung zugreifen.|  
|secondary_allow_connections _DESC|**nvarchar(256)**|Nein<br /><br /> All<br /><br /> Schreibgeschützt|  
  
## <a name="permissions"></a>Berechtigungen

Diese Ansicht ist nur in der **Master** -Datenbank für den Prinzipal Anmelde Namen auf Serverebene verfügbar.  
  
## <a name="example"></a>Beispiel

Zeigen Sie alle Datenbanken mit georeplikationslinks an.  

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

## <a name="see-also"></a>Weitere Informationen

 [Alter Database (Azure SQL-Datenbank)](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [sys. dm_geo_replication_link_status &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [sys. dm_operation_status &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
