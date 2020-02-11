---
title: Formdiagramme (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b8404c1-aa89-4350-8bd6-203bc0446ee4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7194147f60fa039caab1f9a712b9f6f75e2617d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104948"
---
# <a name="shape-charts-report-builder-and-ssrs"></a>Formdiagramme (Berichts-Generator und SSRS)
  Ein Formdiagramm zeigt Wertdaten als Prozentsatz des Ganzen an. Formdiagramme werden üblicherweise zum Anzeigen proportionaler Vergleiche zwischen verschiedenen Werten in einem Satz verwendet. Kategorien werden durch einzelne Segmente der Form dargestellt. Die Größe des Segments wird durch den Wert bestimmt. Formdiagramme werden ähnlich verwendet wie Kreisdiagramme, außer dass die Kategorien von der größten zur kleinsten angeordnet werden.  
  
 Ein Trichterdiagramm zeigt Werte als progressiv abnehmende Verhältnisse an. Die Größe eines Bereichs wird durch den Reihenwert als Prozentsatz der Summe aller Werte bestimmt. Beispielsweise lassen sich in einem Trichterdiagramm Websitebesuchertrends darstellen. Das Trichterdiagramm zeigt meist einen großen Bereich ganz oben an, der die Besuche der Startseite angibt. Die anderen Bereiche werden proportional kleiner. Weitere Informationen zu Hinzufügen von Daten zu einem Trichterdiagramm finden Sie unter [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
 Die folgende Abbildung zeigt ein Beispiel für ein Trichterdiagramm.  
  
 ![Trichterdiagramm](../media/rs-funnelchart.gif "Trichterdiagramm")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Abweichungen  
  
-   **Pyramide**. Ein Pyramidendiagramm zeigt proportionale Daten in Form einer Pyramide an.  
  
## <a name="data-considerations-for-shape-charts"></a>Überlegungen zu Daten für ein Formdiagramm  
  
-   Formdiagramme sind wegen ihrer visuellen Wirkung in Berichten beliebt. Bei Formdiagrammen handelt es sich jedoch um einen sehr vereinfachten Diagrammtyp, der Ihre Daten möglicherweise nicht optimal darstellt. Verwenden Sie ein Formdiagramm ggf. erst, nachdem die Daten zu sieben Datenpunkten oder weniger aggregiert wurden. Mit dem Formdiagramm sollte im Allgemeinen nur eine Kategorie pro Datenbereich angezeigt werden.  
  
-   Formdiagramme zeigen jede Datengruppe als separates Segment im Diagramm an. Sie müssen mindestens ein Datenfeld und ein Kategoriefeld hinzufügen. Wenn dem Formdiagramm mehr als ein Datenfeld hinzugefügt wird, werden beide Datenfelder im selben Diagramm angezeigt.  
  
-   Formdiagramme eignen sich sehr gut, um proportionale Prozentwerte in sortierter Reihenfolge anzuzeigen. Um die Konsistenz zu wahren, werden die Werte im Dataset jedoch standardmäßig nicht sortiert. Es bietet sich an, die Werte vom höchsten zum niedrigsten Wert zu sortieren, um die Daten möglichst exakt als Trichter oder Pyramide darzustellen. Weitere Informationen finden Sie unter [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
-   NULL-, leere und negative Werte haben keine Auswirkungen auf die Berechnung von Verhältnissen. Aus diesem Grund werden diese Werte nicht in einem Formdiagramm angezeigt. Wenn Sie diese Werte in Ihrem Diagramm visuell darstellen möchten, ändern Sie den Diagrammtyp. Weitere Informationen zum Hinzufügen von leeren Punkten zu einem nicht-Form Diagramm finden Sie unter [Hinzufügen von leeren Punkten zum Diagramm &#40;Berichts-Generator und SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).  
  
-   Wenn Sie mithilfe einer benutzerdefinierten Palette eigene Farben in einem Formdiagramm definieren, müssen in der Palette genügend Farben vorhanden sein, damit jeder Datenpunkt mit einer eigenen Farbe hervorgehoben werden kann. Weitere Informationen finden Sie unter [Formatieren von Reihenfarben in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md).  
  
-   Im Gegensatz zu allen anderen Diagrammtypen zeigt ein Formdiagramm einzelne Datenpunkte und keine einzelnen Reihen in der Legende an.  
  
-   Einstellungen für die Wert- und Kategorieachse werden bei Trichterdiagrammen ignoriert. Wenn mehrere Kategorien- oder Reihengruppen vorhanden sind, werden die Gruppenbezeichnungen in der Diagrammlegende angezeigt.  
  
-   Formdiagrammtypen können nicht mit anderen Diagrammtypen im gleichen Diagrammbereich kombiniert werden. Wenn Sie Vergleiche zwischen Daten in einem Formdiagramm und Daten in einem anderen Diagrammtyp anzeigen möchten, müssen Sie einen zweiten Diagrammbereich hinzufügen.  
  
-   Durch Hinzufügen von 3D-Effekten wird die Gesamtdarstellung eines Formdiagrammtyps erheblich verbessert.  
  
-   Sie können zusätzliche Zeichnungsarten für Kreis- und Ringdiagramme verwenden, um die visuelle Wirkung zu erhöhen. Weitere Informationen finden Sie unter [Formatieren von Reihenfarben in einem Diagramm (Berichts-Generator und SSRS)](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Leere und NULL-Datenpunkte in Diagrammen (Berichts-Generator und SSRS)](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Kreisdiagramme &#40;Berichts-Generator und SSRS&#41;](pie-charts-report-builder-and-ssrs.md)  
  
  
