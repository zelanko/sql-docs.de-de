---
title: 'Aufgabe 2: Testen und Veröffentlichen der Abgleichsrichtlinie | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484728"
---
# <a name="task-2-testing-and-publishing-the-matching-policy"></a>Aufgabe 2: Testen und Veröffentlichen der Abgleichrichtlinie
  In dieser Aufgabe testen und veröffentlichen die **Remove Duplicate Suppliers** Abgleichsrichtlinie.  
  
1.  In der **Abgleichsergebnisse** auf **starten** um die gesamte Richtlinie zu testen. In diesem Fall enthält die Richtlinie nur eine Regel, daher sollten die Testergebnisse für die Regel und die Richtlinie identisch sein.  
  
2.  Prüfen Sie alle übereinstimmenden Datensätze und ihre Treffergenauigkeit im Listenfeld. Ein Datensatz mit einem **Grün** zugeordnete Symbol ist ein Duplikat des pivotdatensatzes, der ihm vorausgeht. Hier einige Beispiele:  
  
    1.  Der Datensatz mit **Datensatz-ID: 1000005** ist eine Übereinstimmung des Datensatzes mit der **Datensatz-Id: 1000004** mit **Bewertung: 100 %** da sowohl die Datensätze die gleichen Werte für **SupplierID (Voraussetzung)** , **Lieferantenname**, und **ContactEmailAddress-Spalten**. DQS wählt nach dem Zufallsprinzip einen Datensatz als Pivotdatensatz für einen Cluster aus.  
  
    2.  Der Datensatz **1000023** ist eine Übereinstimmung des Datensatzes **1000022** mit die treffergenauigkeit: 93 %, da die beiden Datensätze die gleichen Werte für haben **SupplierID (Voraussetzung)** und **Lieferantenname** Spalten aber unterschiedliche Werte für die **ContactEmailAddress** die Spalte.  
  
    3.  Führen Sie einen Bildlauf zum unteren Rand der Liste aus, um zwei Datensätze mit IDs anzuzeigen: **1000051** und **1000052**. Datensatz **1000052** als Übereinstimmung mit einer treffergenauigkeit **91 %** da die beiden Datensätze die gleichen Werte für die **SupplierID** und  **ContactEmailAddress** Spalten aber unterschiedliche Werte für die **Lieferantenname** Spalte.  
  
     ![Richtliniendefinition – Richtlinienergebnisse](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "Richtliniendefinition – Richtlinienergebnisse")  
  
3.  Mit der rechten Maustaste auf einen übereinstimmenden Datensatz (mit grünem Symbol), und klicken Sie auf **Details anzeigen** um weitere Details zur Übereinstimmung, wie z. B. Anteil jedes Feldergebnisses an der gesamttreffergenauigkeit anzuzeigen.  
  
     ![Minimale Treffergenauigkeit im Dialogfeld "Details"](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "Treffergenauigkeit im Dialogfeld \"Details\"")  
  
4.  Klicken Sie auf **schließen** schließen die **Details zur Treffergenauigkeit** Dialogfeld.  
  
5.  Klicken Sie auf **Abgleichsergebnisse** Registerkarte am unteren Rand der Seite. Diese Registerkarte enthält Details wie die Anzahl der übereinstimmenden Datensätze, die Anzahl der nicht übereinstimmenden Datensätze, die Anzahl der Cluster mit übereinstimmenden Datensätzen, die durchschnittliche Clustergröße, die minimale Clustergröße und die maximale Clustergröße. Finden Sie unter [Erstellen einer Abgleichsrichtlinie](https://msdn.microsoft.com/library/hh270290.aspx) Weitere Details. Sie können die Ergebnisse dieser Aktivität nicht exportieren. Sie definieren lediglich eine Abgleichsrichtlinie, indem Sie die Beispieldaten verwenden, um Regeln und die Richtlinie unter Verwendung der Beispieldaten zu testen.  
  
     ![Registerkarte "Ergebnisse" übereinstimmende](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "Abgleich der Registerkarte \"Ergebnisse\"")  
  
6.  Klicken Sie auf **Fertig stellen** um die Erstellung der Abgleichsrichtlinie abzuschließen.  
  
    > [!NOTE]  
    >  Sie haben hier die Abgleichsrichtlinie definiert; deshalb können Sie die Ergebnisse nicht in eine Ausgabedatei exportieren. Sie haben im Wesentlichen eine Beispieleingabedatei verwendet, Regeln erstellt und die Regeln und die Richtlinie unter Verwendung der Beispieldaten getestet, mit dem Ziel, die Richtlinie zu definieren.  
  
7.  Klicken Sie in der SQL Server Data Quality Services-Dialogfeld auf **veröffentlichen** , und klicken Sie auf **OK** im Meldungsfeld auf. Nun wird der von Ihnen definierte Abgleichsrichtlinie veröffentlicht, in der **Lieferanten** Knowledge Base. Sie können die Wissensdatenbank verwenden, um den Abgleichsprozess für eine Eingabedatei auszuführen, mit dem Ziel, Duplikate zu identifizieren und zu entfernen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 3: Erstellen und Ausführen von Data Quality-Projekten für den Abgleich](../../2014/tutorials/task-3-creating-and-running-a-data-quality-project-for-matching.md)  
  
  
