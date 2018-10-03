---
title: Dimension-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Dimension Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Dimension
helpviewer_keywords:
- Dimension element
ms.assetid: 71886014-f463-4b70-a2a2-d9e5053ba4f0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 70e4cae1e039f1d604492e78dbde392454b42863
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051140"
---
# <a name="dimension-element-assl"></a>Dimension-Element (ASSL)
  Definiert eine Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Dimensions>  
   <Dimension xsi:type="Dimension">...</Dimension> <!-- ancestor: Database -->  
   <!-- or -->  
   <Dimension xsi:type="AggregationDimension">...</Dimension> <!-- ancestor: Aggregation -->  
   <!-- or -->  
   <Dimension xsi:type="AggregationDesignDimension">...</Dimension> <!-- ancestor: AggregationDesign -->  
   <!-- or -->  
   <Dimension xsi:type="AggregationInstanceCubeDimension">...</Dimension> <!-- ancestor: AggregationInstance -->  
      <!-- or -->  
   <Dimension xsi:type="CubeDimension">...</Dimension> <!-- ancestor: Cube -->  
      <!-- or -->  
   <Dimension xsi:type="MeasureGroupDimension">...</Dimension> <!-- ancestor: MeasureGroup -->  
   <!-- or -->  
   <Dimension xsi:type="PerspectiveDimension">...</Dimension> <!-- ancestor: Perspective -->  
</Dimensions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
|Vorgänger oder übergeordnetes Element|Datentyp|  
|------------------------|---------------|  
|[Datenbank](../data-type/dimension-data-type-assl.md)|  
|[Aggregation](../data-type/aggregationdimension-data-type-assl.md)|  
|[Aggregationdesign-Objekts](../data-type/aggregationdesigndimension-data-type-assl.md)|  
|[AggregationInstance](../data-type/cubedimension-data-type-assl.md)|  
|[Cube](cube-element-assl.md)|[CubeDimension](../data-type/cubedimension-data-type-assl.md)|  
|[MeasureGroup-Objekt](../data-type/measuregroupdimension-data-type-assl.md)|  
|[Perspektive](../data-type/perspectivedimension-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Dimensions](../collections/dimensions-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die entsprechenden Elemente im Analysis Management Objects (AMO)-Objektmodell sind <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.AggregationDimension>, <xref:Microsoft.AnalysisServices.AggregationDesignDimension>, <xref:Microsoft.AnalysisServices.CubeDimension>, <xref:Microsoft.AnalysisServices.MeasureGroupDimension>, und <xref:Microsoft.AnalysisServices.PerspectiveDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
