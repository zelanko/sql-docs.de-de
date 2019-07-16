---
title: Sys.dm_pdw_sys_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 0bc6c97f4d41023b822f42a6bbe4c5b193d42e45
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088756"
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Bietet eine Reihe von Leistungsindikatoren für die Appliance auf Instanzebene, die Gesamtaktivität auf dem Gerät widerspiegeln.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|Anzahl der Sitzungen, die derzeit im System.|0, um Max_active_sessions (siehe unten).|  
|idle_sessions|**int**|Anzahl der Sitzungen, die derzeit im Leerlauf befindet.||  
|active_requests|**int**|Anzahl aktiver Anforderungen, die derzeit ausgeführt.||  
|queued_requests|**int**|Anzahl der derzeit in der Warteschlange befindlichen Anforderungen.||  
|active_loads|**int**|Die Anzahl der Lasten, die derzeit im System.||  
|queued_loads|**int**|Die Anzahl der in Warteschlange stehenden Ladevorgänge für die Ausführung warten.||  
|active_backups|**int**|Die Anzahl von Sicherungen, die derzeit ausgeführt.||  
|active_restores|**int**|Die Anzahl der Sicherung wiederhergestellt, die derzeit ausgeführt.||  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
