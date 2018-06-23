---
title: Sicherheit für den Warteschlangenlese-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 228dc8f4d6b2161b7d6021001d9fbf7603eb522a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162670"
---
# <a name="queue-reader-agent-security"></a>Sicherheit für den Warteschlangenlese-Agent
  Im Dialogfeld **Sicherheit für den Warteschlangenlese-Agent** können Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto angeben, unter dem der Warteschlangenlese-Agent ausgeführt wird und Verbindungen mit dem Verteiler herstellt. Der Agent stellt mithilfe des im Dialogfeld **Verlegereigenschaften** (über das Dialogfeld **Verteilereigenschaften** verfügbar) angegebenen Kontos die Verbindung zum Verleger her. Der Agent stellt für das Abonnement mithilfe desselben Kontexts wie der Verteilungs-Agent die Verbindung mit dem Abonnenten her. Weitere Informationen finden Sie unter [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).  
  
 Das Konto muss für das angegebene Kennwort gültig sein. Konten und Kennwörter werden erst bei der Ausführung eines Agents überprüft.  
  
## <a name="options"></a>Tastatur  
 **Prozesskonto**  
 Geben Sie das Windows-Konto ein, unter dem der Warteschlangenlese-Agent auf dem Verteiler ausgeführt wird. Das angegebene Windows-Konto muss mindestens ein Mitglied der festen Datenbankrolle **db_owner** in der Verteilungsdatenbank sein.  
  
 **Kennwort** und **Kennwort bestätigen**  
 In diese Felder geben Sie das Kennwort für das Windows-Konto ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Anmeldeinformationen und Kennwörtern bei der Replikation](security/manage-logins-and-passwords-in-replication.md)   
 [Sicherheitsmodell des Replikations-Agents](security/replication-agent-security-model.md)   
 [Replikations-Agents (Übersicht)](agents/replication-agents-overview.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)  
  
  