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
ms.openlocfilehash: 5a6b0660635812a216525665832b0f16f64538b9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67894938"
---
# <a name="msmerge_dynamic_snapshots-transact-sql"></a>MSmerge_dynamic_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In der **MSmerge_dynamic_snapshots** Tabelle wird der Speicherort der gefilterten Daten Momentaufnahme für jede Partition nachverfolgt, die für eine Mergeveröffentlichung mit parametrisierten Zeilen filtern definiert ist. Diese Tabelle wird in der **Veröffentlichungs** Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|Die ID der Mergepartition.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Der Standort der gefilterten Datenmomentaufnahme für die Partition.|  
|**last_updated**|**datetime**|Das Datum, an dem die gefilterte Datenmomentaufnahme aktualisiert wurde.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
