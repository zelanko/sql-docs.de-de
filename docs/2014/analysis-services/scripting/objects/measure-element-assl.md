---
title: Measure-Element (ASSL) | Microsoft-Dokumentation
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
- Measure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Measure
helpviewer_keywords:
- Measure element
ms.assetid: 4c2c2ed1-7f78-4564-982a-132f13bea36f
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80d59a5356bf1c0b5712e729f230fff9383603cc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159331"
---
# <a name="measure-element-assl"></a>Measure-Element (ASSL)
  Definiert ein Measure.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Measures>  
   <Measure> <!-- ancestor: MeasureGroup -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <AggregateFunction>...</AggregateFunction>  
            <DataType>...</DataType>  
            <Source>...</Source>  
      <Visible>...</Visible>  
      <MeasureExpression>...</MeasureExpression>  
      <DisplayFolder>...</DisplayFolder>  
      <FormatString>...</FormatString>  
      <BackColor>...</BackColor>  
      <ForeColor>...</ForeColor>  
            <FontName>...</FontName>  
            <FontSize>...</FontSize>  
            <FontFlags>...</FontFlags>  
            <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Measure>  
   <!-- or  -->  
   <Measure xsi:type="AggregationInstanceMeasure">...</Measure> <!-- parent: AggregationInstance -->  
      <!-- or  -->  
   <Measure xsi:type="MeasureBinding">...</Measure> <!-- ancestor: MeasureGroupBinding (out-of-line) -->  
   <!-- or  -->  
   <Measure xsi:type="PerspectiveMeasure">...</Measure> <!-- ancestor: PerspectiveMeasureGroup -->  
</Measures>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
|Vorgänger oder übergeordnetes Element|Datentyp|  
|------------------------|---------------|  
|[AggregationInstance](../data-type/binding-data-type-assl.md)|  
|[MeasureGroup-Objekt](group-element-assl.md)|InclusionThresholdSetting|  
|[MeasureGroupBinding (Out-of-Line)](../data-type/measurebinding-data-type-assl.md)|  
|[PerspectiveMeasureGroup](../data-type/perspectivemeasure-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Measures](../collections/measures-element-assl.md)|  
  
|Vorgänger oder übergeordnetes Element|Untergeordnete Elemente|  
|------------------------|--------------------|  
|[MeasureGroup](../properties/aggregatefunction-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [BackColor](../properties/backcolor-element-assl.md), [DataType](../properties/datatype-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [DisplayFolder ](../properties/displayfolder-element-assl.md), [FontFlags](../properties/fontflags-element-assl.md), [FontName](../properties/name-element-assl.md), [FontSize](../properties/fontsize-element-assl.md), [ForeColor](../properties/forecolor-element-assl.md), [FormatString ](../properties/formatstring-element-assl.md), [ID](../properties/id-element-assl.md), [MeasureExpression](../properties/expression-element-assl.md), [Namen](../properties/name-element-assl.md), [Quelle](../properties/source-element-measure-assl.md), [Übersetzungen](../collections/translations-element-assl.md), [Sichtbar](../properties/visible-element-assl.md)|  
|Alle sonstigen|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Bindungsdetails können für ein Measure bereitgestellt werden. Diese Details fungieren dann als Standard pro Partition.  
  
 In größeren Cubes gibt es möglicherweise Hunderte von Measures und Hierarchien. Die `DisplayFolder` -Eigenschaft definiert die benutzerdarstellung auf dem Client. Der Wert des der `DisplayFolder` Eigenschaft kann eine der folgenden Optionen enthalten:  
  
-   Kann leer sein, wobei angegeben wird, dass das Measure nicht zu einem Ordner gehört.  
  
-   Kann einen einzelnen Ordnernamen enthalten, wobei angegeben wird, dass das Measure als zu einem Ordner mit diesem Namen gehörend gerendert werden sollte.  
  
-   Kann mehrere Ordnernamen an, getrennt durch einen umgekehrten Schrägstrich enthalten (\\), die eine eingebettete Ordnerhierarchie angibt.  
  
 Die `DisplayFolder`-Eigenschaft gilt auch für berechnete Measures und Hierarchien.  
  
 Die entsprechenden Elemente im Analysis Management Objects (AMO)-Objektmodell sind <xref:Microsoft.AnalysisServices.Measure> und <xref:Microsoft.AnalysisServices.PerspectiveMeasure>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
