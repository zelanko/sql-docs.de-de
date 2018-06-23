---
title: MeasureGroupDimension-Datentyp (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupDimension
helpviewer_keywords:
- MeasureGroupDimension data type
ms.assetid: 9d1c1c19-31ce-4c42-b2e6-4c1b08875a83
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 369e20e1eaf3c5716e81a580b587c69efa64455f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160083"
---
# <a name="measuregroupdimension-data-type-assl"></a>MeasureGroupDimension-Datentyp (ASSL)
  Definiert einen abstrakten Grunddatentyp, der die Beziehung zwischen einer Dimension und einer Measuregruppe darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MeasureGroupDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
      <Annotations>...</Annotations>  
   <Source>...</Source>  
</MeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|[DataMiningMeasureGroupDimension](dimension-data-type-assl.md), [DegenerateMeasureGroupDimension](measuregroupdimension-data-type-assl.md), [ManyToManyMeasureGroupDimension](manytomanymeasuregroupdimension-data-type-assl.md), [ReferenceMeasureGroupDimension](referencemeasuregroupdimension-data-type-assl.md), [RegularMeasureGroupDimension](regularmeasuregroupdimension-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Annotations](../collections/annotations-element-assl.md), [CubeDimensionID](../properties/id-element-assl.md), [Source](../properties/source-element-binding-assl.md)|  
|Abgeleitete Elemente|[Dimension](../objects/dimension-element-assl.md) ([Dimensions](../collections/dimensions-element-assl.md) , Auflistung von [MeasureGroup](../objects/group-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Jede `MeasureGroupDimension` ist ein Verweis auf eine der Dimensionen im Cube. Sie definieren, welche Cubedimension für die Measuregruppe gilt.  
  
 Der Attributsatz, der geliefert wird, bestimmt die Granularität (Umfang), indem die Measures in der Measuregruppe bekannt sind. Measures, die für Produktverkäufe stehen, sind beispielsweise in der Verkäufe-Measuregruppe enthalten. Informationen über diese Measures werden auf monatlicher und nicht auf wöchentlicher oder täglicher Basis in der zugrunde liegenden Datenquelle gespeichert. In diesem Fall würde nur das Attribut Monat aufgeführt werden, für die `MeasureGroupDimension` , die die Beziehung zwischen einer Zeitdimension und der Sales-Measuregruppe beschreibt. In seltenen Fällen könnte die Granularität in Hinsicht auf einen Satz von Attributen definiert werden. Wenn man beispielsweise den Attributsatz {Tag, Woche, Monat, Jahr} nimmt, in dem Tag Woche und Monat impliziert, aber Woche nicht Monat impliziert, könnten die in der Vorhersagen-Measuregruppe enthaltenen Measures nach Monat und Woche, nicht aber nach Tag bekannt sein.  
  
 Wenn kein Attribut geliefert wird, ist es so, als ob nur das Schlüsselattribut für die Dimension geliefert wäre (das die niedrigste Granularitätsstufe definiert). Jede Partition einer Measuregruppe muss die gleiche Granularität haben. Der Attributsatz, der aufgelistet wird, sollte in Bezug auf die Beziehungen zwischen Attributen nicht redundant sein. Wenn Monat beispielsweise Jahr impliziert, wird die Granularität als Monat, nicht als Monat  und Jahr definiert.  
  
 Ein `MeasureGroupDimension` muss eine Hierarchie enthalten, nur, wenn Sie darüber etwas bestimmtes angeben kann. (Es gibt keine Möglichkeit, auszuwählen, welche Hierarchien für eine bestimmte Measuregruppe gelten). Genauso muss sie nur dann ein [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md) enthalten, wenn sie darüber etwas Bestimmtes angeben kann.  
  
 Jede Hierarchie muss eine Teilmenge der in der [CubeDimension](cubedimension-data-type-assl.md)enthaltenen Hierarchien sein. Die Ebenen können nicht ausgewählt werden, auch wenn einige Ebenen abhängig von der Granularität der Measuregruppe automatisch deaktiviert werden könnten.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.MeasureGroupDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  