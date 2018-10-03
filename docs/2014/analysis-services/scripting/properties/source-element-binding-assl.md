---
title: Source-Element (Bindung) (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Source Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 1032558c-7546-4ca7-888d-8139df23cb62
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a2600803402d87e880ad479be660de98ff5d32f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061330"
---
# <a name="source-element-binding-assl"></a>Source-Element (Binding) (ASSL)
  Identifiziert die Datenquelle, an die das übergeordnete Element gebunden ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationInstance> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Source>...</Source>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Finden Sie unter Typ Datentabelle unten|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
 **Datentyp und-Länge**  
  
|||  
|-|-|  
|Vorgänger oder übergeordnetes Element|Datentyp|  
|[AggregationInstance](../data-type/binding-data-type-assl.md)|  
|[AggregationInstanceMeasure](../data-type/columnbinding-data-type-assl.md)|  
|[Cube](../data-type/datasourceviewbinding-data-type-assl.md)|  
|[DataItem-Objekt](../data-type/dataitem-data-type-assl.md)|Einen beliebigen Datentyp aufweisen, die von abgeleiteten [Bindung](../data-type/binding-data-type-assl.md), je nachdem, auf das übergeordnete Element des `DataItem`. Weitere Informationen finden Sie in den Hinweisen.|  
|[Dimension](../data-type/dimensionbinding-data-type-assl.md), [DataSourceViewBinding](../data-type/datasourceviewbinding-data-type-assl.md), [DimensionBinding](../data-type/dimensionbinding-data-type-assl.md), [TimeBinding](../data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../data-type/attributebinding-data-type-assl.md), [UserDefinedGroupBinding](../data-type/userdefinedgroupbinding-data-type-assl.md)|  
|[MeasureGroup-Objekt](../data-type/measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupDimension](../data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md)|[CubeDimensionBinding](../data-type/cubedimensionbinding-data-type-assl.md), [DataSourceViewBinding](../data-type/datasourceviewbinding-data-type-assl.md), [DimensionBinding](../data-type/dimensionbinding-data-type-assl.md)|  
|[Partition](../data-type/tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|Einen beliebigen Datentyp aufweisen, die von abgeleiteten [ProactiveCachingBinding](../data-type/proactivecachingbinding-data-type-assl.md), abhängig von den Verarbeitungs- und Benachrichtigungsoptionen, die vom übergeordneten Element verwendet die `ProactiveCaching` Element.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AggregationInstance](../objects/aggregationinstance-element-assl.md), [AggregationInstanceMeasure](../data-type/aggregationinstancemeasure-data-type-assl.md), [Cube](../objects/cube-element-assl.md), [DataItem](../data-type/dataitem-data-type-assl.md), [Dimension](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupDimension](../data-type/dimension-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [Partition ](../objects/partition-element-assl.md), [ProactiveCaching](../objects/proactivecaching-element-assl.md).|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 In der `Source` -Element, das abgeleitete `Binding` Datentypen, die in zulässig sind die `DataItem` Element abhängig vom übergeordneten Element von der `DataItem` Element.  
  
|Übergeordnetes Element von DataItem|Zulässige Datentypen|  
|---------------------|------------------------|  
|[DimensionAttribute](../data-type/attributebinding-data-type-assl.md), [ColumnBinding](../data-type/columnbinding-data-type-assl.md), [TimeAttributeBinding](../data-type/timeattributebinding-data-type-assl.md) (nur für [KeyColumns](../collections/columns-element-assl.md)).|  
|[MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md)|[AttributeBinding](../data-type/attributebinding-data-type-assl.md), [ColumnBinding](../data-type/columnbinding-data-type-assl.md), ["inheritedbinding"](../data-type/inheritedbinding-data-type-assl.md).|  
|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|[ColumnBinding](../data-type/columnbinding-data-type-assl.md)|  
  
 Weitere Informationen zu den `Binding` -Typ und zu Tabellen von Analysis Services Scripting Language (ASSL)-Objekten, von der `Binding` Typ und der Vererbungshierarchie des `Binding` Datentypen, finden Sie unter [Binding-Datentyp &#40;ASSL &#41;](../data-type/binding-data-type-assl.md).  
  
 Weitere Informationen zu datenbindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
