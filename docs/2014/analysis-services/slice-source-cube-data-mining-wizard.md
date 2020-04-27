---
title: Quellcube in Slice (Data Mining-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.slicesourcecube.f1
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bcb156d5c0a3c1332e748878ddebda1772b80696
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068597"
---
# <a name="slice-source-cube-data-mining-wizard"></a>Quellcube in Slices aufteilen (Data Mining-Assistent)
  Im Dialogfeld **Quellcube in Slices aufteilen** können Sie die zum Trainieren des Modells verwendeten Daten einschränken. In der Regel enthält ein Cube Daten, die sich auf viele unterschiedliche Dimensionen und Attribute beziehen, z. B. auf alle Geschäfte, alle Regionen und alle Produkte. Da es nicht empfehlenswert ist, ein Modell für eine unbegrenzte Anzahl von Attributkombinationen zu trainieren, verwenden Sie dieses Dialogfeld, um einen bestimmten Trainingssatz für ein Modell auszuwählen.  
  
 Beispielsweise könnten Sie den AdventureWorks-Cube in Slices aufteilen, um nur einen Teil der Daten zu erhalten. Die Aufteilung kann nach einer bestimmten Produktlinie oder Region bzw. nach einem bestimmten Jahr erfolgen.  
  
 Wenn Sie mit Slices und Cubes nicht vertraut sind, empfehlen wir, die folgenden Artikel zu lesen:  
  
-   [Legen Sie die Eigenschaft Partitions Slice &#40;Analysis Services fest&#41;](multidimensional-models/set-the-partition-slice-property-analysis-services.md)  
  
-   [Erstellen und Verwalten einer lokalen Partition &#40;Analysis Services&#41;](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
> [!NOTE]  
>  Beachten Sie, dass dynamische MDX-Funktionen (z.B. [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) oder [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) in der Slice-Eigenschaft für Partitionen nicht unterstützt werden. Sie müssen das Slice mit expliziten Tupel- oder Elementverweisen definieren.  
>   
>  Anstatt beispielsweise [: &#40;Range&#41; &#40;MDX-&#41;](/sql/mdx/range-mdx) zum Definieren eines Bereichs zu verwenden, müssen Sie jedes Element anhand der bestimmten Jahre auflisten.  
>   
>  Wenn Sie ein komplexes Slice definieren müssen, empfiehlt sich das Definieren der Tupel im Slice mithilfe eines XMLA-Alter-Skripts. Anschließend können Sie das Befehlszeilentool „Ascmd“ oder die SSIS- [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) verwenden, um unmittelbar vor dem Verarbeiten der Partition das Skript auszuführen und den bestimmten Satz an Elementen zu erstellen.  
  
 **Weitere Informationen:** [Data Mining-Assistent &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Erstellen einer relationalen Miningstruktur](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Optionen  
 **Dimension**  
 Wählen Sie die Dimension aus, die Sie in Slices aufteilen möchten.  
  
 **Hierarchy**  
 Wählen Sie die Hierarchie aus, die Sie in Slices aufteilen möchten. Sie können eine beliebige Hierarchieebene auswählen. Allerdings befinden sich die im Modell verwendeten Attribute immer nur auf der ausgewählten Ebene.  
  
 Wenn Sie beispielsweise die Geography-Hierarchie verwenden und "Country" als Ebene auswählen, können Sie kein Modell erstellen, für das "City" als Attribut verwendet wird. Wenn Sie andererseits "City" als Ebene der Hierarchie auswählen, nach der die Sliceaufteilung erfolgen soll, können Sie kein Miningmodell erstellen, das auf "Country" basiert.  
  
 **Operator**  
 Wählen Sie den Operator aus, der beim Erstellen eines Sliceausdrucks verwendet werden soll.  
  
 Wenn Sie z. b. geography als Hierarchie ausgewählt haben, können Sie den Operator = auswählen und dann "Europe" als Filter eingeben, um nur die Cube-Daten für Europa zu erhalten.  
  
 **Filterausdruck**  
 Geben Sie einen Ausdruck ein, der beim Filtern des Cubes nach der ausgewählten Dimension als Kriterium verwendet werden soll.  
  
 **Parameters**  
 Diese Option wird nicht für Data Mining-Modelle verwendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Der Assistent &#40;Data Mining-Assistenten wird abgeschlossen&#41;](completing-the-wizard-data-mining-wizard.md)   
 [Data Mining-Assistent (F1-Hilfe &#40;Analysis Services-Data Mining-&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Verwendungs &#40;Data Mining-Assistenten für Mining Modell Spalten angeben&#41;](specify-mining-model-column-usage-data-mining-wizard.md)  
  
  
