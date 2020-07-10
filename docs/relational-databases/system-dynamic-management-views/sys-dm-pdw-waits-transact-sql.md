---
title: sys. dm_pdw_waits (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6111ce07ecb3de932ff4cb12cf6d7c53d5a1be6d
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197011"
---
# <a name="sysdm_pdw_waits-transact-sql"></a>sys. dm_pdw_waits (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält Informationen zu allen warte Zuständen, die während der Ausführung einer Anforderung oder Abfrage aufgetreten sind, einschließlich Sperren, Warteschlangen für Übertragungs Warteschlangen usw.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Eindeutige numerische ID, die dem Wartezustand zugeordnet ist.<br /><br /> Der Schlüssel für diese Ansicht.|Eindeutig für alle warte Vorgänge im System.|  
|session_id|**nvarchar(32)**|Die ID der Sitzung, für die der Wartezustand aufgetreten ist.|Weitere Informationen finden Sie unter session_id in [sys. dm_pdw_exec_sessions &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Typ|**nvarchar(255)**|Der Typ des warte Vorgangs, den dieser Eintrag darstellt.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_type|**nvarchar(255)**|Der Typ des Objekts, das vom warte Vorgang betroffen ist.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_name|**nvarchar (386)**|Der Name oder die GUID des angegebenen Objekts, das von der Wartezeit betroffen war.||  
|request_id|**nvarchar(32)**|ID der Anforderung, für die der Wartezustand aufgetreten ist.|Weitere Informationen finden Sie unter request_id in [sys. dm_pdw_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|request_time|**datetime**|Der Zeitpunkt, zu dem der Wartezustand angefordert wurde.||  
|acquire_time|**datetime**|Der Zeitpunkt, zu dem die Sperre oder Ressource abgerufen wurde.||  
|state|**nvarchar(50)**|Status des warte Zustands.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Priorität des wartenden Elements.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys. dm_pdw_wait_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
  
