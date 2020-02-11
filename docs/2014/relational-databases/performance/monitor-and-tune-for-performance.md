---
title: Überwachen und Optimieren der Leistung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- instances of SQL Server, monitoring performance
- monitoring server performance [SQL Server]
- Database Engine [SQL Server], performance
- monitoring performance [SQL Server], about performance
- server performance [SQL Server]
- monitoring performance [SQL Server]
- database performance [SQL Server], about performance
- tuning databases [SQL Server], about performance
- status information [SQL Server], performance monitoring
- database monitoring [SQL Server], about performance
- monitoring [SQL Server], queries performance
- server performance [SQL Server], about performance
- tuning databases [SQL Server]
- database performance [SQL Server]
- monitoring [SQL Server], server performance
- database monitoring [SQL Server]
- monitoring server performance [SQL Server], about monitoring server performance
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 683e8044b235828741fe429f133af82d1977031a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63150708"
---
# <a name="monitor-and-tune-for-performance"></a>Überwachen und Optimieren der Leistung
  Ziel der Überwachung von Datenbanken ist es, die Leistung eines Servers zu bewerten. Eine effektive Überwachung umfasst die regelmäßige Erstellung von Momentaufnahmen der aktuellen Leistung, um problematische Prozesse zu isolieren, und die kontinuierliche Sammlung von Daten, um Leistungstrends über längere Zeit zu verfolgen.  
  
 Durch die fortlaufende Auswertung der Datenbankleistung können Sie die Antwortzeiten minimieren und den Durchsatz maximieren, um so die optimale Leistung zu erzielen. Die effiziente Netzwerklast, Datenträger-E/A und CPU-Nutzung sind der Schlüssel zu Höchstleistungen. Hierzu müssen Sie die Anwendungsanforderungen gründlich analysieren, die logische und physische Struktur der Daten kennen, die Datenbanknutzung bewerten und Kompromisse zwischen gegensätzlichen Nutzungen, wie etwa OLTP (Online Transaction Processing) im Gegensatz zur Entscheidungsunterstützung, aushandeln.  
  
## <a name="benefits-of-monitoring-and-tuning-databases-for-performance"></a>Vorteile der Überwachung und Optimierung von Datenbanken für die Leistung  
 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und das Microsoft Windows-Betriebssystem stellen Hilfsprogramme bereit, mit denen Sie den aktuellen Zustand der Datenbank anzeigen und die Leistung unter veränderten Bedingungen nachverfolgen können. Es gibt eine Reihe von Tools und Techniken, die zur Überwachung [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von verwendet werden können. Wenn Sie wissen, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überwacht werden kann, können Sie folgende Vorgänge ausführen:  
  
-   Ermitteln, ob die Leistung verbessert werden kann. Indem Sie beispielsweise die Antwortzeiten für häufig verwendete Abfragen überwachen, können Sie ermitteln, ob Änderungen an der Abfrage oder den Indizes in den Tabellen erforderlich sind.  
  
-   Analysieren der Benutzeraktivität. Wenn Sie beispielsweise überwachen, wie Benutzer versuchen, eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herzustellen, können Sie ermitteln, ob die Sicherheit adäquat eingerichtet ist, und Anwendungen oder Entwicklungssysteme testen. Sie können beispielsweise durch Überwachen von SQL-Abfragen während der Ausführung ermitteln, ob sie richtig geschrieben sind und zu den erwarteten Ergebnissen führen.  
  
-   Beheben möglicher Probleme oder Debuggen von Anwendungskomponenten, wie z. B. den gespeicherten Prozeduren.  
  
### <a name="monitoring-in-a-dynamic-environment"></a>Überwachen in einer dynamischen Umgebung  
 Die Überwachung ist wichtig, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Dienst in einer dynamischen Umgebung bereitstellt. Geänderte Bedingungen bedeuten eine andere Leistung. In Ihren Auswertungen sehen Sie Leistungsänderungen, wenn die Anzahl der Benutzer steigt, wenn die Benutzer andere Zugriffs- und Verbindungsmethoden verwenden, wenn die Datenbank wächst, wenn andere Clientanwendungen genutzt werden, wenn sich die Daten in den Anwendungen ändern, wenn die Abfragen komplexer werden und wenn die Netzwerkbelastung ansteigt. Mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tools für die Leistungsüberwachung können Sie einige Änderungen an der Leistung den geänderten Bedingungen und komplexen Abfragen zuordnen. Die folgenden Szenarien stellen Beispiele bereit:  
  
-   Wenn Sie die Antwortzeiten für häufig verwendete Abfragen überwachen, können Sie ermitteln, ob Änderungen an der Abfrage oder den Indizes in den Tabellen, in denen die Abfragen ausgeführt werden, notwendig sind.  
  
-   Sie können durch Überwachen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen während der Ausführung ermitteln, ob die Abfragen richtig geschrieben sind und zu den erwarteten Ergebnissen führen.  
  
-   Wenn Sie überwachen, wie Benutzer versuchen, eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herzustellen, können Sie ermitteln, ob die Sicherheit adäquat eingerichtet ist, und Anwendungen und Entwicklungssysteme testen.  
  
 Die Antwortzeit ist die Zeitdauer, die benötigt wird, um die erste Zeile des Resultsets in Form einer optischen Bestätigung, dass eine Abfrage verarbeitet wird, an den Benutzer zurückzugeben. Der Durchsatz ist die Gesamtzahl der Abfragen, die vom Server während eines bestimmten Zeitraums bearbeitet werden.  
  
 Mit steigender Benutzerzahl nimmt auch der Wettstreit um die Ressourcen eines Servers zu, was wiederum zu einer erhöhten Antwortzeit und einem insgesamt reduzierten Durchsatz führt.  
  
## <a name="monitoring-and-tuning-performance-tasks"></a>Tasks beim Überwachen und Optimieren der Leistung  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|[Überwachen von SQL Server-Komponenten](monitor-sql-server-components.md)|Gibt die für die effiziente Überwachung der Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erforderlichen Schritte an.|  
|[Tools für die Leistungsüberwachung und -optimierung](performance-monitoring-and-tuning-tools.md)|Listet die Überwachungs- und Optimierungstools von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf.|  
|[Festlegen einer Leistungsbasislinie](establish-a-performance-baseline.md)|Stellt Informationen zum Festlegen einer Leistungsbasislinie bereit.|  
|[Isolieren von Leistungsproblemen](isolate-performance-problems.md)|Beschreibt, wie Datenbankleistungsprobleme isoliert werden.|  
|[Identifizieren von Engpässen](identify-bottlenecks.md)|Beschreibt, wie die Serverleistung zum Identifizieren von Engpässen überwacht und nachverfolgt wird.|  
|[Überwachen der Serverleistung und -aktivität](server-performance-and-activity-monitoring.md)|Beschreibt, wie Leistungs- und Aktivitätsüberwachungstools von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Windows verwendet werden.|  
|[Anzeigen und Speichern von Ausführungsplänen](display-and-save-execution-plans.md)|Beschreibt, wie Ausführungspläne in einer Datei im XML-Format angezeigt und gespeichert werden.|  
|[Überwachen der Leistung mit dem Abfragespeicher](monitoring-performance-by-using-the-query-store.md)|Der Abfragespeicher erfasst automatisch einen Verlauf der Abfragen, Pläne und Laufzeitstatistiken und bewahrt diese zur Überprüfung auf.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Automatisierte Verwaltung in einem Unternehmen](../../ssms/agent/automated-administration-across-an-enterprise.md)   
 [Datenbankoptimierungsratgeber](database-engine-tuning-advisor.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
