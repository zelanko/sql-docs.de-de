---
title: Sys.dm_os_volume_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/06/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_volume_stats_TSQL
- dm_os_volume_stats
- sys.dm_os_volume_stats
- sys.dm_os_volume_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_volume_stats dynamic management function
ms.assetid: fa1c58ad-8487-42ad-956c-983f2229025f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7ec8171b569adbf887c1e153fb2b41619778f48
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899720"
---
# <a name="sysdmosvolumestats-transact-sql"></a>sys.dm_os_volume_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-2008R2SP1-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-2008R2sp1-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zum Betriebssystemvolume (Verzeichnis) zurück, in dem die angegebenen Datenbanken und Dateien in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gespeichert sind. Verwenden Sie diese dynamische Verwaltungsfunktion, um die Attribute des physischen Datenträgers zu überprüfen oder um Informationen zum verfügbaren freien Speicherplatz für das Verzeichnis zurückzugeben.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.dm_os_volume_stats (database_id, file_id)  
```  
  
##  <a name="Arguments"></a> Argumente  
 *database_id*  
 Die ID der Datenbank. *database_id* ist vom Datentyp **int**und hat keinen Standardwert. Lässt keine NULL-Werte zu.  
  
 *file_id*  
 Die ID der Datei. *file_id* ist vom Datentyp **int**und hat keinen Standardwert. Lässt keine NULL-Werte zu.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
||||  
|-|-|-|  
|**Spalte**|**Data type**|**Beschreibung**|  
|**database_id**|**int**|Die ID der Datenbank. Lässt keine NULL-Werte zu.|  
|**file_id**|**int**|Die ID der Datei. Lässt keine NULL-Werte zu.|  
|**volume_mount_point**|**nvarchar(512)**|Der Einbindungspunkt, der das Stammverzeichnis des Volumes darstellt. Kann eine leere Zeichenfolge zurückgeben.|  
|**volume_id**|**nvarchar(512)**|Die ID des Betriebssystemvolumes. Kann eine leere Zeichenfolge zurückgeben.|  
|**logical_volume_name**|**nvarchar(512)**|Der Name des logischen Volumes. Kann eine leere Zeichenfolge zurückgeben.|  
|**file_system_type**|**nvarchar(512)**|Der Typ des Dateisystemvolumes (z. B. NTFS, FAT, RAW). Kann eine leere Zeichenfolge zurückgeben.|  
|**total_bytes**|**bigint**|Die Gesamtgröße des Volumes in Bytes. Lässt keine NULL-Werte zu.|  
|**available_bytes**|**bigint**|Der verfügbare freie Speicherplatz auf dem Volume. Lässt keine NULL-Werte zu.|  
|**supports_compression**|**bit**|Gibt an, ob das Volume eine Komprimierung durch das Betriebssystem unterstützt. Lässt keine NULL-Werte zu.|  
|**supports_alternate_streams**|**bit**|Gibt an, ob das Volume alternative Datenströme unterstützt. Lässt keine NULL-Werte zu.|  
|**supports_sparse_files**|**bit**|Gibt an, ob das Volume Sparsedateien unterstützt.  Lässt keine NULL-Werte zu.|  
|**is_read_only**|**bit**|Gibt an, ob das Volume derzeit als schreibgeschützt gekennzeichnet ist. Lässt keine NULL-Werte zu.|  
|**is_compressed**|**bit**|Gibt an, ob dieses Volume derzeit komprimiert ist. Lässt keine NULL-Werte zu.|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-return-total-space-and-available-space-for-all-database-files"></a>A. Zurückgeben des gesamten und des verfügbaren freien Speicherplatzes für alle Datenbankdateien  
 Im folgenden Beispiel werden der gesamte Speicherplatz und der verfügbare freie Speicherplatz (in Bytes) für alle Datenbankdateien in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurückgegeben.  
  
```sql  
SELECT f.database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.master_files AS f  
CROSS APPLY sys.dm_os_volume_stats(f.database_id, f.file_id);  
```  
  
### <a name="b-return-total-space-and-available-space-for-the-current-database"></a>B. Zurückgeben des gesamten und des verfügbaren freien Speicherplatzes für die aktuelle Datenbank  
 Im folgenden Beispiel werden der gesamte Speicherplatz und der verfügbare freie Speicherplatz (in Bytes) für die Datenbankdateien der aktuellen Datenbank zurückgegeben.  
  
```sql  
SELECT database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.database_files AS f  
CROSS APPLY sys.dm_os_volume_stats(DB_ID(f.name), f.file_id);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
  
  
