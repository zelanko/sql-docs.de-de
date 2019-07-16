---
title: MSreplmonthresholdmetrics (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- msreplmonthresholdmetrics_TSQL
- msreplmonthresholdmetrics
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplmonthresholdmetrics system table
ms.assetid: 0cc9b40a-36ce-485b-9bc2-d4abd5aa6727
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3e8b9c2443a6fa74e113dc1a3f25880ac753dc0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079939"
---
# <a name="msreplmonthresholdmetrics-transact-sql"></a>MSreplmonthresholdmetrics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mithilfe der **MSreplmonthresholdmetrics** -Tabelle werden die für die Überwachung der Replikation bereitgestellten metrischen Daten definiert. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|Identifiziert eine Replikationsleistungsmetrik. Einer der folgenden Werte ist möglich.<br /><br /> **1** = expiration<br /><br /> **2** = latency<br /><br /> **4** = mergeexpiration<br /><br /> **5** = mergeslowrunduration<br /><br /> **6** = mergefastrunduration<br /><br /> **7** = mergefastrunspeed<br /><br /> **8** = mergeslowrunspeed|  
|**title**|**sysname**|Der Name der Replikationsleistungsmetrik|  
|**warningbitstatus**|**int**|Der bitweise Bezeichner, der zum Bereitstellen einer Warnung bei einer Schwellenwertverletzung für die folgenden metrischen Daten verwendet wird:<br /><br /> **1** = Expiration - ein Abonnement für eine transaktionsveröffentlichung hat die Beibehaltungsdauer um mehr als den zulässigen Schwellenwert überschritten, als Prozentwert der Beibehaltungsdauer.<br /><br /> **2** = Latency - die Zeitdauer für die Replikation von Daten von einem Transaktionsverleger auf den Abonnenten überschreitet den Schwellenwert in Sekunden.<br /><br /> **4** = Mergeexpiration - ein Abonnement für eine Mergeveröffentlichung hat die Beibehaltungsdauer um mehr als den zulässigen Schwellenwert überschritten, als Prozentwert der Beibehaltungsdauer.<br /><br /> **8** = Mergefastrunduration - die Zeit zum Abschließen der Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert in Sekunden an, über eine schnelle Netzwerkverbindung.<br /><br /> **16** = Mergeslowrunduration – die Zeit zum Abschließen der Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert in Sekunden an, über eine langsame oder DFÜ Netzwerkverbindung.<br /><br /> **32** = Mergefastrunspeed - die Übermittlungsrate für Zeilen während der Synchronisierung eines Mergeabonnements konnte die Rate Schwellenwert in Zeilen pro Sekunde, über eine schnelle Netzwerkverbindung zu verwalten.<br /><br /> **64** = Mergeslowrunspeed - die Übermittlungsrate für Zeilen während der Synchronisierung eines Mergeabonnements konnte die Rate Schwellenwert in Zeilen pro Sekunde, über eine langsame oder DFÜ Netzwerkverbindung zu verwalten.|  
|**alertmessageid**|**int**|Die ID der Fehlermeldung, die angezeigt wird, wenn die Schwellenwert-Warnungsbedingung auftritt|  
|**description**|**nvarchar(3000)**|Die Beschreibung der Replikationsleistungsmetrik|  
|**default_value**|**sql_variant**|Ein Standardwert für die Replikationsleistungsmetrik|  
|**MIN_VALUE**|**sql_variant**|Der Mindestwert für eine gebundene Replikationsleistungsmetrik|  
|**MAX_VALUE**|**sql_variant**|Der Höchstwert für eine gebundene Replikationsleistungsmetrik|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
