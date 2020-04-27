---
title: Formatieren von Text in einem Textfeld (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df0794b5-96b0-4034-bd17-1be7f31e29db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 976130697e759fa4231ad73113d0970e345dbb3a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105867"
---
# <a name="format-text-in-a-text-box-report-builder-and-ssrs"></a>Formatieren von Text in einem Textfeld (Berichts-Generator und SSRS)
  Sie können beliebige Teile des Texts in einem Textfeld unabhängig voneinander formatieren und Platzhaltertext und statischen Text in einem Textfeld mischen. Durch das Mischen von Formaten und Hinzufügen von Platzhaltertext können Sie im Bericht Seriendrucke oder Vorlagen für Text erstellen. Jeder Ausdruck kann mithilfe eines Platzhalters getrennt definiert und formatiert werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-combine-multiple-formats-in-a-text-box"></a>So kombinieren Sie mehrere Formatierungen in einem Textfeld  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** auf **Textfeld**. Klicken Sie auf die Entwurfsoberfläche, und erstellen Sie dann durch Ziehen ein Feld mit der gewünschten Größe.  
  
2.  Wählen Sie im Textfeld den Text aus, der formatiert werden soll.  
  
3.  Klicken Sie mit der rechten Maustaste auf den markierten Text, und klicken Sie dann auf **Texteigenschaften**.  
  
4.  Legen Sie die Formatierungsoptionen fest. Beispielsweise auf der Registerkarte **Allgemein** :  
  
    -   **QuickInfo:** Geben Sie Text ein oder einen Ausdruck, der zu einer QuickInfo ausgewertet wird. Die QuickInfo wird angezeigt, wenn der Benutzer den Mauszeiger über das Element in einem Bericht hält.  
  
    -   **Markuptyp:** Wählen Sie eine Option aus, um anzugeben, wie der markierte Text gerendert wird:  
  
         **Nur Text:** Zeigt den markierten Text als einfachen Text an. HTML wird als Literaltext behandelt.  
  
         **HTML**  Zeigt den markierten Text als HTML an. Wenn der Ausdruckswert des Platzhalters gültige HTML-Tags enthält, werden diese Tags als HTML gerendert. Weitere Informationen finden Sie unter [Importieren von HTML in einen Bericht (Berichts-Generator und SSRS)](importing-html-into-a-report-report-builder-and-ssrs.md).  
  
5.  Klicken Sie auf **OK**.  
  
6.  Wiederholen Sie die Schritte 2 bis 5 für den übrigen zu formatierenden Text.  
  
### <a name="to-format-text-and-placeholders-differently-in-the-same-text-box"></a>So formatieren Sie Text und Platzhalter im gleichen Textfeld unterschiedlich  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** auf **Liste**. Klicken Sie auf die Entwurfsoberfläche, und erstellen Sie dann durch Ziehen ein Feld mit der gewünschten Größe. Das Dialogfeld **Dataseteigenschaften** wird angezeigt. Sie können ein freigegebenes Dataset oder ein im Bericht eingebettetes Dataset verwenden. Weitere Informationen finden Sie unter [Dataseteigenschaften (Dialogfeld), Abfrage (Berichts-Generator)](../report-data/dataset-properties-dialog-box-query-report-builder.md) oder [Dataseteigenschaften (Dialogfeld), Abfrage](../dataset-properties-dialog-box-query.md).  
  
2.  Klicken Sie auf der Registerkarte **Einfügen** auf **Textfeld**. Klicken Sie in die Liste, und erstellen Sie dann durch Ziehen ein Feld mit der gewünschten Größe.  
  
3.  Geben Sie im Textfeld eine Bezeichnung ein, z. B. **Mein Feld**.  
  
4.  Ziehen Sie ein Feld aus dem Dataset in das Textfeld. Es wird ein Platzhalter für das Feld erstellt.  
  
5.  Wählen Sie für einfache Formatierung den Platzhaltertext aus, und klicken Sie dann auf der Registerkarte **Home** in der Gruppe **Schriftart** auf eine der Formatierungsoptionen. Klicken Sie z.B. auf die Schaltfläche **Bold** (Fett).  
  
     Klicken Sie mit der rechten Maustaste auf den Platzhaltertext, und klicken Sie dann auf **Platzhaltereigenschaften**, um weitere Formatierungsoptionen anzuzeigen.  
  
6.  Klicken Sie auf **OK**. Das Textfeld in der Berichtsentwurfsansicht sollte „**Mein Feld**: [*Feldname*]“ enthalten, wobei *Feldname* der Name des Felds ist.  
  
7.  Klicken Sie auf **Ausführen**.  
  
 Die Liste wird für jeden Wert im Feld einmal wiederholt, und der Platzhalter *Feldname* wird jedes Mal durch den Wert dieses Felds im Dataset ersetzt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Textfelder &#40;Berichts-Generator und SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [Formatieren von Text und Platzhaltern &#40;Berichts-Generator und SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Hinzufügen von HTML in einem Bericht (Berichts-Generator und SSRS)](add-html-into-a-report-report-builder-and-ssrs.md)   
 [Listet &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Formatieren von Zahlen und Datumsangaben &#40;Berichts-Generator und SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Platzhaltereigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
