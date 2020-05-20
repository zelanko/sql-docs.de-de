---
title: sp_addmergepublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepublication
- sp_addmergepublication_TSQL
helpviewer_keywords:
- sp_addmergepublication
ms.assetid: 28a629a1-7374-4614-9b04-279d290a942a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5d5b7870faed5423d4b12861d18f9bdb85e40c68
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826307"
---
# <a name="sp_addmergepublication-transact-sql"></a>sp_addmergepublication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt eine neue Mergeveröffentlichung. Diese gespeicherte Prozedur wird auf Verlegerebene für die Datenbank ausgeführt, die veröffentlicht wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergepublication [ @publication = ] 'publication'   
    [ , [ @description = ] 'description'   
    [ , [ @retention = ] retention ]   
    [ , [ @sync_mode = ] 'sync_mode' ]   
    [ , [ @allow_push = ] 'allow_push' ]   
    [ , [ @allow_pull = ] 'allow_pull' ]   
    [ , [ @allow_anonymous = ] 'allow_anonymous' ]   
    [ , [ @enabled_for_internet = ] 'enabled_for_internet' ]   
    [ , [ @centralized_conflicts = ] 'centralized_conflicts' ]   
    [ , [ @dynamic_filters = ] 'dynamic_filters' ]   
    [ , [ @snapshot_in_defaultfolder = ] 'snapshot_in_default_folder' ]   
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]   
    [ , [ @pre_snapshot_script = ] 'pre_snapshot_script' ]   
    [ , [ @post_snapshot_script = ] 'post_snapshot_script' ]   
    [ , [ @compress_snapshot = ] 'compress_snapshot' ]   
    [ , [ @ftp_address = ] 'ftp_address' ]   
    [ , [ @ftp_port = ] ftp_port ]   
    [ , [ @ftp_subdirectory = ] 'ftp_subdirectory' ]   
    [ , [ @ftp_login = ] 'ftp_login' ]   
    [ , [ @ftp_password = ] 'ftp_password' ]   
    [ , [ @conflict_retention = ] conflict_retention ]   
    [ , [ @keep_partition_changes = ] 'keep_partition_changes' ]   
    [ , [ @allow_subscription_copy = ] 'allow_subscription_copy' ]   
    [ , [ @allow_synctoalternate = ] 'allow_synctoalternate' ]   
    [ , [ @validate_subscriber_info = ] 'validate_subscriber_info' ]   
    [ , [ @add_to_active_directory = ] 'add_to_active_directory' ]   
    [ , [ @max_concurrent_merge = ] maximum_concurrent_merge ]   
    [ , [ @max_concurrent_dynamic_snapshots = ] max_concurrent_dynamic_snapshots ]  
    [ , [ @use_partition_groups = ] 'use_partition_groups' ]  
    [ , [ @publication_compatibility_level = ] 'backward_comp_level' ]  
    [ , [ @replicate_ddl = ] replicate_ddl ]  
    [ , [ @allow_subscriber_initiated_snapshot = ] 'allow_subscriber_initiated_snapshot' ]   
    [ , [ @allow_web_synchronization = ] 'allow_web_synchronization' ]   
    [ , [ @web_synchronization_url = ] 'web_synchronization_url' ]  
    [ , [ @allow_partition_realignment = ] 'allow_partition_realignment' ]  
    [ , [ @retention_period_unit = ] 'retention_period_unit' ]  
    [ , [ @generation_leveling_threshold = ] generation_leveling_threshold ]  
    [ , [ @automatic_reinitialization_policy = ] automatic_reinitialization_policy ]  
    [ , [ @conflict_logging = ] 'conflict_logging' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Mergeveröffentlichung, die erstellt werden soll. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert und darf nicht als Schlüsselwort all angegeben werden. Der Name der Veröffentlichung muss innerhalb der Datenbank eindeutig sein.  
  
`[ @description = ] 'description'`Die Beschreibung der Veröffentlichung. die *Beschreibung* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @retention = ] retention`Die Beibehaltungs Dauer in Einheiten für die Beibehaltungs Dauer, für die Änderungen für die angegebene *Veröffentlichung*gespeichert werden sollen. die *Beibehaltung* ist vom Datentyp **int**. der Standardwert ist 14 Einheiten. Die Einheiten für die Beibehaltungs Dauer werden durch *retention_period_unit*definiert. Wenn das Abonnement nicht innerhalb der Beibehaltungsdauer synchronisiert wird und die ausstehenden Änderungen von einem Cleanupvorgang auf dem Verteiler entfernt wurden, läuft das Abonnement ab und muss erneut initialisiert werden. Die maximal zulässige Beibehaltungsdauer ist die Anzahl von Tagen zwischen dem 31. Dezember 9999 und dem aktuellen Datum.  
  
> [!NOTE]  
>  Für die Beibehaltungsdauer von Mergeveröffentlichungen gilt eine Kulanzfrist von 24 Stunden, um Abonnenten in verschiedenen Zeitzonen zu unterstützen. Wenn Sie beispielsweise eine Beibehaltungsdauer von einem Tag festgelegt haben, beträgt die tatsächliche Beibehaltungsdauer 48 Stunden.  
  
`[ @sync_mode = ] 'sync_mode'`Der Modus der erst Synchronisierung der Abonnenten mit der Veröffentlichung. *sync_mode* ist vom Datentyp **nvarchar (10)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**native** (Standard)|Erstellt eine Massenkopierprogramm-Ausgabe aller Tabellen im einheitlichen Modus.|  
|**Art**|Erstellt eine Massenkopierprogramm-Ausgabe aller Tabellen im Zeichenmodus. Erforderlich, um [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] und nicht--Abonnenten zu unterstützen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
`[ @allow_push = ] 'allow_push'`Gibt an, ob für die angegebene Veröffentlichung Pushabonnements erstellt werden können. *allow_push* ist vom Datentyp **nvarchar (5)** und hat den Standardwert true, mit dem Pushabonnements für die Veröffentlichung zulässig sind.  
  
`[ @allow_pull = ] 'allow_pull'`Gibt an, ob Pullabonnements für die angegebene Veröffentlichung erstellt werden können. *allow_pull* ist vom Datentyp **nvarchar (5)** und hat den Standardwert true, mit dem Pullabonnements für die Veröffentlichung zulässig sind. Sie müssen true angeben, um Abonnenten zu unterstützen [!INCLUDE[ssEW](../../includes/ssew-md.md)] .  
  
`[ @allow_anonymous = ] 'allow_anonymous'`Gibt an, ob für die angegebene Veröffentlichung anonyme Abonnements erstellt werden können. *allow_anonymous* ist vom Datentyp **nvarchar (5)** und hat den Standardwert true, der anonyme Abonnements für die Veröffentlichung zulässt. Um-Abonnenten zu unterstützen [!INCLUDE[ssEW](../../includes/ssew-md.md)] , müssen Sie " **true**" angeben.  
  
`[ @enabled_for_internet = ] 'enabled_for_internet'`Gibt an, ob die Veröffentlichung für das Internet aktiviert ist, und bestimmt, ob die Momentaufnahme Dateien mithilfe von FTP (File Transfer Protocol) auf einen Abonnenten übertragen werden können. *enabled_for_internet* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **True**gibt an, dass die Synchronisierungs Dateien für die Veröffentlichung im Verzeichnis c:\Programme\Microsoft SQL Server\MSSQL\MSSQL.x\Repldata\Ftp abgelegt werden. Der Benutzer muss das FTP-Verzeichnis erstellen. **False**gibt an, dass die Veröffentlichung nicht für den Internet Zugriff aktiviert ist.  
  
`[ @centralized_conflicts = ] 'centralized_conflicts'`Dieser Parameter wurde als veraltet markiert und wird nur für die Abwärtskompatibilität von Skripts unterstützt. Verwenden Sie *conflict_logging* , um den Speicherort anzugeben, an dem Konflikt Datensätze gespeichert werden.  
  
`[ @dynamic_filters = ] 'dynamic_filters'`Ermöglicht es der Mergeveröffentlichung, parametrisierte Zeilen Filter zu verwenden. *dynamic_filters* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
> [!NOTE]  
>  Sie sollten diesen Parameter nicht angeben, sondern stattdessen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zulassen, damit automatisch festgestellt wird, ob parametrisierte Zeilenfilter verwendet werden. Wenn Sie für *dynamic_filters*den Wert " **true** " angeben, müssen Sie einen parametrisierten Zeilen Filter für den Artikel definieren. Weitere Informationen finden Sie unter [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
`[ @snapshot_in_defaultfolder = ] 'snapshot_in_default_folder'`Gibt an, ob die Momentaufnahme Dateien im Standardordner gespeichert werden. *snapshot_in_default_folder* ist vom Datentyp **nvarchar (5)** und hat den Standardwert true. **True**gibt an, dass Momentaufnahme Dateien im Standardordner gefunden werden. Bei " **false**" werden Momentaufnahme Dateien an dem alternativen Speicherort gespeichert, der durch *alternate_snapshot_folder*angegeben wird. Alternative Speicherorte können sich auf einem anderen Server, auf einem Netzlaufwerk oder auf einem Wechselmedium (z. B. CD-ROM oder Wechseldatenträger) befinden. Momentaufnahmedateien lassen sich auch auf einer FTP-Site (File Transfer Protocol) speichern, um zu einem späteren Zeitpunkt vom Abonnenten abgerufen zu werden. Beachten Sie, dass dieser Parameter auf true festgelegt werden kann und noch über einen Speicherort verfügt, der *alt_snapshot_folder*. Diese Kombination gibt an, dass die Momentaufnahmedateien sowohl im Standardpfad als auch im alternativen Pfad gespeichert werden.  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'`Gibt den Speicherort des alternativen Ordners für die Momentaufnahme an. *alternate_snapshot_folder* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @pre_snapshot_script = ] 'pre_snapshot_script'`Gibt einen Zeiger auf einen Speicherort für **SQL** -Dateien an. *pre_snapshot_script* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Der Merge-Agent führt pre_snapshot_script vor allen Skripts für replizierte Objekte aus, wenn die Momentaufnahme auf einem Abonnenten angewendet wird. Das Skript wird in dem Sicherheitskontext ausgeführt, der vom Merge-Agent beim Herstellen einer Verbindung mit der Abonnementdatenbank verwendet wird. Skripts vor der Momentaufnahme werden nicht auf- [!INCLUDE[ssEW](../../includes/ssew-md.md)] Abonnenten ausgeführt.  
  
`[ @post_snapshot_script = ] 'post_snapshot_script'`Gibt einen Zeiger auf einen Speicherort für **SQL** -Dateien an. *post_snapshot_script* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Der Merge-Agent führt das nach der Momentaufnahme ausgeführte Skript aus, nachdem alle anderen Skripts und Daten für replizierte Objekte während einer Erstsynchronisierung angewendet wurden. Das Skript wird in dem Sicherheitskontext ausgeführt, der vom Merge-Agent beim Herstellen einer Verbindung mit der Abonnementdatenbank verwendet wird. Skripts nach der Momentaufnahme werden nicht auf- [!INCLUDE[ssEW](../../includes/ssew-md.md)] Abonnenten ausgeführt.  
  
`[ @compress_snapshot = ] 'compress_snapshot'`Gibt an, dass die an den ** \@ alt_snapshot_folder** Speicherort geschriebene Momentaufnahme in das CAB-Format komprimiert werden soll [!INCLUDE[msCoName](../../includes/msconame-md.md)] . *compress_snapshot* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **false** gibt an, dass die Momentaufnahme nicht komprimiert wird. **true** gibt an, dass die Momentaufnahme komprimiert werden soll. Momentaufnahmedateien, die größer als 2 GB sind, können nicht komprimiert werden. Komprimierte Momentaufnahmedateien werden an der Stelle dekomprimiert, an der der Merge-Agent ausgeführt wird. Pullabonnements werden in der Regel mit komprimierten Momentaufnahmen verwendet, sodass die Dateien auf dem Abonnenten dekomprimiert werden. Die Momentaufnahme im Standardordner kann nicht komprimiert werden. Um-Abonnenten zu unterstützen [!INCLUDE[ssEW](../../includes/ssew-md.md)] , müssen Sie **false**angeben.  
  
`[ @ftp_address = ] 'ftp_address'`Die Netzwerkadresse des FTP-Dienstanbieter für den Verteiler. *ftp_address* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Gibt an, wo sich Veröffentlichungs Momentaufnahme-Dateien befinden, damit die Merge-Agent eines Abonnenten abgerufen werden. Da diese Eigenschaft für jede Veröffentlichung gespeichert wird, kann jede Veröffentlichung über eine andere *ftp_address*verfügen. Die Veröffentlichung muss die Weitergabe von Momentaufnahmen über FTP unterstützen.  
  
`[ @ftp_port = ] ftp_port`Die Portnummer des FTP-Dienstanbieter für den Verteiler. *ftp_port* ist vom Datentyp **int**. der Standardwert ist 21. Gibt an, wo die Veröffentlichungsmomentaufnahmedateien zum Abholen durch den Merge-Agent eines Abonnenten abgelegt werden. Da diese Eigenschaft für jede Veröffentlichung gespeichert wird, kann jede Veröffentlichung über eine eigene *ftp_port*verfügen.  
  
`[ @ftp_subdirectory = ] 'ftp_subdirectory'`Gibt an, wo die Momentaufnahme Dateien für die Merge-Agent des Abonnenten verfügbar sein werden, wenn die Veröffentlichung das Weitergeben von Momentaufnahmen mithilfe von FTP unterstützt. *ftp_subdirectory* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Da diese Eigenschaft für jede Veröffentlichung gespeichert wird, kann jede Veröffentlichung über eine eigene *ftp_subdirctory* verfügen, oder es kann kein Unterverzeichnis vorhanden sein, das mit einem NULL-Wert angegeben wird.  
  
 Wenn Momentaufnahmen für Veröffentlichungen vorab mit parametrisierten Filtern erstellt werden, dann muss die Datenmomentaufnahme für jede Abonnentenpartition jeweils in einem eigenen Ordner abgelegt sein. Die Verzeichnisstruktur für vorab über FTP generierte Momentaufnahmen muss der folgenden Struktur entsprechen:  
  
 *alternate_snapshot_folder*\ftp \\ *publisher_publicationDB_publication* \\ *PartitionID*.  
  
> [!NOTE]  
>  Die oben kursiv dargestellten Werte sind von den Festlegungen für die Veröffentlichung und Abonnentenpartition abhängig.  
  
`[ @ftp_login = ] 'ftp_login'`Der Benutzername, mit dem eine Verbindung zum FTP-Dienst hergestellt wird. *ftp_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert ' anonymous '.  
  
`[ @ftp_password = ] 'ftp_password'`Das Benutzer Kennwort, das zum Herstellen einer Verbindung mit dem FTP-Dienst verwendet wird. *ftp_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort.  
  
`[ @conflict_retention = ] conflict_retention`Gibt die Beibehaltungs Dauer in Tagen an, für die Konflikte beibehalten werden. *conflict_retention* ist vom Datentyp **int**. der Standardwert ist 14 Tage, bevor die Konflikt Zeile aus der Konflikt Tabelle gelöscht wird.  
  
`[ @keep_partition_changes = ] 'keep_partition_changes'`Gibt an, ob Optimierungen von Partitions Änderungen aktiviert werden sollen, wenn Voraus berechnete Partitionen nicht verwendet werden können. *keep_partition_changes* ist vom Datentyp **nvarchar (5)** und hat den Standardwert true. **false** bedeutet, dass Partitions Änderungen nicht optimiert werden, und wenn Voraus berechnete Partitionen nicht verwendet werden, werden die an alle Abonnenten gesendeten Partitionen überprüft, wenn sich Daten in einer Partition ändern. " **true** " bedeutet, dass Partitions Änderungen optimiert werden und nur Abonnenten, die über Zeilen in den geänderten Partitionen verfügen, betroffen sind. Wenn Sie Voraus berechnete Partitionen verwenden, legen Sie *use_partition_groups* auf **true** fest, und legen Sie *keep_partition_changes* auf **false**fest. Weitere Informationen finden Sie unter [Optimieren Parametrisierter Filter-Leistung mit Vorausberechneten Partitionen ](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
> [!NOTE]  
>  Wenn Sie für *keep_partition_changes*den Wert " **true** " angeben, geben Sie den Wert **1** für den Momentaufnahmen-Agent Parameter **-MaxNetworkOptimization**an. Weitere Informationen zu diesem Parameter finden Sie unter [Replikations Momentaufnahmen-Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md). Weitere Informationen zum Angeben von Agentparametern finden Sie unter [Replikations-Agent-Verwaltung](../../relational-databases/replication/agents/replication-agent-administration.md).  
  
 Bei- [!INCLUDE[ssEW](../../includes/ssew-md.md)] Abonnenten muss *keep_partition_changes* auf true festgelegt werden, um sicherzustellen, dass Löschvorgänge ordnungsgemäß weitergegeben werden. Wenn die Einstellung auf "false" festgelegt ist, erhält der Abonnent möglicherweise mehr Zeilen als erwartet.  
  
`[ @allow_subscription_copy = ] 'allow_subscription_copy'`Aktiviert oder deaktiviert die Möglichkeit zum Kopieren der Abonnement Datenbanken, die diese Veröffentlichung abonnieren. *allow_subscription_copy* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. Die Größe der kopierten Abonnementdatenbank muss weniger als 2 Gigabyte (GB) betragen.  
  
`[ @allow_synctoalternate = ] 'allow_synctoalternate'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @validate_subscriber_info = ] 'validate_subscriber_info'`Listet die Funktionen auf, die verwendet werden, um eine Abonnenten Partition der veröffentlichten Daten zu definieren, wenn parametrisierte Zeilen Filter verwendet werden. *validate_subscriber_info* ist vom Datentyp **nvarchar (500)** und hat den Standardwert NULL. Diese Informationen werden vom Merge-Agent verwendet, um die Abonnentenpartition zu überprüfen. Wenn [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) z. b. im parametrisierten Zeilen Filter verwendet wird, sollte der-Parameter lauten `@validate_subscriber_info=N'SUSER_SNAME()'` .  
  
> [!NOTE]  
>  Sie sollten diesen Parameter nicht angeben, sondern stattdessen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zulassen, damit das Filterkriterium automatisch ermittelt wird.  
  
`[ @add_to_active_directory = ] 'add_to_active_directory'`Dieser Parameter wurde als veraltet markiert und wird nur für die Abwärtskompatibilität von Skripts unterstützt. Für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory ist das Hinzufügen von Veröffentlichungsinformationen nicht länger möglich.  
  
`[ @max_concurrent_merge = ] maximum_concurrent_merge`Die maximale Anzahl gleichzeitiger Mergeprozesse. *maximum_concurrent_merge* ist vom Datentyp **int** und hat den Standardwert 0. Der Wert **0** für diese Eigenschaft bedeutet, dass es keine Beschränkung für die Anzahl gleichzeitiger Mergeprozesse gibt, die zu einem beliebigen Zeitpunkt ausgeführt werden. Diese Eigenschaft legt eine Grenze für die Anzahl von gleichzeitigen Mergeprozessen fest, die zu einem Zeitpunkt für eine Mergeveröffentlichung ausgeführt werden können. Wenn für einen Zeitpunkt eine größere Anzahl von Mergeprozessen geplant ist, als der Wert für eine Ausführung zulässt, werden die überzähligen Aufträge in eine Warteschlange gestellt, in der sie warten, bis ein aktuell ausgeführter Mergeprozess beendet wird.  
  
`[ @max_concurrent_dynamic_snapshots = ] max_concurrent_dynamic_snapshots`Die maximale Anzahl von Momentaufnahmen-Agent Sitzungen, die gleichzeitig ausgeführt werden können, um gefilterte Daten Momentaufnahmen für Abonnenten Partitionen zu generieren. *maximum_concurrent_dynamic_snapshots* ist vom Datentyp **int** und hat den Standardwert 0. Wenn der Wert **0**ist, gibt es keine Beschränkung für die Anzahl von Momentaufnahme Sitzungen. Wenn zum gleichen Zeitpunkt mehr Momentaufnahmeprozesse geplant sind, als der Wert für eine Ausführung zulässt, werden die überschüssigen Aufträge in eine Warteschlange eingereiht, in der sie darauf warten, dass ein aktuell ausgeführter Momentaufnahmeprozess abgeschlossen wird.  
  
`[ @use_partition_groups = ] 'use_partition_groups'`Gibt an, dass Voraus berechnete Partitionen verwendet werden sollen, um den Synchronisierungs Prozess zu optimieren. *use_partition_groups* ist vom Datentyp **nvarchar (5)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**true**|Die Veröffentlichung verwendet vorausberechnete Partitionen.|  
|**false**|Die Veröffentlichung verwendet keine vorausberechneten Partitionen.|  
|NULL (Standard)|Die Partitionierungsstrategie wird vom System festgelegt.|  
  
 Standardmäßig werden vorausberechnete Partitionen verwendet. Um die Verwendung Voraus berechneter Partitionen zu vermeiden, müssen *use_partition_groups* auf **false**festgelegt werden. Wird NULL festgelegt, entscheidet das System, ob vorausberechnete Partitionen verwendet werden können. Wenn Voraus berechnete Partitionen nicht verwendet werden können, wird dieser Wert effektiv zu " **false** ", ohne Fehler zu erzeugen. In solchen Fällen können *keep_partition_changes* auf " **true** " festgelegt werden, um eine Optimierung bereitzustellen. Weitere Informationen finden Sie unter [parametrisierte Zeilen Filter](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md) und [Optimieren der Leistung parametrisierter Filter mit voraus berechneten Partitionen](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
`[ @publication_compatibility_level = ] backward_comp_level`Gibt die Abwärtskompatibilität der Veröffentlichung an. *backward_comp_level* ist vom Datentyp **nvarchar (6)**. die folgenden Werte sind möglich:  
  
|Wert|Version|  
|-----------|-------------|  
|**90RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**100RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
  
`[ @replicate_ddl = ] replicate_ddl`Gibt an, ob die Schema Replikation für die Veröffentlichung unterstützt wird. *replicate_ddl* ist vom Datentyp **int**und hat den Standardwert 1. **1** gibt an, dass DDL-Anweisungen (Data Definition Language), die auf dem Verleger ausgeführt werden, repliziert werden, und **0** bedeutet, dass DDL-Anweisungen nicht repliziert werden Weitere Informationen finden Sie unter [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
 Der * \@ replicate_ddl* -Parameter wird berücksichtigt, wenn eine DDL-Anweisung eine Spalte hinzufügt. Der * \@ replicate_ddl* -Parameter wird ignoriert, wenn eine DDL-Anweisung eine Spalte aus den folgenden Gründen ändert oder löscht.  
  
-   Wenn eine Spalte gelöscht wird, muss sysarticlecolumns aktualisiert werden, um zu verhindern, dass neue DML-Anweisungen die gelöschte Spalte aufnehmen, wodurch der Verteilungs-Agent fehlschlagen würde. Der * \@ replicate_ddl* -Parameter wird ignoriert, da die Replikation die Schema Änderung immer replizieren muss.  
  
-   Wenn eine Spalte geändert wird, hat sich möglicherweise der Quelldatentyp oder die NULL-Zulässigkeit geändert. Dies hat zur Folge, dass DML-Anweisungen einen Wert enthalten, der möglicherweise nicht mit der Tabelle beim Abonnenten kompatibel ist. Solche DML-Anweisungen können bewirken, dass der Verteilungs-Agent fehlschlägt. Der * \@ replicate_ddl* -Parameter wird ignoriert, da die Replikation die Schema Änderung immer replizieren muss.  
  
-   Wenn von einer DDL-Anweisung eine neue Spalte hinzugefügt wird, enthält sysarticlecolumns die neue Spalte nicht. DML-Anweisungen versuchen nicht, Daten für die neue Spalte zu replizieren. Der Parameter wird berücksichtigt, da sowohl das Replizieren als auch das Nicht-Replizieren der DDL akzeptabel ist.  
  
`[ @allow_subscriber_initiated_snapshot = ] 'allow_subscriber_initiated_snapshot'`Gibt an, ob Abonnenten dieser Veröffentlichung den Momentaufnahme Prozess initiieren können, um die gefilterte Momentaufnahme für Ihre Daten Partition zu generieren. *allow_subscriber_initiated_snapshot* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **true** gibt an, dass Abonnenten den Momentaufnahme Prozess initiieren können.  
  
`[ @allow_web_synchronization = ] 'allow_web_synchronization'`Gibt an, ob die Veröffentlichung für die Websynchronisierung aktiviert ist. *allow_web_synchronization* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **true** gibt an, dass Abonnements für diese Veröffentlichung über HTTPS synchronisiert werden können. Weitere Informationen finden Sie unter [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md). Um-Abonnenten zu unterstützen [!INCLUDE[ssEW](../../includes/ssew-md.md)] , müssen Sie " **true**" angeben.  
  
`[ @web_synchronization_url = ] 'web_synchronization_url'`Gibt den Standardwert der Internet-URL an, die für die Websynchronisierung verwendet wird. *web_synchronization_url i*s **nvarchar (500)**, der Standardwert ist NULL. Definiert die Standard-Internet-URL, wenn eine nicht explizit festgelegt wird, wenn [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) ausgeführt wird.  
  
`[ @allow_partition_realignment = ] 'allow_partition_realignment'`Bestimmt, ob Löschvorgänge an den Abonnenten gesendet werden, wenn die Änderung der Zeile auf dem Verleger bewirkt, dass die Partition geändert wird. *allow_partition_realignment* ist vom Datentyp **nvarchar (5)** und hat den Standardwert true. **true** sendet Löschvorgänge an den Abonnenten, um die Ergebnisse einer Partitions Änderung widerzuspiegeln, indem Daten entfernt werden, die nicht mehr Bestandteil der Partition des Abonnenten sind. **false** verlässt die Daten aus einer alten Partition auf dem Abonnenten, bei der Änderungen an diesen Daten auf dem Verleger nicht auf diesen Abonnenten repliziert werden, aber die auf dem Abonnenten vorgenommenen Änderungen werden auf den Verleger repliziert. Wenn Sie *allow_partition_realignment* auf " **false** " festlegen, werden Daten in einem Abonnement aus einer alten Partition beibehalten, wenn die Daten für historische Zwecke zugänglich sein müssen.  
  
> [!NOTE]  
>  Daten, die auf dem Abonnenten verbleiben, weil Sie *allow_partition_realignment* auf **false** festgelegt haben, sollten so behandelt werden, als wären sie schreibgeschützt. Dies wird jedoch vom Replikationssystem nicht erzwungen.  
  
`[ @retention_period_unit = ] 'retention_period_unit'`Gibt die Einheiten für die *Beibehaltungs*Dauer an. *retention_period_unit* ist vom Datentyp **nvarchar (10)**. die folgenden Werte sind möglich:  
  
|Wert|Version|  
|-----------|-------------|  
|**Tag** (Standard)|Die Beibehaltungsdauer wird in Tagen angegeben.|  
|**week**|Die Beibehaltungsdauer wird in Wochen angegeben.|  
|**month**|Die Beibehaltungsdauer wird in Monaten angegeben.|  
|**year**|Die Beibehaltungsdauer wird in Jahren angegeben.|  
  
`[ @generation_leveling_threshold = ] generation_leveling_threshold`Gibt die Anzahl der Änderungen an, die in einer Generierung enthalten sind. Eine Generierung ist eine Auflistung von Änderungen, die an einen Verleger oder Abonnenten übermittelt werden. *generation_leveling_threshold* ist vom Datentyp **int**und hat den Standardwert 1000.  
  
`[ @automatic_reinitialization_policy = ] automatic_reinitialization_policy`Gibt an, ob Änderungen vom Abonnenten vor einer automatischen erneuten Initialisierung hochgeladen werden, die für eine Änderung an der Veröffentlichung erforderlich ist, wobei der Wert **1** für ** \@ force_reinit_subscription**angegeben wurde. *automatic_reinitialization_policy* ist vom Typ Bit und hat den Standardwert 0. **1** bedeutet, dass Änderungen vom Abonnenten hochgeladen werden, bevor eine automatische Neuinitialisierung erfolgt.  
  
> [!IMPORTANT]  
>  Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
`[ @conflict_logging = ] 'conflict_logging'`Gibt an, wo Konflikt Datensätze gespeichert werden. *conflict_logging* ist vom Datentyp **nvarchar (15)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**publisher**|Die Konfliktdatensätze werden auf dem Verleger gespeichert.|  
|**Abonnenten**|Die Konfliktdatensätze werden auf dem Abonnenten gespeichert, der den Konflikt verursacht hat. Wird für Abonnenten nicht unterstützt [!INCLUDE[ssEW](../../includes/ssew-md.md)] .|  
|**zwar**|Die Konfliktdatensätze werden auf dem Verleger und auf dem Abonnenten gespeichert.|  
|NULL (Standard)|Bei der Replikation werden *conflict_logging* automatisch auf festgelegt **, wenn der** Wert *backward_comp_level* **90RTM** und in allen anderen Fällen auf **Herausgeber** festgelegt ist.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addmergepublication** wird bei der Mergereplikation verwendet.  
  
 Zum Auflisten von Veröffentlichungs Objekten für die Active Directory mithilfe des ** \@ add_to_active_directory** -Parameters [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss das Objekt bereits in der Active Directory erstellt werden.  
  
 Wenn mehrere Veröffentlichungen vorhanden sind, die das gleiche Datenbankobjekt veröffentlichen, replizieren nur Veröffentlichungen mit dem *replicate_ddl* Wert **1** die DDL-Anweisungen ALTER TABLE, Alter View, ALTER PROCEDURE, Alter Function und Alter Triggern. Eine ALTER TABLE DROP COLUMN DDL-Anweisung wird hingegen von allen Veröffentlichungen repliziert, die die gelöschte Spalte veröffentlichen.  
  
 Für- [!INCLUDE[ssEW](../../includes/ssew-md.md)] Abonnenten wird der Wert von *alternate_snapshot_folder* nur verwendet, wenn der Wert *snapshot_in_default_folder* **false**ist.  
  
 Wenn die DDL-Replikation (_replicate_ddl_**= 1**) für eine Veröffentlichung aktiviert ist, um nicht replizierende DDL-Änderungen an der Veröffentlichung vorzunehmen, müssen [sp_changemergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) zuerst ausgeführt werden, um *replicate_ddl* auf **0**festzulegen. Nachdem die nicht replizierenden DDL-Anweisungen ausgegeben wurden, kann **sp_changemergepublication** erneut ausgeführt werden, um die DDL-Replikation wieder zu aktivieren.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddMergePub](../../relational-databases/replication/codesnippet/tsql/sp-addmergepublication-t_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addmergepublication**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [sp_changemergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
