---
title: Angeben der Typ- und Konfliktauflösungspriorität (Mergeabonnement)
description: Hier erfahren Sie, wie Sie die von einem Mergeabonnement für SQL Server verwendete Richtlinie für Typ- und Konfliktauflösung angeben.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a988935a1d0a614f1b7b336cc95ed82ce2a36214
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "75321737"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Angeben eines Mergeabonnementtyps und einer Konfliktlösungspriorität
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Auf der Seite **Abonnementtyp** des Assistenten für neue Abonnements können Sie einen Mergeabonnementtyp und eine Konfliktlösungspriorität angeben. Weitere Informationen zum Verwenden dieses Assistenten finden Sie unter [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) und [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
 Der Abonnementtyp kann nicht geändert werden, nachdem ein Abonnement erstellt wurde, aber die Priorität kann im Dialogfeld **Abonnementeigenschaften - \<Publisher>: \<PublicationDatabase>** für den Serverabonnementtyp geändert werden. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) und [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>So geben Sie einen Mergeabonnementtyp und eine Konfliktlösungspriorität an  
  
1.  Wählen Sie auf der Seite **Abonnementtyp** des Assistenten für neue Abonnements für die Option **Abonnementtyp** entweder **Client** oder **Server** aus.  
  
2.  Falls Sie den Abonnementtyp **Server**auswählen, geben Sie zudem einen Wert (0,00 bis 99,99) für die Option **Priorität für Konfliktlösung** ein.  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>So ändern Sie die Konfliktlösungspriorität  
  
1.  Wählen Sie unter **Abonnementeigenschaften - \<Publisher>: \<PublicationDatabase>** auf dem Verleger einen Wert (0,00 bid 99,99) für die Option **Priorität** aus.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Konflikterkennung und -lösung der Mergereplikation](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
