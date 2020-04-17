---
title: sp_addmergepullsubscription_agent (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 07cc514d615c86a90dcf37fbd4748c3ab1776f06
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528974"
---
# <a name="sp_addmergepullsubscription_agent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Fügt einen neuen Agentauftrag für die geplante Synchronisierung eines Pullabonnements mit einer Mergeveröffentlichung hinzu. Diese gespeicherte Prozedur wird auf dem Abonnenten in der Abonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @name = ] 'name'`Der Name des Agenten. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'`Der Name des Publisher-Servers. *Publisher* ist **sysname**, ohne Standard.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Publisher-Datenbank. *publisher_db* ist **sysname**, ohne Standardeinstellung.  
  
`[ @publication = ] 'publication'`Der Name der Publikation. *Publikation* ist **sysname**, ohne Standard.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Der Sicherheitsmodus, der beim Herstellen einer Verbindung mit einem Verleger beim Synchronisieren verwendet werden soll. *publisher_security_mode* ist **int**, mit einem Standardwert von 1. Wenn **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt Authentifizierung an. Wenn **1**, gibt die Windows-Authentifizierung an.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Die Anmeldung, die beim Herstellen einer Verbindung mit einem Verleger beim Synchronisieren verwendet werden soll. *publisher_login* ist **sysname**, mit dem Standardwert NULL.  
  
`[ @publisher_password = ] 'publisher_password'`Das Kennwort, das beim Herstellen einer Verbindung mit dem Verleger verwendet wird. *publisher_password* ist **sysname**, mit dem Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Sicherheitsanmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password`Das Festlegen *publisher_encrypted_password* wird nicht mehr unterstützt. Der Versuch, diesen **Bitparameter** auf **1** festzulegen, führt zu einem Fehler.  
  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Abonnent* ist **sysname**, mit dem Standardwert NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'`Der Name der Abonnementdatenbank. *subscriber_db* ist **sysname**, mit dem Standardwert NULL.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode`Der Sicherheitsmodus, der beim Herstellen einer Verbindung mit einem Abonnenten beim Synchronisieren verwendet werden soll. *subscriber_security_mode* ist **int**, mit einem Standardwert von 1. Wenn **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt Authentifizierung an. Wenn **1**, gibt die Windows-Authentifizierung an.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Der Merge-Agent verwendet für die Herstellung einer Verbindung mit dem lokalen Abonnenten stets die Windows-Authentifizierung. Falls für diesen Parameter ein Wert angegeben wird, wird zwar eine Warnmeldung zurückgegeben, doch der Wert selbst wird ignoriert.  
  
`[ @subscriber_login = ] 'subscriber_login'`Ist die Abonnentenanmeldung, die beim Herstellen einer Verbindung mit einem Abonnenten beim Synchronisieren verwendet werden soll. *subscriber_login* ist erforderlich, wenn *subscriber_security_mode* auf **0**gesetzt ist. *subscriber_login* ist **sysname**, mit dem Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Falls für diesen Parameter ein Wert angegeben wird, wird zwar eine Warnmeldung zurückgegeben, doch der Wert selbst wird ignoriert.  
  
`[ @subscriber_password = ] 'subscriber_password'`Das Abonnentenkennwort [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Authentifizierung. *subscriber_password* ist erforderlich, wenn *subscriber_security_mode* auf **0**gesetzt ist. *subscriber_password* ist **sysname**, mit dem Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Falls für diesen Parameter ein Wert angegeben wird, wird zwar eine Warnmeldung zurückgegeben, doch der Wert selbst wird ignoriert.  
  
`[ @distributor = ] 'distributor'`Der Name des Verteilers. *Distributor* ist **sysname**, mit dem Standardwert *von publisher*; D. h., der Verleger ist auch der Verteiler.  
  
`[ @distributor_security_mode = ] distributor_security_mode`Der Sicherheitsmodus, der beim Herstellen einer Verbindung mit einem Verteiler beim Synchronisieren verwendet werden soll. *distributor_security_mode* ist **int**, mit einem Standardwert von 0. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Authentifizierung an. **1** gibt die Windows-Authentifizierung an.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'`Ist die Verteileranmeldung, die beim Herstellen einer Verbindung mit einem Verteiler beim Synchronisieren verwendet werden soll. *distributor_login* ist erforderlich, wenn *distributor_security_mode* auf **0**gesetzt ist. *distributor_login* ist **sysname**, mit dem Standardwert NULL.  
  
`[ @distributor_password = ] 'distributor_password'`Das Kennwort des Verteilers. *distributor_password* ist erforderlich, wenn *distributor_security_mode* auf **0**gesetzt ist. *distributor_password* ist **sysname**, mit dem Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Sicherheitsanmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @encrypted_password = ] encrypted_password`Das Festlegen *encrypted_password* wird nicht mehr unterstützt. Der Versuch, diesen **Bitparameter** auf **1** festzulegen, führt zu einem Fehler.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der der Merge-Agent geplant werden soll. *frequency_type* ist **int**und kann einer der folgenden Werte sein.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|On-Demand-Streaming|  
|**4**|Täglich|  
|**8**|Wöchentlich|  
|**16**|Monatlich|  
|**32**|Monatlich, relativ|  
|**64**|Autostart|  
|**128**|Wiederholt|  
|NULL (Standard)||  
  
> [!NOTE]  
>  Wenn Sie einen Wert von **64** angeben, wird der Merge-Agent im kontinuierlichen Modus ausgeführt. Dies entspricht der Einstellung des Parameters **-Continuous** für den Agenten. Weitere Informationen finden Sie unter [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
`[ @frequency_interval = ] frequency_interval`Der Tag oder die Tage, die der Merge-Agent ausführt. *frequency_interval* ist **int**und kann einer dieser Werte sein.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Sonntag|  
|**2**|Montag|  
|**3**|Tuesday|  
|**4**|Wednesday|  
|**5**|Thursday|  
|**6**|Freitag|  
|**7**|Samstag|  
|**8**|Day (Tag)|  
|**9**|Wochentage|  
|**10**|Wochenendtage|  
|NULL (Standard)||  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Datum des Merge-Agenten. Dieser Parameter wird verwendet, wenn *frequency_type* auf **32** (monatlich relativ) festgelegt ist. *frequency_relative_interval* ist **int**und kann einer dieser Werte sein.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|First (Erster)|  
|**2**|Sekunde|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Last (Letzter)|  
|NULL (Standard)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der Wiederholungsfaktor, der von *frequency_type*verwendet wird. *frequency_recurrence_factor* ist **int**, mit dem Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday`Gibt an, wie oft während des definierten Zeitraums neu geplant werden soll. *frequency_subday* ist **int**und kann einer dieser Werte sein.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|Sekunde|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (Standard)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Das Intervall für *frequency_subday*. *frequency_subday_interval* ist **int**, mit dem Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Uhrzeit, zu der der Merge-Agent zum ersten Mal geplant wird, formatiert als HHMMSS. *active_start_time_of_day* ist **int**, mit dem Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Uhrzeit, zu der der Merge-Agent nicht mehr geplant wird, formatiert als HHMMSS. *active_end_time_of_day* ist **int**, mit dem Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem der Merge-Agent zum ersten Mal geplant wird, formatiert als YYYYMMDD. *active_start_date* ist **int**, mit dem Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Merge-Agent nicht mehr geplant wird, formatiert als YYYYMMDD. *active_end_date* ist **int**, mit dem Standardwert NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'`Eine optionale Eingabeaufforderung, die dem Merge-Agent bereitgestellt wird. *optional_command_line* ist **nvarchar(255)**, mit dem Standardwert ' '. Kann zur Bereitstellung zusätzlicher Parameter für den Merge-Agent verwendet werden, wie im folgenden Beispiel gezeigt wird, bei dem das Standardtimeout für Abfragen auf `600` Sekunden erhöht wird:  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid`Der Ausgabeparameter für die Auftrags-ID. *merge_jobid* ist **binary(16)**, mit dem Standardwert NULL.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'`Gibt an, ob das Abonnement über Den Windows-Synchronisierungs-Manager synchronisiert werden kann. *enabled_for_syncmgr* ist **nvarchar(5)**, mit dem Standardwert FALSE. Wenn **false**, ist das Abonnement nicht beim Synchronisierungs-Manager registriert. Wenn **true**, ist das Abonnement beim Synchronisierungs-Manager registriert und kann synchronisiert werden, ohne zu starten. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
`[ @ftp_address = ] 'ftp_address'`Nur für Abwärtskompatibilität.  
  
`[ @ftp_port = ] ftp_port`Nur für Abwärtskompatibilität.  
  
`[ @ftp_login = ] 'ftp_login'`Nur für Abwärtskompatibilität.  
  
`[ @ftp_password = ] 'ftp_password'`Nur für Abwärtskompatibilität.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'`Gibt den Speicherort an, von dem die Snapshotdateien abholt werden sollen. *alternate_snapshot_folder* ist **nvarchar(255)**, mit dem Standardwert NULL. Wenn dieser Wert NULL ist, werden die Momentaufnahmedateien aus dem vom Verleger angegebenen Standardspeicherort abgeholt.  
  
`[ @working_directory = ] 'working_directory'`Der Name des Arbeitsverzeichnisses, das zum vorübergehenden Speichern von Daten- und Schemadateien für die Publikation verwendet wird, wenn FTP zum Übertragen von Snapshotdateien verwendet wird. *working_directory* ist **nvarchar(255)**, mit dem Standardwert NULL.  
  
`[ @use_ftp = ] 'use_ftp'`Gibt die Verwendung von FTP anstelle des typischen Protokolls zum Abrufen von Snapshots an. *use_ftp* ist **nvarchar(5)**, mit dem Standardwert FALSE.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]`Verwendet interaktive resolver, um Konflikte für alle Artikel zu lösen, die eine interaktive Lösung ermöglichen. *use_interactive_resolver* ist **nvarchar(5)**, mit dem Standardwert FALSE.  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Wenn Sie *remote_agent_activation* auf einen anderen Wert als **false** festlegen, wird ein Fehler generiert.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Wenn Sie *remote_agent_server_name* auf einen beliebigen Nicht-NULL-Wert festlegen, wird ein Fehler generiert.  
  
`[ @job_name = ] 'job_name' ]`Der Name eines vorhandenen Agentenauftrags. *job_name* ist **sysname**, mit dem Standardwert NULL. Dieser Parameter wird nur angegeben, wenn das Abonnement mithilfe eines vorhandenen Auftrags statt mit einem neu erstellten Auftrag (Standard) synchronisiert wird. Wenn Sie kein Mitglied der **sysadmin** Fixed Server-Rolle sind, müssen Sie *job_login* und *job_password* angeben, wenn Sie *job_name*angeben.  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]`Der Pfad zu dem Ordner, aus dem die Snapshotdateien gelesen werden, wenn ein gefilterter Datenmomentaufnahme verwendet werden soll. *dynamic_snapshot_location* ist **nvarchar(260)**, mit dem Standardwert NULL. Weitere Informationen zu parametrisierten Zeilenfiltern finden Sie unter [Parametrisierte Zeilenfilter](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @use_web_sync = ] use_web_sync`Gibt an, dass die Websynchronisierung aktiviert ist. *use_web_sync* ist **Bit**, mit einem Standardwert von 0. **1** gibt an, dass das Pullabonnement über das Internet über HTTP synchronisiert werden kann.  
  
`[ @internet_url = ] 'internet_url'`Der Speicherort des Replikationslisteners (REPLISAPI. DLL) für die Websynchronisierung. *internet_url* ist **nvarchar(260)**, mit dem Standardwert NULL. *internet_url* ist eine vollqualifizierte URL `http://server.domain.com/directory/replisapi.dll`im Format . Wenn der Server so konfiguriert ist, dass er einen anderen Port als Port 80 überwacht, muss auch die Portnummer im Format `http://server.domain.com:portnumber/directory/replisapi.dll` angegeben werden, wobei `portnumber` den Port darstellt.  
  
`[ @internet_login = ] 'internet_login'`Die Anmeldung, die der Merge-Agent beim Herstellen einer Verbindung mit dem Webserver verwendet, der die Websynchronisierung über die HTTP-Standardauthentifizierung hostet. *internet_login* ist **sysname**, mit dem Standardwert NULL.  
  
`[ @internet_password = ] 'internet_password'`Das Kennwort, das der Merge-Agent beim Herstellen einer Verbindung mit dem Webserver verwendet, der die Websynchronisierung über die HTTP-Standardauthentifizierung hostet. *internet_password* ist **nvarchar(524)**, mit dem Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode`Die Authentifizierungsmethode, die vom Merge-Agent beim Herstellen einer Verbindung mit dem Webserver während der Websynchronisierung über HTTPS verwendet wird. *internet_security_mode* ist **int** und kann einer dieser Werte sein.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Die Standardauthentifizierung wird verwendet.|  
|**1** (Standard)|Die integrierte Windows-Authentifizierung wird verwendet.|  
  
> [!NOTE]  
>  Wir empfehlen, bei der Websynchronisierung die Standardauthentifizierung zu verwenden. Um die Websynchronisierung verwenden zu können, müssen Sie eine TLS-Verbindung mit dem Webserver herstellen. Weitere Informationen finden Sie unter [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
`[ @internet_timeout = ] internet_timeout`Die Zeitspanne in Sekunden, bevor eine Websynchronisierungsanforderung abläuft. *internet_timeout* ist **int**, mit einem Standardwert von **300** Sekunden.  
  
`[ @hostname = ] 'hostname'`Überschreibt den Wert von HOST_NAME(), wenn diese Funktion in der WHERE-Klausel eines parametrisierten Filters verwendet wird. *hostname* ist **sysname**, mit dem Standardwert NULL.  
  
`[ @job_login = ] 'job_login'`Die Anmeldung für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_login* ist **nvarchar(257)**, ohne Standard. Für Agentverbindungen mit dem Abonnenten sowie für Verbindungen mit dem Verteiler und Verleger über die integrierte Windows-Authentifizierung wird stets dieses Windows-Konto verwendet.  
  
`[ @job_password = ] 'job_password'`Das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_password* ist **sysname**, ohne Standard.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Für die optimale Sicherheit sollten Anmeldenamen und Kennwörter zur Laufzeit bereitgestellt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addmergepullsubscription_agent** wird bei der Mergereplikation verwendet und verwendet Funktionen, die [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)ähneln.  
  
 Ein Beispiel für das korrekte Angeben von Sicherheitseinstellungen beim Ausführen **sp_addmergepullsubscription_agent**finden Sie unter [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md).  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **sysadmin** Fixed Server-Rolle oder **db_owner** feste Datenbankrolle können **sp_addmergepullsubscription_agent**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Abonnieren Sie Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
