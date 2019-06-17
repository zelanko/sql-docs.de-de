---
title: 'Aufgabe 4: Festlegen von Domänenregeln | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ea4397bddf9ab1c08c099df4c473a5e43c54c9ec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65489075"
---
# <a name="task-4-setting-domain-rules"></a>Aufgabe 4: Festlegen von Domänenregeln
  In dieser Aufgabe erstellen Sie eine Regel für die **Contact Email** Domäne zu überprüfen, ob die e-Mail-Adresse endet **@adventure-works.com** . Finden Sie unter [Erstellen einer Domänenregel](https://msdn.microsoft.com/library/hh510397.aspx) Weitere Informationen auf der Seite.  
  
1.  Klicken Sie auf **Contact Email** in die **Domänenliste**.  
  
2.  Wechseln Sie zu der **Domänenregeln** Registerkarte im rechten Bereich.  
  
     ![Fügen Sie eine neue Symbolleisten-Schaltfläche in einer Domäne Regel](../../2014/tutorials/media/et-settingdomainrules-01.jpg "Hinzufügen einer neuen Domäne (Symbolleistenschaltfläche)")  
  
3.  Klicken Sie im rechten Bereich auf **Fügt eine neue domänenregel hinzu** auf der Symbolleiste (siehe Bild), um eine Regel hinzuzufügen.  
  
4.  Typ **e-Mail-Überprüfung** für die **Regelname** , und drücken Sie **EINGABETASTE**. Die **Active** Kontrollkästchen sollte standardmäßig aktiviert werden. Dieses Steuerelement ermöglicht Ihnen, eine Regel temporär zu deaktivieren.  
  
5.  In der **erstellen Sie eine Regel** Bereich, klicken Sie auf **Pfeil nach unten**, und wählen Sie **Wert endet mit**.  
  
6.  Typ **@adventure-works.com** in das Textfeld ein und drücken Sie **Registerkarte**. Sie können weitere Bedingungen hinzufügen, indem Sie auf **neue Bedingung hinzufügen, um die ausgewählte Klausel** Symbolleisten-Schaltfläche in der **erstellen Sie eine Regel** Bereich.  
  
     ![E-Mail-Überprüfungsregel](../../2014/tutorials/media/et-settingdomainrules-02.jpg "e-Mail-Überprüfungsregel")  
  
7.  Klicken Sie auf **ausgewählte domänenregel für Testdaten ausführen** auf der Symbolleiste im rechten Bereich auf die Regel anhand von Beispieldaten zu testen.  
  
     ![Ausführen die Domänenregel auf die Schaltfläche "Test-Daten-Symbolleiste"](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Domänenregel auf die Schaltfläche \"Test-Daten-Symbolleiste\" ausführen.")  
  
8.  In der **Testdomänenregel** Dialogfeld klicken Sie auf **Fügt einen neuen testbegriff für die domänenregel** auf der Symbolleiste auf die Schaltfläche.  
  
     ![Testen Sie das Dialogfeld "Regel" Domäne](../../2014/tutorials/media/et-settingdomainrules-04.jpg "testen Sie das Dialogfeld \"Regel\" Domäne")  
  
9. Typ **frank7@adventure-works.com** (einen gültigen Wert) in der **Contact Email** Spalte.  
  
10. Wiederholen Sie die vorherigen beiden Schritte hinzufügen **joe2@adventure-work.com** (einen ungültigen Wert ohne den ").  
  
11. Klicken Sie auf die letzte Schaltfläche (**testet die Domänenregeln für alle Begriffe**) auf der Symbolleiste auf die Eingabedaten für die Regel zu testen.  
  
     ![Testet die Domänenregeln für alle Begriffe (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-settingdomainrules-05.jpg "testet die Domänenregeln für alle Begriffe (Symbolleistenschaltfläche)")  
  
12. Beachten Sie, dass der erste Eintrag als gültiges Element und der zweite als ungültiges Element angezeigt wird.  
  
     ![Domänenregeltests](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Domänenregeltests")  
  
13. Klicken Sie auf **schließen** schließen die **Testdomänenregel** Dialogfeld.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Festlegung Begriffsbasierter basierend Beziehungen](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
