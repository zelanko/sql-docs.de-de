---
title: 'Aufgabe 1: Definieren einer Abgleichsrichtlinie | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 6f89a720-fce5-4f60-bef3-a159bbc9f25c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6a94030fdf0f4ef42e0253022913f06f109e4dc3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107440"
---
# <a name="task-1-defining-a-matching-policy"></a>Aufgabe 1: Definieren einer Abgleichsrichtlinie
  In dieser Aufgabe erstellen Sie eine Abgleichsrichtlinie mit einer Regel. Die Regel weist eine erforderliche Komponente: **Supplier ID**, was bedeutet, dass die Lieferanten-IDs vor der Verwendung der anderen Domänen in der Regel übereinstimmen müssen. Die Regel verwendet zwei andere Domänen: **Lieferantenname** mit **Ähnlichkeit** Wert festgelegt wird, um **70 %** und **Contact Email** mit  **Ähnlichkeit** Wert festgelegt wird, um **30 %**.  
  
1.  Auf der Hauptseite des **DQS-Client**, klicken Sie auf **nach rechts weisenden Pfeil** neben **Lieferanten** Knowledge base an, und wählen **Abgleichsrichtlinie**.  
  
     ![Menü "Richtlinie" auf der Hauptseite übereinstimmende Seite](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "übereinstimmende Richtlinie im Menü auf der Hauptseite Seite")  
  
2.  Auf der **Zuordnung** Seite **Excel-Datei** für **Datenquelle**.  
  
3.  Klicken Sie auf **Durchsuchen**, stellen Sie sicher, dass der Filter nastaven NA hodnotu **Excel-Arbeitsmappe**, und wählen Sie **Cleansed Supplier List.xls** Datei, die Sie nach dem Ausführen der bereinigungsaktivität exportiert haben.  
  
    > [!NOTE]  
    >  Am Ende dieser Aktivität können Sie die Ergebnisse nicht exportieren, da diese Aktivität hauptsächlich auf die Definition der Abgleichsrichtlinie fokussiert ist. Sie erstellen ein Data Quality-Projekt für die Abgleichsaktivität, und führen es aus, um Duplikate aus der Lieferantenliste zu entfernen, indem Sie diese Abgleichsrichtlinie in der nächsten Lektion verwenden.  
  
4.  Zuordnung **SupplierID** Spalte **Supplier ID** Domäne **Lieferantenname** Spalte **Supplier Name** Domäne  **ContactEmailAddress** Spalte **Contact Email** Domäne. Sie müssen nur Quellspalten zu Domänen zuordnen, die Sie für die Definition der Abgleichsrichtlinie verwenden möchten. In diesem Fall machen Sie die Domänen "Supplier ID", "Supplier Name" und "Contact Email" für die Abgleichsrichtlinienaktivität verfügbar.  
  
     ![Ordnen Sie auf der Seite Richtlinie Definition Abgleichsprozess](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "Seite übereinstimmender Definitionsprozess für die Richtlinie \"zuordnen\"")  
  
5.  Klicken Sie auf **Weiter** zum Verschieben der **Abgleichsrichtlinie** , in denen Sie eine Abgleichsrichtlinie mit einer Regel in diese definieren, Seite.  
  
6.  Klicken Sie auf **Abgleichsregel erstellen** Symbolleiste auf die Schaltfläche zum Erstellen einer Regel in der Richtlinie.  
  
     ![Erstellen Sie eine übereinstimmende Regel Symbolleisten-Schaltfläche](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "erstellen Sie eine übereinstimmende Regel Symbolleisten-Schaltfläche")  
  
7.  In der **Regeldetails** auf der rechten Seite Geben Sie **Remove Duplicate Suppliers** für die **Regelname**.  
  
8.  Klicken Sie auf **neues Domänenelement hinzufügen** auf der Symbolleiste im rechten Bereich.  
  
     ![Regeldetails – hinzufügen eine neuen Domäne Element Schaltfläche](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "Regeldetails – eine neue Domäne-Element-Schaltfläche \"hinzufügen\"")  
  
9. Wählen Sie **Supplier ID** für die **Domäne** , und wählen Sie die **erforderliche** Kontrollkästchen. Beachten Sie, dass **Ähnlichkeit** wird automatisch festgelegt, um **Exact**. Durch Festlegen von **Supplier ID** als die **erforderliche**, Sie angeben, dass die Werte für dieses Feld in den zwei Datensätzen eine 100 %-Übereinstimmung zurückgeben, andernfalls die Datensätze werden nicht berücksichtigt, eine Übereinstimmung und die anderen Klauseln in der Regel werden ignoriert.  
  
     ![Entfernen doppelter Lieferanten Regeldefinition](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "Entfernen doppelter Lieferanten Regeldefinition")  
  
10. Klicken Sie auf **neues Domänenelement hinzufügen** auf der Symbolleiste erneut.  
  
11. Wählen Sie **Lieferantenname** Domäne, wählen **ähnlich** für **Ähnlichkeit**, und geben **70** für die **Gewichtung**.  Hier geben Sie an, dass Lieferantennamen nicht übereinstimmen müssen, aber ähnlich sein können, damit die Datensätze als Übereinstimmung gelten. Die Gewichtung gibt den Beitrag dieses Feldergebnisses zur Gesamttreffergenauigkeit zwischen zwei Datensätzen an.  
  
12. Wiederholen Sie die vorherigen beiden Schritte hinzufügen **Contact Email** Domäne mit **30** für die **Gewichtung**.  
  
13. Beachten Sie, dass die **minimale treffergenauigkeit** nastaven NA hodnotu **80 %**, dies ist der Wert in angezeigt werden, die **allgemeine** Registerkarte die **Konfiguration** auf der Seite **DQS-Verwaltung**. Sie können dieses Ergebnis hier nur über diesen Schwellenwert erhöhen.  
  
14. Beachten Sie, dass **überlappende Cluster** ausgewählt ist. Mit dieser Option kann ein Datensatz in mehreren Clustern angezeigt werden. Wenn Sie die Einstellung in "Nicht überlappende Cluster" ändern, werden die Cluster mit gemeinsamen Datensätzen in einem einzigen Cluster kombiniert.  
  
15. Die **starten** Schaltfläche auf dieser Seite können Sie jede Regel in der Richtlinie separat zu testen, während der nächsten Seite die Schaltfläche "Start", die Sie auf die gesamte Richtlinie (alle Regeln in der Richtlinie) testen kann.  
  
16. Klicken Sie auf **Weiter** zum Wechseln der **Abgleichsergebnisse** Seite.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2: Testen und Veröffentlichen der Abgleichsrichtlinie](../../2014/tutorials/task-2-testing-and-publishing-the-matching-policy.md)  
  
  
