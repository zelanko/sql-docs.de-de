---
title: Erstellen und Anwenden der Anfangsmomentaufnahme | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], creating
- snapshot replication [SQL Server], initial snapshots
ms.assetid: 742727a1-5189-44ec-b3ae-6fd7aa1f5347
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7ac008fe139adf55376bb50fbf60dddcd6b9ae5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010885"
---
# <a name="create-and-apply-the-initial-snapshot"></a>Erstellen und Anwenden der Anfangsmomentaufnahme
  In diesem Thema wird beschrieben, wie die Anfangsmomentaufnahme in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) erstellt und übernommen wird. Mergeveröffentlichungen, die parametrisierte Filter verwenden, erfordern eine zweiteilige Momentaufnahme. Weitere Informationen finden Sie unter [Erstellen einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 **In diesem Thema**  
  
-   **So erstellen Sie die Anfangsmomentaufnahme und wenden sie an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt wird, wird vom Momentaufnahme-Agent standardmäßig sofort eine Momentaufnahme generiert, nachdem mit dem Assistenten für neue Veröffentlichung eine Veröffentlichung erstellt wurde. Diese Momentaufnahme wird dann standardmäßig vom Verteilungs-Agent (bei der Momentaufnahme- und der Transaktionsreplikation) oder vom Merge-Agent (bei Mergeabonnement) für alle Abonnements angewendet. Eine Momentaufnahme kann auch mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und dem Replikationsmonitor generiert werden. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md).  
  
#### <a name="to-create-a-snapshot-in-management-studio"></a>So erstellen Sie eine Momentaufnahme in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung, für die Sie eine Momentaufnahme erstellen möchten, und klicken Sie anschließend auf **Status des Momentaufnahme-Agents anzeigen**.  
  
4.  Klicken Sie im Dialogfeld **Momentaufnahmen-Agent \<Publication> Status anzeigen-** auf **Start**.  
  
 Nachdem der Momentaufnahme-Agent die Momentaufnahme generiert hat, wird eine Meldung angezeigt, die beispielsweise wie folgt lautet: "[100%] Es wurde eine Momentaufnahme mit 17 Artikel(n) generiert".  
  
#### <a name="to-create-a-snapshot-in-replication-monitor"></a>So erstellen Sie eine Momentaufnahme im Replikationsmonitor  
  
1.  Erweitern Sie im Replikationsmonitor im linken Bereich eine Verlegergruppe, und erweitern Sie dann einen Verleger.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung, für die Sie eine Momentaufnahme generieren möchten, und klicken Sie anschließend auf **Momentaufnahme generieren**.  
  
3.  Zum Anzeigen des Status der Momentaufnahmen-Agent klicken Sie auf die Registerkarte **Agents** . Um ausführlichere Informationen zu erhalten, klicken Sie mit der rechten Maustaste auf das Momentaufnahmen-Agent im Raster, und klicken Sie dann auf **Details anzeigen**.  
  
#### <a name="to-apply-a-snapshot"></a>So wenden Sie eine Momentaufnahme an  
  
1.  Eine generierte Momentaufnahme wird angewendet, indem das Abonnement mit dem Verteilungs-Agent oder dem Merge-Agent synchronisiert wird:  
  
    -   Wenn der Agent fortlaufend ausgeführt wird (die Standardeinstellung bei der Transaktionsreplikation), wird die Momentaufnahme automatisch nach dem Generieren angewendet.  
  
    -   Wenn der Agent nach einem Zeitplan ausgeführt wird, wird die Momentaufnahme bei der nächsten geplanten Ausführung des Agents angewendet.  
  
    -   Wenn der Agent bedarfsgesteuert ausgeführt wird, wird der Snapshot bei der nächsten Ausführung des Agents angewendet.  
  
     Weitere Informationen zum Synchronisieren von Abonnements finden Sie unter [Synchronize a Push Subscription](synchronize-a-push-subscription.md) und [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)verfügbar ist.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können Anfangsmomentaufnahmen programmgesteuert erstellen, indem Sie entweder einen Momentaufnahme-Agentauftrag erstellen und ausführen oder die ausführbare Datei für den Momentaufnahme-Agent von einer Batchdatei ausführen. Nachdem eine Anfangsmomentaufnahme generiert wurde, wird sie an den Abonnenten übertragen und auf diesen angewendet, sobald die erste Synchronisierung für das Abonnement durchgeführt wird. Wenn Sie den Momentaufnahme-Agent von der Eingabeaufforderung oder einer Batchdatei ausführen, müssen Sie den Agent immer dann erneut ausführen, wenn die bestehende Momentaufnahme ungültig wird.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
#### <a name="to-create-and-run-a-snapshot-agent-job-to-generate-the-initial-snapshot"></a>So erstellen Sie einen Momentaufnahme-Agentauftrag und führen ihn aus, um die Anfangsmomentaufnahme zu generieren  
  
1.  Erstellen Sie eine Momentaufnahme-, Transaktions- oder Mergeveröffentlichung. Weitere Informationen finden Sie unter [Erstellen einer Veröffentlichung](publish/create-a-publication.md).  
  
2.  Führen Sie [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) aus. Geben Sie **@publication** und die folgenden Parameter an:  
  
    -   **Der @job_login**: Gibt die Anmeldeinformationen für die Windows-Authentifizierung an, mit denen der Momentaufnahme-Agent auf dem Verteiler ausgeführt wird.  
  
    -   **Der @job_password**: Kennwort für die angegebenen Windows-Anmeldeinformationen.  
  
    -   (Optional) Den Wert **0** für **@publisher_security_mode** , wenn der Agent die SQL Server-Authentifizierung zum Herstellen der Verbindung mit dem Verleger verwendet. In diesem Fall müssen Sie auch die Anmelde Informationen für die SQL Server Authentifizierung für **@publisher_login** und angeben **@publisher_password** .  
  
    -   (Optional) Einen Synchronisierungszeitplan für den Momentaufnahme-Agentauftrag. Weitere Informationen finden Sie unter [Angeben von Synchronisierungs Zeitplänen](specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Fügen Sie der Veröffentlichung Artikel hinzu. Weitere Informationen finden Sie unter [Definieren eines Artikels](publish/define-an-article.md).  
  
4.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_startpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql) unter Angabe des Werts **@publication** aus Schritt 1 aus.  
  
#### <a name="to-run-the-snapshot-agent-to-generate-the-initial-snapshot"></a>So führen Sie den Momentaufnahme-Agent zum Generieren der Anfangsmomentaufnahme aus  
  
1.  Erstellen Sie eine Momentaufnahme-, Transaktions- oder Mergeveröffentlichung. Weitere Informationen finden Sie unter [Erstellen einer Veröffentlichung](publish/create-a-publication.md).  
  
2.  Fügen Sie der Veröffentlichung Artikel hinzu. Weitere Informationen finden Sie unter [Definieren eines Artikels](publish/define-an-article.md).  
  
3.  Starten Sie den [Replication Snapshot Agent](agents/replication-snapshot-agent.md) von der Eingabeaufforderung oder in einer Batchdatei, indem Sie die Datei **snapshot.exe**ausführen. Geben Sie hierzu die folgenden Befehlszeilenargumente ein:  
  
    -   **-Veröffentlichung**  
  
    -   **-Publisher**  
  
    -   **-Verteiler**  
  
    -   **-PublisherDB**  
  
    -   **-ReplicationType**  
  
     Wenn Sie die SQL Server-Authentifizierung verwenden, müssen Sie auch die folgenden Argumente angeben:  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-Distributor SecurityMode**  =  **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode**  =  **0**  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 In diesem Beispiel wird eine Transaktionsveröffentlichung erstellt und ein Momentaufnahme-Agentauftrag für die neue Veröffentlichung hinzugefügt (mithilfe von **sqlcmd** -Skriptvariablen). Im Beispiel wird der Auftrag auch gestartet.  
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../snippets/tsql/SQL15/replication/howto/tsql/createtranpubinitialsnapshot.sql#sp_trangenerate_snapshot)]  
  
 In diesem Beispiel wird eine Mergeveröffentlichung erstellt und ein Momentaufnahme-Agentauftrag für die Veröffentlichung hinzugefügt (mithilfe von **sqlcmd** -Variablen). Im Beispiel wird der Auftrag auch gestartet.  
  
 [!code-sql[HowTo#sp_mergegenerate_snapshot](../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubinitialsnapshot.sql#sp_mergegenerate_snapshot)]  
  
 Die folgenden Befehlszeilenargumente starten den Momentaufnahme-Agent, um die Momentaufnahme für eine Mergeveröffentlichung zu generieren.  
  
> [!NOTE]  
>  Zeilenumbrüche wurden hinzugefügt, um die Lesbarkeit zu verbessern. In einer Batchdatei müssen Befehle in einer einzelnen Zeile stehen.  
  
 [!code-sql[HowTo#startmergesnapshot_10](../../snippets/tsql/SQL15/replication/howto/tsql/createmergesnapshot_10.bat)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Momentaufnahmen werden nach dem Erstellen einer Veröffentlichung vom Momentaufnahme-Agent generiert. Sie können diese Momentaufnahmen mit Replikationsverwaltungsobjekten (RMO) und dem direkten Zugriff von verwaltetem Code auf Funktionen des Replikations-Agents programmgesteuert generieren. Welche Objekte Sie verwenden, hängt vom Typ der Replikation ab. Der Momentaufnahme-Agent kann synchron mit dem <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Objekt oder asynchron mit dem Agentauftrag gestartet werden. Nachdem die Anfangsmomentaufnahme generiert wurde, wird sie an den Abonnenten übertragen und auf diesen angewendet, sobald die erste Synchronisierung für das Abonnement durchgeführt wird. Sie müssen den Agent immer dann erneut ausführen, wenn die vorhandene Momentaufnahme keine gültigen und aktuellen Daten mehr enthält. Weitere Informationen finden Sie unter [Verwalten von Veröffentlichungen](publish/maintain-publications.md).  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Sie Anmelde Informationen speichern müssen, verwenden Sie die [Kryptografiedienste](https://go.microsoft.com/fwlink/?LinkId=34733) , die vom Windows-.NET Framework bereitgestellt werden [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>So generieren Sie die Anfangsmomentaufnahme für eine Momentaufnahme- oder Transaktionsveröffentlichung durch Starten des Auftrags des Momentaufnahme-Agents (asynchron)  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPublication>-Klasse. Legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> -Eigenschaft und die <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> -Eigenschaft für die Veröffentlichung fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die restlichen Objekteigenschaften zu laden. Wenn diese Methode `false` zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  Wenn der Wert von <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> auf `false` lautet, rufen Sie <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> auf, um den Agentauftrag für die Momentaufnahme dieser Veröffentlichung zu erstellen.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> -Methode auf, um den Agentauftrag zu starten, der die Momentaufnahme für diese Veröffentlichung generiert.  
  
6.  (Optional) Wenn der Wert von <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> auf `true` lautet, steht die Momentaufnahme den Abonnenten zur Verfügung.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-running-the-snapshot-agent-synchronous"></a>So generieren Sie die Anfangsmomentaufnahme für eine Momentaufnahme- oder Transaktionsveröffentlichung durch Ausführen des Momentaufnahme-Agents (synchron)  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Klasse, und legen Sie die folgenden erforderlichen Eigenschaften fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> – Name des Verlegers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> – Name der Veröffentlichungsdatenbank  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> &ndash; Den Namen der Veröffentlichung  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> &ndash; Den Namen des Verteilers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> zur Verwendung der Windows-Authentifizierung, wenn eine Verbindung mit dem Verleger hergestellt wird, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> sowie Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> zur Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn eine Verbindung mit dem Verleger hergestellt wird. Die Windows-Authentifizierung wird empfohlen.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> zur Verwendung der Windows-Authentifizierung, wenn eine Verbindung mit dem Verteiler hergestellt wird, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> sowie Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> zur Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn eine Verbindung mit dem Verteiler hergestellt wird. Die Windows-Authentifizierung wird empfohlen.  
  
2.  Legen Sie den Wert <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> oder <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A>-Methode auf.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-merge-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>So generieren Sie die Anfangsmomentaufnahme für eine Mergeveröffentlichung durch Starten des Auftrags des Momentaufnahme-Agents (asynchron)  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication>-Klasse. Legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> -Eigenschaft und die <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> -Eigenschaft für die Veröffentlichung fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die restlichen Objekteigenschaften zu laden. Wenn diese Methode `false` zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  Wenn der Wert von <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> auf `false` lautet, rufen Sie <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> auf, um den Agentauftrag für die Momentaufnahme dieser Veröffentlichung zu erstellen.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> -Methode auf, um den Agentauftrag zu starten, der die Momentaufnahme für diese Veröffentlichung generiert.  
  
6.  (Optional) Wenn der Wert von <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> auf `true` lautet, steht die Momentaufnahme den Abonnenten zur Verfügung.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-merge-publication-by-running-the-snapshot-agent-synchronous"></a>So generieren Sie die Anfangsmomentaufnahme für eine Mergeveröffentlichung durch Ausführen des Momentaufnahme-Agents (synchron)  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Klasse, und legen Sie die folgenden erforderlichen Eigenschaften fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> – Name des Verlegers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> – Name der Veröffentlichungsdatenbank  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> &ndash; Den Namen der Veröffentlichung  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> &ndash; Den Namen des Verteilers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> zur Verwendung der Windows-Authentifizierung, wenn eine Verbindung mit dem Verleger hergestellt wird, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> sowie Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> zur Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn eine Verbindung mit dem Verleger hergestellt wird. Die Windows-Authentifizierung wird empfohlen.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> zur Verwendung der Windows-Authentifizierung, wenn eine Verbindung mit dem Verteiler hergestellt wird, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> sowie Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> zur Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn eine Verbindung mit dem Verteiler hergestellt wird. Die Windows-Authentifizierung wird empfohlen.  
  
2.  Legen Sie den Wert <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A>-Methode auf.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a>Beispiele (RMO)  
 In diesem Beispiel wird der Momentaufnahme-Agent synchron ausgeführt, um die Anfangsmomentaufnahme für eine Transaktionsveröffentlichung zu generieren.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 In diesem Beispiel wird der Agentauftrag asynchron ausgeführt, um die Anfangsmomentaufnahme für eine Transaktionsveröffentlichung zu generieren.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](publish/create-a-publication.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Erstellen eines Pushabonnements](create-a-push-subscription.md)   
 [Synchronisierungs Zeitpläne angeben](specify-synchronization-schedules.md)   
 [Erstellen und Anwenden der Momentaufnahme](create-and-apply-the-snapshot.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](initialize-a-subscription-with-a-snapshot.md)   
 [Replikationsverwaltungsobjekte Konzepte](concepts/replication-management-objects-concepts.md)   
 [Bewährte Sicherheitsmethoden für die Replikation](security/replication-security-best-practices.md)   
 [Konzepte für gespeicherte System Prozeduren von](concepts/replication-system-stored-procedures-concepts.md)   
 [Verwenden von sqlcmd mit Skriptvariablen](../scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
