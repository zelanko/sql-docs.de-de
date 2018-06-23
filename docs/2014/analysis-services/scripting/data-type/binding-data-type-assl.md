---
title: Binding-Datentyp (ASSL) | Microsoft Docs
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
- Binding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- BINDING
helpviewer_keywords:
- Binding data type
ms.assetid: 0a777219-b885-4961-ac66-b76faeb520db
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 24847c70a0baf6ee12c1de6364cdd1e8d4327f91
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151674"
---
# <a name="binding-data-type-assl"></a>Binding-Datentyp (ASSL)
  Definiert einen abstrakten Grunddatentyp, der eine abhängige Beziehung zwischen zwei Objekten darstellt, in der die Daten oder Metadaten des einen Objekts von den Daten oder Metadaten eines gebundenen Objekts abhängen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Binding>...</Binding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|[AttributeBinding](binding-data-type-assl.md), [ColumnBinding](columnbinding-data-type-assl.md), [CubeAttributeBinding](cubeattributebinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), [InheritedBinding](inheritedbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), [MeasureGroupBinding](measuregroupbinding-data-type-assl.md), [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md), [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md), [RowBinding](rowbinding-data-type-assl.md), [TabularBinding](tabularbinding-data-type-assl.md), [TimeAttributeBinding](timeattributebinding-data-type-assl.md), [TimeBinding](timebinding-data-type-assl.md), [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Binding>.  
  
 Weitere Informationen zur Datenbindung finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="elements-of-type-binding"></a>Elemente des Typs "Bindung"  
 Die folgende Tabelle enthält Elemente des Typs `Binding`.  
  
|Übergeordnetes Element|Element des Typs `Binding`|Kommentare|  
|--------------------|---------------------------------|--------------|  
|[AttributeTranslation](../properties/source-element-binding-assl.md) von [CaptionColumn](../objects/column-element-assl.md) (des Typs [DataItem](dataitem-data-type-assl.md))|Geben Sie für die `Binding` muss [AttributeBinding](binding-data-type-assl.md) oder [ColumnBinding](columnbinding-data-type-assl.md)|  
|[Cube](../objects/cube-element-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md)|  
|[CubeBinding (Out-of-Line)](../objects/group-element-assl.md)|Geben Sie für die `Binding` muss [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[DataItem](dataitem-data-type-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|`Binding` kann einen beliebigen Typ sein.|  
|[Dimension](../objects/dimension-element-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), oder [TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](dimensionattribute-data-type-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [AttributeBinding](binding-data-type-assl.md) oder [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
|[DrillThroughAction](action-data-type-assl.md)|[Column](../objects/column-element-assl.md)|Geben Sie für die `Binding` muss [CubeAttributeBinding](cubeattributebinding-data-type-assl.md) oder [MeasureBinding](measurebinding-data-type-assl.md)|  
|[Measure](../objects/measure-element-assl.md)|[Quelle](../properties/source-element-binding-assl.md) (des Typs [DataItem](dataitem-data-type-assl.md))|Geben Sie für die `Binding` muss [ColumnBinding](columnbinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), oder [RowBinding](rowbinding-data-type-assl.md)|  
|[MeasureGroup-Objekt](../objects/measuregroup-element-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[Quelle](../properties/source-element-binding-assl.md) von [KeyColumn](../objects/keycolumn-element-assl.md) (des Typs [DataItem](dataitem-data-type-assl.md))|Geben Sie für die `Binding` muss [AttributeBinding](binding-data-type-assl.md) oder [ColumnBinding](columnbinding-data-type-assl.md), oder [InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[MeasureGroupBinding (Out-of-Line)](measuregroupbinding-data-type-out-of-line-assl.md)|[Dimension](../objects/dimension-element-assl.md)|Geben Sie für die `Binding` muss [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (Out-of-Line)](measuregroupbinding-data-type-out-of-line-assl.md)|[Measure](../objects/measure-element-assl.md)|Geben Sie für die `Binding` muss [MeasureBinding](measurebinding-data-type-assl.md)|  
|[MeasureGroupBinding (Out-of-Line)](../objects/partition-element-assl.md)|Geben Sie für die `Binding` muss [PartitionBinding](partitionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (Out-of-Line)](measuregroupbinding-data-type-out-of-line-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [TableBinding](tablebinding-data-type-assl.md)|  
|[MeasureGroupDimension](dimension-data-type-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), oder [DimensionBinding](dimensionbinding-data-type-assl.md)|  
|[Partition](../objects/partition-element-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [TabularBinding](tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[Quelle](../properties/source-element-binding-assl.md)|Geben Sie für die `Binding` muss [AttributeBinding](binding-data-type-assl.md), [CubeAttributeBinding-Datentyp &#40;ASSL&#41;](cubeattributebinding-data-type-assl.md), oder [MeasureBinding-Datentyp &#40;ASSL&#41;](measurebinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/sourcemeasuregroup-element-assl.md)|Geben Sie für die `Binding` muss [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  