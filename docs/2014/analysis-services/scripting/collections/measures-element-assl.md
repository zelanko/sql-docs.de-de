---
title: Measures-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Measures Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Measures
helpviewer_keywords:
- Measures element
ms.assetid: d2107112-f620-4fd7-a05f-bb2606b4be18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81dee5c883b8fb1f9e839a0e06e6dfd84925cdd1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177580"
---
# <a name="measures-element-assl"></a>Measures-Element (ASSL)
  Enthält die Auflistung der [Measure](../objects/measure-element-assl.md) Elemente, mit dem übergeordneten Element verknüpft sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MeasureGroup> <!-- or AggregationInstance, MeasureGroupBinding (out-of-line), PerspectiveMeasureGroup -->  
   ...  
   <Measures>  
      <Measure>...</Measure>  
   </Measures>  
   ...  
</MeasureGroup>  
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
|Übergeordnete Elemente|[AggregationInstance](../objects/aggregationinstance-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupBinding (Out-of-Line)](../data-type/measuregroupbinding-data-type-out-of-line-assl.md), [PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
|Untergeordnete Elemente|[Measure](../objects/measure-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die entsprechenden Elemente im Analysis Management Objects (AMO)-Objektmodell sind <xref:Microsoft.AnalysisServices.MeasureCollection> und <xref:Microsoft.AnalysisServices.PerspectiveMeasureCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
