---
title: Registerkarte "Clusterunterscheidung" (Miningmodell-Viewer)-Cluster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.discrimination.f1
ms.assetid: ae7cfff7-ab1c-4cf5-9a91-97b21d15d85f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d55f61d9255d19f22fffb7380785a2ada1a2763
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66087900"
---
# <a name="cluster-discrimination-tab-mining-model-viewer"></a>Registerkarte "Clusterunterscheidung" (Miningmodell-Viewer)
  Verwenden Sie die Registerkarte **Clusterunterscheidung** , um zwei in einem Clusteringmodell vorhandene Cluster zu vergleichen. Sie können sehen, wie unterschiedliche Kombinationen von Attributen und Werten innerhalb der Cluster dargestellt werden.  
  
 **Weitere Informationen finden Sie unter** [Microsoft Clustering-Algorithmus](data-mining/microsoft-clustering-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Cluster-Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein Miningmodell aus der aktuellen Miningstruktur aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer für Clusteringmodelle oder den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Viewer für Mininginhalte verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Cluster 1**  
 Wählen Sie einen Cluster aus, damit Sie ihn mit einem anderen Cluster vergleichen können.  
  
 **Cluster 2**  
 Wählen Sie einen zweiten Cluster in der Clusterliste im Miningmodell aus, der mit **Cluster 1**verglichen werden soll. Sie können auch einen Cluster mit seinem Komplement vergleichen, d. h. mit allen Fällen im Modell mit Ausnahme der Fälle im ausgewählten Cluster.  
  
 **Unterscheidungsergebnisse für \<cluster 1 > und \<cluster 2 >**  
 Die Spalten im Diagramm enthalten Informationen über die Beziehungen zwischen den einzelnen Attribut/Wert-Paaren und den beiden ausgewählten Clustern.  
  
|||  
|-|-|  
|**Variablen**|Ein Attribut im Miningmodell.|  
|**Werte**|Ein Wert des in **Variablen**ausgewählten Attributs.|  
|**Begünstigt \<cluster 1 >**|Das Balkendiagramm auf der linken Seite stellt die Wahrscheinlichkeit dar, dass das ausgewählte Attribut/Wert-Paar für den in **Cluster 1** ausgewählten Cluster repräsentativ ist. Sie können mit der Maus auf den Balken zeigen, um einen als Prozentsatz dargestellten Wert anzuzeigen. Beachten Sie, dass dies auch, wenn der Wert 0 (null) ist, das Attribut / Wert bedeutet nicht fehlt unbedingt aus dem Cluster nur, dass die Verteilung auf, einen Cluster gegenüber dem anderen stark begünstigt.|  
|**Begünstigt \<cluster 2 >**|Das Balkendiagramm auf der rechten Seite stellt die Wahrscheinlichkeit dar, dass das ausgewählte Attribut/Wert-Paar für den in **Cluster 2** ausgewählten Cluster repräsentativ ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Data Mining-Modelldesigner&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
