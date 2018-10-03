---
title: Key-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1532db273c83f16678d278f068befefcd8df4b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101280"
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
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Schlüssel](keys-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
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
  
  
