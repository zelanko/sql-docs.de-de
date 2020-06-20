---
title: Anzeigen und Ändern der Verteiler- und Verlegereigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- Distributors [SQL Server replication], modifying
- modifying replication properties, Distributors
- Distributors [SQL Server replication], properties
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 571f6f3a0d44f0fc87c67885249fca441776946d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055571"
---
# <a name="view-and-modify-distributor-and-publisher-properties"></a>Anzeigen und Ändern der Verteiler- und Verlegereigenschaften
  In diesem Thema wird beschrieben, wie die Distributor-Eigenschaft und die Publisher-Eigenschaft in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) angezeigt und geändert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So können Sie Verteiler- und Verlegereigenschaften anzeigen und ändern mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Bei Verlegern, auf denen eine niedrigere Versionen als [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ausgeführt wird, kann ein Benutzer der festen Serverrolle **sysadmin** auf der Seite **Abonnenten** Abonnenten registrieren. Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]müssen Abonnenten für die Replikation nicht mehr explizit registriert werden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-and-modify-distributor-properties"></a>So zeigen Sie die Verteilereigenschaften an oder ändern diese  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Replikation** , und klicken Sie dann auf **Verteilereigenschaften**.  
  
3.  Anzeigen und Ändern der Eigenschaften im Dialogfeld **Verteiler \<Distributor> Eigenschaften-** .  
  
    -   Um die Eigenschaften einer Verteilungsdatenbank anzuzeigen und zu ändern, klicken Sie auf die Schaltfläche Eigenschaften (**...**) für die Datenbank auf der Seite **Allgemein** des Dialogfelds.  
  
    -   Um die mit dem Verteiler verbundenen Verlegereigenschaften anzuzeigen und zu ändern, klicken Sie auf der Seite**Verleger**des Dialogfelds auf die Schaltfläche Eigenschaften ( **...** ) des Verlegers.  
  
    -   Klicken Sie auf der Seite **Allgemein** des Dialogfelds auf **Profilstandards** , um auf die Profile der Replikations-Agents zuzugreifen. Weitere Informationen finden Sie unter [Replication Agent Profiles](agents/replication-agent-profiles.md).  
  
    -   Um das Kennwort des zum Ausführen von administrativen gespeicherten Prozeduren auf dem Verleger und Aktualisieren von Informationen auf dem Verteiler verwendeten Kontos zu ändern, geben Sie auf der Seite **Verleger** des Dialogfelds in den Feldern **Kennwort** und **Kennwort bestätigen** ein neues Kennwort ein. Weitere Informationen finden Sie unter [Schützen des Verteilers](security/secure-the-distributor.md).  
  
4.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
#### <a name="to-view-and-modify-publisher-properties"></a>So zeigen Sie die Verlegereigenschaften an oder ändern diese  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Replikation** , und klicken Sie dann auf **Verlegereigenschaften**.  
  
3.  Anzeigen und Ändern der Eigenschaften im Dialogfeld **Verleger \< Publisher > Eigenschaften-** .  
  
    -   Ein Benutzer der festen Serverrolle **sysadmin** kann Datenbanken für die Replikation auf der Seite **Veröffentlichungsdatenbanken** aktivieren. Durch das Aktivieren wird eine Datenbank nicht veröffentlicht, sondern Benutzer der festen Datenbankrolle **db_owner** für diese Datenbank können dann eine oder mehrere Veröffentlichungen in der Datenbank erstellen.  
  
4.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Die Verleger- und Verteilereigenschaften können mit gespeicherten Replikationsprozeduren programmgesteuert angezeigt werden.  
  
#### <a name="to-view-distributor-and-distribution-database-properties"></a>So zeigen Sie Verleger- und Verteilerdatenbankeigenschaften an  
  
1.  Führen Sie [sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) aus, um Informationen über Verteiler, Verteilungsdatenbank und Arbeitsverzeichnis zurückzugeben.  
  
2.  Führen Sie [sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) aus, um die Eigenschaften einer angegebenen Verteilungsdatenbank zurückzugeben.  
  
#### <a name="to-change-distributor-and-distribution-database-properties"></a>So ändern Sie Verleger- und Verteilerdatenbankeigenschaften  
  
1.  Führen Sie auf dem Verteiler [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) aus, um Verteilereigenschaften zu ändern.  
  
2.  Führen Sie auf dem Verteiler [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) aus, um Eigenschaften der Verteilerdatenbank zu ändern.  
  
3.  Führen Sie auf dem Verteiler [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) aus, um das Verteilerkennwort zu ändern.  
  
    > [!IMPORTANT]  
    >  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Sie Anmeldeinformationen in einer Skriptdatei speichern müssen, sollten Sie die Datei schützen, um nicht autorisierten Zugriff zu verhindern.  
  
4.  Führen Sie auf dem Verteiler [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) aus, um mit dem Verteiler die Eigenschaften eines Verlegers zu ändern.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 Das folgende Beispielskript [!INCLUDE[tsql](../../includes/tsql-md.md)] gibt Informationen über den Verteiler und die Verteilerdatenbank zurück.  
  
 [!code-sql[HowTo#sp_helpdistributor](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributor)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributiondb)]  
  
 Im folgenden Beispiel werden die Beibehaltungsdauer für den Verteiler, das Kennwort für den Verbindungsaufbau zum Verteiler und das Intervall geändert, in dem der Verteiler den Status verschiedener Replikations-Agents überprüft (auch Taktintervall genannt).  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Sie Anmeldeinformationen in einer Skriptdatei speichern müssen, sollten Sie die Datei schützen, um nicht autorisierten Zugriff zu verhindern.  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_property)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributiondb)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_password)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
  
#### <a name="to-view-and-modify-distributor-properties"></a>So zeigen Sie die Verteilereigenschaften an oder ändern diese  
  
1.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.ReplicationServer>-Klasse. Übergeben Sie das <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt aus Schritt 1.  
  
3.  (Optional) überprüfen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> -Eigenschaft, um sich davon zu überzeugen, dass der aktuell verbundene Server ein Verteiler ist.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> -Methode auf, um die Eigenschaften vom Server abzurufen.  
  
5.  (Optional) Zum Ändern der Eigenschaften legen Sie einen neuen Wert für eine oder mehrere der Verteilereigenschaften fest, die im <xref:Microsoft.SqlServer.Replication.ReplicationServer> -Objekt festgelegt werden können.  
  
6.  (Optional) Wenn die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Replication.ReplicationServer>-Objekts auf `true` festgelegt ist, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>-Methode auf, um Änderungen auf dem Server einzutragen.  
  
#### <a name="to-view-and-modify-distribution-database-properties"></a>So zeigen Sie Verteilerdatenbankeigenschaften an oder ändern Sie diese Eigenschaften  
  
1.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.DistributionDatabase>-Klasse. Geben Sie die Namenseigenschaft an, und übergeben Sie das <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt aus Schritt 1.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften vom Server abzurufen. Wenn diese Methode `false` zurückgibt, ist die Datenbank mit dem angegebenen Namen nicht auf dem Server vorhanden.  
  
4.  (Optional) Um Eigenschaften zu ändern, legen Sie einen neuen Wert für eine der definierbaren <xref:Microsoft.SqlServer.Replication.DistributionDatabase> -Eigenschaften fest.  
  
5.  (Optional) Wenn die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Replication.DistributionDatabase>-Objekts auf `true` festgelegt ist, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>-Methode auf, um Änderungen auf dem Server einzutragen.  
  
#### <a name="to-view-and-modify-publisher-properties"></a>So zeigen Sie die Verlegereigenschaften an oder ändern diese  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.DistributionPublisher>-Klasse. Geben Sie die <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> -Eigenschaft an, und übergeben Sie das <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt aus Schritt 1.  
  
3.  (Optional) Um Eigenschaften zu ändern, legen Sie einen neuen Wert für eine der definierbaren <xref:Microsoft.SqlServer.Replication.DistributionPublisher> -Eigenschaften fest.  
  
4.  (Optional) Wenn die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Replication.DistributionPublisher>-Objekts auf `true` festgelegt ist, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>-Methode auf, um Änderungen auf dem Server einzutragen.  
  
#### <a name="to-change-the-password-for-the-administrative-connection-from-the-publisher-to-the-distributor"></a>So ändern Sie das Kennwort für die Verwaltungsverbindung zwischen dem Verleger und dem Verteiler  
  
1.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.ReplicationServer>-Klasse.  
  
3.  Legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A>-Methode auf. Übergeben Sie den neuen Kennwortwert für den *password* -Parameter.  
  
    > [!IMPORTANT]  
    >  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Sie Anmelde Informationen speichern müssen, verwenden Sie die [Kryptografiedienste](https://go.microsoft.com/fwlink/?LinkId=34733) , die vom Windows-.NET Framework bereitgestellt werden [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
6.  (Optional) Führen Sie die folgenden Schritte aus, um das Kennwort bei jedem Remoteverleger zu ändern, der diesen Verteiler verwendet:  
  
    1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
    2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.ReplicationServer>-Klasse.  
  
    3.  Legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 6a erstellte Verbindung fest.  
  
    4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen.  
  
    5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A>-Methode auf. Übergeben Sie den neuen Kennwortwert aus Schritt 5 für den *password* -Parameter.  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a>Beispiel (RMO)  
 In diesem Beispiel wird gezeigt, wie Verteilungs- und Verteilungsdatenbankeigenschaften geändert werden.  
  
> [!IMPORTANT]  
>  Um die Speicherung von Anmeldeinformationen im Code vermeiden, wird das neue Verteilerkennwort zur Laufzeit angegeben.  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationsverwaltungsobjekte Konzepte](concepts/replication-management-objects-concepts.md)   
 [Veröffentlichung und Verteilung deaktivieren](disable-publishing-and-distribution.md)   
 [Verteilung konfigurieren](configure-distribution.md)   
 [Replikationsverwaltungsobjekte Konzepte](concepts/replication-management-objects-concepts.md)   
 [Informations Skript für Verteiler und Verleger](administration/distributor-and-publisher-information-script.md)   
 [Konzepte für gespeicherte System Prozeduren von](concepts/replication-system-stored-procedures-concepts.md)   
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](monitor/view-information-and-perform-tasks-replication-monitor.md)  
  
  
