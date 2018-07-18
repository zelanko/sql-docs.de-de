---
title: Registerkarte "Clustermerkmale" (Miningmodell-Viewer)-Cluster | Microsoft-Dokumentation
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
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6f3b5076884e44926457437ef1c31fd595418edd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172081"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a>Registerkarte "Clustermerkmale" (Miningmodell-Viewer)
  Auf der Registerkarte **Clustermerkmale** können Sie die Eigenschaften eines Clusters in einem Clusteringmodell oder die Gruppe aller Fälle im Modell untersuchen. Das Diagramm zeigt die Wichtigkeit jedes Attribut/Wert-Paars als ein Merkmal, das den Cluster definiert, im Vergleich zu anderen Clustern.  
  
 **Weitere Informationen:** [Microsoft Clustering-Algorithmus](data-mining/microsoft-clustering-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Cluster-Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Tastatur  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein Miningmodell aus der aktuellen Miningstruktur aus. Das Miningmodell wird im benutzerdefinierten Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den diesem Modelltyp zugeordneten benutzerdefinierten Viewer oder den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Viewer für Mininginhalte verwenden. Sie können auch alle verfügbaren Plug-In-Viewer verwenden.  
  
 **Cluster**  
 Wählen Sie den anzuzeigenden Cluster aus, oder wählen Sie **Auffüllung (Alle)** aus, um die Verteilung der Attribute für das ganze Modell anzuzeigen.  
  
 **Merkmale für \<Cluster >**  
 Das Diagramm enthält die folgenden Spalten, in denen die Merkmale des ausgewählten Clusters beschrieben werden.  
  
|value|Description|  
|-----------|-----------------|  
|**Variable**|Listet die Attribute aus dem Miningmodell auf, die im ausgewählten Cluster vorhanden sind.|  
|**Werte**|Listet die Werte der aktuellen Attribute auf, die im derzeit ausgewählten Cluster vorhanden sind.|  
|**Wahrscheinlichkeit**|Der Balken gibt die Stärke des Attribut/Wert-Paars als kennzeichnendes Merkmal dieses Clusters an. Wenn Sie mit der Maus auf den Balken zeigen, wird der Wahrscheinlichkeitswert als Prozentsatz angezeigt. Dies gibt für diese Attribut/Wert-Kombination in jedem einzelnen Fall die Wahrscheinlichkeit an, dass der Fall in diesen Cluster gehört.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Datamining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
