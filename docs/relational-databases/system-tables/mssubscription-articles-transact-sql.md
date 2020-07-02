---
title: MSsubscription_articles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_articles
- MSsubscription_articles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_articles system table
ms.assetid: dbc1737f-261e-4017-b9cd-703b9fc4ac78
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 30488b669265b66036b591191e8e528e1ef74b35
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757761"
---
# <a name="mssubscription_articles-transact-sql"></a>MSsubscription_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Die **MSsubscription_articles** Tabelle enthält Informationen zu den Artikeln in einem in der Warteschlange befindlichen Abonnement. Diese Tabelle wird nur für die folgenden Replikationstypen aufgefüllt: Verzögertes Update über eine Warteschlange und sofortiges Update mit verzögertem Update über eine Warteschlange als Failover.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Die ID der Momentaufnahme, die diesen Artikel bedient.|  
|**artid**|**int**|Die Artikel-ID aus der **sysarticles** -Tabelle.|  
|**Artikel**|**sysname**|Der Name des Artikels in der **sysarticles** -Tabelle.|  
|**dest_table**|**sysname**|Der Name der Ziel Tabelle aus der **sysarticles** -Tabelle.|  
|**Eigentor**|**sysname**|Der Besitzer des Abonnements.|  
|**cft_table**|**sysname**|Der Name der Konflikttabelle dieses Artikels für den Replikationstyp Verzögertes Update über eine Warteschlange.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
