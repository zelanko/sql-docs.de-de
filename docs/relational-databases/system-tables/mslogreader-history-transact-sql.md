---
title: MSlogreader_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSlogreader_history_TSQL
- MSlogreader_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_history system table
ms.assetid: 2e399fa1-3591-4c1c-96b7-7964fe82c7c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fbd2240bdeba50d8ae41bce8d3a8d58b28de036
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67907293"
---
# <a name="mslogreaderhistory-transact-sql"></a>MSlogreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSlogreader_history** -Tabelle enthält Verlaufszeilen für den Protokolllese-Agents mit dem lokalen Verteiler verknüpft ist. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Die ID des Protokolllese-Agents.|  
|**runstatus**|**int**|Der Ausführungsstatus:<br /><br /> 1 = Start.<br /><br /> 2 = Erfolgreich<br /><br /> 3 = Wird ausgeführt<br /><br /> 4 = Im Leerlauf<br /><br /> 5 = Wiederholung<br /><br /> 6 = Fehler|  
|**start_time**|**datetime**|Der Zeitpunkt, zu dem mit der Ausführung des Auftrags begonnen wird.|  
|**time**|**datetime**|Der Zeitpunkt der Protokollierung der Meldung.|  
|**duration**|**int**|Die Dauer der Meldungssitzung in Sekunden.|  
|**Kommentare**|**nvarchar(255)**|Der Meldungstext.|  
|**xact_seqno**|**varbinary(16)**|Die Sequenznummer der zuletzt verarbeiteten Transaktion.|  
|**delivery_time**|**int**|Die Zeit erste Transaktion übermittelt wird.|  
|**delivered_transactions**|**int**|Die Gesamtzahl der in der Sitzung übermittelten Transaktionen.|  
|**delivered_commands**|**int**|Die Gesamtzahl der in der Sitzung übermittelten Befehle.|  
|**average_commands**|**int**|Die durchschnittliche Anzahl der in der Sitzung übermittelten Befehle.|  
|**delivery_rate**|**float**|Die durchschnittliche Anzahl der pro Sekunde übermittelten Befehle.|  
|**delivery_latency**|**int**|Die Latenzzeit zwischen dem Eintritt des Befehls in die veröffentlichte Datenbank und seinem Eintritt in die Verteilungsdatenbank. In Millisekunden|  
|**error_id**|**int**|Die ID des Fehlers in der **MSrepl_error** -Systemtabelle.|  
|**timestamp**|**timestamp**|Die Timestampspalte dieser Tabelle.|  
|**updateable_row**|**bit**|Legen Sie auf **1** Wenn die Verlaufszeile überschrieben werden kann.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
