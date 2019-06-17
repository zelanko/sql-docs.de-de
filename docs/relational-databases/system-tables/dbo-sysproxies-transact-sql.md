---
title: dbo.sysproxies (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxies_TSQL
- sysproxies_TSQL
- dbo.sysproxies
- sysproxies
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxies system table
ms.assetid: a73da875-be22-45fc-b5e2-ea7ebd48e2d6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a37300ad1bf16ac76fbcbd0c6e77870077f7f631
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470599"
---
# <a name="dbosysproxies-transact-sql"></a>dbo.sysproxies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Definiert Attribute eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxykontos. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|ID des Proxykontos.|  
|**name**|**sysname**|Name des Proxykontos.|  
|**credential_id**|**int**|ID der vom Proxykonto verwendeten Anmeldeinformationen.|  
|**enabled**|**tinyint**|Status des Proxykontos:<br /><br /> **0** = Deaktiviert. **1** = Aktiviert.|  
|**description**|**nvarchar(512)**|Beschreibung, die der Benutzer bei Erstellung des Proxykontos eingegeben hat.|  
|**user_sid**|**varbinary(85)**|Microsoft Windows-Sicherheits-ID ( *security_identifier* ) des Benutzers oder der Gruppe, der bzw. die den Proxyanmeldeinformationen zugeordnet ist.|  
|**credential_date_created**|**datetime**|Datum und Uhrzeit des Zeitpunkts, an dem die Anmeldeinformationen erstellt wurden.|  
  
## <a name="remarks"></a>Hinweise  
 Nur Mitglieder der festen Serverrolle **sysadmin** können auf die **sysproxies** -Tabelle zugreifen.  
  
## <a name="see-also"></a>Siehe auch  
 [dbo.sysproxylogin &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)   
 [dbo.sysproxysubsystem &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.syssubsystems &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)  
  
  
