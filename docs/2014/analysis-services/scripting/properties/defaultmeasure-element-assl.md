---
title: DefaultMeasure-Element (ASSL) | Microsoft Docs
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
- DefaultMeasure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultMeasure
helpviewer_keywords:
- DefaultMeasure element
ms.assetid: ceac8b3d-ebae-463f-9e8c-506281d42792
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 72585d3d1bbce32fd3af4bedbf60e660f8b197f5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056790"
---
# <a name="defaultmeasure-element-assl"></a>DefaultMeasure-Element (ASSL)
  Enthält einen Multidimensional Expressions (MDX)-Ausdruck, der das Standardmeasure für definiert eine [Cube](../objects/cube-element-assl.md) oder [Perspektive](../objects/perspective-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Cube> <!-- or Perspective -->  
   ...  
   <DefaultMeasure>...</DefaultMeasure>  
   ...  
</Cube>  
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
|Übergeordnetes Element|[Cube](../objects/cube-element-assl.md), [Perspektive](../objects/perspective-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen `DefaultMeasure` im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.Cube> und <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  