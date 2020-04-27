---
title: Anzeigen und Ändern von Befehlszeilen Parametern des Replikations-Agents (SQL Server Management Studio) | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63192900"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a>Anzeigen und Ändern von Befehlszeilenparametern des Replikations-Agents (SQL Server Management Studio)
  Replikations-Agents sind ausführbare Dateien, die Befehlszeilenparameter akzeptieren. Standardmäßig werden Agents unter Auftragsschritten des [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agents ausgeführt. Deshalb können diese Parameter im Dialogfeld **Auftragseigenschaften – \<Job>** angezeigt und geändert werden. Dieses Dialogfeld steht über den Ordner **Aufträge** in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] sowie über die Registerkarte **Agents** im Replikationsmonitor zur Verfügung. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../monitor/start-the-replication-monitor.md).  
  
> [!NOTE]  
>  Die Änderungen der Agentparameter treten in Kraft, wenn der Agent das nächste Mal gestartet wird. Wenn der Agent ständig ausgeführt wird, müssen Sie den Agent beenden und neu starten.  
  
 Parameter können zwar direkt geändert werden, aber es ist eher üblich, sie über ein Agentprofil zu ändern. Weitere Informationen finden Sie unter [Replication Agent Profiles](replication-agent-profiles.md).  
  
 Wenn Sie über den Ordner **Aufträge** auf Agentaufträge zugreifen, ermitteln Sie mithilfe der folgenden Tabelle den Namen des Agentauftrags und die jeweils für den Agent verfügbaren Parameter.  
  
|Agent|Auftragsname|Eine Liste der Parameter finden Sie unter...|  
|-----------|--------------|------------------------------------|  
|Momentaufnahme-Agent|**\<Verleger>-\<publicationdatabase>-\<Publication>-\<Integer>**|[Replikationsmomentaufnahme-Agent](replication-snapshot-agent.md)|  
|Momentaufnahme-Agent für eine Mergeveröffentlichungspartition|**Dyn_\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<GUID>**|[Replikationsmomentaufnahme-Agent](replication-snapshot-agent.md)|  
|Protokolllese-Agent|**\<Verleger>-\<publicationdatabase>-\<Integer->**|[Replikationsprotokolllese-Agent](replication-log-reader-agent.md)|  
|Merge-Agent für Pullabonnements|**\<Verleger>-\<publicationdatabase>-\<Publication>-\<Subscriber>-\<abonneptiondatabase>-\<Integer>**|[Replication Merge Agent](replication-merge-agent.md)|  
|Merge-Agent für Pushabonnements|**\<Verleger>-\<publicationdatabase>-\<Publication>-\<Subscriber>-\<Integer>**|[Replication Merge Agent](replication-merge-agent.md)|  
|Verteilungs-Agent für Pushabonnements|**\<\<\<Verleger>-publicationdatabase>-Publication>-Subscriber>-\<Integer>1 \<** <sup>1</sup>|[Replikationsverteilungs-Agent](replication-distribution-agent.md)|  
|Verteilungs-Agent für Pullabonnements|**\<\<\<\<Verleger>-\<publicationdatabase>-Publication>-Subscriber>-Abonnement Datenbank>-GUID>2 \<** <sup>2</sup>|[Replikationsverteilungs-Agent](replication-distribution-agent.md)|  
|Verteilungs-Agent für Pushabonnements für Nicht-SQL Server-Abonnenten|**\<Verleger>-\<publicationdatabase>-\<Publication>-\<Subscriber>-\<Integer>**|[Replikationsverteilungs-Agent](replication-distribution-agent.md)|  
|Warteschlangenlese-Agent|**[\<Verteiler>]. \<ganzzahlige>**|[Warteschlangenlese-Agent der Microsoft SQL Server-Replikation](replication-queue-reader-agent.md)|  
  
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
  
4.  Klicken Sie im Fenster **Abonnement Abonnement \< Name>** auf **Aktion**, und klicken Sie dann auf ** \<Agentname> Auftrags Eigenschaften**.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations-Agent](replication-agent-administration.md)   
 [Ausführbare Konzepte für den Replikations-Agent](../concepts/replication-agent-executables-concepts.md)   
 [Replikations-Agents (Übersicht)](replication-agents-overview.md)  
  
  
