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
ms.openlocfilehash: b8c9e2d0f20a91bb11c0d5e08aff00c27785818e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047588"
---
# <a name="tutorial-replicating-data-with-mobile-clients"></a>Lernprogramm: Replizieren von Daten mit mobilen Clients
  Die Replikation stellt eine geeignete Lösung für das Problem des Verschiebens von Daten zwischen einem zentralen Server und mobilen Clients dar, die nur gelegentlich miteinander verbunden sind. Mithilfe von Replikations-Assistenten können Sie eine Replikationstopologie auf einfache Weise konfigurieren und verwalten. In diesem Lernprogramm wird die Konfiguration einer Replikationstopologie für mobile Clients erläutert.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm werden mithilfe einer Mergereplikation Daten aus einer zentralen Datenbank für einen oder für mehrere mobile Benutzer veröffentlicht, sodass jeder Benutzer eine eindeutig gefilterte Teilmenge von Daten erhält. In der ersten Lektion wird die Verwendung von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zum Erstellen einer Veröffentlichung erläutert. In darauf folgenden Lektionen wird erläutert, wie ein Abonnement erstellt und synchronisiert wird.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Dieses Lernprogramm ist für Benutzer vorgesehen, die mit grundlegenden Datenbankvorgängen vertraut sind, aber nur über begrenzte Kenntnisse in Bezug auf die Replikation verfügen. Bevor Sie dieses Tutorial starten, müssen Sie das [Tutorial: Vorbereiten des Servers für die Replikation](tutorial-preparing-the-server-for-replication.md)abschließen.  
  
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
  
 **Geschätzte Zeit bis zum Abschluss dieses Tutorials: 30 Minuten.**  
  
## <a name="lessons-in-this-tutorial"></a>Lektionen in diesem Lernprogramm  
  
-   [Lektion 1: Veröffentlichen von Daten mithilfe der Mergereplikation](lesson-1-publishing-data-using-merge-replication.md)  
  
-   [Lektion 2: Erstellen eines Abonnements für die Mergeveröffentlichung](lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
 [Lernprogramm starten](merge/merge-replication.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte für die Replikationsprogrammierung](concepts/replication-programming-concepts.md)  
  
  
