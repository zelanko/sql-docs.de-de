---
title: Erneutes Initialisieren von Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 7143f28436de8aed4f6b0298d04a57237d88c03e
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769699"
---
# <a name="reinitialize-subscriptions"></a>Erneutes Initialisieren von Abonnements
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Beim erneuten Initialisieren eines Abonnements wird eine neue Momentaufnahme auf einen oder mehrere Artikel auf einem oder mehreren Abonnenten angewendet, wobei bei der Transaktions- und der Momentaufnahmereplikation das erneute Initialisieren einzelner Artikel möglich ist, während bei der Mergereplikation alle Artikel erneut initialisiert werden müssen. Knoten in einer Peer-zu-Peer-Transaktionsreplikationstopologie können nicht erneut initialisiert werden. Wenn Sie sicherstellen müssen, dass ein Knoten eine neue Kopie der Daten besitzt, stellen Sie an diesem Knoten eine Sicherung wieder her. Die Neuinitialisierung erfolgt aus einem der folgenden beiden Gründe:  
  
-   Sie kennzeichnen explizit ein Abonnement für die Neuinitialisierung.  
  
-   Sie führen eine Aktion, wie z. B. die Änderung einer Eigenschaft, aus, die eine Neuinitialisierung erforderlich macht. Weitere Informationen zu Aktionen, die eine Neuinitialisierung erfordern, finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 In beiden Fällen wird bei der nächsten Ausführung des Verteilungs-Agents oder des Merge-Agents auf den Abonnenten die neueste Momentaufnahme angewendet. Bei der Momentaufnahme- und Transaktionsreplikation werden während der Neuinitialisierung alle auf dem Abonnenten vorgenommenen Änderungen, die noch nicht mit dem Verleger synchronisiert wurden, durch Anwenden der neuen Momentaufnahme überschrieben.  
  
 Bei der Mergereplikation können Sie festlegen, ob vor der Anwendung der Momentaufnahme alle Datenänderungen vom Abonnenten hochgeladen werden. Alle ausstehenden Schemaänderungen vom Verleger werden auf den Abonnenten angewendet. Anschließend werden alle Updates auf dem Abonnenten seit der letzten Synchronisierung an den Verleger weitergeleitet, bevor die Momentaufnahme erneut angewendet wird. Dieses Verhalten wird durch die **upload_first** - und **automatic_reinitialization_policy** -Eigenschaften gesteuert. Weitere Informationen dazu finden Sie unter [Reinitialize a Subscription](../../relational-databases/replication/reinitialize-a-subscription.md). Wenn Sie ein Abonnement für eine Neuinitialisierung in SQL Server Management Studio oder im Replikationsmonitor kennzeichnen, können Sie im Dialogfeld **Abonnements erneut initialisieren** festlegen, dass zuerst die Änderungen hochgeladen werden.  
  
> [!IMPORTANT]  
>  Wenn Sie einen parametrisierten Filter in einer Mergereplikation hinzufügen, löschen oder ändern, können die ausstehenden Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
 Wenn Sie beim Erstellen des Abonnements angegeben haben, dass keine Anfangsmomentaufnahme auf den Abonnenten angewendet werden soll, und Sie dann dieses Abonnement für eine erneute Initialisierung kennzeichnen, wird keine Momentaufnahme angewendet. Weitere Informationen finden Sie unter [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)initialisiert wird.  
  
 **So initialisieren Sie ein Abonnement erneut**  
  
 Wenn alle Artikel in einem Abonnement erneut initialisiert werden sollen, verwenden Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], gespeicherte Prozeduren oder Replikationsverwaltungsobjekte (RMO, Replication Management Objects). Wenn nur bestimmte Artikel in einer Momentaufnahme- oder Transaktionsveröffentlichung erneut initialisiert werden sollen, müssen Sie dazu gespeicherte Prozeduren verwenden. Weitere Informationen finden Sie unter [Reinitialize a Subscription](../../relational-databases/replication/reinitialize-a-subscription.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Initialize a Subscription](../../relational-databases/replication/initialize-a-subscription.md)   
 [Abonnementablauf und -deaktivierung](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
