---
title: MSagent_profiles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5147ef1f482850b55a5d01a476b1981dfa012e5e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68021066"
---
# <a name="msagent_profiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSagent_profiles** Tabelle enthält eine Zeile für jedes definierte Replikations-Agentprofil. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|Die Profil-ID.|  
|**profile_name**|**sysname**|Der eindeutige Profilname für den Agenttyp.|  
|**agent_type**|**int**|Der Agenttyp:<br /><br /> **1** = Momentaufnahmen-Agent<br /><br /> **2** = Protokolllese-Agent<br /><br /> **3** = Verteilungs-Agent<br /><br /> **4** = Merge-Agent<br /><br /> **9** = Warteschlangenlese-Agent|  
|**type**|**int**|Der Profiltyp:<br /><br /> **0** = System**1** = Benutzer definiert|  
|**Beschreibung**|**nvarchar (3000)**|Die Beschreibung des Profils.|  
|**def_profile**|**bit**|Gibt an, ob dieses Profil das Standardprofil für diesen Agenttyp ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
