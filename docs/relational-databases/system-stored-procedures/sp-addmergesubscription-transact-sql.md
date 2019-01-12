---
title: Sp_addmergesubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergesubscription_TSQL
- sp_addmergesubscription
helpviewer_keywords:
- sp_addmergesubscription
ms.assetid: a191d817-0132-49ff-93ca-76f13e609b38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c3341c37998f61cba743c8da8a4cd772c2c73d9
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54133760"
---
# <a name="spaddmergesubscription-transact-sql"></a>sp_addmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt ein Mergepushabonnement oder ein Mergepullabonnement. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergesubscription [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @subscriber_type= ] 'subscriber_type' ]  
    [ , [ @subscription_priority= ] subscription_priority ]  
    [ , [ @sync_type= ] 'sync_type' ]  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @optional_command_line= ] 'optional_command_line' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @enabled_for_syncmgr= ] 'enabled_for_syncmgr' ]  
    [ , [ @offloadagent= ] remote_agent_activation]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @use_interactive_resolver= ] 'use_interactive_resolver' ]  
    [ , [ @merge_job_name= ] 'merge_job_name' ]  
    [ , [ @hostname = ] 'hostname'  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=**] **"**_Veröffentlichung_**"**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert. Die Veröffentlichung muss bereits vorhanden sein.  
  
 [  **@subscriber =**] **"**_Abonnenten_**"**  
 Der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@subscriber_db=**] **"**_Subscriber_db_**"**  
 Ist der Name der Abonnementdatenbank. *Subscriber_db*ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@subscription_type=**] **"**_Subscription_type_**"**  
 Ist der Typ des Abonnements. *Subscription_type*ist **nvarchar(15)**, hat den Standardwert PUSH. Wenn **Push**, wird ein Pushabonnement hinzugefügt, und der Merge-Agent auf dem Verteiler hinzugefügt. Wenn **Pull**, ein Pullabonnement wird hinzugefügt, ohne dass ein Merge-Agent auf dem Verteiler hinzugefügt.  
  
> [!NOTE]  
>  Für anonyme Abonnements ist diese gespeicherte Prozedur nicht erforderlich.  
  
 [  **@subscriber_type=**] **"**_Subscriber_type_**"**  
 Der Typ des Abonnenten. *subscriber_type kann*ist **nvarchar(15)**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**lokale** (Standard)|Der Abonnent ist nur dem Verleger bekannt.|  
|**Globale**|Der Abonnent ist allen Servern bekannt.|  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen werden lokale Abonnements als "Clientabonnements" und globale Abonnements als "Serverabonnements" bezeichnet.  
  
 [  **@subscription_priority=**] *Subscription_priority*  
 Eine Zahl, die die Priorität für das Abonnement angibt. *Subscription_priority*ist **echte**, hat den Standardwert NULL. Für lokale und anonyme Abonnements ist die Priorität 0,0. Für globale Abonnements muss die Priorität niedriger als 100,0 sein.  
  
 [  **@sync_type=**] **"**_Sync_type_**"**  
 Der Synchronisierungstyp des Abonnements. *Sync_type*ist **nvarchar(15)**, hat den Standardwert **automatische**. Kann **automatische** oder **keine**. Wenn **automatische**, das Schema und die Ausgangsdaten für veröffentlichte Tabellen zuerst an den Abonnenten übertragen werden. Wenn **keine**, es wird davon ausgegangen, dass der Abonnent hat bereits das Schema und die Ausgangsdaten für veröffentlichte Tabellen. Systemtabellen und Daten werden immer übertragen.  
  
> [!NOTE]  
>  Es wird empfohlen, keine Angabe des Werts **keine**.  
  
 [  **@frequency_type=**] *Frequency_type*  
 Ein Wert, der angibt, wann der Merge-Agent ausgeführt wird. *Frequency_type* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**10**|Monatlicher Zeitplan|  
|**20**|Monatlich, relativ zum Häufigkeitsintervall|  
|**40**|Beim Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents|  
|NULL (Standard)||  
  
 [  **@frequency_interval=**] *Frequency_interval*  
 Die Tage, an denen der Merge-Agent ausgeführt wird. *Frequency_interval* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Sonntag|  
|**2**|Montag|  
|**3**|Dienstag|  
|**4**|Mittwoch|  
|**5**|Donnerstag|  
|**6**|Freitag|  
|**7**|Samstag|  
|**8**|Day|  
|**9**|Wochentage|  
|**10**|Wochenendtage|  
|NULL (Standard)||  
  
 [  **@frequency_relative_interval=**] *Frequency_relative_interval*  
 Die geplante Ausführung von Mergevorgängen mit dem Häufigkeitsintervall in jedem Monat. *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
|NULL (Standard)||  
  
 [  **@frequency_recurrence_factor=**] *Frequency_recurrence_factor*  
 Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor*ist **Int**, hat den Standardwert NULL.  
  
 [  **@frequency_subday=**] *Frequency_subday*  
 Die Einheit für *Frequency_subday_interval*. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (Standard)||  
  
 [  **@frequency_subday_interval=**] *Frequency_subday_interval*  
 Die Häufigkeit von *Frequency_subday* zwischen jedem Mergevorgang ausgeführt. *Frequency_subday_interval* ist **Int**, hat den Standardwert NULL.  
  
 [  **@active_start_time_of_day=**] *Active_start_time_of_day*  
 Die Tageszeit, zu der der Merge-Agent zum ersten Mal geplant ist. Dabei wird das Format HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert NULL.  
  
 [  **@active_end_time_of_day=**] *Active_end_time_of_day*  
 Die Tageszeit, ab der der Merge-Agent nicht mehr geplant ist. Dabei wird das Format HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert NULL.  
  
 [  **@active_start_date=**] *Active_start_date*  
 Das Datum, an dem der Merge-Agent zum ersten Mal geplant ist. Dabei wird das Format JJJJMMTT verwendet. *Active_start_date* ist **Int**, hat den Standardwert NULL.  
  
 [  **@active_end_date=**] *Active_end_date*  
 Das Datum, ab dem der Merge-Agent nicht mehr geplant ist. Dabei wird das Format JJJJMMTT verwendet. *Active_end_date* ist **Int**, hat den Standardwert NULL.  
  
 [  **@optional_command_line=**] **"**_Standardwert_**"**  
 Die optional auszuführende Befehlszeile. *Der Standardwert*ist **nvarchar(4000)**, hat den Standardwert NULL. Dieser Parameter wird verwendet, um einen Befehl hinzuzufügen, der die Ausgabe aufzeichnet und in einer Datei speichert, oder um eine Konfigurationsdatei oder ein Konfigurationsattribut anzugeben.  
  
 [  **@description=**] **"**_Beschreibung_**"**  
 Eine kurze Beschreibung dieses Mergeabonnements. *Beschreibung*ist **nvarchar(255)**, hat den Standardwert NULL. Dieser Wert wird angezeigt, vom Replikationsmonitor in der **Anzeigenamen** Spalte, die zum Sortieren von Abonnements für eine überwachte Veröffentlichung verwendet werden kann.  
  
 [  **@enabled_for_syncmgr=**] **"**_Enabled_for_syncmgr_**"**  
 Gibt an, ob das Abonnement über die Synchronisierungsverwaltung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows synchronisiert werden kann. *Enabled_for_syncmgr* ist **nvarchar(5)**, hat den Standardwert "false". Wenn **"false"**, das Abonnement ist nicht mit der Synchronisierungsverwaltung registriert. Wenn **"true"**, das Abonnement mit der Synchronisierungsverwaltung registriert und kann synchronisiert werden, ohne Starten des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 [  **@offloadagent=** ] *Remote_agent_activation*  
 Gibt an, dass eine Remoteaktivierung der Momentaufnahme möglich ist. *Remote_agent_activation* ist **Bit** hat den Standardwert **0**.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird nur noch bereitgestellt, um Abwärtskompatibilität von Skripts sicherzustellen.  
  
 [  **@offloadserver=** ] **"**_Remote_agent_server_name_**"**  
 Gibt den Netzwerknamen des Servers an, auf dem die Remoteaktivierung der Momentaufnahme erfolgt. *Remote_agent_server_name*ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@use_interactive_resolver=** ] **"**_Use_interactive_resolver_**"**  
 Ermöglicht das interaktive Lösen von Konflikten für alle Artikel, die eine interaktive Auflösung zulassen. *Use_interactive_resolver* ist **nvarchar(5)**, hat den Standardwert "false".  
  
 [  **@merge_job_name=** ] **"**_Merge_job_name_**"**  
 Die *@merge_job_name* -Parameter ist veraltet und kann nicht festgelegt werden. *Merge_job_name* ist **Sysname**, hat den Standardwert NULL.  
  
 [ **@hostname**=] **"**_Hostname_**"**  
 Überschreibt den Rückgabewert von [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) Wenn diese Funktion in der WHERE-Klausel eines parametrisierten Filters verwendet wird. *Hostname* ist **Sysname**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Aus Leistungsgründen wird empfohlen, keine Funktionen auf Spaltennamen in parametrisierten Zeilenfilterklauseln (beispielsweise `LEFT([MyColumn]) = SUSER_SNAME()`) anzuwenden. Bei Verwendung von [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) in einer Filterklausel verwenden und den Wert HOST_NAME überschreiben, ist es möglicherweise erforderlich, um Konvertieren von Datentypen mithilfe von [konvertieren](../../t-sql/functions/cast-and-convert-transact-sql.md). Weitere Informationen zu bewährten Methoden für diesen Fall finden Sie im Abschnitt über das Überschreiben des HOST_NAME()-Werts im Thema [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addmergesubscription** wird bei der Mergereplikation verwendet.  
  
 Wenn **Sp_addmergesubscription** ausgeführt wird, von einem Mitglied der **Sysadmin** feste Serverrolle, um ein Pushabonnement zu erstellen, der Merge-Agent-Auftrag implizit erstellt und ausgeführt wird, klicken Sie unter der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Dienstkonto. Es wird empfohlen, die Sie ausführen [Sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) und geben Sie die Anmeldeinformationen eines anderen, Agent-spezifischen Windows-Kontos für **@job_login** und **@job_password**. Weitere Informationen finden Sie unter [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergesubscription-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addmergesubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Interaktive Konfliktlösung](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [Sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [Sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [Sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
