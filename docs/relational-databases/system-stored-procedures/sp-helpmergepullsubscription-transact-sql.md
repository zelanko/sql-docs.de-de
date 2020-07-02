---
title: sp_helpmergepullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepullsubscription
- sp_helpmergepullsubscription_TSQL
helpviewer_keywords:
- sp_helpmergepullsubscription
ms.assetid: 6f3125f3-0dfa-40bd-b725-8aa1591234f6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e0abc3934e1cfec8e37a4b1f3060a7aeef38a06e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85626940"
---
# <a name="sp_helpmergepullsubscription-transact-sql"></a>sp_helpmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu Pullabonnements zurück, die auf einem Abonnenten vorhanden sind. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergepullsubscription [ [ @publication=] 'publication']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
```  
  
## <a name="argument"></a>Argument  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **%** . Wenn *Publication* **%** den Wert hat, werden Informationen zu allen Mergeveröffentlichungen und Abonnements in der aktuellen Datenbank zurückgegeben.  
  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher*ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **%** .  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Verleger Datenbank. *publisher_db*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert **%** .  
  
`[ @subscription_type = ] 'subscription_type'`Gibt an, ob Pullabonnements angezeigt werden. *subscription_type*ist vom Datentyp **nvarchar (10)** und hat **den**Standardwert Pull. Gültige Werte sind **' Push '**, **' Pull '** oder **' both '**.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**nvarchar (1000)**|Name des Abonnements.|  
|**ung**|**sysname**|Name der Veröffentlichung.|  
|**publisher**|**sysname**|Name des Verlegers.|  
|**publisher_db**|**sysname**|Name der Verlegerdatenbank.|  
|**Abonnenten**|**sysname**|Der Name des Abonnenten.|  
|**subscription_db**|**sysname**|Name der Abonnementdatenbank.|  
|**status**|**int**|Abonnementstatus:<br /><br /> **0** = inaktives Abonnement<br /><br /> **1** = aktives Abonnement<br /><br /> **2** = gelöschtes Abonnement<br /><br /> **3** = getrenntes Abonnement<br /><br /> **4** = angefügtes Abonnement<br /><br /> **5** = Abonnement wurde für die erneute Initialisierung mit Upload gekennzeichnet<br /><br /> **6** = Anfügen des Abonnements fehlgeschlagen<br /><br /> **7** = aus der Sicherung wiederhergestellte Abonnements|  
|**subscriber_type**|**int**|Typ des Abonnenten:<br /><br /> **1** = Global<br /><br /> **2** = lokal<br /><br /> **3** = anonym|  
|**subscription_type**|**int**|Typ des Abonnements:<br /><br /> **0** = Push<br /><br /> **1** = Pull<br /><br /> **2** = anonym|  
|**haben**|**float (8)**|Abonnementpriorität. Der Wert muss kleiner als **100,00**sein.|  
|**sync_type**|**tinyint**|Synchronisierungsart des Abonnements:<br /><br /> **1** = automatisch<br /><br /> **2** = Momentaufnahme wird nicht verwendet.|  
|**description**|**nvarchar(255)**|Kurze Beschreibung des Pullabonnements.|  
|**merge_jobid**|**Binary (16)**|Auftrags-ID des Merge-Agents.|  
|**enabled_for_syncmgr**|**int**|Zeigt an, ob das Abonnement über die Synchronisierungsverwaltung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] synchronisiert werden kann.|  
|**last_updated**|**nvarchar (26)**|Zeitpunkt, zu dem der Merge-Agent das Abonnement zuletzt erfolgreich synchronisiert hat.|  
|**publisher_login**|**sysname**|Anmeldename des Verlegers.|  
|**publisher_password**|**sysname**|Kennwort des Verlegers.|  
|**publisher_security_mode**|**int**|Gibt den Sicherheitsmodus des Verlegers an:<br /><br /> **0** -  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung<br /><br /> **1** = Windows-Authentifizierung|  
|**Verleih**|**sysname**|Name des Verteilers.|  
|**distributor_login**|**sysname**|Anmeldename des Verteilers.|  
|**distributor_password**|**sysname**|Das Verteiler Kennwort.|  
|**distributor_security_mode**|**int**|Gibt den Sicherheitsmodus des Verteilers an:<br /><br /> **0** -  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung<br /><br /> **1** = Windows-Authentifizierung|  
|**ftp_address**|**sysname**|Nur aus Gründen der Abwärtskompatibilität verfügbar. Die Netzwerkadresse des FTP-Dienstanbieter (File Transfer Protocol) für den Verteiler.|  
|**ftp_port**|**int**|Nur aus Gründen der Abwärtskompatibilität verfügbar. Die Anschlussnummer des FTP-Diensts für den Verteiler.|  
|**ftp_login**|**sysname**|Nur aus Gründen der Abwärtskompatibilität verfügbar. Der Benutzername, mit dem eine Verbindung zum FTP-Dienst hergestellt wird.|  
|**ftp_password**|**sysname**|Nur aus Gründen der Abwärtskompatibilität verfügbar. Das Benutzerkennwort, mit dem eine Verbindung zum FTP-Dienst hergestellt wird.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Der Speicherort des Momentaufnahmeordners, wenn dies nicht der standardmäßige Speicherort ist oder ein zusätzlicher Speicherort zum Standardspeicherort vorhanden ist.|  
|**working_directory**|**nvarchar(255)**|Der vollqualifizierte Pfad zum Verzeichnis, in das die Momentaufnahmedateien mithilfe von FTP übertragen werden, wenn diese Option angegeben ist.|  
|**use_ftp**|**bit**|Das Abonnement abonniert die Veröffentlichung über die konfigurierten Internet- und FTP-Adressierungseigenschaften. Wenn der Wert **0**ist, verwendet das Abonnement nicht FTP. Bei **1**verwendet das Abonnement FTP.|  
|**offload_agent**|**bit**|Gibt an, ob eine Remotaktivierung und -ausführung der Momentaufnahme möglich ist. Wenn der Wert **0**ist, kann der Agent nicht remote aktiviert werden.|  
|**offload_server**|**sysname**|Name des Servers, der für die Remoteaktivierung verwendet wird.|  
|**use_interactive_resolver**|**int**|Gibt zurück, ob der interaktive Konfliktlöser während der Konfliktlösung verwendet wird. Wenn der Wert **0**ist, wird der interaktive Konflikt Löser nicht verwendet.|  
|**subid**|**uniqueidentifier**|ID des Abonnenten.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Der Pfad zu dem Ordner, in dem die Momentaufnahmedateien gespeichert werden.|  
|**last_sync_status**|**int**|Synchronisierungsstatus:<br /><br /> **1** = wird gestartet<br /><br /> **2** = erfolgreich<br /><br /> **3** = in Bearbeitung<br /><br /> **4** = im Leerlauf<br /><br /> **5** = Wiederholungsversuch nach einem vorherigen Fehler<br /><br /> **6** = fehlgeschlagen<br /><br /> **7** = Fehler bei der Überprüfung<br /><br /> **8** = Überprüfung erfolgreich<br /><br /> **9** = Herunterfahren angefordert|  
|**last_sync_summary**|**sysname**|Beschreibung der letzten Synchronisierungsergebnisse.|  
|**use_web_sync**|**bit**|Gibt an, ob das Abonnement über HTTPS synchronisiert werden kann, wobei der Wert **1** bedeutet, dass diese Funktion aktiviert ist.|  
|**internet_url**|**nvarchar(260)**|URL, die den Speicherort des Replikations-Listener für die Websynchronisierung darstellt.|  
|**internet_login**|**nvarchar(128)**|Der Anmeldename, der vom Merge-Agent zum Herstellen einer Verbindung mit dem Webserver verwendet wird, der die Websynchronisierung mithilfe der Standardauthentifizierung hostet.|  
|**internet_password**|**nvarchar (524)**|Das Kennwort für den Anmeldenamen, der vom Merge-Agent zum Herstellen einer Verbindung mit dem Webserver verwendet wird, der die Websynchronisierung mithilfe der Standardauthentifizierung hostet.|  
|**internet_security_mode**|**int**|Der verwendete Authentifizierungsmodus beim Herstellen einer Verbindung mit dem Webserver, der die Websynchronisierung hostet. Der Wert **1** steht für die Windows-Authentifizierung und der Wert **0** für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**internet_timeout**|**int**|Zeit in Sekunden, bevor eine Anforderung für eine Websynchronisierung abläuft.|  
|**hostname**|**nvarchar(128)**|Gibt einen überladenen Wert für [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) an, wenn diese Funktion in der WHERE-Klausel eines parametrisierten Zeilen Filters verwendet wird.|  
|**job_login**|**nvarchar(512)**|Das Windows-Konto, unter dem der Merge-Agent ausgeführt wird, der im Format *Domäne* \\ *Benutzername*zurückgegeben wird.|  
|**job_password**|**sysname**|Aus Sicherheitsgründen wird immer der Wert " **\*\*\*\*\*\*\*\*\*\*** " zurückgegeben.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helpmergepullsubscription** wird bei der Mergereplikation verwendet. Im Resultset wird das in **last_updated** zurückgegebene Datum als *YYYYMMDD hh: mm: SS. fff*formatiert.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** und der festen Daten Bank Rolle **db_owner** können **sp_helpmergepullsubscription**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
