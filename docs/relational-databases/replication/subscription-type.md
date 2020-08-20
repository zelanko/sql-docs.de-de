---
description: Subscription Type (Abonnementtyp)
title: Abonnementtyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 7816e2d4b0094b502979811fa25c42c9c447ffc0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482273"
---
# <a name="subscription-type"></a>Subscription Type (Abonnementtyp)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Die Mergereplikation bietet zwei Abonnementtypen: Server und Client (in früheren Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als global bzw. lokal bezeichnet). Abonnenten mit einem Serverabonnement können:  
  
-   Daten für andere Abonnenten erneut veröffentlichen.  
  
-   Als alternative Synchronisierungspartner dienen.  
  
-   Konflikte entsprechend einer von Ihnen festgelegten Priorität lösen.  
  
 Die meisten Abonnenten benötigen diese Funktionalität nicht und können das Clientabonnement verwenden. Mit Clientabonnements können immer noch Konflikte erkannt und gelöst werden, Abonnenten wird jedoch keine Priorität zugeordnet: der erste Abonnent, der eine Änderung an den Verleger sendet, gewinnt in Konflikten, die durch diese Änderung auftreten können.  
  
> [!NOTE]  
>  Nach dem Erstellen eines Abonnements kann der Abonnementtyp nicht mehr geändert werden.  
  
## <a name="options"></a>Optionen  
 **Eigenschaften Abonnement**  
 Wählen Sie für jeden Abonnenten aus der Dropdownliste in der **Abonnementtyp** -Spalte die Option **Client** oder **Server** aus. Geben Sie für Abonnenten mit Serverabonnements in der **Priorität für Konfliktlösung** -Spalte eine Zahl zwischen 0 und 99,99 ein (je höher die Zahl, desto höher die Priorität des Abonnenten).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
