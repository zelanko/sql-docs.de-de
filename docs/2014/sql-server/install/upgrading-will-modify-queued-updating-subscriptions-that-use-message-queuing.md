---
title: Beim Upgrade werden Abonnements Message Queuing mit verzögertem Update über eine Warteschlange geändert. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d44cbad43d75634cbf8660110cc879522265c54d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058854"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a>Das Upgrade ändert Abonnements mit verzögertem Update über eine Warteschlange, die Message Queuing verwenden
  Der Upgrade Advisor hat erkannt, dass möglicherweise mindestens ein Abonnement mit verzögertem Update über eine Warteschlange vorhanden ist, das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (MSMQ) verwendet. Die Replikation unterstützt kein Message Queuing mehr. Deshalb werden die Abonnements so geändert, dass sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlange verwenden.  
  
 Es ist nur der Wert **SQL** zulässig. Vorhandene Veröffentlichungen, für die Message Queuing verwendet wird, werden während des Upgrades geändert, um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlange zu verwenden. Wenn Sie Anwendungen verwenden, die auf dem verzögerten Update über Message Queuing basieren, müssen diese Anwendungen für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlange umgeschrieben werden. Weitere Informationen über Abonnements mit verzögertem Update über eine Warteschlange finden unter "Aktualisierbare Abonnements für die Transaktionsreplikation" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
 Beim Upgrade werden die vorhandenen Message Queuing-Abonnementwarteschlangen entfernt, wenn der Message Queuing-Dienst ausgeführt wird, während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisiert wird.  
  
 Wenn der Message Queuing-Dienst nicht ausgeführt wird, entfernen Sie alle Warteschlangen manuell, nachdem das Upgrade abgeschlossen wurde. Weitere Informationen darüber, wie Warteschlangen entfernt werden, finden Sie in der Windows-Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Probleme beim Replikationsupgrade](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
