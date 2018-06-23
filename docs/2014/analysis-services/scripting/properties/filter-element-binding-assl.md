---
title: Filter-Element (Binding) (ASSL) | Microsoft Docs
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
- Filter Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- filter
helpviewer_keywords:
- Filter element
ms.assetid: 3d4cd169-2903-4266-8541-540ece424b7b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 659719ea4ba87b548b08b5b7cb680e1b28b563d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161001"
---
# <a name="filter-element-binding-assl"></a>Filter-Element (Binding) (ASSL)
  Enthält einen MDX-Ausdruck (Multidimensional Expression), der die Inhalte des übergeordneten Elements filtert.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubeDimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Filter>...</Filter>  
   ...  
</CubeDimensionBinding>  
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
|Übergeordnete Elemente|[CubeDimensionBinding](../data-type/binding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu den `Binding` Typs, einschließlich der Tabellen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Objekte Scripting Language (ASSL) der `Binding` Typ und der Vererbungshierarchie der `Binding` , finden Sie unter [Binding-Datentyp &#40;ASSL &#41;](../data-type/binding-data-type-assl.md).  
  
 Einen Überblick über datenbindungen in ASSL finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `Filter` im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.CubeDimensionBinding> und <xref:Microsoft.AnalysisServices.MeasureGroupBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Binding-Datentyp &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Datenquellen und-Bindungen &#40;SSAS – mehrdimensional&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  