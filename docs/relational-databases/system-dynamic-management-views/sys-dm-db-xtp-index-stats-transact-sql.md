---
description: sys.dm_db_xtp_index_stats (Transact-SQL)
title: sys.dm_db_xtp_index_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_index_stats
- dm_db_xtp_index_stats
- sys.dm_db_xtp_index_stats_TSQL
- dm_db_xtp_index_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_index_stats dynamic management view
ms.assetid: 8d0a50b8-2015-4576-930f-e3307dfc888e
author: markingmyname
ms.author: maghan
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3e6cf5401a48623df1a5b0c2338cf9d1c7287231
ms.sourcegitcommit: 32135463a8494d9ed1600a58f51819359e3c09dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2020
ms.locfileid: "91833793"
---
# <a name="sysdm_db_xtp_index_stats-transact-sql"></a>sys.dm_db_xtp_index_stats (Transact-SQL)
[!INCLUDE[sql-asdb-asdbmi](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

  Enthält Statistiken, die seit dem letzten Neustart der Datenbank erfasst wurden.  
  
 Weitere Informationen finden Sie unter [in-Memory-OLTP &#40;in-Memory-Optimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md) und [Richtlinien für die Verwendung von Indizes für Speicher optimierte Tabellen](/previous-versions/sql/sql-server-2016/dn133166(v=sql.130)).  

  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|ID des Objekts, zu dem dieser Index gehört.|  
|xtp_object_id|**bigint**|Interne ID, die der aktuellen Version des-Objekts entspricht.<br /><br /> Hinweis: gilt für [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] .|  
|index_id|**bigint**|Die ID des Index. Die index_id ist nur innerhalb des Objekts eindeutig.|  
|scans_started|**bigint**|Anzahl der ausgeführten In-Memory OLTP-Indexscans. Jeder Auswähl-, Einfüge-, Update- oder Löschvorgang erfordert einen Indexscan.|  
|scans_retries|**bigint**|Anzahl der Indexscans, die wiederholt werden mussten.|  
|rows_returned|**bigint**|Kumulierte Anzahl der Zeilen, die seit dem Erstellen der Tabelle oder dem Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgegeben wurden.|  
|rows_touched|**bigint**|Kumulierte Anzahl der Zeilen, auf die seit dem Erstellen der Tabelle oder dem Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugegriffen wurde.|  
|rows_expiring|**bigint**|Nur interne Verwendung.|  
|rows_expired|**bigint**|Nur interne Verwendung.|  
|rows_expired_removed|**bigint**|Nur interne Verwendung.|  
|phantom_scans_started|**bigint**|Nur interne Verwendung.|  
|phantom_scans_retries|**bigint**|Nur interne Verwendung.|  
|phantom_rows_touched|**bigint**|Nur interne Verwendung.|  
|phantom_expiring_rows_encountered|**bigint**|Nur interne Verwendung.|  
|phantom_expired_rows_encountered|**bigint**|Nur interne Verwendung.|  
|phantom_expired_removed_rows_encountered|**bigint**|Nur interne Verwendung.|  
|phantom_expired_rows_removed|**bigint**|Nur interne Verwendung.|  
|object_address|**varbinary(8)**|Nur interne Verwendung.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung für die aktuelle Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten für speicheroptimierte Tabellen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
