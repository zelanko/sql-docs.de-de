---
title: CaptionIsMdx-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 44f599046ce0d78a83626f0ef732bf8ded50f9d2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34033061"
---
# <a name="captionismdx-element-assl"></a>CaptionIsMdx-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert, ob die Beschriftung für die [Aktion](../../../analysis-services/scripting/objects/action-element-assl.md) Element ist ein Ausdruck (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action>  
   ...  
   <CaptionIsMdx>...</CaptionIsMdx>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|**False**|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Aktion](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das das übergeordnete Element des entspricht **CaptionIsMdx** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
