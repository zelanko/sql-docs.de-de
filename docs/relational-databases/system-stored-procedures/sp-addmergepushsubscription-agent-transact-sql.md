---
title: Sp_addmergepushsubscription_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepushsubscription_agent_TSQL
- sp_addmergepushsubscription_agent
helpviewer_keywords:
- sp_addmergepushsubscription_agent
ms.assetid: 808a1925-be46-4999-8d69-b3a83010ec81
author: stevestein
ms.author: sstein
ms.openlocfilehash: e24659cc7880a5df34aa451c5051e77b8a4c59d0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68117952"
---
# <a name="spaddmergepushsubscriptionagent-transact-sql"></a>sp_addmergepushsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt einer Mergeveröffentlichung einen neuen Agentauftrag hinzu, mit dem die Synchronisierung eines Pushabonnements geplant wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergepushsubscription_agent [ @publication =] 'publication'   
    [ , [ @subscriber = ] 'subscriber' ]   
    [ , [ @subscriber_db = ] 'subscriber_db' ]   
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]   
    [ , [ @subscriber_login = ] 'subscriber_login' ]   
    [ , [ @subscriber_password = ] 'subscriber_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @job_name = ] 'job_name' ]   
    [ , [ @frequency_type = ] frequency_type ]   
    [ , [ @frequency_interval = ] frequency_interval ]   
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]   
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]   
    [ , [ @frequency_subday = ] frequency_subday ]   
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]   
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]   
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` Ist der Name der Abonnementdatenbank. *Subscriber_db* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` Ist der Sicherheitsmodus, verwenden Sie beim Herstellen einer Verbindung an einen Abonnenten, bei der Synchronisierung. *Subscriber_security_mode* ist **Int**, hat den Standardwert 1. Wenn **0**, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. Wenn **1**, gibt die Windows-Authentifizierung.  
  
`[ @subscriber_login = ] 'subscriber_login'` Ist der Anmeldename des Abonnenten beim Herstellen einer Verbindung an einen Abonnenten, bei der Synchronisierung verwendet. *Subscriber_login* ist erforderlich, wenn *Subscriber_security_mode* nastaven NA hodnotu **0**. *Subscriber_login* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @subscriber_password = ] 'subscriber_password'` Entspricht dem abonnentenkennwort für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. *Subscriber_password* ist erforderlich, wenn *Subscriber_security_mode* nastaven NA hodnotu **0**. *Subscriber_password* ist **Sysname**, hat den Standardwert NULL. Bei Verwendung eines Abonnentenkennworts wird dieses automatisch verschlüsselt.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Ist der Sicherheitsmodus, verwenden Sie beim Herstellen einer Verbindung mit einem Verleger, bei der Synchronisierung. *Publisher_security_mode* ist **Int**, hat den Standardwert 1. Wenn **0**, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. Wenn **1**, gibt die Windows-Authentifizierung.  
  
`[ @publisher_login = ] 'publisher_login'` Ist die Anmeldung beim Herstellen einer Verbindung mit einem Verleger, bei der Synchronisierung verwendet. *Publisher_login* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @publisher_password = ] 'publisher_password'` Das Kennwort wird verwendet werden, wenn eine Verbindung mit dem Verleger herstellen. *Publisher_password* ist **Sysname**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @job_login = ] 'job_login'` Ist der Anmeldename für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_login* ist **nvarchar(257)** , hat den Standardwert NULL. Dieses Windows-Konto wird immer für Agentverbindungen mit dem Verteiler und für Verbindungen mit dem Abonnenten und Verleger verwendet, wenn die integrierte Windows-Authentifizierung verwendet wird.  
  
`[ @job_password = ] 'job_password'` Ist das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_password* ist **Sysname**, hat keinen Standardwert.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @job_name = ] 'job_name'` Ist der Name eines vorhandenen Agent-Auftrags. *Job_name* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter wird nur angegeben, wenn das Abonnement nicht mit einem neu erstellten Auftrag (Standard), sondern mit einem vorhandenen Auftrag synchronisiert wird. Wenn Sie nicht Mitglied der sind die **Sysadmin** festen Serverrolle an, Sie müssen angeben, *Job_login* und *Job_password* beim Angeben von *Job_name*.  
  
`[ @frequency_type = ] frequency_type` Ist die Häufigkeit, mit dem der Merge-Agent zu planen. *Frequency_type* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Bedarfsgesteuert|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ|  
|**64**|Autostart|  
|**128**|Wiederholt|  
|NULL (Standard)||  
  
> [!NOTE]  
>  Geben Sie einen Wert **64** bewirkt, dass der Merge-Agent im fortlaufenden Modus ausgeführt. Dies entspricht dem Festlegen der **-Continuous** Parameter für den Agent. Weitere Informationen finden Sie unter [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
`[ @frequency_interval = ] frequency_interval` Die Tage, die der Merge-Agent ausgeführt wird. *Frequency_interval* ist **Int**, und kann einen der folgenden Werte.  
  
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
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum des Merge-Agents. Dieser Parameter wird verwendet, wenn *Frequency_type* nastaven NA hodnotu **32** (mit relativem Monatsintervall). *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
|NULL (Standard)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday` Ist die Häufigkeit für die erneute geplante Ausführung während des definierten Zeitraums. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (Standard)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für *Frequency_subday*. *Frequency_subday_interval* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit aus, wenn der Merge-Agent zuerst ist, wird geplant HHMMSS. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, ab der Merge-Agent nicht mehr, wird geplant ist HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an den Merge-Agent zuerst ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date` Ist das Datum, ab der Merge-Agent nicht mehr, geplant JJJJMMTT. *Active_end_date* ist **Int**, hat den Standardwert NULL.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Gibt an, ob das Abonnement über Windows Synchronization Manager synchronisiert werden kann. *Enabled_for_syncmgr* ist **nvarchar(5)** , hat den Standardwert "false". Wenn **"false"** , das Abonnement ist nicht mit der Synchronisierungsverwaltung registriert. Wenn **"true"** , das Abonnement mit der Synchronisierungsverwaltung registriert und kann synchronisiert werden, ohne Starten des [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addmergepushsubscription_agent** wird bei der Mergereplikation verwendet und verwendet ähnliche Funktionen wie [Sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepushsubscript_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addmergepushsubscription_agent**.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
