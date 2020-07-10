---
title: sys. dm_pdw_dms_external_work (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f87d950f4fe876e6b04e1df1f529d22126058113
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197125"
---
# <a name="sysdm_pdw_dms_external_work-transact-sql"></a>sys. dm_pdw_dms_external_work (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Systemsicht, die Informationen zu allen DMS-Schritten (Data Movement Service) für externe Vorgänge enthält.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Die Abfrage, die diesen DMS-Worker verwendet.<br /><br /> request_id, step_index und dms_step_index bilden den Schlüssel für diese Ansicht.|Identisch mit request_id in [sys. dm_pdw_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Abfrage Schritt, der diesen DMS-Worker aufruft.<br /><br /> request_id, step_index und dms_step_index bilden den Schlüssel für diese Ansicht.|Identisch mit step_index in [sys. dm_pdw_request_steps &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Aktueller Schritt im DMS-Plan.<br /><br /> request_id, step_index und dms_step_index bilden den Schlüssel für diese Ansicht.|Identisch mit dms___step_index in [sys. dm_pdw_dms_workers &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md).|  
|pdw_node_id|**int**|Knoten, auf dem der DMS-Worker ausgeführt wird.|Identisch mit node_id in [sys. dm_pdw_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|Typ|**nvarchar(60)**|Der Typ des externen Vorgangs, der von diesem Knoten ausgeführt wird.<br /><br /> Beim Aufteilen von Dateien handelt es sich um einen Vorgang in einer externen Hadoop-Datei, der in mehrere kleinere Fälle aufgeteilt wurde.|' Datei Teilung '|  
|work_id|**int**|Die ID der Datei Aufteilung.|Größer oder gleich 0 (null).<br /><br /> Eindeutig pro Computeknoten.|  
|input_name|**nvarchar(60)**|Der Zeichen folgen Name für die gelesene Eingabe.|Bei einer Hadoop-Datei ist dies der Hadoop-Dateiname.|  
|read_location|**bigint**|Offset des Lese Speicher Orts.||  
|estimated_bytes_processed|**bigint**|Anzahl von Bytes, die von diesem Worker verarbeitet werden.|Größer oder gleich 0 (null).|  
|length|**bigint**|Anzahl der Bytes in der Datei Aufteilung.<br /><br /> Für Hadoop ist dies die Größe des HDFS-Blocks.|Benutzer definiert. Der Standardwert ist 64 MB.|  
|status|**nvarchar(32)**|Der Zustand des Workers.|Ausstehend, verarbeitet, abgeschlossen, fehlgeschlagen, abgebrochen|  
|start_time|**datetime**|Der Zeitpunkt, zu dem die Ausführung dieses Workers gestartet wurde.|Die Startzeit ist größer als oder gleich der Startzeit des Abfrage Schritts, zu dem dieser Worker gehört. Weitere Informationen finden Sie unter [sys. dm_pdw_request_steps &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Der Zeitpunkt, zu dem die Ausführung beendet wurde, fehlgeschlagen ist oder abgebrochen wurde.|NULL für laufende oder in der Warteschlange eingereihte Worker. Andernfalls größer als start_time.|  
|total_elapsed_time|**int**|Gesamtzeit für die Ausführung in Millisekunden.|Größer oder gleich 0 (null).<br /><br /> Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, ist total_elapsed_time weiterhin der Höchstwert. Mit dieser Bedingung wird die Warnung "der Höchstwert wurde überschritten" generiert.<br /><br /> Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
  
 Informationen über die maximale Anzahl von Zeilen, die in dieser Sicht beibehalten werden, finden Sie im Abschnitt "Metadaten" im Thema [Kapazitäts Limits](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .
  
## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
