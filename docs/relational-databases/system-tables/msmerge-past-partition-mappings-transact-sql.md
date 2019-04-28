---
title: MSmerge_past_partition_mappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_past_partition_mappings
- MSmerge_past_partition_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_past_partition_mappings system table
ms.assetid: 06d54ff5-4d29-4eeb-b8be-64d032e53134
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7ad8c5db6a067477e3e4e5d349a8faa2adba5199
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903679"
---
# <a name="msmergepastpartitionmappings-transact-sql"></a>MSmerge_past_partition_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_past_partition_mappings** Tabelle speichert eine Zeile für jede Partitions-Id eine bestimmte geänderte Zeile gehört, jedoch nicht mehr zugeordnet ist. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Die veröffentlichungsnummer, die in gespeichert ist **Sysmergepublications**.|  
|**tablenick**|**int**|Der Spitzname der veröffentlichten Tabelle.|  
|**rowguid**|**uniqueidentifier**|Der Zeilenbezeichner für die angegebene Zeile.|  
|**partition_id**|**int**|Die Partitions-ID, die der Zeile zugeordnet ist. Der Wert ist 1, wenn die Änderung der Zeile an alle Abonnenten relevant ist.|  
|**generation**|**bigint**|Der Wert der Generierung, in der die Partitionsänderung aufgetreten ist.|  
|**reason**|**tinyint**|Intern-nur zur Verwendung.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
