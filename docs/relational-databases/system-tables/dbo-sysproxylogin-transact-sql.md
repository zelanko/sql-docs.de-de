---
title: dbo.sysproxylogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fb62d70c1b0a41edf684a8216205fb43e070eea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984880"
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeichnet auf, welche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldungen den einzelnen Proxykonten des SQL Server-Agents zugeordnet sind. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|ID des Proxykontos des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents. Dieser Wert entspricht der **proxy_id** -Spalte in der **sysproxies** -Tabelle.|  
|**sid**|**varbinary(85)**|Microsoft Windows *security_identifier* für die SQL Server-Anmeldung.|  
|**principal_id**|**int**|ID des Benutzers oder der Gruppe, der bzw. die berechtigt ist, das Proxykonto für einen bestimmten Subsystemschritt zu verwenden.|  
|**flags**|**int**|Anmeldungstyp:<br /><br /> **0** = Windows-Benutzer oder -Gruppe und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung.<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feste Systemrolle<br /><br /> **2** = **msdb** -Datenbankrolle|  
  
## <a name="remarks"></a>Hinweise  
 Nur Mitglieder der festen Serverrolle **sysadmin** können auf diese Tabelle zugreifen.  
  
## <a name="see-also"></a>Siehe auch  
 [dbo.sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
