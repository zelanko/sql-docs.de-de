---
title: 'Aufgabe 8: Erstellen einer Verbunddomänenregel | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 18461e889e56f647b869d2b60cae49d662786160
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161253"
---
# <a name="task-8-creating-a-composite-domain-rule"></a>Aufgabe 8: Erstellen einer Verbunddomänenregel
  In dieser Aufgabe erstellen Sie eine Regel für die **Address Validation** verbunddomäne. Sie definieren eine domänenübergreifende Regel: Wenn **City** ist **Los Angeles**, **Status** muss **Zertifizierungsstelle** , in denen **City** und **Zustand** zwei Domänen sind.  
  
1.  Wechseln Sie im rechten Bereich in der **VD-Regeln** Registerkarte.  
  
2.  Klicken Sie auf **Fügt eine neue domänenregel hinzu** aus der Symbolleiste.  
  
3.  Typ **City Regel** für **Namen** , und drücken Sie **EINGABETASTE**.  
  
4.  In der **erstellen Sie eine Regel** klicken Sie im Bereich **City** in der Domänenliste aus, und wählen Sie die Bedingung **Wert ist gleich** und Typ **Los Angeles** für die Wert.  
  
5.  In der **dann** klicken Sie im Bereich **Status** in der Domänenliste aus, und wählen **Wert ist gleich**, Typ **Zertifizierungsstelle** für Wert ein, und drücken Sie **Registerkarte**.  
  
     ![Verbunddomänenregel](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "Verbunddomänenregel")  
  
6.  Klicken Sie auf **schließen** am unteren Rand der Seite So wechseln Sie zur Hauptseite des DQS-Client. In der nächsten Lektion veröffentlichen Sie die Wissensdatenbank. Beachten Sie, dass die Wissensdatenbank gesperrt ist (Schlosssymbol).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 9: Konfigurieren eines Reference Data Service](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  