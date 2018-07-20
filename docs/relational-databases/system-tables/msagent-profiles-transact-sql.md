---
title: MSagent_profiles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e3b246b0c174838529dd5e0c6c38bd633c0a90b8
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101378"
---
# <a name="msagentprofiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSagent_profiles** Tabelle enthält eine Zeile für jede definierte Replikations-Agent-Profil. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|Die Profil-ID.|  
|**profile_name**|**sysname**|Der eindeutige Profilname für den Agenttyp.|  
|**agent_type**|**int**|Der Agenttyp:<br /><br /> **1** = Momentaufnahme-Agent<br /><br /> **2** = Protokolllese-Agent<br /><br /> **3** = Verteilungs-Agent<br /><br /> **4** = Merge-Agent<br /><br /> **9** = Warteschlangenlese-Agent|  
|**type**|**int**|Der Profiltyp:<br /><br /> **0** = System**1** = Benutzerdefiniert|  
|**description**|**nvarchar(3000)**|Die Beschreibung des Profils.|  
|**def_profile**|**bit**|Gibt an, ob dieses Profil das Standardprofil für diesen Agenttyp ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
