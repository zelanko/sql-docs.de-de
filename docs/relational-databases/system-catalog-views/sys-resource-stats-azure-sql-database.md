---
title: Sys. resource_stats (Azure SQL-Datenbank) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: c12b995a52f633c4fbd7829f090f2a95d631751e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56041441"
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt die CPU-Nutzung und Speicherdaten für eine Azure SQL-Datenbank zurück. Die Daten werden in Intervallen von fünf Minuten gesammelt und aggregiert. Ist für jede Benutzerdatenbank gibt es eine Zeile für jedes reporting fünf-Minuten-Fenster, in denen eine Änderung der ressourcennutzung vorhanden ist. Die zurückgegebenen Daten umfassen CPU-Nutzung, Änderung der Speichergröße und Datenbank-SKU-Änderungen. Datenbanken im Leerlauf ohne Änderungen möglicherweise keine Zeilen für alle fünf Minuten-Intervall. Verlaufsdaten werden ungefähr 14 Tage lang beibehalten.  
  
 Die **Sys. resource_stats** Ansicht hat verschiedene Definitionen abhängig von der Version der Azure SQL-Datenbankserver, die die Datenbank zugeordnet ist. Berücksichtigen Sie diese Unterschiede und alle Änderungen, die Ihre Anwendung erfordert, beim Upgrade auf eine neue Serverversion.  
  
 Die folgende Tabelle beschreibt die verfügbaren Spalten bei einem Server mit der Version 12:  
  
|Spalte|Datentyp|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|UTC-Zeit, die den Anfang des 5-Minuten-Berichtsintervalls angibt.|  
|end_time|**datetime**|UTC-Zeit, die das Ende des 5-Minuten-Berichtsintervalls angibt.|  
|database_name|**varchar**|Name der Benutzerdatenbank.|  
|sku|**varchar**|Dienstebene der Datenbank. Folgende Werte sind möglich:<br /><br /> Standard<br /><br /> Standard<br /><br /> Premium<br /><br />Universell<br /><br />Unternehmenskritisch|  
|storage_in_megabytes|**float**|Maximale Speichergröße in Megabyte für den Zeitraum, einschließlich Datenbankdaten, Indizes, gespeicherten Prozeduren und Metadaten.|  
|avg_cpu_percent|**numeric**|Die durchschnittliche Servernutzung als Prozentwert der maximalen Kapazität für die Dienstebene.|  
|avg_data_io_percent|**numeric**|Die durchschnittliche E/A-Nutzung als Prozentwert der maximalen Kapazität für die Dienstebene.|  
|avg_log_write_percent|**numeric**|Die durchschnittliche Nutzung von Schreibressourcen als Prozentwert der maximalen Kapazität für die Dienstebene.|  
|max_worker_percent|**decimal(5,2)**|Maximale gleichzeitige Worker (Anforderungen) als Prozentwert der maximalen Kapazität für die Dienstebene der Datenbank.<br /><br /> Maximale wird derzeit für die fünf-Minuten-Intervall, das basierend auf 15-Sekunden-Beispiele für die Anzahl der gleichzeitigen Worker berechnet.|  
|max_session_percent|**decimal(5,2)**|Maximaler gleichzeitiger Sitzungen als Prozentwert der maximalen Kapazität für die Dienstebene der Datenbank.<br /><br /> Maximale wird derzeit für die fünf-Minuten-Intervall, das basierend auf der 15-Sekunden-Beispiele für gleichzeitige Sitzungen berechnet.|  
|dtu_limit|**int**|Aktuelle maximale DTU datenbankeinstellung für diese Datenbank während dieses Intervalls. |  
|allocated_storage_in_megabytes|**float**|Die Menge der formatierte Dateispeicherplatz in MB, die zum Speichern von Daten zur Verfügung gestellt. Datei-Speicherplatz wird auch als Datenspeicherplatz bezeichnet.  Weitere Informationen finden Sie in den folgenden Themen: [Verwaltung von Übersetzungsdateien Speicherplatz in SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management)|
  
> [!TIP]  
>  Mehr Kontext zu Beschränkungen und Dienstebenen zu erhalten, finden Sie unter den Themen [Dienstebenen](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/).  
    
## <a name="permissions"></a>Berechtigungen  
 Alle Benutzerrollen, die berechtigt sind, eine Verbindung mit der virtuellen **master** -Datenbank herzustellen, haben Zugriff auf diese Sicht.  
  
## <a name="remarks"></a>Hinweise  
 Vom zurückgegebenen Daten **Sys. resource_stats** wird ausgedrückt als Prozentsatz der zulässigen Grenzwerte für die Dienstebene/Leistungsstufe, die Sie ausgeführt werden.  
  
 Wenn eine Datenbank ein Mitglied der Pools für elastische Datenbanken ist, werden Ressourcenstatistiken als Prozentwerte, dargestellt als den Prozentsatz des Höchstwerts für die Datenbanken als in der Konfiguration der Pools für elastische Datenbanken ausgedrückt.  
  
 Verwenden Sie für eine genauere Ansicht dieser Daten, **Sys. dm_db_resource_stats** dynamischen verwaltungssicht in einer Benutzerdatenbank. Diese Sicht erfasst die Daten jede 15 Sekunden und behält die Verlaufsdaten eine Stunde bei.  Weitere Informationen finden Sie unter [Sys. dm_db_resource_stats &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

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
 [Dienstebenen](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Service Tier-Funktionen und Einschränkungen](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
