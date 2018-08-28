---
title: PreConnect:Completed (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 905e4ce4264be5288d04484c109edfc63c821c86
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43078223"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed (Ereignisklasse)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die „PreConnect:Completedevent“-Klasse zeigt an, dass die Ausführung eines LOGON-Triggers oder der Klassifizierungsfunktion der Ressourcenkontrolle zu Ende geht.  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>Datenspalten der PreConnect:Completed-Ereignisklasse  
  
|Datenspaltenname|Datentyp|und Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|216|27|nein|  
|SPID|**int**|Die ID des Serverprozesses, von dem das Ereignis ausgelöst wird.|12|Benutzerkontensteuerung|  
|EventSubClass|**int**|1 für die benutzerdefinierte Klassifizierungsfunktion.|21|Benutzerkontensteuerung|  
|StartTime|**datetime**|Der Zeitpunkt, an dem die benutzerdefinierte Klassifizierungsfunktion beginnt.|14|Benutzerkontensteuerung|  
|EndTime|**datetime**|Der Zeitpunkt, an dem die benutzerdefinierte Klassifizierungsfunktion beginnt.|15|Benutzerkontensteuerung|  
|Duration|**bigint**|Die von der Klassifizierungsfunktion benötigte Zeit (in Mikrosekunden)|13|Benutzerkontensteuerung|  
|ObjectID|**int**|Die ID des benutzerdefinierten Klassifizierungsobjekts.|22|Benutzerkontensteuerung|  
|CPU|**int**|CPU-Verwendung in Millisekunden|18|Benutzerkontensteuerung|  
|Reads|**int**|Die Anzahl der logischen Lesevorgänge|16|Benutzerkontensteuerung|  
|Writes|**int**|Die Anzahl der logischen Schreibvorgänge|17|Benutzerkontensteuerung|  
|GroupID|**int**|Die ID der klassifizierten Arbeitsauslastungsgruppe|66|Benutzerkontensteuerung|  
|Fehler|**int**|Die letzte Fehlernummer, falls die benutzerdefinierte Klassifizierungsfunktion nicht ausgeführt wird|31|Benutzerkontensteuerung|  
|Status|**int**|Der Status des letzten Fehlers|30|Benutzerkontensteuerung|  
|TargetUserName|**sysname**|Der Rückgabewert (Name der Arbeitsauslastungsgruppe) für die benutzerdefinierte Klassifizierungsfunktion, falls das System keine entsprechende aktive Gruppe finden kann. Andernfalls wird diese Spalte auf NULL gesetzt.|39|Benutzerkontensteuerung|  
|ObjectName|**nvarchar(256)**|Der zweiteilige Name der benutzerdefinierten Klassifizierungsfunktion. Beispiel: dbo.classifier.|34|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Starting-Ereignisklasse](../../relational-databases/event-classes/preconnect-starting-event-class.md)   
 [Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md)  
  
  
