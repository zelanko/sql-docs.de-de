---
title: MSsubscription_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_properties
- MSsubscription_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_properties system table
ms.assetid: f96fc1ae-b798-4b05-82a7-564ae6ef23b8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bc3e113ab9ace64cac0d41cb34bdec1c44355e48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63032990"
---
# <a name="mssubscriptionproperties-transact-sql"></a>MSsubscription_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSsubscription_properties** -Tabelle enthält Zeilen für die Parameterinformationen, die zum Ausführen von Replikations-Agents auf dem Abonnenten erforderlich sind. Diese Tabelle wird für ein Pullabonnement auf dem Abonnenten in der Abonnementdatenbank und für ein Pushabonnement auf dem Verteiler in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**publication**|**sysname**|Der Name der Veröffentlichung.|  
|**publication_type**|**int**|Der Typ der Veröffentlichung:<br /><br /> **0** = transaktionsveröffentlichung.<br /><br /> **2** = Merge.|  
|**publisher_login**|**sysname**|Die Anmelde-ID, die verwendet werden, auf dem Verleger für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**publisher_password**|**nvarchar(524)**|Das (verschlüsselte) Kennwort, das auf dem Verleger für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendet wird.|  
|**publisher_security_mode**|**int**|Auf dem Verleger implementierter Sicherheitsmodus:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server-Authentifizierung.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung.<br /><br /> **2** = der Synchronisierungstrigger verwenden einen statischen **Sysservers** -Eintrag für einen Remoteprozeduraufruf (RPC), und *Verleger* muss definiert werden, der **Sysservers**-Tabelle als Remoteserver oder Verbindungsserver.|  
|**distributor**|**sysname**|Der Name des Verteilers.|  
|**distributor_login**|**sysname**|Die Anmelde-ID, die auf dem Verteiler für SQL Server-Authentifizierung verwendet.|  
|**distributor_password**|**nvarchar(524)**|Das Kennwort (verschlüsselt), das auf dem Verteiler für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwendet wird.|  
|**distributor_security_mode**|**int**|Der auf dem Verteiler implementierte Sicherheitsmodus:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.<br /><br /> **1** = Windows-Authentifizierung.|  
|**ftp_address**|**sysname**|Die Netzwerkadresse des FTP-Diensts (File Transfer Protocol) für den Verteiler.|  
|**ftp_port**|**int**|Die Portnummer des FTP-Diensts für den Verteiler.|  
|**ftp_login**|**sysname**|Der Benutzername, der für die Verbindung mit dem FTP-Dienst verwendet wird.|  
|**ftp_password**|**nvarchar(524)**|Das u.User-Kennwort für die Verbindung mit dem FTP-Dienst verwendet.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Gibt den Speicherort des anderen Ordners für die Momentaufnahme an.|  
|**working_directory**|**nvarchar(255)**|Der Name des Arbeitsverzeichnisses zum Speichern von Daten-und Schemadateien verwendet werden soll.|  
|**use_ftp**|**bit**|Gibt anstelle des normalen Protokolls FTP an, um Momentaufnahmen abzurufen. Wenn **1**, wird FTP verwendet.|  
|**dts_package_name**|**sysname**|Gibt den Namen des DTS-Pakets (Data Transformation Services) an.|  
|**dts_package_password**|**nvarchar(524)**|Gibt das Kennwort für das Paket an.|  
|**dts_package_location**|**int**|Der Speicherort des DTS-Pakets.|  
|**enabled_for_syncmgr**|**bit**|Gibt an, ob das Abonnement über die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Synchronisierungsverwaltung synchronisiert werden kann.<br /><br /> **0** = Abonnement ist nicht mit der Synchronisierungsverwaltung registriert.<br /><br /> **1** = Abonnement wird bei der Synchronisierungsverwaltung registriert und kann synchronisiert werden, ohne Starten des [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
|**offload_agent**|**bit**|Gibt an, ob der Agent Remote oder nicht aktiviert werden kann. Wenn **0**, der Agent nicht remote aktiviert werden.|  
|**offload_server**|**sysname**|Gibt den Netzwerknamen des Servers an, der für die Remoteaktivierung verwendet wird.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Gibt den Pfad zum Ordner an, in dem die Momentaufnahmedateien gespeichert werden.|  
|**use_web_sync**|**bit**|Gibt an, ob das Abonnement über HTTP synchronisiert werden kann. Der Wert **1** bedeutet, dass dieses Feature aktiviert ist.|  
|**internet_url**|**nvarchar(260)**|Die URL, die den Speicherort der Replikationsüberwachung für die Websynchronisierung darstellt.|  
|**internet_login**|**sysname**|Der Anmeldename, der der Merge-Agent verwendet beim Herstellen einer Verbindung mit dem Webserver, der die websynchronisierung hostet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**internet_password**|**nvarchar(524)**|Das Kennwort für die Anmeldung, die der Merge-Agent verwendet beim Herstellen einer Verbindung mit dem Webserver, der die websynchronisierung hostet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**internet_security_mode**|**int**|Der verwendete Authentifizierungsmodus beim Herstellen einer Verbindung mit dem Webserver, der die websynchronisierung hostet ein Wert von **1** bedeutet, dass Windows-Authentifizierung und einen Wert von **0** bedeutet, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Die Authentifizierung.|  
|**internet_timeout**|**int**|Die Zeit in Sekunden, nach der eine Websynchronisierungsanforderung abläuft.|  
|**hostname**|**sysname**|Gibt den Wert für **HOST_NAME** Wenn diese Funktion verwendet wird, der **, in denen** -Klausel eines joinfilters oder logischen datensatzbeziehung.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
