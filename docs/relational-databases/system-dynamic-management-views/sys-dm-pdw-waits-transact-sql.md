---
title: Sys. dm_pdw_waits (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5130e498-1c77-4ae3-a80b-9aae396494e9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 61824058d90b7a922f6bd2d288a85b4923c0975e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56042871"
---
# <a name="sysdmpdwwaits-transact-sql"></a>sys.dm_pdw_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen für alle Zustände, die während der Ausführung einer Anforderung zu warten oder Abfrage, einschließlich der Sperren und wartet auf übertragungswarteschlangen und So weiter.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Eindeutige numerische Id, die den Wartezustand zugeordnet.<br /><br /> Der Schlüssel für diese Sicht.|Für alle Wartevorgänge, die im System eindeutig.|  
|session_id|**nvarchar(32)**|Die ID der Sitzung auf der der Wartezustand aufgetreten ist.|Finden Sie unter Sitzungs-ID in [dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Typ|**nvarchar(255)**|Der Typ des Wartevorgangs, den dieser Eintrag darstellt.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_type|**nvarchar(255)**|Der Typ des Objekts, das den Wartevorgang betroffen ist.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_name|**nvarchar(386)**|Name oder die GUID des angegebenen Objekts, das von den Wartevorgang betroffen war.||  
|request_id|**nvarchar(32)**|Die ID der Anforderung auf der der Wartezustand aufgetreten ist.|Finden Sie im Anforderungs-ID [dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|request_time|**datetime**|Der Zeitpunkt, an dem der Wartezustand angefordert wurde.||  
|acquire_time|**datetime**|Der Zeitpunkt, an dem die Sperre oder die Ressource abgerufen wurde.||  
|state|**nvarchar(50)**|Status des den Wartezustand.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Die Priorität des Elements warten.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
  
