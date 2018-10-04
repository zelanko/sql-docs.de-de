---
title: Sperren-Ereigniskategorie | Microsoft-Dokumentation
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
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 220b5287a2ed120092b6c694cac5fc363b33eceb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142260"
---
# <a name="locks-event-category"></a>Sperren-Ereigniskategorie
  Verwenden Sie die Ereignisklassen in der **Sperren** -Ereigniskategorie, um die Sperraktivität in einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]zu überwachen. Diese Ereignisklassen können Ihnen die Untersuchung von Sperrproblemen erleichtern, die auftreten können, wenn Daten von mehreren Benutzern gleichzeitig gelesen und bearbeitet werden.  
  
 Da das [!INCLUDE[ssDE](../../includes/ssde-md.md)] häufig mehrere Sperren verarbeitet, kann das Erfassen der **Sperren** -Ereignisklassen während einer Ablaufverfolgung einen deutlich höheren Verarbeitungsaufwand zur Folge haben. Außerdem können dabei große Ablaufverfolgungsdateien oder -tabellen entstehen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Deadlock Graph (Ereignisklasse)](deadlock-graph-event-class.md)|Stellt eine XML-Beschreibung eines Deadlocks bereit.|  
|[Lock:Acquired (Ereignisklasse)](lock-acquired-event-class.md)|Gibt an, dass für eine Ressource, z. B. eine Zeile in einer Tabelle, eine Sperre eingerichtet wurde.|  
|[Lock:Cancel-Ereignisklasse](lock-cancel-event-class.md)|Verfolgt Sperranforderungen nach, die vor dem Einrichten der Sperre abgebrochen wurden (beispielsweise, um einen Deadlock zu verhindern).|  
|[Lock:Deadlock Chain (Ereignisklasse)](lock-deadlock-chain-event-class.md)|Überwacht, wann Deadlockbedingungen auftreten und welche Objekte betroffen sind.|  
|[Lock:Deadlock (Ereignisklasse)](lock-deadlock-event-class.md)|Verfolgt nach, wann eine Transaktion eine Sperre für eine bereits durch eine andere Transaktion gesperrte Ressource angefordert hat, wodurch ein Deadlock auftritt.|  
|[Lock:Escalation-Ereignisklasse](lock-escalation-event-class.md)|Zeigt an, dass eine differenziertere Sperre in eine gröbere Sperre konvertiert wurde.|  
|[Lock:Released (Ereignisklasse)](lock-released-event-class.md)|Verfolgt nach, wann eine Sperre aufgehoben wird.|  
|[Lock:Timeout &#40;timeout &#62; 0&#41; Ereignisklasse](lock-timeout-timeout-0-event-class.md)|Verfolgt nach, wann Sperranforderungen nicht erfüllt werden können, weil eine andere Transaktion eine blockierende Sperre für die angeforderte Ressource aufrechterhält. Dieses Ereignis tritt nur in Situationen auf, in denen der Wert für den Sperrtimeout größer als Null ist.|  
|[Lock:Timeout (Ereignisklasse)](lock-timeout-event-class.md)|Verfolgt nach, wann Sperranforderungen nicht erfüllt werden können, weil eine andere Transaktion eine blockierende Sperre für die angeforderte Ressource aufrechterhält.|  
  
  
