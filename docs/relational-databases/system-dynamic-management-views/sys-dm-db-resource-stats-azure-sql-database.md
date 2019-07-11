---
title: Sys. dm_db_resource_stats (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/21/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 22d771f57e5ac0d9035b8c283eb6da69027eadb3
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716678"
---
# <a name="sysdmdbresourcestats-azure-sql-database"></a>sys.dm_db_resource_stats (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt CPU-Nutzung, E/A und Arbeitsspeichernutzung für eine [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]-Datenbank zurück. Jede Zeile wird für 15 Sekunden beibehalten, auch wenn keine Aktivität in der Datenbank vorhanden ist. Verlaufsdaten werden eine Stunde lang aufbewahrt.  
  
|Spalte|Datentyp|Beschreibung|  
|-------------|---------------|-----------------|  
|end_time|**datetime**|UTC-Zeit, die das Ende des aktuellen Berichtsintervalls angibt.|  
|avg_cpu_percent|**Decimal (5,2)**|Die durchschnittliche Servernutzung als Prozentwert der maximalen Kapazität für die Dienstebene.|  
|avg_data_io_percent|**Decimal (5,2)**|Durchschnittliche Daten-e/a-Auslastung in Prozent des Grenzwerts der Dienstebene.|  
|avg_log_write_percent|**Decimal (5,2)**|Durchschnittliche Schreib-e/a-Durchsatz Auslastung als Prozentwert der maximalen Kapazität für die Dienstebene.|  
|avg_memory_usage_percent|**Decimal (5,2)**|Die durchschnittliche Arbeitsspeichernutzung als Prozentwert der maximalen Kapazität für die Dienstebene.<br /><br /> Dies schließt für pufferpoolseiten und Speicherung von In-Memory-OLTP-Objekten verwendete Arbeitsspeicher.|  
|xtp_storage_percent|**Decimal (5,2)**|Speicherauslastung für In-Memory OLTP in Prozent des Grenzwerts der Dienstebene (am Ende des Berichtsintervalls). Dies umfasst auch Arbeitsspeicher, die für die Speicherung der folgenden In-Memory OLTP-Objekte verwendet: Speicheroptimierte Tabellen, Indizes und Tabellenvariablen. Darüber hinaus Arbeitsspeicher für die Verarbeitung von ALTER TABLE-Vorgänge verwendet.<br /><br /> Gibt 0 zurück, wenn In-Memory OLTP nicht in der Datenbank verwendet wird.|  
|max_worker_percent|**Decimal (5,2)**|Maximale gleichzeitige Worker (Anforderungen) in Prozent des Grenzwerts der Dienstebene der Datenbank.|  
|max_session_percent|**Decimal (5,2)**|Maximaler gleichzeitiger Sitzungen in Prozent des Grenzwerts der Dienstebene der Datenbank.|  
|dtu_limit|**int**|Aktuelle maximale DTU datenbankeinstellung für diese Datenbank während dieses Intervalls. Bei Datenbanken mit dem virtuellen Kernen basierende Modell ist diese Spalte NULL.|
|cpu_limit|**Decimal (5,2)**|Anzahl von virtuellen Kernen für diese Datenbank während dieses Intervalls. Für Datenbanken, die mit dem DTU-basierte Modell ist diese Spalte NULL.|
|avg_instance_cpu_percent|**Decimal (5,2)**|Durchschnittliche Datenbank CPU-Auslastung in Prozent.|
|avg_instance_memory_percent|**Decimal (5,2)**|Die durchschnittliche arbeitsspeichernutzung als Prozentwert der Datenbank.|
|avg_login_rate_percent|**Decimal (5,2)**|Nur für Informationszwecke identifiziert. Wird nicht unterstützt. Zukünftige Kompatibilität wird nicht sichergestellt.|
|replica_role|**int**|Stellt das aktuelle Replikat Funktion bei 0 als primäres, 1 als sekundäre Datenbank aus, und 2 als Weiterleitung (Geo-Sekundärdatenbank primär). Es wird "1" bei einer Verbindung mit beabsichtigter Schreibschutz auf alle lesbare sekundäre Datenbanken angezeigt. Wenn eine geosekundäre Datenbank-Verbindung ohne Angabe von Beabsichtigter Schreibschutz sollte "2" (Herstellen einer Verbindung mit der Weiterleitung) angezeigt werden.|
|||
  
> [!TIP]  
>  Mehr Kontext zu Beschränkungen und Dienstebenen zu erhalten, finden Sie unter den Themen [Dienstebenen](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) und [Service Tier-Funktionen und Einschränkungen](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/).  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert die VIEW DATABASE STATE-Berechtigung.  
  
## <a name="remarks"></a>Hinweise  
 Vom zurückgegebenen Daten **Sys. dm_db_resource_stats** wird ausgedrückt als Prozentsatz der zulässigen Grenzwerte für die Dienstebene/Leistungsstufe, die Sie ausgeführt werden.
 
 Wenn innerhalb der letzten 60 Minuten ein Failover auf einem anderen Server für die Datenbank durchgeführt wurde, gibt die Ansicht nur die Daten für die Zeit zurück, die diese die primäre Datenbank seit dem Failover darstellt.  
  
 Verwenden Sie für eine weniger präzise Ansicht dieser Daten, **Sys. resource_stats** -Katalogsicht in der **master** Datenbank. Diese Sicht erfasst die Daten jede 5 Minuten und behält die Verlaufsdaten 14 Tage bei.  Weitere Informationen finden Sie unter [Sys. resource_stats &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md).  
  
 Wenn eine Datenbank ein Mitglied der Pools für elastische Datenbanken ist, werden Ressourcenstatistiken als Prozentwerte, dargestellt als den Prozentsatz des Höchstwerts für die Datenbanken als in der Konfiguration der Pools für elastische Datenbanken ausgedrückt.  
  
## <a name="example"></a>Beispiel  
  
Im folgenden Beispiel werden die Ressourcennutzungsdaten sortiert nach der letzten Ausführung der derzeit verbundenen Datenbank zurückgegeben.  
  
```  
SELECT * FROM sys.dm_db_resource_stats ORDER BY end_time DESC;  
  
```  
  
 Im folgenden Beispiel wird die durchschnittliche DTU-Nutzung als Prozentsatz des maximal zulässigen DTU-Grenzwerts in der Leistungsstufe für die Benutzerdatenbank in der letzten Stunde angegeben. Ziehen Sie eine Erhöhung der Leistungsstufe in Erwägung, da sich diese Prozentsätze stets an 100 % annähern.  
  
```  
SELECT end_time,   
  (SELECT Max(v)    
   FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS    
   value(v)) AS [avg_DTU_percent]   
FROM sys.dm_db_resource_stats;  
  
```  
  
 Im folgenden Beispiel werden die durchschnittlichen und maximalen Werte für CPU-Prozentsatz, Daten- und Protokoll-E/A und Arbeitsspeichernutzung innerhalb der letzten Stunde zurückgegeben.  
  
```  
SELECT    
    AVG(avg_cpu_percent) AS 'Average CPU Utilization In Percent',   
    MAX(avg_cpu_percent) AS 'Maximum CPU Utilization In Percent',   
    AVG(avg_data_io_percent) AS 'Average Data IO In Percent',   
    MAX(avg_data_io_percent) AS 'Maximum Data IO In Percent',   
    AVG(avg_log_write_percent) AS 'Average Log Write I/O Throughput Utilization In Percent',   
    MAX(avg_log_write_percent) AS 'Maximum Log Write I/O Throughput Utilization In Percent',   
    AVG(avg_memory_usage_percent) AS 'Average Memory Usage In Percent',   
    MAX(avg_memory_usage_percent) AS 'Maximum Memory Usage In Percent'   
FROM sys.dm_db_resource_stats;  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Sys. resource_stats &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Dienstebenen](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Service Tier-Funktionen und Einschränkungen](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
