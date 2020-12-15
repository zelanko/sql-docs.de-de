---
description: sys.database_event_session_events (Azure SQL-Datenbank)
title: sys.database_event_session_events (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: f4c9eb0a-173c-4c66-8dd8-6f7176b2657f
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 99c8cf898c8e7ee719af0a88b7c2ea80a7e1ec83
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97458944"
---
# <a name="sysdatabase_event_session_events-azure-sql-database"></a>sys.database_event_session_events (Azure SQL-Datenbank)
[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  Gibt eine Zeile für jedes Ereignis in einer Ereignissitzung zurück.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und spätere Versionen.|  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Die ID der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|event_id|**int**|Die ID des Ereignisses. Diese ID ist innerhalb eines Ereignissitzungsobjekts eindeutig. Lässt keine NULL-Werte zu.|  
|name|**sysname**|Der Name des Ereignisses. Lässt keine NULL-Werte zu.|  
|Paket|**sysname**|Der Name des Pakets, welches das Ereignis enthält. Lässt keine NULL-Werte zu.|  
|module|**sysname**|Der Name des Moduls, welches das Ereignis enthält. Lässt keine NULL-Werte zu.|  
|predicate|**nvarchar (3000)**|Der Prädikatausdruck, der auf das Ereignis angewendet wird. Lässt NULL-Werte zu.|  
|predicate_xml|**nvarchar (3000)**|Der XML-Prädikatausdruck, der auf das Ereignis angewendet wird. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung auf dem Server.  
  
## <a name="remarks"></a>Hinweise  
 Diese Sicht hat die folgende Kardinalität der Beziehungen.  
  
| Von | Beschreibung | Beziehung |
| ---- | -- | ------------ |
|sys.database_event_session_events sys.database_event_session_events.event_session_id|sys.database_event_sessions sys.database_event_sessions.event_session_id|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
