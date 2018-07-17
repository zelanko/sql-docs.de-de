---
title: Alle Abonnements überprüfen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.allsubscriptions.f1
helpviewer_keywords:
- Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1c780d50dbe246c8d725d960624eef652ffd29a3
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37358192"
---
# <a name="validate-all-subscriptions"></a>Alle Abonnements überprüfen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Im Dialogfeld **Alle Abonnements überprüfen** können Sie angeben, dass alle Abonnements für eine Mergeveröffentlichung überprüft werden sollen, sobald der Merge-Agent für die einzelnen Abonnements das nächste Mal ausgeführt wird. Die Ergebnisse der Überprüfung werden im Replikationsmonitor angezeigt. Weitere Informationen finden Sie unter [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
 Wenn Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mit der rechten Maustaste auf ein Abonnement klicken und dann auf **Abonnement überprüfen**klicken, können Sie auch ein einzelnes Abonnement überprüfen.  
  
## <a name="options"></a>Tastatur  
 **Nur Zeilenanzahl überprüfen**  
 Wählen Sie diese Option aus, um zu überprüfen, ob die Anzahl der Zeilen in der Tabelle auf dem Abonnenten mit der Anzahl der Zeilen in der Tabelle auf dem Verleger übereinstimmt. Mit dieser Methode wird nicht überprüft, ob die Inhalte der Zeilen übereinstimmen. Die Überprüfung der Zeilenanzahl bietet einen Überprüfungsansatz, der kaum Ressourcen beansprucht und Sie Probleme bei den Daten erkennen lässt.  
  
 **Die Zeilenanzahl überprüfen und Prüfsummen vergleichen, um die Zeilendaten zu überprüfen**  
 Zusätzlich zum Einbinden einer Reihe von Zeilen auf Verleger- und Abonnentenebene wird eine Prüfsumme aller Daten mit dem binären Prüfsummenalgorithmus berechnet. Ist die Zeilenanzahl fehlerhaft, wird die Berechnung der Prüfsumme nicht ausgeführt. Diese Option gilt nicht für [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überprüfen von replizierten Daten](../../relational-databases/replication/validate-replicated-data.md)  
  
  
