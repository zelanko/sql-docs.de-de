---
title: NamingTemplateTranslation-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 224bf07113e5e67e4ce5ab4bb94179a55ed3da87
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="namingtemplatetranslation-element-assl"></a>NamingTemplateTranslation-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Stellt eine lokalisierte Übersetzung der [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md) -Element eines übergeordneten [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md) -Datentyp.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|[Übersetzung](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Namingtemplatetranslation](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Den Wert des der **NamingTemplateTranslation** Element wird nur von übergeordneten Attributen verwendet (also der Wert der der [Verwendung](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) Element von der **DimensionAttribute** übergeordnete festgelegt ist, um *übergeordneten*) zum Speichern der lokalisierten Übersetzung der **NamingTemplate** Wert für eine bestimmte Sprache.  
  
 Das Element, das das übergeordnete Element des entspricht **Namingtemplatetranslation** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [NamingTemplate-Element &#40;ASSL&#41;](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)   
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
