---
title: Löschen eines Artikels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], dropping
- sp_droparticle
- sp_dropmergearticle
- deleting articles
- removing articles
- dropping articles
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4be2287a1c0d43ccfdfaeaca3378f6d10f100134
ms.sourcegitcommit: 619917a0f91c8f1d9112ae6ad9cdd7a46a74f717
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73882275"
---
# <a name="delete-an-article"></a>Delete an Article
  In diesem Thema wird beschrieben, wie ein Artikel in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder Replikationsverwaltungsobjekten (RMO) gelöscht wird. Informationen über die Bedingungen, unter denen Artikel gelöscht werden können, und darüber, ob das Löschen eines Artikels eine neue Momentaufnahme oder die erneute Initialisierung der Abonnements erforderlich macht, finden Sie unter [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](add-articles-to-and-drop-articles-from-existing-publications.md).  
  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Artikel können programmgesteuert mit gespeicherten Replikationsprozeduren gelöscht werden. Die verwendeten gespeicherten Prozeduren hängen vom Typ der Veröffentlichung ab, zu der der Artikel gehört.  
  
#### <a name="to-delete-an-article-from-a-snapshot-or-transactional-publication"></a>So löschen Sie einen Artikel aus einer Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) aus, um einen durch **\@article** angegebenen Artikel aus der durch **\@publication** angegebenen Veröffentlichung zu löschen. Geben Sie fürforce_invalidate_snapshot **den Wert \@1** an.  
  
2.  (Optional) Um das veröffentlichte Objekt vollständig aus der Veröffentlichungsdatenbank zu löschen, führen Sie den Befehl `DROP <objectname>` auf dem Verleger für die Veröffentlichungsdatenbank aus.  
  
#### <a name="to-delete-an-article-from-a-merge-publication"></a>So löschen Sie einen Artikel aus einer Mergeveröffentlichung  
  
1.  Führen Sie [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) aus, um einen durch **\@article** angegebenen Artikel aus der durch **\@publication** angegebenen Veröffentlichung zu löschen. Geben Sie dafür ggf. fürforce_invalidate_snapshot **den Wert \@1** und fürforce_reinit_subscription **den Wert \@1** an.  
  
2.  (Optional) Um das veröffentlichte Objekt vollständig aus der Veröffentlichungsdatenbank zu löschen, führen Sie den Befehl `DROP <objectname>` auf dem Verleger für die Veröffentlichungsdatenbank aus.  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 Im folgenden Beispiel wird ein Artikel aus einer Transaktionsveröffentlichung gelöscht. Da durch diese Änderung die vorhandene Momentaufnahme ungültig wird, wird für den Parameterforce_invalidate_snapshot **der Wert \@1** angegeben.  
  
 [!code-sql[HowTo#sp_droparticle](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droparticle)]  
  
 Im folgenden Beispiel werden zwei Artikel aus einer Mergeveröffentlichung gelöscht. Da durch diese Änderungen die vorhandene Momentaufnahme ungültig wird, wird für den Parameterforce_invalidate_snapshot **der Wert \@1** angegeben.  
  
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergearticle)]
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergearticles.sql#sp_dropmergearticle)]  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Sie können Artikel mithilfe von Replikationsverwaltungsobjekten (RMO) programmgesteuert löschen. Welche RMO-Klassen Sie zum Löschen eines Artikels verwenden, hängt vom Typ der Veröffentlichung ab, zu der der Artikel gehört.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a>So löschen Sie einen Artikel, der zu einer Momentaufnahme- oder Transaktionsveröffentlichung gehört  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransArticle> -Klasse.  
  
3.  Legen Sie die Eigenschaften <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>und <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> fest.  
  
4.  Legen Sie die Verbindung aus Schritt 1 für die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft fest.  
  
5.  Überprüfen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> -Eigenschaft, um festzustellen, ob der Artikel vorhanden ist. Wenn der Wert dieser Eigenschaft `false` lautet, wurden entweder die Artikeleigenschaften in Schritt 3 falsch definiert, oder der Artikel ist nicht vorhanden.  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> -Methode auf.  
  
7.  Trennen Sie alle Verbindungen.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-merge-publication"></a>So löschen Sie einen Artikel, der zu einer Mergeveröffentlichung gehört  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeArticle> -Klasse.  
  
3.  Legen Sie die Eigenschaften <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>und <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> fest.  
  
4.  Legen Sie die Verbindung aus Schritt 1 für die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft fest.  
  
5.  Überprüfen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> -Eigenschaft, um festzustellen, ob der Artikel vorhanden ist. Wenn der Wert dieser Eigenschaft `false` lautet, wurden entweder die Artikeleigenschaften in Schritt 3 falsch definiert, oder der Artikel ist nicht vorhanden.  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> -Methode auf.  
  
7.  Trennen Sie alle Verbindungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Konzepte für gespeicherte Systemprozeduren für die Replikation](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
