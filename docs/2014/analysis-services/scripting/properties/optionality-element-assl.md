---
title: Optionality-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Optionality Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Optionality element
ms.assetid: 6cd2ef0a-6fbe-4462-ab27-4cdfeb33f8ab
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fe204e2b8eed7b5629b9c6d6060295383371aa48
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159361"
---
# <a name="optionality-element-assl"></a>Optionality-Element (ASSL)
  Gibt die Optionalität der Elemente für ein [AttributeRelationship](../objects/attributerelationship-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <Optionality>...</OPtionality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Obligatorisch*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[AttributeRelationship](../objects/attributerelationship-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Obligatorisch*|Jedes Element im zugehörigen Attribut muss mindestens ein Element im Attribut zugeordnet werden, das die `AttributeRelationship` Element.|  
|*Optional*|Jedes Element im zugehörigen Attribut muss nicht mindestens einem Element im Attribut zugeordnet werden, das über das `AttributeRelationship`-Element verfügt.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `Cardinality` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Optionality>.  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute und Attributhierarchien](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
