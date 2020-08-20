---
description: sys.database_event_session_targets (Azure SQL-Datenbank)
title: sys. database_event_session_targets (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 38d775ee-1fe1-4820-88c6-02b2f875a66b
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: db6c71d95637f2ddbdea6100ec94ff76aaa1f0ae
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646122"
---
# <a name="sysdatabase_event_session_targets-azure-sql-database"></a>sys.database_event_session_targets (Azure SQL-Datenbank)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  Gibt für eine Ereignissitzung eine Zeile für jedes Ereignisziel zurück.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und spätere Versionen.|  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Die ID der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|target_id|**int**|Die ID des Ziels. Die ID ist innerhalb des Ereignissitzungsobjekts eindeutig. Lässt keine NULL-Werte zu.|  
|name|**sysname**|Der Name des Ereignisziels. Lässt keine NULL-Werte zu.|  
|package|**sysname**|Der Name des Ereignispakets, das das Ereignisziel enthält. Lässt keine NULL-Werte zu.|  
|module|**sysname**|Der Name des Moduls, das das Ereignisziel enthält. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung auf dem Server.  
  
## <a name="remarks"></a>Hinweise  
 Diese Sicht hat die folgende Kardinalität der Beziehungen.  
  
|Von|An|Beziehung|  
|-|-|-|  
|sys. database_event_session_targets. event_session_id|sys. database_event_sessions. event_session_id|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
