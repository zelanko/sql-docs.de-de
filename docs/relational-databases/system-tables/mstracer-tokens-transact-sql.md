---
title: MStracer_tokens (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MStracer_tokens_TSQL
- MStracer_tokens
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_tokens system table
ms.assetid: b273aa48-8188-4213-8e2c-311543c3236f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 55140e134876870179c0a13208e85ee55414ca8f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628934"
---
# <a name="mstracertokens-transact-sql"></a>MStracer_tokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MStracer_tokens** -Tabelle unterhält eine Aufzeichnung der Überwachungstoken-Datensätze in einer Veröffentlichung eingefügt. Diese Tabelle wird in der Verteilungsdatenbank gespeichert. Sie wird von der Replikation für die Leistungsüberwachung verwendet.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|Identifiziert einen Überwachungstoken-Datensatz.|  
|**publication_id**|**int**|Identifiziert die Veröffentlichung, in die der Überwachungstoken-Datensatz eingefügt wurde.|  
|**publisher_commit**|**datetime**|Das Datum und die Uhrzeit, zu dem ein Commit für den Überwachungstoken-Datensatz auf dem Verleger ausgeführt wurde.|  
|**distributor_commit**|**datetime**|Das Datum und die Uhrzeit, zu dem ein Commit für den Überwachungstoken-Datensatz auf dem Verteiler ausgeführt wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
