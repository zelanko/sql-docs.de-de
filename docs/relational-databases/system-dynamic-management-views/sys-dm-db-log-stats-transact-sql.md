---
title: dm_db_log_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/17/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_log_stats_TSQL
- sys.dm_db_log_stats
- sys.dm_db_log_stats_TSQL
- dm_db_log_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_log_stats dynamic management function
ms.assetid: ''
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: cf12e737a798e671797880667b5fb75930a85847
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278951"
---
# <a name="sysdmdblogstats-transact-sql"></a>dm_db_log_stats (Transact-SQL)   
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

Gibt zurück, zusammenfassende Ebenenattribute und Informationen für Transaktionsprotokolldateien von Datenbanken. Verwenden Sie diese Informationen für die Überwachung und Diagnose der Integrität des Transaktionsprotokolls.   
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
 sys.dm_db_log_stats ( database_id )
```  
  
## <a name="arguments"></a>Argumente  

*Database_id* | NULL | **Standard**

Ist die ID der Datenbank. `database_id` ist `int`. Gültige Eingaben sind die ID einer Datenbank `NULL`, oder `DEFAULT`. Der Standardwert ist `NULL`. `NULL` und `DEFAULT` sind gleichwertig im Kontext der aktuellen Datenbank.  
Die integrierte Funktion [DB_ID](../../t-sql/functions/db-id-transact-sql.md) kann angegeben werden. Bei Verwendung `DB_ID` ohne Angabe eines Datenbanknamens, muss der Kompatibilitätsgrad der aktuellen Datenbank 90 oder höher sein.

  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|database_id    |**int**    |Datenbank-ID |  
|recovery_model |**nvarchar(60)**   |   Das Wiederherstellungsmodell der Datenbank. Zulässige Werte: <br /> SIMPLE<br /> BULK_LOGGED <br /> FULL |  
|log_min_lsn    |**nvarchar(24)**   |   Aktuellen Start [Protokollsequenznummer (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) im Transaktionsprotokoll.|  
|log_end_lsn    |**nvarchar(24)**   |   [Protokollsequenznummer (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) des letzten Protokolldatensatzes im Transaktionsprotokoll.|  
|current_vlf_sequence_number    |**bigint** |   Aktuelle [virtuelle Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) Sequenznummer zum Zeitpunkt der Ausführung.|  
|current_vlf_size_mb    |**float**  |   Aktuelle [virtuelle Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) Größe in MB.|   
|total_vlf_count    |**bigint** |   Gesamtanzahl von [virtuelle Protokolldateien (VLFs)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) im Transaktionsprotokoll. |  
|total_log_size_mb  |**float**  |   Gesamtgröße des Transaktionsprotokolls die Protokollgröße in MB. |  
|active_vlf_count   |**bigint** |   Gesamtzahl der aktiven [virtuelle Protokolldateien (VLFs)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) im Transaktionsprotokoll.|  
|active_log_size_mb |**float**  |   Gesamtgröße des aktiven Transaktionsprotokolls Protokollgröße in MB.|  
|log_truncation_holdup_reason   |**nvarchar(60)**   |   Melden Sie sich die Verzögerung Grund abschneiden. Der Wert ist identisch mit `log_reuse_wait_desc` Spalte `sys.databases`.  (Detaillierte Erklärungen dieser Werte finden Sie unter [das Transaktionsprotokoll](../../relational-databases/logs/the-transaction-log-sql-server.md)). <br />Zulässige Werte: <br />NOTHING<br />CHECKPOINT<br />LOG_BACKUP<br />ACTIVE_BACKUP_OR_RESTORE<br />ACTIVE_TRANSACTION<br />DATABASE_MIRRORING<br />-Replikation<br />DATABASE_SNAPSHOT_CREATION<br />LOG_SCAN<br />AVAILABILITY_REPLICA<br />OLDEST_PAGE<br />XTP_CHECKPOINT<br />ANDERE VORÜBERGEHENDE |  
|log_backup_time    |**datetime**   |   Transaction Log Zeitpunkt der letzten Sicherung.|   
|log_backup_lsn |**nvarchar(24)**   |   Letzte Sicherung des Transaktionsprotokolls [Protokollsequenznummer (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|   
|log_since_last_log_backup_mb   |**float**  |   Protokollgröße in MB seit der letzten Sicherung des Transaktionsprotokolls [Protokollsequenznummer (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|log_checkpoint_lsn |**nvarchar(24)**   |   Letzten Prüfpunkt [Protokollsequenznummer (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|log_since_last_checkpoint_mb   |**float**  |   Protokollgröße in MB seit dem letzten Prüfpunkt [Protokollsequenznummer (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|log_recovery_lsn   |**nvarchar(24)**   |   Wiederherstellung [Protokollsequenznummer (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) der Datenbank. Wenn `log_recovery_lsn` tritt ein, bevor der Prüfpunkt-LSN, `log_recovery_lsn` ist die LSN der ältesten aktiven Transaktion andernfalls `log_recovery_lsn` die Prüfpunkt-LSN ist.|  
|log_recovery_size_mb   |**float**  |   Protokollgröße in MB seit protokollwiederherstellung [Protokollsequenznummer (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch).|  
|recovery_vlf_count |**bigint** |   Gesamtanzahl von [virtuelle Protokolldateien (VLFs)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) wiederhergestellt werden, wenn Failovers oder eines Serverneustarts vorhanden war,. |  


## <a name="remarks"></a>Hinweise
Bei der Ausführung `sys.dm_db_log_stats` für eine Datenbank, das in einer Verfügbarkeitsgruppe als sekundäres Replikat beteiligt ist, wird nur eine Teilmenge der oben beschriebenen Felder zurückgegeben werden.  Derzeit nur `database_id`, `recovery_model`, und `log_backup_time` wird zurückgegeben, wenn für eine sekundäre Datenbank ausgeführt.   

## <a name="permissions"></a>Berechtigungen  
Erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   
  
## <a name="examples"></a>Beispiele  

### <a name="a-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-high-number-of-vlfs"></a>A. Ermitteln von Datenbanken in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz mit einer hohen Anzahl von VLFs   
Die folgende Abfrage gibt die Datenbanken mit mehr als 100 VLFs erstellt, in den Protokolldateien. Große Anzahl von VLFs kann es sich um den Start und Wiederherstellung, Zeitpunkt der Datenbank beeinträchtigen.

```sql  
SELECT name AS 'Database Name', total_vlf_count AS 'VLF count' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id) 
WHERE total_vlf_count  > 100;
```   

### <a name="b-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-transaction-log-backups-older-than-4-hours"></a>B. Ermitteln von Datenbanken in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz mit transaktionsprotokollsicherungen, die älter sind als 4 Stunden   
Die folgende Abfrage ermittelt die letzten Log-Sicherungszeiten für die Datenbanken in der Instanz.

```sql  
SELECT name AS 'Database Name', log_backup_time AS 'last log backup time' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id); 
```

## <a name="see-also"></a>Siehe auch  
[Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)    
  
