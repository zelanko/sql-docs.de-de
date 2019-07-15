---
title: Erstellen und Anwenden der Anfangsmomentaufnahme | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], creating
- snapshot replication [SQL Server], initial snapshots
ms.assetid: 742727a1-5189-44ec-b3ae-6fd7aa1f5347
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 48a3bfbca1b133be9c8be9b05fef3f4e2dd9ae14
ms.sourcegitcommit: 636c02bd04f091ece934e78640b2363d88cac28d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860737"
---
# <a name="create-and-apply-the-initial-snapshot"></a>Erstellen und Anwenden der Anfangsmomentaufnahme
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In diesem Thema wird beschrieben, wie die Anfangsmomentaufnahme in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) erstellt und übernommen wird. Mergeveröffentlichungen, die parametrisierte Filter verwenden, erfordern eine zweiteilige Momentaufnahme. Weitere Informationen finden Sie unter [Erstellen einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  Momentaufnahmen werden nach dem Erstellen einer Veröffentlichung vom Momentaufnahme-Agent generiert. Sie können folgendermaßen generiert werden:  
  
-   Sofort. Standardmäßig wird eine Momentaufnahme für eine Mergeveröffentlichung sofort nach dem Erstellen der Veröffentlichung im Assistenten für neue Veröffentlichung generiert.    
-   Zu einem geplanten Zeitpunkt. Geben Sie auf der Seite **Momentaufnahme-Agent** des Assistenten für neue Veröffentlichung oder beim Verwenden von gespeicherten Prozeduren bzw. Replikationsverwaltungsobjekten (RMO) einen Zeitpunkt an.    
-   Manuell. Führen Sie den Momentaufnahme-Agent von der Eingabeaufforderung oder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aus. Weitere Informationen zum Ausführen von Agents finden Sie unter [Ausführbare Konzepte für die Programmierung von Replikations-Agents](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) und [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
Bei der Mergereplikation wird jedes Mal eine Momentaufnahme generiert, wenn der Momentaufnahme-Agent ausgeführt wird. Bei der Transaktionsreplikation hängt die Momentaufnahmegenerierung von der Einstellung der **immediate_sync**-Veröffentlichungseigenschaft ab. Ist die Eigenschaft auf TRUE festgelegt (die Standardeinstellung bei der Verwendung des Assistenten für neue Veröffentlichung), wird bei jedem Ausführen des Momentaufnahme-Agents eine Momentaufnahme generiert, der jederzeit auf einen Abonnenten angewendet werden kann. Ist die Eigenschaft auf FALSE festgelegt (die Standardeinstellung bei der Verwendung von **sp_addpublication**), wird die Momentaufnahme nur dann generiert, wenn seit dem letzten Ausführen des Momentaufnahme-Agents ein neues Abonnement hinzugefügt wurde. Abonnenten können erst synchronisiert werden, nachdem der Momentaufnahme-Agent abgeschlossen ist.  
  
Generierte Momentaufnahmen werden im Standardmomentaufnahmeordner auf dem Verteiler gespeichert. Sie können Momentaufnahmedateien aber auch auf Wechselmedien wie z. B. Wechseldatenträgern, CD-ROMs oder an anderen Speicherorten als dem Standardmomentaufnahmeordner speichern. Darüber hinaus können Sie die Momentaufnahmedateien komprimieren, sodass sie leichter zu speichern und zu übertragen sind, und Skripts vor oder nach der Anwendung der Momentaufnahme auf den Abonnenten ausführen. Weitere Informationen zu diesen Optionen finden Sie unter [Snapshot Options](../../relational-databases/replication/snapshot-options.md).  
  
Handelt es sich um eine Momentaufnahme für eine Mergeveröffentlichung, die parametrisierte Filter verwendet, wird die Momentaufnahme mit einem zweiteiligen Prozess erstellt. Zuerst wird eine Schemamomentaufnahme erstellt, die die Replikationsskripts und das Schema der veröffentlichten Objekte enthält, nicht jedoch die Daten. Jedes Abonnement wird dann mit einer Momentaufnahme initialisiert, die die aus der Schemamomentaufnahme kopierten Skripts und das Schema sowie die Daten enthält, die zur Partition des Abonnements gehören. Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
Nachdem die Momentaufnahme auf dem Verleger erstellt und am standardmäßigen bzw. einem anderen Momentaufnahmespeicherort gespeichert wurde, kann sie an den Abonnenten übertragen und auf diesen angewendet werden. Der Verteilungs-Agent (bei Momentaufnahme- oder Transaktionsreplikation) bzw. der Merge-Agent (bei Mergereplikation) überträgt die Momentaufnahme und wendet die Schema- und Datendateien während der Erstsynchronisierung auf die Abonnement-Datenbank auf dem Abonnenten an. Standardmäßig erfolgt die Erstsynchronisierung unmittelbar nach dem Erstellen einer Abonnements, wenn Sie den Assistenten für neue Veröffentlichung verwenden. Dieses Verhalten wird von der Option **Initialisierungszeitpunkt** auf der Seite **Abonnements initialisieren** des Assistenten gesteuert. Wenn Momentaufnahmen generiert werden, nachdem ein Abonnement initialisiert wurde, werden sie nicht auf den Abonnenten angewendet, es sei denn, ein Abonnement ist für die erneute Initialisierung markiert. Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
Nachdem der Verteilungs- bzw. der Merge-Agent die Anfangsmomentaufnahme angewendet hat, gibt er nachfolgende Updates und andere Datenänderungen weiter. Wenn Momentaufnahmen an Abonnenten verteilt und auf ihnen angewendet werden, sind nur die Abonnenten betroffen, die auf eine Anfangsmomentaufnahme oder neue Momentaufnahmen warten. Andere Abonnenten dieser Veröffentlichung (diejenigen, die bereits Einfügungen, Updates, Löschungen oder andere Änderungen der veröffentlichten Daten empfangen) sind nicht betroffen.  

Informationen zum Anzeigen oder Ändern des Standardspeicherorts für den Momentaufnahmeordner finden Sie im entsprechenden Abschnitt.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Ändern von Momentaufnahmeoptionen](../../relational-databases/replication/snapshot-options.md)  
  
-   Replikations- und RMO-Programmierung: [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)  

## <a name="default-snapshot-location"></a>Standardspeicherort für Momentaufnahmen

 Geben Sie den standardmäßigen Momentaufnahmespeicherort im Verteilungskonfigurations-Assistenten auf der Seite **Snapshotordner** an. Weitere Informationen zum Verwenden dieses Assistenten finden Sie unter [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md). Wenn Sie eine Veröffentlichung auf einem Server erstellen, der nicht als Verteiler konfiguriert ist, geben Sie im Assistenten für neue Veröffentlichung auf der Seite **Momentaufnahmeordner** einen standardmäßigen Momentaufnahmespeicherort an. Weitere Informationen zum Zugreifen auf diesen Assistenten finden Sie unter [Erstellen einer Veröffentlichung](../../relational-databases/replication/publish/create-a-publication.md).  
  
 Ändern Sie den standardmäßigen Momentaufnahmespeicherort im Dialogfeld **Verteilereigenschaften - \<Distributor>** auf der Seite **Verleger**. Weitere Informationen finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md). Bestimmen Sie den Momentaufnahmeordner für die einzelnen Veröffentlichungen im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** . Weitere Informationen finden Sie unter [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="modify-the-default-snapshot-location"></a>Ändern des Standardspeicherorts für Momentaufnahmen  
  
1.  Klicken Sie auf der Seite **Verleger** des Dialogfelds **Verteilereigenschaften – \<Verteiler>** auf die Schaltfläche mit den Auslassungspunkten ( **...** ) für den Verleger, dessen standardmäßiger Momentaufnahmespeicherort geändert werden soll.  
  
2.  Geben Sie im Dialogfeld **Verlegereigenschaften - \<Publisher>** einen Wert für die Eigenschaft **Standardmomentaufnahmeordner** ein.  
  
    > [!NOTE]  
    >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="create-snapshot"></a>Erstellen einer Momentaufnahme
Wenn der SQL Server-Agent ausgeführt wird, wird vom Momentaufnahmen-Agent standardmäßig sofort eine Momentaufnahme generiert, nachdem mit dem Assistenten für neue Veröffentlichung eine Veröffentlichung erstellt wurde. Diese Momentaufnahme wird dann standardmäßig vom Verteilungs-Agent (bei der Momentaufnahme- und der Transaktionsreplikation) oder vom Merge-Agent (bei Mergeabonnement) für alle Abonnements angewendet. Eine Momentaufnahme kann auch mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und dem Replikationsmonitor generiert werden. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  

### <a name="using-sql-server-management-studio"></a>Verwendung von SQL Server Management Studio

1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.    
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .    
3.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung, für die Sie eine Momentaufnahme erstellen möchten, und klicken Sie anschließend auf **Status des Momentaufnahme-Agents anzeigen**.    
4.  Klicken Sie im Dialogfeld **Status des Momentaufnahme-Agents anzeigen - \<Publication>** auf **Start**.    
 Nachdem der Momentaufnahme-Agent die Momentaufnahme generiert hat, wird eine Meldung angezeigt, die beispielsweise wie folgt lautet: "[100%] Es wurde eine Momentaufnahme mit 17 Artikel(n) generiert".  
  
### <a name="in-replication-monitor"></a>Im Replikationsmonitor:  
  
1.  Erweitern Sie im Replikationsmonitor im linken Bereich eine Verlegergruppe, und erweitern Sie dann einen Verleger.    
2.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung, für die Sie eine Momentaufnahme generieren möchten, und klicken Sie anschließend auf **Momentaufnahme generieren**.    
3.  Um den Status des Momentaufnahme-Agents anzuzeigen, klicken Sie auf die Registerkarte **Agents** . Wenn Sie genauere Informationen anzeigen möchten, klicken Sie im Raster mit der rechten Maustaste auf den Momentaufnahme-Agent, und klicken Sie dann auf **Details anzeigen**.  

## <a name="using-transact-sql"></a>Verwenden von Transact-SQL
Sie können Anfangsmomentaufnahmen programmgesteuert erstellen, indem Sie entweder einen Momentaufnahme-Agentauftrag erstellen und ausführen oder die ausführbare Datei für den Momentaufnahme-Agent von einer Batchdatei ausführen. Nachdem eine Anfangsmomentaufnahme generiert wurde, wird sie an den Abonnenten übertragen und auf diesen angewendet, sobald die erste Synchronisierung für das Abonnement durchgeführt wird. Wenn Sie den Momentaufnahme-Agent von der Eingabeaufforderung oder einer Batchdatei ausführen, müssen Sie den Agent immer dann erneut ausführen, wenn die bestehende Momentaufnahme ungültig wird.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  

1.  Erstellen Sie eine Momentaufnahme-, Transaktions- oder Mergeveröffentlichung. Weitere Informationen finden Sie unter [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Führen Sie [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) aus. Geben Sie **@publication** und die folgenden Parameter an:  
  
    -   **Der @job_login** : Gibt die Anmeldeinformationen für die Windows-Authentifizierung an, mit denen der Momentaufnahme-Agent auf dem Verteiler ausgeführt wird.  
  
    -   **Der @job_password** : Kennwort für die angegebenen Windows-Anmeldeinformationen.  
  
    -   (Optional) Den Wert **0** für **@publisher_security_mode** , wenn der Agent die SQL Server-Authentifizierung zum Herstellen der Verbindung mit dem Verleger verwendet. In diesem Fall müssen Sie auch die Anmeldeinformationen für die SQL Server-Authentifizierung für **@publisher_login** und **@publisher_password** .  
  
    -   (Optional) Einen Synchronisierungszeitplan für den Momentaufnahme-Agentauftrag. Weitere Informationen finden Sie unter [Angeben von Synchronisierungszeitplänen](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
3.  Fügen Sie der Veröffentlichung Artikel hinzu. Weitere Informationen finden Sie unter [Definieren eines Artikels](../../relational-databases/replication/publish/define-an-article.md).  
  
4.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_startpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md) unter Angabe des Werts **@publication** aus Schritt 1 aus.  
  
## <a name="apply-a-snapshot"></a>Anwenden einer Momentaufnahme  

### <a name="using-sql-server-management-studio"></a>Verwendung von SQL Server Management Studio
  
1.  Eine generierte Momentaufnahme wird angewendet, indem das Abonnement mit dem Verteilungs-Agent oder dem Merge-Agent synchronisiert wird:   
    -   Wenn der Agent fortlaufend ausgeführt wird (die Standardeinstellung bei der Transaktionsreplikation), wird die Momentaufnahme automatisch nach dem Generieren angewendet.   
    -   Wenn der Agent nach einem Zeitplan ausgeführt wird, wird die Momentaufnahme bei der nächsten geplanten Ausführung des Agents angewendet.    
    -   Wenn der Agent bedarfsgesteuert ausgeführt wird, wird der Snapshot bei der nächsten Ausführung des Agents angewendet.  
  
     Weitere Informationen zum Synchronisieren von Abonnements finden Sie unter [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md) und [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)verfügbar ist.  
  
###   <a name="use-transact-sql"></a>Verwendung von Transact-SQL  
 
1.  Erstellen Sie eine Momentaufnahme-, Transaktions- oder Mergeveröffentlichung. Weitere Informationen finden Sie unter [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Fügen Sie der Veröffentlichung Artikel hinzu. Weitere Informationen finden Sie unter [Definieren eines Artikels](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Starten Sie den [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md) von der Eingabeaufforderung oder in einer Batchdatei, indem Sie die Datei **snapshot.exe**ausführen. Geben Sie hierzu die folgenden Befehlszeilenargumente ein:  
  
    -   **-Publication**  
    -   **-Publisher**  
    -   **-Distributor**   
    -   **-PublisherDB**   
    -   **-ReplicationType**  
  
     Wenn Sie die SQL Server-Authentifizierung verwenden, müssen Sie auch die folgenden Argumente angeben:  
  
    -   **-DistributorLogin**    
    -   **-DistributorPassword**   
    -   **-DistributorSecurityMode** = **0**    
    -   **-PublisherLogin**    
    -   **-PublisherPassword**    
    -   **-PublisherSecurityMode** = **0**  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 In diesem Beispiel wird eine Transaktionsveröffentlichung erstellt und ein Momentaufnahme-Agentauftrag für die neue Veröffentlichung hinzugefügt (mithilfe von **sqlcmd** -Skriptvariablen). Im Beispiel wird der Auftrag auch gestartet.  
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_1.sql)]  
  
 In diesem Beispiel wird eine Mergeveröffentlichung erstellt und ein Momentaufnahme-Agentauftrag für die Veröffentlichung hinzugefügt (mithilfe von **sqlcmd** -Variablen). Im Beispiel wird der Auftrag auch gestartet.  
  
 [!code-sql[HowTo#sp_mergegenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_2.sql)]  
  
 Die folgenden Befehlszeilenargumente starten den Momentaufnahme-Agent, um die Momentaufnahme für eine Mergeveröffentlichung zu generieren.  
  
> [!NOTE]  
>  Zeilenumbrüche wurden hinzugefügt, um die Lesbarkeit zu verbessern. In einer Batchdatei müssen Befehle in einer einzelnen Zeile stehen.  
  
```  
  
REM -- Declare variables  
SET Publisher=%InstanceName%  
SET PublicationDB=AdventureWorks2012   
SET Publication=AdvWorksSalesOrdersMerge   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Momentaufnahmen werden nach dem Erstellen einer Veröffentlichung vom Momentaufnahme-Agent generiert. Sie können diese Momentaufnahmen mit Replikationsverwaltungsobjekten (RMO) und dem direkten Zugriff von verwaltetem Code auf Funktionen des Replikations-Agents programmgesteuert generieren. Welche Objekte Sie verwenden, hängt vom Typ der Replikation ab. Der Momentaufnahme-Agent kann synchron mit dem <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Objekt oder asynchron mit dem Agentauftrag gestartet werden. Nachdem die Anfangsmomentaufnahme generiert wurde, wird sie an den Abonnenten übertragen und auf diesen angewendet, sobald die erste Synchronisierung für das Abonnement durchgeführt wird. Sie müssen den Agent immer dann erneut ausführen, wenn die vorhandene Momentaufnahme keine gültigen und aktuellen Daten mehr enthält. Weitere Informationen finden Sie unter [Verwalten von Veröffentlichungen](../../relational-databases/replication/publish/maintain-publications.md).  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Sie Anmeldeinformationen speichern müssen, verwenden Sie die [Kryptografiedienste](https://go.microsoft.com/fwlink/?LinkId=34733) von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>So generieren Sie die Anfangsmomentaufnahme für eine Momentaufnahme- oder Transaktionsveröffentlichung durch Starten des Auftrags des Momentaufnahme-Agents (asynchron)  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPublication> -Klasse. Legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> -Eigenschaft und die <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> -Eigenschaft für die Veröffentlichung fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die restlichen Objekteigenschaften zu laden. Wenn diese Methode **false**zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  Wenn der Wert von <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> auf **false**lautet, rufen Sie <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> auf, um den Agentauftrag für die Momentaufnahme dieser Veröffentlichung zu erstellen.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> -Methode auf, um den Agentauftrag zu starten, der die Momentaufnahme für diese Veröffentlichung generiert.  
  
6.  (Optional) Wenn der Wert von <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> auf **true**lautet, steht die Momentaufnahme den Abonnenten zur Verfügung.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-snapshot-or-transactional-publication-by-running-the-snapshot-agent-synchronous"></a>So generieren Sie die Anfangsmomentaufnahme für eine Momentaufnahme- oder Transaktionsveröffentlichung durch Ausführen des Momentaufnahme-Agents (synchron)  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Klasse, und legen Sie die folgenden erforderlichen Eigenschaften fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> – Name des Verlegers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> – Name der Veröffentlichungsdatenbank  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> &ndash; Den Namen der Veröffentlichung  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> &ndash; Den Namen des Verteilers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> zur Verwendung der Windows-Authentifizierung, wenn eine Verbindung mit dem Verleger hergestellt wird, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> sowie Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> zur Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn eine Verbindung mit dem Verleger hergestellt wird. Die Windows-Authentifizierung wird empfohlen.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> zur Verwendung der Windows-Authentifizierung, wenn eine Verbindung mit dem Verteiler hergestellt wird, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> sowie Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> zur Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn eine Verbindung mit dem Verteiler hergestellt wird. Die Windows-Authentifizierung wird empfohlen.  
  
2.  Legen Sie den Wert <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> oder <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> -Methode auf.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-merge-publication-by-starting-the-snapshot-agent-job-asynchronous"></a>So generieren Sie die Anfangsmomentaufnahme für eine Mergeveröffentlichung durch Starten des Auftrags des Momentaufnahme-Agents (asynchron)  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication> -Klasse. Legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> -Eigenschaft und die <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> -Eigenschaft für die Veröffentlichung fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die restlichen Objekteigenschaften zu laden. Wenn diese Methode **false**zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  Wenn der Wert von <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> auf **false**lautet, rufen Sie <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> auf, um den Agentauftrag für die Momentaufnahme dieser Veröffentlichung zu erstellen.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> -Methode auf, um den Agentauftrag zu starten, der die Momentaufnahme für diese Veröffentlichung generiert.  
  
6.  (Optional) Wenn der Wert von <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> auf **true**lautet, steht die Momentaufnahme den Abonnenten zur Verfügung.  
  
#### <a name="to-generate-the-initial-snapshot-for-a-merge-publication-by-running-the-snapshot-agent-synchronous"></a>So generieren Sie die Anfangsmomentaufnahme für eine Mergeveröffentlichung durch Ausführen des Momentaufnahme-Agents (synchron)  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Klasse, und legen Sie die folgenden erforderlichen Eigenschaften fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> – Name des Verlegers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> – Name der Veröffentlichungsdatenbank  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> &ndash; Den Namen der Veröffentlichung  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> &ndash; Den Namen des Verteilers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> zur Verwendung der Windows-Authentifizierung, wenn eine Verbindung mit dem Verleger hergestellt wird, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> sowie Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> zur Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn eine Verbindung mit dem Verleger hergestellt wird. Die Windows-Authentifizierung wird empfohlen.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> Den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> zur Verwendung der Windows-Authentifizierung, wenn eine Verbindung mit dem Verteiler hergestellt wird, oder den Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> sowie Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> zur Verwendung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn eine Verbindung mit dem Verteiler hergestellt wird. Die Windows-Authentifizierung wird empfohlen.  
  
2.  Legen Sie den Wert <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> -Methode auf.  
  
###  <a name="PShellExample"></a> Beispiele (RMO)  
 In diesem Beispiel wird der Momentaufnahme-Agent synchron ausgeführt, um die Anfangsmomentaufnahme für eine Transaktionsveröffentlichung zu generieren.  
  
 [!code-cs[HowTo#rmo_GenerateSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 In diesem Beispiel wird der Agentauftrag asynchron ausgeführt, um die Anfangsmomentaufnahme für eine Transaktionsveröffentlichung zu generieren.  
  
 [!code-cs[HowTo#rmo_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Replication Management Objects Concepts](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Replication System Stored Procedures Concepts](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Verwenden von sqlcmd mit Skriptvariablen](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
