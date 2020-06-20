---
title: Neues Agentprofil | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.newperfprofile.f1
helpviewer_keywords:
- New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0fcdca4d57b21855a959a876c0c9c9344487046b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060667"
---
# <a name="new-agent-profile"></a>Neues Agentprofil
  Im Dialogfeld **Neues Agentprofil** können Sie ein neues Profil erstellen. Neue Profile werden immer auf der Basis von vorhandenen Profilen erstellt. Sie können jedoch so geändert werden, dass bestimmte Anforderungen von Anwendungen erfüllt werden. Nach dem Erstellen kann das Profil auf vorhandene und zukünftige Agentaufträge im Dialogfeld **Agentprofile** angewendet werden. Agentparameterwerte können im \<**AgentProfileName> Dialogfeld Eigenschaften * * bearbeitet werden.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen Namen für das Profil ein.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung für das Profil ein.  
  
 **Parameter**  
 Die im Profil enthaltenen Agentparameter. In dem Profil, das als Basis für das neue Profil fungiert, müssen nicht notwendigerweise für alle Parameter Werte angegeben sein. Wenn Sie alle für einen bestimmten Agent gültigen Parameter anzeigen möchten, müssen Sie das Kontrollkästchen **Nur die in diesem Profil verwendeten Parameter anzeigen** deaktivieren. Eine Beschreibung der einzelnen Parameter finden Sie unter:  
  
-   [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
-   [Replikationsprotokolllese-Agent](agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](agents/replication-distribution-agent.md)  
  
-   [Replication Merge Agent](agents/replication-merge-agent.md)  
  
-   [Replication Queue Reader Agent](agents/replication-queue-reader-agent.md)  
  
 **Standardwert**  
 Der Standardwert für jeden Agentparameter.  
  
 **Wert**  
 Der für den Parameter angegebene Wert in dem Profil, das als Basis für das neue Profil fungiert. Bearbeiten Sie dieses Feld für alle Parameterwerte, die Sie ändern möchten.  
  
 **Nur die in diesem Profil verwendeten Parameter anzeigen**  
 Deaktivieren Sie das Kontrollkästchen, um nur die für einen bestimmten Agent gültigen Parameter anzuzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Replikations-Agent-Profilen](agents/work-with-replication-agent-profiles.md)   
 [Replikations-Agents (Übersicht)](agents/replication-agents-overview.md)   
 [Replikations-Agent-Profile](agents/replication-agent-profiles.md)  
  
  
