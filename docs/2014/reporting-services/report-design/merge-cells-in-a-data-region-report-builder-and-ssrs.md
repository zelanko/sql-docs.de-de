---
title: Zusammenführen von Zellen in einem Datenbereich (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 97e9280512b75aebfccb93c0e11e5402136fa6f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105564"
---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a>Zusammenführen von Zellen in einem Datenbereich (Berichts-Generator und SSRS)
  Sie können Zellen in einem Datenbereich zusammenführen, um Zellen zu kombinieren, die Darstellung des Datenbereichs zu verbessern oder umfassende Bezeichnungen für Spaltengruppen und Zeilengruppen zur Verfügung zu stellen.  
  
> [!NOTE]  
>  Zellen können nur innerhalb der folgenden Bereiche eines Datenbereichs zusammengeführt werden: Ecke, Spaltenkopfzeilen, Gruppendefinition (oder Zeilenköpfe) und Textkörper. Sie können keine Zellen zusammenführen, die über Bereichsgrenzen hinausgehen. Sie können beispielsweise eine Zelle im Eckbereich des Datenbereichs nicht mit einer Zelle im Zeilengruppenbereich zusammenführen. Weitere Informationen zu Tablix--Bereichen finden Sie unter [Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-merge-cells-in-a-data-region"></a>So führen Sie Zellen in einem Datenbereich zusammen  
  
1.  Klicken Sie im Datenbereich auf der Berichtsentwurfsoberfläche auf die erste Zelle, die zusammengeführt werden soll. Drücken Sie die linke Maustaste, und ziehen Sie den Mauszeiger vertikal oder horizontal, um angrenzende Zellen auszuwählen. Die ausgewählten Zellen werden markiert.  
  
2.  Klicken Sie mit der rechten Maustaste auf die ausgewählten Zellen, und wählen Sie **Zellen zusammenführen**aus. Die ausgewählten Zellen werden zu einer einzigen Zelle kombiniert.  
  
3.  Wiederholen Sie die Schritte 1 und 2, um andere angrenzende Zellen in einem Datenbereich zusammenzuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
