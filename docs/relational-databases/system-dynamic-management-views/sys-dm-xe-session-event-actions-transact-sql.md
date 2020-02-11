---
title: sys. dm_xe_session_event_actions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_session_event_actions_TSQL
- sys.dm_xe_session_event_actions_TSQL
- dm_xe_session_event_actions
- sys.dm_xe_session_event_actions
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_xe_session_event_actions dynamic management view
ms.assetid: 0c22a546-683e-4c84-ab97-1e9e95304b03
author: stevestein
ms.author: sstein
ms.openlocfilehash: c10ef9265ef659985d667632e864e55f58ef4911
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090253"
---
# <a name="sysdm_xe_session_event_actions-transact-sql"></a>sys.dm_xe_session_event_actions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu Ereignissitzungsaktionen zurück. Aktionen werden ausgeführt, wenn Ereignisse ausgelöst werden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Die Speicheradresse der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|action_name|**nvarchar(256)**|Der Name der Aktion Lässt keine NULL-Werte zu.|  
|action_package_guid|**uniqueidentifier**|Die GUID für das Paket, das die Aktion enthält. Lässt keine NULL-Werte zu.|  
|event_name|**nvarchar(256)**|Der Name des Ereignisses, an das die Aktion gebunden ist Lässt keine NULL-Werte zu.|  
|event_package_guid|**uniqueidentifier**|Die GUID für das Paket, das das Ereignis enthält Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|To|Beziehung|  
|----------|--------|------------------|  
|sys.dm_xe_session_event_actions.event_session_address|sys.dm_xe_sessions.address|n:1|  
|sys. dm_xe_session_event_actions. action_name,<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name,<br /><br /> sys.dm_xe_session_events.event_package_guid|n:1|  
|sys. dm_xe_session_event_actions. event_name,<br /><br /> sys.dm_xe_session_event_actions.event_package_guid|sys.dm_xe_objects.name,<br /><br /> sys.dm_xe_objects.package_guid|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

