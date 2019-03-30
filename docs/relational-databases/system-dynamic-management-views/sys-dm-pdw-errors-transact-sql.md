---
title: Sys.dm_pdw_errors (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 944eac31-5691-432b-b9f5-f1e11c05191f
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 57b6bd92ded85345dc1b716df2fa395df17fff02
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58657124"
---
# <a name="sysdmpdwerrors-transact-sql"></a>sys.dm_pdw_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen über alle Fehler, die während der Ausführung einer Anforderung oder die Abfrage.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|error_id|**nvarchar(36)**|Der Schlüssel für diese Sicht.<br /><br /> Eindeutige numerische Id des Fehlers.|Für alle Abfragefehler im System eindeutig.|  
|Quelle|**nvarchar(64)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|Typ|**nvarchar(4000)**|Fehlertyp, der aufgetreten ist.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|create_time|**datetime**|Zeitpunkt, an dem der Fehler aufgetreten ist.|Kleiner oder gleich der aktuellen Zeit.|  
|pwd_node_id|**int**|Der Bezeichner des jeweiligen Knotens erfolgt, sofern vorhanden. Weitere Informationen zu Knoten-Ids, finden Sie unter [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).||  
|session_id|**nvarchar(32)**|Der Bezeichner der Sitzung beteiligt sind, sofern vorhanden. Weitere Informationen auf der Sitzungs-Ids finden Sie unter [dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|request_id|**nvarchar(32)**|Der Bezeichner der Anforderung beteiligt sind, sofern vorhanden. Weitere Informationen zu Anforderungs-Ids, finden Sie unter [dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).||  
|spid|**int**|Serverprozess-ID der SQL Server-Sitzung beteiligt sind, sofern vorhanden.||  
|thread_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Details|**nvarchar(4000)**|Enthält die Beschreibung des vollständigen Text.||  
  
 Informationen, die maximale Anzahl Zeilen, die von dieser Sicht beibehalten können, finden Sie im Abschnitt "Metadaten" in der [Kapazitätsgrenzen](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) Thema.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
