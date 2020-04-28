---
title: Definieren eines Artikels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], defining
- sp_addmergearticle
- adding articles
- sp_addarticle
- articles [SQL Server replication], adding
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 65512a212290db4cc9a470402e2ae75175c23cb5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73882316"
---
# <a name="define-an-article"></a>Definieren eines Artikels
  In diesem Thema wird beschrieben, wie ein Artikel in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) definiert wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So definieren Sie einen Artikel mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Artikelnamen dürfen keines der folgenden Zeichen enthalten: % , * , [ , ] , | , : , " , ? , ', \,/, \< , >. Wenn Objekte in der Datenbank eines dieser Zeichen enthalten und Sie die Objekte replizieren möchten, müssen Sie einen Artikelnamen angeben, der sich von dem Objektnamen unterscheidet.  
  
##  <a name="security"></a><a name="Security"></a> Sicherheit  
 Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Sie Anmeldeinformationen speichern müssen, verwenden Sie die [Kryptografiedienste](https://go.microsoft.com/fwlink/?LinkId=34733) von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Mit dem Assistenten für neue Veröffentlichung erstellen Sie Veröffentlichungen und definieren Artikel. Rufen Sie nach der Erstellung einer Veröffentlichung das Dialogfeld **Veröffentlichungseigenschaften – \<Veröffentlichung>** auf, um die Eigenschaften anzuzeigen und zu ändern. Weitere Informationen zum Erstellen von Veröffentlichungen aus einer Oracle-Datenbank finden Sie unter [Erstellen einer Veröffentlichung aus einer Oracle-Datenbank](create-a-publication-from-an-oracle-database.md).  
  
#### <a name="to-create-a-publication-and-define-articles"></a>So erstellen Sie eine Veröffentlichung und definieren Artikel  
  
1.  Stellen Sie in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] eine Verbindung mit dem Herausgeber her, und erweitern Sie den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und klicken Sie dann mit der rechten Maustaste auf den Ordner **Lokale Veröffentlichungen** .  
  
3.  Klicken Sie auf **Neue Veröffentlichung**.  
  
4.  Folgen Sie den Anweisungen auf den Seiten des Assistenten für neue Veröffentlichung, um folgende Vorgänge auszuführen:  
  
    -   Angeben eines Verteilers, falls die Verteilung auf dem Server nicht konfiguriert wurde. Weitere Informationen zum Konfigurieren der Verteilung finden Sie unter [Konfigurieren der Veröffentlichung und der Verteilung](../configure-publishing-and-distribution.md).  
  
         Wenn Sie auf der Seite **Verteiler** angeben, dass der Verleger als eigener Verteiler fungiert (lokaler Verteiler) und der Server nicht als Verteiler konfiguriert ist, erfolgt die Konfiguration des Servers durch den Assistenten für neue Veröffentlichung. Auf der Seite **Momentaufnahmeordner** geben Sie einen Standardmomentaufnahmeordner für den Verteiler an. Der Momentaufnahmeordner ist lediglich ein von Ihnen freigegebenes Verzeichnis. Agents, die aus diesem Ordner lesen bzw. in den Ordner schreiben, benötigen ausreichende Zugriffsberechtigungen. Weitere Informationen zum Sichern des Ordners finden Sie unter [Sichern des Momentaufnahmeordners](../security/secure-the-snapshot-folder.md).  
  
         Wenn Sie angeben, dass ein anderer Server als Verteiler fungieren soll, müssen Sie auf der Seite **Administratorkennwort** ein Kennwort für Verbindungen eingeben, die zwischen dem Verleger und dem Verteiler hergestellt werden. Dieses Kennwort muss mit dem Kennwort übereinstimmen, dass bei der Aktivierung des Verlegers auf dem Remoteverteiler angegeben wurde.  
  
         Weitere Informationen finden Sie unter [Configure Distribution](../configure-distribution.md).  
  
    -   Auswählen einer Veröffentlichungsdatenbank.  
  
    -   Auswählen eines Veröffentlichungstyps. Weitere Informationen finden Sie unter [Replikationstypen](../types-of-replication.md).  
  
    -   Angeben von Daten und Datenbankobjekten, die veröffentlicht werden sollen. Optional können Sie Spalten aus Tabellenartikeln filtern und Artikeleigenschaften angeben.  
  
    -   Optionales Filtern von Zeilen aus Tabellenartikeln. Weitere Informationen finden Sie unter [Filtern von veröffentlichten Daten](filter-published-data.md).  
  
    -   Festlegen des Zeitplans für den Momentaufnahme-Agent.  
  
    -   Angeben der Anmeldeinformationen, unter denen die folgenden Replikations-Agents ausgeführt werden und Verbindungen herstellen:  
  
         \- Momentaufnahme-Agent (für alle Veröffentlichungen)  
  
         \- Protokolllese-Agent (für alle Transaktionsveröffentlichungen)  
  
         \- Warteschlangenlese-Agent für Transaktionsveröffentlichungen, in denen Updates von Abonnements zulässig sind  
  
         Weitere Informationen finden Sie unter [Replication Agent Security Model](../security/replication-agent-security-model.md) und [Replication Security Best Practices](../security/replication-security-best-practices.md).  
  
    -   Optionale Erstellung eines Skripts für die Veröffentlichung. Weitere Informationen finden Sie unter [Scripting Replication](../scripting-replication.md).  
  
    -   Angeben eines Namens für die Veröffentlichung.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Nachdem eine Veröffentlichung erstellt wurde, können Artikel programmgesteuert mithilfe gespeicherter Replikationsprozeduren erstellt werden. Die zur Erstellung eines Artikels verwendeten gespeicherten Prozeduren hängen vom Typ der Veröffentlichung ab, für die der Artikel definiert wird. Weitere Informationen finden Sie unter [Create a Publication](create-a-publication.md).  
  
#### <a name="to-define-an-article-for-a-snapshot-or-transactional-publication"></a>So definieren Sie einen Artikel für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört ** \@**, für die Veröffentlichung, den Namen des ** \@** Artikels für den Artikel, das Datenbankobjekt, das für ** \@source_object**veröffentlicht wird, und alle anderen optionalen Parameter an. Verwenden ** \@Sie source_owner** , um den Schema Besitz des Objekts anzugeben, wenn dies nicht **dbo**ist. Wenn der Artikel kein Protokoll basierter Tabellen Artikel ist, geben Sie den Artikeltyp für den ** \@Typ**an. Weitere Informationen finden Sie unter [Angeben von Artikeltypen &#40;Replikations Programmierung mit Transact-SQL-&#41;](specify-article-types-replication-transact-sql-programming.md).  
  
2.  Um Zeilen eines Tabellen- oder Sichtartikels horizontal zu filtern, verwenden Sie [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) zur Definition der Filterklausel. Weitere Informationen finden Sie unter [Definieren oder Ändern eines statischen Zeilenfilters](define-and-modify-a-static-row-filter.md).  
  
3.  Um Spalten eines Tabellen- oder Sichtartikels vertikal zu filtern, verwenden Sie [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql). Weitere Informationen finden Sie unter [Definieren und Ändern eines Spaltenfilters](define-and-modify-a-column-filter.md).  
  
4.  Führen Sie [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) aus, wenn der Artikel gefiltert wird.  
  
5.  Wenn die Veröffentlichung über vorhandene Abonnements verfügt und [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) den Wert **0** in der Spalte **immediate_sync** zurückgibt, müssen Sie [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) aufrufen, um den Artikel zu jedem vorhandenen Abonnement hinzuzufügen.  
  
6.  Wenn die Veröffentlichung über vorhandene Pullabonnements verfügt, führen Sie [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) auf dem Verleger aus, um für vorhandene Pullabonnements eine neue Momentaufnahme zu erstellen, die nur den neuen Artikel enthält.  
  
    > [!NOTE]  
    >  Für Abonnements, die nicht mithilfe einer Momentaufnahme initialisiert wurden, müssen Sie [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) nicht ausführen, da diese Prozedur von [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)ausgeführt wird.  
  
#### <a name="to-define-an-article-for-a-merge-publication"></a>So definieren Sie einen Artikel für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung für ** \@die Veröffentlichung**, einen Namen für den Artikelnamen ** \@** für den Artikel und das Objekt an, das für ** \@source_object**veröffentlicht wird. Um Tabellenzeilen horizontal zu filtern, geben Sie einen Wert für ** \@subset_filterclause**an. Weitere Informationen finden Sie unter [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) und [Definieren oder Ändern eines statischen Zeilenfilters](define-and-modify-a-static-row-filter.md). Wenn der Artikel kein Tabellen Artikel ist, geben Sie den Artikeltyp für den ** \@Typ**an. Weitere Informationen finden Sie unter [Angeben von Artikeltypen &#40;Replikationsprogrammierung mit Transact-SQL&#41;](specify-article-types-replication-transact-sql-programming.md).  
  
2.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) aus, um einen Joinfilter zwischen zwei Artikeln zu definieren. Weitere Informationen finden Sie unter [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](define-and-modify-a-join-filter-between-merge-articles.md).  
  
3.  (Optional) führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) aus, um Tabellenspalten zu filtern. Weitere Informationen finden Sie unter [Definieren und Ändern eines Spaltenfilters](define-and-modify-a-column-filter.md).  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 In diesem Beispiel wird ein auf der Tabelle `Product` basierender Artikel für eine Transaktionsveröffentlichung definiert, wobei der Artikel sowohl horizontal als auch vertikal gefiltert wird.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 In diesem Beispiel wird ein Artikel für eine Mergeveröffentlichung definiert, bei der der `SalesOrderHeader` -Artikel basierend auf **SalesPersonID**statisch gefiltert wird, und der `SalesOrderDetail` -Artikel mithilfe eines auf `SalesOrderHeader`basierenden Verknüpfungsfilters gefiltert wird.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Sie können Artikel mithilfe von Replikationsverwaltungsobjekten (RMO) programmgesteuert definieren. Die zur Definition eines Artikels verwendeten RMO-Klassen hängen vom Typ der Veröffentlichung ab, für die der Artikel definiert wird.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Beispiele (RMO)  
 Im folgenden Beispiel wird ein Artikel mit Zeilen- und Spaltenfiltern einer Transaktionsveröffentlichung hinzugefügt.  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 Im folgenden Beispiel werden drei Artikel einer Mergeveröffentlichung hinzugefügt. Die Artikel haben Spaltenfilter und zwei Joinfilter, die verwendet werden, um einen parametrisierten Zeilenfilter an andere Artikel weiterzugeben.  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](create-a-publication.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Filtern von veröffentlichten Daten](filter-published-data.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](publish-data-and-database-objects.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
