---
title: Kursdiagramme (Berichts-Generator) | Microsoft-Dokumentation
description: Zeigen Sie im Berichts-Generator Finanzdaten oder wissenschaftliche Daten mit bis zu vier Werten pro Datenpunkt an mithilfe von Markern wie Linien oder Dreiecken.
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: f75ca11e-b7f5-4ac0-ba17-fe6f82742dad
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 40a9ab1568ab2b61a1582f3dfbc62badbd480a1f
ms.sourcegitcommit: f898aa83561e94626024916932568ab05e73b656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2020
ms.locfileid: "84012428"
---
# <a name="stock-charts-report-builder-and-ssrs"></a>Kursdiagramme (Berichts-Generator und SSRS)

  Ein Kursdiagramm ist speziell für Finanz- oder wissenschaftliche Daten ausgelegt, bei denen bis zu vier Werte pro Datenpunkt verwendet werden. Diese Werte werden an den Hoch-, Tief-, Anfangs- und Schlusswerten ausgerichtet, die zur Aufzeichnung von Finanzkursdaten verwendet werden. Dieser Diagrammtyp zeigt Anfangs- und Schlusswerte mit Markern, normalerweise Zeilen oder Dreiecke, an. Im folgenden Beispiel werden die Anfangswerte durch Marker auf der linken Seite angezeigt, und die Schlusswerte werden durch Marker auf der rechten Seite dargestellt.  
  
 ![Kursdiagramm](../../reporting-services/report-design/media/rs-stockchart.gif "Kursdiagramm")  
  
 Ein Beispiel eines Kursdiagramms ist als Berichts-Generator-Beispielbericht verfügbar. Weitere Informationen zum Herunterladen des Beispielberichts und anderer Berichte finden Sie unter [Beispielberichte zu Berichts-Generator und Berichts-Designer](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Abweichungen  
  
-   **Kerze**. Das Kerzendiagramm ist eine spezielle Form des Kursdiagramms, in dem mithilfe von Kästchen der Unterschied zwischen Anfangs- und Schlusswerten angezeigt wird. Wie das Kursdiagramm kann das Kerzendiagramm bis zu vier Werte pro Datenpunkt anzeigen.  
  
## <a name="data-considerations-for-stock-charts"></a>Überlegungen zu Daten für ein Kursdiagramm  
  
-   Bei der Darstellung vieler Kursdatenpunkte, wie bei einem Jahresaktienkurs, ist es schwierig, die einzelnen Anfangs-, Schluss-, Hoch- und Tiefwerte jedes Datenpunkts zu unterscheiden. Erwägen Sie in diesem Fall, ein Liniendiagramm anstelle eines Kursdiagramms zu verwenden.  
  
-   Wenn Achsenbezeichnungen generiert werden, fängt die Kennzeichnung normalerweise auf dem Nullpunkt an.  Im Allgemeinen fluktuieren Aktienkurse nicht so stark wie anderen Datasets. Deshalb ist es eventuell sinnvoll, den Beginn der Achsenbezeichnungen auf dem Nullpunkt zu deaktivieren, um eine bessere Übersicht über Ihre Daten zu erhalten. Legen sie hierzu im Dialogfeld **Achseneigenschaften** oder im Fenster **Eigenschaften** die Option **IncludeZero** auf false fest. Weitere Informationen zum Generieren von Achsenbezeichnungen in einem Diagramm finden Sie unter [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet viele berechnete Zellen zur Verwendung mit Kursdiagrammen, wie "Price Indicator", "Relative Strength Index", "MACD" usw.  

## <a name="next-steps"></a>Nächste Schritte

[Bereichsdiagramme](../../reporting-services/report-design/range-charts-report-builder-and-ssrs.md)   
[Diagramme](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[Formatieren eines Diagramms](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
[Achseneigenschaften (Dialogfeld), Achsenoptionen](https://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
