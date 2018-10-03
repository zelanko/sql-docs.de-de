---
title: MeasureGroup-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureGroup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroup
helpviewer_keywords:
- MeasureGroup element
ms.assetid: 7aa099db-5dc7-4cac-b437-f73fc0921b24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 84186a736f7d3e17587a3a5457b1c7850c02f12b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089710"
---
# <a name="measuregroup-element-assl"></a>MeasureGroup-Element (ASSL)
  Definiert auf der gleichen Ebene wie die Granularität eine Menge von Measures.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MeasureGroups>  
   <MeasureGroup> <!-- ancestor: Cube -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</<Create  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Type>...</Type>  
      <State>...</State>  
      <MeasureQualification>...</MeasureQualification>  
      <Measures>...</Measures>  
      <DataAggregation>...</DataAggregation>  
      <Source>...</Source>  
            <StorageMode>...</StorageMode>  
      <StorageLocation>...</StorageLocation>  
      <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
            <ProactiveCaching>...</ProactiveCaching>  
      <EstimatedRows>...</EstimatedRows>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <EstimatedSize>...</EstimatedSize>  
      <ProcessingMode>...</ProcessingMode>  
      <Dimensions>...</Dimensions>  
      <Partitions>...</Partitions>  
      <AggregationPrefix>...</AggregationPrefix>  
      <ProcessingPriority>...</ProcessingPriority>  
            <AggregationDesigns>...</AggregationDesigns>  
      <Annotations>...</Annotations>  
   </MeasureGroup>  
   <!-- or  -->  
   <MeasureGroup xsi:type="MeasureGroupBinding">...</MeasureGroup> <!-- ancestor: CubeBinding -->  
   <!-- or  -->  
   <MeasureGroup xsi:type="PerspectiveMeasureGroup">...</MeasureGroup> <!-- ancestor: Perspective -->  
</MeasureGroups>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
|Vorgänger oder übergeordnetes Element|Datentyp|  
|------------------------|---------------|  
|[Cube](cube-element-assl.md)|None|  
|[CubeBinding](../data-type/binding-data-type-assl.md)|  
|[Perspektive](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MeasureGroups](../collections/groups-element-assl.md)|  
|Untergeordnete Elemente||  
  
|Vorgänger oder übergeordnetes Element|Untergeordnete Elemente|  
|------------------------|--------------------|  
|[Cube](../collections/aggregationdesigns-element-assl.md), [AggregationPrefix](../properties/aggregationprefix-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DataAggregation](aggregation-element-assl.md), [ Beschreibung](../properties/description-element-assl.md), [Dimensionen](../collections/dimensions-element-assl.md), [ErrorConfiguration](errorconfiguration-element-assl.md), [EstimatedRows](../properties/estimatedrows-element-assl.md), [EstimatedSize](../properties/estimatedsize-element-assl.md), [ID](../properties/id-element-assl.md), [IgnoreUnrelatedDimensions](../properties/ignoreunrelateddimensions-element-assl.md), [LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [ MeasureQualification](../properties/measurequalificaton-element-assl.md), [Measures](../collections/measures-element-assl.md), [Namen](../properties/name-element-assl.md), [Partitionen](../collections/partitions-element-assl.md), [ProactiveCaching](proactivecaching-element-assl.md), [ ProcessingMode](../properties/processingmode-element-assl.md), [ProcessingPriority](../properties/processingpriority-element-assl.md), [Quelle](../properties/source-element-measure-assl.md), [Zustand](../properties/state-element-assl.md), [StorageLocation](../properties/storagelocation-element-assl.md), [ StorageMode](../properties/storagemode-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md), [Typ](../properties/type-element-measuregroup-assl.md)|  
|[CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md)|None|  
|[Perspektive](perspective-element-assl.md)|None|  
  
## <a name="remarks"></a>Hinweise  
 Alle Measures einer Measuregruppe müssen aus einer einzigen Tabelle stammen. Eine Measuregruppe kann Standardbindungen definieren, die für jede Partition überschrieben werden können.  
  
 Das `MeasureGroup`-Element definiert Details, die Measuregruppen auf regulären Cubes und virtuellen Cubes gemein sind. Separate Untertypen definieren die Details spezifisch für jeden Typ.  
  
 Die `State`-Eigenschaft von `MeasureGroup` hat die folgenden Werte:  
  
-   *FullyProcessed* , wenn alle Partitionen verarbeitet wurden.  
  
-   *PartiallyProcessed* , wenn wenigstens eine Partition verarbeitet wurde.  
  
-   *Unprocessed* , wenn keine Partition verarbeitet wurde.  
  
 Die entsprechenden Elemente im Analysis Management Objects (AMO)-Objektmodell sind <xref:Microsoft.AnalysisServices.MeasureGroup> und <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
