---
title: Workloadverwaltung
description: Workloadverwaltung in Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: d14714cb23a9f6b0d6cc63ddca5049cb6741017c
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399444"
---
# <a name="workload-management-in-analytics-platform-system"></a>Workloadverwaltung in Analytics Platform System

Mit den Funktionen der workloadverwaltung von SQL Server PDW können Benutzer und Administratoren Anforderungen an vorkonfigurierte Arbeitsspeicher-und Parallelitäts Konfigurationen zuweisen. Verwenden Sie die workloadverwaltung, um die Leistung Ihrer Arbeitsauslastung zu verbessern (konsistent oder gemischt), indem Sie zulassen, dass Anforderungen über die entsprechenden Ressourcen verfügen, ohne dass dabei Anforderungen  
  
Beispielsweise können Sie mit den Techniken zur Verwaltung von Arbeits Auslastungen in SQL Server PDW folgende Aktionen ausführen:  
  
-   Zuordnen einer großen Anzahl von Ressourcen zu einem Lade Auftrag.  
  
-   Geben Sie weitere Ressourcen zum Aufbau eines columnstore--Indexes an.  
  
-   Beheben Sie die Problembehandlung bei einem Hash Join mit langsamer Leistung, um zu ermitteln, ob mehr Arbeitsspeicher benötigt wird.  
  
## <a name="Basics"></a>Grundlagen der Verwaltung  
  
### <a name="key-terms"></a>Schlüsselbegriffe  
Workloadverwaltung  
** Mit der workloadverwaltung können Sie die Systemressourcen Nutzung verstehen und anpassen, um die beste Leistung für gleichzeitige Anforderungen zu erzielen.  
  
Ressourcenklasse  
In SQL Server PDW handelt es sich bei einer *Ressourcen Klasse* um eine integrierte Server Rolle, die vorab zugewiesene Grenzwerte für Arbeitsspeicher und Parallelität aufweist. SQL Server PDW ordnet Ressourcenanforderungen entsprechend der Server Rollen Mitgliedschaft der Ressourcen Klasse der Anmeldung zu, die die Anforderungen übermittelt.  
  
Auf den Computeknoten verwendet die Implementierung von Ressourcen Klassen das Resource Governor Feature in SQL Server. Weitere Informationen zu Resource Governor finden Sie unter [Resource Governor](../relational-databases/resource-governor/resource-governor.md) auf MSDN.  
  
### <a name="understand-current-resource-utilization"></a>Grundlegendes zur aktuellen Ressourcenverwendung  
Verwenden Sie die dynamischen Verwaltungs Sichten SQL Server PDW, um die Auslastung der Systemressourcen für die aktuell laufenden Anforderungen zu verstehen. Sie können z. b. DMVs verwenden, um zu verstehen, ob ein langsamer, großer HashJoin von einem größeren Arbeitsspeicher profitieren könnte.  
  
<!-- MISSING LINKS
For examples, see [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md).  
-->
  
### <a name="adjust-resource-allocations"></a>Anpassen von Ressourcenzuweisungen  
Zum Anpassen der Ressourcenverwendung ändern Sie die Ressourcen Klassenmitgliedschaft des Anmelde namens, der die Anforderung sendet. Die Ressourcen Klassen-Server Rollen heißen " **medirerc**", " **largerc**" und " **xlargerc**". Sie stellen mittlere, große und große Ressourcen Zuordnungen dar.  
  
Fügen Sie z. b. den Anmelde Namen, der die Anforderung sendet, an die **largerc** -Server Rolle an, um einer Anforderung eine große Menge an Systemressourcen zuzuordnen. Mit der folgenden Alter Server Role-Anweisung wird die Anmelde-Anna der largerc-Server Rolle hinzugefügt.  
  
```sql  
ALTER SERVER ROLE largerc ADD MEMBER Anna;  
```  
  
## <a name="RC"></a>Ressourcen Klassen Beschreibungen  
In der folgenden Tabelle werden die Ressourcen Klassen und deren Systemressourcen Zuordnungen beschrieben.  
  
|Ressourcenklasse|Wichtigkeit anfordern|Maximale Speicherauslastung *|Parallelitäts Slots (Maximum = 32)|Beschreibung|  
|------------------|----------------------|--------------------------|---------------------------------------|---------------|  
|default|Mittel|400 MB|1|Standardmäßig ist für jede Anmeldung eine geringe Menge an Speicherplatz und Parallelitäts Ressourcen für Ihre Anforderungen zulässig.<br /><br />Wenn einer Ressourcen Klasse ein Anmelde Name hinzugefügt wird, hat die neue Klasse Vorrang. Wenn ein Anmelde Name aus allen Ressourcen Klassen gelöscht wird, wird die Standard Ressourcenzuweisung wieder hergestellt.|  
|MediumRC|Mittel|1200 MB|3|Beispiele für Anforderungen, bei denen möglicherweise die mittlere Ressourcen Klasse erforderlich ist:<br /><br />CTAs-Vorgänge mit großen Hashjoins.<br /><br />Wählen Sie Vorgänge aus, die mehr Arbeitsspeicher benötigen, um das Zwischenspeichern auf Datenträgern<br /><br />Laden von Daten in gruppierte columnstore--Indizes.<br /><br />Erstellen, Neuerstellen und Neuorganisieren von gruppierten columnstore--Indizes für kleinere Tabellen mit 10-15-Spalten.|  
|Largerc|Hoch|2,8 GB|7|Beispiele für Anforderungen, bei denen möglicherweise die große Ressourcen Klasse erforderlich ist:<br /><br />Sehr große CTAs-Vorgänge, die über riesige Hashjoins verfügen oder große Aggregationen wie z. b. große Order by-oder GROUP BY-Klauseln enthalten.<br /><br />Select-Vorgänge, bei denen sehr große Mengen an Arbeitsspeicher für Vorgänge wie Hashjoins oder Aggregationen wie Order by-oder GROUP BY-Klauseln erforderlich sind<br /><br />Laden von Daten in gruppierte columnstore--Indizes.<br /><br />Erstellen, Neuerstellen und Neuorganisieren von gruppierten columnstore--Indizes für kleinere Tabellen mit 10-15-Spalten.|  
|xlargerc|Hoch|8,4 GB|22|Die Ressourcen Klasse "Extra Large" ist für Anforderungen vorgesehen, die zur Laufzeit einen extrem großen Ressourcenverbrauch erfordern könnten.|  
  
<sup>*</sup>Die maximale Speicherauslastung ist ein Näherungswert.  
  
### <a name="request-importance"></a>Wichtigkeit anfordern  
Die Anforderungs Wichtigkeit entspricht der CPU-Zeit, die SQL Server, die auf den Computeknoten ausgeführt wird, den Anforderungen entspricht.  Anforderungen mit höherer Priorität erhalten mehr CPU-Zeit.  
  
### <a name="maximum-memory-usage"></a>Maximale Speicherauslastung  
Maximale Speicherauslastung ist die maximale Menge an verfügbarem Arbeitsspeicher, die eine Anforderung in jedem Verarbeitungsbereich verwenden kann. Beispielsweise kann eine medirerc-Anforderung bis zu 1200 MB für die Verarbeitung in jeder Verteilung verwenden. Es ist immer noch wichtig sicherzustellen, dass die Daten nicht verzerrt werden, um zu vermeiden, dass ein paar Verteilungen die meiste Arbeit durchführen.  
  
### <a name="concurrency-slots"></a>Parallelitäts Slots  
Das Ziel der Zuweisung von 1, 3, 7 und 22 Parallelitäts Slots besteht darin, dass große und kleine Prozesse gleichzeitig ausgeführt werden können, ohne dass ein kleiner Prozess blockiert wird, wenn ein großer Prozess ausgeführt wird.  Beispielsweise können SQL Server PDW maximal 32 Parallelitäts Slots zuweisen, um 1 extra große Anforderung (22 Slots), 1 große Anforderung (7 Slots) und eine mittlere Anforderung (3 Slots) gleichzeitig auszuführen.  
  
Beispiele für die Zuordnung von bis zu 32 Parallelitäts Slots für gleichzeitige Anforderungen:  
  
-   28 Slots = 4 groß  
  
-   30 Slots = 10 Mittel  
  
-   32 Slots = 32 Standard  
  
-   32 Slots = 1 extra groß + 1 Groß + 1 Mittel  
  
-   32 Slots = 2 groß + 4 Mittel + 6 Standard  
  
Angenommen, es werden 6 große Anforderungen an SQL Server PDW übermittelt, und dann werden 10 Standardanforderungen übermittelt. SQL Server PDW verarbeitet die Anforderungen in der Reihenfolge ihrer Priorität wie folgt:  
  
-   Weisen Sie 28 Parallelitäts Slots zu, um mit der Verarbeitung von 4 großen Anforderungen zu beginnen, wenn Speicher verfügbar wird, und halten Sie 2 große Anforderungen in der Warteschlange  
  
-   Weisen Sie 4 Parallelitäts Slots zu, um die Verarbeitung von 4 Standardanforderungen zu starten, und behalten Sie sechs Standardanforderungen in der Warteschlange.  
  
Wenn Anforderungen abgeschlossen werden und Parallelitäts Slots verfügbar werden, werden SQL Server PDW die restlichen Anforderungen gemäß verfügbaren Ressourcen und Priorität zuordnen. Wenn z. b. 7 Parallelitäts Slots geöffnet sind, haben wartende große Anforderungen für die 7 Slots eine höhere Priorität als für Wartezeiten mittlerer Anforderungen.  Wenn sechs Steckplätze geöffnet sind, werden von SQL Server PDW 6 weitere Anforderungen mit der standardmäßigen Standardkapazität zugeteilt. Arbeitsspeicher-und Parallelitäts Slots müssen jedoch alle verfügbar sein, bevor SQL Server PDW das Ausführen einer Anforderung zulässt.  
  
In jeder Ressourcen Klasse werden die Anforderungen in der FIFO-Reihenfolge (First in First Out) ausgeführt.  
  
## <a name="GeneralRemarks"></a>Allgemeine Hinweise  
Wenn eine Anmeldung Mitglied von mehr als einer Ressourcen Klasse ist, hat die Klasse mit den meisten Ressourcen Vorrang.  
  
Wenn ein Anmelde Name einer Ressourcen Klasse hinzugefügt oder aus dieser gelöscht wird, tritt die Änderung für alle zukünftigen Anforderungen sofort in Kraft. aktuelle Anforderungen, die ausgeführt werden oder warten, sind nicht betroffen. Der Anmelde Name muss nicht getrennt und erneut verbunden werden, damit die Änderung erfolgt.  
  
Für jeden Anmelde Namen werden die Ressourcen Klassen Einstellungen auf einzelne Anweisungen und Vorgänge angewendet, nicht auf die Sitzung.  
  
Bevor SQL Server PDW eine-Anweisung ausführt, wird versucht, die für die Anforderung benötigten Parallelitäts Slots abzurufen. Wenn nicht genügend Parallelitäts Slots abgerufen werden können, verschiebt SQL Server PDW die Anforderung in einen Zustand, der gewartet werden soll. Alle Ressourcensysteme, die der Anforderung bereits zugeordnet waren, werden an das System zurückgegeben.  
  
Die meisten der SQL-Anweisungen benötigen immer die Standard Ressourcenzuweisungen und werden daher nicht von Ressourcen Klassen gesteuert. Beispielsweise benötigt Create Login nur eine kleine Menge von Ressourcen, und die Standard Ressourcen werden auch dann zugewiesen, wenn die Anmeldung, die Create Login aufgerufen hat, ein Member einer Ressourcen Klasse ist.  Wenn Anna beispielsweise ein Mitglied der largerc-Ressourcen Klasse ist und eine CREATE LOGIN-Anweisung übermittelt, wird die CREATE LOGIN-Anweisung mit der Standard Anzahl von Ressourcen ausgeführt.  
  
SQL-Anweisungen und-Vorgänge, die von Ressourcen Klassen gesteuert werden:  
  
-   ALTER INDEX REBUILD  
  
-   ALTER INDEX REORGANIZE  
  
-   ALTER TABLE REBUILD  
  
-   gruppierten Index erstellen  
  
-   CREATE CLUSTERED COLUMNSTORE INDEX  
  
-   CREATE TABLE AS SELECT  
  
-   Remote Tabelle als SELECT-Tabelle erstellen  
  
-   Laden von Daten mit **"dwloader**.  
  
-   INSERT-SELECT  
  
-   UPDATE  
  
-   DELETE  
  
-   Stellen Sie die Datenbank wieder her, wenn Sie eine Anwendung mit weiteren Computeknoten wiederherstellen.  
  
-   SELECT, ausgenommen nur DMV-Abfragen  
  
## <a name="Limits"></a>Einschränkungen  
Die Ressourcen Klassen Steuern Speicher-und Parallelitäts Zuordnungen.  Sie Steuern keine Eingabe-/Ausgabevorgänge.  
  
## <a name="Metadata"></a>Benötigten  
DMVs, die Informationen zu Ressourcen Klassen und Ressourcen Klassenmembern enthalten.  
  
-   [sys.server_role_members](../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
-   [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
DMVs, die Informationen über den Status von Anforderungen und die benötigten Ressourcen enthalten:  
  
-   [sys. dm_pdw_lock_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-lock-waits-transact-sql.md)  
  
-   [sys. dm_pdw_resource_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)  
  
Verwandte System Sichten, die von den SQL Server DMVs auf den Computeknoten verfügbar gemacht werden. Links zu diesen DMVs auf MSDN finden Sie unter [SQL Server dynamischen Verwaltungs Sichten](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) .  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   sys.dm_pdw_nodes_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_resource_governor_resource_pools  
  
-   sys. dm_pdw_nodws_resource_governor_workload_groups  
  
-   sys.dm_pdw_nodes_exec_sessions  
  
-   sys.dm_pdw_nodes_exec_requests  
  
-   sys.dm_pdw_nodes_exec_query_memory_grants  
  
-   sys.dm_pdw_nodes_exec_query_resource_semaphores  
  
-   sys.dm_pdw_nodes_os_memory_brokers  
  
-   sys.dm_pdw_nodes_os_memory_cache_entries  
  
-   sys.dm_pdw_nodes_exec_cached_plans  
  
## <a name="RelatedTasks"></a>Verwandte Aufgaben  
[Workloadverwaltungsaufgaben](workload-management-tasks.md)  
  
<!-- MISSING LINKS
See the Workload Management section of [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md) for the following tasks:  
  
1.  Find the number of active requests for each resource group.  
  
2.  Determine if my requests need more memory  
  
3.  Determine if there are a high number of query optimizations or suboptimal plan generations.  
  
4.  Determine Average CPU time per request in each resource pool to date  
  
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
