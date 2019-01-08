---
title: Verlegereigenschaften - Verteiler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b6425c4e0dc5175fd9404c1654168e6d79c7b7b5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52764862"
---
# <a name="publisher-properties---distributor"></a>Verlegereigenschaften - Verteiler
  Mithilfe des Dialogfelds **Verlegereigenschaften** können Sie mit der Beziehung zwischen dem Verleger und dem Verteiler verknüpfte Eigenschaften anzeigen und ändern.  
  
## <a name="options"></a>Optionen  
 **Agentverbindung mit dem Verleger**  
 Geben Sie den Kontext an, in dem die folgenden Agenten Verbindungen vom Verteiler zum Verleger herstellen können:  
  
-   Der Warteschlangenlese-Agent für Transaktionsveröffentlichungen, die Abonnements mit verzögertem Update über eine Warteschlange gestatten.  
  
-   Der Momentaufnahme-Agent und der Protokolllese-Agent für Oracle-Veröffentlichungen.  
  
 Wählen Sie **Identität des Agentprozesskontos annehmen** aus, um Verbindungen mit dem Verleger mithilfe des Kontexts des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Kontos herzustellen, unter dem diese Agents ausgeführt werden, oder geben Sie **SQL Server-Authentifizierung**an, und geben Sie dann einen Wert für **Benutzername** und **Kennwort**ein. Es wird empfohlen, **Identität des Agentprozesskontos annehmen**auszuwählen. Weitere Informationen zur Agentsicherheit finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
 Die Windows-Konten, unter denen diese Agents ausgeführt werden, werden im Assistenten für neue Veröffentlichung angegeben. Diese Konten können geändert werden:  
  
-   Im Dialogfeld **Verteilereigenschaften** für den Warteschlangenlese-Agent.  
  
-   Im Dialogfeld **Veröffentlichungseigenschaften** für den Momentaufnahme-Agent und den Protokolllese-Agent.  
  
 **Sonstiges**  
 Die Eigenschaften **Verlegertyp** und **Name der Verteilungsdatenbank** sind schreibgeschützt. Die Eigenschaft **Standardmomentaufnahmeordner** kann geändert werden. Weitere Informationen zum Momentaufnahmeordner finden Sie unter [Sichern des Momentaufnahmeordners](security/secure-the-snapshot-folder.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Publication](publish/create-a-publication.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)   
 [Eigenschaftenreferenz &#40;Replikation&#41;](properties-reference-replication.md)  
  
  
