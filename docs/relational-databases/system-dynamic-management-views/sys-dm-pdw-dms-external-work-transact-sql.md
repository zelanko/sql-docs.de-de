---
title: sys.dm_pdw_dms_external_work (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 47345015-f861-451e-97c4-6e1cb81d1922
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d02a1d50e9c7a5f906e78fa6753d594edced341f
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658118"
---
# <a name="sysdmpdwdmsexternalwork-transact-sql"></a>sys.dm_pdw_dms_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Systemsicht, die Informationen über alle Schritte zur Windows-Verwaltungsinstrumentation (Data Movement Service, DMS) für externe Vorgänge enthält.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Abfrage, die der DMS-Worker verwendet wird.<br /><br /> Anforderungs-ID, Step_index und Dms_step_index bilden den Schlüssel für diese Ansicht ein.|Identisch mit der Anforderungs-ID in [dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Schritte der Abfrage, die der DMS-Worker aufruft.<br /><br /> Anforderungs-ID, Step_index und Dms_step_index bilden den Schlüssel für diese Ansicht ein.|Identisch mit Step_index in [dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Aktuellen Schritt in den DMS-Plan.<br /><br /> Anforderungs-ID, Step_index und Dms_step_index bilden den Schlüssel für diese Ansicht ein.|Identisch mit Dms___step_index in [Sys. dm_pdw_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md).|  
|pdw_node_id|**int**|Knoten, der den DMS-Worker ausgeführt wird.|Identisch mit Node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|Typ|**nvarchar(60)**|Typ des externen Vorgang, den diesem Knoten ausgeführt wird.<br /><br /> Teilen der Datei ist ein Vorgang auf einer externen Hadoop-Datei, die in mehrere kleinere fällt aufgeteilt wurde.|"DATEI SPLIT"|  
|work_id|**int**|Teilen der Datei-ID|Größer als oder gleich 0.<br /><br /> Jede Compute-Knoten eindeutig.|  
|input_name|**nvarchar(60)**|Der Zeichenfolgenname für die Eingabe gelesen wird.|Bei einer Hadoop-Datei ist dies der Name des Hadoop-Datei.|  
|read_location|**bigint**|Offset der schreibgeschützten Speicherort.||  
|estimated_bytes_processed|**bigint**|Anzahl der Bytes, die von diesem Arbeitsthread verarbeitet werden.|Größer als oder gleich 0.|  
|length|**bigint**|Teilen Sie die Anzahl der Bytes in der Datei.<br /><br /> Für Hadoop ist dies die Größe des HDFS-Blocks.|Vom Benutzer definiert. Der Standardwert ist 64 MB.|  
|status|**nvarchar(32)**|Status des Arbeitsthreads.|Ausstehende, Verarbeitung, ausgeführt, Fehler, wurde abgebrochen|  
|start_time|**datetime**|Zeitpunkt, an dem Ausführung dieses Arbeitsthreads gestartet wurde.|Größer als oder gleich der Startzeit des abfrageschritts gehört dieser Worker. Finden Sie unter [dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Zeitpunkt, an der Ausführung beendet wurde, Fehler, oder wurde abgebrochen.|NULL für laufende oder in der Warteschlange-Worker. Andernfalls, Start_time größer.|  
|total_elapsed_time|**int**|Gesamtzeit in der Ausführung in Millisekunden.|Größer als oder gleich 0.<br /><br /> Wenn Total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, weiterhin Total_elapsed_time der maximale Wert sein. Diese Bedingung generiert die Warnung "der maximale Wert überschritten wurde."<br /><br /> Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
  
 Informationen, die maximale Anzahl Zeilen, die von dieser Sicht beibehalten können, finden Sie im Abschnitt "Metadaten" in der [Kapazitätsgrenzen](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) Thema.
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
