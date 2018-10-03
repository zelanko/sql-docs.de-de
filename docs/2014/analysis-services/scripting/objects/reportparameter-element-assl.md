---
title: ReportParameter-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportParameter
helpviewer_keywords:
- ReportParameter element
ms.assetid: 653a5c64-f1af-4796-bb7b-b44a40e52901
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fdc677b6aabd9d07275b977dd3d3af3145ea00a8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093460"
---
# <a name="reportparameter-element-assl"></a>ReportParameter-Element (ASSL)
  Enthält den Namen und Wert eines Parameters, der an eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Bericht zur Laufzeit.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ReportParameters>  
      <ReportParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportParameter>  
</ReportParameters>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[ReportParameters](../collections/reportparameters-element-assl.md)|  
|Untergeordnete Elemente|[Name](../properties/name-element-assl.md), [Value](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das `Value`-Element muss einen MDX-Ausdruck (Multidimensional Expressions) enthalten.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.ReportParameter>.  
  
## <a name="see-also"></a>Siehe auch  
 [ReportAction-Datentyp &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Action-Element &#40;ASSL&#41;](action-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
