---
title: Untersuchen des Naive Bayes-Modells (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: eb35c829b798335a27a37629711acf299ac2c7c9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023531"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a>Untersuchen des Naive Bayes-Modells (Lernprogramm zu Data Mining-Grundlagen)
  Die [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Algorithmus bietet mehrere Methoden für die Interaktion zwischen dem fahrradkaufverhalten und den Eingabeattributen anzuzeigen.  
  
 Die [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Viewer bietet die folgenden Registerkarten zum Durchsuchen von Naive Bayes-Miningmodellen:  
  
 
  
##  <a name="DependencyNetwork"></a> Abhängigkeitsnetzwerk  
 Die **Abhängigkeitsnetzwerk** Tab funktioniert nur auf die gleiche Weise wie die **Abhängigkeitsnetzwerk** auf der Registerkarte die [!INCLUDE[msCoName](../includes/msconame-md.md)] Struktur-Viewer. Jeder Knoten im Viewer steht für ein Attribut, und die Linien zwischen den Knoten stellen Beziehungen dar. In dem Viewer können Sie alle Attribute sehen, die sich auf den Status des vorhersagbaren Attributs Bike Buyer auswirken.  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Abhängigkeitsnetzwerk"  
  
1.  Verwenden der **Miningmodell** Liste am oberen Rand der **Miningmodell-Viewer** Registerkarte wechseln Sie zu der `TM_NaiveBayes` Modell.  
  
2.  Verwenden der **Viewer** Liste aus, wechseln zu **Microsoft Naive Bayes-Viewer**.  
  
3.  Klicken Sie auf die `Bike Buyer` Knoten aus, um die zugehörigen Abhängigkeiten zu identifizieren.  
  
     Die rosa Schattierung gibt an, dass alle Attribute Auswirkungen auf den Fahrradkauf haben.  
  
4.  Stellen Sie den Schieberegler ein, um die einflussreichsten Attribute zu identifizieren.  
  
     Wenn Sie den Schieberegler nach unten ziehen, werden nur noch diejenigen Attribute angezeigt, welche die stärksten Auswirkungen auf die [Bike Buyer]-Spalte haben. Durch Anpassen des Schiebereglers können Sie herausfinden, dass die einflussreichsten Attribute unter anderem folgende sind: Anzahl der Autos im Besitz, Arbeitsweg und Anzahl der Kinder insgesamt.  
 
  
##  <a name="AttributeProfiles"></a> Attributprofile  
 Die **Attributprofile** Registerkarte wird beschrieben, wie die verschiedenen Status der Eingabeattribute das Ergebnis des vorhersagbaren Attributs auswirken.  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Attributprofile"  
  
1.  In der **vorhersagbar** überprüfen Sie, ob `Bike Buyer` ausgewählt ist.  
  
2.  Wenn die **Mininglegende** Anzeige blockiert die **Attributprofile**, verschieben Sie sie aus dem Weg.  
  
3.  In der **Histogramm** wählen Sie im Balken **5**.  
  
     In unserem Modell stellt 5 die maximale Anzahl der Status einer Variablen dar.  
  
     Die Attribute, die sich auf den Status des vorhersagbaren Attributs auswirken, werden zusammen mit den Werten für jeden Status der Eingabeattribute und deren Verteilungen in jedem Status des vorhersagbaren Attributs aufgelistet.  
  
4.  In der **Attribute** Spalte suchen **Number Cars Owned**.  Beachten Sie die Unterschiede in den Histogrammen für Kunden, die ein Fahrrad gekauft haben (Spalte 1) und Kunden, die keinen Kauf getätigt haben (Spalte 0). Personen, die kein oder ein Auto besitzen, kaufen mit größerer Wahrscheinlichkeit ein Fahrrad.  
  
5.  Doppelklicken Sie auf die **Number Cars Owned** Zelle in der Spalte Bike Buyer (Spalte mit der Bezeichnung 1)-Spalte.  
  
     Die **Mininglegende** zeigt eine ausführlichere Ansicht an.  
  
  
##  <a name="AttributeCharacteristics"></a> Attributmerkmale  
 Mit der **Attributmerkmale** Registerkarte können Sie auswählen, ein Attribut und Wert anzeigen, wie häufig die Werte für andere Attribute in den ausgewählten Fällen angezeigt werden.  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Attributmerkmale"  
  
1.  In der **Attribut** , ob `Bike Buyer` ausgewählt ist.  
  
2.  Legen Sie die **Wert** zu **1**.  
  
     Im Viewer sehen Sie, dass Kunden, die keine Kinder zu Hause und einen kurzen Arbeitsweg haben und in Nordamerika leben mit größerer Wahrscheinlichkeit ein Fahrrad kaufen.  
  
  
##  <a name="AttributeDiscrimination"></a> Attributunterscheidung  
 Mit der **Attributunterscheidung** Registerkarte können Sie die Beziehung zwischen zwei diskreten Werten für das fahrradkaufverhalten und anderen Attributwerten prüfen. Da die `TM_NaiveBayes` Modell hat nur zwei Zustände, 1 und 0, müssen Sie nicht in der Ereignisanzeige keine Änderungen vornehmen.  
  
 Im Viewer können Sie sehen, dass Personen, die keine Autos besitzen, tendenziell Fahrräder kaufen. Personen, die zwei Autos besitzen, kaufen tendenziell keine Fahrräder.  
  
## <a name="related-tasks"></a>Related Tasks  
 Die folgenden Themen enthalten Beschreibungen zu den anderen Miningmodellen.  
  
-   [Untersuchen des Entscheidungsstrukturmodells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Untersuchen des Clustering-Modells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lesson 5: Testen von Modellen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Untersuchen des Clustering-Modells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)   
 [Registerkarte "Clusterunterscheidung"-Attribut &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md)   
 [Attribut Profile Registerkarte &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md)   
 [Registerkarte "Attributmerkmale"-Attribut &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md)   
 [Registerkarte Abhängigkeitsnetzwerk &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  
