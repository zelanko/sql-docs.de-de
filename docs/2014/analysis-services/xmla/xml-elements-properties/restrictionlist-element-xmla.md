---
title: RestrictionList-Element (XMLA) | Microsoft-Dokumentation
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
- RestrictionList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords:
- RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 045c5644608c7f9537124450ef2c5637eebbb796
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314590"
---
# <a name="restrictionlist-element-xmla"></a>RestrictionList-Element (XMLA)
  Enthält eine Sammlung von Einschränkungsspalten und Werten, die von der [Discover](../xml-elements-methods-discover.md) -Methode verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Restrictions>  
   <RestrictionList>  
      <!-- Zero or more restriction columns and values -->  
   </RestrictionList>  
</Restrictions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Einschränkungen](restrictions-element-xmla.md)|  
|Untergeordnete Elemente|Einschränkungsspalten und Werte (siehe Hinweise).|  
  
## <a name="remarks"></a>Hinweise  
 Das `RestrictionList`-Element enthält eine Auflistung von Einschränkungsspalten, in denen die von der `Discover`-Methode zurückgegebenen Daten gefiltert werden können. Jede Einschränkungsspalte im `RestrictionList`-Element wird durch ein separates XML-Element definiert. Beim Wert der Einschränkungsspalte handelt es sich um die Daten, die im XML-Element enthalten sind. Der Name der Einschränkungsspalte entspricht dem Namen des XML-Elements.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
