---
title: sp_add_agent_parameter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_add_agent_parameter_TSQL
- sp_add_agent_parameter
helpviewer_keywords:
- sp_add_agent_parameter
ms.assetid: 055f4765-0574-47c3-bf7d-6ef6e9bd8b34
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c1aafa1736ff626f7b0bea9bea8753ae2c509ac4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770960"
---
# <a name="sp_add_agent_parameter-transact-sql"></a>sp_add_agent_parameter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Fügt einem Agentprofil einen neuen Parameter und dessen Wert hinzu. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_agent_parameter [ @profile_id = ] profile_id  
        , [ @parameter_name = ] 'parameter_name'   
        , [ @parameter_value = ] 'parameter_value'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_id = ] profile_id`Die ID des Profils aus der **MSagent_profiles** Tabelle in der **msdb** -Datenbank. *profile_id* ist vom Datentyp **int**und hat keinen Standardwert.  
  
 Um herauszufinden, welcher Agenttyp diese *profile_id* darstellt, suchen Sie die *profile_id* in der [MSagent_profiles &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) Tabelle, und notieren Sie sich den Wert des *agent_type* Felds. Mit den Parametern werden folgende Werte angegeben:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Momentaufnahme-Agent|  
|**2**|Protokolllese-Agent|  
|**€**|Verteilungs-Agent|  
|**4**|Merge-Agent|  
|**21.00**|Warteschlangenlese-Agent|  
  
`[ @parameter_name = ] 'parameter_name'`Der Name des Parameters. *parameter_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Eine Liste der Parameter, die bereits in Systemprofilen definiert sind, finden Sie unter [Replikations-Agentprofile](../../relational-databases/replication/agents/replication-agent-profiles.md). Eine vollständige Liste der gültigen Parameter für die einzelnen Agents finden Sie in den folgenden Themen:  
  
-   [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Replikationsprotokolllese-Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Replication Queue Reader Agent](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
`[ @parameter_value = ] 'parameter_value'`Der Wert, der dem-Parameter zugewiesen werden soll. *parameter_value* ist vom Datentyp **nvarchar (255)** und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_add_agent_parameter** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_add_agent_parameter**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Replikations-Agentprofilen](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Replikationsagentprofile](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_change_agent_profile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_change_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)  
  
  
