---
description: sys.server_event_session_fields (Transact-SQL)
title: sys. server_event_session_fields (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_event_session_fields
- server_event_session_fields_TSQL
- sys.server_event_session_fields
- sys.server_event_session_fields_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_session_fields catalog view
- xe
ms.assetid: 7109f9fb-8a1f-432c-92d1-6f8af3e96af1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 18849b0e5a3911022e90a6f9a768fbbb7e921729
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551397"
---
# <a name="sysserver_event_session_fields-transact-sql"></a>sys.server_event_session_fields (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeile für jede anpassbare Spalte zurück, die explizit für Ereignisse und Ziele festgelegt wurde.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Die ID der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|object_id|**int**|Die ID des dem Objekt zugeordneten Felds Lässt keine NULL-Werte zu.|  
|name|**sysname**|Der Name des Felds. Lässt keine NULL-Werte zu.|  
|value|**sql_variant**|Der Wert des Felds. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="remarks"></a>Hinweise  
 Diese Sicht hat die folgende Kardinalität der Beziehungen.  
  
| From | To | Beziehung |
| ---- | -- | ------------ |
|sys.server_event_session_actions.event_session_id|sys. server_event_sessions. event_session_id|n:1|  
|sys.server_event_session_actions.event_id<br /><br /> sys.server_event_session_actions.object_id<br /><br /> sys.server_event_session_actions.event_session_id|sys.server_event_session_events.event_session_id<br /><br /> sys.server_event_session_events.event_id|n:1|  
|sys.server_event_session_actions.event_session_id<br /><br /> sys.server_event_session_actions.object_id|sys.server_event_session_targets.event_session_id<br /><br /> sys.server_event_session_targets.target_id|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Katalog Sichten für erweiterte Ereignisse &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
