---
title: PreConnect:Starting-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0986e654430a47cc494bf1646c222b4888fc105b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63033512"
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting-Ereignisklasse
  Die PreConnect:Starting-Ereignisklasse zeigt an, dass die Ausführung eines LOGON-Triggers oder der Klassifizierungsfunktion der Ressourcenkontrolle beginnt.  
  
## <a name="preconnectstarting-event-class-data-columns"></a>Datenspalten der PreConnect:Starting-Ereignisklasse  
  
|Datenspaltenname|Datentyp|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|215|27|Nein|  
|SPID|`int`|Die ID des Serverprozesses, von dem das Ereignis ausgelöst wird.|12|Ja|  
|EventSubClass|`int`|1 für die benutzerdefinierte Klassifizierungsfunktion.|21|Ja|  
|StartTime|`datetime`|Der Zeitpunkt, an dem die benutzerdefinierte Klassifizierungsfunktion beginnt.|14|Ja|  
|ObjectID|`int`|Die ID des benutzerdefinierten Klassifizierungsobjekts.|22|Ja|  
|ObjectName|`nvarchar(256)`|Der zweiteilige Name der benutzerdefinierten Klassifizierungsfunktion. Beispiel: dbo.classifier.|34|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [PreConnect: Abgeschlossene Ereignisklasse](preconnect-completed-event-class.md)   
 [Ressourcenkontrolle](../resource-governor/resource-governor.md)  
  
  
