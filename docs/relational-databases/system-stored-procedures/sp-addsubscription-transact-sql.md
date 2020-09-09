---
title: sp_addsubscription (Transact-SQL) | Microsoft-Dokumentation
description: Fügt einer Veröffentlichung ein Abonnement hinzu und legt den Status des Abonnenten fest. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.
ms.date: 06/09/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.custom: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscription
- sp_addsubscription_TSQL
helpviewer_keywords:
- sp_addsubscription
ms.assetid: 61ddf287-1fa0-4c1a-8657-ced50cebf0e0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1cf622748da040060681dac848273238f73c66a5
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548338"
---
# <a name="sp_addsubscription-transact-sql"></a>sp_addsubscription (Transact-SQL)
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]

  Fügt einer Veröffentlichung ein Abonnement hinzu und legt den Status des Abonnenten fest. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addsubscription [ @publication = ] 'publication'  
    [ , [ @article = ] 'article']  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]  
        [ , [ @sync_type = ] 'sync_type' ]  
    [ , [ @status = ] 'status'  
        [ , [ @subscription_type = ] 'subscription_type' ]  
    [ , [ @update_mode = ] 'update_mode' ]  
    [ , [ @loopback_detection = ] 'loopback_detection' ]  
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
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @enabled_for_syncmgr= ] 'enabled_for_syncmgr' ]  
    [ , [ @offloadagent= ] remote_agent_activation]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
    [ , [ @distribution_job_name= ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @backupdevicetype = ] 'backupdevicetype' ]  
    [ , [ @backupdevicename = ] 'backupdevicename' ]  
    [ , [ @mediapassword = ] 'mediapassword' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @fileidhint = ] fileidhint ]  
    [ , [ @unload = ] unload ]  
    [ , [ @subscriptionlsn = ] subscriptionlsn ]  
    [ , [ @subscriptionstreams = ] subscriptionstreams ]  
    [ , [ @subscriber_type = ] subscriber_type ]  
    [ , [ @memory_optimized = ] memory_optimized ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @publication =] '*Veröffentlichung*'  
 Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 [ @article =] '*Artikel*'  
 Der Name des Artikels, für den die Veröffentlichung abonniert wird. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert all. Wird all angegeben, wird allen Artikeln dieser Veröffentlichung ein Abonnement hinzugefügt. Nur die Werte all oder NULL werden für Oracle-Verleger unterstützt.  
  
 [ @subscriber =] '*Abonnent*'  
 Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  

> [!NOTE]
> Der Server Name kann als angegeben werden `<Hostname>,<PortNumber>` . Möglicherweise müssen Sie die Portnummer für die Verbindung angeben, wenn SQL Server unter Linux oder Windows mit einem benutzerdefinierten Port bereitgestellt wird und der-Browser Dienst deaktiviert ist.
  
 [ @destination_db =] '*destination_db*'  
 Der Name der Zieldatenbank, in der die replizierten Daten gespeichert werden sollen. *destination_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn der Wert NULL ist, wird *destination_db* auf den Namen der Veröffentlichungs Datenbank festgelegt. Bei Oracle-Verlegern müssen *destination_db* angegeben werden. Geben Sie für einen nicht-SQL Server Abonnenten den Wert (Standardziel) für *destination_db*an.  
  
 [ @sync_type =] '*sync_type*'  
 Der Synchronisierungstyp des Abonnements. *sync_type* ist vom Datentyp **nvarchar (255)** und kann einen der folgenden Werte aufweisen:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|Keine|Der Abonnent besitzt bereits das Schema und die Ausgangsdaten für veröffentlichte Tabellen.<br /><br /> Hinweis: diese Option ist veraltet. Verwenden Sie stattdessen replication support only.|  
|automatic (Standard)|Das Schema und die Ausgangsdaten für veröffentlichte Tabellen werden zuerst an den Abonnenten übertragen.|  
|replication support only|Stellt auf dem Abonnenten das automatische Generieren von benutzerdefinierten gespeicherten Prozeduren für Artikel und Trigger bereit, die ggf. das Aktualisieren von Abonnements unterstützen. Setzt voraus, dass der Abonnent bereits über das Schema und die Anfangsdaten für veröffentlichte Tabellen verfügt. Stellen Sie beim Konfigurieren einer Peer-zu-Peer-Transaktionsreplikationstopologie sicher, dass die Daten in allen Knoten der Topologie identisch sind. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).<br /><br /> *Wird nicht für Abonnements von nicht SQL Server Veröffentlichungen unterstützt.*|  
|initialize with backup|Das Schema und die Ausgangsdaten für veröffentlichte Tabellen werden von einer Sicherung der Veröffentlichungsdatenbank abgerufen. Es wird davon ausgegangen, dass der Abonnent über Zugriff auf eine Sicherung der Veröffentlichungsdatenbank verfügt. Der Speicherort der Sicherung und der Medientyp für die Sicherung werden von *backupdevicename* und *backupdevicetype*angegeben. Wenn Sie diese Option verwenden, muss eine Peer-zu-Peer-Transaktionsreplikationstopologie während der Konfiguration nicht deaktiviert werden.<br /><br /> *Wird nicht für Abonnements von nicht SQL Server Veröffentlichungen unterstützt.*|  
|initialize from lsn|Wird verwendet, wenn Sie einer Peer-zu-Peer-Transaktionsreplikationstopologie einen Knoten hinzufügen. Wird mit @subscriptionlsn verwendet, um sicherzustellen, dass alle relevanten Transaktionen auf den neuen Knoten repliziert werden. Setzt voraus, dass der Abonnent bereits über das Schema und die Anfangsdaten für veröffentlichte Tabellen verfügt. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
  
> [!NOTE]  
>  Systemtabellen und Daten werden immer übertragen.  
  
 [ @status =] '*Status*'  
 Der Abonnementstatus. der *Status* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn dieser Parameter nicht explizit festgelegt wird, wird er von der Replikation automatisch auf einen der folgenden Werte festgelegt.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|aktiv|Das Abonnement wird initialisiert und ist bereit, Änderungen anzunehmen. Diese Option wird festgelegt, wenn der Wert *sync_type* auf None, initialisieren with Backup oder Replication Support Only festgelegt ist.|  
|subscribed|Das Abonnement muss initialisiert werden. Diese Option wird festgelegt, wenn der Wert *sync_type* automatisch ist.|  
  
 [ @subscription_type =] '*subscription_type*'  
 Der Abonnementtyp. *subscription_type* ist vom Datentyp **nvarchar (4)** und hat den Standardwert Push. Mögliche Werte sind push und pull. Die Verteilungs-Agents von push-Abonnements befinden sich auf dem Verteiler und die Verteilungs-Agents von pull-Abonnements auf dem Abonnenten. *subscription_type* können per Pull ein benanntes Pullabonnement erstellen, das dem Verleger bekannt ist. Weitere Informationen finden Sie unter [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md).  
  
> [!NOTE]  
>  Für anonyme Abonnements ist diese gespeicherte Prozedur nicht erforderlich.  
  
 [ @update_mode =] '*update_mode*'  
 Der Typ des Updates. *update_mode* ist vom Datentyp **nvarchar (30)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|read only (Standard)|Das Abonnement ist schreibgeschützt. Änderungen am Abonnenten werden nicht an den Verleger gesendet.|  
|sync tran|Aktiviert die Unterstützung für das sofortige Aktualisieren von Abonnements. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|queued tran|Aktiviert das verzögerte Aktualisieren über eine Warteschlange für das Abonnement. Daten können auf dem Abonnenten geändert werden; die Änderungen werden in einer Warteschlange gespeichert und an den Verleger weitergegeben. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|failover|Aktiviert das sofortige Aktualisieren für das Abonnement, wobei als Failover das verzögerte Aktualisieren über eine Warteschlange verwendet wird. Daten können auf dem Abonnenten geändert werden; die Änderungen werden sofort an den Verleger weitergegeben. Wenn der Verleger und der Abonnent nicht verbunden sind, kann der Updatemodus geändert werden, damit Datenänderungen auf dem Abonnenten in einer Warteschlange gespeichert werden, bis Abonnent und Verleger erneut verbunden sind. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|queued failover|Ermöglicht das Abonnement als Update über eine Warteschlange, mit der Möglichkeit des Wechsels zum sofortigen Updatemodus. Daten können auf dem Abonnenten geändert und in einer Warteschlange gespeichert werden, bis eine Verbindung zwischen dem Abonnenten und dem Verleger hergestellt wird. Wenn eine kontinuierliche Verbindung hergestellt wird, kann der Updatemodus in den sofortigen Updatemodus geändert werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
  
 Beachten Sie, dass die Werte synctran und Warteschlange Tran nicht zulässig sind, wenn die abonnierte Veröffentlichung DTS zulässt.  
  
 [ @loopback_detection =] '*loopback_detection*'  
 Gibt an, ob der Verteilungs-Agent Transaktionen, die vom Abonnenten stammen, zurück an den Abonnenten sendet. *loopback_detection* ist vom Datentyp **nvarchar (5)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|true|Der Verteilungs-Agent sendet Transaktionen des Abonnenten nicht an den Abonnenten zurück. Wird bei der bidirektionalen Transaktionsreplikation verwendet. Weitere Informationen finden Sie unter [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).|  
|false|Der Verteilungs-Agent sendet Transaktionen des Abonnenten an den Abonnenten zurück.|  
|NULL (Standard)|Wird für einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten automatisch auf true und für einen Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten auf false festgelegt.|  
  
 [ @frequency_type =] *frequency_type*  
 Die Häufigkeit für die Zeitplanung des Verteilungstasks. *frequency_type* ist vom Datentyp int. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|1|Einmalig|  
|2|On-Demand-Streaming|  
|4|Täglich|  
|8|Wöchentlich|  
|16|Monatlich|  
|32|Monatlich, relativ|  
|64 (Standard)|Autostart|  
|128|Wiederholt|  
  
 [ @frequency_interval =] *frequency_interval*  
 Der Wert, der auf die von *frequency_type*festgelegte Häufigkeit angewendet werden soll. *frequency_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
 [ @frequency_relative_interval =] *frequency_relative_interval*  
 Das Datum des Verteilungs-Agents. Dieser Parameter wird verwendet, wenn *frequency_type* auf 32 (monatlich, relativ) festgelegt ist. *frequency_relative_interval* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|1|First|  
|2|Sekunde|  
|4|Third|  
|8|Vierter|  
|16|Last (Letzter)|  
|NULL (Standard)||  
  
 [ @frequency_recurrence_factor =] *frequency_recurrence_factor*  
 Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
 [ @frequency_subday =] *frequency_subday*  
 Die Häufigkeit (in Minuten) für die erneute geplante Ausführung während des definierten Zeitraums. *frequency_subday* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|1|Einmalig|  
|2|Sekunde|  
|4|Minute|  
|8|Stunde|  
|NULL||  
  
 [ @frequency_subday_interval =] *frequency_subday_interval*  
 Das Intervall für die *frequency_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
 [ @active_start_time_of_day =] *active_start_time_of_day*  
 Die Tageszeit, zu der der Verteilungs-Agent zum ersten Mal geplant ist. Dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
 [ @active_end_time_of_day =] *active_end_time_of_day*  
 Die Tageszeit, ab der der Verteilungs-Agent nicht mehr geplant ist. Dabei wird das Format HHMMSS verwendet. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
 [ @active_start_date =] *active_start_date*  
 Das Datum, an dem der Verteilungs-Agent zum ersten Mal geplant ist. Dabei wird das Format JJJJMMTT verwendet. *active_start_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
 [ @active_end_date =] *active_end_date*  
 Das Datum, ab dem der Verteilungs-Agent nicht mehr geplant ist. Dabei wird das Format JJJJMMTT verwendet. *active_end_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
 [ @optional_command_line =] '*optional_command_line*'  
 Die optional auszuführende Befehlszeile. *optional_command_line* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL.  
  
 [ @reserved =] '*reserviert*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @enabled_for_syncmgr =] '*enabled_for_syncmgr*'  
 Gibt an, ob das Abonnement über die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Synchronisierungs Verwaltung von Windows synchronisiert werden kann. *enabled_for_syncmgr* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. Mit FALSE wird das Abonnement nicht bei der Windows-Synchronisierungsverwaltung registriert. Mit TRUE wird das Abonnement bei der Windows-Synchronisierungsverwaltung registriert und kann synchronisiert werden, ohne [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zu starten. Diese Option wird für Oracle-Verleger nicht unterstützt.  
  
 [ @offloadagent =] '*remote_agent_activation*'  
 Gibt an, dass eine Remoteaktivierung der Momentaufnahme möglich ist. *remote_agent_activation* ist vom Typ **Bit** und hat den Standardwert 0.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird nur noch bereitgestellt, um Abwärtskompatibilität von Skripts sicherzustellen.  
  
 [ @offloadserver =] '*remote_agent_server_name*'  
 Gibt den Netzwerknamen des Servers an, der für die Remoteaktivierung verwendet werden soll. *remote_agent_server_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
 [ @dts_package_name =] '*dts_package_name*'  
 Gibt den Namen des DTS-Pakets (Data Transformation Services) an. *dts_package_name* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL. Um z. B. ein Paket namens DTSPub_Package anzugeben, wird der Parameter `@dts_package_name = N'DTSPub_Package'` verwendet. Dieser Parameter ist für Pushabonnements verfügbar. Verwenden Sie sp_addpullsubscription_agent, um einem Pullabonnement DTS-Paketinformationen hinzuzufügen.  
  
 [ @dts_package_password =] '*dts_package_password*'  
 Gibt gegebenenfalls das Kennwort des Pakets an. *dts_package_password* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Wenn *dts_package_name* angegeben ist, müssen Sie ein Kennwort angeben.  
  
 [ @dts_package_location =] '*dts_package_location*'  
 Gibt den Paketspeicherort an. *dts_package_location* ist vom Datentyp **nvarchar (12)** und hat den Standardwert Distributor. Der Speicherort des Pakets kann distributor oder subscriber sein.  
  
 [ @distribution_job_name =] '*distribution_job_name*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @publisher =] '*Verleger*'  
 Gibt einen nicht-- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* darf nicht für einen Verleger angegeben werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 [ @backupdevicetype =] '*backupabvicetype*'  
 Gibt den Sicherungsmedientyp an, der beim Initialisieren eines Abonnenten von einer Sicherung verwendet wird. *backupabvicetype* ist vom Datentyp **nvarchar (20)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|logical (Standard)|Das Sicherungsmedium ist ein logisches Medium.|  
|disk|Das Sicherungsmedium ist ein Laufwerk.|  
|tape|Das Sicherungsmedium ist ein Bandlaufwerk.|  
  
 *backupabvicetype* wird nur verwendet, wenn *sync_method*auf initialize_with_backup festgelegt ist.  
  
 [ @backupdevicename =] '*backupdevicename*'  
 Gibt den Namen des Sicherungsmediums an, das beim Initialisieren eines Abonnenten von einer Sicherung verwendet wird. *backupdevicename* ist vom Datentyp **nvarchar (1000)** und hat den Standardwert NULL.  
  
 [ @mediapassword =] '*Media Password*'  
 Gibt ein Kennwort für den Mediensatz an, falls beim Formatieren des Mediums ein Kennwort festgelegt wurde. *Media Password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 [ @password =] '*Kennwort*'  
 Gibt ein Kennwort für die Sicherung an, falls beim Erstellen der Sicherung ein Kennwort festgelegt wurde. *Password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
 [ @fileidhint =] " *fleidhint* "  
 Identifiziert einen Ordnungswert des wiederherzustellenden Sicherungssatzes. der " *fleidhint* " ist vom Datentyp **int**und hat den Standardwert NULL.  
  
 [ @unload =] *entladen*  
 Gibt an, ob ein Datensicherungsmedium nach Abschluss der Initialisierung von der Sicherung entladen werden soll. *entladen* ist vom Typ **Bit**und hat den Standardwert 1. 1 gibt an, dass das Band entladen werden soll. Das *entladen* wird nur dann verwendet, wenn *backupabvicetype* ein Band ist.  
  
 [ @subscriptionlsn =] *Abonnement-LSN*  
 Gibt die Protokollfolgenummer (LSN, Log Sequence Number) an, bei der ein Abonnement beginnen soll, Änderungen an einen Knoten in einer Peer-zu-Peer-Transaktionsreplikationstopologie zu übermitteln. Wird mit dem @sync_type Wert initialisieren from LSN verwendet, um sicherzustellen, dass alle relevanten Transaktionen auf einem neuen Knoten repliziert werden. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 [ @subscriptionstreams =] *Abonnement Datenströme*  
 Die Anzahl zulässiger Verbindungen pro Verteilungs-Agent, um Änderungsbatches parallel auf einen Abonnenten anzuwenden, während viele Transaktionsmerkmale beibehalten werden, die bei Verwendung eines einzigen Threads vorhanden sind. " *Abonnement Ströme* " ist vom Datentyp **tinyint**und hat den Standardwert NULL. Mögliche Werte zwischen 1 und 64 werden unterstützt. Dieser Parameter wird für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten, Oracle-Verleger oder Peer-zu-Peer-Abonnements nicht unterstützt. Bei Verwendung von subscriptionstreams werden der msreplication_subscriptions-Tabelle zusätzliche Zeilen (eine pro Datenstrom) hinzugefügt, wobei die agent_id auf NULL festgelegt ist.  
  
> [!NOTE]  
>  subscriptionstreams [!INCLUDE[tsql](../../includes/tsql-md.md)]kann nicht für Artikel verwendet werden, die für die Übermittlung von  konfiguriert sind. Um subscriptionstreams zu verwenden, konfigurieren Sie Artikel stattdessen für die Übermittlung von Aufrufen gespeicherter Prozeduren.  
  
 [ @subscriber_type =] *subscriber_type*  
 Der Typ des Abonnenten. *subscriber_type* ist vom Datentyp **tinyint**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|0 (Standard)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten|  
|1|ODBC-Datenquellenserver|  
|2|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet-Datenbank|  
|3|OLE DB-Anbieter|  
  
 [ @memory_optimized =] *memory_optimized*  
 Gibt an, dass das Abonnement Speicher optimierte Tabellen unterstützt. *memory_optimized* ist " **Bit**", wobei "1" true ist (das Abonnement unterstützt Speicher optimierte Tabellen).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 sp_addsubscription wird bei der Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 Wenn sp_addsubscription von einem Mitglied der festen Serverrolle sysadmin ausgeführt wird, um ein Pushabonnement zu erstellen, wird der Auftrag des Verteilungs-Agents implizit erstellt und unter dem Konto des SQL Server-Agent-Diensts ausgeführt. Es wird empfohlen, [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) auszuführen und die Anmelde Informationen eines anderen, agentspezifischen Windows-Kontos für @job_login und anzugeben @job_password . Weitere Informationen finden Sie unter [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 sp_addsubscription hindert ODBC- und OLE DB-Abonnenten am Zugriff auf folgende Veröffentlichungen:  
  
-   Wurde mit dem systemeigenen *sync_method* im [sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)aufgerufen.  
  
-   Enthält Artikel, die der Veröffentlichung mit der gespeicherten Prozedur [sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) hinzugefügt wurden, die den *pre_creation_cmd* -Parameterwert 3 (TRUNCATE) enthielt.  
  
-   Es wurde versucht, *update_mode* auf Sync Tran festzulegen.  
  
-   Veröffentlichungen, bei denen ein Artikel für die Verwendung parametrisierter Anweisungen konfiguriert ist.  
  
 Wenn für eine Veröffentlichung die *allow_queued_tran* -Option auf true festgelegt ist (wodurch Änderungen auf dem Abonnenten in die Warteschlange eingereiht werden können, bis Sie auf dem Verleger angewendet werden können), wird die Zeitstempel-Spalte in einem Artikel als **Zeitstempel**geschrieben, und Änderungen an dieser Spalte werden an den Abonnenten gesendet. Der Abonnent generiert und aktualisiert den Wert der timestamp-Spalte. Bei einem ODBC-oder OLE DB-Abonnenten schlägt sp_addsubscription fehl, wenn versucht wird, eine Veröffentlichung zu abonnieren, bei der *allow_queued_tran* auf true festgelegt ist, und Artikel mit Zeitstempel-Spalten darin.  
  
 Wenn ein Abonnement kein DTS-Paket verwendet, kann es keine Veröffentlichung abonnieren, die auf *allow_transformable_subscriptions*festgelegt ist. Wenn die Tabelle der Veröffentlichung für ein DTS-Abonnement und ein Nicht-DTS-Abonnement repliziert werden muss, müssen zwei separate Veröffentlichungen erstellt werden: eine für jeden Abonnementtyp.  
  
 Bei Auswahl der **sync_type** -Optionen *replication support only*, *initialize with backup*oder *initialize from lsn*muss der Protokolllese-Agent ausgeführt werden, nachdem **sp_addsubscription**ausgeführt wurde, damit die festgelegten Skripts in die Verteilungsdatenbank geschrieben werden. Der Protokolllese-Agent muss unter einem Konto ausgeführt werden, das Mitglied der festen Serverrolle **sysadmin** ist. Wenn die **sync_type** -Option auf *Automatic*festgelegt wird, sind keine speziellen Aktionen für den Protokollleser-Agent erforderlich.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle sysadmin oder der festen Datenbankrolle db_owner können sp_addsubscription ausführen. Für Pullabonnements können Benutzer, deren Anmeldename in der Veröffentlichungszugriffsliste eingetragen ist, sp_addsubscription ausführen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addsubscription-trans_1.sql)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Erstellen eines Abonnements für einen Nicht-SQL Server-Abonnenten](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpushsubscription_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
