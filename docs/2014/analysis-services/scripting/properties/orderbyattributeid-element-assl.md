---
title: OrderByAttributeID-Element (ASSL) | Microsoft Docs
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
- OrderByAttributeID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- OrderByAttributeID
helpviewer_keywords:
- OrderByAttributeID element
ms.assetid: 41d7b650-ac40-4f1a-850d-2f81a19b28cb
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 42d8e9246340b72fad871e92bc30008c68ce786a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150208"
---
# <a name="orderbyattributeid-element-assl"></a>OrderByAttributeID-Element (ASSL)
  Identifiziert ein anderes Attribut, um die Elemente eines bestellen der [Dimension](../data-type/dimensionattribute-data-type-assl.md) Attribut.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderByAttributeID>...</OrderByAttributeID>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `OrderByAttributeID` Element wird nur verwendet, wenn der Wert von der [OrderBy](orderby-element-assl.md) -Element für die `DimensionAttribute` auf festgelegt ist *AttributeKey* oder *AttributeName*.  
  
 Das Element, das das übergeordnete Element des entspricht `OrderByAttributeID` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  