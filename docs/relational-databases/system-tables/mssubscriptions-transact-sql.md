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
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca4364709462eee9df62baa8193dec9f8ea36241
ms.sourcegitcommit: 722f2ec5a1af334f5bcab8341bc744d16a115273
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74866037"
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **msabonnements** -Tabelle enthält eine Zeile für jeden veröffentlichten Artikel in einem Abonnement, das vom lokalen Verteiler bedient wird. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**wartenden**|Die ID der Verlegerdatenbank.|  
|**publisher_id**|**smallint**|Die ID des Verlegers|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**publication_id**|**wartenden**|Die ID der Veröffentlichung.|  
|**article_id**|**wartenden**|Die ID des Artikels.|  
|**subscriber_id**|**smallint**|Die ID des Abonnenten.|  
|**subscriber_db**|**sysname**|Der Name der Abonnement Datenbank.|  
|**subscription_type**|**wartenden**|Der Typ des Abonnements:<br /><br /> **0** = Push.<br /><br /> **1** = Pull.<br /><br /> **2** = anonym.|  
|**sync_type**|**tinyint**|Typ der Synchronisierung:<br /><br /> **1** = automatisch.<br /><br /> **2** = keine Synchronisierung.|  
|**Stands**|**tinyint**|Status des Abonnements:<br /><br /> **0** = inaktiv.<br /><br /> **1** = abonniert.<br /><br /> **2** = aktiv.|  
|**subscription_seqno**|**varbinary(16)**|Die Sequenznummer der Momentaufnahmetransaktion.|  
|**snapshot_seqno_flag**|**trate**|Gibt die Quelle der Sequenznummer der Momentaufnahme Transaktion an, wobei der Wert **1** bedeutet, dass **subscription_seqno** die Momentaufnahme Sequenznummer ist.|  
|**independent_agent**|**bit**|Zeigt an, ob ein Verteilungs-Agent im Einzelplatzmodus für diese Veröffentlichung vorhanden ist.|  
|**subscription_time**|**DateTime**|Nur interne Verwendung.|  
|**loopback_detection**|**bit**|Gilt für Abonnements, die Teil einer bidirektionalen Transaktionsreplikationstopologie sind. Bestimmt, ob der Verteilungs-Agent Transaktionen des Abonnenten zurück an den Abonnenten sendet:<br /><br /> **1** = sendet nicht zurück.<br /><br /> **0** = sendet zurück.<br /><br />|  
|**agent_id**|**wartenden**|Die ID der Momentaufnahme.|  
|**update_mode**|**tinyint**|Der Typ des Updates.|  
|**publisher_seqno**|**varbinary(16)**|Die Sequenznummer der Transaktion auf dem Verleger für dieses Abonnement.|  
|**ss_cplt_seqno**|**varbinary(16)**|Die Sequenznummer, die den Abschluss der Verarbeitung der gleichzeitigen Momentaufnahme anzeigt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
