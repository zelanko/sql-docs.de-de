---
title: Registerkarte "Abhängigkeits Netzwerk" (Mining Modell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.dependencynetwork.f1
ms.assetid: e58ce1b7-20d6-42cb-ade5-916da8471e09
author: minewiskan
ms.author: owend
ms.openlocfilehash: dde94a8d08bba3ea529c9edf3fde12ee0260a3f0
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528736"
---
# <a name="dependency-network-tab-mining-model-viewer"></a>Registerkarte "Abhängigkeitsnetzwerk" (Miningmodell-Viewer)
  Die Registerkarte **Abhängigkeitsnetzwerk** bietet eine grafische Sicht aller im Miningmodell enthaltenen Attribute und gibt die Beziehungen zwischen den Attributen an.  
  
 Die Registerkarte **Abhängigkeitsnetzwerk**  wird für mehrere Typen von Miningmodellen verwendet, darunter Naive Bayes-Modelle, Entscheidungsstrukturmodelle und Zuordnungsmodelle. Weitere Informationen zum Interpretieren des Inhalts der Registerkarte **Abhängigkeitsnetzwerk**  im Kontext dieser Modelle finden Sie unter den folgenden Links:  
  
 [Durchsuchen eines Modells mit dem Microsoft Struktur-Viewer](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
 [Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
 [Modell mit dem Microsoft-Viewer für Zuordnungsregeln durchsuchen](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Mining Modell**  
 Wählen Sie ein anzuzeigendes Miningmodell aus der aktuellen Miningstruktur aus. Das Miningmodell wird in einem benutzerdefinierten Viewer geöffnet. Der jeweils für ein Modell verwendete Typ von benutzerdefiniertem Viewer wird durch den Algorithmus bestimmt, mit dem Sie das Modell erstellt haben.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Für jedes Modell können Sie den benutzerdefinierten Viewer verwenden, der für das betreffende Miningmodell bereitgestellt wird, oder aber den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Viewer für Mininginhalte. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind. Der Microsoft Generic Content Tree Viewer kann mit allen Modellen verwendet werden, wobei der Modellinhalt in einer HTML-Tabelle dargestellt wird.  
  
 **Vergrößern**  
 Vergrößern Sie die Ansicht des Diagramms, damit Sie die Attribute detaillierter einsehen können.  
  
 **Verkleinern**  
 Verkleinern Sie das Diagramm, damit Sie mehr Attribute und die Links zwischen diesen einsehen können.  
  
 **Diagrammsicht kopieren**  
 Kopiert den sichtbaren Abschnitt des Diagramms in die Zwischenablage.  
  
 **Gesamtes Diagramm kopieren**  
 Kopiert das gesamte Diagramm in die Zwischenablage.  
  
 **Links**  
 Passt die Anzahl der im Viewer angezeigten Links (Ränder) und Knoten an, indem der Schieberegler rechts neben den Attributen verschoben wird. Durch Ziehen des Schiebereglers nach unten wird der Schwellenwert erhöht, sodass nur die stärksten Links angezeigt werden. Bei jedem Modelltyp wird ein etwas anderer Wert verwendet, um die Links im Diagramm darzustellen:  
  
-   In einem **Entscheidungsstrukturmodell** stellen die Ränder die prognostizierte Stärke der Verbindung dar, die teilweise vom Teilungsergebnis abhängt.  
  
-   In einem **Naive Bayes-Modell** können die Links zwischen zwei Knoten in beide Richtungen verlaufen: Knoten A kann Knoten B vorhersagen und umgekehrt. Das dem Rand zugeordnete Ergebnis stellt die prognostizierte Stärke der Verbindung dar.  
  
-   In einem **Zuordnungsmodell**stellen die Ränder zwischen Knoten das Wichtigkeitsergebnis der Regel dar, die zwei Itemsets verbindet.  
  
 Allgemeine gilt für alle Modelltypen: je stärker der Link, desto stärker ist auch die prognostizierte Beziehung zwischen den beiden Attributen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
