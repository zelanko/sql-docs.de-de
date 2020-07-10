---
title: sys. dm_pdw_errors (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 0ce09955508fa3743be9d8ef600e05f0e36c4467
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197102"
---
# <a name="sysdm_pdw_errors-transact-sql"></a>sys. dm_pdw_errors (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält Informationen zu allen Fehlern, die während der Ausführung einer Anforderung oder Abfrage aufgetreten sind.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|error_id|**nvarchar (36)**|Der Schlüssel für diese Ansicht.<br /><br /> Eindeutige numerische ID, die dem Fehler zugeordnet ist.|Eindeutig für alle Abfrage Fehler im System.|  
|source|**nvarchar (64)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|Typ|**nvarchar(4000)**|Fehlertyp, der aufgetreten ist.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|create_time|**datetime**|Der Zeitpunkt, zu dem der Fehler aufgetreten ist.|Kleiner oder gleich der aktuellen Uhrzeit.|  
|pwd_node_id|**int**|Der Bezeichner des beteiligten Knotens (sofern vorhanden). Weitere Informationen zu Knoten-IDs finden Sie unter [sys. dm_pdw_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).||  
|session_id|**nvarchar(32)**|Der Bezeichner der beteiligten Sitzung (sofern vorhanden). Weitere Informationen zu Sitzungs-IDs finden Sie unter [sys. dm_pdw_exec_sessions &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|request_id|**nvarchar(32)**|Der Bezeichner der beteiligten Anforderung, falls vorhanden. Weitere Informationen zu Anforderungs-IDs finden Sie unter [sys. dm_pdw_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).||  
|spid|**int**|SPID der beteiligten SQL Server Sitzung (sofern vorhanden).||  
|thread_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Details|**nvarchar(4000)**|Enthält die vollständige Fehlertext Beschreibung.||  
  
 Informationen über die maximale Anzahl von Zeilen, die in dieser Sicht beibehalten werden, finden Sie im Abschnitt "Metadaten" im Thema [Kapazitäts Limits](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
