---
title: AllMemberTranslations-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AllMemberTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllMemberTranslations
helpviewer_keywords:
- AllMemberTranslations element
ms.assetid: 982ee2bf-c88d-4da5-a679-7a6b08a48a0d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0fbb23d215ee8808bae2ad5255447b6384fa7a96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075270"
---
# <a name="allmembertranslations-element-assl"></a>AllMemberTranslations-Element (ASSL)
  Enthält die Auflistung der [Übersetzung](../objects/translation-element-assl.md) Elemente für die Beschriftung des alle-Elements ein [Hierarchie](../objects/hierarchy-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Hierarchy>  
   ...  
   <AllMemberTranslations>  
      <AllMemberTranslation xsi:type="Translation">...  
            </AllMemberTranslation>  
   </AllMemberTranslations>  
      ...  
</Hierarchy>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine (Auflistung)|  
|Standardwert|Keine (Auflistung)|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Hierarchy](../objects/hierarchy-element-assl.md)|  
|Untergeordnete Elemente|[AllMemberTranslation](../objects/allmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `AllMemberTranslations` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Siehe auch  
 [Translation-Element &#40;ASSL&#41;](../objects/translation-element-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
