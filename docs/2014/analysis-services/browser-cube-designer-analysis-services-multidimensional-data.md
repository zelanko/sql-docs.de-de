---
title: Browser (Cube-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.view.f1
ms.assetid: efb5ee1c-de50-4bfc-83ff-08a4f03c3ece
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 902d35dfc20973dbbad5e6608d5934b31245d9d2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78174299"
---
# <a name="browser-cube-designer-analysis-services---multidimensional-data"></a>Browser (Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Untersuchen Sie im Cube-Designer auf der Registerkarte **Browser** Dimensionen, Measures und KPIs in einem Cube. In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]wurde der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Cubebrowser in den MDX-Abfrage-Designer integriert und stellt ein grafische Benutzeroberfläche bereit, auf der Sie MDX-Abfragen, Filter und Slicecubes erstellen und einen Drilldown in Hierarchien ausführen.

 Die Registerkarte **Browser** verfügt über zwei Modi: **Entwurfsmodus** und **Abfragemodus**. In jedem der Modi können Sie die Objekte im Bereich **Metadaten** zur Untersuchung des Cubes verwenden oder Elemente aus dem Bereich **Metadaten** in den Abfragebereich ziehen, um eine MDX-Abfrage zu erstellen, mit der die Daten abgerufen werden, die Sie verwenden möchten.

 **Durchsuchen und Abfragen mithilfe des grafischen Entwurfsmodus**

 In der folgenden Abbildung wird die Schnittstelle **Browser** im grafischen **Entwurfsmodus**angezeigt.

 ![MDX-Abfrage-Designer für Analysis Services, Entwurfsansicht](media/rsqd-dsawas-mdx-designmode.gif "MDX-Abfrage-Designer für Analysis Services, Entwurfsansicht")

 Wenn Sie im grafischen Entwurfs Modus arbeiten und die UMSCHALT Fläche **autoExecute** (![autoExecute the Query](media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen")) auf der Symbolleiste aktiviert ist, führt der **Browser** jedes Mal eine Abfrage aus, wenn Sie ein Metadatenobjekt im Datenbereich ablegen. Sie können die Abfrage auch manuell mithilfe der Schaltfläche **Abfrage ausführen** (![Abfrage ausführen](media/rsqdicon-run.gif "Abfrage ausführen")) auf der Symbolleiste ausführen.

 Um vom grafischen Abfrage-Designer in den **Abfragemodus** zu wechseln und mit dem Text der MDX-Anweisungen zu arbeiten, klicken Sie auf der Symbolleiste auf die Schaltfläche **Entwurfsmodus** .

 **Durchsuchen und Abfragen mithilfe des MDX-Textmodus**

 Im MDX-Testentwurfsmodus können Sie direkt mit MDX arbeiten. Der Bereich **Metadaten** ist immer noch verfügbar, damit Sie dem Abfrageentwurfsbereich Objekte hinzufügen können. Sie können zudem per Drag &amp; Drop MDX-Funktionen und -Operatoren aus der Liste in den Bereich **Funktionen** verschieben.

 In der folgenden Abbildung wird die Schnittstelle **Browser** für den Abfragemodus angezeigt.

 ![MDX-Abfrage-Designer für Analysis Services, Abfrageansicht](media/rsqd-dsawas-mdx-querymode.gif "MDX-Abfrage-Designer für Analysis Services, Abfrageansicht")

 Sie können mit der Arbeit im grafischen Entwurfsmodus beginnen, alle erforderlichen Objekte hinzufügen, Filter hinzufügen, um den Cube in Slices aufzuteilen, und dann in den Textmodus wechseln, um die generierte Standard-MDX-Abfrage zu erweitern, und zusätzliche Elementeigenschaften und Zelleigenschaften einfügen.

 Im Bereich **Metadaten** werden Registerkarten für **Metadaten** und **Funktionen**angezeigt. Auf der Registerkarte **Metadaten** können Sie Dimensionen, Hierarchien, KPIs und Measures in den Abfrageentwurfsbereich ziehen. Auf der Registerkarte **Funktionen** können Sie Funktionen in den Abfrageentwurfsbereich ziehen. Wenn Sie die Abfrage ausführen, werden im Abfrageentwurfsbereich die Ergebnisse für die MDX-Abfrage angezeigt. Sie können auch auf der **Symbolleiste** auf **In Excel analysieren** klicken, um die Daten nach Microsoft Office Excel zu exportieren und die Ergebnisse wie normale Benutzer in einer PivotTable anzuzeigen. In den folgenden Abschnitten werden die Symbolleiste und die jeweiligen Bereiche für die einzelnen **Browsermodi** ausführlicher beschrieben.

 Beachten Sie, dass während der Arbeit im Textmodus die UMSCHALT Fläche **autoExecute** (![autoExecute the Query](media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen")) auf der Symbolleiste nicht verfügbar ist. Sie können Abfragen jedoch manuell mithilfe der Schaltfläche **Abfrage ausführen** (![Abfrage ausführen](media/rsqdicon-run.gif "Abfrage ausführen")) auf der Symbolleiste ausführen.

## <a name="sections"></a>Abschnitte
 **In Excel analysieren** Die Symbolleiste enthält ein Tool, das in der Entwurfsansicht oder der Abfrageansicht verwendet werden kann. Weitere Informationen zur Symbolleiste und zur Verwendung der Funktionen finden Sie unter [Symbolleiste &#40;Registerkarte „Browser“, Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md).

 **Symbolleiste** Untersuchen Sie im Cube-Designer auf der Registerkarte **Symbolleiste** , um die aktuelle Auswahl der Cubedaten an Excel zu senden, damit Sie die Daten in einer PivotTable in der Vorschau anzeigen können. Die aktuelle Auswahl der Daten basiert auf den Elementen, die Sie aus dem Bereich **Metadaten** hinzugefügt haben, und beliebigen Filtern, die Sie möglicherweise mithilfe der Filter- und Abfrageerstellungsfunktionen definiert haben. Weitere Informationen finden Sie unter [Analysieren in Excel &#40;Registerkarte „Browser“, Cube-Designer, Analysis Services – mehrdimensionale Daten&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md).

 **Metadaten** Untersuchen Sie im Cube-Designer auf der Registerkarte **Metadaten** , um im Cube enthaltene Objekte anzuzeigen, einen Drilldown in Hierarchien auszuführen und Measures zu untersuchen und zu verwenden. Nach dem Auswählen und zum Anzeigen der Daten, die ihnen im Bereich **Bericht** zugeordnet sind. Weitere Informationen zu diesem Bereich finden Sie unter [Metadaten &#40;Registerkarte „Browser“, Cube-Designer, Analysis Services – mehrdimensionale Daten&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md).

 **Filter und Abfrage** Verwenden Sie diesen Bereich der Entwurfsoberfläche, um MDX-Abfragen zu erstellen, indem Sie Objekte per Drag & Drop aus dem Bereich **Metadaten** verschieben und Filterkriterien auf dem Quellcube oder der Dimension angeben. Weitere Informationen finden Sie unter [Abfrage und Daten &#40;Registerkarte „Browser“, Cube-Designer, Analysis Services – mehrdimensionale Daten&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md).

## <a name="see-also"></a>Weitere Informationen
 [Cubeobjekte &#40;Analysis Services Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) [Cubes in mehrdimensionalen Modellen](multidimensional-models/cubes-in-multidimensional-models.md) [Cube-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)


