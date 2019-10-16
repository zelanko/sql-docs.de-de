---
title: 'Aufgabe 4: Festlegen von Domänen Regeln | Microsoft-Dokumentation'
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
ms.openlocfilehash: dd59bf315e90bd52ba1388d27c533ab4a3136d3c
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381740"
---
# <a name="task-4-setting-domain-rules"></a>Aufgabe 4: Festlegen von Domänenregeln
  In dieser Aufgabe erstellen Sie eine Regel für die **Kontakt-e-Mail** -Domäne, um zu prüfen, ob die e-Mail-Adresse mit **\@adventure-Works.com**endet. Weitere Informationen zu dieser Seite finden Sie im Thema [Erstellen einer Domänen Regel](https://msdn.microsoft.com/library/hh510397.aspx) .  
  
1.  Klicken Sie in der **Domänen Liste**auf **Contact Email** .  
  
2.  Wechseln Sie im rechten Bereich zur Registerkarte **Domänen Regeln** .  
  
     ![Symbolleisten Schaltfläche für neue Domänen Regel hinzufügen](../../2014/tutorials/media/et-settingdomainrules-01.jpg "Symbolleisten Schaltfläche für neue Domänen Regel hinzufügen")  
  
3.  Klicken Sie im rechten Bereich auf der Symbolleiste auf die Schaltfläche **neue Domänen Regel hinzufügen** (siehe Abbildung), um eine Regel hinzuzufügen.  
  
4.  Geben Sie als **Regelname** **e-Mail-Überprüfung** ein, und drücken **Sie** Das Kontrollkästchen **aktiv** sollte standardmäßig aktiviert sein. Dieses Steuerelement ermöglicht Ihnen, eine Regel temporär zu deaktivieren.  
  
5.  Klicken Sie im Bereich **Regel erstellen** auf **Pfeil nach unten**, und wählen Sie **Wert endet mit**aus.  
  
6.  Geben Sie im Textfeld **\@adventure-Works.com** ein, und drücken Sie die **Tab**-Taste. Sie können weitere Bedingungen hinzufügen, indem Sie im Bereich **Regel erstellen** **auf der Symbolleiste der ausgewählten Klausel auf neue Bedingung hinzufügen** klicken.  
  
     ![Validierungs Regel für e-Mail](../../2014/tutorials/media/et-settingdomainrules-02.jpg "Validierungs Regel für e-Mail")  
  
7.  Klicken Sie auf der Symbolleiste im rechten Bereich auf die Schaltfläche **ausgewählte Domänen Regel für Testdaten ausführen** , um die Regel mit Beispiel Daten zu testen.  
  
     ![Symbolleisten Schaltfläche "Domänen Regel für Testdaten ausführen"](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Symbolleisten Schaltfläche "Domänen Regel für Testdaten ausführen"")  
  
8.  Klicken Sie im Dialogfeld **Test Domänen Regel** auf der Symbolleiste auf **einen neuen Test Begriff für die Domänen Regel hinzufügen** .  
  
     ![Dialog Feld "Domänen Regel testen"](../../2014/tutorials/media/et-settingdomainrules-04.jpg "Dialog Feld "Domänen Regel testen"")  
  
9. Geben Sie in der Spalte **Kontakt-e-Mail** **frank7\@adventure-Works.com** (gültiger Wert) ein.  
  
10. Wiederholen Sie die vorherigen beiden Schritte, um **Joe2\@adventure-work.com** hinzuzufügen (ein ungültiger Wert ohne ' ').  
  
11. Klicken Sie auf der Symbolleiste auf die letzte Schaltfläche (**Testen Sie die Domänen Regel nach allen Begriffen**), um die Eingabedaten für die Regel zu testen.  
  
     ![Symbolleisten Schaltfläche "Domänen Regel auf allen Begriffen testen"](../../2014/tutorials/media/et-settingdomainrules-05.jpg "Symbolleisten Schaltfläche "Domänen Regel auf allen Begriffen testen"")  
  
12. Beachten Sie, dass der erste Eintrag als gültiges Element und der zweite als ungültiges Element angezeigt wird.  
  
     ![Test Domänen Regel Ergebnisse](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Test Domänen Regel Ergebnisse")  
  
13. Klicken Sie auf **Schließen** , um das Dialogfeld **Domänen Regel testen** zu schließen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Festlegung begriffsbasierter Beziehungen](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
