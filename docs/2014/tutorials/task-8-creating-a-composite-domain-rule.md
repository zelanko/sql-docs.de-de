---
title: 'Aufgabe 8: Erstellen einer Verbund Domänen Regel | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7e40ec982a9b2c43c3d55ec60179ac9a0b80e8a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489630"
---
# <a name="task-8-creating-a-composite-domain-rule"></a>Aufgabe 8: Erstellen einer Verbunddomänenregel
  In dieser Aufgabe erstellen Sie eine Regel für die Verbund Domäne der **Adressvalidierung** . Sie definieren eine Domänen übergreifende Regel: Wenn **Stadt** " **Los Angeles**" ist, muss der **Status** " **ca** " lauten, wobei " **City** " und " **State** " zwei Domänen  
  
1.  Wechseln Sie im rechten Bereich zur Registerkarte für die **CD-Regeln** .  
  
2.  Klicken Sie auf der Symbolleiste auf **neue Domänen Regel hinzufügen** .  
  
3.  Geben Sie **City-State Rule** für **Name** ein, und drücken **Sie Eingabe**Taste.  
  
4.  Wählen Sie im Bereich **Regel erstellen** in der Liste Domäne die Option **Stadt** aus, und wählen Sie Bedingungs **Wert ist gleich** aus, und geben Sie für den Wert den Wert **Los Angeles** ein.  
  
5.  Wählen Sie im **Then** -Bereich **State** in der Liste Domäne aus, und wählen Sie **Wert ist gleich**aus, geben Sie **ca** als Wert ein, und drücken Sie die **Tab**-Taste.  
  
     ![Verbunddomänenregel](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "Verbunddomänenregel")  
  
6.  Klicken Sie am unteren Rand der Seite auf die Schaltfläche **Schließen** , um zur Hauptseite des DQS-Clients zu wechseln. In der nächsten Lektion veröffentlichen Sie die Wissensdatenbank. Beachten Sie, dass die Wissensdatenbank gesperrt ist (Schlosssymbol).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 9: Konfigurieren eines Reference Data Service](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
