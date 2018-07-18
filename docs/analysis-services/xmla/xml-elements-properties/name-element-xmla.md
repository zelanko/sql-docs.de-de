---
title: Benennen Sie-Element (XMLA) | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c0686dfbb5949c9b2fe3a20e34824e731369b266
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968882"
---
# <a name="name-element-xmla"></a>Name-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält den Namen eines attributelements für das übergeordnete Element [Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) oder [Übersetzung](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) Element.  
  
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
|Standardwert|InclusionThresholdSetting|  
|Cardinality|Siehe Tabelle unten.|  
  
|Vorgänger oder übergeordnetes Element|Cardinality|  
|------------------------|-----------------|  
|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|1-1: Erforderliches Element, das nur einmal auftritt.|  
|[Übersetzung](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [Übersetzung](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Bei **Attribute** -Elementen enthält das **Name** -Element den Namen des Attributelements, das vom bzw. während des **Insert** - oder **Update** -Befehl(s) eingefügt oder aktualisiert wird.  
  
 Bei **Translation** -Elementen enthält das **Name** -Element die Beschriftung des Attributelements in der Sprache, die vom **Language** -Element des übergeordneten **Translation** -Objekts festgelegt wird. Wenn das **Name** -Element nicht festgelegt ist oder eine leere Zeichenfolge enthält, wird der Wert des **Name** -Elements für das **Attribute** -Element, das das **Translation** -Element enthält, verwendet.  
  
## <a name="see-also"></a>Siehe auch
 [INSERT-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Language-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Update-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
