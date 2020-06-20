---
title: Angeben eines Mergeabonnementtyps und einer Konflikt Lösungs Priorität (SQL Server Management Studio) | Microsoft-Dokumentation
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
ms.openlocfilehash: a19ae6246fe59308283fbaf2f35e2c49f96b140c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055561"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a>Angeben eines Mergeabonnementtyps und einer Konfliktlösungspriorität (Server Management Studio)
  Auf der Seite **Abonnementtyp** des Assistenten für neue Abonnements können Sie einen Mergeabonnementtyp und eine Konfliktlösungspriorität angeben. Weitere Informationen zum Verwenden dieses Assistenten finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md) und [Create a Push Subscription](create-a-push-subscription.md).  
  
 Der Abonnementtyp kann nicht geändert werden, nachdem ein Abonnement erstellt wurde, aber die Priorität kann im Dialogfeld **Abonnement Eigenschaften- \<Publisher> : \<PublicationDatabase> ** für den Server Abonnementtyp geändert werden. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) und [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>So geben Sie einen Mergeabonnementtyp und eine Konfliktlösungspriorität an  
  
1.  Wählen Sie auf der Seite **Abonnementtyp** des Assistenten für neue Abonnements für die Option **Abonnementtyp** entweder **Client** oder **Server** aus.  
  
2.  Falls Sie den Abonnementtyp **Server**auswählen, geben Sie zudem einen Wert (0,00 bis 99,99) für die Option **Priorität für Konfliktlösung** ein.  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>So ändern Sie die Konfliktlösungspriorität  
  
1.  Geben Sie in den **Abonnement Eigenschaften- \<Publisher> : \<PublicationDatabase> ** auf dem Verleger einen Wert (0,00 bis 99,99) für die Option **Priorität** ein.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Konflikterkennung und-Lösung bei der Mergereplikation](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
