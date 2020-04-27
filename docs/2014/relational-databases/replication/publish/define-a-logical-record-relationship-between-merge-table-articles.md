---
title: Definieren einer logischen Datensatzbeziehung zwischen Mergetabellenartikeln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c1c5be804f60fa57b677a418c19d8aadee23f22
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62691662"
---
# <a name="define-a-logical-record-relationship-between-merge-table-articles"></a>Definieren einer logische Datensatzbeziehung zwischen Mergetabellenartikeln
  In diesem Thema wird beschrieben, wie eine logische Datensatzbeziehung zwischen Mergetabellenartikeln in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) definiert wird.  
  
 Mergereplikation ermöglicht Ihnen, eine Beziehung zwischen verknüpften Zeilen in verschiedenen Tabellen zu definieren. Diese Zeilen können dann während der Synchronisierung als Transaktionseinheit verarbeitet werden. Eine logische Datensatzbeziehung zwischen zwei Artikeln kann unabhängig davon definiert werden, ob sie über eine Joinfilterbeziehung verfügen oder nicht. Weitere Informationen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
-   **So definieren Sie eine logische Datensatzbeziehung zwischen Mergetabellenartikeln mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie einen logischen Datensatz hinzufügen, ändern oder löschen, nachdem Abonnements für die Veröffentlichung initialisiert wurden, müssen Sie eine neue Momentaufnahme generieren und alle Abonnements nach vorgenommener Änderung erneut initialisieren. Weitere Informationen zum Ändern von Eigenschaften finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Zum Definieren logischer Datensätze steht Ihnen das Dialogfeld **Join hinzufügen** zur Verfügung, das über den Assistenten für neue Veröffentlichung und das Dialogfeld **Veröffentlichungseigenschaften – \<Veröffentlichung>** verfügbar ist. Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
 Logische Datensätze können nur dann im Dialogfeld **Join hinzufügen** definiert werden, wenn sie auf einen Joinfilter in einer Mergeveröffentlichung angewendet werden und die Veröffentlichung die Anforderungen für die Verwendung vorausberechneter Partitionen erfüllt. Wenn Sie logische Datensätze definieren möchten, die nicht auf Joinfilter angewendet werden, und die Konflikterkennung und -lösung auf der Ebene des logischen Datensatzes festlegen möchten, müssen Sie gespeicherte Prozeduren verwenden.  
  
#### <a name="to-define-a-logical-record-relationship"></a>So definieren Sie eine logische Datensatzbeziehung  
  
1.  Wählen Sie auf der Seite **Tabellenzeilen filtern** des Assistenten für neue Veröffentlichung oder auf der Seite **Zeilen filtern** des Dialogfelds **Veröffentlichungseigenschaften – \<Veröffentlichung>** im Bereich **Gefilterte Tabellen** einen Zeilenfilter aus.  
  
     Logische Datensatzbeziehungen sind mit einem Joinfilter verknüpft, der wiederum einen Zeilenfilter erweitert. Sie müssen daher zuerst einen Zeilenfilter definieren, bevor Sie den Filter mit einem Join erweitern und eine logische Datensatzbeziehung anwenden können. Nach dem Definieren eines Joinfilters können Sie diesen Joinfilter wiederum um einen anderen Joinfilter erweitern. Weitere Informationen zum Definieren von Joinfiltern finden Sie unter [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](define-and-modify-a-join-filter-between-merge-articles.md).  
  
2.  Klicken Sie auf **Hinzufügen**und anschließend auf **Join hinzufügen, um den ausgewählten Filter zu erweitern**.  
  
3.  Definieren Sie im Dialogfeld **Join hinzufügen** einen Joinfilter, und aktivieren Sie dann das Kontrollkästchen **Logischer Datensatz**.  
  
4.  Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften.-.\<Veröffentlichung>** befinden, klicken Sie auf **OK**, um zu speichern und das Dialogfeld zu schließen.  
  
#### <a name="to-delete-a-logical-record-relationship"></a>So löschen Sie eine logische Datensatzbeziehung  
  
-   Sie können entweder nur die logische Datensatzbeziehung oder die logische Datensatzbeziehung und den zugeordneten Joinfilter gemeinsam löschen.  
  
     So löschen Sie nur die logische Datensatzbeziehung:  
  
    1.  Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Zeilen filtern** oder im Dialogfeld **Veröffentlichungseigenschaften – \<Veröffentlichung>** auf der Seite **Zeilen filtern** im Bereich **Gefilterte Tabellen** den der logischen Datensatzbeziehung zugeordneten Joinfilter aus, und klicken Sie dann auf **Bearbeiten**.  
  
    2.  Deaktivieren Sie im Dialogfeld **Join bearbeiten** die Option **Logischer Datensatz**.  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     So löschen Sie die logische Datensatzbeziehung und den zugeordneten Joinfilter:  
  
    -   Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Zeilen filtern** bzw. im Dialogfeld **Veröffentlichungseigenschaften – \<Veröffentlichung>** im Bereich **Gefilterte Tabellen** den betreffenden Filter aus, und klicken Sie dann auf **Löschen**. Wenn der Joinfilter, den Sie löschen möchten, mit anderen Joins erweitert ist, werden diese Joins beim Löschen des Filters selbst ebenfalls gelöscht.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können logische Datensatzbeziehungen zwischen Artikeln programmgesteuert mithilfe gespeicherter Replikationsprozeduren angeben.  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a>So definieren Sie eine logische Datensatzbeziehung ohne einen zugeordneten Joinfilter  
  
1.  Wenn die Veröffentlichung irgendwelche gefilterten Artikel enthält, führen Sie [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)aus, und achten Sie im Resultset auf den Wert von **use_partition_groups** .  
  
    -   Wenn der Wert **1**ist, dann werden bereits vorausberechnete Partitionen verwendet.  
  
    -   Ist der in Schritt 1 ermittelte Wert **0**, führen Sie [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert **use_partition_groups** für **@property** und den Wert **true** für **@value**.  
  
        > [!NOTE]  
        >  Wenn die Veröffentlichung keine vorausberechneten Partitionen unterstützt, dann können keine logischen Datensätze verwendet werden. Weitere Informationen finden Sie unter „Anforderungen für die Verwendung vorausberechneter Partitionen“ im Thema [Optimieren der Leistung parametrisierter Filter mithilfe vorausberechneter Partitionen](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
    -   Ist der Wert NULL, muss der Momentaufnahme-Agent ausgeführt werden, um die Momentaufnahme für die Veröffentlichung zu generieren.  
  
2.  Wenn die Artikel, die den logischen Datensatz umfassen, nicht vorhanden sind, führen Sie [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie eine der folgenden Konflikterkennungs- und -lösungsoptionen für den logischen Datensatz an:  
  
    -   Damit Konflikte, die innerhalb verknüpfter Zeilen im logischen Datensatz auftreten, erkannt und gelöst werden, geben Sie den Wert **true** für **@logical_record_level_conflict_detection** und **@logical_record_level_conflict_resolution**.  
  
    -   Um die Standard Konflikterkennung und-Lösung auf Zeilen-oder Spaltenebene zu verwenden, geben Sie `false` den **@logical_record_level_conflict_detection** Wert **@logical_record_level_conflict_resolution**für und als Standardwert an.  
  
3.  Wiederholen Sie Schritt 2 für jeden Artikel, der den logischen Datensatz umfasst. Sie müssen für jeden Artikel im logischen Datensatz die gleiche Konflikterkennung und Konfliktlösungsoption verwenden. Weitere Informationen finden Sie unter [Ermitteln und Lösen von Konflikten in logischen Datensätzen](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).  
  
4.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)aus. Geben **@publication**Sie, den Namen eines Artikels in der Beziehung für **@article**, den Namen des zweiten **@join_articlename**Artikels für, einen Namen für die Beziehung für **@filtername**, eine-Klausel, die die Beziehung zwischen den beiden Artikeln für **@join_filterclause**definiert, den Typ des Joins **@join_unique_key** für und einen der folgenden Werte für **@filter_type**an:  
  
    -   **2** &ndash; Definiert eine logische Datensatzbeziehung.  
  
    -   **3** &ndash; Definiert eine logische Beziehung mit einem Joinfilter.  
  
    > [!NOTE]  
    >  Wird kein Joinfilter verwendet, ist die Richtung der Beziehung zwischen den beiden Artikeln nicht wichtig.  
  
5.  Wiederholen Sie Schritt 2 für jede weitere logische Datensatzbeziehung in der Veröffentlichung.  
  
#### <a name="to-change-conflict-detection-and-resolution-for-logical-records"></a>So ändern Sie die Konflikterkennung und -lösung für logische Datensätze  
  
1.  So erkennen und lösen Sie Konflikte, die innerhalb verknüpfter Zeilen im logischen Datensatz auftreten:  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)aus. Geben Sie den Wert **logical_record_level_conflict_detection** für **@property** und den Wert **true** für **@value**. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und **@force_reinit_subscription**.  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)aus. Geben Sie den Wert **logical_record_level_conflict_resolution** für **@property** und den Wert **true** für **@value**. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und **@force_reinit_subscription**.  
  
2.  So verwenden Sie die Standard-Konflikterkennung und -lösung auf Zeilen- oder Spaltenebene:  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)aus. Geben Sie den Wert **logical_record_level_conflict_detection** für **@property** und den Wert `false` für **@value**an. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und **@force_reinit_subscription**.  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)aus. Geben Sie den Wert **logical_record_level_conflict_resolution** für **@property** und den Wert `false` für **@value**an. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und **@force_reinit_subscription**.  
  
#### <a name="to-remove-a-logical-record-relationship"></a>So entfernen Sie eine logische Datensatzbeziehung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank die folgende Abfrage aus, um alle Informationen über die für die angegebene Veröffentlichung definierten logischen Datensatzbeziehungen zurückzugeben:  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_returnmergelogicalrecords)]  
  
     Achten Sie auf den Namen der zu entfernenden logischen Datensatzbeziehung in der Spalte `filtername` des Resultsets.  
  
    > [!NOTE]  
    >  Diese Abfrage gibt die gleichen Informationen zurück wie [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql). Diese gespeicherte Systemprozedur ermittelt jedoch nur Informationen über logische Datensatzbeziehungen, die auch Joinfilter sind.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql)aus. Geben **@publication**Sie, den Namen eines der Artikel in der Beziehung für **@article**und den Namen der Beziehung aus Schritt 1 für **@filtername**an.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel werden vorausberechnete Partitionen für eine vorhandene Veröffentlichung aktiviert und ein logischer Datensatz erstellt, der die zwei neuen Artikel für die Tabellen `SalesOrderHeader` und `SalesOrderDetail` umfasst.  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_addmergelogicalrecord)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
  
> [!NOTE]  
>  Bei der Mergereplikation können Sie auch angeben, dass Konflikte auf der Ebene logischer Datensätze nachverfolgt und gelöst werden. Diese Optionen können mit RMO jedoch nicht festgelegt werden.  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a>So definieren Sie eine logische Datensatzbeziehung ohne einen zugeordneten Joinfilter  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication> -Klasse, legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> -Eigenschaft und die <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> -Eigenschaft der Veröffentlichung fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  Wenn die <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> -Eigenschaft auf <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>festgelegt ist, ändern Sie sie in <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.  
  
5.  Wenn die Artikel, die den logischen Datensatz enthalten sollen, nicht vorhanden sind, erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeArticle> -Klasse, und legen Sie die folgenden Eigenschaften fest:  
  
    -   Den Namen des Artikels für <xref:Microsoft.SqlServer.Replication.Article.Name%2A>  
  
    -   Den Namen der Veröffentlichung für <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>  
  
    -   (Optional) Wenn der Artikel horizontal gefiltert wird, geben Sie die Zeilenfilterklausel für die <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> -Eigenschaft an. Verwenden Sie diese Eigenschaft, um einen statischen oder parametrisierten Zeilenfilter anzugeben. Weitere Informationen zu parametrisierten Zeilenfiltern finden Sie unter [Parametrisierte Zeilenfilter](../merge/parameterized-filters-parameterized-row-filters.md).  
  
     Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Article.Create%2A> -Methode auf.  
  
7.  Wiederholen Sie die Schritte 5 und 6 für jeden Artikel, der den logischen Datensatz umfasst.  
  
8.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> -Klasse, um die logische Datensatzbeziehung zwischen Artikeln zu definieren. Legen Sie dann die folgenden Eigenschaften fest:  
  
    -   Den Namen des untergeordneten Artikels in der logischen Datensatzbeziehung für die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> -Eigenschaft  
  
    -   Den Namen des bestehenden übergeordneten Artikels in der logischen Datensatzbeziehung für die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> -Eigenschaft  
  
    -   Einen Namen für die logische Datensatzbeziehung für die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> -Eigenschaft  
  
    -   Einen Ausdruck, der die Beziehung für die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> -Eigenschaft definiert  
  
    -   Den Wert <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> für die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> -Eigenschaft. Wenn die logische Datensatzbeziehung auch ein Joinfilter ist, geben Sie den Wert <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> für diese Eigenschaft an. Weitere Informationen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../merge/group-changes-to-related-rows-with-logical-records.md).  
  
9. Rufen Sie die <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> -Methode für das Objekt auf, das den untergeordneten Artikel in der Beziehung darstellt. Übergeben Sie das <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> -Objekt aus Schritt 8, um die Beziehung zu definieren.  
  
10. Wiederholen Sie die Schritte 8 und 9 für jede weitere logische Datensatzbeziehung in der Veröffentlichung.  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a>Beispiel (RMO)  
 In diesem Beispiel wird ein logischer Datensatz erstellt, der die zwei neuen Artikel für die Tabellen `SalesOrderHeader` und `SalesOrderDetail` umfasst.  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Definieren und Ändern eines Joinfilters zwischen Mergeartikeln](define-and-modify-a-join-filter-between-merge-articles.md)   
 [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Definieren und Ändern eines statischen Zeilen Filters](define-and-modify-a-static-row-filter.md)   
 [Gruppieren von Änderungen an verknüpften Zeilen mit logischen Datensätzen](../merge/group-changes-to-related-rows-with-logical-records.md)   
 [Optimieren der Leistung parametrisierter Filter mit voraus berechneten Partitionen](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)   
 [Gruppieren von Änderungen an verknüpften Zeilen mit logischen Datensätzen](../merge/group-changes-to-related-rows-with-logical-records.md)  
  
  
