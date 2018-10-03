---
title: MembersWithDataCaption-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MembersWithDataCaption Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithDataCaption
helpviewer_keywords:
- MembersWithDataCaption element
ms.assetid: a5d59efd-5d67-485b-a360-67d54a1fe394
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 847a355f2517a5a630096e2617a27bdae396e565
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103900"
---
# <a name="memberswithdatacaption-element-assl"></a>MembersWithDataCaption-Element (ASSL)
  Stellt eine Vorlagenzeichenfolge bereit, die zum Erstellen von Beschriftungen für die vom System generierten Datenelemente verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributeTranslation> <!-- or DimensionAttribute -->  
   ...  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   ...  
</AttributeTranslation>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AttributeTranslation](../data-type/translation-data-type-assl.md), [DimensionAttribute-Objekt](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Den Wert des der `MembersWithDataCaption` Element wird nur von übergeordneten Attributen verwendet (in anderen Worten: der Wert der die [Nutzung](usage-element-dimensionattribute-assl.md) Element der `DimensionAttribute` übergeordnetes Element festgelegt ist, um *übergeordneten*) um zu bestimmen, die die Beschriftung der Datenelemente im übergeordneten Attribut. Weitere Informationen zu Datenelementen finden Sie unter [Attribute in über- und untergeordneten Hierarchien](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `MembersWithDataCaption` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.AttributeTranslation> und <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [MembersWithData-Element &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [AttributeTranslation-Datentyp &#40;ASSL&#41;](../data-type/translation-data-type-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
