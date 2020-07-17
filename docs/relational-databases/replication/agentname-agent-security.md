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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 61c5a4a61f276eedd684ee059bb0de2292c03490
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85724767"
---
# <a name="ltagentnamegt-agent-security"></a>&lt;AgentName&gt;-Agent-Sicherheit
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Auf der Seite **\<AgentName>-Agent-Sicherheit** können Sie die Konten angeben, für die der Verteilungs-Agent (bei Transaktions- oder Momentaufnahmereplikation) oder der Merge-Agent (bei Mergereplikation) Verbindungen mit den Computern einer Replikationstopologie herstellt und ausführt. Informationen zu erforderlichen Berechtigungen für Agents und bewährten Methoden für die Replikationssicherheit finden Sie unter [Sicherheitsmodell des Replikations-Agent](../../relational-databases/replication/security/replication-agent-security-model.md) und [Replikationssicherheit, bewährte Methoden](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="options"></a>Tastatur  
 Klicken Sie in der Zeile jedes Abonnenten auf die Eigenschaftenschaltfläche (die Schaltfläche mit den **drei Punkten**), um eines der beiden Dialogfelder, **Sicherheit für den Verteilungs-Agent** oder **Sicherheit für den Merge-Agent**, zu öffnen. Klicken Sie in dem geöffneten Dialogfeld auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die von den Agents verwendeten Konten erforderlich sind.  
  
 Wenn Sie die Einstellungen in einem der beiden Dialogfelder eingegeben haben, werden im Raster die Verbindungsinformationen zu dem Abonnenten angezeigt.  
  
 **Agent für Abonnent**  
 Die Namen aller Abonnenten.  
  
 **Verbindung mit Verteiler**  
 Wird bei der Transaktions- und Momentaufnahmereplikation angezeigt. Der Kontext, unter dem die Verbindung mit dem Verteiler hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird:  
  
-   Bei Pushabonnements ist die lokale Verbindung diejenige mit dem Verteiler. Daher wird in diesem Feld immer Folgendes angezeigt: **Identität annehmen '\<Domain>\\<Anmeldename\>'** oder **Identität annehmen '\<Computer>\\<Anmeldename\>'** für Pushabonnements  
  
-   Bei Pullabonnements kann die Verbindung auch unter dem Kontext einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung hergestellt werden. In dem Feld wird eine der folgenden Optionen angezeigt: **Anmeldenamen '\<Login>' verwenden**, **Identität annehmen '\<Domain>\\<Anmeldename\>'** oder **Identität annehmen '\<Computer>\\<Anmeldename\>'** [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
 **Verbindung mit Verleger &Verteiler**  
 Wird bei Mergereplikation angezeigt. Der Kontext, unter dem die Verbindung mit dem Verleger und Verteiler hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird.  
  
-   Bei Pushabonnements ist die lokale Verbindung diejenige mit dem Verleger und Verteiler. Daher wird in diesem Feld immer Folgendes angezeigt: **Identität annehmen '\<Domain>\\<Anmeldename\>'** oder **Identität annehmen '\<Computer>\\<Anmeldename\>'** für Pushabonnements  
  
-   Bei Pullabonnements kann die Verbindung auch unter dem Kontext einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung hergestellt werden. In dem Feld wird eine der folgenden Optionen angezeigt: **Anmeldenamen '\<Login>' verwenden**, **Identität annehmen '\<Domain>\\<Anmeldename\>'** oder **Identität annehmen '\<Computer>\\<Anmeldename\>'** [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
 **Verbindung mit Abonnent**  
 Der Kontext, unter dem die Verbindung mit dem Abonnenten hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird.  
  
-   Bei Pullabonnements ist die lokale Verbindung diejenige mit dem Abonnenten. Daher wird in diesem Feld immer Folgendes angezeigt: **Identität annehmen '\<Domain>\\<Anmeldename\>'** oder **Identität annehmen '\<Computer>\\<Anmeldename\>'** für Pushabonnements  
  
-   Bei Pushabonnements kann die Verbindung auch unter dem Kontext einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung hergestellt werden. In dem Feld wird eine der folgenden Optionen angezeigt: **Anmeldenamen '\<Login>' verwenden**, **Identität annehmen '\<Domain>\\<Anmeldename\>'** oder **Identität annehmen '\<Computer>\\<Anmeldename\>'** [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern der Eigenschaften von Pullabonnements](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Anzeigen und Ändern der Eigenschaften von Pushabonnements](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Identität und Zugriffssteuerung (Replikation)](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [Sicherheitsmodell des Replikations-Agents](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Anzeigen und Ändern von Replikationssicherheitseinstellungen](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
