---
title: AttributeAllMemberTranslations-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e3ee9a3a2eb584a51ffeafb885ef6c0f2f8b3f7b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030831"
---
# <a name="attributeallmembertranslations-element-assl"></a>AttributeAllMemberTranslations-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält die Auflistung von Übersetzungen für die Beschriftung des "Alle"-Elements der Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Dimension>  
   ...  
   <AttributeAllMemberTranslations>  
      <AttributeAllMemberTranslation xsi:type="Translation">...</AttributeAllMemberTranslation>  
   </AttributeAllMemberTranslations>  
      ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Untergeordnete Elemente|[AttributeAllMemberTranslation](../../../analysis-services/scripting/objects/attributeallmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das das übergeordnete Element des entspricht **AttributeAllMemberTranslations** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Translation-Element &#40;ASSL&#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
