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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bde828bdb5d99b132373b847daeb9f8126a85f7a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890068"
---
# <a name="msagent_profiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSagent_profiles** Tabelle enthält eine Zeile für jedes definierte Replikations-Agentprofil. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|Die Profil-ID.|  
|**profile_name**|**sysname**|Der eindeutige Profilname für den Agenttyp.|  
|**agent_type**|**int**|Der Agenttyp:<br /><br /> **1** = Momentaufnahmen-Agent<br /><br /> **2** = Protokolllese-Agent<br /><br /> **3** = Verteilungs-Agent<br /><br /> **4** = Merge-Agent<br /><br /> **9** = Warteschlangenlese-Agent|  
|**type**|**int**|Der Profiltyp:<br /><br /> **0** = System**1** = Benutzer definiert|  
|**description**|**nvarchar (3000)**|Die Beschreibung des Profils.|  
|**def_profile**|**bit**|Gibt an, ob dieses Profil das Standardprofil für diesen Agenttyp ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
