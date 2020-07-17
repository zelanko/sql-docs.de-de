---
title: Schwellenwert für blockierte Prozesse (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Schwellenwertoption für blockierte Prozesse verwenden, um das Intervall anzugeben, indem SQL Server Berichte für blockierte Prozesse generiert und Warnungen ausgibt.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bdd5f7d01e7271609562fb7d42126746d6163de4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725245"
---
# <a name="blocked-process-threshold-server-configuration-option"></a>Schwellenwert für blockierte Prozesse (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

 Mit der Option **Schwellenwert für blockierte Prozesse** geben Sie den Schwellenwert in Sekunden an, bei dem Berichte zu blockierten Prozessen generiert werden. Der Schwellenwert kann auf einen Wert zwischen 5 und 86.400 festgelegt werden.  Der Sperrmonitor wird nur alle 5 Sekunden aktiviert, um Blockierbedingungen zu erkennen. Zudem sucht er nach anderen Bedingungen, z. B. Deadlocks. Wenn Sie daher den Schwellenwert für blockierte Prozesse auf 1 festlegen, wird kein Prozess erkannt, der für eine Sekunde blockiert wurde. Die minimale Zeit, in der ein blockierter Prozess erkannt werden kann, beträgt 5 Sekunden.
 
 Standardmäßig werden für blockierte Prozesse keine Berichte erstellt. Dieses Ereignis wird nicht für Systemtasks und Tasks generiert, die auf Ressourcen warten, die keine bekannten Deadlocks generieren.  
  
 Sie können eine [Warnung](../../ssms/agent/alerts.md) festlegen, die bei der Generierung dieses Ereignisses erfolgen soll. So können Sie beispielsweise angeben, dass Administrator eine Aufforderung zur Ergreifung der geeigneten Maßnahmen erhalten soll, um die Blockierung zu lösen.  
  
 Für den Schwellenwert für blockierte Prozesse wird der Hintergrundthread der Deadlocküberwachung verwendet, um auf einen Zeitwert zu warten, der größer oder ein Vielfaches des konfigurierten Schwellenwerts ist. Das Ereignis wird pro Berichtsintervall einmal für jeden blockierten Task generiert.  
  
 Der Bericht zu blockierten Prozessen erfolgt auf Grundlage der besten Leistung. Eine Berichterstellung in Echtzeit oder annähernder Echtzeit kann nicht sichergestellt werden.  
  
 Die Einstellung tritt ohne Beenden und Neustarten des Servers sofort in Kraft.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Wert für `blocked process threshold` auf `20` Sekunden festgelegt. Hiermit wird für jeden blockierten Task ein Bericht zu blockierten Prozessen generiert.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Blocked Process Report-Ereignisklasse](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
