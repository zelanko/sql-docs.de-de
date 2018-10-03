---
title: MSpublications (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSpublications
- MSpublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublications system table
ms.assetid: 7a0b3457-7265-4f24-a255-7f055d908f20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c576bd5ce66661eb601984638c0608ae2eef8f9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732615"
---
# <a name="mspublications-transact-sql"></a>MSpublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSpublications** -Tabelle enthält eine Zeile für jede Veröffentlichung, die von einem Verleger repliziert wird. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Die ID des Verlegers|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**Veröffentlichung**|**sysname**|Der Name der Veröffentlichung.|  
|**publication_id**|**int**|Die ID der Veröffentlichung.|  
|**publication_type**|**int**|Der Typ der Veröffentlichung:<br /><br /> **0** = transaktionsveröffentlichung.<br /><br /> **1** = Momentaufnahme.<br /><br /> **2** = Merge.|  
|**thirdparty_flag**|**bit**|Gibt an, ob eine Veröffentlichung ist eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank:<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **1** = andere Datenquelle als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**independent_agent**|**bit**|Zeigt an, ob ein Verteilungs-Agent im Einzelplatzmodus für diese Veröffentlichung vorhanden ist.|  
|**immediate_sync**|**bit**|Zeigt an, ob bei jeder Ausführung des Momentaufnahme-Agents Synchronisierungsdateien erstellt oder neu erstellt werden.|  
|**allow_push**|**bit**|Zeigt an, ob für die angegebene Veröffentlichung Pushabonnements erstellt werden können.|  
|**allow_pull**|**bit**|Zeigt an, ob für die angegebene Veröffentlichung Pullabonnements erstellt werden können.|  
|**allow_anonymous**|**bit**|Zeigt an, ob für die angegebene Veröffentlichung anonyme Abonnements erstellt werden können.|  
|**description**|**nvarchar(255)**|Die Beschreibung der Veröffentlichung.|  
|**$vendor_name**|**nvarchar(100)**|Der Name des Herstellers, wenn der Verleger keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank ist.|  
|**Beibehaltungsdauer**|**int**|Die Beibehaltungsdauer der Veröffentlichung (in Stunden).|  
|**sync_method**|**int**|Synchronisierungsmethode:<br /><br /> **0** = Native (erzeugt im einheitlichen Modus massenkopierausgabe aller Tabellen).<br /><br /> **1** = Character (erzeugt eine Massenkopierprogramm-Ausgabe aller Tabellen kopieren).<br /><br /> **3** = Concurrent (erzeugt im einheitlichen Modus massenkopierausgabe aller Tabellen sperrt jedoch nicht in der Tabelle während der Momentaufnahme).<br /><br /> **4** = Concurrent_c (erzeugt eine im Zeichenmodus massenkopierausgabe aller Tabellen sperrt jedoch nicht in der Tabelle während der Momentaufnahme)<br /><br /> Die Werte **3** und **4** stehen für Transaktions- und Mergereplikation, aber nicht für die momentaufnahmereplikation.|  
|**allow_subscription_copy**|**bit**|Aktiviert oder deaktiviert die Option zum Kopieren der Abonnementdatenbanken, die diese Veröffentlichung abonniert haben. **0** bedeutet, dass das Kopieren deaktiviert ist, und **1** bedeutet, dass es aktiviert ist.|  
|**thirdparty_options**|**int**|Gibt an, ob die Anzeige einer Veröffentlichung im Ordner "Replikation" in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] unterdrückt wird:<br /><br /> **0** = heterogene Veröffentlichung im Ordner Replikation angezeigt [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].<br /><br /> **1** = unterdrückt die Anzeige im Ordner "Replikation" in heterogene Veröffentlichung [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
|**allow_queued_tran**|**bit**|Gibt an, ob die Veröffentlichung verzögerte Updates über eine Warteschlange zulässt:<br /><br /> **0 =** Veröffentlichung ist nicht in der Warteschlange.<br /><br /> **1** = Veröffentlichung mit Warteschlange.|  
|**options**|**int**|Für diese Version sind keine Informationen verfügbar.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
