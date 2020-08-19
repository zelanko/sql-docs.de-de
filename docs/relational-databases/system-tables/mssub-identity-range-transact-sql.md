---
description: MSsub_identity_range (Transact-SQL)
title: MSsub_identity_range (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsub_identity_range_TSQL
- MSsub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSsub_identity_range system table
ms.assetid: 26e20d28-14ed-44fc-af3b-4de386de4bb8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7ec13e409f637063abbf5d2d3b99549a13d2d5ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419094"
---
# <a name="mssub_identity_range-transact-sql"></a>MSsub_identity_range (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSsub_identity_range** Tabelle bietet Unterstützung für die Identitäts Bereichs Verwaltung für Abonnements. Diese Tabelle wird in Abonnementdatenbanken gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|Die ID der Tabelle, die die durch Replikation verwaltete Identitätsspalte enthält.|  
|**range**|**bigint**|Steuert die Bereichsgröße der aufeinander folgenden Identitätswerte, die auf dem Abonnenten bei einer Anpassung zugewiesen würden.|  
|**last_seed**|**bigint**|Die untere Grenze des aktuellen Bereichs.|  
|**threshold**|**int**|Der Prozentwert, der steuert, wann der Verteilungs-Agent einen neuen Identitätsbereich zuweist. Wenn der in *Schwellenwert* angegebene Prozentsatz der Werte verwendet wird, erstellt der Verteilungs-Agent einen neuen Identitäts Bereich.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
