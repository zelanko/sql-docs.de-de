---
description: sys.database_event_session_fields (Azure SQL-Datenbank)
title: sys. database_event_session_fields (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 9b5c94d6-612c-4e0f-976d-ac6ba55da3ac
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a05d76772d54535f19211098e1e76ad8016a1a28
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88401636"
---
# <a name="sysdatabase_event_session_fields-azure-sql-database"></a>sys.database_event_session_fields (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede anpassbare Spalte zurück, die explizit für Ereignisse und Ziele festgelegt wurde.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und spätere Versionen.|  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Die ID der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|object_id|**int**|Die ID des dem Objekt zugeordneten Felds Lässt keine NULL-Werte zu.|  
|name|**sysname**|Der Name des Felds. Lässt keine NULL-Werte zu.|  
|value|**sql_variant**|Der Wert des Felds. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung auf dem Server.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Sicht hat die folgende Kardinalität der Beziehungen.  
  
| Von | An | Beziehung |
| ---- | -- | ------------ |
|sys. database_event_session_actions. event_session_id|sys. database_event_sessions. event_session_id|n:1|  
|sys. database_event_session_actions. event_id<br /><br /> sys. database_event_session_actions. object_id<br /><br /> sys. database_event_session_actions. event_session_id|sys. database_event_session_events. event_session_id<br /><br /> sys. database_event_session_events. event_id|n:1|  
|sys. database_event_session_actions. event_session_id<br /><br /> sys. database_event_session_actions. object_id|sys. database_event_session_targets. event_session_id<br /><br /> sys. database_event_session_targets. target_id|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
