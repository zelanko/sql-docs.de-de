---
title: Definieren und Ändern eines statischen Zeilenfilters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying filters, static row
- static row filters
- filters [SQL Server replication], static row
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7bb7aebed25c571108e4b0d7e7366fc52c45e3c1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73882306"
---
# <a name="define-and-modify-a-static-row-filter"></a>Definieren oder Ändern eines statischen Zeilenfilters
  In diesem Thema wird beschrieben, wie in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]statische Zeilenfilter definiert und geändert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
-   **So definieren oder ändern Sie einen statischen Zeilenfilter mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie einen statischen Zeilenfilter hinzufügen, ändern oder löschen, nachdem Abonnements für die Veröffentlichung initialisiert wurden, müssen Sie eine neue Momentaufnahme generieren und alle Abonnements nach vorgenommener Änderung erneut initialisieren. Weitere Informationen zum Ändern von Eigenschaften finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md).  
  
-   Wenn die Veröffentlichung für die Peer-zu-Peer-Transaktionsreplikation aktiviert wird, können Tabellen nicht gefiltert werden.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Da diese Filter statisch sind, erhalten alle Abonnenten die gleiche Teilmenge der Daten. Informationen darüber, wie Sie Zeilen in einem Tabellenartikel, der zu einer Mergeveröffentlichung gehört, dynamisch filtern können, damit jeder Abonnent eine andere Partition der Daten erhält, finden Sie unter [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md). Mergereplikation ermöglicht es Ihnen zudem, verknüpfte Zeilen auf Grundlage eines vorhandenen Zeilenfilters zu filtern. Weitere Informationen finden Sie unter [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](define-and-modify-a-join-filter-between-merge-articles.md).  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Definieren, ändern und löschen Sie statische Zeilenfilter auf der Seite **Tabellenzeilen filtern** des Assistenten für neue Veröffentlichung oder der Seite **Filterzeilen** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** . Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
#### <a name="to-define-a-static-row-filter"></a>So definieren Sie einen statischen Zeilenfilter  
  
1.  Die Aktion, die Sie im Assistenten für neue Veröffentlichung auf der Seite **Tabellenzeilen filtern** oder im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** auf der Seite **Zeilen filtern** ausführen, hängt vom Typ der Veröffentlichung ab:  
  
    -   Klicken Sie bei der Momentaufnahme- oder Transaktionsveröffentlichung auf **Hinzufügen**.  
  
    -   Klicken Sie bei der Mergeveröffentlichung auf **Hinzufügen**und dann auf **Filter hinzufügen**.  
  
2.  Wählen Sie in der Dropdownliste im Dialogfeld **Filter hinzufügen** die zu filternde Tabelle aus.  
  
3.  Erstellen Sie im Textfeld **Filteranweisung** eine Filteranweisung. Sie können den Text direkt in den Textbereich eingeben, und Sie können Spalten auch mit Drag und Drop aus dem Listenfeld **Spalten** einfügen.  
  
    > [!NOTE]  
    >  Verwenden Sie einen zweiteiligen Namen für die WHERE-Klausel, drei- oder vierteilige Namen werden nicht unterstützt. Wenn die Veröffentlichung von einem Oracle-Verleger stammt, muss die WHERE-Klausel mit der Oracle-Syntax kompatibel sein.  
  
    -   Der Textbereich **Filteranweisung** enthält den Standardtext im folgenden Format:  
  
        ```sql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   Der Standardtext kann nicht geändert werden. Geben Sie mithilfe der SQL-Standardsyntax im Anschluss an das WHERE-Schlüsselwort die Filterklausel ein. Die vollständige Filterklausel würde folgendermaßen lauten:  
  
        ```sql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   Ein statischer Zeilenfilter kann eine benutzerdefinierte Funktion einschließen. Die vollständige Filterklausel für einen statischen Zeilenfilter mit einer benutzerdefinierten Funktion würde folgendermaßen lauten:  
  
        ```sql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften.-.\<Veröffentlichung>** befinden, klicken Sie auf **OK**, um zu speichern und das Dialogfeld zu schließen.  
  
#### <a name="to-modify-a-static-row-filter"></a>So ändern Sie einen statischen Zeilenfilter  
  
1.  Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Tabellenzeilen filtern** oder im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** auf der Seite **Zeilen filtern** im Bereich **Gefilterte Tabellen** einen Filter aus, und klicken Sie dann auf **Bearbeiten**.  
  
2.  Ändern Sie den Filter im Dialogfeld **Filter bearbeiten** .  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-static-row-filter"></a>So löschen Sie einen statischen Zeilenfilter  
  
1.  Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Tabellenzeilen filtern** oder im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung<** auf der Seite **Zeilen filtern** im Bereich **Gefilterte Tabellen** einen Filter aus, und klicken Sie dann auf **Löschen**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Wenn Sie Tabellenartikel erstellen, können Sie eine WHERE-Klausel definieren, um Zeilen aus einem Artikel zu filtern. Zudem können Sie einen Zeilenfilter ändern, nachdem er definiert wurde. Statische Zeilenfilter können mithilfe gespeicherter Replikationsprozeduren programmgesteuert erstellt und geändert werden.  
  
#### <a name="to-define-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a>So definieren Sie einen statischen Zeilenfilter für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Definieren Sie den zu filternden Artikel. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank, [Sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) aus. Geben Sie für **\@article** den Namen des Artikels, für **\@publication** den Namen der Veröffentlichung, für **\@filter_name** den Namen des Filters und für **\@filter_clause** die Filterklausel an (ausgenommen `WHERE`).  
  
3.  Wenn außerdem ein Spaltenfilter definiert werden muss, finden Sie Informationen unter [Definieren und Ändern eines Spaltenfilters](define-and-modify-a-column-filter.md). Führen Sie andernfalls [Sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) aus. Geben Sie für **\@publication** den Namen der Veröffentlichung, für **\@article** den Namen des gefilterten Artikels und für **\@filter_clause** die in Schritt 2 angegebene Filterklausel an. Damit werden die Synchronisierungsobjekte für den gefilterten Artikel erstellt.  
  
#### <a name="to-modify-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a>So ändern Sie einen statischen Zeilenfilter für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank, [Sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) aus. Geben Sie für **\@article** den Namen des Artikels, für **\@publication** den Namen der Veröffentlichung, für **\@filter_name** den Namen des neuen Filters und für **\@filter_clause** die neue Filterklausel an (ausgenommen `WHERE`). Da durch diese Änderung Daten in vorhandenen Abonnements ungültig werden, geben Sie für **\@force_reinit_subscription** den Wert **1** an.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_articleview#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) aus. Geben Sie für **\@publication** den Namen der Veröffentlichung, für **\@article** den Namen des gefilterten Artikels und für **\@filter_clause** die in Schritt 1 angegebene Filterklausel an. Dadurch wird die Sicht neu erstellt, die den gefilterten Artikel definiert.  
  
3.  Führen Sie den Auftrag des Momentaufnahme-Agents für die Veröffentlichung erneut aus, um eine aktualisierte Momentaufnahme zu erstellen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
4.  Erneutes Initialisieren von Abonnements Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](../reinitialize-subscriptions.md).  
  
#### <a name="to-delete-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a>So löschen Sie einen statischen Zeilenfilter für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank, [Sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) aus. Geben Sie für **\@article** den Namen des Artikels, für **\@publication** den Namen der Veröffentlichung und für sowohl **\@filter_name** als auch **\@filter_clause** den Wert NULL an. Da durch diese Änderung Daten in vorhandenen Abonnements ungültig werden, geben Sie für **\@force_reinit_subscription** den Wert **1** an.  
  
2.  Führen Sie den Auftrag des Momentaufnahme-Agents für die Veröffentlichung erneut aus, um eine aktualisierte Momentaufnahme zu erstellen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
3.  Erneutes Initialisieren von Abonnements Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](../reinitialize-subscriptions.md).  
  
#### <a name="to-define-a-static-row-filter-for-a-merge-publication"></a>So definieren Sie einen statischen Zeilenfilter für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) aus. Geben Sie für **\@subset_filterclause** die Filterklausel an (ausgenommen `WHERE`). Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
2.  Wenn außerdem ein Spaltenfilter definiert werden muss, finden Sie Informationen unter [Definieren und Ändern eines Spaltenfilters](define-and-modify-a-column-filter.md).  
  
#### <a name="to-modify-a-static-row-filter-for-a-merge-publication"></a>So ändern Sie einen statischen Zeilenfilter für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) aus. Geben Sie für **\@publication** den Namen der Veröffentlichung, für **\@article** den Namen des gefilterten Artikels, für **\@property** den Wert **subset_filterclause** und für **\@value** die neue Filterklausel an (ausgenommen `WHERE`). Da durch diese Änderung Daten in vorhandenen Abonnements ungültig werden, geben Sie für **\@force_reinit_subscription** den Wert 1 an.  
  
2.  Führen Sie den Auftrag des Momentaufnahme-Agents für die Veröffentlichung erneut aus, um eine aktualisierte Momentaufnahme zu erstellen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
3.  Erneutes Initialisieren von Abonnements Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](../reinitialize-subscriptions.md).  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 In diesem Beispiel für eine Transaktionsreplikation wird der Artikel horizontal gefiltert, um alle eingestellten Produkte zu entfernen.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 In diesem Beispiel für eine Mergereplikation werden die Artikel horizontal gefiltert, und nur die Zeilen zurückgegeben, die auf den angegebenen Vertriebsmitarbeiter entfallen. Außerdem wird ein Joinfilter verwendet. Weitere Informationen finden Sie unter [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](define-and-modify-a-join-filter-between-merge-articles.md).  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md)   
 [Filtern von veröffentlichten Daten](filter-published-data.md)   
 [Filtern veröffentlichter Daten für die Mergereplikation](../merge/filter-published-data-for-merge-replication.md)  
  
  
