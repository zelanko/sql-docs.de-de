---
title: MSmerge_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
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
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a46c6c1ebaad6cb24ce8ad6bd3185cda74768113
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103628"
---
# <a name="msmergehistory-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_history** -Tabelle enthält Verlaufszeilen mit detaillierten Beschreibungen der Ergebnisse vorheriger auftragssitzungen des Merge-Agent des. Diese Tabelle enthält eine Zeile für jede Ausgabezeile der Momentaufnahme. Diese Tabelle wird in der Verteilungsdatenbank und in jeder Abonnementdatenbank verwendet. In der Verteilungsdatenbank enthält sie den Verlauf für alle Mergeveröffentlichungen und Abonnements, die den Verteiler verwenden. In den einzelnen Abonnementdatenbanken enthält sie den Verlauf für Veröffentlichungen, die der Abonnent abonniert hat.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Die ID des Merge-Agent-Auftrags|  
|**agent_id**|**int**|Die ID des Merge-Agents|  
|**Kommentare**|**nvarchar(255)**|Der Meldungstext.|  
|**Fehler-ID**|**int**|Die ID eines Fehlers in der [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md) -Systemtabelle.|  
|**timestamp**|**timestamp**|Die Timestampspalte dieser Tabelle.|  
|**updatable_row**|**bit**|Legen Sie auf **1** Wenn die Verlaufszeile überschrieben werden kann.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
