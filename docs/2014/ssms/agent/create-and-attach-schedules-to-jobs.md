---
title: Anlegen und Zuweisen von Zeitplänen zu Aufträgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server]
- scheduling jobs [SQL Server]
- jobs [SQL Server], scheduling
- CPU [SQL Server], idle conditions
- automatic job processing
- SQL Server Agent jobs, scheduling
- idle time [SQL Server]
ms.assetid: 079c2984-0052-4a37-a2b8-4ece56e6b6b5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 414ff334139919e08b06291ec910f8531c70cd55
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63136283"
---
# <a name="create-and-attach-schedules-to-jobs"></a>Anlegen und Zuweisen von Zeitplänen zu Aufträgen
  Zeitpläne für Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents zu erstellen bedeutet, die Bedingung(en) zu definieren, durch die die Ausführung des Auftrags ohne Benutzerinteraktion gestartet wird. Sie können einen Auftrag so planen, dass er automatisch ausgeführt wird, indem Sie einen neuen Zeitplan für den Auftrag erstellen oder indem Sie dem Auftrag einen vorhandenen Zeitplan zuweisen.  
  
 Es gibt zwei Möglichkeiten, einen Zeitplan zu erstellen:  
  
-   Erstellen Sie den Zeitplan, während Sie einen Auftrag erstellen.  
  
-   Erstellen Sie den Zeitplan im Objekt-Explorer.  
  
 Nach dem Erstellen eines Zeitplans können Sie ihn mehreren Aufträgen zuweisen, auch wenn der Zeitplan für einen bestimmten Auftrag erstellt wurde. Sie können auch Zeitpläne von Aufträgen trennen.  
  
 Ein Zeitplan kann zeit- oder ereignisbasiert sein. Zum Beispiel können Sie einen Auftrag so planen, dass er zu den folgenden Zeitpunkten ausgeführt wird:  
  
-   Ausführung sobald der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent startet.  
  
-   Ausführung, wenn sich die CPU-Auslastung des Computers in einem Bereich befindet, den Sie als Leerlauf definiert haben.  
  
-   Einmalige Ausführung zu einem bestimmten Zeitpunkt.  
  
-   Regelmäßige Ausführung.  
  
 Als Alternative zu Auftragszeitplänen können Sie auch eine Warnung erstellen, durch die in Reaktion auf ein Ereignis ein bestimmter Auftrag ausgeführt wird.  
  
> [!NOTE]  
>  Es kann nur jeweils eine einzige Instanz eines Auftrags ausgeführt werden. Wenn Sie versuchen, einen Auftrag manuell auszuführen, der bereits im Rahmen eines Zeitplans ausgeführt wird, lehnt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent die Anforderung ab.  
  
 Um zu verhindern, dass ein geplanter Auftrag ausgeführt wird, müssen Sie eine der folgendem Aktionen ausführen:  
  
-   Den Zeitplan deaktivieren.  
  
-   Den Auftrag deaktivieren.  
  
-   Den Zeitplan von dem Auftrag trennen.  
  
-   Den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst beenden.  
  
-   Den Zeitplan löschen.  
  
 Wenn der Zeitplan nicht aktiviert ist, kann der Auftrag dennoch als Reaktion auf eine Warnung oder durch einen Benutzer manuell ausgeführt werden. Wenn der Auftragszeitplan nicht aktiviert ist, ist der Zeitplan auch für keinen der anderen Aufträge aktiviert, die ihn verwenden.  
  
 Ein deaktivierter Zeitplan muss explizit erneut aktiviert werden. Beim Bearbeiten eines Zeitplans wird dieser nicht automatisch erneut aktiviert.  
  
## <a name="scheduling-start-dates"></a>Planen von Startdaten  
 Das Startdatum eines Zeitplans muss größer als oder gleich 19900101 sein.  
  
 Wenn Sie einem Auftrag einen Zeitplan zuweisen, überprüfen Sie das Startdatum, das der Zeitplan für das erstmalige Ausführen des Auftrags verwendet. Das Startdatum hängt von dem Tag und der Uhrzeit ab, zu denen Sie den Zeitplan dem Auftrag zuweisen. Sie erstellen z. B. einen Zeitplan, der an jedem zweiten Montag um 8:00 Uhr ausgeführt wird. Wenn Sie einen Auftrag am Montag, 3. März 2008, um 10:00 Uhr erstellen, ist das Startdatum Montag, 17. März 2008. Wenn Sie einen weiteren Auftrag am Dienstag, dem 4. März 2008 erstellen, ist das Startdatum Montag, der 10. März 2008.  
  
 Sie können das Startdatum des Zeitplans ändern, nachdem Sie den Zeitplan einem Auftrag zugewiesen haben.  
  
## <a name="cpu-idle-schedules"></a>CPU-Leerlauf-Zeitpläne  
 Zur maximalen Nutzung der CPU-Ressourcen können Sie eine CPU-Leerlaufbedingung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent definieren. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent verwendet die CPU-Leerlaufbedingung, um den optimalen Zeitpunkt für die Ausführung von Aufträgen festzustellen. So können Sie beispielsweise einen Zeitplan für einen Auftrag zur Neuerstellung von Indizes erstellen, der während der CPU-Leerlaufzeit und zu Zeiten mit geringer Produktion eintritt.  
  
 Bevor Sie Aufträge definieren, die während der CPU-Leerlaufzeit ausgeführt werden sollen, müssen Sie die CPU-Auslastung während der normalen Verarbeitung ermitteln. Dazu können Sie mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] oder mit dem Systemmonitor den Serververkehr überwachen und Statistiken erfassen. Anschließend können Sie die zusammengestellten Informationen zum Festlegen des Prozentwertes und der Dauer der CPU-Leerlaufzeit verwenden.  
  
 Definieren Sie die CPU-Leerlaufbedingung als Prozentwert, unter den die CPU-Nutzung für eine bestimmte Dauer absinken muss. Legen Sie dann die Zeitdauer fest. Wenn die CPU-Nutzung für die angegebene Zeitdauer unter den angegebenen Prozentwert abfällt, startet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent alle Aufträge mit CPU-Leerlaufzeitplänen. Weitere Informationen zur Verwendung von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] oder Leistungsmonitor zum Überwachen der CPU-Nutzung finden Sie unter [Überwachen der CPU-Nutzung](../../relational-databases/performance-monitor/monitor-cpu-usage.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Beschreibt, wie ein Zeitplan für einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag erstellt wird.|[Create a Schedule](create-a-schedule.md)|  
|Beschreibt, wie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag geplant wird.|[Planen eines Auftrags](schedule-a-job.md)|  
|Erläutert, wie die CPU-Leerlaufbedingung für den Server definiert wird.|[Festlegen der Leerlaufzeit und Leerlaufdauer der CPU &#40;SQL Server Management Studio&#41;](set-cpu-idle-time-and-duration-sql-server-management-studio.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_help_jobschedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql)   
 [dbo.sysjobschedules &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobschedules-transact-sql)  
  
  
