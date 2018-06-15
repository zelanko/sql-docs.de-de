---
title: OrderByAttributeID-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e6ab7a00961d4e5b925556d107eec32b7ddb9c9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34038044"
---
# <a name="orderbyattributeid-element-assl"></a>OrderByAttributeID-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifiziert ein anderes Attribut, um die Elemente eines bestellen der [Dimension](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md) Attribut.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderByAttributeID>...</OrderByAttributeID>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die **OrderByAttributeID** Element wird nur verwendet, wenn der Wert von der [OrderBy](../../../analysis-services/scripting/properties/orderby-element-assl.md) -Element für die **DimensionAttribute** auf festgelegt ist *AttributeKey* oder *AttributeName*.  
  
 Das Element, das das übergeordnete Element des entspricht **OrderByAttributeID** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
