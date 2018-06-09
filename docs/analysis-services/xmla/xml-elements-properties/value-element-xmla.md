---
title: Value-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2ecaaf902ee1f29700b2d6333bbccd549d9c2193
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576792"
---
# <a name="value-element-xmla"></a>Value-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält den gewünschten Wert ein [Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) von hinzuzufügenden Elements ein [einfügen](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) Befehl oder ein [Zelle](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) Element aktualisiert werden ein [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Any|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [Zelle](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Bei **Attribute** -Elementen enthält das **Value** -Element den gewünschten Wert, den das Element nach der Übermittlung des **Insert** -Befehls enthalten soll. Weitere Informationen zum Einfügen von Elementen finden Sie unter [einfügen, aktualisieren und Löschen von Membern &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Bei **Cell** -Elementen enthält das **Value** -Element den gewünschten Wert, den die Zelle nach der Übermittlung des **UpdateCells** -Befehls enthalten soll. Der tatsächliche Wert, der in der Rückschreibetabelle für die Zelle gespeichert ist, ist die Differenz zwischen dem Originalwert der Zelle und dem gewünschten Wert der Zelle.  
  
 Der von diesem Element verwendete Datentyp sollte dem Datentyp der zu aktualisierenden Zelle entsprechen.  
  
 Weitere Informationen zum Aktualisieren von Zellen finden Sie unter [Aktualisieren von Zellen &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Siehe auch
 [CellOrdinal-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/cellordinal-element-xmla.md)   
 [INSERT-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [UpdateCells-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
