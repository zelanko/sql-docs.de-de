---
title: MSmerge_dynamic_snapshots (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_dynamic_snapshots_TSQL
- MSmerge_dynamic_snapshots
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_dynamic_snapshots system table
ms.assetid: a5592b3c-731b-4fc9-ae4b-2602ed78248e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f7e41f604bf9d87b2db0b22749f58ee7fd2acf2b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52791812"
---
# <a name="msmergedynamicsnapshots-transact-sql"></a>MSmerge_dynamic_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_dynamic_snapshots** Tabelle verfolgt den Speicherort der gefilterten datenmomentaufnahme für jede Partition, die für eine Mergeveröffentlichung mit parametrisierten Zeilenfiltern definiert. Diese Tabelle befindet sich in der **Veröffentlichung** Datenbank.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|Die ID der Mergepartition.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Der Standort der gefilterten Datenmomentaufnahme für die Partition.|  
|**last_updated**|**datetime**|Das Datum, an dem die gefilterte Datenmomentaufnahme aktualisiert wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
