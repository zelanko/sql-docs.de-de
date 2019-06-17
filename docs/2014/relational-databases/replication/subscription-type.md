---
title: Abonnementtyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d936c1a1086f13d43bc38758f86a0ab80f757f7b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63249382"
---
# <a name="subscription-type"></a>Abonnementtyp
  Die Mergereplikation umfasst zwei Abonnementtypen: Server und Client (in früheren Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als global bzw. lokal bezeichnet). Abonnenten mit einem Serverabonnement können:  
  
-   Daten für andere Abonnenten erneut veröffentlichen.  
  
-   Als alternative Synchronisierungspartner dienen.  
  
-   Konflikte entsprechend einer von Ihnen festgelegten Priorität lösen.  
  
 Die meisten Abonnenten benötigen diese Funktionalität nicht und können das Clientabonnement verwenden. Mit Clientabonnements können immer noch Konflikte erkannt und gelöst werden, Abonnenten wird jedoch keine Priorität zugeordnet: der erste Abonnent, der eine Änderung an den Verleger sendet, gewinnt in Konflikten, die durch diese Änderung auftreten können.  
  
> [!NOTE]  
>  Nach dem Erstellen eines Abonnements kann der Abonnementtyp nicht mehr geändert werden.  
  
## <a name="options"></a>Optionen  
 **Abonnementeigenschaften**  
 Wählen Sie für jeden Abonnenten aus der Dropdownliste in der **Abonnementtyp** -Spalte die Option **Client** oder **Server** aus. Geben Sie für Abonnenten mit Serverabonnements in der **Priorität für Konfliktlösung** -Spalte eine Zahl zwischen 0 und 99,99 ein (je höher die Zahl, desto höher die Priorität des Abonnenten).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Pullabonnements](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
