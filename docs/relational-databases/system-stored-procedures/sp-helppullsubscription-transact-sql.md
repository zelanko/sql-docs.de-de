---
title: sp_helppullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppullsubscription_TSQL
- sp_helppullsubscription
helpviewer_keywords:
- sp_helppullsubscription
ms.assetid: a0d9c3f1-1fe9-497c-8e2f-5b74f47a7346
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1ab2afba10ff754b5bd99d36df02d642cc5c6bb0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771436"
---
# <a name="sp_helppullsubscription-transact-sql"></a>sp_helppullsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Zeigt Informationen zu einem oder mehreren Abonnements auf dem Abonnenten an. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helppullsubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @show_push = ] 'show_push' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Remote Servers. *Publisher* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert, mit dem Informationen für alle Verleger zurückgegeben werden.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Verleger Datenbank. *publisher_db* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert, mit dem alle Verleger Datenbanken zurückgegeben werden.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert, mit dem alle Veröffentlichungen zurückgegeben werden. Wenn dieser Parameter dem Wert all entspricht, werden nur Pullabonnements mit independent_agent = **0** zurückgegeben.  
  
`[ @show_push = ] 'show_push'`Gibt an, ob alle Pushabonnements zurückgegeben werden sollen. *show_push*ist vom Datentyp **nvarchar (5)** und hat den Standardwert false, bei dem keine Pushabonnements zurückgegeben werden.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Gebers**|**sysname**|Name des Verlegers.|  
|**Verlegerdatenbank**|**sysname**|Name der Verlegerdatenbank.|  
|**ung**|**sysname**|Name der Veröffentlichung.|  
|**independent_agent**|**bit**|Zeigt an, ob ein Verteilungs-Agent im Einzelplatzmodus für diese Veröffentlichung vorhanden ist.|  
|**Abonnementtyp**|**int**|Abonnementtyp für die Veröffentlichung.|  
|**Verteilungs-Agent**|**nvarchar (100)**|Verteilungs-Agent für die Verarbeitung des Abonnements.|  
|**publication description**|**nvarchar(255)**|Die Beschreibung der Veröffentlichung.|  
|**last updating time**|**date**|Zeitpunkt, zu dem die Abonnementinformationen aktualisiert wurden. Dies ist eine UNICODE-Zeichenfolge aus ISO-Datum (114) + ODBC-Zeit (121). Das Format ist yyyymmdd hh:mi:sss.mmm, wobei yyyy das Jahr, mm den Monat, dd den Tag, hh die Stunde, mi die Minute, sss die Sekunden und mmm die Millisekunden angibt.|  
|**Abonnement Name**|**varchar (386)**|Name des Abonnements.|  
|**Zeitstempel der letzten Transaktion**|**varbinary(16)**|Timestamp der letzten replizierten Transaktion.|  
|**Aktualisierungs Modus**|**tinyint**|Zulässige Updatetypen.|  
|**distribution agent job_id**|**int**|Auftrags-ID des Verteilungs-Agents.|  
|**enabled_for_synmgr**|**int**|Zeigt an, ob das Abonnement über die Synchronisierungsverwaltung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] synchronisiert werden kann.|  
|**subscription guid**|**Binary (16)**|Globaler Bezeichner für die Version des Abonnements für die Veröffentlichung.|  
|**subid**|**Binary (16)**|Globaler Bezeichner für ein anonymes Abonnement.|  
|**immediate_sync**|**bit**|Gibt an, ob die Synchronisierungsdateien bei jeder Ausführung des Momentaufnahme-Agents erstellt oder neu erstellt werden.|  
|**Verleger Anmeldung**|**sysname**|Auf dem Verleger für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendete Anmelde-ID.|  
|**publisher password**|**nvarchar (524)**|Das Kennwort (verschlüsselt), das auf dem Verleger für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendet wird.|  
|**publisher security_mode**|**int**|Auf dem Verleger implementierter Sicherheitsmodus:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung<br /><br /> **1** = Windows-Authentifizierung<br /><br /> **2** = die Synchronisierungs Trigger verwenden einen statischen **sysservers** -Eintrag für Remote Prozedur Aufrufe (RPC), und der *Herausgeber* muss in der **sysservers** -Tabelle als Remote Server oder Verbindungs Server definiert sein.|  
|**Verleih**|**sysname**|Name des Verteilers.|  
|**distributor_login**|**sysname**|Auf dem Verteiler für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendete Anmelde-ID.|  
|**distributor_password**|**nvarchar (524)**|Kennwort (verschlüsselt), das auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verteiler für die Authentifizierung verwendet wird.|  
|**distributor_security_mode**|**int**|Auf dem Verteiler implementierter Sicherheitsmodus:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung<br /><br /> **1** = Windows-Authentifizierung|  
|**ftp_address**|**sysname**|Nur aus Gründen der Abwärtskompatibilität beibehalten|  
|**ftp_port**|**int**|Nur aus Gründen der Abwärtskompatibilität beibehalten|  
|**ftp_login**|**sysname**|Nur aus Gründen der Abwärtskompatibilität beibehalten|  
|**ftp_password**|**nvarchar (524)**|Nur aus Gründen der Abwärtskompatibilität beibehalten|  
|**alt_snapshot_folder**|**nvarchar(255)**|Der Speicherort des Momentaufnahmeordners, wenn dies nicht der standardmäßige Speicherort ist oder ein zusätzlicher Speicherort zum Standardspeicherort vorhanden ist.|  
|**working_directory**|**nvarchar(255)**|Der vollgekennzeichnete Pfad zum Verzeichnis, in das die Momentaufnahmedateien mit File Transfer Protocol (FTP) übertragen werden, wenn diese Option angegeben ist.|  
|**use_ftp**|**bit**|Abonnement abonniert die Veröffentlichung über die konfigurierten Internet- und FTP-Adressierungseigenschaften. Wenn der Wert **0**ist, verwendet das Abonnement nicht FTP. Bei **1**verwendet das Abonnement FTP.|  
|**publication_type**|**int**|Gibt den Replikationstyp der Veröffentlichung an.<br /><br /> **0** = Transaktions Replikation<br /><br /> **1** = Momentaufnahme Replikation<br /><br /> **2** = Mergereplikation|  
|**dts_package_name**|**sysname**|Gibt den Namen des DTS-Pakets (Data Transformation Services) an.|  
|**dts_package_location**|**int**|Der Speicherort des DTS-Pakets:<br /><br /> **0** = Verteiler<br /><br /> **1** = Abonnent|  
|**offload_agent**|**bit**|Gibt an, ob der Agent remote aktiviert werden kann. Wenn der Wert **0**ist, kann der Agent nicht remote aktiviert werden.|  
|**offload_server**|**sysname**|Gibt den Netzwerknamen des Servers an, der für die Remoteaktivierung verwendet wird.|  
|**last_sync_status**|**int**|Abonnementstatus:<br /><br /> **0** = alle Aufträge warten auf den Start<br /><br /> **1** = mindestens ein Auftrag wird gestartet.<br /><br /> **2** = alle Aufträge wurden erfolgreich ausgeführt.<br /><br /> **3** = mindestens ein Auftrag wird ausgeführt<br /><br /> **4** = alle Aufträge sind geplant und im Leerlauf<br /><br /> **5** = mindestens ein Auftrag versucht, nach einem vorherigen Fehler auszuführen<br /><br /> **6** = mindestens ein Auftrag konnte nicht erfolgreich ausgeführt werden.|  
|**last_sync_summary**|**sysname**|Beschreibung der letzten Synchronisierungsergebnisse.|  
|**last_sync_time**|**datetime**|Zeitpunkt, zu dem die Abonnementinformationen aktualisiert wurden. Dies ist eine UNICODE-Zeichenfolge aus ISO-Datum (114) + ODBC-Zeit (121). Das Format ist yyyymmdd hh:mi:sss.mmm, wobei yyyy das Jahr, mm den Monat, dd den Tag, hh die Stunde, mi die Minute, sss die Sekunden und mmm die Millisekunden angibt.|  
|**job_login**|**nvarchar(512)**|Das Windows-Konto, unter dem der Verteilungs-Agent ausgeführt wird, das im Format *Domäne*\\*Benutzername*zurückgegeben wird.|  
|**job_password**|**sysname**|Aus Sicherheitsgründen wird immer der Wert**\*\*\*\*\*\*\*\*"\***" zurückgegeben.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helppullsubscription** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_helppullsubscription** ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addpullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
