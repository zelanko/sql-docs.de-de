---
title: Sequence Clustering-Registerkarte Clusterunterscheidung (Miningmodell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.discrimination.f1
ms.assetid: 7dd16479-2633-4f4b-83bf-cf55972a2241
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d4debc43286ffb3fe4f87115ed15e9b4c3f74b06
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187147"
---
# <a name="sequence-clustering-cluster-discrimination-tab-mining-model-viewer"></a>Registerkarte "Sequenzcluster/Clusterunterscheidung" (Miningmodell-Viewer)
  Auf der Registerkarte  **Clusterunterscheidung** im **Microsoft Sequence Cluster-Viewer** werden ausgewählte Cluster aus einem Sequenzclustermodell verglichen.  
  
 Mit dieser Sicht eines Sequenzclustermodells können Sie zwei Cluster vergleichen und anzeigen, welche Status und Übergänge unterschiedlich sind.  
  
 **Weitere Informationen:** [Microsoft Sequence Clustering-Algorithmus](data-mining/microsoft-sequence-clustering-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Tastatur  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein anzuzeigendes, in der aktuellen Miningstruktur enthaltenes Miningmodell aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer oder den **Microsoft Generic Content Tree Viewer**verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Cluster 1**  
 Wählen Sie einen Cluster aus dem Modell aus.  
  
 **Cluster 2**  
 Wählen Sie einen zweiten Cluster aus dem Miningmodell aus, der mit **Cluster 1**verglichen werden soll.  
  
 Wenn Sie keinen anderen Cluster auswählen, wird der ausgewählte Cluster standardmäßig mit seinem Komplement verglichen, d. h. allen Fällen im Modell, die nicht in Cluster 1 enthalten sind.  
  
 **Unterscheidungsergebnisse für \<cluster 1 > und \<cluster 2 >**  
 Dieses Diagramm stellt einen ausführlichen Vergleich der ausgewählten Cluster bereit. Im Allgemeinen weist ein Clusteringmodell selten Status oder Werte ausschließlich einem einzelnen Cluster zu. Daher gibt der Viewer nur an, dass ein bestimmtes Attribut oder ein Status einen bestimmten Cluster *begünstigt* .  
  
 Insgesamt könnte ein bestimmter Cluster mehrere Status enthalten: Ein häufiger Status könnte z. B. der Kauf einer Wasserflasche und eines Flaschenhalters nacheinander sein. Die Sequenz könnte jedoch in anderen Clustern vorhanden sein, die wichtigere definierende Eigenschaften aufweisen. Zum Beispiel könnte ein anderer Cluster am stärksten durch sehr kurze Transaktionszeiten charakterisiert werden, und eine Analyse würde zeigen, dass die Artikel Wasserflasche und Flaschenhalter normalerweise in diesem Cluster gruppiert werden, jedoch nicht immer.  
  
|value|Description|  
|-----------|-----------------|  
|**Variablen**|Ein Attribut im Miningmodell.|  
|**Werte**|Ein Status des Attributs, der unter **Variablen**aufgeführt ist.|  
|**Begünstigt \<cluster 1 >**|Enthält einen schattierten Balken, der anzeigt, wie sehr das Attribut und der Status, die unter **Variablen** und **Wert** aufgeführt sind, den unter **Cluster 1**ausgewählten Cluster begünstigen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Datamining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
