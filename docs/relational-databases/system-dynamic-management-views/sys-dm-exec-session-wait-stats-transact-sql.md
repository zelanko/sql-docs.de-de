---
description: sys. dm_exec_session_wait_stats (Transact-SQL)
title: sys. dm_exec_session_wait_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_session_wait_stats
- sys.dm_exec_session_wait_stats_tsql
- dm_exec_session_wait_stats
- dm_exec_session_wait_stats_tsql
helpviewer_keywords:
- sys.dm_exec_session_wait_stats
ms.assetid: df84842a-71eb-4fda-b448-5953cf9985dc
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6668ab7b975c7325ab4b5d03ca2f30856b2ffbd0
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537003"
---
# <a name="sysdm_exec_session_wait_stats-transact-sql"></a>sys. dm_exec_session_wait_stats (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  Gibt Informationen zu allen warte Vorgängen zurück, die von Threads gefunden wurden, die für jede Sitzung ausgeführt wurden. Mithilfe dieser Ansicht können Sie Leistungsprobleme bei der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sitzung und auch bei bestimmten Abfragen und Batches diagnostizieren.  Diese Sicht gibt eine Sitzung mit denselben Informationen zurück, die für [sys. dm_os_wait_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) aggregiert werden, aber auch die **session_id** Nummer enthält.  
  
**Gilt für:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|Die ID der Sitzung.|  
|wait_type|**nvarchar(60)**|Der Name des Wartetyps. Weitere Informationen finden Sie unter [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|  
|waiting_tasks_count|**bigint**|Anzahl von Wartevorgängen für diesen Wartetyp. Dieser Leistungsindikator wird beim Starten eines Wartevorgangs inkrementiert.|  
|wait_time_ms|**bigint**|Gesamtwartezeit für diesen Wartetyp (in Millisekunden). Diese Zeit beinhaltet signal_wait_time_ms.|  
|max_wait_time_ms|**bigint**|Maximale Wartezeit für diesen Wartetyp.|  
|signal_wait_time_ms|**bigint**|Differenz zwischen dem Zeitpunkt der Signalisierung des wartenden Threads und dem Beginn der Ausführung.|  
  
## <a name="remarks"></a>Hinweise  
 Diese DMV setzt die Informationen für eine Sitzung zurück, wenn die Sitzung geöffnet wird, oder wenn die Sitzung zurückgesetzt wird (bei Verbindungspooling).  
  
 Weitere Informationen zu den warte Typen finden Sie unter [sys. dm_os_wait_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Wenn der Benutzer über die **View Server State** -Berechtigung auf dem Server verfügt, werden dem Benutzer alle ausgeführten Sitzungen in der Instanz von angezeigt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . andernfalls wird dem Benutzer nur die aktuelle Sitzung angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server dynamischen Verwaltungs Sichten im Zusammenhang mit dem Betriebs System &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
 
