---
title: Aktualisierbare Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 00d51c24583231f28ec15dd86c1848ba95c345d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63255393"
---
# <a name="updatable-subscriptions"></a>Aktualisierbare Abonnements
  Bei der Transaktions Replikation sollten replizierte Daten als schreibgeschützt behandelt werden. Sie können jedoch replizierte Daten auf einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten ändern, indem Sie aktualisierbare Abonnements verwenden. Wenn Sie Daten auf dem Abonnenten ändern möchten, wählen Sie in Abhängigkeit von Ihren Anforderungen eine der folgenden Optionen aus:  
  
|Aktualisierbarer Abonnementtyp|Requirements (Anforderungen)|  
|---------------------------------|------------------|  
|Sofortige Updates|Verleger und Abonnent müssen verbunden sein, damit Daten auf dem Abonnenten aktualisiert werden können.|  
|Verzögerte Updates über eine Warteschlange|Verleger und Abonnent müssen nicht verbunden sein, damit Daten auf dem Abonnenten aktualisiert werden können. Updates können zunächst offline vorgenommen und später dann zwischen Verleger und Abonnent synchronisiert werden.|  
  
## <a name="options"></a>Tastatur  
 **Abonnenten Änderungen replizieren**  
 Aktivieren Sie das Kontrollkästchen in der **Replizieren** -Spalte für jeden Abonnenten, der in der Lage sein soll, Updates vorzunehmen. Für jene Abonnenten, die Updates vornehmen können, wählen Sie aus dem Dropdownlistenfeld in der **Commit auf Verleger ausführen** -Spalte die entsprechende Option aus.  
  
-   Für ein Abonnement mit sofortigem Update wählen Sie **Commit für Änderungen gleichzeitig ausführen** aus.  
  
-   Für ein Abonnement mit verzögertem Update über eine Warteschlange wählen Sie **Änderungen in die Warteschlange einreihen und Commit baldmöglichst ausführen** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)   
 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
