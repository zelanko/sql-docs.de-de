---
title: AggregationDesign-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationDesign Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesign
helpviewer_keywords:
- AggregationDesign element
ms.assetid: 80ad98d8-73a8-4353-b5ad-d2a9ac3bc531
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 430035dd83cf137cb80a5db5d159da027014e6c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075290"
---
# <a name="aggregationdesign-element-assl"></a>AggregationDesign-Element (ASSL)
  Definiert einen Satz von Aggregationsdefinitionen, die für mehrere Partitionen in einer Datenbank freigegeben sein können.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationDesigns>  
   <AggregationDesign>  
      <ID>...</ID>  
      <Name>...</Name>  
            <Description>...</Description>  
      <EstimatedRows>...</EstimatedRows>  
      <Dimensions>...</Dimensions>  
            <Aggregations>...</Aggregation>  
      <EstimatedPerformanceGain>...</EstimatedPerformanceGain>  
      <Annotations>...</Annotations>  
   </AggregationDesign>  
</AggregationDesigns>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AggregationDesigns](../collections/aggregationdesigns-element-assl.md)|  
|Untergeordnete Elemente|[Aggregationen](../collections/aggregations-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [Dimensionen](../collections/dimensions-element-assl.md), [EstimatedPerformanceGain](../properties/estimatedperformancegain-element-assl.md), [EstimatedRows](../properties/estimatedrows-element-assl.md), [ID](../properties/id-element-assl.md), [Name](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>Siehe auch  
 [Partitions-Element &#40;ASSL&#41;](partition-element-assl.md)   
 [Aggregation-Element &#40;ASSL&#41;](aggregation-element-assl.md)   
 [Aggregations-Element &#40;ASSL&#41;](../collections/aggregations-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
