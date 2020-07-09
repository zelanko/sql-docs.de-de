---
title: Speicherort des &lt;AgentName&gt;-Agents | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.agentlocation.f1
ms.assetid: dc664d80-fbe3-4586-aba8-a71fa62d14f0
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: c44303cdfde6549c908e024a199f7b4635b46c7f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730243"
---
# <a name="ltagentnamegt-agent-location"></a>Speicherort des &lt;AgentName&gt;-Agents
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Der Merge-Agent (für Mergeabonnements) und der Verteiler-Agent (für Transaktions- und Momentaufnahme-Abonnements) werden auf dem Verteiler oder auf dem Abonnenten ausgeführt. Wenn der Agent auf dem Verteiler ausgeführt wird, wird das Abonnement als Pushabonnement, und bei Ausführung auf dem Abonnenten als Pullabonnement bezeichnet. Weitere Informationen zu Push- und Pullabonnements finden Sie unter [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md). Die in diesem Schritt des Assistenten erstellten Abonnements gehören dem ausgewählten Typ an. Um Abonnements beider Typen zu erstellen, müssen Sie den Assistenten zweimal ausführen.  
  
> [!NOTE]  
>  Nach dem Erstellen eines Abonnements kann der Abonnementtyp nicht mehr geändert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Übersicht über Replikations-Agents](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
