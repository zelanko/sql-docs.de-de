---
title: Erstellen eines Pullabonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], creating
- merge replication subscribing [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 41d1886d-59c9-41fc-9bd6-a59b40e0af6e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f8868957d7c479de3a51a599deed42c34d6676eb
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52753492"
---
# <a name="create-a-pull-subscription"></a>Create a Pull Subscription
  In diesem Thema wird beschrieben, wie ein Pullabonnement in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) erstellt wird.  
  
 Das Einrichten eines Pullabonnements für die P2P-Replikation ist mit einem Skript möglich, aber nicht über den Assistenten.  
  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Erstellen Sie mit dem Assistenten für neue Abonnements ein Pullabonnement auf dem Verleger oder dem Abonnenten. Folgen Sie den Seiten im Assistenten für folgende Aufgaben:  
  
-   Angeben des Verlegers und der Veröffentlichung.  
  
-   Auswählen, wo die Replikations-Agents ausgeführt werden. Wählen Sie für ein Pullabonnement je nach Veröffentlichungstyp auf der Seite **Speicherort des Verteilungs-Agents** bzw. **Speicherort des Merge-Agents** die Option **Jeden Agent auf seinem Abonnenten ausführen (Pullabonnements)** aus.  
  
-   Angeben der Abonnenten und Abonnentendatenbanken.  
  
-   Angeben der Anmeldenamen und Kennwörter für Verbindungen zwischen den Replikations-Agents:  
  
    -   Bei Abonnements für Momentaufnahme- und Transaktionsveröffentlichungen geben Sie die Anmeldeinformationen auf der Seite **Sicherheit für den Verteilungs-Agent** an.  
  
    -   Bei Abonnements für Mergeveröffentlichungen geben Sie die Anmeldeinformationen auf der Seite **Sicherheit für den Merge-Agent** an.  
  
     Informationen zu den für die jeweiligen Agents erforderlichen Berechtigungen finden Sie unter [Sicherheitsmodell des Replikations-Agents](security/replication-agent-security-model.md).  
  
-   Angeben eines Synchronisierungszeitplans und wann der Abonnent initialisiert werden soll.  
  
-   Angeben weiterer Optionen für Mergeveröffentlichungen: Abonnementtyp; Werte für parametrisierte Filter; Informationen für die Synchronisierung über HTTP, wenn die Veröffentlichung für die Websynchronisierung aktiviert ist.  
  
-   Angeben weiterer Optionen für Transaktionsveröffentlichungen, die aktualisierbare Abonnements zulassen: ob Abonnenten sofort ein Commit für Änderungen auf dem Verleger ausführen oder die Änderungen in eine Warteschlange schreiben sollen; die Anmeldeinformationen zum Herstellen einer Verbindung zwischen Abonnenten und Verleger.  
  
-   Optionale Skripterstellung für das Abonnement.  
  
#### <a name="to-create-a-pull-subscription-from-the-publisher"></a>So erstellen Sie ein Pullabonnement auf dem Verleger  
  
1.  Stellen Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung, für die Sie eine oder mehrere Abonnements erstellen möchten, und klicken Sie dann auf **Neue Abonnements**.  
  
4.  Schließen Sie die Seiten im Assistenten für neue Abonnements ab.  
  
#### <a name="to-create-a-pull-subscription-from-the-subscriber"></a>So erstellen Sie ein Pullabonnement auf dem Abonnenten  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Abonnenten her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** .  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Lokale Abonnements** , und klicken Sie dann auf **Neue Abonnements**.  
  
4.  Wählen Sie im Assistenten für neue Abonnements auf der Seite **Veröffentlichung** in der Dropdownliste **Verleger** die Option **\<SQL Server-Verleger suchen>** oder **\<Oracle-Verleger suchen>** aus.  
  
5.  Stellen Sie im Dialogfeld **Verbindung mit Server herstellen** eine Verbindung mit dem Verleger her.  
  
6.  Wählen Sie auf der Seite **Veröffentlichung** eine Veröffentlichung aus.  
  
7.  Schließen Sie die Seiten im Assistenten für neue Abonnements ab.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Pullabonnements können mithilfe von gespeicherten Replikationsprozeduren programmgesteuert erstellt werden. Die verwendeten gespeicherten Prozeduren hängen vom Typ der Veröffentlichung ab, zu der das Abonnement gehört.  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>So erstellen Sie ein Pullabonnement für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Pullabonnements unterstützt, indem Sie [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) ausführen.  
  
    -   Wenn **allow_pull** im Resultset den Wert **1**hat, dann unterstützt die Veröffentlichung Pullabonnements.  
  
    -   Wenn der Wert des **Allow_pull** ist **0**, führen Sie [Sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)Angabe **Allow_pull**für **@property** und `true` für **@value**.  
  
2.  Führen Sie auf dem Abonnenten [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) aus. Geben Sie **@publisher** und **@publication**eine Momentaufnahme über FTP bereitgestellt wird. Informationen zum Aktualisieren von Abonnements finden Sie unter [Erstellen eines aktualisierbaren Abonnements für eine Transaktionsveröffentlichung](publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
3.  Führen Sie auf dem Abonnenten [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) aus. Geben Sie Folgendes an:  
  
    -   Die Parameter **@publisher**, **@publisher_db**und **@publication** .  
  
    -   Die Parameter [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen, unter denen der Verteilungs-Agent auf dem Abonnenten ausgeführt wird, für **@job_login** und **@job_password**.  
  
        > [!NOTE]  
        >  Für Verbindungen, die mit der integrierten Windows-Authentifizierung hergestellt werden, werden immer die mit **@job_login** und **@job_password**erstellt wird. Der Verteilungs-Agent stellt die lokale Verbindung mit dem Abonnenten immer mithilfe der integrierten Windows-Authentifizierung her. Standardmäßig stellt der Agent mithilfe der integrierten Windows-Authentifizierung eine Verbindung mit dem Verteiler her.  
  
    -   (Optional) Der Wert **0** für **@distributor_security_mode** und [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@distributor_login** und **@distributor_password**, wenn die Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn es sich bei der verbindungsherstellung zum Verteiler.  
  
    -   Einen Zeitplan für den Verteilungs-Agentauftrag für dieses Abonnement. Weitere Informationen finden Sie unter [Angeben von Synchronisierungszeitplänen](specify-synchronization-schedules.md).  
  
4.  Führen Sie auf dem Verleger [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) aus, um das Pullabonnement zu registrieren. Geben Sie **@publication**, **@subscriber**und **@destination_db**verfügbar ist. Geben Sie den Wert **pull** für **@subscription_type**.  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication"></a>So erstellen Sie ein Pullabonnement für eine Mergeveröffentlichung  
  
1.  Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Pullabonnements unterstützt, indem Sie [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql) ausführen.  
  
    -   Wenn **allow_pull** im Resultset den Wert **1**hat, dann unterstützt die Veröffentlichung Pullabonnements.  
  
    -   Wenn der Wert des **Allow_pull** ist **0**, führen Sie [Sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), wobei **Allow_pull** für **@property** und `true` für **@value**.  
  
2.  Führen Sie auf dem Abonnenten [sp_addmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql) aus. Geben Sie **@publisher**, **@publisher_db**, **@publication**und die folgenden Parameter an:  
  
    -   **@subscriber_type**: geben Sie für ein Clientabonnement **local** und für ein Serverabonnement **global** an.  
  
    -   **@subscription_priority**: Legen Sie für das Abonnement eine Priorität fest (**0.00** bis **99.99**). Dies ist nur für Serverabonnements erforderlich.  
  
         Weitere Informationen finden Sie unter [Erweiterte Konflikterkennung und -lösung bei der Mergereplikation](merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  Führen Sie auf dem Abonnenten [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql) aus. Geben Sie die folgenden Parameter an:  
  
    -   **@publisher**, **@publisher_db**und **@publication**.  
  
    -   Die Windows-Anmeldeinformationen, unter denen der Merge-Agent auf dem Abonnenten ausgeführt wird, für **@job_login** und **@job_password**.  
  
        > [!NOTE]  
        >  Für Verbindungen, die mit der integrierten Windows-Authentifizierung hergestellt werden, werden immer die mit **@job_login** und **@job_password**. Der Merge-Agent stellt die lokale Verbindung mit dem Abonnenten immer mithilfe der Windows-Authentifizierung her. Standardmäßig stellt der Agent mithilfe der integrierten Windows-Authentifizierung eine Verbindung mit dem Verteiler und dem Verleger her.  
  
    -   (Optional) Den Wert **0** für **@distributor_security_mode** und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@distributor_login** und **@distributor_password**, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung für den Verbindungsaufbau mit dem Verteiler verwendet werden muss.  
  
    -   (Optional) Den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung für den Verbindungsaufbau mit dem Verleger verwendet werden muss.  
  
    -   Einen Zeitplan für den Merge-Agentauftrag für dieses Abonnement. Weitere Informationen finden Sie unter [Erstellen eines aktualisierbaren Abonnements für eine Transaktionsveröffentlichung](publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
4.  Führen Sie auf dem Verleger [sp_addmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) aus. Geben Sie **@publication**, **@subscriber**, **@subscriber_db**und den Wert **pull** für **@subscription_type**. Damit wird das Pullabonnement registriert.  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 Im folgenden Beispiel wird ein Pullabonnement für eine Transaktionsveröffentlichung erstellt. Der erste Batch wird auf dem Abonnenten ausgeführt, und der zweite Batch wird auf dem Verleger ausgeführt. Die Werte für den Anmeldenamen und das Kennwort werden zur Laufzeit mithilfe von sqlcmd-Skriptvariablen bereitgestellt.  
  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpullsub.sql#sp_addtranpullsubscriptionagent)]  
  
 [!code-sql[HowTo#sp_addtranpullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpullsub.sql#sp_addtranpullsubscription)]  
  
 Im folgenden Beispiel wird ein Pullabonnement für eine Mergeveröffentlichung erstellt. Der erste Batch wird auf dem Abonnenten ausgeführt, und der zweite Batch wird auf dem Verleger ausgeführt. Die Werte für den Anmeldenamen und das Kennwort werden zur Laufzeit mithilfe von **sqlcmd** -Skriptvariablen bereitgestellt.  
  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsub.sql#sp_addmergepullsubscriptionagent)]  
  
 [!code-sql[HowTo#sp_addmergepullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsub.sql#sp_addmergepullsubscription)]  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Die RMO-Klassen, die zum Erstellen eines Pullabonnements verwendet werden, richten sich nach dem Typ der Veröffentlichung, zu der das Abonnement gehört.  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>So erstellen Sie ein Pullabonnement für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Stellen Sie die Verbindung zum Abonnenten und zum Verleger her, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPublication> -Klasse, indem Sie die Verlegerverbindung aus Schritt 1 verwenden. Geben Sie <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> und <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>an.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>-Methode auf. Wenn diese Methode `false` zurückgibt, sind entweder die in Schritt 2 angegebenen Eigenschaften falsch definiert, oder die Veröffentlichung ist auf dem Server nicht vorhanden.  
  
4.  Führen Sie ein bitweises logisches AND (`&` in Visual C# und `And` in Visual Basic) zwischen der <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>-Eigenschaft und <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull> aus. Falls das Ergebnis <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None> lautet, legen Sie für <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> das Ergebnis eines bitweisen logischen OR (`|` in Visual C# und `Or` in Visual Basic) zwischen <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> und <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull> fest. Rufen Sie dann <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> auf, um Pullabonnements zu ermöglichen.  
  
5.  Falls die Abonnementdatenbank nicht vorhanden ist, erstellen Sie sie mithilfe der <xref:Microsoft.SqlServer.Management.Smo.Database> -Klasse. Weitere Informationen finden Sie unter [Erstellen, Ändern und Löschen von Datenbanken](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPullSubscription> -Klasse.  
  
7.  Legen Sie folgende Eigenschaften für das Abonnement fest:  
  
    -   Die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> zu dem in Schritt 1 erstellten Abonnenten für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>  
  
    -   Name der Abonnementdatenbank für <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Name des Verlegers für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   Name der Veröffentlichungsdatenbank für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   Name der Veröffentlichung für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   Die Felder <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> und <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> oder <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> von <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>, um die Anmeldeinformationen für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto bereitzustellen, unter dem der Verteilungs-Agent auf dem Abonnenten ausgeführt wird. Mit diesem Konto werden lokale Verbindungen mit dem Abonnenten sowie Remoteverbindungen mithilfe der Windows-Authentifizierung hergestellt.  
  
        > [!NOTE]  
        >  <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> muss zwar nicht festgelegt werden, wenn das Abonnement von einem Mitglied der festen Serverrolle `sysadmin` erstellt wurde, aber es empfiehlt sich. In diesem Fall nimmt der Agent die Identität des SQL Server-Agent-Kontos an. Weitere Informationen finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
    -   (Optional) Den Wert `true` für <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A>, um einen Agentauftrag zu erstellen, mit dem das Abonnement synchronisiert wird. Wenn Sie `false` angeben (Standard), kann das Abonnement nur programmgesteuert synchronisiert werden, und Sie müssen zusätzliche Eigenschaften für <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> angeben, wenn Sie von der <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A>-Eigenschaft auf dieses Objekt zugreifen. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
        > [!NOTE]  
        >  Der SQL Server-Agent ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Wenn Sie den Wert `true` für Express-Abonnenten angeben, wird der Agentauftrag nicht erstellt. Jedoch werden wichtige abonnementbezogene Metadaten auf dem Abonnenten gespeichert.  
  
    -   (Optional) Legen Sie die Werte der Felder <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> und <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> oder <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> für <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> fest, wenn Sie die SQL Server-Authentifizierung verwenden, um die Verbindung zum Verteiler herzustellen.  
  
8.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> -Methode auf.  
  
9. Rufen Sie mit der Instanz der <xref:Microsoft.SqlServer.Replication.TransPublication> -Klasse aus Schritt 2 die <xref:Microsoft.SqlServer.Replication.TransPublication.MakePullSubscriptionWellKnown%2A> -Methode auf, um das Pullabonnement beim Verleger zu registrieren. Wenn diese Registrierung bereits vorhanden ist, tritt eine Ausnahme auf.  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication"></a>So erstellen Sie ein Pullabonnement für eine Mergeveröffentlichung  
  
1.  Stellen Sie die Verbindung zum Abonnenten und zum Verleger her, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication> -Klasse, indem Sie die Verlegerverbindung aus Schritt 1 verwenden. Geben Sie <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>und <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>an.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>-Methode auf. Wenn diese Methode `false` zurückgibt, sind entweder die in Schritt 2 angegebenen Eigenschaften falsch definiert, oder die Veröffentlichung ist auf dem Server nicht vorhanden.  
  
4.  Führen Sie ein bitweises logisches AND (`&` in Visual C# und `And` in Visual Basic) zwischen der <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>-Eigenschaft und <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull> aus. Falls das Ergebnis <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None> lautet, legen Sie für <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> das Ergebnis eines bitweisen logischen OR (`|` in Visual C# und `Or` in Visual Basic) zwischen <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> und <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull> fest. Rufen Sie dann <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> auf, um Pullabonnements zu ermöglichen.  
  
5.  Falls die Abonnementdatenbank nicht vorhanden ist, erstellen Sie sie mithilfe der <xref:Microsoft.SqlServer.Management.Smo.Database> -Klasse. Weitere Informationen finden Sie unter [Erstellen, Ändern und Löschen von Datenbanken](../server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePullSubscription> -Klasse.  
  
7.  Legen Sie folgende Eigenschaften für das Abonnement fest:  
  
    -   Die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> zu dem in Schritt 1 erstellten Abonnenten für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>  
  
    -   Name der Abonnementdatenbank für <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.  
  
    -   Name des Verlegers für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.  
  
    -   Name der Veröffentlichungsdatenbank für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.  
  
    -   Name der Veröffentlichung für <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.  
  
    -   Die Felder <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> und <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> oder <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> von <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>, um die Anmeldeinformationen für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto bereitzustellen, unter dem der Merge-Agent auf dem Abonnenten ausgeführt wird. Mit diesem Konto werden lokale Verbindungen mit dem Abonnenten sowie Remoteverbindungen mithilfe der Windows-Authentifizierung hergestellt.  
  
        > [!NOTE]  
        >  <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> muss zwar nicht festgelegt werden, wenn das Abonnement von einem Mitglied der festen Serverrolle `sysadmin` erstellt wurde, aber es empfiehlt sich. In diesem Fall nimmt der Agent die Identität des SQL Server-Agent-Kontos an. Weitere Informationen finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
    -   (Optional) Den Wert `true` für <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A>, um einen Agentauftrag zu erstellen, mit dem das Abonnement synchronisiert wird. Wenn Sie `false` angeben (Standard), kann das Abonnement nur programmgesteuert synchronisiert werden, und Sie müssen zusätzliche Eigenschaften für <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> angeben, wenn Sie von der <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A>-Eigenschaft auf dieses Objekt zugreifen. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
    -   (Optional) Legen Sie die Werte der Felder <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> und <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> oder <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> für <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> fest, wenn Sie die SQL Server-Authentifizierung verwenden, um die Verbindung zum Verteiler herzustellen.  
  
    -   (Optional) Legen Sie die Felder <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> und <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> oder <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> von <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> fest, wenn Sie die SQL Server-Authentifizierung zum Herstellen einer Verbindung mit dem Verleger verwenden.  
  
8.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>-Methode auf.  
  
9. Rufen Sie mit der Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication> -Klasse aus Schritt 2 die <xref:Microsoft.SqlServer.Replication.MergePublication.MakePullSubscriptionWellKnown%2A> -Methode auf, um das Pullabonnement beim Verleger zu registrieren. Wenn diese Registrierung bereits vorhanden ist, tritt eine Ausnahme auf.  
  
###  <a name="PShellExample"></a> Beispiel (RMO)  
 Im folgenden Beispiel wird ein neues Pullabonnement für eine Transaktionsveröffentlichung erstellt. Die Anmeldeinformationen für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto, mit dem der Verteilungs-Agentauftrag erstellt wird, werden zur Laufzeit übergeben.  
  
 [!code-csharp[HowTo#rmo_CreateTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranpullsub)]  
  
 Im folgenden Beispiel wird ein Pullabonnement für eine Mergeveröffentlichung erstellt. Die Anmeldeinformationen für das Windows-Konto, mit dem der Merge-Agentauftrag erstellt wird, werden zur Laufzeit übergeben.  
  
 [!code-csharp[HowTo#rmo_CreateMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepullsub)]  
  
 In diesem Beispiel wird ein Pullabonnement für eine Mergeveröffentlichung erstellt, ohne dass ein zugehöriger Agentauftrag und Abonnementmetadaten in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql)erstellt werden. Die Anmeldeinformationen für das Windows-Konto, mit dem der Merge-Agentauftrag erstellt wird, werden zur Laufzeit übergeben.  
  
 [!code-csharp[HowTo#rmo_CreateMergePullSub_NoJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepullsub_nojob)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePullSub_NoJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepullsub_nojob)]  
  
 In diesem Beispiel wird ein Pullabonnement für eine Mergeveröffentlichung erstellt, das mithilfe der Websynchronisierung über das Internet synchronisiert werden kann. Die Anmeldeinformationen für das Windows-Konto, mit dem der Merge-Agentauftrag erstellt wird, werden zur Laufzeit übergeben. Weitere Informationen finden Sie unter [Configure Web Synchronization](configure-web-synchronization.md).  
  
 [!code-csharp[HowTo#rmo_CreateMergePullSub_WebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepullsub_websync)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePullSub_WebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepullsub_websync)]  
  
## <a name="see-also"></a>Siehe auch  
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Anzeigen und Ändern der Eigenschaften von Pullabonnements](view-and-modify-pull-subscription-properties.md)   
 [Konfigurieren der Websynchronisierung](configure-web-synchronization.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)   
 [Bewährte Methoden für die Replikationssicherheit](security/replication-security-best-practices.md)  
  
  
