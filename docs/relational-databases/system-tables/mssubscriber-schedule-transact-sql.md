---
title: MSsubscriber_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriber_schedule
- MSsubscriber_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_schedule system table
ms.assetid: ff428306-0ef4-49a3-b536-07ccdf6e2196
author: stevestein
ms.author: sstein
ms.openlocfilehash: 04ad122f6fc999aa285513d41e71bfc347dbfb82
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68139798"
---
# <a name="mssubscriber_schedule-transact-sql"></a>MSsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSsubscriber_schedule** Tabelle enthält für jedes Verleger-/abonnementpaar Standard Zeitpläne für Zusammenführung und Transaktions Synchronisierung. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
> [!NOTE]
>  Diese Systemtabelle wurde als veraltet markiert und wird zur Unterstützung früherer Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]beibehalten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Gebers**|**sysname**|Der Name des Verlegers.|  
|**Abonnenten**|**sysname**|Den Namen des Abonnenten.|  
|**agent_type**|**smallint**|Der Agenttyp:<br /><br /> 0 = Verteilungs-Agent<br /><br /> 1 = Merge-Agent|  
|**frequency_type**|**int**|Die Häufigkeit für die Zeitplanung des Verteilungs-Agents:<br /><br /> **1** = einmal.<br /><br /> **2** = bei Bedarf.<br /><br /> **4** = täglich.<br /><br /> **8** = wöchentlich.<br /><br /> **16** = monatlich.<br /><br /> **32** = monatlich in Relation.<br /><br /> **64** = Autostart.<br /><br /> **128** = wiederholt.|  
|**frequency_interval**|**int**|Der Wert, der auf die von **frequency_type**festgelegte Häufigkeit angewendet werden soll.|  
|**frequency_relative_interval**|**int**|Das Datum des Verteilungs-Agents:<br /><br /> **1** = erste.<br /><br /> **2** = Sekunde.<br /><br /> **4** = Dritte.<br /><br /> **8** = Fourth.<br /><br /> **16** = Letzter.|  
|**frequency_recurrence_factor**|**int**|Der von **frequency_type**verwendete Wiederholungs Faktor.|  
|**frequency_subday**|**int**|Häufigkeit der erneuten Planung während des definierten Zeitraumes:<br /><br /> **1** = einmal.<br /><br /> **2** = Sekunde.<br /><br /> **4** = Minute.<br /><br /> **8** = Stunde.|  
|**frequency_subday_interval**|**int**|Das Intervall für die **frequency_subday**.|  
|**active_start_time_of_day**|**int**|Die Tageszeit, zu der der Einsatz des Verteilungs-Agents zum ersten Mal geplant wird (im Format HHMMSS).|  
|**active_end_time_of_day**|**int**|Die Tageszeit, zu der die Planung des Einsatzes des Verteilungs-Agents beendet wird (im Format HHMMSS).|  
|**active_start_date**|**int**|Das Datum, an dem der Einsatz des Verteilungs-Agents zum ersten Mal geplant wird (im Format YYYYMMDD).|  
|**active_end_date**|**int**|Das Datum, an dem die Planung des Einsatzes des Verteilungs-Agents beendet wird (im Format YYYYMMDD).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
