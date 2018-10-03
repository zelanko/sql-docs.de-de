---
title: MSsubscription_articles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_articles
- MSsubscription_articles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_articles system table
ms.assetid: dbc1737f-261e-4017-b9cd-703b9fc4ac78
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 767df03bda9a11ce629244b15e83b7dc676894a9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47691762"
---
# <a name="mssubscriptionarticles-transact-sql"></a>MSsubscription_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSsubscription_articles** Tabelle enthält Informationen zu den Artikeln in einem Abonnement in der Warteschlange. Diese Tabelle wird nur für die folgenden Replikationstypen aufgefüllt: Verzögertes Update über eine Warteschlange und sofortiges Update mit verzögertem Update über eine Warteschlange als Failover.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Die ID der Momentaufnahme, die diesen Artikel bedient.|  
|**artid**|**int**|Die Artikel-ID aus der **Sysarticles** Tabelle.|  
|**article**|**sysname**|Der Name des Artikels aus der **Sysarticles** Tabelle.|  
|**dest_table**|**sysname**|Der Name der Zieltabelle aus der **Sysarticles** Tabelle.|  
|**Besitzer**|**sysname**|Der Besitzer des Abonnements.|  
|**cft_table**|**sysname**|Der Name der Konflikttabelle dieses Artikels für den Replikationstyp Verzögertes Update über eine Warteschlange.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
