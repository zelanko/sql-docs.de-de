---
title: Erstellen eines aktualisierbaren Abonnements für eine Transaktions Veröffentlichung (Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- updateable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e784216116bdb9ab308dff5fa998740b0fa459b0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060574"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-management-studio"></a>Erstellen eines aktualisierbaren Abonnements für eine Transaktionsveröffentlichung (Management Studio)

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
Bei einer Transaktionsreplikation können am Abonnenten vorgenommene Änderungen mithilfe sofort aktualisierbarer Abonnements oder Abonnements mit verzögerter Aktualisierung über eine Warteschlange an den Verleger zurückgegeben werden. Aktualisierbare Abonnements können mithilfe von gespeicherten Replikationsprozeduren programmgesteuert erstellt werden.

Zum Konfigurieren aktualisierbarer Abonnements steht Ihnen die Seite **Aktualisierbare Abonnements** des **Assistenten für neue Abonnements** zur Verfügung. Diese Seite ist nur verfügbar, wenn Sie eine Transaktionsveröffentlichung für aktualisierbare Abonnements aktiviert haben. Weitere Informationen zum Aktivieren aktualisierbarer Abonnements finden Sie unter [Aktivieren des Aktualisierens von Abonnements für Transaktionsveröffentlichungen](enable-updating-subscriptions-for-transactional-publications.md).   
  
## <a name="configure-an-updatable-subscription-from-the-publisher"></a>Konfigurieren eines aktualisierbaren Abonnements vom Verleger aus  

1. Stellen Sie mit dem Verleger in Microsoft SQL Server Management Studio eine Verbindung her, und erweitern Sie dann den Serverknoten.
2. Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .
3. Klicken Sie mit der rechten Maustaste auf eine Transaktionsveröffentlichung, die für aktualisierbare Abonnements aktiviert ist, und klicken Sie dann auf **Neue Abonnements**.
4. Geben Sie auf den folgenden Seiten des Assistenten die Optionen für das Abonnement an. Geben Sie dabei z. B. an, wo der Verteilungs-Agent ausgeführt werden soll.
5. Kontrollieren Sie auf der Seite **Aktualisierbare Abonnements** des **Assistenten für neue Veröffentlichung**, dass die Option **Replizieren** aktiviert ist.
6. Wählen Sie in der Dropdownliste **Commit auf Verleger ausführen** eine Option aus:

    *  Wenn Sie Abonnements mit sofortigem Update verwenden möchten, aktivieren Sie die Option **Commit für Änderungen gleichzeitig ausführen**. Wenn Sie diese Option aktivieren und die Veröffentlichung Abonnements mit verzögertem Update über eine Warteschlange zulässt (Standardkonfiguration bei Veröffentlichungen, die im Assistenten für neue Veröffentlichung erstellt wurden), wird für die **update_mode**-Abonnementeigenschaft **failover** festgelegt. Dieser Modus ermöglicht es Ihnen, bei Bedarf später zum Update über eine Warteschlange zu wechseln.
    *  Wenn Sie Abonnements mit verzögertem Update über eine Warteschlange verwenden möchten, aktivieren Sie die Option **Änderungen in die Warteschlange einreihen und Commit baldmöglichst ausführen**. Wenn Sie diese Option aktivieren, die Veröffentlichung Abonnements mit sofortigem Update zulässt (Standardkonfiguration bei Veröffentlichungen, die im Assistenten für neue Veröffentlichung erstellt wurden) und auf dem Abonnenten SQL Server 2005 oder eine höhere Version ausgeführt wird, wird für die **update_mode**-Abonnementeigenschaft die Einstellung „queued failover“ festgelegt. Dieser Modus ermöglicht es Ihnen, bei Bedarf später zum sofortigen Update zu wechseln.

    Weitere Informationen zum Umschalten zwischen den Updatemodi finden Sie unter [Umschalten zwischen Updatemodi für ein aktualisierbares Transaktionsabonnement](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

7. Bei Abonnements, die das sofortige Update verwenden oder bei denen für **update_mode** die Einstellung **queued failover** festgelegt ist, wird die Seite **Anmeldename für aktualisierbare Abonnements** angezeigt. Geben Sie auf der Seite **Anmeldename für aktualisierbare Abonnements** einen Verbindungsserver an, über den die Verbindungen mit dem Verleger für Abonnements mit sofortigem Update hergestellt werden sollen. Die Verbindungen werden durch die Trigger verwendet, die auf dem Abonnenten ausgelöst werden und die Änderungen zum Verleger weitergeben. Wählen Sie eine der folgenden Optionen aus:

    * **Verbindungsserver erstellen, der mithilfe der SQL Server-Authentifizierung eine Verbindung herstellt.** Wählen Sie diese Option aus, wenn Sie keinen Remoteserver oder Verbindungsserver für die Verbindungen zwischen dem Abonnenten und dem Verleger definiert haben. Die Replikation erstellt dann einen Verbindungsserver für Sie. Das Konto, das Sie angeben, muss bereits auf dem Verleger vorhanden sein.
    * **Vordefinierten Verbindungsserver oder Remoteserver verwenden** Wählen Sie diese Option aus, wenn Sie einen Remoteserver oder Verbindungsserver zwischen dem Abonnenten und dem Verleger mithilfe von [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio oder einer anderen Methode definiert haben.

    Informationen zu den Berechtigungen, die das Verbindungsserverkonto benötigt, finden Sie unter **Abonnements mit verzögertem Update über eine Warteschlange** unter [Hier Linkbeschreibung eingeben](../security/secure-the-subscriber.md).

8. Schließen Sie den Assistenten ab.

## <a name="configure-an-updatable-subscription-from-the-subscriber"></a>Konfigurieren eines aktualisierbaren Abonnements vom Abonnenten aus


1. Stellen Sie mit dem Abonnenten in SQL Server Management Studio eine Verbindung her, und erweitern Sie dann den Serverknoten.
2. Erweitern Sie den Ordner **Replikation** .
3. Klicken Sie mit der rechten Maustaste auf den Ordner **Lokale Abonnements** , und klicken Sie dann auf **Neue Abonnements**.
4. Aktivieren Sie auf der Seite **Veröffentlichung** des **Assistenten für neue Abonnements** in der Dropdownliste **Verleger** die Option **SQL Server-Verleger suchen**.
5. Stellen Sie im Dialogfeld **Verbindung mit Server herstellen** eine Verbindung mit dem Verleger her.
6. Wählen Sie auf der Seite **Veröffentlichung** eine für aktualisierbare Abonnements aktivierte Transaktionsveröffentlichung aus.
7. Geben Sie auf den folgenden Seiten des Assistenten die Optionen für das Abonnement an. Geben Sie dabei z. B. an, wo der Verteilungs-Agent ausgeführt werden soll.
8. Vergewissern Sie sich, dass auf der Seite **aktualisierbare Abonnements** des Assistenten für neue Abonnements **Replizieren** ausgewählt ist.
9. Wählen Sie in der Dropdownliste **Commit auf Verleger ausführen** eine Option aus:

    * Wenn Sie Abonnements mit sofortigem Update verwenden möchten, aktivieren Sie die Option **Commit für Änderungen gleichzeitig ausführen**. Wenn Sie diese Option aktivieren und die Veröffentlichung Abonnements mit verzögertem Update über eine Warteschlange zulässt (Standardkonfiguration bei Veröffentlichungen, die im Assistenten für neue Veröffentlichung erstellt wurden), wird für die **update_mode**-Abonnementeigenschaft **failover** festgelegt. Dieser Modus ermöglicht es Ihnen, bei Bedarf später zum Update über eine Warteschlange zu wechseln.
    * Wenn Sie Abonnements mit verzögertem Update über eine Warteschlange verwenden möchten, aktivieren Sie die Option **Änderungen in die Warteschlange einreihen und Commit baldmöglichst ausführen**. Wenn Sie diese Option aktivieren und die Veröffentlichung Abonnements mit sofortigem Update zulässt (Standard bei Veröffentlichungen, die mit dem Assistenten für neue Veröffentlichung erstellt wurden) und auf dem Abonnenten SQL Server 2005 oder eine höhere Version ausgeführt wird, wird die Eigenschaft "Abonnement" **update_mode** auf ein verzögertes **Failover**festgelegt. Dieser Modus ermöglicht es Ihnen, bei Bedarf später zum sofortigen Update zu wechseln.

    Weitere Informationen zum Umschalten zwischen den Updatemodi finden Sie unter [Umschalten zwischen Updatemodi für ein aktualisierbares Transaktionsabonnement](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

10. Die Seite **Anmeldung für aktualisierbare Abonnements** wird für Abonnements angezeigt, die sofortiges Aktualisieren verwenden oder **update_mode** auf ein verzögertes **Failover**festgelegt haben. Geben Sie auf der Seite **Anmeldename für aktualisierbare Abonnements** einen Verbindungsserver an, über den die Verbindungen mit dem Verleger für Abonnements mit sofortigem Update hergestellt werden sollen. Die Verbindungen werden durch die Trigger verwendet, die auf dem Abonnenten ausgelöst werden und die Änderungen zum Verleger weitergeben. Wählen Sie eine der folgenden Optionen aus:

    * **Verbindungsserver erstellen, der mithilfe der SQL Server-Authentifizierung eine Verbindung herstellt.** Wählen Sie diese Option aus, wenn Sie keinen Remoteserver oder Verbindungsserver für die Verbindungen zwischen dem Abonnenten und dem Verleger definiert haben. Die Replikation erstellt dann einen Verbindungsserver für Sie. Das Konto, das Sie angeben, muss bereits auf dem Verleger vorhanden sein.
    * **Vordefinierten Verbindungsserver oder Remoteserver verwenden** Wählen Sie diese Option aus, wenn Sie einen Remoteserver oder Verbindungsserver zwischen dem Abonnenten und dem Verleger mithilfe von [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio oder einer anderen Methode definiert haben.

    Informationen zu den Berechtigungen, die das Verbindungsserverkonto benötigt, finden Sie unter **Abonnements mit verzögertem Update über eine Warteschlange** unter [Hier Linkbeschreibung eingeben](../security/secure-the-subscriber.md).

11. Schließen Sie den Assistenten ab.

## <a name="create-an-immediate-updating-pull-subscription"></a>Erstellen eines sofort aktualisierbaren Pullabonnements

1. Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Abonnements mit sofortigem Update unterstützt, indem Sie [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)ausführen. 

    * Wenn `allow_sync_tran` im Resultset den Wert `1`hat, unterstützt die Veröffentlichung Abonnements mit sofortigem Update.
    * Wenn `allow_sync_tran` im Resultset den Wert `0`hat, muss die Veröffentlichung erneut erstellt und die Unterstützung von Abonnements mit sofortigem Update aktiviert werden.

2. Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Pullabonnements unterstützt, indem Sie [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)ausführen. 

    * Wenn `allow_pull` im Resultset den Wert `1`hat, unterstützt die Veröffentlichung Pullabonnements.
    * Wenn `allow_pull` den Wert `0`hat, führen Sie [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus, wobei Sie `allow_pull` für `@property` und `true` für `@value`angeben. 

3. Führen Sie auf dem Abonnenten [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)aus. Geben Sie `@publisher` und `@publication`und einen der folgenden Werte für `@update_mode`fest:

    * `sync tran` – Ermöglicht sofortige Updates des Abonnements.
    * `failover` – Ermöglicht das sofortige Aktualisieren für das Abonnement, wobei als Failoveroption das verzögerte Aktualisieren über eine Warteschlange verwendet wird.

    > [!NOTE]  
>  `failover` erfordert, dass die Veröffentlichung auch Abonnements mit verzögertem Aktualisieren über eine Warteschlange zulässt. 
 
4. Führen Sie auf dem Abonnenten [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)aus. Geben Sie Folgendes an:

    * Die Parameter `@publisher`, `@publisher_db`und `@publication` . 
    * Die Microsoft Windows-Anmeldeinformationen, unter denen der Verteilungs-Agent auf dem Abonnenten für `@job_login` und `@job_password`ausgeführt wird. 

    > [!NOTE]  
>  Für Verbindungen, die mit der integrierten Windows-Authentifizierung hergestellt werden, werden immer die mit `@job_login` und `@job_password`angegebenen Windows-Anmeldeinformationen verwendet. Der Verteilungs-Agent stellt die lokale Verbindung mit dem Abonnenten immer mithilfe der integrierten Windows-Authentifizierung her. Standardmäßig stellt der Agent mithilfe der integrierten Windows-Authentifizierung eine Verbindung mit dem Verteiler her. 
 
    * (Optional) Ein Wert von `0` für `@distributor_security_mode` und die Microsoft SQL Server-Anmeldeinformationen für `@distributor_login` und `@distributor_password`, wenn Sie beim Herstellen einer Verbindung zum Verteiler die SQL Server-Authentifizierung verwenden müssen. 
    * Einen Zeitplan für den Verteilungs-Agentauftrag für dieses Abonnement. 

5. Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)aus. Geben Sie `@publisher`, `@publication`, den Namen der Veröffentlichungsdatenbank für `@publisher_db`und einen der folgenden Werte für `@security_mode`an: 

    * `0` – Verwenden Sie die SQL Server-Authentifizierung, wenn Updates beim Verleger vorgenommen werden. Diese Option erfordert auf dem Verleger die Angabe gültiger Anmeldeinformationen für `@login` und `@password`.
    * `1` – Verwenden Sie zum Verbindungsaufbau mit dem Verleger den Sicherheitskontext des Benutzers, der Änderungen am Abonnenten vornimmt. Weitere Informationen zu den in Verbindung mit diesem Sicherheitsmodus geltenden Beschränkungen finden Sie unter [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) .
    * `2` – Verwenden Sie einen vorhandenen benutzerdefinierten Anmeldenamen für den Verbindungsserver, der mit [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)erstellt wurde.

6. Führen Sie [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) auf dem Verleger aus, und geben Sie dabei, `@publication` `@subscriber` , `@destination_db` , den Wert Pull für `@subscription_type` und den in Schritt 3 für angegebenen Wert an `@update_mode` .

Damit wird das Pullabonnement beim Verleger registriert. 


## <a name="create-an-immediate-updating-push-subscription"></a>Erstellen eines sofort aktualisierbaren Pushabonnements 

1. Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Abonnements mit sofortigem Update unterstützt, indem Sie [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)ausführen. 

    * Wenn `allow_sync_tran` im Resultset den Wert `1`hat, unterstützt die Veröffentlichung Abonnements mit sofortigem Update.
    * Wenn `allow_sync_tran` im Resultset den Wert `0`hat, muss die Veröffentlichung erneut erstellt und die Unterstützung von Abonnements mit sofortigem Update aktiviert werden.

2. Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Pushabonnements unterstützt, indem Sie [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)ausführen. 

    * Wenn `allow_push` im Resultset den Wert `1`hat, unterstützt die Veröffentlichung Pushabonnements.
    * Wenn `allow_push` den Wert `0`hat, führen Sie [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus, wobei Sie `allow_push` für `@property` und `true` für `@value`angeben. 

3. Führen Sie auf dem Verleger [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)aus. Geben Sie `@publication`, `@subscriber`, `@destination_db`und einen der folgenden Werte für `@update_mode`fest:

    * `sync tran` – Aktiviert die Unterstützung für sofortige Updates.
    * `failover` – Aktiviert die Unterstützung für sofortige Updates, wobei verzögerte Updates über eine Warteschlange als Failoveroption verwendet werden.

    > [!NOTE]  
>  `failover` erfordert, dass die Veröffentlichung auch Abonnements mit verzögertem Aktualisieren über eine Warteschlange zulässt. 
 
4. Führen Sie auf dem Verleger [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)aus. Geben Sie die folgenden Parameter an:

    * `@subscriber`, `@subscriber_db`und `@publication`. 
    * Die Windows-Anmeldeinformationen, unter denen der Verteilungs-Agent beim Verteiler für `@job_login` und `@job_password`ausgeführt wird. 

    > [!NOTE]  
>  Für Verbindungen, die mit der integrierten Windows-Authentifizierung hergestellt werden, werden immer die mit `@job_login` und `@job_password`angegebenen Windows-Anmeldeinformationen verwendet. Der Verteilungs-Agent stellt die lokale Verbindung mit dem Verteiler immer mithilfe der Windows-Authentifizierung her. Standardmäßig stellt der Agent mithilfe der integrierten Windows-Authentifizierung eine Verbindung mit dem Abonnenten her. 

    * (Optional) Ein Wert von `0` für `@subscriber_security_mode` und die SQL Server-Anmeldeinformationen für `@subscriber_login` und `@subscriber_password`, wenn Sie beim Herstellen einer Verbindung zum Abonnenten die SQL Server-Authentifizierung verwenden müssen. 
    * Einen Zeitplan für den Verteilungs-Agentauftrag für dieses Abonnement.

5. Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)aus. Geben Sie `@publisher`, `@publication`, den Namen der Veröffentlichungsdatenbank für `@publisher_db`und einen der folgenden Werte für `@security_mode`an: 

     * `0` – Verwenden Sie die SQL Server-Authentifizierung, wenn Updates beim Verleger vorgenommen werden. Diese Option erfordert auf dem Verleger die Angabe gültiger Anmeldeinformationen für `@login` und `@password`.
     * `1` – Verwenden Sie zum Verbindungsaufbau mit dem Verleger den Sicherheitskontext des Benutzers, der Änderungen am Abonnenten vornimmt. Weitere Informationen zu den in Verbindung mit diesem Sicherheitsmodus geltenden Beschränkungen finden Sie unter [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) .
     * `2` – Verwenden Sie einen vorhandenen benutzerdefinierten Anmeldenamen für den Verbindungsserver, der mit [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)erstellt wurde.


## <a name="create-a-queued-updating-pull-subscription"></a>Erstellen eines Pullabonnements mit verzögertem Update über eine Warteschlange ##

1. Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Abonnements mit verzögertem Update über eine Warteschlange unterstützt, indem Sie [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)ausführen. 

    * Wenn `allow_queued_tran` im Resultset den Wert `1`hat, unterstützt die Veröffentlichung Abonnements mit sofortigem Update.
    * Wenn `allow_queued_tran` im Resultset den Wert `0`hat, muss die Veröffentlichung erneut erstellt und die Unterstützung von Abonnements mit verzögertem Update über eine Warteschlange aktiviert werden.

2. Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Pullabonnements unterstützt, indem Sie [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)ausführen. 

    * Wenn `allow_pull` im Resultset den Wert `1`hat, unterstützt die Veröffentlichung Pullabonnements.
    * Wenn `allow_pull` den Wert `0`hat, führen Sie [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus, wobei Sie `allow_pull` für `@property` und `true` für `@value`angeben. 

3. Führen Sie auf dem Abonnenten [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)aus. Geben Sie `@publisher` und `@publication`und einen der folgenden Werte für `@update_mode`fest:

    * `queued tran` – Aktiviert das verzögerte Update über eine Warteschlange für das Abonnement.
    * `queued failover` – Aktiviert die Unterstützung für verzögerte Updates über eine Warteschlange, wobei sofortige Updates als Failoveroption verwendet werden.

    > [!NOTE]  
>  `queued failover` erfordert, dass die Veröffentlichung auch Abonnements mit sofortigem Update zulässt. Damit im Fehlerfall sofortige Updates durchgeführt werden können, müssen Sie unter Verwendung von [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) die Anmeldeinformationen definieren, unter denen Änderungen am Abonnenten auf dem Verleger repliziert werden sollen.
 
4. Führen Sie auf dem Abonnenten [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)aus. Geben Sie die folgenden Parameter an:

    * @publisher, `@publisher_db`und `@publication`. 
    * Die Windows-Anmeldeinformationen, unter denen der Verteilungs-Agent auf dem Abonnenten für `@job_login` und `@job_password`ausgeführt wird. 

    > [!NOTE]  
>  Für Verbindungen, die mit der integrierten Windows-Authentifizierung hergestellt werden, werden immer die mit `@job_login` und `@job_password`angegebenen Windows-Anmeldeinformationen verwendet. Der Verteilungs-Agent stellt die lokale Verbindung mit dem Abonnenten immer mithilfe der integrierten Windows-Authentifizierung her. Standardmäßig stellt der Agent mithilfe der integrierten Windows-Authentifizierung eine Verbindung mit dem Verteiler her. 
 
    * (Optional) Ein Wert von `0` für `@distributor_security_mode` und die SQL Server-Anmeldeinformationen für `@distributor_login` und `@distributor_password`, wenn Sie beim Herstellen einer Verbindung zum Verteiler die SQL Server-Authentifizierung verwenden müssen. 
    * Einen Zeitplan für den Verteilungs-Agentauftrag für dieses Abonnement.

5. Führen Sie auf dem Verleger [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) aus, um den Abonnenten auf dem Verleger zu registrieren, und geben Sie dabei, `@publication` `@subscriber` , `@destination_db` , den Wert Pull für `@subscription_type` und den gleichen Wert an, der in Schritt 3 für angegeben wurde `@update_mode` .

Damit wird das Pullabonnement beim Verleger registriert. 


## <a name="to-create-a-queued-updating-push-subscription"></a>So erstellen Sie ein Pushabonnement mit verzögertem Update über eine Warteschlange ##

1. Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Abonnements mit verzögertem Update über eine Warteschlange unterstützt, indem Sie [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)ausführen. 

    * Wenn „allow_queued_tran“ im Resultset den Wert 1 hat, unterstützt die Veröffentlichung Abonnements mit sofortigem Update.
    * Wenn „allow_queued_tran“ im Resultset den Wert 0 hat, muss die Veröffentlichung erneut erstellt und die Unterstützung von Abonnements mit verzögertem Update über eine Warteschlange aktiviert werden. Weitere Informationen finden Sie unter „Gewusst wie: Aktivieren von aktualisierbaren Abonnements für Transaktionsveröffentlichungen (Replikationsprogrammierung mit Transact-SQL)“.

2. Überprüfen Sie auf dem Verleger, ob die Veröffentlichung Pushabonnements unterstützt, indem Sie [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)ausführen. 

    * Wenn `allow_push` im Resultset den Wert `1`hat, unterstützt die Veröffentlichung Pushabonnements.
    * Wenn `allow_push` den Wert `0`hat, führen Sie [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus, wobei Sie „allow_push“ für `@property` und `true` für `@value`angeben. 

3. Führen Sie auf dem Verleger [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)aus. Geben Sie `@publication`, `@subscriber`, `@destination_db`und einen der folgenden Werte für `@update_mode`fest:

    * `queued tran` – Aktiviert das verzögerte Update über eine Warteschlange für das Abonnement.
    * `queued failover` – Aktiviert die Unterstützung für verzögerte Updates über eine Warteschlange, wobei sofortige Updates als Failoveroption verwendet werden.

    > [!NOTE]  
>  Die Option „queued failover“ erfordert, dass die Veröffentlichung auch Abonnements mit sofortigem Update zulässt. Damit im Fehlerfall sofortige Updates durchgeführt werden können, müssen Sie unter Verwendung von [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) die Anmeldeinformationen definieren, unter denen Änderungen am Abonnenten auf dem Verleger repliziert werden sollen.

4. Führen Sie auf dem Verleger [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)aus. Geben Sie die folgenden Parameter an:

    * `@subscriber`, `@subscriber_db`und `@publication`. 
    * Die Windows-Anmeldeinformationen, unter denen der Verteilungs-Agent beim Verteiler für `@job_login` und `@job_password`ausgeführt wird. 

    > [!NOTE]  
>  Für Verbindungen, die mit der integrierten Windows-Authentifizierung hergestellt werden, werden immer die mit `@job_login` und `@job_password`angegebenen Windows-Anmeldeinformationen verwendet. Der Verteilungs-Agent stellt die lokale Verbindung mit dem Verteiler immer mithilfe der Windows-Authentifizierung her. Standardmäßig stellt der Agent mithilfe der integrierten Windows-Authentifizierung eine Verbindung mit dem Abonnenten her. 
 
    * (Optional) Ein Wert von `0` für `@subscriber_security_mode` und die SQL Server-Anmeldeinformationen für `@subscriber_login` und `@subscriber_password`, wenn Sie beim Herstellen einer Verbindung zum Abonnenten die SQL Server-Authentifizierung verwenden müssen. 
    * Einen Zeitplan für den Verteilungs-Agentauftrag für dieses Abonnement.


## <a name="example"></a>Beispiel ##

In diesem Beispiel wird ein sofort aktualisierbares Abonnement für eine Veröffentlichung erstellt, die Abonnements mit sofortigem Update unterstützt. Die Werte für den Anmeldenamen und das Kennwort werden zur Laufzeit mithilfe von sqlcmd-Skriptvariablen bereitgestellt.

> [!NOTE]  
>  Dieses Skript verwendet „sqlcmd“-Skriptvariablen. Sie weisen das Format `$(MyVariable)`auf. Informationen zur Verwendung von Skriptvariablen in der Befehlszeile und in SQL Server Management Studio finden Sie im Abschnitt **Ausführen von Replikationsskripts** im Thema [Konzepte für gespeicherte Systemprozeduren für die Replikation](../concepts/replication-system-stored-procedures-concepts.md).

```sql
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>Festlegen der Konfliktlösungsoptionen für verzögerte Updates über eine Warteschlange (SQL Server Management Studio)
  Legen Sie im Dialogfeld **Veröffentlichungs Eigenschaften- \<Publication> ** für Veröffentlichungen, die Abonnements mit verzögertem Update über eine Warteschlange unterstützen, Optionen **für die Konflikt** Auflösung fest. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>So legen Sie die Konfliktlösungsoptionen für das verzögerte Update über eine Warteschlange fest  
  
1.  Wählen Sie auf der Seite **Abonnementoptionen** des Dialog Felds **Veröffentlichungs Eigenschaften- \<Publication> ** für die Option **Richtlinie zur Konfliktlösung** einen der folgenden Werte aus:    
    -   **Verlegeränderung beibehalten**    
    -   **Abonnentenänderung beibehalten**    
    -   **Erneutes Initialisieren des Abonnements**    
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="see-also"></a>Weitere Informationen ##
 [Create a Publication](create-a-publication.md)   
 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Verwenden von sqlcmd mit Skriptvariablen](../../scripting/sqlcmd-use-with-scripting-variables.md)   

  
