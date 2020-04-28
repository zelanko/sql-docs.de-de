---
title: Mining Modell-Viewer (Modell-Designer für Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.viewers.f1
ms.assetid: 4ba391d5-c97b-4848-ba7c-7d096fa4b7dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9458f2c1fb3d170bf1b4a2887acae94b55ed877e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175804"
---
# <a name="mining-model-viewers-data-mining-model-designer"></a>Miningmodell-Viewer (Modell-Designer für Data Mining)
  Verwenden Sie die Registerkarte **Miningmodell-Viewer** , um die in einer Miningstruktur enthaltenen Miningmodelle zu durchsuchen.

 Wählen Sie erst das Miningmodell und anschließend einen Viewer aus. Für jedes Modell stehen stets zwei Viewer zur Verfügung: ein benutzerdefinierter Viewer, der mehrere Registerkarten umfassen kann, und der generische Viewer.

 Eine exemplarische Vorgehensweise zum Verwenden jedes Viewers finden Sie unter [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md).

## <a name="common-options"></a>Häufige Optionen
 **Viewerinhalt aktualisieren** Lädt das Miningmodell im Viewer neu.

 **Miningmodell** Wählen Sie ein anzuzeigendes, in der aktuellen Miningstruktur enthaltenes Miningmodell aus. Das Miningmodell wird zuerst im zugeordneten benutzerdefinierten Viewer geöffnet.

 **Viewer** Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Diese Liste [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] enthält die Viewer, die für jedes Mining Modell bereitstellt [!INCLUDE[msCoName](../includes/msconame-md.md)] , den Viewer für Mining Inhalte sowie alle Plug-in-Viewer.

 Das folgende Diagramm zeigt einen benutzerdefinierten Viewer und den generischen Viewer für das gleiche Modell an.

-   Das obere Diagramm zeigt den Viewer für ein Miningmodell auf Grundlage des Microsoft Time Series-Algorithmus an. Dieser spezielle benutzerdefinierte Viewer erstellt automatisch ein Diagramm der Zeitreihe und stellt fünf Vorhersagen zur Verfügung.

-   Das niedrigere Modell zeigt das gleiche Modell mit dem **Microsoft Generic Content Tree Viewer**. Dieser Viewer präsentiert den Inhalt des Miningmodells nach einem standardisierten Schema. Weitere Informationen finden Sie unter [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](microsoft-generic-content-tree-viewer-data-mining.md).

 ![Übersicht über den Data Mining-Modell-Designer](media/generic-mining-model-tab1.gif "Übersicht über den Data Mining-Modell-Designer")

## <a name="viewers-and-their-components"></a>Viewer und ihre Komponenten
 Abhängig vom Modell, das Sie auswählen, wird ein anderer benutzerdefinierter Viewer angezeigt, der an den Algorithmus angepasst wurde, mit dem Sie das ausgewählte Data Mining-Modell erstellt haben. Jeder benutzerdefinierte Viewer verfügt über mehrere Tools und Dialogfelder zum Untersuchen der Statistiken und Muster im Modell.

 Die folgende Liste beschreibt die Optionen in jeden der benutzerdefinierten Viewer.

### <a name="microsoft-association-rules-algorithm"></a>Microsoft Association Rules-Algorithmus

-   [Modell mit dem Microsoft-Viewer für Zuordnungsregeln durchsuchen](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)

    -   [Registerkarte "Itemsets" &#40;Mining Modell-Viewer&#41;](itemsets-tab-mining-model-viewer.md)

    -   [Registerkarte "Regeln" &#40;Mining Modell-Viewer&#41;](rules-tab-mining-model-viewer.md)

    -   [Registerkarte Abhängigkeits Netzwerk &#40;Mining Modell-Viewer&#41;](dependency-network-tab-mining-model-viewer.md)

### <a name="microsoft-clustering-algorithm"></a>Microsoft Clustering-Algorithmus

-   [Durchsuchen eines Modells mit dem Microsoft Cluster-Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)

    -   [Registerkarte "Cluster Diagramm" &#40;Mining Modell-Viewer&#41;](cluster-diagram-tab-mining-model-viewer.md)

    -   [Registerkarte "Cluster profile" &#40;Mining Modell-Viewer&#41;](cluster-profiles-tab-mining-model-viewer.md)

    -   [Registerkarte Cluster Merkmale &#40;Mining Modell-Viewer&#41;](cluster-characteristics-tab-mining-model-viewer.md)

    -   [Registerkarte Cluster Unterscheidung &#40;Mining Modell-Viewer&#41;](cluster-discrimination-tab-mining-model-viewer.md)

    -   [Mining Legende (Dialog Feld) &#40;Mining Modell-Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-decision-tree-algorithm"></a>Microsoft Decision Tree-Algorithmus

-   [Durchsuchen eines Modells mit dem Microsoft Struktur-Viewer](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)

    -   [Registerkarte "Entscheidungsstruktur" &#40;Mining Modell-Viewer&#41;](decision-tree-tab-mining-model-viewer.md)

    -   [Registerkarte Abhängigkeits Netzwerk &#40;Mining Modell-Viewer&#41;](dependency-network-tab-mining-model-viewer.md)

    -   [Mining Legende (Dialog Feld) &#40;Mining Modell-Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-linear-regression-algorithm"></a>Microsoft Linear Regression-Algorithmus

-   [Modell mit dem Microsoft-Viewer für neuronale Netzwerke durchsuchen](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   [Registerkarte "Entscheidungsstruktur" &#40;Mining Modell-Viewer&#41;](decision-tree-tab-mining-model-viewer.md)

    -   [Registerkarte Abhängigkeits Netzwerk &#40;Mining Modell-Viewer&#41;](dependency-network-tab-mining-model-viewer.md)

    -   [Mining Legende (Dialog Feld) &#40;Mining Modell-Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-logistic-regression-algorithm"></a>Microsoft Logistic Regression-Algorithmus

-   [Modell mit dem Microsoft-Viewer für neuronale Netzwerke durchsuchen](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

### <a name="microsoft-nave-bayes-algorithm"></a>Microsoft Naive Bayes-Algorithmus

-   [Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)

    -   [Registerkarte Abhängigkeits Netzwerk &#40;Mining Modell-Viewer&#41;](dependency-network-tab-mining-model-viewer.md)

    -   [Registerkarte "Attribut profile" &#40;Mining Modell-Viewer&#41;](attribute-profiles-tab-mining-model-viewer.md)

    -   [Registerkarte "Attribut Merkmale" &#40;Mining Modell-Viewer&#41;](attribute-characteristics-tab-mining-model-viewer.md)

    -   [Registerkarte Attribut Unterscheidung &#40;Mining Modell-Viewer&#41;](attribute-discrimination-tab-mining-model-viewer.md)

### <a name="microsoft-neural-network-algorithm"></a>Microsoft Neural Network Algorithm

-   [Modell mit dem Microsoft-Viewer für neuronale Netzwerke durchsuchen](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   [Registerkarte Abhängigkeits Netzwerk &#40;Mining Modell-Viewer&#41;](dependency-network-tab-mining-model-viewer.md)

    -   [&#40;Mining Modell-Viewer für neuronale Netzwerke&#41;](neural-network-mining-model-viewer.md)

    -   [Dialog Feld "Knoten suchen" &#40;Mining Modell-Viewer&#41;](find-node-dialog-box-mining-model-viewer.md)

### <a name="microsoft-sequence-clustering-algorithm"></a>Microsoft Sequence Clustering-Algorithmus

-   [Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)

    -   [Registerkarte "Sequenz Cluster/Cluster Diagramm" &#40;Mining Modell-Viewer](sequence-clustering-cluster-diagram-tab-mining-model-viewer.md)

    -   [Registerkarte "Sequenz Cluster-Cluster profile" &#40;Mining Modell-Viewer](sequence-clustering-cluster-profiles-tab-mining-model-viewer.md)

    -   [Registerkarte "Sequenz Cluster/Cluster Merkmale" &#40;Mining Modell-Viewer&#41;](sequence-clustering-cluster-characteristics-tab-mining-model-viewer.md)

    -   [Registerkarte "Sequenz Cluster/Cluster Unterscheidung" &#40;Mining Modell-Viewer&#41;](sequence-clustering-cluster-discrimination-tab-mining-model-viewer.md)

    -   [Registerkarte "Sequenz Cluster/Cluster Übergang" &#40;Mining Modell-Viewer&#41;](sequence-clustering-cluster-transition-tab-mining-model-viewer.md)

### <a name="microsoft-time-series-algorithm"></a>Microsoft Time Series-Algorithmus

-   [Durchsuchen eines Modells mit Microsoft Time Series-Viewer](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)

    -   [Registerkarte "Modell" &#40;Mining Modell-Viewer&#41;](model-tab-mining-model-viewers.md)

    -   [Registerkarte "Diagramm" &#40;Mining Modell-Viewer&#41;](chart-tab-mining-model-viewers.md)

    -   [Mining Legende (Dialog Feld) &#40;Mining Modell-Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)

## <a name="see-also"></a>Weitere Informationen
 [Mining Modelle Ansicht &#40;Data Mining-Modell-Designer&#41;](mining-models-view-data-mining-model-designer.md) [Mining Strukturansicht &#40;Data Mining-Modell-Designer&#41;](mining-structure-view-data-mining-model-designer.md) [Mining Genauigkeits Diagramm-Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) [Vorhersage Abfrage-Generator &#40;Data Mining&#41;](prediction-query-builder-data-mining.md)


