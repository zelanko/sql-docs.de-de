---
title: MStracer_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MStracer_history
- MStracer_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_history system table
ms.assetid: 97237a0c-d574-4b17-8a94-1a8730b31d98
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8c9f554d57935921c068ad25cb51991c47cdbd2a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881477"
---
# <a name="mstracer_history-transact-sql"></a>MStracer_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In der **MStracer_history** Tabelle wird ein Datensatz aller Überwachungs Token verwaltet, die auf dem Abonnenten empfangen wurden. Diese Tabelle wird in der Verteilungsdatenbank gespeichert. Sie wird von der Replikation für die Leistungsüberwachung verwendet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**parent_tracer_id**|**int**|Die eindeutige Identifikation eines Überwachungstokens.|  
|**agent_id**|**int**|Identifiziert den Agent, der den Überwachungstokendatensatz behandelt hat.|  
|**subscriber_commit**|**datetime**|Das Datum und die Uhrzeit, zu denen der Commit des Überwachungstokendatensatzes auf dem Abonnenten durchgeführt wurde.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
