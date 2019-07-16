---
title: dm_db_column_store_row_group_physical_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_column_store_row_group_physical_stats_TSQL
- sys.dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_column_store_row_group_physical_stats
- sys.dm_db_column_store_row_group_physical_stats dynamic management view
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7e5e421935a9642c42a525fe8a25c4c8c9504c97
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68005016"
---
# <a name="sysdmdbcolumnstorerowgroupphysicalstats-transact-sql"></a>dm_db_column_store_row_group_physical_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Stellt die aktuellen Sperren auf Informationen zu allen columnstore-Indizes in der aktuellen Datenbank bereit.  
  
 Dadurch wird die Katalogsicht erweitert [column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md).  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID der zugrunde liegenden Tabelle.|  
|**index_id**|**int**|ID der diesem columnstore-Index für *Object_id* Tabelle.|  
|**partition_number**|**int**|ID der Tabellenpartition, die enthält *Row_group_id*. Sie können partition_number verwenden, um diese DMV mit sys.partitions zu verknüpfen.|  
|**row_group_id**|**int**|ID der dieser Zeilengruppe. Bei partitionierten Tabellen ist dies innerhalb der Partition eindeutig.<br /><br /> -1 für eine in-Memory-Ende.|  
|**delta_store_hobt_id**|**bigint**|Die Hobt_id für eine Zeilengruppe in den deltaspeicher.<br /><br /> NULL, wenn die Zeilengruppe nicht im deltaspeicher ist.<br /><br /> NULL für das Ende einer in-Memory-Tabelle.|  
|**state**|**tinyint**|Verbundene ID-Nummer *State_description*.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED<br /><br /> 4 = TOMBSTONE<br /><br /> KOMPRIMIERTE ist der einzige Zustand, der für in-Memory-Tabellen gilt.|  
|**state_desc**|**nvarchar(60)**|Beschreibung des Status der Zeile:<br /><br /> UNSICHTBARE – eine Zeilengruppe, die erstellt wird. Zum Beispiel: <br />Eine Zeilengruppe in den columnstore-Index ist nicht sichtbar, während die Daten komprimiert wird. Wenn die Komprimierung einer Switch-Metadatenänderungen abgeschlossen ist der Zustand der Zeile columnstore-Gruppe aus nicht sichtbar, COMPRESSED und den Status der Deltastore-Zeilengruppe von geschlossen können ein TOMBSTONING.<br /><br /> GEÖFFNET – eine Deltastore-Zeilengruppe, die neue Zeilen akzeptiert. Eine offene Zeilengruppe befindet sich weiterhin im rowstore-Format und wurde nicht in das columnstore-Format komprimiert.<br /><br /> GESCHLOSSEN – eine Zeilengruppe in den deltaspeicher, der die maximale Anzahl von Zeilen enthält, und wartet darauf, dass tupelverschiebungsprozess, die sie in den Columnstore zu komprimieren.<br /><br /> KOMPRIMIERT: eine Zeilengruppe, die mit columnstore-Komprimierung komprimiert und im Columnstore gespeichert.<br /><br /> TOMBSTONE - verwendet eine Zeilengruppe, die befand sich bisher in den Deltastore und nicht mehr.|  
|**total_rows**|**bigint**|Anzahl der Zeilen, die physischen gespeichert, in der Zeilengruppe. Für komprimierte Zeilengruppen schließt dies die Zeilen, die markiert sind, gelöscht.|  
|**deleted_rows**|**bigint**|Anzahl der Zeilen in einer komprimierten Zeilengruppe physisch gespeichert, die zum Löschen markiert sind.<br /><br /> 0 für Zeilengruppen und Spaltengruppen, die in den deltaspeicher sind.|  
|**size_in_bytes**|**bigint**|Kombinierte Größe in Bytes für alle Seiten in dieser Zeilengruppe. Diese Größe umfasst nicht die Größe, die zum Speichern von Metadaten oder freigegebenen Wörterbüchern erforderlich.|  
|**trim_reason**|**tinyint**|Grund für das die COMPRESSED-Zeilengruppe auf haben ausgelöst ist kleiner als die maximale Anzahl von Zeilen.<br /><br /> 0 – UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION<br /><br /> 1 – NO_TRIM<br /><br /> 2: BULKLOAD<br /><br /> 3 – REORG<br /><br /> 4 – DICTIONARY_SIZE<br /><br /> 5: MEMORY_LIMITATION<br /><br /> 6 – RESIDUAL_ROW_GROUP<br /><br /> 7 - STATS_MISMATCH<br /><br /> 8: SPILLOVER|  
|**trim_reason_desc**|**nvarchar(60)**|Beschreibung der *Trim_reason*.<br /><br /> 0 – UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION: Aufgetreten ist, bei der Aktualisierung von der vorherigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 – NO_TRIM: Die Zeilengruppe wurde nicht abgeschnitten. Die Zeilengruppe wurde mit dem Maximum von 1,048,476 Zeilen komprimiert.  Die Anzahl der Zeilen kann kleiner sein, wenn eine Subsset der Zeilen gelöscht wurde, nachdem Delta-Zeilengruppe geschlossen wurde<br /><br /> 2 – BULKLOAD: Die Batchgröße der Bulk Load beschränkt die Anzahl der Zeilen an.<br /><br /> 3 – REORG:  Komprimierung im Rahmen des neuorganisierungsbefehls wird erzwungen.<br /><br /> 4 – DICTIONARY_SIZE: Größe des Ressourcenverzeichnisses, angewachsen ist zu groß, um alle Zeilen zusammen zu komprimieren.<br /><br /> 5 – MEMORY_LIMITATION: Nicht genügend Arbeitsspeicher verfügbar, um alle Zeilen zusammen zu komprimieren.<br /><br /> 6 – RESIDUAL_ROW_GROUP:  Als Teil der letzten Zeilengruppe mit Zeilen < 1 Million während der indexerstellung geschlossen<br /><br /> STATS_MISMATCH: Nur für Columnstore in in-Memory-Tabelle. Wenn Statistiken nicht ordnungsgemäß angegeben > = 1 Million qualifizierte Zeilen in das Protokollfragment jedoch weniger wurde ermittelt, die komprimierte Zeilengruppe wird < 1 Millionen Zeilen<br /><br /> SPILLOVER: Nur für Columnstore in in-Memory-Tabelle. Tail > 1 million gekennzeichneten Zeilen verfügt, werden die letzten Stapel verbleibenden Zeilen komprimiert ist die Anzahl die 1 Million bis 100 KB|  
|**transition_to_compressed_state**|TINYINT|Zeigt, wie dieser Zeilengruppe aus dem Deltastore in einem komprimierten Zustand in den Columnstore verschoben wurde.<br /><br /> 1 – NOT_APPLICABLE<br /><br /> 2 – INDEX_BUILD<br /><br /> 3 – TUPLE_MOVER<br /><br /> 4 – REORG_NORMAL<br /><br /> 5 – REORG_FORCED<br /><br /> 6: BULKLOAD<br /><br /> 7 - MERGE|  
|**transition_to_compressed_state_desc**|nvarchar(60)|NOT_APPLICABLE - gilt der Vorgang nicht in den deltastore verschoben. Oder, wurde die Zeilengruppe komprimiert, vor dem Upgrade auf [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] in diesem Fall die Versionsgeschichte nicht beibehalten wird.<br /><br /> INDEX_BUILD - Erstellen eines Index oder eines Indexes komprimierte Zeilengruppe.<br /><br /> TUPLE_MOVER - komprimiert, die im Hintergrund ausgeführte tupelverschiebungsvorgang die Zeilengruppe. Dies geschieht, nachdem die Zeilengruppe vom GEÖFFNETEN in geschlossen Zustandsänderungen.<br /><br /> REORG_NORMAL - Neuorganisation des, ALTER INDEX... NEUORGANISATION, die CLOSED-Zeilengruppe aus dem Deltastore in den Columnstore verschoben. Dies ist aufgetreten, bevor der Tuple Mover Zeilengruppe verschieben konnte.<br /><br /> REORG_FORCED - diese Zeilengruppe aufgenommen wurde in den Deltastore geöffnet und wurde in den Columnstore erzwungen, bevor sie eine vollständige Anzahl von Zeilen hatten.<br /><br /> BULKLOAD - komprimiert ein Massenimport die Zeilengruppe direkt ohne Verwendung des deltastores.<br /><br /> MERGE – ein Merge-Vorgang eine oder mehrere Zeilengruppen in diese Zeilengruppe aufgenommen konsolidiert und anschließend ausgeführt, die columnstore-Komprimierung.|  
|**has_vertipaq_optimization**|bit|Vertipaq-Optimierung verbessert die columnstore-Komprimierung durch die neuanordnung der Reihenfolge der Zeilen in der Zeilengruppe, eine höhere Komprimierung zu erreichen. Diese Optimierung erfolgt automatisch in den meisten Fällen. Es gibt zwei Fälle, in die Vertipaq-Optimierung nicht verwendet wird:<br/>  a. Wenn eine Delta-Zeilengruppe wird in den Columnstore verschoben, und es eine oder mehrere nicht gruppierte Indizes für die columnstore-Index gibt - wird in diesem Fall Vertipaq-Optimierung übersprungen, um Änderungen an den Zuordnungsindex minimiert;<br/> b. für columnstore-Indizes für Speicheroptimierte Tabellen. <br /><br /> 0 = Nein<br /><br /> 1 = Ja|  
|**generation**|BIGINT|Zeile Gruppe die Generierung dieser Zeilengruppe zugeordnete.|  
|**created_time**|datetime2|Uhrzeit für die Erstellung dieser Zeilengruppe.<br /><br /> NULL - für einen columnstore-Index für eine in-Memory-Tabelle.|  
|**closed_time**|datetime2|Uhrzeit für die bei dieser Zeilengruppe geschlossen wurde.<br /><br /> NULL - für einen columnstore-Index für eine in-Memory-Tabelle.|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="results"></a>Ergebnisse  
 Gibt eine Zeile für jede Zeilengruppe in der aktuellen Datenbank zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Folgende Berechtigungen sind erforderlich:  
  
-   CONTROL-Berechtigung für die Tabelle.  
  
-   VIEW DATABASE STATE-Berechtigung für die Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-calculate-fragmentaton-to-decide-when-to-reorganize-or-rebuild-a-columnstore-index"></a>A. Fragmentaton, um zu entscheiden, wann Neuorganisieren oder Neuerstellen eines columnstore-Indexes zu berechnen.  
 Für columnstore-Indizes ist dem Prozentsatz der gelöschten Zeilen als guter Maßstab für die Fragmentierung in einer Zeilengruppe. Wenn die Fragmentierung liegt bei 20 % oder mehr es wird empfohlen, die gelöschten Zeilen zu entfernen.  Beispiele finden Sie in [columnstore-Indexdefragmentierung](~/relational-databases/indexes/columnstore-indexes-defragmentation.md).  
  
 In diesem Beispiel verknüpft **dm_db_column_store_row_group_physical_stats** mit anderen Tabellen und berechnet dann die `Fragmentation` Spalte als eine Schätzung der Effizienz der jede Zeilengruppe in der aktuellen Datenbank.     Nach Informationen zu einer einzelnen Tabelle entfernen Sie die kommentarbindestriche vor der **, in denen** -Klausel und geben Sie einen Tabellennamen an.  
  
```sql  
SELECT i.object_id,   
    object_name(i.object_id) AS TableName,   
    i.name AS IndexName,   
    i.index_id,   
    i.type_desc,   
    CSRowGroups.*,  
    100*(ISNULL(deleted_rows,0))/NULLIF(total_rows,0) AS 'Fragmentation'
FROM sys.indexes AS i  
JOIN sys.dm_db_column_store_row_group_physical_stats AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id AND i.index_id = CSRowGroups.index_id   
-- WHERE object_name(i.object_id) = 'table_name'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Beschreibung von Columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
