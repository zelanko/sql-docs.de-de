---
title: sys. dm_geo_replication_link_status
titleSuffix: Azure SQL Database
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
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
author: mashamsft
ms.author: mathoma
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: e642fada95ddf20e81f9fcb7da8b6267469ef0c9
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2019
ms.locfileid: "73843888"
---
# <a name="sysdm_geo_replication_link_status-azure-sql-database"></a>sys.dm_geo_replication_link_status (Azure SQL-Datenbank)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden Replikations Link zwischen primären und sekundären Datenbanken in einer Partnerschaft für die georeplikation. Dies umfasst sowohl primäre als auch sekundäre Datenbanken. Wenn mehr als ein fortlaufender Replikations Link für eine bestimmte primäre Datenbank vorhanden ist, enthält diese Tabelle eine Zeile für jede der Beziehungen. Die Sicht wird in allen Datenbanken erstellt, einschließlich des logischen Masters. Wenn aber diese Sicht in der logischen master-Datenbank abgerufen wird, wird ein leeres Set zurückgegeben.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|link_guid|**uniqueidentifier**|Eindeutige ID des Replikations Links.|  
|partner_server|**sysname**|Der Name des SQL-Datenbankservers, der die verknüpfte Datenbank enthält.|  
|partner_database|**sysname**|Name der Verbindungsdatenbank auf dem SQL-Datenbankverbindungsserver.|  
|last_replication|**datetimeoffset**|Der Zeitstempel der Bestätigung der letzten Transaktion durch den sekundären auf der Grundlage der primären datenbankuhr. Dieser Wert ist nur in der primären Datenbank verfügbar.|  
|replication_lag_sec|**int**|Zeitunterschied in Sekunden zwischen dem last_replication Wert und dem Zeitstempel des Commits der Transaktion auf der primären Datenbank basierend auf der primären Daten Bank Uhr.  Dieser Wert ist nur in der primären Datenbank verfügbar.|  
|replication_state|**tinyint**|Der Status der georeplikation für diese Datenbank, einer von:.<br /><br /> 1 = Seeding. Für das Ziel der georeplikation wird ein Seeding durchgeführt, die beiden Datenbanken sind jedoch noch nicht synchronisiert. Bis das Seeding abgeschlossen ist, können Sie keine Verbindung mit der sekundären Datenbank herstellen. Durch das Entfernen der sekundären Datenbank aus der primären Datenbank wird der Seeding Vorgang abgebrochen.<br /><br /> 2 = Catch-up. Die sekundäre Datenbank befindet sich in einem Transaktions konsistenten Zustand und wird ständig mit der primären Datenbank synchronisiert.<br /><br /> 4 = angehalten. Dies ist keine aktive Beziehung mit kontinuierlichem Kopieren. Dieser Status gibt normalerweise an, dass die Bandbreite, die für den Interlink verfügbar ist, für die Ebene der Transaktionsaktivität in der primären Datenbank nicht ausreicht. Die Beziehung mit kontinuierlichem Kopieren ist jedoch nach wie vor intakt.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|Rolle (role)|**tinyint**|Die georeplikationsrolle ist eine der folgenden:<br /><br /> 0 = primär. Der database_id bezieht sich auf die primäre Datenbank in der georeplikationspartnerschaft.<br /><br /> 1 = sekundär.  Der database_id bezieht sich auf die primäre Datenbank in der georeplikationspartnerschaft.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|Der sekundäre Typ, einer der folgenden:<br /><br /> 0 = Es sind keine direkten Verbindungen mit der sekundären Datenbank zulässig, und die Datenbank ist für den Lesezugriff nicht verfügbar.<br /><br /> 2 = alle Verbindungen sind für die Datenbank in der sekundären repl zulässig; ikation für schreibgeschützten Zugriff.|  
|secondary_allow_connections_desc|**nvarchar(256)**|Nein<br /><br /> Alle|  
|last_commit|**datetimeoffset**|Zeitpunkt der letzten Transaktion, für die ein Commit an die Datenbank ausgeführt wurde. Wenn die Datenbank in der primären Datenbank abgerufen wird, gibt Sie den Zeitpunkt des letzten Commit in der primären Datenbank an. Wenn Sie in der sekundären Datenbank abgerufen wird, gibt Sie den Zeitpunkt des letzten Commit in der sekundären Datenbank an. Wenn Sie in der sekundären Datenbank abgerufen werden, wenn der primäre Replikations Link nicht aktiv ist, wird angezeigt, bis der von der sekundären Datenbank aufgefasste Punkt erreicht wurde|
  
> [!NOTE]  
>  Wenn die Replikations Beziehung durch Entfernen der sekundären Datenbank (Abschnitt 4,2) beendet wird, wird die Zeile für diese Datenbank in der **sys. dm_geo_replication_link_status** -Sicht nicht mehr angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Alle Konten mit view_database_state Berechtigung können **sys. dm_geo_replication_link_status**Abfragen.  
  
## <a name="example"></a>Beispiel  
 Replikations Verzögerungen und Zeitpunkt der letzten Replikation der sekundären Datenbanken anzeigen.  
  
```  
SELECT   
     link_guid  
   , partner_server  
   , last_replication  
   , replication_lag_sec   
FROM sys.dm_geo_replication_link_status;  
```  
  
## <a name="see-also"></a>Siehe auch  
   [ &#40;Azure SQL-Datenbank&#41; ändern](../../t-sql/statements/alter-database-azure-sql-database.md)  
   der [sys &#40;. geo_replication_links Azure&#41; SQL-Datenbank](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)  
 [sys. dm_operation_status &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
