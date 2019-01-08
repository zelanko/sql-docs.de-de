---
title: Sp_addpushsubscription_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpushsubscription_agent_TSQL
- sp_addpushsubscription_agent
helpviewer_keywords:
- sp_addpushsubscription_agent
ms.assetid: 1fdd2052-50d8-4318-8aa7-fc635d5cad18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e438e8584312964d3d16651cb5551a4fb949597d
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53209803"
---
# <a name="spaddpushsubscriptionagent-transact-sql"></a>sp_addpushsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Fügt einen neuen geplanten Agentauftrag hinzu, der zum Synchronisieren eines Pushabonnements mit einer Transaktionsveröffentlichung verwendet wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addpushsubscription_agent [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
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
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @distribution_job_name = ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @subscriber_provider = ] 'subscriber_provider' ]   
    [ , [ @subscriber_datasrc = ] 'subscriber_datasrc' ]   
    [ , [ @subscriber_location = ] 'subscriber_location' ]  
    [ , [ @subscriber_provider_string = ] 'subscriber_provider_string' ]   
    [ , [ @subscriber_catalog = ] 'subscriber_catalog' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication =**] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@subscriber =**] **"***Abonnenten***"**  
 Der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@subscriber_db =**] **"***Subscriber_db***"**  
 Ist der Name der Abonnementdatenbank. *Subscriber_db* ist **Sysname**, hat den Standardwert NULL. Geben Sie den Wert für einen nicht - SQL Server-Abonnenten **(Standardziel)** für *Subscriber_db*.  
  
 [  **@subscriber_security_mode =**] *Subscriber_security_mode*  
 Der Sicherheitsmodus, der beim Synchronisieren zum Herstellen der Verbindung mit einem Abonnenten verwendet wird. *Subscriber_security_mode* ist **Int**, hat den Standardwert 1. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. **1** gibt die Windows-Authentifizierung.  
  
> [!IMPORTANT]  
>  Bei Abonnements mit verzögertem Update über eine Warteschlange verwenden Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung für Verbindungen mit Abonnenten. Geben Sie für die Verbindung zu den einzelnen Abonnenten jeweils ein anderes Konto an. Verwenden Sie für alle anderen Abonnements die Windows-Authentifizierung.  
  
 [  **@subscriber_login =**] **"***Subscriber_login***"**  
 Ist der Anmeldename des Abonnenten beim Herstellen einer Verbindung an einen Abonnenten, bei der Synchronisierung verwendet. *Subscriber_login* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@subscriber_password =**] **"***Subscriber_password***"**  
 Das Kennwort des Abonnenten. *Subscriber_password* ist erforderlich, wenn *Subscriber_security_mode* nastaven NA hodnotu **0**. *Subscriber_password* ist **Sysname**, hat den Standardwert NULL. Bei Verwendung eines Abonnentenkennworts wird dieses automatisch verschlüsselt.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
 [  **@job_login =** ] **"***Job_login***"**  
 Ist der Anmeldename für das Konto, unter dem der Agent ausgeführt wird. Verwenden Sie bei Azure SQL-Datenbank verwaltete Instanzen ein SQL Server-Konto ein. *Job_login* ist **nvarchar(257)**, hat den Standardwert NULL. Dieses Windows-Konto wird immer für Agentverbindungen mit dem Verteiler und für Verbindungen mit dem Abonnenten verwendet, wenn die integrierte Windows-Authentifizierung verwendet wird.  
  
 [  **@job_password =** ] **"***Job_password***"**  
 Ist das Kennwort für das Konto, unter dem der Agent ausgeführt wird. *Job_password* ist **Sysname**, hat keinen Standardwert.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
 [  **@job_name =** ] **"***Job_name***"**  
 Der Name eines vorhandenen Agentauftrags. *Job_name* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter wird nur angegeben, wenn das Abonnement mithilfe eines vorhandenen Auftrags statt mit einem neu erstellten Auftrag (Standard) synchronisiert wird. Wenn Sie nicht Mitglied der sind die **Sysadmin** festen Serverrolle an, Sie müssen angeben, *Job_login* und *Job_password* beim Angeben von *Job_name*.  
  
 [  **@frequency_type =** ] *Frequency_type*  
 Die Häufigkeit für die Zeitplanung des Verteilungs-Agents. *Frequency_type* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Bedarfsgesteuert|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ|  
|**64** (Standard)|Autostart|  
|**128**|Wiederholt|  
  
> [!NOTE]  
>  Geben Sie einen Wert **64** bewirkt, dass der Verteilungs-Agent im fortlaufenden Modus ausgeführt. Dies entspricht dem Festlegen der **-Continuous** Parameter für den Agent. Weitere Informationen finden Sie unter [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
 [  **@frequency_interval =** ] *Frequency_interval*  
 Ist der Wert der Häufigkeit festgelegt, die durch Anwenden *Frequency_type*. *Frequency_interval* ist **Int**, hat den Standardwert 1.  
  
 [  **@frequency_relative_interval =** ] *Frequency_relative_interval*  
 Das Datum des Verteilungs-Agents. Dieser Parameter wird verwendet, wenn *Frequency_type* nastaven NA hodnotu **32** (mit relativem Monatsintervall). *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1** (Standard)|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
 [  **@frequency_recurrence_factor =** ] *Frequency_recurrence_factor*  
 Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert 0.  
  
 [  **@frequency_subday =** ] *Frequency_subday*  
 Die Häufigkeit für die erneute geplante Ausführung während des definierten Zeitraums. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4** (Standard)|Minute|  
|**8**|Hour|  
  
 [  **@frequency_subday_interval =** ] *Frequency_subday_interval*  
 Das Intervall für *Frequency_subday*. *Frequency_subday_interval* ist **Int**, hat den Standardwert 5.  
  
 [  **@active_start_time_of_day =** ] *Active_start_time_of_day*  
 Die Tageszeit, zu der der Verteilungs-Agent zum ersten Mal geplant ist. Dabei wird das Format HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert 0.  
  
 [  **@active_end_time_of_day =** ] *Active_end_time_of_day*  
 Die Tageszeit, ab der der Verteilungs-Agent nicht mehr geplant ist. Dabei wird das Format HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert 235959.  
  
 [ **@active_start_date =** ] *active_start_date*  
 Das Datum, an dem der Verteilungs-Agent zum ersten Mal geplant ist. Dabei wird das Format JJJJMMTT verwendet. *Active_start_date* ist **Int**, hat den Standardwert 0.  
  
 [ **@active_end_date =** ] *active_end_date*  
 Das Datum, ab dem der Verteilungs-Agent nicht mehr geplant ist. Dabei wird das Format JJJJMMTT verwendet. *Active_end_date* ist **Int**, hat den Standardwert 99991231.  
  
 [  **@dts_package_name =** ] **"***Dts_package_name***"**  
 Gibt den Namen des DTS-Pakets (Data Transformation Services) an. *Dts_package_name* ist eine **Sysname** hat den Standardwert NULL. Zum Angeben des Paketnamens `DTSPub_Package` wird beispielsweise der `@dts_package_name = N'DTSPub_Package'`-Parameter verwendet.  
  
 [  **@dts_package_password =** ] **"***Dts_package_password***"**  
 Gibt das zum Ausführen des Pakets erforderliche Kennwort an. *Dts_package_password* ist **Sysname** hat den Standardwert NULL.  
  
> [!NOTE]  
>  Sie müssen ein Kennwort angeben, wenn *Dts_package_name* angegeben ist.  
  
 [  **@dts_package_location =** ] **"***Dts_package_location***"**  
 Gibt den Paketspeicherort an. *Dts_package_location* ist eine **nvarchar(12)**, hat den Standardwert des VERTEILERS. Der Speicherort des Pakets kann sein **Verteiler** oder **Abonnenten**.  
  
 [  **@enabled_for_syncmgr =** ] **"***Enabled_for_syncmgr***"**  
 Gibt an, ob das Abonnement über synchronisiert werden kann [!INCLUDE[msCoName](../../includes/msconame-md.md)] Synchronisierungs-Manager. *Enabled_for_syncmgr* ist **nvarchar(5)**, hat den Standardwert "false". Wenn **"false"**, das Abonnement ist nicht mit der Synchronisierungsverwaltung registriert. Wenn **"true"**, das Abonnement mit der Synchronisierungsverwaltung registriert und kann synchronisiert werden, ohne Starten des [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 [  **@distribution_job_name =** ] **"***distribution_job _name***"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@publisher =** ] **"***Verleger***"**  
 Der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@subscriber_provider=** ] **"***Subscriber_provider***"**  
 Ist der eindeutige Programmbezeichner (PROGID) mit dem OLE DB-Anbieters für den nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenquelle registriert wird. *Subscriber_provider* ist **Sysname**, mit dem Standardwert NULL. *Subscriber_provider* für auf dem Verteiler installierten OLE DB-Anbieter eindeutig sein. *Subscriber_provider* wird nur unterstützt, für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.  
  
 [  **@subscriber_datasrc=** ] **"***Subscriber_datasrc***"**  
 Der Name der Datenquelle im vom OLE DB-Anbieter unterstützten Format. *Subscriber_datasrc* ist **nvarchar(4000)**, hat den Standardwert NULL. *Subscriber_datasrc* wird als DBPROP_INIT_DATASOURCE-Eigenschaft zum Initialisieren des OLE DB-Anbieters übergeben. *Subscriber_datasrc* wird nur unterstützt, für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.  
  
 [  **@subscriber_location=** ] **"***Subscriber_location***"**  
 Ist der Speicherort der Datenbank an, wie er vom OLE DB-Anbieter interpretiert. *Subscriber_location* ist **nvarchar(4000)**, hat den Standardwert NULL. *Subscriber_location* wird als DBPROP_INIT_LOCATION-Eigenschaft zum Initialisieren des OLE DB-Anbieters übergeben. *Subscriber_location* wird nur unterstützt, für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.  
  
 [  **@subscriber_provider_string=** ] **"***Subscriber_provider_string***"**  
 Die für den OLE DB-Anbieter spezifische Verbindungszeichenfolge zum Identifizieren der Datenquelle. *Subscriber_provider_string* ist **nvarchar(4000)**, hat den Standardwert NULL. *Subscriber_provider_string* IDataInitialize übergeben oder als DBPROP_INIT_PROVIDERSTRING-Eigenschaft festgelegt wird, um den OLE DB-Anbieter zu initialisieren. *Subscriber_provider_string* wird nur unterstützt, für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.  
  
 [  **@subscriber_catalog=** ] **"***Subscriber_catalog***"**  
 Der beim Herstellen einer Verbindung mit dem OLE DB-Anbieter zu verwendende Katalog. *Subscriber_catalog* ist **Sysname**, mit dem Standardwert NULL. *Subscriber_catalog* wird als DBPROP_INIT_CATALOG-Eigenschaft zum Initialisieren des OLE DB-Anbieters übergeben. *Subscriber_catalog* wird nur unterstützt, für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addpushsubscription_agent** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addpushsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addpushsubscription_agent**.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Erstellen eines Abonnements für einen Nicht-SQL Server-Abonnenten](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [Sp_changesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [Sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
