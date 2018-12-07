---
title: Überwachen und Optimieren der Leistung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fbfda8b5768242980d61cce90f1ca16f5de6aa9f
ms.sourcegitcommit: f1cf91e679d1121d7f1ef66717b173c22430cb42
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "52586263"
---
# <a name="monitor-and-tune-for-performance"></a>Überwachen und Optimieren der Leistung
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Ziel der Überwachung von Datenbanken ist es, die Leistung eines Servers zu bewerten. Eine effektive Überwachung umfasst die regelmäßige Erstellung von Momentaufnahmen der aktuellen Leistung, um problematische Prozesse zu isolieren, und die kontinuierliche Sammlung von Daten, um Leistungstrends über längere Zeit zu verfolgen.  
  
 Durch die fortlaufende Auswertung der Datenbankleistung können Sie die Antwortzeiten minimieren und den Durchsatz maximieren, um so die optimale Leistung zu erzielen. Die effiziente Netzwerklast, Datenträger-E/A und CPU-Nutzung sind der Schlüssel zu Höchstleistungen. Hierzu müssen Sie die Anwendungsanforderungen gründlich analysieren, die logische und physische Struktur der Daten kennen, die Datenbanknutzung bewerten und Kompromisse zwischen gegensätzlichen Nutzungen, wie etwa OLTP (Online Transaction Processing) im Gegensatz zur Entscheidungsunterstützung, aushandeln.  
  
## <a name="monitoring-and-tuning-databases-for-performance"></a>Überwachen und Optimieren von Datenbanken für die Leistung  
 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Microsoft Windows stellen Hilfsprogramme bereit, mit denen der aktuelle Zustand der Datenbank angezeigt und die Leistung unter veränderten Bedingungen nachverfolgt werden kann. Es gibt eine Reihe von Tools und Methoden, mit denen Sie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]überwachen können. Überwachen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht Ihnen Folgendes:  
  
-   Ermitteln, ob die Leistung verbessert werden kann. Indem Sie beispielsweise die Antwortzeiten für häufig verwendete Abfragen überwachen, können Sie ermitteln, ob Änderungen an der Abfrage oder den Indizes in den Tabellen erforderlich sind.  
  
-   Analysieren der Benutzeraktivität. Wenn Sie beispielsweise überwachen, wie Benutzer versuchen, eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herzustellen, können Sie ermitteln, ob die Sicherheit adäquat eingerichtet ist, und Anwendungen oder Entwicklungssysteme testen. Sie können beispielsweise durch Überwachen von SQL-Abfragen während der Ausführung ermitteln, ob sie richtig geschrieben sind und zu den erwarteten Ergebnissen führen.  
  
-   Beheben von Problemen oder Debuggen von Anwendungskomponenten, z. B. gespeicherte Prozeduren.  
  
## <a name="monitoring-in-a-dynamic-environment"></a>Überwachen in einer dynamischen Umgebung  
Geänderte Bedingungen bedeuten eine andere Leistung. In Ihren Auswertungen sehen Sie Leistungsänderungen, wenn die Anzahl der Benutzer steigt, wenn die Benutzer andere Zugriffs- und Verbindungsmethoden verwenden, wenn die Datenbank wächst, wenn andere Clientanwendungen genutzt werden, wenn sich die Daten in den Anwendungen ändern, wenn die Abfragen komplexer werden und wenn die Netzwerkbelastung ansteigt. Verwenden von Tools für die Leistungsüberwachung ermöglicht es Ihnen, Änderungen in der Leistung mit geänderten Bedingungen und komplexen Abfragen zu verknüpfen. **Beispiele:**  
  
-   Wenn Sie die Antwortzeiten für häufig verwendete Abfragen überwachen, können Sie ermitteln, ob Änderungen an der Abfrage oder den Indizes in den Tabellen, in denen die Abfragen ausgeführt werden, notwendig sind.  
  
-   Sie können durch Überwachen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen während der Ausführung ermitteln, ob die Abfragen richtig geschrieben sind und zu den erwarteten Ergebnissen führen.  
  
-   Wenn Sie überwachen, wie Benutzer versuchen, eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herzustellen, können Sie ermitteln, ob die Sicherheit adäquat eingerichtet ist, und Anwendungen und Entwicklungssysteme testen.  
  
Die Antwortzeit ist die Zeitdauer, die benötigt wird, um die erste Zeile des Resultsets in Form einer optischen Bestätigung, dass eine Abfrage verarbeitet wird, an den Benutzer zurückzugeben. Der Durchsatz ist die Gesamtzahl der Abfragen, die vom Server während eines bestimmten Zeitraums bearbeitet werden.  
  
Mit steigender Benutzerzahl nimmt auch der Wettstreit um die Ressourcen eines Servers zu, was wiederum zu einer erhöhten Antwortzeit und einem insgesamt reduzierten Durchsatz führt.  
  
## <a name="monitoring-and-performance-tuning-tasks"></a>Überwachungs- und Leistungsoptimierungstasks  
  
|Thema| Task|  
|-----------|----------------------|  
|[Überwachen von SQL Server-Komponenten](../../relational-databases/performance/monitor-sql-server-components.md)|Erforderliche Schritte zum Überwachen beliebiger SQL Server-Komponenten, z.B. Aktivitätsmonitor, erweiterte Ereignisse und dynamische Verwaltungssichten und -funktionen usw.|  
|[Tools für die Leistungsüberwachung und -optimierung](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)|Listet die Überwachungs- und Optimierungstools auf, die mit SQL Server verfügbar sind, z.B. Live-Abfragestatistiken und den Datenbankoptimierungsratgeber.|  
|[Upgraden von Datenbanken mit dem Abfrageoptimierungs-Assistenten](../../relational-databases/performance/upgrade-dbcompat-using-qta.md)|Beibehalten der Stabilität der Workloadleistung während des Upgrades auf einen neueren Datenbank-Kompatibilitätsgrad.|  
|[Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)|Verwenden von Abfragespeicher, um automatisch einen Verlauf der Abfragen, Pläne und Laufzeitstatistiken zu erfassen und diese zur Überprüfung aufzubewahren|  
|[Festlegen einer Leistungsbasislinie](../../relational-databases/performance/establish-a-performance-baseline.md)|Beschreibt, wie eine Leistungsbasislinie festgelegt wird|  
|[Isolieren von Leistungsproblemen](../../relational-databases/performance/isolate-performance-problems.md)|Isolieren von Leistungsproblemen bei Datenbanken|  
|[Identifizieren von Engpässen](../../relational-databases/performance/identify-bottlenecks.md)|Überwachen und Nachverfolgen der Serverleistung, um Engpässe zu ermitteln|  
|[Verwenden von DMVs zum Bestimmen von Verwendungsstatistiken und der Leistung von Sichten](../../relational-databases/performance/use-dmvs-determine-usage-performance-views.md)|Behandelt Methoden und Skripts, mit denen Sie Informationen zur Leistung von Abfragen abrufen können.|  
|[Überwachen der Serverleistung und -aktivität](../../relational-databases/performance/server-performance-and-activity-monitoring.md)|Verwenden von Leistungs- und Aktivitätsüberwachungstools von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und von Windows|  
|[Überwachen der Ressourcenverwendung](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)|Verenden des Systemmonitors (auch als „perfmon“ bezeichnet) zum Messen der Leistung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter Verwendung von Leistungsindikatoren.|  

  
## <a name="see-also"></a>Siehe auch  
 [Automatisierte Verwaltung in einem Unternehmen](../../ssms/agent/automated-administration-across-an-enterprise.md)    
 [Vergleichen und Analysieren von Ausführungsplänen](../../relational-databases/performance/compare-and-analyze-execution-plans.md)    
 [Anzeigen und Speichern von Ausführungsplänen](../../relational-databases/performance/display-and-save-execution-plans.md)    
  
  
