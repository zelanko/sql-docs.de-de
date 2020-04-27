---
title: Untersuchen des Clustering-Modells (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9bb2c6457122a5ea49824ca178b6950d88f75563
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63280429"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a>Untersuchen des Clustering-Modells (Lernprogramm zu Data Mining-Grundlagen)
  Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus gruppiert Fälle in Clustern, die ähnliche Merkmale aufweisen. Diese Gruppierungen eignen sich zum Durchsuchen von Daten, Identifizieren von Datenanomalien und Erstellen von Vorhersagen.  
  
 Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Cluster-Viewer bietet die folgenden Registerkarten zum Durchsuchen von Clusteringminingmodellen:  
  

  
##  <a name="cluster-diagram-tab"></a><a name="ClusterDiagramTab"></a>Registerkarte Cluster Diagramm  
 Auf der Registerkarte Clusterdiagramm werden alle Cluster in einem Miningmodell angezeigt. Die Linien zwischen den Clustern geben die jeweilige "Nähe" an. Ihre Schattierung hängt davon ab, wie groß die Ähnlichkeit zwischen den Clustern ist. Die tatsächliche Farbe der einzelnen Cluster gibt die Häufigkeit der Variablen und den Status im Cluster an.  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Clusterdiagramm"  
  
1.  Verwenden Sie die Liste **Mining Modell** oben auf der Registerkarte **Mining Modell-Viewer** , um zum `TM_Clustering` Modell zu wechseln.  
  
2.  Wählen Sie in der Liste **Viewer** den Bereich **Microsoft Cluster-Viewer**aus.  
  
3.  Wählen Sie im Feld **Schattierungs Variable** die Option **Bike Buyer**aus.  
  
     Die Standard Variable ist Auffüllung. Sie können **diese jedoch in**jedes beliebige Attribut des Modells ändern, um zu ermitteln, welche Cluster Member mit den gewünschten Attributen enthalten.  
  
4.  Wählen Sie im Feld **Status** die Option **1** aus, um die Fälle zu untersuchen, in denen ein Fahrrad gekauft wurde  
  
     Die **Dichte** Legende beschreibt die Dichte des Attribut Zustands Paars, das in der Schattierungs Variablen und dem Status ausgewählt ist. In diesem Beispiel gibt es Aufschluss darüber, dass der Cluster mit der dunkelsten Schattierung über den höchsten Prozentsatz der Fahrrad Käufer verfügt.  
  
5.  Zeigen Sie mit der Maus auf den Cluster mit der dunkelsten Schattierung.  
  
     Eine QuickInfo zeigt den Prozentsatz von Fällen an, die über das Attribut `Bike Buyer = 1` verfügen.  
  
6.  Wählen Sie den Cluster mit der höchsten Dichte aus, klicken Sie mit der rechten Maustaste auf den Cluster, wählen Sie **Cluster umbenennen** aus, und geben Sie für spätere Identifizierung **Bike Buyers High** [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Suchen Sie den Cluster, der die hellste Schattierung (und die niedrigste Dichte) aufweist. Klicken Sie mit der rechten Maustaste auf den Cluster, und wählen Sie **Cluster umbenennen** **aus.** [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Klicken Sie auf den Cluster **Fahrrad Käufer hoch** , und ziehen Sie ihn in einen Bereich des Bereichs, in dem Sie eine klare Ansicht der Verbindungen mit den anderen Clustern erhalten.  
  
     Wenn Sie einen Cluster auswählen, werden die Linien hervorgehoben, die diesen Cluster mit anderen Clustern verbinden, sodass Sie alle Beziehungen dieses Clusters rasch erkennen können. Wenn der Cluster nicht ausgewählt ist, können Sie erkennen, wie stark sich die Beziehungen zwischen allen Clustern im Diagramm befinden. Ist die Schattierung schwach oder ist keine Schattierung vorhanden, sind sich die Cluster kaum ähnlich.  
  
9. Mithilfe des Schiebereglers links neben dem Netzwerk können Sie schwächere Links herausfiltern und die Cluster mit den engsten Beziehungen finden. Die Marketingabteilung von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] kann ähnliche Cluster kombinieren, um die beste Methode für das Targeted Mailing zu ermitteln.  
  

  
##  <a name="cluster-profiles-tab"></a><a name="ClusterProfilesTab"></a>Registerkarte Cluster profile  
 Die Registerkarte **Cluster profile** bietet eine allgemeine Ansicht des `TM_Clustering` Modells. Die Registerkarte **Cluster profile** enthält eine Spalte für jeden Cluster im Modell. In der ersten Spalte werden die Attribute aufgelistet, die mit mindestens einem Cluster verknüpft sind. Der Rest des Viewers umfasst die Verteilung der Status eines Attributs für jeden Cluster. Die Verteilung einer diskreten Variablen wird als farbiger Balken mit der maximalen Anzahl von Balken in der Liste der **Histogrammbalken** angezeigt. Kontinuierliche Attribute werden in einem Rautendiagramm angezeigt, das die mittlere und die Standardabweichung in jedem Cluster angibt.  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Profile"  
  
1.  Legen Sie für **Histogrammbalken** den Wert **5**fest.  
  
     In unserem Modell stellt 5 die maximale Anzahl der Status einer Variablen dar.  
  
2.  Wenn die **Mining Legende** die Anzeige der **Attribut profile**blockiert, verschieben Sie Sie nicht mehr.  
  
3.  Wählen Sie die Spalte **Bike Buyers High** aus, und ziehen Sie diese rechts neben die Spalte **Population** .  
  
4.  Wählen Sie die Spalte **Fahrrad Käufer niedrig** aus, und ziehen Sie diese rechts neben die Spalte **Fahrrad Käufer hoch** .  
  
5.  Klicken Sie auf die Spalte **Fahrrad Käufer hoch** .  
  
     Die Spalte **Variablen** wird in der Reihenfolge ihrer Wichtigkeit für diesen Cluster sortiert. Führen Sie einen Bildlauf durch die Spalte aus, und überprüfen Sie Merkmale des Clusters Fahrradkäufer hoch. Beispielsweise ist hier die Wahrscheinlichkeit eines kurzen Arbeitswegs höher.  
  
6.  Doppelklicken Sie in der Spalte **Fahrrad Käufer hoch** auf die Zelle **Alter** .  
  
     Die **Mining Legende** zeigt eine ausführlichere Ansicht an, und Sie können den Altersbereich dieser Kunden sowie das mittlere Alter sehen.  
  
7.  Klicken Sie mit der rechten Maustaste auf die Spalte **Fahrrad Käufer niedrig** , und wählen Sie **Spalte ausblenden**.  
  

  
##  <a name="cluster-characteristics-tab"></a><a name="ClusterCharacteristicsTab"></a>Registerkarte Cluster Merkmale  
 Auf der Registerkarte **Cluster Merkmale** können Sie die Merkmale eines Clusters ausführlicher untersuchen. Anstatt die Merkmale aller Cluster (wie auf der Registerkarte Clusterprofile) zu vergleichen, können Sie auch einen Cluster nach dem anderen betrachten. Wenn Sie z. b. **Bike Buyers High** aus der Liste **Cluster** auswählen, können Sie die Merkmale der Kunden in diesem Cluster sehen. Die Anzeige unterscheidet sich zwar vom Viewer für Clusterprofile, die Ergebnisse sind jedoch gleich.  
  
> [!NOTE]  
>  Wenn Sie keinen Anfangswert für **HoldoutSeed**festlegen, variieren die Ergebnisse jedes Mal, wenn Sie das Modell verarbeiten. Weitere Informationen finden Sie unter [HoldoutSeed-Element](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)  
  

  
##  <a name="cluster-discrimination-tab"></a><a name="ClusterDiscriminationTab"></a>Registerkarte Cluster Unterscheidung  
 Mithilfe der Registerkarte **Cluster Unterscheidung** können Sie die Merkmale unterscheiden, die einen Cluster von einem anderen Cluster unterscheiden. Nachdem Sie zwei Cluster ausgewählt haben, eine aus der Liste **Cluster 1** und eine aus der Liste **Cluster 2** , berechnet der Viewer die Unterschiede zwischen den Clustern und zeigt eine Liste der Attribute an, die die Cluster am meisten unterscheiden.  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Clusterunterscheidung"  
  
1.  Wählen Sie im Feld **Cluster 1** die Option **Bike Buyers High**aus.  
  
2.  Wählen Sie im Feld **Cluster 2** die Option **Fahrrad Käufer niedrig**aus.  
  
3.  Klicken Sie auf **Variablen** , um alphabetisch zu sortieren.  
  
     Zu den wesentlichen Unterschieden zwischen den Kunden in den Clustern **Fahrrad Käufer niedrig** und **Fahrrad Käufer hoch** gehören Alter, Autobesitz, Anzahl der untergeordneten Elemente und Region.  
  
## <a name="related-tasks"></a>Related Tasks  
 Die folgenden Themen enthalten Beschreibungen zu den anderen Miningmodellen.  
  
-   [Untersuchen des Entscheidungsstruktur Modells &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Untersuchen des Naive Bayes-Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Untersuchen des Naive Bayes-Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Untersuchen des Entscheidungsstruktur Modells &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen eines Modells mit dem Microsoft Cluster-Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)   
 [Registerkarte Cluster Unterscheidung &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md)   
 [Registerkarte "Cluster profile" &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md)   
 [Registerkarte Cluster Merkmale &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md)   
 [Registerkarte "Cluster Diagramm" &#40;Mining Modell-Viewer&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)  
  
  
