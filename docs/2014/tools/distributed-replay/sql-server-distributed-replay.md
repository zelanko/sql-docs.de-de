---
title: 'SQL Server: Distributed Replay | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Distributed Replay
- SQL Server Distributed Replay
ms.assetid: 58ef7016-b105-42c2-90a0-364f411849a4
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4d1eebcd00cba9698fc92fd5f4fc2f23f1268d9a
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818866"
---
# <a name="sql-server-distributed-replay"></a>SQL Server Distributed Replay
  Die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay-Funktion unterstützt Sie beim Bewerten der Auswirkungen zukünftiger Upgrades von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Mit dem Hilfsprogramm können Sie auch die Auswirkungen von Hardware- und Betriebssystemupgrades sowie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Optimierungen bewerten.  
  
## <a name="benefits-of-distributed-replay"></a>Vorteile von Distributed Replay  
 Ähnlich wie mit [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]können Sie mithilfe von Distributed Replay eine aufgezeichnete Ablaufverfolgung in einer aktualisierten Testumgebung wiedergeben. Im Gegensatz zu [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]ist Distributed Replay nicht auf die Wiedergabe der Arbeitsauslastung von einem einzelnen Computer beschränkt.  
  
 Distributed Replay bietet eine stärker skalierbare Lösung als [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]. Mit Distributed Replay können Sie eine Arbeitsauslastung von mehreren Computern wiedergeben und eine unternehmenskritische Arbeitsauslastung besser simulieren.  
  
 Die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay-Funktion kann Ablaufverfolgungsdaten mithilfe mehrerer Computer wiedergeben und eine unternehmenswichtige Arbeitsauslastung simulieren. Verwenden des Distributed Replay für Anwendungskompatibilitätstests, Leistungstests oder die Kapazitätsplanung.  
  
## <a name="when-to-use-distributed-replay"></a>Verwendungsbereiche von Distributed Replay  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] und Distributed Replay überschneiden sich einige Funktionen.  
  
 Mit dem [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] können Sie eine aufgezeichnete Ablaufverfolgung in einer aktualisierten Testumgebung wiedergeben. Sie können auch die Wiedergabeergebnisse analysieren, um nach möglichen Funktions- und Leistungsinkompatibilitäten zu suchen. Mit dem [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] kann jedoch nur eine Arbeitsauslastung von einem einzelnen Computer wiedergegeben werden. Wenn Sie eine ressourcenintensive OLTP-Anwendung mit zahlreichen gleichzeitig aktiven Verbindungen oder einem hohen Durchsatz wiedergeben, kann [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] zu einem Ressourcenengpass werden.  
  
 Distributed Replay bietet eine stärker skalierbare Lösung als [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]. Mit Distributed Replay können Sie eine Arbeitsauslastung von mehreren Computern wiedergeben und eine unternehmenskritische Arbeitsauslastung besser simulieren.  
  
 In der folgenden Tabelle ist beschrieben, wann jedes Tool verwendet werden sollte.  
  
|Tool|Verwendung|  
|----------|---------------|  
|[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]|Sie möchten den herkömmlichen Wiedergabemechanismus auf einem einzelnen Computer verwenden. Insbesondere benötigen Sie zeilenweise Debugfunktionen, z.B. die Befehle **Schritt**, **Ausführen bis Cursorposition**und **Haltepunkt ein/aus** .<br /><br /> Sie möchten eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Ablaufverfolgung wiedergeben.|  
|Distributed Replay|Sie möchten die Anwendungskompatibilität auswerten. Sie möchten z. B. Upgradeszenarien für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und das Betriebssystem, Hardwareupgrades oder die Indexoptimierung testen.<br /><br /> Die Parallelität in der aufgezeichneten Ablaufverfolgung ist so stark, dass mit einem einzelnen Wiedergabeclient keine ausreichende Simulation erzielt werden kann.|  
  
## <a name="distributed-replay-concepts"></a>Konzepte von Distributed Replay  
 Die folgenden Komponenten bilden die Distributed Replay-Umgebung:  
  
-   **Verwaltungstool "Distributed Replay"**: eine Konsolenanwendung, `DReplay.exe`, zur Kommunikation mit distributed Replay Controller verwendet. Verwenden Sie das Verwaltungstool zum Steuern der verteilten Wiedergabe.  
  
-   **Distributed Replay Controller**: Ein Computer, auf dem der Windows-Dienst [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay Controller ausgeführt wird. Der Distributed Replay Controller koordiniert die Aktionen der Distributed Replay Clients. Es kann in jeder Distributed Replay-Umgebung jeweils nur eine Controllerinstanz geben.  
  
-   **Distributed Replay Clients**: Ein oder mehrere Computer (physisch oder virtuell), auf denen der Windows-Dienst [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay Client ausgeführt wird. Die Distributed Replay Clients simulieren gemeinsam Arbeitsauslastungen auf einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. In jeder Distributed Replay-Umgebung kann sich mindestens ein Client befinden.  
  
-   **Zielserver**: Eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , mit der Distributed Replay Clients Ablaufverfolgungsdaten wiedergeben können. Es wird empfohlen, den Zielserver in einer Testumgebung zu platzieren.  
  
 Distributed Replay-Verwaltungstool, Controller und Client können auf verschiedenen Computern oder demselben Computer installiert werden. Auf demselben Computer kann nur eine Instanz des Distributed Replay Controller oder Client-Diensts ausgeführt werden.  
  
 In der folgenden Abbildung ist die physische Architektur von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay dargestellt:  
  
 ![Distributed Replay-Architektur](../../database-engine/media/distributedreplayarch.gif "Distributed Replay-Architektur")  
  
## <a name="distributed-replay-tasks"></a>Tasks von Distributed Replay  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie Distributed Replay konfiguriert wird.|[Konfigurieren von Distributed Replay](configure-distributed-replay.md)|  
|Beschreibt, wie die Eingabedaten der Ablaufverfolgung vorbereitet werden.|[Vorbereiten der Eingabedaten für die Ablaufverfolgung](prepare-the-input-trace-data.md)|  
|Beschreibt, wie die Ablaufverfolgungsdaten wiedergegeben werden.|[Wiedergeben von Ablaufverfolgungsdaten](replay-trace-data.md)|  
|Beschreibt, wie die Ergebnisse der Ablaufverfolgungsdaten von Distributed Replay überprüft werden.|[Überprüfen der Wiedergabeergebnisse](review-the-replay-results.md)|  
|Beschreibt, wie das Verwaltungstool zum Initiieren, Überwachen und Abbrechen von Vorgängen auf dem Controller verwendet wird.|[Befehlszeilenoptionen für das Verwaltungstool &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Distributed Replay Forum](http://social.technet.microsoft.com/Forums/sl/sqldru/)   
 [Verwenden von Distributed Replay für den Auslastungstest von SQL Server: Teil 2](http://blogs.msdn.com/b/mspfe/archive/2012/11/14/using-distributed-replay-to-load-test-your-sql-server-part-2.aspx)   
 [Verwenden von Distributed Replay für den Auslastungstest von SQL Server – Teil 1](http://blogs.msdn.com/b/mspfe/archive/2012/11/08/using-distributed-replay-to-load-test-your-sql-server-part-1.aspx)  
  
  
