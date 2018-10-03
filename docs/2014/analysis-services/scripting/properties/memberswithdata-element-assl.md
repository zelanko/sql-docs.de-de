---
title: MembersWithData-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MembersWithData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithData
helpviewer_keywords:
- MembersWithData element
ms.assetid: 845087a2-b12d-4344-a8be-85ca61155296
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17a3fced7327c1fb2211b1c80f774ae859757952
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089645"
---
# <a name="memberswithdata-element-assl"></a>MembersWithData-Element (ASSL)
  Bestimmt, ob Nichtblatt-Datenelemente im übergeordneten Attribut angezeigt werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <MembersWithData>...</MembersWithData>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*NonLeafDataVisible*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DimensionAttribute-Objekt](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Den Wert des der `MembersWithData` Element wird nur von übergeordneten Attributen verwendet (in anderen Worten: der Wert der die [Nutzung](usage-element-dimensionattribute-assl.md) Element der `DimensionAttribute` übergeordnetes Element festgelegt ist, um *übergeordneten*) um zu bestimmen, ob um Datenelemente für nichtblatt-Datenelemente im übergeordneten Attribut angezeigt. Weitere Informationen zu Datenelementen finden Sie unter [Attribute in über- und untergeordneten Hierarchien](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*NonLeafDataHidden*|Nichtblattdaten werden ausgeblendet.|  
|*NonLeafDataVisible*|Nichtblattdaten sind sichtbar.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `MembersWithData` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MembersWithData>.  
  
## <a name="see-also"></a>Siehe auch  
 [MembersWithDataCaption-Element &#40;ASSL&#41;](caption-element-assl.md)   
 [DimensionAttribute-Datentyp &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
