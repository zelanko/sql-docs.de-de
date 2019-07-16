---
title: index_resumable_operations (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.index_resumable_operations_TSQL
- sys.indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes
- sys.index_resumable_operations
ms.assetid: ''
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c934c2fe8357cb4d37484984998edfcb7219c649
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122656"
---
# <a name="indexresumableoperations-transact-sql"></a>Index_resumable_operations (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**index_resumable_operations** ist eine Systemansicht, die überwacht und überprüft den aktuellen Ausführungsstatus für die fortsetzbare indexneuerstellung.  
**Gilt für**: SQL Server 2017 und Azure SQL-Datenbank
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID des Objekts, zu dem dieser Index (nicht NULL-Werte zulässt) gehört.|  
|**index_id**|**int**|Die ID des Indexes (keine NULL-Werte zulässt). **Index_id** ist nur innerhalb des Objekts eindeutig.|
|**name**|**sysname**|Der Name des Indexes. **Namen** ist nur innerhalb des Objekts eindeutig.|  
|**sql_text**|**nvarchar(max)**|Text der DDL-T-SQL-Anweisung|
|**last_max_dop**|**smallint**|Letzte MAX_DOP verwendet (Standard = 0)|
|**partition_number**|**int**|Partitionsnummer im besitzenden Index oder Heap. Für nicht partitionierte Tabellen und Indizes oder im Fall werden alle Partitionen neu erstellt den Wert dieser Spalte NULL ist.|
|**state**|**tinyint**|Betriebszustand für den fortsetzbaren Index:<br /><br />0 = wird ausgeführt<br /><br />1 = anhalten|
|**state_desc**|**nvarchar(60)**|Beschreibung für den Betriebsstatus für den fortsetzbaren Index (ausgeführt oder angehalten)|  
|**start_time**|**datetime**|Startzeit für Index (nicht NULL zulassen)|
|**last_pause_time**|**datatime**| Der Indexvorgang zuletzt angehalten (NULL-Werte zulässt). NULL, wenn der Vorgang ausgeführt wird und nie angehalten wird.|
|**total_execution_time**|**int**|Gesamte Ausführungszeit nach Startzeit in Minuten (nicht NULL zulassen)|
|**percent_complete**|**real**|Index-Vorgang wird ausgeführt-Vervollständigung in % (keine NULL-Werte zulässt).|
|**page_count**|**bigint**|Die Gesamtanzahl von Indexseiten, die von der indexerstellung für die neue und Zuordnung Indizes (nicht NULL-Werte zulässt) zugeordnet.

## <a name="permissions"></a>Berechtigungen

[!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="example"></a>Beispiel

 Dient zum Listen Sie aller eines fortsetzbaren Index Rebuild-Vorgänge auf, die sich im Zustand "angehalten" befinden.

```sql
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```

## <a name="see-also"></a>Siehe auch

- [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)
- [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)
- [Katalogsichten](catalog-views-transact-sql.md)
- [Katalogsichten für Objekte](object-catalog-views-transact-sql.md)
- [sys.indexes](sys-xml-indexes-transact-sql.md)
- [sys.index_columns](sys-index-columns-transact-sql.md)
- [sys.xml_indexes](sys-xml-indexes-transact-sql.md)
- [sys.objects](sys-index-columns-transact-sql.md)
- [sys.key_constraints](sys-key-constraints-transact-sql.md)
- [sys.filegroups](sys-filegroups-transact-sql.md)
- [sys.partition_schemes](sys-partition-schemes-transact-sql.md)
- [Häufig gestellte Fragen zu Abfragen des SQL Server-Systemkatalogs](querying-the-sql-server-system-catalog-faq.md)
