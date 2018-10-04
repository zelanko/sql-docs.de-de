---
title: Eigenschaften der Verteilungsdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distdbproperties.f1
helpviewer_keywords:
- Distribution Database Properties dialog box
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0412108c9b08e8b3345f4930b4076e10c96ec2ce
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207710"
---
# <a name="distribution-database-properties"></a>Eigenschaften der Verteilungsdatenbank
  Mithilfe des Dialogfelds **Eigenschaften der Verteilungsdatenbank** können Sie eine Reihe von Eigenschaften anzeigen und die Transaktionsbeibehaltungsdauer und die Aufbewahrungsdauer für den Verlauf für die Datenbank festlegen.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Der Name der Verteilungsdatenbank. Der Standardwert ist 'distribution' (schreibgeschützt).  
  
 **Dateipfade**  
 Der Speicherort der Datenbankdatei und der Protokolldatei (schreibgeschützt).  
  
 **Transaktionsbeibehaltungsdauer**  
 Wird auch als Beibehaltungsdauer für die Verteilung bezeichnet. Der Zeitraum, für den Transaktionen für die Transaktionsreplikation gespeichert werden. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
 **Aufbewahrungsdauer für Verlauf**  
 Der Zeitraum, für den die Metadaten des Verlaufs für jede Art von Replikation gespeichert werden.  
  
 **Sicherheit für den Warteschlangenlese-Agent**  
 Der Warteschlangenlese-Agent wird von Transaktionsreplikationen verwendet, die Abonnements mit verzögertem Update über eine Warteschlange zulassen. Ein Warteschlangenlese-Agent wird automatisch erstellt, wenn Sie die Option **Transaktionsveröffentlichung mit Updateabonnements** auf der Seite **Veröffentlichungstyp** des Assistenten für neue Veröffentlichung auswählen. Klicken Sie auf **Sicherheitseinstellungen…** , um das Konto zu ändern, unter dem der Agent ausgeführt wird und Verbindungen mit dem Verteiler herstellt.  
  
 Eine Warteschlangenlese-Agent kann auch erstellt werden, indem Sie auf dieser Seite die Option **Warteschlangenlese-Agent erstellen** auswählen (diese Option ist nicht verfügbar, wenn der Agent bereits erstellt wurde).  
  
 Für den Warteschlangenlese-Agent werden zusätzliche Verbindungsinformationen an zwei Stellen angegeben:  
  
-   Die Verbindung mit dem Verleger stellt der Agent mithilfe der Anmeldeinformationen her, die im Dialogfeld **Verlegereigenschaften** angegeben sind. Es ist auf der Seite **Verleger** des Dialogfelds **Verteilereigenschaften** verfügbar.  
  
-   Die Verbindung mit dem Abonnenten stellt der Agent mithilfe der Anmeldeinformationen her, die für den Verteilungs-Agent im Assistenten für neue Abonnements angegeben sind.  
  
 Weitere Informationen finden Sie unter  \\[Replication Agent Security Model](security/replication-agent-security-model.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilung konfigurieren](configure-distribution.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)  
  
  
