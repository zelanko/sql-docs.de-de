---
title: Was&#39;s neue (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/22/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- what's new [SQL Server Database Engine]
- Database Engine [SQL Server], what's new
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ac9a6a1b2d4107d420bab68659b6d05f25805a38
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067026"
---
# <a name="what39s-new-database-engine"></a>Was&#39;s neue (Datenbank-Engine)
  Die neueste Version des [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]s enthält neue Funktionen und Erweiterungen, die die Leistungsfähigkeit und Produktivität von Architekten, Entwicklern und Administratoren erhöhen, die Datenspeichersysteme entwerfen, entwickeln und pflegen. Das [!INCLUDE[ssDE](../includes/ssde-md.md)] wurde in den folgenden Bereichen verbessert.  
  
##  <a name="Feature"></a> Erweiterungen der Datenbank-Engine-Funktion  
  
###  <a name="MemoryOpt"></a> Speicheroptimierte Tabellen  
 In-Memory OLTP ist ein speicheroptimiertes, in die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Engine integrierte Datenbank-Engine. In-Memory OLTP wurde für OLTP optimiert. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
 
  
###  <a name="DataFiles"></a> SQL Server-Datendateien in Microsoft Azure  
 [SQL Server-Datendateien in Windows Azure](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md) bietet systemeigene Unterstützung für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbankdateien, die als Windows Azure-Blobs gespeichert. Mit dieser Funktion können Sie eine Datenbank in einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] erstellen, der lokal oder auf einem virtuellen Computer in Windows Azure ausgeführt wird und der Ihre Daten an einem dedizierten Speicherort im Windows Azure-BLOB-Speicher vorhält.  
  
  
###  <a name="AzureVM"></a> Hosten eine SQL Server-Datenbank in einer Windows Azure-VM  
 Verwenden der [SQL Server-Datenbank auf einem Windows Azure-Computer bereitstellen](http://msdn.microsoft.com/library/dn195938\(v=sql.120\).aspx) Assistenten zum Hosten einer Datenbank von einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in einem Windows Azure-Computer.  
  
  
###  <a name="Backup"></a> Sicherung und Wiederherstellung-Verbesserungen  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] umfasst die folgenden Erweiterungen für die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Sicherung und -Wiederherstellung:  
  
-   **SQL Server-Sicherung über URLs**  
  
     Die in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] SP1 CU2 eingeführte [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]-Sicherung über URLs wird nur von [!INCLUDE[tsql](../includes/tsql-md.md)], PowerShell und SMO unterstützt. In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] können Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] für die Sicherung oder Wiederherstellung im Windows Azure-BLOB-Speicherdienst verwenden. Die neue Option ist sowohl für Sicherungsaufgaben als auch für Wartungspläne verfügbar. Weitere Informationen finden Sie unter [Verwenden des Sicherungstasks in SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#BackupTaskSSMS), [SQL Server Backup to URL Using Maintenance Plan Wizard](../relational-databases/backup-restore/sql-server-backup-to-url.md#MaintenanceWiz), und [wiederherstellen aus dem Windows Azure-Speicher mit SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#RestoreSSMS).  
  
-   **SQL Server Managed Backup für Microsoft Azure**  
  
     Der Dienst [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] basiert auf der [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Sicherung über URLs und wird von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zum Verwalten und Planen von Datenbank- und Protokollsicherungen bereitgestellt. In dieser Version wird nur die Sicherung im Windows Azure-Speicher unterstützt. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] kann sowohl auf Datenbank- als auch auf Instanzebene konfiguriert werden und ermöglicht die präzise Steuerung auf Datenbankebene sowie die Automatisierung auf Instanzebene. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] kann auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanzen konfiguriert werden, die lokal ausgeführt werden, und auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanzen auf virtuellen Computern in Windows Azure und wird für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanzen empfohlen, die auf virtuellen Computern in Windows Azure ausgeführt werden. Weitere Informationen finden Sie unter [SQL Server Managed Backup für Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
-   **Verschlüsselung von Sicherungen**  
  
     Sie haben jetzt die Möglichkeit, die Sicherungsdatei während eines Sicherungsvorgangs zu verschlüsseln.  Es werden mehrere Verschlüsselungsalgorithmen unterstützt, einschließlich AES 128, AES, AES 192 256 und Triple DES. Sie müssen entweder ein Zertifikat oder einen asymmetrischen Schlüssel verwenden, um während des Sicherungsvorgangs eine Verschlüsselung auszuführen. Weitere Informationen finden Sie unter [Sicherungsverschlüsselung](../relational-databases/backup-restore/backup-encryption.md).  
  
  
###  <a name="CE"></a> Neues Design für die Schätzung der Kardinalität  
 Die Logik der kardinalitätsschätzung, wird im neu entworfenen [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] zur Verbesserung der Qualität von Abfrageplänen und somit auch um die abfrageleistung zu verbessern. Die neue Kardinalitätsschätzung umfasst Annahmen und Algorithmen, die sich optimal mit den heutigen OLTP- und Data Warehouse-Arbeitsauslastungen ergänzen. Sie basiert auf intensiven Forschungen zum Verhalten der Kardinalitätsschätzung in heutigen Arbeitsauslastungen sowie auf unseren eigenen Erkenntnissen, die wir in den letzten 15 Jahren bei der Optimierung der SQL Server-Kardinalitätsschätzung gewonnen haben. Das Feedback unserer Kunden zeigt, dass die meisten Abfragen von den Änderungen profitieren oder mindestens mit gleicher Leistung ausgeführt werden. Bei einer geringen Zahl von Abfragen kann jedoch eine Verschlechterung gegenüber der früheren Kardinalitätsschätzung auftreten. Leistung optimieren und testen die Empfehlungen, finden Sie unter [Kardinalitätsschätzung &#40;SQL Server&#41;](../relational-databases/performance/cardinality-estimation-sql-server.md).  
   
  
###  <a name="Durability"></a> Verzögerte Dauerhaftigkeit  
 In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] wurde die Möglichkeit eingeführt, die Latenz zu verringern, indem einige oder alle Transaktionen als verzögert dauerhaft festgelegt werden. Bei einer verzögert dauerhaften Transaktion wird die Steuerung an den Client zurückgegeben, bevor der Transaktionsprotokoll-Datensatz auf den Datenträger geschrieben wird. Dauerhaftigkeit kann auf Datenbankebene, auf COMMIT-Ebene oder auf ATOMIC-Blockebene gesteuert werden.  
  
 Weitere Informationen finden Sie im Thema [Steuern der Transaktionsdauerhaftigkeit](../relational-databases/logs/control-transaction-durability.md).  
  
  
###  <a name="AlwaysOn"></a> AlwaysOn-Erweiterungen  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] enthält die folgenden Erweiterungen für AlwaysOn-Failoverclusterinstanzen und AlwaysOn-Verfügbarkeitsgruppen:  
  
-   Ein Assistent zum Hinzufügen von Azure-Replikaten vereinfacht das Erstellen von Hybridlösungen für AlwaysOn-Verfügbarkeitsgruppen. Weitere Informationen finden Sie unter [verwenden Sie den Assistenten zum Hinzufügen von Azure-Replikaten &#40;SQL Server&#41;](availability-groups/windows/use-the-add-azure-replica-wizard-sql-server.md).  
  
-   Die maximale Anzahl sekundärer Replikate wurde von 4 auf 8 erhöht.  
  
-   Lesbare sekundäre Replikate bleiben jetzt für Lesearbeitslasten weiterhin verfügbar, wenn die Verbindung mit dem primären Replikat getrennt wird oder das Clusterquorum verloren geht.  
  
-   Ab sofort können Failoverclusterinstanzen (FCIs) freigegebene Clustervolumes (CSVs) als freigegebene Clusterdatenträger verwenden. Weitere Informationen finden Sie unter [Failoverclusterinstanzen immer](../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
-   Eine neue Systemfunktion [Sys. fn_hadr_is_primary_replica](/sql/relational-databases/system-functions/sys-fn-hadr-is-primary-replica-transact-sql), und die neue DMV, [dm_io_cluster_valid_path_names](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql), verfügbar ist.  
  
-   Die folgenden DMVs wurden FCI-Informationen für erweiterte und jetzt zurück: [Sys. dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [Sys. dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), und [Sys. dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql).  
  
  
###  <a name="OIR"></a> Partitionswechsel und Indizierung  
 Die einzelnen Partitionen der partitionierten Tabellen können jetzt neu erstellt werden. Weitere Informationen finden Sie unter [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
   
  
###  <a name="Lock"></a> Verwalten der Sperrenpriorität von Onlinevorgängen  
 Die `ONLINE = ON`-Option verfügt nun über eine `WAIT_AT_LOW_PRIORITY`-Option, mit der angegeben werden kann, wie lange der Neuerstellungsprozess auf die erforderlichen Sperren warten soll. Mithilfe der `WAIT_AT_LOW_PRIORITY`-Option kann zusätzlich die Beendigung blockierender Prozesse konfiguriert werden, die sich auf die REBUILD-Anweisung beziehen. Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) und [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql). Informationen zu neuen sperrstatustypen zur Problembehandlung finden Sie im [Sys. dm_tran_locks &#40;Transact-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) und [Sys. dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).  
 
  
###  <a name="CCI"></a> Columnstore-Indizes  
 Die folgenden neuen Funktionen sind für columnstore-Indizes verfügbar:  
  
-   **Gruppierte columnstore-Indizes**  
  
     Verwenden Sie einen gruppierten columnstore-Index, um die Datenkomprimierung und Abfrageleistung für Data Warehousing-Arbeitsauslastungen zu verbessern, die hauptsächlich Massenladevorgänge und schreibgeschützte Abfragen ausführen. Da der gruppierte columnstore-Index aktualisierbar ist, kann die Arbeitsauslastung viele Einfüge-, Update- und Löschvorgänge ausführen. Weitere Informationen finden Sie unter [Beschreibung von columnstore-Indizes](../relational-databases/indexes/columnstore-indexes-described.md) und [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).  
  
-   **SHOWPLAN**  
  
     SHOWPLAN zeigt Informationen zu columnstore-Indizes an. Die **EstimatedExecutionMode** und **ActualExecutionMode** Eigenschaften verfügen über zwei mögliche Werte: **Batch** oder **Zeile**.  Die **Storage** Eigenschaft verfügt über zwei mögliche Werte: **RowStore** und **ColumnStore**.  
  
-   **Archivierungsdatenkomprimierung**  
  
     ALTER INDEX … REBUILD verfügt über die neue COLUMNSTORE_ARCHIVE-Datenkomprimierungsoption, mit der die angegebenen Partitionen eines columnstore-Indexes stärker komprimiert werden. Verwenden Sie diese Option bei der Archivierung und in Situationen, in denen es auf eine geringere Datenspeichergröße und nicht auf den zusätzlichen Zeitaufwand für das Speichern und Abrufen ankommt. Weitere Informationen finden Sie unter [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
   
  
###  <a name="Buffer"></a> Pufferpoolerweiterung  
 Die [Buffer Pool Extension](configure-windows/buffer-pool-extension.md) bietet die nahtlose Integration von Solid State Drives (SSD) als Erweiterung des Arbeitsspeichers (NvRAM) nicht auf die [!INCLUDE[ssDE](../includes/ssde-md.md)] Pufferpool, um die e/a-Durchsatz deutlich zu verbessern.  
   
  
###  <a name="Stats"></a> Inkrementelle Statistiken  
 CREATE STATISTICS und verwandte Statistikanweisungen ermöglicht jetzt mithilfe der INCREMENTAL-Option die Erstellung von Statistiken pro Partition. Verwandte Anweisungen lassen inkrementelle Statistiken zu oder erstellen Berichte. Zur betroffenen Syntax zählen UPDATE STATISTICS, sp_createstats, CREATE INDEX, ALTER INDEX, ALTER DATABASE SET-Optionen, DATABASEPROPERTYEX, sys.databases und sys.stats. Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
  
###  <a name="RG"></a> Erweiterungen der Ressourcenkontrolle für physische e/a-Steuerelement  
 Über die Ressourcenkontrolle können Sie Grenzwerte für die CPU, physische E/A und den Arbeitsspeicher, d. h. Ressourcen festlegen, die eingehenden Anwendungsanforderungen im Ressourcenpool zur Verfügung stehen. In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] können Sie über die neue MIN_IOPS_PER_VOLUME-Einstellung und MAX_IOPS_PER_VOLUME-Einstellung die physischen E/A-Befehle steuern, die für Benutzerthreads eines bestimmten Ressourcenpools ausgegeben werden. Weitere Informationen finden Sie unter [Resource Governor Resource Pool](../relational-databases/resource-governor/resource-governor-resource-pool.md) und [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql).  
  
 Mit der MAX_OUTSTANDING_IO_PER_VOLUME-Einstellung von ALTER RESOURCE GOVENOR werden die maximalen ausstehenden E/A-Vorgänge pro Datenträgervolume festgelegt. Mit dieser Einstellung können Sie die E/A-Ressourcenkontrolle auf die E/A-Eigenschaften eines Datenträgervolumes abstimmen. Außerdem kann sie die Anzahl der E/A-Befehle auf den Grenzwert der SQL Server-Instanz beschränken. Weitere Informationen finden Sie unter [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql).  
  
  
###  <a name="OnlineEvent"></a> Online Index Operation-Ereignisklasse  
 Der Statusbericht für die online Index Operation-Ereignisklasse enthält jetzt zwei neue Datenspalten: **PartitionId** und **PartitionNumber**. Weitere Informationen finden Sie unter [Progress Report: Online Index Operation-Ereignisklasse](../relational-databases/event-classes/progress-report-online-index-operation-event-class.md).  
  
  
###  <a name="Compat"></a> Datenbank-Kompatibilitätsgrad  
 Der Kompatibilitätsgrad 90 ist in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] nicht gültig. Weitere Informationen finden Sie unter [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
##  <a name="TSQL"></a> Transact-SQL-Erweiterungen  
  
### <a name="inline-specification-of-clustered-and-nonclustered"></a>Inlinespezifikation von CLUSTERED und NONCLUSTERED  
 Die Inlinespezifikation von `CLUSTERED`- und `NONCLUSTERED`-Indizes ist jetzt für datenträgerbasierte Tabellen zulässig. Das Erstellen einer Tabelle mit Inlineindizes entspricht der Ausgabe einer CREATE TABLE-Anweisung gefolgt von den entsprechenden `CREATE INDEX`-Anweisungen. Eingeschlossene Spalten und Filterbedingungen werden bei Inlineindizes nicht unterstützt.  
  
### <a name="select--into"></a>SELECT … INTO  
 Die `SELECT … INTO`-Anweisung wurde verbessert und kann nun parallel ausgeführt werden. Der Kompatibilitätsgrad der Datenbank muss auf mindestens 110 festgelegt werden.  
  
### <a name="includetsqlincludestsql-mdmd-enhancements-for-in-memory-oltp"></a>[!INCLUDE[tsql](../includes/tsql-md.md)]-Erweiterungen für In-Memory OLTP  
 Informationen zu den [!INCLUDE[tsql](../includes/tsql-md.md)] Änderungen zur Unterstützung von In-Memory-OLTP finden Sie unter [Transact-SQL-Unterstützung für In-Memory OLTP](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md).  
  
  
##  <a name="SystemTable"></a> Systemsichterweiterungen  
  
### <a name="sysxmlindexes"></a>sys.xml_indexes  
 [Sys. xml_indexes &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-xml-indexes-transact-sql) verfügt über 3 neue Spalten: `xml_index_type`, `xml_index_type_description`, und `path_id`.  
  
### <a name="sysdmexecqueryprofiles"></a>sys.dm_exec_query_profiles  
 [dm_exec_query_profiles &#40;Transact-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql) überwacht Real-Time-Abfrage wird ausgeführt, während eine Abfrage ausgeführt wird.  
  
### <a name="syscolumnstorerowgroups"></a>sys.column_store_row_groups  
 [column_store_row_groups &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql) enthält Informationen zu gruppierten columnstore-Indizes auf Segmentbasis an den Administrator System bei Fragen zur systemverwaltung zu unterstützen.  
  
### <a name="sysdatabases"></a>sys.databases  
 [Sys.Databases &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) verfügt über 3 neue Spalten: `is_auto_create_stats_incremental_on`, `is_query_store_on`, und `resource_pool_id`.  
  
### <a name="system-view-enhancements-for-in-memory-oltp"></a>Systemsichterweiterungen für In-Memory OLTP  
 Weitere Informationen zu den systemsichterweiterungen zur Unterstützung von In-Memory-OLTP finden Sie unter [Systemsichten, gespeicherte Prozeduren, DMVs und Wartetypen für In-Memory OLTP](../../2014/database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md).  
   
  
##  <a name="Security"></a> Sicherheitserweiterungen  
  
### <a name="connect-any-database-permission"></a>CONNECT ANY DATABASE-Berechtigung  
 Eine neue Berechtigung auf Serverebene. Erteilen Sie die **CONNECT ANY DATABASE**-Berechtigung einem Anmeldenamen, der eine Verbindung mit allen derzeit vorhandenen Datenbanken und allen zukünftig erstellten neuen Datenbanken herstellen muss. Gewährt keine Berechtigung für Datenbanken außer der Berechtigung zum Herstellen der Verbindung. Kombinieren mit **SELECT ALL USER SECURABLES** oder `VIEW SERVER STATE` können ein Überwachungsprozess das Anzeigen von alle Daten oder aller Datenbankstatus in der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="impersonate-any-login-permission"></a>IMPERSONATE ANY LOGIN-Berechtigung  
 Eine neue Berechtigung auf Serverebene. Wenn die Berechtigung erteilt wird, kann ein Prozess der mittleren Ebene beim Herstellen der Verbindung mit Datenbanken die Identität des Kontos von Clients annehmen, die eine Verbindung mit ihm herstellen. Wenn die Berechtigung verweigert wird, kann verhindert werden, dass ein Anmeldename mit hohen Privilegien die Identität anderer Anmeldenamen annimmt. Beispielsweise kann verhindert werden, dass ein Anmeldename mit einer **CONTROL SERVER**-Berechtigung die Identität anderer Anmeldenamen annimmt.  
  
### <a name="select-all-user-securables-permission"></a>SELECT ALL USER SECURABLES-Berechtigung  
 Eine neue Berechtigung auf Serverebene. Wenn sie erteilt wird, kann ein Anmeldename, z. B. ein Auditor, Daten in allen Datenbanken anzeigen, mit denen der Benutzer eine Verbindung herstellen kann.  
  
  
##  <a name="Deployment"></a> Verbesserungen für die Bereitstellung  
### <a name="azure-vm"></a>Azure VM
[Bereitstellen einer SQL Server-Datenbank mit einem Microsoft Azure-Computer](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) ermöglicht die Bereitstellung von einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbank auf Windows Azure-VM.  

### <a name="refs"></a>ReFS
Bereitstellung von Datenbanken auf ReFS wird jetzt unterstützt.   
  
## <a name="see-also"></a>Siehe auch  
 [Von den SQL Server 2014-Editionen unterstützte Funktionen](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
   
