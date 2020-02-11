---
title: sys. dm_db_resource_stats (Azure SQL-Datenbank) | Microsoft-Dokumentation
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
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1dd66834788896e6952a0352eb2a19fd1a828513
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75245964"
---
# <a name="sysdm_db_resource_stats-azure-sql-database"></a>sys.dm_db_resource_stats (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt CPU-Nutzung, E/A und Arbeitsspeichernutzung für eine [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]-Datenbank zurück. Für alle 15 Sekunden ist eine Zeile vorhanden, selbst wenn keine Aktivität in der Datenbank erfolgt ist. Verlaufs Daten werden ungefähr eine Stunde lang aufbewahrt.  
  
|Spalten|Datentyp|BESCHREIBUNG|  
|-------------|---------------|-----------------|  
|end_time|**datetime**|UTC-Zeit, die das Ende des aktuellen Berichtsintervalls angibt.|  
|avg_cpu_percent|**Dezimalzahl (5, 2)**|Die durchschnittliche Servernutzung als Prozentwert der maximalen Kapazität für die Dienstebene.|  
|avg_data_io_percent|**Dezimalzahl (5, 2)**|Durchschnittliche Daten-e/a-Auslastung als Prozentsatz des Limits der Dienst Ebene. Informationen zu den Datenbanken mit hyperskalierung finden Sie unter Daten-e/a [in Statistiken](https://docs.microsoft.com/azure/sql-database/sql-database-hyperscale-performance-diagnostics#data-io-in-resource-utilization-statistics)|  
|avg_log_write_percent|**Dezimalzahl (5, 2)**|Durchschnittliche Transaktionsprotokoll Schreibvorgänge (in Mbit/s) als Prozentsatz der Dienst Ebene.|  
|avg_memory_usage_percent|**Dezimalzahl (5, 2)**|Die durchschnittliche Arbeitsspeichernutzung als Prozentwert der maximalen Kapazität für die Dienstebene.<br /><br /> Dies schließt den für Pufferpool Seiten und die Speicherung von in-Memory-OLTP-Objekten verwendeten Arbeitsspeicher ein.|  
|xtp_storage_percent|**Dezimalzahl (5, 2)**|Die Speicherauslastung für in-Memory-OLTP als Prozentsatz des Limits der Dienst Ebene (am Ende des Berichts Intervalls). Dazu gehört auch der Arbeitsspeicher, der für die Speicherung der folgenden in-Memory-OLTP-Objekte verwendet wird: Speicher optimierte Tabellen, Indizes und Tabellen Variablen. Sie enthält auch Speicher, der zum Verarbeiten von ALTER TABLE-Vorgängen verwendet wird<br /><br /> Gibt 0 zurück, wenn in-Memory-OLTP nicht in der Datenbank verwendet wird.|  
|max_worker_percent|**Dezimalzahl (5, 2)**|Maximale Anzahl gleichzeitiger Worker (Anforderungen) als Prozentsatz des Limits der Dienst Ebene der Datenbank.|  
|max_session_percent|**Dezimalzahl (5, 2)**|Maximale Anzahl gleichzeitiger Sitzungen als Prozentsatz des Limits der Dienst Ebene der Datenbank.|  
|dtu_limit|**int**|Aktuelle DTU-Einstellung für die Datenbank für diese Datenbank während dieses Intervalls. Bei Datenbanken, die das v-Kern-basierte Modell verwenden, ist diese Spalte NULL.|
|cpu_limit|**Dezimalzahl (5, 2)**|Anzahl der vkerne für diese Datenbank während dieses Intervalls. Für Datenbanken, die das DTU-basierte Modell verwenden, ist diese Spalte NULL.|
|avg_instance_cpu_percent|**Dezimalzahl (5, 2)**|Durchschnittliche CPU-Auslastung der Datenbank als Prozentsatz des SQL-DB-Prozesses.|
|avg_instance_memory_percent|**Dezimalzahl (5, 2)**|Durchschnittliche Daten Bank Speicherauslastung als Prozentsatz des SQL-DB-Prozesses.|
|avg_login_rate_percent|**Dezimalzahl (5, 2)**|Nur für Informationszwecke identifiziert. Wird nicht unterstützt. Zukünftige Kompatibilität wird nicht sichergestellt.|
|replica_role|**int**|Stellt die Rolle des aktuellen Replikats mit 0 als primär, 1 als Sekundär und 2 als Weiterleitung (primärer sekundäres Replikat) dar. Wenn eine Verbindung mit der schreibgeschützten Absicht für alle lesbaren sekundären Replikate besteht, wird "1" angezeigt. Wenn Sie eine Verbindung mit einem georeplikat herstellen, ohne die schreibgeschützte Absicht anzugeben, sollte "2" (Verbindung mit der Weiterleitung) angezeigt werden.|
|||
  
> [!TIP]  
>  Weitere Informationen zu diesen Grenzwerten und Dienst Ebenen finden Sie in den Themen [Dienst Ebenen](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) und [dienstebenenfunktionen und-Einschränkungen](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/).  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert die VIEW DATABASE STATE-Berechtigung.  
  
## <a name="remarks"></a>Bemerkungen  
 Die von **sys. dm_db_resource_stats** zurückgegebenen Daten werden als Prozentsatz der maximal zulässigen Grenzwerte für die Dienst Ebene/Leistungsstufe ausgedrückt, die Sie ausführen.
 
 Wenn innerhalb der letzten 60 Minuten ein Failover auf einem anderen Server für die Datenbank durchgeführt wurde, gibt die Ansicht nur die Daten für die Zeit zurück, die diese die primäre Datenbank seit dem Failover darstellt.  
  
 Verwenden Sie die **sys. resource_stats** -Katalog Sicht in der **Master** -Datenbank, um eine weniger präzise Ansicht dieser Daten mit längerer Beibehaltungs Dauer zu erhalten. Diese Sicht erfasst die Daten jede 5 Minuten und behält die Verlaufsdaten 14 Tage bei.  Weitere Informationen finden Sie unter [sys. resource_stats &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md).  
  
 Wenn eine Datenbank Mitglied eines Pools für elastische Datenbanken ist, werden Ressourcen Statistiken, die als Prozentwerte dargestellt werden, als Prozentsatz der maximalen Beschränkung für die Datenbanken ausgedrückt, die in der Konfiguration des elastischen Pools festgelegt sind.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. resource_stats &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Dienst Ebenen](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Funktionen und Beschränkungen von Dienstebenen](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
