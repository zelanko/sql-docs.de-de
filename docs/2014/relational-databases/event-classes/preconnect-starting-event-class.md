---
title: PreConnect:Starting-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8ee98c099d13c0d77a239c22739704e5d51cc5e4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048760"
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting-Ereignisklasse
  Die PreConnect:Starting-Ereignisklasse zeigt an, dass die Ausführung eines LOGON-Triggers oder der Klassifizierungsfunktion der Ressourcenkontrolle beginnt.  
  
## <a name="preconnectstarting-event-class-data-columns"></a>Datenspalten der PreConnect:Starting-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|215|27|nein|  
|SPID|`int`|Die ID des Serverprozesses, von dem das Ereignis ausgelöst wird.|12|Benutzerkontensteuerung|  
|EventSubClass|`int`|1 für die benutzerdefinierte Klassifizierungsfunktion.|21|Benutzerkontensteuerung|  
|StartTime|`datetime`|Der Zeitpunkt, an dem die benutzerdefinierte Klassifizierungsfunktion beginnt.|14|Benutzerkontensteuerung|  
|ObjectID|`int`|Die ID des benutzerdefinierten Klassifizierungsobjekts.|22|Benutzerkontensteuerung|  
|ObjectName|`nvarchar(256)`|Der zweiteilige Name der benutzerdefinierten Klassifizierungsfunktion. Beispiel: dbo.classifier.|34|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [PreConnect:Completed (Ereignisklasse)](preconnect-completed-event-class.md)   
 [Ressourcenkontrolle](../resource-governor/resource-governor.md)  
  
  
