---
title: AggregationDimension-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDimension
helpviewer_keywords:
- AggregationDimension data type
ms.assetid: 697e0e09-3210-4a56-882f-80726abc4c68
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 325c6bf84127c060be132ce44107220077e215c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094996"
---
# <a name="aggregationdimension-data-type-assl"></a>AggregationDimension-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der die Beziehung zwischen einer Dimension darstellt und ein [Aggregation](../objects/aggregation-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Attributes>...</Attributes>  
      <Annotations>...</Annotations>  
</AggregationDimension>  
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
|Abgeleitete Elemente|[Dimension](../objects/dimension-element-assl.md) ([Dimensionen](../collections/dimensions-element-assl.md) Auflistung von [Aggregation](../objects/aggregation-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist [AggregationDimension](dimension-data-type-assl.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
