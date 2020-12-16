---
title: Replizieren von Schemaänderungen | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Schemaänderungen in SQL Server mithilfe von SQL Server Management Studio oder Transact-SQL replizieren.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: afabd27f7d4fd6812614d8cac88612916ce130e2
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97468981"
---
# <a name="replicate-schema-changes"></a>Replizieren von Schemaänderungen
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  In diesem Thema wird beschrieben, wie Schemaänderungen in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]repliziert werden.  
  
 Wenn Sie in einem veröffentlichten Artikel die folgenden Schemaänderungen vornehmen, werden diese standardmäßig an [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Abonnenten weitergegeben:  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
-   **So replizieren Sie Schemaänderungen mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Die ALTER TABLE ... Die DROP COLUMN-Anweisung wird grundsätzlich auf alle Abonnenten repliziert, deren Abonnement die Spalten enthält, die gelöscht werden, auch wenn Sie die Replikation von Schemaänderungen deaktiviert haben.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Wenn die Schemaänderungen nicht auf eine Veröffentlichung repliziert werden sollen, deaktivieren Sie im Dialogfeld **Veröffentlichungseigenschaften – \<Publication>** die Replikation der Schemaänderungen. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-disable-replication-of-schema-changes"></a>So deaktivieren Sie die Replikation von Schemaänderungen  
  
1.  Legen Sie auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften – \<Publication>** die Eigenschaft **Schemaänderungen replizieren** auf **FALSE** fest.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

     Wenn nur bestimmte Schemaänderungen weitergegeben werden sollen, legen Sie für die Eigenschaft vor der Schemaänderung **Wahr** und danach **Falsch** fest. Wenn umgekehrt die meisten Schemaänderungen weitergegeben werden sollen und nur eine bestimmte Änderung nicht repliziert werden soll, legen Sie für die Eigenschaft vor der entsprechenden Schemaänderung **Falsch** und anschließend wieder **Wahr** fest.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können mithilfe gespeicherter Replikationsprozeduren angeben, ob diese Schemaänderungen repliziert werden sollen. Welche gespeicherte Prozedur Sie verwenden, hängt vom Typ der Veröffentlichung ab.  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a>So erstellen Sie eine Momentaufnahme- oder Transaktionsveröffentlichung, die keine Schemaänderungen repliziert  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addpublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) aus, und geben Sie einen Wert von `0` für `@replicate_ddl` an. Weitere Informationen finden Sie unter [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a>So erstellen Sie eine Mergeveröffentlichung, die keine Schemaänderungen repliziert  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) aus, und geben Sie einen Wert von `0` für `@replicate_ddl` an. Weitere Informationen finden Sie unter [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a>So deaktivieren Sie vorübergehend die Replikation von Schemaänderungen in einer Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie für eine Veröffentlichung mit Replikation von Schemaänderungen [sp_changepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) aus, und geben Sie einen Wert `replicate_ddl` für `@property` und einen Wert von `0` für `@value` an.  
  
2.  Führen Sie den DDL-Befehl für das veröffentlichte Objekt aus.  
  
3.  (Optional) Aktivieren Sie die Replikation von Schemaänderungen erneut, indem Sie [sp_changepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) ausführen, und geben Sie einen Wert `replicate_ddl` für `@property` und einen Wert von `1` für `@value` an.  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a>So deaktivieren Sie vorübergehend die Replikation von Schemaänderungen in einer Mergeveröffentlichung  
  
1.  Führen Sie für eine Veröffentlichung mit Replikation von Schemaänderungen [sp_changemergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) aus, und geben Sie einen Wert `replicate_ddl` für `@property` und einen Wert von `0` für `@value` an.  
  
2.  Führen Sie den DDL-Befehl für das veröffentlichte Objekt aus.  
  
3.  (Optional) Aktivieren Sie die Replikation von Schemaänderungen erneut, indem Sie [sp_changemergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) ausführen, und geben Sie einen Wert `replicate_ddl` für `@property` und einen Wert von `1` für `@value` an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
