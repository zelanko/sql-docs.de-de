---
title: Translations-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Translations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.translations
- urn:schemas-microsoft-com:xml-analysis#Translations
- http://schemas.microsoft.com/analysisservices/2003/engine#Translations
helpviewer_keywords:
- Translations element
ms.assetid: 86fd2119-9bea-4306-829e-cc439da05566
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f216a564f715efbbaa2af2f094d1e4181f8bdbe9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126750"
---
# <a name="translations-element-xmla"></a>Translations-Element (XMLA)
  Enthält eine Auflistung von [Translation](translation-element-xmla.md) -Elementen, die verwendet werden, um die Elementschlüssel der Attributelemente zu identifizieren, die vom übergeordneten [Attribute](attribute-element-xmla.md) -Element dargestellt werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Attribute>  
   ...  
   <Translations>  
      <Translation>...</Translation>  
   </Translations>  
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
|Übergeordnete Elemente|[Attribut](attribute-element-xmla.md)|  
|Untergeordnete Elemente|[Übersetzung](translation-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [INSERT-Element &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Update-Element &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
