---
title: Veröffentlichungseigenschaften (Agentsicherheit) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.agentsecurity.f1
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5b8f38f877a6a46be70fcfafd2ca3c79fca415b6
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52749022"
---
# <a name="publication-properties-agent-security"></a>Veröffentlichungseigenschaften (Agentsicherheit)
  Mithilfe der Seite **Agentsicherheit** des Dialogfelds **Veröffentlichungseigenschaften** können Sie auf die Eigenschaften für die Konten zugreifen, unter denen die folgenden Agents ausgeführt werden und Verbindungen mit Computern in einer Replikationstopologie herstellen:  
  
-   Der Momentaufnahme-Agent für alle Veröffentlichungen.  
  
-   Der Protokolllese-Agent für alle Transaktionsveröffentlichungen. Es gibt einen Protokolllese-Agent für jede Datenbank, die zur Transaktionsreplikation veröffentlicht wird. Das Ändern der Einstellungen des Protokolllese-Agents betrifft alle Transaktionsveröffentlichungen in einer Datenbank.  
  
-   Der Warteschlangenlese-Agent für Transaktionsveröffentlichungen, die Abonnements mit verzögertem Update über eine Warteschlange gestatten. Es gibt einen Warteschlangenlese-Agent für jede Verteilungsdatenbank. Das Ändern der Einstellungen für den Warteschlangenlese-Agent betrifft alle Transaktionsveröffentlichungen mit Abonnements mit verzögertem Update über eine Warteschlange, die dieselbe Verteilungsdatenbank verwenden. Weitere Informationen zu den Sicherheitseinstellungen des Warteschlangenlese-Agents finden Sie unter [Anzeigen und Ändern von Replikationssicherheitseinstellungen](security/view-and-modify-replication-security-settings.md).  
  
 Weitere Informationen zu den für die einzelnen Agents erforderlichen Sicherheitseinstellungen und Berechtigungen finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
## <a name="options"></a>Optionen  
 **Sicherheitseinstellungen** oder **Agent erstellen**  
 Klicken Sie, nachdem ein Agentauftrag erstellt wurde, auf **Sicherheitseinstellungen** , um auf ein Dialogfeld zuzugreifen, das Ihnen das Ändern der Sicherheitseinstellungen für einen Agent ermöglicht. Wenn kein Agentauftrag erstellt wurde, klicken Sie zum Erstellen eines Agentauftrags auf **Agent erstellen** , und geben Sie die Sicherheitseinstellungen an.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Publication](publish/create-a-publication.md)   
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](publish/view-and-modify-publication-properties.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Sicherheit und Schutz &#40;Replikation&#41;](security/security-and-protection-replication.md)  
  
  
