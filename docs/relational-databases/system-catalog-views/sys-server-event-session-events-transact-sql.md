---
title: Sys. server_event_session_events (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_event_session_events
- server_event_session_events_TSQL
- sys.server_event_session_events
- sys.server_event_session_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_session_events catalog view
- xe
ms.assetid: 75986e91-1fc7-4f14-98ac-4e90154a74db
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ac3c2bd13b5f89ea8d87336e579e196e3754c5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68133228"
---
# <a name="sysservereventsessionevents-transact-sql"></a>sys.server_event_session_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt für jedes Ereignis in einer Ereignissitzung eine Zeile zurück.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Die ID der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|event_id|**int**|Die ID des Ereignisses. Diese ID ist innerhalb eines Ereignissitzungsobjekts eindeutig. Lässt keine NULL-Werte zu.|  
|NAME|**sysname**|Der Name des Ereignisses. Lässt keine NULL-Werte zu.|  
|Paket|**sysname**|Der Name des Pakets, welches das Ereignis enthält. Lässt keine NULL-Werte zu.|  
|module|**sysname**|Der Name des Moduls, welches das Ereignis enthält. Lässt keine NULL-Werte zu.|  
|predicate|**nvarchar(3000)**|Der Prädikatausdruck, der auf das Ereignis angewendet wird. Lässt NULL-Werte zu.|  
|predicate_xml|**nvarchar(3000)**|Der XML-Prädikatausdruck, der auf das Ereignis angewendet wird. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="remarks"></a>Hinweise  
 Diese Sicht hat die folgende Kardinalität der Beziehungen.  
  
||||  
|-|-|-|  
|Von|Beschreibung|Beziehung|  
|sys.server_event_session_events.event_session_id|Sys.server_event_sessions.event_session_id|n:1|  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Katalogsichten für erweiterte Ereignisse &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
