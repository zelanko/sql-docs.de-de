---
title: NamingTemplateTranslation-Element (ASSL) | Microsoft Docs
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
- NamingTemplateTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslation
helpviewer_keywords:
- NamingTemplateTranslation element
ms.assetid: 4a97a31d-23bc-4afd-a4dc-bc0ad7121f08
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dc6c6689f4028c0983267a38435c76e7258768a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149146"
---
# <a name="namingtemplatetranslation-element-assl"></a>NamingTemplateTranslation-Element (ASSL)
  Stellt eine lokalisierte Übersetzung der [NamingTemplate](../properties/namingtemplate-element-assl.md) -Element eines übergeordneten [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) -Datentyp.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[Übersetzung](translation-element-assl.md)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Namingtemplatetranslation](../collections/translations-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Den Wert des der `NamingTemplateTranslation` Element wird nur von übergeordneten Attributen verwendet (also der Wert der die [Verwendung](../properties/usage-element-dimensionattribute-assl.md) Element des der `DimensionAttribute` auf Parent festgelegt ist *übergeordneten*) zum Speichern von lokalisierten Version Übersetzung der `NamingTemplate` Wert für eine bestimmte Sprache.  
  
 Das Element, das das übergeordnete Element des entspricht `NamingTemplateTranslations` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [NamingTemplate-Element &#40;ASSL&#41;](../properties/namingtemplate-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  