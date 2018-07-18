---
title: Optionality-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 779a2e7f83cdd5c49d7a723c31d67224d987670f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34038664"
---
# <a name="optionality-element-assl"></a>Optionality-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt die Optionalität der Elemente für eine [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <Optionality>...</OPtionality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Obligatorisch*|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Obligatorisch*|Jedes Element im zugehörigen Attribut muss mindestens einem Element im Attribut zugeordnet werden, das über das **AttributeRelationship** -Element verfügt.|  
|*Optional*|Jedes Element im zugehörigen Attribut muss nicht mindestens einem Element im Attribut zugeordnet werden, das über das **AttributeRelationship** -Element verfügt.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **Kardinalität** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Optionality>.  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute und Attributhierarchien](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
