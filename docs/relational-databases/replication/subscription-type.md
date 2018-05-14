---
title: Abonnementtyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8e2ff1f1bc62055c10f3f4c03b28aa3770efe5b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="subscription-type"></a>Abonnementtyp
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die Mergereplikation umfasst zwei Abonnementtypen: Server und Client (in früheren Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als global bzw. lokal bezeichnet). Abonnenten mit einem Serverabonnement können:  
  
-   Daten für andere Abonnenten erneut veröffentlichen.  
  
-   Als alternative Synchronisierungspartner dienen.  
  
-   Konflikte entsprechend einer von Ihnen festgelegten Priorität lösen.  
  
 Die meisten Abonnenten benötigen diese Funktionalität nicht und können das Clientabonnement verwenden. Mit Clientabonnements können immer noch Konflikte erkannt und gelöst werden, Abonnenten wird jedoch keine Priorität zugeordnet: der erste Abonnent, der eine Änderung an den Verleger sendet, gewinnt in Konflikten, die durch diese Änderung auftreten können.  
  
> [!NOTE]  
>  Nach dem Erstellen eines Abonnements kann der Abonnementtyp nicht mehr geändert werden.  
  
## <a name="options"></a>Tastatur  
 **Abonnementeigenschaften**  
 Wählen Sie für jeden Abonnenten aus der Dropdownliste in der **Abonnementtyp** -Spalte die Option **Client** oder **Server** aus. Geben Sie für Abonnenten mit Serverabonnements in der **Priorität für Konfliktlösung** -Spalte eine Zahl zwischen 0 und 99,99 ein (je höher die Zahl, desto höher die Priorität des Abonnenten).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
