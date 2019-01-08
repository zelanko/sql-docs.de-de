---
title: Schwellenwert für blockierte Prozesse (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 02f2fcfd3534a4ae1902a2984d2bd0fac0fc727c
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52640078"
---
# <a name="blocked-process-threshold-server-configuration-option"></a>Schwellenwert für blockierte Prozesse (Serverkonfigurationsoption)
  Mit der Option **Schwellenwert für blockierte Prozesse** geben Sie den Schwellenwert in Sekunden an, bei dem Berichte zu blockierten Prozessen generiert werden. Der Schwellenwert kann auf einen Wert zwischen 0 und 86.400 festgelegt werden. Standardmäßig werden für blockierte Prozesse keine Berichte erstellt. Dieses Ereignis wird nicht für Systemtasks und Tasks generiert, die auf Ressourcen warten, die keine bekannten Deadlocks generieren.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Blocked Process Report-Ereignisklasse](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
