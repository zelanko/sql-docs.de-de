---
title: Browser (Cube-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.view.f1
ms.assetid: efb5ee1c-de50-4bfc-83ff-08a4f03c3ece
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8f431abab7f69c957b64d83f2f06c7675c566b2b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147603"
---
# <a name="browser-cube-designer-analysis-services---multidimensional-data"></a>Browser (Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Untersuchen Sie im Cube-Designer auf der Registerkarte **Browser** Dimensionen, Measures und KPIs in einem Cube. In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]wurde der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Cubebrowser in den MDX-Abfrage-Designer integriert und stellt ein grafische Benutzeroberfläche bereit, auf der Sie MDX-Abfragen, Filter und Slicecubes erstellen und einen Drilldown in Hierarchien ausführen.  
  
 Die Registerkarte **Browser** verfügt über zwei Modi: **Entwurfsmodus** und **Abfragemodus**. In jedem der Modi können Sie die Objekte im Bereich **Metadaten** zur Untersuchung des Cubes verwenden oder Elemente aus dem Bereich **Metadaten** in den Abfragebereich ziehen, um eine MDX-Abfrage zu erstellen, mit der die Daten abgerufen werden, die Sie verwenden möchten.  
  
 **Durchsuchen Sie und Fragen Sie mithilfe des Grafischen Entwurfsmodus ab**  
  
 In der folgenden Abbildung wird die Schnittstelle **Browser** im grafischen **Entwurfsmodus**angezeigt.  
  
 ![Analysis Services-MDX-Abfrage-Designer, Entwurfsansicht](media/rsqd-dsawas-mdx-designmode.gif "Analysis Services MDX query designer, design view")  
  
 Während Sie im grafischen Entwurfsmodus arbeiten werden, wenn die **AutoExecute** (![Automatisches Ausführen der Abfrage](media/rsqdicon-autoexecute.gif "Automatisches Ausführen der Abfrage")) auf der Symbolleiste auf die Umschaltfläche ausgewählt ist, die **Browser** führt eine Abfrage jedes Mal, dass Sie ein Metadatenobjekt im Datenbereich ablegen. Sie können auch manuell ausführen, die Abfrage mithilfe der **Abfrage ausführen** (![führen Sie die Abfrage](media/rsqdicon-run.gif "führen Sie die Abfrage")) auf der Symbolleiste.  
  
 Um vom grafischen Abfrage-Designer in den **Abfragemodus** zu wechseln und mit dem Text der MDX-Anweisungen zu arbeiten, klicken Sie auf der Symbolleiste auf die Schaltfläche **Entwurfsmodus** .  
  
 **Durchsuchen Sie und Fragen Sie mithilfe von MDX-Textmodus ab**  
  
 Im MDX-Testentwurfsmodus können Sie direkt mit MDX arbeiten. Der Bereich **Metadaten** ist immer noch verfügbar, damit Sie dem Abfrageentwurfsbereich Objekte hinzufügen können. Sie können zudem per Drag &amp; Drop MDX-Funktionen und -Operatoren aus der Liste in den Bereich **Funktionen** verschieben.  
  
 In der folgenden Abbildung wird die Schnittstelle **Browser** für den Abfragemodus angezeigt.  
  
 ![Analysis Services-MDX-Abfrage-Designer, Abfrageansicht](media/rsqd-dsawas-mdx-querymode.gif "Analysis Services MDX query designer, query view")  
  
 Sie können mit der Arbeit im grafischen Entwurfsmodus beginnen, alle erforderlichen Objekte hinzufügen, Filter hinzufügen, um den Cube in Slices aufzuteilen, und dann in den Textmodus wechseln, um die generierte Standard-MDX-Abfrage zu erweitern, und zusätzliche Elementeigenschaften und Zelleigenschaften einfügen.  
  
 Im Bereich **Metadaten** werden Registerkarten für **Metadaten** und **Funktionen**angezeigt. Auf der Registerkarte **Metadaten** können Sie Dimensionen, Hierarchien, KPIs und Measures in den Abfrageentwurfsbereich ziehen. Auf der Registerkarte **Funktionen** können Sie Funktionen in den Abfrageentwurfsbereich ziehen. Wenn Sie die Abfrage ausführen, werden im Abfrageentwurfsbereich die Ergebnisse für die MDX-Abfrage angezeigt. Sie können auch auf der **Symbolleiste** auf **In Excel analysieren** klicken, um die Daten nach Microsoft Office Excel zu exportieren und die Ergebnisse wie normale Benutzer in einer PivotTable anzuzeigen. In den folgenden Abschnitten werden die Symbolleiste und die jeweiligen Bereiche für die einzelnen **Browsermodi** ausführlicher beschrieben.  
  
 Beachten Sie, dass bei der Arbeit im Textmodus die **AutoExecute** (![Automatisches Ausführen der Abfrage](media/rsqdicon-autoexecute.gif "Automatisches Ausführen der Abfrage")) auf der Symbolleiste auf die Umschaltfläche ist nicht verfügbar. Sie können manuell Abfragen ausführen, mit der **Abfrage ausführen** (![führen Sie die Abfrage](media/rsqdicon-run.gif "führen Sie die Abfrage")) auf der Symbolleiste.  
  
## <a name="sections"></a>Abschnitte  
 **Symbolleiste**  
 Die Symbolleiste enthält ein Tool, das in der Entwurfsansicht oder der Abfrageansicht verwendet werden kann. Weitere Informationen zur Symbolleiste und zur Verwendung der Funktionen finden Sie unter [Symbolleiste &#40;Registerkarte „Browser“, Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md).  
  
 **Analysieren in Excel**  
 Verwenden Sie die Funktion **In Excel analysieren** , um die aktuelle Auswahl der Cubedaten an Excel zu senden, damit Sie die Daten in einer PivotTable in der Vorschau anzeigen können. Die aktuelle Auswahl der Daten basiert auf den Elementen, die Sie aus dem Bereich **Metadaten** hinzugefügt haben, und beliebigen Filtern, die Sie möglicherweise mithilfe der Filter- und Abfrageerstellungsfunktionen definiert haben. Weitere Informationen finden Sie unter [Analysieren in Excel &#40;Registerkarte „Browser“, Cube-Designer, Analysis Services – mehrdimensionale Daten&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md).  
  
 **Metadaten**  
 Verwenden Sie den Bereich **Metadaten** , um im Cube enthaltene Objekte anzuzeigen, einen Drilldown in Hierarchien auszuführen und Measures zu untersuchen und zu verwenden. Nach dem Auswählen und zum Anzeigen der Daten, die ihnen im Bereich **Bericht** zugeordnet sind. Weitere Informationen zu diesem Bereich finden Sie unter [Metadaten &#40;Registerkarte „Browser“, Cube-Designer, Analysis Services – mehrdimensionale Daten&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md).  
  
 **Filter und Abfrage**  
 Verwenden Sie diesen Bereich der Entwurfsoberfläche, um MDX-Abfragen zu erstellen, indem Sie Objekte per Drag &amp; Drop aus dem Bereich **Metadaten** verschieben und Filterkriterien auf dem Quellcube oder der Dimension angeben. Weitere Informationen finden Sie unter [Abfrage und Daten &#40;Registerkarte „Browser“, Cube-Designer, Analysis Services – mehrdimensionale Daten&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Cubeobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)   
 [Cubes in mehrdimensionalen Modellen](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)  
  
  