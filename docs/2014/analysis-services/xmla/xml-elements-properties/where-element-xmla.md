---
title: Wobei-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Where Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Where
- microsoft.xml.analysis.where
- http://schemas.microsoft.com/analysisservices/2003/engine#Where
helpviewer_keywords:
- Where element
ms.assetid: 81fb4190-3379-4ddf-8795-a0772f3b92bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9b45926ec9022e8e8092721580c2419b423dd2b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191370"
---
# <a name="where-element-xmla"></a>Where-Element (XMLA)
  Definiert eine Filterbedingung, die vom übergeordneten Befehl [Drop](../xml-elements-commands/drop-element-xmla.md) oder [Update](../xml-elements-commands/update-element-xmla.md) verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Drop> <!-- or Update -->  
   ...  
   <Where>  
      <Attributes>...</Attributes>  
   </Where>  
   ...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Drop](../xml-elements-commands/drop-element-xmla.md), [Update](../xml-elements-commands/update-element-xmla.md)|  
|Untergeordnete Elemente|[Attribute](attributes-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Für `Drop` Befehle, die `Where` -Element zusammen mit den [DeleteWithDescendants](deletewithdescendants-element-xmla.md) Element identifiziert den Bereich der zu löschenden Attributelemente.  
  
 Bei `Update`-Befehlen identifiziert das `Where`-Element den Umfang der zu aktualisierenden Attributelemente. Mehrere Attributelemente können über eine Kombination aus Attributen, die in der `Attributes`-Auflistung des übergeordneten `Update`-Befehls und der `Attributes`-Auflistung des `Where`-Elements enthalten sind, aktualisiert werden.  
  
 Weitere Informationen zum Löschen und Aktualisieren von Attributelementen finden Sie unter [Einfügen, Aktualisieren und Löschen von Elementen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
