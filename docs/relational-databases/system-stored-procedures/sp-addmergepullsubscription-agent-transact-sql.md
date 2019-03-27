---
title: Sp_addmergepullsubscription_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_agent
- sp_addmergepullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addmergepullsubscription_agent
ms.assetid: a2f4b086-078d-49b5-8971-8a1e3f6a6feb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5859d7e4c026375d5e9ade69628b9cf9e4a76ed0
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494362"
---
# <a name="spaddmergepullsubscriptionagent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt einen neuen Agentauftrag für die geplante Synchronisierung eines Pullabonnements mit einer Mergeveröffentlichung hinzu. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergepullsubscription_agent [ [ @name = ] 'name' ]   
        , [ @publisher = ] 'publisher'   
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication =] 'publication'   
    [ , [ @publisher_security_mod e= ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher_encrypted_password = ] publisher_encrypted_password ]   
    [ , [ @subscriber = ] 'subscriber' ]   
    [ , [ @subscriber_db = ] 'subscriber_db' ]   
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]   
    [ , [ @subscriber_login = ] 'subscriber_login' ]   
    [ , [ @subscriber_password= ] 'subscriber_password' ]   
    [ , [ @distributor = ] 'distributor' ]   
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @encrypted_password = ] encrypted_password ]   
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
    [ , [ @optional_command_line = ] 'optional_command_line' ]   
    [ , [ @merge_jobid = ] merge_jobid ]   
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]   
    [ , [ @ftp_address = ] 'ftp_address' ]   
    [ , [ @ftp_port = ] ftp_port ]   
    [ , [ @ftp_login = ] 'ftp_login' ]   
    [ , [ @ftp_password = ] 'ftp_password' ]    
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]   
    [ , [ @working_directory = ] 'working_directory' ]   
    [ , [ @use_ftp = ] 'use_ftp' ]   
    [ , [ @reserved = ] 'reserved' ]   
    [ , [ @use_interactive_resolver = ] 'use_interactive_resolver' ]   
    [ , [ @offloadagent = ] 'remote_agent_activation' ]   
    [ , [ @offloadserver = ] 'remote_agent_server_name']   
    [ , [ @job_name = ] 'job_name' ]   
    [ , [ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]  
    [ , [ @use_web_sync = ] use_web_sync ]  
        [ , [ @internet_url = ] 'internet_url' ]  
    [ , [ @internet_login = ] 'internet_login' ]  
        [ , [ @internet_password = ] 'internet_password' ]  
    [ , [ @internet_security_mode = ] internet_security_mode ]  
        [ , [ @internet_timeout = ] internet_timeout ]  
    [ , [ @hostname = ] 'hostname' ]  
        [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'` Ist der Name des Agents. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegerservers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Ist der Sicherheitsmodus, verwenden Sie beim Herstellen einer Verbindung mit einem Verleger, bei der Synchronisierung. *Publisher_security_mode* ist **Int**, hat den Standardwert 1. Wenn **0**, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. Wenn **1**, gibt die Windows-Authentifizierung.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Ist die Anmeldung beim Herstellen einer Verbindung mit einem Verleger, bei der Synchronisierung verwendet. *Publisher_login* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @publisher_password = ] 'publisher_password'` Das Kennwort wird verwendet werden, wenn eine Verbindung mit dem Verleger herstellen. *Publisher_password* ist **Sysname**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Sicherheitsanmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password` Festlegen von *Publisher_encrypted_password* wird nicht mehr unterstützt. Es wird versucht, diese festgelegt **Bit** Parameter **1** führt zu einem Fehler.  
  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten. *Abonnenten* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` Ist der Name der Abonnementdatenbank. *Subscriber_db* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` Ist der Sicherheitsmodus, verwenden Sie beim Herstellen einer Verbindung an einen Abonnenten, bei der Synchronisierung. *Subscriber_security_mode* ist **Int**, hat den Standardwert 1. Wenn **0**, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. Wenn **1**, gibt die Windows-Authentifizierung.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Der Merge-Agent verwendet für die Herstellung einer Verbindung mit dem lokalen Abonnenten stets die Windows-Authentifizierung. Falls für diesen Parameter ein Wert angegeben wird, wird zwar eine Warnmeldung zurückgegeben, doch der Wert selbst wird ignoriert.  
  
`[ @subscriber_login = ] 'subscriber_login'` Ist der Anmeldename des Abonnenten beim Herstellen einer Verbindung an einen Abonnenten, bei der Synchronisierung verwendet. *Subscriber_login* ist erforderlich, wenn *Subscriber_security_mode* nastaven NA hodnotu **0**. *Subscriber_login* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Falls für diesen Parameter ein Wert angegeben wird, wird zwar eine Warnmeldung zurückgegeben, doch der Wert selbst wird ignoriert.  
  
`[ @subscriber_password = ] 'subscriber_password'` Entspricht dem abonnentenkennwort für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. *Subscriber_password* ist erforderlich, wenn *Subscriber_security_mode* nastaven NA hodnotu **0**. *Subscriber_password* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Falls für diesen Parameter ein Wert angegeben wird, wird zwar eine Warnmeldung zurückgegeben, doch der Wert selbst wird ignoriert.  
  
`[ @distributor = ] 'distributor'` Ist der Name des Verteilers. *Verteiler* ist **Sysname**, hat den Standardwert *Verleger*; d. h. der Verleger ist auch der Verteiler.  
  
`[ @distributor_security_mode = ] distributor_security_mode` Ist der Sicherheitsmodus, verwenden Sie beim Herstellen einer Verbindung mit einem Verteiler, bei der Synchronisierung. *Distributor_security_mode* ist **Int**, hat den Standardwert 0. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. **1** gibt die Windows-Authentifizierung.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` Ist der Anmeldename des Verteilers beim Verbinden mit einem Verteiler, bei der Synchronisierung verwendet. *Distributor_login* ist erforderlich, wenn *Distributor_security_mode* nastaven NA hodnotu **0**. *Distributor_login* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @distributor_password = ] 'distributor_password'` Ist das Verteilerkennwort. *Distributor_password* ist erforderlich, wenn *Distributor_security_mode* nastaven NA hodnotu **0**. *Distributor_password* ist **Sysname**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Sicherheitsanmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @encrypted_password = ] encrypted_password` Festlegen von *Encrypted_password* wird nicht mehr unterstützt. Es wird versucht, diese festgelegt **Bit** Parameter **1** führt zu einem Fehler.  
  
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
  
`[ @frequency_interval = ] frequency_interval` Der Tag oder die Tage, die der Merge-Agent ausgeführt wird. *Frequency_interval* ist **Int**, und kann einen der folgenden Werte sein.  
  
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
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum des Merge-Agents. Dieser Parameter wird verwendet, wenn *Frequency_type* nastaven NA hodnotu **32** (mit relativem Monatsintervall). *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
|NULL (Standard)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday` Ist die Häufigkeit für die erneute geplante Ausführung während des definierten Zeitraums. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte sein.  
  
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
  
`[ @optional_command_line = ] 'optional_command_line'` Ist eine optionale Eingabeaufforderung, die für den Merge-Agent bereitgestellt wird. *Der Standardwert* ist **nvarchar(255)**, hat den Standardwert ' '. Kann zur Bereitstellung zusätzlicher Parameter für den Merge-Agent verwendet werden, wie im folgenden Beispiel gezeigt wird, bei dem das Standardtimeout für Abfragen auf `600` Sekunden erhöht wird:  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid` Ist der Ausgabeparameter für die Auftrags-ID. *der Standard* ist **'binary(16)'**, hat den Standardwert NULL.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Gibt an, ob das Abonnement über Windows Synchronization Manager synchronisiert werden kann. *Enabled_for_syncmgr* ist **nvarchar(5)**, hat den Standardwert "false". Wenn **"false"**, das Abonnement ist nicht mit der Synchronisierungsverwaltung registriert. Wenn **"true"**, das Abonnement mit der Synchronisierungsverwaltung registriert und kann synchronisiert werden, ohne Starten des [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
`[ @ftp_address = ] 'ftp_address'` Nur für Abwärtskompatibilität.  
  
`[ @ftp_port = ] ftp_port` Nur für Abwärtskompatibilität.  
  
`[ @ftp_login = ] 'ftp_login'` Nur für Abwärtskompatibilität.  
  
`[ @ftp_password = ] 'ftp_password'` Nur für Abwärtskompatibilität.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'` Gibt den Speicherort zum Abholen der momentaufnahmedateien an. *Alternate_snapshot_folder* ist **nvarchar(255)**, hat den Standardwert NULL. Wenn dieser Wert NULL ist, werden die Momentaufnahmedateien aus dem vom Verleger angegebenen Standardspeicherort abgeholt.  
  
`[ @working_directory = ] 'working_directory'` Ist der Name des Arbeitsverzeichnisses zum temporären Speichern von Daten- und Schemadateien für die Veröffentlichung wird zum Übertragen von momentaufnahmedateien FTP verwendet. *Working_directory* ist **nvarchar(255)**, hat den Standardwert NULL.  
  
`[ @use_ftp = ] 'use_ftp'` Gibt die Verwendung an, dass FTP anstelle des normalen Protokolls zum Abrufen von Momentaufnahmen. *Use_ftp* ist **nvarchar(5)**, hat den Standardwert "false".  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]` Verwendet den interaktiven Konfliktlöser zum Lösen von Konflikten für alle Artikel, die interaktive Lösung zulassen. *Use_interactive_resolver* ist **nvarchar(5)**, hat den Standardwert "false".  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Festlegen von *Remote_agent_activation* auf einen anderen Wert als **"false"** wird ein Fehler generiert.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Festlegen von *Remote_agent_server_name* auf einen beliebigen Wert ungleich NULL wird ein Fehler generiert.  
  
`[ @job_name = ] 'job_name' ]` Ist der Name eines vorhandenen Agent-Auftrags. *Job_name* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter wird nur angegeben, wenn das Abonnement mithilfe eines vorhandenen Auftrags statt mit einem neu erstellten Auftrag (Standard) synchronisiert wird. Wenn Sie nicht Mitglied der sind die **Sysadmin** festen Serverrolle an, Sie müssen angeben, *Job_login* und *Job_password* beim Angeben von *Job_name*.  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]` Der Pfad zu dem Ordner, in dem die momentaufnahmedateien aus dem bei eine Momentaufnahme gefilterter Daten gelesen werden, ist, verwendet werden soll. *Dynamic_snapshot_location* ist **nvarchar(260)**, hat den Standardwert NULL. Weitere Informationen zu parametrisierten Zeilenfiltern finden Sie unter [Parametrisierte Zeilenfilter](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @use_web_sync = ] use_web_sync` Gibt an, dass die websynchronisierung aktiviert ist. *Use_web_sync* ist **Bit**, hat den Standardwert 0. **1** gibt an, dass das Pullabonnement mithilfe von HTTP über das Internet synchronisiert werden kann.  
  
`[ @internet_url = ] 'internet_url'` Ist der Speicherort der replikationsüberwachung (REPLISAPI. DLL) für die websynchronisierung. *Internet_url* ist **nvarchar(260)**, hat den Standardwert NULL. *Internet_url* ist eine vollqualifizierte URL im Format `http://server.domain.com/directory/replisapi.dll`. Wenn der Server so konfiguriert ist, dass er einen anderen Port als Port 80 überwacht, muss auch die Portnummer im Format `http://server.domain.com:portnumber/directory/replisapi.dll` angegeben werden, wobei `portnumber` den Port darstellt.  
  
`[ @internet_login = ] 'internet_login'` Der Anmeldename, der der Merge-Agent verwendet beim Herstellen einer Verbindung mit dem Webserver, der die websynchronisierung hostet, die HTTP-Standardauthentifizierung verwendet. *sich* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @internet_password = ] 'internet_password'` Das Kennwort, mit der Merge-Agent beim Herstellen einer Verbindung mit dem Webserver, der die websynchronisierung hostet, die HTTP-Standardauthentifizierung verwendet. *Internet_password* ist **nvarchar(524)**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode` Die Authentifizierungsmethode, die vom Merge-Agent beim Herstellen einer Verbindung mit dem Webserver während der websynchronisierung verwendet wird HTTPS verwendet werden. *Internet_security_mode* ist **Int** und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Die Standardauthentifizierung wird verwendet.|  
|**1** (Standard)|Die integrierte Windows-Authentifizierung wird verwendet.|  
  
> [!NOTE]  
>  Wir empfehlen, bei der Websynchronisierung die Standardauthentifizierung zu verwenden. Für die Websynchronisierung müssen Sie eine SSL-Verbindung mit dem Webserver herstellen. Weitere Informationen finden Sie unter [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
`[ @internet_timeout = ] internet_timeout` Ist die Zeitdauer in Sekunden, bevor eine Websynchronisierungsanforderung an. *Internet_timeout* ist **Int**, hat den Standardwert **300** Sekunden.  
  
`[ @hostname = ] 'hostname'` Überschreibt den Wert von HOST_NAME(), wenn diese Funktion in der WHERE-Klausel eines parametrisierten Filters verwendet wird. *Hostname* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @job_login = ] 'job_login'` Ist der Anmeldename für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_login* ist **nvarchar(257)**, hat keinen Standardwert. Für Agentverbindungen mit dem Abonnenten sowie für Verbindungen mit dem Verteiler und Verleger über die integrierte Windows-Authentifizierung wird stets dieses Windows-Konto verwendet.  
  
`[ @job_password = ] 'job_password'` Ist das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_password* ist **Sysname**, hat keinen Standardwert.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Für die optimale Sicherheit sollten Anmeldenamen und Kennwörter zur Laufzeit bereitgestellt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addmergepullsubscription_agent** wird bei der Mergereplikation verwendet und verwendet ähnliche Funktionen wie [Sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
 Ein Beispiel für die Sicherheitseinstellungen ordnungsgemäß angeben, für die Ausführung **Sp_addmergepullsubscription_agent**, finden Sie unter [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md).  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addmergepullsubscription_agent**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
