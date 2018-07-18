---
title: 'Aufgabe 4: Festlegen von Domänenregeln | Microsoft Docs'
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
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 89e0027b3bf1748fb68a8b6922c45572a7b41bb7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057724"
---
# <a name="task-4-setting-domain-rules"></a>Aufgabe 4: Festlegen von Domänenregeln
  In dieser Aufgabe erstellen Sie eine Regel für die **Contact Email** Domäne zu überprüfen, ob die e-Mail-Adresse endet **@adventure-works.com**. Finden Sie unter [Erstellen einer Domänenregel](http://msdn.microsoft.com/library/hh510397.aspx) Weitere Informationen auf der Seite.  
  
1.  Klicken Sie auf **Contact Email** in der **Domänenliste**.  
  
2.  Wechseln Sie zu der **Domänenregeln** Registerkarte im rechten Bereich.  
  
     ![Hinzufügen eine neuen Domäne Regel Symbolleisten-Schaltfläche](../../2014/tutorials/media/et-settingdomainrules-01.jpg "eine neue Domäne Regel Symbolleisten-Schaltfläche \"hinzufügen\"")  
  
3.  Klicken Sie im rechten Bereich auf **Fügt eine neue domänenregel hinzu** auf der Symbolleiste (siehe Bild), um eine Regel hinzuzufügen.  
  
4.  Typ **E-Mail-Überprüfung+++** für die **Regelname** , und drücken Sie **EINGABETASTE**. Die **Active** Kontrollkästchen sollte standardmäßig aktiviert werden. Dieses Steuerelement ermöglicht Ihnen, eine Regel temporär zu deaktivieren.  
  
5.  In der **erstellen Sie eine Regel** Bereich, klicken Sie auf **Pfeil nach unten**, und wählen Sie **Wert endet mit**.  
  
6.  Typ **@adventure-works.com** in das Textfeld, und drücken Sie **Registerkarte**. Sie können weitere Bedingungen hinzufügen, indem Sie auf **der ausgewählten Klausel eine neue Bedingung hinzufügen** Symbolleisten-Schaltfläche in der **erstellen Sie eine Regel** Bereich.  
  
     ![E-Mail-Überprüfungsregel](../../2014/tutorials/media/et-settingdomainrules-02.jpg "e-Mail-Überprüfungsregel")  
  
7.  Klicken Sie auf **ausgewählte domänenregel für Testdaten ausführen** auf der Symbolleiste im rechten Bereich auf die Regel anhand von Beispieldaten zu testen.  
  
     ![Führen Sie die Domänenregel auf Test Daten Symbolleisten-Schaltfläche](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Domänenregel auf Daten Symbolleisten-Schaltfläche Test ausführen")  
  
8.  In der **Testdomänenregel** (Dialogfeld), klicken Sie auf **Fügt einen neuen testbegriff für die domänenregel** auf der Symbolleiste.  
  
     ![Testen Sie das Dialogfeld "Regel" Domäne](../../2014/tutorials/media/et-settingdomainrules-04.jpg "testen Domäne Regelsatz (Dialogfeld)")  
  
9. Typ **frank7@adventure-works.com** (einen gültigen Wert) in der **Contact Email** Spalte.  
  
10. Wiederholen Sie die vorherigen beiden Schritte hinzufügen **joe2@adventure-work.com** (ohne einen ungültigen Wert des ").  
  
11. Klicken Sie auf die letzte Schaltfläche (**testet die Domänenregeln für alle Begriffe**) auf der Symbolleiste, um die Eingabedaten anhand der Regel zu testen.  
  
     ![Testet die Domänenregeln für alle Begriffe (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-settingdomainrules-05.jpg "testet die Domänenregeln für alle Begriffe (Symbolleistenschaltfläche)")  
  
12. Beachten Sie, dass der erste Eintrag als gültiges Element und der zweite als ungültiges Element angezeigt wird.  
  
     ![Domänenregeltests](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Domänenregeltests")  
  
13. Klicken Sie auf **schließen** schließen die **Testdomänenregel** (Dialogfeld).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Festlegung begriffsbasierter Beziehungen](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  