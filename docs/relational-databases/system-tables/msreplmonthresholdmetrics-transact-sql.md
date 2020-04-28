---
title: Msreplmon-oldmetrics (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68079939"
---
# <a name="msreplmonthresholdmetrics-transact-sql"></a>MSreplmonthresholdmetrics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mithilfe der **MSreplmonthresholdmetrics** -Tabelle werden die für die Überwachung der Replikation bereitgestellten metrischen Daten definiert. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|Identifiziert eine Replikationsleistungsmetrik. Einer der folgenden Werte ist möglich.<br /><br /> **1** = Ablauf<br /><br /> **2** = Latenz<br /><br /> **4** = mergeablauf<br /><br /> **5** = mergeslowrunduration<br /><br /> **6** = mergefastrunduration<br /><br /> **7** = mergefastrunspeed<br /><br /> **8** = mergeslowrunspeed|  
|**title**|**sysname**|Der Name der Replikationsleistungsmetrik|  
|**warningbitstatus**|**int**|Der bitweise Bezeichner, der zum Bereitstellen einer Warnung bei einer Schwellenwertverletzung für die folgenden metrischen Daten verwendet wird:<br /><br /> **1** = Ablauf: ein Abonnement für eine Transaktions Veröffentlichung hat die Beibehaltungs Dauer um mehr als den zulässigen Schwellenwert überschritten (als Prozentsatz der Beibehaltungs Dauer).<br /><br /> **2** = Latenz: die Zeit, die zum Replizieren von Daten von einem transaktionalen Verleger auf den Abonnenten benötigt wird, überschreitet den Schwellenwert (in Sekunden).<br /><br /> **4** = mergeablauf: ein Abonnement für eine Mergeveröffentlichung hat die Beibehaltungs Dauer um mehr als den zulässigen Schwellenwert überschritten, als Prozentsatz der Beibehaltungs Dauer.<br /><br /> **8** = mergefastrauunduration: die Zeit, die zum Abschließen der Synchronisierung eines Mergeabonnements benötigt wird, überschreitet den Schwellenwert über eine schnelle Netzwerkverbindung (in Sekunden).<br /><br /> **16** = mergeslowrunduration: die Zeit für die Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert über eine langsame oder DFÜ-Netzwerkverbindung (in Sekunden).<br /><br /> **32** = mergefastrauunspeed-die Übermittlungs Rate für Zeilen während der Synchronisierung eines Mergeabonnements konnte den Schwellenwert (in Zeilen pro Sekunde) über eine schnelle Netzwerkverbindung nicht aufrechterhalten.<br /><br /> **64** = mergeslowrunspeed-die Übermittlungs Rate für Zeilen während der Synchronisierung eines Mergeabonnements konnte den Schwellenwert (in Zeilen pro Sekunde) über eine langsame oder DFÜ-Netzwerkverbindung nicht aufrechterhalten.|  
|**alertmessageid**|**int**|Die ID der Fehlermeldung, die angezeigt wird, wenn die Schwellenwert-Warnungsbedingung auftritt|  
|**Beschreibung**|**nvarchar (3000)**|Die Beschreibung der Replikationsleistungsmetrik|  
|**default_value**|**sql_variant**|Ein Standardwert für die Replikationsleistungsmetrik|  
|**min_value**|**sql_variant**|Der Mindestwert für eine gebundene Replikationsleistungsmetrik|  
|**max_value**|**sql_variant**|Der Höchstwert für eine gebundene Replikationsleistungsmetrik|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
