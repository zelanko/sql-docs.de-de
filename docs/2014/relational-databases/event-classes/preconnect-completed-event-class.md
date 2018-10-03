---
title: PreConnect:Completed (Ereignisklasse) | Microsoft-Dokumentation
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
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 16720db613815d5c8cce501c1cee2d5d3cc9b3cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150630"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed (Ereignisklasse)
  Die „PreConnect:Completedevent“-Klasse zeigt an, dass die Ausführung eines LOGON-Triggers oder der Klassifizierungsfunktion der Ressourcenkontrolle zu Ende geht.  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>Datenspalten der PreConnect:Completed-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|216|27|nein|  
|SPID|`int`|Die ID des Serverprozesses, von dem das Ereignis ausgelöst wird.|12|Benutzerkontensteuerung|  
|EventSubClass|`int`|1 für die benutzerdefinierte Klassifizierungsfunktion.|21|Benutzerkontensteuerung|  
|StartTime|`datetime`|Der Zeitpunkt, an dem die benutzerdefinierte Klassifizierungsfunktion beginnt.|14|Benutzerkontensteuerung|  
|EndTime|`datetime`|Der Zeitpunkt, an dem die benutzerdefinierte Klassifizierungsfunktion beginnt.|15|Benutzerkontensteuerung|  
|Duration|`bigint`|Die von der Klassifizierungsfunktion benötigte Zeit (in Mikrosekunden)|13|Benutzerkontensteuerung|  
|ObjectID|`int`|Die ID des benutzerdefinierten Klassifizierungsobjekts.|22|Benutzerkontensteuerung|  
|CPU|`int`|CPU-Verwendung in Millisekunden|18|Benutzerkontensteuerung|  
|Reads|`int`|Die Anzahl der logischen Lesevorgänge|16|Benutzerkontensteuerung|  
|Writes|`int`|Die Anzahl der logischen Schreibvorgänge|17|Benutzerkontensteuerung|  
|GroupID|`int`|Die ID der klassifizierten Arbeitsauslastungsgruppe|66|Benutzerkontensteuerung|  
|Fehler|`int`|Die letzte Fehlernummer, falls die benutzerdefinierte Klassifizierungsfunktion nicht ausgeführt wird|31|Benutzerkontensteuerung|  
|Status|`int`|Der Status des letzten Fehlers|30|Benutzerkontensteuerung|  
|TargetUserName|`sysname`|Der Rückgabewert (Name der Arbeitsauslastungsgruppe) für die benutzerdefinierte Klassifizierungsfunktion, falls das System keine entsprechende aktive Gruppe finden kann. Andernfalls wird diese Spalte auf NULL gesetzt.|39|Benutzerkontensteuerung|  
|ObjectName|`nvarchar(256)`|Der zweiteilige Name der benutzerdefinierten Klassifizierungsfunktion. Beispiel: dbo.classifier.|34|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [PreConnect:Starting-Ereignisklasse](preconnect-starting-event-class.md)   
 [Ressourcenkontrolle](../resource-governor/resource-governor.md)  
  
  
