---
title: Sys.pdw_loader_backup_runs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2b72034c-6a11-46b9-a76c-7a88b2bea360
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 067a39c807b546bc8364bab05d0423f86407a625
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014510"
---
# <a name="syspdwloaderbackupruns-transact-sql"></a>sys.pdw_loader_backup_runs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu laufenden und abgeschlossenen sicherungs- und Wiederherstellungsvorgänge in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], und Informationen zu laufenden und abgeschlossenen Sicherung, Wiederherstellung und Ladevorgänge in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Die Informationen persistieren über Systemneustarts.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Eindeutiger Bezeichner für eine bestimmte Sicherung, Wiederherstellung oder Auslastungstests.<br /><br /> Der Schlüssel für diese Sicht.||  
|NAME|**nvarchar(255)**|NULL für den Auslastungstest. Optionaler Name für die Sicherung oder Wiederherstellung.||  
|submit_time|**datetime**|Zeitpunkt, der die Anforderung gesendet wurde.||  
|start_time|**datetime**|Zeit, zu der der Vorgang gestartet wurde.||  
|end_time|**datetime**|Zeitpunkt der Vorgang abgeschlossen, fehlgeschlagen oder wurde abgebrochen.||  
|total_elapsed_time|**int**|Insgesamt verstrichene Zeit zwischen Start_time und aktuelle Uhrzeit oder zwischen Start_time "und" End_time nach abgeschlossenen, abgebrochene oder fehlgeschlagene Ausführungen.|Überschreitet Total_elapsed_time den maximalen Wert für eine ganze Zahl (rund 24,8 Tage in Millisekunden), wird es Materialisierung Fehler aufgrund einer zu einem Überlauf führen.<br /><br /> Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
|operation_type|**nvarchar(16)**|Der Load-Typ.|"BACKUP", "LADEN", "RESTORE"|  
|mode|**nvarchar(16)**|Der Modus, innerhalb des Typs ausgeführt werden soll.|Für Operation_type = **Sicherung**<br />**DIFFERENZIELL**<br />**FULL**<br /><br /> Für Operation_type = **laden**<br />**ANFÜGEN**<br />**ERNEUT LADEN**<br />**UPSERT**<br /><br /> Für Operation_type = **wiederherstellen**<br />**DATABASE**<br />**HEADER_ONLY**|  
|database_name|**nvarchar(255)**|Name der Datenbank, die im Rahmen dieser Vorgang ist||  
|table_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Principal_id|**int**|ID des Benutzers, der den Vorgang anfordert.||  
|session_id|**nvarchar(32)**|Die ID der Sitzung, den Vorgang.|Finden Sie unter Sitzungs-ID in [dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|request_id|**nvarchar(32)**|Die ID der Anforderung den Vorgang. Für das Laden ist dies der aktuellen oder letzten Anforderung, die diese Last zugeordnet...|Finden Sie im Anforderungs-ID [dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|status|**nvarchar(16)**|Status der Ausführung.|'CANCELLED','COMPLETED','FAILED','QUEUED','RUNNING'|  
|Wird ausgeführt|**int**|Prozentsatz der Fertigstellung.|0 bis 100|  
|Befehl|**nvarchar(4000)**|Vollständiger Text des Befehls durch den Benutzer gesendet.|Wird bei mehr als 4000 Zeichen (Zählung von Leerzeichen) abgeschnitten.|  
|rows_processed|**bigint**|Anzahl der Zeilen, die als Teil dieses Vorgangs verarbeitet.||  
|rows_rejected|**bigint**|Anzahl der Zeilen, die als Teil des Vorgangs abgelehnt.||  
|rows_inserted|**bigint**|Anzahl der Zeilen, die in die Tabellen der Datenbank eingefügt wird, im Rahmen dieses Vorgangs.||  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
