---
title: FontName-Element (ASSL) | Microsoft-Dokumentation
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
- FontName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FontName
helpviewer_keywords:
- FontName element
ms.assetid: 5560a852-9745-4abb-93d8-9cebe8a9897c
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d1b179415e7b64c4d64090df6168fcc492ab1c30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289526"
---
# <a name="fontname-element-assl"></a>FontName-Element (ASSL)
  Beschreibt schriftartbezogene Anzeigeeigenschaften der [CalculationProperty](../objects/calculationproperty-element-assl.md) oder [Measure](../objects/measure-element-assl.md) übergeordneten Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FontName>...</FontName>  
   ...  
</CalculationProperty>  
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
|Übergeordnete Elemente|[CalculationProperty](../objects/calculationproperty-element-assl.md), [Measure](../objects/measure-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `FontName` -Eigenschaft enthält einen Ausdruck für MDX (Multidimensional Expressions) und gilt für `CalculationProperty` Elemente mit einem [CalculationType](calculationtype-element-assl.md) von *Member* oder *Zellen* .  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `FontName` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.CalculationProperty> und <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Siehe auch  
 [CalculationProperties-Element &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript-Element &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts-Element &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
