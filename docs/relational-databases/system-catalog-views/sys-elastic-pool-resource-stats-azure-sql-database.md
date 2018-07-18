---
title: Sys. elastic_pool_resource_stats (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/06/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- Azure SQL Database
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a04b60738a48ddbe09db3eb8d7032d2f08b4ba9c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37997982"
---
# <a name="syselasticpoolresourcestats-azure-sql-database"></a>Sys. elastic_pool_resource_stats (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt ressourcenverwendungsstatistiken für alle Pools für elastische Datenbanken in einem logischen Server zurück. Ist für jeden Pool für elastische Datenbanken gibt es eine Zeile für jedes 15-sekündige berichtszeitfenster (vier Zeilen pro Minute). Dies umfasst CPU-, e/a-, Log, Speicherverbrauch und gleichzeitige Anforderungs-/sitzungsauslastung durch alle Datenbanken im Pool. Diese Daten werden 14 Tage lang beibehalten. 
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12.|  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|UTC-Zeit, die den Anfang des Berichtsintervalls von 15 Sekunden.|  
|**end_time**|**datetime2**|UTC-Zeit, die das Ende des Berichtsintervalls von 15 Sekunden.|  
|**elastic_pool_name**|**nvarchar(128)**|Der Name des Pools für elastische Datenbanken.|  
|**avg_cpu_percent**|**decimal(5,2) wird**|Durchschnittliche computeauslastung als Prozentwert der maximalen Kapazität des Pools an.|  
|**avg_data_io_percent**|**decimal(5,2) wird**|Durchschnittliche e/a-Auslastung als Prozentwert der maximalen Kapazität des Pools.|  
|**avg_log_write_percent**|**decimal(5,2) wird**|Durchschnittliche Schreibressourcen als Prozentwert der maximalen Kapazität des Pools.|  
|**avg_storage_percent**|**decimal(5,2) wird**|Durchschnittliche speicherauslastung als Prozentwert der speicherbeschränkung des Pools.|  
|**max_worker_percent**|**decimal(5,2) wird**|Maximale gleichzeitige Worker (Anforderungen) als Prozentwert der maximalen Kapazität des Pools.|  
|**max_session_percent**|**decimal(5,2) wird**|Maximaler gleichzeitiger Sitzungen als Prozentwert der maximalen Kapazität des Pools.|  
|**elastic_pool_dtu_limit**|**int**|Aktuelle Höchstwerte für Pools für elastische Datenbanken DTU-Einstellung für diesen Pool für elastische Datenbanken während dieses Intervalls.|  
|**elastic_pool_storage_limit_mb**|**bigint**|Aktuelle Höchstwerte für Pools für elastische Datenbanken Speichergrenzwert für diesen elastischen Pool in MB während dieses Intervalls festlegen.|  
  
## <a name="remarks"></a>Hinweise  
 In dieser Ansicht vorhanden ist, in der Masterdatenbank des logischen Servers. Muss eine Verbindung mit der Masterdatenbank Abfrage **Sys. elastic_pool_resource_stats**.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **"DBManager"** Rolle.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die ressourcennutzungsdaten sortiert nach der letzten Zeit für alle Pools für elastische Datenbanken auf dem aktuellen logischen Server zurück.  
  
```  
SELECT * FROM sys.elastic_pool_resource_stats   
ORDER BY end_time DESC;  
```  
  
 Im folgende Beispiel wird die durchschnittliche prozentuale DTU-Verbrauch für einen bestimmten Pool berechnet.  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.elastic_pool_resource_stats   
WHERE elastic_pool_name = '<your pool name>'   
ORDER BY end_time DESC;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Explosionsartig steigende Datenmengen mithilfe elastischer Datenbanken](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Erstellen und Verwalten eines Pools für elastische SQL-Datenbank (Vorschau)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [Sys. resource_stats &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Sys. dm_db_resource_stats &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
