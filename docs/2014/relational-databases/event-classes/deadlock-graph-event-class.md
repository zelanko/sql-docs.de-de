---
title: Deadlock Graph (Ereignisklasse) | Microsoft Dokumentation
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
- Deadlock Graph event class
ms.assetid: 20f92233-c912-4382-8993-8e2e23d03fbe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d27707fc52c2620d6905cbd23e1b710f927bd58b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105740"
---
# <a name="deadlock-graph-event-class"></a>Deadlock Graph (Ereignisklasse)
  Die **Deadlock Graph** -Ereignisklasse stellt eine XML-Beschreibung für ein Deadlock bereit. Diese Klasse tritt zusammen mit der **Lock:Deadlock** -Ereignisklasse auf.  
  
## <a name="deadlock-graph-event-class-data-columns"></a>Deadlock Graph-Ereignisklasse (Datenspalten)  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|Ereignistyp = 148.|27|nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer. Bei diesem Ereignis ist der Wert immer 1.|60|Benutzerkontensteuerung|  
|**LoginName**|**nvarchar**|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format „DOMAIN\username“). Bei diesem Ereignis ist der Wert immer mit dem Systembenutzer identisch.|11|Benutzerkontensteuerung|  
|**LoginSid**|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig. Bei diesem Ereignis ist der Wert immer mit der SID des Systembenutzers identisch.|41|Benutzerkontensteuerung|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|**StartTime**|**datetime**|Der Zeitpunkt, an dem der Deadlock entdeckt wurde.|14|Benutzerkontensteuerung|  
|**TextData**|**ntext**|XML-Beschreibung des Deadlocks.|1|Benutzerkontensteuerung|  
|**TransactionID**|**bigint**|Wird nicht verwendet.|4|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Lock:Deadlock (Ereignisklasse)](lock-deadlock-event-class.md)  
  
  
