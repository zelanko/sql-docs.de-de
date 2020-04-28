---
title: Ihextendedabonptionview (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHextendedSubscriptionView_TSQL
- IHextendedSubscriptionView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedSubscriptionView view
ms.assetid: 124756a4-463a-4a81-bf5b-de7e8ffc7a62
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f080f5defd5143d3822e86eeeb3c7242b51d08d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029586"
---
# <a name="ihextendedsubscriptionview-transact-sql"></a>IHextendedSubscriptionView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **ihextendedabonptionview** -Sicht macht Informationen zu Abonnements für eine nicht SQL Server Veröffentlichung verfügbar. Diese Sicht wird in der **Verteilungs** Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|Der eindeutige Bezeichner für einen Artikel.|  
|**dest_db**|**sysname**|Der Name der Zieldatenbank.|  
|**srvid**|**smallint**|Der eindeutige Bezeichner für einen Abonnenten.|  
|**login_name**|**sysname**|Der zum Herstellen einer Verbindung mit einem Abonnenten verwendete Anmeldename.|  
|**distribution_jobid**|**binary**|Identifiziert den Auftrag des Verteilungs-Agents.|  
|**publisher_database_id**|**int**|Identifiziert die Veröffentlichungsdatenbank.|  
|**subscription_type**|**int**|Der Typ des Abonnements:<br /><br /> **0** = Push-der Verteilungs-Agent wird auf dem Abonnenten ausgeführt.<br /><br /> **1** = Pull-der Verteilungs-Agent wird auf dem Verteiler ausgeführt.|  
|**sync_type**|**tinyint**|Der Typ der Erstsynchronisierung:<br /><br /> **1** = automatisch<br /><br /> **2** = keine|  
|**status**|**tinyint**|Status des Abonnements:<br /><br /> **0** = inaktiv<br /><br /> **1** = abonniert<br /><br /> **2** = aktiv|  
|**snapshot_seqno_flag**|**bit**|Gibt an, ob eine Momentaufnahmesequenznummer verwendet wird.|  
|**independent_agent**|**bit**|Gibt an, ob eine eigenständige Verteilungs-Agent für diese Veröffentlichung vorhanden ist.<br /><br /> **0** = die Veröffentlichung verwendet einen freigegebenen Verteilungs-Agent, und jedes Paar aus Verleger Datenbank und Abonnenten Datenbank verfügt über einen einzelnen freigegebenen Agent.<br /><br /> **1** = für diese Veröffentlichung ist ein eigenständiger Verteilungs-Agent vorhanden.|  
|**subscription_time**|**datetime**|Nur interne Verwendung.|  
|**loopback_detection**|**bit**|Gilt für Abonnements, die Teil einer bidirektionalen Transaktionsreplikationstopologie sind. Bestimmt, ob der Verteilungs-Agent Transaktionen des Abonnenten zurück an den Abonnenten sendet:<br /><br /> **1** = sendet nicht zurück.<br /><br /> **0** = sendet zurück.|  
|**agent_id**|**int**|Der eindeutige Bezeichner des Verteilungs-Agents.|  
|**update_mode**|**tinyint**|Gibt den Typ des Updatemodus an, der wie folgt lauten kann:<br /><br /> **0** = schreibgeschützt.<br /><br /> **1** = sofortiges Update.<br /><br /> **2** = verzögertes Update über Message Queuing.<br /><br /> **3** = sofortiges Update mit verzögertem Update über eine Warteschlange als Failover mit Message Queuing.<br /><br /> **4** = verzögertes Update über eine Warteschlange SQL Server Warteschlange.<br /><br /> **5** = sofortiges Update mit verzögertem Update von verzögertem Update mithilfe SQL Server Warteschlange.|  
|**publisher_seqno**|**varbinary(16)**|Die Sequenznummer der Transaktion auf dem Verleger für dieses Abonnement.|  
|**ss_cplt_seqno**|**varbinary(16)**|Die Sequenznummer, die den Abschluss der Verarbeitung der gleichzeitigen Momentaufnahme anzeigt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Replikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
