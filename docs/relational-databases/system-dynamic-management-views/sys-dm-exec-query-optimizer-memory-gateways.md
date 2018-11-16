---
title: Sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL) | Microsoft-Dokumentation
description: Gibt den aktuellen Status der Ressource Semaphore verwendet, um gleichzeitige abfrageoptimierung einschränken
ms.custom: ''
ms.date: 04/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_memory_gateways_TSQL
- dm_exec_query_optimizer_memory_gateways
- sys.dm_exec_query_optimizer_memory_gateways_TSQL
- sys.dm_exec_query_optimizer_memory_gateways
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_optimizer_memory_gateways dynamic management view
author: josack
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7ebd9b778f48e42c9200e7586983aba801b52e4c
ms.sourcegitcommit: ddb682c0061c2a040970ea88c051859330b8ac00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51570719"
---
# <a name="sysdmexecqueryoptimizermemorygateways-transact-sql"></a>Sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Gibt den aktuellen Status der Ressource Semaphore verwendet, um gleichzeitige abfrageoptimierung zu drosseln.

|Spalte|Typ|Description|  
|----------|---------------|-----------------|  
|**pool_id**|**int**|Ressourcenpool-ID unter der Ressourcenkontrolle|  
|**name**|**sysname**|Kompilieren Sie Gate-Namen (kleines Gateway, Gateway Mittel, Groß Gateway)|
|**max_count**|**int**|Der konfigurierten Maximalanzahl von gleichzeitigen Kompilierungen|
|**active_count**|**int**|Die derzeit aktiven Anzahl von Kompilierungen in dieses gate|
|**waiter_count**|**int**|Die Anzahl von Wartevorgängen in dieses gate|
|**threshold_factor**|**bigint**|Schwellenwert für wichtige den maximalen Arbeitsspeicher-Teil definiert, die von der abfrageoptimierung verwendet.  Für das Gateway kleine gibt Threshold_factor die maximale Optimierer Auslastung des Speichers in Byte für eine Abfrage an, bevor sie einen Zugriff im kleinen Gateway erforderlich ist.  Für das Gateway mittelgroßen und großen zeigt Threshold_factor den Teil des Gesamtspeichers auf dem Server verfügbaren Speichers für dieses Gate. Es wird als Divisor verwendet, bei der Berechnung der Schwellenwert für prozessspeicherbelegung für das Gate.|
|**threshold**|**bigint**|Nächste Schwellenwert-Speicher in Bytes.  Die Abfrage ist erforderlich, um einen Zugriff auf dieses Gateway zu erhalten, wenn ihren Arbeitsspeicherverbrauch diesen Schwellenwert erreicht wird.  "1", wenn die Abfrage nicht erforderlich ist, um einen Zugriff auf dieses Gateway zu erhalten.|
|**is_active**|**bit**|Gibt an, ob die Abfrage erforderlich ist, um das aktuelle Gate oder nicht übergeben werden.|


## <a name="permissions"></a>Berechtigungen  
SQL Server erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.

Azure SQL-Datenbank erfordert die VIEW DATABASE STATE-Berechtigung in der Datenbank.


## <a name="remarks"></a>Hinweise  
SQL Server verwendet einen mehrstufigen Gateway-Ansatz zum Einschränken der Anzahl der zulässigen gleichzeitigen Kompilierungen.  Drei Gateways werden verwendet, einschließlich klein, Mittel und groß. Gateways helfen zu verhindern, dass die Überbeanspruchung der gesamten Speicherressourcen von größeren Kompilierung Arbeitsspeicher erfordern Consumern.

Wartet auf ein Gateway Ergebnis bei der verzögerten Kompilierung. Gedrosselte Anforderungen müssen zusätzlich zu Verzögerungen bei der Kompilierung einer zugeordneten RESOURCE_SEMAPHORE_QUERY_COMPILE Typ Accumulation / warten. Der Wartetyp RESOURCE_SEMAPHORE_QUERY_COMPILE hinweisen, dass Abfragen eine große Menge an Arbeitsspeicher für die Kompilierung verwenden und, dass der Arbeitsspeicher ist erschöpft, oder Sie können auch ausreichend Arbeitsspeicher verfügbar ist insgesamt jedoch verfügbaren Einheiten in einer bestimmten Gateway wurde erreicht. Die Ausgabe des **sys.dm_exec_query_optimizer_memory_gateways** können verwendet werden, um die Problembehandlung hilfreich, nicht genügend Arbeitsspeicher, um einen Abfrageausführungsplan zu kompilieren.  

## <a name="examples"></a>Beispiele  

### <a name="a-viewing-statistics-on-resource-semaphores"></a>A. Anzeigen von Statistiken zur Ressource Semaphoren  
Was sind die aktuellen Optimierer Arbeitsspeicher Gateway Statistiken für diese Instanz von SQL Server?

```  
SELECT [pool_id], [name], [max_count], [active_count],
       [waiter_count], [threshold_factor], [threshold],
       [is_active]
FROM sys.dm_exec_query_optimizer_memory_gateways;   

```  

## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](./system-dynamic-management-views.md)   
 [Execution Related Dynamic Management Views and Functions &#40;Transact-SQL&#41; (Dynamische Verwaltungssichten und Funktionen im Zusammenhang mit der Ausführung (Transact-SQL))](./execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[Wie Sie mithilfe des Befehls DBCC MEMORYSTATUS speicherauslastung für SQL Server 2005 überwachen](https://support.microsoft.com/help/907877/how-to-use-the-dbcc-memorystatus-command-to-monitor-memory-usage-on-sql-server-2005)
[große Abfragekompilierung wartet auf RESOURCE_SEMAPHORE_QUERY_COMPILE in SQL Server 2014](https://support.microsoft.com/help/3024815/large-query-compilation-waits-on-resource-semaphore-query-compile-in-sql-server-2014)
