---
title: Synchronisieren eines Pullabonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], synchronizing
- synchronization [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
ms.assetid: 3ca24b23-fdc3-408e-8208-a2ace48fc8e3
caps.latest.revision: 44
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9143c943f18c793ce7b89be8891025b20be2e092
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160361"
---
# <a name="synchronize-a-pull-subscription"></a>Synchronisieren eines Pullabonnements
  In diesem Thema wird beschrieben, wie ein Pullabonnement in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [Replikations-Agents](agents/replication-agents-overview.md)oder Replikationsverwaltungsobjekten (RMO) synchronisiert wird.  
  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Abonnements werden durch den Verteilungs-Agent (für Momentaufnahme- und Transaktionsveröffentlichungen) oder durch den Merge-Agent (für Mergeveröffentlichungen) synchronisiert. Agents können kontinuierlich, bei Bedarf oder nach einem Zeitplan ausgeführt werden. Weitere Informationen zum Angeben von Synchronisierungszeitplänen finden Sie unter [Angeben von Synchronisierungszeitplänen](specify-synchronization-schedules.md).  
  
 Eine bedarfsgesteuerte Synchronisierung eines Abonnements kann im Ordner **Lokale Abonnements** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ausgeführt werden.  
  
#### <a name="to-synchronize-a-pull-subscription-on-demand-in-management-studio"></a>So führen Sie die bedarfsgesteuerte Synchronisierung eines Pullabonnements in Management Studio aus  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Abonnenten her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf das zu synchronisierende Abonnement, und klicken Sie dann auf **Synchronisierungsstatus anzeigen**.  
  
4.  Klicken Sie im Dialogfeld **Synchronisierungsstatus anzeigen - \<Abonnent>:\<SubscriptionDatabase>** auf **Start**. Nach Abschluss der Synchronisierung wird die Meldung **Synchronisierung abgeschlossen** eingeblendet.  
  
5.  Klicken Sie auf **Schließen**.  
  
##  <a name="ReplProg"></a> Replication Agents  
 Pullabonnements können programmgesteuert oder nach Bedarf synchronisiert werden, indem die entsprechende ausführbare Datei für den Replikations-Agent an der Eingabeaufforderung aufgerufen wird. Welche ausführbare Datei für den Replikations-Agent aufgerufen wird, hängt vom Typ der Veröffentlichung ab, zu der das Pullabonnement gehört. Weitere Informationen finden Sie unter [Replication Agents](agents/replication-agents.md).  
  
> [!NOTE]  
>  Replikations-Agents stellen die Verbindung zum lokalen Server anhand der Anmeldeinformationen für die Windows-Authentifizierung des Benutzers her, der den Agenten von der Eingabeaufforderung aus aufgerufen hat. Diese Windows-Anmeldeinformationen werden auch verwendet, wenn mithilfe der integrierten Windows-Authentifizierung eine Verbindung zu Remoteservern hergestellt wird.  
  
#### <a name="to-start-the-distribution-agent-from-the-command-prompt-or-from-a-batch-file"></a>So starten Sie den Verteilungs-Agent von der Eingabeaufforderung oder einer Batchdatei aus  
  
1.  Starten Sie den [Replikationsverteilungs-Agent](agents/replication-distribution-agent.md) von der Eingabeaufforderung oder einer Batchdatei aus, indem Sie **distrib.exe**ausführen. Geben Sie dazu die folgenden Befehlszeilenargumente an:  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Distributor**  
  
    -   **-DistributorSecurityMode** = **1**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriberSecurityMode** = **1**  
  
    -   **-SubscriptionType** = **1**  
  
     Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden, müssen Sie zudem die folgenden Argumente angeben:  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode** = **0**  
  
#### <a name="to-start-the-merge-agent-from-the-command-prompt-or-from-a-batch-file"></a>So starten Sie den Merge-Agent von der Eingabeaufforderung oder einer Batchdatei aus  
  
1.  Starten Sie den [Replikationsmerge-Agent](agents/replication-merge-agent.md) von der Eingabeaufforderung oder einer Batchdatei aus, indem Sie **replmerg.exe**ausführen. Geben Sie dazu die folgenden Befehlszeilenargumente an:  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-PublisherSecurityMode** = **1**  
  
    -   **-Publication**  
  
    -   **-Distributor**  
  
    -   **-DistributorSecurityMode** = **1**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberSecurityMode** = **1**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType** = **1**  
  
     Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden, müssen Sie zudem die folgenden Argumente angeben:  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode** = **0**  
  
###  <a name="TsqlExample"></a> Beispiele (Replikations-Agents)  
 Im folgenden Beispiel wird der Verteilungs-Agent gestartet, um ein Pullabonnement zu synchronisieren. Alle Verbindungen werden mithilfe der Windows-Authentifizierung hergestellt.  
  
 [!code-sql[HowTo#bat_synctranpullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/synctranpullsub_10.bat)]  
  
 Im folgenden Beispiel wird der Merge-Agent gestartet, um ein Pullabonnement zu synchronisieren. Alle Verbindungen werden mithilfe der Windows-Authentifizierung hergestellt.  
  
 [!code-sql[HowTo#bat_syncmergepullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/syncmergepullsub_10.bat)]  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Sie können Pullabonnements mit Replikationsverwaltungsobjekten (RMO) und dem Zugriff von verwaltetem Code auf Funktionen des Replikations-Agent programmgesteuert synchronisieren. Die Klassen für die Synchronisierung eines Pullabonnements richten sich nach dem Typ der Veröffentlichung, zu der das Abonnement gehört.  
  
> [!NOTE]  
>  Starten Sie den Agent asynchron, wenn Sie eine Synchronisierung starten möchten, die autonom ausgeführt wird, ohne sich auf die Anwendung auszuwirken. Wenn Sie während der Synchronisierung das Ergebnis der Synchronisierung überwachen und Rückrufe vom Agent empfangen möchten (z. B. über eine Statusanzeige), müssen Sie den Agent synchron starten. Für [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] -Abonnenten müssen Sie den Agent synchron starten.  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>So synchronisieren Sie ein Pullabonnement für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Erstellen Sie eine Verbindung mit dem Abonnenten, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPullSubscription> -Klasse, und legen Sie die folgenden Eigenschaften fest:  
  
    -   Den Namen der Abonnementdatenbank für <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Den Namen der Veröffentlichung, zu der das Abonnement gehört, für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   Den Namen der Veröffentlichungsdatenbank für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   Den Namen des Verlegers für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   Die in Schritt 1 erstellte Verbindung für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die restlichen Abonnementeigenschaften abzurufen. Wenn diese Methode zurückgibt `false`, stellen Sie sicher, dass das Abonnement vorhanden ist.  
  
4.  Starten Sie den Verteilungs-Agent auf eine der folgenden Arten auf dem Abonnenten:  
  
    -   Rufen Sie die <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> -Methode für die <xref:Microsoft.SqlServer.Replication.TransPullSubscription> -Instanz aus Schritt 2 auf. Diese Methode startet den Verteilungs-Agent asynchron, und die Steuerung wird sofort an die Anwendung zurückgegeben, während der Agentauftrag ausgeführt wird. Sie können diese Methode für [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)]-Abonnenten nicht aufrufen. Diese Methode kann ebenfalls nicht aufgerufen werden, wenn das Abonnement mit dem Wert `false` für <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (dem Standard) erstellt wurde.  
  
    -   Rufen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> -Klasse von der <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> -Eigenschaft ab, und rufen Sie die <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> -Methode auf. Diese Methode startet den Agent synchron, und die Steuerung bleibt beim ausgeführten Agentauftrag. Während der synchronen Ausführung können Sie das <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> -Ereignis verarbeiten, während der Agent ausgeführt wird.  
  
        > [!NOTE]  
        >  Wenn Sie einen Wert von angegeben `false` für <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (Standard) Wenn Sie das Pullabonnement erstellt haben, müssen Sie auch an <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A>, und optional <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> und <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> , da der Agent-Auftrag im Zusammenhang Metadaten für das Abonnement ist nicht verfügbar in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-merge-publication"></a>So synchronisieren Sie ein Pullabonnement mit einer Mergeveröffentlichung  
  
1.  Erstellen Sie eine Verbindung mit dem Abonnenten, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePullSubscription> -Klasse, und legen Sie die folgenden Eigenschaften fest:  
  
    -   Den Namen der Abonnementdatenbank für <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Den Namen der Veröffentlichung, zu der das Abonnement gehört, für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   Den Namen der veröffentlichten Datenbank für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   Den Namen des Verlegers für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   Die in Schritt 1 erstellte Verbindung für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die restlichen Abonnementeigenschaften abzurufen. Wenn diese Methode zurückgibt `false`, stellen Sie sicher, dass das Abonnement vorhanden ist.  
  
4.  Starten Sie den Merge-Agent auf eine der folgenden Arten auf dem Abonnenten:  
  
    -   Rufen Sie die <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> -Methode für die <xref:Microsoft.SqlServer.Replication.MergePullSubscription> -Instanz aus Schritt 2 auf. Diese Methode startet den Merge-Agent asynchron, und die Steuerung wird sofort an die Anwendung zurückgegeben, während der Agentauftrag ausgeführt wird. Sie können diese Methode für [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)]-Abonnenten nicht aufrufen. Diese Methode kann ebenfalls nicht aufgerufen werden, wenn das Abonnement mit dem Wert `false` für <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (dem Standard) erstellt wurde.  
  
    -   Rufen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> -Klasse von der <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> -Eigenschaft ab, und rufen Sie die <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> -Methode auf. Diese Methode startet den Merge-Agent synchron, und die Steuerung bleibt beim ausgeführten Agentauftrag. Während der synchronen Ausführung können Sie das <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> -Ereignis verarbeiten, während der Agent ausgeführt wird.  
  
        > [!NOTE]  
        >  Wenn Sie einen Wert von angegeben `false` für <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (Standard) Wenn Sie das Pullabonnement erstellt haben, müssen Sie auch an <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A>, und optional <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A>, und <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> da den Agentauftrag bezogenen Metadaten für das Abonnement ist nicht verfügbar in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).  
  
###  <a name="PShellExample"></a> Beispiele (RMO)  
 In diesem Beispiel wird ein Pullabonnement mit einer Transaktionsveröffentlichung synchronisiert, wobei der Agent asynchron mit dem Agentauftrag gestartet wird.  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub_withjob)]  
  
 In diesem Beispiel wird ein Pullabonnement mit einer Transaktionsveröffentlichung synchronisiert, wobei der Agent synchron gestartet wird.  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub)]  
  
 In diesem Beispiel wird ein Pullabonnement mit einer Mergeveröffentlichung synchronisiert, wobei der Agent asynchron mit dem Agentauftrag gestartet wird.  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_withjob)]  
  
 In diesem Beispiel wird ein Pullabonnement mit einer Mergeveröffentlichung synchronisiert, wobei der Agent synchron gestartet wird.  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub)]  
  
 In diesem Beispiel wird ein Pullabonnement mit einer Mergeveröffentlichung synchronisiert, wobei die Websynchronisierung verwendet wird. Das Abonnement wurde ohne den Agentauftrag und zugehörige Abonnementmetadaten erstellt, sodass der Agent synchron gestartet werden muss. Außerdem werden zusätzliche Abonnementinformationen bereitgestellt.  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_NoJobWebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_nojobwebsync)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_NoJobWebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_nojobwebsync)]  
  
## <a name="see-also"></a>Siehe auch  
 [Synchronisieren von Daten](synchronize-data.md)   
 [Erstellen eines Pullabonnements](create-a-pull-subscription.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)  
  
  
