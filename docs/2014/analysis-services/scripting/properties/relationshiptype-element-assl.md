---
title: RelationshipType-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RelationshipType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RelationshipType
helpviewer_keywords:
- RelationshipType element
ms.assetid: 72e1ab0e-a95d-4ebe-857d-21de1bf9fe03
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3cc0ca0577b63e655c42c9b8bdcb19b1a67cb538
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096710"
---
# <a name="relationshiptype-element-assl"></a>RelationshipType-Element (ASSL)
  Gibt an, ob die elementbeziehungen für eine [AttributeRelationship](../objects/attributerelationship-element-assl.md) kann geändert werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <RelationshipType>...</RelationshipType>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Flexible*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[AttributeRelationship](../objects/attributerelationship-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Fest*|Die Elementbeziehungen zwischen einem Attribut und einem zugehörigen Attribut können nicht geändert werden.|  
|*Flexible*|Die Elementbeziehungen zwischen einem Attribut und einem zugehörigen Attribut können geändert werden.|  
  
 Z. B. wenn `ZipCode` kann nicht geändert werden von einem `City` in eine andere Beziehung aus `ZipCode` zu `City` als RuntimeCompatibility *fest*.  
  
 Die Enumeration, die den zulässigen Werten für entspricht `RelationshipType` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.RelationshipType>.  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute und Attributhierarchien](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
