---
title: MembersWithDataCaption-Element (ASSL) | Microsoft Docs
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
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ef845a4c77a66ad1c59a0bdad527856a86849de9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058999"
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
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AttributeTranslation](../data-type/translation-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Den Wert des der `MembersWithDataCaption` Element wird nur von übergeordneten Attributen verwendet (in anderen Worten: der Wert der die [Verwendung](usage-element-dimensionattribute-assl.md) Element des der `DimensionAttribute` übergeordnetes Element festgelegt ist, um *übergeordneten*) um zu bestimmen, die die Beschriftung der Datenelemente im übergeordneten Attribut. Weitere Informationen zu Datenelementen finden Sie unter [Attribute in über- und untergeordneten Hierarchien](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `MembersWithDataCaption` im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.AttributeTranslation> und <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [MembersWithData-Element &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [AttributeTranslation-Datentyp &#40;ASSL&#41;](../data-type/translation-data-type-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  