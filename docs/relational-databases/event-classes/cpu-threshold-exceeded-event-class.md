---
title: CPU Threshold Exceeded (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d74d1907b0f96275658c716a7a08061f0eec8995
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67999564"
---
# <a name="cpu-threshold-exceeded-event-class"></a>CPU Threshold Exceeded (Ereignisklasse)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die CPU Threshold Exceeded-Ereignisklasse zeigt an, dass die Ressourcenkontrolle eine Abfrage entdeckt hat, die den für REQUEST_MAX_CPU_TIME_SEC festgelegten CPU-Grenzwert überschritten hat.  
  
> [!NOTE]  
>  Das Erkennungsintervall für dieses Ereignis beträgt fünf Sekunden. Es wird auf jeden Fall ein Ereignis erzeugt, wenn eine Abfrage den festgelegten Grenzwert um mindestens fünf Sekunden überschreitet. Falls jedoch eine Abfrage den festgelegten Grenzwert um weniger als fünf Sekunden überschreitet, kann es sein, dass die Überschreitung je nach Zeitpunkt der Abfrage und dem Zeitpunkt des letzten Erkennungslaufs nicht erkannt wird.  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>Datenspalten der CPU Threshold Exceeded-Ereignisklasse  
  
|Datenspaltenname|Datentyp|und Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|CPU|**int**|CPU-Verwendung in Millisekunden|18|Ja|  
|EventClass|**int**|214|27|Nein|  
|EventSubClass|**int**|CPU-Grenzwertüberschreitung|21|Ja|  
|GroupID|**int**|ID der Gruppe, in der die Überschreitung aufgetreten ist|66|Ja|  
|OwnerID|**int**|SPID des Prozesses, der die Überschreitung verursacht hat|58|Ja|  
|SPID|**int**|ID des Serverprozesses, von dem das Ereignis ausgelöst wird<br /><br /> Hinweis: Diese SPID kann sich von der tatsächlichen Benutzer-SPID unterscheiden, wenn die CPU-Verwendung von einem Systemthread als Hintergrundaufgabe überprüft wird.|12|Ja|  
|StartTime|**datetime**|Zeitpunkt, zu dem das Ereignis ausgelöst wurde|14|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
