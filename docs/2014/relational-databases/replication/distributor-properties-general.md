---
title: Verteilereigenschaften (Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distproperties.general.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: ab4120ec-e524-4c0c-8b48-f2f40adb1a3b
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d2a32e262bd8096ad77ce0ea813e7ced8440c1dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324180"
---
# <a name="distributor-properties-general"></a>Verteilereigenschaften (Allgemein)
  Mithilfe der Seite **Allgemein** des Dialogfelds **Verteilereigenschaften** können Sie Verteilungsdatenbanken hinzufügen und löschen sowie Eigenschaften von Verteilungsdatenbanken festlegen.  
  
 Die Verteilungsdatenbank speichert Metadaten und Verlaufsdaten für alle Replikationstypen und Transaktionen für die Transaktionsreplikation. In vielen Fällen reicht eine Verteilungsdatenbank aus. Wenn jedoch mehrere Verleger einen Verteiler verwenden, sollten Sie die Erstellung einer Verteilungsdatenbank für jeden Verleger in Betracht ziehen. Auf diese Weise stellen Sie sicher, dass die durch jede Verteilungsdatenbank fließenden Daten eindeutig sind.  
  
## <a name="options"></a>Tastatur  
 **Datenbanken**  
 Das Eigenschaftenraster **Datenbanken** zeigt den Namen und die Beibehaltungseigenschaften der Verteilungsdatenbanken auf dem Verteiler an. **Transaktionsbeibehaltung** ist die Dauer, die Transaktionen für die Transaktionsreplikation gespeichert werden (die Transaktionsbeibehaltung wird auch als Verteilungsbeibehaltung bezeichnet). **Verlaufsbeibehaltung** ist die Dauer, die Metadaten des Verlaufs für jede Art von Replikation gespeichert werden. Weitere Informationen zu Beibehaltungsdauer finden Sie unter [Abonnementablauf und -deaktivierung](subscription-expiration-and-deactivation.md).  
  
 Klicken Sie im Eigenschaftenraster **Datenbanken**auf die Eigenschaftenschaltfläche (die Schaltfläche mit den **drei Punkten**), um das Dialogfeld **Eigenschaften der Verteilungsdatenbank** zu öffnen.  
  
 **Neu**  
 Erstellt eine neue Verteilungsdatenbank  
  
 **Delete**  
 Wählen Sie im Eigenschaftenraster **Datenbanken** eine vorhandene Verteilungsdatenbank aus, und klicken Sie auf **Löschen** , um die Datenbank zu löschen. Die Verteilungsdatenbank kann nicht gelöscht werden, wenn es die einzige Datenbank dieser Art ist. Jeder Verteiler muss zumindest eine Verteilungsdatenbank besitzen. Zum Löschen aller Verteilungsdatenbanken müssen Sie die Verteilung auf dem Computer deaktivieren. Weitere Informationen finden Sie unter [Deaktivieren der Veröffentlichung und Verteilung](disable-publishing-and-distribution.md).  
  
 **Profilstandards**  
 Klicken Sie auf diese Option, um auf die Replikations-Agentprofile im Dialogfeld **Agentprofile** zuzugreifen. Weitere Informationen zu Profilen finden Sie unter [Replication Agent Profiles](agents/replication-agent-profiles.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilung konfigurieren](configure-distribution.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)  
  
  
