---
title: Sys.Tables (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- tables_TSQL
- sys.tables_TSQL
- sys.tables
- tables
dev_langs:
- TSQL
helpviewer_keywords:
- sys.tables catalog view
ms.assetid: 8c42eba1-c19f-4045-ac82-b97a5e994090
caps.latest.revision: 70
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 960ffccc2945531aa525c9a1d1db45cc47951190
ms.sourcegitcommit: a7edd16af7be25f627d16e5c8a6e8d6de7071a28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2018
ms.locfileid: "47178316"
---
# <a name="systables-transact-sql"></a>sys.tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jede Benutzertabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|\<geerbte Spalten >||Eine Liste der Spalten, die in dieser Ansicht erbt, finden Sie unter [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|lob_data_space_id|**int**|Ein Wert ungleich 0 (null) ist die ID des Datenbereichs (Dateigruppe oder Partitionsschema), der die LOB-Binärdaten (Large Object) für diese Tabelle enthält. Beispiele für LOB-Datentypen **'varbinary(max)'**, **varchar(max)**, **Geography**, oder **Xml**.<br /><br /> 0 = Die Tabelle enthält keine LOB-Daten.|  
|filestream_data_space_id|**int**|Die ID des Datenbereichs für eine FILESTREAM-Dateigruppe oder ein Partitionsschema, das aus FILESTREAM-Dateigruppen besteht.<br /><br /> Führen Sie die Abfrage, um den Namen einer FILESTREAM-Dateigruppe zu melden, `SELECT FILEGROUP_NAME (filestream_data_space_id) FROM sys.tables`.<br /><br /> sys.tables kann zu den folgenden Sichten über filestream_data_space_id = data_space_id verknüpft werden.<br /><br /> -"Sys.FileGroups"<br /><br /> -sys.partition_schemes<br /><br /> -sys.indexes<br /><br /> -Sys. allocation_units<br /><br /> -Sys. fulltext_catalogs<br /><br /> -sys.data_spaces<br /><br /> -Sys. destination_data_spaces<br /><br /> -Sys. master_files<br /><br /> -Sys. database_files<br /><br /> -Backupfilegroup (Join über Filegroup_id)|  
|max_column_id_used|**int**|Höchste Spalten-ID, die von dieser Tabelle je verwendet wurde|  
|lock_on_bulk_load|**bit**|Die Tabelle wird bei Massenladevorgängen gesperrt. Weitere Informationen finden Sie unter [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).|  
|uses_ansi_nulls|**bit**|Beim Erstellen der Tabelle war die Datenbankoption SET ANSI_NULLS auf ON festgelegt.|  
|is_replicated|**bit**|1 = Die Tabelle wird mithilfe der Momentaufnahme- oder der Transaktionsreplikation veröffentlicht.|  
|has_replication_filter|**bit**|1 = Die Tabelle hat einen Replikationsfilter.|  
|is_merge_published|**bit**|1 = Die Tabelle wird mithilfe der Mergereplikation veröffentlicht.|  
|is_sync_tran_subscribed|**bit**|1 = Die Tabelle wird mithilfe eines Abonnements mit sofortigem Update abonniert.|  
|has_unchecked_assembly_data|**bit**|1 = Die Tabelle enthält persistente Daten, die von einer Assembly abhängen, deren Definition bei der letzten ALTER ASSEMBLY-Anweisung geändert wurde. Der Wert wird nach der nächsten erfolgreichen Ausführung von DBCC CHECKDB oder DBCC CHECKTABLE auf 0 zurückgesetzt.|  
|text_in_row_limit|**int**|Die zulässige Höchstzahl der Bytes für Text in Zeilen.<br /><br /> 0 = Text in Zeile Option nicht festgelegt ist. Weitere Informationen finden Sie unter [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).|  
|large_value_types_out_of_row|**bit**|1 = Umfangreiche Werttypen werden außerhalb der Zeile gespeichert. Weitere Informationen finden Sie unter [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).|  
|is_tracked_by_cdc|**bit**|1 = Tabelle wird für Change Data Capture aktiviert. Weitere Informationen finden Sie unter [Sys. sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).|  
|lock_escalation|**tinyint**|Der Wert der LOCK_ESCALATION-Option für die Tabelle:<br /><br /> 0 = TABLE<br /><br /> 1 = DISABLE<br /><br /> 2 = AUTO|  
|lock_escalation_desc|**nvarchar(60)**|Eine Textbeschreibung der lock_escalation-Option für die Tabelle. Mögliche Werte sind TABLE, AUTO und DISABLE.|  
|is_filetable|**bit**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> 1 = Tabelle ist eine FileTable.<br /><br /> Weitere Informationen zu FileTables finden Sie unter [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md).|  
|durability|**tinyint**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Folgende Werte sind möglich:<br /><br /> 0 = SCHEMA_AND_DATA<br /><br /> 1 = SCHEMA_ONLY<br /><br /> 0 ist der Standardwert.|  
|durability_desc|**nvarchar(60)**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Folgende Werte sind möglich:<br /><br /> SCHEMA_ONLY<br /><br /> SCHEMA_AND_DATA<br /><br /> Der Wert von SCHEMA_AND_DATA gibt an, dass die Tabelle eine dauerhafte speicherinterne Tabelle ist. SCHEMA_AND_DATA ist der Standardwert für Speicheroptimierte Tabellen. Der Wert von SCHEMA_ONLY gibt an, dass die Tabellendaten nicht nach dem Neustart der Datenbank mit speicheroptimierten Objekten beibehalten werden.|  
|is_memory_optimized|**bit**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Folgende Werte sind möglich:<br /><br /> 0 = nicht speicheroptimiert.<br /><br /> 1 = ist speicheroptimiert.<br /><br /> Der Wert 0 ist der Standardwert.<br /><br /> Speicheroptimierte Tabellen sind in-Memory-Benutzertabellen, deren, die Schema, von denen auf dem Datenträger ähnlich anderen Benutzertabellen beibehalten wird. Speicheroptimierte Tabellen nativ aus zugegriffen werden können kompilierten gespeicherten Prozeduren.|  
|temporal_type|**tinyint**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Der numerische Wert, der den Typ der Tabelle darstellt:<br /><br /> 0 = NON_TEMPORAL_TABLE<br /><br /> 1 = HISTORY_TABLE<br /><br /> 2 = SYSTEM_VERSIONED_TEMPORAL_TABLE|  
|temporal_type_desc|**nvarchar(60)**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Die textbeschreibung des Typs der Tabelle:<br /><br /> NON_TEMPORAL_TABLE<br /><br /> HISTORY_TABLE<br /><br /> SYSTEM_VERSIONED_TEMPORAL_TABLE|  
|history_table_id|**int**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].<br /><br /> Wenn Temporal_type IN (2, 4) gibt Object_id der Tabelle, die historische Daten verwaltet. Andernfalls wird NULL zurückgegeben.|  
|is_remote_data_archive_enabled|**bit**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]<br /><br /> Gibt an, ob die Tabelle für Stretch aktiviert ist.<br /><br /> 0 = die Tabelle kann nicht für die Stretch-aktivierten.<br /><br /> 1 = die Tabelle ist Stretch-aktivierten.<br /><br /> Weitere Informationen finden Sie unter [Stretch Database](../../sql-server/stretch-database/stretch-database.md).|  
|is_external|**bit**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)], und [!INCLUDE[sssdwfull](../../includes/sssdwfull-md.md)].<br /><br /> Gibt an, dass die Tabelle eine externe Tabelle ist.<br /><br /> 0 = die Tabelle ist keine externe Tabelle.<br /><br /> 1 = die Tabelle ist eine externe Tabelle.| 
|history_retention_period|**int**|**Gilt für**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]. <br/><br/>Der numerische Wert, der die Beibehaltungsdauer von temporaler Verlaufsdaten in Einheiten, die mit History_retention_period_unit angegeben darstellt. |  
|history_retention_period_unit|**int**|**Gilt für**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]. <br/><br/>Der numerische Wert, der Typ der temporalen Einheit für die verlaufsbeibehaltungsdauer darstellt. <br /><br />-1: UNENDLICH <br /><br />3: TAGE <br /><br />4: WOCHE <br /><br />5: MONAT <br /><br />6: JAHR |  
|history_retention_period_unit_desc|**nvarchar(10)**|**Gilt für**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]. <br/><br/>Die textbeschreibung des Typs der temporalen Einheit für die verlaufsbeibehaltungsdauer. <br /><br />INFINITE <br /><br />DAY <br /><br />WEEK <br /><br />MONTH <br /><br />YEAR |  
|is_node|**bit**|**Gilt für**: [!INCLUDE[sssql17-md.md](../../includes/sssql17-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]. <br/><br/>1 = Dies ist eine Tabelle der Graph-Knoten. <br /><br />0 = Dies ist dabei nicht um eine Knotentabelle Graph. |  
|is_edge|**bit**|**Gilt für**: [!INCLUDE[sssql17-md.md](../../includes/sssql17-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]. <br/><br/>1 = Dies ist eine Graph-Edge-Tabelle. <br /><br />0 = Dies ist dabei nicht um eine Graph-Edge-Tabelle. |  

## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Benutzertabellen zurückgegeben, die keinen Primärschlüssel aufweisen.  
  
```  
SELECT SCHEMA_NAME(schema_id) AS schema_name  
    ,name AS table_name   
FROM sys.tables   
WHERE OBJECTPROPERTY(object_id,'TableHasPrimaryKey') = 0  
ORDER BY schema_name, table_name;  
GO  
  
```  
  
Das folgende Beispiel zeigt, wie verwandte temporale Daten verfügbar gemacht werden können.  
   
**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].
  
```  
SELECT T1.object_id, T1.name as TemporalTableName, SCHEMA_NAME(T1.schema_id) AS TemporalTableSchema,  
T2.name as HistoryTableName, SCHEMA_NAME(T2.schema_id) AS HistoryTableSchema,  
T1.temporal_type_desc  
FROM sys.tables T1  
LEFT JOIN sys.tables T2   
ON T1.history_table_id = T2.object_id  
ORDER BY T1.temporal_type desc  
```  

Das folgende Beispiel zeigt, wie Informationen zur Beibehaltung temporaler Verlaufsdaten verfügbar gemacht werden kann.  

**Gilt für**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)].  
  
```  
SELECT DB.is_temporal_history_retention_enabled, SCHEMA_NAME(T1.schema_id) AS TemporalTableSchema, 
T1.name as TemporalTableName, SCHEMA_NAME(T2.schema_id) AS HistoryTableSchema, T2.name as HistoryTableName,
T1.history_retention_period, T1.history_retention_period_unit_desc
FROM sys.tables T1  
OUTER APPLY (select is_temporal_history_retention_enabled from sys.databases where name = DB_NAME()) DB
LEFT JOIN sys.tables T2   
ON T1.history_table_id = T2.object_id WHERE T1.temporal_type = 2 
```  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [DBCC CHECKDB (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)   
 [DBCC CHECKTABLE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)   
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
