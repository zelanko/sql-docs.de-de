---
title: sys. resource_stats (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2018
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: f151d62a03cebf931c58f37b1e126a7331cefae9
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68418867"
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt die CPU-Nutzung und Speicherdaten für eine Azure SQL-Datenbank zurück. Die Daten werden in Intervallen von fünf Minuten gesammelt und aggregiert. Für jede Benutzerdatenbank gibt es eine Zeile für jedes fünfminütige Berichtsfenster, in dem sich der Ressourcenverbrauch geändert hat. Die zurückgegebenen Daten umfassen CPU-Auslastung, Änderung der Speichergröße und Änderung der Daten Bank SKU. Datenbanken im Leerlauf ohne Änderungen dürfen nicht alle fünf Minuten Zeilen enthalten. Verlaufsdaten werden ungefähr 14 Tage lang beibehalten.  
  
 Die **sys. resource_stats** -Sicht hat abhängig von der Version des Azure SQL-Datenbankservers, dem die Datenbank zugeordnet ist, unterschiedliche Definitionen. Berücksichtigen Sie diese Unterschiede und alle Änderungen, die Ihre Anwendung erfordert, beim Upgrade auf eine neue Serverversion.  
  
 Die folgende Tabelle beschreibt die verfügbaren Spalten bei einem Server mit der Version 12:  
  
|Spalte|Datentyp|Beschreibung|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Die UTC-Zeit, die den Beginn des fünfminütigen Berichts Intervalls angibt.|  
|end_time|**datetime**|Die UTC-Zeit, die das Ende des fünfminütigen Berichts Intervalls angibt.|  
|database_name|**nvarchar(128)**|Name der Benutzerdatenbank.|  
|sku|**nvarchar(128)**|Dienstebene der Datenbank. Folgende Werte sind möglich:<br /><br /> Standard<br /><br /> Standard<br /><br /> Premium<br /><br />Universell<br /><br />Unternehmenskritisch|  
|storage_in_megabytes|**float**|Maximale Speichergröße in Megabyte für den Zeitraum, einschließlich Datenbankdaten, Indizes, gespeicherte Prozeduren und Metadaten.|  
|avg_cpu_percent|**Dezimalzahl (5, 2)**|Die durchschnittliche Servernutzung als Prozentwert der maximalen Kapazität für die Dienstebene.|  
|avg_data_io_percent|**Dezimalzahl (5, 2)**|Die durchschnittliche E/A-Nutzung als Prozentwert der maximalen Kapazität für die Dienstebene.|  
|avg_log_write_percent|**Dezimalzahl (5, 2)**|Die durchschnittliche Nutzung von Schreibressourcen als Prozentwert der maximalen Kapazität für die Dienstebene.|  
|max_worker_percent|**Dezimalzahl (5, 2)**|Maximale Anzahl gleichzeitiger Worker (Anforderungen) in Prozent, basierend auf dem Grenzwert der Dienst Ebene der Datenbank.<br /><br /> Das Maximum wird derzeit für das 5-Minuten-Intervall berechnet, basierend auf den 15-Sekunden-Stichproben der gleichzeitigen Anzahl von Workern.|  
|max_session_percent|**Dezimalzahl (5, 2)**|Maximale Anzahl gleichzeitiger Sitzungen in Prozent, basierend auf dem Grenzwert der Dienst Ebene der Datenbank.<br /><br /> Das Maximum wird derzeit für das 5-Minuten-Intervall berechnet, das auf den 15-Sekunden-Stichproben der gleichzeitigen Sitzungs Anzahl basiert.|  
|dtu_limit|**int**|Aktuelle DTU-Einstellung für die Datenbank für diese Datenbank während dieses Intervalls. |   
|allocated_storage_in_megabytes|**float**|Der Umfang des formatierten Datei Speicherplatzes in MB, der zum Speichern von Datenbankdaten verfügbar gemacht wird. Der formatierte Datei Bereich wird auch als zugeordneter Datenspeicher bezeichnet.  Weitere Informationen finden Sie in den folgenden Themen: [Verwaltung von Dateispeicher in SQL-DB](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management)|
  
> [!TIP]  
>  Weitere Informationen zu diesen Grenzwerten und Dienst Ebenen finden Sie in den Themen [Dienst Ebenen](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/).  
    
## <a name="permissions"></a>Berechtigungen  
 Alle Benutzerrollen, die berechtigt sind, eine Verbindung mit der virtuellen **master** -Datenbank herzustellen, haben Zugriff auf diese Sicht.  
  
## <a name="remarks"></a>Hinweise  
 Die von **sys. resource_stats** zurückgegebenen Daten werden als Prozentsatz der maximal zulässigen Grenzwerte für die Dienst Ebene/Leistungsstufe ausgedrückt, die Sie ausführen.  
  
 Wenn eine Datenbank Mitglied eines Pools für elastische Datenbanken ist, werden Ressourcen Statistiken, die als Prozentwerte dargestellt werden, als Prozentsatz der maximalen Beschränkung für die Datenbanken ausgedrückt, die in der Konfiguration des elastischen Pools festgelegt sind.  
  
 Um eine präzisetere Ansicht dieser Daten zu erhalten, verwenden Sie die dynamische Verwaltungs Sicht **sys. DM _db_resource_stats** in einer Benutzerdatenbank. Diese Sicht erfasst die Daten jede 15 Sekunden und behält die Verlaufsdaten eine Stunde bei.  Weitere Informationen finden Sie unter [sys. DM _db_resource_stats &#40;Azure SQL-&#41;Datenbank](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Datenbanken zurückgegeben, die in der letzten Woche mindestens 80 % der Serverkapazität genutzt haben.  
  
```sql  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT database_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY database_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
    
## <a name="see-also"></a>Siehe auch  
 [Dienst Ebenen](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Funktionen und Grenzwerte für die Dienst Ebene](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
