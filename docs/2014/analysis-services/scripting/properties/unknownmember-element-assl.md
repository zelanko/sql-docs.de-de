---
title: UnknownMember-Element (ASSL) | Microsoft Docs
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
- UnknownMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- UnknownMember
helpviewer_keywords:
- UnknownMember element
ms.assetid: 5558961e-e3c6-4f4e-817d-5b12b0734c03
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 85bc7a517642ccc5b4386f65e7b4a9c89d757ce6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049779"
---
# <a name="unknownmember-element-assl"></a>UnknownMember-Element (ASSL)
  Gibt an, ob das unbekannte Element sichtbar ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMember>...</UnknownMember>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Keine*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Dimension](../objects/dimension-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Sichtbar*|Das unbekannte Element ist vorhanden und wird angezeigt.|  
|*Ausgeblendet*|Das unbekannte Element ist vorhanden, aber wird nicht angezeigt.|  
|*Keine*|Das unbekannte Element wird nicht verwendet.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `UnknownMember` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.UnknownMemberBehavior>.  
  
## <a name="see-also"></a>Siehe auch  
 [UnknownMemberName-Element &#40;ASSL&#41;](name-element-assl.md)   
 [UnknownMemberTranslation-Element &#40;ASSL&#41;](../objects/translation-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  