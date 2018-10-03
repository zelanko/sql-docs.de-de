---
title: AggregationInstance-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationInstance Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstance element
ms.assetid: 2e77e9e1-9f2c-4df4-9aa6-5b7b911016a3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aef7afde2cf93d18ad0a567f5a5e1071b7e42ebf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177900"
---
# <a name="aggregationinstance-element-assl"></a>AggregationInstance-Element (ASSL)
  Definiert für eine Partition eine Aggregationsinstanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationInstances>  
   <AggregationInstance>  
      <AggregationType>...</AggregationType>  
      <AggregationID>...</AggregationID>  
      <Source>...</Source>  
      <Dimensions>...</Dimensions>  
      <Measures>...</Measures>  
      <Annotations>...</Annotations>  
   </AggregationInstance>  
</AggregationInstances>  
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
|Übergeordnete Elemente|[AggregationInstances](../collections/aggregationinstances-element-assl.md)|  
|Untergeordnete Elemente|[AggregationID](../properties/id-element-assl.md), [AggregationType](../properties/aggregationtype-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [Dimensions](../collections/dimensions-element-assl.md), [Measures](../collections/measures-element-assl.md), [Source](../properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine [Partition](partition-element-assl.md) -Element verwendet ein [AggregationDesign](aggregationdesign-element-assl.md) -Element zum Generieren von Aggregationen für diese Partition, jedes [Aggregation](aggregation-element-assl.md) in die `AggregationDesign` ist für diese Partition instanziiert. Mehrere Partitionen können den gleichen Aggregationsentwurf verwenden, um mehrere Instanzen einer definierten Aggregation zu generieren. Das `AggregationInstance`-Element stellt eine Instanz einer definierten Aggregation dar.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
