---
title: MSmerge_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4bde1a345f03eb93dbc02b630df6889efe9b8568
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737578"
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
  
  
