---
title: Berechnungstools (Registerkarte ' Aktionen ', Cube-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionsview.calculationtoolspane.f1
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0613734c2ba4c2a8618d46854f2a3a7554068c71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328828"
---
# <a name="calculation-tools-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>Berechnungstools (Registerkarte 'Aktionen', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Bereichs **Berechnungstools** auf der Registerkarte **Aktionen** im Cube-Designer können Sie Metadaten, Funktionen und Vorlagen durchsuchen, die zum Verwenden in Aktionen, Drillthroughaktionen und Berichtsaktionen verfügbar sind.  
  
## <a name="options"></a>Tastatur  
 **Metadaten**  
 Zeigt die Metadaten für den ausgewählten Cube an.  
  
 Ziehen Sie ein ausgewähltes Element in den Bereich des **Aktionsformular-Editors**, **Drillthroughaktionsformular-Editors**oder **Berichtsaktionsformular-Editors** , um die MDX-Syntax (Multidimensional Expressions) für dieses Element am ausgewählten Speicherort in dem Bereich einzuschließen.  
  
 **Funktionen**  
 Zeigt die verfügbaren Funktionen für Ausdrücke und Bedingungen an.  
  
 Ziehen Sie ein ausgewähltes Element in den Bereich des **Aktionsformular-Editors**, **Drillthroughaktionsformular-Editors**oder **Berichtsaktionsformular-Editors** , um die MDX-Syntax für dieses Element am ausgewählten Speicherort in dem Bereich einzuschließen.  
  
> [!NOTE]  
>  Im Projektmodus liest das Dialogfeld **Berechnungstools** Informationen für diese Option aus einer XML-Datei mit dem Namen "MDXFunctions.xml", die in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]enthalten ist. Im Onlinemodus werden die Information für diese Optionen aus dem MDSCHEMA_FUNCTIONS-Schemarowset für die Instanz abgerufen.  
  
 **Vorlagen**  
 Zeigt die vordefinierten Vorlagen an, die für Aktionen verfügbar sind.  
  
 Ziehen Sie ein ausgewähltes Element in den Bereich des **Aktionsformular-Editors**, **Drillthroughaktionsformular-Editors**oder **Berichtsaktionsformular-Editors** , um die MDX-Syntax für dieses Element am ausgewählten Speicherort in dem Bereich einzuschließen.  
  
## <a name="context-menu"></a>Kontextmenü  
 Wenn Sie mit der rechten Maustaste auf eines der im Bereich **Berechnungstools** angezeigten Elemente klicken, wird ein Kontextmenü angezeigt, das die folgenden Optionen enthält:  
  
|Option|Definition|  
|------------|----------------|  
|**Kopieren**|Wählen Sie diese Option aus, um das in **Metadaten** oder **Funktionen** ausgewählte Element in die Zwischenablage zu kopieren.<br /><br /> Beachten Sie, dass diese Option nicht angezeigt wird **Vorlagen** ausgewählt ist. Beachten Sie, dass diese Option deaktiviert ist, wenn das ausgewählte Element kann, wie z. B. kopiert werden die **legt** Ordner einer Dimension, die im angezeigten **Metadaten** oder den funktionsgruppenordner für eine Funktion, die im angezeigt **Funktionen**.|  
|**Elemente filtern**|Wählen Sie diese Option aus, um das Dialogfeld **Elemente filtern** anzuzeigen und die angezeigten Elemente nach dem ausgewählten Element in **Metadaten**zu filtern. Weitere Informationen zum Dialogfeld **Elemente filtern** finden Sie unter [Dialogfeld „Elemente filtern“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Beachten Sie, dass diese Option nur, wenn angezeigt wird **Metadaten** ausgewählt ist. Beachten Sie, dass diese Option ist nur aktiviert, wenn in eine Ebene für ein Attribut ausgewählt ist **Metadaten**.|  
|**Vorlage hinzufügen**|Wählen Sie diese Option aus, um dem Cube eine neue Aktion, Drillthroughaktion oder Berichtsaktion auf der Grundlage der ausgewählten Vorlage hinzuzufügen und dementsprechend den **Aktionsformular-Editor**, **Drillthroughaktionsformular-Editor**oder **Berichtsaktionsformular-Editor**anzuzeigen.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Metadaten** ausgewählt ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Skripts Grundlagen &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Aktionen &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Aktionsplaner &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Aktionsformular-Editor &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Drillthroughaktionsformular-Editors &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Berichtsaktionsformular-Editors &#40;Registerkarte ' Aktionen ', Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
