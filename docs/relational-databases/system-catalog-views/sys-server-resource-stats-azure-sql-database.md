---
title: Sys.server_resource_stats (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/28/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: carlrab, edmaca
ms.technology: ''
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
ms.assetid: ''
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.openlocfilehash: 82cd70d9f1baa7741f4ecc449167d5c56e7fe954
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52392633"
---
# <a name="sysserverresourcestats-azure-sql-database"></a>Sys.server_resource_stats (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Gibt Daten zur CPU-Nutzung, e/a und Speicher für eine verwaltete Instanz von Azure SQL zurück. Die Daten werden in Intervallen von fünf Minuten gesammelt und aggregiert. Es gibt eine Zeile für alle 15 Sekunden, die berichterstellung. Die zurückgegebenen Daten umfassen CPU-Auslastung, Speichergröße, e/a-Auslastung und eine verwaltete Instanz SKU. Verlaufsdaten werden ungefähr 14 Tage lang beibehalten.

Die **sys.server_resource_stats** Ansicht hat verschiedene Definitionen abhängig von der Version der verwalteten Azure SQL-Instanz, die die Datenbank zugeordnet ist. Berücksichtigen Sie diese Unterschiede und alle Änderungen, die Ihre Anwendung erfordert, beim Upgrade auf eine neue Serverversion.
 
  
 Die folgende Tabelle beschreibt die verfügbaren Spalten bei einem Server mit der Version 12:  
  
|Spalte|Datentyp|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime2**|UTC-Zeit, die den Anfang des 15-Sekunden-Intervalls reporting|  
|end_time|**datetime**|UTC-Zeit, die das Ende des 15-Sekunden-Intervalls reporting|
|resource_type|vom Datentyp nvarchar(128)|Typ der Ressource für die Metriken bereitgestellt werden.|
|resource_name|nvarchar(128)|Der Name der Ressource.|
|sku|nvarchar(128)|Verwaltete Instanz Dienstebene der Instanz an. Folgende Werte sind möglich: <br><ul><li>Universell</li></ul><ul><li>Unternehmenskritisch</li></ul>|
|hardware_generation|nvarchar(128)|Hardware-Generation-ID: z.B. Gen 4 oder 5 Gen|
|virtual_core_count|ssNoversion|Stellt die Anzahl virtueller Kerne pro Instanz (8, 16 oder 24 in der öffentlichen Vorschau)|
|avg_cpu_percent|decimal(5,2) wird|Durchschnittliche servernutzung als Prozentwert der maximalen Kapazität für die verwaltete Instanz Dienstebene, die von der Instanz verwendet. Dabei handelt es sich als Summe der CPU-Zeit des alle-Ressourcenpools für alle Datenbanken in der Instanz berechnet geteilt durch die verfügbare CPU-Zeit für die jeweilige Ebene im angegebenen Intervall.|
|reserved_storage_mb|BIGINT|Reserviert Speicher pro Instanz (die Menge an Speicher Leerzeichen Kunden erworben wurden, für die verwaltete Instanz)|
|storage_space_used_mb|decimal(18,2)|Von allen verwaltete Instanzdatenbanken-Dateien (einschließlich sowohl Benutzer- und Systemdatenbanken) verwendeten Speicher|
|io_request|BIGINT|Gesamtzahl physischer e/a-Vorgänge innerhalb eines Intervalls|
|io_bytes_read|BIGINT|Anzahl der physischen gelesenen Bytes innerhalb eines Intervalls|
|io_bytes_written|BIGINT|Anzahl der physischen, in dem Intervall geschriebenen bytes|

 
> [!TIP]  
>  Mehr Kontext zu Beschränkungen und Dienstebenen zu erhalten, finden Sie unter den Themen [Dienstebenen für die verwaltete Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tier).  
    
## <a name="permissions"></a>Berechtigungen  
 Die Ansicht kann auf alle Benutzerrollen mit Berechtigungen zum Herstellen einer Verbindung mit der **master** Datenbank.  
  
## <a name="remarks"></a>Hinweise  
 Vom zurückgegebenen Daten **sys.server_resource_stats** als Avg_cpu, die als Prozentsatz der zulässigen Limits für den Dienst ausgedrückt wird als die Summe in Bytes oder Megabyte (beschrieben in Spaltennamen) verwendet wird Dienstebene/Leistungsstufe, die Sie ausgeführt werden.  
 
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Datenbanken zurückgegeben, die in der letzten Woche mindestens 80 % der Serverkapazität genutzt haben.  
  
```sql  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT resource_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.server_resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY resource_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
    
## <a name="see-also"></a>Siehe auch  
 [Verwaltete Instanz von Dienstebenen](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tier)
