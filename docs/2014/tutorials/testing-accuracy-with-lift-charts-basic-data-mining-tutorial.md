---
title: Überprüfen der Genauigkeit mit Prognosegütediagrammen (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 06cefcdac192b715fe843f842088456f769cdd24
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042651"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a>Überprüfen der Genauigkeit mit Prognosegütediagrammen (Lernprogramm zu Data Mining-Grundlagen)
  Auf der **Mininggenauigkeitsdiagramm** Registerkarte des Data Mining-Designer können Sie berechnen, wie gut jeder Ihrer Modelle Vorhersagen trifft und die Ergebnisse der einzelnen Modelle direkt mit den Ergebnissen der anderen Modelle vergleichen. Diese Methode des Vergleichs wird als bezeichnet ein *prognosegütediagramm*. In der Regel wird die Vorhersagegenauigkeit eines Miningmodells mit dem Lift oder der Klassifizierungsgenauigkeit gemessen. In diesem Lernprogramm wird nur das Prognosegütediagramm verwendet.  
  
 Im Rahmen dieses Themas führen Sie die folgenden Aufgaben aus:  
  
-   [Auswählen der Eingabedaten](#BKMK_InputData)  
  
-   [Konfigurieren von Parametern für das Genauigkeitsdiagramm](#BKMK_Selecting)  
  
##  <a name="BKMK_InputData"></a> Die Eingabedaten auswählen  
 Der erste Schritt beim Testen der Genauigkeit von Miningmodellen ist die Auswahl der Datenquelle, die Sie für den Test verwenden möchten. Sie überprüfen die Leistung der Modelle anhand der Testdaten und verwenden dieses anschließend mit externen Daten.  
  
#### <a name="to-select-the-data-set"></a>So wählen Sie das Dataset aus  
  
1.  Wechseln Sie zu der **Mininggenauigkeitsdiagramm** Registerkarte im Data Mining-Designer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , und wählen Sie die **Eingabeauswahl** Registerkarte.  
  
2.  In der **Dataset auswählen, für das Genauigkeitsdiagramm verwendet werden** Gruppe wählen Sie im **Testfälle für Miningstruktur verwenden**. Dies sind die Testdaten, die Sie beim Erstellen der Miningstruktur vorgesehen haben.  
  
     Weitere Informationen zu den anderen Optionen finden Sie unter [Auswählen eines Genauigkeitsdiagrammtyps und Festlegen von Diagrammoptionen](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).  
  
##  <a name="BKMK_Selecting"></a> Festlegen von Parametern für das Genauigkeitsdiagramm  
 Beim Erstellen eines Genauigkeitsdiagramms müssen Sie drei Entscheidungen treffen:  
  
-   Welche Modelle sollen in das Genauigkeitsdiagramm eingeschlossen werden?  
  
-   Welches vorhersagbare Attribut soll gemessen werden? Einige Modelle verfügen u. U. über mehrere Ziele, allerdings kann mit jedem Diagramm jeweils nur ein Ergebnis gemessen werden.  
  
     Verwenden Sie eine Spalte als die **Name der vorhersagbaren Spalte** die Spalten müssen in einem Genauigkeitsdiagramm, den Verwendungstyp des `Predict` oder `Predict Only`. Darüber hinaus muss der Inhaltstyp der Zielspalte entweder `Discrete` oder `Discretized` lauten. Dies bedeutet, dass die Genauigkeit nicht unter Verwendung kontinuierlicher numerischer Ergebnisse mit dem Prognosegütediagramm gemessen werden kann.  
  
-   Möchten Sie die allgemeine Genauigkeit des Modells und seine Genauigkeit der Vorhersage eines bestimmten Werts messen (z. B. [Bike Buyer] = "Yes")  
  
#### <a name="to-generate-the-lift-chart"></a>So erstellen Sie das Prognosegütediagramm  
  
1.  Auf der **Eingabeauswahl** -Registerkarte des Data Mining-Designers unter **wählen Sie die vorhersagbaren Miningmodellspalten im prognosegütediagramm angezeigt**, aktivieren Sie das Kontrollkästchen **synchronisieren Vorhersagespalten und Werte**.  
  
2.  In der **Name der vorhersagbaren Spalte** Spalte überprüfen Sie, ob **Bike Buyer** für jedes Modell ausgewählt ist.  
  
3.  In der **anzeigen** Spalte, wählen Sie die einzelnen Modelle.  
  
     Standardmäßig werden alle Modelle in der Miningstruktur ausgewählt. Sie können angeben, dass ein Modell nicht mit aufgenommen werden soll. Behalten Sie jedoch für dieses Lernprogramm die Auswahl aller Modelle bei.  
  
4.  In der **Wert Vorhersagen** Spalte **1**. Der gleiche Wert wird automatisch für jedes Modell eingegeben, das die gleiche vorhersagbare Spalte besitzt.  
  
5.  Wählen Sie die **Prognosegütediagramm** Registerkarte.  
  
     Wenn Sie auf die Registerkarte klicken, wird eine Vorhersageabfrage ausgeführt, um Vorhersagen für die Testdaten abzurufen. Anschließend werden die Ergebnisse mit den bekannten Werten verglichen. Die Ergebnisse werden im Diagramm angezeigt.  
  
     Wenn Sie ein bestimmtes zielergebnis angegeben die **Wert Vorhersagen** Option das prognosegütediagramm stellt die Ergebnisse von zufallsvorhersagen und die Ergebnisse eines idealen Modells.  
  
    -   Die Zufallsvorhersagelinie zeigt, wie genau das Modell wäre, wenn keine Informationsdaten für die Vorhersagen bereitgestellt würden: d. h. eine Aufteilung von 50:50 zwischen zwei Ergebnissen. Mithilfe des Prognosegütediagramms kann visuell dargestellt werden, wie viel besser das Modell im Vergleich zu einer Zufallsvorhersage abschneidet.  
  
    -   Die Linie für das ideale Modell stellt die Obergrenze der Genauigkeit dar. Sie zeigt den maximal möglichen Nutzen, den Sie erzielen könnten, wenn die Modellvorhersage immer genau wäre.  
  
     Die von Ihnen erstellten Miningmodelle bewegen sich normalerweise zwischen diesen beiden Extremen. Jede Verbesserung gegenüber der zufallsvorhersage wird als betrachtet *lift*.  
  
6.  Verwenden Sie die Legende, um die farbigen Zeilen zu identifizieren, die das Idealmodell und das Zufallsvorhersagemodell darstellen.  
  
     Sie werden feststellen, dass die `TM_Decision_Tree` Modell bietet die größten Lift zu verzeichnen Clustering sowohl Naive Bayes-Modelle voraus.  
  
 Eine nähere Erläuterung eines prognosegütediagramms wie den in dieser Lektion erstellt haben, finden Sie unter [Prognosegütediagramm &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Testen eines gefilterten Modells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Prognosegütediagramm &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Prognosegütediagrammtyp (Registerkarte) &#40;Mininggenauigkeitsdiagrammsicht&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)  
  
  
