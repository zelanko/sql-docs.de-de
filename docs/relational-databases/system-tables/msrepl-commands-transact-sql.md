---
title: MSrepl_commands (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_commands
- MSrepl_commands_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_commands system table
ms.assetid: 53b9f9cd-9429-47a0-aba2-908fc60e7036
author: stevestein
ms.author: sstein
ms.openlocfilehash: c02a0201483617966d7d1c8aadfbad4ab39971e3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127430"
---
# <a name="msrepl_commands-transact-sql"></a>MSrepl_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSrepl_commands** Tabelle enthält Zeilen mit replizierten Befehlen. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Die ID der Verlegerdatenbank.|  
|**xact_seqno**|**varbinary(16)**|Die Transaktionssequenznummer.|  
|**type**|**int**|Der Befehlstyp.|  
|**article_id**|**int**|Die ID des Artikels.|  
|**originator_id**|**int**|Die ID des Urhebers.|  
|**command_id**|**int**|Die Befehls-ID.|  
|**partial_command**|**bit**|Gibt an, ob es sich um einen Teilbefehl handelt.|  
|**s**|**varbinary (1024)**|Der Befehlswert.|  
|**hashkey**|**int**|Nur intern verwendet.|  
|**originator_lsn**|**varbinary(16)**|Identifiziert die LSN des Befehls in der Ausgangsveröffentlichung. Wird in der Peer-zu-Peer-Transaktionsreplikation verwendet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)  
  
  
