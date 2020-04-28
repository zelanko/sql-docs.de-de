---
title: Festlegen des Ablaufdatums für Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], expiration
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- deactivating subscriptions
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 663de184c811291c4b583ddbaf2fb6862097c54f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73882178"
---
# <a name="set-the-expiration-period-for-subscriptions"></a>Festlegen des Ablaufdatums für Abonnements
  In diesem Thema wird beschrieben, wie der Ablaufzeitraum für Abonnements in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]festgelegt wird. Der Ablaufzeitraum für Abonnements bestimmt den Zeitraum, bevor ein Abonnement abläuft und entfernt wird. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
-   **So legen Sie das Ablaufdatum für Abonnements fest mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Das Abonnementablaufdatum wird auch als *Beibehaltungsdauer*bezeichnet. Der Cleanup von Mergereplikationsmetadaten wird durch diese Einstellung bestimmt:  
  
    -   Die Replikation kann der Cleanup von Metadaten aus den Veröffentlichungs- und Abonnementdatenbanken erst ausführen, wenn das Ablaufdatum erreicht ist. Geben Sie keinen zu hohen Wert für die Beibehaltungsdauer an, da dies zu einer Beeinträchtigung der Replikationsleistung führen kann. Es wird empfohlen, eine niedrigere Einstellung zu verwenden, wenn Sie zuverlässig einschätzen können, dass alle Abonnenten innerhalb dieser Zeitspanne regelmäßig synchronisiert werden.  
  
         Die Beibehaltungsdauer für Mergeveröffentlichungen weist eine 24-stündige Kulanzfrist auf, um Abonnenten in unterschiedlichen Zeitzonen aufzunehmen. Wenn Sie beispielsweise eine Beibehaltungsdauer von einem Tag festgelegt haben, beträgt die tatsächliche Beibehaltungsdauer 48 Stunden.  
  
    -   Es ist möglich, anzugeben, dass Abonnements nie ablaufen. Es wird jedoch nachdrücklich empfohlen, diesen Wert nicht zu verwenden, da sonst kein Cleanup der Metadaten ausgeführt werden kann.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Geben Sie das Ablaufdatum von Abonnements im Dialogfeld **Veröffentlichungseigenschaften -** Veröffentlichung> **auf der Seite \<Allgemein** an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
#### <a name="to-set-the-expiration-period-for-subscriptions"></a>So legen Sie das Ablaufdatum für Abonnements fest  
  
1.  Geben Sie im Dialogfeld **Veröffentlichungseigenschaften -** Veröffentlichung>**auf der Seite**Allgemein **im Bereich \<Ablaufdatum für das Abonnement** an, ob Abonnements ablaufen sollen.  
  
2.  Falls dies der Fall ist, geben Sie die Dauer an, nach der Abonnements ablaufen sollen.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können gespeicherte Replikationsprozeduren dazu verwenden, diesen Wert festzulegen, wenn eine Veröffentlichung erstellt wird, und diesen Wert zu einem späteren Zeitpunkt zu ändern.  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a>So legen Sie den Ablaufzeitraum eines Abonnements für eine Momentaufnahme- oder eine Transaktionsveröffentlichung fest  
  
1.  Führen Sie auf dem Verleger [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)aus. Geben Sie für **\@retention** den gewünschten Ablaufzeitraum für das Abonnement in Stunden an. Der Standardablaufzeitraum beträgt 336 Stunden. Weitere Informationen finden Sie unter [Create a Publication](create-a-publication.md).  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-merge-publication"></a>So legen Sie den Ablaufzeitraum eines Abonnements für eine Mergeveröffentlichung fest  
  
1.  Führen Sie auf dem Verleger [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)aus. Geben Sie für **\@retention** den gewünschten Wert für den Ablaufzeitraum des Abonnements an. Geben Sie für **\@retention_period_unit** die Einheiten an, in denen der Ablaufzeitraum ausgedrückt wird. Es stehen die folgenden Werte zur Auswahl:  
  
    -   **1** = Woche  
  
    -   **2** = Monat  
  
    -   **3** = Jahr  
  
     Der Standardablaufzeitraum beträgt 14 Tage. Weitere Informationen finden Sie unter [Create a Publication](create-a-publication.md).  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a>So ändern Sie den Ablaufzeitraum eines Abonnements für eine Momentaufnahme- oder eine Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus. Geben Sie **retention** für **\@property** und den neuen Abonnementablaufzeitraum in Stunden für **\@value** an.  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-merge-publication"></a>So ändern Sie den Ablaufzeitraum eines Abonnements für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql) aus, und geben Sie dazu **\@publication** und **\@publisher** an. Der Wert von **retention_period_unit** im Resultset ist einer der folgenden:  
  
    -   **0** = Tag  
  
    -   **1** = Woche  
  
    -   **2** = Monat  
  
    -   **3** = Jahr  
  
2.  Führen Sie auf dem Verleger [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus. Geben Sie **retention** für **\@property** und den neuen Abonnementablaufzeitraum als Text, der auf der Einheit für die Beibehaltungsdauer aus Schritt 1 basiert, für **\@value** an.  
  
3.  (Optional) Führen Sie auf dem Verleger [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus. Geben Sie **retention_period_unit** für **\@property** und eine neue Einheit für den Abonnementablaufzeitraum für **\@value** an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Abonnementablauf und -deaktivierung](../subscription-expiration-and-deactivation.md)  
  
  
