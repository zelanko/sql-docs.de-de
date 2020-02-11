---
title: MSpub_identity_range (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpub_identity_range_TSQL
- MSpub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSpub_identity_range system table
ms.assetid: 68746eef-32e1-42bc-aff0-9798cd0e88b8
author: stevestein
ms.author: sstein
ms.openlocfilehash: b1b204024d65e72eb65eefc9f63f914eab6ace29
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032600"
---
# <a name="mspub_identity_range-transact-sql"></a>MSpub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSpub_identity_range** Tabelle bietet Unterstützung für die Identitäts Bereichs Verwaltung. Diese Tabelle wird in den Datenbanken publication und subscription gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|Die ID der Tabelle, die die durch Replikation verwaltete Identitätsspalte enthält.|  
|**Bereich**|**BIGINT**|Steuert die Bereichsgröße der aufeinander folgenden Identitätswerte, die im Abonnement bei einer Anpassung zugewiesen würden.|  
|**pub_range**|**BIGINT**|Steuert die Bereichsgröße der aufeinander folgenden Identitätswerte, die in der Veröffentlichung bei einer Anpassung zugewiesen würden.|  
|**current_pub_range**|**BIGINT**|Der aktuelle Bereich, der von der Veröffentlichung verwendet wird. Sie kann sich von *pub_range* unterscheiden, wenn Sie nach der Änderung durch **sp_changearticle** und vor der nächsten Bereichs Anpassung angezeigt wird.|  
|**Mindest**|**int**|Der Prozentwert, der steuert, wann der Verteilungs-Agent einen neuen Identitätsbereich zuweist. Wenn der in *Schwellenwert* angegebene Prozentsatz der Werte verwendet wird, erstellt der Verteilungs-Agent einen neuen Identitäts Bereich.|  
|**last_seed**|**BIGINT**|Die untere Grenze des aktuellen Bereichs.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
