---
title: Registerkarte "Sequenz Cluster-Cluster profile" (Mining Modell-Viewer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.profiles.f1
ms.assetid: 44230895-0a42-4032-8d6c-0cdb8a2dbb8c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f277abea585715f6a3656fffe7672f347233507
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66069096"
---
# <a name="sequence-clustering-cluster-profiles-tab-mining-model-viewer"></a>Registerkarte "Clusterprofile des Sequenzclustermodells" (Miningmodell-Viewer)
  Auf der Registerkarte **Clusterprofile** im **Microsoft Sequence Cluster-Viewer** wird eine farbcodierte Sicht der in den einzelnen Clustern enthaltenen Sequenzen bereitgestellt.  
  
 Mit dieser Sicht eines Sequenzclustermodells erhalten Sie einen schnellen Überblick über die Gruppierung der vom Modell gefundenen Sequenzen. Sie können auf einen Blick sehen, wie viele Sequenzen lang bzw. kurz sind. Sie können auch auf einen Cluster klicken und die **Mininglegende** anzeigen, um genau sehen zu können, welche Status die Farben in den Sequenzen angeben.  
  
 **Weitere Informationen:**  [Microsoft Sequence Clustering-Algorithmus](data-mining/microsoft-sequence-clustering-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Mining Modell**  
 Wählen Sie ein anzuzeigendes, in der aktuellen Miningstruktur enthaltenes Miningmodell aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer oder den **Microsoft Generic Content Tree Viewer**verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Legende anzeigen**  
 Wählen Sie diese Option zum Anzeigen einer Legende aus, in der die Korrelation zwischen den in den Clusterprofilen angezeigten Farben und den Textwerten der Status angezeigt wird.  
  
 **Histogrammbalken**  
 Mit dieser Option können Sie die Anzahl der farbigen Balken im Histogramm ändern. Sind mehr Balken vorhanden, als Sie zum Anzeigen ausgewählt haben, werden die wichtigsten Balken beibehalten. Die restlichen Balken werden unter **Sonstige**gruppiert.  
  
 **Attribute** und **Clusterprofile**  
 In diesem Abschnitt des Diagramms werden die Cluster von Sequenzen aufgeführt, die im Modell gefunden wurden.  
  
 Jeder Sequenzcluster wird mit der Anzahl der Status angezeigt, die Sie in der Option **Histogrammbalken**ausgewählt haben.  
  
 Für jeden Cluster im Modell werden zwei Sätze von Histogrammen angezeigt, jeweils in einer anderen Zeile im Diagramm:  
  
-   **Attribut Name>. Samples: die Histogramme in dieser Zeile zeigen die Sequenzen von Elementen an, die für jeden Cluster repräsentativ sind. \<** In DMX-Begriffen ausgedrückt, sind dies die Beispielfälle für jeden Cluster.  
  
-   Attribut Name>: die Histogramme in dieser Zeile beschreiben alle Elemente, die der Cluster enthält, sowie ihre Gesamtverteilung. ** \< ** Klicken Sie auf ein Histogramm, wenn die **Mininglegende** sichtbar ist, um die jeweiligen numerischen Werte anzuzeigen.  
  
 **Zustände**  
 Diese Spalte im Diagramm ist optional und kann durch Auswählen der Option **Legende anzeigen** angezeigt bzw. entfernt werden. Die Spalte **Status** bietet einen Überblick darüber, welcher Status durch welche Farbe im entsprechenden Clusterhistogramm dargestellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Microsoft Sequence Clustering-Algorithmus](data-mining/microsoft-sequence-clustering-algorithm.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Viewer für Data Mining-Modelle](data-mining/data-mining-model-viewers.md)   
 [Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
  
