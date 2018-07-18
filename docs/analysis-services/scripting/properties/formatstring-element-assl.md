---
title: FormatString-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 64722c5e95a9de813d4634dd3ca5ded7434e9e05
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031831"
---
# <a name="formatstring-element-assl"></a>FormatString-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt das Anzeigeformat für ein [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) Element oder ein [Measure](../../../analysis-services/scripting/objects/measure-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FormatString>...</FormatString>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [Measure](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die **FormatString** -Eigenschaft enthält einen MDX-Ausdruck (Multidimensional Expressions). Im Fall von **CalculationProperty** -Elementen gilt dies für Elemente mit einem [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) von *Member* oder *Zellen*.  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen **"FormatString"** im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.CalculationProperty> und <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Siehe auch  
 [CalculationProperties-Element &#40;ASSL&#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript-Element &#40;ASSL&#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts-Element &#40;ASSL&#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
