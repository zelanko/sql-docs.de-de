---
title: sys. Partitions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- partitions
- partitions_TSQL
- sys.partitions_TSQL
- sys.partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partitions catalog view
ms.assetid: 1c19e1b1-c925-4dad-a652-581692f4ab5e
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d56671fd3c1dbd38cc2ff4bc4d9f4331e5484b91
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305024"
---
# <a name="syspartitions-transact-sql"></a>sys.partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile für jede Partition aller Tabellen und der meisten Indizes in der Datenbank. Besondere Indextypen wie Volltext, räumlich und XML sind in dieser Sicht nicht enthalten. Alle Tabellen und Indizes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthalten mindestens eine Partition, unabhängig davon, ob sie explizit partitioniert sind oder nicht.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|Gibt die Partitions-ID an. Ist innerhalb einer Datenbank eindeutig.|  
|object_id|**int**|Gibt die ID des Objekts an, zu dem diese Partition gehört. Jede Tabelle oder Sicht besteht aus mindestens einer Partition.|  
|index_id|**int**|Gibt die ID des Indexes innerhalb des Objekts an, zu dem diese Partition gehört.<br /><br /> 0 = Heap<br />1 = gruppierter Index<br />2 oder höher = nicht gruppierter Index|  
|partition_number|**int**|Eine auf 1 basierende Partitionsnummer im besitzenden Index oder Heap. Für nicht partitionierte Tabellen und Indizes ist der Wert dieser Spalte 1.|  
|hobt_id|**bigint**|Gibt die ID des Data Heap-oder B-Struktur (hubt) an, das die Zeilen für diese Partition enthält.|  
|rows|**bigint**|Gibt die ungefähre Anzahl der Zeilen in dieser Partition an.|  
|filestream_filegroup_id|**smallint**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Gibt die ID der auf dieser Partition gespeicherten FILESTREAM-Dateigruppe an.|  
|data_compression|**tinyint**|Gibt den Status der Komprimierung für jede Partition an:<br /><br /> 0 = NONE <br />1 = ROW <br />2 = PAGE <br />3 = COLUMNSTORE: **Gilt für** : [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />4 = COLUMNSTORE_ARCHIVE: **Gilt für** : [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> **Hinweis**: Volltextindizes werden in jeder Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] komprimiert.|  
|data_compression_desc|**nvarchar(60)**|Gibt den Status der Komprimierung für jede Partition an. Mögliche Werte für rowstore-Tabellen sind NONE, ROW und PAGE. Mögliche Werte für columnstore-Tabellen sind COLUMNSTORE und COLUMNSTORE_ARCHIVE.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Häufig gestellte Fragen zu Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
