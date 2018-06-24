---
title: Punktdiagramme (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2520ae24-0609-4890-807d-3267018aba8e
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: d15dd1e13a7f855b897a0eebdfb8b0225da07cf3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048667"
---
# <a name="scatter-charts-report-builder-and-ssrs"></a>Punktdiagramme (Berichts-Generator und SSRS)
  Ein Punktdiagramm zeigt eine Reihe als Menge von Punkten an. Die Werte werden durch die Position der Punkte im Diagramm dargestellt. Kategorien werden durch verschiedene Marker im Diagramm dargestellt. Punktdiagramme dienen im Allgemeinen zum Vergleich aggregierter Daten über Kategorien hinweg. Weitere Informationen zum Hinzufügen von Daten zu einem Punktdiagramm finden Sie unter [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
 Die folgende Abbildung zeigt ein Beispiel für ein Punktdiagramm.  
  
 ![Punktdiagramm](../media/rs-scatterchart.gif "Scatter chart")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Variationen  
  
-   **Blase.** Blasendiagramme zeigen den Unterschied zwischen zwei Werten eines Datenpunkts basierend auf der Größe der Blase an. Je größer die Blase, desto größer der Unterschied zwischen den beiden Werten.  
  
-   **3D-Blase**. Ein dreidimensionales Blasendiagramm.  
  
## <a name="data-considerations-for-a-scatter-chart"></a>Überlegungen zu Daten für ein Punktdiagramm  
  
-   Punktdiagramme werden im Allgemeinen zum Anzeigen und Vergleichen numerischer Werte, wie wissenschaftliche, statistische und technische Daten, verwendet.  
  
-   Verwenden Sie das Punktdiagramm, wenn Sie große Mengen von Datenpunkten ohne Berücksichtigung des Zeitfaktors vergleichen möchten. Je mehr Daten Sie in ein Punktdiagramm integrieren, desto besser ist die Qualität der Vergleiche.  
  
-   Das Blasendiagramm erfordert zwei Werte (oben und unten) pro Datenpunkt.  
  
-   Punktdiagramme eignen sich ideal für die Verteilung von Werten und Clustern von Datenpunkten. Dies ist der am besten geeignete Diagrammtyp, wenn das Dataset viele Punkte (z. B. mehrere tausend Punkte) enthält. Die Anzeige mehrerer Reihen in einem Punktdiagramm lenkt visuell ab und sollte vermieden werden. Erwägen Sie in einem solchen Fall, ein Liniendiagramm zu verwenden.  
  
-   Standardmäßig zeigen Punktdiagramme Datenpunkte als Kreise an. Wenn mehrere Reihen in einem Punktdiagramm vorhanden sind, ändern Sie die Form des Markers für jeden Punkt gegebenenfalls in quadratisch, dreieckig, rautenförmig oder eine andere Form.  
  
## <a name="see-also"></a>Siehe auch  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Liniendiagramme &#40;Berichts-Generator und SSRS&#41;](line-charts-report-builder-and-ssrs.md)  
  
  