---
title: sp_helpmergepublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepublication
- sp_helpmergepublication_TSQL
helpviewer_keywords:
- sp_helpmergepublication
ms.assetid: dfe1e1e1-9a65-406a-aced-6385a078e135
author: stevestein
ms.author: sstein
ms.openlocfilehash: d291288c44341c3a707696b0b3baecdcd15779ef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68137653"
---
# <a name="sp_helpmergepublication-transact-sql"></a>sp_helpmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu einer Mergeveröffentlichung zurück. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergepublication [ [ @publication = ] 'publication' ]  
    [ , [ @found = ] 'found' OUTPUT ]  
    [ , [ @publication_id = ] 'publication_id' OUTPUT ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @publication **=** ] **'**_Veröffentlichung_**'**  
 Der Name der Veröffentlichung. *Publication*ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert, mit dem Informationen zu allen Mergeveröffentlichungen in der aktuellen Datenbank zurückgegeben werden.  
  
 [ @found **=** ] **'***found***** Ausgabe ' gefunden.  
 Ein Flag, das die Rückgabe von Zeilen angibt. " *found*" ist vom Datentyp **int** und ein Output-Parameter. der Standardwert ist NULL. **1** gibt an, dass die Veröffentlichung gefunden wurde. **0** gibt an, dass die Veröffentlichung nicht gefunden wurde.  
  
 [ @publication_id **=**] **'***publication_id***** Ausgabe '  
 Die Veröffentlichung-ID. *publication_id* ist vom Datentyp **uniqueidentifier** und ein Output-Parameter. der Standardwert ist NULL.  
  
 [ @reserved **=**] **'***reserviert***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]*reserved* ist vom Datentyp **nvarchar (20)** und hat den Standardwert NULL.  
  
 [ @publisher **=** ] **'***Verleger***'**  
 Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
 [@publisher_db **=** ] **'***publisher_db***'**  
 Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|id|**int**|Sequenzielle Position der Veröffentlichung in der Liste im Resultset.|  
|Name|**sysname**|Name der Veröffentlichung.|  
|description|**nvarchar(255)**|Die Beschreibung der Veröffentlichung.|  
|status|**tinyint**|Gibt an, wann Veröffentlichungsdaten verfügbar sind.|  
|retention|**int**|Die Zeit, die Metadaten zu Änderungen in Artikeln in der Veröffentlichung gespeichert werden sollen. Die Einheiten für diesen Zeitraum kann Tage, Wochen, Monate oder Jahre sein. Informationen zu Einheiten finden Sie in der retention_period_unit-Spalte.|  
|sync_mode|**tinyint**|Synchronisierungsmodus dieser Veröffentlichung.<br /><br /> **0** = System eigenes Massen Kopier Programm (**bcp** -Hilfsprogramm)<br /><br /> **1** = Massen Kopieren von Zeichen|  
|allow_push|**int**|Bestimmt, ob für die angegebene Veröffentlichung Pushabonnements erstellt werden können. **0** bedeutet, dass ein Pushabonnement nicht zulässig ist.|  
|allow_pull|**int**|Bestimmt, ob für die angegebene Veröffentlichung Pullabonnements erstellt werden können. **0** bedeutet, dass ein Pullabonnement nicht zulässig ist.|  
|allow_anonymous|**int**|Bestimmt, ob für die angegebene Veröffentlichung anonyme Abonnements erstellt werden können. **0** bedeutet, dass ein anonymes Abonnement nicht zulässig ist.|  
|centralized_conflicts|**int**|Legt fest, ob Konfliktdatensätze auf dem angegebenen Verleger gespeichert werden:<br /><br /> **0** = Konflikt Datensätze werden sowohl auf dem Verleger als auch auf dem Abonnenten gespeichert, der den Konflikt verursacht hat.<br /><br /> **1** = alle Konflikt Datensätze werden auf dem Verleger gespeichert.|  
|priority|**float (8)**|Priorität des Loopbackabonnements.|  
|snapshot_ready|**tinyint**|Gibt an, ob die Momentaufnahme dieser Veröffentlichung einsatzbereit ist.<br /><br /> **0** = Momentaufnahme kann verwendet werden.<br /><br /> **1** = Momentaufnahme ist nicht einsatzbereit.|  
|publication_type|**int**|Typ der Veröffentlichung:<br /><br /> **0** = Momentaufnahme.<br /><br /> **1** = transaktional.<br /><br /> **2** = Merge.|  
|pubid|**uniqueidentifier**|Eindeutiger Bezeichner dieser Veröffentlichung.|  
|snapshot_jobid|**Binary (16)**|Auftrags-ID des Momentaufnahme-Agents. Wenn Sie den Eintrag für den Momentaufnahme Auftrag in der [sysjobs](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md) -Systemtabelle abrufen möchten, müssen Sie diesen Hexadezimalwert in **uniqueidentifier**konvertieren.|  
|enabled_for_internet|**int**|Legt fest, ob die Veröffentlichung für das Internet aktiviert ist. Bei **1**werden die Synchronisierungs Dateien für die Veröffentlichung im `C:\Program Files\Microsoft SQL Server\MSSQL\Repldata\Ftp` Verzeichnis abgelegt. Der Benutzer muss das FTP-Verzeichnis (File Transfer Protocol) erstellen. Wenn der Wert **0**ist, ist die Veröffentlichung nicht für den Internet Zugriff aktiviert.|  
|dynamic_filter|**int**|Gibt an, ob ein parametrisierter Zeilenfilter verwendet wird. **0** bedeutet, dass kein parametrisierter Zeilen Filter verwendet wird.|  
|has_subscription|**bit**|Gibt an, ob die Veröffentlichung über Abonnements verfügt. **0** bedeutet, dass zurzeit keine Abonnements für diese Veröffentlichung vorhanden sind.|  
|snapshot_in_default_folder|**bit**|Legt fest, ob die Momentaufnahmedateien im Standardordner gespeichert werden.<br /><br /> Wenn der Wert **1**ist, befinden sich die Momentaufnahme Dateien im Standardordner.<br /><br /> Wenn der Wert **0**ist, werden Momentaufnahme Dateien am alternativen Speicherort gespeichert, der durch **alt_snapshot_folder**angegeben wird. Alternative Speicherorte können sich auf einem anderen Server, auf einem Netzlaufwerk oder auf einem Wechselmedium (z. B. CD-ROM oder Wechseldatenträger) befinden. Momentaufnahmedateien lassen sich auch in einer FTP-Site speichern, um zu einem späteren Zeitpunkt vom Abonnenten abgerufen zu werden.<br /><br /> Hinweis: dieser Parameter kann "true" sein und noch über eine Position im **alt_snapshot_folder** -Parameter verfügen. Diese Kombination gibt an, dass die Momentaufnahmedateien sowohl an den Standardspeicherorten als auch an den alternativen Standorten gespeichert werden.|  
|alt_snapshot_folder|**nvarchar(255)**|Gibt den Speicherort des anderen Ordners für die Momentaufnahme an.|  
|pre_snapshot_script|**nvarchar(255)**|Gibt einen Zeiger auf eine **SQL** -Datei an, die der Merge-Agent vor einem der replizierten Objekt Skripts ausführt, wenn die Momentaufnahme auf einem Abonnenten angewendet wird.|  
|post_snapshot_script|**nvarchar(255)**|Gibt einen Zeiger auf eine **SQL** -Datei an, die der Merge-Agent ausgeführt wird, nachdem alle anderen Skripts für replizierte Objekte und Daten während der erst Synchronisierung angewendet wurden.|  
|compress_snapshot|**bit**|Gibt an, dass die Momentaufnahme, die an den **alt_snapshot_folder** Speicherort geschrieben [!INCLUDE[msCoName](../../includes/msconame-md.md)] wird, in das CAB-Format komprimiert wird.|  
|ftp_address|**sysname**|Die Netzwerkadresse des FTP-Diensts für den Verteiler. Gibt an, wo sich Veröffentlichungs Momentaufnahme-Dateien befinden, damit die Merge-Agent abgerufen werden können.|  
|ftp_port|**int**|Die Anschlussnummer des FTP-Diensts für den Verteiler. **ftp_port** hat den Standardwert **21**. Gibt an, wo die Veröffentlichungsmomentaufnahmedateien zum Abholen durch den Merge-Agent gespeichert sind.|  
|ftp_subdirectory|**nvarchar(255)**|Gibt an, wo die Veröffentlichungsmomentaufnahmedateien zum Abholen durch den Merge-Agent gespeichert sind, wenn die Momentaufnahme mithilfe von FTP übermittelt wird.|  
|ftp_login|**sysname**|Der Benutzername, mit dem eine Verbindung zum FTP-Dienst hergestellt wird.|  
|conflict_retention|**int**|Gibt die Aufbewahrungsdauer in Tagen an, für die Konflikte beibehalten werden. Wenn die angegebene Anzahl von Tagen abgelaufen ist, wird die Konfliktzeile aus der Konflikttabelle gelöscht.|  
|keep_partition_changes|**int**|Gibt an, ob die Synchronisierungsoptimierung für diese Veröffentlichung erfolgt. **keep_partition_changes** hat den Standardwert **0**. Der Wert **0** bedeutet, dass die Synchronisierung nicht optimiert wird und die an alle Abonnenten gesendeten Partitionen überprüft werden, wenn sich Daten in einer Partition ändern.<br /><br /> **1** bedeutet, dass die Synchronisierung optimiert ist, und nur Abonnenten, die Zeilen in der geänderten Partition haben, sind betroffen.<br /><br /> Hinweis: in Mergeveröffentlichungen werden standardmäßig Voraus berechnete Partitionen verwendet, wodurch eine höhere Optimierung als bei dieser Option möglich ist. Weitere Informationen finden Sie unter [parametrisierte Zeilen Filter](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md) und [Optimieren der Leistung parametrisierter Filter mit voraus berechneten Partitionen](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).|  
|allow_subscription_copy|**int**|Gibt an, ob die Möglichkeit zum Kopieren der Abonnementdatenbanken aktiviert wurde, die diese Veröffentlichung abonniert haben. Der Wert **0** bedeutet, dass das Kopieren nicht zulässig ist.|  
|allow_synctoalternate|**int**|Gibt an, ob ein alternativer Synchronisierungspartner für die Synchronisierung mit diesem Verleger zulässig ist. Der Wert **0** bedeutet, dass ein Synchronisierungs Partner nicht zulässig ist.|  
|validate_subscriber_info|**nvarchar (500)**|Listet die Funktionen auf, die zum Abrufen der Abonnenteninformationen sowie zum Überprüfen der parametrisierten Zeilenfilterkriterien für den Abonnenten verwendet werden. Dies hilft dabei, zu überprüfen, ob die Informationen bei jedem Mergeprozess konsistent partitioniert werden.|  
|backward_comp_level|**int**|Der Datenbank-Kompatibilitätsgrad. Folgende Werte sind möglich:<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **90** =  90[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1<br /><br /> **90** =  90[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP2<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|publish_to_activedirectory|**bit**|Gibt an, ob die Veröffentlichungsinformationen in Active Directory veröffentlicht werden. Der Wert **0** bedeutet, dass die Veröffentlichungsinformationen aus Active Directory nicht verfügbar sind.<br /><br /> Dieser Parameter wurde als veraltet markiert und wird nur zum Sicherstellen der Abwärtskompatibilität von Skripts unterstützt. Sie können Active Directory nicht länger Veröffentlichungsinformationen hinzufügen.|  
|max_concurrent_merge|**int**|Die Anzahl gleichzeitiger Mergeprozesse. Wenn der Wert **0**ist, gibt es keine Beschränkung für die Anzahl gleichzeitiger Mergeprozesse, die zu einem beliebigen Zeitpunkt ausgeführt werden.|  
|max_concurrent_dynamic_snapshots|**int**|Die maximale Anzahl gleichzeitiger Sitzungen für eine Momentaufnahme gefilterter Daten, die für die Mergeveröffentlichung ausgeführt werden können. Wenn der Wert **0**ist, gibt es keine Beschränkung für die maximale Anzahl gleichzeitiger gefilterter Daten Momentaufnahme Sitzungen, die gleichzeitig für die Veröffentlichung ausgeführt werden können.|  
|use_partition_groups|**int**|Legt fest, ob vorausberechnete Partitionen verwendet werden. Der Wert **1** bedeutet, dass Voraus berechnete Partitionen verwendet werden.|  
|num_of_articles|**int**|Anzahl der Artikel in der Veröffentlichung.|  
|replicate_ddl|**int**|Gibt an, ob Schemaänderungen an veröffentlichten Tabellen repliziert werden. Der Wert **1** bedeutet, dass Schema Änderungen repliziert werden.|  
|publication_number|**smallint**|Die Nummer, die dieser Veröffentlichung zugewiesen ist.|  
|allow_subscriber_initiated_snapshot|**bit**|Legt fest, ob Abonnenten den Prozess für die Generierung eine Momentaufnahme für gefilterte Daten initiieren können. Der Wert **1** bedeutet, dass Abonnenten den Momentaufnahme Prozess initiieren können.|  
|allow_web_synchronization|**bit**|Legt fest, ob die Veröffentlichung für die Websynchronisierung aktiviert ist. Der Wert **1** bedeutet, dass die Websynchronisierung aktiviert ist.|  
|web_synchronization_url|**nvarchar (500)**|Die für die Websynchronisierung verwendete Internet-URL.|  
|allow_partition_realignment|**bit**|Legt fest, ob Löschvorgänge an den Abonnenten gesendet werden, wenn die Änderung der Zeile auf dem Verleger zum Ändern der Partition führt. Der Wert **1** bedeutet, dass Löschvorgänge an den Abonnenten gesendet werden.  Weitere Informationen finden Sie unter [sp_addmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).|  
|retention_period_unit|**tinyint**|Definiert die Einheit, die beim Definieren der Beibehaltung verwendet wird. Mögliche Werte:<br /><br /> **0** = Tag<br /><br /> **1** = Woche<br /><br /> **2** = Monat<br /><br /> **3** = Jahr|  
|has_downloadonly_articles|**bit**|Gibt an, ob es sich bei Artikeln, die zur Veröffentlichung gehören, um nur herunterladbare Artikel handelt. Der Wert **1** gibt an, dass nur herunterladbare Artikel vorhanden sind.|  
|decentralized_conflicts|**int**|Gibt an, ob die Konfliktdatensätze auf dem Abonnenten gespeichert werden, der den Konflikt verursacht hat. Der Wert **0** gibt an, dass Konflikt Datensätze nicht auf dem Abonnenten gespeichert werden. Ein Wert von 1 gibt an, dass Konfliktdatensätze auf dem Abonnenten gespeichert werden.|  
|generation_leveling_threshold|**int**|Gibt die Anzahl der Änderungen an, die in einer Generierung enthalten sind. Eine Generierung ist eine Sammlung von Änderungen, die an einen Verleger oder Abonnenten übermittelt werden.|  
|automatic_reinitialization_policy|**bit**|Gibt an, ob Änderungen vom Abonnenten vor einer automatischen erneuten Initialisierung hochgeladen werden. Der Wert **1** gibt an, dass Änderungen vom Abonnenten hochgeladen werden, bevor eine automatische Neuinitialisierung erfolgt. Der Wert 0 gibt an, dass Änderungen vom Abonnenten vor einer automatischen Neuinitialisierung nicht hochgeladen werden.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 sp_helpmergepublication wird für die Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der Veröffentlichungszugriffsliste für eine Veröffentlichung können sp_helpmergepublication für diese Veröffentlichung ausführen. Mitglieder der festen Datenbankrolle db_owner für die Veröffentlichungsdatenbank können sp_helpmergepublication für Informationen zu allen Veröffentlichungen ausführen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_helpmergepublication](../../relational-databases/replication/codesnippet/tsql/sp-helpmergepublication-_1.sql)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [sp_addmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
