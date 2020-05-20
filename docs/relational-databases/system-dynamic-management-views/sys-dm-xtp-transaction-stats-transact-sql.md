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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3e272d66fef1a6426e13cc6ab8ea72d3912003d3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829012"
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
|dependencies_taken|**bigint**|Nur zur internen Verwendung.|  
|dependencies_failed|**bigint**|Die Häufigkeit, mit der eine Transaktion aufgrund des Abbruchs einer anderen Transaktion, von der diese abhängig war, abgebrochen wurde.|  
|savepoint_create|**bigint**|Die Anzahl der erstellten Sicherungspunkte. Für jeden atomaren Block wird ein neuer Sicherungspunkt erstellt.|  
|savepoint_rollbacks|**bigint**|Die Anzahl der Rollbacks zu einem vorherigen Sicherungspunkt.|  
|savepoint_refreshes|**bigint**|Nur zur internen Verwendung.|  
|log_bytes_written|**bigint**|Die Gesamtanzahl von Bytes, die in die In-Memory OLTP-Protokolldatensätze geschrieben werden.|  
|log_IO_count|**bigint**|Die Gesamtzahl der Transaktionen, die Protokoll-EAs erfordern. Berücksichtigt nur Transaktionen für permanente Tabellen.|  
|phantom_scans_started|**bigint**|Nur zur internen Verwendung.|  
|phantom_scans_retries|**bigint**|Nur zur internen Verwendung.|  
|phantom_rows_touched|**bigint**|Nur zur internen Verwendung.|  
|phantom_rows_expiring|**bigint**|Nur zur internen Verwendung.|  
|phantom_rows_expired|**bigint**|Nur zur internen Verwendung.|  
|phantom_rows_expired_removed|**bigint**|Nur zur internen Verwendung.|  
|scans_started|**bigint**|Nur zur internen Verwendung.|  
|scans_retried|**bigint**|Nur zur internen Verwendung.|  
|rows_returned|**bigint**|Nur zur internen Verwendung.|  
|rows_touched|**bigint**|Nur zur internen Verwendung.|  
|rows_expiring|**bigint**|Nur zur internen Verwendung.|  
|rows_expired|**bigint**|Nur zur internen Verwendung.|  
|rows_expired_removed|**bigint**|Nur zur internen Verwendung.|  
|rows_inserted|**bigint**|Nur zur internen Verwendung.|  
|rows_updated|**bigint**|Nur zur internen Verwendung.|  
|rows_deleted|**bigint**|Nur zur internen Verwendung.|  
|write_conflicts|**bigint**|Nur zur internen Verwendung.|  
|unique_constraint_violations|**bigint**|Die Gesamtzahl von UNIQUE-Einschränkungsverletzungen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten für speicheroptimierte Tabellen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
