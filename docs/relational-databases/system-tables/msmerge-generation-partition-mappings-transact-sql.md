---
title: MSmerge_generation_partition_mappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_generation_partition_mappings_TSQL
- MSmerge_generation_partition_mappings
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_generation_partition_mappings system table
ms.assetid: 443a4024-ce48-4772-9ee5-95bd6fb6476b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b57650c8000307d102e27ae9cab277f26ee4735
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644528"
---
# <a name="msmergegenerationpartitionmappings-transact-sql"></a>MSmerge_generation_partition_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_generation_partition_mappings** -Tabelle dient zum Nachverfolgen von Änderungen an Partitionen in einer Mergeveröffentlichung definiert. Diese Tabelle wird in der Veröffentlichungs- und der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Identifiziert die Mergeveröffentlichung|  
|**generation**|**bigint**|Der Generierungswert.|  
|**partition_id**|**int**|Identifiziert die Partition.|  
|**"changecount"**|**int**|Die Anzahl der Änderungen der Partition.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
