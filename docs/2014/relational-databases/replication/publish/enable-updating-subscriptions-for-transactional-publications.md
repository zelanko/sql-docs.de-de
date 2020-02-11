---
title: Aktivieren des Aktualisierens von Abonnements für Transaktionsveröffentlichungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, enabling
- subscriptions [SQL Server replication], updatable
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 963fe86b0d5939c82bffb9c07d5adacbadadba89
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68199425"
---
# <a name="enable-updating-subscriptions-for-transactional-publications"></a>Aktivieren des Aktualisierens von Abonnements für Transaktionsveröffentlichungen
  In diesem Thema wird beschrieben, wie das Aktualisieren von Abonnements für Transaktionsveröffentlichungen in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]aktiviert wird.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  

  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Aktivieren Sie aktualisierbare Abonnements für Transaktionsveröffentlichungen auf der Seite **Veröffentlichungstyp** des Assistenten für neue Veröffentlichung. Weitere Informationen zum Zugreifen auf diesen Assistenten finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md). Nach der Erstellung einer Veröffentlichung ist das Aktivieren von aktualisierbaren Abonnements nicht mehr möglich.  
  
 Um aktualisierbare Abonnements verwenden zu können, müssen auch im Assistenten für neue Abonnements Optionen konfiguriert werden. Weitere Informationen finden Sie unter [Erstellen eines aktualisierbaren Abonnements für eine Transaktionsveröffentlichung](../publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
#### <a name="to-enable-updating-subscriptions"></a>So aktivieren Sie aktualisierbare Abonnements  
  
1.  Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Veröffentlichungstyp** die Option **Transaktionsveröffentlichung mit aktualisierbaren Abonnements**aus.  
  
2.  Geben Sie auf der Seite **Agentsicherheit** neben den Sicherheitseinstellungen für den Momentaufnahme-Agent und den Protokolllese-Agent auch die Sicherheitseinstellungen für den Warteschlangenlese-Agent an. Weitere Informationen zu den Berechtigungen, die für das Konto erforderlich sind, unter dem der Warteschlangenlese-Agent ausgeführt wird, finden Sie unter [Replication Agent Security Model](../security/replication-agent-security-model.md).  
  
    > [!NOTE]  
    >  Der Warteschlangenlese-Agent wird auch dann konfiguriert, wenn Sie lediglich Abonnements mit sofortigem Update verwenden.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Wenn Sie mithilfe von gespeicherten Replikationsprozeduren programmgesteuert eine Transaktionsveröffentlichung erstellen, können Sie das sofortige oder das verzögerte Aktualisieren der Abonnements aktivieren.  
  
#### <a name="to-create-a-publication-that-supports-immediate-updating-subscriptions"></a>So erstellen Sie eine Veröffentlichung, die Abonnements mit sofortigem Update unterstützt  
  
1.  Erstellen Sie, falls notwendig, einen Protokolllese-Agentauftrag für die Veröffentlichungsdatenbank.  
  
    -   Wenn bereits ein Protokolllese-Agentauftrag für die Veröffentlichungsdatenbank vorhanden ist, fahren Sie mit Schritt 2 fort.  
  
    -   Wenn Sie sich nicht sicher sind, ob ein Protokolllese-Agentauftrag für die Veröffentlichungsdatenbank vorhanden ist, dann führen Sie [sp_helplogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Wenn das Resultset leer ist, muss ein Protokolllese-Agentauftrag erstellt werden.  
  
    -   Führen Sie [sp_addlogreader_agent &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)auf dem Verleger aus. Geben Sie [!INCLUDE[msCoName](../../../includes/msconame-md.md)] die Windows-Anmelde Informationen an, unter **@job_name** denen **@password**der Agent für und ausgeführt wird. Wenn der Agent zum Herstellen der Verbindung mit dem Verleger die SQL Server-Authentifizierung verwendet, müssen Sie zudem den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**.  
  
2.  Führen Sie [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) aus, und geben Sie den Wert **TRUE** für den Parameter **@allow_sync_tran** an.  
  
3.  Führen Sie auf dem Verleger [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) aus. Geben Sie den in Schritt 2 für **@publication** verwendeten Veröffentlichungsnamen und die Windows-Anmelde Informationen an, unter **@job_name** denen **@password**die Momentaufnahmen-Agent für und ausgeführt wird. Wenn der Agent zum Herstellen der Verbindung mit dem Verleger die SQL Server-Authentifizierung verwendet, müssen Sie zudem den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**. Dadurch wird ein Auftrag des Momentaufnahme-Agents für die Veröffentlichung erstellt.  
  
4.  Fügen Sie der Veröffentlichung Artikel hinzu. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
5.  Erstellen Sie auf dem Abonnenten ein Abonnement mit Update für diese Veröffentlichung. Weitere Informationen finden Sie unter [Erstellen eines aktualisierbaren Abonnements für eine Transaktionsveröffentlichung](../publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
#### <a name="to-create-a-publication-that-supports-queued-updating-subscriptions"></a>So erstellen Sie eine Veröffentlichung, die Abonnements mit verzögertem Update über eine Warteschlange unterstützt  
  
1.  Erstellen Sie, falls notwendig, einen Protokolllese-Agentauftrag für die Veröffentlichungsdatenbank.  
  
    -   Wenn bereits ein Protokolllese-Agentauftrag für die Veröffentlichungsdatenbank vorhanden ist, fahren Sie mit Schritt 2 fort.  
  
    -   Wenn Sie sich nicht sicher sind, ob ein Protokolllese-Agentauftrag für die Veröffentlichungsdatenbank vorhanden ist, dann führen Sie [sp_helplogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Wenn das Resultset leer ist, muss ein Protokolllese-Agentauftrag erstellt werden.  
  
    -   Führen Sie [sp_addlogreader_agent &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)auf dem Verleger aus. Geben Sie die Windows-Anmelde Informationen an, unter **@job_name** denen **@password**der Agent für und ausgeführt wird. Wenn der Agent zum Herstellen der Verbindung mit dem Verleger die SQL Server-Authentifizierung verwendet, müssen Sie zudem den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**.  
  
2.  Erstellen Sie, falls notwendig, einen Warteschlangenlese-Agentauftrag für den Verteiler.  
  
    -   Wenn bereits ein Warteschlangenlese-Agentauftrag für die Verteilungsdatenbank vorhanden ist, fahren Sie mit Schritt 3 fort.  
  
    -   Wenn Sie sich nicht sicher sind, ob ein Warteschlangenlese-Agentauftrag für die Verteilungsdatenbank vorhanden ist, dann führen Sie [sp_helpqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql) auf dem Verteiler für die Verteilungsdatenbank aus. Wenn das Resultset leer ist, muss ein Warteschlangenlese-Agentauftrag erstellt werden.  
  
    -   Führen Sie auf dem Verteiler [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) aus. Geben Sie die Windows-Anmelde Informationen an, unter **@job_name** denen **@password**der Agent für und ausgeführt wird. Diese Anmeldeinformationen werden verwendet, wenn der Warteschlangenlese-Agent eine Verbindung mit dem Verleger und dem Abonnenten herstellt. Weitere Informationen finden Sie unter [Sicherheitsmodell des Replikations-Agents](../security/replication-agent-security-model.md).  
  
3.  Führen Sie [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) aus, und geben Sie den Wert **TRUE** für den Parameter **@allow_queued_tran** und den Wert **Pub Wins**, **Sub Reinit** oder **Sub Wins** für **@conflict_policy** an.  
  
4.  Führen Sie auf dem Verleger [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) aus. Geben Sie den in Schritt 3 für **@publication** verwendeten Veröffentlichungsnamen und die Windows-Anmelde Informationen an, unter **@snapshot_job_name** denen **@password**die Momentaufnahmen-Agent für und ausgeführt wird. Wenn der Agent zum Herstellen der Verbindung mit dem Verleger die SQL Server-Authentifizierung verwendet, müssen Sie zudem den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**. Dadurch wird ein Auftrag des Momentaufnahme-Agents für die Veröffentlichung erstellt.  
  
5.  Fügen Sie der Veröffentlichung Artikel hinzu. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
6.  Erstellen Sie auf dem Abonnenten ein Abonnement mit Update für diese Veröffentlichung. Weitere Informationen finden Sie unter [Erstellen eines aktualisierbaren Abonnements für eine Transaktionsveröffentlichung](../publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
#### <a name="to-change-the-conflict-policy-for-a-publication-that-allows-queued-updating-subscriptions"></a>So ändern Sie die Konfliktrichtlinie für eine Veröffentlichung, die Abonnements mit verzögertem Update über eine Warteschlange zulässt  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) aus. Geben Sie den Wert **conflict_policy** für **@property** sowie für die gewünschte Konfliktrichtlinie einen der Werte **pub wins**, **sub reinit**oder **sub wins** für **@value**aktiviert wird.  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 In diesem Beispiel wird eine Veröffentlichung erstellt, die sowohl sofortige als auch verzögerte Updates von Pullabonnements unterstützt.  
  
 [!code-sql[HowTo#sp_createtranupdatingpub](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpubupdate.sql#sp_createtranupdatingpub)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen der Konflikt Lösungs Optionen für verzögerte Updates über eine Warteschlange &#40;SQL Server Management Studio&#41;](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Veröffentlichungs Typen für die Transaktions Replikation](../transactional/transactional-replication.md)   
 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Create a Publication](create-a-publication.md)   
 [Erstellen eines aktualisierbaren Abonnements für eine Transaktions Veröffentlichung](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Aktualisierbare Abonnements für die Transaktions Replikation](../transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Verwenden von sqlcmd mit Skriptvariablen](../../scripting/sqlcmd-use-with-scripting-variables.md)  
  
  
