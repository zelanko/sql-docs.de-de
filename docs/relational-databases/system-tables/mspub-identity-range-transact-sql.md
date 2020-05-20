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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 733fac032af45eb81b50bae4b20316d04234223e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82812488"
---
# <a name="mspub_identity_range-transact-sql"></a>MSpub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSpub_identity_range** Tabelle bietet Unterstützung für die Identitäts Bereichs Verwaltung. Diese Tabelle wird in den Datenbanken publication und subscription gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|Die ID der Tabelle, die die durch Replikation verwaltete Identitätsspalte enthält.|  
|**range**|**bigint**|Steuert die Bereichsgröße der aufeinander folgenden Identitätswerte, die im Abonnement bei einer Anpassung zugewiesen würden.|  
|**pub_range**|**bigint**|Steuert die Bereichsgröße der aufeinander folgenden Identitätswerte, die in der Veröffentlichung bei einer Anpassung zugewiesen würden.|  
|**current_pub_range**|**bigint**|Der aktuelle Bereich, der von der Veröffentlichung verwendet wird. Sie kann sich von *pub_range* unterscheiden, wenn Sie nach der Änderung durch **sp_changearticle** und vor der nächsten Bereichs Anpassung angezeigt wird.|  
|**Mindest**|**int**|Der Prozentwert, der steuert, wann der Verteilungs-Agent einen neuen Identitätsbereich zuweist. Wenn der in *Schwellenwert* angegebene Prozentsatz der Werte verwendet wird, erstellt der Verteilungs-Agent einen neuen Identitäts Bereich.|  
|**last_seed**|**bigint**|Die untere Grenze des aktuellen Bereichs.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
