---
title: AssociatedMeasureGroupID-Element (ASSL) | Microsoft-Dokumentation
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
- AssociatedMeasureGroupID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AssociatedMeasureGroupID
helpviewer_keywords:
- AssociatedMeasureGroupID element
ms.assetid: a18ff25b-00a2-4ddf-abcc-ef4d52c8a462
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad28fbc5023c06bdc260e301732bfb1567ce27f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155331"
---
# <a name="associatedmeasuregroupid-element-assl"></a>AssociatedMeasureGroupID-Element (ASSL)
  Enthält die ID des der [MeasureGroup](../objects/group-element-assl.md) zugeordnete Element eine [CalculationProperty](../objects/calculationproperty-element-assl.md) Element oder ein [Kpi](../objects/kpi-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CalculationProperty> <!-- or Kpi -->  
   ...  
   <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
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
|Übergeordnetes Element|[CalculationProperty](../objects/calculationproperty-element-assl.md), [Kpi](../objects/kpi-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Bei Anwendung auf `CalculationProperty` Elemente, die `AssociatedMeasureGroupID` Eigenschaft gilt für Elemente mit einem [CalculationType](calculationtype-element-assl.md) von *Member*.  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `AssociatedMeasureGroupID` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.CalculationProperty> und <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>Siehe auch  
 [CalculationProperties-Element &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript-Element &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts-Element &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
