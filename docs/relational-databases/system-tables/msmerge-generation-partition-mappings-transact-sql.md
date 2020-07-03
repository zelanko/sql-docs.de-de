---
title: MSmerge_generation_partition_mappings (T-SQL)
description: Beschreibt die MSmerge_generation_partition_mappings gespeicherte Prozedur, die zum Nachverfolgen von Änderungen an Partitionen in einer Mergeveröffentlichung verwendet wird.
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_generation_partition_mappings_TSQL
- MSmerge_generation_partition_mappings
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_generation_partition_mappings system table
ms.assetid: 443a4024-ce48-4772-9ee5-95bd6fb6476b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7760b7893632f2171edc2b4823f8b87b8313000f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889825"
---
# <a name="msmerge_generation_partition_mappings-transact-sql"></a>MSmerge_generation_partition_mappings (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSmerge_generation_partition_mappings** Tabelle dient zum Nachverfolgen von Änderungen an Partitionen in einer Mergeveröffentlichung. Diese Tabelle wird in der Veröffentlichungs- und der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Identifiziert die Mergeveröffentlichung|  
|**Stro**|**bigint**|Der Generierungswert.|  
|**partition_id**|**int**|Identifiziert die Partition.|  
|**changecount**|**int**|Die Anzahl der Änderungen der Partition.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
