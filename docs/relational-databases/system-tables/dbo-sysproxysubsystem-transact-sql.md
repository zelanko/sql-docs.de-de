---
description: dbo.sysproxysubsystem (Transact-SQL)
title: dbo.sysproxysubsystem (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8f11103d163fab6209ef8ae65b48aae83ef9ee1a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88373786"
---
# <a name="dbosysproxysubsystem-transact-sql"></a>dbo.sysproxysubsystem (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeichnet auf, welches Subsystem des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents von den einzelnen Proxykonten verwendet wird. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Die ID des Subsystems. Dieser Wert entspricht der **subsystem_id** -Spalte in der **syssubsystems** -Tabelle.|  
|**proxy_id**|**int**|ID des Proxykontos. Dieser Wert entspricht der **proxy_id** -Spalte in der **sysproxies** -Tabelle.|  
  
## <a name="remarks"></a>Bemerkungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können auf diese Tabelle zugreifen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo.sysSubsysteme &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)   
 [dbo.sysProxys &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
