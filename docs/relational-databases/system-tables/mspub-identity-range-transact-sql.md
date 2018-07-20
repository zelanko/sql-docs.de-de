---
title: MSpub_identity_range (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSpub_identity_range_TSQL
- MSpub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSpub_identity_range system table
ms.assetid: 68746eef-32e1-42bc-aff0-9798cd0e88b8
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 11da4746a138b2deafd990ef237ecfb4537cbce4
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101898"
---
# <a name="mspubidentityrange-transact-sql"></a>MSpub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSpub_identity_range** Tabelle stellt Unterstützung für die identitätsbereichsverwaltung bereit. Diese Tabelle wird in den Datenbanken publication und subscription gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Objekt-ID**|**int**|Die ID der Tabelle, die die durch Replikation verwaltete Identitätsspalte enthält.|  
|**range**|**bigint**|Steuert die Bereichsgröße der aufeinander folgenden Identitätswerte, die im Abonnement bei einer Anpassung zugewiesen würden.|  
|**pub_range**|**bigint**|Steuert die Bereichsgröße der aufeinander folgenden Identitätswerte, die in der Veröffentlichung bei einer Anpassung zugewiesen würden.|  
|**current_pub_range**|**bigint**|Der aktuelle Bereich, der von der Veröffentlichung verwendet wird. Unterschiedlich sein *Pub_range* Wenn angezeigt wird, nachdem geändert wird, indem **Sp_changearticle** und vor dem nächsten Bereich Einstellung.|  
|**threshold**|**int**|Der Prozentwert, der steuert, wann der Verteilungs-Agent einen neuen Identitätsbereich zuweist. Wenn der Prozentsatz der Werte in angegebenen *Schwellenwert* wird verwendet, erstellt der Verteilungs-Agent einen neuen Identitätsbereich.|  
|**last_seed**|**bigint**|Die untere Grenze des aktuellen Bereichs.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
