---
title: sp_update_agent_profile (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_update_agent_profile_TSQL
- sp_update_agent_profile
helpviewer_keywords:
- sp_update_agent_profile
ms.assetid: cc81f227-0df3-4151-bb4d-4f45ea997b71
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a529df241a5d827c277f3a39110ae04697a13e17
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891388"
---
# <a name="sp_update_agent_profile-transact-sql"></a>sp_update_agent_profile (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Aktualisiert das von einem Replikations-Agent verwendete Profil. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_update_agent_profile [@agent_type=] agent_type, [ @agent_id= ] agent_id, [ @profile_id= ] profile_id  
```  
  
## <a name="arguments"></a>Argumente  
`[ @agent_type = ] 'agent_type'`Der Typ des Agents. *agent_type* ist vom Datentyp **int**und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Momentaufnahmen-Agent.|  
|**2**|Protokolllese-Agent.|  
|**3**|Verteilungs-Agent.|  
|**4**|Merge-Agent.|  
|**9**|Warteschlangenlese-Agent|  
  
`[ @agent_id = ] 'agent_id'`Die ID des Agents. *agent_id* ist vom Datentyp **int**und hat keinen Standardwert.  
  
`[ @profile_id = ] 'profile_id'`Die ID des Profils, das der Agent verwenden soll. *profile_id* ist vom Datentyp **int**und hat keinen Standardwert. Verwenden Sie [sp_help_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md), um eine Liste der Profile anzuzeigen, die für jeden Agent definiert sind. Weitere Informationen zu Systemprofilen finden Sie unter [Replikations-Agentprofile](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_update_agent_profile** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_update_agent_profile**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationsagentprofile](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_change_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_drop_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
