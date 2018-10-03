---
title: Sys.dm_pdw_sys_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ad7311759e2ea38f5b9b375785b7f035d1dcdbfa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821518"
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Bietet eine Reihe von Leistungsindikatoren für die Appliance auf Instanzebene, die Gesamtaktivität auf dem Gerät widerspiegeln.  
  
|Spaltenname|Datentyp|Description|Bereich|  
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
  
  
