---
title: Msabonnements (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriptions_TSQL
- MSsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriptions system table
ms.assetid: b7e8301d-d115-41f6-8d4f-e0d25f453b25
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 787217996a491b37bb7b46ec505ac7d374d9aed8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758675"
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Die **msabonnements** -Tabelle enthält eine Zeile für jeden veröffentlichten Artikel in einem Abonnement, das vom lokalen Verteiler bedient wird. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Die ID der Verlegerdatenbank.|  
|**publisher_id**|**smallint**|Die ID des Verlegers|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**publication_id**|**int**|Die ID der Veröffentlichung.|  
|**article_id**|**int**|Die ID des Artikels.|  
|**subscriber_id**|**smallint**|Die ID des Abonnenten.|  
|**subscriber_db**|**sysname**|Der Name der Abonnement Datenbank.|  
|**subscription_type**|**int**|Der Typ des Abonnements:<br /><br /> **0** = Push.<br /><br /> **1** = Pull.<br /><br /> **2** = anonym.|  
|**sync_type**|**tinyint**|Typ der Synchronisierung:<br /><br /> **1** = automatisch.<br /><br /> **2** = keine Synchronisierung.|  
|**status**|**tinyint**|Status des Abonnements:<br /><br /> **0** = inaktiv.<br /><br /> **1** = abonniert.<br /><br /> **2** = aktiv.|  
|**subscription_seqno**|**varbinary(16)**|Die Sequenznummer der Momentaufnahmetransaktion.|  
|**snapshot_seqno_flag**|**bit**|Gibt die Quelle der Sequenznummer der Momentaufnahme Transaktion an, wobei der Wert **1** bedeutet, dass **subscription_seqno** die Momentaufnahme Sequenznummer ist.|  
|**independent_agent**|**bit**|Zeigt an, ob ein Verteilungs-Agent im Einzelplatzmodus für diese Veröffentlichung vorhanden ist.|  
|**subscription_time**|**datetime**|Nur interne Verwendung.|  
|**loopback_detection**|**bit**|Gilt für Abonnements, die Teil einer bidirektionalen Transaktionsreplikationstopologie sind. Bestimmt, ob der Verteilungs-Agent Transaktionen des Abonnenten zurück an den Abonnenten sendet:<br /><br /> **1** = sendet nicht zurück.<br /><br /> **0** = sendet zurück.<br /><br />|  
|**agent_id**|**int**|Die ID der Momentaufnahme.|  
|**update_mode**|**tinyint**|Der Typ des Updates.|  
|**publisher_seqno**|**varbinary(16)**|Die Sequenznummer der Transaktion auf dem Verleger für dieses Abonnement.|  
|**ss_cplt_seqno**|**varbinary(16)**|Die Sequenznummer, die den Abschluss der Verarbeitung der gleichzeitigen Momentaufnahme anzeigt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
