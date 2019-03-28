---
title: Sp_help_agent_default (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_agent_default
- sp_help_agent_default_TSQL
helpviewer_keywords:
- sp_help_agent_default
ms.assetid: 7ba55e39-05dd-43c7-b5da-b268ed8426dd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 182f13347a1fdf4dc06e6d3276e481ce54f01e45
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527972"
---
# <a name="sphelpagentdefault-transact-sql"></a>sp_help_agent_default (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ruft die ID der Standardkonfiguration für den Agenttyp ab, der als Parameter übergeben wird. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_agent_default [ @profile_id= ] profile_id OUTPUT   
        , [ @agent_type = ] agent_type  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_id = ] _profile_idOUTPUT` Ist die ID der Standardkonfiguration für den Typ des Agents. *Profile_id* ist **Int**, hat keinen Standardwert. *Profile_id* ist auch ein OUTPUT-Parameter und gibt die ID der Standardkonfiguration für den Typ des Agents zurück.  
  
`[ @agent_type = ] 'agent_type'` Ist der Typ des Agents. *Agent_type* ist **Int**und hat keinen Standardwert und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Momentaufnahme-Agent.|  
|**2**|Protokolllese-Agent.|  
|**3**|Verteilungs-Agent.|  
|**4**|Merge-Agent.|  
|**9**|Warteschlangenlese-Agent|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_help_agent_default** wird in allen Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Replmonitor** feste Datenbankrolle können ausführen **Sp_help_agent_default**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
