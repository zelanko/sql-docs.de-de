---
title: Berechnungs Tools (Registerkarte ' KPIs ', Cube-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpisview.calculationtoolspane.f1
ms.assetid: c030c725-7763-4c23-9988-4b274a88fc31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecd16965c81ccb091d70320bd91c56112d3c15a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088270"
---
# <a name="calculation-tools-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a>Berechnungstools (Registerkarte 'KPIs', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Bereichs **Berechnungstools** auf der Registerkarte **KPIs** im Cube-Designer können Sie Metadaten, Funktionen und Vorlagen durchsuchen, die zum Verwenden in KPIs (Key Performance Indicators) verfügbar sind.  
  
> [!NOTE]  
>  Der Bereich wird nur in der Formularansicht angezeigt.  
  
## <a name="options"></a>Tastatur  
 **Metadaten**  
 Zeigt die Metadaten für den ausgewählten Cube an.  
  
 Ziehen Sie ein ausgewähltes Element in den Bereich des **KPI-Formular-Editors** , um die MDX-Syntax (Multidimensional Expressions) für dieses Element am ausgewählten Speicherort in dem Bereich einzuschließen.  
  
 **Funktionen**  
 Zeigt die verfügbaren Funktionen für Ausdrücke und Bedingungen an.  
  
 Ziehen Sie ein ausgewähltes Element in den Bereich des KPI-Formular-Editors **** , um die MDX-Syntax für dieses Element am ausgewählten Speicherort in dem Bereich einzuschließen.  
  
> [!NOTE]  
>  Im Projektmodus liest das Dialogfeld **Berechnungstools** Informationen für diese Option aus einer XML-Datei mit dem Namen "MDXFunctions.xml", die in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]enthalten ist. Im Onlinemodus werden die Information für diese Optionen aus dem MDSCHEMA_FUNCTIONS-Schemarowset für die Instanz abgerufen.  
  
 **Betrachtet**  
 Zeigt die vordefinierten Vorlagen an, die für KPIs verfügbar sind.  
  
 Ziehen Sie ein ausgewähltes Element in den Bereich des KPI-Formular-Editors **** , um die MDX-Syntax für dieses Element am ausgewählten Speicherort in dem Bereich einzuschließen.  
  
## <a name="context-menu"></a>Kontextmenü  
 Wenn Sie mit der rechten Maustaste auf eines der im Bereich **Berechnungstools** angezeigten Elemente klicken, wird ein Kontextmenü angezeigt, das die folgenden Optionen enthält:  
  
 **Copy**  
 Wählen Sie diese Option aus, um das in **Metadaten** oder **Funktionen** ausgewählte Element in die Zwischenablage zu kopieren.  
  
> [!NOTE]  
>  Diese Option wird nicht angezeigt, wenn **Vorlagen** ausgewählt ist.  
  
> [!NOTE]  
>  Diese Option ist deaktiviert, wenn das ausgewählte Element nicht kopiert werden kann, z. b. der Ordner **Sets** einer Dimension, die unter **Metadaten** angezeigt wird, oder der Funktionsgruppen Ordner für eine Funktion, die in **Functions**angezeigt wird.  
  
 **Elemente filtern**  
 Wählen Sie diese Option aus, um das Dialogfeld **Elemente filtern** anzuzeigen und die angezeigten Elemente nach dem ausgewählten Element in **Metadaten**zu filtern. Weitere Informationen zum Dialogfeld **Elemente filtern** finden Sie unter [Dialogfeld „Elemente filtern“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn **Metadaten** ausgewählt wird.  
  
> [!NOTE]  
>  Diese Option ist nur aktiviert, wenn eine Ebene für ein Attribut in den **Metadaten**ausgewählt ist.  
  
 **Vorlage hinzufügen**  
 Wählen Sie diese Option aus, um dem Cubeskript ein neues berechnetes Element, eine neue benannte Menge oder einen Skriptbefehl auf der Basis der ausgewählten Vorlage hinzuzufügen und den **KPI-Formular-Editor** in der Formularansicht anzuzeigen.  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn **Metadaten** ausgewählt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cube-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [KPIs &#40;Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte ' KPIs ', Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [KPI-Planer &#40;Registerkarte KPIs, Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [KPI-Formular-Editor &#40;Registerkarte KPIs, Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [KPI-Browser &#40;Registerkarte KPIs, Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
