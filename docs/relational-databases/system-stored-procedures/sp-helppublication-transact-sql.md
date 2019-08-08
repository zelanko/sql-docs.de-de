---
title: sp_helppublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppublication_TSQL
- sp_helppublication
helpviewer_keywords:
- sp_helppublication
ms.assetid: e801c3f0-dcbd-4b4a-b254-949a05f63518
author: stevestein
ms.author: sstein
ms.openlocfilehash: 693e9f580c2b51c2ff8a6fd82973d06c2a80d287
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771133"
---
# <a name="sp_helppublication-transact-sql"></a>sp_helppublication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt Informationen zu einer Veröffentlichung zurück. Für eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Veröffentlichung wird diese gespeicherte Prozedur auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt. Bei einer Veröffentlichung für Oracle wird diese gespeicherte Prozedur auf dem Verteiler für eine beliebige Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helppublication [ [ @publication = ] 'publication' ]  
    [ , [ @found=] found OUTPUT]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, die angezeigt werden soll. *Publication* ist vom **%** Datentyp sysname und hat den Standardwert, mit dem Informationen zu allen Veröffentlichungen zurückgegeben werden.  
  
`[ @found = ] 'found' OUTPUT`Ein Flag, das die Rückgabe von Zeilen angibt. " *found*" ist vom Datentyp **int** und ein Output-Parameter. der Standardwert ist **23456**. **1** gibt an, dass die Veröffentlichung gefunden wurde. **0** gibt an, dass die Veröffentlichung nicht gefunden wurde.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom Datentyp sysname und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht angegeben werden, wenn Veröffentlichungsinformationen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einem Verleger angefordert werden.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|pubid|**int**|ID für die Veröffentlichung.|  
|NAME|**sysname**|Name der Veröffentlichung.|  
|restricted|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**tinyint**|Der aktuelle Status der Veröffentlichung.<br /><br /> **0** = inaktiv.<br /><br /> **1** = aktiv.|  
|Task (task)||Dieser Parameter wird aus Gründen der Abwärtskompatibilität verwendet.|  
|replication frequency|**tinyint**|Art der Replikationshäufigkeit:<br /><br /> **0** = transaktional<br /><br /> **1** = Momentaufnahme|  
|synchronization method|**tinyint**|Synchronisierungsmethode:<br /><br /> **0** = System eigenes Massen Kopier Programm (**bcp** -Hilfsprogramm)<br /><br /> **1** = Massen Kopieren von Zeichen<br /><br /> **3** = gleichzeitig, d. h., es wird ein System eigenes Massen Kopiervorgang (**bcp**-Hilfsprogramm) verwendet, aber Tabellen sind während der Momentaufnahme<br /><br /> **4** = concurrent_c, d. h., das Massen Kopieren von Zeichen wird verwendet, aber Tabellen sind während der Momentaufnahme nicht gesperrt.|  
|description|**nvarchar(255)**|Optionale Beschreibung für die Veröffentlichung.|  
|immediate_sync|**bit**|Gibt an, ob die Synchronisierungsdateien bei jeder Ausführung des Momentaufnahme-Agents erstellt oder neu erstellt werden.|  
|enabled_for_internet|**bit**|Gibt an, ob die Synchronisierungsdateien für die Veröffentlichung im Internet über FTP (File Transfer Protocol) oder andere Dienste bereitgestellt werden.|  
|allow_push|**bit**|Gibt an, ob Pushabonnements für die Veröffentlichung zulässig sind.|  
|allow_pull|**bit**|Gibt an, ob Pullabonnements für die Veröffentlichung zulässig sind.|  
|allow_anonymous|**bit**|Gibt an, ob anonyme Abonnements für die Veröffentlichung zulässig sind.|  
|independent_agent|**bit**|Gibt an, ob eine eigenständige Verteilungs-Agent für diese Veröffentlichung vorhanden ist.|  
|immediate_sync_ready|**bit**|Gibt an, ob der Momentaufnahme-Agent eine Momentaufnahme generiert, der zum Verwenden durch neue Abonnements bereitsteht. Dieser Parameter wird nur definiert, wenn die Veröffentlichung so festgelegt ist, dass sie immer eine Momentaufnahme für neue oder neu initialisierte Abonnements zur Verfügung hat.|  
|allow_sync_tran|**bit**|Gibt an, ob sofort aktualisierbare Abonnements für die Veröffentlichung zulässig sind.|  
|autogen_sync_procs|**bit**|Gibt an, ob gespeicherte Prozeduren automatisch generiert werden sollen, um sofort aktualisierbare Abonnements zu unterstützen.|  
|snapshot_jobid|**binary(16)**|ID für geplanten Task.|  
|retention|**int**|Der Änderungsumfang (in Stunden), der für die angegebene Veröffentlichung eingespart werden soll.|  
|has subscription|**bit**|Gibt an, ob die Veröffentlichung über aktive Abonnements verfügt. **1** bedeutet, dass die Veröffentlichung über aktive Abonnements verfügt und **0** bedeutet, dass die Veröffentlichung über keine Abonnements verfügt.|  
|allow_queued_tran|**bit**|Gibt an, ob das Hinzufügen von Änderungen beim Abonnenten zu Warteschlangen, bis diese beim Verleger zugeordnet werden können, aktiviert wurde. Bei **0**werden Änderungen auf dem Abonnenten nicht in die Warteschlange eingereiht.|  
|snapshot_in_defaultfolder|**bit**|Gibt an, ob Momentaufnahme Dateien im Standardordner gespeichert werden. Wenn der Wert **0**ist, wurden Momentaufnahme Dateien am alternativen Speicherort gespeichert, der durch *alternate_snapshot_folder*angegeben wurde. Wenn der Wert **1**ist, befinden sich die Momentaufnahme Dateien im Standardordner.|  
|alt_snapshot_folder|**nvarchar(255)**|Gibt den Speicherort des anderen Ordners für die Momentaufnahme an.|  
|pre_snapshot_script|**nvarchar(255)**|Gibt einen Zeiger auf einen Speicherort für **SQL** -Dateien an. Der Verteilungs-Agent führt das vor der Momentaufnahme ausgeführte Skript vor allen Skripts für replizierte Objekte aus, wenn die Momentaufnahme bei einem Abonnenten angewendet wird.|  
|post_snapshot_script|**nvarchar(255)**|Gibt einen Zeiger auf einen Speicherort für **SQL** -Dateien an. Der Verteilungs-Agent führt das nach der Momentaufnahme ausgeführte Skript aus, nachdem alle anderen Skripts für replizierte Objekte und Daten während der Erstsynchronisierung angewendet wurden.|  
|compress_snapshot|**bit**|Gibt an, dass die Momentaufnahme, die an den Speicherort *alt_snapshot_folder* geschrieben wird, [!INCLUDE[msCoName](../../includes/msconame-md.md)] in das CAB-Format komprimiert werden soll. der Wert **0** gibt an, dass die Momentaufnahme nicht komprimiert wird.|  
|ftp_address|**sysname**|Die Netzwerkadresse des FTP-Dienstanbieter für den Verteiler. Gibt an, wo die Veröffentlichungsmomentaufnahmedateien für den Verteilungs-Agent oder Merge-Agent eines Abonnenten zum Abholen gespeichert sind.|  
|ftp_port|**int**|Die Portnummer des FTP-Dienstanbieter für den Verteiler.|  
|ftp_subdirectory|**nvarchar(255)**|Gibt an, wo die Momentaufnahmedateien für den Verteilungs-Agent oder Merge-Agent eines Abonnenten zum Abholen verfügbar sind, wenn die Veröffentlichung das Weitergeben von Momentaufnahmen mithilfe von FTP unterstützt.|  
|ftp_login|**sysname**|Der zum Herstellen einer Verbindung mit dem FTP-Dienst verwendete Benutzername.|  
|allow_dts|**bit**|Gibt an, dass die Veröffentlichung Datentransformationen zulässt. der Wert **0** gibt an, dass DTS-Transformationen nicht zulässig sind.|  
|allow_subscription_copy|**bit**|Gibt an, ob die Möglichkeit zum Kopieren der Abonnementdatenbanken aktiviert wurde, die diese Veröffentlichung abonniert haben. **0** bedeutet, dass das Kopieren nicht zulässig ist.|  
|centralized_conflicts|**bit**|Gibt an, ob Konfliktdatensätze auf dem Verleger gespeichert werden:<br /><br /> **0** = Konflikt Datensätze werden sowohl auf dem Verleger als auch auf dem Abonnenten gespeichert, der den Konflikt verursacht hat.<br /><br /> **1** = Konflikt Datensätze werden auf dem Verleger gespeichert.|  
|conflict_retention|**int**|Gibt die Konfliktaufbewahrungsdauer in Tagen an.|  
|conflict_policy|**int**|Gibt die Richtlinie zur Konfliktlösung an, die für die Option zur verzögerten Aktualisierung über eine Warteschlange verwendet wird. Kann einen der folgenden Werte aufweisen:<br /><br /> **1** = der Verleger gewinnt den Konflikt.<br /><br /> **2** = Abonnent gewinnt den Konflikt.<br /><br /> **3** = das Abonnement wird erneut initialisiert.|  
|queue_type||Gibt an, welcher Wartenschlangentyp verwendet wird. Kann einen der folgenden Werte aufweisen:<br /><br /> **MSMQ** = verwendet [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing, um Transaktionen zu speichern.<br /><br /> **SQL** = wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Speichern von Transaktionen verwendet.<br /><br /> Hinweis: Unterstützung für Message Queuing wurde eingestellt.|  
|backward_comp_level||Der Datenbank-Kompatibilitätsgrad. Folgende Werte sind möglich:<br /><br /> **90** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **100** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|publish_to_AD|**bit**|Gibt an, ob die Veröffentlichung im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory veröffentlicht wird???. Der Wert **1** gibt an, dass Sie veröffentlicht wird, und der Wert **0** gibt an, dass Sie nicht veröffentlicht wird.|  
|allow_initialize_from_backup|**bit**|Gibt an, ob Abonnenten ein Abonnement für diese Veröffentlichung über eine Sicherung anstelle einer Anfangsmomentaufnahme initialisieren können. **1** bedeutet, dass Abonnements aus einer Sicherung initialisiert werden können, und **0** bedeutet, dass Sie nicht möglich sind. Weitere Informationen finden Sie unter [Initialisieren eines Transaktions Abonnements ohne Momentaufnahme](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md) einen Transaktions Abonnenten ohne Momentaufnahme.|  
|replicate_ddl|**int**|Gibt an, ob die Schema Replikation für die Veröffentlichung unterstützt wird. **1** gibt an, dass DDL-Anweisungen (Data Definition Language), die auf dem Verleger ausgeführt werden, repliziert werden, und **0** bedeutet, dass DDL-Anweisungen nicht repliziert werden Weitere Informationen finden Sie unter [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).|  
|enabled_for_p2p|**int**|Gibt an, ob die Veröffentlichung in einer Peer-zu-Peer-Replikationstopologie verwendet werden kann. **1** gibt an, dass die Veröffentlichung die Peer-zu-Peer-Replikation unterstützt. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
|publish_local_changes_only|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|enabled_for_het_sub|**int**|Gibt an, ob die Veröffentlichung Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten unterstützt. Der Wert **1** bedeutet, dass nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten unterstützt werden. Der Wert **0** bedeutet, dass nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten unterstützt werden. Weitere Informationen finden Sie unter [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).|  
|enabled_for_p2p_conflictdetection|**int**|Gibt an, ob der Verteilungs-Agent Konflikte für eine Veröffentlichung erkennt, die für die Peer-zu-Peer-Replikation aktiviert ist. Der Wert **1** bedeutet, dass Konflikte erkannt werden. Weitere Informationen finden Sie unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|originator_id|**int**|Gibt eine ID für einen Knoten in einer Peer-zu-Peer-Topologie an. Diese ID wird für die Konflikterkennung verwendet, wenn **enabled_for_p2p_conflictdetection** auf **1**festgelegt ist. Zum Anzeigen einer Liste der bereits verwendeten IDs fragen Sie die [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) -Systemtabelle ab.|  
|p2p_continue_onconflict|**int**|Gibt an, ob der Verteilungs-Agent bei Erkennung eines Konflikts die Verarbeitung von Änderungen fortsetzt. Der Wert **1** bedeutet, dass der Agent die Verarbeitung von Änderungen fortsetzt.<br /><br /> **Vorsicht:\*es wird empfohlen, dass Sie den Standardwert 0 verwenden. \* \* \*** Wenn diese Option auf **1**festgelegt ist, versucht der Verteilungs-Agent, die Daten in der Topologie zusammenzuführen, indem die Konflikt verursachende Zeile von dem Knoten mit der höchsten Absender-ID angewendet wird. Bei dieser Methode ist keine Konvergenz garantiert. Sie sollten sicherstellen, dass die Topologie nach der Erkennung eines Konflikts konsistent ist. Weitere Informationen finden Sie im Abschnitt "Konfliktbehandlung" unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|allow_partition_switch|**int**|Gibt an, ob ALTER TABLE... Switch-Anweisungen können für die veröffentlichte Datenbank ausgeführt werden. Weitere Informationen finden Sie unter [Replicate Partitioned Tables and Indexes](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md).|  
|replicate_partition_switch|**int**|Gibt an, ob ALTER TABLE... Switch-Anweisungen, die für die veröffentlichte Datenbank ausgeführt werden, sollten auf Abonnenten repliziert werden. Diese Option ist nur gültig, wenn *allow_partition_switch* auf **1**festgelegt ist.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_helppublication wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 sp_helppublication gibt Informationen zu allen Veröffentlichungen zurück, die sich im Besitz des Benutzers befinden, der diese Prozedur ausführt.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_helppublication](../../relational-databases/replication/codesnippet/tsql/sp-helppublication-trans_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle sysadmin auf dem Verleger oder Mitglieder der festen Daten Bank Rolle db_owner für die Veröffentlichungs Datenbank oder Benutzer in der Veröffentlichungs Zugriffsliste (Publication Access List, PAL) können sp_helppublication ausführen.  
  
 Bei einem nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger können nur Mitglieder der festen Server Rolle sysadmin auf dem Verteiler oder Mitglieder der festen Daten Bank Rolle db_owner in der Verteilungs Datenbank oder die Benutzer in der PAL sp_helppublication ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
