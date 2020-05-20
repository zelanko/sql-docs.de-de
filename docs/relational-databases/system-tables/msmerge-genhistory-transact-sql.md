---
title: MSmerge_genhistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8d79f0c0cc71b2295dbea6340c515afb5e2c899c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82805365"
---
# <a name="msmerge_genhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_genhistory** Tabelle enthält eine Zeile für jede Generierung, die ein Abonnent kennt (innerhalb der Beibehaltungs Dauer). Sie wird verwendet, um zu verhindern, dass allgemeine Generierungsvorgänge bei Austauschvorgängen gesendet werden, und um aus Sicherungen wiederhergestellte Abonnenten erneut zu synchronisieren. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|Der globale Bezeichner der durch Generierung auf dem Abonnenten identifizierten Änderungen.|  
|**pubid**|**uniqueidentifier**|Der Bezeichner der Veröffentlichung.|  
|**Stro**|**bigint**|Der Generierungswert.|  
|**art_nick**|**int**|Der Spitzname für den Artikel.|  
|**nicknames**|**varbinary (1001)**|Eine Liste der Spitznamen anderer Abonnenten, die bekanntermaßen bereits diese Generierung aufweisen. Die Liste wird verwendet, um das Senden einer Generierung an einen Abonnenten zu verhindern, der über diese Änderungen bereits informiert ist. Spitznamen in der Spitznamenliste werden in sortierter Reihenfolge verwaltet, damit Suchvorgänge effizienter ausgeführt werden können. Falls mehr Spitznamen vorhanden sind, als in dieses Feld passen, bietet diese Optimierung für sie keine Vorteile.|  
|**coldate**|**datetime**|Datum, an dem der Tabelle die aktuelle Generierung hinzugefügt wird.|  
|**genstatus**|**tinyint**|Der Status der Generierung:<br /><br /> **0** = geöffnet.<br /><br /> **1** = geschlossen.<br /><br /> **2** = geschlossen und stammt von einem anderen Abonnenten.|  
|**changecount**|**int**|Die Anzahl von Änderungen, die in einer bestimmten Generierung widergespiegelt sind.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
