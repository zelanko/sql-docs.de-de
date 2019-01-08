---
title: Sicherheit für den Merge-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.MA.f1
helpviewer_keywords:
- Merge Agent Security dialog box
ms.assetid: 9b86171a-4381-4b39-869a-cdc161e7cd15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 47571fcfe6b11945ab910f40feeb35145ab8d2a3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52765082"
---
# <a name="merge-agent-security"></a>Sicherheit für den Merge-Agent
  Im Dialogfeld **Sicherheit für den Merge-Agent** können Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto angeben, unter dem der Merge-Agent ausgeführt wird. Der Merge-Agent wird für Pushabonnements auf dem Verteiler und für Pullabonnements auf dem Abonnenten ausgeführt. Das Windows-Konto wird auch als *Prozesskonto*bezeichnet, da der Agentprozess unter diesem Konto ausgeführt wird. Abhängig davon, wie Sie auf dieses Dialogfeld zugreifen, stehen zusätzliche Optionen zur Verfügung:  
  
-   Wenn Sie das Dialogfeld über den Assistenten für neue Abonnements aufrufen, können Sie auch den Kontext angeben, unter dem der Merge-Agent Verbindungen mit dem Abonnenten (bei Pushabonnements) oder dem Verleger und Verteiler (bei Pullabonnements) herstellt. Die Verbindung kann entweder mithilfe des Windows-Kontos oder unter dem Kontext eines von Ihnen angegebenen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Kontos hergestellt werden.  
  
-   Im Falle eines Zugriffs über das Dialogfeld **Abonnementeigenschaften** geben Sie den Kontext ein, unter dem der Merge-Agent Verbindungen herstellen soll, indem Sie in der Zeile**Abonnentenverbindung**bzw. **Verlegerverbindung** dieses Dialogfelds auf die **Schaltfläche mit den drei Punkten** klicken. Weitere Informationen zum Zugreifen auf die **Abonnementeigenschaften** im Dialogfeld finden Sie unter [anzeigen und Ändern der Eigenschaften von Pushabonnements](view-and-modify-push-subscription-properties.md) und Gewusst wie: [Anzeigen und Ändern der Eigenschaften von Pullabonnements](view-and-modify-pull-subscription-properties.md).  
  
 Alle Konten müssen gültig sein, und für jedes Konto muss das richtige Kennwort angegeben sein. Konten und Kennwörter werden erst bei der Ausführung eines Agents überprüft.  
  
## <a name="options"></a>Optionen  
 **Process Account**  
 Geben Sie ein Windows-Konto ein, unter dem der Merge-Agent ausgeführt wird.  
  
-   Bei Pushabonnements muss das Konto folgende Voraussetzungen erfüllen:  
  
    -   Es muss mindestens Mitglied der festen Datenbankrolle **db_owner** in der Verteilungsdatenbank sein.  
  
    -   Es muss Mitglied der Veröffentlichungszugriffsliste sein.  
  
    -   Die Anmeldung muss mit einem Benutzer in der Veröffentlichungsdatenbank verknüpft sein.  
  
    -   Es muss über Leseberechtigungen für die Momentaufnahmefreigabe verfügen.  
  
-   Bei Pullabonnements muss das Konto mindestens Mitglied der festen Datenbankrolle **db_owner** in der Abonnementdatenbank sein.  
  
 Zusätzliche Berechtigungen sind erforderlich, wenn beim Herstellen von Verbindungen die Identität des Prozesskontos angenommen wird. Siehe nachstehende Abschnitte **Verbindung mit dem Verleger und mit dem Verteiler herstellen** und **Verbindung mit dem Abonnenten herstellen** .  
  
 **Process Account** kann bei Pullabonnements für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]nicht angegeben werden, da der Merge-Agent auf Instanzen von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
 **Kennwort** und **Kennwort bestätigen**  
 In diese Felder geben Sie das Kennwort für das Windows-Konto ein.  
  
 **Verbindung mit dem Verleger und mit dem Verteiler herstellen**  
 Bei Pushabonnements werden Verbindungen mit dem Verleger und dem Verteiler immer hergestellt, indem der Agent die Identität des im Textfeld **Prozesskonto** angegebenen Kontos annimmt.  
  
 Bei Pullabonnements müssen Sie auswählen, ob der Merge-Agent die Verbindungen mit dem Verleger und dem Verteiler entweder durch Annahme der Identität des im Textfeld **Prozesskonto** angegebenen Kontos oder mithilfe eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Kontos herstellt. Wenn Sie sich für ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto entscheiden, müssen Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzernamen und ein Kennwort eingeben.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, kein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto zu verwenden und stattdessen festzulegen, dass der Agent die Identität des Windows-Kontos annimmt.  
  
 Das für die Verbindung verwendete Windows-Konto bzw. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto muss die folgenden Voraussetzungen erfüllen:  
  
-   Es muss Mitglied der Veröffentlichungszugriffsliste sein.  
  
-   Die Anmeldung muss mit einem Benutzer in der Veröffentlichungsdatenbank verknüpft sein.  
  
-   Die Anmeldung muss mit einem Benutzer in der Verteilungsdatenbank verknüpft sein (der Benutzer kann der Gastbenutzer sein).  
  
-   Es muss über Leseberechtigungen für die Momentaufnahmefreigabe verfügen.  
  
 **Verbindung mit dem Abonnenten herstellen**  
 Bei Pullabonnements wird eine Verbindung mit dem Abonnenten immer hergestellt, indem die Identität des im Textfeld **Prozesskonto** angegebenen Kontos angenommen wird.  
  
 Bei Pushabonnements müssen Sie auswählen, ob der Merge-Agent die Verbindungen mit dem Verleger und dem Verteiler entweder durch Annahme der Identität des im Textfeld **Prozesskonto** angegebenen Kontos oder mithilfe eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Kontos herstellt. Wenn Sie sich für ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto entscheiden, müssen Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzernamen und ein Kennwort eingeben.  
  
> [!NOTE]  
>  Es wird empfohlen, kein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto zu verwenden und stattdessen festzulegen, dass der Agent die Identität des Windows-Kontos annimmt.  
  
 Das für die Verbindung mit dem Abonnenten verwendete Windows-Konto bzw. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto muss mindestens Mitglied der festen Datenbankrolle **db_owner** in der Abonnementdatenbank sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Anmeldeinformationen und Kennwörtern bei der Replikation](security/manage-logins-and-passwords-in-replication.md)   
 [Sicherheitsmodell des Replikations-Agents](security/replication-agent-security-model.md)   
 [Replikations-Agents (Übersicht)](agents/replication-agents-overview.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
