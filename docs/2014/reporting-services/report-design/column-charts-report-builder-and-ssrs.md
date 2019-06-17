---
title: Säulendiagramme (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae8c138b-e356-4ad8-862c-a4a8d0c04149
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e8477b4e8e0e6c0fc6e4801a975b11d79dadf83f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106231"
---
# <a name="column-charts-report-builder-and-ssrs"></a>Säulendiagramme (Berichts-Generator und SSRS)
  Ein Säulendiagramm zeigt eine Reihe als Satz vertikaler Balken an, die nach Kategorie gruppiert sind. Säulendiagramme sind nützlich, um Datenänderungen über einen bestimmten Zeitraum anzuzeigen oder Vergleiche zwischen Elementen zu veranschaulichen. Das einfache Säulendiagramm ist eng mit dem Balkendiagramm und dem Säulenbereichsdiagramm verbunden. Das Balkendiagramm zeigt Reihen als Sätze horizontaler Balken an, während das Bereichssäulendiagramm Reihen als Sätze vertikaler Balken mit verschiedenen Anfangs- und Endpunkten darstellt. Weitere Informationen finden Sie unter [Balkendiagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md) und [Bereichsdiagramme &#40;Berichts-Generator und SSRS&#41;](range-charts-report-builder-and-ssrs.md).  
  
 Das Säulendiagramm ist für diese Daten ausgezeichnet geeignet, da alle drei Reihen einen gemeinsamen Zeitraum verwenden und so zuverlässige Vergleiche vorgenommen werden können.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations-of-a-column-chart"></a>Variationen eines Säulendiagramms  
  
-   **Gestapelt**. Ein Säulendiagramm, in dem mehrere Reihen vertikal gestapelt werden. Wenn nur eine Reihe im Diagramm vorhanden ist, wird das gestapelte Säulendiagramm angezeigt wie ein Säulendiagramm.  
  
-   **Prozentual gestapelt**. Ein Säulendiagramm, in dem mehrere Reihen vertikal gestapelt sind, um auf 100 % der Diagrammfläche zu passen. Wenn nur eine Reihe im Diagramm vorhanden ist, werden alle Säulenbalken so angepasst, dass sie 100 % der Diagrammfläche ausfüllen.  
  
-   **3D gruppiert**. Ein Säulendiagramm, das in einem 3D-Diagramm einzelne Reihen in separaten Zeilen anzeigt.  
  
-   **3D-Zylinder**. Ein Säulendiagramm, dessen Balken wie Zylinder in einem 3D-Diagramm gestaltet sind.  
  
-   `Histogram`. installiert haben. Ein Säulendiagramm, das das Diagramm berechnet, damit seine Balken in einer Normalverteilung angeordnet werden.  
  
-   `Pareto`. installiert haben. Ein Säulendiagramm, dessen Balken von der höchsten zur niedrigsten Instanz angeordnet werden.  
  
## <a name="data-considerations-for-a-column-chart"></a>Überlegungen zu Daten für ein Säulendiagramm  
  
-   Balken- und Säulendiagramme werden häufig verwendet, um Vergleiche zwischen Gruppen anzuzeigen. Wenn mehr als drei Reihen im Diagramm vorhanden sind, bietet sich eher ein gestapeltes Balken- oder Säulendiagramm an. Außerdem können Sie gestapelte Balken- oder Säulendiagramme in mehrere Gruppen zusammenfassen, wenn mehrere Reihen im Diagramm vorhanden sind. Weitere Informationen finden Sie unter [Balkendiagrammen &#40;Berichts-Generator und SSRS&#41; ](charts-report-builder-and-ssrs.md) und *Säulendiagramme*.  
  
-   In einem Säulendiagramm haben Sie weniger Platz, um Kategorieachsenbezeichnungen horizontal anzuzeigen. Bei längeren Kategoriebezeichnungen sollten Sie erwägen, ein Balkendiagramm zu verwenden oder den Drehwinkel für die Bezeichnung zu ändern.  
  
-   Sie können den einzelnen Balken eines Säulendiagramms besondere Zeichnungsarten hinzufügen, um die visuelle Wirkung zu erhöhen. Zeichnungsarten schließen Keil, Prägen, Zylinder und Helligkeitsabstufungen ein. Diese Effekte sollen die Darstellung des 2D-Diagramms verbessern. Bei Verwendung eines 3D-Diagramms werden die Zeichnungsarten zwar ebenfalls übernommen, sie haben jedoch möglicherweise nicht den gleichen Effekt. Weitere Informationen zum Hinzufügen einer Zeichnungsart zu einem Diagramm finden Sie unter [Hinzufügen einer Abschrägung, Prägung und Struktur zu einem Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).  
  
-   Säulendiagramme besitzen die einzigartige Fähigkeit, ein Diagramm als Histogramm oder Paretodiagramm anzuzeigen. Zu diesem Zweck legen Sie die ShowColumnAs-Eigenschaft auf `Histogram` oder `Pareto` im Fenster Eigenschaften in `true`.  
  
## <a name="see-also"></a>Siehe auch  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [Balkendiagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Bereichsdiagramme &#40;Berichts-Generator und SSRS&#41;](range-charts-report-builder-and-ssrs.md)   
 [Tutorial: Hinzufügen eines Balkendiagramms zu einem Bericht (Berichts-Generator)](../tutorial-add-a-bar-chart-to-your-report-report-builder.md)   
 [Leere und NULL-Datenpunkte in Diagrammen &#40;Berichts-Generator und SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
