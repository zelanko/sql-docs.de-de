---
title: Sys. elastic_pool_resource_stats (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: reference
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 210e051088539920ad9c26e8036c7d9a911a2e4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47653128"
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
|**avg_allocated_storage_percent**|**decimal(5,2) wird**|Der Prozentsatz an Datenspeicherplatz, von allen Datenbanken im Pool für elastische Datenbanken.  Dies ist das Verhältnis des Datenspeicherplatzes, die Daten die maximale Größe für den elastischen Pool zugeordnet.  Weitere Informationen finden Sie unter: [adressraumverwaltung in SQL-DB-Datei](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management)|  
  
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
  
  
