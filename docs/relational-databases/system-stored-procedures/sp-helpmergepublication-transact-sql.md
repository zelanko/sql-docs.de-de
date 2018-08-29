---
title: Sp_helpmergepublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpmergepublication
- sp_helpmergepublication_TSQL
helpviewer_keywords:
- sp_helpmergepublication
ms.assetid: dfe1e1e1-9a65-406a-aced-6385a078e135
caps.latest.revision: 55
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3898ae087e1dd918d014735ce4c03316bef4551c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027267"
---
# <a name="sphelpmergepublication-transact-sql"></a>sp_helpmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu einer Mergeveröffentlichung zurück. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 [ @publication **=** ] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung. *Veröffentlichung*ist **Sysname**, hat den Standardwert **%**, womit Informationen zu allen mergeveröffentlichungen in der aktuellen Datenbank zurückgegeben.  
  
 [ @found **=** ] **"***gefunden***"** Ausgabe  
 Ein Flag zur Angabe zurückgegebener Zeilen. *finden Sie*ist **Int** und ein OUTPUT-Parameter hat den Standardwert NULL. **1** gibt an, die Veröffentlichung gefunden wurde. **0** gibt an, die Veröffentlichung wurde nicht gefunden.  
  
 [ @publication_id **=**] **"***Publication_id***"** Ausgabe  
 Die Veröffentlichung-ID. *Publication_id* ist **Uniqueidentifier** und ein OUTPUT-Parameter hat den Standardwert NULL.  
  
 [ @reserved **=**] **"***reservierte***"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *reservierte* ist **nvarchar(20)**, hat den Standardwert NULL.  
  
 [ @publisher **=** ] **"***Verleger***"**  
 Der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
 [@publisher_db **=** ] **"***Publisher_db***"**  
 Der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|id|**int**|Sequenzielle Position der Veröffentlichung in der Liste im Resultset.|  
|NAME|**sysname**|Name der Veröffentlichung.|  
|description|**nvarchar(255)**|Beschreibung der Veröffentlichung.|  
|status|**tinyint**|Gibt an, wann Veröffentlichungsdaten verfügbar sind.|  
|retention|**int**|Die Zeit, die Metadaten zu Änderungen in Artikeln in der Veröffentlichung gespeichert werden sollen. Die Einheiten für diesen Zeitraum kann Tage, Wochen, Monate oder Jahre sein. Informationen zu Einheiten finden Sie in der retention_period_unit-Spalte.|  
|sync_mode|**tinyint**|Synchronisierungsmodus dieser Veröffentlichung.<br /><br /> **0** = systemeigenes Massenkopierprogramm (**Bcp** Hilfsprogramm)<br /><br /> **1** = Massenkopieren von Zeichen|  
|allow_push|**int**|Bestimmt, ob für die angegebene Veröffentlichung Pushabonnements erstellt werden können. **0** bedeutet, dass ein Pushabonnement nicht zulässig ist.|  
|allow_pull|**int**|Bestimmt, ob für die angegebene Veröffentlichung Pullabonnements erstellt werden können. **0** bedeutet, dass ein Pullabonnement nicht zulässig ist.|  
|allow_anonymous|**int**|Bestimmt, ob für die angegebene Veröffentlichung anonyme Abonnements erstellt werden können. **0** bedeutet, dass ein anonymes Abonnement nicht zulässig ist.|  
|centralized_conflicts|**int**|Legt fest, ob Konfliktdatensätze auf dem angegebenen Verleger gespeichert werden:<br /><br /> **0** = die Konfliktdatensätze gespeichert werden, auf dem Verleger und auf dem Abonnenten, die den Konflikt verursacht hat.<br /><br /> **1** = alle Konfliktdatensätze auf dem Verleger gespeichert werden.|  
|priority|**float(8)**|Priorität des Loopbackabonnements.|  
|snapshot_ready|**tinyint**|Gibt an, ob die Momentaufnahme dieser Veröffentlichung einsatzbereit ist.<br /><br /> **0** = Momentaufnahme ist für die Verwendung bereit.<br /><br /> **1** = Momentaufnahme kann nicht für die Verwendung.|  
|publication_type|**int**|Typ der Veröffentlichung:<br /><br /> **0** = Momentaufnahme.<br /><br /> **1** = transaktionsveröffentlichung.<br /><br /> **2** = Merge.|  
|pubid|**uniqueidentifier**|Eindeutiger Bezeichner dieser Veröffentlichung.|  
|snapshot_jobid|**'binary(16)'**|Auftrags-ID des Momentaufnahme-Agents. Zum Abrufen des Eintrags für den momentaufnahmeauftrag in der [Sysjobs](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md) -Systemtabelle, müssen Sie diesen Hexadezimalwert in konvertieren **Uniqueidentifier**.|  
|enabled_for_internet|**int**|Legt fest, ob die Veröffentlichung für das Internet aktiviert ist. Wenn **1**, werden die Synchronisierungsdateien für die Veröffentlichung eingefügt, in der `C:\Program Files\Microsoft SQL Server\MSSQL\Repldata\Ftp` Verzeichnis. Der Benutzer muss das FTP-Verzeichnis (File Transfer Protocol) erstellen. Wenn **0**, die Veröffentlichung ist nicht für den Internetzugriff aktiviert.|  
|dynamic_filter|**int**|Gibt an, ob ein parametrisierter Zeilenfilter verwendet wird. **0** bedeutet ein parametrisierten Filter wird nicht verwendet.|  
|has_subscription|**bit**|Gibt an, ob die Veröffentlichung über Abonnements verfügt. **0** bedeutet, dass derzeit keine Abonnements für diese Veröffentlichung vorhanden sind.|  
|snapshot_in_default_folder|**bit**|Legt fest, ob die Momentaufnahmedateien im Standardordner gespeichert werden.<br /><br /> Wenn **1**, momentaufnahmedateien im Standardordner speichern befinden.<br /><br /> Wenn **0**, werden momentaufnahmedateien am alternativen Speicherort vom angegebenen gespeichert **Alt_snapshot_folder**. Alternative Speicherorte können sich auf einem anderen Server, auf einem Netzlaufwerk oder auf einem Wechselmedium (z. B. CD-ROM oder Wechseldatenträger) befinden. Momentaufnahmedateien lassen sich auch in einer FTP-Site speichern, um zu einem späteren Zeitpunkt vom Abonnenten abgerufen zu werden.<br /><br /> Hinweis: Dieser Parameter kann "true" werden und immer noch einen Speicherort der **Alt_snapshot_folder** Parameter. Diese Kombination gibt an, dass die Momentaufnahmedateien sowohl an den Standardspeicherorten als auch an den alternativen Standorten gespeichert werden.|  
|alt_snapshot_folder|**nvarchar(255)**|Gibt den Speicherort des anderen Ordners für die Momentaufnahme an.|  
|pre_snapshot_script|**nvarchar(255)**|Gibt einen Zeiger auf ein **.sql** Skripts-Datei, die der Merge-Agent vor allen replizierten Objektskripts ausführt, beim Anwenden der Momentaufnahme auf einem Abonnenten.|  
|post_snapshot_script|**nvarchar(255)**|Gibt einen Zeiger auf ein **.sql** Datei, die der Merge-Agent ausführt nach allen anderen Skripts für replizierte Objekte und Daten während der anfangssynchronisierung angewendet wurden.|  
|compress_snapshot|**bit**|Gibt an, dass die Momentaufnahme, die geschrieben wird die **Alt_snapshot_folder** Speicherort wird in komprimiert die [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB-Format.|  
|ftp_address|**sysname**|Die Netzwerkadresse des FTP-Diensts für den Verteiler. Gibt an, wo die veröffentlichungsmomentaufnahmedateien zum Abholen durch den Merge-Agent gespeichert sind.|  
|ftp_port|**int**|Die Anschlussnummer des FTP-Diensts für den Verteiler. **Ftp_port** hat den Standardwert **21**. Gibt an, wo die Veröffentlichungsmomentaufnahmedateien zum Abholen durch den Merge-Agent gespeichert sind.|  
|ftp_subdirectory|**nvarchar(255)**|Gibt an, wo die Veröffentlichungsmomentaufnahmedateien zum Abholen durch den Merge-Agent gespeichert sind, wenn die Momentaufnahme mithilfe von FTP übermittelt wird.|  
|ftp_login|**sysname**|Der Benutzername wird für die Verbindung mit dem FTP-Dienst verwendet werden.|  
|conflict_retention|**int**|Gibt die Aufbewahrungsdauer in Tagen an, für die Konflikte beibehalten werden. Wenn die angegebene Anzahl von Tagen abgelaufen ist, wird die Konfliktzeile aus der Konflikttabelle gelöscht.|  
|keep_partition_changes|**int**|Gibt an, ob die Synchronisierungsoptimierung für diese Veröffentlichung erfolgt. **Keep_partition_changes** hat den Standardwert **0**. Der Wert **0** bedeutet, dass die Synchronisierung wird nicht optimiert, und die an alle Abonnenten gesendeten Partitionen überprüft werden, wenn sich Daten in einer Partition ändern.<br /><br /> **1** bedeutet, dass die Synchronisierung wird optimiert, und sind nur Abonnenten, die über Zeilen in der geänderten Partition betroffen.<br /><br /> Hinweis: Standardmäßig verwenden mergeveröffentlichungen Vorausberechnete Partitionen, die einen höheren Grad der Optimierung, als diese Option bietet. Weitere Informationen finden Sie unter [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md) und [Optimieren der Leistung parametrisierter Filter mithilfe vorausberechneter Partitionen](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).|  
|allow_subscription_copy|**int**|Gibt an, ob die Möglichkeit zum Kopieren der Abonnementdatenbanken aktiviert wurde, die diese Veröffentlichung abonniert haben. Der Wert **0** bedeutet, dass kopieren nicht zulässig.|  
|allow_synctoalternate|**int**|Gibt an, ob ein alternativer Synchronisierungspartner für die Synchronisierung mit diesem Verleger zulässig ist. Der Wert **0** bedeutet, dass ein alternativer Synchronisierungspartner ist nicht zulässig.|  
|validate_subscriber_info|**nvarchar(500)**|Listet die Funktionen auf, die zum Abrufen der Abonnenteninformationen sowie zum Überprüfen der parametrisierten Zeilenfilterkriterien für den Abonnenten verwendet werden. Dies hilft dabei, zu überprüfen, ob die Informationen bei jedem Mergeprozess konsistent partitioniert werden.|  
|backward_comp_level|**int**|Der Datenbank-Kompatibilitätsgrad. Folgende Werte sind möglich:<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **90**  =  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1<br /><br /> **90**  =  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP2<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|publish_to_activedirectory|**bit**|Gibt an, ob die Veröffentlichungsinformationen in Active Directory veröffentlicht werden. Der Wert **0** bedeutet, dass die Veröffentlichungsinformationen nicht aus Active Directory verfügbar.<br /><br /> Dieser Parameter wurde als veraltet markiert und wird nur zum Sicherstellen der Abwärtskompatibilität von Skripts unterstützt. Sie können Active Directory nicht länger Veröffentlichungsinformationen hinzufügen.|  
|max_concurrent_merge|**int**|Die Anzahl gleichzeitiger Mergeprozesse. Wenn **0**, es gibt keine Beschränkung der Anzahl gleichzeitiger Mergeprozesse, die einem bestimmten Zeitpunkt ausgeführt.|  
|max_concurrent_dynamic_snapshots|**int**|Die maximale Anzahl gleichzeitiger Sitzungen für eine Momentaufnahme gefilterter Daten, die für die Mergeveröffentlichung ausgeführt werden können. Wenn **0**, es gibt keine Beschränkung auf die maximale Anzahl gleichzeitiger datenfilterungs-momentaufnahmesitzungen, die für die Veröffentlichung in einem bestimmten Zeitpunkt ausgeführt werden können.|  
|use_partition_groups|**int**|Legt fest, ob vorausberechnete Partitionen verwendet werden. Der Wert **1** bedeutet, dass Partitionen vorausberechnete verwendet werden.|  
|num_of_articles|**int**|Anzahl der Artikel in der Veröffentlichung.|  
|replicate_ddl|**int**|Gibt an, ob Schemaänderungen an veröffentlichten Tabellen repliziert werden. Der Wert **1** bedeutet, dass schemaänderungen repliziert werden.|  
|publication_number|**smallint**|Die Nummer, die dieser Veröffentlichung zugewiesen ist.|  
|allow_subscriber_initiated_snapshot|**bit**|Legt fest, ob Abonnenten den Prozess für die Generierung eine Momentaufnahme für gefilterte Daten initiieren können. Der Wert **1** bedeutet, dass Abonnenten den momentaufnahmeprozess initiieren können.|  
|allow_web_synchronization|**bit**|Legt fest, ob die Veröffentlichung für die Websynchronisierung aktiviert ist. Der Wert **1** bedeutet, dass die websynchronisierung aktiviert ist.|  
|web_synchronization_url|**nvarchar(500)**|Die für die Websynchronisierung verwendete Internet-URL.|  
|allow_partition_realignment|**bit**|Legt fest, ob Löschvorgänge an den Abonnenten gesendet werden, wenn die Änderung der Zeile auf dem Verleger zum Ändern der Partition führt. Der Wert **1** bedeutet, dass Löschvorgänge an den Abonnenten gesendet werden.  Weitere Informationen finden Sie unter [Sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).|  
|retention_period_unit|**tinyint**|Definiert die Einheit, die beim Definieren der Beibehaltung verwendet wird. Dies kann einen der folgenden Werte sein:<br /><br /> **0** = Tag<br /><br /> **1** = Woche<br /><br /> **2** = Monat<br /><br /> **3** = Jahr|  
|has_downloadonly_articles|**bit**|Gibt an, ob es sich bei Artikeln, die zur Veröffentlichung gehören, um nur herunterladbare Artikel handelt. Der Wert **1** gibt an, dass nur herunterladbare Artikel vorhanden sind.|  
|decentralized_conflicts|**int**|Gibt an, ob die Konfliktdatensätze auf dem Abonnenten gespeichert werden, der den Konflikt verursacht hat. Der Wert **0** gibt an, dass Konfliktdatensätze auf dem Abonnenten nicht gespeichert werden. Ein Wert von 1 gibt an, dass Konfliktdatensätze auf dem Abonnenten gespeichert werden.|  
|generation_leveling_threshold|**int**|Gibt die Anzahl der Änderungen, die in einer Generierung enthalten sind. Eine Generierung ist eine Auflistung von Änderungen, die auf einem Verleger oder Abonnenten übermittelt werden|  
|automatic_reinitialization_policy|**bit**|Gibt an, ob Änderungen vom Abonnenten vor einer automatischen erneuten Initialisierung hochgeladen werden. Der Wert **1** gibt an, dass Änderungen, vor einer automatischen neuinitialisierung vom Abonnenten hochgeladen werden. Der Wert 0 gibt an, dass Änderungen vom Abonnenten vor einer automatischen Neuinitialisierung nicht hochgeladen werden.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_helpmergepublication wird für die Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der Veröffentlichungszugriffsliste für eine Veröffentlichung können sp_helpmergepublication für diese Veröffentlichung ausführen. Mitglieder der festen Datenbankrolle db_owner für die Veröffentlichungsdatenbank können sp_helpmergepublication für Informationen zu allen Veröffentlichungen ausführen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_helpmergepublication](../../relational-databases/replication/codesnippet/tsql/sp-helpmergepublication-_1.sql)]  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [Sp_dropmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
