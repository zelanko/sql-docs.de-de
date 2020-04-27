---
title: Aktualisieren von Replikationsskripts (Replikationsprogrammierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- scripts [SQL Server replication], upgrading
- upgrading SQL Server, replicated databases
- upgrading replication applications
- replication [SQL Server], scripting
- replication [SQL Server], upgrading
- upgrading replicated databases
ms.assetid: 0b8720bd-f339-4842-bc8f-b35a46f6d3ee
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cd3f6498cbfb4ef8cf38e27879d619472a6693ce
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68210764"
---
# <a name="upgrade-replication-scripts-replication-transact-sql-programming"></a>Aktualisieren von Replikationsskripts (Replikationsprogrammierung mit Transact-SQL)
  Mithilfe von[!INCLUDE[tsql](../../../includes/tsql-md.md)] -Skriptdateien kann eine Replikationstopologie programmgesteuert konfiguriert werden. Weitere Informationen finden Sie unter [Replikationskonzepte für gespeicherte Systemprozeduren](../concepts/replication-system-stored-procedures-concepts.md).  
  
> [!IMPORTANT]  
>  Skripts, die von Mitgliedern der `sysadmin`-Rolle ausgeführt werden, müssen nicht aktualisiert werden. Dennoch empfiehlt es sich, vorhandene Skripts wie in diesem Thema beschrieben zu ändern. Geben Sie ein Konto mit Mindestberechtigungen für jeden Replikations-Agent an, wie im Abschnitt zu den für die Agents erforderlichen Berechtigungen im Thema [Replication Agent Security Model](../security/replication-agent-security-model.md)beschrieben.  
  
 Diese Sicherheitsverbesserungen, die Ihnen mehr Kontrolle über Berechtigungen bieten, indem Sie explizit die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Konten angeben können, unter denen Replikations-Agentaufträge ausgeführt werden, wirken sich auf die folgenden gespeicherten Prozeduren in vorhandenen Skripts aus:  
  
-   **sp_addpublication_snapshot**:  
  
     Sie sollten nun die Windows-Anmelde Informationen **@job_login** als **@job_password** und angeben, wenn Sie [sp_addpublication_snapshot &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) ausführen, um den Auftrag zu erstellen, unter dem der Momentaufnahmen-Agent auf dem Verteiler ausgeführt wird.  
  
-   **sp_addpushsubscription_agent**:  
  
     Sie sollten nun [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql) ausführen, um explizit einen Auftrag hinzuzufügen, und die Windows-Anmeldeinformationen (**@job_login** und **@job_password**) anzugeben, unter denen der Auftrag des Verteilungs-Agents auf dem Verteiler ausgeführt wird. In Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]wurde dieser Vorgang automatisch beim Erstellen eines Pushabonnements ausgeführt.  
  
-   **sp_addmergepushsubscription_agent**:  
  
     Sie sollten nun [sp_addmergepushsubscription_agent &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql) ausführen, um explizit einen Auftrag hinzuzufügen und die Windows**@job_login** - **@job_password**Anmelde Informationen (und) anzugeben, unter denen der Merge-Agent Auftrag auf dem Verteiler ausgeführt wird. In Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]wurde dieser Vorgang automatisch beim Erstellen eines Pushabonnements ausgeführt.  
  
-   **sp_addpullsubscription_agent**:  
  
     Sie sollten nun die Windows-Anmelde Informationen **@job_login** als **@job_password** und angeben, wenn Sie [sp_addpullsubscription_agent &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) ausführen, um den Auftrag zu erstellen, unter dem der Verteilungs-Agent auf dem Abonnenten ausgeführt wird.  
  
-   **sp_addmergepullsubscription_agent**:  
  
     Sie sollten nun die Windows-Anmelde Informationen **@job_login** als **@job_password** und angeben, wenn Sie [sp_addmergepullsubscription_agent &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql) ausführen, um den Auftrag zu erstellen, unter dem der Merge-Agent auf dem Abonnenten ausgeführt wird.  
  
-   **sp_addlogreader_agent**:  
  
     Sie sollten nun [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) ausführen, um den Auftrag manuell hinzuzufügen, und die Windows-Anmeldeinformationen anzugeben, unter denen der Protokolllese-Agent auf dem Verteiler ausgeführt wird. In Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]wurde dieser Vorgang automatisch beim Erstellen einer Transaktionsveröffentlichung ausgeführt.  
  
-   **sp_addqreader_agent**:  
  
     Sie sollten nun [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) ausführen, um den Auftrag manuell hinzuzufügen, und die Windows-Anmeldeinformationen anzugeben, unter denen der Warteschlangenlese-Agent auf dem Verteiler ausgeführt wird. In Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]wurde dieser Vorgang automatisch beim Erstellen einer Transaktionsveröffentlichung mit Unterstützung des verzögerten Aktualisierens ausgeführt.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]In dem in eingeführten Sicherheitsmodell stellen Replikations-Agents Verbindungen mit der lokalen Instanz [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von immer mit der Windows-Authentifizierung her **@job_name** . **@job_password**dabei werden die in und angegebenen Anmelde Informationen verwendet. Informationen zu den Anforderungen für beim Ausführen von Replikations-Agentaufträgen verwendeten Windows-Konten finden Sie unter [Replication Agent Security Model](../security/replication-agent-security-model.md).  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden, müssen Sie sicherstellen, dass die Datei geschützt ist.  
  
### <a name="to-upgrade-scripts-that-configure-a-snapshot-or-transactional-publication"></a>So aktualisieren Sie Skripts, mit denen eine Momentaufnahme- oder eine Transaktionsveröffentlichung konfiguriert werden  
  
1.  Führen Sie im vorhandenen Skript [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) vor [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie die Windows-Anmelde Informationen an, unter **@job_name** denen **@job_password**die Protokolllese-Agent für und ausgeführt wird. Wenn der Agent zum Herstellen der Verbindung mit dem Verleger die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung verwendet, müssen Sie zudem den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**. Dadurch wird ein Auftrag des Protokolllese-Agents für die Veröffentlichungsdatenbank erstellt.  
  
    > [!NOTE]  
    >  Dieser Schritt muss nur bei Transaktionsveröffentlichungen, nicht bei Momentaufnahmeveröffentlichungen ausgeführt werden.  
  
2.  (Optional) Führen Sie [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) vor [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) auf dem Verteiler für die Verteilungsdatenbank aus. Geben Sie die Windows-Anmelde Informationen an, unter **@job_name** denen **@job_password**die Warteschlangenlese-Agent für und ausgeführt wird. Dadurch wird ein Auftrag des Warteschlangenlese-Agents für den Verteiler erstellt.  
  
    > [!NOTE]  
    >  Dieser Schritt muss nur bei Transaktionsveröffentlichungen ausgeführt werden, die Abonnenten mit verzögertem Update über eine Warteschlange unterstützen.  
  
3.  (Optional) Aktualisieren Sie die Ausführung von [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), um alle Nichtstandardwerte für Parameter festzulegen, die neue Replikationsfunktionen implementieren.  
  
4.  Führen Sie nach [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)[sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben **@publication** Sie und die Windows-Anmelde Informationen an, unter **@job_name** denen **@job_password**die Momentaufnahmen-Agent für und ausgeführt wird. Wenn der Agent zum Herstellen der Verbindung mit dem Verleger die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung verwendet, müssen Sie zudem den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**. Dadurch wird ein Auftrag des Momentaufnahme-Agents für die Veröffentlichung erstellt.  
  
5.  (Optional) Aktualisieren Sie die Ausführung von [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql), um alle Nichtstandardwerte für Parameter festzulegen, die neue Replikationsfunktionen implementieren.  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-snapshot-or-transactional-publication"></a>So aktualisieren Sie Skripts, mit denen einer Momentaufnahme- oder Transaktionsveröffentlichung Abonnements hinzugefügt werden  
  
1.  Nach dem Ausführen der gespeicherten Prozedur, mit der das Abonnement erstellt wird, müssen Sie die gespeicherte Prozedur ausführen, mit der der Auftrag des Verteilungs-Agents erstellt wird, damit das Abonnement synchronisiert wird. Welche gespeicherte Prozedur Sie verwenden, hängt vom Typ des Abonnements ab.  
  
    -   Aktualisieren Sie bei einem Pullabonnement die Ausführung von [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql), um die Windows-Anmeldeinformationen bereitzustellen, unter denen der Verteilungs-Agent auf dem Abonnenten für **@job_name** und **@job_password** ausgeführt wird. Dies geschieht nach der Ausführung von [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). Weitere Informationen finden Sie unter [Create a Pull Subscription](../create-a-pull-subscription.md).  
  
    -   Führen Sie [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql) für ein Pushabonnement auf dem Verleger aus. Geben **@subscriber**Sie **@subscriber_db**, **@publication**,, Windows-Anmelde Informationen, unter denen die Verteilungs-Agent auf **@job_name** dem **@job_password**Verteiler für und ausgeführt wird, sowie einen Zeitplan für diesen Agentauftrag an. Weitere Informationen finden Sie unter [Angeben von Synchronisierungs Zeitplänen](../specify-synchronization-schedules.md). Dies geschieht nach der Ausführung von [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Weitere Informationen finden Sie unter [Create a Push Subscription](../create-a-push-subscription.md).  
  
### <a name="to-upgrade-scripts-that-configure-a-merge-publication"></a>So aktualisieren Sie Skripts, mit denen eine Mergeveröffentlichung konfiguriert wird  
  
1.  (Optional) Aktualisieren Sie im vorhandenen Skript die Ausführung von [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), um alle Nichtstandardwerte für Parameter festzulegen, die neue Replikationsfunktionen implementieren.  
  
2.  Führen Sie nach [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)[sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben **@publication** Sie und die Windows-Anmelde Informationen an, unter **@job_name** denen **@job_password**die Momentaufnahmen-Agent für und ausgeführt wird. Wenn der Agent zum Herstellen der Verbindung mit dem Verleger die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung verwendet, müssen Sie zudem den Wert **0** für **@publisher_security_mode** und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldeinformationen für **@publisher_login** und **@publisher_password**. Dadurch wird ein Auftrag des Momentaufnahme-Agents für die Veröffentlichung erstellt.  
  
3.  (Optional) Aktualisieren Sie die Ausführung von [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), um alle Nichtstandardwerte für Parameter festzulegen, die neue Replikationsfunktionen implementieren.  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-merge-publication"></a>So aktualisieren Sie Skripts, mit denen einer Mergeveröffentlichung Abonnements hinzugefügt werden  
  
1.  Nach dem Ausführen der gespeicherten Prozedur, mit der das Abonnement erstellt wird, müssen Sie die gespeicherte Prozedur ausführen, mit der der Auftrag des Merge-Agents erstellt wird, damit das Abonnement synchronisiert wird. Welche gespeicherte Prozedur Sie verwenden, hängt vom Typ des Abonnements ab.  
  
    -   Aktualisieren Sie bei einem Pullabonnement die Ausführung von [sp_addmergepullsubscription_agent &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql) , um die Windows-Anmelde Informationen bereitzustellen, **@job_name** unter **@job_password**denen die Merge-Agent auf dem Abonnenten für und ausgeführt wird. Dies geschieht nach der Ausführung von [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql). Weitere Informationen finden Sie unter [Create a Pull Subscription](../create-a-pull-subscription.md).  
  
    -   Führen Sie für ein Pushabonnement [sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql) auf dem Verleger aus. Geben **@subscriber**Sie **@subscriber_db**, **@publication**,, die Windows-Anmelde Informationen, unter denen die Merge-Agent auf **@job_name** dem **@job_password**Verteiler ausgeführt wird, für und und einen Zeitplan für diesen Agentauftrag an. Weitere Informationen finden Sie unter [Angeben von Synchronisierungs Zeitplänen](../specify-synchronization-schedules.md). Dies geschieht nach der Ausführung von [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql). Weitere Informationen finden Sie unter [Create a Push Subscription](../create-a-push-subscription.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] -Skript dargestellt, mit dem eine Transaktionsveröffentlichung für die Product-Tabelle erstellt wird. Diese Veröffentlichung unterstützt sofortige Updates mit Updates über eine Warteschlange als Failover. Standardparameter wurden zwecks besserer Lesbarkeit entfernt.  
  
 [!code-sql[HowTo#sp_createtranpub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpub80.sql#sp_createtranpub_nwpreupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Aktualisierung des vorherigen Skripts dargestellt, mit dem eine Transaktionsveröffentlichung erstellt wird, damit es unter [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und späteren Versionen erfolgreich ausgeführt werden kann. Diese Veröffentlichung unterstützt sofortige Updates mit Updates über eine Warteschlange als Failover. Standardwerte für neue Parameter wurden explizit deklariert.  
  
> [!NOTE]  
>   Windows-Anmeldeinformationen werden zur Laufzeit mithilfe von **sqlcmd** -Skriptvariablen angegeben.  
  
 [!code-sql[HowTo#sp_createtranpub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpublication.sql#sp_createtranpub_nwpostupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] -Skript dargestellt, mit dem eine Mergeveröffentlichung für die Customers-Tabelle erstellt wird. Standardparameter wurden zwecks besserer Lesbarkeit entfernt.  
  
 [!code-sql[HowTo#sp_createmergepub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepub80.sql#sp_createmergepub_nwpreupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das vorherige Skript dargestellt, mit dem eine Mergeveröffentlichung erstellt wird und das aktualisiert wurde, damit es unter [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und späteren Versionen erfolgreich ausgeführt werden kann. Standardwerte für neue Parameter wurden explizit deklariert.  
  
> [!NOTE]  
>   Windows-Anmeldeinformationen werden zur Laufzeit mithilfe von **sqlcmd** -Skriptvariablen angegeben.  
  
 [!code-sql[HowTo#sp_createmergepub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepublication.sql#sp_createmergepub_nwpostupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] -Skript dargestellt, mit dem ein Pushabonnement für eine Transaktionsveröffentlichung erstellt wird. Standardparameter wurden zwecks besserer Lesbarkeit entfernt.  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpushsub80.sql#sp_createtranpushsub_nwpreupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Aktualisierung des vorherigen Skripts dargestellt, mit dem ein Pushabonnement für eine Transaktionsveröffentlichung erstellt wird und das aktualisiert wurde, damit es unter [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und späteren Versionen erfolgreich ausgeführt werden kann. Standardwerte für neue Parameter wurden explizit deklariert.  
  
> [!NOTE]  
>   Windows-Anmeldeinformationen werden zur Laufzeit mithilfe von **sqlcmd** -Skriptvariablen angegeben.  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpushsub.sql#sp_createtranpushsub_nwpostupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] -Skript dargestellt, mit dem ein Pushabonnement für eine Mergeveröffentlichung erstellt wird. Standardparameter wurden zwecks besserer Lesbarkeit entfernt.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepushsub80.sql#sp_createmergepushsub_nwpreupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Aktualisierung des vorherigen Skripts dargestellt, mit dem ein Pushabonnement für eine Mergeveröffentlichung erstellt wird und das aktualisiert wurde, damit es unter [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und späteren Versionen erfolgreich ausgeführt werden kann. Standardwerte für neue Parameter wurden explizit deklariert.  
  
> [!NOTE]  
>   Windows-Anmeldeinformationen werden zur Laufzeit mithilfe von **sqlcmd** -Skriptvariablen angegeben.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpushsub.sql#sp_createmergepushsub_nwpostupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] -Skript dargestellt, mit dem ein Pullabonnement für eine Transaktionsveröffentlichung erstellt wird. Standardparameter wurden zwecks besserer Lesbarkeit entfernt.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepushsub80.sql#sp_createmergepushsub_nwpreupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Aktualisierung des vorherigen Skripts dargestellt, mit dem ein Pullabonnement für eine Transaktionsveröffentlichung erstellt wird und das aktualisiert wurde, damit es unter [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und späteren Versionen erfolgreich ausgeführt werden kann. Standardwerte für neue Parameter wurden explizit deklariert.  
  
> [!NOTE]  
>   Windows-Anmeldeinformationen werden zur Laufzeit mithilfe von **sqlcmd** -Skriptvariablen angegeben.  
  
 [!code-sql[HowTo#sp_createtranpullsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpullsub.sql#sp_createtranpullsub_nwpostupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] -Skript dargestellt, mit dem ein Pullabonnement für eine Mergeveröffentlichung erstellt wird. Standardparameter wurden zwecks besserer Lesbarkeit entfernt.  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepullsub80.sql#sp_createmergepullsub_nwpreupgrade)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Aktualisierung des vorherigen Skripts dargestellt, mit dem ein Pullabonnement für eine Mergeveröffentlichung erstellt wird und das aktualisiert wurde, damit es unter [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und späteren Versionen erfolgreich ausgeführt werden kann. Standardwerte für neue Parameter wurden explizit deklariert.  
  
> [!NOTE]  
>   Windows-Anmeldeinformationen werden zur Laufzeit mithilfe von **sqlcmd** -Skriptvariablen angegeben.  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpullsub.sql#sp_createmergepullsub_nwpostupgrade)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](../publish/create-a-publication.md)   
 [Erstellen eines Pushabonnements](../create-a-push-subscription.md)   
 [Create a Pull Subscription](../create-a-pull-subscription.md)   
 [Anzeigen und Ändern von Replikations Sicherheitseinstellungen](../security/view-and-modify-replication-security-settings.md)   
 [MSSQL_ENG021797](../mssql-eng021797.md)   
 [MSSQL_ENG021798](../mssql-eng021798.md)   
 [Konzepte für gespeicherte System Prozeduren von](../concepts/replication-system-stored-procedures-concepts.md)   
 [Aktualisieren von replizierten Datenbanken](../../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
