---
title: 'Aufgabe 2: Testen und Veröffentlichen der abgleichsrichtlinie | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e1ffb6d7-fbc5-4695-b538-cc2302d1a17d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: a9957625e09bde8bb733eca6e564dfdcfbb0bd98
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65484728"
---
# <a name="task-2-testing-and-publishing-the-matching-policy"></a>Aufgabe 2: Testen und Veröffentlichen der Abgleichrichtlinie
  In dieser Aufgabe testen und veröffentlichen Sie die abgleichsrichtlinie zum **Entfernen doppelter Lieferanten** .  
  
1.  Klicken Sie auf der Seite Abgleichsergebnisse auf **starten** , um die gesamte Richtlinie zu testen **Matching Results** In diesem Fall enthält die Richtlinie nur eine Regel, daher sollten die Testergebnisse für die Regel und die Richtlinie identisch sein.  
  
2.  Prüfen Sie alle übereinstimmenden Datensätze und ihre Treffergenauigkeit im Listenfeld. Ein Datensatz, dem ein **grünes** Symbol zugeordnet ist, ist ein Duplikat des pivotdatensatz, der ihm vorangestellt ist. Hier einige Beispiele:  
  
    1.  Der Datensatz mit der **Datensatz-ID: 1000005** ist eine Übereinstimmung des Datensatzes mit der **Datensatz-ID: 1000004** mit **Score: 100%** , weil beide Datensätze die gleichen Werte für die Spalten **SupplierID (Voraussetzung)**, **Supplier Name**und **contactemailaddress**aufweisen. DQS wählt nach dem Zufallsprinzip einen Datensatz als Pivotdatensatz für einen Cluster aus.  
  
    2.  Der Datensatz **1000023** ist eine Übereinstimmung mit dem Datensatz **1000022** mit der Treffergenauigkeit: 93%, da die beiden Datensätze die gleichen Werte für die Spalten **SupplierID (Voraussetzung)** und **Supplier Name** aufweisen, aber unterschiedliche Werte für die Spalte **contactemailaddress** .  
  
    3.  Führen Sie einen Bildlauf zum Ende der Liste durch, um zwei Datensätze mit den Daten Satz-IDs anzuzeigen: **1000051** und **1000052**. Der Datensatz **1000052** gilt als Übereinstimmung mit der Treffergenauigkeit **91%** , da die beiden Datensätze die gleichen Werte für die Spalten **SupplierID** und **contactemailaddress** aufweisen, aber unterschiedliche Werte für die Spalte **Lieferanten Name** .  
  
     ![Richtliniendefinition – Richtlinienergebnisse](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "Richtliniendefinition – Richtlinienergebnisse")  
  
3.  Klicken Sie mit der rechten Maustaste auf einen übereinstimmenden Datensatz (mit grünes Symbol), und klicken Sie auf **Details anzeigen** , um weitere Details zum Abgleich anzuzeigen, z. b. den Beitrag der einzelnen Feld Ergebnisse zur Gesamt Treffergenauigkeit  
  
     ![Details zur Treffergenauigkeit (Dialogfeld)](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "Details zur Treffergenauigkeit (Dialogfeld)")  
  
4.  Klicken Sie auf **Schließen** , um das Dialogfeld Treffer Bewertungs **Details** zu schließen.  
  
5.  Klicken Sie unten auf der Seite auf die Registerkarte **Abgleichsergebnisse** . Diese Registerkarte enthält Details wie die Anzahl der übereinstimmenden Datensätze, die Anzahl der nicht übereinstimmenden Datensätze, die Anzahl der Cluster mit übereinstimmenden Datensätzen, die durchschnittliche Clustergröße, die minimale Clustergröße und die maximale Clustergröße. Weitere Informationen finden Sie unter [Erstellen einer abgleichsrichtlinie](https://msdn.microsoft.com/library/hh270290.aspx) . Sie können die Ergebnisse dieser Aktivität nicht exportieren. Sie definieren lediglich eine Abgleichsrichtlinie, indem Sie die Beispieldaten verwenden, um Regeln und die Richtlinie unter Verwendung der Beispieldaten zu testen.  
  
     ![Registerkarte „Abgleichsergebnisse“](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "Registerkarte „Abgleichsergebnisse“")  
  
6.  Klicken Sie auf **Fertig** stellen, um die abgleichsrichtlinie zu erstellen  
  
    > [!NOTE]  
    >  Sie haben hier die Abgleichsrichtlinie definiert; deshalb können Sie die Ergebnisse nicht in eine Ausgabedatei exportieren. Sie haben im Wesentlichen eine Beispieleingabedatei verwendet, Regeln erstellt und die Regeln und die Richtlinie unter Verwendung der Beispieldaten getestet, mit dem Ziel, die Richtlinie zu definieren.  
  
7.  Klicken Sie im Dialogfeld SQL Server Data Quality Services auf **veröffentlichen** , und klicken Sie dann im Meldungs Feld auf **OK** . Nun wird die von Ihnen definierte abgleichsrichtlinie in der Wissensdatenbank **Suppliers** veröffentlicht. Sie können die Wissensdatenbank verwenden, um den Abgleichsprozess für eine Eingabedatei auszuführen, mit dem Ziel, Duplikate zu identifizieren und zu entfernen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 3: Erstellen und Ausführen eines Data Quality-Projekts für Abgleiche](../../2014/tutorials/task-3-creating-and-running-a-data-quality-project-for-matching.md)  
  
  
