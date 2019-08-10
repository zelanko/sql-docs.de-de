---
title: sp_addpullsubscription_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/08/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpullsubscription_agent
- sp_addpullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addpullsubscription_agent
ms.assetid: b9c2eaed-6d2d-4b78-ae9b-73633133180b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ab0624abf7a0479ac12f1ab51efd00c7e45a82a
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893817"
---
# <a name="sp_addpullsubscription_agent-transact-sql"></a>sp_addpullsubscription_agent (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
 
  Fügt einer Transaktionsveröffentlichung einen neuen geplanten Agent-Auftrag hinzu, mit dem ein Pullabonnement synchronisiert wird. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addpullsubscription_agent [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]          , [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor = ] 'distributor' ]  
    [ , [ @distribution_db = ] 'distribution_db' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]  
    [ , [ @distributor_login = ] 'distributor_login' ]  
    [ , [ @distributor_password = ] 'distributor_password' ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
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
    [ , [ @distribution_jobid = ] distribution_jobid OUTPUT ]  
    [ , [ @encrypted_distributor_password = ] encrypted_distributor_password ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @ftp_address = ] 'ftp_address' ]  
    [ , [ @ftp_port = ] ftp_port ]  
    [ , [ @ftp_login = ] 'ftp_login' ]  
    [ , [ @ftp_password = ] 'ftp_password' ]  
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]  
    [ , [ @working_directory = ] 'working_directory' ]  
    [ , [ @use_ftp = ] 'use_ftp' ]  
    [ , [ @publication_type = ] publication_type ]  
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @offloadagent = ] 'remote_agent_activation' ]  
    [ , [ @offloadserver = ] 'remote_agent_server_name']  
    [ , [ @job_name = ] 'job_name' ]  
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'_`Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. *publisher_db* wird von Oracle-Verlegern ignoriert.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'`Der Name der Abonnenten Instanz oder der Name des Verfügbarkeits Gruppen-Listener, wenn die Abonnenten Datenbank eine Verfügbarkeits Gruppe ist. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
`[ @subscriber_db = ] 'subscriber_db'`Der Name der Abonnement Datenbank. *subscriber_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode`Der Sicherheitsmodus, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Abonnenten verwendet wird. *subscriber_security_mode* ist vom Datentyp **int und hat** den Standardwert NULL. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die-Authentifizierung an. **1** gibt die Windows-Authentifizierung an.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Der Verteilungs-Agent stellt eine Verbindung mit dem lokalen Abonnenten immer mithilfe der Windows-Authentifizierung her. Wenn für diesen Parameter ein anderer Wert als NULL oder **1** angegeben wird, wird eine Warnmeldung zurückgegeben.  
  
`[ @subscriber_login = ] 'subscriber_login'`Der Anmelde Name des Abonnenten, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Abonnenten verwendet wird. *subscriber_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Wird für diesen Parameter ein Wert angegeben, wird eine Warnmeldung zurückgegeben, der Wert jedoch ignoriert.  
  
`[ @subscriber_password = ] 'subscriber_password'`Das Kennwort des Abonnenten. *subscriber_password* ist erforderlich, wenn *subscriber_security_mode* auf **0**festgelegt ist. *subscriber_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Bei Verwendung eines Abonnentenkennworts wird dieses automatisch verschlüsselt.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Wird für diesen Parameter ein Wert angegeben, wird eine Warnmeldung zurückgegeben, der Wert jedoch ignoriert.  
  
`[ @distributor = ] 'distributor'`Der Name des Verteilers. *Distributor* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist der vom *Verleger*angegebene Wert.  
  
`[ @distribution_db = ] 'distribution_db'`Der Name der Verteilungs Datenbank. *distribution_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @distributor_security_mode = ] distributor_security_mode`Der Sicherheitsmodus, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verteiler verwendet wird. *distributor_security_mode* ist vom Datentyp **int**und hat den Standardwert **1**. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die-Authentifizierung an. **1** gibt die Windows-Authentifizierung an.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'`Der Verteiler Anmelde Name, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verteiler verwendet wird. *distributor_login* ist erforderlich, wenn *distributor_security_mode* auf **0**festgelegt ist. *distributor_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @distributor_password = ] 'distributor_password'`Das Verteiler Kennwort. *distributor_password* ist erforderlich, wenn *distributor_security_mode* auf **0**festgelegt ist. *distributor_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @optional_command_line = ] 'optional_command_line'`Ist eine optionale Eingabeaufforderung, die für die Verteilungs-Agent bereitgestellt wird. Beispiel: **-DefinitionFile** c:\Distdef.txt oder **-CommitBatchSize** 10. *optional_command_line* ist vom Datentyp **nvarchar (4000)** . der Standardwert ist eine leere Zeichenfolge.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der die Verteilungs-Agent geplant werden soll. *frequency_type* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2** (Standardwert)|Bedarfsgesteuert|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ|  
|**64**|Autostart|  
|**128**|Wiederholt|  
  
> [!NOTE]  
>  Das Angeben des Werts **64** bewirkt, dass die Verteilungs-Agent im kontinuierlichen Modus ausgeführt wird. Dies entspricht dem Festlegen des **-Continuous-** Parameters für den Agent. Weitere Informationen finden Sie unter [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
`[ @frequency_interval = ] frequency_interval`Der Wert, der auf die von *frequency_type*festgelegte Häufigkeit angewendet werden soll. *frequency_interval* ist vom Datentyp **int**und hat den Standardwert 1.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Datum der Verteilungs-Agent. Dieser Parameter wird verwendet, wenn *frequency_type* auf **32** (monatlich, relativ) festgelegt ist. *frequency_relative_interval* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**1** (Standard)|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert **1**.  
  
`[ @frequency_subday = ] frequency_subday`Gibt an, wie oft innerhalb des definierten Zeitraums neu geplant werden soll. *frequency_subday* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**1** (Standard)|Einmal|  
|**2**|Zweimal|  
|**4**|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Das Intervall für *frequency_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert **1**.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der die Verteilungs-Agent zum ersten Mal geplant ist. dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der die Verteilungs-Agent nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem die Verteilungs-Agent zum ersten Mal geplant ist, formatiert als YYYYMMDD. *active_start_date* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Verteilungs-Agent nicht mehr geplant ist, formatiert als YYYYMMDD. *active_end_date* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @distribution_jobid = ] _distribution_jobidOUTPUT`Die ID der Verteilungs-Agent für diesen Auftrag. *distribution_jobid* ist vom Typ **Binary (16)** und hat den Standardwert NULL, und es handelt sich um einen Output-Parameter.  
  
`[ @encrypted_distributor_password = ] encrypted_distributor_password`Das Festlegen von *encrypted_distributor_password* wird nicht mehr unterstützt. Der Versuch, diesen **Bit** -Parameter auf **1** festzulegen, führt zu einem Fehler.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'`Gibt an, ob das Abonnement über [!INCLUDE[msCoName](../../includes/msconame-md.md)] den Synchronisierungs-Manager synchronisiert werden kann. *enabled_for_syncmgr* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. Wenn der Wert **false**ist, wird das Abonnement nicht bei der Synchronisierungs Verwaltung registriert. Wenn der Wert **true**ist, wird das Abonnement bei der Synchronisierungs Verwaltung registriert und [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]kann synchronisiert werden, ohne zu starten.  
  
`[ @ftp_address = ] 'ftp_address'`Nur aus Gründen der Abwärtskompatibilität.  
  
`[ @ftp_port = ] ftp_port`Nur aus Gründen der Abwärtskompatibilität.  
  
`[ @ftp_login = ] 'ftp_login'`Nur aus Gründen der Abwärtskompatibilität.  
  
`[ @ftp_password = ] 'ftp_password'`Nur aus Gründen der Abwärtskompatibilität.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'_`Gibt den Speicherort des alternativen Ordners für die Momentaufnahme an. *alternate_snapshot_folder* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @working_directory = ] 'working_director'`Der Name des Arbeitsverzeichnisses, das zum Speichern von Daten-und Schema Dateien für die Veröffentlichung verwendet wird. *working_directory* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Dieser Name sollte im UNC-Format angegeben werden.  
  
`[ @use_ftp = ] 'use_ftp'`Gibt an, dass FTP anstelle des regulären Protokolls zum Abrufen von Momentaufnahmen verwendet wird. *use_ftp* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
`[ @publication_type = ] publication_type`Gibt den Replikationstyp der Veröffentlichung an. *publication_type* ist vom Datentyp **tinyint** . der Standardwert ist **0**. Wenn der Wert **0**ist, ist die Veröffentlichung ein Transaktionstyp. Bei **1**handelt es sich bei der Veröffentlichung um einen momentaufnahmetyp Wenn der Wert **2**ist, ist die Veröffentlichung ein mergetyp.  
  
`[ @dts_package_name = ] 'dts_package_name'`Gibt den Namen des DTS-Pakets an. *dts_package_name* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL. Zum Angeben eines Pakets mit dem Namen `DTSPub_Package` wird beispielsweise der `@dts_package_name = N'DTSPub_Package'`-Parameter verwendet.  
  
`[ @dts_package_password = ] 'dts_package_password'`Gibt ggf. das Kennwort für das Paket an. *dts_package_password* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL. Dies bedeutet, dass kein Kennwort für das Paket gilt.  
  
> [!NOTE]  
>  Sie müssen ein Kennwort angeben, wenn *dts_package_name* angegeben wird.  
  
`[ @dts_package_location = ] 'dts_package_location'`Gibt den Speicherort des Pakets an. *dts_package_location* ist vom Datentyp **nvarchar (12)** und hat den Standardwert **Subscriber**. Der Speicherort des Pakets kann **Distributor** oder **Subscriber**sein.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Wenn Sie *remote_agent_activation* auf einen anderen Wert als **false** festlegen, wird ein Fehler generiert.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Wenn *remote_agent_server_name* auf einen anderen Wert als NULL festgelegt wird, wird ein Fehler generiert.  
  
`[ @job_name = ] 'job_name'`Der Name eines vorhandenen Agentauftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter wird nur angegeben, wenn das Abonnement mithilfe eines vorhandenen Auftrags statt mit einem neu erstellten Auftrag (Standard) synchronisiert wird. Wenn Sie kein Mitglied der festen Server Rolle **sysadmin** sind, müssen Sie *job_login* und *job_password* angeben, wenn Sie *job_name*angeben.  
  
`[ @job_login = ] 'job_login'`Der Anmelde Name für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_login* ist vom Datentyp **nvarchar (257)** und hat keinen Standardwert. Dieses Windows-Konto wird immer für Agent-Verbindungen mit dem Abonnenten verwendet.  
  
`[ @job_password = ] 'job_password'`Das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_addpullsubscription_agent** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addpullsubscription_agent**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
