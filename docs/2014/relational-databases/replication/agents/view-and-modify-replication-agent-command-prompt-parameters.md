---
title: Anzeigen und ändern Sie die Replikation Befehlszeilenparametern Agents (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], command prompt parameters
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6e4327de10dd03b3ff8cf034ade64391d18d2a86
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192900"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a>Anzeigen und Ändern von Befehlszeilenparametern des Replikations-Agents (SQL Server Management Studio)
  Replikations-Agents sind ausführbare Dateien, die Befehlszeilenparameter akzeptieren. Standardmäßig werden Agents unter Auftragsschritten des [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agents ausgeführt. Deshalb können diese Parameter im Dialogfeld **Auftragseigenschaften – \<Job>** angezeigt und geändert werden. Dieses Dialogfeld steht über den Ordner **Aufträge** in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] sowie über die Registerkarte **Agents** im Replikationsmonitor zur Verfügung. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../monitor/start-the-replication-monitor.md).  
  
> [!NOTE]  
>  Die Änderungen der Agentparameter treten in Kraft, wenn der Agent das nächste Mal gestartet wird. Wenn der Agent ständig ausgeführt wird, müssen Sie den Agent beenden und neu starten.  
  
 Parameter können zwar direkt geändert werden, aber es ist eher üblich, sie über ein Agentprofil zu ändern. Weitere Informationen finden Sie unter [Replication Agent Profiles](replication-agent-profiles.md).  
  
 Wenn Sie über den Ordner **Aufträge** auf Agentaufträge zugreifen, ermitteln Sie mithilfe der folgenden Tabelle den Namen des Agentauftrags und die jeweils für den Agent verfügbaren Parameter.  
  
|Agent|Auftragsname|Eine Liste der Parameter finden Sie unter...|  
|-----------|--------------|------------------------------------|  
|Momentaufnahme-Agent|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Ganzzahl>**|[Replication Snapshot Agent](replication-snapshot-agent.md)|  
|Momentaufnahme-Agent für eine Mergeveröffentlichungspartition|**Dyn_\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<GUID>**|[Replication Snapshot Agent](replication-snapshot-agent.md)|  
|Protokolllese-Agent|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Ganzzahl>**|[Replikationsprotokolllese-Agent](replication-log-reader-agent.md)|  
|Merge-Agent für Pullabonnements|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Abonnementdatenbank>-\<Integer>**|[Replication Merge Agent](replication-merge-agent.md)|  
|Merge-Agent für Pushabonnements|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Integer>**|[Replication Merge Agent](replication-merge-agent.md)|  
|Verteilungs-Agent für Pushabonnements|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Integer>** <sup>1</sup>|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Verteilungs-Agent für Pullabonnements|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Abonnementdatenbank>-\<GUID>** <sup>2</sup>|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Verteilungs-Agent für Pushabonnements für Nicht-SQL Server-Abonnenten|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Ganzzahl>**|[Replication Distribution Agent](replication-distribution-agent.md)|  
|Warteschlangenlese-Agent|**[\<Verteiler>].\<Ganzzahl>**|[Replication Queue Reader Agent](replication-queue-reader-agent.md)|  
  
 <sup>1</sup> Bei Pushabonnements für Oracle-Veröffentlichungen heißt es **\<Verleger>-\<Verleger**> anstatt **\<Verleger>-\<Veröffentlichungsdatenbank>**.  
  
 <sup>2</sup> Bei Pullabonnements für Oracle-Veröffentlichungen heißt es **\<Verleger>-\<Verteilungsdatenbank**> anstatt **\<Verleger>-\<Veröffentlichungsdatenbank>**.  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a>So zeigen Sie Befehlszeilenparameter des Replikations-Agents in SQL Server Management Studio an und ändern Sie die Parameter  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem entsprechenden Computer her, und erweitern Sie dann den Serverknoten:  
  
    -   Beim Verteilungs-Agent und Merge-Agent für Pullabonnements stellen Sie eine Verbindung mit dem Abonnenten her.  
  
    -   Bei allen anderen Agents stellen Sie eine Verbindung mit dem Verteiler her.  
  
2.  Erweitern Sie den Ordner **SQL Server-Agent** und anschließend den Ordner **Aufträge** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Wählen Sie im Dialogfeld **Auftragseigenschaften – \<Job>** auf der Seite **Schritte** den Schritt **Agent ausführen** aus, und klicken Sie dann auf **Bearbeiten**.  
  
5.  Bearbeiten Sie im Dialogfeld **Auftragsschritt-Eigenschaften - Führt den Agent aus** das Feld **Befehl** .  
  
6.  Klicken Sie in beiden Dialogfeldern auf **OK** .  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a>So zeigen Sie Befehlszeilenparameter des Verteilungs- und des Merge-Agents in Replikationsmonitor an und ändern Sie die Parameter  
  
1.  Erweitern Sie im linken Bereich des Replikationsmonitors eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Alle Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf ein Abonnement, und klicken Sie dann auf **Details anzeigen**.  
  
4.  In der **Abonnement \< SubscriptionName >** Fenster, klicken Sie auf **Aktion**, und klicken Sie dann auf  **\<AgentName > Auftragseigenschaften**.  
  
5.  Wählen Sie im Dialogfeld **Auftragseigenschaften – \<Job>** auf der Seite **Schritte** den Schritt **Agent ausführen** aus, und klicken Sie dann auf **Bearbeiten**.  
  
6.  Bearbeiten Sie im Dialogfeld **Auftragsschritt-Eigenschaften - Führt den Agent aus** das Feld **Befehl** .  
  
7.  Klicken Sie in beiden Dialogfeldern auf **OK** .  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a>So zeigen Sie Befehlszeilenparameter des Momentaufnahme-, des Protolllese- und des Warteschlangenlese-Agents im Replikationsmonitor an und ändern Sie die Parameter  
  
1.  Erweitern Sie im linken Bereich des Replikationsmonitors eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Agents** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Agent im Raster, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Wählen Sie im Dialogfeld **Auftragseigenschaften – \<Job>** auf der Seite **Schritte** den Schritt **Agent ausführen** aus, und klicken Sie dann auf **Bearbeiten**.  
  
5.  Bearbeiten Sie im Dialogfeld **Auftragsschritt-Eigenschaften - Führt den Agent aus** das Feld **Befehl** .  
  
6.  Klicken Sie in beiden Dialogfeldern auf **OK** .  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltung des Replikations-Agents](replication-agent-administration.md)   
 [Ausführbare Konzepte für den Replikations-Agent](../concepts/replication-agent-executables-concepts.md)   
 [Replication Agents Overview](replication-agents-overview.md)  
  
  
