---
title: Definieren von Farben in einem Diagramm mit einer Palette (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4cae758708ce0ac703aa2b6e82b574b45c54195a
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65572273"
---
# <a name="define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs"></a>Definieren von Farben in einem Diagramm mit einer Palette (Berichts-Generator und SSRS)
  Sie können die Farbpalette für ein Diagramm durch Auswählen einer vordefinierten Palette oder durch Definieren einer benutzerdefinierten Palette ändern. Benutzerdefinierte Paletten sind diagrammspezifisch.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-colors-on-the-chart-using-a-built-in-color-palette"></a>So ändern Sie die Farben im Diagramm mit einer integrierten Farbpalette  
  
1.  Öffnen Sie den Bereich Eigenschaften.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf das Diagramm. Die Eigenschaften für das Diagrammobjekt werden im Bereich Eigenschaften angezeigt.  
  
     Der Objektname (standardmäßig**Chart1** ) wird in der Dropdownliste oben im Bereich „Eigenschaften“ aufgeführt.  
  
3.  Wählen Sie im Abschnitt **Diagramm** für die „Palette“-Eigenschaft eine neue Palette aus der Dropdownliste aus.  
  
    > [!NOTE]  
    >  Sie können die Farben oder die Reihenfolge in einer vordefinierten Palette nicht ändern.  
  
### <a name="to-define-your-own-colors-on-the-chart-using-a-custom-color-palette"></a>So definieren Sie eigene Farben im Diagramm mit einer benutzerdefinierten Farbpalette  
  
1.  Öffnen Sie den Bereich Eigenschaften.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf das Diagramm. Die Eigenschaften für das Diagrammobjekt werden im Bereich Eigenschaften angezeigt.  
  
3.  Wählen Sie im Abschnitt **Diagramm** für die Eigenschaft **Palette** die Option **Benutzerdefiniert**aus.  
  
4.  Klicken Sie in der CustomPaletteColors-Eigenschaft auf die Schaltfläche zum Bearbeiten der Collection (**…**). Das Dialogfeld **ReportColorExpression-Auflistungs-Editor** wird geöffnet.  
  
5.  Klicken Sie auf **Hinzufügen** , um eine Farbe hinzuzufügen. Wählen Sie in der Dropdownliste eine Farbe aus, oder wählen Sie Ausdruck, und geben Sie einen hexadezimalen Wert für eine bestimmte Farbe an, z. B. ff6600 für "Orange".  
  
     Weitere Informationen zu Hexadezimalwerten finden Sie unter [Color Table](https://go.microsoft.com/fwlink/?linkid=9258) auf MSDN.  
  
6.  Klicken Sie auf **Hinzufügen** , um der Palette weitere Farben hinzuzufügen.  
  
7.  Abschließend klicken Sie auf **OK**.  
  
 Wenn Sie eine benutzerdefinierte Palette verwenden, können Sie die Reihenfolge der Farben ändern, um die Farbe verschiedener Reihen im Diagramm zu ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Reihenfarben in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Angeben von Farben, die für mehrere Formdiagramme konsistent sind &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
  
