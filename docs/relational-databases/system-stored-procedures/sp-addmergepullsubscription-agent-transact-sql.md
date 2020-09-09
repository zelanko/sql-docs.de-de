---
description: sp_addmergepullsubscription_agent (Transact-SQL)
title: sp_addmergepullsubscription_agent (Transact-SQL) | Microsoft-Dokumentation
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7ad9425df176a7f822b18ab793d0eada4362c551
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89530114"
---
# <a name="sp_addmergepullsubscription_agent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Fügt einen neuen Agentauftrag für die geplante Synchronisierung eines Pullabonnements mit einer Mergeveröffentlichung hinzu. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
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
`[ @name = ] 'name'` Der Name des Agents. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'` Der Name des Verleger Servers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Der Sicherheitsmodus, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verleger verwendet wird. *publisher_security_mode* ist vom Datentyp **int**und hat den Standardwert 1. Bei **0**wird die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung angegeben. Wenn der **1**ist, wird die Windows-Authentifizierung angegeben.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Der Anmelde Name, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verleger verwendet wird. *publisher_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @publisher_password = ] 'publisher_password'` Das Kennwort, das beim Herstellen einer Verbindung mit dem Verleger verwendet wird. *publisher_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Sicherheitsanmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password` Das Festlegen von *publisher_encrypted_password* wird nicht mehr unterstützt. Der Versuch, diesen **Bit** -Parameter auf **1** festzulegen, führt zu einem Fehler.  
  
`[ @subscriber = ] 'subscriber'` Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'` Der Name der Abonnement Datenbank. *subscriber_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` Der Sicherheitsmodus, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Abonnenten verwendet wird. *subscriber_security_mode* ist vom Datentyp **int**und hat den Standardwert 1. Bei **0**wird die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung angegeben. Wenn der **1**ist, wird die Windows-Authentifizierung angegeben.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Der Merge-Agent verwendet für die Herstellung einer Verbindung mit dem lokalen Abonnenten stets die Windows-Authentifizierung. Falls für diesen Parameter ein Wert angegeben wird, wird zwar eine Warnmeldung zurückgegeben, doch der Wert selbst wird ignoriert.  
  
`[ @subscriber_login = ] 'subscriber_login'` Der Anmelde Name des Abonnenten, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Abonnenten verwendet wird. *subscriber_login* ist erforderlich, wenn *subscriber_security_mode* auf **0**festgelegt ist. *subscriber_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Falls für diesen Parameter ein Wert angegeben wird, wird zwar eine Warnmeldung zurückgegeben, doch der Wert selbst wird ignoriert.  
  
`[ @subscriber_password = ] 'subscriber_password'` Das Kennwort des Abonnenten für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. *subscriber_password* ist erforderlich, wenn *subscriber_security_mode* auf **0**festgelegt ist. *subscriber_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Falls für diesen Parameter ein Wert angegeben wird, wird zwar eine Warnmeldung zurückgegeben, doch der Wert selbst wird ignoriert.  
  
`[ @distributor = ] 'distributor'` Der Name des Verteilers. *Distributor* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist *Publisher*. Das heißt, der Verleger ist auch der Verteiler.  
  
`[ @distributor_security_mode = ] distributor_security_mode` Der Sicherheitsmodus, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verteiler verwendet wird. *distributor_security_mode* ist vom Datentyp **int**und hat den Standardwert 0. **0** gibt die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung an. **1** gibt die Windows-Authentifizierung an.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` Der Verteiler Anmelde Name, der beim Synchronisieren zum Herstellen einer Verbindung mit einem Verteiler verwendet wird. *distributor_login* ist erforderlich, wenn *distributor_security_mode* auf **0**festgelegt ist. *distributor_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @distributor_password = ] 'distributor_password'` Das Verteiler Kennwort. *distributor_password* ist erforderlich, wenn *distributor_security_mode* auf **0**festgelegt ist. *distributor_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Sicherheitsanmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @encrypted_password = ] encrypted_password` Das Festlegen von *encrypted_password* wird nicht mehr unterstützt. Der Versuch, diesen **Bit** -Parameter auf **1** festzulegen, führt zu einem Fehler.  
  
`[ @frequency_type = ] frequency_type` Die Häufigkeit, mit der die Merge-Agent geplant werden soll. *frequency_type* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
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
>  Das Angeben des Werts **64** bewirkt, dass die Merge-Agent im kontinuierlichen Modus ausgeführt wird. Dies entspricht dem Festlegen des **-Continuous-** Parameters für den Agent. Weitere Informationen finden Sie unter [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
`[ @frequency_interval = ] frequency_interval` Der Tag oder die Tage, an denen die Merge-Agent ausgeführt wird. *frequency_interval* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Sonntag|  
|**2**|Montag|  
|**3**|Tuesday|  
|**4**|Wednesday|  
|**5**|Thursday|  
|**6**|Freitag|  
|**7**|Samstag|  
|**8**|Tag|  
|**9**|Wochentage|  
|**10**|Wochenendtage|  
|NULL (Standard)||  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Das Datum der Merge-Agent. Dieser Parameter wird verwendet, wenn *frequency_type* auf **32** (monatlich, relativ) festgelegt ist. *frequency_relative_interval* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|First|  
|**2**|Sekunde|  
|**4**|Third|  
|**8**|Vierter|  
|**16**|Last (Letzter)|  
|NULL (Standard)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday` Gibt an, wie oft innerhalb des definierten Zeitraums neu geplant werden soll. *frequency_subday* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|Sekunde|  
|**4**|Minute|  
|**8**|Stunde|  
|NULL (Standard)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für die *frequency_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit, zu der die Merge-Agent zum ersten Mal geplant ist. dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, zu der die Merge-Agent nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an dem die Merge-Agent zum ersten Mal geplant ist, formatiert als YYYYMMDD. *active_start_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date` Das Datum, an dem der Merge-Agent nicht mehr geplant ist, formatiert als YYYYMMDD. *active_end_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'` Ist eine optionale Eingabeaufforderung, die für die Merge-Agent bereitgestellt wird. *optional_command_line* ist vom Datentyp **nvarchar (255)**. der Standardwert ist "". Kann zur Bereitstellung zusätzlicher Parameter für den Merge-Agent verwendet werden, wie im folgenden Beispiel gezeigt wird, bei dem das Standardtimeout für Abfragen auf `600` Sekunden erhöht wird:  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid` Der Output-Parameter für die Auftrags-ID. *merge_jobid* ist **Binary (16)** und hat den Standardwert NULL.  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Gibt an, ob das Abonnement über die Synchronisierungs Verwaltung von Windows synchronisiert werden kann. *enabled_for_syncmgr* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. Wenn der Wert **false**ist, wird das Abonnement nicht bei der Synchronisierungs Verwaltung registriert. Wenn der Wert **true**ist, wird das Abonnement bei der Synchronisierungs Verwaltung registriert und kann synchronisiert werden, ohne zu starten [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
`[ @ftp_address = ] 'ftp_address'` Nur aus Gründen der Abwärtskompatibilität.  
  
`[ @ftp_port = ] ftp_port` Nur aus Gründen der Abwärtskompatibilität.  
  
`[ @ftp_login = ] 'ftp_login'` Nur aus Gründen der Abwärtskompatibilität.  
  
`[ @ftp_password = ] 'ftp_password'` Nur aus Gründen der Abwärtskompatibilität.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'` Gibt den Speicherort an, von dem die Momentaufnahme Dateien abgerufen werden sollen. *alternate_snapshot_folder* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Wenn dieser Wert NULL ist, werden die Momentaufnahmedateien aus dem vom Verleger angegebenen Standardspeicherort abgeholt.  
  
`[ @working_directory = ] 'working_directory'` Der Name des Arbeitsverzeichnisses, das zum vorübergehenden Speichern von Daten-und Schema Dateien für die Veröffentlichung verwendet wird, wenn FTP zum Übertragen von Momentaufnahme Dateien verwendet wird. *working_directory* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @use_ftp = ] 'use_ftp'` Gibt an, dass FTP anstelle des üblichen Protokolls zum Abrufen von Momentaufnahmen verwendet wird. *use_ftp* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]` Verwendet den interaktiven Konflikt Löser, um Konflikte für alle Artikel aufzulösen, die eine interaktive Auflösung ermöglichen. *use_interactive_resolver* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Wenn Sie *remote_agent_activation* auf einen anderen Wert als **false** festlegen, wird ein Fehler generiert.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Wenn Sie *remote_agent_server_name* auf einen nicht-NULL-Wert festlegen, wird ein Fehler generiert.  
  
`[ @job_name = ] 'job_name' ]` Der Name eines vorhandenen Agentauftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter wird nur angegeben, wenn das Abonnement mithilfe eines vorhandenen Auftrags statt mit einem neu erstellten Auftrag (Standard) synchronisiert wird. Wenn Sie kein Mitglied der festen Server Rolle **sysadmin** sind, müssen Sie *job_login* und *job_password* angeben, wenn Sie *job_name*angeben.  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]` Der Pfad zu dem Ordner, aus dem die Momentaufnahme Dateien gelesen werden, wenn eine gefilterte Daten Momentaufnahme verwendet werden soll. *dynamic_snapshot_location* ist vom Datentyp **nvarchar (260)** und hat den Standardwert NULL. Weitere Informationen zu parametrisierten Zeilenfiltern finden Sie unter [Parametrisierte Zeilenfilter](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @use_web_sync = ] use_web_sync` Gibt an, dass die Websynchronisierung aktiviert ist. *use_web_sync* ist vom Typ **Bit**. der Standardwert ist 0. **1** gibt an, dass das Pullabonnement mithilfe von http über das Internet synchronisiert werden kann.  
  
`[ @internet_url = ] 'internet_url'` Der Speicherort des Replikations-Listener (REPLISAPI.DLL) für die Websynchronisierung. *internet_url* ist vom Datentyp **nvarchar (260)** und hat den Standardwert NULL. *internet_url* ist eine voll qualifizierte URL im Format `http://server.domain.com/directory/replisapi.dll` . Wenn der Server so konfiguriert ist, dass er einen anderen Port als Port 80 überwacht, muss auch die Portnummer im Format `http://server.domain.com:portnumber/directory/replisapi.dll` angegeben werden, wobei `portnumber` den Port darstellt.  
  
`[ @internet_login = ] 'internet_login'` Der Anmelde Name, den der Merge-Agent verwendet, wenn eine Verbindung mit dem Webserver hergestellt wird, der die Websynchronisierung mithilfe der http-Standard Authentifizierung verwendet. *internet_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @internet_password = ] 'internet_password'` Das Kennwort, das der Merge-Agent verwendet, wenn eine Verbindung mit dem Webserver hergestellt wird, der die Websynchronisierung mithilfe der http-Standard Authentifizierung verwendet. *internet_password* ist vom Datentyp **nvarchar (524)** und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode` Die beim Herstellen einer Verbindung mit dem Webserver während der Websynchronisierung mithilfe Merge-Agent von HTTPS verwendete Authentifizierungsmethode. *internet_security_mode* ist vom Datentyp **int** und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Die Standardauthentifizierung wird verwendet.|  
|**1** (Standard)|Die integrierte Windows-Authentifizierung wird verwendet.|  
  
> [!NOTE]  
>  Wir empfehlen, bei der Websynchronisierung die Standardauthentifizierung zu verwenden. Um die Websynchronisierung zu verwenden, müssen Sie eine TLS-Verbindung mit dem Webserver herstellen. Weitere Informationen finden Sie unter [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
`[ @internet_timeout = ] internet_timeout` Die Zeitdauer in Sekunden, bevor eine Websynchronisierungs Anforderung abläuft. *internet_timeout* ist vom Datentyp **int**und hat den Standardwert **300** Sekunden.  
  
`[ @hostname = ] 'hostname'` Überschreibt den Wert von HOST_NAME (), wenn diese Funktion in der WHERE-Klausel eines parametrisierten Filters verwendet wird. der *Hostname* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @job_login = ] 'job_login'` Der Anmelde Name für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_login* ist vom Datentyp **nvarchar (257)** und hat keinen Standardwert. Für Agentverbindungen mit dem Abonnenten sowie für Verbindungen mit dem Verteiler und Verleger über die integrierte Windows-Authentifizierung wird stets dieses Windows-Konto verwendet.  
  
`[ @job_password = ] 'job_password'` Das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Für die optimale Sicherheit sollten Anmeldenamen und Kennwörter zur Laufzeit bereitgestellt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addmergepullsubscription_agent** wird bei der Mergereplikation verwendet und verwendet ähnliche Funktionen wie [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md).  
  
 Ein Beispiel für die ordnungsgemäße Angabe von Sicherheitseinstellungen beim Ausführen **sp_addmergepullsubscription_agent**finden Sie unter [Erstellen eines](../../relational-databases/replication/create-a-pull-subscription.md)Pullabonnements.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addmergepullsubscription_agent**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
