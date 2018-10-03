---
title: MSmerge_genhistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d57447c1e7beeb29da3a39517e1cb5b84f0b32f9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692358"
---
# <a name="msmergegenhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_genhistory** -Tabelle enthält eine Zeile für jede Generierung, die ein Abonnent bekannt (innerhalb der Aufbewahrungsdauer sind). Sie wird verwendet, um zu verhindern, dass allgemeine Generierungsvorgänge bei Austauschvorgängen gesendet werden, und um aus Sicherungen wiederhergestellte Abonnenten erneut zu synchronisieren. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|Der globale Bezeichner der durch Generierung auf dem Abonnenten identifizierten Änderungen.|  
|**pubid**|**uniqueidentifier**|Der Bezeichner der Veröffentlichung.|  
|**generation**|**bigint**|Der Generierungswert.|  
|**art_nick**|**int**|Der Spitzname für den Artikel.|  
|**Spitznamen**|**varbinary(1001)**|Eine Liste der Spitznamen anderer Abonnenten, die bekanntermaßen bereits diese Generierung aufweisen. Die Liste wird verwendet, um das Senden einer Generierung an einen Abonnenten zu verhindern, der über diese Änderungen bereits informiert ist. Spitznamen in der Spitznamenliste werden in sortierter Reihenfolge verwaltet, damit Suchvorgänge effizienter ausgeführt werden können. Falls mehr Spitznamen vorhanden sind, als in dieses Feld passen, bietet diese Optimierung für sie keine Vorteile.|  
|**colDate**|**datetime**|Datum, an dem der Tabelle die aktuelle Generierung hinzugefügt wird.|  
|**genstatus**|**tinyint**|Der Status der Generierung:<br /><br /> **0** = geöffnet.<br /><br /> **1** = geschlossen.<br /><br /> **2** = geschlossen und stammt von einem anderen Abonnenten.|  
|**"changecount"**|**int**|Die Anzahl von Änderungen, die in einer bestimmten Generierung widergespiegelt sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
