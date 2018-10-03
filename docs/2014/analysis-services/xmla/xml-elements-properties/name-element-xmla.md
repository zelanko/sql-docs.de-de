---
title: Benennen Sie-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 422bd152e82a471ce0f130a26aaa12a56026419a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48127900"
---
# <a name="name-element-xmla"></a>Name-Element (XMLA)
  Enthält den Namen eines attributelements für das übergeordnete Element [Attribut](attribute-element-xmla.md) oder [Übersetzung](translation-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Vorgänger oder übergeordnetes Element:|Cardinality|  
|[Attribut](attribute-element-xmla.md)|1-1: Erforderliches Element, das nur einmal auftritt.|  
|[Übersetzung](translation-element-xmla.md)|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Attribut](attribute-element-xmla.md), [Übersetzung](translation-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Für `Attribute` Elemente, die `Name` Element enthält den Namen des attributelements eingefügt oder aktualisiert, während die `Insert` oder `Update` Befehl.  
  
 Für `Translation` Elemente, die `Name` Element enthält die Beschriftung des attributelements in der angegebenen Sprache der `Language` -Element des übergeordneten `Translation` Objekt. Wenn die `Name` Element nicht angegeben ist, oder eine leere Zeichenfolge enthält, den Wert des der `Name` -Element für die `Attribute` -Element, enthält die `Translation` Element wird verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [INSERT-Element &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Language-Element &#40;XMLA&#41;](language-element-xmla.md)   
 [Update-Element &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
