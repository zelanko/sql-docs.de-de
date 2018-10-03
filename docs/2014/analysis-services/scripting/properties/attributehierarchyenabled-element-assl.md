---
title: AttributeHierarchyEnabled-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeHierarchyEnabled Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeHierarchyEnabled
helpviewer_keywords:
- AttributeHierarchyEnabled element
ms.assetid: 1e95307f-530e-4e98-a0e1-2b0462d330a3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: adcb11beda15b6ab4fc27357cb52134cb53b501b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079330"
---
# <a name="attributehierarchyenabled-element-assl"></a>AttributeHierarchyEnabled-Element (ASSL)
  Bestimmt, ob eine Attributhierarchie für das Attribut aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute><!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|`True`|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md), [DimensionAttribute-Objekt](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `AttributeHierarchyEnabled` -Element bestimmt, ob eine Attributhierarchie von generierten [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] für das Attribut. Wird die Attributhierarchie nicht aktiviert, kann weder das Attribut in einer benutzerdefinierten Hierarchie verwendet werden, noch kann in MDX-Anweisungen (Multidimensional Expressions) auf die Attributhierarchie verwiesen werden.  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `AttributeHierarchyEnabled` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.CubeAttribute> und <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [AttributeHierarchyVisible-Element &#40;ASSL&#41;](visible-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
