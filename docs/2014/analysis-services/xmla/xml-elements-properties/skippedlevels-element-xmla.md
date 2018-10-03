---
title: SkippedLevels-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SkippedLevels Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#SkippedLevels
- microsoft.xml.analysis.skippedlevels
- urn:schemas-microsoft-com:xml-analysis#SkippedLevels
helpviewer_keywords:
- SkippedLevels element
ms.assetid: 4887b557-0ffc-4f42-b6b9-c98ad1208ca5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb76860b4f022bf076e7d5ccaed2234c917e3f73
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049410"
---
# <a name="skippedlevels-element-xmla"></a>SkippedLevels-Element (XMLA)
  Enthält die Anzahl der Ebenen, die von einem Attributelement, das vom übergeordneten [Attribute](attribute-element-xmla.md) -Element dargestellt wird, übersprungen werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Attribute>  
   ...  
   <SkippedLevels>...</SkippedLevels>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Integer|  
|Standardwert|0|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Attribut](attribute-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `SkippedLevels` Element bestimmt die Anzahl der Ebenen, die übersprungen werden, indem ein Attributelement, das vom übergeordneten Element definiert `Attribute` Element.  
  
## <a name="see-also"></a>Siehe auch  
 [INSERT-Element &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Update-Element &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
