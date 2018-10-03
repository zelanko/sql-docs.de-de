---
title: Attributes-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Attributes Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Attributes
helpviewer_keywords:
- Attributes element
ms.assetid: d6b545e6-1521-496f-a731-f2c2c44118e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d726fe60be6aa2e79e8f1032f4f49606472baf3f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131210"
---
# <a name="attributes-element-assl"></a>Attributes-Element (ASSL)
  Enthält die Auflistung der Attribute für die verknüpfte Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationDesignDimension> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Attributes>  
      <Attribute>...</Attribute>  
  </Attributes>  
   ...  
</AggregationDesignDimension>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AggregationDesignDimension](../data-type/dimension-data-type-assl.md), [AggregationDimension](../data-type/aggregationdimension-data-type-assl.md), [AggregationInstanceCubeDimension](../data-type/cubedimension-data-type-assl.md), [CubeDimension](../data-type/cubedimension-data-type-assl.md), [Dimension ](../objects/dimension-element-assl.md), [PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md), [RegularMeasureGroupDimension](../data-type/measuregroupdimension-data-type-assl.md), [' relationshipEnd '](../data-type/relationshipend-data-type-assl.md)|  
|Untergeordnete Elemente|[Attribut](../objects/attribute-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die entsprechenden Elemente im Analysis Management Objects (AMO)-Objektmodell sind <xref:Microsoft.AnalysisServices.AggregationAttributeCollection>, <xref:Microsoft.AnalysisServices.AggregationDesignAttributeCollection>, <xref:Microsoft.AnalysisServices.AggregationInstanceAttributeCollection>, <xref:Microsoft.AnalysisServices.CubeAttributeCollection>, <xref:Microsoft.AnalysisServices.DimensionAttributeCollection>, <xref:Microsoft.AnalysisServices.MeasureGroupAttributeCollection>, und <xref:Microsoft.AnalysisServices.PerspectiveAttributeCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
