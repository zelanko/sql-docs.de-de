---
title: Sys.dm_pdw_os_event_logs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7365cf89d1f8bb69cefbbb13585a296a78bcd4b8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56039121"
---
# <a name="sysdmpdwoseventlogs-transact-sql"></a>sys.dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu den verschiedenen Windows-Ereignis für die anderen Knoten protokolliert.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Appliance-Knoten, die dieses Protokoll stammt.<br /><br /> Pdw_node_id und Log_name bilden den Schlüssel für diese Ansicht ein.||  
|log_name|**nvarchar(255)**|Der Name der Windows-Ereignisprotokoll.<br /><br /> Pdw_node_id und Log_name bilden den Schlüssel für diese Ansicht ein.||  
|log_source|**nvarchar(255)**|Quellname für Windows-Ereignisprotokoll.||  
|event_id|**int**|Die ID des Ereignisses. Nicht eindeutig.||  
|event_type|**nvarchar(255)**|Der Typ des Ereignisses, Schweregrad identifizieren.|'Information', 'Warning', 'Error'|  
|event_message|**nvarchar(4000)**|Details des Ereignisses.||  
|generate_time|**datetime**|Zeitpunkt, der das Ereignis erstellt wurde.||  
|write_time|**datetime**|Zeitpunkt, der das Ereignis tatsächlich in das Protokoll geschrieben wurde.||  
  
 Informationen, die maximale Anzahl Zeilen, die von dieser Sicht beibehalten können, finden Sie im Abschnitt "maximale Systemwerte anzeigen" in der [Mindest- und Höchstwerte (SQL Server PDW)](https://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9) Thema.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
