---
title: 'Eigenschaften von Warnung: Neue Warnung (Optionsseite) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b6e9cc28520099d9e3e3fad059a58e487b35859f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151791"
---
# <a name="alert-properties-new-alert-options-page"></a>Eigenschaften von Warnung: Neue Warnung (Optionsseite)
  Mithilfe dieser Seite können Sie die Optionen für Agentwarnungen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
 **E-Mail**  
 Schließt Fehlertext des Ereignisses ggf. in E-Mail-Benachrichtigungen ein.  
  
 **Pager**  
 Schließt Fehlertext des Ereignisses ggf. in Pagerbenachrichtigungen ein.  
  
 **NET SEND**  
 Schließt Fehlertext des Ereignisses ggf. in NET SEND-Benachrichtigungen ein.  
  
 **Zusätzlich zu sendende Warnbenachrichtigung**  
 Geben Sie hier zusätzlichen Text ein, der in die Benachrichtigungsmeldungen aufgenommen werden soll.  
  
 **Antwortverzögerung**  
 Geben Sie eine Verzögerung für das wiederholte Auftreten des Ereignisses an. Einige Ereignisse können innerhalb einer kurzen Zeitspanne häufig auftreten. In diesem Fall könnte es sinnvoll sein, zwar über das Auftreten des Ereignisses informiert zu werden, nicht aber für jedes Auftreten eine Meldung zu erhalten. Mithilfe dieser Option können Sie einen Timeoutwert angeben. Durch die Angabe einer Verzögerung nach der Warnungsantwort auf ein Ereignis wartet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent die angegebene Verzögerungszeit ab, bevor eine weitere Antwort zurückgegeben wird, unabhängig davon, ob das Ereignis in der Zwischenzeit wieder auftritt.  
  
 **Minuten**  
 Geben Sie eine Verzögerung in Minuten an. Wenn bei jedem Auftreten des Ereignisses geantwortet werden soll, geben Sie 0 Minuten und 0 Sekunden an.  
  
 **Sekunden**  
 Geben Sie eine Verzögerung in Sekunden an. Wenn bei jedem Auftreten des Ereignisses geantwortet werden soll, geben Sie 0 Minuten und 0 Sekunden an.  
  
## <a name="see-also"></a>Siehe auch  
 [Warnungen](alerts.md)  
  
  
