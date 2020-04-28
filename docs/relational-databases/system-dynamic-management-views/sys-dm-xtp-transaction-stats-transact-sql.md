---
title: sys. dm_xtp_transaction_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_transaction_stats_TSQL
- dm_xtp_transaction_stats
- sys.dm_xtp_transaction_stats_TSQL
- sys.dm_xtp_transaction_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_transaction_stats dynamic management view
ms.assetid: 9389f48d-0de5-47bd-9821-4db8f04504e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 755b5f836b833512a122ad92e5cedbd7e938a4e8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68090076"
---
# <a name="sysdm_xtp_transaction_stats-transact-sql"></a>sys.dm_xtp_transaction_stats (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Zeigt Statistiken zu Transaktionen, die ausgeführt wurden, seit der Server gestartet wurde.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|total_count|**bigint**|Die Gesamtanzahl der Transaktionen, die in derIn-Memory-OLTP-Datenbank-Engine ausgeführt wurden.|  
|read_only_count|**bigint**|Die Anzahl der schreibgeschützten Transaktionen.|  
|total_aborts|**bigint**|Die Gesamtanzahl der Transaktionen, die durch den Benutzer oder das System abgebrochen wurden.|  
|user_aborts|**bigint**|Die Anzahl der vom System initiierten Abbrüche. Mögliche Ursachen: Schreibkonflikte, Überprüfungsfehler oder Abhängigkeitsfehler.|  
|validation_failures|**bigint**|Die Häufigkeit, mit der eine Transaktion aufgrund eines Überprüfungsfehlers abgebrochen wurde.|  
|dependencies_taken|**bigint**|Nur interne Verwendung.|  
|dependencies_failed|**bigint**|Die Häufigkeit, mit der eine Transaktion aufgrund des Abbruchs einer anderen Transaktion, von der diese abhängig war, abgebrochen wurde.|  
|savepoint_create|**bigint**|Die Anzahl der erstellten Sicherungspunkte. Für jeden atomaren Block wird ein neuer Sicherungspunkt erstellt.|  
|savepoint_rollbacks|**bigint**|Die Anzahl der Rollbacks zu einem vorherigen Sicherungspunkt.|  
|savepoint_refreshes|**bigint**|Nur interne Verwendung.|  
|log_bytes_written|**bigint**|Die Gesamtanzahl von Bytes, die in die In-Memory OLTP-Protokolldatensätze geschrieben werden.|  
|log_IO_count|**bigint**|Die Gesamtzahl der Transaktionen, die Protokoll-EAs erfordern. Berücksichtigt nur Transaktionen für permanente Tabellen.|  
|phantom_scans_started|**bigint**|Nur interne Verwendung.|  
|phantom_scans_retries|**bigint**|Nur interne Verwendung.|  
|phantom_rows_touched|**bigint**|Nur interne Verwendung.|  
|phantom_rows_expiring|**bigint**|Nur interne Verwendung.|  
|phantom_rows_expired|**bigint**|Nur interne Verwendung.|  
|phantom_rows_expired_removed|**bigint**|Nur interne Verwendung.|  
|scans_started|**bigint**|Nur interne Verwendung.|  
|scans_retried|**bigint**|Nur interne Verwendung.|  
|rows_returned|**bigint**|Nur interne Verwendung.|  
|rows_touched|**bigint**|Nur interne Verwendung.|  
|rows_expiring|**bigint**|Nur interne Verwendung.|  
|rows_expired|**bigint**|Nur interne Verwendung.|  
|rows_expired_removed|**bigint**|Nur interne Verwendung.|  
|rows_inserted|**bigint**|Nur interne Verwendung.|  
|rows_updated|**bigint**|Nur interne Verwendung.|  
|rows_deleted|**bigint**|Nur interne Verwendung.|  
|write_conflicts|**bigint**|Nur interne Verwendung.|  
|unique_constraint_violations|**bigint**|Die Gesamtzahl von UNIQUE-Einschränkungsverletzungen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten für speicheroptimierte Tabellen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
