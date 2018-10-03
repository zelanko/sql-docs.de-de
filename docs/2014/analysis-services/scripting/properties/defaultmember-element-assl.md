---
title: DefaultMember-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DefaultMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultMember
helpviewer_keywords:
- DefaultMember element
ms.assetid: db4eea9f-f7cf-40de-abd0-b62014e7ec2d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c90abe48fc1d3bfa099e39234d22df822a03782
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055295"
---
# <a name="defaultmember-element-assl"></a>DefaultMember-Element (ASSL)
  Enthält einen MDX-Ausdruck (Multidimensional Expression), der das Standardelement des übergeordneten Elements definiert.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributePermission> <!-- or DimensionAttribute, ManyToManyMeasureGroupDimension, PerspectiveAttribute -->  
      ...  
   <DefaultMember>...</DefaultMember>  
      ...  
</AttributePermission>  
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
|Übergeordnetes Element|[AttributePermission](../objects/attributepermission-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md), [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `DefaultMember` -Element definiert das Standardelement für das übergeordnete Element. Wenn `DefaultMember` ist nicht angegeben oder auf eine leere Zeichenfolge festgelegt ist [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] wählt ein Element, das als Standardelement verwendet.  
  
 Für `ManyToManyMeasureGroupDimension` Elemente, die `DefaultMember` Element enthält einen MDX-Ausdruck, der angibt, ein Element in der Dimension identifiziert, die der `CubeDimensionID` Element der `ManyToManyMeasureGroupDimension`. Der MDX-Ausdruck ähnelt der [StrToMember](/sql/mdx/strtomember-mdx) MDX-Funktion mit dem Schlüsselwort CONSTRAINED, da sie MDX oder benutzerdefinierten Funktionen enthalten kann.  
  
 Weitere Informationen zu Standardelementen finden Sie unter [Definieren eines Standardelements](../../multidimensional-models/attribute-properties-define-a-default-member.md).  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `DefaultMember` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.AttributePermission>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, und <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
