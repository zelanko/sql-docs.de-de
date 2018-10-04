---
title: AggregationDesignDimension-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationDesignDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesignDimension
helpviewer_keywords:
- AggregationDesignDimension data type
ms.assetid: 06a0d418-014c-4f40-a63a-5cfeee3f6a41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 758fc3a42b2ff1277deda1e7cff566b9eba17a26
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200410"
---
# <a name="aggregationdesigndimension-data-type-assl"></a>AggregationDesignDimension-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der die Beziehung zwischen einer Cubedimension darstellt und ein [AggregationDesign](../objects/aggregationdesign-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationDesignDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Attributes>...</Attributes>  
      <Annotations>...</Annotations>  
</AggregationDesignDimension>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [Attribute](../collections/attributes-element-assl.md), [CubeDimensionID](../properties/id-element-assl.md)|  
|Abgeleitete Elemente|[Dimension](../objects/dimension-element-assl.md) ([Dimensionen](../collections/dimensions-element-assl.md) Auflistung von [AggregationDesign](../objects/aggregationdesign-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.AggregationDesignDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [AggregationDesign-Element &#40;ASSL&#41;](../objects/aggregationdesign-element-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
