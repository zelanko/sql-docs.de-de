---
title: Name-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ade2d80141163c3a2cb0effb805f82ee837390c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|Siehe Tabelle unten.|  
  
|Vorgänger oder übergeordnetes Element|Kardinalität|  
|------------------------|-----------------|  
|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|1-1: Erforderliches Element, das nur einmal auftritt.|  
|[Übersetzung](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [Übersetzung](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Bei **Attribute** -Elementen enthält das **Name** -Element den Namen des Attributelements, das vom bzw. während des **Insert** - oder **Update** -Befehl(s) eingefügt oder aktualisiert wird.  
  
 Bei **Translation** -Elementen enthält das **Name** -Element die Beschriftung des Attributelements in der Sprache, die vom **Language** -Element des übergeordneten **Translation** -Objekts festgelegt wird. Wenn das **Name** -Element nicht festgelegt ist oder eine leere Zeichenfolge enthält, wird der Wert des **Name** -Elements für das **Attribute** -Element, das das **Translation** -Element enthält, verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [INSERT-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Sprachelement &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Update-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
