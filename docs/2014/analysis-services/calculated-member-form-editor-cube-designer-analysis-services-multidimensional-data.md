---
title: Formular-Editor für berechnete Elemente (Registerkarte ' Berechnungen ', Cube-Designer) (Analysis Services-Multidimensional Data) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationexpression.calculatedmember.f1
ms.assetid: f7719b9e-b1e6-4792-90a6-30d9d8eb1196
author: minewiskan
ms.author: owend
ms.openlocfilehash: 35c9ee36bf30b18859fa3ded540e607a48d0beb9
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527657"
---
# <a name="calculated-member-form-editor-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a>Formular-Editor für berechnete Elemente (Registerkarte 'Berechnungen', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Im Bereich des **Formular-Editors für berechnete Elemente** der Registerkarte **Berechnungen** können Sie im Cube-Designer ein berechnetes Element erstellen oder ändern.  
  
 **Hinweis** Dieser Bereich wird nur in der Formularansicht angezeigt.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen des berechneten Elements ein.  
  
 **Eigenschaften für übergeordnetes Element**  
 Erweitern Sie das Element, um die Optionen **Übergeordnete Hierarchie**, **Übergeordnetes Element**und **Ändern** anzuzeigen.  
  
 **Übergeordnete Hierarchie**  
 Wählen Sie die Dimension und die Hierarchie im ausgewählten Cube aus, die in das berechnete Element eingeschlossen werden sollen. Wählen Sie MEASURES aus, um ein berechnetes Element zu definieren.  
  
 **Übergeordnetes Element**  
 Wählen Sie das Element aus, unter dem das berechnete Element angeordnet werden soll.  
  
 **Hinweis** Diese Option ist verfügbar, wenn unter **Übergeordnete Hierarchie** eine andere Hierarchie als MEASURES angegeben ist.  
  
 **Änderung**  
 Wählen Sie diese Option aus, um das Dialogfeld **Übergeordnetes Element auswählen** anzuzeigen und ein Element unter **Übergeordnetes Element**auszuwählen. Weitere Informationen zum Dialogfeld **Übergeordnetes Element auswählen** finden Sie unter [Übergeordnetes Element auswählen &#40;Dialogfeld, Analysis Services – mehrdimensionale Daten&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md).  
  
 **expression**  
 Erweitern Sie das Element, um den MDX-Ausdruck (Multidimensional Expressions) für das berechnete Element anzuzeigen oder zu bearbeiten.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
> [!NOTE]  
>  Es wird empfohlen, diesen Ausdruck als Zeichenfolge oder numerischen Wert auszuwerten.  
  
 **Zusätzliche Eigenschaften**  
 Erweitern Sie das Element, um die Optionen **Formatzeichenfolge**, **Sichtbar**, **Verhalten für nicht leere Elemente**, **Farbausdrücke**und **Schriftartausdrücke** anzuzeigen.  
  
 **Formatzeichenfolge**  
 Geben Sie die MDX-Formatzeichenfolge ein, die zum Formatieren des vom berechneten Element zurückgegebenen Werts verwendet wird, oder wählen Sie eine vordefinierte Formatzeichenfolge aus.  
  
 Weitere Informationen zu MDX-Formatzeichenfolgen finden Sie unter [FORMAT_STRING – Inhalt &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md).  
  
 **Sichtbar**  
 Wählen Sie **TRUE** aus, um so das berechnete Element für Clientanwendungen sichtbar zu machen.  
  
 **Verhalten für nicht leere Elemente**  
 Wählen Sie den Namen des Measures aus, das in MDX zum Auflösen von NON EMPTY-Abfragen für das berechnete Element verwendet wird. Wenn die Eigenschaft **Verhalten für nicht leere Elemente** leer ist, muss das berechnete Element wiederholt ausgewertet werden, um zu ermitteln, ob ein Element leer ist. Wenn die Eigenschaft **Verhalten für nicht leere Elemente** den Namen eines Measures enthält, wird das berechnete Element so behandelt, als wäre das angegebene Measure leer.  
  
> [!WARNING]  
>  Diese Eigenschaft ist veraltet. Vermeiden Sie es, sie festzulegen. Weitere Informationen finden Sie [unter Veraltete Analysis Services Features in SQL Server 2014](deprecated-analysis-services-features-in-sql-server-2014.md) .  
  
 **Farb Ausdrücke**  
 Erweitern Sie dieses Element, um die Optionen **Vordergrundfarbe** und **Hintergrundfarbe** anzuzeigen.  
  
 **Vordergrundfarbe**  
 Geben Sie den MDX-Ausdruck ein, der die Vordergrundfarbe für das berechnete Element bereitstellt.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 Klicken Sie auf die Auswahlschaltfläche für die Farbe, um das Dialogfeld **Farbe** anzuzeigen, und fügen Sie den RGB-Wert (Rot, Grün, Blau) für eine angegebene Farbe in den MDX-Ausdruck ein. Weitere Informationen zu RGB-Werten finden Sie unter [FORE_COLOR und BACK_COLOR – Inhalte &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).  
  
 **Hintergrundfarbe**  
 Geben Sie den MDX-Ausdruck ein, der die Hintergrundfarbe für das berechnete Element bereitstellt.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 Klicken Sie auf die Auswahlschaltfläche für die Farbe, um das Dialogfeld **Farbe** anzuzeigen, und fügen Sie den RGB-Wert (Rot, Grün, Blau) für eine angegebene Farbe in den MDX-Ausdruck ein. Weitere Informationen zu RGB-Werten finden Sie unter [FORE_COLOR und BACK_COLOR – Inhalte &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).  
  
 **Schriftartausdrücke**  
 Erweitern Sie das Element, um die Optionen **Schriftartname**, **Schriftgrad**und **Schriftartflags** anzuzeigen.  
  
 **Schriftart Name**  
 Geben Sie den MDX-Ausdruck ein, der den Namen der Schriftart bereitstellt, der für das berechnete Element verwendet werden soll.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 Klicken Sie auf die Auswahlschaltfläche für Schriftarten, um das Dialogfeld **Schriftart** anzuzeigen, und fügen Sie die Eigenschaftswerte für eine angegebene Schriftart in den MDX-Ausdruck ein. Weitere Informationen zu Eigenschaftswerten finden Sie unter [Erstellen und Verwenden von Eigenschaftswerten &#40;MDX&#41;](creating-and-using-property-values-mdx.md).  
  
 **Schriftgrad**  
 Geben Sie den MDX-Ausdruck ein, der den Schriftgrad bereitstellt, der für das berechnete Element verwendet werden soll.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 Klicken Sie auf die Auswahlschaltfläche für Schriftarten, um das Dialogfeld **Schriftart** anzuzeigen, und fügen Sie die Eigenschaftswerte für eine angegebene Schriftart in den MDX-Ausdruck ein. Weitere Informationen zu Eigenschaftswerten finden Sie unter [Erstellen und Verwenden von Eigenschaftswerten &#40;MDX&#41;](creating-and-using-property-values-mdx.md).  
  
 **Schriftartflags**  
 Geben Sie den MDX-Ausdruck ein, der den Bitmapwert mit den Schriftartflags für die Schriftart enthält (z. B. Unterstrichen oder Fett), die für das berechnete Element verwendet werden soll.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 Klicken Sie auf die Auswahlschaltfläche für Schriftarten, um das Dialogfeld **Schriftart** anzuzeigen, und fügen Sie die Eigenschaftswerte für eine angegebene Schriftart in den MDX-Ausdruck ein. Weitere Informationen zu Eigenschaftswerten finden Sie unter [Erstellen und Verwenden von Eigenschaftswerten &#40;MDX&#41;](creating-and-using-property-values-mdx.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einbeziehen](multidimensional-models-olap-logical-cube-objects/calculations.md)   
 [Erstellen von berechneten Elementen](multidimensional-models/create-calculated-members.md)   
 [Cube-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Berechnungen &#40;Cube-Designer-&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte "Berechnungen", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Skript Planer &#40;Registerkarte "Berechnungen", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Berechnungs Tools &#40;Registerkarte "Berechnungen", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md)   
 [Formular-Editor für benannte Mengen &#40;Registerkarte "Berechnungen", Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Skript-Editor &#40;Registerkarte "Berechnungen", Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
