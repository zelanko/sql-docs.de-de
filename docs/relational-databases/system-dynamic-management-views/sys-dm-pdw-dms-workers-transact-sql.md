---
title: sys. dm_pdw_dms_workers (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6e5f295637db0e138caf324e3126707b9e0ea774
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899504"
---
# <a name="sysdm_pdw_dms_workers-transact-sql"></a>sys. dm_pdw_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen Workern, die DMS-Schritte abschließen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar (32)**|Abfrage, zu der dieser DMS-Worker gehört.<br /><br /> request_id, step_index und dms_step_index bilden den Schlüssel für diese Ansicht.|Weitere Informationen finden Sie unter request_id in [sys. dm_pdw_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Abfrage Schritt, zu dem dieser DMS-Worker gehört.<br /><br /> request_id, step_index und dms_step_index bilden den Schlüssel für diese Ansicht.|Weitere Informationen finden Sie unter step_index in [sys. dm_pdw_request_steps &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Schritt in den DMS-Plan, den dieser Worker ausgeführt wird.<br /><br /> request_id, step_index und dms_step_index bilden den Schlüssel für diese Ansicht.||  
|pdw_node_id|**int**|Knoten, auf dem der Worker ausgeführt wird.|Weitere Informationen finden Sie unter node_id in [sys. dm_pdw_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**Wartenden**|Die Verteilung, auf der der Worker ausgeführt wird (sofern vorhanden).|Weitere Informationen finden Sie unter distribution_id in [sys. pdw_distributions &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md).|  
|type|**nvarchar (32)**|Der Typ des DMS-Arbeitsthreads, den dieser Eintrag darstellt.|' DIRECT_CONVERTER ', ' DIRECT_READER ', ' FILE_READER ', ' HASH_CONVERTER ', ' HASH_READER ', ' ROUNDROBIN_CONVERTER ', ' EXPORT_READER ', ' EXTERNAL_READER ', ' EXTERNAL_WRITER ', ' PARALLEL_COPY_READER ', ' REJECT_WRITER ', ' Writer '|  
|status|**nvarchar (32)**|Der Status des DMS-Workers.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**BIGINT**|Lese-oder Schreibdurchsatz in der letzten Sekunde.|Größer oder gleich 0 (null). NULL, wenn die Abfrage abgebrochen wurde oder fehlgeschlagen ist, bevor der Worker ausgeführt werden konnte.|  
|bytes_processed|**BIGINT**|Gesamtanzahl der Bytes, die von diesem Worker verarbeitet wurden.|Größer oder gleich 0 (null). NULL, wenn die Abfrage abgebrochen wurde oder fehlgeschlagen ist, bevor der Worker ausgeführt werden konnte.|  
|rows_processed|**BIGINT**|Anzahl der für diesen Worker gelesenen oder geschriebenen Zeilen.|Größer oder gleich 0 (null). NULL, wenn die Abfrage abgebrochen wurde oder fehlgeschlagen ist, bevor der Worker ausgeführt werden konnte.|  
|start_time|**datetime**|Der Zeitpunkt, zu dem die Ausführung dieses Workers gestartet wurde.|Die Startzeit ist größer als oder gleich der Startzeit des Abfrage Schritts, zu dem dieser Worker gehört. Weitere Informationen finden Sie unter [sys. dm_pdw_request_steps &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Der Zeitpunkt, zu dem die Ausführung beendet wurde, fehlgeschlagen ist oder abgebrochen wurde.|NULL für laufende oder in der Warteschlange eingereihte Worker. Andernfalls größer als start_time.|  
|total_elapsed_time|**int**|Gesamtzeit für die Ausführung in Millisekunden.|Größer oder gleich 0 (null).<br /><br /> Gesamtzeit seit dem Start oder Neustart des Systems. Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl (24,8 Tage in Millisekunden) überschreitet, führt dies zu einem Materialisierungs Fehler aufgrund eines Überlaufs.<br /><br /> Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
|cpu_time|**BIGINT**|Die von diesem Worker verbrauchte CPU-Zeit in Millisekunden.|Größer oder gleich 0 (null).|  
|query_time|**int**|Der Zeitraum, nach dem SQL mit der Rückgabe von Zeilen an den Thread beginnt (in Millisekunden).|Größer oder gleich 0 (null).|  
|buffers_available|**int**|Anzahl der nicht verwendeten Puffer.| NULL, wenn die Abfrage abgebrochen wurde oder fehlgeschlagen ist, bevor der Worker ausgeführt werden konnte.|  
|sql_spid|**int**|Sitzungs-ID für die SQL Server-Instanz, die die Arbeit für diesen DMS-Worker ausführt.||  
|dms_cpid|**int**|Prozess-ID des aktuellen Threads, der ausgeführt wird.||  
|error_id|**nvarchar (36)**|Eindeutiger Bezeichner des Fehlers, der bei der Ausführung dieses Workers aufgetreten ist, sofern vorhanden.|Weitere Informationen finden Sie unter error_id in [sys. dm_pdw_request_steps &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|source_info|**nvarchar(4000)**|Für einen Reader die Angabe der Quell Tabellen und-Spalten.||  
|destination_info|**nvarchar(4000)**|Für einen Writer die Angabe der Ziel Tabellen.||  
  
 Informationen über die maximale Anzahl von Zeilen, die in dieser Sicht beibehalten werden, finden Sie im Abschnitt "Metadaten" im Thema [Kapazitäts Limits](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
