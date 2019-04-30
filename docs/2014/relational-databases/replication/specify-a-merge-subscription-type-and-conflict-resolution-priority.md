---
title: Geben Sie einen Mergeabonnementtyps und einer Konfliktlösungspriorität (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ef72b3c36e1cfc7d59792056e080d1cbf2d5c55
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156351"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a>Angeben eines Mergeabonnementtyps und einer Konfliktlösungspriorität (Server Management Studio)
  Auf der Seite **Abonnementtyp** des Assistenten für neue Abonnements können Sie einen Mergeabonnementtyp und eine Konfliktlösungspriorität angeben. Weitere Informationen zum Verwenden dieses Assistenten finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md) und [Create a Push Subscription](create-a-push-subscription.md).  
  
 Abonnementtyp kann nicht geändert werden, nachdem ein Abonnement wird erstellt, aber die Priorität werden, für den serverabonnementtyp in geändert kann die **Abonnementeigenschaften - \<Verleger >: \<PublicationDatabase >** Dialogfeld. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) und [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>So geben Sie einen Mergeabonnementtyp und eine Konfliktlösungspriorität an  
  
1.  Wählen Sie auf der Seite **Abonnementtyp** des Assistenten für neue Abonnements für die Option **Abonnementtyp** entweder **Client** oder **Server** aus.  
  
2.  Falls Sie den Abonnementtyp **Server**auswählen, geben Sie zudem einen Wert (0,00 bis 99,99) für die Option **Priorität für Konfliktlösung** ein.  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>So ändern Sie die Konfliktlösungspriorität  
  
1.  In der **Abonnementeigenschaften - \<Verleger >: \<PublicationDatabase >** Geben Sie auf dem Verleger einen Wert (0,00 bis 99,99) für die **Priorität** Option.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Konflikterkennung und -lösung bei der Mergereplikation](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
