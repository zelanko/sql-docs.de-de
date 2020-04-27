---
title: Testen der Genauigkeit mit Lift Diagrammen (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63042651"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a>Überprüfen der Genauigkeit mit Prognosegütediagrammen (Lernprogramm zu Data Mining-Grundlagen)
  Auf der Registerkarte **Mining Genauigkeits Diagramm** des Data Mining-Designers können Sie berechnen, wie gut die einzelnen Modelle Vorhersagen treffen, und die Ergebnisse der einzelnen Modelle direkt mit den Ergebnissen der anderen Modelle vergleichen. Diese Vergleichsmethode wird als *Lift Chart*bezeichnet. In der Regel wird die Vorhersagegenauigkeit eines Miningmodells mit dem Lift oder der Klassifizierungsgenauigkeit gemessen. In diesem Lernprogramm wird nur das Prognosegütediagramm verwendet.  
  
 Im Rahmen dieses Themas führen Sie die folgenden Aufgaben aus:  
  
-   [Auswählen der Eingabedaten](#BKMK_InputData)  
  
-   [Konfigurieren von Parametern für das Genauigkeitsdiagramm](#BKMK_Selecting)  
  
##  <a name="choosing-the-input-data"></a><a name="BKMK_InputData"></a>Auswählen der Eingabedaten  
 Der erste Schritt beim Testen der Genauigkeit von Miningmodellen ist die Auswahl der Datenquelle, die Sie für den Test verwenden möchten. Sie überprüfen die Leistung der Modelle anhand der Testdaten und verwenden dieses anschließend mit externen Daten.  
  
#### <a name="to-select-the-data-set"></a>So wählen Sie das Dataset aus  
  
1.  Wechseln Sie in zur Registerkarte **Mining Genauigkeits Diagramm** im [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] Data Mining-Designer, und wählen Sie die Registerkarte **Eingabeauswahl** aus.  
  
2.  Wählen Sie im Gruppenfeld Dataset **auswählen, das für das Genauigkeits Diagramm verwendet werden soll** die Option **Testfälle für Mining Struktur verwenden**aus. Dies sind die Testdaten, die Sie beim Erstellen der Miningstruktur vorgesehen haben.  
  
     Weitere Informationen zu den anderen Optionen finden Sie unter [Auswählen eines Genauigkeits Diagramm Typs und Festlegen von Diagramm Optionen](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).  
  
##  <a name="setting-accuracy-chart-parameters"></a><a name="BKMK_Selecting"></a>Festlegen von Genauigkeits Diagramm Parametern  
 Beim Erstellen eines Genauigkeitsdiagramms müssen Sie drei Entscheidungen treffen:  
  
-   Welche Modelle sollen in das Genauigkeitsdiagramm eingeschlossen werden?  
  
-   Welches vorhersagbare Attribut soll gemessen werden? Einige Modelle verfügen u. U. über mehrere Ziele, allerdings kann mit jedem Diagramm jeweils nur ein Ergebnis gemessen werden.  
  
     Wenn Sie eine Spalte als **vorhersagbaren Spaltennamen** in einem Genauigkeits Diagramm verwenden möchten, müssen die Spalten `Predict` den `Predict Only`Verwendungstyp oder aufweisen. Darüber hinaus muss der Inhaltstyp der Zielspalte entweder `Discrete` oder `Discretized` lauten. Dies bedeutet, dass die Genauigkeit nicht unter Verwendung kontinuierlicher numerischer Ergebnisse mit dem Prognosegütediagramm gemessen werden kann.  
  
-   Möchten Sie die allgemeine Genauigkeit des Modells oder seine Genauigkeit bei der Vorhersage eines bestimmten Werts Messen (z. b. [Bike Buyer] = ' yes ')  
  
#### <a name="to-generate-the-lift-chart"></a>So erstellen Sie das Prognosegütediagramm  
  
1.  Aktivieren Sie auf der Registerkarte **Eingabeauswahl** des Data Mining-Designers unter **Wählen Sie die vorhersagbaren Mining Modell Spalten**aus, die im Prognose Prognose Diagramm angezeigt werden sollen das Kontrollkästchen **Vorhersage Spalten und-Werte synchronisieren**.  
  
2.  Überprüfen Sie in der Spalte **Name der vorhersagbaren Spalte** , ob **Bike Buyer** für jedes Modell ausgewählt ist.  
  
3.  Wählen Sie in der Spalte **anzeigen** die einzelnen Modelle aus.  
  
     Standardmäßig werden alle Modelle in der Miningstruktur ausgewählt. Sie können angeben, dass ein Modell nicht mit aufgenommen werden soll. Behalten Sie jedoch für dieses Lernprogramm die Auswahl aller Modelle bei.  
  
4.  Wählen Sie in der Spalte **Wert vorhersagen den Wert** **1**aus. Der gleiche Wert wird automatisch für jedes Modell eingegeben, das die gleiche vorhersagbare Spalte besitzt.  
  
5.  Wählen Sie die Registerkarte **Lift Chart** aus.  
  
     Wenn Sie auf die Registerkarte klicken, wird eine Vorhersageabfrage ausgeführt, um Vorhersagen für die Testdaten abzurufen. Anschließend werden die Ergebnisse mit den bekannten Werten verglichen. Die Ergebnisse werden im Diagramm angezeigt.  
  
     Wenn Sie mithilfe der Option **Wert vorhersagen** ein bestimmtes Zielergebnis angegeben haben, werden die Ergebnisse zufälliger Vermutungen und die Ergebnisse eines idealen Modells durch das Prognose Diagramm dargestellt.  
  
    -   Die Zufallsvorhersagelinie zeigt, wie genau das Modell wäre, wenn keine Informationsdaten für die Vorhersagen bereitgestellt würden: d. h. eine Aufteilung von 50:50 zwischen zwei Ergebnissen. Mithilfe des Prognosegütediagramms kann visuell dargestellt werden, wie viel besser das Modell im Vergleich zu einer Zufallsvorhersage abschneidet.  
  
    -   Die Linie für das ideale Modell stellt die Obergrenze der Genauigkeit dar. Sie zeigt den maximal möglichen Nutzen, den Sie erzielen könnten, wenn die Modellvorhersage immer genau wäre.  
  
     Die von Ihnen erstellten Miningmodelle bewegen sich normalerweise zwischen diesen beiden Extremen. Jede Verbesserung der Zufalls Vorhersage wird als *Lift*betrachtet.  
  
6.  Verwenden Sie die Legende, um die farbigen Zeilen zu identifizieren, die das Idealmodell und das Zufallsvorhersagemodell darstellen.  
  
     Sie werden feststellen, `TM_Decision_Tree` dass das Modell den größten Lift bietet und dabei sowohl die Clustering-als auch Naive Bayes-Modelle bietet.  
  
 Eine ausführliche Erläuterung eines in dieser Lektion erstellten Lift Diagramms finden Sie unter [Lift Chart &#40;Analysis Services-Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Testen eines gefilterten Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lift Chart &#40;Analysis Services-Data Mining-&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Registerkarte "Lift Chart" &#40;Mining Genauigkeits Diagramm Ansicht&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)  
  
  
