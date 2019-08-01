---
title: Agentprofile (einzelner Agent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.profiles.perfprofileagentname.f1
helpviewer_keywords:
- Agent Profile dialog box
ms.assetid: 22713555-c496-4ce1-8ec7-4ae75cfadca8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 69358e8163fffb0cc09e7e910a24ebc47d92a3de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68027859"
---
# <a name="agent-profiles-single-agent"></a>Agentprofile (einzelner Agent)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mithilfe des Dialogfelds **Agentprofile** können Sie Agentprofile verwalten. Agentprofile stellen eine einfache Möglichkeit dar, die Laufzeitparameter jedes Agents zu verwalten. Jeder Agent verfügt über ein Standardprofil, und einige Agents verfügen über zusätzliche vordefinierte Profile. Der Merge-Agent verfügt z. B. über ein Profil für langsame Verbindungen, das für Verbindungen mit geringer Bandbreite angelegt wurde. Die vordefinierten Profile reichen für die meisten Anwendungen aus, aber Sie können auch benutzerdefinierte Profile erstellen, mit denen Sie das Verhalten der Agents je nach Bedarf anpassen können.  
  
## <a name="options"></a>enthalten  
 **Standardwert für Neu**  
 Wählen Sie das Profil aus, das verwendet werden soll, wenn für einen Agent des angegebenen Typs Aufträge erstellt werden. Wenn Sie z. B. mehrere Abonnements für eine Mergeveröffentlichung erstellen, wird für den Auftrag des Merge-Agents für jedes Abonnement das ausgewählte Profil verwendet. Wenn Sie das Profil für vorhandene Aufträge ändern möchten, wählen Sie ein Profil aus, und klicken Sie auf **Vorhandene Agents ändern**.  
  
 **Name**  
 Der Name des Profils.  
  
 **Typ**  
 Der Profiltyp: **Benutzer** (benutzerdefiniert) oder **System** (vordefiniert).  
  
 **Eigenschaften (...)**  
 Klicken Sie auf diese Option, um die Werte anzuzeigen, die für jeden Parameter im Agentprofil verwendet werden.  
  
 **Neu**  
 Klicken Sie hier, um ein neues Profil zu erstellen.  
  
 **Löschen**  
 Wählen Sie ein benutzerdefiniertes Profil aus, und klicken Sie auf **Löschen** , um dieses Profil zu löschen. Vordefinierte Profile können nicht gelöscht werden.  
  
 **Vorhandene Agents ändern**  
 Wählen Sie ein Profil aus, und klicken Sie dann auf **Vorhandene Agents ändern** , um anzugeben, dass alle vorhandenen Aufträge für einen Agent des angegebenen Typs das ausgewählte Profil verwenden sollen. Wenn Sie z. B. mehrere Abonnements für eine Mergeveröffentlichung erstellt haben und das Profil so ändern möchten, dass die Merge-Agentaufträge für alle diese Abonnements das **Agentprofil für langsame Links**verwenden, wählen Sie dieses Profil aus, und klicken Sie auf **Vorhandene Agents ändern**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Replikations-Agent-Profilen](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Replikations-Agents (Übersicht)](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Replikations-Agent-Profile](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  
