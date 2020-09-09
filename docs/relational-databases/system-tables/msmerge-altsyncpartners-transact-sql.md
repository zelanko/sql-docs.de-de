---
description: MSmerge_altsyncpartners (Transact-SQL)
title: MSmerge_altsyncpartners (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_altsyncpartners_TSQL
- MSmerge_altsyncpartners
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_altsyncpartners system table
ms.assetid: da51b0f8-5ad0-4aeb-96ed-2b3672a2a6e2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ccec6fa369580fd68af0089c7e581ef1e915e868
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545658"
---
# <a name="msmerge_altsyncpartners-transact-sql"></a>MSmerge_altsyncpartners (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In der **MSmerge_altsyncpartners** Tabelle wird die Zuordnung der aktuellen Synchronisierungs Partner für einen Verleger nachverfolgt. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Der Bezeichner des ursprünglichen Verlegers.|  
|**alternate_subid**|**uniqueidentifier**|Der Bezeichner des Abonnenten, der der alternative Synchronisierungspartner ist.|  
|**description**|**nvarchar(255)**|Die Beschreibung des alternativen Synchronisierungspartners.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
