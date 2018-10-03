---
title: Erkennen und Beseitigen von Konflikten bei der Mergereplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- conflict resolution [SQL Server replication]
- viewing merge replication conflicts
- resolving merge replication conflicts
- articles [SQL Server replication], conflict resolution
- merge replication conflict resolution [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7da5ae2c327410f7904f712ecd83516b983b894c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170360"
---
# <a name="detect-and-resolve-merge-replication-conflicts"></a>Erkennen und Beseitigen von Konflikten bei der Mergereplikation
  Wenn zwischen einem Verleger und einem Abonnenten eine Verbindung besteht und die Synchronisierung vorgenommen wird, werden jegliche Konflikte vom Merge-Agent erkannt. Wenn Konflikte erkannt werden, legt der Merge-Agent mithilfe eines Konfliktlösers fest, welche Daten akzeptiert und für andere Sites weitergegeben werden.  
  
> [!NOTE]  
>  Obwohl ein Abonnement die Synchronisierung mit dem Verleger vornimmt, treten Konflikte in der Regel zwischen Updates auf, die auf verschiedenen Abonnenten vorgenommen wurden, und nicht notwendigerweise zwischen Updates auf einem Abonnenten und dem Verleger.  
  
 Die Mergereplikation bietet eine Reihe unterschiedlicher Methoden zur Erkennung und Lösung von Konflikten. Für die meisten Anwendungen empfiehlt sich die Standardmethode.  
  
-   Wenn es zwischen einem Verleger und einem Abonnenten zu einem Konflikt kommt, wird die Verlegeränderung beibehalten und die Abonnentenänderung verworfen.  
  
-   Wenn es zwischen zwei Abonnenten bei der Verwendung von Clientabonnements (dem Standardtyp für Pullabonnements) zu einem Konflikt kommt, wird die Änderung des Abonnenten beibehalten, der als erster die Synchronisierung mit dem Verleger vornimmt. Die Änderung des zweiten Abonnenten wird verworfen. Informationen zum Angeben von Client- und Serverabonnements finden Sie unter [Angeben eines Mergeabonnementtyps und einer Konfliktlösungspriorität &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md).  
  
-   Wenn es zwischen zwei Abonnenten bei der Verwendung von Serverabonnements (dem Standardtyp für Pushabonnements) zu einem Konflikt kommt, wird die Änderung des Abonnenten mit dem höchsten priority-Wert beibehalten, die Änderung des zweiten Abonnenten wird verworfen. Wenn die priority-Werte identisch sind, wird die Änderung des Abonnenten beibehalten, der als erster die Synchronisierung mit dem Verleger vornimmt.  
  
 Weitere Informationen zur Konflikterkennung und -lösung bei der Mergereplikation finden Sie unter [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Article Options for Merge Replication](article-options-for-merge-replication.md)   
 [Abonnieren von Veröffentlichungen](../subscribe-to-publications.md)  
  
  
