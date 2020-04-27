---
title: Zusammenfassen von kleinen Slices in einem Kreisdiagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 517f5c5dddd809ee71037a95d04109a005968132
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106223"
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a>Zusammenfassen von kleinen Slices in einem Kreisdiagramm (Berichts-Generator und SSRS)
  Wenn Kreisdiagramme zu viele Datenpunkte enthalten, werden sie unübersichtlich. Zur Vermeidung dieses Problems können Sie alle Daten, die unter einen bestimmten Wert fallen, im Kreisdiagramm als einen gemeinsamen Slice anzeigen.  
  
 Wenn Sie kleinere Slices zu einem einzelnen Slice zusammenfassen möchten, müssen Sie zuerst entscheiden, ob der Schwellenwert für das Zusammenfassen kleiner Slices als Prozentanteil des Kreisdiagramms oder als fester Wert gemessen werden soll. Legen Sie dann die Eigenschaften CollectedThreshold und CollectedThresholdUsePercent fest. Legen Sie die Eigenschaft CollectedThreshold entweder auf den Prozentanteil des Diagramms, unter den die Werte fallen müssen, damit sie zusammengefasst werden, oder auf den tatsächlichen Schwellendatenwert für die Zusammenfassung fest. Legen Sie die Eigenschaft collectedationsolduse% `True` auf fest, um einen `False` Prozentsatz oder einen tatsächlichen Wert zu verwenden.  
  
 Sie können kleinere Slices auch zu einem zweiten Kreisdiagramm zusammenfassen, das aus einem zusammengefassten Slice des ersten Kreisdiagramms gebildet wird. Das zweite Kreisdiagramm wird rechts vom ursprünglichen Kreisdiagramm dargestellt.  
  
 Slices von Trichter- oder Pyramidendiagrammen können nicht zu einem Slice zusammengefasst werden.  
  
 Ein Beispiel für dieses Diagramm ist als Beispielbericht verfügbar. Weitere Informationen zum Herunterladen des Beispielberichts und anderer Berichte finden Sie unter [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Beispielberichte zu Berichts-Generator und Berichts-Designer](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
### <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a>So fassen Sie kleinere Slices zu einem einzelnen Slice in einem Kreisdiagramm zusammen  
  
1.  Öffnen Sie den Bereich Eigenschaften.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf ein Segment des Kreisdiagramms. Die Eigenschaften für die Reihe werden im Bereich "Eigenschaften" angezeigt.  
  
3.  Erweitern Sie im Abschnitt **Allgemein** den Knoten **CustomAttributes** .  
  
4.  Legen Sie die Eigenschaft CollectedStyle auf **SingleSlice**fest.  
  
5.  Legen Sie den Schwellenwert für die Zusammenfassung und den Typ des Schwellenwerts fest. Die folgenden Beispiele zeigen häufig verwendete Methoden zum Festlegen der Schwellenwerte für die Zusammenfassung.  
  
    -   **Nach Prozentanteil.** So fassen Sie beispielsweise in einem Kreisdiagramm Slices zusammen, die weniger als 10 % darstellen:  
  
         Legen Sie die Eigenschaft collectedfür olduse% `True`auf fest.  
  
         Legen Sie die Eigenschaft CollectedThreshold auf **10**fest.  
  
        > [!NOTE]  
        >  Wenn Sie CollectedStyle auf **SingleSlice**, CollectedThreshold auf einen Wert größer als **100**und collectedagraolduseprozent auf festlegen `True`, löst das Diagramm eine Ausnahme aus, da es keinen Prozentsatz berechnen kann. Zur Behebung dieses Problems legen Sie CollectedThreshold auf einen Wert kleiner als **100** fest.  
  
    -   **Nach Datenwert.** So fassen Sie beispielsweise in einem Kreisdiagramm Slices zusammen, die weniger als 5000 darstellen:  
  
         Legen Sie die Eigenschaft collectedfür olduse% `False`auf fest.  
  
         Legen Sie die Eigenschaft CollectedThreshold auf **5000**fest.  
  
6.  Legen Sie die Eigenschaft CollectedLabel auf eine Zeichenfolge fest, die als Beschriftung für das zusammengefasste Segment angezeigt werden soll.  
  
7.  (Optional) Legen Sie die Eigenschaften CollectedSliceExploded, CollectedColor, CollectedLegendText und CollectedToolTip fest. Diese Eigenschaften ändern die Darstellung, die Farbe, den Bezeichnungstext, den Legendentext und die QuickInfo des zusammengefassten Slice.  
  
### <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a>So fassen Sie kleinere Slices zu einem sekundären Legendenkreisdiagramm zusammen  
  
1.  Führen Sie die Schritte 1-3 von oben aus.  
  
2.  Legen Sie die Eigenschaft CollectedStyle auf **CollectedPie**fest.  
  
3.  Legen Sie die Eigenschaft CollectedThresholdproperty auf den Wert fest, der als Schwellenwert für die Zusammenfassung kleinerer Segmente zu einem einzelnen Segment verwendet werden soll. Wenn die Eigenschaft CollectedStyle auf **CollectedPie**festgelegt ist, wird die Eigenschaft CollectedThreshold olduse%immer auf `True`festgelegt, und der erfasste Schwellenwert wird immer in Prozent gemessen.  
  
4.  (Optional) Legen Sie die Eigenschaften CollectedColor, CollectedLabel, CollectedLegendText und CollectedToolTip fest. Alle anderen Eigenschaften mit der Bezeichnung "Collected" gelten nicht für den zusammengefassten Slice in einem Kreisdiagramm.  
  
> [!NOTE]  
>  Das sekundäre Kreisdiagramm wird auf der Grundlage der kleinen Slices in Ihren Daten berechnet, sodass es nur in der Vorschau angezeigt wird. Es wird nicht auf der Entwurfsoberfläche angezeigt.  
  
> [!NOTE]  
>  Sie können das sekundäre Kreisdiagramm nicht formatieren. Aus diesem Grund wird dringend empfohlen, beim Zusammenfassen von Slices in einem Kreisdiagramm die erste Methode zu verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kreis Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Anzeigen von Datenpunkt Bezeichnungen außerhalb eines Kreis Diagramms &#40;Berichts-Generator und SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Anzeigen von Prozentwerten in einem Kreis Diagramm &#40;Berichts-Generator und SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)   
 [Hinzufügen von 3D-Effekten zu einem Diagramm (Berichts-Generator und SSRS)](chart-effects-add-3d-effects-report-builder.md)  
  
  
