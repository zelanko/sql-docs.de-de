---
title: sys. database_files (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/19/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_files
- sys.database_files_TSQL
- database_files
- database_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_files catalog view
ms.assetid: 0f5b0aac-c17d-4e99-b8f7-d04efc9edf44
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 41132cc875898b98a793e84a35b5c93eee2699e3
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983178"
---
# <a name="sysdatabase_files-transact-sql"></a>sys.database_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile pro Datei einer Datenbank, wie sie in der Datenbank selbst gespeichert ist. Hierbei handelt es sich um eine Sicht pro Datenbank.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|**file_id**|**int**|ID der Datei in der Datenbank|  
|**file_guid**|**uniqueidentifier**|GUID der Datei.<br /><br /> NULL = die Datenbank wurde von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisiert (gültig für SQL Server 2005 und früher).|  
|**Typ**|**tinyint**|Dateityp:<br/><br /> 0 = Zeilen<br /><br/> 1 = Protokoll<br/><br /> 2 = FILESTREAM<br /><br /> 3 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 4 = Volltext|  
|**type_desc**|**nvarchar(60)**|Beschreibung des Dateityps:<br /><br /> ROWS <br /><br /> LOG<br /><br /> FILESTREAM<br /><br /> FULLTEXT|  
|**data_space_id**|**int**|Der Wert kann 0 oder größer sein. Der Wert 0 stellt die Datenbankprotokolldatei dar, und ein Wert größer als 0 stellt die ID der Dateigruppe dar, in der diese Datendatei gespeichert ist.|  
|**name**|**sysname**|Logischer Name der Datei in der Datenbank|  
|**physical_name**|**nvarchar(260)**|Betriebssystem-Dateiname Wenn die Datenbank durch ein [lesbares sekundäres](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)AlwaysOn-Replikat gehostet wird, gibt **physical_name** den Datei Speicherort der primären Replikat Datenbank an. Um den korrekten Datei Speicherort einer lesbaren sekundären Datenbank zu erhalten, Fragen Sie [sys. sysaltfiles](../../relational-databases/system-compatibility-views/sys-sysaltfiles-transact-sql.md)ab.|  
|**state**|**tinyint**|Dateistatus:<br /><br /> 0 = ONLINE<br /><br /> 1 = RESTORING<br /><br /> 2 = RECOVERING<br /><br /> 3 = RECOVERY_PENDING<br /><br /> 4 = SUSPECT<br /><br /> 5 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 6 = OFFLINE<br /><br /> 7 = DEFUNCT|  
|**state_desc**|**nvarchar(60)**|Beschreibung des Dateistatus:<br /><br /> ONLINE<br /><br /> RESTORING<br /><br /> RECOVERING<br /><br /> RECOVERY_PENDING<br /><br /> SUSPECT<br /><br /> OFFLINE<br /><br /> DEFUNCT<br /><br /> Weitere Informationen finden Sie im Abschnitt [Dateistatus](../../relational-databases/databases/file-states.md).|  
|**size**|**int**|Aktuelle Größe der Datei in Seiten mit einer Größe von 8 KB.<br /><br /> 0 = Nicht zutreffend<br /><br /> Bei einer Daten Bank Momentaufnahme gibt Größe den maximalen Speicherplatz an, der von der Momentaufnahme für die Datei verwendet werden kann.<br /><br /> Bei FILESTREAM-Dateigruppen Containern entspricht Größe der aktuellen verwendeten Größe des Containers.|  
|**max_size**|**int**|Maximale Dateigröße in Seiten mit einer Größe von 8 KB:<br /><br /> 0 = Keine Vergrößerung zulässig.<br /><br /> -1 = Datei wird vergrößert, bis der Datenträger voll ist.<br /><br /> 268435456 = Protokolldatei wird bis zu einer maximalen Größe von 2 TB vergrößert.<br /><br /> Bei FILESTREAM-Dateigruppen Containern max_size die maximale Größe des Containers wider.<br /><br /> Beachten Sie, dass für Datenbanken, die mit einer unbegrenzten Protokolldatei Größe aktualisiert werden, der Wert-1 für die maximale Größe der Protokolldatei gemeldet wird.|  
|**growth**|**int**|0 = Die Datei hat eine feste Größe und wird nicht vergrößert.<br /><br /> > 0 = die Datei wird automatisch vergrößert.<br /><br /> Wenn is_percent_growth = 0, liegt das Vergrößerungs Inkrement in Einheiten von 8-KB-Seiten, auf die nächstgelegene 64 KB gerundet.<br /><br /> Wenn is_percent_growth = 1, wird das Vergrößerungs Inkrement als ganze Zahl angegeben.|  
|**is_media_read_only**|**bit**|1 = Die Datei befindet sich auf einem schreibgeschützten Medium.<br /><br /> 0 = Die Datei befindet sich auf einem Lese/Schreib-Medium.|  
|**is_read_only**|**bit**|1 = Die Datei ist als schreibgeschützt gekennzeichnet.<br /><br /> 0 = Die Datei ist als Lese/Schreib-Datei gekennzeichnet.|  
|**is_sparse**|**bit**|1 = Die Datei ist eine Sparsedatei.<br /><br /> 0 = Die Datei ist keine Sparsedatei.<br /><br /> Weitere Informationen finden Sie unter [Anzeigen der Größe der Datei mit geringer Dichte einer Datenbank-Momentaufnahme &#40;Transact-SQL&#41;](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md).|  
|**is_percent_growth**|**bit**|1 = Die Vergrößerung der Datei erfolgt prozentual.<br /><br /> 0 = Absolute Vergrößerung in Seiten.|  
|**is_name_reserved**|**bit**|1 = der gelöschte Dateiname (Name oder physical_name) kann erst nach der nächsten Protokoll Sicherung wieder verwendet werden. Wenn Dateien aus einer Datenbank gelöscht werden, bleiben die logischen Namen bis zur nächsten Protokollsicherung reserviert. Diese Spalte ist nur beim vollständigen und beim massenprotokollierten Wiederherstellungsmodell relevant.|  
|**create_lsn**|**numeric(25,0)**|Protokollfolgenummer (LSN, Log Sequence Number), bei der die Datei erstellt wurde|  
|**drop_lsn**|**numeric(25,0)**|LSN, bei der die Datei gelöscht wurde<br /><br /> 0 = Der Dateiname ist nicht für die Wiederverwendung verfügbar.|  
|**read_only_lsn**|**numeric(25,0)**|LSN, bei der die Dateigruppe mit der Datei von Lesen/Schreiben in Schreibgeschützt geändert wurde (letzte Änderung)|  
|**read_write_lsn**|**numeric(25,0)**|LSN, bei der die Dateigruppe mit der Datei von Schreibgeschützt in Lesen/Schreiben geändert wurde (letzte Änderung)|  
|**differential_base_lsn**|**numeric(25,0)**|Die Basis für differenzielle Sicherungen. Datenblöcke, die nach dieser LSN geändert wurden, werden in eine differenzielle Sicherung eingeschlossen.|  
|**differential_base_guid**|**uniqueidentifier**|Der eindeutige Bezeichner der Basissicherung, auf der eine differenzielle Sicherung basiert.|  
|**differential_base_time**|**datetime**|Zeit, die differential_base_lsn entspricht.|  
|**redo_start_lsn**|**numeric(25,0)**|LSN, bei der das nächste Rollforward beginnen muss.<br /><br /> Ist NULL, es sei denn, State = Wiederherstellung oder state = RECOVERY_PENDING.|  
|**redo_start_fork_guid**|**uniqueidentifier**|Eindeutiger Bezeichner des Verzweigungspunkts. Der first_fork_guid der nächsten wiederhergestellten Protokoll Sicherung muss mit diesem Wert identisch sein. Dies stellt den aktuellen Status der Datei dar.|  
|**redo_target_lsn**|**numeric(25,0)**|Die LSN, bei der das Onlinerollforward für diese Datei beendet werden kann.<br /><br /> Ist NULL, es sei denn, State = Wiederherstellung oder state = RECOVERY_PENDING.|  
|**redo_target_fork_guid**|**uniqueidentifier**|Die Wiederherstellungsverzweigung, auf der die Datei wiederhergestellt werden kann. Gekoppelt mit redo_target_lsn.|  
|**backup_lsn**|**numeric(25,0)**|Die LSN der letzten Datensicherung oder differenziellen Sicherung der Datei.|  
  
> [!NOTE]  
>  Wenn Sie große Indizes löschen oder neu erstellen bzw. wenn Sie große Tabellen löschen oder abschneiden, verzögert [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Aufhebung der aktuellen Seitenzuordnungen sowie die zugehörigen Sperren, bis für die Transaktion ein Commit ausgeführt wird. Bei verzögerten Löschvorgängen wird der zugeordnete Speicherplatz nicht sofort freigegeben. Daher spiegeln die von sys. database_files unmittelbar nach dem Löschen oder Abschneiden eines großen Objekts zurückgegebenen Werte nicht den tatsächlich verfügbaren Speicherplatz wider.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Rolle **public** . Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="examples"></a>Beispiele  
Die folgende Anweisung gibt den Namen, die Dateigröße und die Menge des leeren Speicherplatzes für jede Datenbankdatei zurück.

```
SELECT name, size/128.0 FileSizeInMB,
size/128.0 - CAST(FILEPROPERTY(name, 'SpaceUsed') AS int)/128.0 
   AS EmptySpaceInMB
FROM sys.database_files;
```
Weitere Informationen zum Verwenden von [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]finden Sie unter [bestimmen der Datenbankgröße in Azure SQL-Datenbank V12](https://blogs.msdn.microsoft.com/sqlcat/2016/09/21/determining-database-size-in-azure-sql-database-v12/) im Blog des SQL Customer Advisory Teams.
  
## <a name="see-also"></a>Siehe auch  
 [Datenbanken und Dateikatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Datei](../../relational-databases/databases/file-states.md) Status   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md)   
 [sys.data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)  
  
  
