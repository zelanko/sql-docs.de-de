---
title: Untersuchen des Entscheidungsstruktur Modells (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2e1472c2-3f3e-4dae-acb3-62fca374d397
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e7b77b445ff8cbef8be3acb72ef9cdb6fa3af159
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63224596"
---
# <a name="exploring-the-decision-tree-model-basic-data-mining-tutorial"></a>Untersuchen des Entscheidungsstrukturmodells (Lernprogramm zu Data Mining-Grundlagen)
  Durch den [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus wird anhand der übrigen Spalten im Trainingssatz vorhergesagt, welche Spalten die Entscheidung über den Kauf eines Fahrrads beeinflussen.  
  

  
##  <a name="decision-tree-tab"></a><a name="Decision_Tree_Tab"></a>Registerkarte Entscheidungsstruktur  
 Auf der Registerkarte **Entscheidungs** Struktur können Sie Entscheidungsbäume für jedes vorhersagbare Attribut im Dataset anzeigen.  
  
 In diesem Fall prognostiziert das Modell nur eine Spalte Bike Buyer, sodass nur eine Struktur angezeigt werden kann. Wenn weitere Strukturen vorhanden waren, können **Sie das Struktur** Feld verwenden, um eine andere Struktur auszuwählen.  
  
 Wenn Sie das `TM_Decision_Tree` Modell im Decision Tree-Viewer anzeigen, können Sie die wichtigsten Attribute auf der linken Seite des Diagramms sehen. "Am wichtigsten" bedeutet, dass diese Attribute den größten Einfluss auf das Ergebnis haben. Die weiter unten in der Struktur (auf der rechten Diagrammseite) angezeigten Attribute weisen einen geringeren Einfluss auf.  
  
 In diesem Beispiel ist das Alter der wichtigste Einzelfaktor für die Vorhersage eines Fahrradkaufs. Im Modell werden Kunden nach dem Alter gruppiert, und anschließend wird das nächstwichtigere Attribut für jede Altersgruppe angezeigt. In der Kundengruppe von 34 bis 40 Jahren ist die Anzahl der Kraftfahrzeuge im Besitz des Kunden nach dem Alter der bedeutendste Vorhersagefaktor.  
  
#### <a name="to-explore-the-model-in-the-decision-tree-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Entscheidungsstruktur"  
  
1.  Wählen Sie im **Data Mining-Designer**die Registerkarte **Mining Modell-Viewer** aus.  
  
     Standardmäßig wird der Designer mit dem ersten Modell geöffnet, das der Struktur hinzugefügt wurde, in diesem Fall `TM_Decision_Tree`.  
  
2.  Mithilfe der Lupensymbole können Sie die Größe der Strukturanzeige einstellen.  
  
     Standardmäßig werden im [!INCLUDE[msCoName](../includes/msconame-md.md)] Struktur-Viewer nur die ersten drei Strukturebenen angezeigt. Umfasst die Struktur weniger als drei Ebenen, zeigt der Viewer nur die vorhandenen Ebenen an. Mit dem Schieberegler **Ebene anzeigen** oder der **Standard Erweiterungs** Liste können Sie weitere Ebenen anzeigen.  
  
3.  Folie **zeigt die Ebene** auf den vierten Balken an.  
  
4.  Ändern Sie **Background** den Wert für `1`background in.  
  
     Durch Ändern der **Hintergrund** Einstellung können Sie schnell die Anzahl der Fälle in jedem Knoten sehen, die den Zielwert `1` für [Bike Buyer] aufweisen. In diesem besonderen Szenario stellt jeder Fall einen Kunden dar. Der Wert `1` gibt an, dass der Kunde zuvor ein Fahrrad gekauft hat. der Wert **0** gibt an, dass der Kunde kein Fahrrad gekauft hat. Je dunkler die Schattierung des Knotens ist, desto höher ist der Prozentsatz der Fälle im Knoten mit dem Zielwert.  
  
5.  Platzieren Sie den Cursor über dem Knoten mit der Bezeichnung **alle**. Daraufhin wird eine QuickInfo mit folgenden Informationen angezeigt:  
  
    -   Gesamtzahl der Fälle  
  
    -   Anzahl der Kunden, die keinen Kauf getätigt haben  
  
    -   Anzahl der Kunden, die einen Kauf getätigt haben  
  
    -   Anzahl der Fälle mit unvollständigen Werten für [Bike Buyer]  
  
     Sie können den Cursor auch auf einem beliebigen Knoten in der Struktur platzieren, um die Bedingung anzuzeigen, die erforderlich ist, um den Knoten vom vorhergehenden Knoten aus zu erreichen. Sie können dieselben Informationen auch in der **Mining Legende**anzeigen.  
  
6.  Klicken Sie auf den Knoten für **Age >= 34 und < 41**. Das Histogramm wird als schmaler horizontaler Balken über dem Knoten angezeigt. Es stellt die Verteilung der Kunden in der entsprechenden Altersgruppe dar, die bereits ein Fahrrad gekauft (rosa) bzw. noch kein Fahrrad gekauft haben (blau). Dem Viewer ist zu entnehmen, dass Kunden im Alter von 34 bis 40 Jahren, die ein oder kein Auto besitzen, wahrscheinlich ein Fahrrad kaufen. Bei einer genaueren Betrachtung stellt sich heraus, dass die Wahrscheinlichkeit, ein Fahrrad zu kaufen, im Alter von 38 bis 40 Jahren am größten ist.  
  
 Beim Erstellen von Struktur und Modell haben Sie Drillthrough aktiviert. Sie können daher detaillierte Informationen über die Modellfälle und die Miningstruktur einschließlich Spalten abrufen, die nicht Teil des Miningmodells sind (beispielsweise emailAddress, FirstName).  
  
 Weitere Informationen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-drill-through-to-case-data"></a>So führen Sie einen Drillthrough zu Falldaten aus  
  
1.  Klicken Sie mit der rechten Maustaste auf einen Knoten, und wählen Sie **Drillthrough** und dann **nur Modell Spalten**.  
  
     Die Details für die einzelnen Trainingsfälle werden im Arbeitsblattformat angezeigt. Sie wurden der vTargetMail-Sicht entnommen, die beim Erstellen der Miningstruktur als Falltabelle ausgewählt wurde.  
  
2.  Klicken Sie mit der rechten Maustaste auf einen Knoten, und wählen Sie **Drillthrough** und dann **Modell-und Struktur Spalten**  
  
     Das gleiche Arbeitsblatt wird angezeigt, und die Strukturspalten wurden an das Ende angefügt.  
  
  
###  <a name="dependency-network-tab"></a><a name="Dependency_Network_Tab"></a>Registerkarte Abhängigkeits Netzwerk  
 Auf der Registerkarte **Abhängigkeits Netzwerk** werden die Beziehungen zwischen den Attributen angezeigt, die zur Vorhersagefähigkeit des Mining Modells beitragen. Der Abhängigkeitsnetzwerk-Viewer bestätigt die Erkenntnisse, dass Alter und Region wichtige Faktoren für den Kauf eines Fahrrads darstellen.  
  
##### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Abhängigkeitsnetzwerk"  
  
1.  Klicken Sie `Bike Buyer` auf den Knoten, um seine Abhängigkeiten zu identifizieren.  
  
     Der zentrale Knoten des Abhängigkeitsnetzwerks `Bike Buyer` steht für das vorhersagbare Attribut im Miningmodell. Im Diagramm werden alle verbundenen Knoten hervorgehoben, die das vorhersagbare Attribut beeinflussen.  
  
2.  Passen Sie den Schieberegler **alle Links** an, um das einflussreichste Attribut zu identifizieren.  
  
     Wenn Sie den Schieberegler nach unten ziehen, werden Attribute, die nur eine schwache Auswirkung auf die Spalte [Bike Buyer] haben, aus dem Diagramm entfernt. Mithilfe des Reglers können Sie feststellen, dass Alter und Region die wichtigste Faktoren bei der Vorhersage sind, ob ein Kunde ein Fahrrad kauft.  
  
## <a name="related-tasks"></a>Related Tasks  
 In den folgenden Themen wird erläutert, wie Daten unter Verwendung anderer Modellarten analysiert werden können.  
  
-   [Erkunden des Clustering-Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [Untersuchen des Naive Bayes-Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erkunden des Clustering-Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tasks und Anleitungen des Mining Modell-Viewers](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Registerkarte "Entscheidungsstruktur" &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/decision-tree-tab-mining-model-viewer.md)   
 [Registerkarte Abhängigkeits Netzwerk &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)   
 [Durchsuchen eines Modells mit dem Microsoft Struktur-Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
  
