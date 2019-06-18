---
title: Zusammenführen von Zellen in einem Datenbereich (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1c0f695bc5c7cb6d68935d23e918f19c1408d475
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65570787"
---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a>Zusammenführen von Zellen in einem Datenbereich (Berichts-Generator und SSRS)
In einem paginierten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bericht können Sie Zellen in einem Datenbereich zusammenführen, um Zellen zu kombinieren, die Darstellung des Datenbereichs zu verbessern oder umfassende Bezeichnungen für Spalten- und Zeilengruppen zur Verfügung zu stellen.  
  
Zellen können nur innerhalb der folgenden Bereiche eines Datenbereichs zusammengeführt werden: Ecke, Spaltenheader, Gruppendefinition (oder Zeilenheader) und Textkörper. Sie können keine Zellen zusammenführen, die über Bereichsgrenzen hinausgehen. Sie können beispielsweise eine Zelle im Eckbereich des Datenbereichs nicht mit einer Zelle im Zeilengruppenbereich zusammenführen. Erfahren Sie mehr unter [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-merge-cells-in-a-data-region"></a>So führen Sie Zellen in einem Datenbereich zusammen  
  
1.  Klicken Sie im Datenbereich auf der Berichtsentwurfsoberfläche auf die erste Zelle, die zusammengeführt werden soll. Drücken Sie die linke Maustaste, und ziehen Sie den Mauszeiger vertikal oder horizontal, um angrenzende Zellen auszuwählen. Die ausgewählten Zellen werden markiert.  
  
2.  Klicken Sie mit der rechten Maustaste auf die ausgewählten Zellen, und wählen Sie **Zellen zusammenführen**aus. Die ausgewählten Zellen werden zu einer einzigen Zelle kombiniert.  
  
3.  Wiederholen Sie die Schritte 1 und 2, um andere angrenzende Zellen in einem Datenbereich zusammenzuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Tablix-Datenbereich](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)  
 [Tabellen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Erstellen einer Matrix (Berichts-Generator und SSRS)](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Erstellen von Rechnungen und Formulare mit Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
[Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
