---
title: Sequence Clustering-Cluster ", Registerkarte" Clustermerkmale "(Miningmodell-Viewer) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.characteristics.f1
ms.assetid: 3a9e8a0c-7d03-47cc-8625-e68d73a8c947
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 75601cb33f04eaacfdb3970f858dd8a359abd4bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161214"
---
# <a name="sequence-clustering-cluster-characteristics-tab-mining-model-viewer"></a>Registerkarte "Sequenzcluster/Clustermerkmale" (Miningmodell-Viewer)
  Die Registerkarte **Clustermerkmale** im **Microsoft Sequence Cluster-Viewer** stellt eine detaillierte Liste der Eigenschaften bereit, die einen Sequenzcluster definieren. Diese Eigenschaften können einfache Attribut/Wert-Paare, aber auch Übergänge zwischen Status einschließen.  
  
 Mit dieser Sicht eines Sequenzclustermodells können Sie einen Drilldown in den Clusterinhalt ausführen und die Sequenzen anzeigen, die für einen Cluster repräsentativ sind.  
  
 **Weitere Informationen:** [Microsoft Sequence Clustering-Algorithmus](data-mining/microsoft-sequence-clustering-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Tastatur  
 **Viewerinhalt**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein anzuzeigendes, in der aktuellen Miningstruktur enthaltenes Miningmodell aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Ereignisanzeige**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer oder den **Microsoft Generic Content Tree Viewer**verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Cluster**  
 Wählen Sie den Cluster aus, den Sie anzeigen möchten.  
  
 **Merkmale für \<Cluster >**  
 Diese Tabelle stellt eine Liste der Sequenzen bereit, die dem aktuellen Cluster zugewiesen wurden, sortiert nach Wahrscheinlichkeit. Beachten Sie, dass es sich bei einer Sequenz im Grunde um ein Attribut/Wert-Paar handelt, gefolgt von einem oder mehreren zusätzlichen Attribut/Wert-Paaren. Die Kombination aus Sequenzen und ihren Wahrscheinlichkeiten stellt die definierenden Eigenschaften jedes Clusters dar.  
  
 In einem Sequenzclustermodell auf Grundlage einer Warenkorbanalyse könnte ein Cluster z. B. als oberstes Merkmal einen Kunden aufweisen, der das Verkaufselement auswählt und dann die Transaktion beendet, ohne etwas anderes zu kaufen. In einem Sequenzclustermodell, mit dem Serverfehler analysiert werden sollen, könnten die primären Eigenschaften eines Clusters eine Reihe von häufig vorkommenden Fehlerereignissen sein.  
  
|value|Description|  
|-----------|-----------------|  
|**Variable**|Diese Spalte gibt an, ob das Merkmal ein Wert oder einen Übergang.<br /><br /> Wenn das Merkmal ein Wert, ist die **Variable** Spalte enthält den Namen des Attributs.<br /><br /> Wenn das Merkmal einen Statusübergang darstellt der **Variable** Spalte enthält den Text "Übergänge".|  
|**Werte**|Der Wert dieser Spalte hängt davon, ob das Merkmal ein einfaches Attribut / Wert-Paar ist, oder ein Statusübergang, eine häufige Sequenz von Elementen oder Ereignissen darstellt.<br /><br /> Wenn das Merkmal ein Wert, ist die **Wert** Spalte enthält den Status.<br /><br /> Wenn das Merkmal einen Statusübergang darstellt der **Wert** Spalte enthält die Beschreibung des statusübergangs.|  
|**Wahrscheinlichkeit**|In dieser Spalte wird ein Balken angezeigt, der die relative Wahrscheinlichkeit angibt, dass dieses Merkmal (entweder ein einfaches Attribut/Wert-Paar oder eine Kombination von Status) Element des aktuellen Clusters ist.<br /><br /> Sie können mit der Maus auf den Balken zeigen, um den Frequenzwert für das Merkmal anzuzeigen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Datamining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  