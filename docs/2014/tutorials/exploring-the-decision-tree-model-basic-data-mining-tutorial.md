---
title: Untersuchen des Entscheidungsstrukturmodells (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
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
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013741"
---
# <a name="exploring-the-decision-tree-model-basic-data-mining-tutorial"></a>Untersuchen des Entscheidungsstrukturmodells (Lernprogramm zu Data Mining-Grundlagen)
  Durch den [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus wird anhand der übrigen Spalten im Trainingssatz vorhergesagt, welche Spalten die Entscheidung über den Kauf eines Fahrrads beeinflussen.  
  

  
##  <a name="Decision_Tree_Tab"></a> Registerkarte Entscheidungsstruktur  
 Auf der **Entscheidungsstruktur** Registerkarte können Sie Entscheidungsstrukturen für jedes vorhersagbare Attribut im Dataset anzeigen.  
  
 In diesem Fall sagt das Modell nur eine Spalte Bike Buyer, gibt es also nur eine Struktur zu sehen. Falls mehrere Strukturen sind, können Sie die **Struktur** Feld, um eine andere Struktur auswählen.  
  
 Wie Sie anzeigen, die `TM_Decision_Tree` Modell in den Decision Tree-Viewer, können Sie die wichtigsten Attribute auf der linken Seite des Diagramms sehen. "Wichtigsten" bedeutet, dass diese Attribute den größten Einfluss auf das Ergebnis. Die weiter unten in der Struktur (auf der rechten Diagrammseite) angezeigten Attribute weisen einen geringeren Einfluss auf.  
  
 In diesem Beispiel ist das Alter der wichtigste Einzelfaktor für die Vorhersage eines Fahrradkaufs. Im Modell werden Kunden nach dem Alter gruppiert, und anschließend wird das nächstwichtigere Attribut für jede Altersgruppe angezeigt. In der Kundengruppe von 34 bis 40 Jahren ist die Anzahl der Kraftfahrzeuge im Besitz des Kunden nach dem Alter der bedeutendste Vorhersagefaktor.  
  
#### <a name="to-explore-the-model-in-the-decision-tree-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Entscheidungsstruktur"  
  
1.  Wählen Sie die **Miningmodell-Viewer** Registerkarte **Data Mining-Designer**.  
  
     In der Standardeinstellung der Designer wird geöffnet, das erste Modell, das der Struktur, in diesem Fall hinzugefügt wurde `TM_Decision_Tree`.  
  
2.  Mithilfe der Lupensymbole können Sie die Größe der Strukturanzeige einstellen.  
  
     Standardmäßig werden im [!INCLUDE[msCoName](../includes/msconame-md.md)] Struktur-Viewer nur die ersten drei Strukturebenen angezeigt. Umfasst die Struktur weniger als drei Ebenen, zeigt der Viewer nur die vorhandenen Ebenen an. Sie können weitere Ebenen anzeigen, indem Sie mit der **Ebene anzeigen** Schieberegler oder **Standarderweiterung** Liste.  
  
3.  Schieben Sie **Ebene anzeigen** zum vierten Balken.  
  
4.  Ändern der **Hintergrund** Wert `1`.  
  
     Durch Ändern der **Hintergrund** festlegen, können Sie rasch erkennen die Anzahl der Fälle in den einzelnen Knoten, die den Zielwert `1` für [Bike Buyer]. In diesem besonderen Szenario stellt jeder Fall einen Kunden dar. Der Wert `1` gibt an, dass der Kunde zuvor ein Fahrrad gekauft Wert **0** gibt an, dass der Kunde kein Fahrrad gekauft hat. Je dunkler die Schattierung des Knotens ist, desto höher ist der Prozentsatz der Fälle im Knoten mit dem Zielwert.  
  
5.  Platzieren Sie den Cursor über dem Knoten mit der Bezeichnung **alle**. Daraufhin wird eine QuickInfo mit folgenden Informationen angezeigt:  
  
    -   Gesamtzahl der Fälle  
  
    -   Anzahl der Kunden, die keinen Kauf getätigt haben  
  
    -   Anzahl der Kunden, die einen Kauf getätigt haben  
  
    -   Anzahl der Fälle mit unvollständigen Werten für [Bike Buyer]  
  
     Sie können den Cursor auch auf einem beliebigen Knoten in der Struktur platzieren, um die Bedingung anzuzeigen, die erforderlich ist, um den Knoten vom vorhergehenden Knoten aus zu erreichen. Sie können auch anzeigen, diese Informationen in den **Mininglegende**.  
  
6.  Klicken Sie auf den Knoten für **Age > = 34 and < 41**. Das Histogramm wird als schmaler horizontaler Balken über dem Knoten angezeigt. Es stellt die Verteilung der Kunden in der entsprechenden Altersgruppe dar, die bereits ein Fahrrad gekauft (rosa) bzw. noch kein Fahrrad gekauft haben (blau). Dem Viewer ist zu entnehmen, dass Kunden im Alter von 34 bis 40 Jahren, die ein oder kein Auto besitzen, wahrscheinlich ein Fahrrad kaufen. Bei einer genaueren Betrachtung stellt sich heraus, dass die Wahrscheinlichkeit, ein Fahrrad zu kaufen, im Alter von 38 bis 40 Jahren am größten ist.  
  
 Beim Erstellen von Struktur und Modell haben Sie Drillthrough aktiviert. Sie können daher detaillierte Informationen über die Modellfälle und die Miningstruktur einschließlich Spalten abrufen, die nicht Teil des Miningmodells sind (beispielsweise emailAddress, FirstName).  
  
 Weitere Informationen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-drill-through-to-case-data"></a>So führen Sie einen Drillthrough zu Falldaten aus  
  
1.  Mit der rechten Maustaste in eines Knotens, und wählen **Drillthrough** dann **nur Modellspalten**.  
  
     Die Details für die einzelnen Trainingsfälle werden im Arbeitsblattformat angezeigt. Sie wurden der vTargetMail-Sicht entnommen, die beim Erstellen der Miningstruktur als Falltabelle ausgewählt wurde.  
  
2.  Mit der rechten Maustaste in eines Knotens, und wählen **Drillthrough** dann **Modell- und Strukturspalten**.  
  
     Das gleiche Arbeitsblatt wird angezeigt, und die Strukturspalten wurden an das Ende angefügt.  
  
  
###  <a name="Dependency_Network_Tab"></a> Registerkarte Abhängigkeitsnetzwerk  
 Die **Abhängigkeitsnetzwerk** Registerkarte zeigt die Beziehungen zwischen den Attributen, die zur vorhersagefähigkeit für das Miningmodell beitragen. Der Abhängigkeitsnetzwerk-Viewer bestätigt die Erkenntnisse, dass Alter und Region wichtige Faktoren für den Kauf eines Fahrrads darstellen.  
  
##### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Abhängigkeitsnetzwerk"  
  
1.  Klicken Sie auf die `Bike Buyer` Knoten aus, um die zugehörigen Abhängigkeiten zu identifizieren.  
  
     Der zentrale Knoten des Abhängigkeitsnetzwerks `Bike Buyer` steht für das vorhersagbare Attribut im Miningmodell. Im Diagramm werden alle verbundenen Knoten hervorgehoben, die das vorhersagbare Attribut beeinflussen.  
  
2.  Anpassen der **alle Links** Schieberegler, um die einflussreichsten Attribute zu identifizieren.  
  
     Wie Sie den Schieberegler nach unten ziehen, werden die Attribute, die nur eine geringe Auswirkung auf die Spalte [Bike Buyer] aus dem Diagramm entfernt. Mithilfe des Reglers können Sie feststellen, dass Alter und Region die wichtigste Faktoren bei der Vorhersage sind, ob ein Kunde ein Fahrrad kauft.  
  
## <a name="related-tasks"></a>Related Tasks  
 In den folgenden Themen wird erläutert, wie Daten unter Verwendung anderer Modellarten analysiert werden können.  
  
-   [Untersuchen des Clustering-Modells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [Untersuchen des Naive Bayes-Modells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Untersuchen des Clustering-Modells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningmodell-Viewer](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Registerkarte Entscheidungsstruktur &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/decision-tree-tab-mining-model-viewer.md)   
 [Registerkarte Abhängigkeitsnetzwerk &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)   
 [Durchsuchen eines Modells mit dem Microsoft Struktur-Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
  
