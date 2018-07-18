---
title: HideMemberIf-Element (ASSL) | Microsoft Docs
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
- HideMemberIf Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- HideMemberIf
helpviewer_keywords:
- HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2b1540a3b7f5d1e1a93ea3b4628bfbde186e5bb2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059436"
---
# <a name="hidememberif-element-assl"></a>HideMemberIf-Element (ASSL)
  Gibt an, ob und wann ein Element auf einer Ebene aus Clientanwendungen ausgeblendet werden sollte.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Nie*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Level](../objects/level-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Nie*|Elemente werden nie ausgeblendet.|  
|*OnlyChildWithNoName*|Ein Element wird ausgeblendet, wenn es das einzige untergeordnete Element seines übergeordneten Elements ist und sein Name leer ist.|  
|*OnlyChildWithParentName*|Ein Element wird ausgeblendet, wenn es das einzige untergeordnete Element seines übergeordneten Elements ist und identisch mit seinem übergeordneten Element ist.|  
|*NoName*|Ein Element wird ausgeblendet, wenn sein Name leer ist.|  
|*ParentName*|Ein Element wird ausgeblendet, wenn sein Name dem seines übergeordneten Elements entspricht.|  
  
## <a name="remarks"></a>Hinweise  
 Die Enumeration, die den zulässigen Werten für entspricht `HideMemberIf` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  