---
title: Events-Element (ASSL) | Microsoft-Dokumentation
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
- Events Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Events
helpviewer_keywords:
- Events element
ms.assetid: de887998-dc4b-44dc-8fec-08d67b92f96d
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 33f6d302557369d7cbc90c1d5786bc21d37b0f42
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293500"
---
# <a name="events-element-assl"></a>Events-Element (ASSL)
  Definiert die Auflistung der [Event](../objects/event-element-assl.md) -Elemente, die von einem [Trace](../objects/trace-element-assl.md)-Element erfasst werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Trace>  
   ...  
   <Events>  
      <Event>...</Event>  
   </Events>  
   ...  
</Trace>  
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
|Übergeordnetes Element|[Ablaufverfolgung](../objects/trace-element-assl.md)|  
|Untergeordnete Elemente|[Ereignis](../objects/event-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.TraceEventCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Führt eine Ablaufverfolgung für Element &#40;ASSL&#41;](traces-element-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
