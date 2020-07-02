---
title: dbo.sysSubsysteme (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syssubsystems
- syssubsystems
- syssubsystems_TSQL
- dbo.syssubsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syssubsystems system table
ms.assetid: 114b3d55-1ad6-4777-b868-8ef0c86ba596
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4a4374f0ffddb380f56e5c51e26a59e253e7585b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750271"
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo.syssubsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Enthält Informationen zu allen verfügbaren Proxysubsystemen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents. Die **syssubsystems** -Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Die ID des Subsystems.|  
|**System**|**nvarchar(40)**|Der Name des Subsystems.|  
|**description_id**|**int**|Meldungs-ID der Zeile in der **sys.messages** -Katalogsicht, die die Beschreibung des Subsystems enthält.|  
|**subsystem_dll**|**nvarchar(255)**|Speicherort der Subsystem-DLL.|  
|**agent_exe**|**nvarchar(255)**|Vollständiger Pfad zur ausführbaren Datei, die das Subsystem verwendet.|  
|**start_entry_point**|**nvarchar(30)**|Funktion, die beim Initialisieren des Subsystems aufgerufen wird.|  
|**event_entry_point**|**nvarchar(30)**|Funktion, die beim Ausführen eines Subsystems aufgerufen wird.|  
|**stop_entry_point**|**nvarchar(30)**|Funktion, die beim Beenden der Ausführung eines Subsystems aufgerufen wird.|  
|**max_worker_threads**|**int**|Maximale Anzahl paralleler Schritte für ein bestimmtes Subsystem.|  
  
## <a name="remarks"></a>Hinweise  
 Nur Mitglieder der festen Serverrolle **sysadmin** können auf diese Tabelle zugreifen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo.sysproxysubsystem &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.sysProxys &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
