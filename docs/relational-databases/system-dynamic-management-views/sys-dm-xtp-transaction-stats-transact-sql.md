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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090076"
---
# <a name="sysdm_xtp_transaction_stats-transact-sql"></a>sys.dm_xtp_transaction_stats (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Zeigt Statistiken zu Transaktionen, die ausgeführt wurden, seit der Server gestartet wurde.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|total_count|**BIGINT**|Die Gesamtanzahl der Transaktionen, die in derIn-Memory-OLTP-Datenbank-Engine ausgeführt wurden.|  
|read_only_count|**BIGINT**|Die Anzahl der schreibgeschützten Transaktionen.|  
|total_aborts|**BIGINT**|Die Gesamtanzahl der Transaktionen, die durch den Benutzer oder das System abgebrochen wurden.|  
|user_aborts|**BIGINT**|Die Anzahl der vom System initiierten Abbrüche. Mögliche Ursachen: Schreibkonflikte, Überprüfungsfehler oder Abhängigkeitsfehler.|  
|validation_failures|**BIGINT**|Die Häufigkeit, mit der eine Transaktion aufgrund eines Überprüfungsfehlers abgebrochen wurde.|  
|dependencies_taken|**BIGINT**|Nur interne Verwendung.|  
|dependencies_failed|**BIGINT**|Die Häufigkeit, mit der eine Transaktion aufgrund des Abbruchs einer anderen Transaktion, von der diese abhängig war, abgebrochen wurde.|  
|savepoint_create|**BIGINT**|Die Anzahl der erstellten Sicherungspunkte. Für jeden atomaren Block wird ein neuer Sicherungspunkt erstellt.|  
|savepoint_rollbacks|**BIGINT**|Die Anzahl der Rollbacks zu einem vorherigen Sicherungspunkt.|  
|savepoint_refreshes|**BIGINT**|Nur interne Verwendung.|  
|log_bytes_written|**BIGINT**|Die Gesamtanzahl von Bytes, die in die In-Memory OLTP-Protokolldatensätze geschrieben werden.|  
|log_IO_count|**BIGINT**|Die Gesamtzahl der Transaktionen, die Protokoll-EAs erfordern. Berücksichtigt nur Transaktionen für permanente Tabellen.|  
|phantom_scans_started|**BIGINT**|Nur interne Verwendung.|  
|phantom_scans_retries|**BIGINT**|Nur interne Verwendung.|  
|phantom_rows_touched|**BIGINT**|Nur interne Verwendung.|  
|phantom_rows_expiring|**BIGINT**|Nur interne Verwendung.|  
|phantom_rows_expired|**BIGINT**|Nur interne Verwendung.|  
|phantom_rows_expired_removed|**BIGINT**|Nur interne Verwendung.|  
|scans_started|**BIGINT**|Nur interne Verwendung.|  
|scans_retried|**BIGINT**|Nur interne Verwendung.|  
|rows_returned|**BIGINT**|Nur interne Verwendung.|  
|rows_touched|**BIGINT**|Nur interne Verwendung.|  
|rows_expiring|**BIGINT**|Nur interne Verwendung.|  
|rows_expired|**BIGINT**|Nur interne Verwendung.|  
|rows_expired_removed|**BIGINT**|Nur interne Verwendung.|  
|rows_inserted|**BIGINT**|Nur interne Verwendung.|  
|rows_updated|**BIGINT**|Nur interne Verwendung.|  
|rows_deleted|**BIGINT**|Nur interne Verwendung.|  
|write_conflicts|**BIGINT**|Nur interne Verwendung.|  
|unique_constraint_violations|**BIGINT**|Die Gesamtzahl von UNIQUE-Einschränkungsverletzungen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten für Speicher optimierte Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
