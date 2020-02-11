---
title: Registerkarte "Entscheidungsstruktur" (Mining Modell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.decisiontree.f1
ms.assetid: dc88606f-ba7c-4f8d-af65-bfa17ec16e2b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cee721aca66f5266a29d3bf61babf9060e9aef32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082299"
---
# <a name="decision-tree-tab-mining-model-viewer"></a>Registerkarte "Entscheidungsstruktur" (Miningmodell-Viewer)
  Im Bereich **Entscheidungsstruktur** wird eine visuelle Darstellung der Entscheidungsregeln angezeigt, die in einem Entscheidungsstrukturmodell erstellt werden. Entscheidungsregeln beschreiben Pfade zu einem bestimmten Ergebnis.  
  
 **Weitere Informationen finden** Sie unter [Microsoft Decision Trees-Algorithmus](data-mining/microsoft-decision-trees-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Tree Viewer](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md) .  
  
## <a name="options"></a>Tastatur  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Mining Modell**  
 Wählen Sie ein Miningmodell aus der aktuellen Miningstruktur aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer oder den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Viewer für Mininginhalte verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Vergrößern**  
 Vergrößern Sie die Ansicht, um eine detaillierte Sicht der Knoten und Verzweigungen in der Entscheidungsstruktur zu erhalten. In einem komplexen Modell können Entscheidungsstrukturen über viele Verzweigungsebenen verfügen.  
  
 **Verkleinern**  
 Verkleinern Sie die Ansicht, um einen Überblick über die Struktur zu erhalten.  
  
 **Diagrammsicht kopieren**  
 Kopiert den sichtbaren Abschnitt des Diagramms in die Zwischenablage.  
  
 **Gesamtes Diagramm kopieren**  
 Kopiert das gesamte Diagramm in die Zwischenablage.  
  
 **Diagramm an Fenstergröße anpassen**  
 Verkleinert das Diagramm so weit, dass die gesamte Baumstruktur auf den Bildschirm passt.  
  
 **Histogramme**  
 Wählen Sie aus, wie viele Status im Histogramm für jeden Knoten angezeigt werden können. Wenn die Anzahl der Status im Modell geringer als der ausgewählte Wert ist, werden keine zusätzlichen Balken angezeigt.  
  
 **Linde**  
 Wählen Sie die Struktur aus, die im Viewer angezeigt werden soll. Wenn Sie ein Modell erstellen, das über mehrere vorhersagbare Attribute verfügt, erstellt der Algorithmus eine separate Struktur für jedes vorhersagbare Attribut.  
  
 **Hintergrund**  
 Wählen Sie einen Wert des vorhersagbaren Attributs aus, der beim Darstellen der Hintergrundfarbe für die einzelnen Knoten verwendet werden soll. Wenn Sie beispielsweise in den AdventureWorks-Beispielmodellen **Hintergrund** auf 1 ([Bike Buyer] = Yes) festlegen, werden die Knoten dunkler schattiert, wenn sie über einen größeren Anteil von Fahrradkäufern verfügen. Diese Option stellt einen zusätzlichen visuellen Hinweis auf die Bedeutung der Verzweigungen und Knoten in der Struktur bereit.  
  
 **Standarderweiterung**  
 Wählen Sie einen Wert aus der Liste aus, um den Standardwert für die Anzahl der im Strukturdiagramm angezeigten Ebenen festzulegen.  
  
 **Ebene anzeigen**  
 Verschieben Sie den Schieberegler nach rechts oder links, um die Anzahl der Ebenen anzupassen, die im Strukturdiagramm angezeigt werden. Schieben Sie den Regler ganz nach rechts, um alle Knoten im Modell anzuzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
