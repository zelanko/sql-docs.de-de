---
title: Anzeigen und Ändern von Veröffentlichungseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- publications [SQL Server replication], properties
- articles [SQL Server replication], properties
- modifying replication properties, publications
- publications [SQL Server replication], modifying
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 439a2009e6cb5e470ef09d3c766c4349d54ecdb8
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52792291"
---
# <a name="view-and-modify-publication-properties"></a>Anzeigen und Ändern von Veröffentlichungseigenschaften
  In diesem Thema wird beschrieben, wie die Veröffentlichungseigenschaften in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) angezeigt und geändert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
-   **So zeigen Sie Veröffentlichungseigenschaften an und ändern sie mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Einige Eigenschaften können nicht geändert werden, nachdem eine Veröffentlichung erstellt wurde. Andere Eigenschaften können nicht geändert werden, wenn Abonnements für die Veröffentlichung vorhanden sind. Eigenschaften, die nicht geändert werden können, werden als schreibgeschützt angezeigt.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Nachdem eine Veröffentlichung erstellt wurde, ist für bestimmte Eigenschaftsänderungen eine neue Momentaufnahme erforderlich. Wenn für eine Veröffentlichung Abonnements erstellt wurden, müssen bei bestimmten Änderungen alle Abonnements erneut initialisiert werden. Weitere Informationen finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md) und [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Sie können die Eigenschaften von Veröffentlichungen im Dialogfeld **Veröffentlichungseigenschaften - \<<Veröffentlichung>** anzeigen und ändern. Dieses Dialogfeld ist in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] und im Replikationsmonitor verfügbar. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../monitor/start-the-replication-monitor.md).  
  
 Das Dialogfeld **Veröffentlichungseigenschaften - \<<Veröffentlichung>** enthält folgende Seiten:  
  
-   Die Seite **Allgemein** enthält den Namen und die Beschreibung der Veröffentlichung, den Datenbanknamen, den Typ der Veröffentlichung und die Einstellungen für den Abonnementablauf.  
  
-   Die Seite **Artikel** entspricht der Seite **Artikel** des Assistenten für neue Veröffentlichung. Verwenden Sie diese Seite, um Artikel hinzuzufügen und zu löschen und um Eigenschaften sowie die Spaltenfilterung für Artikel zu ändern.  
  
-   Die Seite **Zeilen filtern** entspricht der Seite **Tabellenzeilen filtern** des Assistenten für neue Veröffentlichung. Mithilfe dieser Seite können Sie statische Zeilenfilter für sämtliche Veröffentlichungstypen hinzufügen, bearbeiten und löschen sowie parametrisierte Zeilenfilter und Joinfilter für Mergeveröffentlichungen hinzufügen, bearbeiten und löschen.  
  
-   Auf der Seite **Momentaufnahme** können Sie das Format und den Speicherort der Momentaufnahme angeben und zudem angeben, ob die Momentaufnahme komprimiert werden soll und ob Skripts ausgeführt werden sollen, bevor und nachdem die Momentaufnahme angewendet wird.  
  
-   Die Seite **FTP-Momentaufnahme** (bei Momentaufnahme- und Transaktionsveröffentlichungen sowie Mergeveröffentlichungen für Verleger, auf denen frühere Versionen als SQL Server 2005 ausgeführt werden) bietet die Möglichkeit anzugeben, ob Abonnenten Momentaufnahmedateien über FTP (File Transfer Protocol) herunterladen können.  
  
-   Auf der Seite **FTP-Momentaufnahme und Internet** (bei Mergeveröffentlichungen von Verlegern, auf denen SQL Server 2005 oder höher ausgeführt wird) können Sie angeben, ob Abonnenten Momentaufnahmedateien per FTP herunterladen können und ob Abonnenten Abonnements über HTTPS synchronisieren können.  
  
-   Auf der Seite **Abonnementoptionen** können Sie eine Reihe von Optionen festlegen, die auf alle Abonnements angewendet werden. Die Optionen hängen vom Veröffentlichungstyp ab.  
  
-   Auf der Seite **Veröffentlichungszugriffsliste** können Sie angeben, welche Anmeldungen und Gruppen auf eine Veröffentlichung zugreifen können.  
  
-   Über die Seite **Agentsicherheit** können Sie auf die Einstellungen für die Konten zugreifen, unter denen folgende Agents ausgeführt werden. Sie können außerdem Verbindungen mit den Computern in einer Replikationstopologie herstellen: Momentaufnahme-Agent für alle Veröffentlichungen, Protokolllese-Agent für alle Transaktionsveröffentlichungen und Warteschlangenlese-Agent für Transaktionsveröffentlichungen, die Abonnements mit verzögertem Update über eine Warteschlange zulassen.  
  
-   Auf der Seite **Datenpartitionen** (für Mergeveröffentlichungen von Verlegern, auf denen SQL Server 2005 oder höher ausgeführt wird) können Sie angeben, ob Abonnenten von Veröffentlichungen mit parametrisierten Filtern eine Momentaufnahme anfordern können, wenn diese nicht verfügbar ist. Sie haben zudem die Möglichkeit, Momentaufnahmen für eine oder mehrere Partitionen entweder einmalig oder wiederkehrend gemäß einem Zeitplan zu generieren.  
  
#### <a name="to-view-and-modify-publication-properties-in-management-studio"></a>So zeigen Sie Veröffentlichungseigenschaften in Management Studio an und ändern sie  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf eine Veröffentlichung, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
#### <a name="to-view-and-modify-publication-properties-in-replication-monitor"></a>So zeigen Sie Veröffentlichungseigenschaften im Replikationsmonitor an und ändern sie  
  
1.  Erweitern Sie im linken Bereich des Replikationsmonitors eine Verlegergruppe, und erweitern Sie dann einen Verleger.  
  
2.  Klicken Sie mit der rechten Maustaste auf eine Veröffentlichung, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Veröffentlichungen können mithilfe gespeicherter Replikationsprozeduren programmgesteuert geändert und ihre Eigenschaften zurückgegeben werden. Welche gespeicherten Prozeduren Sie verwenden, hängt vom Typ der Veröffentlichung ab.  
  
#### <a name="to-view-the-properties-of-a-snapshot-or-transactional-publication"></a>So zeigen Sie die Eigenschaften einer Momentaufnahme oder einer Transaktionsveröffentlichung an  
  
1.  Führen Sie [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)aus, und geben Sie dabei den Namen der Veröffentlichung für den **@publication** -Parameter an. Wenn Sie diesen Parameter nicht angeben, werden Informationen über alle Veröffentlichungen beim Verleger zurückgegeben.  
  
#### <a name="to-change-the-properties-of-a-snapshot-or-transactional-publication"></a>So ändern Sie die Eigenschaften einer Momentaufnahme oder einer Transaktionsveröffentlichung  
  
1.  Führen Sie [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus, und geben Sie dabei die zu ändernde Veröffentlichungseigenschaft im **@property** -Parameter und den neuen Wert dieser Eigenschaft im **@value** -Parameter an.  
  
    > [!NOTE]  
    >  Wenn die Änderung das Generieren einer neuen Momentaufnahme erfordert, müssen Sie zudem den Wert **1** für **@force_invalidate_snapshot**angeben, und wenn die Änderung das erneute Initialisieren der Abonnenten erfordert, müssen Sie den Wert **1** für **@force_reinit_subscription**. Weitere Informationen zu den Eigenschaften, die bei Änderung eine neue Momentaufnahme oder eine erneute Initialisierung erfordern, finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md).  
  
#### <a name="to-view-the-properties-of-a-merge-publication"></a>So zeigen Sie die Eigenschaften einer Mergeveröffentlichung an  
  
1.  Führen Sie [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)aus, und geben Sie dabei den Namen der Veröffentlichung für den **@publication** -Parameter an. Wenn Sie diesen Parameter nicht angeben, werden Informationen über alle Veröffentlichungen beim Verleger zurückgegeben.  
  
#### <a name="to-change-the-properties-of-a-merge-publication"></a>So ändern Sie die Eigenschaften einer Mergeveröffentlichung  
  
1.  Führen Sie [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus, und geben Sie dabei die zu ändernde Veröffentlichungseigenschaft im **@property** -Parameter und den neuen Wert dieser Eigenschaft im **@value** -Parameter an.  
  
    > [!NOTE]  
    >  Wenn die Änderung das Generieren einer neuen Momentaufnahme erfordert, müssen Sie auch einen Wert **1** für **@force_invalidate_snapshot** angeben, und wenn die Änderung erfordert, dass Abonnenten erneut initialisiert werden, geben Sie den Wert **1** für **@force_reinit_subscription** an. Weitere Informationen zu den Eigenschaften, die bei Änderung eine neue Momentaufnahme oder eine erneute Initialisierung erfordern, finden Sie unter [Ändern der Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md).  
  
#### <a name="to-view-the-properties-of-a-snapshot"></a>So zeigen Sie die Eigenschaften einer Momentaufnahme an  
  
1.  Führen Sie [sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql)aus, und geben Sie dabei den Namen der Veröffentlichung für den **@publication** -Parameter an.  
  
#### <a name="to-change-the-properties-of-a-snapshot"></a>So ändern Sie die Eigenschaften einer Momentaufnahme  
  
1.  Führen Sie [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)aus, und geben Sie dabei eine oder mehrere der neuen Momentaufnahmeeigenschaften für die entsprechenden Momentaufnahmeparameter an.  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 In diesem Beispiel für Transaktionsreplikation werden die Eigenschaften der Veröffentlichung zurückgegeben.  
  
 [!code-sql[HowTo#sp_helppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_helppublication)]  
  
 In diesem Beispiel für Transaktionsreplikation wird die Schemareplikation für die Veröffentlichung deaktiviert.  
  
 [!code-sql[HowTo#sp_changepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_changepublication)]  
  
 In diesem Beispiel für Mergereplikation werden die Eigenschaften der Veröffentlichung zurückgegeben.  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_helpmergepublication)]  
  
 In diesem Beispiel für Mergereplikation wird die Schemareplikation für die Veröffentlichung deaktiviert.  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_changemergepublication)]  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Sie können Veröffentlichungen ändern und mithilfe von Replikationsverwaltungsobjekten (RMO) programmgesteuert auf ihre Eigenschaften zugreifen. Welche RMO-Klassen zum Anzeigen oder Ändern von Veröffentlichungseigenschaften verwendet werden, hängt vom Typ der Veröffentlichung ab.  
  
#### <a name="to-view-or-modify-properties-of-a-snapshot-or-transactional-publication"></a>So zeigen Sie die Eigenschaften einer Momentaufnahme- oder einer Transaktionsveröffentlichung an oder ändern diese  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPublication> -Klasse, legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> -Eigenschaft und die <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> -Eigenschaft der Veröffentlichung fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  (Optional) Um Eigenschaften zu ändern, legen Sie einen neuen Wert für eine oder mehrere festlegbaren Eigenschaften fest. Verwenden Sie den logischen AND-Operator (`&` in Microsoft Visual C# and `And` in Microsoft Visual Basic), um zu ermitteln, ob ein gegebener <xref:Microsoft.SqlServer.Replication.PublicationAttributes>-Wert für die <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>-Eigenschaft festgelegt wurde. Verwenden Sie den inklusiven logischen OR-Operator (`|` in Visual C# and `Or` in Visual Basic) und den exklusiven logischen OR-Operator (`^` in Visual C# und `Xor` in Visual Basic), um die <xref:Microsoft.SqlServer.Replication.PublicationAttributes>-Werte für die <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>-Eigenschaft zu ändern.  
  
5.  (Optional) Wenn Sie den Wert `true` für <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> angegeben haben, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>-Methode auf, um die Änderungen auf dem Server einzutragen. Wenn Sie den Wert `false` für <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (die Standardeinstellung) angegeben haben, werden die Änderungen sofort an den Server gesendet.  
  
#### <a name="to-view-or-modify-properties-of-a-merge-publication"></a>So zeigen Sie die Eigenschaften einer Mergeveröffentlichung an oder ändern diese  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication> -Klasse, legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> -Eigenschaft und die <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> -Eigenschaft der Veröffentlichung fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  (Optional) Um Eigenschaften zu ändern, legen Sie einen neuen Wert für eine oder mehrere festlegbaren Eigenschaften fest. Verwenden Sie den logischen AND-Operator (`&` in Visual C#- und `And` in Visual Basic) zu entscheiden, ob eine angegebene <xref:Microsoft.SqlServer.Replication.PublicationAttributes> Wert wird festgelegt, für die <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> Eigenschaft. Verwenden Sie den inklusiven logischen OR-Operator (`|` in Visual C# and `Or` in Visual Basic) und den exklusiven logischen OR-Operator (`^` in Visual C# und `Xor` in Visual Basic), um die <xref:Microsoft.SqlServer.Replication.PublicationAttributes>-Werte für die <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>-Eigenschaft zu ändern.  
  
5.  (Optional) Wenn Sie den Wert `true` für <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> angegeben haben, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>-Methode auf, um die Änderungen auf dem Server einzutragen. Wenn Sie den Wert `false` für <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (die Standardeinstellung) angegeben haben, werden die Änderungen sofort an den Server gesendet.  
  
###  <a name="PShellExample"></a> Beispiele (RMO)  
 In diesem Beispiel werden Veröffentlichungsattribute einer Transaktionsveröffentlichung festgelegt. Die Änderungen werden zwischengespeichert, bis sie explizit zum Server gesendet werden.  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 In diesem Beispiel wird die DDL-Replikation für eine Mergeveröffentlichung deaktiviert.  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von Daten und Datenbankobjekten](publish-data-and-database-objects.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md)   
 [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](make-schema-changes-on-publication-databases.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Hinzufügen von Artikeln zu einer Veröffentlichung und Löschen von Artikeln aus einer Veröffentlichung &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md)   
 [Anzeigen von Informationen und Ausführen von Aufgaben für eine Veröffentlichung &#40;Replikationsmonitor&#41;](../monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Anzeigen und Ändern von Artikeleigenschaften](view-and-modify-article-properties.md)  
  
  
