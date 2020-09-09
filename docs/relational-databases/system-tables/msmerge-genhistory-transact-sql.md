---
description: MSmerge_genhistory (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4031540d14a0af583fa544d51fc43eddf589a9f1
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544494"
---
# <a name="msmerge_genhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
  
