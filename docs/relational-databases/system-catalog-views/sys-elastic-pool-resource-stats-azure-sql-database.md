---
title: sys.elastic_pool_resource_stats
titleSuffix: Azure SQL Database
ms.date: 01/28/2019
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
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
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 0712785a5af3e8cc3c606a597ba02e0075c88dd9
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2019
ms.locfileid: "73843871"
---
# <a name="syselastic_pool_resource_stats-azure-sql-database"></a>sys. elastic_pool_resource_stats (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt Ressourcen Verwendungs Statistiken für alle Pools für elastische Datenbanken auf einem SQL-Datenbankserver zurück. Für jeden Pool für elastische Datenbanken gibt es eine Zeile für jedes 15-Sekunden-Berichtsfenster (vier Zeilen pro Minute). Dies umfasst CPU, e/a, Protokoll, Speicherverbrauch und gleichzeitige Anforderungs-/sitzungsauslastung durch alle Datenbanken im Pool. Diese Daten werden 14 Tage lang aufbewahrt. 
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12.|  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|Die UTC-Zeit, die den Beginn des 15-Sekunden-Berichts Intervalls angibt.|  
|**end_time**|**datetime2**|Die UTC-Zeit, die das Ende des 15-Sekunden-Berichts Intervalls angibt.|  
|**elastic_pool_name**|**nvarchar(128)**|Der Name des Pools für elastische Datenbanken.|  
|**avg_cpu_percent**|**Dezimalzahl (5, 2)**|Durchschnittliche Compute-Auslastung als Prozentsatz des Pools.|  
|**avg_data_io_percent**|**Dezimalzahl (5, 2)**|Durchschnittliche e/a-Auslastung (in Prozent) basierend auf dem Grenzwert des Pools.|  
|**avg_log_write_percent**|**Dezimalzahl (5, 2)**|Durchschnittliche Auslastung der Schreib Ressourcen als Prozentsatz des Pools.|  
|**avg_storage_percent**|**Dezimalzahl (5, 2)**|Die durchschnittliche Speicherauslastung als Prozentsatz der Speicherbeschränkung des Pools.|  
|**max_worker_percent**|**Dezimalzahl (5, 2)**|Maximale Anzahl gleichzeitiger Worker (Anforderungen) in Prozent, basierend auf dem Grenzwert des Pools.|  
|**max_session_percent**|**Dezimalzahl (5, 2)**|Maximale Anzahl gleichzeitiger Sitzungen als Prozentsatz basierend auf dem Grenzwert des Pools.|  
|**elastic_pool_dtu_limit**|**int**|Aktuelle maximale DTU-Einstellung für elastische Datenbanken für diesen Pool für elastische Datenbanken während dieses Intervalls.|  
|**elastic_pool_storage_limit_mb**|**bigint**|Aktuelle maximale Speicherbeschränkung für Pools für elastische Datenbanken für diesen Pool für elastische Datenbanken während dieses Intervalls in Megabyte.|
|**avg_allocated_storage_percent**|**Dezimalzahl (5, 2)**|Der Prozentsatz des Daten Speicherplatzes, der von allen Datenbanken im elastischen Pool zugewiesen wird.  Dies ist das Verhältnis des Daten Speicherplatzes, der der maximalen Datengröße für den Pool für elastische Datenbanken zugeordnet ist.  Weitere Informationen finden Sie [unter: Dateispeicher Platz Verwaltung in SQL-DB](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management) .|  
  
## <a name="remarks"></a>Remarks

 Diese Sicht ist in der Master-Datenbank des SQL-Datenbankservers vorhanden. Sie müssen mit der Master-Datenbank verbunden sein, um **sys. elastic_pool_resource_stats**Abfragen zu können.  
  
## <a name="permissions"></a>Berechtigungen

 Erfordert die Mitgliedschaft in der **DBManager** -Rolle.  
  
## <a name="examples"></a>Beispiele

 Im folgenden Beispiel werden Ressourcen Verwendungs Daten zurückgegeben, die nach dem letzten Zeitpunkt für alle Pools für elastische Datenbanken im aktuellen SQL-Datenbankserver geordnet sind.  
  
```sql
SELECT * FROM sys.elastic_pool_resource_stats
ORDER BY end_time DESC;  
```

 Im folgenden Beispiel wird der durchschnittliche prozentuale DTU-Verbrauch für einen bestimmten Pool berechnet.  

```sql
SELECT start_time, end_time,
  (SELECT Max(v)
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]
FROM sys.elastic_pool_resource_stats
WHERE elastic_pool_name = '<your pool name>'
ORDER BY end_time DESC;  
```

## <a name="see-also"></a>Siehe auch

 [Zämes Explosions Wachstum mit elastischen Datenbanken](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Erstellen und Verwalten eines Pools für elastische SQL-Datenbank-Datenbanken (Vorschau)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
   der [sys &#40;. resource_stats Azure&#41; SQL-Datenbank](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)  
 [sys. dm_db_resource_stats &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
