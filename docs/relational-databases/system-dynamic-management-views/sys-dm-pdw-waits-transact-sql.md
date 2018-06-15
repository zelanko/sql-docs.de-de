---
title: Sys.dm_pdw_waits (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5130e498-1c77-4ae3-a80b-9aae396494e9
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1e6f94590f63366e8483ac6bfcb493327f38f714
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
ms.locfileid: "34466546"
---
# <a name="sysdmpdwwaits-transact-sql"></a>Sys.dm_pdw_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen warten Zustände, die bei der Ausführung einer Anforderung oder Abfrage, einschließlich der Sperren, wartet auf übertragungswarteschlangen und So weiter.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Eindeutige numerische Id, die den Wartezustand zugeordnet.<br /><br /> Der Schlüssel für diese Ansicht.|Für alle Wartezeiten im System eindeutig.|  
|session_id|**nvarchar(32)**|ID der Sitzung auf der der Wartezustand aufgetreten ist.|Finden Sie unter Session_id in [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Typ|**nvarchar(255)**|Der Typ des Wartevorgangs, diesen Eintrag darstellt.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_type|**nvarchar(255)**|Typ des Objekts, das den Wartevorgang betroffen ist.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_name|**nvarchar(386)**|Der Name oder die GUID des angegebenen Objekts, das den Wartevorgang betroffen war.||  
|request_id|**nvarchar(32)**|Die ID der Anforderung auf der der Wartezustand aufgetreten ist.|Finden Sie unter Request_id in [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|request_time|**datetime**|Der Zeitpunkt, an dem die Wartestatus angefordert wurde.||  
|acquire_time|**datetime**|Der Zeitpunkt, an dem die Sperre oder eine Ressource eingerichtet wurde.||  
|state|**nvarchar(50)**|Status des den Wartezustand.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Die Priorität des Elements warten.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
  
