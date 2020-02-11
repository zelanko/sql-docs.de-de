---
title: sp_add_agent_profile (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_add_agent_profile
- sp_add_agent_profile_TSQL
helpviewer_keywords:
- sp_add_agent_profile
ms.assetid: 5c246a33-2c21-4a77-9c2a-a2c9f0c5dda1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 24a900409ae5979c13bdbff0d67d9d2670059208
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770855"
---
# <a name="sp_add_agent_profile-transact-sql"></a>sp_add_agent_profile (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt für einen Replikations-Agent ein neues Profil. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_agent_profile [ [ @profile_id= ] profile_id OUTPUT ]  
        , [ @profile_name= ] 'profile_name'   
        , [ @agent_type= ] 'agent_type' ]   
    [ , [ @profile_type= ] profile_type ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @default= ] default ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_id = ] profile_id`Die ID, die dem neu eingefügten Profil zugeordnet ist. *profile_id* ist vom Datentyp **int** und ein optionaler OUTPUT-Parameter. Wenn profile_id angegeben wird, wird der Wert auf die ID des neuen Profils festgelegt.  
  
`[ @profile_name = ] 'profile_name'`Der Name des Profils. *profile_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @agent_type = ] 'agent_type'`Der Typ des Replikations-Agents. *agent_type* ist vom Datentyp **int**und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Momentaufnahme-Agent|  
|**2**|Protokolllese-Agent|  
|**€**|Verteilungs-Agent|  
|**4**|Merge-Agent|  
|**21.00**|Warteschlangenlese-Agent|  
  
`[ @profile_type = ] profile_type`Der Typ des Profils. *profile_type* ist vom Datentyp **int**und hat den Standardwert **1**.  
  
 **0** gibt ein Systemprofil an. **1** gibt ein benutzerdefiniertes Profil an. Mit dieser gespeicherten Prozedur können nur benutzerdefinierte Profile erstellt werden. Daher ist der einzige gültige Wert **1**. Erstellt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur Systemprofile.  
  
`[ @description = ] 'description'`Ist eine Beschreibung des Profils. die *Beschreibung* ist vom Datentyp **nvarchar (3000)** und hat keinen Standardwert.  
  
`[ @default = ] default`Gibt an, ob das Profil der Standardwert für *agent_type * * ist.* der *Standard* Wert ist **Bit**. der Standardwert ist **0**. **1** gibt an, dass das hinzu zufügende Profil zum neuen Standardprofil für den Agent wird, der durch *agent_type*angegeben wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_add_agent_profile** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
 Benutzerdefinierte Agentprofile werden mit den standardmäßigen Agentparameterwerten hinzugefügt. Verwenden Sie [sp_change_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md) , um diese Standardwerte zu ändern, oder [sp_add_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md) , um zusätzliche Parameter hinzuzufügen.  
  
 Wenn **sp_add_agent_profile** ausgeführt wird, wird eine Zeile für das neue benutzerdefinierte Profil in der [MSagent_profiles &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) Tabelle hinzugefügt, und die zugehörigen Standardparameter für dieses Profil werden der MSagent_parameters Tabelle &#40;[&#41;Transact-SQL](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) -Tabelle hinzugefügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_add_agent_profile**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Replikations-Agentprofilen](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Replikationsagentprofile](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_change_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [sp_change_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_drop_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [sp_help_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)  
  
  
