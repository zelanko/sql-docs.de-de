---
description: sys.database_event_session_actions (Azure SQL-Datenbank)
title: sys. database_event_session_actions (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 32494df1-7ab7-4b88-a858-6b1021d67433
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1ecfcd40d79e3374663259648fa3447db96e6986
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542630"
---
# <a name="sysdatabase_event_session_actions-azure-sql-database"></a>sys.database_event_session_actions (Azure SQL-Datenbank)
[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  Gibt für jede Aktion jedes Ereignisses einer Ereignissitzung eine Zeile zurück.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und spätere Versionen.|  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Die ID der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|event_id|**int**|Die ID des Ereignisses. Diese ID ist innerhalb des Ereignissitzungsobjekts eindeutig. Lässt keine NULL-Werte zu.|  
|name|**sysname**|Der Name der Aktion Lässt NULL-Werte zu.|  
|package|**sysname**|Der Name des Pakets, welches das Ereignis enthält. Lässt NULL-Werte zu.|  
|module|**sysname**|Der Name des Moduls, welches das Ereignis enthält. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung auf dem Server.  
  
## <a name="remarks"></a>Hinweise  
 Diese Sicht hat die folgende Kardinalität der Beziehungen.  
  
| From | To | Beziehung |
| ---- | -- | ------------ |
|sys. database_event_session_actions. event_session_id|sys.sys. database_event_sessions. event_session_id|n:1|  
|sys. database_event_session_actions. event_id<br /><br /> sys. database_event_session_actions. event_session_id|sys. database_event_session_events. event_session_id<br /><br /> sys. database_event_session_events. event_id|n:1|  
  
  
