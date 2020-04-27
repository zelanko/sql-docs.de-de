---
title: Registerkarte "Sequenz Cluster/Cluster Merkmale" (Mining Modell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.characteristics.f1
ms.assetid: 3a9e8a0c-7d03-47cc-8625-e68d73a8c947
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a3a9121129ab0f7e4e185e35418132a4f1aa663f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66069166"
---
# <a name="sequence-clustering-cluster-characteristics-tab-mining-model-viewer"></a>Registerkarte "Sequenzcluster/Clustermerkmale" (Miningmodell-Viewer)
  Die Registerkarte **Clustermerkmale** im **Microsoft Sequence Cluster-Viewer** stellt eine detaillierte Liste der Eigenschaften bereit, die einen Sequenzcluster definieren. Diese Eigenschaften können einfache Attribut/Wert-Paare, aber auch Übergänge zwischen Status einschließen.  
  
 Mit dieser Sicht eines Sequenzclustermodells können Sie einen Drilldown in den Clusterinhalt ausführen und die Sequenzen anzeigen, die für einen Cluster repräsentativ sind.  
  
 **Weitere Informationen:** [Microsoft Sequence Clustering-Algorithmus](data-mining/microsoft-sequence-clustering-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Mining Modell**  
 Wählen Sie ein anzuzeigendes, in der aktuellen Miningstruktur enthaltenes Miningmodell aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer oder den **Microsoft Generic Content Tree Viewer**verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Kombi**  
 Wählen Sie den Cluster aus, den Sie anzeigen möchten.  
  
 **Merkmale für \<Cluster>**  
 Diese Tabelle stellt eine Liste der Sequenzen bereit, die dem aktuellen Cluster zugewiesen wurden, sortiert nach Wahrscheinlichkeit. Beachten Sie, dass es sich bei einer Sequenz im Grunde um ein Attribut/Wert-Paar handelt, gefolgt von einem oder mehreren zusätzlichen Attribut/Wert-Paaren. Die Kombination aus Sequenzen und ihren Wahrscheinlichkeiten stellt die definierenden Eigenschaften jedes Clusters dar.  
  
 In einem Sequenzclustermodell auf Grundlage einer Warenkorbanalyse könnte ein Cluster z. B. als oberstes Merkmal einen Kunden aufweisen, der das Verkaufselement auswählt und dann die Transaktion beendet, ohne etwas anderes zu kaufen. In einem Sequenzclustermodell, mit dem Serverfehler analysiert werden sollen, könnten die primären Eigenschaften eines Clusters eine Reihe von häufig vorkommenden Fehlerereignissen sein.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Variable**|In dieser Spalte wird angegeben, ob es sich bei der Eigenschaft um einen Wert oder einen Übergang handelt.<br /><br /> Wenn das Merkmal ein Wert ist, enthält die Spalte **Variable** den Attributnamen.<br /><br /> Wenn das Merkmal einen Status Übergang darstellt, enthält die Spalte **Variable** den Text "Übergänge".|  
|**Werte**|Der Wert dieser Spalte hängt davon ab, ob das Merkmal ein einfaches Attribut/Wert-Paar oder ein Zustandsübergang ist, der eine häufige Sequenz von Elementen oder Ereignissen darstellt.<br /><br /> Wenn das Merkmal ein Wert ist, enthält die Spalte **Wert** den Status.<br /><br /> Wenn das Merkmal einen Status Übergang darstellt, enthält die Spalte **Wert** die Beschreibung des Status Übergangs.|  
|**Besteht**|In dieser Spalte wird ein Balken angezeigt, der die relative Wahrscheinlichkeit angibt, dass dieses Merkmal (entweder ein einfaches Attribut/Wert-Paar oder eine Kombination von Status) Element des aktuellen Clusters ist.<br /><br /> Sie können mit der Maus auf den Balken zeigen, um den Frequenzwert für das Merkmal anzuzeigen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
