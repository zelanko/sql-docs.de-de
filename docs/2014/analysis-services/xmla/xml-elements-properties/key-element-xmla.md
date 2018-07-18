---
title: Key-Element (XMLA) | Microsoft-Dokumentation
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
- Key Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Key
- urn:schemas-microsoft-com:xml-analysis#Key
- microsoft.xml.analysis.key
helpviewer_keywords:
- Key element
ms.assetid: 09d3cd48-49f7-4b58-b8bb-ca75b81bb02f
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1f98ae6863f0aab25149ee4f8a69ef13b65da974
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213760"
---
# <a name="key-element-xmla"></a>Key-Element (XMLA)
  Enthält einen Elementschlüsselwert für ein Attributelement.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Keys>  
   ...  
   <Key>...</Key>  
   ...  
</Keys>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Any|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Schlüssel](keys-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der von diesem Element verwendete Datentyp sollte dem Datentyp der jeweiligen Schlüsselspalte für das angegebene Attribut entsprechen. Wenn `Key` Elemente sind nicht für ein übergeordnetes Element angegeben `Attribute` -Element, das `AttributeName` und `Name` im übergeordneten Element angegebenen Elemente `Attribute` Element werden verwendet, um das Attributelement geändert werden, zu identifizieren.  
  
## <a name="see-also"></a>Siehe auch  
 [-Attribut des Elements &#40;XMLA&#41;](attribute-element-xmla.md)   
 [AttributeName-Element &#40;XMLA&#41;](name-element-xmla.md)   
 [Drop-Element &#40;XMLA&#41;](../xml-elements-commands/drop-element-xmla.md)   
 [INSERT-Element &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [KeyColumn-Element &#40;ASSL&#41;](../../scripting/objects/column-element-assl.md)   
 [Update-Element &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [In dem Element &#40;XMLA&#41;](where-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
