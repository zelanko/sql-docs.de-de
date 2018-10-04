---
title: Condition-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Condition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- condition
helpviewer_keywords:
- Condition element
ms.assetid: 9c3cb31c-4aa1-49e4-aeb2-6cab54db0be3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9fa61c470eaf39edc883aac73707e86c21a9e24c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227920"
---
# <a name="condition-element-assl"></a>Condition-Element (ASSL)
  Enthält einen Multidimensional Expressions (MDX)-Ausdruck, der bestimmt, ob die [Aktion](../objects/action-element-assl.md) übergeordnetes Element für das Ziel gilt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action>  
   ...  
   <Condition>...</Condition  
      ...  
</Action>  
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
|Übergeordnetes Element|[Aktion](../objects/action-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das `Condition`-Element enthält einen MDX-Ausdruck, der einen booleschen Wert ergibt. Wenn der Ausdruck zurückgibt `True`, und klicken Sie dann die `Action` gilt für die im angegebenen Ziel die [Ziel](target-element-assl.md) Element. Andernfalls die `Action` ist nicht anwendbar.  
  
 Das Element, das dem übergeordneten entspricht `Condition` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
