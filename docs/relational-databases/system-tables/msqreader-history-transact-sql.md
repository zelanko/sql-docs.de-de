---
title: MSqreader_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSqreader_history
- MSqreader_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSqreader_history system table
ms.assetid: c5c91d39-513c-4a77-870b-c8ef74a1cd6b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f21873e8db662bc77bd1acbb5d48c6af49aba404
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032531"
---
# <a name="msqreaderhistory-transact-sql"></a>MSqreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSqreader_history** -Tabelle enthält Verlaufszeilen für den Warteschlangenlese-Agents mit dem lokalen Verteiler verknüpft ist. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Die ID des Warteschlangenlese-Agents.|  
|**publication_id**|**int**|Die ID der Veröffentlichung.|  
|**runstatus**|**int**|Ausführungsstatus der Momentaufnahme:<br /><br /> **1** = Start.<br /><br /> **2** = erfolgreich ausgeführt werden.<br /><br /> **3** = wird ausgeführt.<br /><br /> **4** = im Leerlauf.<br /><br /> **5** = wiederholen.<br /><br /> **6** = Fehler.|  
|**start_time**|**datetime**|Datum und Uhrzeit des Starts der Agentsitzung.|  
|**time**|**datetime**|Datum und Uhrzeit der zuletzt protokollierten Meldung.|  
|**duration**|**int**|Während der protokollierten Sitzungsaktivität verstrichene Zeit in Sekunden.|  
|**Kommentare**|**nvarchar(255)**|Beschreibender Text.|  
|**transaction_id**|**nvarchar(40)**|Mit der Meldung gespeicherte Transaktions-ID (sofern vorhanden).|  
|**transaction_status**|**int**|Status der Transaktion.|  
|**transactions_processed**|**int**|Kumulierte Anzahl der in der Sitzung verarbeiteten Transaktionen.|  
|**commands_processed**|**int**|Kumulierte Anzahl der in der Sitzung verarbeiteten Befehle.|  
|**delivery_rate**|**float(53)**|Die durchschnittliche Anzahl der pro Sekunde übermittelten Befehle.|  
|**transaction_rate**|**float(53)**|Rate der verarbeiteten Transaktionen.|  
|**subscriber**|**sysname**|Den Namen des Abonnenten.|  
|**subscriberdb**|**sysname**|Der Name der Abonnementdatenbank.|  
|**error_id**|**int**|Wenn Sie nicht 0 (null), der Wert gibt eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlermeldung angezeigt.|  
|**timestamp**|**timestamp**|Timestampspalte der Tabelle.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
