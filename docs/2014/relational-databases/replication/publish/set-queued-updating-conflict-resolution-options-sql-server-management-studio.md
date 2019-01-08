---
title: Festlegen der Konfliktlösungsoptionen für verzögerte Updates über eine Warteschlange (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: f05328a43c75158e9be6c13e4fc23b0cc9ab2799
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52749003"
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>Festlegen der Konfliktlösungsoptionen für verzögerte Updates über eine Warteschlange (SQL Server Management Studio)
  Die Konfliktlösungsoptionen für Veröffentlichungen, die Abonnements mit verzögertem Update über eine Warteschlange unterstützen, werden auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** festgelegt. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>So legen Sie die Konfliktlösungsoptionen für das verzögerte Update über eine Warteschlange fest  
  
1.  Wählen Sie auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** für die Option **Richtlinie zur Konfliktlösung** einen der folgenden Werte aus:  
  
    -   **Verlegeränderung beibehalten**  
  
    -   **Abonnentenänderung beibehalten**  
  
    -   **Abonnement erneut initialisieren**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren des Aktualisierens von Abonnements für Transaktionsveröffentlichungen](enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
