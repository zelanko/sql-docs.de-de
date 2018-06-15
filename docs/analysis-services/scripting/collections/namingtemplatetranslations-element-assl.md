---
title: Namingtemplatetranslation-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9fb5f592afa70595eb92ef5905512bad730819bd
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029301"
---
# <a name="namingtemplatetranslations-element-assl"></a>NamingTemplateTranslation-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Stellt eine Auflistung lokalisierter Übersetzungen für das [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md) -Element des übergeordneten Elements, [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), bereit.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Attribute xsi:type="DimensionAttribute">  
   ...  
   <NamingTemplateTranslations>  
            <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
...</NamingTemplateTranslations>  
   ...  
</Attribute>  
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
|Übergeordnete Elemente|[Attribute](../../../analysis-services/scripting/objects/attribute-element-assl.md) des Typs [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|[NamingTemplateTranslation](../../../analysis-services/scripting/objects/namingtemplatetranslation-element-assl.md) vom Typ [Translation](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des **NamingTemplateTranslation** -Elements wird nur für übergeordnete Attribute verwendet (mit anderen Worten, der Wert des [Usage](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) -Elements für das übergeordnete **DimensionAttribute** -Element wird auf *Parent*festgelegt).  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
