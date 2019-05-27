---
title: Hinzufügen einer Abschrägung, eines Reliefs und von Texturstilen zu einem Diagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b25d12646a2662cb5c6ab8f2a9b510aa02d7c49b
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66106283"
---
# <a name="add-bevel-emboss-and-texture-styles-to-a-chart-report-builder-and-ssrs"></a>Hinzufügen einer Abschrägung, Prägung und Struktur zu einem Diagramm (Berichts-Generator und SSRS)
  Bei bestimmten Diagrammtypen können Sie einen Zeichnungseffekt angeben, um die visuelle Wirkung des Diagramms zu erhöhen. Diese Zeichnungseffekte werden nur für die Reihen des Diagramms übernommen. Sie haben keine Auswirkungen auf andere Diagrammelemente.  
  
 Wenn Sie eine Variante eines Kreis- oder Ringdiagramms verwenden, können Sie einen weichen Rand oder eine konkave Zeichnungsart angeben ähnlich wie Abschrägungs- oder Prägungseffekte für ein Bild.  
  
 Bei Verwendung einer Variante eines Balken- oder Säulendiagramms können Sie Strukturarten wie Zylinder, Keil und Helligkeitsabstufungen auf einzelne Balken oder Säulen anwenden.  
  
 Zusätzlich zu diesen Zeichnungsarten können vielen Diagrammelementen Rahmen und Schatten hinzugefügt werden, um eine Illusion von Tiefe zu vermitteln. Weitere Informationen zu anderen Möglichkeiten, das Diagramm zu formatieren, finden Sie unter [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a>So fügen Sie Abschrägungs- und Prägungseffekte zu einem Kreis- oder Ringdiagramm hinzu  
  
1.  Wählen Sie auf der Registerkarte **Ansicht** die Option **Eigenschaften** aus, um den Eigenschaftenbereich zu öffnen.  
  
2.  Wählen Sie das Kreis- oder Ringdiagramm aus, das Sie optimieren möchten. Wählen Sie ein Datenfeld im Diagramm aus und nicht das gesamte Diagramm.  
  
3.  Erweitern Sie im Bereich Eigenschaften den Knoten **CustomAttributes** .  
  
4.  Wählen Sie für PieDrawingStyle eine Art aus der Dropdownliste aus.  
  
> [!NOTE]  
>  Sie können 3D nicht mit Abschrägungen oder Prägungen im selben Diagramm verwenden. Wenn Sie für das Diagramm 3D aktiviert haben, wird die PieDrawingStyle-Eigenschaft nicht angezeigt.  
  
 ![Kreisdiagramm mit konkaver Zeichnungsart](../media/rs-piedrawingeffects-concave.gif "Pie chart with concave drawing style")  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a>So fügen Sie einem Balken- oder Säulendiagramm Strukturarten hinzu  
  
1.  Wählen Sie das Balken- oder Säulendiagramm aus, das Sie optimieren möchten. Wählen Sie ein Datenfeld im Diagramm aus und nicht das gesamte Diagramm.  
  
2.  Öffnen Sie den Bereich Eigenschaften.  
  
3.  Erweitern Sie den Knoten **CustomAttributes** .  
  
4.  Wählen Sie für DrawingStyle eine Art aus der Dropdownliste aus.  
  
> [!NOTE]  
>  Sie können 3D nicht mit Abschrägungen oder Prägungen im selben Diagramm verwenden. Wenn Sie für das Diagramm 3D aktiviert haben, wird die PieDrawingStyle-Eigenschaft nicht angezeigt.  
  
 ![Balkendiagramm mit LightToDark-Zeichnungseffekt](../media/rs-bardrawingeffects-lighttodark.gif "Bar chart with LightToDark drawing effect")  
  
## <a name="see-also"></a>Siehe auch  
 [Balkendiagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Säulendiagramme (Berichts-Generator und SSRS)](column-charts-report-builder-and-ssrs.md)   
 [Kreisdiagramme &#40;Berichts-Generator und SSRS&#41;](pie-charts-report-builder-and-ssrs.md)   
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
