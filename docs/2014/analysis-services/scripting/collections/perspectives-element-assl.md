---
title: Perspectives-Element (ASSL) | Microsoft Docs
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
- Perspectives Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Perspectives
helpviewer_keywords:
- Perspectives element
ms.assetid: d071acc3-469b-44f3-b724-423a48da2d41
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8df6386c14d3c7219826e7df156b6343a92fc1f7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147992"
---
# <a name="perspectives-element-assl"></a>Perspectives-Element (ASSL)
  Enthält die Auflistung der [Perspektive](../objects/perspective-element-assl.md) Elemente, die zu einem [Cube](../objects/cube-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Cube>  
   ...  
   <Perspectives>  
      <Perspective>...</Pespective>  
   </Perspectives>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Cube](../objects/cube-element-assl.md)|  
|Untergeordnete Elemente|[Perspektive](../objects/perspective-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.PerspectiveCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  