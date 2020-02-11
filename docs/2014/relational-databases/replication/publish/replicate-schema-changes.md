---
title: Replizieren von Schemaänderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 84918dd3f50d129485911fc880e67c0152fa905c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73882248"
---
# <a name="replicate-schema-changes"></a>Replizieren von Schemaänderungen
  In diesem Thema wird beschrieben, wie Schemaänderungen in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]repliziert werden.  
  
 Wenn Sie die folgenden Schema Änderungen an einem veröffentlichten Artikel vornehmen, werden diese standardmäßig an die Abonnenten weiter [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gegeben:  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
-   **So replizieren Sie Schema Änderungen mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   ALTER TABLE... Die Drop Column-Anweisung wird immer auf alle Abonnenten repliziert, deren Abonnement die Spalten enthält, die gelöscht werden, auch wenn Sie die Replikation von Schema Änderungen deaktivieren.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Wenn die Schemaänderungen nicht auf eine Veröffentlichung repliziert werden sollen, deaktivieren Sie im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Replikation der Schemaänderungen. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
#### <a name="to-disable-replication-of-schema-changes"></a>So deaktivieren Sie die Replikation von Schemaänderungen  
  
1.  Legen Sie auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Eigenschaft **Schemaänderungen replizieren** auf **FALSE** fest.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Wenn nur bestimmte Schemaänderungen weitergegeben werden sollen, legen Sie für die Eigenschaft vor der Schemaänderung **Wahr** und danach **Falsch** fest. Wenn umgekehrt die meisten Schemaänderungen weitergegeben werden sollen und nur eine bestimmte Änderung nicht repliziert werden soll, legen Sie für die Eigenschaft vor der entsprechenden Schemaänderung **Falsch** und anschließend wieder **Wahr** fest.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können mithilfe gespeicherter Replikationsprozeduren angeben, ob diese Schemaänderungen repliziert werden sollen. Welche gespeicherte Prozedur Sie verwenden, hängt vom Typ der Veröffentlichung ab.  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a>So erstellen Sie eine Momentaufnahme- oder Transaktionsveröffentlichung, die keine Schemaänderungen repliziert  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungs Datenbank [sp_addpublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)aus, und geben Sie für ** \@replicate_ddl**den Wert **0** an. Weitere Informationen finden Sie unter [Create a Publication](create-a-publication.md).  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a>So erstellen Sie eine Mergeveröffentlichung, die keine Schemaänderungen repliziert  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungs Datenbank [sp_addmergepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)aus, und geben Sie für ** \@replicate_ddl**den Wert **0** an. Weitere Informationen finden Sie unter [Create a Publication](create-a-publication.md).  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a>So deaktivieren Sie vorübergehend die Replikation von Schemaänderungen in einer Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie für eine Veröffentlichung mit Replikation von Schema Änderungen [sp_changepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus, und geben Sie dabei den Wert **replicate_ddl** für ** \@** die-Eigenschaft und den Wert **0** für ** \@Value**an.  
  
2.  Führen Sie den DDL-Befehl für das veröffentlichte Objekt aus.  
  
3.  Optionale Aktivieren Sie die Replikation von Schema Änderungen erneut, indem Sie [sp_changepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)ausführen, und ** \@** geben Sie dabei den Wert **replicate_ddl** für die-Eigenschaft und den Wert **1** für ** \@Value**an.  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a>So deaktivieren Sie vorübergehend die Replikation von Schemaänderungen in einer Mergeveröffentlichung  
  
1.  Führen Sie für eine Veröffentlichung mit Replikation von Schema Änderungen [sp_changemergepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus, und geben Sie dabei den Wert **replicate_ddl** für ** \@** die-Eigenschaft und den Wert **0** für ** \@Value**an.  
  
2.  Führen Sie den DDL-Befehl für das veröffentlichte Objekt aus.  
  
3.  Optionale Aktivieren Sie die Replikation von Schema Änderungen erneut, indem Sie [sp_changemergepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)ausführen, und ** \@** geben Sie dabei den Wert **replicate_ddl** für die-Eigenschaft und den Wert **1** für ** \@Value**an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vornehmen von Schema Änderungen in Veröffentlichungs Datenbanken](make-schema-changes-on-publication-databases.md)   
 [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](make-schema-changes-on-publication-databases.md)  
  
  
