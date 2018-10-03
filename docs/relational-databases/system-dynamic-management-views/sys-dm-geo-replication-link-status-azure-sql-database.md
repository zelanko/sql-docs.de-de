---
title: dm_geo_replication_link_status (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/13/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_link_status
- dm_geo_replication_link_status_TSQL
- sys.dm_geo_replication_link_status
- sys.dm_geo_replication_link_status_TSQL
helpviewer_keywords:
- dm_geo_replication_link_status dynamic management view
- sys.dm_geo_replication_link_status dynamic management view
ms.assetid: d763d679-470a-4c21-86ab-dfe98d37e9fd
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 57212bc80087e3f2227f90ab6fa16678df37517e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809078"
---
# <a name="sysdmgeoreplicationlinkstatus-azure-sql-database"></a>sys.dm_geo_replication_link_status (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden Replikationslink zwischen primären und sekundären Datenbanken in einer georeplikationspartnerschaft. Dies schließt primäre und sekundäre Datenbanken. Wenn mehr als einen Link für die fortlaufende Replikation für eine bestimmte primäre Datenbank vorhanden ist, enthält diese Tabelle eine Zeile für jede der Beziehungen. Die Sicht wird in allen Datenbanken, einschließlich der logischen Master erstellt. Wenn aber diese Sicht in der logischen master-Datenbank abgerufen wird, wird ein leeres Set zurückgegeben.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|link_guid|**uniqueidentifier**|Eindeutige ID des Replikationslinks.|  
|partner_server|**sysname**|Der Name des logischen Servers mit der verknüpften Datenbank.|  
|partner_database|**sysname**|Der Name der Verbindungsdatenbank auf dem logischen Verbindungsserver.|  
|last_replication|**datetimeoffset**|Der Zeitstempel, der die letzte Transaktion Bestätigung vom sekundären basierend auf der primären Datenbank Uhr. Dieser Wert ist auf nur die primäre Datenbank verfügbar.|  
|replication_lag_sec|**int**|Der Zeitunterschied in Sekunden zwischen der Last_replication-Wert und dem Zeitstempel des, Transaktionscommits auf dem primären Replikat basierend auf der primären Datenbank Uhr.  Dieser Wert ist auf nur die primäre Datenbank verfügbar.|  
|replication_state|**tinyint**|Der Status der geografischen Replikation für diese Datenbank, eines:.<br /><br /> 1 = Seeding. Das Ziel für die geografische Replikation ist das Seeding durchgeführt wird, aber die beiden Datenbanken sind noch nicht synchronisiert. Bis zum Abschluss des Seedings können nicht Sie in der sekundären Datenbank verbinden. Entfernen der sekundären Datenbank vom primären Replikat wird den Seedingvorgang abzubrechen.<br /><br /> 2 = aufholen. Die sekundäre Datenbank befindet sich in einem transaktionskonsistenten Zustand und wird ständig mit der primären Datenbank synchronisiert.<br /><br /> 4 = angehalten. Dies ist keine aktive Beziehung mit kontinuierlichem Kopieren. Dieser Status gibt normalerweise an, dass die Bandbreite, die für den Interlink verfügbar ist, für die Ebene der Transaktionsaktivität in der primären Datenbank nicht ausreicht. Die Beziehung mit kontinuierlichem Kopieren ist jedoch nach wie vor intakt.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|Rolle (role)|**tinyint**|Rolle "georeplikation", eine der:<br /><br /> 0 = Primary. Die Database_id bezieht sich auf der primären Datenbank in der georeplikationspartnerschaft.<br /><br /> 1 = der sekundären Datenbank.  Die Database_id bezieht sich auf der primären Datenbank in der georeplikationspartnerschaft.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Sekundären Typs, eines der:<br /><br /> 0 = keine direkten Verbindungen zugelassen sind, auf die sekundäre Datenbank und die Datenbank ist nicht für Lesezugriff verfügbar.<br /><br /> 2 = alle Verbindungen sind zulässig, mit der Datenbank in der sekundären Repl; Ication für schreibgeschützten Zugriff.|  
|secondary_allow_connections_desc|**nvarchar(256)**|nein<br /><br /> All|  
|last_commit|**datetimeoffset**|Der Zeitpunkt der letzten Transaktion, die an die Datenbank übergeben werden soll. Wenn in der primären Datenbank abgerufen wird, gibt es die letzte Commitzeit für die primäre Datenbank an. Wenn in der sekundären Datenbank abgerufen wird, gibt es die letzte Commitzeit für die sekundäre Datenbank an. Wenn in der sekundären Datenbank abgerufen, wenn das primäre Replikat der des Replikationslinks ausgefallen ist, bedeutet dies bis was zeigen Sie die sekundäre Datenbank erreicht ist.|
  
> [!NOTE]  
>  Wenn die replikationsbeziehung beendet wird, durch das Entfernen der sekundären Datenbank (Abschnitt 4.2), die Zeile für diese Datenbank in der **dm_geo_replication_link_status** -Sicht nicht mehr angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Ein Konto mit Berechtigung für View_database_state kann Abfragen **dm_geo_replication_link_status**.  
  
## <a name="example"></a>Beispiel  
 Zeigen Sie die replikationsverzögerungen und den Zeitpunkt der letzten Replikation des eigenen sekundären Datenbanken.  
  
```  
SELECT   
     link_guid  
   , partner_server  
   , last_replication  
   , replication_lag_sec   
FROM sys.dm_geo_replication_link_status;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER_DATABASE &#40;Azure SQL-Datenbank&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [Sys. geo_replication_links &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [Sys. dm_operation_status &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
