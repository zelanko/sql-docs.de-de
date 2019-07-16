---
title: MSdynamicsnapshotjobs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdynamicsnapshotjobs_TSQL
- MSdynamicsnapshotjobs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdynamicsnapshotjobs system table
ms.assetid: 4f36a325-0e3c-46c4-aeeb-416346cce0bc
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8822b0e7c56fe109a251365050f5aed9cdef178
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67907359"
---
# <a name="msdynamicsnapshotjobs-transact-sql"></a>MSdynamicsnapshotjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSdynamicsnapshotjobs** -Tabelle verfolgt nach, die parametrisierten zeilenfilterinformationen angewendet, um eine Momentaufnahme gefilterter Daten zu generieren. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Die ID des gefilterten Datenmomentaufnahmeauftrags.|  
|**name**|**sysname**|Der Name des gefilterten Datenmomentaufnahmeauftrags.|  
|**pubid**|**uniqueidentifier**|Die eindeutige ID für diese Veröffentlichung.|  
|**job_id**|**uniqueidentifier**|Die ID der SQL Server-Agent-Auftrags auf dem Verteiler.|  
|**agent_id**|**int**|Die ID der SQL Server-Agent.|  
|**dynamic_filter_login**|**sysname**|Der Wert, der zum Auswerten von der [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) -Funktion in parametrisierten Zeilenfiltern für die Veröffentlichung.|  
|**dynamic_filter_hostname**|**sysname**|Der Wert, der zum Auswerten von der [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) -Funktion in parametrisierten Zeilenfiltern für die Veröffentlichung.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Der Pfad zu dem Ordner, aus dem die Momentaufnahmedateien gelesen werden, wenn eine gefilterte Datenmomentaufnahme verwendet wird.|  
|**partition_id**|**int**|Die ID der Datenpartition, der der Auftrag angehört.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
