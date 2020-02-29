---
title: 'SQL Server: Distributed Replay | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Distributed Replay
- SQL Server Distributed Replay
ms.assetid: 58ef7016-b105-42c2-90a0-364f411849a4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 583af6e77d699c88e7712ac03053467138bd5a5f
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177350"
---
# <a name="sql-server-distributed-replay"></a>SQL Server Distributed Replay
  Das Distributed Replay-Feature von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt Sie beim Bewerten der Auswirkungen zukünftiger Upgrades von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Mit dem Hilfsprogramm können Sie auch die Auswirkungen von Hardware- und Betriebssystemupgrades sowie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Optimierungen bewerten.

## <a name="benefits-of-distributed-replay"></a>Vorteile von Distributed Replay
 Ähnlich wie mit [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]können Sie mithilfe von Distributed Replay eine aufgezeichnete Ablaufverfolgung in einer aktualisierten Testumgebung wiedergeben. Im Gegensatz zu [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]ist Distributed Replay nicht auf die Wiedergabe der Arbeitsauslastung von einem einzelnen Computer beschränkt.

 Distributed Replay bietet eine stärker skalierbare Lösung als [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]. Mit Distributed Replay können Sie eine Arbeitsauslastung von mehreren Computern wiedergeben und eine unternehmenskritische Arbeitsauslastung besser simulieren.

 Das [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay-Feature kann Ablaufverfolgungsdaten mithilfe mehrerer Computer verwenden und eine unternehmenskritische Arbeitsauslastung simulieren. Verwenden des Distributed Replay für Anwendungskompatibilitätstests, Leistungstests oder die Kapazitätsplanung.

## <a name="when-to-use-distributed-replay"></a>Verwendungsbereiche von Distributed Replay
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] und Distributed Replay überschneiden sich in manchen Punkten.

 Mit dem [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] können Sie eine aufgezeichnete Ablaufverfolgung in einer aktualisierten Testumgebung wiedergeben. Sie können auch die Wiedergabeergebnisse analysieren, um nach möglichen Funktions- und Leistungsinkompatibilitäten zu suchen. Mit dem [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] kann jedoch nur eine Arbeitsauslastung von einem einzelnen Computer wiedergegeben werden. Wenn Sie eine ressourcenintensive OLTP-Anwendung mit zahlreichen gleichzeitig aktiven Verbindungen oder einem hohen Durchsatz wiedergeben, kann [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] zu einem Ressourcenengpass werden.

 Distributed Replay bietet eine stärker skalierbare Lösung als [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]. Mit Distributed Replay können Sie eine Arbeitsauslastung von mehreren Computern wiedergeben und eine unternehmenskritische Arbeitsauslastung besser simulieren.

 In der folgenden Tabelle ist beschrieben, wann jedes Tool verwendet werden sollte.

|Tool|Verwenden, wenn ...|
|----------|---------------|
|[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]|Sie möchten den herkömmlichen Wiedergabemechanismus auf einem einzelnen Computer verwenden. Insbesondere benötigen Sie zeilenweise Debugfunktionen, z.B. die Befehle **Schritt**, **Ausführen bis Cursorposition**und **Haltepunkt ein/aus** .<br /><br /> Sie möchten eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Ablaufverfolgung wiedergeben.|
|Distributed Replay|Sie möchten die Anwendungskompatibilität auswerten. Sie möchten z. B. Upgradeszenarien für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und das Betriebssystem, Hardwareupgrades oder die Indexoptimierung testen.<br /><br /> Die Parallelität in der aufgezeichneten Ablaufverfolgung ist so stark, dass mit einem einzelnen Wiedergabeclient keine ausreichende Simulation erzielt werden kann.|

## <a name="distributed-replay-concepts"></a>Konzepte von Distributed Replay
 Die folgenden Komponenten bilden die Distributed Replay-Umgebung:

-   **Distributed Replay Verwaltungs Tool**: eine Konsolenanwendung, `DReplay.exe`die für die Kommunikation mit dem verteilten Wiedergabe Controller verwendet wird. Verwenden Sie das Verwaltungstool zum Steuern der verteilten Wiedergabe.

-   **Distributed Replay-Controller:** Ein Computer, auf dem der Windows-Dienst „[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay-Controller“ ausgeführt wird. Der Distributed Replay Controller koordiniert die Aktionen der Distributed Replay Clients. Es kann in jeder Distributed Replay-Umgebung jeweils nur eine Controllerinstanz geben.

-   **Distributed Replay-Clients:** Mindestens ein Computer (physisch oder virtuell), auf dem der Windows-Dienst „[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay-Client“ ausgeführt wird. Die Distributed Replay Clients simulieren gemeinsam Arbeitsauslastungen auf einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. In jeder Distributed Replay-Umgebung kann sich mindestens ein Client befinden.

-   **Zielserver**: Eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], mit der Distributed Replay-Clients Ablaufverfolgungsdaten wiedergeben können. Es wird empfohlen, den Zielserver in einer Testumgebung zu platzieren.

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

## <a name="see-also"></a>Weitere Informationen
 [SQL Server Distributed Replay Forum](https://social.technet.microsoft.com/Forums/sl/sqldru/) [mit Distributed Replay zum Auslastungs Test Ihrer SQL Server-Teil 2](https://blogs.msdn.com/b/mspfe/archive/2012/11/14/using-distributed-replay-to-load-test-your-sql-server-part-2.aspx) [mithilfe Distributed Replay zum Auslastungs Test Ihres SQL Server Teils 1](https://blogs.msdn.com/b/mspfe/archive/2012/11/08/using-distributed-replay-to-load-test-your-sql-server-part-1.aspx)


