---
title: Sp_addpullsubscription_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
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
manager: craigg
ms.openlocfilehash: ef3f22ffa0456c69b7e46f8c5aadfc89f95ccc67
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493492"
---
# <a name="spaddpullsubscriptionagent-transact-sql"></a>sp_addpullsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
 
  Fügt einer Transaktionsveröffentlichung einen neuen geplanten Agent-Auftrag hinzu, mit dem ein Pullabonnement synchronisiert wird. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
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
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'_` Ist der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL. *Publisher_db* wird von Oracle-Verlegern ignoriert.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
`[ @subscriber_db = ] 'subscriber_db'` Ist der Name der Abonnementdatenbank. *Subscriber_db* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` Ist der Sicherheitsmodus, verwenden Sie beim Herstellen einer Verbindung an einen Abonnenten, bei der Synchronisierung. *Subscriber_security_mode* ist **ganze Zahl,** hat den Standardwert NULL. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. **1** gibt die Windows-Authentifizierung.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Der Verteilungs-Agent stellt eine Verbindung mit dem lokalen Abonnenten immer mithilfe der Windows-Authentifizierung her. Wenn ein anderer Wert als NULL oder **1** angegeben ist für diesen Parameter wird eine Warnmeldung zurückgegeben.  
  
`[ @subscriber_login = ] 'subscriber_login'` Ist der Anmeldename des Abonnenten beim Herstellen einer Verbindung an einen Abonnenten, bei der Synchronisierung verwendet. *Subscriber_login* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Wird für diesen Parameter ein Wert angegeben, wird eine Warnmeldung zurückgegeben, der Wert jedoch ignoriert.  
  
`[ @subscriber_password = ] 'subscriber_password'` Ist das Kennwort des Abonnenten. *Subscriber_password* ist erforderlich, wenn *Subscriber_security_mode* nastaven NA hodnotu **0**. *Subscriber_password* ist **Sysname**, hat den Standardwert NULL. Bei Verwendung eines Abonnentenkennworts wird dieses automatisch verschlüsselt.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Wird für diesen Parameter ein Wert angegeben, wird eine Warnmeldung zurückgegeben, der Wert jedoch ignoriert.  
  
`[ @distributor = ] 'distributor'` Ist der Name des Verteilers. *Verteiler* ist **Sysname**, hat den Standardwert der Wert von *Verleger*.  
  
`[ @distribution_db = ] 'distribution_db'` Ist der Name der Verteilungsdatenbank. *Distribution_db* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @distributor_security_mode = ] distributor_security_mode` Ist der Sicherheitsmodus, verwenden Sie beim Herstellen einer Verbindung mit einem Verteiler, bei der Synchronisierung. *Distributor_security_mode* ist **Int**, hat den Standardwert **1**. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. **1** gibt die Windows-Authentifizierung.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` Ist der Anmeldename des Verteilers beim Verbinden mit einem Verteiler, bei der Synchronisierung verwendet. *Distributor_login* ist erforderlich, wenn *Distributor_security_mode* nastaven NA hodnotu **0**. *Distributor_login* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @distributor_password = ] 'distributor_password'` Ist das Verteilerkennwort. *Distributor_password* ist erforderlich, wenn *Distributor_security_mode* nastaven NA hodnotu **0**. *Distributor_password* ist **Sysname**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @optional_command_line = ] 'optional_command_line'` Eine optionale Befehlszeile ist des Verteilungs-Agents angegeben werden. Z. B. **- DefinitionFile** C:\Distdef.txt oder **- CommitBatchSize** 10. *Der Standardwert* ist **nvarchar(4000)**, Standardwert ist eine leere Zeichenfolge.  
  
`[ @frequency_type = ] frequency_type` Kann die Häufigkeit, mit denen der Verteilungs-Agent zu planen. *Frequency_type* ist **Int**, und kann einen der folgenden Werte.  
  
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
>  Geben Sie einen Wert **64** bewirkt, dass der Verteilungs-Agent im fortlaufenden Modus ausgeführt. Dies entspricht dem Festlegen der **-Continuous** Parameter für den Agent. Weitere Informationen finden Sie unter [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
`[ @frequency_interval = ] frequency_interval` Ist der Wert der Häufigkeit festgelegt, die durch Anwenden *Frequency_type*. *Frequency_interval* ist **Int**, hat den Standardwert 1.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum des Verteilungs-Agents. Dieser Parameter wird verwendet, wenn *Frequency_type* nastaven NA hodnotu **32** (mit relativem Monatsintervall). *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1** (Standard)|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert **1**.  
  
`[ @frequency_subday = ] frequency_subday` Ist die Häufigkeit für die erneute geplante Ausführung während des definierten Zeitraums. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1** (Standard)|Einmal|  
|**2**|Zweimal|  
|**4**|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für *Frequency_subday*. *Frequency_subday_interval* ist **Int**, hat den Standardwert **1**.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit aus, wenn der erste der Verteilungs-Agent ist, erfolgt Format: HHMMSS. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert **0**.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, ab der Verteilungs-Agent nicht mehr, wird geplant ist HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert **0**.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an den Verteilungs-Agent zuerst ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat den Standardwert **0**.  
  
`[ @active_end_date = ] active_end_date` Ist das Datum, ab der Verteilungs-Agent nicht mehr, geplant JJJJMMTT. *Active_end_date* ist **Int**, hat den Standardwert **0**.  
  
`[ @distribution_jobid = ] _distribution_jobidOUTPUT` Ist die ID des Verteilungs-Agents für diesen Auftrag. *Distribution_jobid* ist **'binary(16)'**, hat den Standardwert NULL, und es ist ein OUTPUT-Parameter.  
  
`[ @encrypted_distributor_password = ] encrypted_distributor_password` Festlegen von *Encrypted_distributor_password* wird nicht mehr unterstützt. Es wird versucht, diese festgelegt **Bit** Parameter **1** führt zu einem Fehler.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Gibt an, ob das Abonnement über synchronisiert werden kann [!INCLUDE[msCoName](../../includes/msconame-md.md)] Synchronisierungs-Manager. *Enabled_for_syncmgr* ist **nvarchar(5)**, hat den Standardwert "false". Wenn **"false"**, das Abonnement ist nicht mit der Synchronisierungsverwaltung registriert. Wenn **"true"**, das Abonnement mit der Synchronisierungsverwaltung registriert und kann synchronisiert werden, ohne Starten des [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
`[ @ftp_address = ] 'ftp_address'` Nur für Abwärtskompatibilität.  
  
`[ @ftp_port = ] ftp_port` Nur für Abwärtskompatibilität.  
  
`[ @ftp_login = ] 'ftp_login'` Nur für Abwärtskompatibilität.  
  
`[ @ftp_password = ] 'ftp_password'` Nur für Abwärtskompatibilität.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'_` Gibt den Speicherort des alternativen Ordners für die Momentaufnahme. *Alternate_snapshot_folder* ist **nvarchar(255)**, hat den Standardwert NULL.  
  
`[ @working_directory = ] 'working_director'` Ist der Name des Arbeitsverzeichnisses zum Speichern von Daten- und Schemadateien für die Veröffentlichung verwendet. *Working_directory* ist **nvarchar(255)**, hat den Standardwert NULL. Dieser Name sollte im UNC-Format angegeben werden.  
  
`[ @use_ftp = ] 'use_ftp'` Gibt die Verwendung an, dass FTP anstelle des regulären Protokolls zum Abrufen von Momentaufnahmen. *Use_ftp* ist **nvarchar(5)**, hat den Standardwert "false".  
  
`[ @publication_type = ] publication_type` Gibt den Replikationstyp der Veröffentlichung an. *Publication_type* ist eine **Tinyint** hat den Standardwert **0**. Wenn **0**, handelt es sich eine Transaktion. Wenn **1**, handelt es sich Momentaufnahme. Wenn **2**, handelt es sich zusammenführen.  
  
`[ @dts_package_name = ] 'dts_package_name'` Gibt den Namen des DTS-Pakets. *Dts_package_name* ist eine **Sysname** hat den Standardwert NULL. Zum Angeben eines Pakets mit dem Namen `DTSPub_Package` wird beispielsweise der `@dts_package_name = N'DTSPub_Package'`-Parameter verwendet.  
  
`[ @dts_package_password = ] 'dts_package_password'` Gibt das Kennwort des Pakets an, sofern vorhanden. *Dts_package_password* ist **Sysname** hat den Standardwert NULL, was bedeutet es ist kein Kennwort für das Paket.  
  
> [!NOTE]  
>  Sie müssen ein Kennwort angeben, wenn *Dts_package_name* angegeben ist.  
  
`[ @dts_package_location = ] 'dts_package_location'` Gibt den Speicherort des Pakets an. *Dts_package_location* ist eine **nvarchar(12)**, hat den Standardwert **Abonnenten**. Der Speicherort des Pakets kann sein **Verteiler** oder **Abonnenten**.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Festlegen von *Remote_agent_activation* auf einen anderen Wert als **"false"** wird ein Fehler generiert.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Festlegen von *Remote_agent_server_name* auf einen beliebigen Wert ungleich NULL wird ein Fehler generiert.  
  
`[ @job_name = ] 'job_name'` Ist der Name eines vorhandenen Agent-Auftrags. *Job_name* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter wird nur angegeben, wenn das Abonnement mithilfe eines vorhandenen Auftrags statt mit einem neu erstellten Auftrag (Standard) synchronisiert wird. Wenn Sie nicht Mitglied der sind die **Sysadmin** festen Serverrolle an, Sie müssen angeben, *Job_login* und *Job_password* beim Angeben von *Job_name*.  
  
`[ @job_login = ] 'job_login'` Ist der Anmeldename für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_login* ist **nvarchar(257)**, hat keinen Standardwert. Dieses Windows-Konto wird immer für Agent-Verbindungen mit dem Abonnenten verwendet.  
  
`[ @job_password = ] 'job_password'` Ist das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_password* ist **Sysname**, hat keinen Standardwert.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addpullsubscription_agent** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addpullsubscription_agent**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
