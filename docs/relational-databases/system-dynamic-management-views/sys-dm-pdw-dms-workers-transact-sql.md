---
title: Sys. dm_pdw_dms_workers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0a284d18-3c46-4ffa-bcc9-689e660ee8b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 756943d49a794781d9422071dd5e233ce4e37806
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027361"
---
# <a name="sysdmpdwdmsworkers-transact-sql"></a>sys.dm_pdw_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen Workern, die DMS-Schritte.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Abfrage, die der DMS-Worker angehört.<br /><br /> Anforderungs-ID, Step_index und Dms_step_index bilden den Schlüssel für diese Ansicht ein.|Finden Sie im Anforderungs-ID [dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Fragen Sie Schritt ab, den der DMS-Worker angehört.<br /><br /> Anforderungs-ID, Step_index und Dms_step_index bilden den Schlüssel für diese Ansicht ein.|Finden Sie unter Step_index in [dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Schritt in den DMS-Plan, den dieser Arbeitsthread ausgeführt wird.<br /><br /> Anforderungs-ID, Step_index und Dms_step_index bilden den Schlüssel für diese Ansicht ein.||  
|pdw_node_id|**int**|Knoten, der die Worker ausgeführt wird.|Finden Sie unter Node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**Int**|Verteilung, die der Arbeitsthread ggf. ausgeführt wird.|Finden Sie unter Distribution_id in [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md).|  
|Typ|**nvarchar(32)**|Der Typ des DMS-Arbeitsthread, den dieser Eintrag darstellt.|'DIRECT_CONVERTER', "DIRECT_READER", "FILE_READER", "HASH_CONVERTER", "HASH_READER", "ROUNDROBIN_CONVERTER", "EXPORT_READER", "EXTERNAL_READER", "EXTERNAL_WRITER", "PARALLEL_COPY_READER", "REJECT_WRITER", "WRITER"|  
|status|**nvarchar(32)**|Status der DMS-Worker.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**bigint**|Durchsatz von Lese- oder Schreibvorgang in der letzten Sekunde.|Größer als oder gleich 0. NULL, wenn die Abfrage wurde abgebrochen oder Fehler, bevor der Arbeitsthread ausgeführt werden konnte.|  
|bytes_processed|**bigint**|Gesamtzahl der Bytes von diesem Arbeitsthread verarbeitet werden.|Größer als oder gleich 0. NULL, wenn die Abfrage wurde abgebrochen oder Fehler, bevor der Arbeitsthread ausgeführt werden konnte.|  
|rows_processed|**bigint**|Anzahl der Zeilen gelesen oder geschrieben werden, für diesen Arbeitsthread.|Größer als oder gleich 0. NULL, wenn die Abfrage wurde abgebrochen oder Fehler, bevor der Arbeitsthread ausgeführt werden konnte.|  
|start_time|**datetime**|Zeitpunkt, an dem Ausführung dieses Arbeitsthreads gestartet wurde.|Größer als oder gleich der Startzeit des abfrageschritts gehört dieser Worker. Finden Sie unter [dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Zeitpunkt, an der Ausführung beendet wurde, Fehler, oder wurde abgebrochen.|NULL für laufende oder in der Warteschlange-Worker. Andernfalls, Start_time größer.|  
|total_elapsed_time|**int**|Gesamtzeit in der Ausführung in Millisekunden.|Größer als oder gleich 0.<br /><br /> Insgesamt verstrichene Zeit seit System starten oder neu starten. Überschreitet Total_elapsed_time den maximalen Wert für eine ganze Zahl (rund 24,8 Tage in Millisekunden), wird es Materialisierung Fehler aufgrund einer zu einem Überlauf führen.<br /><br /> Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
|cpu_time|**bigint**|CPU-Zeit verbraucht, die von diesem Arbeitsthread, in Millisekunden.|Größer als oder gleich 0.|  
|query_time|**int**|Wartezeit für SQL startet wiederkehrender Zeilen für den Thread, in Millisekunden.|Größer als oder gleich 0.|  
|buffers_available|**int**|Anzahl der nicht verwendeten Puffer.| NULL, wenn die Abfrage wurde abgebrochen oder Fehler, bevor der Arbeitsthread ausgeführt werden konnte.|  
|sql_spid|**int**|Sitzungs-Id für die SQL Server-Instanz, die die Arbeit für diesen DMS-Worker ausgeführt.||  
|dms_cpid|**int**|Prozess-ID, der der Thread ausgeführt wird.||  
|error_id|**nvarchar(36)**|Eindeutiger Bezeichner des Fehlers während der Ausführung dieses Arbeitsthreads, sofern vorhanden.|Finden Sie unter Fehler-ID in [dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|source_info|**nvarchar(4000)**|Für ein Leser, die Spezifikation der Quelltabellen und Spalten.||  
|destination_info|**nvarchar(4000)**|Für einen Writer Spezifikation der Zieltabellen.||  
  
 Weitere Informationen zu den maximalen Zeilen, die von dieser Sicht beibehalten, finden Sie unter [System Ansicht Maximalwerte](https://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
