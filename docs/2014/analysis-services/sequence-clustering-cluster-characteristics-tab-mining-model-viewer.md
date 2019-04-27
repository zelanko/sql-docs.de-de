---
title: Sequence Clustering-Cluster ", Registerkarte" Clustermerkmale "(Miningmodell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.characteristics.f1
ms.assetid: 3a9e8a0c-7d03-47cc-8625-e68d73a8c947
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 156bd83662b9b6fa42eb99e8e5810bb4fc71d51a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62747266"
---
# <a name="sequence-clustering-cluster-characteristics-tab-mining-model-viewer"></a>Registerkarte "Sequenzcluster/Clustermerkmale" (Miningmodell-Viewer)
  Die Registerkarte **Clustermerkmale** im **Microsoft Sequence Cluster-Viewer** stellt eine detaillierte Liste der Eigenschaften bereit, die einen Sequenzcluster definieren. Diese Eigenschaften können einfache Attribut/Wert-Paare, aber auch Übergänge zwischen Status einschließen.  
  
 Mit dieser Sicht eines Sequenzclustermodells können Sie einen Drilldown in den Clusterinhalt ausführen und die Sequenzen anzeigen, die für einen Cluster repräsentativ sind.  
  
 **Weitere Informationen finden Sie unter** [Microsoft Sequence Clustering-Algorithmus](data-mining/microsoft-sequence-clustering-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein anzuzeigendes, in der aktuellen Miningstruktur enthaltenes Miningmodell aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer oder den **Microsoft Generic Content Tree Viewer**verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Cluster**  
 Wählen Sie den Cluster aus, den Sie anzeigen möchten.  
  
 **Merkmale für \<Cluster >**  
 Diese Tabelle stellt eine Liste der Sequenzen bereit, die dem aktuellen Cluster zugewiesen wurden, sortiert nach Wahrscheinlichkeit. Beachten Sie, dass es sich bei einer Sequenz im Grunde um ein Attribut/Wert-Paar handelt, gefolgt von einem oder mehreren zusätzlichen Attribut/Wert-Paaren. Die Kombination aus Sequenzen und ihren Wahrscheinlichkeiten stellt die definierenden Eigenschaften jedes Clusters dar.  
  
 In einem Sequenzclustermodell auf Grundlage einer Warenkorbanalyse könnte ein Cluster z. B. als oberstes Merkmal einen Kunden aufweisen, der das Verkaufselement auswählt und dann die Transaktion beendet, ohne etwas anderes zu kaufen. In einem Sequenzclustermodell, mit dem Serverfehler analysiert werden sollen, könnten die primären Eigenschaften eines Clusters eine Reihe von häufig vorkommenden Fehlerereignissen sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Variable**|Diese Spalte gibt an, ob das Merkmal ein Wert ist oder ein Übergang.<br /><br /> Wenn das Merkmal ein Wert ist die **Variable** Spalte enthält den Attributnamen an.<br /><br /> Wenn das Merkmal einen Statusübergang darstellt. die **Variable** Spalte enthält den Text "Übergänge".|  
|**Werte**|Der Wert dieser Spalte hängt davon, ob das Merkmal ein einfaches Attribut / Wert-Paar ist, oder ein Statusübergang, der eine allgemeine Sequenz von Elementen oder Ereignissen darstellt.<br /><br /> Wenn das Merkmal ein Wert ist die **Wert** Spalte enthält den Status.<br /><br /> Wenn das Merkmal einen Statusübergang darstellt. die **Wert** Spalte enthält die Beschreibung des statusübergangs.|  
|**Wahrscheinlichkeit**|In dieser Spalte wird ein Balken angezeigt, der die relative Wahrscheinlichkeit angibt, dass dieses Merkmal (entweder ein einfaches Attribut/Wert-Paar oder eine Kombination von Status) Element des aktuellen Clusters ist.<br /><br /> Sie können mit der Maus auf den Balken zeigen, um den Frequenzwert für das Merkmal anzuzeigen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Data Mining-Modelldesigner&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
