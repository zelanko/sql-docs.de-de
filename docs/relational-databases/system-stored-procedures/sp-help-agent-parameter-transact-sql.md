---
description: sp_help_agent_parameter (Transact-SQL)
title: sp_help_agent_parameter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_agent_parameter
- sp_help_agent_parameter_TSQL
helpviewer_keywords:
- sp_help_agent_parameter
ms.assetid: 8fb4a9c3-19af-4a34-8004-572729ba3d15
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cfb61e7c3bbfcbb3bd1c93bff3d650912f7ebd01
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493237"
---
# <a name="sp_help_agent_parameter-transact-sql"></a>sp_help_agent_parameter (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt alle Parameter eines Profils aus der [MSagent_parameters &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) Systemtabelle zurück. Diese gespeicherte Prozedur wird auf dem Verteiler, auf dem der Agent ausgeführt wird, für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_agent_parameter [ [ @profile_id = ] profile_id ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_id = ] profile_id` Die ID des Profils aus der [MSagent_parameters &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) -Tabelle. *profile_id* ist vom Datentyp **int**und hat den Standardwert **-1**, der alle Parameter zurückgibt.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|ID des Agentprofils|  
|**parameter_name**|**sysname**|Der Name des Parameters.|  
|**value**|**nvarchar(255)**|Wert des Parameters|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_help_agent_parameter** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **replmonitor** können **sp_help_agent_parameter**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Replikations-Agent-Profilen](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [sp_add_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
