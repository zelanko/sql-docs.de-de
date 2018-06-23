---
title: Annotations-Element (ASSL) | Microsoft Docs
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
- Annotations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Annotations
helpviewer_keywords:
- Annotations element
ms.assetid: b2236075-6a48-470d-8182-b0de112e258a
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b673e7f9edd199d32f7bd89d082d39b6d58f876a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148190"
---
# <a name="annotations-element-assl"></a>Annotations-Element (ASSL)
  Enthält die Auflistung der [Anmerkung](../objects/annotation-element-assl.md) Elemente mit dem übergeordneten Element verknüpft sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Account>  
<!-- or another object in the Analysis Services Scripting Language -->  
   ...  
   <Annotations>  
      <Annotation>...</Annotation>  
   </Annotations>  
   ...  
</Account>  
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
|Übergeordnete Elemente|Die meisten Objekte in der Analysis Services Scripting Language|  
|Untergeordnete Elemente|[Anmerkung](../objects/annotation-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.AnnotationCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  