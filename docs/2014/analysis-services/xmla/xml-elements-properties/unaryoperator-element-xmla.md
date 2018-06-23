---
title: UnaryOperator-Element (XMLA) | Microsoft Docs
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
- UnaryOperator Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#UnaryOperator
- urn:schemas-microsoft-com:xml-analysis#UnaryOperator
- microsoft.xml.analysis.unaryoperator
helpviewer_keywords:
- UnaryOperator element
ms.assetid: 4dc9cfbe-6f8b-42bc-8d3a-42f48ca5d299
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: c4e40b91c8d8f3d533362e3d938d99c351ae4f8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060120"
---
# <a name="unaryoperator-element-xmla"></a>UnaryOperator-Element (XMLA)
  Enthält den unäroperator für ein Attributelement, das durch das übergeordnete Element dargestellten [Attribut](attribute-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Attribute>  
   ...  
   <UnaryOperator>...</UnaryOperator>  
   ...  
</Attribute>  
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
|Übergeordnete Elemente|[Attribut](attribute-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `UnaryOperator` Element enthält einen Multidimensional Expressions (MDX)-Ausdruck, den unäre Operator für das Attributelement, das vom übergeordneten Element definiert definiert `Attribute` Element.  
  
 Weitere Informationen zu MDX-Ausdrücken finden Sie unter [Ausdrücke &#40;MDX&#41;](/sql/mdx/expressions-mdx).  
  
## <a name="see-also"></a>Siehe auch  
 [INSERT-Element &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Update-Element &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
