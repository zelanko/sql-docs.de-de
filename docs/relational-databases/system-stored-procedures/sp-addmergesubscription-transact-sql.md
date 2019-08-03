---
title: sp_addmergesubscription (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: b501a2c06a6d9e8e3573ef5d5814c3318c4e623b
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769134"
---
# <a name="spaddmergesubscription-transact-sql"></a>sp_addmergesubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt ein Mergepushabonnement oder ein Mergepullabonnement. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
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
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Die Veröffentlichung muss bereits vorhanden sein.  
  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'`Der Name der Abonnement Datenbank. *subscriber_db*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subscription_type = ] 'subscription_type'`Der Abonnementtyp. *subscription_type*ist vom Datentyp **nvarchar (15)** und hat den Standardwert Push. Bei **Push**wird ein Pushabonnement hinzugefügt, und das Merge-Agent wird auf dem Verteiler hinzugefügt. Wenn **Pull**, wird ein Pullabonnement hinzugefügt, ohne auf dem Verteiler eine Merge-Agent hinzuzufügen.  
  
> [!NOTE]  
>  Für anonyme Abonnements ist diese gespeicherte Prozedur nicht erforderlich.  
  
`[ @subscriber_type = ] 'subscriber_type'`Der Typ des Abonnenten. *subscriber_type*ist vom Datentyp **nvarchar (15)** . die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**lokal** vorgegebene|Der Abonnent ist nur dem Verleger bekannt.|  
|**global**|Der Abonnent ist allen Servern bekannt.|  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen werden lokale Abonnements als "Clientabonnements" und globale Abonnements als "Serverabonnements" bezeichnet.  
  
`[ @subscription_priority = ] subscription_priority`Eine Zahl, die die Priorität für das Abonnement angibt. *subscription_priority*ist vom Typ **Real**und hat den Standardwert NULL. Für lokale und anonyme Abonnements ist die Priorität 0,0. Für globale Abonnements muss die Priorität niedriger als 100,0 sein.  
  
`[ @sync_type = ] 'sync_type'`Der Synchronisierungstyp des Abonnements. *sync_type*ist vom Datentyp **nvarchar (15)** . der Standardwert ist **automatisch**. Kann " **Automatic** " oder " **None**" sein. Wenn **automatisch**, werden das Schema und die Anfangsdaten für veröffentlichte Tabellen zuerst an den Abonnenten übertragen. Wenn **keiner**vorhanden ist, wird davon ausgegangen, dass der Abonnent bereits über das Schema und die Anfangsdaten für veröffentlichte Tabellen verfügt. Systemtabellen und Daten werden immer übertragen.  
  
> [!NOTE]  
>  Es wird empfohlen, nicht den Wert " **None**" anzugeben.  
  
`[ @frequency_type = ] frequency_type`Ein Wert, der angibt, wann die Merge-Agent ausgeführt wird. *frequency_type* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**10**|Monatlicher Zeitplan|  
|**20**|Monatlich, relativ zum Häufigkeitsintervall|  
|**40**|Beim Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents|  
|NULL (Standard)||  
  
`[ @frequency_interval = ] frequency_interval`Der Tag oder die Tage, an denen die Merge-Agent ausgeführt wird. *frequency_interval* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
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
|**9**|Tage|  
|**10**|Wochenendtage|  
|NULL (Standard)||  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das geplante Merge-Vorkommen des Häufigkeits Intervalls in jedem Monat. *frequency_relative_interval* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
|NULL (Standard)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor*ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday`Ist die Einheit für *frequency_subday_interval*. *frequency_subday* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (Standard)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Die Häufigkeit, mit der *frequency_subday* zwischen den einzelnen zusammenführen auftritt. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der die Merge-Agent zum ersten Mal geplant ist. dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der die Merge-Agent nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem die Merge-Agent zum ersten Mal geplant ist, formatiert als YYYYMMDD. *active_start_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Merge-Agent nicht mehr geplant ist, formatiert als YYYYMMDD. *active_end_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'`Die optionale Eingabeaufforderung, die ausgeführt werden soll. *optional_command_line*ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL. Dieser Parameter wird verwendet, um einen Befehl hinzuzufügen, der die Ausgabe aufzeichnet und in einer Datei speichert, oder um eine Konfigurationsdatei oder ein Konfigurationsattribut anzugeben.  
  
`[ @description = ] 'description'`Eine kurze Beschreibung dieses Mergeabonnements. die *Beschreibung*ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Dieser Wert wird vom Replikations Monitor in der Spalte Anzeige **Name** angezeigt, der zum Sortieren der Abonnements für eine überwachte Veröffentlichung verwendet werden kann.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'`Gibt an, ob das Abonnement über [!INCLUDE[msCoName](../../includes/msconame-md.md)] die Synchronisierungs Verwaltung von Windows synchronisiert werden kann. *enabled_for_syncmgr* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. Wenn der Wert **false**ist, wird das Abonnement nicht bei der Synchronisierungs Verwaltung registriert. Wenn der Wert **true**ist, wird das Abonnement bei der Synchronisierungs Verwaltung registriert und [!INCLUDE[msCoName](../../includes/msconame-md.md)] kann synchronisiert werden, ohne zu starten [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
`[ @offloadagent = ] remote_agent_activation`Gibt an, dass der Agent Remote aktiviert werden kann. *remote_agent_activation* ist vom Typ **Bit** und hat den Standardwert **0**.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird nur noch bereitgestellt, um Abwärtskompatibilität von Skripts sicherzustellen.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`Gibt den Netzwerknamen des Servers an, der für die Remote-Agentaktivierung verwendet werden soll. *remote_agent_server_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver'`Ermöglicht das interaktive Auflösen von Konflikten für alle Artikel, die eine interaktive Auflösung ermöglichen. *use_interactive_resolver* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
`[ @merge_job_name = ] 'merge_job_name'`Der merge_job_name-Parameter ist veraltet und kann nicht festgelegt werden.  *\@* *merge_job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @hostname = ] 'hostname'`Überschreibt den von [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) zurückgegebenen Wert, wenn diese Funktion in der WHERE-Klausel eines parametrisierten Filters verwendet wird. Der *Hostname* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Aus Leistungsgründen wird empfohlen, keine Funktionen auf Spaltennamen in parametrisierten Zeilenfilterklauseln (beispielsweise `LEFT([MyColumn]) = SUSER_SNAME()`) anzuwenden. Wenn Sie [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) in einer Filter Klausel verwenden und den HOST_NAME-Wert überschreiben, ist es möglicherweise erforderlich, Datentypen mithilfe von [Convert](../../t-sql/functions/cast-and-convert-transact-sql.md)zu konvertieren. Weitere Informationen zu bewährten Methoden für diesen Fall finden Sie im Abschnitt über das Überschreiben des HOST_NAME()-Werts im Thema [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_addmergesubscription** wird bei der Mergereplikation verwendet.  
  
 Wenn **sp_addmergesubscription** von einem Mitglied der festen Server Rolle **sysadmin** ausgeführt wird, um ein Pushabonnement zu erstellen, wird der Merge-Agent Auftrag implizit erstellt und unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst Konto ausgeführt. Es wird empfohlen, dass Sie [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) ausführen und die Anmelde Informationen eines anderen, agentspezifischen Windows-Kontos für  **\@job_login** und  **\@job_password**angeben. Weitere Informationen finden Sie unter [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergesubscription-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addmergesubscription**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Interaktive Konfliktlösung](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
