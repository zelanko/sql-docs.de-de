---
title: sys. dm_pdw_os_event_logs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ed27e25a1aa977c8fc78186ae2bc9f96ee0e231e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82819293"
---
# <a name="sysdm_pdw_os_event_logs-transact-sql"></a>sys. dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu den verschiedenen Windows-Ereignisprotokollen auf den verschiedenen Knoten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
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
  
  
