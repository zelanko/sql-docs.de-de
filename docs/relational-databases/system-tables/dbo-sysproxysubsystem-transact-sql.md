---
title: dbo. sysproxysubsystem (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxysubsystem_TSQL
- dbo.sysproxysubsystem
- sysproxysubsystem_TSQL
- sysproxysubsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxysubsystem system table
ms.assetid: 6d7713f5-1253-4a19-b1fb-635c377c95c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: f3a140a4cf1c82deda3b9d6a15b419b33b411974
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097018"
---
# <a name="dbosysproxysubsystem-transact-sql"></a>dbo.sysproxysubsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeichnet auf, welches Subsystem des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents von den einzelnen Proxykonten verwendet wird. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Die ID des Subsystems. Dieser Wert entspricht der **subsystem_id** -Spalte in der **syssubsystems** -Tabelle.|  
|**proxy_id**|**int**|ID des Proxykontos. Dieser Wert entspricht der **proxy_id** -Spalte in der **sysproxies** -Tabelle.|  
  
## <a name="remarks"></a>Bemerkungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können auf diese Tabelle zugreifen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo. syssubsystems &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)   
 [dbo. sysproxies &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
