---
title: MSmerge_subscriptions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_subscriptions
- MSmerge_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_subscriptions system table
ms.assetid: cafd954a-92f8-44cb-a5d0-dce9aafa5ee1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5341eae935d9c97eb7ff0ae6b71b21bba3d986e1
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52811793"
---
# <a name="msmergesubscriptions-transact-sql"></a>MSmerge_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_subscriptions** -Tabelle enthält eine Zeile für jedes Abonnement, das vom Merge-Agent auf dem Abonnenten bedient. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Die ID des Verlegers|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**publication_id**|**int**|Die ID der Veröffentlichung.|  
|**subscriber_id**|**smallint**|Die ID des Abonnenten.|  
|**subscriber_db**|**sysname**|Der Name der Abonnementdatenbank.|  
|**subscription_type**|**int**|Der Typ des Abonnements:<br /><br /> 0 = Push.<br /><br /> 1 = Pull.<br /><br /> 2 = Anonym.|  
|**sync_type**|**tinyint**|Typ der Synchronisierung:<br /><br /> 1 = Automatisch.<br /><br /> 2 = Keine Synchronisierung|  
|**status**|**tinyint**|Status des Abonnements.|  
|**subscription_time**|**datetime**|Zeitpunkt, zu dem das Abonnement hinzugefügt wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
