---
title: Namingtemplatetranslation-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NamingTemplateTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslations
helpviewer_keywords:
- NamingTemplateTranslations element
ms.assetid: fde65778-1fa3-490a-9874-8bf2052ef25c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b1c7accfde72c3e64b3845f720c33fce5b55711e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099401"
---
# <a name="namingtemplatetranslations-element-assl"></a>NamingTemplateTranslation-Element (ASSL)
  Stellt eine Auflistung lokalisierter Übersetzungen für das [NamingTemplate](../properties/namingtemplate-element-assl.md) -Element des übergeordneten Elements, [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), bereit.  
  
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
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Attribute](../objects/attribute-element-assl.md) des Typs [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|[NamingTemplateTranslation](../objects/translation-element-assl.md) vom Typ [Translation](translations-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des der `NamingTemplateTranslation` Element wird nur von übergeordneten Attributen verwendet (in anderen Worten: der Wert der die [Nutzung](../properties/usage-element-dimensionattribute-assl.md) -Element des übergeordneten `DimensionAttribute` nastaven NA hodnotu *übergeordneten*.)  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
