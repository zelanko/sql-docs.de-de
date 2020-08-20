---
description: syspublications (Systemsicht) (Transact-SQL)
title: syspublications (System Sicht) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- syspublications
- syspublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspublications view
ms.assetid: e5f57c32-efc0-4455-a74f-684dc2ae51f8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 051a57d3cce26d7367cff1ce3afc720534e920bb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488671"
---
# <a name="syspublications-system-view-transact-sql"></a>syspublications (Systemsicht) (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die Ansicht " **syspublications** " zeigt Veröffentlichungsinformationen an. Diese Sicht wird in der distribution-Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Beschreibung**|**nvarchar(255)**|Der beschreibende Eintrag für die Veröffentlichung.|  
|**name**|**sysname**|Der eindeutige der Veröffentlichung zugeordnete Name.|  
|**pubid**|**int**|Die Identitätsspalte mit einer eindeutigen ID für die Veröffentlichung.|  
|**repl_freq**|**tinyint**|Replikationshäufigkeit:<br /><br /> **0** = Transaktions basiert (transaktional).<br /><br /> **1** = geplante Tabellen Aktualisierung (Momentaufnahme).|  
|**status**|**tinyint**|Veröffentlichungsstatus:<br /><br /> **0** = inaktiv.<br /><br /> **1** = aktiv.|  
|**sync_method**|**tinyint**|Die Synchronisierungsmethode:<br /><br /> **0** = System eigenes Hilfsprogramm zum Massen kopieren (BCP).<br /><br /> **1** = Zeichen bcp.<br /><br /> **3** = gleichzeitig, d. h., das systemeigene BCP wird verwendet, aber Tabellen sind während der Momentaufnahme nicht gesperrt.<br /><br /> **4** = concurrent_c. Dies bedeutet, dass das bcp-Zeichen verwendet wird, aber Tabellen während der Momentaufnahme nicht gesperrt sind.|  
|**snapshot_jobid**|**Binary (16)**|Identifiziert den Agentauftrag, der die Anfangsmomentaufnahme generieren soll.|  
|**independent_agent**|**bit**|Gibt an, ob eine eigenständige Verteilungs-Agent für diese Veröffentlichung vorhanden ist.<br /><br /> **0** = die Veröffentlichung verwendet einen freigegebenen Verteilungs-Agent, und jedes Paar aus Verleger Datenbank und Abonnenten Datenbank verfügt über einen einzelnen freigegebenen Agent.<br /><br /> **1** = für diese Veröffentlichung ist ein eigenständiger Verteilungs-Agent vorhanden.|  
|**immediate_sync**|**bit**|Gibt an, ob die Synchronisierungs Dateien bei jeder Ausführung des Momentaufnahmen-Agent erstellt oder neu erstellt werden, wobei **1** bedeutet, dass Sie bei jeder Ausführung des Agents erstellt werden.|  
|**enabled_for_internet**|**bit**|Gibt an, ob die Synchronisierungs Dateien für die Veröffentlichung im Internet über FTP (File Transfer Protocol) und andere Dienste verfügbar gemacht werden, wobei **1** bedeutet, dass über das Internet auf Sie zugegriffen werden kann.|  
|**allow_push**|**bit**|Gibt an, ob Pushabonnements für die Veröffentlichung zulässig sind. der Wert **1** bedeutet, dass Sie zulässig sind.|  
|**allow_pull**|**bit**|Gibt an, ob Pullabonnements für die Veröffentlichung zulässig sind, wobei **1** bedeutet, dass Sie zulässig sind.|  
|**allow_anonymous**|**bit**|Gibt an, ob anonyme Abonnements für die Veröffentlichung zulässig sind. der Wert **1** bedeutet, dass Sie zulässig sind.|  
|**immediate_sync_ready**|**bit**|Zeigt an, ob die Momentaufnahme vom Momentaufnahme-Agent generiert wurde und dieser zum Verwenden durch neue Abonnements bereit ist. Dies ist nur für sofort aktualisierbare Veröffentlichungen von Bedeutung. **1** gibt an, dass die Momentaufnahme bereit ist.|  
|**allow_sync_tran**|**bit**|Gibt an, ob Abonnements mit sofortiger Aktualisierung für die Veröffentlichung zulässig sind. **1** bedeutet, dass Abonnements mit sofortigem Update zulässig sind.|  
|**autogen_sync_procs**|**bit**|Gibt an, ob die synchronisierende gespeicherte Prozedur für Abonnements mit sofortiger Aktualisierung beim Verleger generiert wird. der Wert **1** bedeutet, dass er auf dem Verleger generiert wird.|  
|**Beibehaltung**|**int**|Der Zeitraum (in Stunden), in dem Änderungen an der Veröffentlichung in der Verteilungsdatenbank beibehalten werden.|  
|**allow_queued_tran**|**bit**|Gibt an, ob das Einreihen von Änderungen auf dem Abonnenten in Warteschlangen, bis diese Änderungen auf dem Verleger angewendet werden können, aktiviert wurde. Bei **1**werden Änderungen auf dem Abonnenten in die Warteschlange eingereiht.|  
|**snapshot_in_defaultfolder**|**bit**|Gibt an, ob Momentaufnahme Dateien im Standardordner gespeichert werden. Wenn der Wert **0**ist, wurden die Momentaufnahme Dateien am alternativen Speicherort gespeichert, der durch *alternate_snapshot_folder*angegeben wurde. Bei 1 befinden sich die Momentaufnahmedateien im Standardordner.|  
|**alt_snapshot_folder**|**nvarchar (510)**|Gibt den Speicherort des anderen Ordners für die Momentaufnahme an.|  
|**pre_snapshot_script**|**nvarchar (510)**|Gibt einen Zeiger auf einen **SQL** -Datei Speicherort an. Der Verteilungs-Agent führt das vor der Momentaufnahme ausgeführte Skript vor allen Skripts für replizierte Objekte aus, wenn die Momentaufnahme auf einem Abonnenten angewendet wird.|  
|**post_snapshot_script**|**nvarchar (510)**|Gibt einen Zeiger auf einen **SQL** -Datei Speicherort an. Der Verteilungs-Agent führt das Skript nach der Momentaufnahme aus, nachdem alle anderen Skripts für replizierte Objekte und Daten während der erst Synchronisierung angewendet wurden.|  
|**compress_snapshot**|**bit**|Gibt an, dass die Momentaufnahme, die an den *alt_snapshot_folder* Speicherort geschrieben wird, in das CAB-Format komprimiert werden soll [!INCLUDE[msCoName](../../includes/msconame-md.md)] . **1** bedeutet, dass die Momentaufnahme komprimiert wird.|  
|**ftp_address**|**sysname**|Die Netzwerkadresse des FTP-Dienstanbieter für den Verteiler. Gibt an, wo die Veröffentlichungsmomentaufnahmedateien zum Aufnehmen durch den Verteilungs-Agent gespeichert sind.|  
|**ftp_port**|**int**|Die Portnummer des FTP-Dienstanbieter für den Verteiler. Gibt an, wo sich die Veröffentlichungs Momentaufnahme-Dateien befinden, damit die Verteilungs-Agent abgerufen werden können.|  
|**ftp_subdirectory**|**nvarchar (510)**|Gibt an, wo die Momentaufnahmedateien für den Verteilungs-Agent zum Aufnehmen verfügbar sind, wenn die Veröffentlichung das Weitergeben von Momentaufnahmen mithilfe von FTP unterstützt.|  
|**ftp_login**|**nvarchar(256)**|Der zum Herstellen einer Verbindung mit dem FTP-Dienst verwendete Benutzername.|  
|**ftp_password**|**nvarchar (1048)**|Das Benutzer Kennwort, das für die Verbindung mit dem FTP-Dienst verwendet wird|  
|**allow_dts**|**bit**|Gibt an, ob die Veröffentlichung DTS-Transformationen (Data Transformation Services) für [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] zulässt. **1** gibt an, dass DTS-Transformationen zulässig sind.|  
|**allow_subscription_copy**|**bit**|Gibt an, ob die Möglichkeit zum Kopieren der Abonnementdatenbanken aktiviert wurde, die diese Veröffentlichung abonniert haben. **1** bedeutet, dass das Kopieren zulässig ist.|  
|**centralized_conflicts**|**bit**|Gibt an, ob Konfliktdatensätze auf dem Verleger gespeichert werden:<br /><br /> **0** = Konflikt Datensätze werden sowohl auf dem Verleger als auch auf dem Abonnenten gespeichert, der den Konflikt verursacht hat.<br /><br /> **1** = Konflikt Datensätze werden auf dem Verleger gespeichert.|  
|**conflict_retention**|**int**|Gibt die Beibehaltungsdauer für Konfliktdatensätze in Tagen an.|  
|**conflict_policy**|**int**|Gibt die Richtlinie zur Konfliktlösung an, die für die Option zur verzögerten Aktualisierung über eine Warteschlange verwendet wird. Einer der folgenden Werte ist möglich:<br /><br /> **1** = der Verleger gewinnt den Konflikt.<br /><br /> **2** = Abonnent gewinnt den Konflikt.<br /><br /> **3** = das Abonnement wird erneut initialisiert.|  
|**queue_type**|**int**|Gibt an, welcher Wartenschlangentyp verwendet wird. Einer der folgenden Werte ist möglich:<br /><br /> **1** =. MSMQ, der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing zum Speichern von Transaktionen verwendet.<br /><br /> **2** =. SQL, das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Speichern von Transaktionen verwendet.<br /><br /> Hinweis: die Verwendung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing wurde als veraltet markiert und wird nicht mehr unterstützt.|  
|**ad_guidname**|**sysname**|Gibt an, ob die Veröffentlichung in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory veröffentlicht wird. Ein gültiger GUID (Globally Unique Identifier) gibt an, dass die Veröffentlichung in Active Directory veröffentlicht wird, und der GUID ist das entsprechende Active Directory-Veröffentlichungsobjekt objectGUID. Wenn dieser Wert NULL ist, wird die Veröffentlichung nicht in Active Directory veröffentlicht.<br /><br /> Hinweis: das Veröffentlichen in Active Directory wird nicht mehr unterstützt.|  
|**backward_comp_level**|**int**|Datenbankkompatibilitätsgrad, der einen der folgenden Werte annehmen kann:<br /><br /> **90**  =  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .<br /><br /> **100**  =  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] .|  
|**allow_initialize_from_backup**|**bit**|Gibt an, ob Abonnenten ein Abonnement für diese Veröffentlichung aus einer Sicherung anstelle einer Anfangs Momentaufnahme initialisieren können. **1** bedeutet, dass Abonnements aus einer Sicherung initialisiert werden können, und **0** bedeutet, dass Sie nicht möglich sind. Weitere Informationen finden Sie unter [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)initialisiert wird.|  
|**min_autonosync_lsn**|**Binary (1)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**replicate_ddl**|**int**|Gibt an, ob die Schemareplikation für die Veröffentlichung unterstützt wird.<br /><br /> **1** = auf dem Verleger ausgeführte DDL-Anweisungen werden repliziert.<br /><br /> **0** = gibt an, dass DDL-Anweisungen nicht repliziert werden. Weitere Informationen finden Sie unter [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).|  
|**options**|**int**|Ein Bitmuster, mit dem zusätzliche Veröffentlichungsoptionen angegeben werden. Dabei gibt es folgende bitweise Optionswerte:<br /><br /> **0x1** : für die Peer-zu-Peer-Replikation aktiviert.<br /><br /> **0x2** -nur lokale Änderungen für die Peer-zu-Peer-Replikation veröffentlichen.<br /><br /> **0x4** -aktiviert für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.<br /><br /> **0x8** : für Peer-zu-Peer-Konflikterkennung aktiviert.|  
|**originator_id**|**smallint**|Kennzeichnet jeden Knoten in einer Peer-zu-Peer-Replikationstopologie zum Zweck der Konflikterkennung. Weitere Informationen finden Sie unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Gespeicherte Replikations Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_addpublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)  
  
  
