---
title: Überwachen der Auftragsaktivität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- jobs [SQL Server Agent], monitoring
- monitoring [SQL Server], jobs
- activity monitoring [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- SQL Server Agent Job Activity Monitor
- SQL Server Agent jobs, monitoring
- performance [SQL Server], jobs
- current activity
ms.assetid: 71cb432b-631d-4b8b-9965-e731b3d8266d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6310453e1257aaee1a02f035c7213ef4fe6131af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62704777"
---
# <a name="monitor-job-activity"></a>Überwachen der Auftragsaktivität
  Sie können die aktuellen Aktivitäten aller definierten Aufträge auf einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überwachen, indem Sie den Auftragsaktivitätsmonitor des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verwenden.  
  
## <a name="sql-server-agent-sessions"></a>Sitzungen des SQL Server-Agents  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent erstellt jedes Mal, wenn der Dienst gestartet wird, eine neue Sitzung. Beim Erstellen einer neuen Sitzung wird die **sysjobactivity** -Tabelle in der **msdb** -Datenbank mit allen vorhandenen definierten Aufträgen aufgefüllt. Beim Neustart des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents bleibt die letzte Auftragsaktivität in dieser Tabelle erhalten. Jede Sitzung zeichnet die normale Auftragsaktivität des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents vom Anfang bis zum Ende des Auftrags auf. Informationen zu diesen Sitzungen werden in der **syssessions** -Tabelle der **msdb** -Datenbank gespeichert.  
  
## <a name="job-activity-monitor"></a>Auftragsaktivitätsmonitor  
 Mit dem Auftragsaktivitätsmonitor können Sie die **sysjobactivity** -Tabelle mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]anzeigen. Sie können alle Aufträge auf dem Server anzeigen oder Filter definieren, um die Anzahl der angezeigten Aufträge zu beschränken. Sie können die Auftragsinformationen auch sortieren, indem Sie auf eine Spaltenüberschrift im Raster **Agentauftragsaktivität** klicken. Wenn Sie beispielsweise die Spaltenüberschrift **Letzte Ausführung** auswählen, können Sie die Aufträge in der Reihenfolge anzeigen, in der sie zuletzt ausgeführt wurden. Wenn Sie erneut auf die Spaltenüberschrift klicken, werden die Aufträge je nach ihrem letzten Ausführungsdatum so umgeschaltet, dass sie in auf- bzw. absteigender Reihenfolge angezeigt werden.  
  
 Mit dem Auftragsaktivitätsmonitor können Sie folgende Aufgaben ausführen:  
  
-   Starten und Beenden von Aufträgen  
  
-   Anzeigen von Auftragseigenschaften  
  
-   Anzeigen des Verlaufsprotokolls für einen bestimmten Auftrag  
  
-   Manuelles Aktualisieren der Informationen im Raster **Agentauftragsaktivität** oder Festlegen eines automatischen Aktualisierungsintervalls durch Klicken auf **Aktualisierungseinstellungen anzeigen**.  
  
 Verwenden Sie den Auftragsaktivitätsmonitor, um zu ermitteln, für welche Aufträge eine Ausführung geplant ist, oder um festzustellen, welche Aufträge derzeit ausgeführt werden bzw. im Leerlauf sind. Sie können mit dem Auftragsaktivitätsmonitor auch das Ergebnis von Aufträgen anzeigen, die während der aktuellen Sitzung ausgeführt wurden. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst unerwartet einen Fehler erzeugt, können Sie ermitteln, welche Aufträge zum Zeitpunkt des Fehlers ausgeführt wurden, indem Sie im Auftragsaktivitätsmonitor die vorherige Sitzung anzeigen.  
  
 Erweitern Sie im Objekt-Explorer von **die Option** SQL Server-Agent [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , um den Auftragsaktivitätsmonitor zu öffnen. Klicken Sie mit der rechten Maustaste auf **Auftragsaktivitätsmonitor**, und klicken Sie dann auf **Auftragsaktivitäten anzeigen**.  
  
 Sie können Auftragsaktivitäten für die aktuelle Sitzung auch mithilfe der gespeicherten Prozedur **sp_help_jobactivity**anzeigen.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Beschreibt, wie der Laufzeitstatus von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträgen angezeigt wird.|[Auftragsaktivitäten anzeigen](view-job-activity.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen der Auftrags Aktivität](view-job-activity.md)   
 [dbo. sysjobactivity &#40;Transact-SQL-&#41;](/sql/relational-databases/system-tables/dbo-sysjobactivity-transact-sql)   
 [dbo. syssessions &#40;Transact-SQL-&#41;](/sql/relational-databases/system-tables/dbo-syssessions-transact-sql)   
 [sp_help_jobactivity &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql)  
  
  
