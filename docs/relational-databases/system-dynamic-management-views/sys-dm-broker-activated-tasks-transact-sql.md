---
title: sys. dm_broker_activated_tasks (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_activated_tasks
- sys.dm_broker_activated_tasks_TSQL
- dm_broker_activated_tasks
- dm_broker_activated_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_activated_tasks dynamic management view
ms.assetid: 17e6f87f-8f56-489d-9aed-216afc8ef310
author: stevestein
ms.author: sstein
ms.openlocfilehash: f80ec78e37707058a354a03bb2605a38abdfa803
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68099188"
---
# <a name="sysdm_broker_activated_tasks-transact-sql"></a>sys.dm_broker_activated_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede von Service Broker aktivierte gespeicherte Prozedur zurück.  
 

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**spid**|**int**|ID der Sitzung der aktivierten gespeicherten Prozedur. Lässt NULL-Werte zu.|  
|**database_id**|**smallint**|ID der Datenbank, in der die Warteschlange definiert wird. Lässt NULL-Werte zu.|  
|**queue_id**|**int**|ID des Warteschlangenobjekts, für das die gespeicherte Prozedur aktiviert wurde. Lässt NULL-Werte zu.|  
|**procedure_name**|**nvarchar (650)**|Name der aktivierten gespeicherten Prozedur. Lässt NULL-Werte zu.|  
|**execute_as**|**int**|ID des Benutzers, unter dem die gespeicherte Prozedur ausgeführt wird. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="physical-joins"></a>Physische Joins  
 ![Joins für sys.dm_broker_activated_tasks](../../relational-databases/system-dynamic-management-views/media/join-dm-broker-activated-tasks-1.gif "Joins für sys.dm_broker_activated_tasks")  
  
## <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|To|Beziehung|  
|----------|--------|------------------|  
|dm_broker_activated_tasks.spid|dm_exec_sessions.session_id|1:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker verwandte dynamische Verwaltungs Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

