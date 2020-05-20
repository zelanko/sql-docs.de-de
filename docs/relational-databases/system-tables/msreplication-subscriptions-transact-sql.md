---
title: MSreplication_subscriptions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_subscriptions
- MSreplication_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_subscriptions system table
ms.assetid: fd0c5843-4e9b-4448-8bfb-0a4067d1d8d1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 37114a42cd7e9c64872ff42848bb916b21c1d941
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82812364"
---
# <a name="msreplication_subscriptions-transact-sql"></a>MSreplication_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSreplication_subscriptions** Tabelle enthält eine Zeile mit Replikations Informationen für jede Verteilungs-Agent, die die lokale Abonnenten Datenbank bedient. Diese Tabelle wird in der Abonnement Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**ung**|**sysname**|Der Name der Veröffentlichung.|  
|**independent_agent**|**bit**|Zeigt an, ob ein Verteilungs-Agent im Einzelplatzmodus für diese Veröffentlichung vorhanden ist.|  
|**subscription_type**|**int**|Der Typ des Abonnements:<br /><br /> 0 = Push.<br /><br /> 1 = Pull.<br /><br /> 2 = Anonym.|  
|**distribution_agent**|**sysname**|Der Name des Verteilungs-Agents.|  
|**Time**|**smalldatetime**|Der Zeitpunkt des letzten Updates durch den Verteilungs-Agent.|  
|**Beschreibung**|**nvarchar(255)**|Die Beschreibung des Abonnements.|  
|**transaction_timestamp**|**varbinary(16)**|Nur intern verwendet.|  
|**update_mode**|**tinyint**|Der Typ des Updates.|  
|**agent_id**|**Binary (16)**|Die ID der Momentaufnahme.|  
|**subscription_guid**|**Binary (16)**|Der globale Bezeichner für die Version des Abonnements für die Veröffentlichung.|  
|**subid**|**Binary (16)**|Der globale Bezeichner für ein anonymes Abonnement.|  
|**immediate_sync**|**bit**|Zeigt an, ob bei jeder Ausführung des Momentaufnahme-Agents Synchronisierungsdateien erstellt oder neu erstellt werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
