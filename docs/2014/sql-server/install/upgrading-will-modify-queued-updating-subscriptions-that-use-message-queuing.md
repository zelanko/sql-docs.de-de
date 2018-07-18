---
title: Upgrade ändert Abonnements mit verzögertem Aktualisieren, die Message Queuing verwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 37fcfeecfb7160b48d2ed875f76e3b970c29a880
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272366"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a>Das Upgrade ändert Abonnements mit verzögertem Update über eine Warteschlange, die Message Queuing verwenden
  Der Upgrade Advisor hat erkannt, dass möglicherweise mindestens ein Abonnement mit verzögertem Update über eine Warteschlange vorhanden ist, das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (MSMQ) verwendet. Die Replikation unterstützt kein Message Queuing mehr. Deshalb werden die Abonnements so geändert, dass sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlange verwenden.  
  
 Nur der Wert **Sql** ist zulässig. Vorhandene Veröffentlichungen, für die Message Queuing verwendet wird, werden während des Upgrades geändert, um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlange zu verwenden. Wenn Sie Anwendungen verwenden, die auf dem verzögerten Update über Message Queuing basieren, müssen diese Anwendungen für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlange umgeschrieben werden. Weitere Informationen über Abonnements mit verzögertem Update über eine Warteschlange finden unter "Aktualisierbare Abonnements für die Transaktionsreplikation" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
 Beim Upgrade werden die vorhandenen Message Queuing-Abonnementwarteschlangen entfernt, wenn der Message Queuing-Dienst ausgeführt wird, während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisiert wird.  
  
 Wenn der Message Queuing-Dienst nicht ausgeführt wird, entfernen Sie alle Warteschlangen manuell, nachdem das Upgrade abgeschlossen wurde. Weitere Informationen darüber, wie Warteschlangen entfernt werden, finden Sie in der Windows-Dokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Probleme beim Replikationsupgrade](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
