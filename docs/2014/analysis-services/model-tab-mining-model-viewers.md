---
title: Registerkarte "Modell" (Mining Modell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.timeseries.decisiontree.f1
ms.assetid: 50570bb4-fcac-411e-b530-0398437efda7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42285f94057441d01259c5fd54ce896dd0316b94
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84537362"
---
# <a name="model-tab-mining-model-viewers"></a>Registerkarte "Modell" (Miningmodell-Viewer)
  Auf der Registerkarte **Modell** im Microsoft Time Series-Viewer wird eine Darstellung einer Zeitreihe als Knoten in einem Diagramm angezeigt, ähnlich wie in Entscheidungsstrukturmodellen.  
  
 Mit dieser Sicht eines Zeitreihenmodells können Sie nützliche Informationen zur Zeitreihenanalyse extrahieren, u. a. die Gleichung für den Graph, die ARIMA-Terme und die Koeffizienten.  
  
 **Weitere Informationen:** [Microsoft Time Series-Algorithmus](data-mining/microsoft-time-series-algorithm.md), [Durchsuchen eines Modells mit Microsoft Time Series-Viewer](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md), [Microsoft Time Series-Algorithmus](data-mining/microsoft-time-series-algorithm.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Mining Modell**  
 Wählen Sie ein Miningmodell zur Ansicht aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer für diesen Modelltyp oder den **Microsoft Generic Content Tree Viewer** verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Vergrößern**  
 Vergrößert das Diagramm.  
  
 **Verkleinern**  
 Verkleinert das Diagramm.  
  
 **Diagrammsicht kopieren**  
 Kopiert den sichtbaren Abschnitt des Diagramms in die Zwischenablage.  
  
 **Gesamtes Diagramm kopieren**  
 Kopiert das gesamte Diagramm in die Zwischenablage.  
  
 **Diagramm an Fenstergröße anpassen**  
 Verkleinert das Diagramm so weit, dass das gesamte Diagramm auf den Bildschirm passt.  
  
 **Linde**  
 Wählen Sie eine Struktur aus der Dropdownliste aus, die im Viewer angezeigt werden soll.  
  
 Wenn das Zeitreihenmodell mehrere Reihen umfasst, wird jede Reihe als separate Struktur dargestellt. Wenn Sie z. B. für [Menge] und [Umsatz] Vorhersagen über einen Zeitraum erstellt haben, wird eine separate Reihe für jedes vorhersagbare Attribut erstellt.  
  
 Die Länge der Farbhervorhebung in der Liste gibt die Anzahl von Ebenen in der Struktur an. Das bedeutet, dass bei einem Zeitreihenmodell, das von einem einzelnen Knoten dargestellt werden kann, der Trend von einer einzelnen Gleichung beschrieben würde und der farbige Balken sehr kurz wäre. (Wenn das Modell ein MIXED-Modell ist, enthält der Knoten natürlich sowohl eine ARIMA- als auch eine ARTXP-Gleichung.)  
  
 Wenn die in der Dropdownliste angezeigte Struktur über einen längeren farbigen Balken verfügt, bedeutet dies, dass das Modell viele Verzweigungen in der Struktur aufweist. Verzweigungen bedeuten, dass die Regression komplexer ist und das Modell in mehrere Segmente aufgegliedert werden muss, wobei jeder Knoten eine andere Gleichung (oder ein Paar von Gleichungen) enthält.  
  
 **Hintergrund**  
 Wählen Sie mit diesem Steuerelement den Status aus, der von der Hintergrundfarbe in jedem Knoten dargestellt wird.  
  
 **Standard Erweiterung**  
 Damit passen Sie die standardmäßige Anzahl der Ebenen an, die für alle im Modell vorhandenen Strukturen angezeigt werden.  
  
 **Ebene anzeigen**  
 Damit ändern Sie die Anzahl der Ebenen, die in der Struktur angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
