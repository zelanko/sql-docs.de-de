---
title: Registerkarte "Sequenz Cluster/Cluster Unterscheidung" (Mining Modell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.discrimination.f1
ms.assetid: 7dd16479-2633-4f4b-83bf-cf55972a2241
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 914629fca09d4bcffb5ac931316331bbb7e7eebe
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66069139"
---
# <a name="sequence-clustering-cluster-discrimination-tab-mining-model-viewer"></a>Registerkarte "Sequenzcluster/Clusterunterscheidung" (Miningmodell-Viewer)
  Auf der Registerkarte  **Clusterunterscheidung** im **Microsoft Sequence Cluster-Viewer** werden ausgewählte Cluster aus einem Sequenzclustermodell verglichen.  
  
 Mit dieser Sicht eines Sequenzclustermodells können Sie zwei Cluster vergleichen und anzeigen, welche Status und Übergänge unterschiedlich sind.  
  
 **Weitere Informationen:** [Microsoft Sequence Clustering-Algorithmus](data-mining/microsoft-sequence-clustering-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Mining Modell**  
 Wählen Sie ein anzuzeigendes, in der aktuellen Miningstruktur enthaltenes Miningmodell aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer oder den **Microsoft Generic Content Tree Viewer**verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Cluster 1**  
 Wählen Sie einen Cluster aus dem Modell aus.  
  
 **Cluster 2**  
 Wählen Sie einen zweiten Cluster aus dem Miningmodell aus, der mit **Cluster 1**verglichen werden soll.  
  
 Wenn Sie keinen anderen Cluster auswählen, wird der ausgewählte Cluster standardmäßig mit seinem Komplement verglichen, d. h. allen Fällen im Modell, die nicht in Cluster 1 enthalten sind.  
  
 **Unterscheidungs Ergebnisse \<für Cluster 1> \<und Cluster 2>**  
 Dieses Diagramm stellt einen ausführlichen Vergleich der ausgewählten Cluster bereit. Im Allgemeinen weist ein Clusteringmodell selten Status oder Werte ausschließlich einem einzelnen Cluster zu. Daher gibt der Viewer nur an, dass ein bestimmtes Attribut oder ein Status einen bestimmten Cluster *begünstigt* .  
  
 Insgesamt könnte ein bestimmter Cluster mehrere Status enthalten: Ein häufiger Status könnte z. B. der Kauf einer Wasserflasche und eines Flaschenhalters nacheinander sein. Die Sequenz könnte jedoch in anderen Clustern vorhanden sein, die wichtigere definierende Eigenschaften aufweisen. Zum Beispiel könnte ein anderer Cluster am stärksten durch sehr kurze Transaktionszeiten charakterisiert werden, und eine Analyse würde zeigen, dass die Artikel Wasserflasche und Flaschenhalter normalerweise in diesem Cluster gruppiert werden, jedoch nicht immer.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Variablen**|Ein Attribut im Miningmodell.|  
|**Werte**|Ein Status des Attributs, der unter **Variablen**aufgeführt ist.|  
|**Begünstigt \<Cluster 1>**|Enthält einen schattierten Balken, der anzeigt, wie sehr das Attribut und der Status, die unter **Variablen** und **Wert** aufgeführt sind, den unter **Cluster 1**ausgewählten Cluster begünstigen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
