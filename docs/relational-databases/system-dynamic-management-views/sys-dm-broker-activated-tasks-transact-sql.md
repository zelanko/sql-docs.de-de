---
description: sys.dm_broker_activated_tasks (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3a09275a9b000ab673e187fdb2e1a47d35c1e548
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498382"
---
# <a name="sysdm_broker_activated_tasks-transact-sql"></a>sys.dm_broker_activated_tasks (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
|Von|An|Beziehung|  
|----------|--------|------------------|  
|dm_broker_activated_tasks.spid|dm_exec_sessions.session_id|1:1|  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

