---
title: '&#39;Neuerungen (Datenbank-Engine) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/22/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- what's new [SQL Server Database Engine]
- Database Engine [SQL Server], what's new
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5e51cda61bb44d1f143cab50901276b927cca73a
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176078"
---
# <a name="what39s-new-database-engine"></a>&#39;Neues (Datenbank-Engine)
  Die neueste Version des [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]s enthält neue Funktionen und Erweiterungen, die die Leistungsfähigkeit und Produktivität von Architekten, Entwicklern und Administratoren erhöhen, die Datenspeichersysteme entwerfen, entwickeln und pflegen. Das [!INCLUDE[ssDE](../includes/ssde-md.md)] wurde in den folgenden Bereichen verbessert.  
  
##  <a name="Feature"></a>Erweiterungen der Datenbank-Engine Features  
  
###  <a name="MemoryOpt"></a>Speicher optimierte Tabellen  
 In-Memory OLTP ist ein speicheroptimiertes, in die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Engine integrierte Datenbank-Engine. In-Memory OLTP wurde für OLTP optimiert. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
 
  
###  <a name="DataFiles"></a>SQL Server von Datendateien in Azure  
 [SQL Server Datendateien in Azure](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md) ermöglicht Native Unterstützung [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für Datenbankdateien, die als Azure-blobspeicher gespeichert sind. Diese Funktion ermöglicht es Ihnen, eine Datenbank in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zu erstellen, die lokal oder auf einem virtuellen Computer in Azure ausgeführt wird, wobei ein dedizierter Speicherort für Ihre Daten in Azure BLOB Storage.  
  
  
###  <a name="AzureVM"></a>Hosten einer SQL Server-Datenbank auf einem virtuellen Azure-Computer  
 Verwenden Sie den Assistenten zum Bereitstellen [einer SQL Server Datenbank auf einem virtuellen Azure-Computer](https://msdn.microsoft.com/library/dn195938\(v=sql.120\).aspx) , um eine Datenbank [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] von einer Instanz von auf einem virtuellen Azure-Computer zu hosten.  
  
  
###  <a name="Backup"></a>Sicherungs-und Wiederherstellungs Erweiterungen  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] umfasst die folgenden Erweiterungen für die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Sicherung und -Wiederherstellung:  
  
-   **SQL Server-Sicherung über URLs**  
  
     Die in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] SP1 CU2 eingeführte [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]-Sicherung über URLs wird nur von [!INCLUDE[tsql](../includes/tsql-md.md)], PowerShell und SMO unterstützt. In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] können Sie zum [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] sichern oder Wiederherstellen aus dem Azure-BLOB-Speicherdienst verwenden. Die neue Option ist sowohl für Sicherungsaufgaben als auch für Wartungspläne verfügbar. Weitere Informationen finden Sie unter [Verwenden von Sicherungs Tasks in SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#BackupTaskSSMS), [SQL Server Sicherung über URLs mithilfe des Wartungsplanungs-Assistenten](../relational-databases/backup-restore/sql-server-backup-to-url.md#MaintenanceWiz)und [Wiederherstellen aus Azure Storage mithilfe von SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#RestoreSSMS).  
  
-   **SQL Server verwaltete Sicherung in Azure**  
  
     Der Dienst [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] basiert auf der [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Sicherung über URLs und wird von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zum Verwalten und Planen von Datenbank- und Protokollsicherungen bereitgestellt. In dieser Version wird nur die Sicherung in Azure Storage unterstützt. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] kann sowohl auf Datenbank- als auch auf Instanzebene konfiguriert werden und ermöglicht die präzise Steuerung auf Datenbankebene sowie die Automatisierung auf Instanzebene. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]kann für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Instanzen konfiguriert werden, die lokal ausgeführt werden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , sowie für Instanzen, die auf virtuellen Azure-Computern ausgeführt werden. Dies wird für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Instanzen empfohlen, die auf virtuellen Azure-Computern ausgeführt werden. Weitere Informationen finden Sie unter [SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
-   **Verschlüsselung für Sicherungen**  
  
     Sie haben jetzt die Möglichkeit, die Sicherungsdatei während eines Sicherungsvorgangs zu verschlüsseln.  Es werden mehrere Verschlüsselungsalgorithmen unterstützt, einschließlich AES 128, AES, AES 192 256 und Triple DES. Sie müssen entweder ein Zertifikat oder einen asymmetrischen Schlüssel verwenden, um während des Sicherungsvorgangs eine Verschlüsselung auszuführen. Weitere Informationen finden Sie unter [Verschlüsseln der Sicherung](../relational-databases/backup-restore/backup-encryption.md).  
  
  
###  <a name="CE"></a>Neuer Entwurf für die Kardinalitätsschätzung  
 Die Logik der Kardinalitätsschätzung wurde in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] überarbeitet, um die Qualität von Abfrageplänen und somit die Abfrageleistung zu verbessern. Die neue Kardinalitätsschätzung umfasst Annahmen und Algorithmen, die sich optimal mit den heutigen OLTP- und Data Warehouse-Arbeitsauslastungen ergänzen. Sie basiert auf intensiven Forschungen zum Verhalten der Kardinalitätsschätzung in heutigen Arbeitsauslastungen sowie auf unseren eigenen Erkenntnissen, die wir in den letzten 15 Jahren bei der Optimierung der SQL Server-Kardinalitätsschätzung gewonnen haben. Das Feedback unserer Kunden zeigt, dass die meisten Abfragen von den Änderungen profitieren oder mindestens mit gleicher Leistung ausgeführt werden. Bei einer geringen Zahl von Abfragen kann jedoch eine Verschlechterung gegenüber der früheren Kardinalitätsschätzung auftreten. Empfehlungen zur Leistungsoptimierung und zum Testen finden Sie unter [Kardinalitätsschätzung &#40;SQL Server&#41;](../relational-databases/performance/cardinality-estimation-sql-server.md).  
   
  
###  <a name="Durability"></a>Verzögerte Dauerhaftigkeit  
 In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] wurde die Möglichkeit eingeführt, die Latenz zu verringern, indem einige oder alle Transaktionen als verzögert dauerhaft festgelegt werden. Bei einer verzögert dauerhaften Transaktion wird die Steuerung an den Client zurückgegeben, bevor der Transaktionsprotokoll-Datensatz auf den Datenträger geschrieben wird. Dauerhaftigkeit kann auf Datenbankebene, auf COMMIT-Ebene oder auf ATOMIC-Blockebene gesteuert werden.  
  
 Weitere Informationen finden Sie im Thema [Steuern der Transaktions Dauerhaftigkeit](../relational-databases/logs/control-transaction-durability.md).  
  
  
###  <a name="AlwaysOn"></a>AlwaysOn-Erweiterungen  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] enthält die folgenden Erweiterungen für AlwaysOn-Failoverclusterinstanzen und AlwaysOn-Verfügbarkeitsgruppen:  
  
-   Ein Assistent zum Hinzufügen von Azure-Replikaten vereinfacht das Erstellen von Hybridlösungen für AlwaysOn-Verfügbarkeitsgruppen. Weitere Informationen finden Sie unter [Verwenden des Assistenten &#40;zum Hinzufügen von&#41;Azure](availability-groups/windows/use-the-add-azure-replica-wizard-sql-server.md)-Replikaten SQL Server.  
  
-   Die maximale Anzahl sekundärer Replikate wurde von 4 auf 8 erhöht.  
  
-   Lesbare sekundäre Replikate bleiben jetzt für Lesearbeitslasten weiterhin verfügbar, wenn die Verbindung mit dem primären Replikat getrennt wird oder das Clusterquorum verloren geht.  
  
-   Ab sofort können Failoverclusterinstanzen (FCIs) freigegebene Clustervolumes (CSVs) als freigegebene Clusterdatenträger verwenden. Weitere Informationen finden Sie unter [Always on](../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)-Failoverclusterinstanzen.  
  
-   Die neue Systemfunktion [sys. fn_hadr_is_primary_replica](/sql/relational-databases/system-functions/sys-fn-hadr-is-primary-replica-transact-sql)und eine neue DMV, [sys. DM _io_cluster_valid_path_names](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql), sind verfügbar.  
  
-   Die folgenden DMVs wurden verbessert und geben jetzt FCI-Informationen zurück: [sys. DM _hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys. DM _hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)und [sys. DM _hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql).  
  
  
###  <a name="OIR"></a>Partitions Wechsel und Indizierung  
 Die einzelnen Partitionen der partitionierten Tabellen können jetzt neu erstellt werden. Weitere Informationen finden Sie unter [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
   
  
###  <a name="Lock"></a>Verwalten der sperrenpriorität von Online Vorgängen  
 Die `ONLINE = ON`-Option verfügt nun über eine `WAIT_AT_LOW_PRIORITY`-Option, mit der angegeben werden kann, wie lange der Neuerstellungsprozess auf die erforderlichen Sperren warten soll. Mithilfe der `WAIT_AT_LOW_PRIORITY`-Option kann zusätzlich die Beendigung blockierender Prozesse konfiguriert werden, die sich auf die REBUILD-Anweisung beziehen. Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) und [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql). Informationen zur Problembehandlung für neue Typen von Sperr Zuständen finden Sie in [sys. &#40;DM _tran_locks Transact&#41; -SQL](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) und [sys. &#40;DM _os_wait_stats Transact&#41;-SQL](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).  
 
  
###  <a name="CCI"></a> Columnstore-Indizes  
 Die folgenden neuen Funktionen sind für columnstore-Indizes verfügbar:  
  
-   **Gruppierte columnstore--Indizes**  
  
     Verwenden Sie einen gruppierten columnstore-Index, um die Datenkomprimierung und Abfrageleistung für Data Warehousing-Arbeitsauslastungen zu verbessern, die hauptsächlich Massenladevorgänge und schreibgeschützte Abfragen ausführen. Da der gruppierte columnstore-Index aktualisierbar ist, kann die Arbeitsauslastung viele Einfüge-, Update- und Löschvorgänge ausführen. Weitere Informationen finden Sie unter [columnstore-Indizes beschrieben](../relational-databases/indexes/columnstore-indexes-described.md) und [Verwenden von gruppierten columnstore-Indizes](../relational-databases/indexes/indexes.md).  
  
-   **SHOWPLAN**  
  
     SHOWPLAN zeigt Informationen zu columnstore-Indizes an. Die **estimatedexecutionmode** -Eigenschaft und die **actualexecutionmode** -Eigenschaft verfügen über zwei mögliche Werte: **Batch** oder **Row**.  Die **Storage** -Eigenschaft verfügt über zwei mögliche Werte: **Rowstore** und **columnstore**.  
  
-   **Datenkomprimierung für Archivierung**  
  
     ALTER INDEX ... Rebuild verfügt über eine neue COLUMNSTORE_ARCHIVE-Daten Komprimierungs Option, mit der die angegebenen Partitionen eines columnstore--Indexes weiter komprimiert werden. Verwenden Sie diese Option bei der Archivierung und in Situationen, in denen es auf eine geringere Datenspeichergröße und nicht auf den zusätzlichen Zeitaufwand für das Speichern und Abrufen ankommt. Weitere Informationen finden Sie unter [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
   
  
###  <a name="Buffer"></a>Puffer Pool Erweiterung  
 Die [Pufferpool Erweiterung](configure-windows/buffer-pool-extension.md) ermöglicht die nahtlose Integration von Solid-State-Laufwerken (SSD) als nicht flüchtige Erweiterung des Zufalls zugriffsspeichers (NVRAM) [!INCLUDE[ssDE](../includes/ssde-md.md)] in den Pufferpool, um den e/a-Durchsatz deutlich zu verbessern.  
   
  
###  <a name="Stats"></a>Krementelle Statistiken  
 CREATE STATISTICS und verwandte Statistikanweisungen ermöglicht jetzt mithilfe der INCREMENTAL-Option die Erstellung von Statistiken pro Partition. Verwandte Anweisungen lassen inkrementelle Statistiken zu oder erstellen Berichte. Zu den betroffenen Syntax zählen Update Statistics, sp_createstats, CREATE Index, Alter Index, ALTER DATABASE SET-Optionen, DATABASEPROPERTYEX, sys. Database und sys. stats. Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
  
###  <a name="RG"></a>Resource Governor Erweiterungen für physisches IO-Steuerelement  
 Über die Ressourcenkontrolle können Sie Grenzwerte für die CPU, physische E/A und den Arbeitsspeicher, d. h. Ressourcen festlegen, die eingehenden Anwendungsanforderungen im Ressourcenpool zur Verfügung stehen. In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] können Sie über die neue MIN_IOPS_PER_VOLUME-Einstellung und MAX_IOPS_PER_VOLUME-Einstellung die physischen E/A-Befehle steuern, die für Benutzerthreads eines bestimmten Ressourcenpools ausgegeben werden. Weitere Informationen finden Sie unter [Resource Governor Ressourcenpools](../relational-databases/resource-governor/resource-governor-resource-pool.md) und [Erstellen eines Ressourcen &#40;Pools Transact-&#41;SQL](/sql/t-sql/statements/create-resource-pool-transact-sql).  
  
 Mit der MAX_OUTSTANDING_IO_PER_VOLUME-Einstellung von ALTER RESOURCE GOVENOR werden die maximalen ausstehenden E/A-Vorgänge pro Datenträgervolume festgelegt. Mit dieser Einstellung können Sie die E/A-Ressourcenkontrolle auf die E/A-Eigenschaften eines Datenträgervolumes abstimmen. Außerdem kann sie die Anzahl der E/A-Befehle auf den Grenzwert der SQL Server-Instanz beschränken. Weitere Informationen finden Sie unter [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql).  
  
  
###  <a name="OnlineEvent"></a>Online Index Operation (Ereignisklasse)  
 Der Fortschrittsbericht für die Online Index Operation-Ereignisklasse enthält jetzt zwei neue Datenspalten: **PartitionID** und **PARTITIONNUMBER**. Weitere Informationen finden [Sie unter Fortschrittsbericht: Online Index Operation-Ereignis](../relational-databases/event-classes/progress-report-online-index-operation-event-class.md)Klasse.  
  
  
###  <a name="Compat"></a>Datenbank-Kompatibilitäts Grad  
 Der Kompatibilitätsgrad 90 ist in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] nicht gültig. Weitere Informationen finden Sie unter [ALTER DATABASE-Kompatibilitäts Grad &#40;(Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) ).  
  
##  <a name="TSQL"></a> Transact-SQL-Erweiterungen  
  
### <a name="inline-specification-of-clustered-and-nonclustered"></a>Inlinespezifikation von CLUSTERED und NONCLUSTERED  
 Die Inlinespezifikation von `CLUSTERED`- und `NONCLUSTERED`-Indizes ist jetzt für datenträgerbasierte Tabellen zulässig. Das Erstellen einer Tabelle mit Inlineindizes entspricht der Ausgabe einer CREATE TABLE-Anweisung gefolgt von den entsprechenden `CREATE INDEX`-Anweisungen. Eingeschlossene Spalten und Filterbedingungen werden bei Inlineindizes nicht unterstützt.  
  
### <a name="select--into"></a>WÄHLEN SIE... INTO  
 Die `SELECT ... INTO`-Anweisung wurde verbessert und kann nun parallel ausgeführt werden. Der Kompatibilitätsgrad der Datenbank muss auf mindestens 110 festgelegt werden.  
  
### <a name="includetsqlincludestsql-mdmd-enhancements-for-in-memory-oltp"></a>[!INCLUDE[tsql](../includes/tsql-md.md)]-Erweiterungen für In-Memory OLTP  
 Informationen zu den Änderungen [!INCLUDE[tsql](../includes/tsql-md.md)] , die in-Memory OLTP unterstützen, finden Sie unter [Transact-SQL-Unterstützung für in-Memory OLTP](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md).  
  
  
##  <a name="SystemTable"></a> Systemsichterweiterungen  
  
### <a name="sysxml_indexes"></a>sys.xml_indexes  
 [sys. XML _indexes &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-xml-indexes-transact-sql) weist drei neue Spalten auf `xml_index_type`: `xml_index_type_description`, und `path_id`.  
  
### <a name="sysdm_exec_query_profiles"></a>sys.dm_exec_query_profiles  
 [sys. DM _exec_query_profiles &#40;Transact-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql) überwacht den Echt Zeit Abfrage Fortschritt, während eine Abfrage ausgeführt wird.  
  
### <a name="syscolumn_store_row_groups"></a>sys.column_store_row_groups  
 [sys. column_store_row_groups &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql) stellt Informationen zu gruppierten columnstore--Indizes auf Segment Basis bereit, damit Administratoren System Verwaltungsentscheidungen treffen können.  
  
### <a name="sysdatabases"></a>sys.databases  
 [sys. Datenbanken &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) weist drei neue Spalten auf `is_auto_create_stats_incremental_on`: `is_query_store_on`, und `resource_pool_id`.  
  
### <a name="system-view-enhancements-for-in-memory-oltp"></a>Systemsichterweiterungen für In-Memory OLTP  
 Informationen zu den Verbesserungen der Systemsicht zur Unterstützung von in-Memory OLTP finden Sie unter [System Sichten, gespeicherte Prozeduren, DMVs und warte Typen für in-Memory OLTP](../../2014/database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md).  
   
  
##  <a name="Security"></a> Sicherheitserweiterungen  
  
### <a name="connect-any-database-permission"></a>CONNECT ANY DATABASE-Berechtigung  
 Eine neue Berechtigung auf Serverebene. Erteilen Sie die **CONNECT ANY DATABASE**-Berechtigung einem Anmeldenamen, der eine Verbindung mit allen derzeit vorhandenen Datenbanken und allen zukünftig erstellten neuen Datenbanken herstellen muss. Gewährt keine Berechtigung für Datenbanken außer der Berechtigung zum Herstellen der Verbindung. Kombinieren **Sie mit Select all User securables** oder `VIEW SERVER STATE` , um einem Überwachungsprozess das Anzeigen aller Daten oder aller Daten Bank Zustände [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]in der-Instanz zu ermöglichen.  
  
### <a name="impersonate-any-login-permission"></a>IMPERSONATE ANY LOGIN-Berechtigung  
 Eine neue Berechtigung auf Serverebene. Wenn die Berechtigung erteilt wird, kann ein Prozess der mittleren Ebene beim Herstellen der Verbindung mit Datenbanken die Identität des Kontos von Clients annehmen, die eine Verbindung mit ihm herstellen. Wenn die Berechtigung verweigert wird, kann verhindert werden, dass ein Anmeldename mit hohen Privilegien die Identität anderer Anmeldenamen annimmt. Beispielsweise kann verhindert werden, dass ein Anmeldename mit einer **CONTROL SERVER**-Berechtigung die Identität anderer Anmeldenamen annimmt.  
  
### <a name="select-all-user-securables-permission"></a>SELECT ALL USER SECURABLES-Berechtigung  
 Eine neue Berechtigung auf Serverebene. Wenn sie erteilt wird, kann ein Anmeldename, z. B. ein Auditor, Daten in allen Datenbanken anzeigen, mit denen der Benutzer eine Verbindung herstellen kann.  
  
  
##  <a name="Deployment"></a>Erweiterungen der Bereitstellung  
### <a name="azure-vm"></a>Azure VM
Bereitstellen [einer SQL Server Datenbank auf einem Microsoft Azure virtuellen Computer](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) ermöglicht die bereit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Stellung einer Datenbank auf einem virtuellen Azure-Computer.  

### <a name="refs"></a>ReFS
Die Bereitstellung von Datenbanken auf refs wird jetzt unterstützt.   
  
## <a name="see-also"></a>Siehe auch  
 [Von den SQL Server 2014-Editionen unterstützte Funktionen](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
   
