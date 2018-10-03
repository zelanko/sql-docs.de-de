---
title: AllMemberName-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AllMemberName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllMemberName
helpviewer_keywords:
- AllMemberName element
ms.assetid: 5fda5563-cb7a-4402-82ad-3d6c432b6a7e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b5a9e16de5a541b9d95cb50c0e2585f6f29ab3ba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139540"
---
# <a name="allmembername-element-assl"></a>AllMemberName-Element (ASSL)
  Enthält die Beschriftung in der Standardsprache für alle-Elements ein [Hierarchie](../objects/hierarchy-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Hierarchy>  
      ...  
      <AllMemberName>...</AllMemberName>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Hierarchy](../objects/hierarchy-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `AllMemberName` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
