---
title: '&lt;AgentName&gt;-Agent-Sicherheit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d77f8d6acb449bc9aa2298dbcba9782fd7bc07e7
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54127436"
---
# <a name="ltagentnamegt-agent-security"></a>&lt;AgentName&gt;-Agent-Sicherheit
  Auf der Seite **\<AgentName> Agentsicherheit** können Sie die Konten angeben, unter denen der Verteilungs-Agent (bei Transaktions- oder Momentaufnahmereplikation) oder Merge-Agent (bei Mergereplikation) Verbindungen mit den Computern einer Replikationstopologie herstellt und ausführt. Informationen zu erforderlichen Berechtigungen für Agents und bewährten Methoden für die Replikationssicherheit finden Sie unter [Sicherheitsmodell des Replikations-Agent](security/replication-agent-security-model.md) und [Replikationssicherheit, bewährte Methoden](security/replication-security-best-practices.md).  
  
## <a name="options"></a>Optionen  
 Klicken Sie in der Zeile jedes Abonnenten auf die Eigenschaftenschaltfläche **...**(die Schaltfläche mit den drei Punkten), um eines der beiden Dialogfelder, **Sicherheit für den Verteilungs-Agent** oder **Sicherheit für den Merge-Agent** , zu öffnen. Klicken Sie in dem geöffneten Dialogfeld auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die von den Agents verwendeten Konten erforderlich sind.  
  
 Wenn Sie die Einstellungen in einem der beiden Dialogfelder eingegeben haben, werden im Raster die Verbindungsinformationen zu dem Abonnenten angezeigt.  
  
 **Agent für Abonnent**  
 Die Namen aller Abonnenten.  
  
 **Verbindung mit Verteiler**  
 Wird bei der Transaktions- und Momentaufnahmereplikation angezeigt. Der Kontext, unter dem die Verbindung mit dem Verteiler hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird:  
  
-   Bei Pushabonnements ist die lokale Verbindung die Verbindung mit dem Verteiler, damit dieses Feld immer angezeigt werden: **Impersonate '\<Domäne >\\< Anmeldung\>"** oder **Impersonate '\<Computer >\\< Anmeldung\>"** für Pushvorgänge Abonnements.  
  
-   Bei Pullabonnements kann die Verbindung auch unter dem Kontext einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung hergestellt werden. Das Feld zeigt eine der folgenden: **Anmeldung verwenden '\<Login >'**, **Impersonate '\<Domäne >\\< Anmeldung\>"** oder **Impersonate '\<Computer >\\< Login\>"**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
 **Verbindung mit Verleger &Verteiler**  
 Wird bei Mergereplikation angezeigt. Der Kontext, unter dem die Verbindung mit dem Verleger und Verteiler hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird.  
  
-   Bei Pushabonnements ist die lokale Verbindung die Verbindung mit dem Verleger und Verteiler, damit dieses Feld immer angezeigt werden: **Impersonate '\<Domäne >\\< Anmeldung\>"** oder **Impersonate '\<Computer >\\< Anmeldung\>"** für Pushvorgänge Abonnements.  
  
-   Bei Pullabonnements kann die Verbindung auch unter dem Kontext einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung hergestellt werden. Das Feld zeigt eine der folgenden: **Anmeldung verwenden '\<Login >'**, **Impersonate '\<Domäne >\\< Anmeldung\>"** oder **Impersonate '\<Computer >\\< Login\>"**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
 **Verbindung mit Abonnent**  
 Der Kontext, unter dem die Verbindung mit dem Abonnenten hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird.  
  
-   Bei Pullabonnements ist die lokale Verbindung die Verbindung mit dem Abonnenten, damit dieses Feld immer angezeigt werden: **Impersonate '\<Domäne >\\< Anmeldung\>"** oder **Impersonate '\<Computer >\\< Anmeldung\>"** für Pushvorgänge Abonnements.  
  
-   Bei Pushabonnements kann die Verbindung auch unter dem Kontext einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung hergestellt werden. Das Feld zeigt eine der folgenden: **Anmeldung verwenden '\<Login >'**, **Impersonate '\<Domäne >\\< Anmeldung\>"** oder **Impersonate '\<Computer >\\< Login\>"**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Eigenschaften von Pullabonnements](view-and-modify-pull-subscription-properties.md)   
 [Anzeigen und Ändern der Eigenschaften von Pushabonnements](view-and-modify-push-subscription-properties.md)   
 [Verwalten von Anmeldeinformationen und Kennwörtern bei der Replikation](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Sicherheitsmodell des Replikations-Agents](security/replication-agent-security-model.md)   
 [Sicherheit von SQL Server-Replikation](security/view-and-modify-replication-security-settings.md)  
  
  
