---
title: MSrepl_backup_lsns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_backup_lsns_TSQL
- MSrepl_backup_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_backup_Isns system table
ms.assetid: de06c349-82a8-48c6-b602-b5d6938514f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a1f22edf81e5e5e8ac7e2d9b44ce26e6b1f8bad2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68032516"
---
# <a name="msrepl_backup_lsns-transact-sql"></a>MSrepl_backup_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSrepl_backup_lsns** Tabelle enthält Transaktionsprotokoll-Sequenznummern (Log Sequence Number, LSN) zur Unterstützung der Option ' sync with Backup ' der Verteilungs Datenbank. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Die ID der Verlegerdatenbank.|  
|**valid_xact_id**|**varbinary(16)**|Die ID der Transaktion, die an den Verleger gesendet werden soll, um den Protokollkürzungspunkt zu markieren. Wird nur verwendet, wenn sich die Verteilungsdatenbank im Modus 'sync with backup' befindet. Enthält die ID der zuletzt in der Verteilungsdatenbank replizierten Transaktion, die gesichert wurde. Sie wird an den Verleger gesendet, damit der Protokollkürzungspunkt vom Protokollleser markiert werden kann.|  
|**valid_xact_seqno**|**varbinary(16)**|Die Sequenznummer der Transaktion, die an den Verleger gesendet werden soll, um den Protokollkürzungspunkt zu markieren. Sie wird nur verwendet, wenn sich die Verteilungsdatenbank im Modus 'sync with backup' befindet. Dies ist die Protokollfolgenummer (LSN, Log Sequence Number) der zuletzt in der Verteilungsdatenbank replizierten Transaktion, die gesichert wurde. Sie wird an den Verleger gesendet, damit der Protokollkürzungspunkt vom Protokollleser markiert werden kann.|  
|**next_xact_id**|**varbinary(16)**|Die temporäre Protokollfolgenummer (LSN, Log Sequence Number), die von Sicherungsvorgängen verwendet wird.|  
|**nextx_xact_seqno**|**varbinary(16)**|Die temporäre Protokollfolgenummer (LSN, Log Sequence Number), die von Sicherungsvorgängen verwendet wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
