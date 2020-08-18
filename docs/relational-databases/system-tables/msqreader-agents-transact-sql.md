---
description: MSqreader_agents (Transact-SQL)
title: MSqreader_agents (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSqreader_agents_TSQL
- MSqreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSqreader_agents system table
ms.assetid: dfa1f45e-c531-4385-a097-0a9edd1d7eab
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 10ed60edbbbe2e94e09a9205d34f856cee42c687
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492762"
---
# <a name="msqreader_agents-transact-sql"></a>MSqreader_agents (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSqreader_agents** Tabelle enthält eine Zeile für jede Warteschlangenlese-Agent, die auf dem lokalen Verteiler ausgeführt wird. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Die ID des Warteschlangenlese-Agents.|  
|**name**|**nvarchar (100)**|Der Name des Warteschlangenlese-Agents.|  
|**job_id**|**Binary (16)**|Die eindeutige Auftrags-ID aus der **sysjobs** -Tabelle.|  
|**profile_id**|**int**|Die Profil-ID aus der **MSagent_profiles** Tabelle.|  
|**job_step_uid**|**uniqueidentifier**|Die eindeutige ID des Auftragsschritts des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents, in dem der Agent gestartet wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
