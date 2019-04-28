---
title: Neue Peerinitialisierung (Peer-zu-Peer-Replikation) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.init.f1
ms.assetid: 050c00e1-78bd-4d9c-affe-40e22feb4d94
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 51e5ec3832d497f342c4fc3132a75261f6c3c154
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63022685"
---
# <a name="new-peer-initialization-peer-to-peer-replication"></a>Neue Peerinitialisierung (Peer-zu-Peer-Replikation)
  Auf der Seite **Neue Peerinitialisierung** können Sie angeben, wie Peerdatenbanken initialisiert wurden. (Peers müssen initialisiert werden, bevor Sie diesen Assistenten abschließen.) Peers werden manuell oder mithilfe der Funktionalität **initialize with backup** initialisiert, die durch die Transaktionsreplikation zur Verfügung gestellt wird. (Die Peer-zu-Peer-Transaktionsreplikation bietet keine Unterstützung für die Initialisierung von Peers mithilfe von Momentaufnahmen.) Wenn verschiedene Peers mithilfe unterschiedlicher Methoden initialisiert werden müssen, müssen Sie diesen Assistenten mehrfach ausführen, um die Peers einzeln hinzuzufügen.  
  
## <a name="options"></a>Optionen  
 **Geben Sie an, wie die neuen Peerdatenbanken initialisiert wurden**  
 Das Schema und die Daten aller veröffentlichten Objekte müssen für jeden Peer vorliegen. Wählen Sie eine der folgenden Optionen aus:  
  
-   Wählen Sie die erste Option aus, wenn Sie das Schema für veröffentlichte Objekte manuell erstellt haben oder eine Sicherung wiederhergestellt haben und seit der Sicherung an der Veröffentlichungsdatenbank keine Änderungen vorgenommen wurden. Wenn Sie das Schema manuell erstellt haben, müssen Sie sicherstellen, dass alle erforderlichen Daten für die einzelnen Peers vorliegen. Diese Option entspricht dem Wert **replication support only** für die **sync_type**-Abonnementeigenschaft.  
  
-   Wählen Sie die zweite Option aus, wenn Sie eine Sicherung wiederhergestellt haben und seit der Sicherung an der ersten Veröffentlichungsdatenbank Änderungen vorgenommen wurden. Die Replikation muss nun Änderungen übermitteln, die an der ersten Veröffentlichungsdatenbank vorgenommen wurden, und die nicht in der Sicherung enthalten sind. Diese Option entspricht dem Wert **initialize with backup** für die **sync_type**-Abonnementeigenschaft.  
  
     Wenn eine Veröffentlichung für die Peer-zu-Peer-Replikation aktiviert ist, wird die Veröffentlichungseigenschaft **allow_initialize_from_backup** festgelegt. Die Replikation beginnt sofort mit der Nachverfolgung von Änderungen in der ersten Veröffentlichungsdatenbank. Daher können diese Änderungen an eine wiederhergestellte Datenbank für einen oder mehrere Peers übermittelt werden, wenn die Option **initialize with backup** ausgewählt ist. Klicken Sie auf die Schaltfläche **Durchsuchen** , um nach der verwendeten Sicherung zu suchen. Die Replikation liest die Protokollfolgenummer (Log Sequence Number, LSN) aus der Sicherung. Alle Änderungen in der ersten Veröffentlichungsdatenbank mit einer höheren LSN werden an alle Peers übermittelt.  
  
     Diese Option ist möglicherweise nicht verfügbar, wenn Sie eine Topologie erstellen, die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]umfasst, oder einer solchen Topologie Knoten hinzufügen. Die folgende Tabelle zeigt, ob die Option beim Hinzufügen eines Knotens zu einer vorhandenen Topologie verfügbar ist.  
  
    |Neuer Knoten|Erster Knoten|Weitere Knoten|Option|  
    |--------------|----------------|----------------------|------------|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Disabled|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|None|Disabled|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Disabled|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|None|Aktiviert|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|None|Aktiviert|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Aktiviert|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|None|Aktiviert|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten einer Peer-zu-Peer-Topologie &#40;Replikationsprogrammierung mit Transact-SQL&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)  
  
  
