---
title: sp_help_agent_default (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 57b3016f0f5ee9f58e41ce6993af69c33aa3b742
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827767"
---
# <a name="sp_help_agent_default-transact-sql"></a>sp_help_agent_default (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ruft die ID der Standardkonfiguration für den Agenttyp ab, der als Parameter übergeben wird. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_agent_default [ @profile_id= ] profile_id OUTPUT   
        , [ @agent_type = ] agent_type  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_id = ] _profile_idOUTPUT`Die ID der Standardkonfiguration für den Agenttyp. *profile_id* ist vom Datentyp **int**und hat keinen Standardwert. *profile_id* ist auch ein Output-Parameter und gibt die ID der Standardkonfiguration für den Agenttyp zurück.  
  
`[ @agent_type = ] 'agent_type'`Der Typ des Agents. *agent_type* ist vom Datentyp **int**und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Momentaufnahmen-Agent.|  
|**2**|Protokolllese-Agent.|  
|**3**|Verteilungs-Agent.|  
|**4**|Merge-Agent.|  
|**9**|Warteschlangenlese-Agent|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_help_agent_default** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **replmonitor** können **sp_help_agent_default**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
