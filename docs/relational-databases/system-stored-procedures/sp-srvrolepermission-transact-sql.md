---
title: sp_srvrolepermission (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_srvrolepermission_TSQL
- sp_srvrolepermission
dev_langs:
- TSQL
helpviewer_keywords:
- sp_srvrolepermission
ms.assetid: 5709667f-e3e4-48a2-93ec-af5e22a2ac58
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6613c4e94ce8c802e45fe003ac73e51b3f38072b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68032810"
---
# <a name="sp_srvrolepermission-transact-sql"></a>sp_srvrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt die Berechtigungen einer festen Serverrolle an.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_srvrolepermission [ [ @srvrolename = ] 'role']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @srvrolename = ] 'role'`Der Name der Server Rolle, für die Berechtigungen zurückgegeben werden. *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. Wenn keine Rolle angegeben wird, werden die Berechtigungen für alle festen Serverrollen zurückgegeben. *role* kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Serverrollen**|Systemadministratoren|  
|**securityadmin**|Sicherheitsadministratoren|  
|**serveradmin**|Serveradministratoren|  
|**setupadmin**|Setupadministratoren|  
|**processadmin**|Prozessadministratoren|  
|**diskadmin**|Datenträgeradministratoren|  
|**dbcreator**|Datenbankersteller|  
|**bulkadmin**|Kann BULK INSERT-Anweisungen ausführen|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**ServerRole**|**sysname**|Der Name einer festen Serverrolle|  
|**Berechtigung**|**sysname**|Die **ServerRole**zugeordnete Berechtigung|  
  
## <a name="remarks"></a>Bemerkungen  
 Zu den aufgeführten Berechtigungen zählen die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, die ausgeführt werden können, sowie andere spezielle Aktivitäten, die von Mitgliedern der festen Serverrolle ausgeführt werden können. Führen Sie **sp_helpsrvrole**aus, um eine Liste der festen Serverrollen anzuzeigen.  
  
 Die feste Serverrolle **sysadmin** hat die Berechtigungen aller anderen festen Serverrollen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 In der folgenden Abfrage werden die Berechtigungen zurückgegeben, die der festen Serverrolle `sysadmin` zugeordnet sind.  
  
```  
EXEC sp_srvrolepermission 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
