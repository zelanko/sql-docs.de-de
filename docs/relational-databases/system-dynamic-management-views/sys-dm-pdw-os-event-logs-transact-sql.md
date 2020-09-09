---
description: sys. dm_pdw_os_event_logs (Transact-SQL)
title: sys. dm_pdw_os_event_logs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fb4194b866595009b46aea888f600488b6a1cc3b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89530711"
---
# <a name="sysdm_pdw_os_event_logs-transact-sql"></a>sys. dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Enthält Informationen zu den verschiedenen Windows-Ereignisprotokollen auf den verschiedenen Knoten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Der Geräteknoten, von dem dieses Protokoll abgeleitet ist.<br /><br /> pdw_node_id und log_name den Schlüssel für diese Ansicht bilden.||  
|log_name|**nvarchar(255)**|Der Name des Windows-Ereignis Protokolls.<br /><br /> pdw_node_id und log_name den Schlüssel für diese Ansicht bilden.||  
|log_source|**nvarchar(255)**|Quellen Name des Windows-Ereignis Protokolls.||  
|event_id|**int**|ID des Ereignisses. Nicht eindeutig.||  
|event_type|**nvarchar(255)**|Der Typ des Ereignisses, der den Schweregrad identifiziert.|"Information", "Warning", "Error"|  
|event_message|**nvarchar(4000)**|Details zum Ereignis.||  
|generate_time|**datetime**|Zeitpunkt, zu dem das Ereignis erstellt wurde.||  
|write_time|**datetime**|Uhrzeit, zu der das Ereignis tatsächlich in das Protokoll geschrieben wurde.||  
  
 Informationen über die maximale Anzahl von Zeilen, die in dieser Sicht beibehalten werden, finden Sie im Abschnitt "Metadaten" im Thema [Kapazitäts Limits](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) . 
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
