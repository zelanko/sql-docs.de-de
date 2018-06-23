---
title: Untersuchen des Clustering-Modells (Lernprogramm zu Datamining-Lernprogramm) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0d731d16bdb19fdf600f050d580a8b018515fe8d
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313188"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a>Untersuchen des Clustering-Modells (Lernprogramm zu Data Mining-Grundlagen)
  Die [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus gruppiert Fälle in Clustern, die ähnliche Merkmale enthalten. Diese Gruppierungen eignen sich zum Durchsuchen von Daten, Identifizieren von Datenanomalien und Erstellen von Vorhersagen.  
  
 Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Cluster-Viewer bietet die folgenden Registerkarten zum Durchsuchen von Clusteringminingmodellen:  
  

  
##  <a name="ClusterDiagramTab"></a> Cluster-Registerkarte "Clusterdiagramm"  
 Auf der Registerkarte Clusterdiagramm werden alle Cluster in einem Miningmodell angezeigt. Die Linien zwischen den Clustern geben die jeweilige "Nähe" an. Ihre Schattierung hängt davon ab, wie groß die Ähnlichkeit zwischen den Clustern ist. Die tatsächliche Farbe der einzelnen Cluster gibt die Häufigkeit der Variablen und den Status im Cluster an.  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Clusterdiagramm"  
  
1.  Verwenden der **Miningmodell** Liste am oberen Rand der **Miningmodell-Viewer** Registerkarte wechseln Sie zu der `TM_Clustering` Modell.  
  
2.  In der **Viewer** Liste **Microsoft Cluster-Viewer**.  
  
3.  In der **Schattierungsvariable** wählen Sie im **Bike Buyer**.  
  
     Die Standardvariable lautet **Auffüllung**, aber Sie können diese ändern, um jedes beliebige Attribut des Modells, um festzustellen, welche Cluster jeweils Elemente enthalten, die die Attribute haben sollen.  
  
4.  Wählen Sie **1** in der **Status** auf jene Fälle zu untersuchen, in denen ein Fahrrad gekauft wurde.  
  
     Die **Dichte** Legende wird die Dichte des Attribut-/ statuspaares in Schattierungsvariable und Status der ausgewählten beschrieben. In diesem Beispiel weist es uns, dass die Clusterwith der dunkelsten Schattierung den höchsten Prozentsatz an fahrradkäufern hat.  
  
5.  Zeigen Sie mit der Maus auf den Cluster mit der dunkelsten Schattierung.  
  
     Eine QuickInfo zeigt den Prozentsatz von Fällen an, die über das Attribut `Bike Buyer = 1` verfügen.  
  
6.  Wählen Sie den Cluster mit der höchsten Dichte aus, mit der rechten Maustaste in des Clusters, wählen Sie **Cluster umbenennen** und Typ **Fahrradkäufer hoch** für die zukünftige Identifikation. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Suchen Sie den Cluster, der die hellste Schattierung (und die niedrigste Dichte) aufweist. Mit der rechten Maustaste in des Clusters, wählen Sie **Cluster umbenennen** und Typ **Fahrradkäufer niedrig**. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Klicken Sie auf die **Fahrradkäufer hoch** cluster, und ziehen Sie es auf einen Teil des Bereichs, die Sie löschen einen Überblick über alle Verbindungen zu anderen Clustern erkennen kann.  
  
     Wenn Sie einen Cluster auswählen, werden die Linien hervorgehoben, die diesen Cluster mit anderen Clustern verbinden, sodass Sie alle Beziehungen dieses Clusters rasch erkennen können. Wenn der Cluster nicht aktiviert ist, können Sie anhand der Dunkelheit der Linien erkennen, wie stark die Beziehungen zwischen allen Clustern im Diagramm sind. Ist die Schattierung schwach oder ist keine Schattierung vorhanden, sind sich die Cluster kaum ähnlich.  
  
9. Mithilfe des Schiebereglers links neben dem Netzwerk können Sie schwächere Links herausfiltern und die Cluster mit den engsten Beziehungen finden. Die Marketingabteilung von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] kann ähnliche Cluster kombinieren, um die beste Methode für das Targeted Mailing zu ermitteln.  
  

  
##  <a name="ClusterProfilesTab"></a> Registerkarte Clusterprofile  
 Die **Clusterprofile** Registerkarte bietet einen Überblick über die `TM_Clustering` Modell. Die **Clusterprofile** Registerkarte enthält eine Spalte für jeden Cluster im Modell. In der ersten Spalte werden die Attribute aufgelistet, die mit mindestens einem Cluster verknüpft sind. Der Rest des Viewers umfasst die Verteilung der Status eines Attributs für jeden Cluster. Die Verteilung einer diskreten Variablen wird dargestellt, als farbige Balken mit der maximalen Anzahl Balken wird in der **Histogrammbalken** Liste. Kontinuierliche Attribute werden in einem Rautendiagramm angezeigt, das die mittlere und die Standardabweichung in jedem Cluster angibt.  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Profile"  
  
1.  Legen Sie **Histogramm** Steuerleisten **5**.  
  
     In unserem Modell stellt 5 die maximale Anzahl der Status einer Variablen dar.  
  
2.  Wenn die **Mininglegende** blockiert die Anzeige der **Attributprofile**, verschieben Sie sie aus dem Weg.  
  
3.  Wählen Sie die **Fahrradkäufer hoch** Spalte und ziehen Sie es rechts neben der **Auffüllung** Spalte.  
  
4.  Wählen Sie die **Fahrradkäufer niedrig** Spalte und ziehen Sie es rechts neben der **Fahrradkäufer hoch** Spalte.  
  
5.  Klicken Sie auf die **Fahrradkäufer hoch** Spalte.  
  
     Die **Variablen** Spalte in der Reihenfolge ihrer Wichtigkeit für diesen Cluster sortiert wird. Führen Sie einen Bildlauf durch die Spalte aus, und überprüfen Sie Merkmale des Clusters Fahrradkäufer hoch. Beispielsweise ist hier die Wahrscheinlichkeit eines kurzen Arbeitswegs höher.  
  
6.  Doppelklicken Sie auf die **Alter** Zelle der **Fahrradkäufer hoch** Spalte.  
  
     Die **Mininglegende** enthält eine detailliertere anzeigen und Sie können die Altersgruppe der Kunden sowie Durchschnittsalter anzeigen.  
  
7.  Mit der rechten Maustaste die **Fahrradkäufer niedrig** Spalte, und wählen **Spalte ausblenden**.  
  

  
##  <a name="ClusterCharacteristicsTab"></a> Registerkarte Clustermerkmale  
 Mit der **Clustermerkmale** Registerkarte können Sie untersuchen ausführlicher Merkmale, die einen Cluster darstellen. Anstatt die Merkmale aller Cluster (wie auf der Registerkarte Clusterprofile) zu vergleichen, können Sie auch einen Cluster nach dem anderen betrachten. Wenn Sie auswählen, z. B. **Fahrradkäufer hoch** aus der **Cluster** Liste, sehen Sie die Merkmale der Kunden in diesem Cluster. Die Anzeige unterscheidet sich zwar vom Viewer für Clusterprofile, die Ergebnisse sind jedoch gleich.  
  
> [!NOTE]  
>  Es sei denn, Sie legen Sie einen Anfangswert für **Holdoutseed**, die Ergebnisse variieren jeder Verarbeitung des Modells. Weitere Informationen finden Sie unter [HoldoutSeed-Element](../analysis-services/scripting/properties/holdoutseed-element.md)  
  

  
##  <a name="ClusterDiscriminationTab"></a> Registerkarte Clusterunterscheidung  
 Mit der **Clusterunterscheidung** Registerkarte, untersuchen Sie die Eigenschaften, die einen Cluster voneinander unterscheiden. Nach der Auswahl von zwei Clustern, aus der **Cluster 1** Liste und aus der **Cluster 2** Viewer berechnet die Unterschiede zwischen den Clustern und zeigt eine Liste der Attribute, unterscheiden Sie die Cluster am häufigsten.  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a>So untersuchen Sie das Modell auf der Registerkarte "Clusterunterscheidung"  
  
1.  In der **Cluster 1** wählen Sie im **Fahrradkäufer hoch**.  
  
2.  In der **Cluster 2** wählen Sie im **Fahrradkäufer niedrig**.  
  
3.  Klicken Sie auf **Variablen** alphabetisch sortiert.  
  
     Einige der bedeutenderen Unterschieden bei den Kunden in den **Fahrradkäufer niedrig** und **Fahrradkäufer hoch** Clustern gehören Alter, autobesitz, kinderzahl und Region.  
  
## <a name="related-tasks"></a>Related Tasks  
 Die folgenden Themen enthalten Beschreibungen zu den anderen Miningmodellen.  
  
-   [Untersuchen des Entscheidungsstrukturmodells &#40;Lernprogramm zu Datamining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Untersuchen des Naive Bayes-Modells &#40;Lernprogramm zu Datamining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Untersuchen des Naive Bayes-Modells &#40;Lernprogramm zu Datamining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Untersuchen des Entscheidungsstrukturmodells &#40;Lernprogramm zu Datamining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen eines Modells mit dem Microsoft Cluster-Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)   
 [Registerkarte "Attributunterscheidung" Cluster &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md)   
 [Cluster Profile Registerkarte &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md)   
 [Registerkarte "Attributmerkmale" Cluster &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md)   
 [Registerkarte "Clusterdiagramm" Cluster &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)  
  
  