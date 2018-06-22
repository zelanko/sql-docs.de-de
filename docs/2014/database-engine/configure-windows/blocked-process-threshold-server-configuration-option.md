---
title: Schwellenwert für blockierte Prozesse (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 56c19d246b4b976cdbca8ea3e175d97c964afffb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050651"
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
  
  
