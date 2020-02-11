---
title: Untersuchen des Naive Bayes-Modells (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62472884"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a>Untersuchen des Naive Bayes-Modells (Lernprogramm zu Data Mining-Grundlagen)
  Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Algorithmus bietet mehrere Methoden zum Anzeigen der Interaktion zwischen dem Fahrradkauf und den Eingabe Attributen.  
  
 Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Viewer bietet die folgenden Registerkarten zur Untersuchung von Naive Bayes-Mining Modellen:  
  
 
  
##  <a name="DependencyNetwork"></a>Abhängigkeits Netzwerk  
 Die Registerkarte **Abhängigkeits Netzwerk** funktioniert auf die gleiche Weise wie die Registerkarte **Abhängigkeits Netzwerk** für den [!INCLUDE[msCoName](../includes/msconame-md.md)] Struktur-Viewer. Jeder Knoten im Viewer steht für ein Attribut, und die Linien zwischen den Knoten stellen Beziehungen dar. In dem Viewer können Sie alle Attribute sehen, die sich auf den Status des vorhersagbaren Attributs Bike Buyer auswirken.  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Abhängigkeitsnetzwerk"  
  
1.  Verwenden Sie die Liste **Mining Modell** oben auf der Registerkarte **Mining Modell-Viewer** , um zum `TM_NaiveBayes` Modell zu wechseln.  
  
2.  Verwenden Sie die Liste **Viewer** , um zum **Microsoft Naive Bayes-Viewer**zu wechseln.  
  
3.  Klicken Sie `Bike Buyer` auf den Knoten, um seine Abhängigkeiten zu identifizieren.  
  
     Die rosa Schattierung gibt an, dass alle Attribute Auswirkungen auf den Fahrradkauf haben.  
  
4.  Stellen Sie den Schieberegler ein, um die einflussreichsten Attribute zu identifizieren.  
  
     Wenn Sie den Schieberegler nach unten ziehen, werden nur noch diejenigen Attribute angezeigt, welche die stärksten Auswirkungen auf die [Bike Buyer]-Spalte haben. Durch Anpassen des Schiebereglers können Sie herausfinden, dass die einflussreichsten Attribute unter anderem folgende sind: Anzahl der Autos im Besitz, Arbeitsweg und Anzahl der Kinder insgesamt.  
 
  
##  <a name="AttributeProfiles"></a>Attribut profile  
 Auf der Registerkarte **Attribut profile** wird beschrieben, wie sich unterschiedliche Zustände der Eingabe Attribute auf das Ergebnis des vorhersagbaren Attributs auswirken.  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Attributprofile"  
  
1.  Vergewissern Sie sich, dass `Bike Buyer` im Feld **vorhersagbare** Felder ausgewählt ist.  
  
2.  Wenn die **Mining Legende** die Anzeige der **Attribut profile**blockiert, verschieben Sie Sie nicht mehr.  
  
3.  Wählen Sie im Feld **Histogrammbalken** den Text **5**aus.  
  
     In unserem Modell stellt 5 die maximale Anzahl der Status einer Variablen dar.  
  
     Die Attribute, die sich auf den Status des vorhersagbaren Attributs auswirken, werden zusammen mit den Werten für jeden Status der Eingabeattribute und deren Verteilungen in jedem Status des vorhersagbaren Attributs aufgelistet.  
  
4.  Suchen Sie in der Spalte **Attribute** nach **Zahlen Autos im Besitz**von.  Beachten Sie die Unterschiede in den Histogrammen für Kunden, die ein Fahrrad gekauft haben (Spalte 1) und Kunden, die keinen Kauf getätigt haben (Spalte 0). Personen, die kein oder ein Auto besitzen, kaufen mit größerer Wahrscheinlichkeit ein Fahrrad.  
  
5.  Doppelklicken Sie in der Spalte Bike Buyer (Spalte mit der Bezeichnung 1) auf **die Zelle in der Zelle** .  
  
     Die **Mining Legende** zeigt eine ausführlichere Ansicht an.  
  
  
##  <a name="AttributeCharacteristics"></a>Attribut Merkmale  
 Mit der Registerkarte **Attribut Merkmale** können Sie ein Attribut und einen Wert auswählen, um zu sehen, wie häufig Werte für andere Attribute in den ausgewählten Wert Fällen angezeigt werden.  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Attributmerkmale"  
  
1.  Vergewissern Sie **** sich, dass `Bike Buyer` in der Liste Attribut die Option ausgewählt ist.  
  
2.  Legen Sie den **Wert** auf **1**fest.  
  
     Im Viewer sehen Sie, dass Kunden, die keine Kinder zu Hause und einen kurzen Arbeitsweg haben und in Nordamerika leben mit größerer Wahrscheinlichkeit ein Fahrrad kaufen.  
  
  
##  <a name="AttributeDiscrimination"></a>Attribut Unterscheidung  
 Mithilfe der Registerkarte **Attribut Unterscheidung** können Sie die Beziehung zwischen zwei diskreten Werten von Bike Einkauf und anderen Attributwerten untersuchen. Da das `TM_NaiveBayes` Modell nur zwei Zustände aufweist: 1 und 0, müssen Sie keine Änderungen am Viewer vornehmen.  
  
 Im Viewer können Sie sehen, dass Personen, die keine Autos besitzen, tendenziell Fahrräder kaufen. Personen, die zwei Autos besitzen, kaufen tendenziell keine Fahrräder.  
  
## <a name="related-tasks"></a>Related Tasks  
 Die folgenden Themen enthalten Beschreibungen zu den anderen Miningmodellen.  
  
-   [Untersuchen des Entscheidungsstruktur Modells &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Erkunden des Clustering-Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 5: Testen von Modellen &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Erkunden des Clustering-Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)   
 [Registerkarte Attribut Unterscheidung &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md)   
 [Registerkarte "Attribut profile" &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md)   
 [Registerkarte "Attribut Merkmale" &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md)   
 [Registerkarte Abhängigkeits Netzwerk &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  
