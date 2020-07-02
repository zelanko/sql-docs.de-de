---
title: MSsubscription_agents (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_agents
- MSsubscription_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_agents system table
ms.assetid: 86ad5891-0bef-4963-9381-7d5b45245a0c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 740610a9fa20d3c47472f3737548a4c22fe20a19
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757778"
---
# <a name="mssubscription_agents-transact-sql"></a>MSsubscription_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Die **MSsubscription_agents** Tabelle wird von Verteilungs-Agent und Triggern aktualisierbarer Abonnements verwendet, um Abonnement Eigenschaften zu verfolgen. Diese Tabelle wird in der Abonnement Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Die ID der Zeile.|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Veröffentlichungs Datenbank.|  
|**ung**|**sysname**|Der Name der Veröffentlichung.|  
|**subscription_type**|**int**|Der Abonnementtyp:<br /><br /> 0 = Push.<br /><br /> 1 = Pullabonnement.<br /><br /> 2 = Anonymes Pullabonnement.|  
|**queue_id**|**sysname**|Die ID der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Nachrichten Warteschlange auf dem Verleger. *queue_id* ist für SQL-basiertes verzögertes Update über eine Warteschlange auf **SQL** festgelegt.|  
|**update_mode**|**tinyint**|Typ des Aktualisierens:<br /><br /> **0** = schreibgeschützt.<br /><br /> **1** = sofortiges Update.<br /><br /> **2** = verzögertes Update über Message Queuing.<br /><br /> **3** = sofortiges Update mit verzögertem Update über eine Warteschlange als Failover mit Message Queuing.<br /><br /> **4** = verzögertes Update über eine Warteschlange SQL Server Warteschlange.<br /><br /> **5** = sofortiges Update mit verzögertem Update von verzögertem Update mithilfe SQL Server Warteschlange.|  
|**failover_mode**|**bit**|Wenn für das Update ein Failovertyp angegeben war, ist dies der gewählte Failovertyp:<br /><br /> **0** = sofortiges Update wird verwendet. Failover ist nicht aktiviert.<br /><br /> **1** = verzögertes Update in der Warteschlange wird verwendet. Failover ist aktiviert. Die Warteschlange, die für das Failover verwendet wird, wird im *update_mode* Wert angegeben.|  
|**SPID**|**int**|Die Systemprozess-ID der Verbindung, die von dem Verteilungs-Agent verwendet wird, der derzeit ausgeführt wird oder gerade ausgeführt wurde.|  
|**login_time**|**datetime**|Das Datum und die Uhrzeit der Verbindung des Verteilungs-Agents, der derzeit ausgeführt wird oder gerade ausgeführt wurde.|  
|**allow_subscription_copy**|**bit**|Gibt an, ob die Abonnementdatenbank kopiert werden darf oder nicht.|  
|**attach_state**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**attach_version**|**Binary (16)**|Der eindeutige Bezeichner, der die Version eines angefügten Abonnements darstellt.|  
|**last_sync_status**|**int**|Der letzte Ausführungsstatus des Verteilungs-Agents, der derzeit ausgeführt wird oder gerade ausgeführt wurde. Der Status kann Folgendes sein:<br /><br /> **1** = gestartet.<br /><br /> **2** = erfolgreich.<br /><br /> **3** = wird ausgeführt.<br /><br /> **4** = im Leerlauf.<br /><br /> **5** = Wiederholungsversuch.<br /><br /> **6** = Fehler.|  
|**last_sync_summary**|**sysname**|Die letzte Meldung des Verteilungs-Agents, der derzeit ausgeführt wird oder gerade ausgeführt wurde. Der Status kann Folgendes sein:<br /><br /> **Anfingen.**<br /><br /> **Erfolgreich.**<br /><br /> **In Bearbeitung.**<br /><br /> **Gesch.**<br /><br /> **Wiederholen Sie.**<br /><br /> **UN.**|  
|**last_sync_time**|**datetime**|Das Datum und die Uhrzeit der Aktualisierung der Spalten *last_sync_summary* und *last_sync_status* . Verteilungs-Agents für Pull- oder anonyme Abonnements, die als Aufträge des SQL Server-Agent-Diensts ausgeführt werden, aktualisieren diese Spalten nicht. Die Verlaufsinformationen werden in diesem Fall stattdessen in der Auftragsverlaufstabelle protokolliert.|  
|**queue_server**|**sysname**|Nur interne Verwendung.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)  
  
  
