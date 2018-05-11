---
title: HideMemberIf-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0e01cbbf403636bf42a806ba516f9947eaab20e4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="hidememberif-element-assl"></a>HideMemberIf-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Nie*|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Ebene](../../../analysis-services/scripting/objects/level-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Nie*|Elemente werden nie ausgeblendet.|  
|*OnlyChildWithNoName*|Ein Element wird ausgeblendet, wenn es das einzige untergeordnete Element seines übergeordneten Elements ist und sein Name leer ist.|  
|*OnlyChildWithParentName*|Ein Element wird ausgeblendet, wenn es das einzige untergeordnete Element seines übergeordneten Elements ist und identisch mit seinem übergeordneten Element ist.|  
|*NoName*|Ein Element wird ausgeblendet, wenn sein Name leer ist.|  
|*ParentName*|Ein Element wird ausgeblendet, wenn sein Name dem seines übergeordneten Elements entspricht.|  
  
## <a name="remarks"></a>Hinweise  
 Die Enumeration, die den zulässigen Werten für entspricht **HideMemberIf** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
