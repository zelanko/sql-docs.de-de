---
title: Optionen für die Abonnementüberprüfung (Mergeabonnements) | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.mergeoptions.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: 4958c4ab-2025-42ce-b836-6fb4e9e6f24d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d7631df4a1e4c6ec37effbc06b6a141b0d41ebc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63249300"
---
# <a name="subscription-validation-options-merge-subscriptions"></a>Optionen für die Abonnementüberprüfung (Mergeabonnements)
  Verwenden Sie das Dialogfeld Optionen für die **Abonnement** Überprüfung, um anzugeben, ob die Überprüfung nur die Zeilen Anzahl oder die Zeilen Anzahl und eine binäre Prüfsumme verwenden soll.  
  
## <a name="options"></a>Tastatur  
 **Nur Zeilenanzahl überprüfen**  
 Wählen Sie diese Option aus, um zu überprüfen, ob die Anzahl der Zeilen in der Tabelle auf dem Abonnenten mit der Anzahl der Zeilen in der Tabelle auf dem Verleger übereinstimmt. Mit dieser Methode wird nicht überprüft, ob die Inhalte der Zeilen übereinstimmen. Die Überprüfung der Zeilenanzahl bietet einen Überprüfungsansatz, der kaum Ressourcen beansprucht und Sie Probleme bei den Daten erkennen lässt.  
  
 **Die Zeilenanzahl überprüfen und Prüfsummen vergleichen, um die Zeilendaten zu überprüfen**  
 Zusätzlich zum Einbinden einer Reihe von Zeilen auf Verleger- und Abonnentenebene wird eine Prüfsumme aller Daten mit dem binären Prüfsummenalgorithmus berechnet. Ist die Zeilenanzahl fehlerhaft, wird die Berechnung der Prüfsumme nicht ausgeführt. Diese Option gilt nicht für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überprüfen der Daten am Abonnenten](validate-data-at-the-subscriber.md)   
 [Überprüfen von replizierten Daten](validate-data-at-the-subscriber.md)  
  
  
