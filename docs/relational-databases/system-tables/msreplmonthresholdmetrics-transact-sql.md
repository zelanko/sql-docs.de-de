---
title: MSreplmonthresholdmetrics (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
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
manager: craigg
ms.openlocfilehash: 90d750d05af52b051bfcba4778f4aba7c911753e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777258"
---
# <a name="msreplmonthresholdmetrics-transact-sql"></a>MSreplmonthresholdmetrics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mithilfe der **MSreplmonthresholdmetrics** -Tabelle werden die für die Überwachung der Replikation bereitgestellten metrischen Daten definiert. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|Identifiziert eine Replikationsleistungsmetrik. Einer der folgenden Werte ist möglich.<br /><br /> **1** = expiration<br /><br /> **2** = latency<br /><br /> **4** = mergeexpiration<br /><br /> **5** = mergeslowrunduration<br /><br /> **6** = mergefastrunduration<br /><br /> **7** = mergefastrunspeed<br /><br /> **8** = mergeslowrunspeed|  
|**title**|**sysname**|Der Name der Replikationsleistungsmetrik|  
|**warningbitstatus**|**int**|Der bitweise Bezeichner, der zum Bereitstellen einer Warnung bei einer Schwellenwertverletzung für die folgenden metrischen Daten verwendet wird:<br /><br /> **1** = expiration - Ein Abonnement einer Transaktionsveröffentlichung hat die Aufbewahrungsdauer um mehr als den zulässigen Schwellenwert überschritten (als Prozentwert der Aufbewahrungsdauer).<br /><br /> **2** = latency – Die Zeitdauer der Replikation von Daten von einem Transaktionsverleger auf den Abonnenten überschreitet den Schwellenwert (in Sekunden).<br /><br /> **4** = mergeexpiration – Ein Abonnement einer Mergeveröffentlichung hat die Aufbewahrungsdauer um mehr als den zulässigen Schwellenwert überschritten (als Prozentwert der Aufbewahrungsdauer).<br /><br /> **8** = mergefastrunduration – Die Zeitdauer für die Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert über eine schnelle Netzwerkverbindung (in Sekunden).<br /><br /> **16** = mergeslowrunduration – Die Zeitdauer für die Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert über eine langsame oder DFÜ-Netzwerkverbindung (in Sekunden).<br /><br /> **32** = mergefastrunspeed - Die Übermittlungsrate für Zeilen während der Synchronisierung eines Mergeabonnements konnte die als Schwellenwert festgelegte Mindestrate über eine schnelle Netzwerkverbindung nicht aufrecht erhalten (in Zeilen pro Sekunde).<br /><br /> **64** = mergeslowrunspeed - Die Übermittlungsrate für Zeilen während der Synchronisierung eines Mergeabonnements konnte die als Schwellenwert festgelegte Mindestrate über eine langsame oder DFÜ-Netzwerkverbindung nicht aufrecht erhalten (in Zeilen pro Sekunde).|  
|**alertmessageid**|**int**|Die ID der Fehlermeldung, die angezeigt wird, wenn die Schwellenwert-Warnungsbedingung auftritt|  
|**description**|**nvarchar(3000)**|Die Beschreibung der Replikationsleistungsmetrik|  
|**default_value**|**sql_variant**|Ein Standardwert für die Replikationsleistungsmetrik|  
|**MIN_VALUE**|**sql_variant**|Der Mindestwert für eine gebundene Replikationsleistungsmetrik|  
|**MAX_VALUE**|**sql_variant**|Der Höchstwert für eine gebundene Replikationsleistungsmetrik|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
