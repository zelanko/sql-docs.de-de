---
title: Attribute-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f2519eb45be36526bbd5ac0450eb8a07b622aef
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="attributes-element-xmla"></a>Attributes-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Sammlung der [Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) -Elemente, die vom übergeordneten [Insert](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) - oder [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md) -Befehl oder vom übergeordneten [Where](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md) -Element verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Insert > <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Attributes>  
      <Attribute>...</Attribute>  
   </Attributes>  
   ...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Insert](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), [Where](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)|  
|Untergeordnete Elemente|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
