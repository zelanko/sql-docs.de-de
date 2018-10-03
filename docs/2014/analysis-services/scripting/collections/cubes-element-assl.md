---
title: Cubes-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cubes Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Cubes
helpviewer_keywords:
- Cubes element
ms.assetid: 0eaaaf3f-0c78-4eb4-bc3a-d266579eca56
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f289951caa8357c1fe5f63162636e3dee9999de3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222060"
---
# <a name="cubes-element-assl"></a>Cubes-Element (ASSL)
  Enthält die Auflistung der [Cube](../objects/cube-element-assl.md) Elemente, die zu einem [Datenbank](../objects/database-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Database>  
   ...  
   <Cubes>  
            <Cube>...</Cube>  
   </Cubes>  
      ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Datenbank](../objects/database-element-assl.md)|  
|Untergeordnete Elemente|[Cube](../objects/cube-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.CubeCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
