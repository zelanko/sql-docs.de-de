---
title: 'Tutorial: Replizieren von Daten mit mobilen Clients | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c36eae0ca3d9613dfdaf13bce3a5e748f91b123f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63255394"
---
# <a name="tutorial-replicating-data-with-mobile-clients"></a>Tutorial: Replizieren von Daten mit mobilen Clients
  Die Replikation stellt eine geeignete Lösung für das Problem des Verschiebens von Daten zwischen einem zentralen Server und mobilen Clients dar, die nur gelegentlich miteinander verbunden sind. Mithilfe von Replikations-Assistenten können Sie eine Replikationstopologie auf einfache Weise konfigurieren und verwalten. In diesem Lernprogramm wird die Konfiguration einer Replikationstopologie für mobile Clients erläutert.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm werden mithilfe einer Mergereplikation Daten aus einer zentralen Datenbank für einen oder für mehrere mobile Benutzer veröffentlicht, sodass jeder Benutzer eine eindeutig gefilterte Teilmenge von Daten erhält. In der ersten Lektion wird die Verwendung von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zum Erstellen einer Veröffentlichung erläutert. In darauf folgenden Lektionen wird erläutert, wie ein Abonnement erstellt und synchronisiert wird.  
  
## <a name="requirements"></a>Anforderungen  
 Dieses Lernprogramm ist für Benutzer vorgesehen, die mit grundlegenden Datenbankvorgängen vertraut sind, aber nur über begrenzte Kenntnisse in Bezug auf die Replikation verfügen. Bevor Sie dieses Tutorial starten, sollten Sie Folgendes abgeschlossen haben: [Tutorial: Vorbereiten des Servers für die Replikation](tutorial-preparing-the-server-for-replication.md).  
  
 Ihr System muss die folgenden installierten Komponenten aufweisen, damit dieses Lernprogramm verwendet werden kann:  
  
-   Auf dem Verlegerserver (Quelle):  
  
    -   Eine beliebige Edition von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]mit Ausnahme von Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) und [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Diese Editionen können nicht als Replikationsverleger fungieren.  
  
    -   Die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert.  
  
-   Abonnentenserver (Ziel):  
  
    -   Eine beliebige Edition von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]mit Ausnahme von [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] wird nicht von der in diesem Lernprogramm erstellten Veröffentlichung unterstützt.  
  
    > [!NOTE]  
    >  Die Replikation wird bei [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]nicht standardmäßig installiert.  
  
> [!NOTE]  
>  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]muss eine Verbindung mit dem Verleger und dem Abonnenten hergestellt werden. Dazu wird ein Anmeldename verwendet, der Mitglied der festen Serverrolle sysadmin ist.  
  
 **Ungefähre Dauer dieses Tutorials: 30 Minuten.**  
  
## <a name="lessons-in-this-tutorial"></a>Lektionen in diesem Lernprogramm  
  
-   [Lektion 1: Veröffentlichen von Daten mithilfe der Mergereplikation](lesson-1-publishing-data-using-merge-replication.md)  
  
-   [Lektion 2: Erstellen eines Abonnements für die Mergeveröffentlichung](lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
 [Lernprogramm starten](merge/merge-replication.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Konzepte für die Replikationsprogrammierung](concepts/replication-programming-concepts.md)  
  
  
