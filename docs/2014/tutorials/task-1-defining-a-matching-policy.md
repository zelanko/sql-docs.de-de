---
title: 'Aufgabe 1: Definieren einer abgleichsrichtlinie | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f89a720-fce5-4f60-bef3-a159bbc9f25c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3e4777cf05e7f3eab62c389ace8b8d8a96cae304
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65481315"
---
# <a name="task-1-defining-a-matching-policy"></a>Aufgabe 1: Definieren einer Abgleichsrichtlinie
  In dieser Aufgabe erstellen Sie eine Abgleichsrichtlinie mit einer Regel. Die Regel verfügt über eine Voraussetzung: **Lieferanten-ID**. Dies bedeutet, dass die Lieferanten-IDs erfüllt werden müssen, bevor die anderen Domänen in der Regel verwendet werden. Die Regel verwendet zwei andere Domänen: **Lieferanten Name** mit dem **Ähnlichkeits** Wert **70%** und **Contact Email** mit einem **Ähnlichkeits** Wert von **30%**.  
  
1.  Klicken Sie auf der Hauptseite des **DQS-Clients**auf den **Pfeil nach rechts** neben der Wissensdatenbank **Suppliers** , und wählen Sie abgleichsrichtlinie aus. ****  
  
     ![Menü "Abgleichsrichtlinie" auf Hauptseite](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "Menü "Abgleichsrichtlinie" auf Hauptseite")  
  
2.  Wählen Sie **auf der Seite** zuordnen die Option **Excel-Datei** für **Datenquelle**aus.  
  
3.  Klicken Sie auf **Durchsuchen**, stellen Sie sicher, dass Filter auf **Excel-Arbeitsmappe**festgelegt ist, und wählen Sie die Datei ". xls", die Sie nach der **Bereinigungs** Aktivität exportiert haben.  
  
    > [!NOTE]  
    >  Am Ende dieser Aktivität können Sie die Ergebnisse nicht exportieren, da diese Aktivität hauptsächlich auf die Definition der Abgleichsrichtlinie fokussiert ist. Sie erstellen ein Data Quality-Projekt für die Abgleichsaktivität, und führen es aus, um Duplikate aus der Lieferantenliste zu entfernen, indem Sie diese Abgleichsrichtlinie in der nächsten Lektion verwenden.  
  
4.  Ordnen Sie die Spalte " **SupplierID** " der **Lieferanten-ID** -Domäne, der Spalte " **Lieferanten Name** " zur Domäne " **Lieferanten Name** " und der Spalte " **contactemailaddress** **" an** Sie müssen nur Quellspalten zu Domänen zuordnen, die Sie für die Definition der Abgleichsrichtlinie verwenden möchten. In diesem Fall machen Sie die Domänen "Supplier ID", "Supplier Name" und "Contact Email" für die Abgleichsrichtlinienaktivität verfügbar.  
  
     ![Seite "Zuordnen" bei der Definition der Abgleichsrichtlinie](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "Seite "Zuordnen" bei der Definition der Abgleichsrichtlinie")  
  
5.  Klicken Sie auf **weiter** , um zur Seite abgleichsrichtlinie zu wechseln, auf der Sie eine abgleichsrichtlinie mit einer Regel definieren. ****  
  
6.  Klicken Sie auf der Symbolleiste auf die Schaltfläche Vergleichs **Regel erstellen** , um eine Regel in der Richtlinie zu erstellen.  
  
     ![Abgleichsregel erstellen (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "Abgleichsregel erstellen (Symbolleistenschaltfläche)")  
  
7.  Geben Sie im Bereich **Regel Details** auf der rechten Seite die Option **doppelte Lieferanten** als **Regelname**entfernen ein.  
  
8.  Klicken Sie in der Symbolleiste im rechten **Bereich auf neues Domänen Element hinzufügen** .  
  
     ![Regeldetails – Neues Domänenelement hinzufügen (Schaltfläche)](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "Regeldetails – Neues Domänenelement hinzufügen (Schaltfläche)")  
  
9. Wählen Sie **Lieferanten-ID** für die **Domäne** aus, und aktivieren Sie das Kontrollkästchen **Voraussetzung** . Beachten Sie, dass **Ähnlichkeit** automatisch auf **genau**festgelegt wird. Durch Festlegen der **Lieferanten-ID** als **Voraussetzung**geben Sie an, dass die Werte für dieses Feld in den zwei Datensätzen eine 100%-Entsprechung zurückgeben müssen. andernfalls werden die Datensätze nicht als "Match" angesehen, und die anderen Klauseln in der Regel werden ignoriert.  
  
     ![Definition der Regel zum Entfernen doppelter Lieferanten](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "Definition der Regel zum Entfernen doppelter Lieferanten")  
  
10. Klicken Sie erneut auf der Symbolleiste auf **Neues Domänen Element hinzufügen** .  
  
11. Wählen Sie **Lieferanten Name** Domäne aus, wählen **Sie Ähnlichkeit** **aus,** und geben Sie **70** für die **Gewichtung**ein.  Hier geben Sie an, dass Lieferantennamen nicht übereinstimmen müssen, aber ähnlich sein können, damit die Datensätze als Übereinstimmung gelten. Die Gewichtung gibt den Beitrag des Ergebnisses dieses Felds zur Gesamt Treffergenauigkeit an.  
  
12. Wiederholen Sie die vorherigen beiden Schritte **, um die** **e-Mail-Adresse für die e-Mail-Adresse** ****  
  
13. Beachten Sie, dass die **minimale Treffer** Genauigkeit auf **80%** festgelegt ist. Dies ist der Wert, der auf der Registerkarte **Allgemein** der **Konfigurations** Seite der **DQS-Verwaltung**angezeigt wird. Sie können dieses Ergebnis hier nur über diesen Schwellenwert erhöhen.  
  
14. Beachten Sie, dass über **Lapp Ende Cluster** Optionen ausgewählt werden. Mit dieser Option kann ein Datensatz in mehreren Clustern angezeigt werden. Wenn Sie die Einstellung in "Nicht überlappende Cluster" ändern, werden die Cluster mit gemeinsamen Datensätzen in einem einzigen Cluster kombiniert.  
  
15. Mithilfe der Schaltfläche " **Start** " auf dieser Seite können Sie jede Regel separat testen, während die Schaltfläche "Start" auf der nächsten Seite das Testen der gesamten Richtlinie ermöglicht (alle Regeln in der Richtlinie).  
  
16. Klicken Sie auf **weiter** , um zur Seite **passende Ergebnisse** zu wechseln.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2: Testen und Veröffentlichen der Abgleichsrichtlinie](../../2014/tutorials/task-2-testing-and-publishing-the-matching-policy.md)  
  
  
