---
title: CPU Threshold Exceeded (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7883dff5b548ad0b6903934c4dd8d90be8cf2423
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164685"
---
# <a name="cpu-threshold-exceeded-event-class"></a>CPU Threshold Exceeded (Ereignisklasse)
  Die CPU Threshold Exceeded-Ereignisklasse zeigt an, dass die Ressourcenkontrolle eine Abfrage entdeckt hat, die den für REQUEST_MAX_CPU_TIME_SEC festgelegten CPU-Grenzwert überschritten hat.  
  
> [!NOTE]  
>  Das Erkennungsintervall für dieses Ereignis beträgt fünf Sekunden. Es wird auf jeden Fall ein Ereignis erzeugt, wenn eine Abfrage den festgelegten Grenzwert um mindestens fünf Sekunden überschreitet. Falls jedoch eine Abfrage den festgelegten Grenzwert um weniger als fünf Sekunden überschreitet, kann es sein, dass die Überschreitung je nach Zeitpunkt der Abfrage und dem Zeitpunkt des letzten Erkennungslaufs nicht erkannt wird.  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>Datenspalten der CPU Threshold Exceeded-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|CPU|`int`|CPU-Verwendung in Millisekunden|18|ja|  
|EventClass|`int`|214|27|nein|  
|EventSubClass|`int`|CPU-Grenzwertüberschreitung|21|ja|  
|GroupID|`int`|ID der Gruppe, in der die Überschreitung aufgetreten ist|66|ja|  
|OwnerID|`int`|SPID des Prozesses, der die Überschreitung verursacht hat|58|ja|  
|SPID|`int`|ID des Serverprozesses, von dem das Ereignis ausgelöst wird<br /><br /> Hinweis: Diese SPID kann sich von der tatsächlichen Benutzer-SPID unterscheiden, wenn die CPU-Verwendung von einem Systemthread als Hintergrundaufgabe überprüft wird.|12|ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis ausgelöst wurde|14|ja|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
