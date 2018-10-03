---
title: dm_repl_tranhash (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_tranhash
- sys.dm_repl_tranhash_TSQL
- dm_repl_tranhash_TSQL
- dm_repl_tranhash
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_tranhash dynamic management view
ms.assetid: 0cc52338-e805-4ed4-9835-b19bbf72448e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d10d4451071ac476b25fdfef00ab4a48d1c3f63
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736583"
---
# <a name="sysdmrepltranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu Transaktionen zurück, die in einer Transaktionsveröffentlichung repliziert werden.  
  
|column_name|data_type|description|  
|------------------|----------------|-----------------|  
|**buckets**|**bigint**|Die Anzahl der Buckets in der Hashtabelle.|  
|**hashed_trans**|**bigint**|Anzahl der im aktuellen Batch replizierten Transaktionen, für die ein Commit durchgeführt wurde.|  
|**completed_trans**|**bigint**|Anzahl der bisher abgeschlossenen Transaktionen.|  
|**compensated_trans**|**bigint**|Anzahl der Transaktionen, die teilweise Rollbacks enthalten.|  
|**first_begin_lsn**|**Nvarchar(64)**|Erste Protokollfolgenummer (LSN, Log Sequence Number) im aktuellen Batch.|  
|**last_commit_lsn**|**Nvarchar(64)**|LSN des letzten Commits im aktuellen Batch.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung für die Veröffentlichungsdatenbank, die **dm_repl_tranhash**aufruft.  
  
## <a name="remarks"></a>Hinweise  
 Informationen werden nur für replizierte Datenbankobjekte zurückgegeben, die zurzeit in den Replikationsartikelcache geladen sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Replikation verbundene dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
