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
ms.openlocfilehash: 639c090f1c133183dc4b864a3e0215e4c64b6773
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493012"
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
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert. Die Veröffentlichung muss bereits vorhanden sein.  
  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` Ist der Name der Abonnementdatenbank. *Subscriber_db*ist **Sysname**, hat den Standardwert NULL.  
  
`[ @subscription_type = ] 'subscription_type'` Ist der Typ des Abonnements. *Subscription_type*ist **nvarchar(15)**, hat den Standardwert PUSH. Wenn **Push**, wird ein Pushabonnement hinzugefügt, und der Merge-Agent auf dem Verteiler hinzugefügt. Wenn **Pull**, ein Pullabonnement wird hinzugefügt, ohne dass ein Merge-Agent auf dem Verteiler hinzugefügt.  
  
> [!NOTE]  
>  Für anonyme Abonnements ist diese gespeicherte Prozedur nicht erforderlich.  
  
`[ @subscriber_type = ] 'subscriber_type'` Ist der Typ des Abonnenten. *subscriber_type kann*ist **nvarchar(15)**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**lokale** (Standard)|Der Abonnent ist nur dem Verleger bekannt.|  
|**global**|Der Abonnent ist allen Servern bekannt.|  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen werden lokale Abonnements als "Clientabonnements" und globale Abonnements als "Serverabonnements" bezeichnet.  
  
`[ @subscription_priority = ] subscription_priority` Ist eine Zahl, die die Priorität für das Abonnement angibt. *Subscription_priority*ist **echte**, hat den Standardwert NULL. Für lokale und anonyme Abonnements ist die Priorität 0,0. Für globale Abonnements muss die Priorität niedriger als 100,0 sein.  
  
`[ @sync_type = ] 'sync_type'` Ist der Synchronisierungsart des Abonnements an. *Sync_type*ist **nvarchar(15)**, hat den Standardwert **automatische**. Kann **automatische** oder **keine**. Wenn **automatische**, das Schema und die Ausgangsdaten für veröffentlichte Tabellen zuerst an den Abonnenten übertragen werden. Wenn **keine**, es wird davon ausgegangen, dass der Abonnent hat bereits das Schema und die Ausgangsdaten für veröffentlichte Tabellen. Systemtabellen und Daten werden immer übertragen.  
  
> [!NOTE]  
>  Es wird empfohlen, keine Angabe des Werts **keine**.  
  
`[ @frequency_type = ] frequency_type` Ist ein Wert, der angibt, wann der Merge-Agent ausgeführt wird. *Frequency_type* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**10**|Monatlicher Zeitplan|  
|**20**|Monatlich, relativ zum Häufigkeitsintervall|  
|**40**|Beim Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents|  
|NULL (Standard)||  
  
`[ @frequency_interval = ] frequency_interval` Der Tag oder die Tage, die der Merge-Agent ausgeführt wird. *Frequency_interval* ist **Int**, und kann einen der folgenden Werte.  
  
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
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist die geplante Ausführung von Mergevorgängen mit dem Häufigkeitsintervall in jedem Monat. *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
|NULL (Standard)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor*ist **Int**, hat den Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday` Die Einheit für *Frequency_subday_interval*. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (Standard)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Die Häufigkeit von *Frequency_subday* zwischen jedem Mergevorgang ausgeführt. *Frequency_subday_interval* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit aus, wenn der Merge-Agent zuerst ist, wird geplant HHMMSS. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, ab der Merge-Agent nicht mehr, wird geplant ist HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an den Merge-Agent zuerst ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date` Ist das Datum, ab der Merge-Agent nicht mehr, geplant JJJJMMTT. *Active_end_date* ist **Int**, hat den Standardwert NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'` Ist die optional auszuführende Befehlszeile an. *Der Standardwert*ist **nvarchar(4000)**, hat den Standardwert NULL. Dieser Parameter wird verwendet, um einen Befehl hinzuzufügen, der die Ausgabe aufzeichnet und in einer Datei speichert, oder um eine Konfigurationsdatei oder ein Konfigurationsattribut anzugeben.  
  
`[ @description = ] 'description'` Ist eine kurze Beschreibung dieses Mergeabonnements. *Beschreibung*ist **nvarchar(255)**, hat den Standardwert NULL. Dieser Wert wird angezeigt, vom Replikationsmonitor in der **Anzeigenamen** Spalte, die zum Sortieren von Abonnements für eine überwachte Veröffentlichung verwendet werden kann.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Gibt an, ob das Abonnement kann, über synchronisiert werden [!INCLUDE[msCoName](../../includes/msconame-md.md)] Synchronisierungsverwaltung von Windows. *Enabled_for_syncmgr* ist **nvarchar(5)**, hat den Standardwert "false". Wenn **"false"**, das Abonnement ist nicht mit der Synchronisierungsverwaltung registriert. Wenn **"true"**, das Abonnement mit der Synchronisierungsverwaltung registriert und kann synchronisiert werden, ohne Starten des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
`[ @offloadagent = ] remote_agent_activation` Gibt an, dass der Agent Remote aktiviert werden kann. *Remote_agent_activation* ist **Bit** hat den Standardwert **0**.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird nur noch bereitgestellt, um Abwärtskompatibilität von Skripts sicherzustellen.  
  
`[ @offloadserver = ] 'remote_agent_server_name'` Gibt den Netzwerknamen des Servers für Remoteaktivierung der Momentaufnahme verwendet werden soll. *Remote_agent_server_name*ist **Sysname**, hat den Standardwert NULL.  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver'` Können Konflikte interaktiv für alle Artikel aufgelöst werden, die interaktive Lösung zulassen. *Use_interactive_resolver* ist **nvarchar(5)**, hat den Standardwert "false".  
  
`[ @merge_job_name = ] 'merge_job_name'` Die *@merge_job_name* -Parameter ist veraltet und kann nicht festgelegt werden. *Merge_job_name* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @hostname = ] 'hostname'` Überschreibt den Rückgabewert von [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) Wenn diese Funktion in der WHERE-Klausel eines parametrisierten Filters verwendet wird. *Hostname* ist **Sysname**, hat den Standardwert NULL.  
  
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
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Interaktive Konfliktlösung](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
