---
title: Verwaltung von arbeitsauslastungen in Analytics Platform System | Microsoft-Dokumentation
description: Workloadverwaltung in Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e602cacff0c8f92b2a7748f4113a5a2ec2f34947
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100380"
---
# <a name="workload-management-in-analytics-platform-system"></a>Verwaltung von arbeitsauslastungen in Analytics Platform System

SQL Server-PDW-arbeitsauslastung Verwaltungsfunktionen ermöglichen Benutzern und Administratoren das Zuweisen von Anforderungen an den Konfigurationen von Speicher- und parallelitätsgrenzwerte voreingestellt. Verwenden Sie workloadverwaltung, um die Leistung Ihrer Workload, konsistente oder gemischten, zu verbessern, indem Sie Anforderungen an die entsprechenden Ressourcen haben, ohne das belegen Anforderungen immer zulassen.  
  
Mit der Workload-Management-Techniken in SQL Server PDW könnten Sie beispielsweise:  
  
-   Ordnen Sie eine große Anzahl von Ressourcen, die einen Auftrag zum Laden.  
  
-   Geben Sie weitere Ressourcen für einen columnstore-Index erstellen.  
  
-   Problembehandlung bei einem langsamen HashJoin um festzustellen, ob es sich um mehr Arbeitsspeicher benötigt, und geben Sie ihr mehr Arbeitsspeicher.  
  
## <a name="Basics"></a>Grundlagen der Workload-Verwaltung  
  
### <a name="key-terms"></a>Schlüsselbegriffe  
Workloadverwaltung  
*Workloadverwaltung* ist die Möglichkeit, verstehen und Anpassen von Ressourcenverwendung System um die beste Leistung für gleichzeitige Anforderungen zu erreichen.  
  
Ressourcenklasse  
In SQL Server PDW eine *Ressourcenklasse* ist eine integrierte Serverrolle, die bereits zugewiesenen Grenzwerte für Arbeitsspeicher und Parallelität aufweist. SQL Server PDW weist Ressourcen, die Anforderungen gemäß der Resource-Klasse Serverrollen-Mitgliedschaft des Anmeldenamens, der die Anforderungen übermittelt.  
  
Auf den Computeknoten verwendet die Implementierung von Ressourcenklassen das Feature "Ressourcenkontrolle" in SQL Server. Weitere Informationen zur Ressourcenkontrolle finden Sie unter [Resource Governor](../relational-databases/resource-governor/resource-governor.md) auf MSDN.  
  
### <a name="understand-current-resource-utilization"></a>Verstehen Sie die aktuelle Ressourcenverwendung  
Um System-Ressourcenverwendung für die momentan ausgeführten Anforderungen zu verstehen, verwenden Sie die dynamischen Verwaltungssichten von SQL Server PDW. Beispielsweise können Sie DMVs verwenden, um herauszufinden, ob ein langsam ausgeführte große HashJoin profitieren kann, dass mehr Arbeitsspeicher.  
  
<!-- MISSING LINKS
For examples, see [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md).  
-->
  
### <a name="adjust-resource-allocations"></a>Ressourcenzuweisungen anpassen  
Um die Ressourcenverwendung anzupassen, ändern Sie Mitgliedschaft der Ressource der Anmeldung, die die Anforderung übermittelt wird. Die Resource-Klasse-Server-Rollen sind mit dem Namen **"mediumrc"**, **"largerc"**, und **"xlargerc"**. Sie stellen Mittel, Groß und Extragroß ressourcenzuordnungen bzw. dar.  
  
Z. B. um eine große Menge an Systemressourcen auf eine Anforderung zuzuordnen, Hinzufügen der Anmeldename, der die Anforderung übermittelt die **"largerc"** -Serverrolle. Die folgende ALTER SERVER ROLE-Anweisung wird die Serverrolle "largerc" der Anmeldename Anna hinzugefügt.  
  
```sql  
ALTER SERVER ROLE largerc ADD MEMBER Anna;  
```  
  
## <a name="RC"></a>-Klasse-Ressourcenbeschreibungen.  
Die folgende Tabelle beschreibt die Ressourcenklassen und die ressourcenzuweisungen System.  
  
|Ressourcenklasse|Anfordern von Bedeutung|Maximaler Arbeitsspeicher Nutzung *|Parallelitätsslots (maximale = 32)|Description|  
|------------------|----------------------|--------------------------|---------------------------------------|---------------|  
|default|Medium|400 MB|1|Standardmäßig ist jeder Anmeldung eine kleine Menge von Arbeitsspeicher und Parallelitätsressourcen für ihre Anforderungen zulässig.<br /><br />Wenn ein Anmeldename einer Ressourcenklasse hinzugefügt wird, hat die neue Klasse Vorrang vor. Wenn eine Anmeldung aus allen Ressourcenklassen gelöscht wird, wird die Anmeldung auf die standardzuweisung für die Ressource zurückgesetzt.|  
|"Mediumrc"|Medium|1200 MB|3|Beispiele für Anforderungen, die möglicherweise bei mittelgroßen Ressourcenklasse:<br /><br />CTAS-Vorgänge, die großen hashjoins.<br /><br />Auswählen von Vorgängen, die mehr Arbeitsspeicher nicht auf dem Datenträger zwischengespeichert wird.<br /><br />Laden von Daten in gruppierten columnstore-Indizes ein.<br /><br />Erstellen, Neuerstellen und Organisieren von gruppierten columnstore-Indizes für kleinere Tabellen mit 10 bis 15 Spalten.|  
|"Largerc"|High|2,8 GB|7|Beispiele für Anforderungen, die möglicherweise bei der großen Ressourcenklasse:<br /><br />Sehr große CTAS-Vorgänge, die große hashjoins oder große Aggregationen, z.B. große ORDER BY- oder GROUP BY-Klauseln enthalten.<br /><br />Wählen Sie die Vorgänge, die sehr große Mengen an Arbeitsspeicher für Vorgänge wie hashjoins oder Aggregationen wie z. B. die ORDER BY oder GROUP BY-Klausel erfordern.<br /><br />Laden von Daten in gruppierten columnstore-Indizes ein.<br /><br />Erstellen, Neuerstellen und Organisieren von gruppierten columnstore-Indizes für kleinere Tabellen mit 10 bis 15 Spalten.|  
|"xlargerc"|High|8.4 GB|22|Die größte Ressourcenklasse ist für Anforderungen, die eine sehr große Ressourcenverbrauch zur Laufzeit erfordern.|  
  
<sup>*</sup>Maximale speicherauslastung ist eine Annäherung an.  
  
### <a name="request-importance"></a>Anfordern von Bedeutung  
Die Anforderung Wichtigkeit wird die Menge an CPU-Zeit, die SQL Server, auf den Compute-Knoten, auf die Anforderungen erhalten.  Supportanfragen mit höherer Priorität mehr CPU-Zeit.  
  
### <a name="maximum-memory-usage"></a>Maximale Speicherauslastung  
Maximale speicherauslastung ist die maximale Menge an verfügbarem Arbeitsspeicher an, die innerhalb jedes Leerzeichen für die Verarbeitung eine Anforderung verwendet werden kann. Beispielsweise können eine Anforderung "mediumrc" bis zu 1200 MB für die Verarbeitung in den einzelnen Verteilungen. Es ist immer noch wichtig, um sicherzustellen, dass Daten nicht verzerrt werden, um zu vermeiden, dass einige Verteilungen, die meisten Aufgaben ausführen.  
  
### <a name="concurrency-slots"></a>Parallelitätsslots  
Das Ziel der Zuweisung von 1, 3, 7 und 22 parallelitätsslots ist zu groß und klein Prozesse zur gleichen Zeit, ohne Blockierung kleine Prozess aus, wenn ein große Prozess ausgeführt wird.  SQL Server PDW können beispielsweise bis zu 32 parallelitätsslots 1 sehr große Anforderung (22 Slots), 1 umfangreiche Anforderung (7 Slots) und 1 mittlere Anforderung (3 Slots) zur gleichen Zeit ausführen zuordnen.  
  
Beispiele für das Zuordnen von bis zu 32 parallelitätsslots auf gleichzeitige Anforderungen:  
  
-   28 Slots = 4 große  
  
-   30 Slots = 10 Mittel  
  
-   32 Plätze = 32 Standard  
  
-   32 Plätze = 1, die sehr große + 1 Mittel für große + 1  
  
-   32 Plätze = 2 Mittel für große + 4 + 6 Standard  
  
Nehmen wir an 6 große Anforderungen an SQL Server PDW gesendet werden, und klicken Sie dann 10 Standard-Anforderungen gesendet werden. SQL Server PDW verarbeitet Anforderungen in der Reihenfolge ihrer Priorität wie folgt:  
  
-   Zuordnen von 28 parallelitätsslots, um die Verarbeitung 4 große Anforderungen wie Arbeitsspeicher verfügbar ist, und 2 große Anforderungen in der Warteschlange beibehalten.  
  
-   Zuordnen von 4 parallelitätsslots, beginnt die Verarbeitung von Anforderungen von 4 standardmäßig aus, und halten Sie 6 Standard-Anforderungen in der Warteschlange.  
  
Da Anforderungen abgeschlossen wurden und parallelitätsslots verfügbar, wird SQL Server PDW Ihre verbleibenden Anforderungen gemäß den verfügbaren Ressourcen und Priorität zugeordnet. Z. B. wenn 7 Parallelität, Slots zu öffnen, sind, müssen warten umfangreiche Anforderungen höheren Priorität für die 7 Slots als mittlere Anforderungen warten.  Wenn 6 Slots öffnen, klicken Sie dann belegt SQL Server PDW 6 weitere Standardgröße Anforderungen. Allerdings müssen Speicher- und parallelitätsgrenzwerte Slots alle verfügbar sein, bevor SQL Server PDW eine Anforderung zum ausführen können.  
  
In jeder Ressourcenklasse führen die Anforderungen in First out (FIFO) ersten nacheinander aus.  
  
## <a name="GeneralRemarks"></a>Allgemeine Hinweise  
Wenn eine Anmeldung ein Mitglied von mehr als einer Ressourcenklasse ist, hat die Klasse, die meisten Ressourcen Vorrang vor.  
  
Wenn eine Anmeldung hinzugefügt oder aus einer Ressourcenklasse gelöscht wird, wirkt sich die Änderung sofort für alle zukünftigen Anforderungen; aktuelle Anforderungen, die ausgeführt wird oder darauf warten, sind nicht betroffen. Der Anmeldename muss nicht trennen und wiederherstellen, damit die Änderung auftreten.  
  
Für jede Anmeldung werden die Einstellungen für die Ressource für einzelne Anweisungen und Vorgänge, und nicht für die Sitzung angewendet.  
  
Bevor SQL Server PDW eine Anweisung ausgeführt wird, wird versucht, die parallelitätsslots für die Anforderung benötigt abrufen. Wenn sie genügend parallelitätsslots abrufen kann, verschiebt SQL Server PDW die Anforderung in einen Zustand warten-auf--ausgeführt werden. Alle Ressourcen-System, die die Anforderung bereits zugewiesen wurden, werden zurück an das System zurückgegeben.  
  
Die meisten der SQL-Anweisungen stets die standardzuordnungen für die Ressource benötigen, und werden daher nicht über Ressourcenklassen gesteuert. Z. B. CREATE LOGIN nur eine kleine Menge von Ressourcen benötigt, und die Standardressourcen wird zugeordnet, selbst wenn der Anmeldename, der CREATE LOGIN Aufrufen einer Ressourcenklasse angehört.  Z. B. wenn Anna ein Mitglied der Ressourcenklasse "largerc ist", und er eine CREATE LOGIN-Anweisung sendet, die CREATE LOGIN-Anweisung mit der Standardanzahl von Ressourcen ausgeführt.  
  
SQL-Anweisungen und über Ressourcenklassen gesteuerte Vorgänge:  
  
-   ALTER INDEX REBUILD  
  
-   ALTER INDEX REORGANIZE  
  
-   ALTER TABLE REBUILD  
  
-   ERSTELLEN VON GRUPPIERTEN INDEX  
  
-   CREATE CLUSTERED COLUMNSTORE INDEX  
  
-   CREATE TABLE AS SELECT  
  
-   CREATE REMOTE TABLE AS SELECT  
  
-   Laden von Daten mit **Dwloader**.  
  
-   INSERT-SELECT  
  
-   UPDATE  
  
-   Delete  
  
-   RESTORE DATABASE beim Wiederherstellen in einer Appliance mit mehr Computeknoten.  
  
-   Wählen Sie aus, mit Ausnahme von nur-DMV-Abfragen  
  
## <a name="Limits"></a>Einschränkungen  
Die Ressourcenklassen gesteuert, die Speicher- und parallelitätsgrenzwerte Zuordnungen.  Sie ist nicht e/a-Vorgänge steuern.  
  
## <a name="Metadata"></a>Metadaten  
DMVs, die Informationen zu Ressourcenklassen und Resource-Klasse, Elemente enthalten.  
  
-   [sys.server_role_members](../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
-   [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
DMVs, die Informationen über den Status von Anforderungen und die benötigten Ressourcen enthalten:  
  
-   [sys.dm_pdw_lock_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-lock-waits-transact-sql.md)  
  
-   [sys.dm_pdw_resource_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)  
  
Verwandte Systemsichten verfügbar gemacht werden, mithilfe der SQL Server-DMVs auf den Computeknoten. Finden Sie unter [SQL Server Dynamic Management Views](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) für Verknüpfungen zu DMVs auf MSDN.  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   Sys.dm_pdw_nodes_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   Sys.dm_pdw_nodws_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_exec_sessions  
  
-   sys.dm_pdw_nodes_exec_requests  
  
-   sys.dm_pdw_nodes_exec_query_memory_grants  
  
-   sys.dm_pdw_nodes_exec_query_resource_semaphores  
  
-   sys.dm_pdw_nodes_os_memory_brokers  
  
-   sys.dm_pdw_nodes_os_memory_cache_entries  
  
-   sys.dm_pdw_nodes_exec_cached_plans  
  
## <a name="RelatedTasks"></a>Verwandte Aufgaben  
[Workload-Verwaltungsaufgaben](workload-management-tasks.md)  
  
<!-- MISSING LINKS
See the Workload Management section of [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md) for the following tasks:  
  
1.  Find the number of active requests for each resource group.  
  
2.  Determine if my requests need more memory  
  
3.  Determine if there are a high number of query optimizations or suboptimal plan generations.  
  
4.  Determine Average CPU time per request in each resource pool to date  
  
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
