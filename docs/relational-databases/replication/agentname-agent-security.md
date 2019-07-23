---
title: '&lt;AgentName&gt;-Agent-Sicherheit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4eb95e374ee4fa31dca4bf6348baf543e4c9fdd8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085983"
---
# <a name="ltagentnamegt-agent-security"></a>&lt;AgentName&gt;-Agent-Sicherheit
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Auf der Seite **\<AgentName> Agentsicherheit** können Sie die Konten angeben, unter denen der Verteilungs-Agent (bei Transaktions- oder Momentaufnahmereplikation) oder Merge-Agent (bei Mergereplikation) Verbindungen mit den Computern einer Replikationstopologie herstellt und ausführt. Informationen zu erforderlichen Berechtigungen für Agents und bewährten Methoden für die Replikationssicherheit finden Sie unter [Sicherheitsmodell des Replikations-Agent](../../relational-databases/replication/security/replication-agent-security-model.md) und [Replikationssicherheit, bewährte Methoden](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="options"></a>enthalten  
 Klicken Sie in der Zeile jedes Abonnenten auf die Eigenschaftenschaltfläche (die Schaltfläche mit den **drei Punkten**), um eines der beiden Dialogfelder, **Sicherheit für den Verteilungs-Agent** oder **Sicherheit für den Merge-Agent**, zu öffnen. Klicken Sie in dem geöffneten Dialogfeld auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die von den Agents verwendeten Konten erforderlich sind.  
  
 Wenn Sie die Einstellungen in einem der beiden Dialogfelder eingegeben haben, werden im Raster die Verbindungsinformationen zu dem Abonnenten angezeigt.  
  
 **Agent für Abonnent**  
 Die Namen aller Abonnenten.  
  
 **Verbindung mit Verteiler**  
 Wird bei der Transaktions- und Momentaufnahmereplikation angezeigt. Der Kontext, unter dem die Verbindung mit dem Verteiler hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird:  
  
-   Bei Pushabonnements ist die lokale Verbindung diejenige mit dem Verteiler. Daher wird in diesem Feld immer Folgendes angezeigt: **Impersonate '\<Domain>\\<Login\>'** (Folgende Identität annehmen: „<Domain>\<Anmeldename>“) oder **Impersonate '\<Computer>\\<Login\>'** (Folgende Identität annehmen: „<Computer>\<Anmeldename>“) für Pushabonnements.  
  
-   Bei Pullabonnements kann die Verbindung auch unter dem Kontext einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung hergestellt werden. In dem Feld wird eine der folgenden Optionen angezeigt: **Use login '\<Login>'** (Anmeldename verwenden: „<Anmeldename>“), **Impersonate '\<Domain>\\<Login\>'** (Folgende Identität annehmen: „<Domain>\<Anmeldename>“) oder **Impersonate '\<Computer>\\<Login\>'** (Folgende Identität annehmen: <Computer>\<Anmeldename>)“. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
 **Verbindung mit Verleger &Verteiler**  
 Wird bei Mergereplikation angezeigt. Der Kontext, unter dem die Verbindung mit dem Verleger und Verteiler hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird.  
  
-   Bei Pushabonnements ist die lokale Verbindung diejenige mit dem Verleger und Verteiler. Daher wird in diesem Feld immer Folgendes angezeigt: **Impersonate '\<Domain>\\<Login\>'** (Folgende Identität annehmen: „<Domain>\<Anmeldename>“) oder **Impersonate '\<Computer>\\<Login\>'** (Folgende Identität annehmen: „<Computer>\<Anmeldename>“) für Pushabonnements.  
  
-   Bei Pullabonnements kann die Verbindung auch unter dem Kontext einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung hergestellt werden. In dem Feld wird eine der folgenden Optionen angezeigt: **Use login '\<Login>'** (Anmeldename verwenden: „<Anmeldename>“), **Impersonate '\<Domain>\\<Login\>'** (Folgende Identität annehmen: „<Domain>\<Anmeldename>“) oder **Impersonate '\<Computer>\\<Login\>'** (Folgende Identität annehmen: <Computer>\<Anmeldename>)“. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
 **Verbindung mit Abonnent**  
 Der Kontext, unter dem die Verbindung mit dem Abonnenten hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird.  
  
-   Bei Pullabonnements ist die lokale Verbindung diejenige mit dem Abonnenten. Daher wird in diesem Feld immer Folgendes angezeigt: **Impersonate '\<Domain>\\<Login\>'** (Folgende Identität annehmen: „<Domain>\<Anmeldename>“) oder **Impersonate '\<Computer>\\<Login\>'** (Folgende Identität annehmen: „<Computer>\<Anmeldename>“) für Pushabonnements.  
  
-   Bei Pushabonnements kann die Verbindung auch unter dem Kontext einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung hergestellt werden. In dem Feld wird eine der folgenden Optionen angezeigt: **Use login '\<Login>'** (Anmeldename verwenden: „<Anmeldename>“), **Impersonate '\<Domain>\\<Login\>'** (Folgende Identität annehmen: „<Domain>\<Anmeldename>“) oder **Impersonate '\<Computer>\\<Login\>'** (Folgende Identität annehmen: <Computer>\<Anmeldename>)“. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern der Eigenschaften von Pullabonnements](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Anzeigen und Ändern der Eigenschaften von Pushabonnements](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Identität und Zugriffssteuerung (Replikation)](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [Sicherheitsmodell des Replikations-Agents](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Anzeigen und Ändern von Replikationssicherheitseinstellungen](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
