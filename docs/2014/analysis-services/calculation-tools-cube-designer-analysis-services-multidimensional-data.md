---
title: Berechnungstools (Registerkarte ' Berechnungen ', Cube-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.calculationtoolspane.f1
ms.assetid: b1aa8a1a-6532-45d2-8f53-d3e211d7197a
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 106821212578d341292be4ef5f33bef055d5c1c8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161250"
---
# <a name="calculation-tools-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a>Berechnungstools (Registerkarte 'Berechnungen', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Bereichs **Berechnungstools** auf der Registerkarte **Berechnungen** im Cube-Designer können Sie Metadaten, Funktionen und Vorlagen durchsuchen, die zum Verwenden in Berechnungen verfügbar sind.  
  
## <a name="options"></a>Tastatur  
 **Metadaten**  
 Zeigt die Metadaten für den ausgewählten Cube an.  
  
 Ziehen Sie ein ausgewähltes Element in den Bereich des Skript-Editors, des Formular-Editors für berechnete Elemente oder des Formular-Editors für benannte Mengen, um die MDX-Syntax für dieses Element an der ausgewählten Position in dem Bereich einzuschließen.  
  
 **Funktionen**  
 Zeigt die verfügbaren Funktionen für Ausdrücke und Bedingungen an.  
  
 Ziehen Sie ein ausgewähltes Element in den Bereich des **Skript-Editors**, des **Formular-Editors für berechnete Elemente**oder des **Formular-Editors für benannte Mengen** , um die MDX-Syntax für dieses Element am ausgewählten Speicherort in dem Bereich einzuschließen.  
  
> [!NOTE]  
>  Im Projektmodus liest das Dialogfeld **Berechnungstools** Informationen für diese Option aus einer XML-Datei mit dem Namen "MDXFunctions.xml", die in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]enthalten ist. Im Onlinemodus werden die Information für diese Optionen aus dem MDSCHEMA_FUNCTIONS-Schemarowset für die Instanz abgerufen.  
  
 **Vorlagen**  
 Zeigt die vordefinierten Vorlagen an, die für berechnete Elemente, benannte Mengen und Skriptbefehle verfügbar sind.  
  
 Ziehen Sie ein ausgewähltes Element in den Bereich des **Skript-Editors**, des **Formular-Editors für berechnete Elemente**oder des **Formular-Editors für benannte Mengen** , um die MDX-Syntax für dieses Element am ausgewählten Speicherort in dem Bereich einzuschließen.  
  
## <a name="context-menu"></a>Kontextmenü  
 Wenn Sie mit der rechten Maustaste auf eines der im Bereich **Berechnungstools** angezeigten Elemente klicken, wird ein Kontextmenü angezeigt, das die folgenden Optionen enthält:  
  
 **Kopieren**  
 Wählen Sie diese Option aus, um das in **Metadaten** oder **Funktionen** ausgewählte Element in die Zwischenablage zu kopieren.  
  
> [!NOTE]  
>  Diese Option wird nicht angezeigt, wenn **Vorlagen** ausgewählt ist.  
  
> [!NOTE]  
>  Diese Option ist nicht verfügbar, wenn das ausgewählte Element nicht kopiert werden kann. Das gilt z. B. für den Ordner **Mengen** einer Dimension, die unter **Metadaten** angezeigt wird, oder für den Funktionsgruppenordner für eine Funktion, die unter **Funktionen**angezeigt wird.  
  
 **Elemente filtern**  
 Wählen Sie diese Option aus, um das Dialogfeld **Elemente filtern** anzuzeigen und die angezeigten Elemente nach dem ausgewählten Element in **Metadaten**zu filtern. Weitere Informationen zum Dialogfeld **Elemente filtern** finden Sie unter [Dialogfeld „Elemente filtern“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn **Metadaten** ausgewählt wird.  
  
> [!NOTE]  
>  Die Option ist nur verfügbar, wenn eine Ebene für ein Attribut in **Metadaten**ausgewählt wird.  
  
 **Vorlage hinzufügen**  
 Wählen Sie diese Option aus, um dem Cubeskript ein neues berechnetes Element, eine neue benannte Menge oder einen neuen Skriptbefehl hinzuzufügen, und um den **Skript-Editor**, den **Formular-Editor für berechnete Elemente**oder den **Formular-Editor für benannte Mengen** für den betreffenden Befehl (in der Formularansicht) anzuzeigen. Sie können auch zu der Stelle im Bereich des **Skript-Editors** scrollen, an der sich der Befehl im Cubeskript befindet (in der Skriptansicht).  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn **Metadaten** ausgewählt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte Berechnungen, Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Skriptplaner &#40;Registerkarte Berechnungen, Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Formular-Editor &#40;Registerkarte Berechnungen, Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Set-Formular-Editor für benannte &#40;Registerkarte Berechnungen, Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Skript-Editor &#40;Registerkarte Berechnungen, Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)   
 [Berechnungen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  