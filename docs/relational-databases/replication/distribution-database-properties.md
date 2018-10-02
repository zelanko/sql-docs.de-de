---
title: Eigenschaften der Verteilungsdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.distdbproperties.f1
helpviewer_keywords:
- Distribution Database Properties dialog box
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97e6fea955e2ee82250f094fcf9f2bf76b15f452
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701158"
---
# <a name="distribution-database-properties"></a>Eigenschaften der Verteilungsdatenbank
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mithilfe des Dialogfelds **Eigenschaften der Verteilungsdatenbank** können Sie eine Reihe von Eigenschaften anzeigen und die Transaktionsbeibehaltungsdauer und die Aufbewahrungsdauer für den Verlauf für die Datenbank festlegen.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Der Name der Verteilungsdatenbank. Der Standardwert ist 'distribution' (schreibgeschützt).  
  
 **Dateipfade**  
 Der Speicherort der Datenbankdatei und der Protokolldatei (schreibgeschützt).  
  
 **Transaktionsbeibehaltungsdauer**  
 Wird auch als Beibehaltungsdauer für die Verteilung bezeichnet. Der Zeitraum, für den Transaktionen für die Transaktionsreplikation gespeichert werden. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Aufbewahrungsdauer für Verlauf**  
 Der Zeitraum, für den die Metadaten des Verlaufs für jede Art von Replikation gespeichert werden.  
  
 **Sicherheit für den Warteschlangenlese-Agent**  
 Der Warteschlangenlese-Agent wird von Transaktionsreplikationen verwendet, die Abonnements mit verzögertem Update über eine Warteschlange zulassen. Ein Warteschlangenlese-Agent wird automatisch erstellt, wenn Sie die Option **Transaktionsveröffentlichung mit Updateabonnements** auf der Seite **Veröffentlichungstyp** des Assistenten für neue Veröffentlichung auswählen. Klicken Sie auf **Sicherheitseinstellungen…** , um das Konto zu ändern, unter dem der Agent ausgeführt wird und Verbindungen mit dem Verteiler herstellt.  
  
 Eine Warteschlangenlese-Agent kann auch erstellt werden, indem Sie auf dieser Seite die Option **Warteschlangenlese-Agent erstellen** auswählen (diese Option ist nicht verfügbar, wenn der Agent bereits erstellt wurde).  
  
 Für den Warteschlangenlese-Agent werden zusätzliche Verbindungsinformationen an zwei Stellen angegeben:  
  
-   Die Verbindung mit dem Verleger stellt der Agent mithilfe der Anmeldeinformationen her, die im Dialogfeld **Verlegereigenschaften** angegeben sind. Es ist auf der Seite **Verleger** des Dialogfelds **Verteilereigenschaften** verfügbar.  
  
-   Die Verbindung mit dem Abonnenten stellt der Agent mithilfe der Anmeldeinformationen her, die für den Verteilungs-Agent im Assistenten für neue Abonnements angegeben sind.  
  
 Weitere Informationen finden Sie unter  [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
