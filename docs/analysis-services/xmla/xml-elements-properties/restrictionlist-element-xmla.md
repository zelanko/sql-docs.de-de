---
title: RestrictionList-Element (XMLA) | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c802b20b0e2d6212f68fa4dc43c35426ff377957
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37994782"
---
# <a name="restrictionlist-element-xmla"></a>RestrictionList-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Sammlung von Einschränkungsspalten und Werten, die von der [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) -Methode verwendet werden.  
  
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
|Übergeordnete Elemente|[Einschränkungen](../../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
|Untergeordnete Elemente|Einschränkungsspalten und Werte (siehe Hinweise).|  
  
## <a name="remarks"></a>Hinweise  
 Das **RestrictionList** -Element enthält eine Auflistung von Einschränkungsspalten, in denen die von der **Discover** -Methode zurückgegebenen Daten gefiltert werden können. Jede Einschränkungsspalte im **RestrictionList** -Element wird durch ein separates XML-Element definiert. Beim Wert der Einschränkungsspalte handelt es sich um die Daten, die im XML-Element enthalten sind. Der Name der Einschränkungsspalte entspricht dem Namen des XML-Elements.  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
