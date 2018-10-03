---
title: MSmerge_partition_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_partition_groups_TSQL
- MSmerge_partition_groups
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_partition_groups system table
ms.assetid: 5d56d780-ee40-4afc-9c2a-d1723d86e430
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d6b0b9f18377de89f6cf607f9aaab6c294f4a716
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846568"
---
# <a name="msmergepartitiongroups-transact-sql"></a>MSmerge_partition_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_partition_groups** -Tabelle speichert eine Zeile für jede Partition in einer bestimmten Datenbank berechnet. Neben den aufgelisteten Spalten wird dieser Tabelle eine Spalte für jede Funktion hinzugefügt, die in einem parametrisierten Zeilenfilter verwendet wird. Z. B. eine Spalte, die mit dem Namen **HOST_NAME_FN** zur Tabelle hinzugefügt wird, wenn ein Filter verwendet das [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) Funktion. Eine Zeile wird für jeden eindeutigen Funktionswertesatz gespeichert, der mit diesem Verleger synchronisiert wurde. Wenn mindestens zwei Abonnenten mit genau dem gleichen Wert für alle diese Funktionen synchronisiert werden, nutzen sie gemeinsam dieselbe Zeile in dieser Tabelle und deshalb auch die gleiche Partitions-ID. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|Die Identitätsspalte, die eine eindeutige ID für die vorausberechnete Partition bereitstellt.|  
|**publication_number**|**smallint**|Die veröffentlichungsnummer, die in gespeichert ist **Sysmergepublications**.|  
|**maxgen_whenadded**|**bigint**|Die höchste bekannte Generierung auf dem Verleger zu dem Zeitpunkt, als die Zeile in dieser Tabelle eingefügt wurde.|  
|**using_partition_groups**|**bit**|Gibt an, ob die Partition zu einer Veröffentlichung gehört, die vorausberechnete Partitionen verwendet. Die folgenden Werte sind möglich:<br /><br /> **0** = Veröffentlichung verwendet Vorausberechnete Partitionen nicht.<br /><br /> **1** = Veröffentlichung verwendet Vorausberechnete Partitionen<br /><br /> Weitere Informationen finden Sie unter [Optimieren Parametrisierter Filter-Leistung mit Vorausberechneten Partitionen ](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).|  
|**HOST_NAME_FN**|**nvarchar(128)**|Der bereitgestellte Wert, wenn parametrisierte Zeilenfilter zum Generieren von Partitionen verwendet werden. Weitere Informationen finden Sie unter [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
