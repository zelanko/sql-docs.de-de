---
title: MStracer_tokens (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: dc2e7e5b2cf767972ab6531b5f06c2043a3f07fc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68016460"
---
# <a name="mstracer_tokens-transact-sql"></a>MStracer_tokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MStracer_tokens** Tabelle verwaltet einen Datensatz von Überwachungs Token-Datensätzen, die in eine Veröffentlichung eingefügt werden. Diese Tabelle wird in der Verteilungsdatenbank gespeichert. Sie wird von der Replikation für die Leistungsüberwachung verwendet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|Identifiziert einen Überwachungstoken-Datensatz.|  
|**publication_id**|**int**|Identifiziert die Veröffentlichung, in die der Überwachungstoken-Datensatz eingefügt wurde.|  
|**publisher_commit**|**datetime**|Das Datum und die Uhrzeit, zu dem ein Commit für den Überwachungstoken-Datensatz auf dem Verleger ausgeführt wurde.|  
|**distributor_commit**|**datetime**|Das Datum und die Uhrzeit, zu dem ein Commit für den Überwachungstoken-Datensatz auf dem Verteiler ausgeführt wurde.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
