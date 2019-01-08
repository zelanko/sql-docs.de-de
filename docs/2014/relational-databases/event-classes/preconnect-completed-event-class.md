---
title: PreConnect:Completed (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eaad0a80fd77257c6e79e092733d75c0c8df5df5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52755982"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed (Ereignisklasse)
  Die „PreConnect:Completedevent“-Klasse zeigt an, dass die Ausführung eines LOGON-Triggers oder der Klassifizierungsfunktion der Ressourcenkontrolle zu Ende geht.  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>Datenspalten der PreConnect:Completed-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|216|27|Nein|  
|SPID|`int`|Die ID des Serverprozesses, von dem das Ereignis ausgelöst wird.|12|Ja|  
|EventSubClass|`int`|1 für die benutzerdefinierte Klassifizierungsfunktion.|21|Ja|  
|StartTime|`datetime`|Der Zeitpunkt, an dem die benutzerdefinierte Klassifizierungsfunktion beginnt.|14|Ja|  
|EndTime|`datetime`|Der Zeitpunkt, an dem die benutzerdefinierte Klassifizierungsfunktion beginnt.|15|Ja|  
|Duration|`bigint`|Die von der Klassifizierungsfunktion benötigte Zeit (in Mikrosekunden)|13|Ja|  
|ObjectID|`int`|Die ID des benutzerdefinierten Klassifizierungsobjekts.|22|Ja|  
|CPU|`int`|CPU-Verwendung in Millisekunden|18|Ja|  
|Reads|`int`|Die Anzahl der logischen Lesevorgänge|16|Ja|  
|Writes|`int`|Die Anzahl der logischen Schreibvorgänge|17|Ja|  
|GroupID|`int`|Die ID der klassifizierten Arbeitsauslastungsgruppe|66|Ja|  
|Fehler|`int`|Die letzte Fehlernummer, falls die benutzerdefinierte Klassifizierungsfunktion nicht ausgeführt wird|31|Ja|  
|Status|`int`|Der Status des letzten Fehlers|30|Ja|  
|TargetUserName|`sysname`|Der Rückgabewert (Name der Arbeitsauslastungsgruppe) für die benutzerdefinierte Klassifizierungsfunktion, falls das System keine entsprechende aktive Gruppe finden kann. Andernfalls wird diese Spalte auf NULL gesetzt.|39|Ja|  
|ObjectName|`nvarchar(256)`|Der zweiteilige Name der benutzerdefinierten Klassifizierungsfunktion. Beispiel: dbo.classifier.|34|Ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [PreConnect:Starting-Ereignisklasse](preconnect-starting-event-class.md)   
 [Ressourcenkontrolle](../resource-governor/resource-governor.md)  
  
  
