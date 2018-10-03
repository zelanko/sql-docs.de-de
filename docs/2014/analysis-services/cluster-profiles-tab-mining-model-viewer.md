---
title: Cluster Profile Registerkarte (Miningmodell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.profiles.f1
ms.assetid: 1ebafa1f-74e9-4c05-b278-a690fa8543bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 663b12f2e83de016d3f1799536b8a3ed674ef544
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196076"
---
# <a name="cluster-profiles-tab-mining-model-viewer"></a>Registerkarte "Clusterprofile" (Miningmodell-Viewer)
  Auf der Registerkarte **Clusterprofile** erhalten Sie einen Überblick über die vom Algorithmus in einem Clustermodell erkannten Cluster. Die Registerkarte zeigt jedes Attribut zusammen mit der Verteilung des Attributs in jedem Cluster an.  
  
 **Weitere Informationen finden Sie unter:** [Microsoft Clustering-Algorithmus](data-mining/microsoft-clustering-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Cluster-Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Tastatur  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein Miningmodell aus der aktuellen Miningstruktur aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie einen Viewer aus, mit dem das ausgewählte Miningmodell angezeigt werden soll. Sie können den benutzerdefinierten Viewer für das Miningmodell oder den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Viewer für Mininginhalte verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Legende anzeigen**  
 Wählen Sie diese Option zum Anzeigen eines Schlüssels aus, der die Zuordnung von Farben im Viewer zu Werten in der Spalte **Status** anzeigt.  
  
 **Histogrammbalken**  
 Ändern Sie diesen Wert, um zu steuern, wie viele Status in jedem Histogramm eingeschlossen werden. Wenn mehr Status vorhanden sind, als Sie für die Anzeige ausgewählt haben, werden die Status mit der höchsten Wahrscheinlichkeit im Histogramm angezeigt, und die restlichen Status werden unter **Sonstige**gruppiert.  
  
 **Attribute**  
 Listet die Spalten im Clusteringmodell auf. Die Histogramme für jedes Attribut zeigen an, wie das Attribut in den vom Algorithmus identifizierten Clustern verteilt ist.  
  
 **Status**  
 Stellt einen Schlüssel bereit, der angibt, durch welche Farben die einzelnen Status in der entsprechenden Clusterreihe dargestellt werden, oder einen Schieberegler mit einer Raute, mit dem die Verteilung von kontinuierlichen numerischen Werten angegeben wird. Sie können diese Spalte mit dem Kontrollkästchen **Legende anzeigen** ein- und ausblenden.  
  
 **Clusterprofile**  
 Dieser Abschnitt enthält eine Spalte für jeden Cluster im Modell. Für jedes Attribut wird im Histogramm die Verteilung der Werte im Attribut nur für diesen Cluster angezeigt. Das Diagramm enthält auch eine Spalte für **Auffüllung**, bei der ebenfalls mit Histogrammen die Verteilung der Werte für jedes Attribut angezeigt wird, dies jedoch für alle Fälle im Modell.  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Datamining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
