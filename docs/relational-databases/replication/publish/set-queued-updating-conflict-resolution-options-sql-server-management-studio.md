---
title: Festlegen der Konfliktlösungsoptionen für verzögerte Updates über eine Warteschlange (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e0259cd61f563c50dbed0fdeac2cbebf11418b03
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850988"
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>Festlegen der Konfliktlösungsoptionen für verzögerte Updates über eine Warteschlange (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Konfliktlösungsoptionen für Veröffentlichungen, die Abonnements mit verzögertem Update über eine Warteschlange unterstützen, werden auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** festgelegt. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>So legen Sie die Konfliktlösungsoptionen für das verzögerte Update über eine Warteschlange fest  
  
1.  Wählen Sie auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** für die Option **Richtlinie zur Konfliktlösung** einen der folgenden Werte aus:  
  
    -   **Verlegeränderung beibehalten**  
  
    -   **Abonnentenänderung beibehalten**  
  
    -   **Abonnement erneut initialisieren**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Aktivieren des Aktualisierens von Abonnements für Transaktionsveröffentlichungen](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
